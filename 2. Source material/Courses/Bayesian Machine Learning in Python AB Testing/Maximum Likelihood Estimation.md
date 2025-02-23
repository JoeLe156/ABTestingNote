2025-02-17 00:04

Source: 

Status: #mature 

Tags: [[bayesian statistics]]

# Concept overview
Process of data modelling: Data collected -> Fit data to a model (parameters)
Modern example: [[deep learning]] -> the learning path is essentially finding the best parameters to fit the data.
Maximum Likelihood Estimation (MLE) is a statistical method used to find the best parameters for a model based on the data collected. Here’s a simplified breakdown:

1. **Data Collection**: Imagine you have a bag of candy. You want to know how many of each type of candy are in the bag, but you can only take a few pieces out to see.
    
2. **Guessing**: Each time you take a piece of candy, you note what type it is. You might think there are more chocolates than gummies.
    
3. **Finding the Best Guess**: MLE helps you make a guess that is as close as possible to the actual number of each candy type in the bag. It does this by finding the parameters (numbers) that make your guess match the candy you pulled out.
    
4. **Maximizing**: The goal is to adjust your guess until you find the one that makes the most sense – like saying, “I believe there are 70 chocolates and 30 gummies because this helps explain the candies I pulled very well.”
    

In a more technical sense, MLE is about using the likelihood function, which measures how likely it is to get the observed data given certain parameters, and adjusting those parameters to maximize this likelihood. This process allows you to make the best statistical guess based on your collected data!

## MLE 1 - [[Bernoulli distribution]]
- Apply to [[Discrete random variables]], x is in {0, 1}
- [[PMF]] (Probability Mass Function):$$
p(x)= \theta^{x}(1-\theta)^{1-x}
$$
- $$ p(x=0) = 1 - \theta $$
- $$ p(x=1) = \theta $$
![[Pasted image 20250221003636.png]]
### [[Likelihood function]]
Likelihood function quantifies how likely the observed data is given a specific value of $\theta$ 
$$ L(\theta) = p(data|\theta) = \prod_{i}^{N}p(x_i|\theta) = \prod_{i}^{N} \theta^{x_i}(1-\theta)^{1-x_i} $$
- The likelihood function ( L(θ) ) is a function of ( θ ), while the data (aka x in this case, x receives the value of either 0 or 1 per each event) is fixed.
- In MLE, the goal is to find the value of ( θ ) that maximizes this likelihood function, meaning we want the parameter value that makes the observed data most probable.
- Try plug the real data of {x1 = 1, x2 = 0, x3 = 1} into this likelihood function:
	- $$ L(\theta) = \prod_{i}^{3} \theta^{x_i}(1-\theta)^{1-x_i} = \theta * (1-\theta) * \theta = \theta^{2}(1-\theta)$$
To find $\theta$ that maximize the L($\theta$), best practice is take the log of the likelihood before differentiating, since log() is monotonically increasing =>  $\theta$ that maximizes log (L) also maximizes L
$\theta$ that maximizes L <=> $\theta$ that maximize l = logL($\theta$) <=> $\frac{dl}{d\theta}$ = 0
Solve the above equation, we arrive at 
$$
\theta = \frac{1}{N} \sum_{i=1}^{N}x_i
$$
Which equals to total num of heads / total coin tosses.

### [[CTR]] as Bernoulli distribution
- CTR prediction can be considered the probability a user clicks on an ad/link, it's a binary event, they either click or not. Similarly, conversion rate as in the probability a user purchases an item is also a binary event.
- As such, these fall under the Bernoulli distribution
## MLE 2 - [[Normal Distribution]]
- Apply to [[Continuous random variables]] , e.g.: reals 
- Other real value distribution: [[T-distribution]], [[exponent distribution]], [[gamma distribution]] ...
- The process of MLE is the same for all distributions
- Normal distribution is ubiquitous in nature due to [[central limit theorem]]
![[Pasted image 20250222001234.png]]
### Likelihood function
- Collect the height of all people in a class: data = {x1, x2, ..., xn}
- Write down the likelihood function as Gaussian [[PDF]] (probability density function) since x is continuous
	- $$ L(\theta) = p(data|\theta) = \prod_{i}^{N}p(x_i|\theta) , where \space \theta= \left\{\mu,\sigma^2\right\} = \prod_{i}^{N} \frac{1}{\sqrt{2\pi\sigma^2}}e^{-\frac{1}{2}(\frac{x_i-\mu}{\sigma})^2} $$
	- ![[Pasted image 20250222004342.png]]
