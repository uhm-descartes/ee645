---
title: "High Dimensional EM"
published: true
morea_id: assessment-high-dim
morea_summary: "How to read a paper"
morea_outcomes_assessed:
 # - outcome-CHANGE-ME
morea_type: assessment
morea_start_date: "2024-03-16T09:00"
morea_labels:
---
These questions are meant to test your understanding of the paper. The first set of questions are comprehension (and the ability to identify different parts of the paper). The questions are in three levels.

Recall that there are \\(k\\) cluster components, the data and the Gaussian mixture model \\(n\\) coordinate vectors
and there are \\(m\\) training samples. Each training samples comes from one of the Gaussian mixture components, but
the identity of the component is never revealed to the learner. The EM iteration procedure in each iteration first assigns splits each example probabilitistically over all cluster components, and uses likelihood given the soft assignment to update the cluster centers. 

* Level 0
1. What is the central result of the paper? 
2. How does the paper measure the distance between the means of the mixture components?
3. The paper describes concentration properties of high dimensional Gaussians that we covered in class as well. Which Lemmas are on this topic?
4. How many rounds of EM suffice for convergence? What happens at this point?
5. How many clusters does one initialize with? When are they pruned?

* Level 1
1. How small can \\(c\\) be to get at least polynomial in \\(n\\) confidence? Treat all \\(w_i = 1/k\\). Call this \\(c^*\\).
2. At separation \\(c^*\\) how many clusters do you start with, how many samples are required, how close are the mean parameters to the true values after the second EM iteration?
3. Simplify and explain the order of magnitude of each term in Lemma 3 when the distance between \\( \mu_i \\) and \\(\mu_j\\) is \\(c^*\\). 
4. In Section 5, para 2, second sentence, the paper says "Combining the last few lemmas tells us that if \\(c^2\sqrt{n} \gg \ln l\\) ... ". Prove this line.
5. After the first round of EM, the paper shows that center estimates of clusters with large enough mixing weights are already reasonably accurate. How close are they after the first iteration when the cluster separation is \\(c^*\sqrt{n}\\)?

* Level 2
1. Can you extend the results to the case where there are \\(k+1\\)
   clusters, but two clusters are separated by less than \\( n^{1/4}
   \\). But here, you do not care about errors in these two close
   clusters, so you treat them as one. More generally, what if we
   simply treat close clusters as one? This approach cannot
   indefinitely work, so what are the limits?
2. Can you think of new angles to this problem? Look into papers that
   cite this paper or are published later to get ideas.


