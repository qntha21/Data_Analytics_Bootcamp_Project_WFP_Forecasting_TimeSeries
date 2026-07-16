# Data_Analytics_Bootcamp_Project_WFP_Forecasting_TimeSeries

# Indonesia Egg Price Forecasting

## Overview
Built 2 interactive Tableau dashboards analyzing Indonesia's food commodity landscape and forecasting egg prices, covering regional price disparities, commodity selection rationale, historical price trends, and a validated 12-month forecast using SARIMA time series modeling.

## Problem Statement
Indonesia's archipelago geography creates real price disparities across its 34 provinces, and food price volatility directly affects both household welfare and commercial procurement planning. Eggs alone are consumed across every income level, making price stability a genuine public and business concern. Yet forecasting food prices is inherently difficult: structural shocks (like 2023's corn feed cost crisis) and calendar-driven demand events (like Ramadan, which shifts ~11 days earlier every year) can undermine even well-built models. This project asks: which commodity offers the cleanest signal for forecasting, what has actually driven Indonesia's egg price movements since 2022, and how well can that price be predicted 12 months out?

## Dataset
- **Source:** WFP Global Food Prices Database (data.humdata.org)
- **Size:** ~1.8M price observations across 72 countries (2022–2026), narrowed to Indonesia
- **Includes:** commodity, province, market, price (local currency + USD), price flag (actual/estimated), price type (retail/wholesale), date

## Key Findings
- **Commodity selection:** Of 8 commodities with full 48-month data coverage, eggs is the only major protein staple with no government price intervention (unlike rice, sugar, and cooking oil) making it the cleanest market signal, with moderate volatility (CV 14%) that's neither artificially flat nor chaotic
- **Regional gap:** Eastern Indonesia pays measurably more for food on average than Western Indonesia. A pattern consistent across the broader commodity basket, not isolated to one province or product
- **Price trajectory:** Egg prices spiked sharply in 2023 (corn feed cost crisis), stabilized through 2024, and have shown a gentle upward drift since, reaching $1.90/kg by December 2025
- **Forecast performance:** A SARIMA model (regime-aware, changepoint-informed) forecasted January 2026 at $1.96/kg; actual came in at $2.03/kg — a gap explained by Ramadan falling on February 18, 2026, the earliest date in the entire 4-year training window, with no historical January precedent for the resulting demand pull-forward
- **Model discipline:** Various forecasting approaches were tested; none consistently outperformed a simple 3-month moving average during stable periods. A legitimate finding, not a modeling failure, confirming the data itself carries limited additional signal beyond recent price levels in low-volatility windows

## Recommendations
- **Treat eggs as the benchmark commodity** for future food-price monitoring in Indonesia: unregulated, complete data coverage, and a volatility profile well suited to forecasting
- **Build calendar-awareness into procurement planning, not just statistical models:** apply a manual demand buffer in months immediately preceding Ramadan, since the lunar calendar shift means no fixed-month statistical pattern can reliably anticipate it
- **Default to simple forecasting methods in stable periods:** added model complexity (Holt-Winters, Prophet, ensembling) did not improve accuracy and in several cases performed worse than a naive moving average

## Tools Used
Tableau Public (2 dashboards) · Python (Pandas, NumPy, Statsmodels, Prophet, SciPy) · SARIMA/SARIMAX · Regime-Aware Adaptive Forecasting · Changepoint Detection

*Part of the Data Analytics Bootcamp portfolio (2026)*
