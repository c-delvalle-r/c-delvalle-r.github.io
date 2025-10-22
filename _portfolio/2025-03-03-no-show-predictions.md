---
title: Healthcare No Show Prediction with Machine Learning
toc: true
toc_sticky: true
tags: python sklearn machine-learning exploratory-data-analysis
excerpt: Machine learning models to predict when a patient will miss their medical appointment!
permalink: /:collection/no-show-predictions
---

This was the final project I presented for my Data Science and Applied AI Certification. [This dataset](https://www.kaggle.com/datasets/wajahat1064/healthcare-appointment-dataset/data) found in Kaggle, has Brazil data regarding patients, their medical appointments and whether they showed up or not.

## Executive Summary
- The dataset indicates that 30% of patients are missing their medical appointments. The objective of the project is to develop a machine learning model capable of identifying those patients that are will miss their appointment so the business can engage with them to confirm their appointment or cancel the appointment to schedule a different patient. 


## Business Problem
- Patients not showing up to a medical appointment is lost opportunity for medical practices. They represent wasted capacity, staff time and material. 
- In this case, the company should bo more interested in predicting the the patient is NOT going to attend their medical appointment so that we can try to do something about it to prevent the opportunity loss. Therefore, the most important metric to look out for is Recall, because by being able to catch all patients that will miss their appointment so that we can contact them or backfill the appointment space for another patient.
- A few of the developed and tuned models were yielding approximately 0.66 recall score. Meaning **the model is able to identify 2 out of every three appointments are are missed (true positives)**.

## Methodology
- The methodology is based on the CRISP-DM framework. That includes the following steps:
    1. Business Understanding: Understand the problem at hand, how it impacts the business and the importance and impact the model will have in the business.
    2. Data Understanding: Understanding the dataset. This involves understanding the metadata and variables it contains, **data profiling and an exploratory data analysis (EDA)** that includes univariate and bivariate analyses.
    3. Data Preparation: Prepare the data for modeling. This encompasses **data cleansing** (dealing with missing values, ) and **feature engineering**.
    4. Modeling: Develop different models and tune their hyperparameters.
    5. Evaluation: Identify the most important evaluation metrics for the task at hand and evaluate the model (we included **cross validation** and making sure the model does not fall into over-fitting)
    6. Deployment: This is out of scope for this project. Deployment would be done after a model is deemed good enough for the business' requirement and is put in production.

![crisp-dm methodology](/assets/images/CRISP-DMBasics.jpg){: .align-center}

## Skills
- Python
    - Numpy, pandas, exploratory data analysis (EDA)
- Data Visualization
    - Matplotlib, seaborn, plotly express
- Machine Learning : 
    - sklearn, model evaluation, feature engineering, classification, class balancing

## Results and Business Recommendations
1. If this dataset is representative of the whole population of appointments, the company would have a serious no show problem. Losing 3 out of every ten appointments would leave a lot of room for improvement and may become if it is not already a financial issue.
2. With the tried features, models and hyperparameters, the best recall score we could get was aroung 0.66. Which is honestly pretty low still. only catching two thirds of the real no shows is still low.
3. So far, the chosen ML algrythm, parameter tuning and whether to include or not neighborhood as is has not made a significant difference.
4. The difference between the appointment date and when it was scheduled and chronic conditions such as hypertension and diabetes are the best predictors to determine patient no-show.

## Next Steps
1. If percent of no shows in the dataset is representative of the usual behavior of the population of appointments, I would suggest the company to take immediate action with a contingency plan like calling patients for appointment confirmation.
2. Regarding the ML model. I would try the next following approaches:
    - Go back to the process of feature engineering an try a different approach like transforming variables in a different way or changing the way the binning is done.
    - I would try to enrich the dataset with external sources. A big contender would be to add more information based on the neighborhood such as population or socioeconomical factors.
    - If I had access to more detailes information, I would try to use data related to the patient or derived from patient information such as the number of days since last visit or the distance from their address to where the appointment was.