# 📊 Sales Report — Power BI Dashboard

<div align="center">

![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-F2C811?logo=powerbi&logoColor=black)
![Data Source](https://img.shields.io/badge/Data-Kaggle-20BEFF?logo=kaggle&logoColor=white)
![Years](https://img.shields.io/badge/Period-2017--2019-purple)
![Status](https://img.shields.io/badge/Project-Completed-brightgreen)
![Domain](https://img.shields.io/badge/Domain-Sales%20Analytics-blueviolet)
![Type](https://img.shields.io/badge/Type-Business%20Intelligence-orange)

**A multi-page interactive Power BI dashboard delivering end-to-end visibility into sales performance, channel behaviour, product trends, regional pricing, and 3-year revenue patterns — designed to drive smarter, faster business decisions.**

</div>

---

## 📌 Table of Contents

- [Problem Statement](#-problem-statement)
- [Project Overview](#-project-overview)
- [Tech Stack & Data](#-tech-stack--data)
- [Data Model — Relationships & Views](#-data-model--relationships--views)
- [Dashboard Walkthrough](#-dashboard-walkthrough)
- [Key KPIs at a Glance](#-key-kpis-at-a-glance)
- [Key Analysis Insights](#-key-analysis-insights)
- [Business Benefits](#-business-benefits)
- [Future Scope](#-future-scope)
- [Project Files](#-project-files)
- [How to Run](#-how-to-run)
- [Author](#-author)

---

## 🚨 Problem Statement

Sales teams and business managers in retail and distribution businesses often struggle with:

- Relying on **static spreadsheets** that cannot answer "why" or "where" questions in real time
- Having **no unified view** across orders, customers, channels, products, warehouses, and geographies simultaneously
- Being unable to identify **which channels and regions** are actually driving revenue vs. volume
- Lacking **granular time-series visibility** to spot daily, monthly, or seasonal revenue shifts by distribution type
- Making **inventory and logistics decisions** without warehouse-level cost intelligence

Without an interactive, cross-dimensional analytics layer, decisions are slow, reactive, and based on incomplete pictures.

> **Goal:** Build a fully interactive, multi-page Power BI dashboard for Superstore Mart that consolidates orders, customer data, product performance, regional pricing, and 3-year revenue trends — giving every stakeholder from operations to leadership a single source of truth.

---

## 🔍 Project Overview

This project delivers a **5-page Power BI sales analytics dashboard** built on Kaggle's `Sales_Analysis_Report` dataset, covering **3 full fiscal years (2017–2019)** across three sales channels: **Distributor, Export, and Wholesale**.

The report is structured into five purpose-built pages:

| Page | Title | Purpose |
|---|---|---|
| **1** | Executive Summary & KPI Overview | Headline metrics, product cost-demand analysis, regional pricing map, slicers |
| **2** | Yearly Sales (2017–2019) | Max monthly revenue by channel across all 3 years on one view |
| **3** | 2017 Monthly Sales | Day-level revenue breakdown by channel for all 12 months of 2017 |
| **4** | 2018 Monthly Sales | Day-level revenue breakdown by channel for all 12 months of 2018 |
| **5** | 2019 Monthly Sales | Day-level revenue breakdown by channel for all 12 months of 2019 |

**What this project demonstrates:**
- End-to-end Power BI development: data modelling → DAX measures → multi-page reporting
- Star schema relational data modelling across 4 tables
- Time-series analysis at monthly and daily granularity across 3 fiscal years
- Multi-channel revenue comparison (Distributor vs. Export vs. Wholesale)
- Business-focused design accessible to both technical and non-technical stakeholders
- Geographic intelligence through tree map pricing visualisation across 100 regions

---

## 🚀 Tech Stack & Data

| Layer | Tool / Source |
|---|---|
| **BI & Visualisation** | Microsoft Power BI Desktop |
| **Data Modelling** | Power BI Relationships — Star Schema |
| **Calculations** | DAX (Data Analysis Expressions) |
| **Data Source** | Kaggle — `Sales_Analysis_Report` dataset |

---

## 🗂️ Data Model — Relationships & Views

The dashboard is powered by a **star schema** with one central fact table connected to three dimension tables:

```
                    ┌──────────────────┐
                    │  Products_Data   │
                    │  (Product names, │
                    │  unit cost,      │
                    │  unit price)     │
                    └────────┬─────────┘
                             │ (many-to-one)
         ┌───────────────────▼────────────────────┐
         │             Sales_Orders               │
         │  ─── Core Fact Table ───               │
         │  Order ID · Date · Channel             │
         │  Quantity · Total Revenue              │
         │  Unit Cost · Warehouse Code            │
         └──────┬──────────────────────┬──────────┘
   (many-to-one)│                      │(many-to-one)
   ┌────────────▼─────┐   ┌────────────▼──────────────┐
   │  Customer_Data   │   │       Region_Data          │
   │  50 unique       │   │  City · Suburb             │
   │  buyers          │   │  100 regions               │
   └──────────────────┘   └───────────────────────────┘
```

**Interactive Slicers (Page 1) — filter the entire report by:**

| Slicer | Options |
|---|---|
| **Types of Channels** | Distributor · Export · Wholesale |
| **Unique Cities** | Auckland, Central Otago, Christchurch, + more |
| **Unique Warehouses** | AXW291 · FLR025 · GUT930 · (4 total) |
| **Unique Suburbs** | Algies Bay, Aramoho, Atawhai, + more |

---

## 📋 Dashboard Walkthrough

### Page 1 — Executive Summary & KPI Overview

![Page 1 — KPI Overview & Product Analysis](./Dashboard-Screenshots/Page%201.png)

The landing page combines headline KPI cards, interactive slicers, and two core visualisations giving an instant read on cost-demand dynamics and geographic pricing.

**📊 Area Chart — Avg. Total Unit Cost & Avg. Order Quantity by Product Name**

Plots the average total unit cost (left Y-axis, ranging ~1,300–1,500) against the average order quantity (right Y-axis, ranging ~8.2–8.8) for each product (Product 1 through Product 9+). The dual-axis design immediately surfaces which products carry high costs relative to their order volumes — critical for margin analysis and inventory prioritisation. Products with high cost but low order quantity are candidates for portfolio review.

**🗺️ Tree Map — Unit Price Divided by City and Suburb**

A richly coloured tree map covering all 100 regions, with rectangle size proportional to relative average unit price by suburb within each city. Key cities visible include Christchurch, Waitakere, Manukau, Wanganui, North Shore, Hamilton, Palmerston North, Whangarei, Auckland, Dunedin, Napier, and more. Darker or larger blocks indicate higher average pricing — immediately revealing premium markets and discount-heavy suburbs for localised pricing strategy.

---

### Page 2 — Yearly Sales Overview (2017–2019)

![Page 2 — Yearly Sales 2017-2019](./Dashboard-Screenshots/Page%202.png)

Three stacked area charts, one per year, each plotting **Max Revenue Month-wise** segmented by channel (Distributor = light blue, Export = dark blue, Wholesale = orange). Revenue consistently reaches ~0.2M monthly across all three years, with Wholesale being the dominant channel layer throughout. This view is ideal for year-over-year pattern comparison and spotting channel mix shifts across the full 3-year window.

**Key observations from this page:**
- **Wholesale (orange)** consistently occupies the top revenue band in all three years
- **Export (dark blue)** is the thinnest band, indicating it generates the lowest maximum monthly revenue of the three channels
- **2017** shows a notable revenue peak in **March** before tapering slightly mid-year
- **2018** shows relative stability with a slight uptick in **July–August**
- **2019** shows a gradual decline in the Distributor and Wholesale bands in the back half of the year

---

### Page 3 — 2017 Monthly Sales (Daily Granularity by Channel)

![Page 3 — 2017 Monthly Sales](./Dashboard-Screenshots/Page%203.png)

A 4×3 grid of 12 line charts — one per month — each showing **Max Revenue by Day** broken down by Distributor (light blue), Export (dark blue), and Wholesale (orange). Revenue peaks frequently reach **~50K** within individual months. The multi-chart layout enables month-by-month comparison of intra-month volatility and channel-specific daily spikes in a single glance.

**2017 Notable Patterns:**
- Daily revenue is volatile across all channels with frequent spikes to 50K+
- Wholesale and Distributor channels are tightly competitive throughout the year
- Export consistently tracks lower on a daily basis but occasionally spikes to match the others
- **January and December** show higher intra-month Distributor peaks, suggesting seasonal demand from this channel at year-start and year-end

---

### Page 4 — 2018 Monthly Sales (Daily Granularity by Channel)

![Page 4 — 2018 Monthly Sales](./Dashboard-Screenshots/Page%204.png)

Identical layout to Page 3 — 12 line charts for all months of 2018. Revenue peaks again reach ~50K at the daily level with similar channel volatility to 2017. This page allows direct visual comparison against the 2017 page to identify whether daily revenue patterns are becoming more or less volatile year-over-year.

**2018 Notable Patterns:**
- Wholesale channel shows more pronounced mid-month spikes compared to 2017, particularly in **May, June, and November**
- Distributor and Export channels show increased competition (lines crossing more frequently) in the second half of 2018
- **August** shows a noticeable Export channel spike, suggesting a one-off or seasonal export event

---

### Page 5 — 2019 Monthly Sales (Daily Granularity by Channel)

![Page 5 — 2019 Monthly Sales](./Dashboard-Screenshots/Page%205.png)

2019's daily-level charts show a visible shift: the three channel lines appear **closer together and more compressed** compared to 2017 and 2018, suggesting revenue convergence across channels. The 50K daily peak still occurs but less frequently, and the Export channel shows increased activity relative to prior years.

**2019 Notable Patterns:**
- Channel lines are noticeably tighter — less separation between Distributor, Export, and Wholesale
- **Export channel strengthens** relative to 2017–2018, closing the gap with Distributor and Wholesale
- **February** shows an unusually sharp spike in the Export channel, the largest single-month Export peak visible across all three years
- Revenue in later months of 2019 is visibly more compressed and lower on average, potentially signalling market saturation or data truncation

---

## 📈 Key KPIs at a Glance

| KPI | Value | What It Tells You |
|---|---|---|
| **Total Orders** | **7,991** | High-volume operation — nearly 8K transactions across the period |
| **Average Order Quantity** | **8.46 units** | Sits just below the bulk threshold of 9 — a key upsell lever |
| **Total Unique Customers** | **50** | Concentrated base: ~160 orders per customer on average |
| **Total Products** | **15** | Lean, focused product portfolio driving strong per-SKU demand |
| **Total Regions Served** | **100** | Wide geographic footprint across New Zealand |
| **Total Warehouses** | **4** | AXW291, FLR025, GUT930 + one more — compact fulfilment network |

---

## 💡 Key Analysis Insights

### 1. Wholesale is the Revenue Backbone — But Watch the Trend
Across all three yearly area charts, **Wholesale (orange)** consistently holds the highest revenue band. However, the 2019 daily charts show the channel gap narrowing, which warrants close monitoring. An over-dependence on one channel creates concentration risk.

### 2. Average Order Quantity is a Hair Below the Bulk Threshold
At **8.46 units per order**, the business is tantalizingly close to a natural bulk-buying cut-off (9+ units). A targeted nudge — a small incentive, tiered pricing, or minimum order promotion — could shift a meaningful share of orders over the threshold and lift average order value.

### 3. 50 Customers Generating ~8,000 Orders = Extreme Repeat-Buy Loyalty
With only 50 unique buyers placing 7,991 orders, each customer averages roughly **160 orders**. This is a deeply relationship-driven, likely B2B, buying model. The business's revenue health is almost entirely dependent on customer retention — losing even 2–3 key accounts would be material.

### 4. Export Channel is Gaining Ground in 2019
Across 2017 and 2018, Export (dark blue) is consistently the lowest revenue channel. But in 2019 — particularly February — Export shows the sharpest spike of any channel in any single month across the 3-year dataset. This could signal a new contract, market entry, or seasonal export event worth investigating for replication.

### 5. Geographic Pricing is Highly Uneven Across 100 Regions
The tree map reveals major price variation across New Zealand cities and their suburbs. Cities like **Christchurch, Waitakere, and Hamilton** occupy large blocks, indicating either high pricing or high transaction volume. Smaller or lower-colour blocks in outer suburbs may represent underpriced markets or discount-heavy accounts.

### 6. Product Cost vs. Demand Gaps Signal Margin Risk
The dual-axis area chart on Page 1 shows that unit cost (ranging ~1,300–1,500) and order quantity (ranging ~8.2–8.8) do not always move together. Products with rising unit cost but flat or declining order quantity are quietly eroding margins and should be flagged for pricing review or discontinuation.

### 7. Daily Revenue is Volatile — Wholesale Spikes Drive the Peaks
Across all 36 monthly line charts (Pages 3–5), the most extreme daily spikes (~50K) are consistently driven by the Wholesale channel, with Distributor occasionally competing. These spikes likely correspond to large single-order events (bulk restocking, promotions). Understanding and anticipating these events is key to inventory and cash-flow management.

---

## 💼 Business Benefits

| Benefit | Impact |
|---|---|
| **Single Source of Truth** | Replaces disconnected spreadsheets with one dashboard consolidating all dimensions: orders, channels, geography, products, and time |
| **Channel Strategy Clarity** | Real visibility into Wholesale dominance, Export growth, and Distributor trends — enabling channel investment decisions based on data, not intuition |
| **Bulk Order Opportunity** | Average quantity of 8.46 units reveals a specific, actionable upsell lever requiring only a small behavioural nudge to convert |
| **Customer Retention Focus** | 50-customer concentration makes every relationship critical — the dashboard supports proactive account monitoring |
| **Geographic Pricing Intelligence** | 100-region tree map identifies premium markets and potential pricing gaps across New Zealand cities and suburbs |
| **Seasonal & Daily Planning** | 36 monthly line charts (3 years × 12 months) enable proactive inventory, staffing, and promotional planning aligned with actual demand cycles |
| **Executive-Ready Design** | KPI cards and slicers mean non-technical stakeholders can self-serve answers without analyst involvement |

---

## 🔮 Future Scope

This dashboard is a strong analytics foundation. Here is how it can evolve into a production-grade business intelligence platform:

### 🔧 Technical Enhancements

- **Live Data Pipeline** — Connect Power BI to a SQL Server, Azure SQL Database, or cloud warehouse (Snowflake / BigQuery) for automated daily/weekly refresh, eliminating manual CSV imports entirely
- **Advanced DAX Measures** — Add Month-over-Month revenue growth %, Year-over-Year variance per channel, Rolling 12-Month Average Revenue, and Channel Market Share % to move from raw figures to trend intelligence
- **Row-Level Security (RLS)** — Restrict dashboard views so regional managers see only their city/suburb data and channel managers see only their channel — enabling secure, self-service access across the organisation
- **Power BI Service Deployment** — Publish to Power BI Service for browser-based and mobile access, automated email report subscriptions, and embedded analytics in internal business portals
- **Bookmarks & Navigation Buttons** — Add drill-through pages and back-navigation buttons so users can click from the yearly overview directly into any specific month's daily chart without manual tab navigation

### 📊 Analytics Extensions

- **Revenue Forecasting** — Integrate Power BI's native forecasting capability (or connect Python/R scripts) to project monthly revenue per channel for the next 6–12 months, based on the 3-year seasonality baseline already captured in the dashboard
- **Customer RFM Segmentation** — With 50 customers and ~8,000 orders, a Recency/Frequency/Monetary segmentation would classify accounts into VIP, at-risk, and lapsed tiers — enabling differentiated retention and upsell strategies
- **Gross Margin Analysis** — Layer in cost-of-goods-sold data per product and warehouse to calculate actual gross margin per channel, region, and SKU — shifting the dashboard from revenue reporting to profit-focused decision support
- **Cohort Analysis** — Track whether customers first ordering in a given month continue to order across subsequent months, revealing retention curves and identifying the point at which customer relationships typically weaken

### 🏢 Business & Integration Extensions

- **ERP / CRM Integration** — Connect Power BI to Salesforce, SAP, or Microsoft Dynamics 365 via native connectors to enrich sales data with pipeline stage, lead source, sales rep, and contract information, creating a unified commercial intelligence layer
- **Supplier & Procurement Linkage** — Extend the data model with supplier dimension tables to link customer order demand signals directly to procurement lead times — enabling demand-driven purchasing and reducing both overstock and stockout risk
- **Mobile-Optimised Report Layout** — Design a dedicated Power BI mobile report so field sales representatives can access live channel and regional KPIs from their phones during customer visits
- **Alerting & Anomaly Notifications** — Set Power BI data alerts on key KPIs (e.g., if daily Wholesale revenue drops below a threshold) to trigger automatic email or Teams notifications to relevant stakeholders
- **Cross-Domain Reuse** — The star schema architecture, channel-segmented time-series design, and geographic tree map pattern used in this project are directly reusable for e-commerce analytics, FMCG distribution, pharmaceutical supply chains, and logistics performance dashboards with minimal structural changes

---

## 📂 Project Files

```
SalesReport-Dashboard/
│
├── SalesReport.pbix                              # Main Power BI report file (open in Power BI Desktop)
├── SalesReport-Doc.docx                          # Full project documentation & visual descriptions
│
├── data/
│   ├── Screenshot_2026-05-14_at_11_37_10_AM.png      # Page 1 — KPI Overview & Product/Regional Analysis
│   ├── Screenshot_2026-05-14_at_11_38_03_AM.png      # Page 2 — Yearly Sales 2017–2019 by Channel
│   ├── Screenshot_2026-05-14_at_11_38_19_AM.png      # Page 3 — 2017 Monthly Sales (Daily by Channel)
│   └── Screenshot_2026-05-14_at_11_39_26_AM.png      # Page 4 — 2018 Monthly Sales (Daily by Channel)
│   └── Screenshot_2026-05-14_at_11_39_54_AM.png      # Page 5 — 2019 Monthly Sales (Daily by Channel)
│
└── README.md                                     # This file
```

---

## ▶️ How to Run

### Prerequisites
- [Power BI Desktop](https://powerbi.microsoft.com/desktop/) — free download, Windows only
- Dataset CSVs from the `data/` folder

### Steps

```bash
# 1. Clone this repository
git clone https://github.com/yanshiSharma/SalesReport-Dashboard.git
cd SalesReport-Dashboard

# 2. Open Power BI Desktop

# 3. Open the report
#    File → Open Report → select SalesReport.pbix

# 4. Update data source paths if prompted
#    Home → Transform Data → Data Source Settings
#    Update file paths to point to your local data/ folder

# 5. Click Refresh on the Home ribbon to load data

# 6. Navigate pages using the tabs at the bottom of the report
#    Page 1: Use the slicers (Channel, City, Warehouse, Suburb) to filter all visuals interactively
#    Pages 2–5: Review yearly and monthly revenue trends by channel
```

### Publish to Power BI Service (Optional)
```
1. Sign in to Power BI Desktop with a Microsoft work or school account
2. Home → Publish → select your target workspace
3. Open the published report at https://app.powerbi.com
4. Configure scheduled data refresh under Dataset Settings
```

---

## 👩‍💻 Author

**Yanshi Sharma**

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?logo=linkedin&logoColor=white)](https://linkedin.com/in/yanshi-sharma)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-181717?logo=github&logoColor=white)](https://github.com/yanshiSharma)

> *Open to Data Analyst, Business Intelligence Analyst, and Reporting Analyst roles. Feel free to connect!*

---

<div align="center">

⭐ **If you found this project useful, please give it a star!** ⭐

*Built with Power BI · DAX · Star Schema Design · 3-Year Sales Data · New Zealand Market*

</div>
