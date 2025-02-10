# 🕵️‍♀️Project Overview

PhoneNow is a Telecom company that wants to implement a retention management to improve their services and wants to understand what are the factors that contibutes to a customer's reason for cutting off their services.

The Retention Manager wants answers to the following questions:
- Number of customers who left within the last month
- Services which the customer has signed for
- Demographic info of the customers
<br>

## Methods

In order to answer these questions, I made DAX measures to summarize the data that is needed for the visual presentation. This is the list of measures that were done: 

***1. Calculating the Churn Rate:***
   
```sql
Churn_Rate = 
    DIVIDE(
        COUNTROWS(FILTER(Table1, Table1[Churn] = "Yes")),
        COUNTROWS(Table1),
        0
    )
```

***2. Grouping the length of years when a customer stays and continue to use the services.***

> `For 1-10 Years`
```sql
Tenure_1-10 = 
    COUNTROWS(
        FILTER(Table1, Table1[tenure] >= 0 && Table1[tenure] <= 10)
    )
```
> `For 11-20 Years`
```sql
Tenure_11-20 = 
    COUNTROWS(
        FILTER(Table1, Table1[tenure] >= 11 && Table1[tenure] <= 20)
    )
```
> `For 21 Years and Beyond`
```sql
Tenure_21&Above = 
    COUNTROWS(
        FILTER(Table1, Table1[tenure] >= 21)
    )
```

***3. Counting the total number of Admin and Technical tickets raised.***
```sql
TotalAdminTickets = SUM(Table1[numAdminTickets])
```
```sql
TotalTechTickets = SUM(Table1[numTechTickets])
```

***4. Calculating the number of customers who uses the same internet services.***
```sql
Total_Categories_Count = 
    COUNTROWS(FILTER(Table1, 
        Table1[InternetService] = "DSL" || 
        Table1[InternetService] = "Fiber Optic" || 
        Table1[InternetService] = "No"))
```
-------
<br>

## 📊 Visualization

<img src="https://github.com/AlexisShagyo/Images/blob/main/Customer%20Retention.jpg" alt="Image" width="800" height="450">
<br>

## 📚 Insights

- In the previous month, approximately 27% of our customers discontinued our services. The majority of these customers were on monthly contracts, totaling 1,655 individuals. Many of them were subscribed to Fiber Optic Internet, which accounted for 1,162 customers. Additionally, around 1,313 customers in this group raised technical support tickets.
  
- 39% of the customers have signed up for services such as: Multiple Lines, Online Security, Online Backup, Device Protection, Tech Support, Streaming TV and Streaming Movies.
  
- 30% of the customers have dependents and 48% of them have partners.
  
- 49% of the customers are female and 51% are composed of males. 59% of our customers have been using the services for more than 20 years and most of them are using Fiber Optic (44%) internet.
  
- It is essential for agents to prioritize resolving technical issues for Fiber Optic users. In contrast, agents assisting DSL customers and those without internet access should first address their administrative concerns. 
<br>

## 📚 Recommendations:



- Given the data, there are some identified gaps that needed to be addressed, particularly what are the frequently occuring technical concern for Fiber Optic users. Consequently, what strategies can agents implement to effectively address the administrative concerns of customers who uses DSL and those without internet?
