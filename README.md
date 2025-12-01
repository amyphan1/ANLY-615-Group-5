# ANLY-615-Group-5
Final Project for ANLY 615 Data Wrangling.

## Project Overview  

This project analyzes the UCI_Credit_Card dataset to investigate how credit card utilization relates to the risk of defaulting on the next month’s payment. The dataset includes data regarding 30,000 credit clients in Taiwan from April 2005 to Septemeber 2005. We cleaned the raw dataset, engineered new features such as average credit utilization, created visualizations to aid in analysis, and applied logistic regression to estimate the probability of default for different credit utilization bands (50-75%, 75-90%, >90%).  

## Purpose 

The goal of the analysis was to evaluate if credit utilization could be used to identify at-risk consumers so support could be provided. If this analysis proves to be successful in idenitfying at-risk consumers, it can be used in the future to reduce risk to the bank by providing support to at-risk consumers in the form of communication, education, and offering debt-solution coaching. 

## Dataset 

- Source: [Default of Credit Card Clients Dataset](https://www.kaggle.com/datasets/uciml/default-of-credit-card-clients-dataset) (Kaggle, originally from the UCI Machine Learning Repository).  

- File used: UCI_Credit_Card.csv 

- Observations: 30,000 credit card clients.  

- Key variables used:  

- LIMIT_BAL: credit limit.  

- BILL_AMT1 - BILL_AMT6: prior bill amounts. 

- PAY_AMT0 - PAY_AMT6: prior payment amounts.  

- DEFAULT_PMT_NEXT_MONTH: 1 if the client defaults next month, 0 otherwise.  

- Engineered variables: 

- BILL_AVG: average of the six past bill amounts.  

- AVG_CREDIT_UTIL: BILL_AVG / LIMIT_BAL 

- util_band: utilization buckets (50-75%, 75-90%, >90%).  

 

## Methods and Analysis  

1. Data Cleaning 

	- Dropped demographic columns not used in the analysis.  
	
	- Converted LIMIT_BAL to float and fixed formatting.  
	
	- Replaced payment status code -2 with NaN.  
	
	- Removed rows with BILL_AVG = 0 (no debt).  

 

2. Feature Engineering 

	- Created BILL_AVG, AVG_CREDIT_UTIL, and AVG_CREDIT_UTIL_PCT.  
	
	- Stored the cleaned data in a SQLite database and ran SQL queries to:  
	
	- Count customers above utilization thresholds (i.e., 30%) 
	
		- Broke down utilization thresholds to 50-75%, 75-90%, and >90% 
	
	- Defines “risk bands” based on utilization.  

 

3. Visualization 

	- Scatterplot: BILL_AVG vs AVG_CREDIT_UTIL colored by default status.  
	
	- Boxplot: credit utilization by default vs non‑default.  
	
	- Bar chart: default rate by utilization band.  
	
	- Confusion matrices: model performance overall and within each utilization band.  

 

4. Logistic Regression 

	- Implemented logistic regression using NumPy.  
	
	- Used features AVG_CREDIT_UTIL, LIMIT_BAL, and BILL_AVG 
	
	- Evaluated accuracy and confusion matrices for:  
	
	- All customers.  
	
	- High‑utilization bands: 50-75%, 75-90%, and >90%.  
	
	- Interpreted coefficients and odds ratios to describe how utilization and limit relate to default risk.  

 

## How to Run the Code  

1. Requirements 

	- Python 3.x  
	
	- Libraries:  
	
	- pandas 
	
	- numpy 
	
	- matplotlib 
	
	- sqlite3  
	
	- seaborn 

## Steps 

1. Clone this repository:  

	Git: clone https://github.com/amyphan2/ANLY-615-Group-5.git 

2. Install packages (example with pip):  
	
	pip install pandas numpy matplotlib statsmodels  

3. Make sure UCI_Credit_Card.csv is in the project folder.  

4. Run the notebook or script:  
	
	- Open Data Cleaning and Wrangling.ipynb and run all cells in order.  

5. The code will:  

	- Clean and save the dataset. 
	
	- Run the logistic regression.  
	
	- Display visualizations (scatterplots, boxplots, bar chart, and confusion 	matrices).  

## Project Data 

- UCI_Credit_Card.csv - raw dataset.  

- cleaned_dataset.xlsx - cleaned and engineered dataset (created by the code).  

- main.py or Data Cleaning and Wrangling.ipynb - main analysis and visualizations.  

- README.md - Project overview, purpose, info. 
