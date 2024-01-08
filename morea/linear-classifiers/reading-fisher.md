---
title: "Fisher Discriminant"
published: true
morea_id: reading-fisher
morea_summary: "Lin Reg with categorical labels interpreted as numbers"
morea_url: 
morea_type: reading
morea_labels:
---

A "hack" to usign linear regression for classification is to interpret
the categorical labels (say $\pm 1$) as numbers, and using them as the
target in a regular linear regression. This is not a bad idea at all,
and coincides with what is known as the Fisher Discriminant. Doing so
projects the data into a one-dimensional space, followed by a
threshold classifier in the one-dimensional space. The one-dimensional
space obtained turns out to be optimized to control the intra-class
spread while keeping the distance between centroids as far as
possible. Read more about this [here](https://uhm-descartes.github.io/ee445/morea/linear-classifiers/fisher.pdf)
