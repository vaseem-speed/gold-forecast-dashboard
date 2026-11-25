# AUREUS QUANT — Gold Price Forecasting & Live Market Dashboard

An interactive, client-side econometric forecasting and market analytics dashboard tracking **International Spot Gold (`XAU/USD`)** and **Indian Domestic Bullion (`MCX` & Hyderabad Retail 24K/22K)**.

🔗 **Live Dashboard:** [https://vaseem-speed.github.io/gold-forecast-dashboard/](https://vaseem-speed.github.io/gold-forecast-dashboard/)

---

## Features

- **Live Market Benchmarks:** Tracks International Spot Gold (`$/oz`), `USD/INR`, MCX India Spot & Futures (`₹/10g`), and Hyderabad Retail Bullion rates (`24K` & `22K`) with streaming micro-ticks and manual spot sync.
- **Actuals & 14-Day Forecast Cone:** Interactive Chart.js visualization plotting historical spot prices alongside the model's theoretical fair value and a $\pm 1\sigma$ 14-day projection cone. Toggle seamlessly between `XAU/USD ($/oz)` and `India 24K (₹/10g)`.
- **Multi-Factor Econometric Engine:** Adjust macro inputs in real time to observe factor attribution and fair-value shifts:
  - US 10-Year Nominal Treasury Yield & Core PCE Inflation (auto-deriving US 10Y Real Yield)
  - US Dollar Index (`DXY`)
  - Central Bank & Gold ETF Net Flows (tonnes/month)
  - CBOE Volatility Index (`VIX`)
  - `USD/INR` Exchange Rate, Basic Customs Duty + AIDC, and GST
- **One-Click Macro Scenarios:** Simulate regime shocks such as *Hot US PCE / Hawkish Fed*, *Dovish Pivot / Yield Drop*, and *Rupee Shock (`₹95.00`)*
- **Indian Tax & Duty Waterfall:** Transparent breakdown from international CIF spot conversion (`troy oz → 10g`) through customs duty, GST, and local retail premiums.

---

## Econometric Pricing Model

### 1. International Fair Value (`XAU/USD`)
$$P_{\text{Fair}} = P_0 \cdot \exp\Big(-\beta_1 (r_{\text{real}} - r_0) - \beta_2 \ln(\text{DXY}/\text{DXY}_0) + \beta_3 \Delta\text{Flows} + \beta_4 \Delta\text{VIX}\Big)$$

### 2. Indian Domestic Conversion (`₹ / 10g`)
$$P_{\text{India}} = \left(\frac{P_{\text{Gold (USD/oz)}}}{31.1035} \times 10 \times \text{USDINR}\right) \times (1 + \text{Duty} + \text{GST}) + \text{Local Premium}$$

---

## Project Structure

```text St
gold-forecast-dashboard/
├── index.html   # Single-file interactive dashboard (HTML5, Tailwind CSS, Chart.js)
└── README.md    # Project documentation & econometric methodology
