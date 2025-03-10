---
title: "Kernel methods"
published: true
morea_id: assessment-kernels
morea_summary: "Problems and mini-project"
morea_outcomes_assessed:
 # - outcome-CHANGE-ME
morea_type: assessment
morea_start_date: "2021-07-16T09:00"
morea_labels:
---
# Theory
\\(\newcommand{\w}{\mathbf w}\\)
\\(\newcommand{\x}{\mathbf x}\\)
\\(\newcommand{\z}{\mathbf z}\\)
\\(\newcommand{\reals}{\mathbb R}\\)

1. Show that the distance of any point \\( \z_i\in \reals^p \\) from a hyperplane \\(\w^T\x -b=0 \\) (where \\(\w\\) and \\(\x\\) are in \\(\reals^p\\),
and \\(b\in \reals\\) is a number) is given by

	$$\frac{\w^T \z_i -b }{|| \w||}.$$

2. Find an approach to assign probabilities to the classes using a support vector machine. See part 3 in the mini-project.

# Mini-project

Please take a look at the [following](https://archive.ics.uci.edu/dataset/350/default+of+credit+card+clients) credit risk dataset. Unlike real datasets, this has no missing values, and no complications in data preprocessing since we want to focus on the usage of kernel methods.

Build a model to predict risk using the base SVM approach by choosing
appropriate kernel. You need to separate out the data into train and
test parts, and no part of the test data should be touched in any
training step (not even to normalize). In the train part, you may want
to further hold out a validation set to make decisions. 
	
1. In the regular SVC approach, identify dual coefficients, support
   vectors, and explore how the kernel hyperparameters matter for the
   classifier.
   
2. A SVC generally treats the two classes the same: support vectors
   are equidistant (in the lifted space) from the separating
   hyperplane. In our problem, misclassification of one kind may be
   worse than the other. Find an approach to use different margins for
   positive and negative examples and explain why it should work.

Next, enhance the base methods with
	
3\.  Probability modeling for the credit risk (in your report,
   describe how the probability scoring works). This is a repeat of
   theory question 2.
   
4\.  Ensemble methods: rather than use just one classifier, use one of
   the two approaches (i) boosting or (ii) bagging. These are methods
   that take a base learner and amplify them in different
   ways. Boosting takes weak learners and amplifies their
   power. Bagging reduces the variance of learners by generating
   randomly subsampled training data and training multiple models on
   them. There are two kinds of base learners you could build: (i)
   randomly training on a subset of the training data (which bagging
   already does, so try this with boosting) or (ii) randomly training
   on a subset of the features (which you can use for
   bagging). Explore how various hyperparameters (the size of the
   subsets, kernel hyperparameters) matter for your prediction.

