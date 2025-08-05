# 🏦 Banking Analysis Project

### Created by Vivek Pattnaik
<p align="left"> <a href="https://www.linkedin.com/in/vivekpattnaik" target="_blank"> <img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"> </a>  </a> <a href="mailto:vivek.pattnaik@gmail.com"> <img src="https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Email"> </a> </p>

## 📊 Interactive Dashboard

This project features a comprehensive Power BI dashboard that provides a deep dive into the bank's customer data, financial performance, and risk profiles.
<a href="https://project.novypro.com/gdufdN" target="_blank"> <img src="https://img.shields.io/badge/View_Live_Dashboard-FF6347?style=for-the-badge&logo=powerbi&logoColor=white" alt="Live Dashboard"> </a>

<img width="1774" height="981" alt="Screenshot 2025-08-05 002028" src="https://github.com/user-attachments/assets/f8de90b8-5d99-462c-aff7-8f065694a916" />



## 📝 Project Overview

This project presents an in-depth analysis of a diverse banking dataset encompassing 3,000 clients. The primary objective is to transform raw transactional and demographic data into actionable business intelligence. By leveraging **MySQL** for data storage, **Python (with Pandas in a Jupyter Notebook)** for initial data handling, and **Power BI** for advanced analysis and visualization, this project uncovers critical insights into customer behavior, financial health, and risk assessment.

The key objectives were:

-   **To perform a detailed analysis of the banking data.**

-   **To segment customers based on various factors like age, income, and relationship type.**

-   **To identify and categorize client risk levels.**

-   **To visualize complex data trends for easy interpretation.**

-   **To create a professional and insightful Power BI dashboard to showcase the findings.**


<br>

The analysis is structured around three key pillars:
1.  **Customer Demographics & Profiling:** Understanding who the customers are.
2.  **Financial Product Performance:** Analyzing the performance of financial products like loans and deposits.
3.  **Risk & Compliance Management:** Identifying and managing client-associated risks.

## 🛠️ Tools & Technologies

| Tool | Purpose |
| :--- | :--- |
| **MySQL** | Backend database for storing and managing the customer and financial data. |
| **Python (Jupyter Notebook)** | Data Processing & Exploration: Pandas, Matplotlib, Seaborn |
| **Power BI** | The core tool for data modeling, creating complex DAX measures, and building the interactive, multi-page dashboard for visualization and insight generation. |

## ⚙️ Project Execution

### 1. Data Extraction (ETL)

The process began with connecting to a local MySQL server to fetch the raw banking data. The following Python script was executed in a Jupyter Notebook to load the data into a Pandas DataFrame for preliminary inspection. [Banking_Analysis.ipynb](https://github.com/AnalystVivek/Banking_Analysis/blob/main/Banking_Analysis.ipynb)

```python
import mysql.connector
import pandas as pd

# Establish connection to the MySQL server
cnx = mysql.connector.connect(
    host="127.0.0.1",
    port=3306,
    user="user_id",
    password="password" # Replace with your password
)

# SQL query to select all data from the customers table
query = "SELECT * FROM banking_analysis.customers"

# Load data into a Pandas DataFrame
df = pd.read_sql(query, cnx)

# Close the database connection
cnx.close()

# Display the first few rows of the dataset
print(df.head())
```

### 2. Data Modeling & DAX Measures

Within Power BI, the data was modeled to establish relationships between different tables. Several powerful DAX measures were created to enable dynamic and complex calculations. Here are some of the key measures used :

<img width="1434" height="151" alt="image" src="https://github.com/user-attachments/assets/9c1322fd-2ed3-47ac-8d4c-54d8aac33c71" />

<br>

## 💡 Key Insights & Findings

The dashboard is organized into three main analytical views, each providing unique insights.

### I. Customer Demographics & Profile Analysis

This section provides a comprehensive overview of the client base, segmenting them by their relationship with the bank, age, and income levels.

<img width="1794" height="1035" alt="Screenshot 2025-08-05 211446" src="https://github.com/user-attachments/assets/834138db-706e-4799-8441-5eb0d5d41cc2" />

-   **Client Segmentation:**
    -   **Private Banking** clients represent the largest segment, with **1,352** individuals, indicating a strong focus on high-net-worth relationships.
    -   The **Adult (30-59)** age group is the most significant demographic, comprising **1,309 clients**, followed by Seniors (60+) with 1,127 clients.
-   **Income Distribution:**
    -   The majority of clients (**50.57%** or 1,517 clients) fall into the **Medium** income band.
-   **Loyalty Insights:**
    -   **Jade** is the most common loyalty tier, particularly among Adult and Senior clients, suggesting a stable, long-term customer base.

### II. Financial Product Performance & Portfolio

This view analyzes the bank's core financial products, highlighting the balance between deposits and loans and exploring credit usage patterns.

<img width="1793" height="1034" alt="Screenshot 2025-08-05 211506" src="https://github.com/user-attachments/assets/05c8023a-a983-4030-992e-e02c0b5ca98b" />


-   **Deposits vs. Loans:**
    -   The bank maintains a healthy financial position, with **Total Deposits (€2.0bn)** significantly exceeding **Total Loans (€1.8bn)**.
    -   **Private Banking** is the primary driver for both deposits (€925M) and loans (€814M).
-   **Credit Card Holdings:**
    -   The **Adult (30-59)** age group holds the highest number of credit cards, with a nearly even split between male and female clients. This group represents a key target for credit-related products.
-   **Business Lending Leaders:**
    -   Clients with occupations like **Structural Analysis Engineer** (€33M) and **Automation Specialist IV** (€28M) are associated with the highest amounts of business lending, pointing to specific professional segments driving commercial loan activity.

### III. Risk & Compliance Overview

This critical section assesses the bank's risk exposure by categorizing clients based on their risk weighting and analyzing the distribution of risk across different segments.

<img width="1790" height="1033" alt="Screenshot 2025-08-05 211533" src="https://github.com/user-attachments/assets/e021cd93-5b2e-45dc-b9b0-83fe874aa5c3" />


-   **Risk Distribution:**
    -   A majority of clients (**40.73%**) are classified as **Low Risk**, with another **27.87%** as **Very Low Risk**, indicating a generally conservative and healthy client portfolio.
    -   However, **15.33%** of clients fall into the **High Risk** category and **5.33%** into **Very High Risk**, which requires strategic monitoring.
-   **High-Risk Client Profile:**
    -   Clients of **European** nationality make up the largest group of high-risk individuals, followed by those of Asian and American descent.
    -   The number of **High-Risk** clients has seen a noticeable increase over time, peaking in recent years. This trend warrants further investigation to understand the underlying causes and mitigate potential defaults.
-   **Loan Portfolio by Risk:**
    -   The analysis of total loans by risk profile shows that while **Low Risk** clients have substantial loan amounts, the **High Risk** and **Very High Risk** categories also hold significant loan balances, representing a concentrated area of financial risk for the bank.
