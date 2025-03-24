# Customer Churn Analysis and Prediction (Power BI)

## Overview
This project focuses on analyzing and predicting customer churn using a telecom dataset. The Power BI dashboard provides insights into churn trends, customer demographics, and engagement levels, enabling businesses to take proactive measures to reduce churn.

## Project Links
- **Power BI Dashboard:** [View Dashboard](https://github.com/Saher-Younas/Customer-Churn-Analysis-and-Prediction-PowerBI/blob/main/Customer%20Churn%20Dashboard.pdf)
- **Dataset:** [Download Dataset](https://github.com/Saher-Younas/Customer-Churn-Analysis-and-Prediction-PowerBI/blob/main/Telco_Customer_Churn_Dataset%20%20(2).csv)

---
## Key Features
- **Churn Analysis:** Breakdown of churn rate, customer retention, and churn trends.
- **Customer Demographics:** Insights into gender, senior citizens, partner status, and dependents.
- **Engagement Metrics:** Analysis of monthly charges, total charges, and tenure-based engagement levels.
- **Service & Billing Insights:** Examination of payment methods, internet service types, and contract duration impacts on churn.
- **Data-Driven Measures:** Advanced DAX measures for precise analysis.
- **Filters and Slicers:** Added filters for contract type, tenure, payment method, and services for enhanced interactivity.

---
## Dashboard Insights and Analysis
### 1. Churn Rate and Retention Trends
- The overall churn rate is **26.54%**, indicating a significant portion of customers are leaving.
- The highest churn occurs in the early tenure stage (**0-12 months**).
- **Month-to-month contract** customers exhibit the highest churn rate.
- **Fiber optic service users** have a higher churn rate compared to DSL users.

### 2. Customer Engagement and Billing Behavior
- Customers with **higher monthly charges** tend to have higher engagement levels.
- The **electronic check payment method** shows the highest churn rate.
- Customers opting for **paperless billing** are more likely to churn compared to traditional billing methods.

### 3. Service and Contract Type Impact
- Customers with **long-term contracts (one or two years)** are less likely to churn.
- Customers with **multiple lines** show a lower churn rate than single-line users.
- **High-speed fiber optic internet users** are at the highest risk of churning.

### 4. Churn Rate by Demographics
- **Senior citizens** have a higher churn rate compared to younger customers.
- Customers **without dependents or partners** are more likely to leave.
- **Gender does not significantly impact churn probability**.

### 5. Monthly Charges and Total Charges Distribution
- Customers paying **higher monthly charges** are more likely to churn.
- Customers with **higher total charges (longer tenure)** are more likely to stay.
- Lower monthly charge customers tend to be retained longer.

### 6. Tenure-Based Churn Segmentation
- **New customers (tenure 0-6 months)** have the highest churn risk.
- Customers with **tenure >24 months** are more likely to stay.
- Customers in the **first year of their contract** require additional engagement strategies.

### 7. Internet Service Type and Its Effect on Churn
- **Fiber optic internet users** have a significantly higher churn rate.
- **DSL users** are relatively stable with a lower churn rate.
- Customers with **no internet service** have the lowest churn.

### 8. Payment Method and Billing Impact on Churn
- **Electronic check users** have the highest churn rate.
- Customers using **bank transfers or mailed checks** have a lower churn rate.
- **Automatic payment options** can potentially reduce churn.

---
## Filters and Slicers in the Dashboard
A filter button allows users to dynamically explore churn trends. The following slicers refine insights:
- **Contract Type:** Filters data based on month-to-month, one-year, or two-year contracts.
- **Tenure:** Segments customers based on subscription duration.
- **Payment Method:** Enables analysis based on credit card, electronic check, mailed check, or bank transfer.
- **Services Used:** Provides insights based on multiple-line usage, internet service type, and additional services.

---
## Data Enhancements and Custom Measures
To enhance analytical capabilities, additional custom columns and measures were created using DAX (Data Analysis Expressions).

### Custom Measures in Power BI (DAX Code)
#### 1. Churn Rate Calculation
```DAX
Churn Rate =
VAR TotalCustomers = COUNT(CustomerID)
VAR ChurnedCustomers = CALCULATE(COUNT(CustomerID), Churn="Yes")
RETURN DIVIDE(ChurnedCustomers, TotalCustomers, 0)
```
#### 2. Count of Active Customers
```DAX
Active Customers = CALCULATE(COUNT(CustomerID), Churn="No")
```
#### 3. Engagement Level Classification
```DAX
Engagement Level =
SWITCH(
    TRUE(),
    [MonthlyCharges] < 30, "Low",
    [MonthlyCharges] >= 30 && [MonthlyCharges] < 70, "Moderate",
    [MonthlyCharges] >= 70, "High",
    "Unknown"
)
```
#### 4. Multi-Line User Classification
```DAX
Multi-Line User =
IF( [MultipleLines] = "Yes", "Multi-Line", "Single-Line")
```
#### 5. Senior Citizen Percentage
```DAX
Senior Citizen Percentage =
DIVIDE(
    CALCULATE(COUNT(CustomerID), [SeniorCitizen] = 1),
    COUNT(CustomerID),
    0
)
```
#### 6. Tenure Growth Stage Classification
```DAX
Tenure Stage =
SWITCH(
    TRUE(),
    [Tenure] <= 12, "New Customer",
    [Tenure] > 12 && [Tenure] <= 36, "Established Customer",
    [Tenure] > 36, "Loyal Customer",
    "Unknown"
)
```
#### 7. Tenure Segmentation (Monthwise)
```DAX
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
```

---
## Step-by-Step Implementation
### 1. Data Preparation and Preprocessing
- Load the telecom customer dataset.
- Clean missing values and remove irrelevant columns.
- Transform categorical values into meaningful labels.

### 2. Creating Power BI Dashboard
- Import the cleaned dataset into Power BI.
- Use DAX functions to create calculated measures.
- Design interactive visuals using charts, KPIs, slicers, and filters.

### 3. Analysis and Insights
- Identify high-risk churn segments using filters and charts.
- Compare churn trends across contract types, payment methods, and services.
- Validate insights using DAX measures and custom calculations.

### 4. Business Recommendations
- Encourage long-term contracts to reduce churn.
- Offer discounts and loyalty benefits to early-stage customers.
- Improve customer service for fiber optic users to lower churn.

---
## Future Enhancements
- Implement machine learning models for churn prediction.
- Enable real-time data updates in Power BI.
- Introduce behavioral and demographic clustering for deeper insights.



