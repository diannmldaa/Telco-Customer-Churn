# Telco Costumer Churn
## Use Case Summary
### Objective Statement
* Get an insight about the influence of gender on customer churn.
* Describe customer satisfaction seen from the length of their contract that affects customer churn.
* Get to know how much influence the Senior Citizen has on customer churn.
* Get to know how much influence the Dependents have on customer churn.
* Get to know how much influence Paperless Billing has on customer churn
* Get to know how important partners influence customer churn
* Get to know how important the type of InternetService to influence customer churn
* Get an insight about how much influence the Phone Services on customer churn
* Get an insight about how much influence the Online Security on customer churn
* Get an insight about how much influence the Online Backup on customer churn
* Get an insight about how much influence the Device Protection on customer churn
* Get an insight about how much influence the Tech Support on customer churn
* Get an insight about how much influence the StreamingTV on customer churn
* Get an insight about how much influence the Streaming Movie on customer churn
* Get an insight about how much influence the payment method on Customer Churn
* Create machine learning models to predict customers who will churn

### Challenges
* The data have a lot missing value
* There is data that has an inappropriate data type
* The data scale is not all the same

### Methodology / Analytic Technique
* Descriptive analysis
* Graph analysis
* Machine learning model (classification)

### Business Benefit
* Help marketing strategies to improve products or services so that customer churn can be reduced.
* Help find out which aspects need to be developed to reduce customer churn.

### Expected Outcome
* Knowing the influence of gender on customer churn.
* Knowing customer satisfaction seen from the length of their contract that affects customer churn.
* Get to know how much influence the Senior Citizen on customer churn.
* Get to know how much influence the Dependents on customer churn.
* Get to know how much influence the Paperless Billing on customer churn.
* Knowing how important partners influence customer churn.
* Knowing how important the type of InternetService to influence customer churn
* Get to know how much influence the Phone Services on customer churn.
* Get to know how much influence the Online Security on customer churn.
* Get to know how much influence the Online Backup on customer churn.
* Get to know how much influence the Device Protection on customer churn.
* Get to know how much influence the Tech Support on customer churn.
* Get to know how much influence the StreamingTV on customer churn.
* Get to know how much influence the Streaming Movie on customer churn.
* Gain an insight about how services affect the customer churn.
* Get to know how much influence the payment method on Customer Churn
* Making machine learning models to predict customers who will churn

## Business Understanding
**Customer Churn** refers to the loss of customers. Churn is intimately connected to a company’s performance. The more one learns about buyers’ behavior, the more money one can make. Analyzing customer churn also aids in finding and improving the shortcomings of services provided by the company. Customer churn rate must to be reduce so that the company's income increases

this case has some business question using the data:
* How gender affects customer churn?
* How does customer satisfaction see from the length of their contract affects customer churn?
* How important services to affect customer churn?
* How important do partners influence customer churn?
* How important is the type of internet service to influence customer churn ?
* How many percentage is predict to be churn?

