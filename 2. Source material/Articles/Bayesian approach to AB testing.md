2024-12-26 00:19

Source: 
- https://www.mida.so/blog/frequentist-vs-bayesian-in-ab-testing
- https://www.invespcro.com/blog/bayesian-vs-frequentist-ab-testing-which-testing-method-is-better/

Status: #developing

Tags: [[bayesian statistics]] [[ab testing]] 

# Bayesian approach to AB testing

The Bayesian approach, in contrast to the frequentist approach, is a theory of probability that incorporates prior beliefs or knowledge about an event or experiment. It updates these prior beliefs using observed evidence to create a posterior probability distribution.

In a coin-toss experiment, the Bayesian approach considers not only the observed outcomes but also any prior information or beliefs we may have about the coin. Suppose we have a prior belief that the coin may not be fair, and we assign a certain probability distribution to the possible bias of the coin.

As we conduct the coin tosses and observe the outcomes, our prior beliefs are updated to form the posterior probability distribution. The observed data is used to revise our initial beliefs about the coin's bias. This updating process follows Bayes' theorem, which involves multiplying the prior probability by the likelihood of the observed data given that prior, and then normalizing to obtain the posterior probability distribution.

The Bayesian approach allows for the incorporation of subjective prior information and enables us to update our beliefs based on new evidence. It provides a framework to quantify uncertainty and make decisions incorporating both prior knowledge and observed data. Unlike the frequentist approach, which treats probability as the long-term frequency of an event, the Bayesian approach treats probability as a measure of subjective belief.

![Law of large numbers - Wikipedia](https://cdn.prod.website-files.com/64fddd2973684cc4d9ae2722/65366c4cbbf53a7dca254e0e_1200px-Lawoflargenumbers.svg.webp)

‍

As you continue to toss the coin more, you keep updating your belief based on the observed results. After many more tosses, the Bayesian and Frequentist approaches would likely converge to similar conclusions which is 50% in a coin tossed experiment.

# References
