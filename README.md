## Retail-Customer-Segmentations Case Study

**Problem statement**

*It is a business critical requirement to understand the value derived from a customer. RFM is a method used for analyzing customer value.Perform customer segmentation using RFM analysis. The resulting segments can be ordered from most valuable (highest recency, frequency, and value) to least valuable (lowest recency, frequency, and value). Identifying the most valuable RFM segments can capitalize on chance relationships in the data used for this analysis.*

**Introduction:**

This report presents an analysis of an Online Retail dataset containing information on various transactions from December 2010 to December 2011. The dataset contains information such as InvoiceNo, StockCode, Description, Quantity, InvoiceDate, UnitPrice, CustomerID, and Country. The dataset is collected from the Kaggle.

**Importing Libraries:**

The required libraries, such as pandas, numpy, operator, datetime, sklearn.preprocessing, seaborn, and matplotlib, are imported to perform data manipulation, analysis, and visualization.

**Loading Dataset:**

The "Online Retail.xlsx" dataset is loaded using pandas and the initial structure of the dataset is examined with the .info() method.

**Data Cleaning:**

The dataset is checked for missing values and it is found that there are 1,454 missing values in the "Description" column and 135,080 missing values in the "CustomerID" column. Missing values in the "CustomerID" column are dropped, and then the dataset is checked for duplicate records. 5,225 duplicate records are found and removed from the dataset.

**Descriptive Analytics:**

Some descriptive statistics are calculated, such as the total number of unique customers (4,372) and the number of unique countries (37). The number of customers per country is also calculated, and it is found that the United Kingdom has the most customers (3,950). Also, 69.97% of customers ordered more than one item.

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

        ii. Combined three ratings to get a RFM segment as strings: After the quartile values are assigned, the code calculates the 
        RFM score for each customer by concatenating the quartile values for recency, frequency, and monetary metrics such as "111"
        for the best customers, "444" for the lost cheap customers, and more.

        iii. Calculated the RFM score by adding up the three ratings: This RFM score helps in classifying customers into different
        segments, such as Best Customers, Loyal Customers, Big Spenders, Almost Lost, Lost Customers, and Lost Cheap Customers.
        
        iv. Created a pandas DataFrame with the customer segments, their corresponding RFM scores, and a description of each segment. 

**K means Clustering:**

        a. Selecte the relevant features: The frequency and monetary value columns of the segmented_rfm DataFrame are chosen for
        clustering.

        b. Data Standardized: Normalized the selected features using the StandardScaler() function, which standardizes the data by 
        transforming it to have zero mean and unit variance.

        c. Plotting: Visualized the distribution of the standardized frequency and monetary values using seaborn's distplot function.

        d. Elbow Method: Used the Elbow Method to find the optimal number of clusters (k). The method calculates the within-cluster 
        sum of square (WCSS) for different k values (ranging from 1 to 10). It then plots WCSS against the number of clusters. The 
        optimal k value is generally considered to be at the location of a bend (knee) in the plot. From the plot, I concluded that
        the optimal number of clusters is 4.

        e. Perform K-Means clustering: Performed the clustering with the 4 clusters.

        f. Visualization of customer cluster: Visualized the resulting customer clusters in a scatter plot. Each cluster represents
        a different type of customer:

                * Lost Customer (red): customers who haven't made a purchase recently
                * Loyal Customer (blue): customers who purchase frequently
                * Average Customer (green): customers with average spending and frequency
                * Bought frequently but spend less (cyan): customers who buy often but spend less on each purchase

**Results:**

1. From the RFM segmentation and analysis performed, we can conclude the following about the customers:

    a. Best Customers (RFM 111): These customers have bought the most recently, most often, and spend the most. They are the most valuable segment and should be the focus of retention and marketing efforts.

    b. Loyal Customers (X1X): These customers buy the most frequently. They may not spend the most, but their consistent purchases make them valuable. It's crucial to maintain a relationship with them and engage them with loyalty programs and personalized offers.

    c. Big Spenders (XX1): These customers spend the most on each purchase. It's essential to target them with upselling and cross-selling opportunities to maximize their spending.

    d. Almost Lost (311): These customers have not purchased for some time, but they previously purchased frequently and spent a significant amount. It's crucial to re-engage them with win-back campaigns and special offers to encourage them to return.

    e. Lost Customers (411): These customers haven't purchased for some time but previously purchased frequently and spent a considerable amount. Similar to the "Almost Lost" segment, win-back campaigns, and special offers are needed to re-engage them.

    f. Lost Cheap Customers (444): These customers last purchased a long time ago, made few purchases, and spent little. They represent the lowest value segment, and it may not be cost-effective to invest heavily in trying to win them back.

2. Based on the K-means clustering analysis, customers were divided into four segments:

    a. Lost Customers (Red): These customers have a low buying frequency and low total spending. They need to be targeted with win-back campaigns and offers to encourage repeat purchases and increase spending.

    b. Loyal Customers (Blue): These customers have high buying frequency and high total spending. They are the most valuable segment and should be prioritized in marketing and retention efforts.

    c. Average Customers (Green): These customers have average buying frequency and total spending. Efforts should be made to increase their purchase frequency and spending by engaging them with personalized offers and incentives.

    d. Bought Frequently but Spent Less (Cyan): These customers have a high buying frequency but low total spending. Upselling and cross-selling strategies can help increase their spending.
    
**Performance of the model:**

The K-means clustering model's performance in this analysis appears to be satisfactory. It successfully segmented customers into four distinct groups based on their buying frequency and total spending. The Elbow method was used to determine the optimal number of clusters, which turned out to be 4 in this case. The model captures the differences between various customer groups and helps to identify specific behaviors that can be targeted by marketing, sales, and customer service teams.

**Optimization recommendations:**

* Analyze additional features: The current model considers only buying frequency, total spending, and recency. Including more features such as average transaction value, or product categories might improve segmentation and provide better insights into customer behavior.

* Alternative clustering algorithms: Experiment with other clustering algorithms like DBSCAN or Agglomerative Clustering, which might reveal different structures in the data and provide more meaningful segmentation.

* Hyperparameter tuning: Experiment with different hyperparameters for the K-means algorithm, such as the number of iterations, initialization methods, or even the distance metric, to optimize the performance of the model.

**Overall conclusion:**

The K-means clustering model provided useful insights into the customer dataset, identifying distinct customer segments based on their buying frequency and total spending. By understanding these segments, businesses can tailor their marketing, sales, and customer service strategies to target each group more effectively, improving customer retention, satisfaction, and revenue generation. Further optimization and validation of the model could lead to even more actionable insights and better targeting of specific customer behaviors.



