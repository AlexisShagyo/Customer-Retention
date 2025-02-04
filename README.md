# Project Overview
--------
PhoneNow is a Telecom company that wants to implement a retention management to improve their services and wants to understand what are the factors that contibutes to a customer's reason for cutting off their services.

The Retention Manager wants answers to the following questions:
- Number of customers who left within the last month
- Services which the customer has signed for
- Demographic info of the customers

In order to answer these questions, I made DAX measures to summarize the data that is needed for the visual presentation. This is the list of measures that were done: 

***1. Calculating the Churn Rate:***
   
|Churn_Rate = DIVIDE(COUNTROWS(FILTER(Table1, Table1[Churn] = "Yes")),COUNTROWS(Table1), 0)|
|-------------|

***2. Grouping the length of years when a customer stays and continue to use the services.***
| Tenure_1-10 = COUNTROWS(FILTER(Table1, Table1[tenure] >= 0 && Table1[tenure] <= 10)) |
|-------------|

| Tenure_11-20 = COUNTROWS(FILTER(Table1, Table1[tenure] >= 11 && Table1[tenure] <= 20)) |
|-------------|

| Tenure_21&Above = COUNTROWS(FILTER(Table1, Table1[tenure] >= 21)) |
|-------------|

***3. Counting the total number of Admin and Technical tickets raised.***

| TotalAdminTickets = SUM(Table1[numAdminTickets]) |
|-------------|

| TotalTechTickets = SUM(Table1[numTechTickets]) |
|------------|

-------
## 📊 Visualization

<img src="https://github.com/AlexisShagyo/Images/blob/main/Customer%20Retention.jpg" alt="Image" width="1000" height="600">

## 📚 Insights

- About 27% of our customers have left our services for the previous month. Most of which are under monthly basis contract (1,655 customers) and customers which has Fiber Optic as their internet provider (1,162 customers). About 1,313 customers have raised concerns with techinical problems.
- 39% of the customers have signed up for services such as: Multiple Lines, Online Security, Online Backup, Device Protection, Tech Support, Streaming TV and Streaming Movies.
- 30% of the customers have dependents and 48% of them have partners. 
- 49% of the customers are female and 51% are composed of males. 59% of our customers have been using the services for more than 20 years and most of them are using Fiber Optic (44%) internet.

## 📚 Recommendations:

According to the Churn data, customers are more likely to stay with concerns of the administrative one rather than the technical requirements. While a large part of the customers who left within the month have technical tickets raised, dominantly from Fiber Optic and only binded by a monthly contract.

Agents should focus on solving Technical concerns from customers who uses Fiber Optic while DSL and those with no internet should prioritize solving the administrative aspect.

