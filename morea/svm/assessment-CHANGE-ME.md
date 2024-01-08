---
title: "Support Vector Machine"
published: true
morea_id: assessment-svm
morea_summary: "Assessment"
morea_outcomes_assessed:
 # - outcome-CHANGE-ME
morea_type: assessment
morea_start_date: "2021-07-16T09:00"
morea_labels:
---
# Theory
* Follow the reading material and write up the dual formulation of the general
(not linearly-separable) support vector classifier formulation.

* One way to interpret the generalization ability of the support
vector classifier is dependent on the number of support vectors we
obtain.  Read and comment on the following recent award-winning
[paper](http://proceedings.mlr.press/v132/hanneke21a/hanneke21a.pdf)
on this subject. At an undergraduate (or beginning graduate, or if you
are graduate outside of learning theory/EE) level you may find reading
the paper to be advanced. Here is what you should do to begin:

** Collect all the different technical terms you find in the
introduction. For this paper, we have mentioned most of them in class.

** Look them up (with my help if necessary) so you understand the
context.  

** Understand the main results Thm 1 and 3. In learning theory and in
many other areas, the main result is usually a precise mathematical
statement. To understand this, you will need to (i) parse the logical
statement, (ii) see if you can apply it to corner cases and (iii)
compare with other statements you already know. At the beginner level
here, you should compare the statement with the Perceptron Learning 
bound in the Single Neuron Network module. 

You will realize that most of these things can be done by reading the
first 4 pages of the paper (and a lot of other background reading). 
Undergraduates can stop here. Graduate students should continue trying
to understand the results through Thm 6 in a similar fashion.

** Once you understand what the authors are trying to say, you unravel
the proofs. Reading the proofs is usually with your advisor in the initial
phases, where you learn how to parse critically, and extract from it 
broader principles. Not all authors write well unfortunately, but good
authors do this for you. 


# Practice

Implement the Support Vector Classifier on the leukemia dataset. Explore 
whether preselecting features before using the support vector classifier helps
or does not help.
