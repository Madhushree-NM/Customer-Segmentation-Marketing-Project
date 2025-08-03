# Customer Segmentation for Personalized Marketing

## Project Overview

This project focuses on leveraging transactional data to identify distinct customer segments based on their purchasing behavior. By understanding these segments, businesses can develop and implement highly personalized marketing strategies, ultimately leading to increased customer engagement, retention, and overall revenue.

## Problem Statement

A common challenge for businesses is the inefficiency of generic, one-size-fits-all marketing campaigns. These campaigns often result in low customer engagement and suboptimal conversion rates. The objective of this project is to address this by grouping customers into meaningful segments, allowing for targeted and more effective marketing interventions.

## Dataset

The analysis uses the **Online Retail II Dataset**, a comprehensive transactional dataset from a UK-based online retail store. It covers purchases made between December 2009 and December 2011.

* **Source:** [https://www.kaggle.com/datasets/mashlyn/online-retail-ii-uci](https://www.kaggle.com/datasets/mashlyn/online-retail-ii-uci)

## Goal

The primary goal of this project is to:
* Identify distinct customer groups based on their Recency, Frequency, and Monetary (RFM) values.
* Characterize each customer segment with clear behavioral profiles.
* Provide actionable, data-driven recommendations for personalized marketing strategies tailored to each segment.

## Methodology

The project followed a structured data analysis pipeline:

1.  **Data Loading & Initial Inspection:** Loaded the dataset and performed initial checks on its structure, data types, and missing values.
2.  **Data Cleaning & Preprocessing:**
    * Handled missing `Customer ID` values (critical for customer-level analysis).
    * Converted `InvoiceDate` to datetime objects and `Customer ID` to integer type.
    * Removed duplicate transaction entries.
    * Filtered out invalid `Quantity` (e.g., negative for returns) and `Price` (e.g., zero or negative) values.
3.  **RFM Feature Engineering:** Calculated three key metrics for each customer:
    * **Recency (R):** How recently a customer made a purchase (days since last purchase).
    * **Frequency (F):** How often a customer purchases (total number of unique invoices).
    * **Monetary (M):** How much money a customer spends (total spending).
4.  **Exploratory Data Analysis (EDA) on RFM:** Visualized the distributions of R, F, and M to understand their spread and identify skewness.
5.  **Data Transformation & Scaling:** Applied log transformation to reduce skewness and `StandardScaler` to bring all RFM features to a comparable scale, optimizing them for clustering.
6.  **Customer Segmentation (K-Means Clustering):**
    * Used the Elbow Method and Silhouette Score to determine the optimal number of clusters (`K=3` was chosen based on your analysis).
    * Applied the K-Means algorithm to segment the customers.
7.  **Cluster Profiling & Interpretation:** Calculated and visualized the average RFM values for each cluster to understand their unique characteristics and assigned descriptive names to each segment.
8.  **Marketing Strategy Formulation:** Developed specific, actionable marketing recommendations tailored to the behavior and needs of each identified customer segment.

## Key Findings: Customer Segments

The analysis identified **3 distinct customer segments** based on their shopping behavior:

### 1. **Champions (Cluster 1)**
* **Number of Customers:** 1301
* **Avg Recency:** 27 days (Very Low)
* **Avg Frequency:** 18.1 purchases (Very High)
* **Avg Monetary:** $10,042.72 (Extremely High)
* **Description:** These are the most valuable, loyal, and recently active customers. They represent the core of the business's revenue and should be prioritized for retention and engagement.

### 2. **Potential Loyalists (Cluster 2)**
* **Number of Customers:** 2346
* **Avg Recency:** 141 days (Medium)
* **Avg Frequency:** 4.4 purchases (Medium)
* **Avg Monetary:** $1,511.56 (Medium)
* **Description:** This segment comprises regular customers who show good potential for growth. They purchase periodically and contribute steadily but could be encouraged to increase their frequency and spending to become champions.

### 3. **At-Risk / Churned Customers (Cluster 0)**
* **Number of Customers:** 2231
* **Avg Recency:** 367 days (Very High)
* **Avg Frequency:** 1.4 purchases (Very Low)
* **Avg Monetary:** $342.05 (Very Low)
* **Description:** These customers are largely inactive, having not purchased in a long time. They may be at risk of churning or are already churned, often being one-time or very low-value buyers.

## Marketing Recommendations

Tailored marketing strategies for each segment:

### **Segment: Champions (Cluster 1)**
* **Goal:** Retention & Loyalty, Upsell/Cross-sell premium products.
* **Actions:**
    * Implement exclusive loyalty programs and tiered rewards.
    * Offer early access to new products or sales.
    * Provide personalized recommendations based on past purchases.
    * Send 'thank you' notes or small gifts to acknowledge their value.
    * Gather feedback through surveys to understand their evolving needs and preferences (e.g., NPS surveys).
    * Offer VIP customer service.

### **Segment: Potential Loyalists (Cluster 2)**
* **Goal:** Growth (increase frequency & Average Order Value), conversion to 'Champions'.
* **Actions:**
    * Send personalized product recommendations based on Browse history or similar customers.
    * Offer targeted promotions or discounts to encourage their next purchase.
    * Promote loyalty program benefits they could achieve with more purchases.
    * Send reminders about abandoned carts or wish lists to nudge conversions.
    * Highlight popular products or new arrivals relevant to their demonstrated interests.

### **Segment: At-Risk / Churned Customers (Cluster 0)**
* **Goal:** Re-activation (win-back), gather feedback.
* **Actions:**
    * Send win-back campaigns with aggressive discounts or special offers to entice a return.
    * Conduct 'we miss you' email campaigns with compelling reasons to revisit the brand.
    * Offer surveys to understand their reasons for inactivity (e.g., product issues, service issues, pricing concerns).
    * If re-engagement efforts prove unsuccessful, consider segmenting them further for very low-cost campaigns or simply archiving them from active marketing lists to optimize spend.
    * Avoid high-cost marketing to this group unless specific signs of re-engagement are observed.

## Tools & Libraries Used

* **Python**
* **Pandas** (for data manipulation and analysis)
* **NumPy** (for numerical operations)
* **Scikit-learn** (for clustering algorithms and data preprocessing)
* **Matplotlib** (for data visualization)
* **Seaborn** (for enhanced data visualization)

## How to Run This Project

1.  **Clone the Repository:**
    ```bash
    git clone [https://github.com/Madhushree-NM/Customer-Segmentation-Marketing-Project.git](https://github.com/Madhushree-NM/Customer-Segmentation-Marketing-Project.git)
    cd Customer-Segmentation-Marketing-Project
    ```
2.  **Download the Dataset:**
    Download the `online_retail_II.csv` file from [Kaggle](https://www.kaggle.com/datasets/mashlyn/online-retail-ii-uci) and place it in the project's root directory.
3.  **Install Dependencies:**
    ```bash
    pip install pandas numpy matplotlib seaborn scikit-learn
    ```
4.  **Open the Jupyter Notebook:**
    ```bash
    jupyter notebook Customer_Segmentation_Project.ipynb
    ```
5.  **Run Cells:** Execute all cells in the notebook sequentially.

## Future Work

This project lays a strong foundation for personalized marketing. Potential future extensions include:

* **A/B Testing Campaigns:** Design and execute A/B tests for the proposed marketing strategies to quantitatively measure their effectiveness and optimize them.
* **Product-based Segmentation:** Integrate product-level data to identify popular product categories within each segment and provide more precise product recommendations.
* **Churn Prediction:** Develop a predictive machine learning model to identify 'at-risk' customers earlier, enabling proactive intervention.
* **Interactive Dashboard:** Create a dynamic dashboard (e.g., using Tableau, Power BI, or Streamlit) to allow marketing teams to monitor segment performance and customer movement between segments in real-time.
* **Temporal Analysis:** Analyze how customer segments evolve over time and adapt strategies accordingly.
