# 📊 Padanjaly E-Commerce Analytics — Power BI Portfolio Project

## 🧾 Project Overview

This project presents an end-to-end **Power BI analytics solution** for **Padanjaly E-Commerce**, an Ayurvedic products business.  
The dashboard analyzes product demand, sales performance, geographic distribution, and e-commerce customer behaviour to support inventory planning, revenue optimization, and business decision-making.

The project includes four interconnected dashboards:

1. **Product Demand Dashboard**
2. **Sales Geography Dashboard**
3. **Sales Performance Dashboard**
4. **E-Commerce Analytics Dashboard**

The report uses a clean and consistent visual theme:

- Mint-green headers and accents  
- Bright-blue charts and KPI values  
- Light-gray background  
- Rounded visual containers with subtle shadows  
- Consistent INR currency formatting  
- Trend and insight text beneath key visuals  

---

## 🎯 Business Objective

The main objective is to understand:

- Which products generate the highest demand and revenue  
- How sales performance changes monthly and yearly  
- Which locations contribute most to sales  
- How customers move through the e-commerce purchase funnel  
- Where the business can improve inventory planning, marketing, and conversion  

---

## 📁 Project Files

| File | Description |
|---|---|
| File                                                    | Description                                    |
| -----------------------------------------------------   | ---------------------------------------------- |
| README.md                                               | Project overview and calculation documentation |
| '-customer-PBIX-dashboard--padanjaly Copy.pdf'          | Customer dashboard PDF                         |
| 'customer-PBIX-dashboard--padanjaly.pbix'               | Customer dashboard Power BI report             |
| 'padanjaly-order-cleaning-dashboard-POwer.pbix'         | Order / sales dashboard Power BI report        |
| 'padanjaly-order-cleaning-dashboard-pdf.pdf'            | Order / sales dashboard PDF                    |
| 'product--dashboard--padanjaly.pdf'                     | Product demand dashboard PDF                   |
| 'product-PBIX-dashboard--padanjaly.pbix'                | Product demand Power BI report                 |
| 'updated-padanjaly--dashboard-Sales-geography Copy.pdf' | Sales geography dashboard PDF                  |
| 'updated-padanjaly--dashboard-Sales-geography.pbix'     | Sales geography Power BI report                |
---

## 🧱 Data Model

The data model is designed around a sales fact table and supporting dimension tables.

### Fact Table

**Sales / Orders**

| Column | Description |
|---|---|
| Order ID | Unique order identifier |
| Order Date | Date of transaction |
| Product Name | Product sold |
| Category | Product category |
| Quantity | Units sold |
| Unit Price | Price per unit |
| Subtotal / Revenue | Revenue generated |
| State / City | Customer location |
| Traffic Source | Website acquisition channel |
| Device | Customer device type |

### Dimension Tables

| Table | Purpose |
|---|---|
| `Products` | Product details, category, and packaging |
| `Calendar` | Date, month, quarter, and year analysis |
| `Geography` | State, city, and regional analysis |
| `Measures` | Central table for all DAX measures |

A dedicated measures table keeps calculation logic separate from raw data, improving maintainability and reusability. [4]

---

## 📈 Dashboard 1 — Product Demand Dashboard

### Key Metrics

| KPI | Value |
|---|---:|
| Total Products | 11 |
| Total Quantity | 1.08K |
| Top Quantity Product | Agnijith 90 gms |
| Top Revenue Product | Agnijith 90 gms |

### Visuals

| Visual | Purpose |
|---|---|
| Monthly Product Demand — Line Chart | Tracks monthly quantity from January 2023 to July 2026 |
| Top 10 Products by Quantity — Column Chart | Identifies highest-selling products |
| Yearly Product Demand — Area Chart | Shows annual demand growth |
| Product Quantity vs Revenue — Scatter Chart | Compares sales volume with revenue contribution |

### Product Demand Insights

- **Agnijith 90 gms** is the leading product with **508 units sold**.
- **Agnihari 90gms** is the second-best seller with **252 units**.
- Demand increased from **110 units in 2023** to **364 units in 2025**.
- 2026 recorded **363 units**, though the data covers only part of the year.
- High-demand products should be prioritized in inventory planning.

---

## 🗺️ Dashboard 2 — Sales Geography Dashboard

