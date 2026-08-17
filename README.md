# Supply Chain & E-commerce Analytics Dashboard

SupplyChain & E-commerce Analytics  is a personal data analytics project built around a large supply-chain dataset. I used Python and Pandas to explore and prepare the data, and then used Power BI to turn the analysis into an interactive business dashboard.

The main purpose of the project was to go through the complete analytics workflow rather than jump straight into visualization: understand the dataset, prepare it, investigate patterns, build useful measures, and finally present the results in a way that is easy to explore.

---

## Project Overview

The project started with the **DataCo SMART SUPPLY CHAIN FOR BIG DATA ANALYSIS** dataset downloaded from Kaggle.

The dataset contains **180,519 records and 53 columns**, covering areas such as:

- Orders and order dates
- Customers and customer segments
- Products and categories
- Revenue and profit
- Discounts
- Markets
- Shipping modes
- Delivery performance
- Shipping delays

I worked with the data in several stages before building the final dashboard.

```text
Kaggle Dataset
      ↓
Data Preparation
      ↓
Feature Engineering
      ↓
Exploratory Data Analysis
      ↓
Power BI Data Model
      ↓
DAX Measures
      ↓
Dashboard
      ↓
Business Insights
```

---

## Tools Used

- **Python**
- **Pandas**
- **Jupyter Notebook**
- **Power BI**
- **DAX**

SQL/PostgreSQL was considered during the project but was not used in the final workflow.

---

## Project Structure

```text
SupplyChain & E-commerce Analytics /
│
├── README.md
|
├── notebooks/
│   ├── 01_Business_Understanding/
│   ├── 02_Data_Preparation/
│   ├── 03_Feature_Engineering/
│   └── 04_EDA/
│
├── powerbi dashboard/
│   └── Supply Chain & E-commerce Analytics Dashboard.pbix
│
├── report/
    └── Supply Chain & E-commerce Analytics_Report.pdf

```

The data is kept in separate Raw, Cleaned and Engineered stages so that the progression from the original dataset to the analysis-ready data is clear.

---

## Exploratory Data Analysis

Before building the Power BI dashboard, I used Python and Pandas to understand the dataset.

The EDA included:

- Monthly revenue and order analysis
- Revenue per order
- Quantity per order
- Order-item quantity distribution
- Product price analysis
- Discount analysis
- Revenue, profit and profit margin
- Category performance
- Customer segment performance
- Customer lifetime revenue
- Product performance
- Unique products over time
- Shipping performance
- Delivery delay analysis

One of the main reasons for doing the EDA first was to avoid building visuals without understanding the data behind them.

---

## Some Findings

A few findings from the analysis stood out.

### Revenue Trend

Revenue was relatively stable through much of 2015 and 2016 and became stronger during much of 2017. It reached approximately **$1.03M in September 2017** before falling to approximately **$0.30M in January 2018**.

However, I did not treat this as a straightforward decline in business performance. The underlying data also changed during this period. Product availability and order composition shifted significantly, and items per order dropped from around 3 for much of the earlier period to about 1 from October 2017 onward.

This was a useful reminder that a change in a business metric should be investigated together with changes in the underlying data.

### Customer Segments

Consumer was the largest customer segment in the dataset, with approximately:

- **$17.16M revenue**
- **$2.07M profit**
- **34,119 orders**

Corporate generated approximately $10.03M in revenue and $1.20M in profit, while Home Office generated approximately $5.86M in revenue and $0.69M in profit.

### Delivery Performance

Overall delivery performance was approximately:

- **57.3% Delayed**
- **42.7% On Time**

During the analysis, I also found an issue with an earlier late-delivery calculation and corrected it before using the result in the final dashboard.

---

## Power BI Data Model

A dedicated `DateTable` was created for time-based analysis with:

- Date
- Day
- Month
- Month No.
- Quarter
- Week No.
- Year

The model uses an active one-to-many relationship:

```text
DateTable[Date]
      │
      │ 1 : *
      ▼
Featured_Engineering[Order Date]
```

Month was sorted using Month No. so that months appear chronologically.

I also created a separate **Measures** table to keep the DAX measures organized.

