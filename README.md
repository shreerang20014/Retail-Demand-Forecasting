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

## Executive Summary
This project evaluates whether modern machine learning models can improve short‑term retail demand forecasting compared with a simple Seasonal Naïve baseline, using Walmart’s publicly available M5 dataset. The dataset contains over 3,000 products sold across 10 stores in California, Texas, and Wisconsin, resulting in tens of thousands of item–store daily time series. Retail demand at the SKU level is highly intermittent, with 62%–78% of days with zero sales, making forecasting particularly challenging and underscoring the importance of stable, hierarchy‑aware models.

Across both validation and test datasets, machine learning models significantly outperform the baseline. LightGBM shows the strongest overall performance, producing lower WRMSSE values and more stable forecasts at aggregated levels, where retail planning decisions typically occur. These results demonstrate that global ML forecasting models can provide meaningful improvements in visibility and reliability for short‑term retail demand.

The improved forecasts were translated into simple, buffer‑based daily inventory signals, illustrating how enhanced predictive accuracy can support replenishment decisions, even without a full optimisation model.

<img width="769" height="608" alt="image" src="https://github.com/user-attachments/assets/6149c152-71a6-45a8-a2f0-6f193241101c" />


## Key Insights
### Forecasting Performance Trends
•	**Seasonal Naïve Baseline:**
Provided consistent but inflexible forecasts, repeating prior weekly patterns. It struggled with sudden shifts in demand and produced systematic bias due to its inability to adapt to new patterns. 

•	**XGBoost and LightGBM Improvements:**
Both ML models delivered substantially lower MAE, RMSE, and WRMSSE scores. LightGBM generated smoother, more stable predictions across categories and stores, especially for high-volume aggregated levels.

•	**Impact of Intermittent Demand:**
High sparsity made SKU-level forecasting difficult for all models. However, aggregation reduced noise and revealed clear weekly seasonality patterns, allowing machine learning models to perform disproportionately better at the category, store, and state levels. 

•	**Hierarchical Structure Matters:**
Improvements were strongest where they count operationally, at higher levels where retailers set inventory budgets, plan distribution, and manage capacity. This validates the use of WRMSSE as the primary evaluation metric. 

<img width="500" height="200" alt="image" src="https://github.com/user-attachments/assets/4edaf166-6644-44d7-97ad-993c90a04edf" />


### Demand Patterns & Behavioral Insights
•	**Weekly Seasonality:**
All states and categories exhibited strong weekday patterns, with demand increasing toward weekends. This supports the use of a weekly seasonal baseline. 

•	**Category Differences:**
FOODS showed the highest volume and lower sparsity, while HOBBIES and HOUSEHOLD exhibited the most intermittent behaviour (up to 78% zero sales days), influencing forecasting difficulty. 

•	**Geographical Variation:**
Sales totals for CA, TX, and WI varied significantly, confirming the importance of store and state identifiers in forecasting models. 

<img width="1227" height="302" alt="image" src="https://github.com/user-attachments/assets/9633861e-eda7-43de-a401-723fb2a89c3a" />
<img width="810" height="299" alt="image" src="https://github.com/user-attachments/assets/6f53f10e-1be9-410e-9520-219a04f000df" />


## Recommendations
Based on the empirical findings of the forecasting models and observed demand patterns, the following recommendations are provided:

•	**Use LightGBM for short-term retail forecasting.**
It delivers the most stable and accurate results, especially for operationally important aggregated levels.

•	**Prioritise aggregated-level forecasts for planning.**
Category, store, and state-level predictions are more reliable and more relevant for replenishment and distribution scheduling.

•	**Apply simple buffer-based inventory rules.**
Translating forecasts into inventory signals using percentage buffers provides actionable guidance even without full optimisation. 

•	**Monitor high sparsity categories.**
HOBBIES and HOUSEHOLD items need extra attention due to intermittent demand and higher uncertainty. Consider adjusting safety buffers or reviewing store-level stocking strategies. 

•	**Leverage calendar attributes for planning.**
Weekday cycles, events, and SNAP-driven behaviour significantly influence demand; retail planners should integrate these into ordering cycles.





