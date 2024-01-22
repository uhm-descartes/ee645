---
title: "Linear Regression"
published: true
morea_id: assessment-lr
morea_summary: "Linear Regression"
morea_outcomes_assessed:
 # - outcome-CHANGE-ME
morea_type: assessment
morea_start_date: "2021-07-16T09:00"
morea_labels:
---
# Theory

\\( \newcommand{\w}{\mathbf{w}} \\)
\\( \newcommand{\x}{\mathbf{x}} \\)
\\( \newcommand{\y}{\mathbf{y}} \\)
\\( \newcommand{\z}{\mathbf{z}} \\)
Here are a few questions to assess where you stand. The first question is just a recap of what you learned, but the remaining three probe your understanding. 

* (basic) Let \\(B\\) be a \\(n\times p\\) matrix of training examples, with target
\\(\y\\).  Derive the OLS/ML and the Bayesian linear regressors for the target using the training data. You do not need to submit this, just make sure you understand how to.

* Let \\( \w_1 \\) and \\( \w_2 \\) respectively be the projections of
points \\( \z_1 \\) and \\( \z_2 \\) into a linear space \\( \mathcal L \\), that
is, for \\( i = 1,2 \\),
\\[ \w_i = \arg\min_{ \w \in {\mathcal L} } || \z_i - \w ||^2, \\]
What is the projection of \\( \alpha \z_1 +\beta \z_2 \\) into \\( \mathcal L \\)? You may want to see the fourth problem, part (iii) too.

* Show that if the columns of \\( B \\) are linearly independent, \\(B^TB\\) is invertible.

* If \\(B = \begin{bmatrix} 1 &0 \\\\ 1 & 1 \\\\ 1& 2 \end{bmatrix}\\) and
\\({\bf y} = \begin{bmatrix} 6 \\\\ 0 \\\\ 0 \end{bmatrix}\\), find \\[(i)
\x_{OLS} = \arg\min_{\x} || \y - B\x ||^2, \\] (ii)
the point \\(p\\) in the column space of \\(B\\) closest to \\(\y\\), and
(iii) a matrix \\(P\\) such that the projection of any vector \\(\z\\)
with three coordinates into the column space of \\(B\\) is \\(P\z\\). 

* Let \\(B\\) be a \\(n\times p\\) matrix of training examples, with
target \\(\y\\). Let \\(B_{-1}\\) be the \\( n\times (p-1)\\) matrix with
the first column deleted from \\(B\\). Can you find a unit vector in the
column space of \\(B\\) that is perpendicular to the column space of
\\(B_{-1}\\)?



# Practice

The following data is from the M.D. Anderson Cancer Center, and
contains 191 patients diagnosed with Acute Myelogenous Leukaemia, a
kind of cancer. Measurements include clinical variables including
demographics, history of cancer, chemotherapy or radiation treatments,
blood tests, as well as cytogenic, genomic and proteomic measurements.
These patients were treated with a particular treatment, and we need
to model why some patients responded to the treatment and others did
not.  A full list of measurements and descriptions are available
[here](https://www.synapse.org/#!Synapse:syn2455683/wiki/64621),
though for this problem, you will not need a crash course in biology.
The dataset is available
[here](https://uhm-descartes.github.io/ee445/morea/linear-regression/trainingData-release.csv),
and has been downloaded from
[here](https://www.synapse.org/#!Synapse:syn2488690).

The task is to model the following targets: 

 * resp.simple: Response to treatment, categorical (CR: complete response or RESISTANT)
 * Relapse: Whether the patient had a relapse, categorical (Yes, No, NA)
 * vital status: Final status of patient at the end of study, categorical (A: alive or D: deceased)
 * Overall_Survival: Overall survival in weeks from diagnosis to exiting the study, real valued data
 * Remission Duration: Duration of time in remission in weeks (numerical data or NA)
 
Build linear regression based models that predict each of the above
targets. Note that you have a lot of features (about 271), but only
191 patients, typical of most medical applications. You cannot use
vanilla linear regression. This statement is deliberately left open
ended. Work with me to come up with a plan to develop and implement
your approch in tackling this task, and subsequently write up a report
about your efforts. In any report you write, please be sure to cite
the paper

Hu et. al., A quantitative analysis of heterogeneities and hallmarks in acute myelogenous leukaemia. Nature Biomedical Engineering, vol 3, Nov 2019, pages 889-901.

for the data.
