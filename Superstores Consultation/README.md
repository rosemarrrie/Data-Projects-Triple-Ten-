# Saving SuperStore: Profitability and Operations Analysis

## Project Overview

As a consultant for a superstore facing potential bankruptcy, this project focused on analyzing its operations to identify key profit and loss centers, optimize product offerings, and assess the viability of advertising campaigns. The goal was to provide data-driven recommendations to increase overall profitability.

## Business Problem

The superstore is experiencing financial difficulties, requiring a comprehensive review of its business performance to identify areas for improvement and guide strategic decisions. The main challenges addressed were:
* Identifying top-performing and underperforming profit/loss centers.
* Determining which products or subcategories to discontinue or prioritize.
* Evaluating the most opportune times and locations for advertising investments.
* Analyzing product return rates to identify potential cost-saving opportunities.

## Data Source

The project utilized the superstore's operational data, including sales, profit, and returns information. The analysis involved dimensions such as product subcategory, region, shipping mode, product ID, state, month, and customer information, along with order and returns data.

## Project Phases & Methodology

The analysis was structured into three main parts, each addressing a critical aspect of the superstore's operations. Each conclusion was supported by individual visualizations.

### Part 1: Profits & Losses

This section aimed to pinpoint areas of strong performance and significant losses.

* **1.1 Identifying Profit & Loss Centers:**
    * **Objective:** Determine the two biggest profit centers and two biggest loss-makers among various pairs of dimensions.
    * **Findings:**
        * Profit in the Central, South, and East regions is highest among the category of Technology.
        * The Western Region has the most profit coming from office supplies.
        * The Consumer Segment yields the highest profit of all three segments across all stores.
        * In the Central region, supplies in the furniture and office category are at a net loss.
        * Among the Consumer Segment, bookcases and tables are at a net loss.

* **1.2 Product Optimization:**
    * **Objective:** Identify products and product subcategories that should be discontinued or prioritized.
    * **Recommendations:**
        * Discontinue sales of bookcases and tables in the Consumer Segment, and focus more on sales of products such as phones, copiers, and accessories in this segment.
        * In the Central region, consider not carrying furniture and office supplies to mitigate losses.
        * During July, Office supplies are a net loss, so avoid selling these products and focus on technology instead.
        * In January, October, and April, furniture sales are at a net loss.
        * The superstore should stop selling the product ATIVA V14 Cut-Shredder because its average profit rate is extremely low in comparison to its return rate.

### Part 2: Advertising Strategy

This part focused on identifying the most profitable advertising opportunities based on average profit per unit sold.

* **Objective:** Identify the 3 best combinations of states and months of the year to advertise in, and determine the willingness to pay for advertising (1/5 of profits).
* **Findings:**
    * **Top 3 Advertising Opportunities (State, Month, Recommended Spend):**
        1.  **California, December:** Recommended spending up to $22,866 in advertising.
        2.  **New York, September:** Recommended spending up to $25,520 in advertising.
        3.  **Washington, March:** Recommended spending up to $104,000 in advertising.

### Part 3: Returned Items Analysis

This section analyzed product return rates to identify items costing the company money.

* **Methodology:**
    * A calculated field was created for `Returned`, converting null values to `0` and "Yes" values to `1`.
    * Visualizations were created to show products and customers with the highest return rates.
    * A visualization of average profit against average return rate was created based on a chosen dimension.
* **Key Findings & Recommendations:**
    * The product ATIVA V14 Cut-Shredder has an extremely low average profit compared to its high return rate, making it a candidate for discontinuation.
    * The analysis identified specific products and customers with high return rates.

## Conclusion & Recommendations

This comprehensive analysis provides actionable insights for the superstore to improve its profitability. By strategically managing product offerings, optimizing regional sales, and targeting advertising efforts, the superstore can move away from bankruptcy. Key recommendations include:

* **Product Portfolio Optimization:** Discontinue low-profit, high-return products like ATIVA V14 Cut-Shredder, and re-evaluate furniture and office supply sales in underperforming regions/months (e.g., Central region, July for office supplies, Jan/Oct/Apr for furniture). Focus on high-profit items like technology in relevant regions.
* **Targeted Advertising:** Invest advertising funds strategically in high-profitability state-month combinations such as California in December, New York in September, and Washington in March, allocating up to 1/5 of the expected profits.
* **Return Management:** Continuously monitor product and customer return rates to identify and address issues that impact profitability.

By implementing these recommendations, the superstore can enhance its operational efficiency and move towards a more sustainable and profitable future.
