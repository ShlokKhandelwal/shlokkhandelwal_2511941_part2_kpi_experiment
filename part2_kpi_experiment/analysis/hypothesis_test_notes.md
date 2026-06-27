# Hypothesis Test Notes

## Business Context
The company launched a new onboarding and activation campaign (Treatment) against 
the existing experience (Control). We need to determine if the Treatment 
significantly improves paid conversion rate.

## Metric Being Tested
Paid Conversion Rate - proportion of users who converted to paid subscription

## Hypotheses
- Null Hypothesis (H0): The paid conversion rate of Treatment is equal to or less 
  than Control. There is no meaningful improvement.
- Alternate Hypothesis (H1): The paid conversion rate of Treatment is greater than 
  Control. The campaign improves conversion.

## Test Type
- One-tailed z-test for proportions
- Direction: right-tailed (testing if Treatment > Control)
- Significance level: 0.05 (5%)

## Reason for Choosing This Metric
Paid Conversion Rate is the North Star metric because it directly measures whether 
users move from free to paid, which drives business revenue. It is the clearest 
signal of campaign success.

## Test Inputs
- Control users: 693
- Treatment users: 715
- Control converted: 22
- Treatment converted: 50
- Control conversion rate: 3.17%
- Treatment conversion rate: 6.99%

## Test Calculations
- Pooled proportion: 0.0511
- Standard error: 0.0117
- Z-score: 3.25
- P-value (one-tail): 0.000573
- P-value (two-tail): 0.001146

## Decision Rule
Reject H0 if p-value < 0.05

## Result
P-value of 0.00115 is far below 0.05. We REJECT the null hypothesis.

## Business Interpretation
The treatment group shows a statistically significant improvement in paid 
conversion rate. The 120% lift from 3.17% to 6.99% is not due to random chance. 
The z-score of 3.25 is well above the critical value of 1.645 for a one-tailed 
test at 5% significance.

## Interpretation Logic
Even with a two-tailed test the p-value of 0.00115 is far below 0.05, confirming 
the result is robust. The treatment effect is strong and statistically reliable.

## Limitations
- Test duration and sample size should be verified for business adequacy
- Novelty effect possible - users may behave differently over longer periods
- Guardrail metrics must be checked before final launch decision