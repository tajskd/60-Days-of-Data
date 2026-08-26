# Day 30 – Review of Statistical Significance & Sample Size

## Objective
To solidify understanding of statistical significance, sample size, and how to apply these concepts in real-world A/B testing.

## Key Concepts
- **Statistical Significance (p-value):** Probability the result is due to chance. Threshold: p < 0.05.
- **Sample Size:** Number of users needed to detect a meaningful effect. Larger effects need fewer users; smaller effects need more.
- **Power:** Probability of detecting a real effect. Standard: 80%.
- **Minimum Detectable Effect (MDE):** The smallest lift that matters to the business.

---

## Reflection: Designing a New Test

**Scenario:** Testing a new website layout expected to increase average order value by **5%**.

### 1. Minimum Sample Size
Because we are looking for a relatively large 5% increase in average order value (a large Minimum Detectable Effect), we need a smaller overall sample size than if we were trying to detect a tiny 1% change. However, we still need enough users in both groups to achieve at least 80% statistical power.

### 2. Test Duration
The duration depends directly on our daily traffic volume. We divide the required sample size by our average daily website visitors to calculate the required days, ensuring we run the test for at least 1 to 2 full weeks to capture full weekly shopping patterns (like weekend vs. weekday spending habits).

### 3. Action for p = 0.06
Since p = 0.06 is strictly above our 0.05 cutoff, the result is not statistically significant and we cannot safely roll out the change yet. Instead, I would extend the test duration to collect a larger sample size or evaluate whether the business risk allows a slightly higher threshold (like 90% confidence instead of 95%) before deciding.

---

## Key Takeaway
A/B testing is not just about running a test—it's about designing it correctly from the start. Understanding sample size and statistical significance ensures you make decisions based on evidence, not luck.

## Next Steps
- Day 31: Advanced SQL Practice (CTEs, Window Functions)
