**CREDIT CARD CUSTOMER ATTRITION (CHURN) PREDICTION**

**Introduction**

Building a predictive churn model helps us make proactive changes to the retention efforts that drive down churn rates. Understanding how churn impacts the current revenue goals and making predictions about how to manage those issues in the future also helps us stem the flow of churned customers. The ability to predict that a particular customer is at a high risk of churning, while there is still time to do something about it, represents a huge additional potential revenue source for every online business. To gain revenue and retain customers flow, I have selected my capstone project topics as “Credit Card Customer Attrition (Churn) Prediction”.

**Problem Statement**
Predict the credit card customer attrition rate and find the potential churning customers by analyzing data for a specific period (last twelve month) of time to minimize churn rate by providing better service for company’s growth and financial stability.

**Description of Attributes**
By importing necessary libraries and loading the downloaded dataset ‘BankChurners.csv’, I have observed that there are total of 21 attributes. The description of attributes is given below:

CLIENTNUM: Client number. Unique identifier for the customer holding the account

Attrition_Flag: Internal event (customer activity) variable - if the account is closed then 1 else 0

Customer_Age: Demographic variable - Customer's Age in Years

Gender: Demographic variable - M=Male, F=Female

Dependent_count: Demographic variable - Number of dependents

Education_Level: Demographic variable - Educational Qualification of the account holder (example: high school, college graduate, etc.)

Marital_Status: Demographic variable - Married, Single, Divorced, Unknown

Income_Category: Demographic variable - Annual Income Category of the account holder (< 40K,40K,40K - 60K, 60K−60K−80K, 80K−80K−120K, >

Card_Category: Product Variable - Type of Card (Blue, Silver, Gold, Platinum)

Months_on_book: Period of relationship with bank

Total_Relationship_Count: Total no. of products held by the customer

Months_Inactive_12_mon: No. of months inactive in the last 12 months

Contacts_Count_12_mon: No. of Contacts in the last 12 months

Credit_Limit; Credit Limit on the Credit Card

Total_Revolving_Bal: Total Revolving Balance on the Credit Card

Avg_Open_To_Buy: Open to Buy Credit Line (Average of last 12 months)

Total_Amt_Chng_Q4_Q1: Change in Transaction Amount (Q4 over Q1)

Total_Trans_Amt: Total Transaction Amount (Last 12 months)

Total_Trans_Ct: Total Transaction Count (Last 12 months)

Total_Ct_Chng_Q4_Q1: Change in Transaction Count (Q4 over Q1)

Avg_Utilization_Ratio: Average Card Utilization Ratio

**Dataset Summary**
The dataset had initially 10135 observations and 21 attributes. I have deleted the unnecessary ‘CLIETNUM’ columns and renamed the necessary attributes for simplicity. The index of the dataset is range index and columns are mixed with numerical and categorical values. Among the rest 20 attributes, 7 columns contain categorical values, and 14 columns contain numerical values. Broadly speaking 40% of the columns data types are ‘int64’, 30% of the columns data type is ‘float64’, and the rest 30% of the columns data types are ‘object’.
![image](https://user-images.githubusercontent.com/79649430/139185564-6a88c18a-607e-47a6-80f8-19277974bf20.png)

**Visualizing the Distribution of Numerical Attributes**
The histogram of any numerical column will depict the visual distribution of values of that column. The figure below shows the distribution of numerical columns by using histogram. By observing histogram its clear that some of the numerical columns are continuous and the rest are discrete. The columns ‘Dependent_Count’, ‘Total_Relationship_Count’, ‘Months_Inactive’, ‘Contacts_Count’ columns are discrete. Among those discrete columns the values of ‘Dependent_Count’ and ‘Contacts_Count’ columns are normally distributed and the other two columns have no trend or skewness. The rest numerical columns are continuous and among them the 'Total_Amt_Chng_Q4_Q1', 'Total_Ct_Chng_Q4_Q1', and the ‘Age’ columns are also normally distributed. The values of ‘Total_Trans_Count’ column shows bimodal distribution. The values of the ‘Credit_Limit’, ‘Avg_Utilization_Ratio’, and ‘Average_Open_To_Buy’ columns are skewed to the right. The peak count value of those three columns at ‘0’ clearly shows us that a significant amount customer is not utilizing their credits at all. The ‘Total_Revolving_Bal’ column shows that also a huge number of customers utilizes all their credit limit and does not have any balance to spend. By observing the ‘Total_Trans_Amt’ column it is clear that most of the customers spending is in between 0 and 5000 USD for 12-month duration period. 
![image](https://user-images.githubusercontent.com/79649430/139188748-a19bae48-028c-4a86-9065-16824e26548d.png)

The figure below shows the comparison between the theoretical cdf with empirical cdf. I have used this visualization to more precisely make a conclusion about the distribution of numerical columns whether it is normally distributed or not. It is clearly visible that the continuous numerical columns 'Age', ‘'Total_Amt_Chng_Q4_Q1', 'Total_Ct_Chng_Q4_Q1', and in the dataframe are approximately normally distributed and the rest are not normally distributed. Also, the discrete numerical columns 'Dependent_Count', 'Total_Relationship_Count', 'Months_Inactive', 'Contacts_Count' are also approximately normally distributed.

![image](https://user-images.githubusercontent.com/79649430/139188859-8bf7df42-ebb7-41b7-9835-dbcf1fcb0cde.png) ![image](https://user-images.githubusercontent.com/79649430/139188888-1892ed5a-74f8-474c-aed6-3ec574189873.png) 
![image](https://user-images.githubusercontent.com/79649430/139188929-ba706dc0-943f-4035-87d2-7266393eb13d.png) ![image](https://user-images.githubusercontent.com/79649430/139188967-80dcb100-c2c1-4177-8d18-6241790dceac.png)


