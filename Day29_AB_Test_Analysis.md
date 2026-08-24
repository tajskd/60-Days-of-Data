# Day 29 – Mock A/B Test: Analyzing Results

## Objective
To apply A/B testing concepts to a mock dataset and interpret the results with a business lens.

## Scenario
Superstore wants to test if offering a 10% discount increases average sales per customer.

## Test Design
- **Control Group (A):** Standard pricing (53 users)
- **Treatment Group (B):** 10% discount (47 users)
- **Metric:** Average Sales per User
- **Duration:** 2 weeks

## Results

| Group | Average Sales | Standard Deviation | Count |
| :--- | :--- | :--- | :--- |
| Control | $101.75 | $18.30 | 53 |
| Treatment | $107.78 | $20.02 | 47 |

**Lift:** 5.93% ($6.03 per order)

## Analysis & Recommendation

### 1. Difference in Average Sales
The Treatment group averaged **$107.78**, which is **$6.03 higher** than the Control group ($101.75).

### 2. Percentage Lift
The treatment delivered a **5.93% increase** in average sales.

### 3. Recommendation
**Do not roll out immediately.** While the lift is positive, the sample size is small (only 100 total users). The result could be due to random chance. I would run a statistical t-test to check for significance (p-value). If p < 0.05, I would recommend a full rollout. If p > 0.05, I would run the test longer to increase sample size.

## Key Takeaway
A positive lift is encouraging, but **statistical significance** is the gatekeeper. Without it, you risk making decisions based on random noise. A/B testing is about evidence, not just numbers.

## Next Steps
- Day 30: Review of Statistical Significance & Sample Size
