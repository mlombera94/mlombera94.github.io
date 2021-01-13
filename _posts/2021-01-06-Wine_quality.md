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

Ever wondered what would happen if we combined machine learning and wine together? In this fun little project, we attempt to use support vector machines in R to 
classify the quality of various red and white Portuguese "Vinho Verde" wines on a scale of 1-10 using only the physicochemical properties of the wines. 

## Data: 
The <a href="https://archive.ics.uci.edu/ml/datasets/Wine+Quality" target="_blank">Wine Dataset</a> includes 6,497 observations with 12 variables in total. 
In order to train the models, the data is split into three datasets using random sampling methods: Training, Validation, and Testing. Because there are very few 
observations regarding quality three and nine wines, they are removed from the dataset to avoid introducing unneccessary noise in the data. 
