---
layout: post
author: Leo Tze Yang
title: "Applied Data Science Project Documentation"
categories: ITD214
---
## Project Background
<i><b>Business Objective</b></i>: Support the establishment of the hotel by lowering the wastage of resources which could otherwise arise from allocating resources into factors that are not as important. 

<i><b>Objectives</b></i>:
1. To predict whether customers will cancel their bookings & factors affecting it.
2. Identify key themes in hotel reviews to prioritise operations and guide establishment of the new hotel (Text Analysis).

I will be working on objective No.1 to help fullfilled the business goal.

## Work Accomplished
Document your work done to accomplish the outcome

### Data Preparation
<p>Before analysis and modelling, we need to understand our data. I do exploratory data analysis (EDA) on my dataset "hotel_bookings.csv" downloaded from kaggle. The hotel data and record are based in portugal. There are total of 119,390 rows and 32 features. The details of the 32 features can be found in our submitted group proposal and milestone powerpoint slide. In the dataset, there are few variables like 'children', 'country', 'adr' with null values. I removed those rows with null values as they are less than 1% of the dataset. I did not delete those features as I might need them for analysis later. Unique variables like agent ID and company ID with large number of categories are discarded. They will only "thinned out" the effect of the variable and does not help in prediction.</p>
<p>On further analysis of the data, there are some parts that are not sensible - "adr" (average daily rate) that are less than 0 and 'adult' features equal to 0. Average daily rate is the average amount of customer spending per day so it doesn't look reasonable to be negtive. Children cannot book the hotel alone so 'adult' should not be zero. These error rows (less than 1% of dataset) are removed.</p>
<p>There are some similiar categorical features like my target variable 'is_canceled' and 'reservation_status' & 'distribution_channel' and 'market_segment'. I kept 'is_canceled' (target variable) & 'market_segment'(3 more features than distribution channel) and removed 'reservation_status' & 'distribution_channel'.</p>
<p>After removing the null and error row, I will do some feature engineering. I change 'country' variable to 'region' variable. 177 countries is segment into 16 regions (eg. Asia, Middle_East, South_America, just to name a few) to reduce the number of features. Since I have the 'region' feature, column 'country' is discarded. There are 2 variables which can be combined into one variable. They are 'reserve_room_type' and 'assigned_room_type'. I combines these 2 variables to one variable named 'correct/incorrect room type'.</p>
<p>I used correlation heatmap to select the features that will feed into my model and also to check for any multicollinear variables. The features with middle to high correlations are 'lead_time', 'previous_cancellations', 'booking_changes', 'required_car_parking_space', and 'total_of_special_request'. 'lead_time' has a range from 0 to 737 and 'previous_cancellation' has range from 0 to 26. I do not want any feature to have greater influence due to high range resulting in poor/incorrect prediction. Thus, I used z-score method to normalize these 5 features (as there are lot of outlier for these features). For the rest of the categorical variables ('region', 'market segment' and 'deposit type'), I do one-hot encoding.</p>
<p>The original data of 119390 rows and 32 columns are now 118504 rows and 33 columns. The columns is big due to one-hot encoding for 'region' variable (16 regions) & some other categorical variables.</p>

### Modelling
<p>I split 80% of data for training 20% of data for testing.</p> 
<p>The data is almost ready for modelling except the target variables are not balance. The training 'non-cancelled' class has 60,000 records while training 'cancelled' has only 35,000 records. This will create bias result for my modelling. I use Synthetic Minority Oversampling Technique (SMOTE) to oversample minority class ('cancelled') using k-nearest neighbour. The reason for choosing oversampling instead of undersampling is because I want to preserve the quantity of data. If I use undersampling technique, 25000 rows of data will be lost. This is quite a large amount of data lost.</p>
<p>Since the objective is find the reason affecting cancellation, I will use white box model for my prediction. The 3 models chosen are Logistic Regression, Decision Tree and Grdient Boosting. Althought Gradient Boosting is not a white box model, we can use technique to see the important features.</p>

### Evaluation
<p>Even though we are interested in knowing the factors that affect cancellation, we are using the model to predict which customer will cancel and which customer will not cancel. Thus, True positive and true negative is important. I will use accuracy as my model assessment criteria.</p>
<p>After adjusting the hyperparameter of the 3 models, Decision Tree has the highest accuracy of 0.811. Although True Positive is the lowest among the 3 models, Decision Tree has the highest True negative. This mean that the model perform better in predicting non-cancelling.</p>
<p>There is dillema of parameter tunnning for modelling. Take example, a more complex tree (increase the level and leaf node) in Decision Tree help lower bias and capture complex pattern. Accuracy increased but this complexity also increase variance. This mean that the model is more sentive to small variance or noise in the training data and not able generalize well. Overfitting may occur. Thus, I adjust the Decision Tree to a level where accuracy increase but there is little or no overfitting.</p>
<p>Decision Tree cover the objective of predicting whether customer cancel or not cancel. From the model (a white box model), we can also learn the factors affecting cancellation. Since we know the factors affecting cancellation, we just need to focus on those factors to prevent cancellation. This save resource and time on allcating manpower or reduce unnecessary budget in hiring third-party company to investigate the cause (our business objective of lowering wastage of resource).</p>

## Recommendation and Analysis
Explain the analysis and recommendations
<p>I import RFECV from Scki-learn to check the numbers and their mean test score. I set the parameter with cross validation to 10 folds and step to 1. The code work by removing each variable at each step to check the importance of the input variable. I plot the decision tree mean test score and the number of features into a chart. 7 features has the highest correct classification. Below are the list of important features in descending order.</p>
<img width="500" height="200" alt="image" src="https://github.com/user-attachments/assets/d7bf1ebb-4bc3-49d0-98b0-6b3921a34486" />
<p>We focus on features that have importance that is equal or greater than 0.10. They are 'deposit_type_non_refund', 'correct_incorrect room type' and 'total_of_special_request'. It is paradox that deposit type with non refund is associated with cancellation. Ususally, this type of booking is associated with high risk like high lead time (difference between time of booking and arrival date), large number of rooms book or many days of stay. As I do not have information on the high risk reason (except lead time), I will recommend the start-up hotel to reduce this kind of high risk booking. It can be frustrating when customer do not get the room they want. A notification system can be implemented to alert customer before their stay that the room that he/she initially wanted is now available for booking. Customer will be satisfied to change the room type (with a little top-up or partial refund (if downgrading of room type)). Lastly, I will recommend the start-up hotel to create a team to handle special request (within hotel limit and request is reasonable) so every request is being look into.</p>

## AI Ethics
Discuss the potential data science ethics issues (privacy, fairness, accuracy, accountability, transparency) in your project. 

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce bibendum neque eget nunc mattis eu sollicitudin enim tincidunt. Vestibulum lacus tortor, ultricies id dignissim ac, bibendum in velit. Proin convallis mi ac felis pharetra aliquam. Curabitur dignissim accumsan rutrum. In arcu magna, aliquet vel pretium et, molestie et arcu. Mauris lobortis nulla et felis ullamcorper bibendum. Phasellus et hendrerit mauris. Proin eget nibh a massa vestibulum pretium. Suspendisse eu nisl a ante aliquet bibendum quis a nunc. Praesent varius interdum vehicula. Aenean risus libero, placerat at vestibulum eget, ultricies eu enim. Praesent nulla tortor, malesuada adipiscing adipiscing sollicitudin, adipiscing eget est.

## Source Codes and Datasets
Upload your model files and dataset into a GitHub repo and add the link here. 
