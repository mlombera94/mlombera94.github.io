---
title: Projects
permalink: /_pages/projects/
toc: true
toc_sticky: true
gallery: 
  - url: /images/project/naive_bayes/unnamed-chunk-5-2.png 
    image_path: /images/project/naive_bayes/unnamed-chunk-5-2.png
    alt: "placeholder image 1"
    title: "Ratio of total tweets per Airline"
  - url: /images/project/naive_bayes/unnamed-chunk-5-4.png 
    image_path: /images/project/naive_bayes/unnamed-chunk-5-4.png
    alt: "placeholder image 2"
    title: "Frequency of each classified tweet per Airline"
  - url: /images/project/naive_bayes//unnamed-chunk-12-1.png 
    image_path: /images/project/naive_bayes/unnamed-chunk-12-1.png
    alt: "placeholder image 3"
    title: "Word Cloud Visualization of Positive Tweets"
  - url: /images/project/naive_bayes//unnamed-chunk-12-2.png 
    image_path: /images/project/naive_bayes/unnamed-chunk-12-2.png
    alt: "placeholder image 4"
    title: "Word Cloud Visualization of Negative Tweets"
  - url: /images/project/naive_bayes//unnamed-chunk-18-1.png 
    image_path: /images/project/naive_bayes/unnamed-chunk-18-1.png
    alt: "placeholder image 5"
    title: "Confusion Matrix for Binary Classification (91.61% classified correctly)"
  - url: /images/project/naive_bayes//unnamed-chunk-16-1.png 
    image_path: /images/project/naive_bayes/unnamed-chunk-16-1.png
    alt: "placeholder image 6"
    title: "Confusion Matrix for Positive/Negative/Neutral Classification (77.42% classified correctly)"
---

## **Forecast Application with R-shiny**
[![View on GitHub](https://img.shields.io/badge/GitHub-View_on_GitHub-blue?logo=GitHub)](https://github.com/mlombera94/forecast_R-shiny) [![View on shinyapps.io](https://img.shields.io/badge/shinyapps.io-View_on_shinyapps.io-276DC3?logo=R)](https://mlombera.shinyapps.io/forecast_r-shiny/)

 **Summary:**
This R-shiny application was developed to allows users to forecast monthly demand of products by applying various time series models and comparing the performance of each model. There are four main functions of this application including:
- Uploading raw demand data in a csv format and filtering data
- Single SKU forecasts and visualization
- Batch SKU forecasts
- Statistical analysis/visualization

To view more information about the application, visit the [github page](https://github.com/mlombera94/forecast_R-shiny) and if you're interested in testing the application for yourself, visit the [shinyapp.io page](https://mlombera.shinyapps.io/forecast_r-shiny/) where the application is hosted. 

![gif2](https://user-images.githubusercontent.com/20471627/66339136-5872de80-e8f7-11e9-9f05-650156aff007.gif)

## **Airline Tweet Sentiment Analysis with Naive-Bayes Classification algorithm**
[![View on GitHub](https://img.shields.io/badge/GitHub-View_on_GitHub-blue?logo=GitHub)](https://github.com/mlombera94/airline_sentiment)

**Summary:**
The following project explores the efficacy of Naive Bayes algorithm for classifying tweets related to US airline services as either having positive, negative or neutral sentiment. The project uses the following <a href="https://raw.githubusercontent.com/mlombera94/airline_sentiment/master/Tweets.csv" target="_blank">Dataset</a> which can be downloaded from <a href="https://www.kaggle.com/crowdflower/twitter-airline-sentiment" target="_blank">Kaggle</a>. The machine learning project is split into two classification problems. The <a href="https://github.com/mlombera94/airline_sentiment/blob/master/NB_Classification__Pos%2C_Neg%2C_Nue_.md" target="_blank">first classification project</a> involves training the Naive Bayes algorithm to classify a tweet's sentiment as either positive, negative or neutral. The <a href="https://github.com/mlombera94/airline_sentiment/blob/master/NB_Classification_Binary__Pos%2C_Neg_.md" target="_blank">second classification project</a> involves only training the Naive Bayes algorithm to classify a tweet's sentiment as either positive or negative.
 
This project provides a great opportunity to work with a simple yet effective machine learning model as well as the opportunity to work with textual data scraped from Twitter. To learn more about this project and it's findings, visit the [github page](https://github.com/mlombera94/airline_sentiment)

{% include gallery caption="Naive Bayes Airline Tweet Sentiment Visualizations" %}
