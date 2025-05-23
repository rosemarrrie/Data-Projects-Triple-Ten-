# E-commerce Business Analytics Project: Conversion Funnel & Cohort Analysis

## Project Overview

As a newly hired junior analyst at an e-commerce company, my primary task for this project was to analyze raw transaction logs to derive key business metrics. This involved two main parts: building a conversion funnel to understand user interaction from product views to purchases, and performing a cohort analysis to track user retention based on their first purchase month. This project emphasizes advanced spreadsheet techniques for data preparation, aggregation, and insightful reporting for executive stakeholders.

## Business Challenge

The executive team is keen on understanding user behavior on the website to optimize conversion rates and enhance customer retention. Specifically, the challenges were to:

1.  **Quantify Conversion from Views to Purchases:** Understand the effectiveness of the website in converting product page views into actual purchases.
2.  **Analyze User Retention by Acquisition Cohort:** Track how user engagement (specifically purchases) changes over time for different groups of users acquired in the same month.

## Data Source

The analysis was based on a dataset of `raw_user_activity` containing detailed event logs from the company's website. Each row represents a specific user activity, such as viewing a product, opening a shopping cart, or completing a purchase.

**Columns in `raw_user_activity`:**
* `user_id`: unique customer IDs
* `event_type`: the type of activity by the user
* `category_code`: category of the product being viewed or purchased
* `brand`: company that makes the product
* `price`: price of the product, in USD
* `event_date`: date of the user activity, in YYYY-MM-DD format

## Project Phases & Methodology

### Task 1: Build a Conversion Funnel

To understand how well product page views convert into purchases, a conversion funnel was constructed.

* **Objective:** Create a conversion funnel to understand user interaction from product views to purchases.
* **Methodology:**
    * A pivot table named "conversion_funnel" was created from the `raw_user_activity` sheet.
    * Unique users were counted for each of the three funnel stages (view, cart, purchase).
    * Formulas were added to calculate `total conversion rates` and `conversion rates to the next step`.

### Task 2: Prepare Data for Cohort Analysis

This was the most extensive part, focusing on preparing data for building acquisition cohorts based on the month of a user's first purchase.

* **Objective:** Prepare data to build acquisition cohorts based on the month of a user’s first purchase and track cohort metrics monthly.
* **Methodology:**
    * **Filtering Purchases:** A new sheet, "purchase_activity", was created containing only `purchase` event types from `raw_user_activity` (4,845 rows including headers).
    * **Calculating First Purchase Dates:**
        * A pivot table, "first_purchase", was used to find the minimum `event_date` (first purchase date) for each unique user.
        * The `first_purchase_date` was then added as a new column in the "purchase_activity" sheet using `VLOOKUP()` to match user IDs.
    * **Setting Up Monthly Data for Cohorts:**
        * Three new columns were created in "purchase_activity":
            * `event_month`: Calculated using `TEXT(event_date, "YYYY-MM")`.
            * `first_purchase_month`: Calculated using `TEXT(first_purchase_date, "YYYY-MM")`.
            * `cohort_age`: Calculated using `DATEDIF(first_purchase_date, event_date, "M")` to determine the number of months between the first purchase and subsequent events (ranging from 0 to 4 months).

### Task 3: Calculate Retention Rates

The last steps involved aggregating purchase data into cohorts and calculating monthly retention rates.

* **Objective:** Aggregate purchase data into cohorts and calculate retention rates month by month.
* **Methodology:**
    * **Grouping Data into Cohorts:** A pivot table, "cohort_analysis", was created from "purchase_activity" to group data by `first_purchase_month` (6 cohorts) and count unique users by `cohort_age` in columns.
    * **Calculating Overall Retention Rates:**
        * A new sheet, "retention_rates", was created.
        * Row labels for cohorts (A3:A7) and column labels for cohort ages (B2:E2, from 1 to 4 months, excluding age 0) were added.
        * Formulas were implemented to calculate retention rates for each cohort at each cohort age, referencing the starting cohort sizes from "cohort_analysis".

### Part 4: Organize and Document Spreadsheet

To ensure the project was polished and professional for the executive team, best practices for spreadsheet organization and documentation were applied.

* **Executive Summary:**
    * A brief summary of results and conclusions from the "conversion_funnel" and "retention_rates" sheets was provided.
    * Analysis descriptions detailed the raw data (timespan, event types, usage), how conversion rates were calculated (user counts), and decisions made in cohort analysis (cohort formation, tracking period, retention rate calculation).
* **Sheet Organization:** Tabs were reordered for logical flow: "Table of Contents" and "Executive Summary" first, followed by analytical results, calculation sheets, and finally raw data sheets. The "Table of Contents" was filled with the organized sheet order and brief descriptions.
* **Formatting:** Spreadsheets were formatted for readability, including number and date formatting, table borders, bold column headers, frozen rows, and highlighted calculation cells.

## Project Deliverable

The final deliverable is a well-organized and documented Google PDF file, with view-only access provided via a shared link, demonstrating the conversion funnel analysis and cohort-based retention rates.
