# Padanjaly Sales Performance Dashboard

Sales performance, customer and market analysis for Padanjaly Ayurveda (Power BI dashboard and final report).

<img width="1320" height="797" alt="Sales Performance Dashboard" src="https://github.com/user-attachments/assets/48deb9d4-7ddd-475b-80fb-5645ecc7cf00" />

## Overview

Padanjaly Ayurveda sells Ayurvedic products online (mainly Agnijith and Agnihari creams) through a WooCommerce store. This project turns 690 orders into a Power BI sales dashboard and a combined business report. The report brings together four sources: the sales dashboard report, the Agnijith product and market research, the WooCommerce data-cleaning report, and the customer project report.

## Deliverables

| Folder / file | Description |
|---|---|
| [`powerbi/Padanjaly_Sales_Dashboard.pbix`](powerbi/Padanjaly_Sales_Dashboard.pbix) | Power BI working file: data model, Power Query steps, DAX measures and dashboard |
| [`powerbi/Dashboard_Export.pdf`](powerbi/Dashboard_Export.pdf) | PDF export of the final dashboard |
| [`reports/Padanjaly_Final_Report_v2.pdf`](reports/Padanjaly_Final_Report_v2.pdf) | Final 5-page business report (best for reading) |
| [`reports/Padanjaly_Final_Report_v2.docx`](reports/Padanjaly_Final_Report_v2.docx) | Editable Word version of the final report |
| [`source-reports/`](source-reports/) | The reports the final report is built from (see below) |
| [`images/dashboard.jpg`](images/dashboard.jpg) | Dashboard screenshot |

### Source reports

| File | Content |
|---|---|
| `DA-003_WooCommerce_Data_Cleaning_Report.docx` | Data cleaning and quality report (7 cleaning steps, 690 records, 688 after cleaning) |
| `Padanjaly_Sales_Performance_Report_2_Page.docx` | 2-page summary of the Power BI dashboard (KPIs, trends, validation checks) |
| `Padanjaly_Ayurveda_Project_Report_Abyson.docx` | Customer analysis and business recommendations |

## Key findings

- **Sales:** ₹1.5M (INR) and $18.2K (USD) from 690 orders; average order about ₹2,145.
- **Growth:** about 0.08M (2023), 0.41M (2024), 0.53M (2025) and 0.42M for 2026 to July. Big peaks in January and April/May 2026 point to campaign-driven sales.
- **One product carries the business:** Agnijith 90 g is about 62% of sales (0.93M); the next product is 0.15M.
- **Order status:** 405 orders completed (58.7%), 285 still processing (41.3%).
- **Customers:** 324 unique customers; 93.2% bought once and the repeat rate is 6.8%. About half of orders are guest orders. B2B is 10% of orders, with a higher average order value (₹2,380 vs ₹2,126).
- **Payments:** 99.1% prepaid (mainly Razorpay); cash on delivery is under 1%.
- **Markets:** India 88.3% of orders (Kerala 34.2% of all orders); international 11.7%, led by the USA, UK, Australia and UAE.

## Data

- Source: WooCommerce order export, 690 records (688 after removing 2 duplicate order IDs).
- Cleaning: guest flags, standardised states, countries, payments and product names, date and time split, zero-value test orders separated, and raw data kept for traceability.
- INR and USD are reported separately and are not added together.

## Power BI Model

- **Data table:** `padanjaly-order export0 csv`
- **Measures table:** `Rates` (holds all five KPI measures)
- **Page 1:** KPI cards, revenue trend by year/quarter/month, order-status donut, top 10 products by sales, yearly sales by product, billing-country map, with a trend and an insight written under each chart
- **Page 2:** Total Sales INR by order date (KPI visual)

## KPI Definitions and Validation

All five KPI measures are in the `Rates` table of the Power BI model. The dashboard values below match the report.

| KPI | Dashboard value | Definition (DAX) | Status |
|---|---|---|---|
| Total Sales INR | ₹1.5M | `<paste DAX>` | To confirm |
| Total Sales USD | $18.2K | `<paste DAX>` | To confirm |
| Product 1 Sales | 1.25M | `<paste DAX>` | To confirm |
| Total Orders | 690 | `<paste DAX>` | To confirm |
| Avg Order Value | 2.15K | `<paste DAX>` | To confirm |

Assumptions to confirm in the model:
- INR and USD sales are kept separate and never added together.
- Total Orders counts distinct order IDs.
- Orders in "processing" status (285 of 690) are included in total sales.
- Data runs through July 2026, so 2026 is a partial year.

## Report contents

1. Executive summary
2. Data cleaning
3. Sales dashboard and KPIs
4. Revenue trend
5. Product performance
6. Orders and payments
7. Customers
8. Markets and geography, website and pricing
9. Where the source reports disagree
10. Recommendations
11. Expected impact (illustrative)
12. Conclusion

## Recommendations (summary)

1. **0 to 30 days:** clear the 285 processing orders; run a day-35 repeat-purchase offer; test an Agnijith + Agnihari combo; fix website currency, booking button and health-claim wording; pilot COD in Kerala.
2. **1 to 3 months:** repeat the early-2026 campaign approach; test subscriptions, B2B discounts and a loyalty programme.
3. **3 to 12 months:** build an international storefront; test advertising focus on the top product and top states; test pack-size tiers.

## Open issues

- order count (690 on the dashboard vs 688 after cleaning)
- period covered (2023 to 2025 in one report, through July 2026 on the dashboard)
- revenue counted from all orders, including those still processing
- pack sizes (25 g on the website vs a proposed 45 g trial pack)

## Tools

Microsoft Power BI, Power Query, DAX, WooCommerce data export.

## Notes

Figures from the supplied reports have not been independently verified. The website's health claims and review rating are unverified. This is not a sales audit or medical assessment.