---

## Main DAX Measures

The main measures used in the dashboard include:

- Net Revenue
- Total Profit
- Total Orders
- Total Customers
- Average Order Value
- Overall Profit Margin
- Total Quantity Sold
- Average Delivery Delay
- Late Delivery Rate

Some overall reference values from the project are:

| KPI | Value |
|---|---:|
| Net Revenue | ~$33.05M |
| Total Profit | ~$3.97M |
| Total Orders | ~65.75K |
| Total Customers | ~20.65K |
| Average Order Value | ~$502.71 |
| Overall Profit Margin | ~12.00% |

---

# Dashboard

The final dashboard is divided into four pages. I kept the number of pages limited because several visuals started becoming repetitive during development.

## 1. Executive Overview

This page provides a quick view of overall business performance.

It includes:

- Net Revenue
- Total Profit
- Total Orders
- Total Customers
- Average Order Value
- Overall Profit Margin
- Monthly Revenue Trend
- Revenue by Market
- Delivery Performance
- Year filter

## 2. Customer Value & Order Behavior

This page focuses on customers and order behaviour.

It includes:

- Revenue by Customer Segment
- Customer Profit Mix
- Top 10 Customers by Revenue
- Average Order Value Trend
- Items per Order Trend

## 3. Commercial Performance & Profitability

This page looks at category performance and profitability.

It includes:

- Revenue vs Profit Margin by Category
- Profit Margin by Discount Level
- Profit Contribution by Order Size
- Unique Products Over Time
- Top 10 Categories by Profit

## 4. Fulfillment & Delivery Control

This page focuses on shipping and delivery operations.

It includes:

- Delivery Outcome by Shipping Mode
- Average Delivery Delay by Shipping Mode
- Order Mix by Shipping Mode
- Shipping Delay Trend

---

## Dashboard Design

The dashboard went through several iterations before reaching the current structure.

I avoided using a visual simply to fill available space. Each visual was selected based on the type of question it answers.

For example:

- **Bar charts** are used for comparisons and rankings.
- **Line charts** are used for trends over time.
- **Combo charts** are used when related measures have different scales.
- **Donut charts** are used only where the number of categories is small enough to remain readable.

I also avoided combining Net Revenue and Total Profit on the same monthly axis because their scales are very different. Doing so would make the profit trend difficult to interpret.

---

## What I Learned

This project helped me understand that a good dashboard starts before Power BI.

Working through the project gave me practical experience with:

- Working with a large transactional dataset
- Data preparation
- Feature engineering
- Exploratory data analysis with Pandas
- Time-based analysis
- Power BI data modeling
- Relationships
- DAX measures
- KPI design
- Choosing appropriate visualizations
- Dashboard layout and readability
- Turning analysis into business insights

One of the most useful lessons was learning to investigate the data behind an unexpected result before drawing a conclusion. The late-2017 revenue drop was a good example of this because the composition of the underlying data was changing at the same time.

---

## Future Improvement

The next improvement I am considering is a **Dynamic Analysis** page using Power BI **Field Parameters**.

The idea is to allow the user to choose what they want to analyse instead of creating a separate fixed visual for every possible combination.

For example, the user could choose a dimension such as:

- Category
- Market
- Customer Segment
- Shipping Mode

and a metric such as:

- Revenue
- Profit
- Orders
- Quantity
- Profit Margin

This is a planned enhancement and is not part of the completed four-page dashboard.

---

## Dataset Source

**DataCo SMART SUPPLY CHAIN FOR BIG DATA ANALYSIS**  
Source: Kaggle  
Original file: `DataCoSupplyChainDataset.csv`

The raw dataset is not included in this repository unless its licensing and redistribution terms permit it. The original Kaggle source should be used to obtain the dataset.

---

## Report

A detailed project report is available in:

`reports/SupplyChain & E-commerce Analytics _Project_Report.docx`

The report explains the project from the initial dataset and EDA through the Power BI model, DAX measures, dashboard pages and findings.

---

## Author

**Nitin**

This project was built as part of my learning and portfolio work in data analytics and Power BI.
