# Zuber Ride Sharing Data Analysis: Chicago Market Insights

## Project Overview

This project involved acting as a data analyst for Zuber, a new ride-sharing company launching in Chicago. The core task was to identify patterns in available taxi ride data, understand passenger preferences, and analyze the impact of external factors, specifically weather, on ride frequency and duration. The analysis utilized SQL queries to extract, transform, and analyze data from various database tables.

## Business Challenge

Zuber aims to understand the Chicago ride-sharing market better to optimize its launch strategy. The key questions addressed by this analysis include:
* Identifying the most popular taxi companies in Chicago.
* Understanding ride patterns, including popular pickup/dropoff locations and day-of-week trends.
* Investigating the impact of weather conditions on ride duration, specifically for key routes.

## Data Source

The analysis was performed using a relational database containing information on taxi rides in Chicago. The database comprised the following tables:

* **`neighborhoods` table:** Contains data on city neighborhoods, including `name` and `neighborhood_id`.
* **`cabs` table:** Contains data on taxis, including `cab_id`, `vehicle_id`, and `company_name`.
* **`trips` table:** Contains data on individual rides, including `trip_id`, `cab_id`, `start_ts` (start date/time), `end_ts` (end date/time), `duration_seconds` (ride duration), `distance_miles` (ride distance), `pickup_location_id`, and `dropoff_location_id`.
* **`weather_records` table:** Contains data on weather conditions, including `record_id`, `ts` (record date/time), `temperature`, and `description` (e.g., "light rain").

**Note on Table Connection:** There is no direct connection between the `trips` and `weather_records` tables. They were joined using `trips.start_ts` and `weather_records.ts` (time rounded to the hour) to link rides with corresponding weather conditions.

## Project Phases & Methodology

The project was divided into two main steps: exploratory data analysis and a deeper investigation into weather impact.

### Goal 1: Exploratory Data Analysis (SQL Queries)

This phase focused on understanding the general landscape of the Chicago taxi market and identifying popular companies and ride volumes.

* **1.1 Top Taxi Companies by Ride Count (November 15-16, 2017):**
    * **Objective:** Find the number of taxi rides for each taxi company for a specific two-day period.
    * **Methodology:** SQL query joining `cabs` and `trips` tables, filtering by `start_ts` date range, grouping by `company_name`, and ordering by `trips_amount` in descending order.
    * **Result:**
        | company_name                 | trips_amount |
        | :--------------------------- | :----------- |
        | Flash Cab                    | 19558        |
        | Taxi Affiliation Services    | 11422        |
        | Medallion Leasin             | 10367        |
        | Yellow Cab                   | 9888         |
        | Taxi Affiliation Service Yellow | 9299         |
        | Chicago Carriage Cab Corp    | 9181         |
        | City Service                 | 8448         |

* **1.2 Rides for "Yellow" or "Blue" Companies (November 1-7, 2017):**
    * **Objective:** Count rides for companies whose names contain "Yellow" or "Blue" for a specific week.
    * **Methodology:** SQL query using `UNION ALL` to combine results for companies matching 'Yellow' and 'Blue' patterns, filtering by `start_ts` date range, and grouping by `company_name`.
    * **Result:**
        | company_name                     | trips_amount |
        | :------------------------------- | :----------- |
        | Taxi Affiliation Service Yellow  | 29213        |
        | Yellow Cab                       | 33668        |
        | Blue Diamond                     | 6764         |
        | Blue Ribbon Taxi Association Inc.| 17675        |

* **1.3 Consolidated Company Ride Counts (November 1-7, 2017):**
    * **Objective:** Group rides for Flash Cab and Taxi Affiliation Services, and consolidate all other companies into an "Other" category.
    * **Methodology:** SQL query using `CASE` statement to assign company names to "Flash Cab", "Taxi Affiliation Services", or "Other", filtering by `start_ts` date range, grouping by the new `company` field, and sorting by `trips_amount` in descending order.
    * **Result:**
        | company                      | trips_amount |
        | :--------------------------- | :----------- |
        | Other                        | 335771       |
        | Flash Cab                    | 64084        |
        | Taxi Affiliation Services    | 37583        |

### Goal 2: Impact of Weather on Rides from Loop to O'Hare

This phase focused on a specific route and how weather conditions affect ride duration.

* **2.1 Retrieve Neighborhood Identifiers:**
    * **Objective:** Get the `neighborhood_id` for "O'Hare" and "Loop" neighborhoods.
    * **Methodology:** SQL query on the `neighborhoods` table, filtering by `name`.
    * **Result:**
        * Loop: `neighborhood_id` 50
        * O'Hare: `neighborhood_id` 63

* **2.2 Categorize Weather Conditions:**
    * **Objective:** Classify hourly weather records as "Good" or "Bad" based on description.
    * **Methodology:** SQL query on the `weather_records` table using a `CASE` operator to assign `weather_conditions` ("Bad" for "rain" or "storm", "Good" otherwise).
    * **Result (Example):**
        | ts                      | weather_conditions |
        | :---------------------- | :----------------- |
        | 2017-11-01 00:00:00     | Good               |
        | 2017-11-01 01:00:00     | Good               |
        | ...                     | ...                |

* **2.3 Analyze Loop to O'Hare Rides on Saturdays with Weather:**
    * **Objective:** Retrieve all rides from Loop (ID 50) to O'Hare (ID 63) on Saturdays, along with their weather conditions and duration.
    * **Methodology:** SQL query joining `trips` table with a subquery that categorizes `weather_records` (as in 2.2). Filters applied for `pickup_location_id`, `dropoff_location_id`, and `EXTRACT(DOW)` for Saturday. Results sorted by `trip_id`.
    * **Result (Example):**
        | start_ts                | weather_conditions | duration_seconds |
        | :---------------------- | :----------------- | :--------------- |
        | 2017-11-25 12:00:00     | Good               | 1380             |
        | 2017-11-25 16:00:00     | Good               | 2410             |
        | 2017-11-25 14:00:00     | Good               | 1920             |
        | 2017-11-25 12:00:00     | Good               | 1543             |
        | 2017-11-04 10:00:00     | Good               | 2512             |
        | ...                     | ...                | ...              |

## Conclusion & Next Steps

This project provided foundational insights into the Chicago taxi market for Zuber. The analysis revealed popular taxi companies, high-volume routes, and a preliminary understanding of how weather conditions might influence ride patterns for a specific, high-value route.

Future analysis could delve deeper into:
* Comparing ride durations on "Good" vs. "Bad" weather Saturdays for the Loop-O'Hare route to quantify the impact of weather.
* Analyzing ride frequency patterns based on weather conditions across various routes.
* Investigating passenger preferences based on `category_code` or `brand` if additional product-related data were available in a ride-sharing context.
