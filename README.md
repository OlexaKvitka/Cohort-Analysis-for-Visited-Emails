# Cohort-Analysis-for-Visited-Emails

**TASK:** Perform a cohort analysis using Tableau to determine the percentage of followers who open emails after creating an account. To get a dataset for analysis, was used data from Big Query.

## Task completion stages:

1.Write a request that will count accounts and their return in clicks on emails

SELECT
a.id account_id,
s.date AS account_creat_date,
DATE_ADD(s.date, INTERVAL ev.visit_date day) AS visit_date
FROM
`DA.account` a
JOIN
`DA.account_session` acs
ON
a.id = acs.account_id
JOIN
`DA.session` s
ON
s.ga_session_id = acs.ga_session_id
LEFT JOIN
`DA.email_visit` ev
ON
ev.id_account = a.id

2.Based on this dataset, create a cohort analysis in Tableau. On the X axis, display the number of weeks that have passed since the creation of the account in the system, and on the Y axis –, cohorts formed by the weeks of creation of the accounts.
 It is also necessary to show the percentage of accounts created in a specific week that open letters during a certain period of their existence in the system.

## Deliverables  
- Interactive Tableau Dashboard: https://public.tableau.com/app/profile/olexandra.kvasnevska/viz/CustomerRetentionCohortAnalysis_17704900692100/Dashboard1

## Tableau Public Dashboard Preview:
![Tableau Dashboard Performance](https://github.com/OlexaKvitka/Cohort-Analysis-for-Visited-Emails/blob/main/Customer%20Retention%20Cohort%20Analysis.PNG)

## Conclusions and recommendations:

Analysis of 46,154 accounts across 13 cohorts reveals critical retention challenges. Average retention of 7.69% indicates significant user disengagement, with the most dramatic drop-off occurring in the first week post-signup. 

 **KEY FINDINGS:**
 **1.The first week indicates the highest Churn Rate:**
 
-Week 0 engagement: 51.19% (initial open rate)
-Week 1 retention: 49.25%
-Week 3 retention: 26.98%
-Week 5 retention: 0.49%
**Insight:** The company experiences a 65% loss of engaged users within the first two weeks. By Week 5, retention approaches zero, indicating almost complete user abandonment.


**2. Inconsistent Cohort Performance**
The "Retention by Cohort" chart shows significant variance between cohorts:

- Best performing cohort (Week 50 index): maintains higher engagement through Week 2.
- Worst performing cohorts: sharp decline after Week 0.
Most cohorts converge to near-zero retention by Week 4-5.
**Insight:** Timing of account creation impacts retention, suggesting external factors (seasonality, marketing campaigns, product changes) influence user behavior.

**3. Cohort Size Variability**

-Largest cohort: 23,482 accounts (Week of Account Created: first bar)
- Subsequent cohorts: 5,000-7,000 accounts
- Average cohort size: 2,150 accounts
**Insight:** One anomalously large cohort skews the average. This could indicate a major marketing campaign, product launch or data collection issue.

**4. The "Never Opened" Segment**

The heatmap shows a "Never Opened" column, representing users who created accounts but never engaged with emails.
**Insight:** A substantial portion of signups represent low-intent users, indicating potential issues with signup friction, value proposition clarity, or acquisition channel quality.

*Based on these patterns, likely contributing factors can  include:*

-Weak onboarding experience: users don't understand product value within first week.
-Irrelevant email content: messages don't match user needs or expectations.
-Poor acquisition targeting: high volume of low-intent signups.
-Competitive pressure: users quickly switch to alternatives.
-Technical issues: deliverability problems or poor email rendering.

## RECOMMENDATIONS

**IMMEDIATE ACTIONS (Week 1-2 Implementation):**

Priority 1: Week 0-1 Intervention Campaign
+Trigger automated email sequence on days 2, 4, and 6 post-signup.
+Focus on education and quick wins rather than promotional content
+A/B test subject lines and content formats
Expected impact: 5-10 percentage point improvement in Week 1 retention

Priority 2: Segment-Specific Messaging
+Analyze the high-performing cohort (Week 50 index) to identify success factors
+Apply learnings to future campaigns
+Create distinct email tracks based on signup source or user behavior.


**SHORT-TERM IMPROVEMENTS (Month 1-2)**

1. Signup Quality Optimization
+Audit acquisition channels contributing to "Never Opened" segment
+Add expectation-setting during signup (frequency, content type)

2. Re-engagement Campaign for Week 2-4 Users
+Target users showing declining engagement
+Offer incentive or value-add content
+Test "we miss you" messaging vs. feature highlights

**LONG-TERM STRATEGIC INITIATIVES (Quarter 1-2)**
1. Comprehensive Onboarding Redesign
+Map user journey from signup through first value realization
+Identify and eliminate friction points
+Implement progressive onboarding (spread learning over time)

2. Predictive Churn Modeling
+Build ML model to identify at-risk users before Week 1 drop-off
+Personalize content based on churn probability

3. Email Preference Center
+Allow users to control frequency and content type
+Gather data on content preferences 

4. Cross-Channel Engagement Strategy
+Don't rely solely on email for retention
Create community or social engagement opportunities.

## POTENTIAL GAMECHANGER:  CRM Integration Opportunity:

Automated Early Warning System: Implement CRM workflows that automatically flag at-risk accounts based on disengagement signals:

-No email opens within 48 hours post-signup
-No product login within 3 days
-Zero click-through activity in first week
-This enables sales or customer success teams to proactively reach out with personalized onboarding assistance, potentially recovering at-risk accounts before they churn.

