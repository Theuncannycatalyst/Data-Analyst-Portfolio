# Customer Shopping Trends Analysis
## Project Overview
The dataset offers a comprehensive view of customer shopping trends, aiming to uncover patterns and behaviors in retail purchasing. It contains detailed transactional data across various product categories, customer demographics, and purchase channels. The goal is to analyse customer purchasing patterns over time, identify popular product categories and high performing segments. 
## Data Sources
The data is gotten from Kaggle website
## Tools
Python, Excel, Chatgpt
## Data cleaning and preparation
This section documents the steps taken to clean and prepare the dataset for analysis, ensuring accuracy, consistency, and readiness for further exploration. All was done using python
Loading the dataset into a pandas Dataframe from the CSV file
```
#load excel into pandas dataframe
df = pd.read_csv(r"c:\...\Data sets from kaggle\shopping_trends.csv")
```
Initial examination of the data and saving the information in various files for later reference
```
#print the headers
print(df.head())
#save the output to a csv file
df.head().to_csv("head_ouput.csv", index=False)

#print the information about the data set
print(df.info())
#saves the information to a text file
with open("info_output.txt", "w") as f:
    df.info(buf=f)

#print the statistical data
print(df.describe())
#saves the statistical data to a csv file
df.describe().to_csv("describe_output.csv", index=False)
```
handling missing data
```
#print the sum of missing values per column
print(df.isnull().sum())
```
Formating data types i.e. columns with binary yes/no converted to boolean true/false for easier comparsion and analysis
```
#convert yes/no columns to booleans for easier comparison
df["Discount Applied"] = df["Discount Applied"].map({"Yes" : True, "No":False})
df["Promo Code Used"] = df["Promo Code Used"].map({"Yes" : True, "No" : False})
```
Saving the cleaned data for future analysis
```
#load saved data with new info
df.to_csv(r"C:\..\Data Analytics Project\CustomerShoppingTrends.csv")
```
## Exploratory Data Analysis 

## Results/Findings
