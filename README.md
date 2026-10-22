# Padanjaly Sales Performance Dashboard

Sales performance, customer and market analysis for Padanjaly Ayurveda (Power BI dashboard and final report).

<img width="1320" height="797" alt="Sales Performance Dashboard" src="https://github.com/user-attachments/assets/48deb9d4-7ddd-475b-80fb-5645ecc7cf00" />

## Overview

Padanjaly Ayurveda sells Ayurvedic products online (mainly Agnijith and Agnihari creams) through a WooCommerce store. This project turns 690 orders into a Power BI sales dashboard and a combined business report. The report brings together four sources: the sales dashboard report, the Agnijith product and market research, the WooCommerce data-cleaning report, and the customer project report.

The report covers:
- how sales have changed over time and what drove the peaks
- which products carry the business and where the risk is
- who the customers are, and how many come back
- which markets matter, in India and abroad
- what to fix on the website, and what to do next

## Files

| File | Description |
|---|---|
| `Padanjaly_Final_Report_v2.pdf` | Final 5-page report (best for reading and sharing) |
| `Padanjaly_Final_Report_v2.docx` | Editable Word version of the same report |

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

## Recommendations (summary)

1. **0 to 30 days:** clear the 285 processing orders; run a day-35 repeat-purchase offer; test an Agnijith + Agnihari combo; fix website currency, booking button and health-claim wording; pilot COD in Kerala.
2
