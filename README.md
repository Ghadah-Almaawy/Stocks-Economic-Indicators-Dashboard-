# Stocks & Economic Indicators Dashboard

An interactive, multi-page **Power BI** dashboard that integrates Saudi stock market data with global macroeconomic indicators, combining descriptive, predictive, and prescriptive analytics to help users explore the relationship between financial markets and economic conditions.

> Course project — DS322: Business Intelligence, 2nd Semester 2025–2026.
> Aligned with **UN SDG 8** (Decent Work and Economic Growth) and **SDG 9** (Industry, Innovation and Infrastructure).

##  Problem Statement

Financial markets and economic conditions are closely linked, but investors and analysts often lack a unified tool to analyze both together. Do rising inflation rates negatively affect stock prices? Does strong GDP growth lead to better market performance? This dashboard was built to make these relationships explorable rather than theoretical.

##  Data Sources

| Dataset | Source | Format | Records | Date Range |
|---|---|---|---|---|
| Stock Market Data | Saudi Exchange (Tadawul) | CSV / Excel | 1,000+ rows | 2019–2025 |
| Economic Indicators | World Bank Open Data | CSV | 500+ rows | 1960–2025 |

- **Companies covered:** Ades, Saudi Aramco, Rabigh Refining & Petrochemical, STC
- **Countries covered:** Saudi Arabia, Brazil, France, Japan, Jordan

The two datasets — daily stock data and yearly economic data — were linked through a shared `Year` field in the data model (`CompanyFact`, `DataGDP`, `DataInflation`, `DataUnemployment` tables).

##  Dashboard Preview

**Saudi Stock Market Dashboard**
![Stocks Dashboard](screenshots/01_stocks_dashboard.png)

**EconomyData Dashboard**
![Economy Dashboard](screenshots/02_economy_dashboard.png)

**Economy vs Stocks Predictive Dashboard**
![Predictive Dashboard](screenshots/03_predictive_dashboard.png)

**Market Insights Dashboard**
![Market Insights Dashboard](screenshots/04_market_insights_dashboard.png)

##  Dashboard Pages

**1. Stocks Dashboard** — KPI cards (Peak Trading Value, Highest Low/High Price), a DAX-driven **Investment Recommendation** card (BUY/HOLD/SELL based on trading activity), average value traded by year and by company, and normalized closing-price trends across the four companies.

**2. EconomyData Dashboard** — KPI cards for average GDP growth, unemployment, and inflation; a GDP-growth-over-time line chart across three countries; a GDP-by-country comparison; and an animated GDP-vs-inflation scatter chart with a year slider.

**3. Economy vs Stocks Predictive Dashboard** — An inflation-risk gauge, unemployment and GDP trend lines **with forecasts extending to 2035**, and a second investment-recommendation card driven by forecasted conditions.

**4. Market Insights Dashboard** — A donut chart of trading share by company, GDP/unemployment KPI cards, and a **decomposition tree** that breaks trading activity down by company, year, GDP, inflation, and unemployment for interactive root-cause exploration.

All pages include slicers (date range, company, country, year) for interactive filtering.

##  Key DAX Measures

- **Investment Recommendation** — a `SWITCH`-based measure returning `SELL — High Risk`, `HOLD — Medium Risk`, or `BUY — Low Risk` based on average value traded (prescriptive analytics).
- **Normalized Close / Normalized Value Traded** — scales each company's values by the dataset maximum, enabling fair cross-company comparison.
- **Peak Trading Value, Highest Low Price, Peak High Price** — KPI measures for the Stocks page.
- **Average GDP Growth, Unemployment, Inflation** — `AVERAGE()`-based KPI measures used across the economy pages.

##  Tech Stack

- Microsoft Power BI (Power Query, Data Model relationships, DAX)
- Built-in Power BI forecasting for predictive trend lines

##  Opening the Project

```bash
git clone <this-repo-url>
```
Open `stocks_economy_dashboard.pbix` in **Power BI Desktop** (free download from Microsoft). No external database connection is required — the data is embedded in the model.

##  Limitations & Future Work

- Economic data is yearly while stock data is daily, so comparisons are necessarily approximate (linked via the `Year` field).
- Only 4 companies are covered, which may not represent the broader Saudi market.
- External factors such as oil prices, interest rates, and global events are not included.
- No real-time/live data streaming — the model uses historical data up to 2025.

Planned improvements: connecting to live data via APIs (e.g. Yahoo Finance, Alpha Vantage), using quarterly instead of yearly economic data, applying ML-based forecasting/classification models, and adding sentiment analysis from financial news.


##  License

This project is shared for educational and portfolio purposes.
