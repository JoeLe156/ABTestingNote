2025-01-01 23:24

Source: 
- https://www.udemy.com/course/bayesian-machine-learning-in-python-ab-testing/learn/lecture/21180562#learning-tools

Status: #developing 

Tags: [[bayesian statistics]]

# Bayes probability concepts
## Distributions
### Marginal distribution, Joint distribution, Conditional distribution
Given 2 random variables A & B, then we have:
- [[joint distribution]] p(A, B) => the most popular, since from this, we calculate everything else
- [[marginal distribution]] p(A), p(B)
$$
	p(A)=\sum_{B}^{}p(A,B)
$$
$$
p(B)=\sum_{A}^{}p(A,B)
$$
- [[conditional distribution]] p(A|B), p(B|A)

$$
p(A|B) = \frac{p(A,B)}{p(B)} = \frac{p(A,B)}{\sum_{A}^{}p(A,B)}
$$
$$
p(B|A) = \frac{p(A,B)}{p(A)} = \frac{p(A,B)}{\sum_{B}^{}p(A,B)}
$$
![[Pasted image 20250102001500.png]] _Relationship among the 3 distributions_

### Bayes' rule
[[Bayes' rule]] is the centerpiece of Bayesian statistic
$$
p(B|A) = \frac{p(A,B)}{p(A)} = \frac{p(A,B)}{\sum_{B}^{}p(A,B)} = \frac{p(A|B)*p(B)}{\sum_{B}^{}p(A|B)*p(B)}
$$
### [[Discrete random variables]] VS [[Continuous random variables]]
- p() is a probability density instead of a single value
- but the rules regarding probability calculation still hold, but replace sum() with integral()
$$
p(B)=\int{}^{}p(A,B) dA
$$
$$
p(B|A) = \frac{p(A|B)*p(B)}{\int_{}^{}p(A|B) dB*p(B)}
$$

### Independent variables
Methods to define random variables from a given problem#Practice 2 - Decide if 2 random variables are independent
Knowing one variable's value doesn't tell me anything about the other => [[independent variables]] 
$$
A \bot B \iff p(A, B) = p(A)*p(B)
$$
### Common related problems
[[Gambler fallacy]], [[Monty Hall problem]] 
### Statistics VS machine learning
- Statistics: we build a model and the params of it are learned from data. Just like what we did with [[Maximum Likelihood Estimation]]
- [[Machine learning]]: 3 categories of ML

| Header                 | Header                                             | Techniques                                                   |
| ---------------------- | -------------------------------------------------- | ------------------------------------------------------------ |
| Supervised learning    | We have a target                                   | Classification (Discrete), Regression (Continuous)           |
| Unsupervised learning  | We don't have a target                             | Clustering (Discrete), Dimensionality Reduction (Continuous) |
| Reinforcement learning | We have a reward signal (a conversion is a reward) |                                                              |
# Time to practice
## Problem 1
Given the number of users that finished buying from your site in the table below

|             | Mexico | US  | Canada |
| ----------- | ------ | --- | ------ |
| Buy = True  | 10     | 50  | 20     |
| Buy = False | 200    | 500 | 300    |
Now, find the probability of buying given the country <=> Find p (buy | country)
#### Solution
1. Define random variables in the problem
	- Origin country of the visitor: Country
	- Buy event: Buy
2. Calculate probability
	- [[marginal distribution]]
		- p (Country)
			- p (Country = MX) = 210/(210+550+320) = 0.19
			- p (Country = US) = 550/(210+550+320) = 0.51
			- p (Country = CA) = 320/(210+550+320) = 0.3
	- [[joint distribution]]
		- p (Buy, Country)
			- p (Buy = True, Country = MX) = 10/1080 = 0.0093
			- p (Buy = True, Country = US) = 50/1080 = 0.046
			- p (Buy = True, Country = CA) = 0.019
			- p (Buy = False, Country = MX) = 0.185
			- p (Buy = False, Country = US) = 0.46
			- p (Buy = False, Country = CA) = 0.28
	- [[conditional distribution]]
		- p (Buy | Country)
			- p (Buy = True | Country = MX) = 0.0093/0.19 = 0.05
			- p (Buy = True | Country = US) = 0.09
			- p (Buy = True | Country = CA) = 0.07
			- p (Buy = False | Country = MX) = 0.97
			- p (Buy = False | Country = US) = 0.91
			- p (Buy = False | Country = CA) = 0.93
3. Alternate calculation
	- Utilize the independent variable concept, suppose that knowing if a user buys or not buy doesn't tell me which country they come from => Buy is independent of Country => In fact, this is only true if buy rate is the same for every country
	- $$ p(Buy, Country) = p(Buy) * p(Country) $$
	- $$ p (Buy | Country) = \frac{p(Buy, Country)}{p(Country)} = p(Buy) $$

# References
