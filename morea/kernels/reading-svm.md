---
title: "Support Vector Machines"
published: true
morea_id: reading-svm
morea_summary: "Primal: Linearly separable"
morea_type: reading
morea_labels:
---
\\( \newcommand{\cD}{\mathcal{D}} \\)
\\( \newcommand{\q}{\mathbf{q}} \\)
\\( \newcommand{\w}{\mathbf{w}} \\)
\\( \newcommand{\x}{\mathbf{x}} \\)
\\( \newcommand{\y}{\mathbf{y}} \\)
\\( \newcommand{\z}{\mathbf{z}} \\)
\\( \newcommand{\k}{\mathbf{k}} \\)
\\( \newcommand{\reals}{\mathbb{R}} \\)
\\( \newcommand{\half}{\frac12} \\)
\\( \newcommand{\upto}{, \ldots, } \\)
\\( \newcommand{\cL}{\mathcal{L}} \\)
\\( \newcommand{\ed}{\stackrel{\mathrm{def}}{=}} \\)


## Support Vector Machines 
Consider classification of linearly separable examples.  We studied
Fisher discriminants in linear classification, but there are other
kinds of linear classifiers as well (logistic regression, and support
vector machines that we will see here).  Not all classification is
equivalent, even if they all classify the examples properly. 

Support vector machines capture the idea that the larger the
distance between the examples and the separating hyperplane, the more
desirable it is.

We will formulate an optimization problem for training that not only
tries to get a separating hyperplane, but also one that will ensure
that the examples are as far away from it as possible. 


#### Training for maximum margin
Suppose \\( \z_1\upto \z_n \\\) are \\(n\\\)
training examples in \(\reals^p\\) given to us with labels \\(y_1\upto y_n\\)
respectively (each label is either \\(+1\\) or \\(-1\\)). Let \\(\w\in\reals^p\\)
and \\(b\\) be a number, and define the distance of the $i'$th point from the plane $\w^T\x-b=0$ (where $\x$ is a dummy variable) to be $\gamma_i(\w,b)$, and
hence

$$\gamma_i(\w,b) = \frac{\w^T\z_i - b}{||\w||}.$$

Let the _margin_ of the classifier be
$$
\gamma(\w,b) = \min_{1\le i\le n} \gamma_i(\w,b) = \min_{1\le i\le n}\frac{\w^T\z_i - b}{||\w||}\tag*{(1)}
$$
so that the smallest distance between the examples and the hyperplane
is \\(\gamma(\w,b)\\).

From our training data, we want to obtain that plane \\(\w^T\x-b=0\\) which
classifies all examples correctly, but in addition has the largest
margin. This plane is what we will learn from the training examples, and
what we will use to predict on the test examples. 

So for training, we first set up an optimization. Note that \\(\gamma\\)
is some complicated function of \\(\w\\) and \\(b\\). Different values of
\\(\w\\) and \\(b\\) yield potentially different orientations and
intercepts of the separating hyperplane, and their margin is
determined by different examples (\ie the minimizer
in (1) is different).  Even though we may not have
\\(\gamma(\w,b)\\) in a simple form, we can still ask for

$$
\w^*,b^* = \arg\max_{\w,b} \gamma(\w,b)
$$
subject to \\( y_i(\w^T \z_i -b) \ge 0 \text{ for all } 1\le i\le n.\\)

In the optimization above, the first line asks to maximize the margin,
while the constraints (there are \\(n\\) of them) ensure that each
example is classified properly.

So far so good, but we don't really want to compute \\(\gamma(\w,b)\\\) or
try expressing it in any closed/numerical form. But there is a simple
conceptual way around it. Note that scaling both \\(\w\\) and \\(b\\) by the same
number doesn't change the margin. So when searching for the best \\(\w\\) and
\\(b\\), among all choices of the pair \\((\w, b)\\) that happen to be scalings
of each other, we only need to choose one representative. We do this choice
smartly, picking that value of \\((\w,b)\\) among all scalings that set
\begin{equation}
\min_{i} y_i(\w^T \z_i -b) =1\tag*{(2)}
\end{equation}
Note that the left side is not the margin \\(\gamma(\w,b)\\), but its numerator.


This now implies that for all valid \(\w, b\), (\ie the ones hat satisfy (2)),
the margin is
$$ \frac1{||\w||}.$$ 
We choose the best among them. Therefore

