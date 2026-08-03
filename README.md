 # Forecasting The Future Sales

## Problem Statement: Budget planning of capital  to the categories for the first month of 2019

### Original Sales Data

<img width="800" height="300" alt="Image" src="https://github.com/user-attachments/assets/a9ceea8e-6ce7-4691-8fc4-b333f6274ecd" />

### Cleaned Sales Data 

<img width="800" height="300" alt="Image" src="https://github.com/user-attachments/assets/eea299ed-43f0-4a1d-8aec-2122e986b881" />

### Statistical details of Sales data

<img width="800" height="300" alt="Image" src="https://github.com/user-attachments/assets/2b64d5ee-0bcf-4a9e-b521-a1397d0c732c" />

>The data has details of orders from the year of 2015 to 2018

>The above image showing that standard deviation greater than mean value that simply means that sales values are widely dispersed and not closer to the mean value

>The sales values are between 250 to 22700

### Total Sales Over The Time By each Year

<img width="800" height="300" alt="Image" src="https://github.com/user-attachments/assets/92a47368-eb35-494c-88e1-08ec06b572c2" />

>This image clearly depicting that in which months sales are in high spike of each year

>August generates the highest revenue  month  in 2015 and 2016 years

>February generates the highest revenue month in 2017 and 2018 years<img width="1600" height="662" alt="Sales_img6" src="https://github.com/user-attachments/assets/76238874-04cc-4f92-967f-d4ef7c1d3ddd" />

### Total Sales of Category By Region

<img width="800" height="300" alt="Image" src="https://github.com/user-attachments/assets/c0eec271-be9e-4d59-9655-f95f3ad0a76b" />

### The insights from the Category analysis by region

>All categories generates high revenue in east and west region among all regions 

>East and west are best performing regions with small differences

>South was contributing least revenue as compared to the remaining

>Technology in east region generates highest sales and furniture in south generates the least revenue

### Sales Data Required fields For Training And Testing

<img width="800" height="300" alt="Image" src="https://github.com/user-attachments/assets/afca831c-557d-4270-a2cd-f390b429abc8" />

>Now this data is used for three purpose, the first one is for training the data model using the data of 2015 to 2017 from the monthly sales data

>The second purpose is for test the 2018 data by getting from the monthly sales data

>The third purpose is to get the last three month of data from monthly sales for predicting first month sales of 2019

### original sales and Predicted Sales data of 2018

<img width="800" height="300" alt="Image" src="https://github.com/user-attachments/assets/7f194cfe-5044-4689-8a24-3dd6e27de664" />

>First we prepare and train the 2015 to 2017 data using the random forest regressor

>Next make predictions on 2018 data to check how much predicted sales and sales match.

>As the actual sales and predicted sales of 2018 are almost perfectly matched.

>And it also shows the average growth value by region and category over the time

>Increase investment on category by region if growth value is 20 or more

>Maintain same investment on category if growth value is less than 20 or zero

>Reduce the investment on category if growth values shows in negative values

### 





