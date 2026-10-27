# Padanjaly Sales Performance & Geography Dashboard

A Power BI project analyzing 690 WooCommerce orders for Padanjaly Ayurveda to understand sales performance, product trends, order status, and geographic distribution.

## Overview

Built two Power BI dashboards using Power Query and DAX:

- **Sales Performance:** Revenue trends, product sales, order status, and KPI-cards.
- **Sales Geography:** State-wise Sales Contribution , Geographical Sales Distribution Across States, Order Distribution by Country, Annual Sales Trend, Top 10 Country by Sales  and Domestic vs International Share of Sales.

## Project Files

| File | Description |
|---|---|
| `padanjaly-order-cleaning-dashboard-POwer.pbix` | Sales Performance Dashboard |
| `padanjaly-order-cleaning-dashboard-pdf.pdf` | Sales dashboard PDF |
| `updated-padanjaly--dashboard-Sales-geography.pbix` | Sales Geography Dashboard |
| `updated-padanjaly--dashboard-Sales-geography Copy.pdf` | Geography dashboard PDF |

## Key Findings

- **Total sales:** Approximately ₹1.5M and $18.2K, reported separately.
- **Total orders:** 690, with 405 completed and 285 processing.
- **Sales trend:** Revenue increased from ₹0.08M in 2023 to ₹0.53M in 2025, reaching ₹0.42M through July 2026.
- **Top product:** Agnijith 90 gms generated approximately ₹0.93M in sales.
- **Geography:** Kerala leads the visible state-wise sales chart at approximately ₹0.39M.
- **Order distribution:** International orders account for 11.74%, while domestic orders account for 88.26%.

## Data Preparation

- Cleaned and standardized product, state, country, and payment fields.
- Prepared date fields for time-based analysis.
- Separated zero-value test orders for traceability.
- Kept INR and USD sales separate.

## DAX Measures

### Total Orders
```dax
Total Orders = DISTINCTCOUNT('padanjaly-order export0 csv'[order_id])
```

### Total Sales INR
```dax
Total Sales INR = SUM('padanjaly-order export0 csv'[order_subtotal])
```

### Total Sales USD
```dax
Total Sales USD = 
VAR Rate = FIRSTNONBLANK('padanjaly-order export0 csv'[usd_inr_rate], 1)
RETURN DIVIDE([Total Sales INR], Rate)
```

### International Share %
```dax
International Share % = 
DIVIDE ( [International Orders], [Total Orders] )
```

### Domestic Share %
```dax
Domestic Share % = 1 - [International Share %]
```

*Note: The international and domestic measures calculate order shares, not sales revenue shares. Validate the USD conversion rate methodology before relying on the converted total.*

## Business Recommendations

1. Review processing orders and investigate delays.
2. Analyze peak sales months to identify successful campaigns.
3. Promote multipacks and combo products to diversify revenue.
4. Use geographic insights to prioritize key markets.
5. Explore opportunities to grow international orders.

## Tools & Technologies

- Microsoft Power BI
- Power Query
- DAX
- WooCommerce
- Data Cleaning and Visualization

## Limitations

Dashboard figures have not been independently audited. The 2026 data covers January through July, so it is a partial-year comparison. KPI values and currency conversions should be validated against the Power BI model.
