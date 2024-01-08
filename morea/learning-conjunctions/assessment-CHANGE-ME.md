---
title: "Assessments"
published: true
morea_id: assessment-conjunctions
morea_summary: "Learning conjunctions"
morea_outcomes_assessed:
 # - outcome-conjunctions
morea_type: assessment
morea_start_date: "2021-07-16T09:00"
morea_labels:
---

## Warmup

\\( \newcommand{\sets}[1]{\{#1\}} \\)
\\( \newcommand{\ceil}[1]{\lceil#1\rceil} \\)

Suppose \\(X\\) is a random variable concentrated around 3, and
\\(P( |X-3| >.2) < .01\\). If you use 3 as an estimate of \\(X\\),
what is the accuracy and with what confidence? 

## Estimating the size of a set by sampling

If you can do this problem, you understand the primary thrust of the
module. If you are not comfortable with probability, you may need to
take my help for this.

Consider estimating the size of a finite set \\(S=\sets{1,2,\ldots, n}\\)
(we do not know \\(n\\) in advance). We have the ability to sample from
\\(S\\) uniformly at random (meaning the elements of \\(S\\) are distributed
uniformly, and different draws of elements from \\(S\\) are independent).

Here, you can estimate the size \\(n\\) to within a factor of \\(2\\) with
\\(\ceil{\log n}\\) draws with confidence \\(\ge 1-\frac 1n\\). The log is to
base 2. Can you figure out how? Implement any algorithm you come up
with to approximately estimate \\(n\\) (to some confidence), and simulate
(the sampling and your estimate). 

Show that you can estimate the size \\(n\\) to within a factor of \\(2\\) with
\\(\ceil{\log n}\\) draws with confidence \\(\ge 1-\frac 1n\\).

## Follow ups

In the previous example, suppose you desire the set size to within a
factor of \\(1+\epsilon\\) for some fixed \\(\epsilon>0\\) with confidence
\\(\ge 1-\frac 1n\\). How many samples would you need? 

## Estimator

Can you come up with at least two different estimators for the set size \\(n\\),
and analyze both? Come to me for any help you need for analysis.


