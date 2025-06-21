# Analyzing Electric Vehicles Population in Washington State
This project analyzes the population of electric vehicles in Washington State, focusing on attributes such as make, model, electric vehicle type, Clean Alternative Fuel Vehicle (CAFV) eligibility, electric range, county, and location. After cleaning the dataset and performing Exploratory Data Analysis (EDA) to uncover key patterns, a Decision Tree classifier is applied. To address class imbalance in the training data, the Synthetic Minority Oversampling Technique (SMOTE) is used.

# Data Source
This dataset shows the Battery Electric Vehicles (BEVs) and Plug-in Hybrid Electric Vehicles (PHEVs) that are currently registered through Washington State Department of Licensing (DOL).
https://catalog.data.gov/dataset/electric-vehicle-population-data

# Methods for Data Analysis
1. Perform Data Cleaning
2. Univariate Analysis
3. Bivariate Analysis
5. Encoding Categorical Features
6. Apply Machine Learning Model: Decision Tree
7. Evaluate Model Performance Using Classification Report and Confusion Matrix
8. Addressing Class Imbalance using SMOTE
9. Train the new Decision Tree Model
10. Evaluate Model Performance using Classification Report and Confusion Matrix

# Project Files
1. Electric-Vehicle-Analysis.rmd - Project Description and Summary of Findings
2. EV Analysis _Thy Phan.ipynb - Python Notebook

# Summary of Findings
# Univariate Analysis
## 1. Univariate Analysis of Electric Range

