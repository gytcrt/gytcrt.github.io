---
layout: post
title: My definition of Bayesian statistics
tags: [Blog]
---

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;In my writing class, I tried to explain what Bayesian statistics is to my professor and mentor, but even the [Wikipedia page of Bayesian statistics](https://en.wikipedia.org/wiki/Bayesian_statistics){:target="_blank"} is full of jargons for people out of my field. It reminds me of the first time I knew about Bayesian statistics from a senior student at Duke, I barely understood nothing he talked about Bayesian during the conversation. Therefore, I attempted to define Bayesian statistics in a more plain way. I've revised the definition for several times. It's not perfect yet, but I'd like to post it here. I'm willing to hear some advice on it:)


<center> <h3>Bayesian statistics </h3> </center>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Bayesian statistics is named after Thomas Bayes, a British statistician, who first formulated a specific case of Bayesian statistics. In general, statistics is the study of underlying properties of observed data from a statistical population. Bayesian statistics is one of the predominant subfields of statistics now. The fundamental idea of Bayesian statistics is that we change our estimation of the statistical population based on Bayes’ theorem [1]. Bayes’ theorem mathematically illustrates the probability of an event given some new data, and demonstrates how the estimation of the event should be updated after observing the new data.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Compared with classical Frequentist statistics, Bayesian statistics is relatively new, and gradually became popular after the late 20th century. If a random variable X has a probability distribution, and the probability distribution is a mathematical formula which can be represented by the symbol [2], then Bayesian statistics treats  as a random variable. Treating  as a random variable makes the estimation of  able to be estimated and changed based on data which is a new evidence of the probability distribution. On the contrary, Frequentist statistics considers  a fixed value. Bayesian statistics usually has prior estimation of  before observing any data, but Frequentist estimates  only based on observed data. For example, a Bayesian doctor would have some prior judgment before they know a patient’s symptom, because the Bayesian doctor has already read the patient’s previous medical record. However, a Frequentist doctor would only make judgment after knowing the patient’s symptom.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Bayesian statistics has developed its original version of statistical inference, parameter estimation, hypothesis testing and interval estimation, which are all statistical approaches to study the underlying properties of observed data. Bayesian statistics has become more influential since in recent decades more complicated statistical models can be easily introduced and estimated [3] by Bayesian statistics via Markov chain Monte Carlo (MCMC) algorithms and efficient modern computer. For instance, Metroplis-Hastings and Gibbs sampling are the most widely used MCMC algorithms to compute Bayesian statistical models.

### Reference
[1] Hoff, Peter D. A first course in Bayesian statistical methods. Springer Science & Business Media, 2009.<br />
[2] Hogg, Robert V., Joseph W. McKean, and Allen T. Craig. "introduction to mathematical statistics SIXTH EDITION." (2005).<br />
[3] Gelman, Andrew, et al. Bayesian data analysis. Vol. 2. Boca Raton, FL, USA: Chapman & Hall/CRC, 2014.
