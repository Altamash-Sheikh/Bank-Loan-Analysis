📊 Loan Analysis Dashboard – Power BI

📌 Project Overview
This Power BI project provides a comprehensive Loan Portfolio Analysis, enabling financial institutions to monitor loan applications, funded amounts, repayments, interest rates, and borrower health. The dashboard highlights both portfolio-wide KPIs and Good vs Bad loan performance, supporting data-driven decision-making.
________________________________________
🚀 Key Features
🔑 KPI Analysis
•	Total Loan Applications (with MTD & MoM growth)
•	Total Funded Amount (with MTD & MoM growth)
•	Total Amount Received (with MTD & MoM growth)
•	Average Interest Rate (MTD & MoM variations)
•	Average Debt-to-Income Ratio (DTI) (MTD & MoM fluctuations)
✅ Good Loan vs ❌ Bad Loan KPIs
Good Loans
•	Good Loan Applications & % of total
•	Good Loan Funded Amount
•	Good Loan Amount Received
Bad Loans
•	Bad Loan Applications & % of total
•	Bad Loan Funded Amount
•	Bad Loan Amount Received
📋 Loan Status Grid View
A detailed grid categorized by Loan Status displaying:
•	Total Loan Applications
•	Total Funded Amount
•	Total Amount Received
•	MTD Funded Amount
•	MTD Amount Received
•	Average Interest Rate
•	Average Debt-to-Income Ratio (DTI)
________________________________________
📈 Visualizations in Dashboard
•	Monthly Trends by Issue Date (Line Chart): Detect seasonality and long-term lending trends
•	Regional Analysis by State (Filled Map): Highlight geographic loan distribution
•	Loan Term Analysis (Donut Chart): Show loan distribution by term lengths
•	Employment Length Analysis (Bar Chart): Explore borrower employment history impact
•	Loan Purpose Breakdown (Bar Chart): Understand reasons for borrowing
•	Home Ownership Analysis (Tree Map): Assess impact of home ownership on loans
Each visualization is tied to key metrics:
•	Total Loan Applications
•	Total Funded Amount
•	Total Amount Received
________________________________________
🛠️ Tech Stack
•	Power BI Desktop
•	DAX (Data Analysis Expressions) for calculations (MTD, MoM, YoY, grouping)
•	Data Source: Loan dataset (cleaned & anonymized)

________________________________________







🧮 Key DAX Measures
📌 Applications
Total Loan Application =
COUNT('bank_loan financial_loan'[id])

MTD Loan Application =
TOTALMTD(
    [Total Loan Application],
    'Date table'[Date]
)

Previous Month Loan Application =
CALCULATE(
    [Total Loan Application],
    PREVIOUSMONTH('Date table'[Date])
)

MoM Growth % Loan Applications =
DIVIDE(
    [Total Loan Application] - [Previous Month Loan Application],
    [Previous Month Loan Application]
)

📌 Loan Amounts

Total Loan Sanctioned =
SUM('bank_loan financial_loan'[loan_amount])

Previous Month Loan Sanctioned =
CALCULATE(
    [Total Loan Sanctioned],
    PREVIOUSMONTH('Date table'[Date])
)

MoM Growth % Loan Sanctioned =
DIVIDE(
    [Total Loan Sanctioned] - [Previous Month Loan Sanctioned],
    [Previous Month Loan Sanctioned]
)

📌 Payments
Total Loan Payment Received =
SUM('bank_loan financial_loan'[payment_received])

Previous Month Loan Payment Received =
CALCULATE(
    [Total Loan Payment Received],
    PREVIOUSMONTH('Date table'[Date])
)

MoM Growth % Loan Payment Received =
DIVIDE(
    [Total Loan Payment Received] - [Previous Month Loan Payment Received],
    [Previous Month Loan Payment Received]
)

📌 Interest Rate & DTI

Monthly Avg Interest Rate =
CALCULATE(AVERAGE('bank_loan financial_loan'[int_rate]))

Previous Month Avg Interest Rate =
CALCULATE(
    [Monthly Avg Interest Rate],
    PREVIOUSMONTH('Date table'[Date])
)

MoM Growth % Avg Interest Rate =
DIVIDE(
    [Monthly Avg Interest Rate] - [Previous Month Avg Interest Rate],
    [Previous Month Avg Interest Rate]
)

Monthly Avg DTI =
CALCULATE(AVERAGE('bank_loan financial_loan'[dti])) * 100

Previous Month Avg DTI =
CALCULATE(
    [Monthly Avg DTI],
    PREVIOUSMONTH('Date table'[Date])
)

MoM Growth % Avg DTI =
DIVIDE(
    [Monthly Avg DTI] - [Previous Month Avg DTI],
    [Previous Month Avg DTI]
)

📌 Loan Status (Good vs Bad)
Current + Fully Paid =
CALCULATE(
    COUNTROWS('bank_loan financial_loan'),
    'bank_loan financial_loan'[loan_status] IN {"Current", "Fully Paid"}
)

% Current + Fully Paid =
DIVIDE(
    [Current + Fully Paid],
    COUNTROWS('bank_loan financial_loan')
)

Charged Off =
CALCULATE(
    COUNTROWS('bank_loan financial_loan'),
    'bank_loan financial_loan'[loan_status] = "Charged Off"
)

% Charged Off =
DIVIDE(
    [Charged Off],
    COUNTROWS('bank_loan financial_loan')
)

________________________________________
📸 Dashboard Preview
SUMMARY
 

OVERVIEW
 

•	Home Ownership Impact: 48% of loans are taken by homeowners, indicating strong participation of financially stable borrowers.
•	Loan Term Preference: 73% of loans have a 36-month duration, highlighting borrowers’ preference for shorter-term commitments.
•	Portfolio Health: The total amount received consistently exceeds the total funded amount, reflecting healthy repayment behavior and strong loan portfolio performance.

