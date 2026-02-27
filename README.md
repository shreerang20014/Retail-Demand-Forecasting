# Retail-Demand-Forecasting

## Project Background
Retail organisations operate in highly dynamic environments where thousands of products are sold across multiple stores and regions every day. Walmart, one of the world’s largest retailers, manages over 3,000 products across 10 stores in three U.S. states in the M5 dataset. This scale results in tens of thousands of SKU–store time series, each with its own sales patterns, seasonal behaviour, and sensitivity to pricing and calendar events. 

Despite having rich historical data (sales, prices, and detailed calendar attributes), much of this information is often underutilised in generating accurate short‑term forecasts. Retail demand at the SKU level is also highly intermittent, with 60–77% of item‑store observations recording zero sales, depending on the category, making the forecasting task even more challenging. 

This project investigates whether modern machine learning models can improve short‑term retail demand forecasting relative to a simple Seasonal Naïve benchmark, while maintaining consistency across the hierarchical product and store structure. The study uses Walmart’s publicly available M5 dataset to generate 28‑day daily forecasts and evaluates them at multiple aggregation levels, reflecting real retail decision‑making needs. 

The project ultimately aims to enhance demand visibility and support better inventory‑related decisions by converting forecasts into simplified stock‑level signals.
