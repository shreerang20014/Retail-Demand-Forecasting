# Retail-Demand-Forecasting

## Project Background
Retail organisations operate in highly dynamic environments where thousands of products are sold across multiple stores and regions every day. Walmart, one of the world’s largest retailers, manages over 3,000 products across 10 stores in three U.S. states in the M5 dataset. This scale results in tens of thousands of SKU–store time series, each with its own sales patterns, seasonal behaviour, and sensitivity to pricing and calendar events. 

Despite having rich historical data (sales, prices, and detailed calendar attributes), much of this information is often underutilised in generating accurate short‑term forecasts. Retail demand at the SKU level is also highly intermittent, with 60–77% of item‑store observations recording zero sales, depending on the category, making the forecasting task even more challenging. 

This project investigates whether modern machine learning models can improve short‑term retail demand forecasting relative to a simple Seasonal Naïve benchmark, while maintaining consistency across the hierarchical product and store structure. The study uses Walmart’s publicly available M5 dataset to generate 28‑day daily forecasts and evaluates them at multiple aggregation levels, reflecting real retail decision‑making needs. 

The project ultimately aims to enhance demand visibility and support better inventory‑related decisions by converting forecasts into simplified stock‑level signals.

### Key Focus Areas of the Project:
•	**Short Term Sales Forecasting:**
Forecasting daily demand for 28 days across more than 30,000 SKU–store combinations, comparing machine learning approaches with a Seasonal Naïve baseline.

•	**Hierarchical Forecast Evaluation:**
Assessing forecast accuracy across all aggregation levels, item, department, category, store, and state, using WRMSSE and traditional error metrics.

•	**Demand Pattern Analysis:**
Understanding key demand drivers such as weekly seasonality, geographic variation, intermittent behaviour, and category-level differences.

•	**Inventory Decision Support:**
Converting forecast outputs into simple, buffer-based inventory signals that demonstrate how improved demand visibility can assist replenishment planning.


## Data Structure & Initial Checks
The dataset used in this project is derived from Walmart’s publicly available M5 retail forecasting files and consists of three key tables: SALES, CALENDAR, and SELL_PRICES. The SALES table contains daily unit sales for 3,049 products across 10 stores in three U.S. states, along with identifiers such as item, department, category, store, and state. The CALENDAR table provides detailed daily attributes, including weekday, month, year, special event labels, and SNAP program indicators for each state. The SELL_PRICES table captures weekly selling prices for every item‑store combination, enabling analysis of how pricing aligns with weekly demand patterns. Together, these tables form a large‑scale relational dataset containing over 54 million sales‑calendar‑price records when joined.

<img width="1225" height="659" alt="image" src="https://github.com/user-attachments/assets/6b8ddc37-f6ff-4285-a24e-6652635a7b05" />


Before beginning the analysis, several initial checks were performed to ensure the dataset was complete and reliable. A uniqueness check confirmed that each item‑store‑day record was represented once, with no duplicate observations after merging. The date range from 2011‑01‑29 to 2015‑12‑31 was verified to contain no missing days, ensuring stable time‑series continuity. Sales values were checked for validity, confirming no negative quantities and revealing a high level of sparsity, with zero‑sales days accounting for 62% to 78% of observations, depending on product category. Memory‑efficient data types were applied to support downstream processing, reducing the merged dataset to approximately 1.6 GB while preserving integrity. These checks ensured a clean, consistent foundation for forecasting and further exploration.


