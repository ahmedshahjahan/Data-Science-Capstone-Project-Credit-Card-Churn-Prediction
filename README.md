**CREDIT CARD CUSTOMER ATTRITION (CHURN) PREDICTION**

Building a predictive churn model helps us make proactive changes to the retention efforts that drive down churn rates. Understanding how churn impacts the current revenue goals and making predictions about how to manage those issues in the future also helps us stem the flow of churned customers. The ability to predict that a particular customer is at a high risk of churning, while there is still time to do something about it, represents a huge additional potential revenue source for every online business. To gain revenue and retain customers flow, I have selected my capstone project topics as “Credit Card Customer Attrition (Churn) Prediction”.

**1. Problem Statement**

Predict the credit card customer attrition rate and find the potential churning customers by analyzing data for a specific period (last twelve month) of time to minimize churn rate by providing better service for company’s growth and financial stability.

**2. Description of Attributes**

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

![Pie_Chart](https://user-images.githubusercontent.com/79649430/139298701-ab86c9bc-5d26-4cba-a164-5898a01cf0fd.png)

**3. Exploratory Data Analysis**

**Visualizing the Distribution of Numerical Attributes**

The histogram of any numerical column will depict the visual distribution of values of that column. The figure below shows the distribution of numerical columns by using histogram. By observing histogram its clear that some of the numerical columns are continuous and the rest are discrete. The columns ‘Dependent_Count’, ‘Total_Relationship_Count’, ‘Months_Inactive’, ‘Contacts_Count’ columns are discrete. Among those discrete columns the values of ‘Dependent_Count’ and ‘Contacts_Count’ columns are normally distributed and the other two columns have no trend or skewness. The rest numerical columns are continuous and among them the 'Total_Amt_Chng_Q4_Q1', 'Total_Ct_Chng_Q4_Q1', and the ‘Age’ columns are also normally distributed. The values of ‘Total_Trans_Count’ column shows bimodal distribution. The values of the ‘Credit_Limit’, ‘Avg_Utilization_Ratio’, and ‘Average_Open_To_Buy’ columns are skewed to the right. The peak count value of those three columns at ‘0’ clearly shows us that a significant amount customer is not utilizing their credits at all. The ‘Total_Revolving_Bal’ column shows that also a huge number of customers utilizes all their credit limit and does not have any balance to spend. By observing the ‘Total_Trans_Amt’ column it is clear that most of the customers spending is in between 0 and 5000 USD for 12-month duration period. 

![Histogram](https://user-images.githubusercontent.com/79649430/139299060-17de9c67-e804-4a66-8489-d259c2fd2b37.png)
![Boxplot](https://user-images.githubusercontent.com/79649430/139299087-8304bccf-fc00-47ec-9cc8-ec7c02f2e0fe.png)


The figure below shows the comparison between the theoretical cdf with empirical cdf. I have used this visualization to more precisely make a conclusion about the distribution of numerical columns whether it is normally distributed or not. It is clearly visible that the continuous numerical columns 'Age', ‘'Total_Amt_Chng_Q4_Q1', 'Total_Ct_Chng_Q4_Q1', and in the dataframe are approximately normally distributed and the rest are not normally distributed. Also, the discrete numerical columns 'Dependent_Count', 'Total_Relationship_Count', 'Months_Inactive', 'Contacts_Count' are also approximately normally distributed.

![ECDF_of_Age_Column](https://user-images.githubusercontent.com/79649430/139299171-650e9322-4542-4cbf-a4e6-c712f95bcf95.png)
![ECDF_of_Total_Ct_Chng_Q4_Q1_Column](https://user-images.githubusercontent.com/79649430/139299297-4ca0e0b7-b0d9-4fad-b580-d0017eb488e7.png)
![ECDF_of_Total_Relationship_Count_Column](https://user-images.githubusercontent.com/79649430/139299337-d8e3675d-4000-4b09-8752-5a2dbeb76c5e.png)
![ECDF_of_Avg_Open_To_Buy_Column](https://user-images.githubusercontent.com/79649430/139299213-e3182ed5-2313-4245-b30a-4cf646601d6e.png)
![ECDF_of_Dependent_Count_Column](https://user-images.githubusercontent.com/79649430/139299239-68dfa922-81bb-41fd-a1fd-5b50380b27ef.png)
![ECDF_of_Months_On_Book_Column](https://user-images.githubusercontent.com/79649430/139299265-084f7931-f08d-4080-8b16-7829b8a6fe6a.png)
![ECDF_of_Total_Amt_Chng_Q4_Q1_Column](https://user-images.githubusercontent.com/79649430/139299280-7e23cccb-5e1b-4517-8b08-0de13ed7a84e.png)


**Detecting and Removing Outliers**

Boxplot is an essential visualization type for detecting outlier of a numerical column. Figure below shows the boxplot of few numerical columns and the visualization of standard deviation-based outlier detection. To accurately detect and correct the columns that contain outlier value I have used standard deviation-based outlier detection. If the distribution of values in a particular column is above or below the Mean±3*Standard_Deviation the column contain outlier and it must be removed to get better classification accuracy. By observing the histogram and vertical lines (Mean,  Mean±3*Standard_Deviation) its visible that the numerical columns 'Months_Inactive', 'Contact_Count', 'Total_Amt_Chng_Q4_Q1', 'Total_Trans_Amt', 'Total_Ct_Chng_Q4_Q1' contains significant outliers. Finally, I have removed those outlier values from the dataset without the discrete 'Months_Inactive', and 'Contact_Count' columns. The result of outlier value removal creates few ‘NaN’ entries in the dataset and those null values have further removed from the dataset.

![Visualizing_Outlier_of_Total_Trans_Amt_Column](https://user-images.githubusercontent.com/79649430/139299541-29306cfe-79d2-49df-bc9c-0d16235af57a.png)
![Visualizing_Outlier_of_Total_Ct_Chng_Q4_Q1_Column](https://user-images.githubusercontent.com/79649430/139299575-f1736a89-86a9-4185-8ae0-29a447f84269.png)
![Visualizing_Outlier_of_Total_Amt_Chng_Q4_Q1_Column](https://user-images.githubusercontent.com/79649430/139299599-e246eba0-4376-4c74-80b9-861d15a33c78.png)
![Visualizing_Outlier_of_Age_Column](https://user-images.githubusercontent.com/79649430/139299622-62dbcaf9-1806-46fc-821a-139434bd6de4.png)
![Visualizing_Outlier_of_Months_Inactive_Column](https://user-images.githubusercontent.com/79649430/139299651-f8534083-6428-49cb-9475-3967e7b02595.png)

**Detecting and Removing Correlations**

Heatmaps are used to show relationships between two variables, one plotted on each axis. By observing how cell colors change across each axis, we can observe if there are any patterns in value for one or both variables. By observing the output of heatmap it is clearly visible that there is a significantly high positive correlations between the 'Credit_Limit' and 'Avg_Open_To_Buy' columns and the Pearson correlation coefficient value is 0.9958. Also, there is a positive and negative correlation between few other columns also.

![Heatmap](https://user-images.githubusercontent.com/79649430/139299406-8f2a88d9-0635-4769-b694-7189d81fc47b.png)
![High_Correlated_Columns](https://user-images.githubusercontent.com/79649430/139301123-9d399c70-34bb-4255-a45a-0a65adcd1975.png)


**Visualizing the Distribution of Categorical Attributes**

The figures below show the count plot which visualizes the distribution of categorical columns. The 'Card_Category' column contains class imbalance data.

![Count_Plot_of_Attrition_Flag_Column](https://user-images.githubusercontent.com/79649430/139300882-ce2690dd-b0d2-4e90-8d06-ab48bf2d3503.png)
![Count_Plot_of_Card_Category_Column](https://user-images.githubusercontent.com/79649430/139300903-4e9c5d09-dce8-41de-8f3f-a7de350ae031.png)
![Count_Plot_of_Income_Column](https://user-images.githubusercontent.com/79649430/139300964-a683e7aa-1882-4751-b2ef-029186008f4c.png)
![Count_Plot_of_Education_Column](https://user-images.githubusercontent.com/79649430/139300921-64cbd517-ceea-48fe-a120-f9105e40d137.png)
![Count_Plot_of_Marital_Status_Column](https://user-images.githubusercontent.com/79649430/139300996-13c26e05-20a6-4004-93e0-24885a445e64.png)
![Count_Plot_of_Gender_Column](https://user-images.githubusercontent.com/79649430/139301018-65abf346-af46-4c08-a7c7-75e1bd1c5dca.png)


**4. Preprocessing and Training Data Development**

Data preprocessing is an integral step in Machine Learning as the quality of data and the useful information that can be derived from it directly affects the ability of our model to learn; therefore, it is extremely important to preprocess the data before feeding it into our model. The steps I followed for preprocess the data is given below:

Encoded the target attribute ‘Attrition_Flag’ to binary 1 and 0. I have encoded the binary ‘1’ for 'Attrited Customer' and binary ‘0’ for 'Existing Customer'. The main goal of the classification algorithms is to find the possible 'Attrited Customer' or is to predict ‘1’.

Separated the target/dependent variable y, and the predictor/Independent variables X from the dataset.

Split the data (X and y) into train and test with default test size of 0.25 for performing training and evaluation for each classifier. After splitting the shape of the X_train, X_test, y_train, and y_test respectively (7108, 19), (2370, 19), (7108,), and (2370,)

I have used StandardScaler as scaling function for training and test set separately because StandardScaler removes the mean and scales each feature/variable to unit variance. This operation is performed feature-wise in an independent way. I have used scaling function because the numerical columns of the dataset still contained outliers and the range of each individual columns are different. A significant number of observations are below numerical value 1 and some are above 35000.

**5. Modeling**

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

**Classification Algorithms and Evaluation Results**

To find the best classifier algorithm to predict the possible churning customer I have used different classification algorithms including KNN, Logistic Regression, Decision Tree. Support Vector Machines, Random Forest, Gradient Boosting, and XGBoost Classifiers. For each of those classification algorithms, I have used hyperparameter tuning by using the randomized search cv with cv=5 to get the best model. The result of the randomized search cv outputs the best parameter of the model. By using those parameters, I have trained the training data and evaluated the test data to measure model performance. The table and figure below for each classifier shows the final outcomes of the corresponding model, the confusion matrix, and the ROC curve.

<img width="487" alt="Screenshot 2021-10-28 105220" src="https://user-images.githubusercontent.com/79649430/139281349-56bab588-e87f-4fc3-869d-a23999620c8e.png">

**Optimum Model and Findings**

Among all, the XGBoost Classifier performed well based on the several model evaluation metrics I have used. The resultant summary of XGBoost classifier is Precision Score: 0.935, Recall Score: 0.909, Training Accuracy: 0.999, Test Accuracy: 0.974, F1 Score: 0.974, Area Under ROC: 0.994. To predict all possible churning customer accurately or to get a model that will have low false negatives, I have used the metric ‘Recall’ as my main evaluation metric. A good classification model should have a high recall value to classify all possible churning customers. Despite the target attribute of my model contained class imbalance data, the ‘Recall’ value of 0.909 or 91% indicates that my model worked well on predicting possible churning customers. Also, the ‘F1 Score’ of 0.974 and the Area under roc curve of 0.994 indicates that my model performed well.

<img width="494" alt="Screenshot 2021-10-28 105822" src="https://user-images.githubusercontent.com/79649430/139282533-fb258387-244f-4dd4-a2e0-f7bdb53989b3.png">

**Conclusion and Future Work**

The target attributes have class imbalance data, and approximately 16% of the customers are labeled with ‘Attrited Customer’ and the remaining 84% customers are labeled with ‘Current Customer’. Despite of the class imbalance, the ‘Recall’ value of 0.909 or 91%, ‘F1 Score’ of 0.974, and AUROC of 0.994 indicates that the XGBoost classifier accurately predicted the possible churning customers. There are also few correlations, and outliers in the dataset, and for that my model did not get 100% accuracy on all of the metrics. Spending more time on preprocessing to tackle those issues will be helpful to get better accuracy on each of the evaluation metrics I have used.






