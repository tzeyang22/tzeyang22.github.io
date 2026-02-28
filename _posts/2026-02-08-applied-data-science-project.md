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
<p>Before analysis and modelling, we need to understand our data. I do exploratory data analysis(EDA) on my dataset "hotel_bookings.csv" downloaded from kaggle. The hotel data and record are based in portugal. There are total of 119,390 rows and 32 features. The details of the 32 features can be found in our submitted group project and milestone powerpoint slide. In the dataset, there are few variables like 'children', 'country', 'adr' with null values. I removed those rows with null values as they are less than 1% of the dataset. I did not delete those features as I might need them for analysis later. Variables like agent ID and company ID which are useless & meaningless are removed from the dataset. On further analysis of the data, there are some parts that are not sensible. "adr" (average daily rate) that are less than 0 and 'adult' features equal to 0. Average daily rate is the average amount of customer spending per day so it doesn't look reasonable to be negtive. Children cannont book the hotel alone so 'adult' cannot be zero. These rows (less than 1% of dataset) are removed.</p>

<p>On further analysis of the data, there are some parts that are not sensible. adr</p>

### Modelling
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce bibendum neque eget nunc mattis eu sollicitudin enim tincidunt. Vestibulum lacus tortor, ultricies id dignissim ac, bibendum in velit. Proin convallis mi ac felis pharetra aliquam. Curabitur dignissim accumsan rutrum. In arcu magna, aliquet vel pretium et, molestie et arcu. Mauris lobortis nulla et felis ullamcorper bibendum. Phasellus et hendrerit mauris. Proin eget nibh a massa vestibulum pretium. Suspendisse eu nisl a ante aliquet bibendum quis a nunc. Praesent varius interdum vehicula. Aenean risus libero, placerat at vestibulum eget, ultricies eu enim. Praesent nulla tortor, malesuada adipiscing adipiscing sollicitudin, adipiscing eget est.

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
