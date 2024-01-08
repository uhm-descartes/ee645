---
title: "Autoencoders"
published: true
morea_id: experience-auto
morea_type: experience
morea_summary: "Autoencoders and SVD"
morea_start_date: "2021-07-15T23:00"
morea_labels:
---

First review the section about eigenvalues and eigenspaces
[here]. Recall that \\({\mathbb R}^p\\) represents the linear space of
all vectors with \\(p\\) real coordinates. For a matrix \\(n\times p\\)
matrix \\(X\\), one can use spectral decomposition of \\(X^TX\\)
(respectively \\(XX^T\\)) to find an orthonormal basis for \\({\mathbb
R}^p\\) (respectively \\({\mathbb R}^n\\)) using eigenvectors of \\(X^TX\\)
(respectively \\(XX^T\\)), and therefore for the rows (respectively
columns) of \\(X\\). Assume that \\(n \ge p\\), and let the eigenvalues
of \\(X^TX\\) be \\(\lambda_1\ge \lambda_2 \cdots \ge \lambda_p\\), then
the highest \\(p\\) eigenvalues of \\(XX^T\\) are also
\\(\lambda_1, \lambda_2 \upto \lambda_p\\), while the remaining \\(n-p\\)
eigenvalues are all 0. 


Let \\(V\\) (respectively \\(U\\)) be the matrix formed
by placing as columns the orthonormal basis obtained by the
eigendecomposition of \\(X^TX\\) (respectively \\(XX^T\\)).
Let \\(\Sigma\\)
be the \\(n\times p\\) matrix formed with the positive square roots of
the eigenvalues of \\(X^TX\\) in all the diagonal locations.
The singular value decomposition observes that
$$ X = U \Sigma V^T. $$

The following
[notebook](https://uhm-descartes.github.io/ee445/morea/neural-networks/autoencoder.ipynb)
shows you how to build a neural network that recovers the singular
value decomposition, the autoencoder. In the assessment, you will
reuse the code, but with non-linear activations to project the MNIST
dataset into a low dimensional manifold.

