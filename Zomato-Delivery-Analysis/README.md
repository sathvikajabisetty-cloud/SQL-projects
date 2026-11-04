Zomato Delivery Analysis — SQL & Power BI

Project Overview

This project analyzes Zomato food delivery data to understand delivery performance and identify the factors associated with longer delivery times.

The analysis was performed using **MySQL** for data cleaning, validation, exploration, and business analysis, followed by **Power BI** for interactive visualization and dashboard creation.

The project demonstrates an end-to-end data analytics workflow:

**Raw Data → SQL Cleaning → SQL Analysis → Business Insights → Power BI Dashboard**

---

Objectives

The main objectives of this project were to:

- Analyze overall delivery performance
- Understand the impact of traffic conditions on delivery time
- Examine the relationship between weather and delivery time
- Analyze the effect of multiple deliveries on delivery duration
- Compare delivery performance across different time periods
- Analyze order distribution across cities
- Explore the relationship between vehicle condition and traffic
- Identify recurring delivery scenarios associated with longer delivery times

---

Tools & Technologies

- **MySQL** — Data cleaning, validation and analysis
- **Power BI** — Dashboard and data visualization
- **SQL** — Business analysis and aggregations
- **DAX** — Power BI calculated columns and measures
- **Power Query** — Data preparation in Power BI

---

Dataset

The dataset contains food delivery records with information such as:

- Order ID
- Delivery Partner ID
- Delivery Partner Age
- Delivery Partner Ratings
- Order Date
- Time Ordered
- Time Taken for Delivery
- Weather Conditions
- Road Traffic Density
- Vehicle Condition
- Type of Order
- Multiple Deliveries
- City
- Festival information
- City Type

The final dataset used for analysis contained **45,584 delivery records**.

---

Data Cleaning & Validation

The data was first examined and validated using SQL.

Cleaning performed

- Checked for missing values
- Checked for duplicate IDs
- Validated delivery partner ages
- Validated delivery ratings
- Checked delivery time values
- Identified invalid age values
- Corrected invalid delivery ratings
- Examined distinct categorical values
- Performed final data-quality validation

 Data quality corrections

Delivery ratings greater than 5 were treated as invalid and set to `NULL`.

Delivery partner age values of **15** were identified as invalid and set to `NULL`.

After cleaning, the dataset was used for further analysis.

---

 SQL Analysis

Several business questions were explored using SQL.

### 1. Traffic vs Delivery Time

Delivery time increased as traffic conditions became heavier.

| Traffic Condition | Orders | Avg. Delivery Time |
|---|---:|---:|
| Jam | 14,139 | 31.18 min |
| High | 4,423 | 27.24 min |
| Medium | 10,945 | 26.70 min |
| Low | 15,476 | 21.27 min |

The difference between **Jam** and **Low** traffic was approximately **9.91 minutes**.

---

2. Weather vs Delivery Time

Weather conditions also showed differences in average delivery time.

| Weather | Avg. Delivery Time |
|---|---:|
| Cloudy | 28.92 min |
| Fog | 28.91 min |
| Windy | 26.12 min |
| Sandstorms | 25.88 min |
| Stormy | 25.87 min |
| Sunny | 21.86 min |

Cloudy and foggy conditions had average delivery times around 7 minutes higher than sunny conditions in this dataset.

---

3. Multiple Deliveries

The number of multiple deliveries associated with an order showed a substantial difference in average delivery time.

| Multiple Deliveries | Orders | Avg. Delivery Time |
|---|---:|---:|
| 0 | 14,094 | 22.88 min |
| 1 | 28,151 | 26.85 min |
| 2 | 1,985 | 40.45 min |
| 3 | 361 | 47.82 min |

Orders associated with 3 multiple deliveries had an average delivery time of **47.82 minutes** compared with **22.88 minutes** for orders with 0.

The 3-delivery category contains only 361 records, so this result should be interpreted with the smaller sample size in mind.

---

4. Time of Day

Delivery performance was also analyzed across different time periods.

| Time Period | Orders | Avg. Delivery Time |
|---|---:|---:|
| Morning | 7,135 | 21.42 min |
| Afternoon | 3,567 | 25.51 min |
| Evening | 20,822 | 29.66 min |
| Night | 12,329 | 23.66 min |

The **Evening** period had both the highest number of orders and the highest average delivery time among the four periods.

---

5. Order Type

Average delivery times across order types were relatively similar.

| Order Type | Avg. Delivery Time |
|---|---:|
| Meal | 26.42 min |
| Snack | 26.29 min |
| Buffet | 26.28 min |
| Drinks | 26.19 min |

The difference between the highest and lowest averages was only about **0.23 minutes**.

---

 6. Traffic + Weather

The combination of traffic and weather conditions was also analyzed.

Some of the higher average delivery times included:

- Jam + Fog → **36.81 min**
- Jam + Cloudy → **36.69 min**
- Jam + Windy → **30.22 min**
- Jam + Sandstorms → **30.02 min**
- Jam + Stormy → **29.85 min**

This analysis helped examine how multiple delivery conditions can occur together.

---

7. Vehicle Condition + Traffic

Delivery time was also compared across vehicle-condition categories and traffic levels.

For example:

- Vehicle condition 0 + Jam → **36.28 min**
- Vehicle condition 1 + Jam → **28.75 min**
- Vehicle condition 2 + Jam → **28.69 min**

The dataset uses vehicle-condition values of **0, 1 and 2**, but the available data does not establish a specific semantic meaning for those values, so they are treated as categories rather than labels such as "good" or "bad."

---

Power BI Dashboard

The cleaned SQL dataset was connected to Power BI using the MySQL connector.

The dashboard contains:

KPI Cards

- **Total Orders:** 45,584
- **Average Delivery Time:** 26.29 minutes
- **Average Rating:** 4.63 / 5
- **Delivery Partners:** 1,320

 Visualizations

- Average Delivery Time by Traffic
- Average Delivery Time by Multiple Deliveries
- Orders by City
- Average Delivery Time by Weather Conditions
- Average Delivery Time by Time Period

The dashboard was designed as a single-page summary of the SQL analysis.

---

Key Insights

Traffic has a strong association with delivery time

Average delivery time was **31.18 minutes during Jam traffic** compared with **21.27 minutes during Low traffic**.

Weather conditions are associated with different delivery times

Cloudy and foggy conditions had higher average delivery times than sunny conditions in this dataset.

Multiple deliveries are associated with longer delivery times

Average delivery time increased from **22.88 minutes** for orders with 0 multiple deliveries to **47.82 minutes** for orders with 3.

Evening deliveries take longer on average

Evening deliveries averaged **29.66 minutes**, compared with **21.42 minutes** in the morning.

Order type shows relatively little difference

Meal, Snack, Buffet and Drinks had very similar average delivery times, with only about **0.23 minutes** separating the highest and lowest averages.

---

 Overall Delivery Performance

| KPI | Value |
|---|---:|
| Total Orders | 45,584 |
| Average Delivery Time | 26.29 min |
| Fastest Delivery | 10 min |
| Slowest Delivery | 54 min |
| Average Rating | 4.63 / 5 |
| Cities | 3 |
| Delivery Partners | 1,320 |


