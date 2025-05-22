# Data-Analysis-Using-Power-Bi

# Overview
The Coffee Shop Sales Analysis Dashboard is a Power BI project that provides a comprehensive visualization of sales data for a local coffee shop chain. It highlights key performance indicators (KPIs) such as total sales, number of orders, and total quantity sold. The dashboard offers in-depth insights through breakdowns by product category, product type, store location, and time-based sales trends. Designed for business stakeholders, the dashboard helps uncover sales patterns, pinpoint top-performing products, and support data-driven decisions to enhance operational efficiency and growth.

## Dataset
- **transaction_id**: Unique identifier for each transaction.
- **transaction_date**: Date of the transaction.
- **transaction_time**: Time of the transaction.
- **transaction_qty**: Quantity of items sold in the transaction.
- **store_id**: Unique identifier for the store.
- **store_location**: Location of the store.
- **product_id**: Unique identifier for the product.
- **unit_price**: Price per unit of the product.
- **product_category**: Category of the product.
- **product_type**: Type of product within the category.
- **product_detail**: Specific details of the product.




### DAX Forumlas
- **Key Metrics and Formulas**:
  - **Total Sales**: Sum of sales revenue for the selected period.
    - Formula: `SUM(Transactions[Sales])`
  - **Total Orders**: Total number of distinct orders placed.
    - Formula: `DISTINCTCOUNT(Transactions[transaction_id])`
  - **Total Quantity Sold**: Total number of units sold.
    - Formula: `SUM(Transactions[Transaction_Qty])`
  - **Average Sales**: Average daily sales amount.
    - Formula: `AVERAGEX(ALLSELECTED(Transactions[transaction_date]), 'Date Table'[Total Sales])`
  - **Previous Month Sales**: Sales in the previous month.
    - Formula: `CALCULATE('Transactions'[CM], DATEADD('Date Table'[Date], -1, MONTH))`
  - **Previous Month Orders**: Number of orders in the previous month.
    - Formula: `CALCULATE('Transactions'[CM Orders], DATEADD('Date Table'[Date], -1, MONTH))`
  - **Previous Month Quantity Sold**: Quantity sold in the previous month.
    - Formula: `CALCULATE('Transactions'[CM Qty], DATEADD('Date Table'[Date], -1, MONTH))`
  - **Current Month Sales**: Sales for the selected month.
    - Formula: 
      ```
      DAX VAR selected_month = SELECTEDVALUE('Date Table'[Month])
      RETURN TOTALMTD(
        CALCULATE(SUM(Transactions[Sales]), 'Date Table'[Month] = selected_month),
        'Date Table'[Date]
      )
      ```
The dashboard includes the following components:
- Some of the important KPIs that I have included are Total sales, orders, and quantity sold with month-over-month comparisons.
