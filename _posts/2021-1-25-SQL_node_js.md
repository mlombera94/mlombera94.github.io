---
title: "No Data? No Problem!" 
toc: true
toc_sticky: true
tags: 
  - MySQL
  - Node.js  
gallery: 
  - url: /images/project/no_data_no_problem/successful_node.png 
    image_path: /images/project/no_data_no_problem/successful_node.png
    alt: "placeholder image 1"
    title: "Successful app.js Run" 
gallery2: 
  - url: /images/project/no_data_no_problem/successful_mysql.png 
    image_path: /images/project/no_data_no_problem/successful_mysql.png
    alt: "placeholder image 1"
    title: "Successful MySQL Query"
  - url: /images/project/no_data_no_problem/successful_mysql2.png 
    image_path: /images/project/no_data_no_problem/successful_mysql2.png
    alt: "placeholder image 1"
    title: "Successful MySQL Query"
---

## Introduction: 

Interested in generating mock data to work with in your MySQL database? What if you could generated thousands of entries of realistic mock data including names, email addresses, street addresses, business occupations, and phone numbers. With the help of a Node.js package called [faker.js](https://www.npmjs.com/package/faker), realistic data can be generated with a few lines of code and then inserted into your MySQL table(s). This post explains step by step how to get started by first connecting to Node.js to MySQL. 

## Connect Node.js to MySQL

Before you begin, make sure to have MySQL installed on your computer. You can download MySQL using the following [link](https://www.mysql.com/downloads/). 

### Step 1: Create a new Node.js project
As with any new Node.js project, it's important to create a new directory and initialize it using the NPM

```bash
mkdir node_js_DB && cd node_js_DB
npm init --y
```

### Step 2: Install mysql and faker node modules
The mysql module connects Node.js to MySQL while faker generates mock data. Both will be used in conjuction to generate mock data and insert into MySQL table(s).
Learn more about [mysql](https://www.npmjs.com/package/mysql). 
```bash
npm install --save mysql
npm install --save faker
```

### Step 3: Connect with MySQL
Within the same directory, create an **app.js** file and copy/paste the code below. Make sure to adjust the code below to account for you MySQL credentials. 
```javascript
var db = require('mysql');
var faker = require('faker');

var conn = db.createConnection({
  host: "localhost",
  user: "root",
  password: "password",
  database: "database_name"
});

conn.connect(function(err) {
  if (err) throw err;
  console.log("Connected!");
});

conn.end();
```

Once the code has been copied/pasted and the MySQL server credentials have been updated, run the code in your terminal using the following command.
```bash
node app.js
```
Your terminal should say 'Connected!' once a connection has been established. 

### Troubleshooting
It's possible you may recieve the following error message if you have the latest MySQL server install. 
```javascript
{
  code: 'ER_NOT_SUPPORTED_AUTH_MODE',
  errno: 1251,
  sqlMessage: 'Client does not support authentication protocol requested by server; consider upgrading MySQL client',
  sqlState: '08004',
  fatal: true
}
```

To remove this error, simply create a new user in your MySQL server with **'mysql_native_password'** authentication. First, log onto the MySQL server using root access. 
```bash
mysql -u root -p
```
Run the following commands in order.
```bash
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password'
``` 
Once the new credentials have been updated, Node.js should be connected to MySQL. 

## Create table 
Before we begin generating mock data, we will have to create a data table within the database specified in the app.js file to store the mock data. Navigate to your respective MySQL database and use the following code to create a table called **"users"**. 

To keep this example simple, we will add the following: **id**, **first name**, **last name**, **email**, and **created_at**. We will use **id** as the Primary Key for this table and designate it as an **INTEGER** type. Next, **first_name**, **last_name**, and **email** will be **VARCHAR** data that cannot have NULL values. Lastly, **created_at** will be designated as a **TIMESTAMP** type with **DEFAULT** set to **NOW()** in the absence of data. 

Copy/paste and run the following code within your MySQL server. 
```sql
CREATE TABLE users (
    id INTEGER AUTO_INCREMENT PRIMARY KEY,
    first_name VARCHAR(255) NOT NULL,
    last_name VARCHAR(255) NOT NULL,
    email VARCHAR(255) NOT NULL,
    created_at TIMESTAMP DEFAULT NOW()
);
```

## Generate mock data
Now that our table has been created in MySQL, let's return to our **app.js** file and add the necessary code to generate and insert mock data into our table. 

We will create 500 entries of mock data using a `for loop`, however, you can adjust the code and increase/decrease the number of total entries. The mock data will be stored in an array called **data**. Within the array **data**, we will store further arrays as each entry will include multiple data entries (first_name, last_name, etc.).  

Copy/paste the following code below your `db.createConnection();` code. 
```javascript
var data = [];
for(var i = 0; i < 500; i++){ // Adjust # to +/- # of entries
    data.push([
        faker.name.firstName(),
        faker.name.lastName(),
        faker.internet.email(),
        faker.date.past()
    ]);
};
```

## Insert data 
The next step is to insert the mock data into our MySQL table. Let's do this by creating a variable to store MySQL query that will be used within the **app.js** file. Make sure the name of the table you are inserting the data in matches the table within the database you connected to earlier. 

Copy/paste the following code below the previous code.
```javascript
var q = 'INSERT INTO users (first_name, last_name, email, created_at) VALUES ?';
```

The final step is to insert the data using the `conn.query()` function. Create a function to verify whether the data insertion was successful or not by returning either the `err` or the `result`. 

Copy/paste the following code below the previous code. 
```javascript
conn.query(q, [data], function(err, result) {
  console.log(err);
  console.log(result);
});
```

Next, let's comment out the following code from the initial set up as it is no longer necessary. 
```javascript
//conn.connect(function(err) {
//  if (err) throw err;
//  console.log("Connected!");
//});
```

## Final Code
Your final **app.js** code should look like the following:
```javascript
var db = require('mysql');
var faker = require('faker');

var conn = db.createConnection({
  host: "localhost",
  user: "root",
  password: "password",
  database: "database_name"
});

var data = [];
for(var i = 0; i < 500; i++){
    data.push([
        faker.name.firstName(),
        faker.name.lastName(),
        faker.internet.email(),
        faker.date.past()
    ]);
};

var q = 'INSERT INTO users (first_name, last_name, email, created_at) VALUES ?';

conn.query(q, [data], function(err, result) {
  console.log(err);
  console.log(result);
});

//conn.connect(function(err) {
//  if (err) throw err;
//  console.log("Connected!");
//});

conn.end();
```

Go ahead and save the file. Once you're ready, open up your terminal to the file directory and run the **app.js** file with the following. 
```bash
node app.js
```
## Successful Insertion
You should see something similar if your mock data insertion was successful. 
{% include gallery id="gallery" caption="* Note the node.js filename used is different" %}
 
Just to double check our data insertion was successful, let's query data from the users table. 
{% include gallery id="gallery2" caption="MySQL Queries" %}
 
## Conclusion
Using Node.js, we learned how to quickly set up a connection between node.js and our MySQL server. Once connected, we used the faker.js and mysql.js packages to create mock data and insert realistic data into a table within our database. The possibilities are endless as faker.js provies various functions to create different types of mock data including account numbers, addresses, credit card numbers and much more! 
