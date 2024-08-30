# Background:
- Homeownership is a key component of the American dream.
- Securing a mortgage is a crucial step in achieving homeownership.
- The mortgage approval process is often opaque and uncertain.
3.6 - 5.4 million mortgage applications are denied each year (20-30%)

# Objective: 
-Analyze home mortgage data to identify key factors influencing approval decisions.
- Develop a prediction model to estimate the likelihood of mortgage approval based on individual characteristics.
- Use data analysis and predictive modeling to make the mortgage process more transparent.
- Aim to improve understanding of approval criteria and assist individuals in assessing their mortgage prospects.


# Data Acquisition:
The Home Mortgage Disclosure Act (HMDA) 
The Federal Financial Institutions Examination Council’s (FIFEC) Consumer Financial Protection Bureau (CFPB) provides a trove of information related to mortgage applications, at various stages.
Downloaded dataset for 2023 Massachusetts Mortgages (~210,000 entries, 81MB)
72 Numerical features (But many have “Exempt” Case)
26 Categorical Features


# Data Exploration:
Created complete HDMA dictionary to check value entries, convert NA/Nulls, and encode data in expected format as per standard.
Performed univariate analysis for all features.

<img width="263" alt="image" src="https://github.com/user-attachments/assets/d26a22eb-8fa7-4b8a-9dc2-98a47351df04">

<img width="321" alt="image" src="https://github.com/user-attachments/assets/ae857a90-27eb-41a0-820a-21f2f8ef7d83">

<img width="270" alt="image" src="https://github.com/user-attachments/assets/2ee06445-366b-45a2-a346-956557f085de">


# Univariate Analysis

Perform univariate analysis on our features by displaying histograms for numerical values and bar plots for categorical values.

Some Examples below:

<img width="325" alt="image" src="https://github.com/user-attachments/assets/cbc2d43d-8ea1-4f5a-9f6b-d41e23cd594f">

<img width="322" alt="image" src="https://github.com/user-attachments/assets/73eaeaa4-2e4d-424f-ac12-40b8eac40fd3">

<img width="322" alt="image" src="https://github.com/user-attachments/assets/e5a7458c-ef1d-4013-a595-0184719d648d">


# Feature Selection

Feature Selection:
- Dealing with the curse of dimensionality with 98 features was paramount
- Noticed that many features were highly correlated with one another and often redundant:
	Ex: Loan_Type and Derived_Product_Loan_Type
- Used cross correlation matrix do identify highly correlated features (Red = Positive, Blue = Negative)
- Dropped feature with correlation above 0.8
- Allowed feature space reduction of ~28%.

-- Initial Feature Set
<img width="401" alt="image" src="https://github.com/user-attachments/assets/bbb5cd22-4121-46da-88e5-4f85b8acc0d1">

-- Reduced Feature Set
<img width="433" alt="image" src="https://github.com/user-attachments/assets/37d6060e-7a56-417c-bd6d-0d845b2faebe">

# Model Selection

Given the fact that the outcome variable for this dataset is not binary, we must use a multinomial model. A simple model fit for this task is a multinomial logistic regression model. This is a suitable choice due to the fact that:

- We have a categorical dependent variable that is multinominal -> action_taken = [1,2,3,4,5,6,7,8]
- It is likely that there are non-linear relationships between the features (For instance: A linear reduction in debt-to-income ratio will have a more than linearly proportional effect on chances of obtaining a mortgage loan.) This model does not assume a linear relationshop between these features.


# Results:
-Performed well for determining Mortgage loan approval or denial. 
-Didn’t perform as well for under sampled classes. (Classes 2,5,7,8 comprise only 7.2% of dataset)

<img width="302" alt="image" src="https://github.com/user-attachments/assets/16dad442-c0c0-4949-913b-cd9dc65a9617">

<img width="302" alt="image" src="https://github.com/user-attachments/assets/5a5cf63c-5caa-44fc-ba59-aad5fb596e5f">

<img width="394" alt="image" src="https://github.com/user-attachments/assets/627b780c-bfc4-4e2e-9fad-b9a0641230ee">

<img width="431" alt="image" src="https://github.com/user-attachments/assets/49cb25ab-4e9a-4888-9471-a29c8a344d21">

# Further Improvements

- Potential for improvement of under sampled classes:
- SMOTE (Synthetic Minority Over-sampling Technique)
- Ensemble Methods
  - Potential improvements in further feature engineering: income_per_dependent, loan_to_income_ratio.
- Deeper dive into legal entity identifiers.
- We could perform a multi-year analysis on MA mortgage loans to determine changes in behavior (Pre-2008 vs Now).
- We could perform a nationwide analysis to determine mortgage origination behaviors between states.

  
![Picture1](https://github.com/user-attachments/assets/c88690b5-f09c-4c68-ae12-e3522eed1964)

