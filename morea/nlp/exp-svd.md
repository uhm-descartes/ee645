---
title: "Understanding SVD"
published: true
morea_id: exp-svd
morea_type: experience
morea_summary: "Singular value decompositions"
morea_start_date: "2025-03-25"
morea_sort_order: 4
morea_labels:
---

# Singular Value Decomposition
\\( \newcommand{\u}{\mathbf{u}} \\)
\\( \newcommand{\v}{\mathbf{v}} \\)
\\( \newcommand{\upto}{,\ldots,} \\)
\\( \newcommand{\prob}{\mathbb{P}} \\)
Use the following [notebook](./demosvd.ipynb) to run the simulations. The anonymized movie preference data is [here](./movieratingsfall23.csv).

## Motivation
The singular value decomposition is a neat way to understand what is happening with matrix operations, and one good direction to interpret LLMs under the hood. We begin with a motivating example: the movie ratings data. The below is a snippet of preferences (from 1-5 where 5 is best) of 26 movies rated by 61 students (anonymized):

<img src="./movieprefs.png" alt="Movie ratings" width="900px"/>

Let \\( R\\) be the \\(n\times p\\) matrix of these movie ratings, and let \\(X\\) be the centered version of \\(R\\) (namely, the mean of all the rows of \\(R\\) is subtracted out from each row of \\(R\\)). In this specific example, \\(n=61\\) and \\(p=26\\). From what we learned about PCA, the directions of maximum variance of the rows are captured by the eigenvectors of \\(X^TX\\). Let \\(V\\) be the matrix of eigenvectors of \\(X^TX\\), i.e. \\(V\\) is \\(p\times p\\) whose columns are the eigenvectors of \\(X^TX\\). Following convention, let the eigenvectors be arranged as the columns of \\(V\\), \\(\v_1\upto \v_n\\), with associated eigenvalues \\(\lambda_1\upto \lambda_p\\) satisfying \\(\lambda_1\ge \lambda_2\ge\cdots\ge \lambda_p\\). Therefore, we have for \\(i=1\upto p\\) that

$$ X^TX \v_i = \lambda_i \v_i. \tag*{(1)}$$

Say we do that and examine the eigenvectors. The eigenvectors assign
weights to the \\(p\\) movies, and are directions in the movie
space. In large datasets, we would probably think of them as "genres". With the
small set we have, we don't quite that level of detail, but we still get something. For example, the second eigenvector assigns the following weights (we have omitted those with small weights):

<img src="./secondeig.png" alt="Weights for movies" width="400px"/>

A cursory post-fact interpretation may be that this direction weights heavy/intense movies at one end of the scale and lighter/relaxing ones at the other end. Not to worry, in larger systems, for example, weights in large language models, we will find much better interpretations and examples. The point is, the decomposition helped us find very interesting patterns in the data.

We could do the same with columns. For arguments sake, without worrying about
centering, let us say we start with \\(X^T\\), whose rows are the columns of \\(X\\). We would then take the eigendecomposition of the \\(n\times n\\) matrix \\( (X^T)^T X^T\\), ie \\(XX^T\\). Also note that multiplying both sides of Equation (1) with \\(X\\) on the left yields

$$ X X^T X \v_i = \lambda_i X\v_i, $$

which implies that so long as \\( X\v_i\ne 0\\), it is an eigenvector
of \\(XX^T\\) with eigenvalue \\(\lambda_i\\) for each \\(1\le i \le
p\\).  Let the above eigenvectors \\(X\v_i = \u_i\\) for all \\(i\\)
such that \\(X\v_i\ne 0\\). The remaining eigenvectors span the null
space of \\(XX^T\\), so the rest of the eigenvalues are 0, and one can
take any orthogonal basis of the null space to be the remaining
eigenvectors. Put the \\(n\\) eigenvectors as columns of a matrix \\(U\\)

You can also verify the same way that, if you fixed the eigenvectors of \\(XX^T\\) to be \\(\u_1\upto \u_n\\), as long as \\(X^T\u_i\ne 0\\) it will be an eigenvector of \\(X^TX\\). 

Putting these together, and letting \\(\Lambda\\) be the \\(p\times p\\) diagonal matrix whose entries are \\(\lambda_1\upto \lambda_p\\), we have (can you show why?)

$$ X^T X = V \Lambda V^T \text{ and } XX^T = U \begin{bmatrix} \Lambda\\ {\bf 0}_{(n-p)\times p} \end{bmatrix} U^T.$$

Multiplying the left equation by \\(X\\) on the left and noting 

$$XV = U\begin{bmatrix} \Lambda \\ {\bf 0}_{(n-p)\times p}\end{bmatrix},$$ 

we have (show why?)

$$ XX^T X = U \begin{bmatrix} \Lambda^2 \\ {\bf 0}_{(n-p)\times p} \end{bmatrix} V^T, $$
and therefore noting that \\(V^T = V^{-1}\\), we have

$$ X = U \begin{bmatrix} \Lambda \\ {\bf 0}_{(n-p)\times p} \end{bmatrix} V^T. $$

This is the singular value decomposition. 


