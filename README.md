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

## Data
The dataset contains aggregated campaign and user behavior features. Each row represents one user’s last targeting event in the campaign.
| Column                  | Description                                                     |
|-------------------------|-----------------------------------------------------------------|
| user_id                 | Unique identifier for the customer                               |
| last_target_date        | Date of the last campaign targeting event                        |
| channel                 | Marketing channel (email, push, text)                            |
| personalization_score   | Recommender system score for product affinity (0–1)             |
| past_7d_sessions        | Number of website/app sessions in the 7 days before targeting   |
| past_30d_purchases      | Number of purchases in the 30 days before targeting             |
| days_since_last_purchase| Days since the user’s last purchase                              |
| is_pro_customer         | Boolean indicating whether the user is a pro/loyalty customer   |
| product_price           | Price of the recommended product                                 |
| treatment_variant       | Campaign variant (control vs personalized text)                 |
| converted_7d            | Target variable: did the user purchase within 7 days (0/1)      |
| num_previous_targets    | Number of previous campaign targets for this user               |

## Model
A Bayesian logistic regression classifier:

Goal: Estimate the probability that a user converts (converted_7d = 1) given features like personalization score, past behavior, and campaign variant.

Why Bayesian:
1. Allows incorporation of prior beliefs (e.g., average conversion rate).
2. Naturally handles uncertainty, which is useful when data is sparse or noisy.
3. Can model hierarchical effects (e.g., user-level random effects or channel effects) if needed.
