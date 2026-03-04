# Customer Segmentation Executive Overview

## 1. Introduction

The objective of this work is to segment customers based on their purchasing behavior and use these segments to grow revenue, improve retention, and focus marketing investments. Using the Online Retail transaction data, we created behaviorally coherent customer segments and defined concrete playbooks, scenario-based impact estimates, and KPIs for ongoing monitoring.

---

## 2. Methodology

- **Data**: Historical transaction data including invoice, date, quantity, price, customer ID, and country.
- **Behavioral features**:
  - **Recency**: Days since last purchase.
  - **Frequency**: Number of invoices per customer.
  - **Monetary**: Total spend over the analysis window.
  - **Additional features**: Average order value, average basket size, number of unique products purchased.
- **Segmentation approach**:
  - Customers are clustered into a small number of groups using these behavioral features.
  - Clusters are interpreted and labeled with business-friendly names.
- **Goal**: Move from generic, one-size-fits-all campaigns to targeted strategies that reflect how different customers actually behave.

---

## 3. Segment Definitions

### 3.1 Champions (High-Value Loyal)

- **Profile**: Very recent, very frequent purchasers with high cumulative spend. Often buy across multiple product categories and have large baskets.
- **Business role**: Small in number but drive a large share of total revenue.

### 3.2 Loyal Customers

- **Profile**: Regular, steady buyers with solid spend and predictable purchasing patterns.
- **Business role**: Main engine of stable, recurring revenue.

### 3.3 At-Risk (High Value)

- **Profile**: Historically high-value customers whose recency has significantly declined.
- **Business role**: Previously important revenue contributors now at risk of churn.

### 3.4 New & Promising

- **Profile**: Recent first-time or second-time buyers with encouraging early spend and engagement.
- **Business role**: Pipeline for future Loyal and Champion customers.

### 3.5 Need Attention / Occasional

- **Profile**: Low-frequency and/or low-spend customers, often promotion- or occasion-driven.
- **Business role**: Large in count but smaller share of revenue; pool for selective uplift.

### 3.6 Potential Loyalists

- **Profile**: Moderate recency, frequency, and spend with consistent engagement.
- **Business role**: Candidates to be upgraded efficiently into Loyal or Champions.

---

## 4. Segment Playbooks

### 4.1 Champions (High-Value Loyal)

- **Who they are**
  - Recent, frequent purchasers with very high total spend.
  - Multi-category, high-engagement customers.
- **Why they matter**
  - Core revenue drivers; losing them has immediate impact.
  - Strong candidates for advocacy and referrals.
- **What to do**
  - **Campaigns**: VIP programs, early access, exclusive previews, surprise-and-delight offers.
  - **Messaging**: “Thank you / VIP appreciation”, recognition of their loyalty, premium positioning.
  - **Cadence**: 1–2 high-value touches per week plus behavior-triggered journeys.
  - **KPIs**:
    - Champions retention rate.
    - Orders per customer and average order value (AOV).
    - Participation in VIP/referral programs.
    - Revenue share from Champions over time.

---

### 4.2 Loyal Customers

- **Who they are**
  - Regular buyers with strong but not extreme spend.
  - Main contributor to predictable, recurring revenue.
- **Why they matter**
  - Large and stable revenue base.
  - Pipeline for future Champions.
- **What to do**
  - **Campaigns**: Points-based loyalty, bundles, cross-sell into adjacent categories.
  - **Messaging**: Personalized recommendations, “complete the look” offers, progress toward VIP status.
  - **Cadence**: 1–3 touches per week plus behavioral triggers.
  - **KPIs**:
    - Upgrade rate from Loyal → Champions.
    - Repeat purchase rate and time between orders.
    - Loyalty program participation.
    - Revenue per Loyal customer per month/quarter.

---

### 4.3 At-Risk (High Value)

- **Who they are**
  - Previously high-spend customers who have not purchased for a long time.
  - Often former Champions or Loyal now drifting away.
- **Why they matter**
  - Represent expensive churn if lost.
  - Offer fast, high-ROI opportunities through win-back campaigns.
