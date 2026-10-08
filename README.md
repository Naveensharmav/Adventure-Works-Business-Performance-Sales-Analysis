# Adventure Works Business Performance Analysis

> **Course Project:** This project was completed as part of the **Microsoft Power BI course by Maven Analytics**.
> It is a coursework project focused on analyzing business performance and building an interactive Power BI dashboard.

## Project Background

Adventure Works is a global manufacturing company that produces cycling equipment and accessories. The company operates across multiple regions and offers a range of products across different categories.

This project analyzes Adventure Works' business data to provide a clear view of its sales and overall business performance, with a focus on regional, product, and customer trends.

Insights and recommendations are provided on the following key areas:

- **Business Performance:** Track overall sales, revenue, profit, returns, and key performance indicators to understand how the business is performing over time.
- **Regional Performance:** Compare sales and profitability across regions to identify strong-performing and underperforming markets.
- **Product Performance:** Analyze product, subcategory, and category trends to identify top performers, underperforming products, and return patterns.
- **Customer Value:** Identify high-value customers and understand their contribution to overall sales and revenue.

Interactive Power BI dashboard exploring Adventure Works’ business performance and key trends [link].

# Data Structure & Initial Checks

The Adventure Works data model consists of 8 core tables: 2 fact tables (Sales Data, Returns Data) and 6 lookup tables. A description of each table is as follows:

- **Sales Data:** Order-level transactions, including order date, stock date, order number, line item, quantity, and keys linking to the customer, product, and territory.
- **Returns Data:** Returned products, including return date, quantity, and keys linking to the product and territory.
- **Customer Lookup:** Customer details such as name, birth date, marital status, gender, education, occupation, annual income, and email.
- **Product Lookup:** Product details such as SKU, name, model, color, style, cost, and price.
- **Product Subcategories Lookup / Product Categories Lookup:** The product hierarchy (product → subcategory → category).
- **Territory Lookup:** Sales regions, countries, and continents.
- **Calendar Lookup:** Date table used for time-based analysis.

![Data Model](images/Data-Model-view.png)

### Data Preparation in Power Query

All source files were loaded as CSVs and cleaned in Power Query before modelling:

- **All tables:** Promoted headers and set the correct data types (dates, whole numbers, text).
- **Sales Data:** The sales files were loaded together from a folder and combined into one table, then the helper `Source.Name` column was removed.
- **Customer Lookup:** Removed rows with errors in `CustomerKey` and filtered out blank keys. Standardised name capitalisation and created a `Full Name` column. Extracted the email domain into a `Domain Name` column and cleaned its formatting.
- **Product Lookup:** Converted cost and price to currency, removed the unused `ProductSize` column, replaced `0` with `NA` in `ProductStyle`, extracted a `SKU Type` from the SKU, and created a `Discount Price` column (10% below the product price).
- **Calendar Lookup:** Added day name, month, quarter, year, and start-of-period columns for time analysis.
