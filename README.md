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
![image](https://user-images.githubusercontent.com/79649430/139188929-ba706dc0-943f-4035-87d2-7266393eb13d.png) ![image](https://user-images.githubusercontent.com/79649430/139188967-80dcb100-c2c1-4177-8d18-6241790dceac.png) ![image](https://user-images.githubusercontent.com/79649430/139189093-0b17d69d-ceeb-418e-8239-076ae1ac1edc.png) ![image](https://user-images.githubusercontent.com/79649430/139189121-225991b7-865b-43e6-8a73-a825c6689b31.png)

**Detecting and Removing Outliers**

Boxplot is an essential visualization type for detecting outlier of a numerical column. Figure below shows the boxplot of few numerical columns and the visualization of standard deviation-based outlier detection. To accurately detect and correct the columns that contain outlier value I have used standard deviation-based outlier detection. If the distribution of values in a particular column is above or below the Mean±3*Standard_Deviation the column contain outlier and it must be removed to get better classification accuracy. By observing the histogram and vertical lines (Mean,  Mean±3*Standard_Deviation) its visible that the numerical columns 'Months_Inactive', 'Contact_Count', 'Total_Amt_Chng_Q4_Q1', 'Total_Trans_Amt', 'Total_Ct_Chng_Q4_Q1' contains significant outliers. Finally, I have removed those outlier values from the dataset without the discrete 'Months_Inactive', and 'Contact_Count' columns. The result of outlier value removal creates few ‘NaN’ entries in the dataset and those null values have further removed from the dataset.

![image](https://user-images.githubusercontent.com/79649430/139189226-a047cd65-b6a6-4f51-8019-4058eba6b685.png)

![image](https://user-images.githubusercontent.com/79649430/139189262-84e4bf38-85bf-4d57-bf92-ebdcb718cdfc.png) ![image](https://user-images.githubusercontent.com/79649430/139189278-6e89cbf7-da54-472f-b6d0-c2df980adce9.png) ![image](https://user-images.githubusercontent.com/79649430/139189305-083cb888-243d-4f62-8d9d-11384439498d.png) ![image](https://user-images.githubusercontent.com/79649430/139189334-2c908f21-748f-4c52-a1d8-6ced7fac5495.png)

**Detecting and Removing Correlations**

Heatmaps are used to show relationships between two variables, one plotted on each axis. By observing how cell colors change across each axis, we can observe if there are any patterns in value for one or both variables. By observing the output of heatmap it is clearly visible that there is a significantly high positive correlations between the 'Credit_Limit' and 'Avg_Open_To_Buy' columns and the Pearson correlation coefficient value is 0.9958. Also, there is a positive and negative correlation between few other columns also.

![image](https://user-images.githubusercontent.com/79649430/139189433-80ed8f9f-3857-4be6-9622-ba63915124d6.png)

**Visualizing the Distribution of Categorical Attributes**

The figures below show the count plot which visualizes the distribution of categorical columns. The 'Card_Category' column contains class imbalance data.

![image](https://user-images.githubusercontent.com/79649430/139189564-d34dcf0a-56c2-4693-a645-d3f1cfc83da2.png) ![image](https://user-images.githubusercontent.com/79649430/139189583-58e026dd-540a-4b04-981c-e8b4cb54c0a6.png) ![image](https://user-images.githubusercontent.com/79649430/139189613-99f431c1-3b44-4e7f-9e82-b7e36b4713dd.png) ![image](https://user-images.githubusercontent.com/79649430/139189633-5e01a8fa-f448-402d-91a5-2687e6c970ad.png)

**Preprocessing and Training Data Development**

Data preprocessing is an integral step in Machine Learning as the quality of data and the useful information that can be derived from it directly affects the ability of our model to learn; therefore, it is extremely important to preprocess the data before feeding it into our model. The steps I followed for preprocess the data is given below:

Encoded the target attribute ‘Attrition_Flag’ to binary 1 and 0. I have encoded the binary ‘1’ for 'Attrited Customer' and binary ‘0’ for 'Existing Customer'. The main goal of the classification algorithms is to find the possible 'Attrited Customer' or is to predict ‘1’.

Separated the target/dependent variable y, and the predictor/Independent variables X from the dataset.

Split the data (X and y) into train and test with default test size of 0.25 for performing training and evaluation for each classifier. After splitting the shape of the X_train, X_test, y_train, and y_test respectively (7108, 19), (2370, 19), (7108,), and (2370,)

I have used StandardScaler as scaling function for training and test set separately because StandardScaler removes the mean and scales each feature/variable to unit variance. This operation is performed feature-wise in an independent way. I have used scaling function because the numerical columns of the dataset still contained outliers and the range of each individual columns are different. A significant number of observations are below numerical value 1 and some are above 35000.

**Modeling**

To predict the class or category we need to use the classification algorithm. The Classification algorithm’s function is to identify the category of new observations based on training data. In Classification, a program learns from the given dataset or observations and then classifies new observation into classes or groups. Such as, Yes or No, 0 or 1. In classification algorithm, a discrete output function(y) is mapped to input variable(x). 

**Evaluation Metrics for Model Evaluation**
Accuracy

Accuracy in classification problems is the number of correct predictions made by the model over all kinds of predictions made.

Precision

Precision in binary classification (Yes/No) refers to a model's ability to correctly interpret positive observations. In other words, how often does a positive value forecast turn out to be correct? We may manipulate this metric by only returning positive for the single observation in which we have the most confidence.

Recall

The recall is also known as sensitivity. In binary classification (Yes/No) recall is used to measure how “sensitive” the classifier is to detecting positive cases. To put it another way, how many real findings did we “catch” in our sample? We may manipulate this metric by classifying both results as positive. In our case recall is a measure that tells us what proportion of customer in the dataset that going to churn will diagnosed by the algorithm as possible churner. 

AUC-ROC curve

ROC curve stands for Receiver Operating Characteristics Curve and AUC stands for Area Under the Curve. It is a graph that shows the performance of the classification model at different thresholds. To visualize the performance of the multi-class classification model, we use the AUC-ROC Curve. The ROC curve is plotted with TPR and FPR, where TPR (True Positive Rate) on Y-axis and FPR(False Positive Rate) on X-axis.

F1 Score

The F1 score can be thought of as a weighted average of precision and recall, with the best value being 1 and the worst being 0. Precision and recall also make an equal contribution to the F1 ranking.










