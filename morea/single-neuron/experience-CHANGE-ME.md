---
title: "Python Notebook"
published: true
morea_id: experience-snn
morea_type: experience
morea_summary: "Perceptron/Linear Regression/SVM"
morea_start_date: "2021-07-15T23:00"
morea_labels:
---

# Build and train on keras

The following python
[notebook](https://uhm-descartes.github.io/ee445/morea/single-neuron/perceptron.ipynb)
walks you through building a perceptron and replicating the Perceptron Algorithm using
the stochastic gradient descent algorithm. Along these lines, you are asked to replicate
the Linear Regression and the Support Vector Machine algorithms as well.

The particular point to note is the perceptron loss defined in the notebook. This is a tensorflow
function written in the notebook rather than a loss function imported from keras, and
it implements the loss 
\\[ l(y, \hat{y})  = \max \bigl[ 0, - y \hat{y} \bigr], \\]
where \\(y\\) is the true label of an example \\(\textbf{z}\\) and \\(\hat{y} = \textbf{w}\cdot \textbf{z} -b \\) is the prediction
of the perceptron with current weight \\(\textbf{w}\\). 

As you can see, to replicate the Perceptron Learning algorithm, we just call upon the Stochastic Gradient Descent
algorithm with learning rate 1 on the above loss function. This has the same effect as the Perceptron
Learning Algorithm described in the handout. In class, we computed the gradients and figured out why this
should be so. Do you see this?


## Submission Instructions

Try to get the Linear Regression and SVM solutions to match the analytically calculated versions as closely as possible. Stochastic
Gradient Descent is not the greatest algorithm, and you may not be able to do it very closely. But look up improvements on
SGD and try to get them to give you an answer as close to the analytical minimum as possible. Please submit the notebook on Laulima.
