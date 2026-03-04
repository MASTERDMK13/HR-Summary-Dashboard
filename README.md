📌 Project Overview
This project presents a comprehensive HR analytics dashboard built in Tableau, powered by a cleaned and validated dataset processed using Python (Pandas). The dashboard enables HR stakeholders to monitor workforce health, track hiring and attrition trends, and identify pay equity gaps — all in one interactive interface.
The dataset covers a workforce of 7,984 active employees across multiple departments, education levels, and job roles.

🎯 Objectives

Provide a real-time view of headcount, hiring trends, and termination patterns
Identify salary distribution disparities across gender, department, and education level
Enable data-driven recruitment and retention strategy decisions
Visualize workforce demographics to support DEI (Diversity, Equity & Inclusion) reporting


🛠️ Tools & Technologies
ToolPurposeTableauDashboard design and interactive visualizationsPython (Pandas)Data cleaning, transformation, and validationMicrosoft ExcelRaw data storage and initial exploration

📊 Dashboard Features
1. Workforce Overview

Total active employees, hiring count, and termination count at a glance
Month-over-month hiring vs. attrition trend line
Department-wise headcount breakdown

2. Demographics Analysis

Gender distribution across departments and job roles
Education level breakdown (High School, Bachelor's, Master's, PhD)
Age group distribution across the workforce

3. Salary Benchmarks

Average salary by department, role, and education level
Gender pay gap visualization — highlights equity gaps across comparable roles
Salary distribution histogram for spread analysis

4. Recruitment & Attrition Trends

Hiring trend over time (monthly/quarterly)
Termination trends with department-level drill-down
Active vs. terminated employee ratio


🐍 Python Data Preparation
Before loading data into Tableau, the following preprocessing was performed using Python:
pythonimport pandas as pd

# Load raw HR data
df = pd.read_csv('hr_raw_data.csv')

# Handle missing values
df.dropna(subset=['EmployeeID', 'Department', 'Salary'], inplace=True)
df['TerminationDate'].fillna('Active', inplace=True)

# Standardize categorical values
df['Gender'] = df['Gender'].str.strip().str.title()
df['Department'] = df['Department'].str.strip().str.upper()

# Feature engineering
df['Tenure_Years'] = (pd.to_datetime('today') - pd.to_datetime(df['HireDate'])).dt.days / 365
df['Status'] = df['TerminationDate'].apply(lambda x: 'Active' if x == 'Active' else 'Terminated')

# Export cleaned dataset
df.to_csv('hr_cleaned.csv', index=False)
print(f"Clean dataset: {df.shape[0]} records, {df.shape[1]} columns")

📁 Project Structure
HR-Summary-Dashboard/
│
├── data/
│   ├── hr_raw_data.csv          # Original dataset
│   └── hr_cleaned.csv           # Cleaned dataset (Python output)
│
├── scripts/
│   └── data_cleaning.py         # Python preprocessing script
│
├── dashboard/
│   └── HR_Dashboard.twbx        # Packaged Tableau workbook
│
├── assets/
│   └── preview.png              # Dashboard screenshot
│
└── README.md

💡 Key Insights

Attrition spike identified in Q3 correlating with performance review cycles
Pay gap of approximately 8–12% observed between male and female employees at the Senior Analyst level
Operations department had the highest termination rate, signaling potential retention risk
Master's degree holders had 23% higher average salary than Bachelor's degree holders in comparable roles


Note: Dataset used is synthetic/mock data for portfolio purposes