### Purpose

This dashboard identifies where Padanjaly products are selling and which locations generate the strongest demand.

### Visuals

| Visual | Purpose |
|---|---|
| Sales Map | Shows geographic distribution of sales |
| Sales by State | Compares state-level performance |
| Top Cities by Revenue | Highlights high-value customer locations |
| Product Performance by Region | Identifies regional product preferences |
| Monthly Geographic Trend | Tracks location-based demand over time |

### Geography Insights

- Identify high-performing states and cities for targeted marketing.
- Use regional demand patterns to plan stock allocation.
- Detect locations with strong traffic but low conversion.
- Support delivery, logistics, and regional campaign planning.

---

## 💰 Dashboard 3 — Sales Performance Dashboard

### Purpose

This dashboard measures overall revenue performance, product contribution, and sales trends.

### Visuals

| Visual | Purpose |
|---|---|
| Monthly Revenue Trend | Tracks revenue movement over time |
| Revenue by Product | Identifies top revenue-generating products |
| Top 10 Products by Revenue | Highlights best-performing products |
| Quantity vs Revenue | Compares volume with revenue contribution |
| Year-over-Year Sales | Measures annual growth |

### Sales Insights

- Revenue generally increases with product quantity.
- **Agnijith 90 gms** leads both quantity and revenue.
- Lower-volume products may need improved visibility, bundling, or promotional support.
- Year-over-year comparison helps assess sustainable growth.

---

## 🛒 Dashboard 4 — E-Commerce Analytics Dashboard

### Purpose

This dashboard analyzes website and purchase behaviour to identify conversion opportunities.

### Visuals

| Visual | Purpose |
|---|---|
| Website Traffic Trend | Tracks users or sessions over time |
| Conversion Funnel | Shows product view → add to cart → checkout → purchase |
| Revenue by Traffic Source | Identifies highest-value acquisition channels |
| Device Performance | Compares mobile, desktop, and tablet behaviour |
| Customer Location Analysis | Connects geography with online demand |

### E-Commerce Insights

- A high volume of product views with fewer purchases indicates a conversion gap.
- Traffic source analysis helps identify the most profitable marketing channels.
- Funnel analysis reveals where customers drop off before completing a purchase.
- Device-level analysis can identify mobile usability or checkout issues.

---

## 🧮 DAX Measures

All measures are stored in a dedicated `Measures` table.  
They are written as explicit DAX measures so they respond correctly to report filters, slicers, and visual context. [6][12]

> Replace table and column names such as `Sales`, `Products`, `Orders`, and `Calendar` with the exact names used in your Power BI model.

### 1. Core Sales Measures

```DAX
Total Quantity =
SUM ( Sales[Quantity] )
```

```DAX
Total Revenue =
SUM ( Sales[Subtotal] )
```

```DAX
Total Products =
DISTINCTCOUNT ( Sales[Product Name] )
```

```DAX
Total Orders =
DISTINCTCOUNT ( Sales[Order ID] )
```

```DAX
Average Order Value =
DIVIDE (
    [Total Revenue],
    [Total Orders],
    0
)
```

```DAX
Average Quantity per Order =
DIVIDE (
    [Total Quantity],
    [Total Orders],
    0
)
```

```DAX
Average Revenue per Product =
AVERAGEX (
    VALUES ( Sales[Product Name] ),
    [Total Revenue]
)
```

---

### 2. Product Performance Measures

```DAX
Top Quantity Product =
MAXX (
    TOPN (
        1,
        VALUES ( Sales[Product Name] ),
        [Total Quantity],
        DESC
    ),
    Sales[Product Name]
)
```

```DAX
Top Revenue Product =
MAXX (
    TOPN (
        1,
        VALUES ( Sales[Product Name] ),
        [Total Revenue],
        DESC
    ),
    Sales[Product Name]
)
```

```DAX
Top Product Quantity =
MAXX (
    VALUES ( Sales[Product Name] ),
    [Total Quantity]
)
```

```DAX
Top Product Revenue =
MAXX (
    VALUES ( Sales[Product Name] ),
    [Total Revenue]
)
```

```DAX
Product Quantity Rank =
RANKX (
    ALL ( Sales[Product Name] ),
    [Total Quantity],
    ,
    DESC,
    DENSE
)
```

