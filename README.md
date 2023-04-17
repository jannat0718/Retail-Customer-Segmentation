## Retail-Customer-Segmentations Case Study

**Problem statement**

*It is a business critical requirement to understand the value derived from a customer. RFM is a method used for analyzing customer value.Perform customer segmentation using RFM analysis. The resulting segments can be ordered from most valuable (highest recency, frequency, and value) to least valuable (lowest recency, frequency, and value). Identifying the most valuable RFM segments can capitalize on chance relationships in the data used for this analysis.*

**Data Source: kaggle**

**Approaches:**   

**Importing Libraries:**

The required libraries, such as pandas, numpy, operator, datetime, sklearn.preprocessing, seaborn, and matplotlib, are imported to perform data manipulation, analysis, and visualization.

**Loading Dataset**

The "Online Retail.xlsx" dataset is loaded using pandas and the initial structure of the dataset is examined with the .info() method.

**Data Cleaning:**

The dataset is checked for missing values and it is found that there are 1,454 missing values in the "Description" column and 135,080 missing values in the "CustomerID" column. Missing values in the "CustomerID" column are dropped, and then the dataset is checked for duplicate records. 5,225 duplicate records are found and removed from the dataset.

**Descriptive Analytics:**

Some descriptive statistics are calculated, such as the total number of unique customers (4,372) and the number of unique countries (37). The number of customers per country is also calculated, and it is found that the United Kingdom has the most customers (3,950).

**Data Transformation:**

Cohort analysis is performed to understand customer behavior by grouping customers based on their first purchase month. A cohort is a group of subjects who share a defining characteristic. We can observe how a cohort behaves across time and compare it to other cohorts. The dataset is modified to include 'order_month' and 'cohort' columns. A pivot table is created to show the number of active customers in each cohort, and the retention matrix is calculated to show the retention rates of customers.

**RFM Model:**

An RFM model was built to analyze customer value by calculating Recency, Frequency, and Monetary metrics for each customer. The objective of this analysis is to understand customer behavior and identify potential areas for improving customer relationships. **Recency** is about when was the last order of a customer. It means the number of days since a customer made the last purchase. If it’s a case for a website or an app, this could be interpreted as the last visit day or the last login time. **Frequency** is about the number of purchase in a given period. It could be 3 months, 6 months or 1 year. So we can understand this value as for how often or how many a customer used the product of a company. The bigger the value is, the more engaged the customers are. Customer Engaement level dose not necceaasyly indicate if the customer is VIP or not beause we also have to think about how much they actually paid for each purchase, which means monetary value. **Monetary** is the total amount of money a customer spent in that given period. Therefore big spenders will be differentiated with other customers such as MVP or VIP.

    a. Calculation of RFM metrics:

        i. Calculated Recency as the time in no. of days since last transaction

        ii. Calculated Frequency as  count of purchases done 

        iii. Calculated Monetary value  as total amount spend 

    b. Built RFM Segments:

        i. Gave Recency, Frequency and Monetary scores individually by dividing them in to quartiles. "Recency" for customer who 
        have been active more recently better than the less recent customer, because each company wants its customers to be recent.
        In addition, "Frequency" and "Monetary Value" higher label because we want customer to spend more money and visit more often.

        ii. Combined three ratings to get a RFM segment as strings.

        iii. Calculated the RFM score by adding up the three ratings.

    c. Analysed the RFM Segments by summarizing them .

**4. Created clusters using K means Clustering Algorithm.**

    a.Prepared the data for the algorithm.

        i.Checked if the data is Un-Symmetrically distributed,then managed the skewness with appropriate transformation.

        ii.Standardized / scaled the data.

    b.Found out the optimum number of clusters to be formed.
    
    c.Analysed these clusters and plotted the results.

