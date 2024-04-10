---
title: "Convex Functions"
published: true
morea_id: reading-convex
morea_summary: "Convex functions"
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

## Convex Functions

There are two closely related concepts here: a _convex set_ and and a
_convex function_, though we will restrict our attention to convex
functions. Convexity is a fundamental topic, though we did not go
through these in class---consider taking EE 617 for an indepth study
of this topic. But we will encounter some basics over and over again
in various fields, including when looking at gradient descent in more
detail.

Suppose \\(C\subset \reals^d\\) is a set of vectors with \\(d\\) coordinates.
Then we say \\(C\\) is a convex set if given \\(\x\\) and \\(\x'\\) in \\(C\\),
all points between \\(\x\\) and \\(\x'\\) are also in \\(C\\). Formally, if
\\(\x\in C\\) and \\(\x'\in C\\), we must have for \\(0\le \alpha\le 1\\),
the point \\(\alpha \x + (1-\alpha)\x'\in C\\),

A _convex function_ of \\(d\\) variables is any function \\(f\\) 
that satisfies for all points \\(\x\\) and \\(\x'\\), and all \\(0\le \alpha \le 1\\)
that

\\[ 
f(\alpha \x +(1-\alpha)\x') \le \alpha f(\x) + (1-\alpha) f(\x'),\tag*{(1)}
\\]

namely the chord connecting the points \\((\x, f(\x))\\) and \\((\x', f(\x))\\)
lies _above_ the surface \\(g(\x,y)=f(\x)-y=0\\) when we set the arguments
of \\(f\\) between \\(\x\\) and \\(\x'\\).

There are many other ways to identify convex functions in
some restricted cases. You should think of the following as properties
rather than definitions in the strict sense. 

**Tangents:** If \\(f\\) is also differentiable (or in multiple
dimensions, the gradient exists), then the tangent plane at any point
\\((\x_0, f(\x_0))\\) (the hyperplane perpendicular to the gradient) lies
completely below the surface \\(g(\x,y) = f(\x)-y=0\\). The tangent
interpretation is not a definition since there is no requirement that
convex functions have to be differentiable (they are just defined
through Equation (1)). So the tangent characterization only applies to
those convex functions that also happen to be differentiable as well, absence
of a derivative of a function is not a factor in determining convexity/absence thereof.

**Exercise** Let \\(x\\) be a real number.
Is the function \\(|x|\\) (absolute value of \\(x\\)) convex? Is it differentiable
everywhere?


(You can skip this derivation if you wish, but I recommend you try to
understand the following.)  Mathematically, consider the \\(d+1\\)
dimensional space (where we plot the arguments of \\(f\\) in the first
\\(d\\) dimensions, followed by the value of \\(f\\) in the last
dimension---this is like a 3d plot for a function of 2
variables, the argument of the function is on the \\(x-y\\) plane, and
the value \\(f(x,y)\\) is along the \\(z\\) dimension\}).  In this
\\(d+1\\)-dimensional space, let us plot tangents of the surface
\\(g(\x,y) = f(\x)-y =0\\), where \\(\x\\) corresponds to the
\$d-\$dimensional argument and \\(y\\) is the last dimension that will
represent the magnitude of the function (so the surface
\\(f(\x)-y=0\\) sets \\(y=f(\x)\\)). 

Specifically, let us look at the
tangent to the surface \\(g(\x,y)=0\\) at the point \\(\z_0=(\x_0,f(\x_0)\\). 

This is a plane that is perpendicular to the gradient of
\\(g\\), and which passes through the point above, \ie all points
\\(\z = (\x,y)\\) satisfying 

\\[ \bigl(\nabla_{\x,y} g \bigr)^T_{\z_0} ( \z-\z_0) = 0, \\] 

where \\(\nabla_{\x,y}\\) is the gradient with respect to all arguments of \\(g\\), _i.e._ all coordinates of \\(\x\\) _and_ \\(y\\). 

Note that 
\\[ \nabla_{\x\text{,y}} g = 
\begin{bmatrix} 
\nabla_x g \\\\ \frac{\partial g}{\partial y}\end{bmatrix} 
= \begin{bmatrix} \nabla_{\x} f\\\\ -1 \end{bmatrix}.  \\]

and therefore the
tangent is all points \\((\x,y)\\) satisfying 

\\[ \bigl(\nabla_{\x,y} g \bigr)^T_{\z_0} ( \z -\z_0) = \Bigl(\nabla_{\x} f \Bigr)^T_{\x_0}(\x-\x_0) -
(y- f(\x_0)) = 0, \\] 

or, reorganizing the above, the tangent plane is
all points \\((\x,y_\x)\\) satisfying 

\\[ y_\x = f(\x_0) + \Bigl(\nabla_{\x} f \Bigr)^T_{\x_0}(\x-\x_0).  \\] 

\\(f(\x)\\) is the value
of the function at any point \\(\x\\). If we require the tangent plane
to be below the function, it means that any point on the tangent plane
\\((\x, y_\x)\\) must be below the point \\((\x, f(\x))\\). That
means, if \\(f\\) is convex with the first derivative, we have for all
\\(\x\\) and \\(\x_0\\) that 

\\[
f(\x_0) + \Bigl(\nabla_{\x} f \Bigr)^T_{\x_0}(\x-\x_0) \le f(\x)
\\]

**Hessians:** Convex functions that have the second
derivatives can be characterized by their Hessians. Looking
at (1), and because the quadratic approximation
of \\(f(\x)\\) from the Taylor series around \\(\x_0\\)

\\[ f(\x_0) +
  \Bigl(\nabla_{\x} f \Bigr)^T_{\x_0}(\x-\x_0) +
  (\x-\x_0)^T \Bigl(\nabla\nabla^T f\Bigr)_{\x_0} (\x-\x_0),
\\]

we can conclude that

\\[
  (\x-\x_0)^T \Bigl(\nabla\nabla^T f\Bigr)_{\x_0} (\x-\x_0) \ge 0
\\]

no matter what \\(\x\\) and \\(\x_0\\) are. 

In other words the Hessian of \\(f\\) at any point \\(\x_0\\),
\\[
  \Bigl(\nabla\nabla^T f\Bigr)_{\x_0}
\\]
must be positive-definite (or all eigenvalues are \\(\ge 0\\))
for \\(f\\) to be convex.

**Exercise** Let \\(\w=(w_1,w_2)\\) be a vector with two
coordinates.  Recall that the length of \\(\w\\) is
\\(||\w||= \sqrt{w_1^2+w_2^2}\\).

 	1. Compute the Hessians of the function \\( f(\w)=||\w||^2 \\) and the function \\( h(\w)= ||\w||\\).
    2. Which of the Hessians are positive definite? Which functions are convex?
  
Again, the Hessian characterization
only applies to those convex functions that happen to have a second
derivative. In general, convex functions need not even have a first
derivative leave alone the second---absence of derivatives
must not be construed as evidence that the function is not convex.


**Level sets:** If \\(f\\) is a convex function of \\(\x\\), then
all level sets of \\(\x\\), \ie for all \\(L\\), the sets

\\[
f_L=  \bigl\{\x \in \reals^d : f(\x) \le L \bigr\}
\\]

are convex _sets_. The converse need not generally hold, but this
is often a quick test that helps you rule out functions that are
not convex.