![image](https://github.com/user-attachments/assets/434c8eb1-c1c5-4fed-8a8f-fe733453a60b)

### The most common electric range is around 20 miles, with approximately 17,500 vehicles falling into this category — clearly dominating the distribution. 
#
![image](https://github.com/user-attachments/assets/9e91c4e3-583f-4192-a56e-9ffc322640fd)

### The electric range varies widely, with most vehicles falling between approximately 30 and 220 miles. The median range is around 60 miles, highlighting a strong skew toward lower-range vehicles.
#
## 2. Univariate Anlaysis of Electric Vehicle Types

![image](https://github.com/user-attachments/assets/3c92771e-512f-4455-9a4b-3365c760b85b)

### Battery Electric Vehicles (BEVs) make up approximately 200,000 registrations—about four times more than Plug-In Hybrid Electric Vehicles (PHEVs), which total around 50,000. This reflects a strong shift in consumer and manufacturer preference toward BEVs.
#
## 3. Univariate Analysis of Model Year

![image](https://github.com/user-attachments/assets/67aee098-c6f2-4175-991e-1925c50469d4)

### Electric vehicles started showing up around 2012, and their numbers kept growing every year. The peak was in 2023 with about 60,000 vehicles. There’s a drop in 2024, and again in 2025 and 2026— probably because those years aren’t over yet and not all vehicles have been registered.
#
## 4. Univariate Analysis of Vehicle Make

![image](https://github.com/user-attachments/assets/8dda3179-dd4b-4c7d-9aed-52766cdfe53f)

### Tesla leads the top 10 with 105,001 vehicles — nearly five times more than Chevrolet and Nissan, which have 17,840 and 15,892 respectively. Apart from Tesla, the number of vehicles across other top manufacturers is relatively similar.
#
## 5. Univariate Analysis of Vehicle Model

![image](https://github.com/user-attachments/assets/4a7fb8e9-0d35-4e73-8aa2-99b27426ea97)

### Tesla Model Y and Model 3 dominate the Top 10 Electric Vehicle Models with 51,528 and 37,427 vehicles, respectively. Interestingly, the Nissan Leaf ranks third with 13,950 vehicles—outpacing the Tesla Model S, which ranks fourth with 7,912 vehicles.
#
# Bivariate Analysis 
## 1. Bivariate Analysis for Eletric Vehicle Types with Electric Range under CAFV Eligibility

![image](https://github.com/user-attachments/assets/30c01704-c1fb-46b3-b4f5-fd6974686419)

### Battery Electric Vehicles (BEVs) generally have a significantly longer electric range—averaging around 200 miles—which qualifies most of them for Clean Alternative Fuel Vehicle (CAFV) eligibility. In contrast, BEVs with shorter ranges (~25 miles) are typically not eligible.
### Plug-in Hybrid Electric Vehicles (PHEVs), with a maximum range of about 45 miles, show a smaller distinction. Some PHEVs qualify for CAFV eligibility, while others fall just below the 20-mile threshold and are not eligible.
#
## 2. Bivariate Analysis for Electric Range and Model Year

![image](https://github.com/user-attachments/assets/05185c29-c515-4770-aaa1-893d70037613)

### Electric range has shown notable fluctuations over time. It peaked around 2010 with an average of 250 miles and again in 2020 at approximately 256 miles. However, a sharp decline is observed after 2020, continuing into 2025. This recent drop may be attributed to incomplete data for newer model years, as 2025 is still ongoing.
#
## 3. Bivariate Analysis of Makes (Top 10) and Location (longtitude, latitude)

![image](https://github.com/user-attachments/assets/84c50081-692a-499e-8ea7-9307d17f32ee)

### The top 10 EV makes are visualized based on geographic coordinates (longitude and latitude), with each make represented by a unique color. This scatter plot highlights how different EV brands are distributed across Washington State.


# Decision Tree
## 1. Plot Tree 
![image](https://github.com/user-attachments/assets/745a9fbd-7c3a-4189-b273-e1ee1cf924f8)
### The following decision tree visualization shows how the model splits on features like Model Year and Electric Range to distinguish between BEV and PHEV.
#
## 2. Classification Report and Confusion Matrix
![image](https://github.com/user-attachments/assets/aac0794a-9583-44a4-b7cd-ea9f34478710)
#
## 3. Normalized Confusion Matrix (showed percentage of each label)
![image](https://github.com/user-attachments/assets/8fc9c47a-aaa9-4483-88c9-1f364670f531)

### The initial Decision Tree model shows a strong bias toward the majority class — Battery Electric Vehicles (BEV) — over the minority class — Plug-in Hybrid Electric Vehicles (PHEV). While the model achieves 78.90% accuracy for classifying BEV (class 0), it only correctly identifies 12.77% of PHEV (class 1) cases. 
### This imbalance is showed in both the confusion matrix and the classification report, where BEV metrics notably outperform those for PHEV. To address this class imbalance and improve model fairness, I will apply the SMOTE (Synthetic Minority Over-sampling Technique) method in the next step.
#
# Address Class Imbalance
![image](https://github.com/user-attachments/assets/7191d8df-d27f-4a01-8d74-83511cdc9d3e)

### Before applying SMOTE, the dataset was imbalanced, with 121,897 Battery Electric Vehicles (BEV) and only 22,690 Plug-in Hybrid Electric Vehicles (PHEV).
### After SMOTE, the minority class (PHEV) was synthetically oversampled to match the majority class, resulting in a balanced dataset with 121,897 records for both BEV and PHEV.
#
# Decision Tree After Applying SMOTE
## 1. Plot Tree  
![image](https://github.com/user-attachments/assets/37b1cadd-53c2-4e41-a03e-6c713a3bf6f2)
### Compared to the original model, the new decision tree after applying SMOTE has more branches. This is likely because the balanced data allows the model to make more detailed splits.
#
## 2. Classification Report and Confusion Matrix
![image](https://github.com/user-attachments/assets/096129a7-2f0b-4c2d-8902-8be59ef6dc33)
#
## 3. Normalized Confusion Matrix (showed percentage of each label)
![image](https://github.com/user-attachments/assets/ad51b0c8-c4d7-4b7e-879e-55d08aae9ae0)
### After applying SMOTE, the updated decision tree model achieves 93.17% accuracy in classifying BEV (class 0) and 83.36% accuracy in classifying PHEV (class 1). This marks a significant improvement compared to the original model’s performance, which classified BEV at 78.90% and PHEV at only 12.77%.
#
# Project Wrap Up
## Websites Explored During My Electric Vehicle Analysis Project
1. Mastering Exploratory Data Analysis: https://medium.com/@nomannayeem/mastering-exploratory-data-analysis-eda-a-comprehensive-python-pandas-guide-for-data-insights-c0be7c5b8889
2. Master Visualization in EDA: https://pujitha-vasanth.medium.com/mastering-visualizations-in-eda-univariate-bivariate-and-multivariate-analyses-1ca72906205b
3. Confusion Matrix Visualization: https://medium.com/@dtuk81/confusion-matrix-visualization-fc31e3f30fea
4. Class Imbalance Strategies: https://medium.com/data-science/class-imbalance-strategies-a-visual-guide-with-code-8bc8fae71e1a
5. Seaborn documentation: https://seaborn.pydata.org/
6. Sklearn documentation: https://scikit-learn.org/stable/
7. Matplotlib documentation: https://matplotlib.org/




















