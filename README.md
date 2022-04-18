# Retail-Customer-Segmentation

**Problem statement
It is a business critical requirement to understand the value derived from a customer. RFM is a method used for analyzing customer value.
Perform customer segmentation using RFM analysis. The resulting segments can be ordered from most valuable (highest recency, frequency, and value) to least valuable (lowest recency, frequency, and value). Identifying the most valuable RFM segments can capitalize on chance relationships in the data used for this analysis.**

**Approach:**   

**1.Performed a preliminary data inspection and Data cleaning**

    a.Checked for missing data and formulated apt strategy to treat them.

    b.Checked for the duplicate data records and remove them if present.

    c.Performed Descriptive analytics on the given data.


**2.Cohort Analysis:**

*Note: A cohort is a group of subjects who share a defining characteristic. We can observe how a cohort behaves across time and compare it to other cohorts.* 

    a.Createed month cohorts and analysed active  customers for each cohort.

    b.Analysed the retention rate of customers.

**3.Built a RFM model – Recency Frequency and Monetary based on customer purchase behaviour.**

*Note: Recency is about when was the last order of a customer. It means the number of days since a customer made the last purchase. If it’s a case for a website or an app, this could be interpreted as the last visit day or the last login time.*

*Frequency is about the number of purchase in a given period. It could be 3 months, 6 months or 1 year. So we can understand this value as for how often or how many a customer used the product of a company. The bigger the value is, the more engaged the customers are.Customer Engaement level dose not necceaasyly indicate if the customer is VIP or not beause we also have to think about how much they actually paid for each purchase, which means monetary value.*

*Monetary is the total amount of money a customer spent in that given period. Therefore big spenders will be differentiated with other customers such as MVP or VIP.*

    a.Calculation of RFM metrics:

        i.Calculated Recency as the time in no. of days since last transaction

        ii.Calculated Frequency as  count of purchases done 

        iii.Calculated Monetary value  as total amount spend 

    b.Built RFM Segments:

        i.Gave Recency, Frequency and Monetary scores individually by dividing them in to quartiles.

        Note:Rate "Recency" for customer who have been active more recently better than the less recent customer, because each company wants its customers to be recent Rate "Frequency" and "Monetary Value" higher label because we want customer to spend more money and visit more often.

        ii.Combined three ratings to get a RFM segment as strings.

        iii.Calculated the RFM score by adding up the three ratings.

    c.Analysed the RFM Segments by summarizing them .

**4.Created clusters using K means Clustering Algorithm.**

    a.Prepared the data for the algorithm.

        i.Checked if the data is Un-Symmetrically distributed,then managed the skewness with appropriate transformation.

        ii.Standardized / scaled the data.

    b.Found out the optimum number of clusters to be formed.
    c.Analysed these clusters and plotted the results.