- Similar to the PMF, we take the log of L($\mu,\sigma^2$) before finding ($\mu,\sigma^2$) that makes $\frac{dl}{d\theta} = 0$
	-  $$ log(\mu,\sigma^2) = logL(\mu,\sigma^2) = log\prod_{i}^{N} \frac{1}{\sqrt{2\pi\sigma^2}}e^{-\frac{1}{2}(\frac{x_i-\mu}{\sigma})^2}=\sum_{i}^{N} log\frac{1}{\sqrt{2\pi\sigma^2}}e^{-\frac{1}{2}(\frac{x_i-\mu}{\sigma})^2}$$
	- $$ = \sum_{i}^{N} (log\frac{1}{\sqrt{2\pi\sigma^2}} + loge^{-\frac{1}{2}(\frac{x_i-\mu}{\sigma})^2})  = \sum_{i}^{N} - \frac{1}{2}log({2\pi\sigma^2}) - \frac{1}{2}(\frac{x_i-\mu}{\sigma})^2 = -\frac{N}{2}log(2\pi\sigma^2) - \frac{1}{2}\sum_{1}^{N}(\frac{x_i-\mu}{\sigma})^2$$
- Now, take partial derivative with respect to $\mu$ first
	- $$\frac{\partial{l}}{\partial\mu} = \sum_{1}^{N}(\frac{x_i-\mu}{\sigma})\frac{1}{\sigma} = 0$$
	- Solve the equation, we get the sample mean $$\mu = \frac{1}{N} \sum_{i=1}^{N}x_i$$
- Then, take the partial derivative to $\sigma^2$
	- $$log (u, v) = -\frac{N}{2}log(2\pi v) - \frac{1}{2v}\sum_{1}^{N}({x_i-\mu})^2 \; where\; v = \sigma^2$$
	- $$ \frac{\partial{l}}{\partial v} = -\frac{N}{2} \frac{1}{v} - (-1) \frac{1}{2v^2}\sum_{1}^{N}({x_i-\mu})^2 = 0$$
	- $$\Leftrightarrow v = \frac{1}{N}\sum_{1}^{N}({x_i-\mu})^2  $$
### Functions of random variables are random variables
- Ex: Z = X1 + X2
- Z receives the value of {0, 1, 2} => it's random
- Our MLE estimates are also random variables, take a look back at $\mu$ and $\sigma^2$ equation, they are represented as f(x1, x2, x3..., xn), and x1, x2..., xn are random variables, in fact, they are iid random variables.
- Since they are random variables, we can ask:
	- What is their distribution?
	- What is their expectation E($\hat\mu$) & E($\hat\sigma^2$)
		- E($\hat\mu$) = $\mu$
		- E($\hat\sigma^2$) = $\frac{N-1}{N}\sigma^2$
## [[CDF]] - Cumulative distribution function
- Discrete random variable $$F(x) = P(X <= x) = \sum_{k=-\infty}^{x} p(k) $$
- Continuous random variable $$ F(x) = P(X<=x) = \int_{-\infty}^{x}f(t)dt $$
## [[Normal distribution]] in real world
- Exam grades:
	- Max grade: 200
	- Probability of a student achieving <= 170? => Typical continuous [[CDF]] finding problem, let's say it's 95%
	- Max score of bottom 95% of the students? => Inverse CDF, also known as [[PPF]] (0.95) = 170
	- If the student height is 180cm, what is the probability that someone is taller than them? => Survival function ([[SF]]) = 1 - CDF
- Height:
	- Suppose $\mu$ = 170cm, $\sigma$ = 7cm
	- Someone says: I'm in the 95th percentile => $F^{-1}$ (95%, $\mu$ = 170, $\sigma$ = 7) = 181.5cm
	- Someone says: I'm 160 cm => percentile??? => F (160, $\mu$ = 170, $\sigma$ = 7) = 0.08 => 8th percentile
- Rating, Amount of time user spent on your site
- Gaussian/normal distribution may not be the real case here but it could be a fine approximation.
## Confidence interval
1. When doing MLE, we often end up with as single value. How confident are we in this estimate? Is it good or bad? 
2. Suppose we have the estimates of CTR A & CTR B, how can we be confident that A is better than B?
=> We use [[3. Tags/confidence interval]] to answer these questions.

# References
