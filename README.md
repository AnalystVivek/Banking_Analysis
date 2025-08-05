```markdown
# 📊 Banking Analytics Dashboard

![Banking Dashboard Banner]([https://via.placeholder.com/1200x300?text=Banking+Analytics+Dashboard](https://github.com/AnalystVivek/Banking_Analysis/blob/main/Screenshot%202025-08-05%20002028.png)  

## 🚀 Project Overview

Welcome to the **Banking Analytics Dashboard** project! This is a comprehensive data analytics initiative focused on analyzing banking customer data to uncover key insights into customer demographics, financial performance, risk profiles, and compliance metrics. As a Data Analyst, I leveraged this project to demonstrate skills in data extraction, transformation, visualization, and insightful reporting.

The dashboard provides an interactive view of banking operations, helping stakeholders understand client behaviors, financial health, and risk exposures. Built using real-world banking data, it highlights trends in deposits, loans, customer loyalty, and risk categories across various demographics.

Key highlights:
- **Domain**: Data Analytics in Banking
- **Tools Used**: MySQL for data storage and querying, Jupyter Notebook for data exploration and ETL, Power BI for interactive visualizations and dashboard creation.
- **Dataset**: A CSV file (`Banking.csv`) containing customer details like age, income, banking relationships, deposits, loans, and more (sample attached in repo).
- **Objective**: To create actionable insights for banking executives to optimize customer engagement, manage risks, and drive financial growth.

This project showcases end-to-end data analytics: from raw data ingestion to insightful dashboards. Explore the live Power BI report [here](https://project.novypro.com/gdufdN) for interactive exploration!

---

## 🛠 Tools and Technologies

- **Database**: MySQL - For storing and querying the banking dataset.
- **Data Processing**: Jupyter Notebook - Used for initial data loading, cleaning, and analysis (see `Banking_Analysis.ipynb` in the repo).
- **Visualization**: Power BI - For building the interactive dashboard with DAX measures and custom visuals.
- **Other**: Python (Pandas, MySQL Connector) for ETL in Jupyter.

---

## 📂 Data Source and Preparation

The dataset is sourced from `Banking.csv`, which includes columns like:
- `client_id`, `name`, `gender`, `age`, `banking_relationship`, `estimated_income`, `loyalty_classification`, `bank_loans`, `bank_deposits`, etc.

### Data Loading in Jupyter Notebook
Here's a snippet from `Banking_Analysis.ipynb` showing how data was loaded from MySQL:

```
import mysql.connector
import pandas as pd

# Connect to MySQL server
cnx = mysql.connector.connect(
    host="127.0.0.1",
    port=3306,
    user="root",
    password="284585"
)

# Query to fetch data
query = "SELECT * FROM banking_analysis.customers"

# Load into Pandas DataFrame
df = pd.read_sql(query, cnx)
cnx.close()

