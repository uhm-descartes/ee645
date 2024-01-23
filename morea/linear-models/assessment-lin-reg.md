---
title: "Linear methods"
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
\\( \newcommand{\CD}{\mathcal{D}} \\)
\\( \newcommand{\q}{\mathbf{q}} \\)
\\( \newcommand{\w}{\mathbf{w}} \\)
\\( \newcommand{\x}{\mathbf{x}} \\)
\\( \newcommand{\y}{\mathbf{y}} \\)
\\( \newcommand{\z}{\mathbf{z}} \\)
\\( \newcommand{\k}{\mathbf{k}} \\)
We covered the basic highlights of linear methods in class, but these
topics are quite interesting. Here are different angles to think about them.

1. For a \\(n\times p\\) training matrix \\(X\\) with target \\(\y\\),
   we have seen that the least squares solution is \\[ {\hat \w} =
   (X^TX)^{-1} X^T \y, \\] so that on a test example \\(\z\\), the
   prediction is \\[ \z^T{\hat \w} = {\z}^T (X^TX)^{-1} X^T \y. \\]

   Furthermore let the projection of \\(\y\\) into the column space of
   \\(X\\) be \\[ {\hat y} = \begin{bmatrix} {\hat y}_1\\\\ \vdots
   \\\\ {\hat y}_n\end{bmatrix}. \\] We will try to understand
   (practicing what we know about matrix multiplication) linear
   regression in a different way. This view becomes useful when we
   start looking at something called attention in Transformer-based
   Large Language Models (like chatGPT).  In the attention approach,
   there is a dictionary \\(\cD\\) (think of a python dictionary
   object)---a set of key-value pairs, say \\((\k_i, v_i)\\), where
   \\(i\\) runs from 1 through \\(n\\). Given a query \\(\q\\), the
   attention mechanism computes the attention the query gives to each
   key \\(\k_i\\) as

   \\[ \alpha(\q, \k_i) = (W_q \q)^T (W_k \k_i), \\]

   where $W_q$ and $W_k$ are weight matrices. An example of such
   weight matrices would be to pass the key/query through a (linear)
   neural network, but in general, we could think of them as a
   transformation that prepare the key and query to interact with each
   other. Now, the attention mechanism returns a weighted sum of the
   values in the dictionary, with each value \\(v_i\\) being weighted
   by the attention given to its key, namely

   \\[ \sum_{i} \alpha(\q, \k_i) v_i. \\]

   It is also common to normalize the attention (or pass it through a
   softmax layer---do not worry if you do not recognize this word
   yet), but let us not worry about that right away.

   	  1. Can you show that the linear regression prediction falls into
  	  	  this template? Let me get you started: the test sample, $\z$
  	  	  can be thought of as the query. What would be the key/value
  	  	  pairs?  What would be the transformation matrices?

   	  2. If \\(\y\\) could be perfectly modeled by a linear model
  	      (that is \\(\y\\) is in the column space of \\(X\\)), what
  	      will be the output of the attention mechanism if one of the
  	      training examples, \\(\x_i\\), is used as the query? What if
  	      \\(\y\\) cannot be perfectly modeled linearly?

2. Prove that in the case of binary classification, the line onto
   which the Fisher discriminant projects all the training points onto
   is along the Linear Regression solution (with class labels \\(\pm
   1\\). Assume the two classes are balanced (that is they have the
   same number of points).  You are welcome to use any resource on the
   web for this.

   How would you obtain the Fisher discrimant for binary
   classification with Linear Regression if the classes were not
   balanced (there are more examples for one class)?

3. The following data is from the M.D. Anderson Cancer Center, and
   contains 191 patients diagnosed with Acute Myelogenous Leukaemia, a
   kind of cancer. Measurements include clinical variables including
   demographics, history of cancer, chemotherapy or radiation
   treatments, blood tests, as well as cytogenic, genomic and
   proteomic measurements.  These patients were treated with a
   particular treatment, and we need to model why some patients
   responded to the treatment and others did not.  A full list of
   measurements and descriptions are available
   [here](https://www.synapse.org/#!Synapse:syn2455683/wiki/64621),
   though for this problem, you will not need a crash course in
   biology.  The dataset is available
   [here](https://uhm-descartes.github.io/ee445/morea/linear-regression/trainingData-release.csv),
   and has been downloaded from
   [here](https://www.synapse.org/#!Synapse:syn2488690).

   The task is to model the following targets:

      1. resp.simple: Response to treatment, categorical (CR: complete
	   response or RESISTANT)
  
      2. Relapse: Whether the patient had a relapse, categorical (Yes, No, NA)

	  3. vital status: Final status of patient at the end of study,
	   categorical (A: alive or D: deceased)

	  4. Overall_Survival: Overall survival in weeks from diagnosis to
	   exiting the study, real valued data

	  5. Remission Duration: Duration of time in remission in weeks
	   (numerical data or NA)
 
   Build linear regression based models that predict each of the above
   targets. Note that you have a lot of features (about 271), but only
   191 patients, typical of most medical applications. You cannot use
   vanilla linear regression. This statement is deliberately left open
   ended. Work with me to come up with a plan to develop and implement
   your approch in tackling this task, and subsequently write up a
   report about your efforts. In any report you write, please be sure
   to cite the paper

    Hu et. al., A quantitative analysis of heterogeneities and
    hallmarks in acute myelogenous leukaemia. Nature Biomedical
    Engineering, vol 3, Nov 2019, pages 889-901.

    for the data.

4. In social sciences and economics, the way data is collected
    sometimes renders different examples to be dependent. In such
    cases, _mixed effects_ models are often used in place of vanilla
    linear regression we studied in class. Find a dataset or
    application where mixed effects models are more appropriate than
    vanilla linear regression.

