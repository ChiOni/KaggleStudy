# Kullback-Leibler divergence

Also called relative entropy

= how one pdf is different from a second, reference pdf



- In contrast to variation of information

  <b> It is a ditribution-wise asymmetric measure</b>



In simple, KL-divergence of 0 = Two distributions in question are identical



#### Definition

For discrete pdf P & Q on the same probability space

- the KL-divergence of Q from P 

  = D(P||Q) =  -1  * sigma(P(x) * log(Q(x) / P(x)))

   				  = sigma (P(x)  *  log(P(x) / Q(x)))

  ​				   = Expectation of the logarithmic difference between P & Q



- More generally, if P & Q are probability measures over a set X

  and P is absolutely continuous with respect to Q, then

  = D(P||Q) = integral (  log(dP/dQ)  ~dP)

  = which is the entropy of Q relative to P



#### Interpretations

In the context of ML, D(P||Q) is called the <b>information gain</b> if Q is used instead of P

It is also called the relative entropy of P with respect to Q

(+)

In the language of <b>Bayesian inference,</b>

D(P||Q) is a measure of the information gained when one revises one's beliefs from

the <b>prior probability distribution Q  to the posterior probability distribution P</b>



-  It is the amount of information lost when Q is used to approximate P

- P typically represents the 'true' distribution of data,  while Q represents a model

  <b> In order to find Q that is closest to P, we can minimize KL divergence</b>