# Basic stats
df.describe()
```

This ETL process ensured data was cleaned, transformed, and ready for analysis in Power BI.

---

## 🔍 Key Insights

Through rigorous analysis, the dashboard reveals several critical insights into the banking dataset of 3000 customers:

1. **Customer Demographics**:
   - **Total Clients**: 3000, with a balanced gender distribution (50.4% Female, 49.6% Male).
   - **Age Groups**: Adults (30-59) dominate at 43.63% (1309 clients), followed by Seniors (60+) at 37.57% (1127), and Young (18-29) at 18.8% (564).
   - **Nationality Breakdown**: European (40.73%), Asian (27.87%), American (15.33%), Australian (10.73%), African (5.33%).
   - **Insight**: Growth in customer base has been steady since 1995, with a spike in recent years. Private Banking holds the most clients (1352), indicating strong high-net-worth engagement.

   ![Customer Demographics Chart](images/customer_demographics.png)  
   *(Extracted from Banking_analysis.pdf - Age Group and Nationality Distribution.)*

2. **Financial Performance**:
   - **Total Deposits**: 2.0bn, with Private Banking contributing the highest.
   - **Total Loans**: 1.8bn, showing a healthy loan-to-deposit ratio.
   - **Savings and Balances**: Total Savings Balance at 69.87bn, Checking at 96.33bn, Foreign Currency at 8.97bn, Superannuation at 7.66bn.
   - **Credit Exposure**: High in credit cards and business lending, with top occupations like Software Engineers and Accountants driving high net worth.
   - **Insight**: Debt-to-Income ratios are stable, but young clients show higher variability. Top 10 customers by net worth contribute significantly to deposits (e.g., John Frazier with 49M net worth).

   ![Financial Portfolio Chart](images/financial_portfolio.png)  
   *(Extracted from Banking_analysis.pdf - Deposits vs. Loans by Relationship Type.)*

3. **Risk and Compliance**:
   - **Risk Distribution**: Low Risk (40.73%), Very Low Risk (27.87%), Moderate (15.33%), High (10.73%), Very High (5.33%).
   - **High-Risk Clients**: Concentrated in Europeans (206) and Asians (121), with trends showing peaks in 2010-2020.
   - **Loan Portfolio Growth**: Steady increase with strong collateral in properties owned.
   - **Insight**: Very High Risk clients are minimal (5.33%), but monitoring is crucial for Moderate Risk groups (459 clients). Risk weighting correlates with higher loans in Institutional Banking.

   ![Risk Distribution Chart](images/risk_distribution.png)  
   *(Extracted from Banking_analysis.pdf - Client Distribution by Risk Weighting.)*

   Additional Insights:
   - Loyalty Classification: Jade (majority), followed by Gold, Platinum, Silver – linked to higher deposits.
   - Income Bands: Medium income clients (50.57%) hold the most accounts, but High income drives 40% of loans.
   - Gender Trends in Credit: Males hold more credit cards in Senior groups, while Females dominate in Young categories.
   - Over Time: Client net worth has grown 3x since 2000, with risk profiles stabilizing post-2015.

These insights empower banks to target high-value segments, mitigate risks, and enhance product offerings.

---

## 📈 DAX Measures Used in Power BI

Custom DAX measures were pivotal for calculations. Here are some key ones:

1. **Age Group Calculation**:
   ```
   Age group = IF(Banking[age] < 30, "Young (18-29)", IF(Banking[age] < 60, "Adult (30-59)", "Senior (60 +)"))
   ```

2. **Client Net Worth**:
   ```
   Client Net Worth = SUM('Banking'[bank_deposits]) + SUM('Banking'[saving_accounts]) + SUM('Banking'[superannuation_savings]) - SUM('Banking'[bank_loans]) - SUM('Banking'[creditcard_balance])
   ```

3. **Custom Label for Bar Charts**:
   ```
   Cust_Label for Bar chart =
   VAR BankingRel = SELECTEDVALUE('Banking'[banking_relationship])
   VAR NameCount = CALCULATE(COUNT('Banking'[name]), ALLEXCEPT('Banking', 'Banking'[banking_relationship]))
   RETURN
   BankingRel & " | " & FORMAT(NameCount, "0")
   ```

4. **Risk-Related Measures**:
   ```
   High Risk Clients = CALCULATE(COUNT(Banking[client_id]), Banking[risk_weighting] = 4)
   Moderate Risk Clients = CALCULATE(COUNT(Banking[client_id]), Banking[risk_weighting] = 3)
   Very High Risk Clients = CALCULATE(COUNT(Banking[client_id]), Banking[risk_weighting] = 5)
   ```

5. **Total Credit Exposure**:
   ```
   Total Credit Exposure = SUM('Banking'[creditcard_balance]) + SUM('Banking'[bank_loans]) + SUM('Banking'[business_lending])
   ```

6. **Risk Category**:
   ```
   Risk Category =
   SWITCH (
       'Banking'[risk_weighting],
       1, "Very Low Risk",
       2, "Low Risk",
       3, "Moderate Risk",
       4, "High Risk",
       5, "Very High Risk", "Unknown"
   )
   ```

And more – full list in the Power BI file.

---

## 🏃‍♂️ How to Run the Project

1. **Clone the Repo**: `git clone https://github.com/AnalystVivek/Banking-Analytics-Dashboard.git`
2. **Setup MySQL**: Import the dataset into MySQL using the provided SQL scripts.
3. **Run Jupyter Notebook**: Open `Banking_Analysis.ipynb` to explore data.
4. **View Dashboard**: Open the `.pbix` file in Power BI Desktop or visit the [live report](https://project.novypro.com/gdufdN).

---

## 📞 Contact and Links

- **LinkedIn**: [Vivek Pattnaik](https://www.linkedin.com/in/vivekpattnaik)  
- **GitHub**: [AnalystVivek](https://github.com/AnalystVivek)  
- **Email**: vivek.pattnaik@gmail.com  
- **Live Power BI Report**: [Banking Analytics Dashboard](https://project.novypro.com/gdufdN)

Feel free to star ⭐ this repo, fork it, or reach out for collaborations!

---

*This project is open-source under MIT License. Contributions welcome!*
```

[1] https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/82624519/53d3d74e-873f-44c8-9391-fc071a7c98d8/Banking.csv
[2] https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/82624519/5ff6f4ec-f7be-4d81-b445-7464fc42f90f/Banking_Analysis.ipynb
[3] https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/82624519/60deb7c5-214b-487b-8e94-2285a715dc93/Banking_analysis.pdf
