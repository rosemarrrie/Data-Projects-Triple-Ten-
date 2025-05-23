# E-commerce Business Analytics Project: Conversion Funnel & Cohort Analysis

## Project Overview

This project was undertaken as a junior analyst at an e-commerce company, focusing on transforming raw user transaction logs into actionable business metrics. The primary objective was to understand user behavior on the company's website by building a conversion funnel and conducting a comprehensive cohort analysis to track customer retention. The project heavily utilized advanced spreadsheet techniques for data preparation, aggregation, and analysis.

## Business Challenge

The executive team was keen to gain deeper insights into user interaction and long-term customer value. The key business challenges addressed were:

1.  **Conversion Funnel Analysis:** Understanding how effectively product page views convert into purchases to identify potential drop-off points and optimize the user journey.
2.  **Cohort-Based Retention Analysis:** Building acquisition cohorts based on users' first purchase month and tracking their retention rates over time to assess the effectiveness of customer acquisition and engagement strategies.

## Data Source

The analysis was performed on the `raw_user_activity` dataset, which contains event logs of user activities on the e-commerce website. Each row represents a specific user event.

**Dataset Columns:**
* `user_id`: Unique customer IDs.
* `event_type`: The type of activity by the user (e.g., `view`, `cart`, `purchase`).
* `category_code`: Category of the product being viewed or purchased.
* `brand`: Company that manufactures the product.
* `price`: Price of the product in USD.
* `event_date`: Date of the user activity in అంతే-MM-DD format.

## Project Phases & Methodology

The project was executed in distinct phases, focusing on data preparation, analytical insights, and comprehensive documentation.

### Goal 1: Build a Conversion Funnel

This phase aimed to visualize and quantify the user journey from viewing a product to making a purchase.

* **Objective:** Create a conversion funnel to better understand how users interact with the website.
* **Methodology:**
    * A pivot table named `conversion_funnel` was created from the `raw_user_activity` sheet.
    * Unique users were counted for each stage of the funnel.
    * Formulas were implemented to calculate both `total conversion rates` and `conversion rates to the next step` within the pivot table.
* **Key Findings (Conversion Funnel):**
    * The e-commerce store has a high conversion rate.
    * Total conversion ranged from 10-29%.
    * Conversion from each stage of the funnel ranged from 29-36%.
    * 10% of overall users on the website end up making a purchase.
    * Specific unique user counts per stage were: `view` (10453 users), `shopping_cart` (3036 users), and `purchase` (1081 users).

### Goal 2: Prepare Data for Cohort Analysis

This was a critical data preparation phase, leveraging advanced spreadsheet techniques to structure data for cohort analysis.

* **Objective:** Build acquisition cohorts based on the month of a user’s first purchase and track cohort metrics month by month.
* **Methodology:**
    * **Filter Purchases:**
        * A new sheet, `purchase_activity`, was created by filtering `raw_user_activity` to include only `purchase` event types.
        * This resulted in 4,845 rows (including column headers).
    * **Calculate First Purchase Dates:**
        * A pivot table was created to find the first purchase date for each user by calculating the minimum `event_date` per user.
        * These first purchase dates were then transferred to a new column (`first_purchase_date`) within the `purchase_activity` sheet using a `VLOOKUP()` function.
    * **Set Up Monthly Data for Cohorts:**
        * Three new columns were added to `purchase_activity` to facilitate cohort grouping:
            * `event_month`: Derived from `event_date` using the `TEXT()` function.
            * `first_purchase_month`: Derived from `first_purchase_date` using the `TEXT()` function.
            * `cohort_age`: Calculated as the number of months between the first purchase and subsequent purchase events using the `DATEDIF()` function, representing the age of the purchase event within the cohort.

### Goal 3: Calculate Retention Rates

This phase involved aggregating the prepared data into cohorts and calculating retention rates.

* **Objective:** Aggregate purchase data into cohorts and calculate retention rates for each cohort month by month.
* **Methodology:**
    * **Group Data into Cohorts:**
        * A pivot table named `cohort_analysis` was created from `purchase_activity`.
        * Rows represented `first_purchase_month` (e.g., "2020-09", "2020-10"), and columns contained the count of unique users for each `cohort_age` (0, 1, 2, 3, 4). There were 6 cohorts.
        * Example cohort data:
            * **2020-09 cohort:** 32 users at age 0, 4 at age 1, 2 at age 2.
            * **2020-10 cohort:** 187 users at age 0, 14 at age 1, 7 at age 2.
            * **2020-11 cohort:** 238 users at age 0, 13 at age 1, 7 at age 2.
            * **2020-12 cohort:** 203 users at age 0, 9 at age 1, 6 at age 2.
            * **2021-01 cohort:** 233 users at age 0, 16 at age 1.
            * **2021-02 cohort:** 188 users at age 0.
    * **Calculate Overall Retention Rates:**
        * A new sheet, `retention_rates`, was created to display the retention rates.
        * Formulas were used to calculate retention rates using the formula: (Number of individuals retained / Number of individuals at the beginning of the period) x 100.
* **Key Findings (Retention Rates):**
    * The retention rate of the E-commerce store generally seems to lower over time.
    * Roughly half of the users from each cohort ended up purchasing again in the next month after their first purchase.
    * Specific retention percentages:
        * **2020-09 cohort:** 12.50% at age 1, 6.25% at age 2, 0.00% at age 3, 3.13% at age 4.
        * **2020-10 cohort:** 7.49% at age 1, 3.74% at age 2, 0.53% at age 3, 0.53% at age 4.
        * **2020-11 cohort:** 5.46% at age 1, 2.94% at age 2, 0.42% at age 3, 0.00% at age 4.
        * **2020-12 cohort:** 4.43% at age 1, 2.96% at age 2, 0.00% at age 3, 0.00% at age 4.
        * **2021-01 cohort:** 6.87% at age 1, 0.00% at ages 2, 3, 4.

### Goal 4: Organize and Document Spreadsheet

To ensure a polished and professional deliverable for the executive team, best practices in spreadsheet organization and documentation were applied.

* **Executive Summary:**
    * Briefly summarized results and conclusions from the `conversion_funnel` and `retention_rates` sheets.
    * Provided analysis descriptions, including raw data properties (collected from user activity log, used user ID, event type, event date; category code, price, and brand were not used).
    * Explained how conversion rates were calculated (unique user counts, simple division).
    * Explained decisions made in cohort analysis of retention rates (first purchase date, tracking monthly purchases, simple division).
* **Table of Contents:** Filled with organized sheet order and brief descriptions.
* **Sheet Organization:**
    * Sheet tabs were reordered for logical flow: `Table of Contents` and `Executive Summary` first, followed by analytical results (`conversion_funnel`, `retention_rates`, `cohort_analysis`), then calculation sheets (`purchase_activity`, `first_purchase`), and finally raw data (`raw_user_activity`).
* **Formatting:**
    * Spreadsheets were formatted for readability: numbers and dates formatted, borders added to tables, bold fonts used for column headers, rows frozen, and calculation cells highlighted.
    * A `Cleaning log` sheet documented all data cleaning steps.
    * Unnecessary columns were hidden.

## Project Deliverable

The final project was a well-organized and professionally documented Google Sheets file, providing key insights into user conversion and retention for the e-commerce company, suitable for presentation to executive stakeholders.
