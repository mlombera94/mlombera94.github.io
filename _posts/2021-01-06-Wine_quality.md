---
title: "Machine Learning with Wine Quality" 
toc: true
toc_sticky: true
tags: 
  - Data Science
  - Machine Learning
  - Support Vector Machines
  - R
  - Wine
---

[![View on GitHub](https://img.shields.io/badge/GitHub-View_on_GitHub-blue?logo=GitHub)](https://github.com/mlombera94/Wine-Classification)

## Summary: 

Ever wondered what would happen if we combined machine learning and wine together? In this fun little project, we attempt to use support vector machines using R to classify the quality of various red and white Portuguese "Vinho Verde" wines on a scale of 1-10 (1 being the worst to 10 being the best)using only the physicochemical properties of the wines. The full project involved using both support vector machines and neural networks and can be found by clicking on the github badge above. However, for the purposes of this post, we will focus primarily on how to deploy support vector machines. 

## Data: 
The <a href="https://archive.ics.uci.edu/ml/datasets/Wine+Quality" target="_blank">Wine Dataset</a> includes 6,497 observations with 12 variables in total. 
In order to train the models, the data is split into three datasets using random sampling methods: Training, Validation, and Testing. Because there are very few 
observations regarding quality three and nine wines, they are removed from the dataset to avoid introducing unneccessary noise in the data. 

## Step 1: Load Libraries and read in the Data
Let's begin by the loading the necessary libraries for this project. 
``` r
library(ggplot2)
library(tidyverse)
library(kernlab)
library(e1071)
library(caret)
```
As a quick summary of each libar, [ggplot2](https://ggplot2.tidyverse.or)]is used for data visualization, [tidyverse](http://vita.had.co.nz/papers/tidy-data.html) is a data cleaning tool, [kernlab](https://cran.r-project.org/web/packages/kernlab/kernlab.pdf) package containing multiple kernel based machine learning models, and [caret](https://cran.r-project.org/web/packages/caret/caret.pdf), a package containing miscellaneous functions for training and plotting classification and regression models.  