```DAX
Product Revenue Rank =
RANKX (
    ALL ( Sales[Product Name] ),
    [Total Revenue],
    ,
    DESC,
    DENSE
)
```

```DAX
Top 10 Products Quantity =
CALCULATE (
    [Total Quantity],
    TOPN (
        10,
        ALL ( Sales[Product Name] ),
        [Total Quantity],
        DESC
    )
)
```

```DAX
Top 10 Products Revenue =
CALCULATE (
    [Total Revenue],
    TOPN (
        10,
        ALL ( Sales[Product Name] ),
        [Total Revenue],
        DESC
    )
)
```

---

### 3. Time Intelligence Measures

These measures require a marked date table named `Calendar`, related to `Sales[Order Date]`.

```DAX
Total Revenue LY =
CALCULATE (
    [Total Revenue],
    SAMEPERIODLASTYEAR ( Calendar[Date] )
)
```

```DAX
Total Quantity LY =
CALCULATE (
    [Total Quantity],
    SAMEPERIODLASTYEAR ( Calendar[Date] )
)
```

```DAX
Revenue YoY Growth % =
DIVIDE (
    [Total Revenue] - [Total Revenue LY],
    [Total Revenue LY],
    0
)
```

```DAX
Quantity YoY Growth % =
DIVIDE (
    [Total Quantity] - [Total Quantity LY],
    [Total Quantity LY],
    0
)
```

```DAX
Revenue MoM Growth % =
VAR CurrentRevenue = [Total Revenue]
VAR PreviousRevenue =
    CALCULATE (
        [Total Revenue],
        DATEADD ( Calendar[Date], -1, MONTH )
    )
RETURN
DIVIDE (
    CurrentRevenue - PreviousRevenue,
    PreviousRevenue,
    0
)
```

```DAX
Quantity MoM Growth % =
VAR CurrentQuantity = [Total Quantity]
VAR PreviousQuantity =
    CALCULATE (
        [Total Quantity],
        DATEADD ( Calendar[Date], -1, MONTH )
    )
RETURN
DIVIDE (
    CurrentQuantity - PreviousQuantity,
    PreviousQuantity,
    0
)
```

```DAX
Revenue YTD =
TOTALYTD (
    [Total Revenue],
    Calendar[Date]
)
```

```DAX
Quantity YTD =
TOTALYTD (
    [Total Quantity],
    Calendar[Date]
)
```

```DAX
Revenue MTD =
TOTALMTD (
    [Total Revenue],
    Calendar[Date]
)
```

---

### 4. Geography Measures

```DAX
Total States =
DISTINCTCOUNT ( Sales[State] )
```

```DAX
Total Cities =
DISTINCTCOUNT ( Sales[City] )
```

```DAX
Top State by Revenue =
MAXX (
    TOPN (
        1,
        VALUES ( Sales[State] ),
        [Total Revenue],
        DESC
    ),
    Sales[State]
)
```

```DAX
Top City by Revenue =
MAXX (
    TOPN (
        1,
        VALUES ( Sales[City] ),
        [Total Revenue],
        DESC
    ),
    Sales[City]
)
```

```DAX
Top State Revenue =
MAXX (
    VALUES ( Sales[State] ),
    [Total Revenue]
)
```

```DAX
Top City Revenue =
MAXX (
    VALUES ( Sales[City] ),
    [Total Revenue]
)
```

```DAX
State Revenue Contribution % =
DIVIDE (
    [Total Revenue],
    CALCULATE (
        [Total Revenue],
        ALL ( Sales[State] )
    ),
    0
)
```

```DAX
City Revenue Contribution % =
DIVIDE (
    [Total Revenue],
    CALCULATE (
        [Total Revenue],
        ALL ( Sales[City] )
    ),
    0
)
```

---

### 5. E-Commerce Funnel Measures

```DAX
Product Views =
CALCULATE (
    COUNTROWS ( Sales ),
    Sales[Event Type] = "view_product"
)
```

```DAX
Add to Cart =
CALCULATE (
    COUNTROWS ( Sales ),
    Sales[Event Type] = "add_to_cart"
)
```

```DAX
Checkout Started =
CALCULATE (
    COUNTROWS ( Sales ),
    Sales[Event Type] = "checkout_start"
)
```

