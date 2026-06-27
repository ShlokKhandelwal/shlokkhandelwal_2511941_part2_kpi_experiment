# Part 2 - KPI Framework, Business Experiment Analysis & Decision Recommendation

## Business Context
A subscription-based digital product company launched a new onboarding and 
activation campaign. Users were split into Control (existing experience) and 
Treatment (new campaign). Leadership needs to decide whether to launch the 
treatment to all users based on experiment results.

## Business Problem Statement
- Decision to be made: Launch, reject, or conditionally launch the new campaign
- Who it impacts: Product, marketing, and customer success teams
- Metric that should improve: Paid conversion rate
- Risks to monitor: Refund rate, support ticket rate, revenue quality
- Evidence required: Statistically significant conversion improvement with 
  stable guardrail metrics

## Dataset Description
- File: campaign_experiment_data.xlsx
- Total users: 1408
- Control group: 693 users
- Treatment group: 715 users
- Columns: user_id, signup_date, experiment_group, region, device_type,
  traffic_source, plan_type, visited_landing_page, started_trial,
  completed_onboarding, converted_to_paid, revenue_30d, support_tickets_30d,
  refund_requested, days_to_convert, engagement_score

## Data Quality Checks
- Duplicate user_ids: 8 (flagged not deleted)
- Missing device_type: 18 (retained as is)
- Missing traffic_source: 24 (retained as is)
- Missing engagement_score: 14 (retained as is)
- Revenue outlier max: 8610.72 (retained)
- days_to_convert nulls: 1336 (only 72 users converted)

## North Star Metric Selected
Paid Conversion Rate - the proportion of users who converted to a paid 
subscription within 30 days. Selected because it directly measures 
revenue-generating behaviour and campaign success.

## KPI Tree Summary
- North Star: Paid Conversion Rate
- Driver 1 User Activation: Landing Page Visit Rate, Trial Start Rate
- Driver 2 Onboarding Quality: Onboarding Completion Rate, Days to Convert
- Driver 3 Revenue Quality: Avg Revenue Per User, Engagement Score
- Guardrail Metrics: Refund Rate, Support Ticket Rate, Revenue Quality

## Experiment Analysis Approach
- Compared 11 metrics between Control and Treatment groups
- Calculated conversion rates, revenue, refund and support metrics
- Performed segment analysis by region for paid conversion rate
- Used z-test for proportions to test statistical significance

## Hypothesis Test Summary
- Test: One-tailed z-test for proportions
- H0: Treatment conversion rate is equal to or less than Control
- H1: Treatment conversion rate is greater than Control
- Significance level: 0.05
- Z-score: 3.25
- P-value: 0.00115
- Result: REJECT null hypothesis - Treatment significantly improves conversion

## Guardrail Metrics Considered
1. Refund Rate: Increased from 0% to 0.42% - new risk in treatment
2. Support Ticket Rate: Increased 69.62% - significant concern
3. Revenue Quality: Avg revenue per user up 4.11% - acceptable but small sample

## Final Recommendation
LAUNCH WITH CONDITIONS
- Investigate support ticket spike before full rollout
- Monitor refund rate in first 30 days
- Consider phased rollout starting with North region
- Set guardrail alerts during rollout

## Assumptions and Limitations
- Experiment duration unknown - novelty effect possible
- Small converter sample (72 users) limits revenue quality assessment
- 8 duplicate user IDs may affect counts marginally
- Missing values in device_type and traffic_source excluded from segment cuts

## Screenshots Included
- screenshots/summary_metrics.png - Control vs Treatment comparison table
- screenshots/hypothesis_test_output.png - Z-test calculation and result
- screenshots/kpi_tree_preview.png - KPI tree diagram