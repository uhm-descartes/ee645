---
title: "Linear methods: overview"
published: true
morea_id: lecture-overview
morea_type: experience
morea_summary: "Lecture from Jan 15"
morea_start_date: "2025-01-15"
morea_sort_order: 1
morea_labels:
---

# Overview of Linear Methods

Slides for the lecture are [here](./logreg.pdf). 

### Jan 15

There were bugs in the recording on Jan 15 so I apologize I don't
have the video recording, but we will sort them out by next class.

We went over

* **Basic visualization of linear regression:** each column (feature)
  is a vector, and we visualize the set of all linear combinations of
  the features (a hyper-plane). The target is generally not within the
  hyper-plane, but we project it into this plane. The square error is
  the distance of the target to the plane, the projection on the plane
  is the specific linear combination corresponding to the ordinary
  least squares solution. This visualization is different from the
  high school view of fitting a bunch of points.
  
* **Visualization of classification:** here we visualize the space of
  all possible examples. There are two general approaches.
  
	  1. In the **deterministic** view, the space is partitioned and
		  different regions are assigned to different labels.

	  2. In the **probabilisitic** view, each label corresponds to a different 
	    probability model over the example space (but the supports of these 
		probability models are allowed to overlap). So in the probabilistic 
		view, multiple classes could potentially generate the same example, 
		albeit with different probabilities.  

### Jan 22

We looked at **logistic regression** in the class, using the
probabilistic view of classification. Note that the approach in
class is different from what you may have seen in basic stat classes
and
[presented](https://docs.google.com/presentation/d/1PivvNMMgu9gnwzK8dfhZx9MT8UbOo9z1EhTqgYTpUU4/edit?usp=sharing)
by Loc and Saber.

But the two angles are completely equivalent and lead to the
same optimizations and solutions. The view we take here has a couple of advantages however. It allows
us to understand

* why logistic regression is a _maximum entropy_ approach
* _where_ the logit function appears from (in the basic stat approach, we just pulled that out of a hat)
 
 
The [handout](./logistic.pdf) and the theory assessement walk you through the 
details. They are also a good way to brush up/catch up on some of the probability basics before we head to other topics.


