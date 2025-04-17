# CUSTOMER-SEGMENTATION
# Data Analytics Customer Segmentation

## Goal of the project
This project aims to conduct a Customer Segmentation Analysis for an Automobile bike Company. Customer segmentation is performed by developing an RFM Model. RFM (Recency, Frequency, Monetary) analysis is a behavior-based approach that groups customers into segments. It groups the customers based on their previous purchase transactions. In this analysis, the customer segment was divided into 11 groups. The analysis will help determine which customer segments should be targeted to enhance sales revenue for the company. A <b>Sales Dashboard for Customer Segmentation</b> is developed using <b>Tableau</b> and the data quality assessment and analysis are done using <b>Python</b>.



<img src="data%20visualization/Sales%20Dashboard.gif" height="500" align="middle"><br>

<b>In case of failure of loading Jupyter Notebooks on Github, the following notebooks can be found in nbviewer. Click on the respective hyperlinks to view:</b>
- [RFM Analysis.ipynb](https://nbviewer.jupyter.org/github/AbhishekGit-hash/Data-Analytics-Customer-Segmentation/blob/master/RFM%20Analysis.ipynb)
- [DQA and Data Cleaning CustomerDemographic.ipynb](https://nbviewer.jupyter.org/github/AbhishekGit-hash/Data-Analytics-Customer-Segmentation/blob/master/DQA%20and%20Data%20Cleaning%20CustomerDemographic.ipynb)
- [DQA and Data Cleaning NewCustomerList.ipynb](https://nbviewer.jupyter.org/github/AbhishekGit-hash/Data-Analytics-Customer-Segmentation/blob/master/DQA%20and%20Data%20Cleaning%20NewCustomerList.ipynb)
- [DQA and Data Cleaning Transactions.ipynb](https://nbviewer.jupyter.org/github/AbhishekGit-hash/Data-Analytics-Customer-Segmentation/blob/master/DQA%20and%20Data%20Cleaning%20Transactions.ipynb)
- [DQA and Data Cleaning Customer Address.ipynb](https://nbviewer.jupyter.org/github/AbhishekGit-hash/Data-Analytics-Customer-Segmentation/blob/master/DQA%20and%20Data%20Cleaning%20Customer%20Address.ipynb)


## Analysis Approach
### 1. Data Quality Assessment and Data Cleaning
The first step towards generating useful insights from the data was the data preparation, quality assessment, and data cleaning step. After the cleaning process, exploratory data analysis on the dataset and identification of customer purchasing behaviours to generate insights can be performed.

In the data cleaning step, the data quality of the following datasets was first assessed. After a data quality assessment, the following data quality issues were observed, and the necessary process to mitigate the issue was followed :
- <b>CustomerDemographics.xlsx</b> :
  - 1 Irrelevant column was present, and such columns were dropped from the dataset.
  - There were 5 columns where Missing values were present. For such columns based on the volume of the missing values, either the records were dropped, or appropriate values were imputed atthe  places of missing values
  - For the gender column, there was no standardisation of data. Based on the values available, the column data was standardised to remove data inconsistency.
  - The Date of Birth column was transformed to create a new feature column 'Age' and 'Age Group' to check for discrepancies in age distribution. An <b>outlier</b> was observed, and the record was removed.
  - Checked whether there are duplicate records present in the dataset. In this dataset, there were no duplicate records.
- <b>NewCustomerList.xlsx</b> :
  - 5 Irrelevant columns were present, and such columns were dropped from the dataset.
  - There were 4 columns where Missing values were present. For such columns based on the volume of the missing values, either the records were dropped, or appropriate values were imputed at the places of missing values
  - The Date of Birth column was transformed to create a new feature column 'Age' and 'Age Group' to check for discripency of age distribution.
  - There was no data inconsistency.
  - Checked whether there are duplicate records present in the dataset. In this dataset, there were no duplicate records.
- <b>Transaction_data.xlsx </b>:
  - The product_first_sold_date column is not in datetime format. The data type of this column was changed from int64 to datetime format.
  - There were 7 columns where Missing values were present. For such columns based on the volume of the missing values, either the records were dropped or appropriate values were imputed at places of missing values
  - A new feature column 'Profit' was created, which is basically the difference between the list price and the standard price.
  - There was no data inconsistency.
  - Checked whether there are duplicate records present in the dataset. In this dataset, there were no duplicate records.
- <b>CustomerAddress.xlsx</b> :
  - For states column there was no standardisation of data. Based on the values available the column data was standardised to remove data inconsistency.
  - There were certain customer IDs from the Customer Demographics table that were getting dropped in the Address table.

### 2. Exploratory Data Analysis on Customer Segments
After the data cleaning process, exploratory analysis on the dataset is performed, and the following insights are obtained :
- <b>New vs Old Customers Age Distribution</b><br> 
  - Most New customers are aged between 40-49 Also, for Old Customers the most of them are aged between 40-49
  - The lowest number of customers for both types of customers is present in the age bracket under 20 and above 80 age groups.
  - The automobile company is popular among New Customers among the age groups 20-29 and 40-49. 
  - A steep drop in customers is observed in the 30-39 age group among the New Customers<br>
  <table>
  <tr>
    <td><b>Old Customers by Age Distribution</b></td>
    <td><b>New Customers by Age Distribution</b></td>
  </tr>
  <tr>
    <td><img src="data%20visualization/Old%20Customers%20Age%20Distribution.PNG" height="400" align="middle"></td>
    <td><img src="data%20visualization/New%20Customers%20Age%20Distribution.PNG" height="400" align="middle"></td>
  </tr>
  </table>
  
- <b>Bike purchases over last 3 years by Gender</b><br> 
  - Most bike purchases have been made by females over the last 3 years. Approximately 51% of the bike purchases are made by females compared to 49% of the purchases being done by Male.
  - The Female purchases are 10,000 more than those of Male purchases (numerically).
  <img src="data%20visualization/Female%20vs%20Male%20Bike%20Purchases.PNG" height="400" align="middle">
  
- <b>New vs Old Customers Job Industry Distribution</b><br> 
  - Most New customers are from the Manufacturing and Financial Services sector (approx 20% of the New Customers).
  - The lowest number of customers is from the Agriculture and Telecom sector approximately 3%.
  - A similar trend is observed among Old Customers as well.<br>
  <table>
  <tr>
    <td><b>Old Customers by Job Industry</b></td>
    <td><b>New Customers by Job Industry</b></td>
  </tr>
  <tr>
    <td><img src="data%20visualization/Old%20Customers%20Job%20Industry.PNG" height="400" align="middle"></td>
    <td><img src="data%20visualization/New%20Customers%20Job%20Industry.PNG" height="400" align="middle"></td>
  </tr>
  </table>

- <b>Wealth Segmentation by Age Category</b><br> 
  - Across all age categories, the largest number of customers is from the 'Mass Customer' Segment
  - The next category comes from the 'High Net Worth' customers.
  - In the age group 40-49, the Affluent segment outperforms the High Net Worth customers in terms of the number of customers.<br>
  <table>
  <tr>
    <td><b>Old Customers Wealth by Age Group</b></td>
    <td><b>New Customers Wealth by Age Group</b></td>
  </tr>
  <tr>
    <td><img src="data%20visualization/Old%20Customers%20Wealth%20Segment.PNG" height="400" align="middle"></td>
    <td><img src="data%20visualization/New%20Customer%20Wealth%20Segment.PNG" height="400" align="middle"></td>
  </tr>
  </table>

- <b>Cars owned by States</b><br> 
  - New South Wales has the largest number of people who do not own a car.
  - In Victoria, the proportion is quite even.
  - In Queensland, the number of people owning a car is greater than who donot have a car.
  <img src="data%20visualization/Car%20Owners%20by%20State.PNG" height="400" align="middle">


### 3. RFM Analysis and Customer Segmentation
In this stage of analysis, the customer segmentation was done by developing an RFM Model. The RFM (Recency, Frequency, Monetary) analysis is a behavior-based approach grouping customers into segments. It groups the customers on the basis of their previous purchase transactions.

In this analysis, the customer segment was divided into 11 groups. The groups are: 
- Platinum Customers
- Very Loyal Customers
- Recent Customers
- Potential Customers
- Lost Customers
- Losing Customers
- Late Bloomer
- High Risk Customers
- Evasive Customers
- Becoming Loyal
- Almost lost Customers

As of the current state of the Automobile business, the current distribution of customer segments is depicted below:
<img src="data%20visualization/Customer%20Segment%20Distribution.PNG" height="400" align="middle">

### 4. RFM Analysis: Scatter Plots
#### Recency vs Monetary :
The visualization shows that recent customers have purchased more products and generated relatively more revenue than the customers who visited a while ago.<br>
<img src="data%20visualization/Recency%20vs%20Monetary.PNG" height="400" align="middle"><br>

#### Frequency vs Monetary : 
The visualization shows that customers belonging to Platinum/ Very Loyal/ Becoming Loyal Customer Segments have a greater frequency and generate greater monetary value for the business<br>
<img src="data%20visualization/Frequency%20vs%20Monetary.PNG" height="400" align="middle"><br>

## Datasets Used
The datasets used include:
- __Raw_data.xlsx__: This Excel file dataset included the following sheets of data:
  -  __Transactions_data.xlsx__: This dataset included the transaction data of the customers across all the different states in Australia.
  -  __NewCustomerList.xlsx__: This dataset included the new customers who visited the automobile bike company recently.
  -  __CustomerDemographic.xlsx__: This dataset includedthe  entire details of the Customer Demographics.
  -  __CustomerAddress.xlsx__: This dataset included the address of the Customers.


## Tools and Technologies used
The tools used in this project include:
- __Python__ - This was needed to conduct <b>Data Quality Assessment</b> and also for <b>Data Cleaning processes</b>. With Python libraries <b>pandas, matplotlib, seaborn</b> exploratory data analysis of the datasets and to gain useful insights from the data was possible.



## Built With
- Python 3.8.2

## Authors
- DEEKSHITH REDDY NAREDDY- [Github Profile]
