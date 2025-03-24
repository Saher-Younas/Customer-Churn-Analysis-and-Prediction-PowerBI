# Customer-Churn-Analysis-and-Prediction-PowerBI

Customer Churn Analysis and Prediction
# Overview
This project focuses on analyzing and predicting customer churn using a telecom dataset. The Power BI dashboard provides insights into churn trends, customer demographics, and engagement levels, enabling businesses to take proactive measures to reduce churn.
Project Links
•	Power BI Dashboard: (https://github.com/Saher-Younas/Customer-Churn-Analysis-and-Prediction-PowerBI/blob/main/Customer%20Churn%20Dashboard.pdf)
•	Dataset: [(https://github.com/Saher-Younas/Customer-Churn-Analysis-and-Prediction-PowerBI/blob/main/Telco_Customer_Churn_Dataset%20%20(2).csv)]
________________________________________
# Key Features
•	# Churn Analysis: Breakdown of churn rate, customer retention, and churn trends.
•	# Customer Demographics: Insights into gender, senior citizens, partner status, and dependents.
•	# Engagement Metrics: Analysis of monthly charges, total charges, and tenure-based engagement levels.
•	## Service & Billing Insights: Examination of payment methods, internet service types, and contract duration impacts on churn.
•	Data-Driven Measures: Advanced DAX measures for precise analysis.
•	Filters and Slicers: A filter button has been added for enhanced interactivity, along with slicers for contract type, tenure, payment method, and services.
________________________________________
# Dashboard Insights and Analysis
# 1. Churn Rate and Retention Trends
•	The overall churn rate is 26.54%, meaning a significant portion of customers are leaving.
•	The highest churn occurs in the early tenure stage (0-12 months).
•	Customers on month-to-month contracts exhibit the highest churn rate.
•	Customers using fiber optic services have a higher churn rate compared to DSL users.
# 2. Customer Engagement and Billing Behavior
•	Customers with higher monthly charges tend to have higher engagement levels.
•	The electronic check payment method shows the highest churn rate among all payment options.
•	Customers who opted for paperless billing are more likely to churn compared to those using traditional billing methods.
# 3. Service and Contract Type Impact
•	Customers with long-term contracts (one or two years) are less likely to churn.
•	Customers with multiple lines show a lower churn rate than single-line users.
•	High-speed fiber optic internet users are at the highest risk of churning.
# 4. Churn Rate by Demographics
•	Senior citizens have a higher churn rate compared to younger customers.
•	Customers without dependents or partners are more likely to leave.
•	Gender does not play a significant role in churn probability.
# 5. Monthly Charges and Total Charges Distribution
•	Customers paying higher monthly charges are more likely to churn.
•	However, customers with a high total charge (longer tenure) are more likely to stay.
•	The distribution pattern shows that lower monthly charge customers tend to be retained longer.
# 6. Tenure-Based Churn Segmentation
•	New customers (tenure 0-6 months) have the highest churn risk.
•	Customers with a tenure of more than 24 months are more likely to stay.
•	Customers in the first year of their contract require additional engagement strategies to reduce churn.
# 7. Internet Service Type and its Effect on Churn
•	Fiber optic internet users show a significantly higher churn rate than DSL or customers without internet service.
•	DSL users are relatively stable, with a lower churn rate.
•	Customers with no internet service have the lowest churn, likely due to using only phone services.
# 8. Payment Method and Billing Impact on Churn
•	Electronic check users have the highest churn rate, followed by credit card automatic payments.
•	Customers using bank transfers or mailed checks have a lower churn rate.
•	The inclusion of automatic payment options can potentially reduce churn for customers at risk.
________________________________________
# Filters and Slicers in the Dashboard
A filter button has been added to allow users to dynamically explore churn trends across various dimensions. The following slicers have been included to refine insights:
•	# Contract Type #: Filters data based on month-to-month, one-year, or two-year contracts.
•	Tenure: Allows segmentation of customers based on their subscription duration.
•	Payment Method: Enables analysis based on credit card, electronic check, mailed check, or bank transfer.
•	Services Used: Provides insights based on multiple-line usage, internet service type, and additional services such as streaming or security packages.
________________________________________
# Data Enhancements and Custom Measures
To enhance analytical capabilities, additional custom columns and measures were created using DAX (Data Analysis Expressions).
# Custom Measures in Power BI (DAX Code)
# 1. Churn Rate Calculation
Churn Rate = 
VAR TotalCustomers = COUNT(CustomerID)
VAR ChurnedCustomers = CALCULATE(COUNT(CustomerID), Churn="Yes")
RETURN DIVIDE(ChurnedCustomers, TotalCustomers, 0)
# 2. Count of Active Customers
Active Customers = CALCULATE(COUNT(CustomerID), Churn="No")
# 3. Engagement Level Classification (Low, Moderate, High)
Engagement Level = 
SWITCH(
    TRUE(),
    [MonthlyCharges] < 30, "Low",
    [MonthlyCharges] >= 30 && [MonthlyCharges] < 70, "Moderate",
    [MonthlyCharges] >= 70, "High",
    "Unknown"
)
# 4. Multi-Line User Classification
Multi-Line User = 
IF( [MultipleLines] = "Yes", "Multi-Line", "Single-Line")
# 5. Senior Citizen Percentage
Senior Citizen Percentage = 
DIVIDE(
    CALCULATE(COUNT(CustomerID), [SeniorCitizen] = 1),
    COUNT(CustomerID),
    0
)
# 6. Tenure Growth Stage Classification
Tenure Stage = 
SWITCH(
    TRUE(),
    [Tenure] <= 12, "New Customer",
    [Tenure] > 12 && [Tenure] <= 36, "Established Customer",
    [Tenure] > 36, "Loyal Customer",
    "Unknown"
)
# 7. Tenure Segmentation (Monthwise)
Tenure Segmentation = 
SWITCH(
    TRUE(),
    [Tenure] <= 6, "0-6 months",
    [Tenure] > 6 && [Tenure] <= 12, "6-12 months",
    [Tenure] > 12 && [Tenure] <= 24, "1-2 years",
    [Tenure] > 24 && [Tenure] <= 48, "2-4 years",
    [Tenure] > 48, "4+ years",
    "Unknown"
)
________________________________________
# Step-by-Step Implementation
1. Data Preparation and Preprocessing
•	Load the telecom customer dataset.
•	Clean missing values and remove irrelevant columns.
•	Transform categorical values into meaningful labels.
2. Creating Power BI Dashboard
•	Import the cleaned dataset into Power BI.
•	Use DAX functions to create calculated measures.
•	Design interactive visuals using charts, KPIs, slicers, and filters.
3. Analysis and Insights
•	Identify high-risk churn segments using filters and charts.
•	Compare churn trends across contract types, payment methods, and services.
•	Validate insights using DAX measures and custom calculations.
4. Business Recommendations
•	Encourage long-term contracts to reduce churn.
•	Offer discounts and loyalty benefits to early-stage customers.
•	Improve customer service for fiber optic users to lower churn.
________________________________________
# Future Enhancements
•	Implement machine learning models for churn prediction.
•	Enable real-time data updates in Power BI.
•	Introduce behavioral and demographic clustering for deeper insights.
This README now includes structured insights for all visualizations, enhanced details about filters and slicers, and optimized DAX code. Let me know if you need further refinements.