$$\w^*,b^* = \arg\max_{\w,b} \frac{1}{||\w||}$$
subject to \\(y_i(\w^T \z_i -b) \ge 1\\) for all \\(1\le i\le n.\\)

Inmaximizing \\(1/||\w||\\) is the same as minimizing \\(||\w||\\), which is in turn
the same as minimizing \\(\half ||\w||^2\\). We can therefore write our training
objective as obtaining the hyperplane \\( {\w^*}^T \x-b^*=0 \\), where 

$$  \w^*,b^* = \arg\min_{\w,b} \half{||\w||^2} \tag*{(3)}$$
subject to \\(y_i(\w^T \z_i -{b}) \ge 1 \\) for all \\(1\le i\le n.\\)


#### Lagrangian for the SVM problem
To write the Lagrangian for this problem, we rewrite each inequality
constraint above so that it looks like \\(f_i(\w,b) \le 0\\), namely

$$1-y_i(\w^T \z_i -{b}) \le 0.$$

Each inequality gets its own Lagrange multiplier \\(\lambda_i\\), so our
Lagrangian is (letting \\(\Lambda = (\lambda_1\upto \lambda_n)\\))

$$\cL(\w,b, \Lambda) = \half{||\w||^2} + \sum_{i=1}^n \lambda_i (1-y_i(\w^T \z_i -{b})).$$

Now consider the following problem for a specific choice of \\(\w\\) and \\(b\\),

$$\max_{\Lambda \ge 0}\cL(\w,b, \Lambda) ,$$

where \\(\Lambda\ge 0\\) is shorthand for \\(\lambda_1\ge 0, \lambda_2\ge
0,\cdots,\lambda_n\ge 0\\). Now if \\(\w\\) and \\(b\\) satisfy all constraints,
we will have for all \\(1\le i\le n\\) that

$$1-y_i(\w^T \z_i -{b}) \le 0,$$

therefore 

$$\cL(\w,b, \Lambda) = \half{||\w||^2} + \sum_{i=1}^n \lambda_i (1-y_i(\w^T \z_i -{b})) \le \half{||\w||^2}, $$

with equality in the second equation iff we choose \\(\lambda_i=0\\) for all \\(i\\). Therefore, for any  \\(\w\\) and \\(b\\) satisfying all constraints,

$$\max_{\Lambda \ge 0}\cL(\w,b, \Lambda)  = \half ||\w||^2.$$

On the other hand if \\(\w\\) and \\(b\\) are such that there is even a single
constraint violated, that is for some \\(j\\),

$$1-y_j(\w^T \z_j -{b}) \ge 0.$$

Then to maximize \\(\cL(\w,b, \Lambda)\\), we can choose \\(\lambda_j\to \infty\\),
therefore

$$\lambda_j(1-y_j(\w^T \z_j -{b})) \to +\infty,$$

therefore

$$\max_{\Lambda \ge 0}\cL(\w,b, \Lambda)  = \infty.$$

Putting it together

$$
\max_{\Lambda \ge 0}\cL(\w,b, \Lambda)  =
\begin{cases}
\half ||\w||^2 & \w, b \text{ satisfy all $n$ constraints}\\
\infty & \text{else.}
\end{cases}
$$

Let us call 

$$g(\w,b) \ed \max_{\Lambda \ge 0}\cL(\w,b, \Lambda)$$

for convenience. Now there is definitely at least one \\(\w\\), \\(b\\) that
satisfies all constraints (since the points are linearly
separable). Therefore, the smallest value \\(g(\w,b)\\) can take is
definitely not infinity (so any \\(\w,b\\) that violates any constraint
will never minimize \\(g(\w,b)\\)). That means that if we look for

$$\arg \min_{\w,b} g(\w,b),$$

the solution must be \\(\w^*,b^*\\) from (), since we are
minimizing \\(\half ||\w||^2\\) but only among such \\(\w,b\\) that satisfy
every constraint given.

Therefore, we can pose () as follows:

$$\w^*,b^* = \arg\min_{\w,b} \max_{\Lambda \ge 0} \cL(\w,b, \Lambda).\tag*{(4)}$$


We will call the above the \emph{primal} formulation of the
constrained optimization problem (3)---where we write the Lagrangian,
and observe that the solution of (3) is
obtained by the minmax formulation (4).


As the name ``primal'' suggests, we will also have a \emph{dual}
formulation of the optimization problem in (3). But before
we get into the dual formulation, we have a little segue into elementary
game theory.
