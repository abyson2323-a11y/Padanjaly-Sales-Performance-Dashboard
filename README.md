Padanjaly E-Commerce Analytics (Power BI)
A Power BI project that analyses WooCommerce order data from the Padanjaly store, from January 2023 to July 2026. It has four dashboards covering sales performance, sales geography, product demand and customer purchase behavior.

Tools Used:
•	Power BI Desktop
•	DAX: (measures and calculated columns)
•	WooCommerce order export (CSV)

**Dashboards:**
1. Sales Performance Dashboard:
Tracks order volume, order status and revenue over time.
Key areas:
•	Total orders and order status (completed vs processing)
•	Yearly sales trend
•	Top-selling products by sales value
•	Sales reported separately in INR and USD

2. Sales Geography Dashboard:
Shows where orders and sales come from.
Key areas:
•	State-wise and country-wise sales
•	Domestic vs international order share
•	Leading states and markets

3. Product Demand Dashboard:
Analyses product-level demand, quantity sold, monthly trends, and the relationship between product quantity and revenue.
Key areas:
•	Total products and total quantity
•	Monthly product demand from January 2023 to July 2026
•	Top 10 products by quantity
•	Yearly product demand
•	Product quantity versus revenue
•	Top-performing products by quantity and revenue

4. Customer Purchase Behavior Dashboard:
Analyzes how customers buy, how often they return, and how orders change over time.
Key areas:
•	Registered customers, total orders and repeat customers
•	Monthly order trend from January 2023 to July 2026
•	Order frequency distribution (1, 2, 3 and 5+ orders)
•	First-time vs repeat customers
•	Orders by status
•	Top 10 customers by purchase value
•	Filters for country, state, city, status and order date

## Project Files

| File | Description |
|---|---|
| [padanjaly-order-cleaning-dashboard-POwer.pbix](padanjaly-order-cleaning-dashboard-POwer.pbix) | Sales Performance Dashboard |
| [padanjaly-order-cleaning-dashboard-pdf.pdf](padanjaly-order-cleaning-dashboard-pdf.pdf) | Sales Performance Dashboard PDF |
| [updated-padanjaly--dashboard-Sales-geography.pbix](updated-padanjaly--dashboard-Sales-geography.pbix) | Sales Geography Dashboard |
| [updated-padanjaly--dashboard-Sales-geography Copy.pdf](updated-padanjaly--dashboard-Sales-geography%20Copy.pdf) | Sales Geography Dashboard PDF |
| [product-PBIX-dashboard--padanjaly.pbix](product-PBIX-dashboard--padanjaly.pbix) | Product Demand Dashboard |
| [product--dashboard--padanjaly.pdf](product--dashboard--padanjaly.pdf) | Product Demand Dashboard PDF |
| [customer-PBIX-dashboard--padanjaly.pbix](customer-PBIX-dashboard--padanjaly.pbix) | Customer Purchase Behavior Dashboard |
| [customer-PBIX-dashboard--padanjaly Copy.pdf](customer-PBIX-dashboard--padanjaly%20Copy.pdf) | Customer Purchase Behavior Dashboard PDF |

**Key Findings:**
Sales Performance:
•	Total orders: 690 orders analyzed.
•	Order status: 405 completed orders and 285 processing orders.
•	Sales performance: Revenue increased from approximately ₹0.08 million in 2023 to ₹0.53 million in 2025.
•	2026 sales: Approximately ₹0.42 million through July 2026.
•	Top product: Agnijith 90 gms generated approximately ₹0.93 million in sales.
•	Currency reporting: INR and USD sales are reported separately.

Sales Geography:
•	Leading state: Kerala, with approximately ₹0.39 million in sales in the visible state-wise chart.
•	Domestic orders: 88.26% of total orders.
•	International orders: 11.74% of total orders.
•	Geographic analysis: The dashboard compares state and country performance to identify important sales markets.

Product Demand:
•	Total products: 11.
•	Total quantity: Approximately 1.08K units.
•	Top quantity product: Agnijith 90 gms, with 508 units.
•	Second-highest quantity product: Agnihari Kasmeerini 90gms, with 252 units.
•	Top revenue product: Agnijith 90 gms.

Customer Purchase Behaviour:
•	Registered customers: 323 customers and 690 total orders analyzed.
•	One-time buyers: 302 customers (about 93.5%) placed only one order.
•	Repeat buyers: About 6.5% of customers placed more than one order.
•	Order frequency: 19 customers ordered twice, 1 ordered three times and 1 ordered five or more times.
•	Order trend: Monthly orders grew from about 3 to 5 in early 2023 to 20 to 40 by 2025 and early 2026, with a spike of roughly 80 orders just before July 2026. The drop after the spike is likely because July 2026 is a partial month (data ends on 14 Jul 2026).
•	Retention opportunity: Repeat purchase is the biggest area for growth. Follow-ups such as a thank-you coupon or a reorder reminder after the first order would target the right group.


