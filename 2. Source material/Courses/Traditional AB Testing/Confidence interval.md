2025-02-23 21:32

Source: 

Status: #developing 

Tags: [[ab testing]] [[frequentist statistics]]

# [[3. Tags/confidence interval|confidence interval]]
- Scenario 1: Which estimate are we more confident about?
	- Dataset 1: X = {1, 3, 5} $\rightarrow$ $\mu$ = 3
	- Dataset 2: X = {2.9, 3.0, 3.1} $\rightarrow$ $\mu$ = 3
	- It's accepted that we're more confident in the case of Dataset 2, since with DTS 1, the mean could very much be 4, which is unlikely to DTS2 => we're more confident if the values are closer together.
- Scenario 2: 
	- DTS1: collect 10 samples $\rightarrow$ $\mu$ = 0.6
	- DTS2: collect 1000 samples $\rightarrow$ $\mu$ = 0.6
	- DTS2 is more reliable about the estimate since we hope random effect averages out with more samples
=> 2 things affect our confidence in an estimate: sample spread (variance) & sample size
## z-confidence interval & $\gamma$ confidence interval
- 95% confidence interval = $[\hat\mu - 1.96\frac{\hat\sigma}{\sqrt{N}},\hat\mu + 1.96\frac{\hat\sigma}{\sqrt{N}}]$
	- $\sigma$ increases => interval width increases => less confident
	- N increases => interval width decreases => more confident

# References
