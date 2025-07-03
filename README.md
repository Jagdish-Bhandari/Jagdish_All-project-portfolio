# Jagdish_All-project-portfolio

## [project-1: Supply Chain Management Overview](https://github.com/Jagdish-Bhandari/Supply-Chain-Dynamic-Dashboard.git)
* 📊 Project Overview:
  
This dashboard is powered by two fact tables and five dimension tables. I performed data cleaning and structured the dataset using the Power Query Editor (ETL tool) to ensure a disciplined, analysis-ready format.

You’ll find region-wise, product-wise, state-wise, and country-wise sales performance visualized through interactive charts. A Combo Chart is used to compare Sales Value with Profit and Cost, leveraging dynamic measures and parameters for deeper insights.

The dashboard also includes DAX calculations that reveal customer purchase patterns, showcasing customer counts based on buying behavior. Interactive features such as bookmarks and slicers enhance navigation and user-driven exploration.


### Supply chain dashboard overview: 
#### _Also published this on Power-BI_

<img src="https://github.com/user-attachments/assets/cb64d5a5-6640-4cf1-9f22-1600b1787f58" width ="700"/>

🔗 *Thank you for exploring this analysis! For the interactive dashboard and source files, please refer to the repository.*

---

## [project-2: Work life Analysis Overview](https://github.com/Jagdish-Bhandari/Work_life_analysis.git)
#### ***A primary Data prespective***
* 📊 Project Overview:
This project is based on primary data analysis collected through a Google Form. The survey was distributed to working professionals across various industry domains to gain insights into their work-life balance. The form was thoughtfully structured into three key sections:

    1. Basic Information – capturing demographic and background details
    2. Job Satisfaction & Alignment – understanding how well individuals feel aligned with their roles and overall job satisfaction
    3. Educational Aspirations – exploring their interest in further studies and the barriers they may face.

**“In this Work-Life Analysis project, I developed two distinct Power BI dashboards to demonstrate different data integration approaches. The first dashboard is connected to a MySQL database, enabling structured data exploration. The second is directly linked to Google Form responses, allowing real-time updates as new inputs are submitted.
This dual setup ensures that insights remain current, dynamic, and reflective of the latest respondent feedback.
You can explore the full dashboard walkthrough and insights toward the end of this README.”** 

The goal is to uncover meaningful patterns in how career paths, satisfaction levels, and personal growth opportunities intersect in the modern workplace. Feel free to participate in the survey through the link below—it would be great to have your perspective.

* 📈 Data Analysis – KPIs
Key metrics identified to evaluate the work-life landscape:

  - Average Job Satisfaction Rating
  - Percentage of Respondents Feeling Safe/Respected at Work
  - Distribution of Annual Salary Ranges
  - Alignment of Jobs with Educational Background
  - Industry-wise Job Satisfaction Trends
  - Mental Health Impact Score Across Age Groups
  - Proportion Interested in Further Education vs Barriers Faced These KPIs helped surface high-level insights for deeper exploration.

### work_life_analysis Dashboard overview

<img src="https://github.com/user-attachments/assets/fc04b538-d6ba-4c08-9e73-b629f372b888" width="700"/>

---

## work_life_analysis Dashboard overview
### ***connected to google form responses Radar: Auto Tracking Dashboard***
![Updateding Dashboard](https://github.com/user-attachments/assets/252d9cf8-7eeb-45c2-bd62-6b5cd9f0e1d2)

🔗 *Thank you for exploring this analysis! For the interactive dashboard and source files, please refer to the repository.*



---

## 🏦 [Bank Transaction Monitoring (MySQL Project)](https://github.com/Jagdish-Bhandari/Bank_transactions_overview.git)

## 📌 Project Overview
---
This project is designed to support a banking system in monitoring credit and debit transaction behavior across banks, branches, and customers. The dashboard enables:

- Identification of top spending customers
- Detection of high-traffic branches
- Analysis of preferred payment methods
- Flagging periods of low transaction activity
- Detection of suspicious or potentially fraudulent transactions
---
## 🎯 Key Features

- Dynamic KPIs and SQL Views
- Fraud and risk flagging logic
- Real-time transaction insights
- Data structured for integration with BI tools (Tableau/Power BI)
---
## 📊 KPIs Monitored

- Transaction Volume by Bank & Branch
- Transaction Trend Overview
- Top 10 Customers by Balance & Amount
- Branch-wise Count of Transactions Over Period
- Credit to Debit Ratio
- High-Risk Transaction Counts
- more...
---
## 🏗️ Database Schema

Table: Bank Debit_Credit transactions
---
## SQL Queries like:

### Total_transaction_Amount:
```sql
SELECT CONCAT(ROUND(SUM(Amount) / 1000000, 1), 'M') AS total_transaction_amount
FROM `debit and credit bank_data`;
```
---
### Transaction wise total_amount
```sql
select `transaction type`,concat(round(sum(Amount/1000000),2),"M") as Total_amount 
from `debit and credit bank_data`
group by `transaction type`;
```
---
### Credit_to_debit ratio
```Sql
SELECT 
round( (SELECT SUM(Amount) FROM `debit and credit bank_data` WHERE `Transaction Type` = 'credit') /
    (SELECT SUM(Amount) FROM `debit and credit bank_data` WHERE `Transaction Type` = 'debit'),4) 
    AS credit_to_debit_ratio;
```
---
### Net transaction amount
```sql
SELECT
round((SELECT SUM(Amount) FROM `debit and credit bank_data` WHERE `Transaction Type` = 'credit') -
    (SELECT SUM(Amount) FROM `debit and credit bank_data` WHERE `Transaction Type` = 'debit'),2)
AS credit_to_debit_ratio;
```
---
### TOP-10 Account_IDs and their transaction ratios
```sql
SELECT `Account Number`, COUNT(*) AS total_transactions, MAX(Balance) AS account_balance,
    ROUND(COUNT(*) / MAX(Balance), 4) AS activity_ratio
FROM `debit and credit bank_data`
GROUP BY `Account Number` order by account_balance desc limit 10;
```
---
### Transactions number as per years , months , weak , days
```sql
select year(`transaction date`) as Years,month(`transaction date`) As Monthly,monthname(`transaction date`) as Month_names,
week(`transaction date`) as weekly,day(`transaction date`) as Day_wise,count(*) as Total_transaction_count 
from `debit and credit bank_data`
group by Years,Monthly,Month_names,weekly, Day_wise;
```
---

###  High-Risk Transaction Flag

```sql
-- Disable safe updates to allow data modification
SET SQL_SAFE_UPDATES = 0;

-- Add a column for transaction type
ALTER TABLE `debit and credit bank_data` 
ADD COLUMN Threshold VARCHAR(25);

-- Update the column based on amount threshold
UPDATE `debit and credit bank_data`
SET Threshold = CASE 
    WHEN Amount > 2549 THEN 'High_Trans'
    ELSE 'Normal_Trans'
END;

-- View updated records
SELECT * FROM `debit and credit bank_data`;

```

### Suspicious Transaction Frequency:

```sql
select `Account Number`,Threshold,sum(amount) as Trans_amount , count(*) as trans_count from `debit and credit bank_data`
where threshold = "High_Trans"
group by `Account Number`,Threshold order by trans_amount desc limit 10;
```

---

🔍 *Explore more insightful SQL queries and data projects in my GitHub profile — just click on the repository title above!*

🔗 *Thank you for exploring this analysis! For the interactive dashboard and source files, please refer to the repository.*

---




