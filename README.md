## Customer Segmentation – Executive Summary

### Why segment customers?

Effective customer segmentation allows the business to:
- **Prioritize high-value customers** for retention and upsell.
- **Detect at‑risk but valuable customers** before they churn.
- **Tailor marketing and product decisions** to distinct behavioral groups instead of treating all customers the same.

This project uses the Online Retail transaction dataset to move from raw invoices to **actionable, business‑friendly customer segments**.

### How the segmentation was done (non‑technical)

1. **Start from transactions**  
   We used the full Online Retail dataset (invoices, products, quantities, prices, customers, dates, and country).

2. **Clean and prepare the data**  
   - Kept only rows with a valid `CustomerID` so each customer can be tracked over time.  
   - Removed cancelled/returned orders and non‑positive quantities/prices to focus on normal purchasing behavior.  
   - Calculated a **line value** for each transaction (`TotalPrice = Quantity × UnitPrice`).

3. **Build customer‑level metrics**  
   For each customer, we summarized purchase behavior into:
   - **Recency** – how long it has been since their last purchase.
   - **Frequency** – how often they buy (number of invoices).
   - **Monetary value** – how much revenue they generate.
   - Additional behavior, such as **average order value**, **basket size**, and **product diversity**.

4. **Group similar customers together**  
   We fed these metrics into a clustering algorithm so that customers with **similar patterns of spend, frequency, and recency** end up in the same segment.

5. **Profile and name segments**  
   Each cluster was translated into **plain‑English segment labels** (for example, “Champions” or “At‑Risk”) and described in terms that business stakeholders can act on.

### What segments exist and what they mean

Actual segment sizes and revenue contribution are computed in the notebook; conceptually, we obtain segments such as:

- **Champions (High‑Value Loyal)**  
  - Recent buyers with **very high frequency and spend**.  
  - Small share of customers but often the **largest share of revenue**.  
  - **Business meaning:** VIP core base that should receive the best treatment and most protection.

- **Loyal Customers**  
  - Buy **regularly** with solid spend, though not as extreme as Champions.  
  - Reliable repeat business; strong candidates for cross‑sell and loyalty programs.  
  - **Business meaning:** profitable middle of the customer base, where systematic loyalty efforts pay off.

- **At‑Risk (High Value)**  
  - Historically high spend, but **haven’t purchased for a long time**.  
  - High potential loss if they fully churn.  
  - **Business meaning:** key targets for win‑back campaigns, feedback, and tailored offers.

- **New & Promising**  
  - Recently acquired customers with **few purchases so far**, but good early spend.  
  - **Business meaning:** nurture group; onboarding and second‑purchase incentives can grow them into Loyal/Champions.

- **Need Attention / Occasional**  
  - Infrequent buyers or low spend; often long gaps between purchases.  
  - **Business meaning:** low‑engagement pool; targeted promotions can reactivate a portion, but ROI must be monitored.

- **Potential Loyalists** (optional, depending on data)  
  - Moderate recency/frequency/spend; between Occasional and Loyal.  
  - **Business meaning:** candidates for campaigns that nudge them towards higher engagement.

### High‑impact recommendations (with estimated impact)

Exact numbers depend on business economics, but this segmentation enables concrete scenarios such as:

- **Retain At‑Risk high‑value customers**  
  - If **10% of At‑Risk customers** can be reactivated (e.g., via personalized offers or surveys), the business can recover a meaningful fraction of their historical revenue.  
  - Example framing: *“Re‑engaging just 10% of At‑Risk customers could protect approximately X% of annual revenue from this group.”*

- **Grow New & Promising into Loyal/Champions**  
  - Design an onboarding and “second‑purchase” journey.  
  - If **5–10% of New & Promising customers** upgrade into Loyal/Champions, total customer lifetime value (CLV) can increase by several percentage points.

- **Protect and reward Champions and Loyal segments**  
  - Introduce **VIP treatment** (exclusive previews, higher‑touch service, unique bundles).  
  - Small relative increases in retention or spending within these segments can drive **disproportionate gains**, since they already represent a large share of revenue.

- **Optimize marketing spend on low‑value segments**  
  - For Need Attention / Occasional customers, test **lower‑cost or automated campaigns** and strict performance thresholds.  
  - This can **reduce wasted spend** while still allowing selective re‑engagement of those who respond.

