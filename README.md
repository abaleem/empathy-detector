# Empathy Detector
![empathy-intro](http://blogs.jpmsonline.com/wp-content/uploads/2018/03/EmpathicDoctor.jpg)

by Abdullah Aleem </br>
Univeristy of Illinos at Chicago (CS 412 Intro to ML)

---

## Introduction
The task was to predict how	suitable a person is to volunteer at a non-profit organization working with	Alzheimer’s patients.

In the dataset Young People Survey (https://www.kaggle.com/miroslavsabo/young-people-survey/) people had rated different music genre, school subjects and answered questions about their fears, smoking habits, alcohol consumption, number of siblings etc.


## Table of Contents

- [Introduction](#introduction)
- [Preprocessing](#preprocessing)
- [Models Used](#models used)
- [Evaluation Metrics Used](#evaluation-metrics-used)
- [Results](#results)

## Preprocessing
- Encoded the object/strings type to categorical data so it would be similar to other rows.
- Dropped the rows that had undefined class (empathy).
- Binarized the class labels.
- Filled the missing values with the rounded mean for the column. I also saved the rounded means for each column so if we have some new testing data with missing values we can fill it using means for best performance 
- Converted Age, Height, Weight and Siblings to categorical data between 1 and 5 to normalize. I used reasonable Max and Mix values so if in future we have new testing data, it can be scaled accordingly.

## Models Used

I chose SVM with RBF kernel. I tried multiple linear models to eventually come up with the conclusion that the problem isn’t linearly separable, as they couldn’t converge to a good solution. The data had attributes like height which were continuous and had larger values than other attributes and hence data needed to be normalized. What I though was to convert everything to categorical so there might be a correlation between categories of attributes to the class labels. SVM with RBF kernel made the most sense because it would divide up these categories with different pairs of categories corresponding to different classes with, which is not the case in linear models or KNN where we use distances between attributes. SVM RBF made most sense with data and preprocessing and gave the best accuracy.

## Evaluation Metrics Used

I used a combination of 10fold cross validation accuracy, recall, and precision as metrics to evaluate the best classifier. It’s important to get high recall as we don’t want misclassify empathic persons. At the same time we want to achieve maximum accuracy to ensure our model is doing capable to classify. For tuning hyper parameters I split data in training and validation and optimized my model. 


## Results

**Baseline** 

- Random: Accuracy: 46.76 Recall: 49.23 Precision: 63.06 
- Mode: Accuracy: 64.68 Recall: 100.0 Precision: 64.66 
- Decision tree: Accuracy: 60.70 Recall: 71.54 Precision: 68.89 
- KNN: Accuracy: 62.12 Recall: 60.77 Precision: 75.96 
- Naive Bayes: Accuracy: 72.14 Recall: 80.77 Precision: 77.21 
- Random forest: Accuracy: 70.15 Recall: 94.61 Precision: 69.89

**My Model**

- SVM RBF: Accuracy: 73.63 Recall: 96.15 Precision: 72.25
