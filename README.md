# Customer Churn Prediction: A Comprehensive ML and Power BI Project
<img src="https://github.com/user-attachments/assets/4a3d29aa-5ec0-46d1-9ded-f7f568c30fc9" alt="Screenshot of Power BI Dashboard" style="width:80%; margin-bottom: 20px;">

This repository contains a project focused on predicting customer churn for a telecom company. The project involves a detailed analysis of customer data, building machine learning models, and creating a Power BI dashboard to visualize the insights.






## Table of Contents

1. [Overview](#overview)
2. [Dataset](#dataset)
3. [Exploratory Data Analysis](#exploratory-data-analysis)
4. [Data Preprocessing](#data-preprocessing)
5. [Model Building](#model-building)
6. [Results and Evaluation](#results-and-evaluation)
7. [Power BI Dashboard](#power-bi-dashboard)
8. [How to Run](#how-to-run)
9. [Conclusion](#conclusion)
10. [Files in the Repository](#files-in-the-repository)

## Overview

Customer churn is a significant problem for telecom companies, as retaining customers is often more cost-effective than acquiring new ones. This project aims to predict which customers are likely to churn (i.e., stop using the company's services) using various machine learning techniques and to visualize the key factors leading to churn using a Power BI dashboard.

## Dataset

- The dataset used for this project is a sample telecom customer dataset, containing information such as customer demographics, account information, and usage details.
- It includes features like `gender`, `SeniorCitizen`, `Partner`, `Dependents`, `tenure`, `PhoneService`, `MultipleLines`, `InternetService`, `OnlineSecurity`, `TechSupport`, `Contract`, `PaymentMethod`, `MonthlyCharges`, `TotalCharges`, and the target variable `Churn`.

## Exploratory Data Analysis

1. **Data Overview**: Loaded the dataset and explored its structure, data types, and basic statistics.
2. **Data Cleaning**:
   - Identified and handled missing values, particularly in the `TotalCharges` column.
   - Converted `TotalCharges` to a numeric data type.
   - Removed records with missing values.
3. **Feature Engineering**:
   - Grouped `tenure` into bins to create a new feature, `tenure_group`.
   - Dropped irrelevant columns (`customerID`, `tenure`).
   - Converted categorical variables to dummy variables.
4. **Visualizations**:
   - Plotted distributions of key variables and their relationship with churn.
   - Used heatmaps and bar plots to understand correlations and feature importance.

## Data Preprocessing

1. **Handling Class Imbalance**:
   - Applied `SMOTEENN` (Synthetic Minority Over-sampling Technique and Edited Nearest Neighbors) to address the class imbalance in the target variable (`Churn`).
2. **Data Splitting**:
   - Split the data into training and test sets (80% training, 20% testing).

## Model Building

1. **Decision Tree Classifier**:
   - Built an initial model using a Decision Tree Classifier.
   - Achieved an accuracy of ~78% on the imbalanced dataset, but with low recall for the minority class (churned customers).
2. **Improving Model Performance**:
   - Applied `SMOTEENN` to resample the data and improve model performance.
   - Retrained the Decision Tree model, achieving an accuracy of ~93% with improved recall (0.98) and precision (0.91) for the minority class.
3. **Random Forest Classifier**:
   - Built a Random Forest Classifier on both the original and resampled datasets.
   - The resampled model achieved an overall accuracy of ~94%, with high recall (0.96) and precision (0.94) for the minority class.
4. **Dimensionality Reduction**:
   - Applied PCA (Principal Component Analysis) to reduce dimensionality; however, it did not improve model performance significantly.

## Results and Evaluation

- The final Random Forest model with `SMOTEENN` resampling showed the best performance with an accuracy of 94%, and high recall and precision for churn prediction.
- The model is saved as `model.sav` using `pickle` for deployment.

## Power BI Dashboard

A Power BI dashboard was created to visualize the key insights from the data and the model. The dashboard includes:

1. **Customer Demographics**: Breakdown by gender, tenure, senior citizen status, etc.
2. **Churn Analysis**: Visualizations of churn distribution across different features (e.g., contract type, payment method, online security).
3. **Risk Segmentation**: Classification of customers into risk groups (Non-risky, Low-risk, Risky, High-risk).
4. **Churn Reasons**: Key reasons for customer churn, such as lack of tech support or online security.
5. **Interactive Features**: An "Ask a Question" feature for dynamic exploration of the data.

![Dashboard Screenshot](path/to/dashboard/screenshot.png)

## How to Run

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/yourusername/telecom-churn-prediction.git
   cd telecom-churn-prediction
   ```
2. **Install the Required Packages**:
   Make sure you have Python 3.x and install the required packages:
   ```bash
   pip install -r requirements.txt
   ```
3. **Run the Flask Application**:
   ```bash
   python app.py
   ```
   The app will run on `http://127.0.0.1:5000/`, where you can input customer data and get churn predictions.

## Conclusion

The project successfully predicted customer churn using a combination of data preprocessing, feature engineering, model building, and visualization. The Random Forest model with `SMOTEENN` resampling showed the best performance, and the Power BI dashboard provided clear insights into the factors influencing churn.

## Files in the Repository

- **app.py**: Flask application for deploying the churn prediction model.
- **model.sav**: Serialized model file for the Random Forest Classifier.
- **Churn-Prediction-Analysis-Dashboard.pdf**: Power BI dashboard showcasing the churn analysis.
- **requirements.txt**: List of required Python packages.
- **README.md**: Project documentation.
