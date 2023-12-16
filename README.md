<img src="https://github.com/Nowosied/International.Debt/assets/149282488/7fe97bbc-c549-4784-8d74-67680253b579" width="400" height="200">

# **International Debt Statistics** 

**Platform**: DataCamp

**Data Source**: [worldbank.com](https://www.worldbank.org)

**Objective**: Utilizing SQL to analyze and extract insights from extensive international debt datasets.

**Key Tasks**:
Answering six fundamental questions about international debt dynamics.
Leveraging SQL's querying capabilities to navigate and manipulate relational databases.

1. What is the number of distinct countries present in the database?
```sql
SELECT COUNT(DISTINCT country_name) AS num_distinct_countries
FROM international_debt
```
2. What are the distinct debt indicators?
```sql
SELECT DISTINCT(indicator_code) AS distinct_debt_indicators
FROM international_debt
```
3. What is the total amount of debt owed by all the countries present in the table, in millions?
```sql
SELECT ROUND(SUM(debt) / 1000000, 2) AS total_debt
FROM international_debt
```
4. What country has the highest amount of debt?
```sql
SELECT country_name, SUM(debt) AS total_debt
FROM international_debt
GROUP BY country_name
ORDER BY total_debt DESC
LIMIT 1
```
5. What is the average amount of debt across different debt indicators?
```sql
SELECT indicator_code AS debt_indicator, indicator_name, AVG(debt) AS average_debt 
FROM international_debt 
GROUP BY debt_indicator, indicator_name
ORDER BY average_debt DESC
LIMIT 10
```
6. What is the highest amount of principal repayments in the "DT.AMT.DLXF.CD" category?
```sql
SELECT country_name, indicator_name
FROM international_debt 
WHERE debt = (SELECT MAX(debt)
			  FROM international_debt
			 WHERE indicator_code = 'DT.AMT.DLXF.CD')
```


**Software Used**: SQL for data querying and analysis.

**Significance**: Unveiling crucial insights into global financial trends and inter-country borrowing dynamics.

# **Snapshot of the database**
<img src="https://github.com/Nowosied/International.Debt/assets/149282488/10d88ac7-0946-4275-9843-ddc46240bbbe" width="700" height="300">

