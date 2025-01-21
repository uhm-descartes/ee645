---
title: "Logistic Regression"
published: true
morea_id: assessment-logistic
morea_summary: "Logistic Regression"
morea_outcomes_assessed:
  - outcome-linear
morea_type: assessment
morea_start_date: "2024-01-20"
morea_labels:
---

1. From google
   [drive](https://drive.google.com/drive/folders/1TvOiktbpG784mYLSRRjk6LULKVGECH3r?usp=sharing),
   obtain the Hawaii-Mar dataset that contains hourly weather data in
   the month of Mar for Hawaii for approximately 40 years. Take the
   help of your mentors to read the format of the dataset. Use this
   dataset to build a logistic regression model that predicts cloud
   cover 6 hours in the future using current weather
   measurements. Evaluate your model with a receiver operating
   characteristic curve, and find the area under the curve. For the
   evaluation, you will have to make sure that the training and test
   data are not the same. It is up to you to figure out how to manage
   this. Test your model on weather data from Stockholm (again obtain
   the dataset from koa). How good or bad is the model trained in
   Hawaii?

2. Build a neural network with one neuron (with an appropriate choice of
    a loss function, regularization, and activation) that mimics
	 * Linear Regression 
	 * Linear Regression with regularization (LASSO or Ridge)
	 * (optional) Linear classification via Perceptrons
	 * Binary logistic regression 
	 * (optional) Linear classification via Support Vector machines (linear kernel)
	
	You are welcome to use either pytorch or any wrapper around
	tensorflow. I would encourage you to use pytorch (just a lot
	simpler down the line). But if you are already established
	with keras or another wrapper, stick with it.
	
    You do not need to turn in the optional parts yet---you can do so if
	you already know about perceptrons and support vector machines. Optimize the
	neural network weights using Stochastic Gradient Descent, and see
	how closely you can match the optimal fit obtained by
	corresponding closed-form/convex-optimized solutions.

