# SuperStore Returns Analysis: Optimizing Profitability

## Project Overview

As a consultant for the Superstore, this project's primary goal was to analyze the root causes of high return rates, understand their impact on profitability, and provide actionable recommendations to the CEO for reducing returned orders and improving the store's financial health. The project involved in-depth data analysis, visualization, and the development of a dashboard for ongoing monitoring.

## Business Problem

The Superstore is experiencing a significant volume of returned orders, impacting its profitability and operational efficiency. The key questions addressed in this analysis were:
* What are the primary drivers behind the high number of returned orders?
* Are there specific products, customers, or geographic areas contributing disproportionately to returns?
* Does time or seasonality play a role in return rates?
* How can the Superstore leverage insights from this analysis to reduce returns and improve its bottom line?

## Data Source

The analysis utilized the Superstore's operational data, focusing on order and return records. Key data points included product information, customer details, geographical data, sales figures, and return status for each order.

## Project Phases & Methodology

The project was structured into three main phases: data analysis to identify return root causes, dashboard creation for monitoring, and presentation of findings.

### Goal 1: What is Causing Returns? (Exploratory Data Analysis)

This phase focused on identifying patterns and root causes of returned orders through various visualizations.

* **Data Preparation:** The `Returns` table was LEFT JOINed onto the `Orders` table. A new calculated field, `Returned`, was created where null values were converted to `0` and "Yes" values to `1`. The average of this field represents the return rate.
* **Key Analytical Views Developed:**
    * **Correlation between Total Sales and Total Returns by Product Subcategory:** To assess if higher sales always lead to higher returns.
    * **Return Rate by Product Category:** To pinpoint which product categories have the highest propensity for returns.
    * **Return Rate by Customer:** To identify customers who are more prone to making returns (filtering out customers with only 1 order).
    * **Return Rate by Geographic Measure (State/City):** To uncover any geographic concentrations of returned orders.
    * **Return Rate by Measure of Time (Month/Week):** To detect seasonal effects on return rates.
    * **Composite Charts:** Two different composite charts combining multiple factors (e.g., date, geography, product category) to provide a holistic view of return drivers.

* **Key Findings from Return Rate Analysis:**
    * **Geographic Concentration:** Certain states accounted for a majority of the returns. States like California, Texas, New York, and Washington had among the highest rates of returns. California alone contributed 42.47% of all total returns.
    * **Category in California:** In California, Office Supplies were mainly responsible for the high return rate.
    * **Technology Trend:** Given California's leading role in technology adoption, this high return rate in office supplies might indicate a broader shift across states, where products for traditional office needs are becoming obsolete due to remote work and cloud technology. Technology is the smallest category making up SuperStore returns.
    * **Customer Return Rates:** Specific customers were identified as having the highest return rates, many of whom reside in the top return states.

* **Overall Recommendations for SuperStore**
    * Get into touch with the California, New York, and Texas customers. Ask them what their needs are and how can you accommodate them. Establish demand.
    * I recommend lessening your supply of office supplies such as binders, papers and art. 
    * Make this an opportunity to create a system that can be applied to other markets as other states soon may follow behind California. 
