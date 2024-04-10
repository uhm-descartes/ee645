---
title: "Support Vector Machines"
published: true
morea_id: reading-svm
morea_summary: "Support Vector Machines"
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
that the examples are as far away from it as possible. To do this,
first note the following exercise.


#### Training for maximum margin
Suppose \\( \z_1\upto \z_n \\\) are \\(n\\\)
training examples in \(\reals^p\\) given to us with labels \\(y_1\upto y_n\\)
respectively (each label is either \\(+1\\) or \\(-1\\)). Let \\(\w\in\reals^p\\)
and \\(b\\) be a number, and define

$$\gamma_i(\w,b) = \w^T\z_i - b.$$


Therefore, the distances of the \\(n\\) points to the plane \\(\w^T\x-b=0\\) 
are respectively \\(\gamma_1/||\w|| \upto \gamma_n/||\w||\\). In addition,
let 

$$
\gamma(\w,b) = \min_{1\le i\le n} \gamma_i(\w,b) = \min_{1\le i\le n}\w^T\z_i - b\tag*{(1)}
$$

so that the smallest distance between the examples and the hyperplane
is \\(\gamma(\w,b)/||\w||\\). This is called the \emph{margin} of the classifier
\\(\w^T\x-b=0\\).

From our training data, we want to obtain that plane \\(\w^T\x-b=0\\) which
classifies all examples correctly, but in addition has the largest
margin. This plane is what we will learn from the training examples, and
what we will use to predict on the test examples. 

So for training, we first set up an optimization. Note that \\(\gamma\\)
is some complicated function of \\(\w\\) and \\(b\\). Different values of
\\(\w\\) and \\(b\\) yield potentially different orientations and
intercepts of the separating hyperplane, and their margin is
determined by different examples (\ie the minimizer
in\textasciitilde{}\eqref{eq:gamma} is different).  Even though we may not have
\\(\gamma(\w,b)\\) in a simple form, we can still ask for


$$\w^*,b^* = \arg\max{\w,b} \frac{\gamma(\w,b)}{||\w||}$$
subject to \\( y_i(\w^T \z_i -b) \ge 0 \text{ for all } 1\le i\le n.\\)

In the optimization above, the first line asks to maximize the margin,
while the constraints (there are \\(n\\) of them) ensure that each
example is classified properly.

So far so good, but we don't really want to compute \\(\gamma(\w,b)\\) or
try expressing it in any closed/numerical form. But there is a simple
conceptual way around it. Suppose \\(\w\\) and \\(\b\\) classified all examples
such that every example, \\(\z_1\upto \z_n\\) satisfied

\begin{equation}
\label{eq:constraints}
 y_i(\w^T \z_i -b) \ge \nu, \qquad 1\le i\le n.
\end{equation}

For a given \\(\w\\) and \\(b\\), since \\(\gamma(\w,b)/||\w||\\) happens to be the
distance of the closest point to the plane \\(\w^T \x -b =0\\), we could
satisfy all \\(n\\) constraints of\textasciitilde{}\eqref{eq:constraints} above for every value of \\(\nu\\) in the range \\(0 \le\nu \le \gamma(\w,b)\\) and for no
other.

Therefore, we ask to find the maximum number \\(\nu\\) such that all the
constraints in\textasciitilde{}\eqref{eq:constraints} are satisfied.
Note the shift now---we treat \\(\nu\\) as just a number (not a
function of \\(\w\\) and \\(b\\)) and see which is the largest combination
of the number \\(\nu\\), the vector \\(\w\\) and \\(b\\) that satisfies

$$\w^*,b^*,\nu^* &= \arg\max_{\nu,\w,b} \frac{\nu}{||\w||}$$
subject to \\(y_i(\w^T \z_i -b) \ge \nu \text{ for all } 1\le i\le n.\\)

We can make one more simplification. There is no distinction between
the plane \\(\w^T\x-b=0\\) and the plane
\\(k(\w^T\x-b) =0\\) for any real number \\(k\ne 0\\) (because
if \\(\x\\) satisfies the equation \\({\w}^T\x-{b}=0\\), it
automatically satifies the other and vice versa). So all the
candidates (\\(k{\w}, k{b}\\)), \\(k\ne 0\\), yield exactly the
same plane (and hence same margin). We may choose just one candidate among
these while searching for the optimum. To make our life simpler, we
can choose \\(k\\) such that 

$$\min_{1\le i\le n} k({\w}^T\z_i - {b}) = 1 $$

or equivalently, given any \\({\w}\\) and \\({b}\\), we scale it by
\\(k=\frac1\gamma\\), where \\(\gamma\\) is as defined as
in~\eqref{eq:gamma}, to get \\(\tilde{\w}\\) and \\(\tilde{b}\\), and
optimize over only the \\(\tilde{\w}\\) and \\(\tilde{b}\\).

Then, we will have 

$$\min_{1\le i\le n} (\tilde{\w}^T\z_i -\tilde{b}) = 1 $$

and the margin of the hyperplane \\(\tilde{\w}^T
\x-\tilde{b}=0\\) is \\(1/||\tilde{\w}||\\).
So we can rewrite our training goal to be the optimization

$$\w^*,b^*,\nu^* &= \arg\max_{\nu,\tilde{\w},b} \frac{1}{||\tilde{\w}||}$$
subject to \\(y_i(\tilde{\w}^T \z_i -\tilde{b}) \ge 1\\) for all \\(1\le i\le n.\\)

Clearly, the \\(\nu\\) 's are now superflous---they don't exist in either the
objective or the constraints---we can discard them.
In the above, the \\(\tilde\w\\) and \\(\tilde b\\) are just dummy variables,
we can call them by any other name and nothing will really change. Furthermore,
maximizing \\(1/||\w||\\) is the same as minimizing \\(||\w||\\), which is in turn
the same as minimizing \\(\half ||\w||^2\\). We can therefore write our training
objective as obtaining the hyperplane \\((\w^*)^T \x-b^*=0\\), where 

$$  \w^*,b^* &= \arg\min_{\w,b} \half{||\w||^2} \tag*{(2)}$$
subject to \\(y_i(\w^T \z_i -{b}) \ge 1 \\) for all \\(1\le i\le n.\\)

You may wonder why we transformed maximizing \\(1/||\w||\\) to minimizing
\\(\half ||\w||^2\\). The reason is that we want our objectives and
constraints to be \emph{convex} functions. We will have a little
digression here to define convex functions and sets, but practically
every large constrained optimization we can solve is convex (or we
just fake the steps of a convex optimization if we are stuck with
non-convex optimization). Often, even convex optimization does not
look that way to begin with---we need to tweak the formulation as 
above to get to the correct form.
