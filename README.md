# UK Online Retail Customer Segmentation

> *"Where should marketing spend their time and budget today?"*

## Project Overview

In the highly competitive e-commerce landscape, treating all customers identically is a fast track to wasted marketing spend and diminishing margins. This project translates raw, granular transactional data into a **strategic customer segmentation model** designed to uncover who is actually driving the business and where untapped value lies. 

Leveraging **RFM (Recency, Frequency, Monetary)** methodologies extended with behavioral clustering, this analysis partitions a customer base of ~4.3K users into distinct, actionable cohorts. The capstone of this project is an interactive **Power BI Dashboard** built to bridge the gap between data science and marketing operations, offering concrete levers for targeted retention and revenue growth.

## The Business Problem

The marketing team faced common retail challenges:

- **Budget dilution:** Blanketing the entire database with generic promotional emails resulting in low conversion and high unsubscribe rates.
- **Churn blindness:** High-value customers quietly churning without being intercepted.
- **Lost upside:** Mid-tier buyers stagnating when minor behavioral nudges could upgrade them into high-value loyalists.

**Objective:** Develop a robust, interpretable segmentation framework to allocate marketing budget efficiently, maximize Lifetime Value (LTV), and minimize the churn of top-tier customers.

---

## Methodology: Beyond Basic RFM

While traditional RFM is powerful, this project enriches it with advanced behavioral metrics to capture deeper purchasing nuances:

- **Source data:** Transactions from the Online Retail dataset, using the CSV export `Chen, D. (2015). Online Retail [Dataset]. UCI Machine Learning Repository. [https://doi.org/10.24432/C5BW33]`.
1. **Data Engineering & Cleaning:** Processed over 540K transaction records, handling returns, missing IDs, and temporal inconsistencies.
2. **Feature Engineering:** Calculated core RFM alongside extended features: *Average Order Value (AOV), Basket Size, and Product Diversity*.
3. **Unsupervised Machine Learning:** Applied **K-Means Clustering** on scaled behavioral features to group customers. Segment stability and business interpretability were prioritized to determine the optimal cohorts.

---

##  Key Findings: "Who is driving our business?"

The clustering algorithm surfaced four highly distinct customer segments, revealing a massive Pareto principle (80/20 rule) in action:


| Segment                          | % of Base | Revenue Share | Avg. Recency | Avg. Freq | AOV  |
| -------------------------------- | --------- | ------------- | ------------ | --------- | ---- |
| **Champions (High-Value Loyal)** | 22%       | **68%**       | 24 Days      | 11.8x     | £460 |
| **Loyal Customers**              | 50%       | 28%           | 59 Days      | 2.5x      | £518 |
| **At-Risk (High Value)**         | 16%       | 3%            | 258 Days     | 1.3x      | £285 |
| **Potential Loyalists**          | 12%       | 1%            | 135 Days     | 1.5x      | £113 |


### Strategic Insights & Marketing Playbook

**1. The Revenue Engine: Champions**

- **Insight:** Our Champions make up only 22% of the customer base but generate a staggering **68% of total revenue (£6.07M)**. 
- **Action:** Pivot budget toward retention. These customers do not need aggressive discounting. Offer VIP treatment, early access to new collections, and referral rewards to protect margins while driving organic acquisition.

**2. The Growth Opportunity: Loyal Customers**

- **Insight:** This segment represents half of the customer base. Interestingly, their **Average Order Value (£518)** is *higher* than the Champions, but they only purchase 2.5 times a year. 
- **Action:** *Frequency is the lever.* Implement triggered, personalized email campaigns to drive them to make just *one more purchase a year*. Even a fractional increase in frequency here yields massive absolute revenue gains.

**3. The Churn Intercept: At-Risk (High Value)**

- **Insight:** These 683 customers showed high historical value but haven't bought in over 8 months (258 days average recency).
- **Action:** Deploy aggressive win-back campaigns. A targeted, high-value discount is mathematically justified here to save the acquisition cost of replacing them.

---

## Technology Stack

Together, these decisions and checks ensure the segmentation is **analytically sound**, **transparent**, and **ready to be integrated** into CRM and decision‑making workflows.

- **Data Processing & ML:** Python (`pandas`, `numpy`, `scikit-learn`, `seaborn`)
- **Jupyter Notebooks:** For exploratory data analysis (EDA), feature engineering, and model training.
- **Business Intelligence:** Power BI (Interactive reporting, DAX, dynamic filtering).

## Repository Structure

```text
├── notebooks/
│   ├── Customer Clustering.ipynb             # Full ML pipeline: EDA, feature engineering, K-Means
│   └── README.md                             # Segment definitions and playbook details
├── dashboards/
│   └── Customer Segmentation Dashboard.pbix  # Power BI interactive dashboard
├── output/
│   └── customer_segments.csv                 # Final scored dataset for CRM ingestion
└── README.md                                 # Executive summary (You are here)
```

## Next Steps & Future Work

- **Propensity Modeling:** Train a supervised classification model to predict which "Potential Loyalists" are most likely to upgrade to "Champions."
- **Market Basket Analysis:** Implement Apriori or FP-Growth to understand *what* the Champions are buying to optimize cross-selling strategies for the Loyal segment.
- **Automated Pipeline:** Deploy the Python script as a recurring job to update segment assignments dynamically within the CRM on a weekly cadence.