```DAX
Purchases =
CALCULATE (
    COUNTROWS ( Sales ),
    Sales[Event Type] = "purchase"
)
```

```DAX
Conversion Rate % =
DIVIDE (
    [Purchases],
    [Product Views],
    0
)
```

```DAX
Add-to-Cart Rate % =
DIVIDE (
    [Add to Cart],
    [Product Views],
    0
)
```

```DAX
Checkout Completion Rate % =
DIVIDE (
    [Purchases],
    [Checkout Started],
    0
)
```

```DAX
Cart Abandonment Rate % =
DIVIDE (
    [Checkout Started] - [Purchases],
    [Checkout Started],
    0
)
```

---

### 6. Traffic and Device Measures

```DAX
Total Sessions =
DISTINCTCOUNT ( Sales[Session ID] )
```

```DAX
Total Users =
DISTINCTCOUNT ( Sales[User ID] )
```

```DAX
Revenue per User =
DIVIDE (
    [Total Revenue],
    [Total Users],
    0
)
```

```DAX
Revenue per Session =
DIVIDE (
    [Total Revenue],
    [Total Sessions],
    0
)
```

```DAX
Top Traffic Source =
MAXX (
    TOPN (
        1,
        VALUES ( Sales[Traffic Source] ),
        [Total Revenue],
        DESC
    ),
    Sales[Traffic Source]
)
```

```DAX
Top Device =
MAXX (
    TOPN (
        1,
        VALUES ( Sales[Device] ),
        [Total Revenue],
        DESC
    ),
    Sales[Device]
)
```

```DAX
Mobile Revenue % =
DIVIDE (
    CALCULATE (
        [Total Revenue],
        Sales[Device] = "Mobile"
    ),
    [Total Revenue],
    0
)
```

---

## 🧠 Key DAX Functions Used

| Function | Purpose |
|---|---|
| `SUM` | Adds numeric values such as quantity or revenue |
| `DISTINCTCOUNT` | Counts unique products, orders, users, states, or cities |
| `DIVIDE` | Performs safe division and handles divide-by-zero cases |
| `CALCULATE` | Changes filter context for targeted calculations |
| `FILTER` | Applies row-level conditions |
| `TOPN` | Returns top-performing products, cities, or channels |
| `RANKX` | Ranks products by quantity or revenue |
| `MAXX` | Returns the highest value from an iterated table |
| `VALUES` | Returns distinct values in the current filter context |
| `SAMEPERIODLASTYEAR` | Compares performance with the same period last year |
| `DATEADD` | Shifts dates for month-over-month calculations |
| `TOTALYTD` | Calculates year-to-date totals |
| `TOTALMTD` | Calculates month-to-date totals |

`DIVIDE` is preferred over the `/` operator because it safely manages zero or blank denominators. [9]  
`AVERAGEX` and `VALUES` are useful when calculating averages across orders or products rather than simply averaging raw rows. [10]

---

## 📌 Key Business Recommendations

1. **Prioritize inventory for best sellers**  
   Maintain stronger stock levels for **Agnijith 90 gms** and **Agnihari 90gms**, which drive the majority of product demand.

2. **Investigate demand spikes**  
   Analyze months with unusually high demand to understand promotions, seasonality, or repeat purchase behaviour.

3. **Improve low-demand product visibility**  
   Use bundles, recommendations, and homepage placement to increase exposure for lower-selling products.

4. **Optimize the purchase funnel**  
   Track product views, add-to-cart actions, checkout starts, and completed purchases to identify drop-off points.

5. **Target high-performing regions**  
   Focus marketing and delivery planning on states and cities with the highest revenue contribution.

6. **Use mobile-first optimization**  
   If mobile traffic is high but conversion is low, improve mobile page speed, product-page clarity, and checkout usability.

---

## 🏁 Project Outcome

This Power BI project converts raw sales and e-commerce data into clear, actionable insights.  
It helps Padanjaly understand product demand, monitor revenue performance, identify geographic opportunities, and improve online conversion.

The dashboards provide a practical foundation for data-driven decisions in:

- Inventory planning  
- Sales strategy  
- Regional marketing  
- Product promotion  
- E-commerce conversion optimization  
