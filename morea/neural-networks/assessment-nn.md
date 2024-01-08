---
title: "Assessment"
published: true
morea_id: assessment-nn
morea_summary: "Neural Networks"
morea_outcomes_assessed:
 # - outcome-CHANGE-ME
morea_type: assessment
morea_start_date: "2021-07-16T09:00"
morea_labels:
---
# Problems

* Use a feedforward architecture to train and predict on the CIFAR-10
  and Fashion-MNIST dataset. Here, you may need to use dropout to
  train better and reduce overfitting---find out how to implement this
  technique. We discussed dropout very briefly in class, so you may want
  to look up Dropout techniques online for more background.

* Project the MNIST dataset into as small a manifold as
  possible. Meaning, you should come up with two transformations (we
  will call them encoder and decoder). The encoder should represent
  each \(28\times 28\) test image into a small vector (you can have
  this vector have less than 10 coordinates, but it is ok if your
  output is slightly larger too), but that doesn't lose
  information---namely the decoder can reconstruct the original image
  (with negligible loss) from the small vector output from the
  encoder.
