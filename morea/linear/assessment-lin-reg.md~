---
title: "Linear methods: theory"
published: true
morea_id: assessment-linear
morea_summary: "Linear methods"
morea_outcomes_assessed:
  - outcome-linear
morea_type: assessment
morea_start_date: "2024-01-24"
morea_labels:
---

# Theory
\\( \newcommand{\cD}{\mathcal{D}} \\)
\\( \newcommand{\q}{\mathbf{q}} \\)
\\( \newcommand{\w}{\mathbf{w}} \\)
\\( \newcommand{\x}{\mathbf{x}} \\)
\\( \newcommand{\y}{\mathbf{y}} \\)
\\( \newcommand{\z}{\mathbf{z}} \\)
\\( \newcommand{\k}{\mathbf{k}} \\)
We covered the basic highlights of linear methods in class, but these
topics are quite interesting. Here are different angles to think about them.
Work on these problems in teams. 

1. For a \\(n\times p\\) training matrix \\(X\\) with target \\(\y\\),
   we have seen that the least squares solution is \\[ {\hat \w} =
   (X^TX)^{-1} X^T \y, \\] so that on a test example \\(\z\\), the
   prediction is \\[ \z^T{\hat \w} = {\z}^T (X^TX)^{-1} X^T \y. \\]

   Furthermore let the projection of \\(\y\\) into the column space of
   \\(X\\) be 
   
   \\[ {\hat y} = \begin{bmatrix} {\hat y}_1\\\\ \vdots \\\\ {\hat y}_n\end{bmatrix}. \\] 
   
   We will try to understand
   (practicing what we know about matrix multiplication) linear
   regression in a different way. This view becomes useful when we
   start looking at something called _attention_ in Transformer-based
   Large Language Models (like chatGPT or most other models in popular
   imagination).  In the attention approach,
   there is a dictionary \\(\cD\\) (think of a python dictionary
   object)---a set of key-value pairs, say \\((\k_i, v_i)\\), where
   \\(i\\) runs from 1 through \\(n\\). Given a query \\(\q\\), the
   attention mechanism computes the attention the query gives to each
   key \\(\k_i\\) as

   \\[ \alpha(\q, \k_i) = (W_q \q)^T (W_k \k_i), \\]

   where \\(W_q\\) and \\(W_k\\) are weight matrices. An example of such
   weight matrices would be to pass the key/query through a
   neural network, but in general, we could think of them as 
   transformations that prepare the key and query to interact with each
   other. Now, the attention mechanism returns a weighted sum of the
   values in the dictionary, with each value \\(v_i\\) being weighted
   by the attention given to its key, namely

   \\[ \sum_{i} \alpha(\q, \k_i) v_i. \\]

   It is also common to normalize the attention (or pass it through a
   softmax layer), but let us not worry about normalization right
   away.

    * Can you show that the linear regression prediction falls into
  	  this template? Let me get you started: the test sample, \\(\z\\) can
  	  be thought of as the query. What would be the key/value pairs?
  	  What would be the transformation matrices?

    * If \\(\y\\) could be perfectly modeled by a linear model (that
  	  is \\(\y\\) is in the column space of \\(X\\)), what will be the
  	  output of the above linear regression attention if one
  	  of the training examples, \\(\x_i\\), is used as the query? What
  	  if \\(\y\\) cannot be perfectly modeled linearly?

   In fact, other machine learning algorithms, not just linear
   regression, can be thought of in this framework as well. There is
   more to how attention works, of course, but it naturally follows from
   what we have always done.


2. Prove that in the case of binary classification, the line onto
   which the Fisher discriminant projects all the training points onto
   is along the Linear Regression solution (with class labels \\(\pm
   1\\). Assume the two classes are balanced (that is they have the
   same number of points).  You are welcome to use any resource on the
   web for this.

   How would you obtain the Fisher discrimant for binary
   classification with Linear Regression if the classes were not
   balanced (there are more examples for one class)?

3. Build a neural network with one neuron (with an appropriate choice of
    a loss function, regularization, and activation) that mimics
	 * Linear Regression 
	 * Linear Regression with regularization (LASSO or Ridge)
	 * Linear classification via Perceptrons
	 * Linear classification via Support Vector machines (linear kernel)
   	Optimize the neural network weights using Stochastic Gradient Descent,
	and see how closely you can match the optimal fit obtained by
	corresponding closed form solutions. 

4. In social sciences and economics, the way data is collected
    sometimes renders different examples to be dependent. In such
    cases, _mixed effects_ models are often used in place of vanilla
    linear regression we studied in class. Find datasets or
    applications where mixed effects models are more appropriate than
    vanilla linear regression.


5. Generate a set of \\(n\\) examples with \\(p\\) features (your code
   should be able to generate examples for any input values of \\(n\\)
   and \\(p\\)) with binary class labels so that the Fisher
   discriminant direction (the line onto which the points are
   projected) coincides with the first principal component of the data
   matrix. Specifically, generate a \\(n\times p\\) data matrix
   \\(X\\), binary class labels for each row of \\(X\\), so that the
   Fisher discriminant projection coincides with the first principal
   component of \\(X\\).
   
