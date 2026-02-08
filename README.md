# Python_project_p3

## Lets Perform Data Cleaning on Superstore Sales Dataset

**Imporing required Python Libraries**
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```
**Let's First Load The  Superstore dataset**

>dataset=pd.read_csv(r"C:\Users\mahes\Desktop\python_projects\train.csv")

**Let's See The SuperStore  Dataset**

>dataset

**Display the First 5 Rows of the SuperStore Dataset**

>dataset.head(5)

**Display The last 10 Rows of the SuperStore Dataset**

>dataset.tail(10)

**Getting information about our dataset like total no of rows,total no of columns,datatype of each column 
and memory requirement**

>dataset.info()

**Let's Check Shape Of The Superstore Dataset**

>dataset.shape

**Let's Check what are columns are there in superstore dataset**

>dataset.columns

**Let's Check Is there any null values in dataset**

>dataset.isnull().sum()

**Check blank (Empty String) values**

>(dataset==" ").sum()

**Let's check duplicate value in the dataset**

>dataset.duplicated().sum()

>dataset[dataset.duplicated()]

**Let's Check duplicated values in the customer id and order id**

>dataset[dataset.duplicated(subset=['Order ID','Customer ID'])]

>dataset[dataset.duplicated(subset=['Order ID'])]

**Checking how many duplicated values in each column**

>dataset.duplicated(keep=False).sum()

**Drop The Duplicate Values in The super store Data**

>dataset.drop_duplicates(inplace=True)

**Drop The Duplicate Values in Customer ID,Order ID and Product ID**
```
dataset.drop_duplicates(
    subset=['Order ID', 'Product ID', 'Sales'],
    inplace=True
)
```
**Drop The Duplicate Values in OderID**
```
dataset.drop_duplicates(
    subset=['Order ID'],
    inplace=True
)
```
## Let's Perform Data Analysis on SuperStore Dataset

### Sales Performance Insights (Revenue-focused)

**Total & Trend Analysis**

>dataset.columns
```
dataset['Sales']=dataset['Sales'].round(2)
dataset
```
**Creating Month column from Order date column**
```
dataset['Month']=pd.to_datetime(dataset['Order Date'],errors='coerce').dt.month_name()
dataset
```
**Creating Year column from Order Date column**
```
dataset['Year']=pd.to_datetime(dataset['Order Date'],errors='coerce').dt.year
dataset
```
>dataset

**Creating *Year_Month* column from *Order date* column**

>dataset['Year_Month']=dataset['Order Date'].dt.strftime('%Y-%B')

**Let's See How Year_Month Column  Values calculated Using Order Date**

>dataset[['Order Date','Year_Month']].head()



**Calculating yearly sales trend using group by function**
```
yearly_sales=dataset.groupby(dataset['Order Date'].dt.year)['Sales'].sum()   
print(yearly_sales)
```
#### After Performing Yearly analysis ,we knew that sales are steady from 2015 to 2016 but  there is large increase in 2017 and small increase in 2018

**Lets Visually see the sales trend analysis by Year-Wise** 
```
plt.figure()
plt.plot(yearly_sales.index, yearly_sales.values, marker='o')
plt.xlabel('Year')
plt.ylabel('Total Sales')
plt.title('Yearly Sales Trend')
plt.show()
```
**Lets Check total revenue generated of every month by each year**
```
monthly_sales=dataset.groupby([dataset['Order Date']
                    .dt.year,dataset['Order Date']
                    .dt.month])['Sales'].sum()
monthly_sales
```
```
monthly_sales_year = (
    dataset.groupby(['Year_Month'])['Sales']
      .sum()
      .reset_index()
)
monthly_sales_year
```
**Visually see the sales trend analysis by Month-Wise**
```
monthly_sales.index=monthly_sales.index.astype(str)
plt.figure()
plt.plot(monthly_sales.index, monthly_sales.values, marker='o')
plt.xlabel('month')
plt.ylabel('Total Sales')
plt.title('Monthly Sales Trend')
plt.show()
```
**Calculating Top Customers by Total sales**
```
top_customer=(
    dataset.groupby('Customer Name')['Sales']
    .sum().sort_values(ascending=False)
    .head()
)
top_customer
```
**Calculating total revenue by category wise**
```
category_revenue=(dataset.groupby('Category')['Sales']
                  .sum()
                  .sort_values(ascending=False)
)
category_revenue
```
**Visually Showing Category wise comparision**
```
category_revenue.plot(kind='bar')
plt.title('Category-wise Total Revenue')
plt.xlabel('Category')
plt.ylabel('Total Revenue')
plt.show()
```
**Let's Calculate Region-Wise Total-Revenue Generated**
```
Region_revenue_df=(
    dataset.groupby('Region',as_index=False)['Sales']
    .sum()
    .sort_values('Sales',ascending=False)
)
Region_revenue_df
```
**Visually Showing Region-Wise Total_Revenue generated Percentage**
```
Region_revenue_df.plot(kind='bar')
plt.title('Region-wise Total Revenue')
plt.xlabel('Region')
plt.ylabel('Total Revenue')
plt.show()
```
**Let's Check For Top Repeated 5 Customers**

>dataset['Customer ID'].value_counts().sort_values(ascending=False).head(5)

**Let's Calculate Order Count Repeated Customers**
```
Customer_order_count=(
    dataset.groupby('Customer ID')['Order ID']
.nunique().sort_values(ascending=False)
)
Customer_order_count.head(6)
```
**Lets Check Full details of Repeated Customers**
```
Repeat_customer_data=dataset[dataset['Customer ID'].
isin(Repeated_customers)]
Repeat_customer_data
```
**Lets Check for What Categories Repeated Customers Buying**
```
Customer_order_count=(
    dataset.groupby('Customer ID')['Category']
.unique()
)
Customer_order_count
```
**Lets check what are the categories and sub-categories and their count of repeated customers purchasing**
```
Category_subcategory=(
    Repeat_customer_data.groupby(['Category','Sub-Category'])
    .size()
    .sort_values(ascending=False)
)
Category_subcategory
```
**Calculating Total_Revenue Generated By Sub_category wise**
```
Subcategory_total_revenue=(
    dataset.groupby('Sub-Category')['Sales']
    .sum()
    .sort_values(ascending=False)

)
Subcategory_total_revenue
```