DAX-Measures:
Core Measures:
•	Total Orders:
Dax::
Total Orders =
DISTINCTCOUNT(
    'padanjaly-order export0 csv'[order_id]
)
•	Total Sales INR:
Dax:
Total Sales INR =
SUM(
    'padanjaly-order export0 csv'[order_subtotal]
)
•	Total Sales USD:
Dax:
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
Note: Validate the exchange-rate methodology and currency-specific totals before using the converted figures for financial reporting.
Geography Measures:
•	International Share %:
Dax:
International Share % =
DIVIDE(
    [International Orders],
    [Total Orders]
)
•	Domestic Share %:
Dax:
Domestic Share % =
1 - [International Share %]
Product Measures:
•	Average Quantity per Order:
Dax:
Average Quantity per Order =
DIVIDE(
    SUM('full_Product'[Quantity]),
    DISTINCTCOUNT('full_Product'[order_id]),
    0
)
•	Most Sold Product:
Dax:
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
Customer Purchase Behavior Measures:
•	Registered Customers:
Dax:
Registered Customers =
CALCULATE(
    DISTINCTCOUNT('padanjaly-order export0 csv'[customer_id]),
    'padanjaly-order export0 csv'[customer_id] <> 0
)
•	Repeat Customers:
Dax:
Repeat Customers =
CALCULATE(
    DISTINCTCOUNT('padanjaly-order export0 csv'[customer_id]),
    'padanjaly-order export0 csv'[Customer Type] = "Repeat"
)
•	Repeat Rate:
Dax:
Repeat Rate =
DIVIDE(
    [Repeat Customers],
    [Registered Customers]
)
•	Registered Orders:
Dax:
Registered Orders =
CALCULATE(
    [Total Orders],
    'padanjaly-order export0 csv'[customer_id] <> 0
)
•	Orders per Customer;
Dax:
Orders per Customer =
DIVIDE(
    [Registered Orders],
    [Registered Customers]
)
Customer Purchase Value:
Dax:
Customer Purchase Value =
SUM('padanjaly-order export0 csv'[order_subtotal])
•	Average Customer Value:
Dax:
Average Customer Value =
DIVIDE(
    CALCULATE(
        [Total Sales INR],
        'padanjaly-order export0 csv'[customer_id] <> 0
    ),
    [Registered Customers]
)
Customer Calculated Columns:
These are created as New column in the main table, not as measures.
•	Customer Type:
Dax:
Customer Type =
VAR CustID = 'padanjaly-order export0 csv'[customer_id]
VAR OrderCnt =
    CALCULATE(
        DISTINCTCOUNT('padanjaly-order export0 csv'[order_id]),
        ALLEXCEPT(
            'padanjaly-order export0 csv',
            'padanjaly-order export0 csv'[customer_id]
        )
    )
RETURN
    IF(
        ISBLANK(CustID) || CustID = 0,
        "Guest",
        IF(OrderCnt > 1, "Repeat", "First-Time")
    )
•	Customer Order Count:
Dax:
Customer Order Count =
VAR CustID = 'padanjaly-order export0 csv'[customer_id]
RETURN
IF(
    ISBLANK(CustID) || CustID = 0,
    BLANK(),
    CALCULATE(
        DISTINCTCOUNT('padanjaly-order export0 csv'[order_id]),
        ALLEXCEPT(
            'padanjaly-order export0 csv',
            'padanjaly-order export0 csv'[customer_id]
        )
    )
)
•	Order Frequency Band:
Dax:
Order Frequency Band =
VAR Orders = 'padanjaly-order export0 csv'[Customer Order Count]
RETURN
    SWITCH(
        TRUE(),
        ISBLANK(Orders), BLANK(),
        Orders >= 5, "5+",
        FORMAT(Orders, "0")
    )
•	Order Frequency Sort:
Used to sort Order Frequency Band as 1, 2, 3, 5+ (Column tools → Sort by column).
Dax:
Order Frequency Sort =
VAR Orders = 'padanjaly-order export0 csv'[Customer Order Count]
RETURN
    IF(
        ISBLANK(Orders),
        BLANK(),
        MIN(Orders, 5)
    )

Top 10 Customers by Value	Clustered bar chart	Y: customer_id, X: Customer Purchase Value, Top N filter = 10

