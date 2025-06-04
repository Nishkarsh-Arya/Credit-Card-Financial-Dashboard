# 💳 Credit Card Financial Dashboard (Power BI)

This project is a complete end-to-end dashboard developed using Power BI + PostgreSQL, designed to analyze and visualize credit card customer behavior and transaction patterns. It empowers financial analysts and decision-makers with actionable insights on revenue, customer segmentation, and spending trends.

---

## 🎯 Project Purpose

To monitor and improve credit card business performance by:

- Analyzing transaction data and customer demographics
- Identifying revenue-driving factors
- Segmenting customer profiles for strategic targeting
- Providing weekly and quarterly insights for stakeholder decisions

---

## 📊 Key Metrics (KPIs)

The dashboard tracks and visualizes several core KPIs:

- **Total Revenue & Interest Earned**
- **Customer Count and Acquisition Cost**
- **Transaction Volume and Value**
- **Gender & Age-wise Revenue Contribution**
- **Card Category Revenue Breakdown**
- **Quarterly Performance (Revenue & Transaction Count)**
- **Revenue by Job, Education, State, and Expenditure Type**

---

## 📈 Charts & Visuals

Visual elements created in Power BI:

- **Bar Charts**: Revenue by job, card type, state, education
- **Pie Charts**: Gender distribution, salary group, marital status
- **Line Graph**: Revenue trend over time
- **Stacked Columns**: Quarter-wise revenue and transaction count
- **KPI Cards**: Total revenue, total interest, transaction amount, customer acquisition cost
- **Slicers & Filters**: Age group, salary group, week number, etc.

---

## 🔁 DAX Measures (Sample)

### Age Group Classification:
```dax
AgeGroup = SWITCH(
    TRUE(),
    'public cust_detail'[customer_age] < 30, "20-30",
    'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
    'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
    'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
    'public cust_detail'[customer_age] >= 60, "60+",
    "unknown"
)
```

### Revenue Calculation:
```dax
Revenue = 
'public cc_detail'[annual_fees] +
'public cc_detail'[total_trans_amt] +
'public cc_detail'[interest_earned]
```

---

## 🗓️ Weekly Metrics Calculation

### Weekly Revenue:
```dax
Current_week_Reveneue = CALCULATE(
    SUM('public cc_detail'[Revenue]),
    FILTER(ALL('public cc_detail'), 
    'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2]))
)
```

### Previous Week Revenue:
```dax
Previous_week_Reveneue = CALCULATE(
    SUM('public cc_detail'[Revenue]),
    FILTER(ALL('public cc_detail'), 
    'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2]) - 1)
)
```

---

## ✅ Final Dashboard

- Built with Power BI for interactive filtering and detailed drill-down
- Dynamic visuals across multiple dimensions (time, gender, region, card type, etc.)
- Supports SQL integration and DAX-based calculations
- Designed for weekly monitoring and strategic decision-making

![Credit Card Financial Dashboard](Project_Files/Dashboard_Screenshot.png)

---

## 📁 Project Files

- `credit_card.csv`, `customer.csv`, `cust_add.csv`, `cc_add.csv` – Source data files
- `Credit Card Financial Weekly Dashboard Report` – Main Project file
- `Credit Card Financial Dashboard-Customer(screenshot2)` – Customer-focused insights
- `Credit Card Financial Dashboard-Transaction(screenshot1)` – Transaction-focused insights
- `README.md` – Project documentation

---

## 🚀 How to Use

1. Load the CSV files into SQL or Power BI
2. Use provided DAX expressions to create calculated columns and measures
3. Build visuals using fields from processed data
4. Apply slicers to filter by card type, age group, week number, etc.
5. Export insights and share the report with stakeholders

---

## 🧰 Built With

- Power BI Desktop
- SQL (for data ingestion)
- DAX (for calculated fields)
- Excel (for raw data preparation)

---

## 📬 Contact

For questions, feedback, or collaboration:



---

## 🏁 Acknowledgments

This project is part of a professional analytics portfolio. It demonstrates real-world application of Power BI in financial analysis using credit card data for a comprehensive weekly performance dashboard.
