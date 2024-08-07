
# Adventure Works Sales Analysis




## Table of Contents



    1.Overview
    2. Problem Statement
    3. Cleaning and Pre processing Data
    4. Generating Visuals, Report and Insights provided
    5. Analysis on insights provided
    6. Appendix





## Overview and Problem Statement


AdventureWorks is a sample database provided by microsoft (https://learn.microsoft.com/en-us/sql/samples/adventureworks-install-configure?view=sql-server-ver15&tabs=ssms). This database contains a lot of different types of table containing different types of data. For this particular project AdventureWorksDW2019.bak was used. Data importing, cleaning, transformation and analysis, I've tried to cover all the aspects of this project in this readme file in as much details as possible. 

We have an example buisness mail from Steven who works at the company. We have the buisness request from him. The requirement is to create a visual dashboard which focuses on how much they have sold of what products, to which clients and how it has been over time.
They also have a sample budget file to compare the sales against.

Steps taken to achieve the visualisation-
    
    1. Creating buisness demand overview and user stories to understand the requirement

    2. Identifying the necessary tables inside the database. I've taken 3 dimensional table and one fact table from the database

    3. Cleaning the data through sql. Removing all the unnecessary ccoloumns

    4. preprocessing data through power query. Declaring the necessary datatypes and reclean the data to spot any anomalies.

    5. Designing the schema, connecting the necessary tables and defining the relations.

    6. Designing the Visuals



### Cleaning and pre processing data 

1. Load the db into MS Sql Server Management Studio by following the steps here -
https://learn.microsoft.com/en-us/sql/samples/adventureworks-install-configure?view=sql-server-ver15&tabs=ssms


![image](https://github.com/user-attachments/assets/b2504ee7-2858-429f-b56e-62e4529112c7)


2. After restoring the database select the tables to work with. As provided in the requirement we'll be working with the following tables-
dbo.DimCustomer, dbo.DimDate, dbo.DimProduct, dbo.Factinternet sales.

3. Clean the table to remove any unnecessary coloumns, nulls and blanks. Also from the calendar and sales select sales from 2022.

(Sql Scripts attached)

snap of customer table-
![image](https://github.com/user-attachments/assets/6f38bf51-858a-4d74-aa34-5c130347ddb8)


4. Save the result as csv file this is the data we will be working with.
(CSV files also attached)

snap of Customer table CSV-
![image](https://github.com/user-attachments/assets/229eafe6-8ef2-4c14-9c32-133c0f2d599b)


5. Load the data in power BI and open power query. Also load the budget file. Set the necesssary data types and look for any anomalies and blank. Also I've grouped the fact table and dimensions table seperately for a clean picture.

6. Create the schema defining relations. FactInternet sales table is being used as base and other table are connected to it in a one to many relation. Also budget is connected in the same way to calendar to map the date with sales and budget.

note- defining the relation between date of dim_calendar and date of budget table was one of the challenge I faced as the data was mapped in one to one bi-directionally.


snap-

![image](https://github.com/user-attachments/assets/60c3891c-b831-4698-90b4-f2e02ec7c2f8)


7. Now we have our data cleaned and we have our schema defined. We are good to go and create visuals.



### Generating Visuals, Report and Insights provided

Now since we have cleaned and processed our data we are now ready to generate some insights and answer to some of question based on our datasets. The report created is of 3 pages. 

Page 1 is a Sales overview of how the company has performed over the past 2 years. Also sales have been compared against budget which paints an overall performance picture.

snap - 

![image](https://github.com/user-attachments/assets/00d39128-6aa6-475a-8bc2-408fea3088ef)


Page 2 deals with customer_details which provide information on our top customers.

snap - 

![image](https://github.com/user-attachments/assets/24a78b83-824f-4108-b329-4516cd08fe13)


page 3 deals with product overview. It gives us an idea of our most profitable and least profitable product.

snap-

![image](https://github.com/user-attachments/assets/f0da5613-71d3-4af9-ac1f-31d272aa306d)



These details can be further filtered by city, category, sub category, year and month.


Dax used-

Budget Variance = [Sales] - [BudgetAmount]

BudgetAmount = SUM(Fact_Budget[Budget])

Sales = SUM('FACT_InternetSales Table_Cleaned'[SalesAmount])

sales/budget = DIVIDE([Sales],[BudgetAmount])






### Analysis on insights provided

1. Sales and total BudgetAmount are negatively correlated with each other.

Sales and BudgetAmount diverged the most when the MonthShort was Jun, when Sales were 1533177.78 higher than BudgetAmount.

Bikes had the highest Sales at 1551225.44, followed by Accessories at 62526.89 and Clothing at 29425.45.

Across all 102 Product Name, Sales ranged from 161.82 to 98684.57.

2. At 1874360.29, Dec had the highest Sales and was 143.00% higher than Feb, which had the lowest Sales at 771348.74.

Dec accounted for 11.46% of Sales.


Sales was highest for JordanTurner at 11484.33, followed by MauriceShan and JanetMunoz.

Across all 15,409 Customers, Sales ranged from 2.29 to 11484.33.

3. Mountain-200 Black, 42 had the highest Sales at 674727.06, followed by Mountain-200 Silver, 38 and Mountain-200 Black, 38. Racing Socks, L had the lowest Sales at 2049.72.

Across all 102 Products, Sales ranged from 2049.72 to 674727.06.





## Appendix

The dataset is purely fictious and is used for analysis purpose, Adventure Works is a sample database provided by microsoft for analysis purpose. Lot of hardwork and understanding was required to create this report. Hope you read through all of it and like it.

For any suggession and addition of any section feel free to reach out to -

sarkarsiddhartha14@gmail.com

Finally, thanks for taking the time to read through the report, hope you enjoy it.

Thanks,
Siddhartha









 
