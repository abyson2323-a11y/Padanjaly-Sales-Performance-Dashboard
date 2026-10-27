# Padanjaly Business Intelligence Dashboard Suite

A Power BI project analyzing WooCommerce data for Padanjaly Ayurveda to understand sales performance, product demand, and geographic sales distribution. The project includes three interactive dashboards developed using Microsoft Power BI, Power Query, and DAX.

## Project Overview

This project transforms WooCommerce data into interactive dashboards to support business analysis and data-driven decision-making.

The project contains three dashboards:

### 1. Sales Performance Dashboard

Analyzes overall sales performance, revenue trends, product sales, order status, and key business metrics.

**Key areas:**
- Total sales and order KPIs
- Revenue trends over time
- Product sales performance
- Order status distribution
- Annual sales comparison

### 2. Sales Geography Dashboard

Analyzes the geographic distribution of sales across domestic and international markets.

**Key areas:**
- State-wise sales contribution
- Geographic sales distribution across states
- Order distribution by country
- Annual sales trends
- Top 10 countries by sales
- Domestic versus international share of orders

### 3. Product Demand Dashboard

Analyzes product-level demand, quantity sold, monthly trends, and the relationship between product quantity and revenue.

**Key areas:**
- Total products and total quantity
- Monthly product demand from January 2023 to July 2026
- Top 10 products by quantity
- Yearly product demand
- Product quantity versus revenue
- Top-performing products by quantity and revenue

## Project Files

| File | Description |
|---|---|
| `padanjaly-order-cleaning-dashboard-POwer.pbix` | Sales Performance Dashboard |
| `padanjaly-order-cleaning-dashboard-pdf.pdf` | Sales Performance Dashboard PDF |
| `updated-padanjaly--dashboard-Sales-geography.pbix` | Sales Geography Dashboard |
| `updated-padanjaly--dashboard-Sales-geography Copy.pdf` | Sales Geography Dashboard PDF |
| `product-PBIX-dashboard--padanjaly.pbix` | Product Demand Dashboard |
| `product--dashboard--padanjaly.pdf` | Product Demand Dashboard PDF |

The `.pbix` files contain the Power BI reports, while the PDF files provide exported dashboard views.

## Key Findings

### Sales Performance

- **Total orders:** 690 orders analyzed.
- **Order status:** 405 completed orders and 285 processing orders.
- **Sales performance:** Revenue increased from approximately ₹0.08 million in 2023 to ₹0.53 million in 2025.
- **2026 sales:** Approximately ₹0.42 million through July 2026.
- **Top product:** Agnijith 90 gms generated approximately ₹0.93 million in sales.
- **Currency reporting:** INR and USD sales are reported separately.

### Sales Geography

- **Leading state:** Kerala, with approximately ₹0.39 million in sales in the visible state-wise chart.
- **Domestic orders:** 88.26% of total orders.
- **International orders:** 11.74% of total orders.
- **Geographic analysis:** The dashboard compares state and country performance to identify important sales markets.

### Product Demand

- **Total products:** 11.
- **Total quantity:** Approximately 1.08K units.
- **Top quantity product:** Agnijith 90 gms, with 508 units.
- **Second-highest quantity product:** Agnihari Kasmeerini 90gms, with 252 units.
- **Top revenue product:** Agnijith 90 gms.

**Yearly product demand:**

| Year | Quantity |
|---|---:|
| 2023 | 110 |
| 2024 | 243 |
| 2025 | 364 |
| 2026 (through July) | 363 |

Product demand increased substantially between 2023 and 2025. The 2026 figure represents only a partial year and should not be interpreted as a full-year comparison.

## Data Preparation

Data preparation and transformation were performed to improve consistency and support reliable reporting.

- Cleaned and standardized product, state, country, and payment fields.
- Prepared date fields for monthly and yearly analysis.
- Separated zero-value test orders for traceability.
- Kept INR and USD sales separate in the sales analysis.
- Prepared product-level information for demand and revenue comparisons.
- Used Power Query to transform data for reporting and visualization.

## DAX Measures

The following examples illustrate key measures used in the sales analysis. Table and column names must match the actual Power BI model.

### Total Orders

```dax
Total Orders =
DISTINCTCOUNT(
    'padanjaly-order export0 csv'[order_id]
)
```

### Total Sales INR

```dax
Total Sales INR =
SUM(
    'padanjaly-order export0 csv'[order_subtotal]
)
```

### Total Sales USD

```dax
Total Sales USD =
VAR Rate =
    FIRSTNONBLANK(
        'padanjaly-order export0 csv'[usd_inr_rate],
        1
    )
RETURN
    DIVIDE(
        [Total Sales INR],
        Rate
    )
```

*Note: Validate the exchange-rate methodology and currency-specific totals before using the converted figures for financial reporting.*

### International Share %

```dax
International Share % =
DIVIDE(
    [International Orders],
    [Total Orders]
)
```

### Domestic Share %

```dax
Domestic Share % =
1 - [International Share %]
```

### Average Quantity per Order

```dax
Average Quantity per Order =
DIVIDE(
    SUM('full_Product'[Quantity]),
    DISTINCTCOUNT('full_Product'[order_id]),
    0
)
```

### Most Sold Product

```dax
Most Sold Product =
VAR ProductSales =
    TOPN(
        1,
        SUMMARIZE(
            'full_Product',
            'full_Product'[Name],
            "TotalQty",
            SUM('full_Product'[Quantity])
        ),
        [TotalQty], DESC,
        'full_Product'[Name], ASC
    )
RETURN
    CONCATENATEX(
        ProductSales,
        'full_Product'[Name],
        ", "
    )
```

These are representative measures from the project analysis, not a complete list of every measure in the three reports.

## Business Recommendations

1. **Monitor processing orders:** Review pending and processing orders to identify delays and improve fulfillment.
2. **Investigate sales peaks:** Analyze high-performing months to identify potential campaign, seasonal, or market-related drivers.
3. **Maintain best-selling products:** Prioritize inventory planning for Agnijith 90 gms and other high-demand products.
4. **Improve lower-demand products:** Evaluate product positioning, pricing, and promotion opportunities.
5. **Prioritize geographic markets:** Use state and country performance to guide marketing and distribution decisions.
6. **Explore international growth:** Investigate opportunities to increase international orders while monitoring fulfillment and market requirements.
7. **Track performance consistently:** Update dashboards regularly to monitor sales, demand, and geographic trends.

## Tools & Technologies

- Microsoft Power BI
- Power Query
- DAX (Data Analysis Expressions)
- WooCommerce data
- Data Cleaning and Transformation
- KPI Development
- Data Visualization
- Sales and Product Demand Analysis

## Limitations

- Dashboard figures have not been independently audited.
- The 2026 sales and demand figures cover January through July, representing partial-year data.
- INR and USD sales are reported separately; currency conversion should be validated before financial comparisons.
- Domestic and international percentages represent order shares, not sales revenue shares.
- Geographic findings reflect the values displayed in the dashboard and should be checked against the underlying dataset before making business decisions.
- The reported product quantities and sales values should be validated against the final Power BI model.

## Project Objective

The objective of this project is to demonstrate practical business intelligence skills by converting WooCommerce data into useful insights about sales performance, product demand, and geographic distribution.

The three dashboards provide complementary perspectives on business performance and demonstrate the application of data cleaning, data modeling, DAX calculations, and interactive visualization using Power BI.
