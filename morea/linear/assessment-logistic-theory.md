---
title: "Linear methods: theory"
published: true
morea_id: assessment-logistic-thy
morea_summary: "Logistic regression theory"
morea_outcomes_assessed:
  - outcome-linear
morea_type: assessment
morea_start_date: "2024-01-24"
morea_labels:
---

# Theory
\\( \newcommand{\cD}{\mathcal{D}} \\)
\\( \newcommand{\E}{\mathbf{E}} \\)
\\( \newcommand{\q}{\mathbf{q}} \\)
\\( \newcommand{\w}{\mathbf{w}} \\)
\\( \newcommand{\x}{\mathbf{x}} \\)
\\( \newcommand{\y}{\mathbf{y}} \\)
\\( \newcommand{\z}{\mathbf{z}} \\)
\\( \newcommand{\k}{\mathbf{k}} \\)
\\( \newcommand{\upto}{,\ldots,} \\)
\\( \newcommand{\prob}{\mathbb{P}} \\)
We covered the basic highlights of linear methods in class, but these
topics are quite interesting. Here are different angles to think about them.

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

   It is also common to normalize the attention (by passing it through
   a softmax layer) to make it into a probability distribution, but
   let us not worry about normalization right away.

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


2. Fill in the mathematical details behind logistic regresion. Refer
   to this [handout](./logistic.pdf) for reference and help in this
   problem. Let the training data \\( (\x_i, y_i) \\), for \\(i = 1\upto
   n\\). The examples \\(\x\\) are from a continuous
   (real-valued) space and the labels \\(y_i\\) are from the set
   \\(\\{0,1\\}\\).  We will also use \\(X\\) (resp. \\(Y\\) ) to denote
   a random example (resp. label).
   
     1. Subject to \\( \E[X| Y=0] = c\\) for a real number \\(c\\),
		show that the maximum entropy conditional probability density
		on \\(X\\) given \\(Y=0\\) is
	   
	    \\[ f(X=\x | Y=0) = \exp(\beta_0 +\beta_1^T \x).\\]
	   
	    Explain also how the number \\(\beta_0\\) and the vector
		\\(\beta_1\\) can be determined in principle given any value
		for \\(c\\).  Similar observation holds for the conditional
		density of \\(X\\) given \\(Y=1\\).
	   
	 2. From Bayes' rule find \\(\prob(Y=0| X=x)\\) and \\(\prob(Y=1| X=x)\\).
	 
	 3. Show that an unbiased estimate of \\(\E[X|Y=j]\\) (for \\(j=0,1\\)) is
		 \\[ \frac{\sum_{i:y_i=j} \x_i }{N_j}\\]
		 where \\(N_j \)) is the number of examples in the training data with label \\(j\\).
		 
	 4. Show that
		 \\[ \E[X\prob(Y=j|X)] = \E[X|Y=j] \prob(Y=j). \\]
	 
	 5. A Monte Carlo estimate of \\(\E[X\prob(Y=j|X)]\\) is \\(\sum_i
		 \x_i \prob(Y=j|\x_i)\\).  Substituting the Monte Carlo
		 estimate, parts 2 and 3 into 4, set up an equality you would
		 solve to yield \\(\prob(Y=j|X)\\). This is the logistic regression model.
		 
	 6. Show that the equality in 5 above is exactly what you would solve from the basic
		 stat approach as well.