These scenarios can be quantified by combining: current revenue by segment, segment sizes, and assumed uplift or retention rates (see notebook for the underlying metrics).

---

## Technical Appendix

### Data preparation decisions

- **Source data**  
  - Transactions from the Online Retail dataset, using the CSV export `Chen, D. (2015). Online Retail [Dataset]. UCI Machine Learning Repository. [https://doi.org/10.24432/C5BW33]`.

- **Customer identification**  
  - **Only rows with non‑null `CustomerID`** were kept, so each transaction can be attributed to an individual customer.  
  - This excludes anonymous purchases; any insights are therefore specific to identified customers.

- **Cancelled and returned orders**  
  - Invoices where `InvoiceNo` starts with `\"C\"` and rows with **negative quantities** or **non‑positive prices** were removed from the main analysis.  
  - Rationale: the goal is to model **normal purchasing behavior**, not operational corrections. Returns can be analyzed separately if needed.

- **Transaction value**  
  - A line‑level value `TotalPrice` was created as `Quantity × UnitPrice`.  
  - This is the basis for all **revenue and monetary metrics** at the customer level.

- **Time window and dates**  
  - `InvoiceDate` was parsed as a proper datetime.  
  - A **snapshot date** was defined as the **max invoice date + 1 day**; recency is measured in days from the last purchase to this snapshot.

### Modeling choices

- **Customer‑level features**  
  - Core RFM metrics:  
    - `Recency` – days since last purchase.  
    - `Frequency` – number of invoices.  
    - `Monetary` – total revenue.  
  - Additional behavioral features such as:  
    - `AvgOrderValue` – average revenue per invoice.  
    - `AvgBasketSize` – average quantity per invoice.  
    - `N_UniqueProducts` / product diversity – number of distinct products purchased.

- **Transformations and scaling**  
  - Many monetary and frequency variables are **right‑skewed**, so a **log(1 + x)** transformation was applied to Frequency, Monetary, and related features (but not Recency).  
  - All features were **standardized** using `StandardScaler` before clustering to prevent high‑variance variables from dominating.

- **Clustering algorithm**  
  - **K‑Means** was used as the primary clustering method due to its:  
    - Interpretability for business stakeholders (fixed number of segments).  
    - Good performance for RFM‑style numerical features.  
  - Candidate values of K in the range **2–10** were evaluated.

- **Choice of number of clusters (K)**  
  - The number of clusters was selected by combining:  
    - The **elbow method** on within‑cluster sum of squares (inertia).  
    - The **silhouette score**, which measures how well‑separated clusters are.  
    - **Business interpretability** – ensuring each segment has a clear story and sufficient size.  
  - A value of **K = 5** was chosen as a good balance between separation and readability of segments.

- **Dimensionality reduction for visualization**  
  - **PCA (2 components)** was fitted on the standardized features.  
  - The 2D PCA projection is used only for **visualizing cluster structure**, not for driving business decisions directly.

### Validation and robustness

- **Internal validation**  
  - Silhouette scores were computed for each candidate K to quantify **cluster separation**.  
  - The final K produced a **reasonably high silhouette score**, indicating meaningful separation.

- **Stability checks**  
  - K‑Means was run multiple times with **different random seeds** while keeping K fixed.  
  - While exact cluster labels can permute, the **distribution of cluster sizes and overall segment profiles** remained similar, indicating a stable structure.

- **Practicality checks**  
  - Each cluster was examined for:  
    - **Size** – avoid segments that are too small to be worthwhile.  
    - **Reachability** – ensure segments can be referenced in downstream systems via `CustomerID` and exported attributes.  
    - **Actionability** – confirm that realistic marketing or product actions can be defined for each segment.

- **Limitations**  
  - Customers without a `CustomerID` are not represented in the segmentation.  
  - All history is treated uniformly; more advanced versions could use **rolling windows or seasonality adjustments**.  
  - Profitability or margin is not modeled explicitly; all monetary metrics reflect revenue, not contribution margin.

Together, these decisions and checks ensure the segmentation is **analytically sound**, **transparent**, and **ready to be integrated** into CRM and decision‑making workflows.
