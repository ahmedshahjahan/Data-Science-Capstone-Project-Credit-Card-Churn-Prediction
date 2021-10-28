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
