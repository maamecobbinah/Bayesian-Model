# Bayesian Classifier Model for Marketing Personalization
This repository contains data and a Bayesian classifier model used to predict the likelihood of a customer making a purchase after receiving a personalized marketing campaign.

## Problem Statement
Cymbal is a fashion retailer that wants to optimize its marketing campaigns. Customers can receive targeted recommendations based on:
1. Cart abandonment
2. Wishlist items
3. Past purchase behavior
The key question is: Can we use a Bayesian model to predict which users are most likely to purchase, so we can target them efficiently?

## Approach
#### Data Collection
Aggregate marketing campaign data, user behavior, and customer profiles.
#### Exploratory Data Analysis (EDA)
Understand feature distributions, missing values, and correlations.
#### Feature Engineering
Create features such as: past_7d_sessions, past_30d_purchases, days_since_last_purchase, num_previous_targets, Channel and treatment variant encoding
#### Build Model
Use a Bayesian logistic regression classifier to predict the probability of purchase (converted_7d).
#### Model Evaluation
Evaluate using metrics like ROC-AUC, log loss, and calibration plots.
#### Prediction
Score the customer list and prioritize targeting users with the highest predicted conversion likelihood.
