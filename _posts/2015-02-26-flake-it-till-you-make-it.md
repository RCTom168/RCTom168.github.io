---
layout: post
title: CS Build Week 1 LS K-Nearest Neighbors Model

image: /img/1024px-Flag_of_the_Governor_of_Hong_Kong_(1959–1997).svg.png
---

![KNN Visual.jpeg](/img/KNN Visual.jpeg)

## Introduction
  In the data science world, there are many different machine learning algorithms to choose from. Each one is unique in its function and complexity. 

Some of the most notable ones are:
  1) K-Means Clustering
  2) K-Nearest Neighbors
  3) Decision Tree Learning
  4) Naive Bayes Classifier
  5) DBSCAN Clustering
  
Today, I will be breaking down, analyzing, and recreating the K-Nearest Neighbors algorithm.


## What is the K-Nearest Neighbors Algorithm?
  The KNN alogrithm is a simple and versatile machine learning algorithm that has a wide range of applications. It can be used in industries such as finance, healthcare, and political science, as well as more niche fields like facial recognition, handwriting detection, image recognition, and video recognition. KNN is considered to be a non-parametric, instance-based learning form of pattern recognition used for both classification and regression. It falls under the umbrella of supervised learning algorithms, and operates on labeled datasets to predict either a class (as in classification) or a numerical value (as in regression)


## Our reconstruction
  To begin we need to determine our variables, the amount of neighbors that we will measure data points against, and how the data points will be weighted against each other.

  ![class LS_K_Nearest_Neighbors.png](/img/class LS_K_Nearest_Neighbors.png)


  To start our algorithm, we first need to determine the distance between 2 points. These points are the data points that we want to classify and the training point that we are using for comparison. For this, we are using the common Euclidian distance formula, but others could be used as well, such as the Manhattan distance formula.
 
  ![def euclidian_distance.png](/img/def euclidian_distance.png)


  Of course, we want to make sure that the data is all fit to the model.
 
  ![def fit.png](/img/def fit.png)
 

  Our next step is to find the neighbors that we want to check in with. A KNN model will only work if other data points can be located, and we need to work with the closest ones.
  
  For our purposes, the actual distance value itself between the data points is irrelevant, what we need is the order of the data points in terms of how close or far they are from the data point we are classifying.
  
  The euclidean_distance function will do the measuring, and then we have to determine the order of these distances, and hence, the order of the data points.

  For the following kneighbors function, the data points that we want to classify are part of the test dataset and the rest of the data points are part of the training dataset. When we measure the distance between a data point in the test dataset and the training dataset we store these distance as point distributions in the point_dist variable.
  
  Each row stored in point_dist represents a list of distances between 1 test dataset data point against all of the data points in the training dataset.
  
  After each test dataset data point has been measured against we will list (enumerate) and sort each row according to the measured distances. It is important to do this for ALL of the rows because we don't want to lose the information of the training data points that we calculated the distances with. This information will be important when we refer to them later.

  The sorted_neigh variable holds the first nearest neighbors of our test data points, sorted accordingly by their measured euclidian distances. From sorted_neigh, we extract the indicies and distance values and return them.

  ![def kneighbors.png](/img/def kneighbors.png)


  Once the nearest neighbors have been located and measured, we use our predict function to attempt to predict the classes that each of our test data points belong to. 
  
  The method that we use to determine this differs depending on the criteria that we have chosen. One of the more important choices that needs to be determined is how the data points will be weighed against each other, uniformly or by distance.

  Weighing by uniform involves getting the indices of each neighbor and then using the indices to match their corresponding class labels with those from the training dataset. Each row in the neighbors variable corresponds to the set of neighbors that each one of the test data points has.

  The bincount function is then used to find the occurrences of the class labels,and to get the index that has the maximum occurrence. This index corresponds to the predicted class label.

  ![def predict_distance.png](/img/def predict_distance.png)


  Weighing by distance involves finding the mean inverse of the distances between each neighbor and calculating the class probabilities for each test data point.

  ![def predict_uniform.png](/img/def predict_uniform.png)


## The Results
  I was able to test my model against 3 Scikit Learn datasets:
  
The Breast Cancer dataset

  ![breast_cancer_test.png](/img/breast_cancer_test.png)
  
  
The Iris dataset
  
  ![iris_test.png](/img/iris_test.png)
  
and The Wine dataset
  
  ![wine_test.png](/img/wine_test.png)
