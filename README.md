# Padanjaly Sales Performance Dashboard

Power BI sales dashboard for Padanjaly Ayurveda, built from 690 WooCommerce orders.

<img width="1320" height="797" alt="Sales Performance Dashboard" src="https://github.com/user-attachments/assets/48deb9d4-7ddd-475b-80fb-5645ecc7cf00" />

## Overview

Padanjaly Ayurveda sells Ayurvedic products online (mainly Agnijith and Agnihari creams) through a WooCommerce store. This project cleans the order export and turns it into a Power BI dashboard covering revenue, products, order status and billing countries. Each chart has a short trend and insight written under it.

## Deliverables

| File | Description |
|---|---|
| `padanjaly-order-cleaning-dashboard-POwer.pbix` | Power BI working file containing the data model, Power Query steps, DAX measures, and dashboard |
| `Dashboard_Export.pdf` | PDF export of the final dashboard |
| `padanjaly-order--dashboard-location-geography.pbix` | Power BI dashboard focused on sales geography and location analysis |
| `padanjaly-order--dashboard-location-geography.pdf` | PDF export of the Sales Geography Dashboard |

## Dashboard findings

- **Sales:** ₹1.5M (INR) and $18.2K (USD) from 690 orders; average order value 2.15K.
- **Growth:** about 0.08M (2023), 0.41M (2024), 0.53M (2025) and 0.42M for 2026 to July. Peaks of 101K in January and 125K around April/May 2026 point to campaign-driven sales, followed by dips to 18K to 26K.
- **One product carries the business:** Agnijith 90 gms is 0.93M (about 62% of sales); the next product is 0.15M and eight products are below 0.07M.
- **Order status:** 405 orders completed (58.7%) and 285 processing (41.3%).
- **Geography:** billing orders come from India, the USA, UK, UAE, Europe and Australia; USD sales are only $18.2K.

## Data

- Source: WooCommerce order export (690 records).
- Cleaning: guest flags, standardised states, countries, payments and product names, date and time split, zero-value test orders separated, and raw data kept for traceability.
- INR and USD are reported separately and are not added together.

## Power BI Model

- **Data table:** `padanjaly-order export0 csv`
- **Measures table:** `Rates` (holds all five KPI measures)
- **Page 1:** KPI cards, revenue trend by year/quarter/month, order-status donut, top 10 products by sales, yearly sales by product, billing-country map
- **Page 2:** Total Sales INR by order date (KPI visual)

## KPI Definitions and Validation

All five KPI measures are in the `Rates` table of the Power BI model.

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

## Business insights from the dashboard

1. Clear the 285 processing orders (about ₹6 lakh, estimate) to unlock revenue.
2. Repeat the January and April/May 2026 campaign approach to avoid dips.
3. Reduce single-product risk: push the Agnijith 5-Pack and combo packs to build a second hero product.
4. Bring back combo packs and multi-packs; 2025 had the best product mix and 2026 has less variety.
5. Test a 5-pack bundle for the international (NRI) market, since USD sales are low.

## Tools

Microsoft Power BI, Power Query, DAX, WooCommerce data export.

## Notes

Dashboard values were taken from the Power BI file and its PDF export. Figures have not been independently verified.
