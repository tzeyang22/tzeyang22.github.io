---
layout: post
author: Leo Tze Yang
ID: 8248527U
title: "Applied Data Science Project Documentation"
categories: ITD214
---
## Project Background
<i><b>Business Objective</b></i>: Group2 Global Enterprise is planning to set up a hotel in Portugal. Apart from internal resource management, hotels also experience wastage of resources due to external factors in the form of guest behaviour such as booking cancellation or mismatch in guest expectations & preferences. 
As the hotel will be based in Portugal, guests will likely be tourists from Europe.

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
<p>I used correlation heatmap to select the features that will feed into my model and also to check for any multicollinear variables. The features with middle to high correlations are 'lead_time', 'previous_cancellations', 'booking_changes', 'required_car_parking_space', and 'total_of_special_request'. 'lead_time' has a range from 0 to 737 and 'previous_cancellation' has range from 0 to 26. I do not want any feature to have greater influence due to high range resulting in poor/incorrect prediction. Thus, I used z-score method to normalize these 5 features (as there are lot of outlier for these features). For the rest of the categorical variables ('region', 'market segment' and deposit type), I do one-hot encoding.</p>
<p>The original data of 119390 rows and 32 columns are now 118504 rows and 33 columns. The columns is big due to one-hot encoding for 'region' variable (16 regions) & some categorical variables.</p>

### Modelling
<p>I split 80% of data for training 20% of data for testing.</p> 
<p>The data is almost ready for modelling except the target variables are not balance. The training 'non-cancelled' class has 60,000 records while training 'cancelled' has only 35,000 records (split into 80% training & 20% testing). This will create bias result for my modelling. I use Synthetic Minority Oversampling Technique (SMOTE) to oversample minority class ('cancelled') using k-nearest neighbour. The reason for choosing oversampling instead of undersampling is because I want to preserve the quantity of data. If I use undesampling technique, 25000 rows of data will be lost. This is quite a large amount of data lost.</p>

### Evaluation
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce bibendum neque eget nunc mattis eu sollicitudin enim tincidunt. Vestibulum lacus tortor, ultricies id dignissim ac, bibendum in velit. Proin convallis mi ac felis pharetra aliquam. Curabitur dignissim accumsan rutrum. In arcu magna, aliquet vel pretium et, molestie et arcu. Mauris lobortis nulla et felis ullamcorper bibendum. Phasellus et hendrerit mauris. Proin eget nibh a massa vestibulum pretium. Suspendisse eu nisl a ante aliquet bibendum quis a nunc. Praesent varius interdum vehicula. Aenean risus libero, placerat at vestibulum eget, ultricies eu enim. Praesent nulla tortor, malesuada adipiscing adipiscing sollicitudin, adipiscing eget est.

## Recommendation and Analysis
Explain the analysis and recommendations

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce bibendum neque eget nunc mattis eu sollicitudin enim tincidunt. Vestibulum lacus tortor, ultricies id dignissim ac, bibendum in velit. Proin convallis mi ac felis pharetra aliquam. Curabitur dignissim accumsan rutrum. In arcu magna, aliquet vel pretium et, molestie et arcu. Mauris lobortis nulla et felis ullamcorper bibendum. Phasellus et hendrerit mauris. Proin eget nibh a massa vestibulum pretium. Suspendisse eu nisl a ante aliquet bibendum quis a nunc. Praesent varius interdum vehicula. Aenean risus libero, placerat at vestibulum eget, ultricies eu enim. Praesent nulla tortor, malesuada adipiscing adipiscing sollicitudin, adipiscing eget est.

## AI Ethics
Discuss the potential data science ethics issues (privacy, fairness, accuracy, accountability, transparency) in your project. 

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce bibendum neque eget nunc mattis eu sollicitudin enim tincidunt. Vestibulum lacus tortor, ultricies id dignissim ac, bibendum in velit. Proin convallis mi ac felis pharetra aliquam. Curabitur dignissim accumsan rutrum. In arcu magna, aliquet vel pretium et, molestie et arcu. Mauris lobortis nulla et felis ullamcorper bibendum. Phasellus et hendrerit mauris. Proin eget nibh a massa vestibulum pretium. Suspendisse eu nisl a ante aliquet bibendum quis a nunc. Praesent varius interdum vehicula. Aenean risus libero, placerat at vestibulum eget, ultricies eu enim. Praesent nulla tortor, malesuada adipiscing adipiscing sollicitudin, adipiscing eget est.

## Source Codes and Datasets
Upload your model files and dataset into a GitHub repo and add the link here. 
