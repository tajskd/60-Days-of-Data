# Day 28 – A/B Testing Fundamentals

## Objective
To understand the core concepts of A/B testing and apply them to a real-world business scenario.

## Key Concepts
- **A/B Test:** An experiment where two versions (A and B) are tested to see which performs better.
- **Control Group:** The group that sees the original version (A).
- **Treatment Group:** The group that sees the new version (B).
- **Statistical Significance:** The likelihood that the observed difference is real (usually p < 0.05).
- **Sample Size:** The number of users in each group—must be large enough to detect a meaningful difference.

## Scenario: 10% Discount Test
Superstore wants to test if offering a 10% discount increases total sales.

## My Design

### Customer Split
Randomly split online visitors 50/50 so 50% see prices with a 10% discount (Treatment) and 50% see regular prices (Control).

### Metric & Duration
Measure total sales revenue and average order value over 2 to 4 weeks to account for weekly shopping patterns.

### Action Plan
If the test shows a statistically significant increase in overall sales and profit, roll out the 10% discount to all customers.

## 3-Sentence Summary
To test the discount, I would randomly assign 50% of customers to receive a 10% discount (Treatment) and 50% to see standard pricing (Control). Over a two-week run time, I would measure total sales revenue and profit margin per user to assess overall impact. If the test yields a statistically significant increase in total revenue without ruining profit margins, I would recommend rolling out the discount broadly.

## Key Insight & Follow-up Question
**Question:** What do we do if sales go up, but overall profit goes down?

**Answer:** The test fails. A successful test must increase **profitable** sales. If profit drops, the discount is harming the business. The recommendation would be to not roll out the discount and to investigate which products are being discounted too heavily or have high costs that erase the profit margin.

## Key Takeaway
A/B testing removes guesswork from decision-making. It allows businesses to make data-driven changes with confidence, but the key metric must be **profitable growth**, not just revenue growth.

## Next Steps
- Day 29: Mock A/B Test – Analyzing Test Results
