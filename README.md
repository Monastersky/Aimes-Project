# Project 2 - Ames Housing Data and Kaggle Challenge

## Problem Statement

Zillow would like to increase their home estimation calculator which is important so owners can know the proper estimate of their house as well as homebuyers knowing the price of homes in certain areas. I have been tasked with creating an price estimator that will determine the price of a house using housing data from Ames, Iowa. 

## Executive Summary

We were initially given very messy data so a large amount of time was spent cleaning the data so that it could be modelled effectively. For all categorical columns that didn’t have any sort of clear order I made the column into dummy variables. For all categorical columns that did have a clear order I created a dictionary and made each value into an integer so the worst category would be a 0 and then each value above that would be one more. For all numerical columns I left as is. In terms of missing values if it was a categorical column, I changed the null values to none and if the column was numerical, I changed the column to 0 as I assumed that feature did not exist. For the square feet columns there were clear outliers, so I changed all outliers to be the mean of that column so that the outliers weren’t destroying my model. I found this to be a better approach than changing those values to 0 since dropping outliers was not an option.

When I first started exploring my data a couple things shot out at me. Most of the houses were in the 150,000 to 250,000 range although there were quite a few outliers on the positive side for pricing. I assumed that since Ames is a college town lots of the housing is probably student housing which is generally less expensive but some of the more expensive housing may by for professors that were making a fair amount of money. I also noticed that there where clusters in 1960 and 2005 for what year the house was built. I am not sure why this is exactly, but I assumed this meant that year the house was built might be an important predictor.

When I was choosing my model, I decided to use all the features that I had available and let me lasso regression choose which predictors were important enough to keep in my model. I conducted a train test split on my data so that I had training data to create my model on and then testing data to test the accuracy of my model on. I used a power transformer to fit my data which is important because by using that it scales my data and makes sure each variable has a normal distribution. I then used a lasso model to predict my data so that I will only have variables in my model that have an impact on my data. 

### Data Sets

I used the following site as my data dictionary for this project.
http://jse.amstat.org/v19n3/decock/DataDocumentation.txt

This data contains housing information from the town Ames, Iowa from the years 2006-2010. Ames is home to Iowa State University and is around 30 miles away from the capital of Iowa, Des Moines. This data was collected by Dean De Cock from Truman State University.

### Data Analysis

Please look at the jupyter notebook project_2_submission for my data cleaning and data modelling work.

## Conclusion

Overall my model had an R-squared score of .9310 which means my model can accurately predict ~93 percent of the change in housing price. Although I don’t have benchmarks of previous Zillow models to compare my model to I think that this is quite good when considering all of the possible different aspects of a house that affects its price. I believe a great next step would be to see if model works well on housing prices in other markets before we launch this on Zillow’s website. 