- **What to do**
  - **Campaigns**: Win-back sequences, targeted discounts on historically purchased categories, “we miss you” outreach.
  - **Messaging**: Remind them of previous favorites, highlight new products and improved experiences, emphasize ease of returning.
  - **Cadence**: 3–5 contacts over 30–45 days, then downshift if unresponsive.
  - **KPIs**:
    - Churn rate in the At-Risk segment.
    - Win-back / reactivation rate.
    - Revenue recovered from reactivated customers.
    - Time-to-reactivation after first win-back contact.

---

### 4.4 New & Promising

- **Who they are**
  - Very recent customers with one or a few purchases and above-average early spend.
  - Early-stage customers with strong potential.
- **Why they matter**
  - Main source of future Loyal and Champions.
  - Early experience largely determines lifetime value.
- **What to do**
  - **Campaigns**: Onboarding journeys, educational content, second and third-purchase incentives.
  - **Messaging**: Welcome and orientation, how to get value from products, social proof and bestsellers.
  - **Cadence**: High-touch for the first 30–60 days, then align with Loyal cadence.
  - **KPIs**:
    - Second-purchase rate and time to second purchase.
    - Conversion rate into Loyal / Champions.
    - Early-cohort LTV vs. historical cohorts.
    - Engagement with onboarding communications.

---

### 4.5 Need Attention / Occasional

- **Who they are**
  - Infrequent or low-spend customers, often promotion-led or occasion-driven.
  - Large segment in count but relatively small revenue contribution.
- **Why they matter**
  - Large pool where small improvements can generate meaningful revenue.
  - However, ROI must be carefully managed to avoid over-investment.
- **What to do**
  - **Campaigns**: Broad re-engagement, seasonal promotions, low-cost newsletters and content.
  - **Messaging**: Simple, clear value propositions and discounts; highlight relevance and convenience.
  - **Cadence**: Weekly or bi-weekly, with intensity increased around peak seasons.
  - **KPIs**:
    - Re-activation rate.
    - Upgrade rate into New & Promising / Potential Loyalists.
    - Revenue per contacted customer vs. cost of incentives.
    - Unsubscribe or complaint rates.

---

### 4.6 Potential Loyalists

- **Who they are**
  - Customers with moderate recency/frequency/spend and consistent engagement.
  - Positioned between Need Attention and Loyal.
- **Why they matter**
  - High upside for value growth with manageable effort.
  - More efficient to upgrade than acquiring brand-new high-value customers.
- **What to do**
  - **Campaigns**: Threshold-based offers (“spend X more to reach VIP”), cross-sell and upsell recommendations, bundles.
  - **Messaging**: Emphasize progression (“you’re close to [tier]”), curated recommendations, benefits of moving up.
  - **Cadence**: Similar to Loyal but with focus on value-building opportunities.
  - **KPIs**:
    - Upgrade rate to Loyal / Champions.
    - Change in AOV and purchase frequency post-campaign.
    - Engagement with recommendation and threshold campaigns.

---

## 5. KPIs and Monitoring Framework

### 5.1 Core Segment-Level KPIs

- **Size & composition**
  - Number of customers in each segment.
  - % of total customers and % of total revenue by segment.
- **Value & engagement**
  - ARPU (average revenue per user) by segment.
  - Average order value and orders per customer.
  - Engagement metrics: open/click rates, sessions, campaign participation.
- **Risk & opportunity**
  - Churn or inactivity rate (no purchase over a defined period).
  - Upgrade/downgrade flows between segments (e.g., New → Loyal, Loyal → At-Risk).
  - Approximate CLV by segment (where feasible).

### 5.2 Monitoring Cadence

- **Monthly**
  - Segment sizes and revenue share.
  - ARPU and AOV per segment.
  - Net movement between key segments (New → Loyal, Loyal → At-Risk).
- **Quarterly**
  - Churn rates by segment.
  - CLV by segment and changes over time.
  - Cohort-level retention curves by initial segment.

### 5.3 Example Alert Thresholds

- At-Risk churn rate increases by >5 percentage points vs. previous quarter.
- Number of Champions decreases by >10% quarter-on-quarter.
- > 50% of the base concentrated in Need Attention / Occasional.

