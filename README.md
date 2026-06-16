 📌 Project Title
🏥 Patient Health Records Data Preprocessing Project



________________________________________
📌 Project Title
Patient Health Records Data Preprocessing and Outlier Detection using Python
________________________________________
📖 Project Description
This project demonstrates real-world healthcare data preprocessing techniques using Python.
The project performs:
	Missing Value Handling 
	Data Imputation 
	KNN Imputation 
	Outlier Detection 
	Winsorization 
	Feature Engineering 
	Dataset Cleaning 
	Data Export 
The dataset contains patient health information such as:
	Age 
	Gender 
	Region 
	BMI 
	Cholesterol 
	Glucose Level 
________________________________________
🎯 Objectives
✅ Handle missing values
✅ Impute categorical and numerical data
✅ Detect outliers
✅ Remove extreme values
✅ Prepare clean data for Machine Learning models
________________________________________
📂 Dataset Features
Column	Description
patient_id	Unique Patient ID
age	Patient Age
gender	Male/Female
region	Geographic Region
bmi	Body Mass Index
cholesterol	Cholesterol Level
glucose	Glucose Level
________________________________________
🛠 Libraries Used
import pandas as pd
import numpy as np
from sklearn.impute import SimpleImputer
from sklearn.impute import KNNImputer
from scipy.stats import zscore
from scipy.stats.mstats import winsorize
import matplotlib.pyplot as plt
________________________________________
🚀 Step 1: Create Dataset

data=({
    'patient_id': [1, 2, 3, 4, 5, 6, 7, 8, 9, 10],
    'age': [25, 30, np.nan, 50, 35, 42, 28, np.nan, 55, 48],
    'gender': ['Male', 'Female', 'Male', np.nan, 'Male', 'Female', 'Male', 'Female', np.nan, 'Male'],
    'region': ['North', 'South', np.nan, 'West', 'North', 'East', 'South', 'West', 'North', np.nan],
    'bmi': [22.5, 27.1, 30.2, np.nan, 26.4, 24.8, 50.0, 23.5, 5.0, 28.7],
    'blood_pressure': [120, 130, 140, 125, 135, 128, 250, 122, 118, 220],
    'cholesterol': [180, 210, np.nan, 190, 220, 200, 400, 185, 50, np.nan],
    'glucose': [90, 100, 110, np.nan, 105, 95, 300, 92, 30, np.nan],
    'disease_risk': [0, 1, 1, 0, 1, 0, 1, 0, 1, 1]
})
df=pd.DataFrame(data)
print(df)
screenshort
![Original Dataset](screenshots/original_dataset.png)

# Check missing values
print("\nMissing Values:")
![Missing Values](screenshots/missing_values.png)
print(df.isnull().sum())________________________________________
🔹 Step 2: Mean Imputation
Replace missing BMI values using Mean.
mean_imputer = SimpleImputer(strategy='mean')
df['bmi'] = mean_imputer.fit_transform(df[['bmi']])
Output
BMI missing values replaced with mean value.
________________________________________
🔹 Step 3: Region Imputation
Replace missing Region using Most Frequent value.
cat_imputer = SimpleImputer(strategy='most_frequent')
df['region'] = cat_imputer.fit_transform(df[['region']])
________________________________________
🔹 Step 4: Gender Imputation
gender_imputer = SimpleImputer(strategy='most_frequent')

df['gender'] = gender_imputer.fit_transform(df[['gender']])
________________________________________
🔹 Step 5: Random Sample Imputation
Create missing indicator and fill Age values randomly.
df['age_missing'] = df['age'].isnull().astype(int)
________________________________________
🔹 Step 6: KNN Imputation
Convert categorical values into numeric form.
df['gender'] = df['gender'].map({
    'Male':0,
    'Female':1
})

knn = KNNImputer(n_neighbors=2)

df[cols] = knn.fit_transform(df[cols])
Output
Missing values filled using nearest neighbors.
Screenshort
![KNN Imputation](screenshots/knn_imputation.png)
________________________________________
🔹 Step 7: Z-Score Outlier Detection
z_scores = zscore(df[['cholesterol','glucose']])

outliers = (abs(z_scores) > 3)
Formula
Z=(X-μ)/σ

________________________________________
🔹 Step 8: IQR Method
Q1 = df['bmi'].quantile(0.25)
Q3 = df['bmi'].quantile(0.75)

IQR = Q3 - Q1
Formula
IQR=Q3-Q1
Lower=Q1-1.5(IQR)
Upper=Q3+1.5(IQR)

________________________________________
🔹 Step 9: Percentile Method
lower_limit = df['cholesterol'].quantile(0.01)
upper_limit = df['cholesterol'].quantile(0.99)
Remove values outside the percentile range.
________________________________________
🔹 Step 10: Winsorization
df['glucose_winsorized'] = winsorize(
    df['glucose'],
    limits=[0.05,0.05]
)
Purpose
Extreme values are capped instead of removed.
________________________________________
🔹 Step 11: Save Clean Dataset
df.to_csv(
    "final_clean_dataset.csv",
    index=False
)
Output:
Dataset saved successfully!
________________________________________
📊 Techniques Implemented
Technique	Purpose
Mean Imputation	Fill numerical missing values
Most Frequent Imputation	Fill categorical values
Random Sample Imputation	Preserve data distribution
KNN Imputation	Smart missing value handling
Z-Score	Detect outliers
IQR Method	Detect extreme values
Percentile Method	Remove outliers
Winsorization	Cap extreme values
________________________________________
📈 Workflow
Raw Dataset
      ↓
Missing Value Detection
      ↓
Imputation Techniques
      ↓
Feature Engineering
      ↓
Outlier Detection
      ↓
Winsorization
      ↓
Final Clean Dataset
      ↓
CSV Export
________________________________________
🏆 Learning Outcomes
After completing this project, you will understand:
	Data Cleaning 
	Missing Value Handling 
	Feature Engineering 
	Outlier Detection 
	Data Preprocessing Pipeline 
	Machine Learning Data Preparation 
________________________________________
👨‍💻 Author
Rahul Zala
MCA Student | Python Developer | Data Science Enthusiast
________________________________________
⭐ Project Highlights
✅ Real-world healthcare dataset
✅ Advanced preprocessing techniques
✅ Outlier detection methods
✅ Machine Learning ready dataset
✅ End-to-End Data Cleaning Pipeline
________________________________________
You can copy this entire content into a file named README.md and upload it to GitHub with your notebook project2.ipynb.

