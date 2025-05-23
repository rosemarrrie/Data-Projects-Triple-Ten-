# Zomato Business Performance Analysis: Restaurant Insights

## Project Overview

As a junior analyst at Zomato, a multinational restaurant aggregator and food delivery company, my initial assignment involved analyzing test datasets to understand business performance. My focus was on **Restaurant Analysis**, aiming to identify popular restaurants, understand their revenue generation, and derive actionable insights for Zomato's business strategy. The project culminated in a dashboard and a report summarizing key findings.

## Business Problem

Zomato's BI-Analytics Team performs various analyses, including Customer, Restaurant, and Sales. My task was to select one of these areas and develop a research plan to analyze business performance. I chose to concentrate on Restaurant Analysis to help Zomato with future prospecting for new restaurant partners and understanding customer preferences.

## Data Source

The analysis utilized datasets provided by Zomato, specifically focusing on restaurant and order information. The data archive, "Zomato data.zip", contained five tables:

* `food`
* `menu`
* `orders`
* `restaurant`
* `users`

For this analysis, I primarily used the `restaurant` and `orders` datasets, as the other tables were not directly relevant to my focus area.

## Methodology

My approach involved data cleaning, transformation, and visualization to uncover patterns and trends in restaurant performance.

1.  **Data Cleaning and Preparation:**
    * Converted all dollar amounts to USD for consistency.
    * Removed any trailing spaces from data entries.
    * Split any two-phrased cuisines into two separate columns for easier analysis.
    * Handled unavailable restaurant ratings by inputting them as '0' to maintain consistency with numeric data.
    * Null values in the second cuisine column were left in the dataset, and filters were applied in Tableau to manage these spaces during visualization.

2.  **Visualization and Trend Discovery:**
    * Once data was prepared, I utilized Tableau to create various visualizations, including bar charts, pie charts, packed bubbles, and tree maps.
    * While not all visualizations were included in the final dashboard, they were all instrumental in discovering underlying patterns and trends within the data.

## Key Findings & Results

The analysis of restaurant orders revealed several crucial insights:

1.  **Restaurant Popularity & Quality:**
    * The most popular restaurants on the Zomato app are rated in the lower to mid-range quality spectrum (e.g., 2.5-3.5 out of 5 stars).
    * Higher-rated restaurants (e.g., 4.5 stars) had fewer orders.
    * This suggests that customers prioritize accessibility and value over premium dining experiences on the app.

2.  **Top Performing Restaurants:**
    * The top 5 restaurants by order count are:
        1.  Domino's Style Pizza
        2.  Pizza Hut
        3.  McDonald's
        4.  Subway
        5.  KFC
    * These are all corporate restaurant chains known for fast food.

3.  **Order Distribution by City:**
    * The highest number of orders comes from restaurants within major cities, with a few outliers.
    * Cities like Surat, Pune, and Mumbai frequently appeared on the list of high-order territories.
    * The visualization highlighted how popular restaurants contribute to each territory's total orders.

4.  **Most Popular Cuisines:**
    * The most popular cuisines on the Zomato app were:
        1.  North Indian
        2.  Chinese
        3.  Indian
        4.  Biryani
        5.  South Indian

## Recommendations

Based on the trends discovered during this analysis, I recommend that Zomato:

* **Focus on Corporate Chains:** Prioritize doing business with corporate restaurant chains that serve fast food in the low to mid-quality range.
* **Avoid Niche/High-End:** Strategically avoid fine dining establishments or smaller, independent "mom and pop shops" if the goal is to maintain high order volumes.
* **Target Major Cities:** Concentrate efforts on serving corporate restaurant chains that have locations within major cities.
* **Promote Popular Cuisines:** Emphasize partnerships with restaurants selling Indian, Chinese, North Indian, South Indian, and Biryani cuisines, as these show the highest demand.

By aiming to reach these suggested criteria for client acquisition, the Zomato App is likely to perform well in terms of order volume and customer satisfaction.

## Project Deliverables

* **Interactive Dashboard:** A Tableau dashboard visualizing the key findings of the restaurant analysis.
* **Project Report/Presentation:** A summary report detailing the methodology, findings, and recommendations.
