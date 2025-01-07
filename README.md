# Customer Shopping Trends Analysis
## Project Overview
The dataset offers a comprehensive view of customer shopping trends, aiming to uncover patterns and behaviors in retail purchasing. It contains detailed transactional data across various product categories, customer demographics, and purchase channels. The goal is to analyse customer purchasing patterns over time, identify popular product categories and high performing segments. 
## Data Sources
The data is sourced from Kaggle website
## Tools
Python
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
### Age distribution
This is the code used;
```
plt.hist(df["Age"], bins = 20, edgecolor = "k")
plt.title("Age Distribution")
plt.xlabel("Age")
plt.ylabel("Frequency")
plt.show()
```
The age distribution of the customers is uniform suggesting an even distribution of customers across different ages with slight concentration in the late 20s/early 30s and around 60
![Age distribution](https://github.com/user-attachments/assets/b86fc873-a648-4ec1-bda2-5c1834d4a9f2)
### Gender distribution
This is the code used;
```
gender_counts = df["Gender"].value_counts()
plt.figure(figsize=(8, 8))
gender_counts.plot(
    kind="pie",
    autopct = "%1.1f%%",
    startangle = 90,
    colors=["#ff9999", "#66b3ff", "#99ff99", "#ffcc99"],
    explode = [0.05]*len(gender_counts)
)
plt.title("Distribution of gender")
plt.show()
```
The pie chart reveals that males comprise the majority of customers (68%), while females make up 32%. This indicates a significantly larger proportion of male customers in the dataset
![Gender distribution](https://github.com/user-attachments/assets/e0e894cd-dc90-4bf6-b30b-2758246ce6e0)
### Category distribution
This is the code used;
```
category_counts = df["Category"].value_counts()
plt.figure(figsize=(8, 8))
category_counts.plot(
    kind="pie",
    autopct = "%1.1f%%",
    startangle = 90,
    colors=["#ff9999", "#66b3ff", "#99ff99", "#ffcc99"],
    explode = [0.05]*len(category_counts)
)
plt.title("Product Categories")
plt.ylabel("")
plt.show()
```
The pie chart illustrates the breakdown of product categories, revealing their relative proportions within the dataset. Clothing is the most dominant category, accounting for a substantial 44.5% of the total. Following closely is Accessories at 31.8%. Footwear constitutes 15.4% of the product mix, while Outerwear represents the smallest proportion at 8.3%
![Product categories distribution](https://github.com/user-attachments/assets/f29ad360-e45b-4db8-97b5-920a48a8f712)
### Purchase amount distribution
This is the code used;
```
plt.hist(df["Purchase Amount (USD)"], bins = 20, edgecolor = "k")
plt.title("Purchase Amount Distribution")
plt.xlabel("Purchase Amount (USD)")
plt.ylabel("Count")
plt.show()
```
The distribution appears roughly uniform, indicating that purchases are relatively evenly spread across the range of approximately $20 to $100. There isn't a strong central tendency or a clearly defined peak. While there's a slight increase in frequency towards the higher end of the purchase amounts (around $90-$100), it's not a dramatic spike, but rather a gradual increase. This suggests a tendency for slightly more purchases at higher price points within the observed range, but overall the distribution is fairly even. There are no obvious outliers or gaps in the data.
![Purchase amount distribution](https://github.com/user-attachments/assets/18fdc867-73f7-4262-898e-940b47f88c4d)

### Payment method
This is the code used;
```
plt.figure(figsize=(10, 6))
df["Payment Method"].value_counts().plot(kind = "bar", color = ['#FF5733', '#33FF57', '#3357FF', '#FF33A1', '#FFD700', '#8A2BE2'], edgecolor = "black")
plt.title("Payment method frequency")
plt.xlabel("Payment Method")
plt.xticks(rotation = 0)
plt.ylabel("Count")
plt.show()
```
The chart reveals that Credit Card is the most preferred payment method, followed closely by Venmo and Cash. PayPal and Debit Card are also popular choices, while Bank Transfer is used less frequently.
![Payment method frequency](https://github.com/user-attachments/assets/325935e2-4c51-49f5-b78c-d19d4f3bf9c9)
### Sales rate by seasons
This is the code used;
```
season_counts = df["Season"].value_counts()
plt.figure(figsize=(8, 8))
season_counts.plot(
    kind="pie",
    autopct = "%1.1f%%",
    startangle = 90,
    colors=["#ff9999", "#66b3ff", "#99ff99", "#ffcc99"],
    explode = [0.05]*len(season_counts)
)
plt.title("Distribution of seasons")
plt.ylabel("")
plt.show()
```
The sales are distributed relatively evenly across all four seasons. Spring has the highest sales rate at 25.6%, followed closely by Fall at 25.0%. Winter has a sales rate of 24.9%, and Summer has the lowest, but still comparable, sales rate at 24.5%
![Sales rate by season](https://github.com/user-attachments/assets/dcf787bc-9d81-4769-98e9-3a1e8248cc19)

## Results/Findings
This section presents the key findings from the exploratory data analysis of the customer shopping trends dataset. The analysis focused on understanding customer demographics, product preferences, payment methods, and seasonal trends.
### Customer Demographics
#### Age Distribution 
The age distribution of customers is relatively uniform, spanning from approximately 18 to 70 years old, with possible minor concentrations in the late 20s/early 30s and around 60. This suggests a broad customer base across different age groups.
#### Gender Distribution
Males represent a significantly larger portion of the customer base (68%) compared to females (32%). This indicates a strong male presence among the customer population.
### Product Preferences 
Product Category Distribution: Clothing is the most popular product category, accounting for 44.5% of all purchases. Accessories follow closely at 31.8%. Footwear and Outerwear represent smaller proportions at 15.4% and 8.3%, respectively. This highlights the dominance of apparel-related items in customer purchases.
### Payment Methods
Payment Method Frequency: Credit cards are the most frequently used payment method, followed by Venmo and Cash. PayPal and Debit Card are used with comparable frequency, while Bank Transfer is the least common option. This suggests a preference for traditional payment methods and digital wallets over bank transfers.
### Seasonal Trends
Sales Rate by Season: Sales are distributed relatively evenly across all four seasons. Spring has a slightly higher sales rate (25.6%), but the difference between seasons is minimal. This indicates that seasonality does not significantly impact overall sales volume.

## Conclusion
These findings provide valuable insights into customer demographics, preferences, and behavior. This information can be used to inform marketing strategies, product development, and inventory management decisions.
