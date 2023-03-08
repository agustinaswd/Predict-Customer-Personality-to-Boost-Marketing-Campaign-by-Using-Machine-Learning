# Predict Customer Personality to Boost Marketing Campaign by Using Machine Learning
This is my 3rd mini project from Data Science Bootcamp at Rakamin Academy. You can chech [here](https://speakerdeck.com/agustinaswd/predict-customer-personality-to-boost-marketing-campaign-by-using-machine-learning) for the **slide**.

## Background
A company can rapidly develop when it knows its customer personality behavior, so it can provide better services and benefits to customers who have the potential to become loyal customers. By processing historical marketing campaign data to improve performance and target the right customers so they can transact on the company's platform, from this data insight, our focus is to create a cluster prediction model to make it easier for companies to make decisions.

## Content
- Conversion rate analysis<br />
Conversion rate analysis is a search for insight into the percentage of website visitors and what actions they take while visiting the site, and whether their actions result in a purchase transaction or not while visiting the website.<br />
- Clustering with Kmeans
- Cluster Summary & Recommendation

## Analysis Data
### Data Info
- 2240 total row & 30 total columns.
- Income column missing 24 rows.
- Need to adjust data type for Dt_Customers, change it to datetime.

### Feature Engineering
- Age
- Total Kids
- Marital Status
- Is Parents
- Total Spending
- Total Accepted Campaign
- Total Transaction
- Conversion Rate
- Age Group

### Exploratory Data Analysis
**Multivariate Analysis**
![correlation](https://user-images.githubusercontent.com/116469338/223867670-7936e70e-db71-426f-90c8-62ca99b14b9f.png)
![Income vs Age](https://user-images.githubusercontent.com/116469338/223868483-25de0184-5878-443f-bb82-34e3c26669dc.png)
![Age vs Total Spending)](https://user-images.githubusercontent.com/116469338/223868490-7cd331b5-be51-45dc-b930-08298c784c32.png)
![Age vs Conversion Rate](https://user-images.githubusercontent.com/116469338/223868493-d9b57ac6-211b-4893-a316-8433feb73445.png)
![Conversion Rate vs Total Spending](https://user-images.githubusercontent.com/116469338/223868496-bc4e519f-ce4f-4f2c-9e0b-29c6e46ae0c0.png)
![Conversion Rate vs Income](https://user-images.githubusercontent.com/116469338/223868503-2a29ac90-d5e2-4230-ad09-62c844ac2a90.png)
![Income vs Total Spending](https://user-images.githubusercontent.com/116469338/223868506-e3656a48-b40d-4eb8-b648-093d19f37212.png)

### Insight 
- The greater the income, the greater the convention rate that a customer has.
- The greater the income, the greater the total spending customers spend on our platform.
- The relationship between total spending and the convention rate is also linear. 
- The greater the total spending, the greater the convention rate.No specific age describes "certain ages have a higher convention rate.“

### Recommendation
The greater the income, the greater the convention rate. We can target customers whose income is higher (60.000.000) and we will give them the more specific campaign

### Data Cleaning
- Missing Value: Column Income has 24 missing value, we will drop it.<br />
- Duplicated Value: There's no duplicated Values
- Drop Column which are not needed:'Unnamed: 0','ID','Year_Birth', 'Dt_Customer','Kidhome','Teenhome', 'Complain','Z_CostContact','Z_Revenue', 'Response','Marital_Status'

### Data Preprocessing
**Feature Encoding**
Encoding strategy:<br />
- label encode: Education
- One Hot Encoding: MaritalStatus, AgeGroup

**Feature Standardisation**

### Data Modeling
**Elbow Method**
![elbow method)](https://user-images.githubusercontent.com/116469338/223869673-3eea4409-701f-47ac-bc9f-cac73c772b89.png)<br />
**We choose to use 3 clusters for this model**<br />
Use RFM Analysis for feature selection to find the best clustering
- (Recency) Recency: The last time the customer made a transaction.
- (Frequency) Conversion Rate: Frequency of transactions / visit made by the Customer.
- (Monetary) Income: Customers’ revenue

**Sillhouette Score**
![shilluette](https://user-images.githubusercontent.com/116469338/223869671-3c506f97-75d0-4b1c-ae9d-e35a1302c3d3.png)<br />
We can see that the clustering with 4 and 6 clusters has a slightly higher score than clustering with 3 clusters. But, the number of 3 clusters will produce a better group in providing insights for the business/marketing team to improve the company's business. So, we still choose to cluster with 3 cluster.s<br />

**PCA**
![PCA)](https://user-images.githubusercontent.com/116469338/223869660-50e78dc4-57ea-4b8e-b14b-056867933db0.png)
Clusters:<br />
2: High Spender<br />
1: Low Spender<br />
0: Risk of Churn<br />

### Cluster Summary
**Cluster 2 (High Spender)**
- Have 873 customers
- Senior Adults (>55 years old)is the domination(226 customers)
- Customers with the highest income (IDR 81 million in a year) and total spending (IDR 1.3 million per year)
- The second highest recency
- The highest conversion rate
- The lowest number of the website visit
- The lowest number of deals/promo purchase
- Is the Customer Champions

**Cluster 1 (Low Spender)**
- Have 877 customers
- Middle Adults (36-55 years old) is the dominant (497 customers)
- Customers with the lowest income (IDR 44 million per year) and total spending (IDR 400K per year)
- The lowest recency
- The lowest conversion rate
- The highest number of the website visit
- The second highest number of deals/promo purchase
- Is the Customer Need Attention

**Cluster 0 (Risk of Churn)**
- Have 466 customers
- Middle Adults (>55 years old)is the domination (454 customers)
- Customers who are at the second highest income (IDR 45 million per year) and total spending (IDR 427K per year)
- The highest recency
- The second highest conversion rate
- The second highest number of the website visit
- The highest number the deals/promo purchase
- Is the Customer At Risk

### Recommendations
- Must maintain our High Spender Customers. We can make a special promo for customers in this cluster so they don't churn
- The Low Spender and Risk of Churn clusters are the group that often visit our website but rarely buy. This case happened maybe cause their promo is not suitable for them. We need to do more analysis to know why this case happened
