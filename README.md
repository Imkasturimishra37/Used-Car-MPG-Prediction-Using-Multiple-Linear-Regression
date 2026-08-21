# Used-Car-MPG-Prediction-Using-Multiple-Linear-Regression
Problem Statement

The client/business deals with used car sales.

Customers in this sector give strong preference to less-aged cars and popular brands with good resale value. This creates a challenge for used-car businesses because they have a limited range of vehicle options to showcase.

There are also no predefined standards for determining the appropriate value and performance of a used car. Prices and evaluations may be determined using unstructured and arbitrary methods.

The objective is to use Machine Learning to analyze vehicle-related factors and predict the Miles Per Gallon (MPG) of a car, helping businesses better understand vehicle performance.

Objective

Build a Multiple Linear Regression Machine Learning model to predict the MPG of used cars based on vehicle-related features.

The project focuses on data preprocessing, exploratory data analysis, feature selection, statistical analysis, model building, model evaluation, and model optimization.

Machine Learning Approach

The project follows a structured machine learning workflow:

Business and Data Understanding
Data Loading
Exploratory Data Analysis
Missing Value Analysis
Outlier Detection and Treatment
Feature Scaling
Categorical Feature Encoding
Correlation Analysis
Multicollinearity Analysis using VIF
Feature Selection
Train-Test Split
Multiple Linear Regression
Model Evaluation
Cross-Validation
Recursive Feature Elimination (RFE)
Hyperparameter/Feature Selection using GridSearchCV
Model Saving
Dataset

The dataset contains used-car related information, including numerical and categorical vehicle features.

The dataset is initially loaded from a CSV file and stored in a MySQL database to simulate a client/business data environment.

The data is then retrieved from MySQL using SQL queries for further analysis and model building.

Data Preprocessing
Missing Value Treatment

Missing values are checked using:

isnull().any()
isnull().sum()
info()

Numerical missing values are handled using Mean Imputation with SimpleImputer.

Outlier Treatment

Boxplots are used to identify potential outliers in numerical features.

Outliers are treated using Winsorization with:

Capping method: IQR
Both tails capped
Fold: 1.5

This limits the influence of extreme values on the model.

Feature Scaling

Numerical features are scaled using MinMaxScaler so that the features are transformed to a common scale.

Categorical Encoding

Categorical variables are converted into numerical representations using OneHotEncoder.

The encoded categorical features are then combined with the scaled numerical features to create the final modeling dataset.

Exploratory Data Analysis

The project includes:

Descriptive statistics
Missing-value analysis
Frequency analysis of categorical variables
Boxplots for outlier detection
Pairplot for multivariate analysis
Correlation analysis
Correlation heatmap

The analysis also identifies highly correlated feature pairs, including:

VOL and WT
HP and SP
Multicollinearity Analysis

Variance Inflation Factor (VIF) is used to identify multicollinearity among predictors.

Based on the analysis, the highly collinear WT variable is removed before building the refined regression model.

Model Building
Algorithm

Multiple Linear Regression

The model is initially built using Ordinary Least Squares (OLS) from the statsmodels library.

The refined dataset is divided into training and testing sets using:

Test size: 20%
Random state: 0
Model Evaluation

The model is evaluated using:

R² Score

R² is used to measure how well the model explains the variation in the target variable.

RMSE

Root Mean Squared Error is calculated to measure the prediction error of the regression model.

Both training and testing performance are evaluated.

Cross-Validation

A 5-Fold Cross-Validation strategy is used to evaluate the model across multiple data splits.

The project uses:

KFold
5 folds
Shuffling
Random state: 100
R² as the evaluation metric
Feature Selection

Recursive Feature Elimination (RFE) is used along with GridSearchCV to identify an appropriate number of features.

The number of selected features is evaluated using cross-validation and R² score.

Model Saving

The final selected regression model is saved as:

mpg.pkl

The preprocessing components are also saved separately using Joblib:

meanimpute
winsor
minmax
encoding

This allows the preprocessing steps and trained model to be reused for future predictions.

Technologies Used
Python
Pandas
NumPy
Matplotlib
Seaborn
Scikit-learn
Statsmodels
Feature-engine
SQLAlchemy
MySQL
Joblib
Pickle
Project Workflow
Used Car Dataset
       ↓
MySQL Database
       ↓
Data Extraction
       ↓
EDA
       ↓
Missing Value Treatment
       ↓
Outlier Treatment
       ↓
Feature Scaling
       ↓
Categorical Encoding
       ↓
Correlation Analysis
       ↓
VIF / Multicollinearity Analysis
       ↓
Feature Selection
       ↓
Train-Test Split
       ↓
Multiple Linear Regression
       ↓
R² & RMSE Evaluation
       ↓
5-Fold Cross Validation
       ↓
RFE + GridSearchCV
       ↓
Final Model
       ↓
Model Saving
Project Structure
used-car-mpg-prediction/
│
├── data/
│   └── CarswithEnginetype.csv
│
├── models/
│   ├── mpg.pkl
│   ├── meanimpute
│   ├── winsor
│   ├── minmax
│   └── encoding
│
├── notebooks/
│   └── used_car_mpg_prediction.ipynb
│
├── requirements.txt
├── README.md
└── .gitignore
