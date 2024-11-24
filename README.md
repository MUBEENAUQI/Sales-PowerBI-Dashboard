# GrowUp Sales Analysis Dashboard (PowerBI)
Sales dashboard using power BI

# 1. Project Title
GrowUp Sales and Profit Analysis Dashboard

# 2. Overview
This Power BI dashboard provides an in-depth analysis of sales, profits, customer behavior, and returns for the company GrowUp. It is designed to help stakeholders make data-driven decisions by visualizing key metrics and trends.

Pages Included:

**Overview**: High-level metrics like total sales, profits, and top products.
**Sales**: Detailed breakdown of sales trends, segments, and shipping.
**Profit**: Profit analysis by category, product, and region.
**Returns**: Insights into product returns and their impact.
**Customers**: Customer segmentation and behavior analysis.

# 3. Key Features
**Returns Analysis**:
Visualizes product categories with high return rates.
Shows the financial impact of returns on profits.

**Customer Insights**:
Highlights customer demographics and purchasing behavior.
Analyzes sales contributions from different customer segments.

# 4. Screenshots
**Overview Page**
![image](https://github.com/user-attachments/assets/5938dc64-b9e1-41d1-b151-4375f607406b)

**Sales Page**
![image](https://github.com/user-attachments/assets/b626a287-633a-4855-a57c-0961a89dbbba)

**Profit Page**
![image](https://github.com/user-attachments/assets/80259ab0-d97e-4534-ba9b-af62edf6c449)

**Returns Page**
![image](https://github.com/user-attachments/assets/9ad14f50-4e42-4487-b9be-0ef2ecdd9b35)

**Customers Page**
![image](https://github.com/user-attachments/assets/4fd97ef8-6f5c-4064-90d7-d4f38b509087)

# 5. How to Use
Clone this repository to your local system.
Open the Power BI file or explore screenshots.
Interact with the dashboard for actionable insights.

# 6. Insights and Learnings
Highlight new insights from the Returns and Customers pages:
"Returns are highest in the furniture category, impacting profitability."
"Consumer segment leads in purchases but shows moderate return rates."
"Top customers contribute to 60% of sales, indicating a loyal customer base.

# 7. Data Cleaning Process
The dataset was preprocessed to ensure accurate and meaningful analysis:
- Removed duplicates and handled missing values.
- Standardized columns for consistency.
- Applied transformations to enhance usability (e.g., date formatting, category merging).

# 8. DAX (Data Analysis Expressions)
This project incorporates advanced DAX coding to derive meaningful insights:

Created calculated columns and measures, such as:
> Date
```DAX
Date = 
VAR MinYear = YEAR ( MIN ( Orders[Order Date] ) )
VAR MaxYear = YEAR ( MAX ( Orders[Order Date] ) )
RETURN
ADDCOLUMNS (
    FILTER (
        CALENDARAUTO( ),
        AND ( YEAR ( [Date] ) >= MinYear, YEAR ( [Date] ) <= MaxYear )
    ),
    "Calendar Year", YEAR ( [Date] ),
    "Month Name", FORMAT ( [Date], "mmm" ),
    "Month Number", MONTH ( [Date] ),
    "Weekday", FORMAT ( [Date], "dddd" ),
    "Weekday number", WEEKDAY( [Date] ),
    "Quarter", "Q" & TRUNC ( ( MONTH ( [Date] ) - 1 ) / 3 ) + 1,
    "Month and Year", FORMAT ( [Date], "mmmm yyyy" )
```
> Return Rate
```DAX
Return Rate = DIVIDE([Total Returns], [Total Orders])
```
> New Customer Count
```DAX
New Customer Count = 
CALCULATE(
    COUNTROWS(Orders),
    FILTER(
        Orders,
        COUNTROWS(
            FILTER(Orders, Orders[Customer ID] = EARLIER(Orders[Customer ID]))
        ) = 1
    )
)
```

# Contributing
Feel free to fork the repository and submit pull requests for improvements.