## Data Understanding
### Source Data
* Source Data: [Telco Data](https://github.com/Yesaya03/Machine-Learning-Regression-and-Timeseries/blob/main/data_telco.csv)
* 7043 rows
* 21 columns

### Data Dictionary
Services that each customer has signed
* OnlineSecurity: customer has online security or not (Yes, No, No internet service)
* OnlineBackup: customer has online backup or not (Yes, No, No internet service)
* PhoneService: customer has a phone service or not (Yes, No)
* MultipleLines: customer has multiple lines or not (Yes, No, No phone service)
* InternetService: Customer’s internet service provider (DSL, Fiber optic, No)
* DeviceProtection: customer has device protection or not (Yes, No, No internet service)
* TechSupport: customer has tech support or not (Yes, No, No internet service)
* StreamingTV:customer has streaming TV or not (Yes, No, No internet service)
* StreamingMovies: customer has streaming movies or not (Yes, No, No internet service)

Information account for customer
* tenure : Number of months the customer has stayed with the company
* Contract: The contract term of the customer (Month-to-month, One year, Two year)
* PaymentMethod: The customer’s payment method (Electronic check, Mailed check, Bank transfer (automatic), Credit card (automatic))
* PaperlessBilling: customer has paperless billing or not (Yes, No)
* MonthlyCharges: The amount charged to the customer monthly
* TotalCharges: The total amount charged to the customer

Demographic info
* gender : male or a female (Male, Female)
* Partner : customer has a partner or not (Yes, No)
* Dependents : customer has dependents or not (Yes, No)
* customerID : Customer ID
* SeniorCitizen :customer is a senior citizen or not (1, 0)

labels for classification
* Churn :customer churned or not (Yes or No)

## Data Preparation
* Python version : 3.9.12
* Packages Version : Pandas, numpy, matplotlib, seaborn, and sklearn

## Data Cleansing
1. There are 13 columns containing missing values, with 12 of them being categorical data so that it is imputed with "unknown" and the remaining 1 column is numeric data with positive-skew distribution so that it is imputed using the median.
2. There is 1 column that has an inappropriate data type so it is necessary to adjust the data type.
3. There are 16 categorical columns that need to be encoded, with 15 of them being nominal data so that they are encoded using One Hot Encoding and the remaining 1 column is ordinal data so that they are encoded using a map.
4. The numeric columns in the dataset have different scales so it is necessary to scale the data using the StandardScaler.
5. The identifier column (customerID) and the multicollinear column (TotalCharges) are removed.

## EDA
### Churn Rate
![image](https://user-images.githubusercontent.com/55911060/200087624-eb562607-a5e1-495b-bd05-91bb221e1786.png)
The graph above shows that most of the customers don't churn, the loyal customer is more than churn customer

### Customer churn Based On Gender
![image](https://user-images.githubusercontent.com/55911060/200087699-985935e1-1ef0-41f8-af9f-c9ceb49bc90c.png)
Based on gender, telco customer distribution seems equal between males and female
The churn rate is almost at an equal level, in other words, we can say that churn rates are not depending on the gender of the customer
from 7043 customers there are 5147 customers who remain subscribed, or about 73.46% of telco data. and based on the results of EDA gender does not have much effect on customer churn, because the percentage results show the same thing, which is in the range of 31% of the total

### Customer Churn Based on Contract
![image](https://user-images.githubusercontent.com/55911060/200087774-46d16aa9-2656-47d3-828e-ecbd4d71ad31.png)
* Only less than 4% of customers churn when they subscribe for 1 year and 2 years, and this explains that there is no fatal cause that makes customers churn.
* There is an increase in the percentage of about 4.82% between 1-year to 2-year subscriptions for customers who do not churn. that means some loyal customers are still satisfied with the services provided by the company.
* The high number of Month to Month customers who decide to churn is around 23.50%, which means that there are still many early customers who are not interested in the services provided by the company.

### Customer Churn Based on Senior Citizen
![senc g](https://user-images.githubusercontent.com/99872829/200094529-5e17f0e8-6ab5-4ed6-98ae-c6a28fa72dbb.JPG)
* Based on the senior citizen category, we can see that most telco customers are not senior citizen (younger citizen) in front of the percentage 71.80%, The level of customer churn of senior citizens is also low, the largest customer churn is from the non-senior citizen class with a percentage of 17%

### Customer Churn Based on Dependents
![depn g](https://user-images.githubusercontent.com/99872829/200094556-7ffba589-fadb-4172-a2d8-8135ea3c286a.JPG)
* Telco customers mostly do not have dependants with a percentage of 60.17% compared to customers who have a dependent that is equal to 25.50%. Customers who churn based on the most dependents are customers who do not have dependents with a percentage of 18.83%, even so, customers who still stick with telco services still quite a lot with a total of 73.47%

### Customer Churn Based on Paperless Billing
![pb g](https://user-images.githubusercontent.com/99872829/200094549-3bd810ef-2f28-4472-a2dc-e52b2aaf55da.JPG)
* Telco customers based on paperless billing are the most customers who using paperless billing with a presentation of 59.22%, while customers who do not use paperless billing in amount 40.78%. The customers who churn the most are customers who use paperless billing with a percentage of 19.88%

### Customer Churn Based on Partner
![image](https://user-images.githubusercontent.com/55911060/200088851-49b5615d-2b95-483a-b7e2-16c1376ee8d0.png)
* Although the percentage of customers who do not churn and do not have partners is still high, namely 29.52%, partners are important things that can affect customer churn or not. It can be seen that there is a significant difference between churn customers who have partners and customers who do not churn without partners, namely 25.14% . </br> From this we know, that most customers who enjoy the service are customers who do not have a partner. This is in line with the number of customers who churn, where more are customers who do not have partners. Companies can increase promotions on days associated with couples such as Valentine, to increase customers who want to use the company's services.

### Customer Churn Based on Phone Service
![image](https://user-images.githubusercontent.com/55911060/200088916-bf864c7c-80d4-44a2-a795-5f056e767e99.png)
The churn rate for phone service is low, while customers who have a lot of churn are customers who use phone service, this is in line with the number of phone service subscribers who are more (6361) than those who do not subscribe (682)
![image](https://user-images.githubusercontent.com/55911060/200088930-d99a1be3-db20-4178-adb9-cbdb18b8b98d.png)

### Customer Churn Based on Internet Service
![image](https://user-images.githubusercontent.com/55911060/200088958-930a4acd-3dc2-4977-9b11-f5d6e85d92ca.png)
Not only being the highest at 24.01%, but DSL also has a much lower percentage in influencing customer churn than Fiber Optic, which is a difference of 10%. This shows that DSL Internet Service is still superior for customer use. </br> From this we know that most customers who enjoy the service use Fiber Optic internet services, and the second is DSL. However, the number of customers who churn more is using Fiber Optic internet services. Companies can improve or maintain Fiber Optic-based services, so that customers can continue to survive or add new customers

### Customer Churn Based on Online Security
![image](https://user-images.githubusercontent.com/55911060/200089019-f1b31c93-8656-4f25-8f73-b0c898f6bac8.png)
From the data above, it is known that most customers do not subscribe to Online Security, followed by 1720 customers who subscribe to Online Security, 1321 customers who do not have internet service, and 1009 unknown customers. The churn rate in Online Security is dominated by customers who do not churn, while customers who churn are dominated by customers who do not use Online Security services.

### Customer Churn Based on Online Backup
![image](https://user-images.githubusercontent.com/55911060/200089067-d6095455-3718-49f5-af95-f48b5ca4db93.png)
From the data above, it is known that most customers do not subscribe to Device Protection, followed by 2070 customers who do not subscribe to Device Protection, 1321 customers who do not have internet service, and 1009 unknown customers. The churn rate in Device Protection is dominated by customers who do not have internet service. do not churn, while customers who churn are dominated by customers who do not use Device Protection services.

### Customer Churn Based on Tech Support
![image](https://user-images.githubusercontent.com/55911060/200089127-6c4b218a-0a14-4307-8df8-da2dda1482b4.png)
From the data above, it is known that most customers do not subscribe to Tech Support, followed by 1740 customers who subscribe to Tech Support, 1321 customers who do not have internet service, and 1009 unknown customers. The churn rate in Tech Support is dominated by customers who do not churn, while customers who churn are dominated by customers who do not use Tech Support services.

### Customer Churn Based on Streaming TV
![image](https://user-images.githubusercontent.com/55911060/200089219-94c69a26-7604-4a5e-972a-e0589980febe.png)
From the data above, it is known that most customers do not subscribe to Streaming TV, followed by customers who subscribe to 2310 customers, 1321 customers who do not have internet service, and 1009 unknown customers. The churn rate on Streaming TV is dominated by customers who do not churn, while subscribers who churn are not much different between those who subscribe and do not subscribe to Streaming TV

### Customer Churn Based on Streaming Movies
![image](https://user-images.githubusercontent.com/55911060/200089247-82477f63-62a5-46b9-8a5a-d018b8a4c4e4.png)
From the data above, it is known that most customers do not subscribe to Streaming Movies, followed by 2319 subscribers, 1321 customers who do not have internet service, and 1009 unknown customers. The churn rate for Streaming Movies is dominated by customers who do not churn, while subscribers who churn are not much different from those who subscribe and do not subscribe to Streaming Movies. </br> From all the data services above, it shows that the services provided are still not superior that can be utilized by the company because there are still many customers who continue to subscribe even though they do not use the services provided by the company.

### Customer Churn Based on Payment Method
![image](https://user-images.githubusercontent.com/55911060/200089308-008a7636-c980-47b3-9080-af68405843cb.png)
From the data above, it is known that most customers use Electronic Check for the Payment Method, the churn rate in the Payment Method is dominated by customers who do not churn, while customers who churn are dominated by customers who use Electronic check for the payment method.

### How Services Affect the Customer Churn
![image](https://user-images.githubusercontent.com/91566708/200112474-03359362-b359-498e-9052-62caa5255d26.png)

From the overall data, there are still many customers who continue in telco even though they do not use the services provided. can be seen if the average is almost more than 22% of the total data, customers do not use the services provided by the company.

From the overall data, there are still many customers who still in telco but they do not have internet services in it, about 17% of the total data.

## Modeling : Logistic Regression
* Logistic Regression algorithm is an supervised machine learning algorithm for predicting the categorical dependant variable using a given set of independent variables  

* Logistic gives best result under the following conditions :
  * The dependant variable in binary logistic regression must be binary
  * Only the variables that are relevant should be included
  * The independent variable must be unrelated to one another(Have minimal or no multicollinearity in the model)
  * The log chance are proportional to the independent variables
  * Required large sampe size
 
 ## Evaluation
![pres al](https://user-images.githubusercontent.com/99872829/200104563-d61ad470-2ac8-4389-9212-ad27dbc3c47d.JPG)

In the logistic regression model, for the evaluation model, we use the Confusion Matrix. The Confusion Matrix contains precision, recall, f1-score, accuracy, and support. </br> From the modeling, we get 75% churn accuracy, 51% Precision churn, 84% Recall churn, and 64% F1 Score churn. In this case modeling, it is better to see someone who does not churn into churn so it is better to use recall as an indication of model performanc

## Result
* [Gender on churn]

  Based on gender, telco customer distribution seems equal between males and female. The churn rate is almost at an equal level, in other words, we can say that churn   rates are not depending on the gender of the customer, from 7043 customers there are 5147 customers who remain subscribed, or about 73.46% of telco data. and based     on the results of EDA gender does not have much effect on customer churn, because the percentage results show the same thing, which is in the range of 31% of the      total
* [Contract on churn]

  Only less than 4% of customers churn when they subscribe for 1 year and 2 years, and this explains that there is no fatal cause that makes customers churn. There is   an increase in the percentage of about 4.82% between 1-year to 2-year subscriptions for customers who do not churn. that means some loyal customers are still     satisfied with the services provided by the company. The high number of Month to Month customers who decide to churn is around 23.50%, which means that there are still   many early customers who are not interested in the services provided by the company.

* [Services on churn]

  From the overall data, there are still many customers who continue in telco even though they do not use the services provided. can be seen if the average is almost     more than 22% of the total data, customers do not use the services provided by the company. From the overall data, there are still many customers who still in telco   but they do not have internet services in it, about 17% of the total data.

* [Partner on churn]

  Although the percentage of customers who do not churn and do not have partners is still high, namely 29.52%, partners are important things that can affect customer     churn or not. It can be seen that there is a significant difference between churn customers who have partners and customers who do not churn without partners, namely
  25.14% . From this we know, that most customers who enjoy the service are customers who do not have a partner. This is in line with the number of customers who       churn, where more are customers who do not have partners. Companies can increase promotions on days associated with couples such as Valentine, to increase customers     who want to use the company's services.

* [SeniorCitizen on churn]

Based on the senior citizen category, we can see that most telco customers are not senior citizen (younger citizen) in front of the percentage 71.80%, The level of customer churn of senior citizens is also low, the largest customer churn is from the non-senior citizen class with a percentage of 17%

* [Dependents on churn]

Telco customers mostly do not have dependents with a percentage of 60.17% compared to customers who have a dependent that is equal to 25.50%. Customers who churn based on the most dependents are customers who do not have dependents with a percentage of 18.83%, even so, customers who still stick with telco services still quite a lot with a total of 73.47%

* [Paperless Billing on churn]

Telco customers based on paperless billing are the most customers who using paperless billing with a presentation of 59.22%, while customers who do not use paperless billing in amount 40.78%. The customers who churn the most are customers who use paperless billing with a percentage of 19.88%.

* [Internet Service on churn]

Not only being the highest at 24.01%, but DSL also has a much lower percentage in influencing customer churn than Fiber Optic, which is a difference of 10%. This shows that DSL InternetService is still superior for customer use. From this we know that most customers who enjoy the service use Fiber Optic internet services, and the second is DSL. However, the number of customers who churn more is using Fiber Optic internet services. Companies can improve or maintain Fiber Optic-based services, so that customers can continue to survive or add new customers

* From the modeling, we get 75% churn accuracy, 51% Precision churn, 84% Recall churn, and 64% F1 Score churn. In this case modeling, it is better to see someone who does not churn into churn so it is better to use recall as an indication of model performance.
* To see further performance of the model, a probability check was carried out with ROC-AUC, it was found that the difference in accuracy between the train data and the test data was less than 0.05, so it can be concluded that the model made is good.
* When parameter adjustment is made with hyperparameter tuning, there is not much change in accuracy

## Recommendation
* Recommendation for "Churn" Customer : 
1. Focus on promotion, campaign, or give advantage for return old customers such as discount reactivation or free services. Make a point reactivation strategy, give the big advantage to old customers who already churns 
* Recommendation for "Not Churn" Customer: 
1. Focus on a strategy to raise income such as down-selling such as bundles for a few products
2. Indeed, services have not been very influential in terms of customer churn, but internet services need to be improved because there are still many customers who do not have internet services, which could be one of the big influences on why customers have not used the service.
