### Developed By : Shriram S
### Reg. NO . 212222240098
### Date: 

# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION


### AIM:

To Illustrates how to perform time series analysis and decomposition on the Vegetable Prices data.

### ALGORITHM:

1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:


```py

# Importing the required libraries
import pandas as pd
from statsmodels.tsa.seasonal import seasonal_decompose
import matplotlib.pyplot as plt

# Load the dataset
  # Replace with the correct path to your file
df = pd.read_csv('prices.csv')

# Display the first 5 rows of the dataset
print("First 5 Rows of the dataset:")
print(df.head())

# Converting the 'date' column to datetime and setting it as the index
df['Price Dates'] = pd.to_datetime(df['Price Dates'], format='%d-%m-%Y') 
df = df.set_index('Price Dates')

# Filling missing values for the "tank" column (if any) using forward fill
df.fillna(method='ffill', inplace=True)

# Performing seasonal decomposition on the "tank" feature (additive model)
decomposition = seasonal_decompose(df['Methi'], model='additive', period=7)

# Plot and save each component separately with different colors

# Plot and save the observed (original) data
plt.figure(figsize=(10, 4))
decomposition.observed.plot(color='red')
plt.title('Observed')
plt.ylabel('Observed')
plt.savefig('observed_plot.png')
plt.show()

# Plot and save the trend component
plt.figure(figsize=(10, 4))
decomposition.trend.plot(color='blue')
plt.title('Trend')
plt.ylabel('Trend')
plt.savefig('trend_plot.png')
plt.show()

# Plot and save the seasonal component
plt.figure(figsize=(10, 4))
decomposition.seasonal.plot(color='black')
plt.title('Seasonal')
plt.ylabel('Seasonal')
plt.savefig('seasonal_plot.png')
plt.show()

# Plot and save the residual component
plt.figure(figsize=(10, 4))
decomposition.resid.plot(color='purple')
plt.title('Residual')
plt.ylabel('Residual')
plt.savefig('residual_plot.png')
plt.show()

```


### OUTPUT:

#### FIRST FIVE ROWS:

![image](https://github.com/user-attachments/assets/2932edc5-ac4f-4b41-989b-c52976bb1e42)






#### SEASONAL PLOT REPRESENTATION :

![image](https://github.com/user-attachments/assets/62d97f4a-4353-46f1-bd4d-a7ac142f643a)


#### TREND PLOT REPRESENTATION :

![image](https://github.com/user-attachments/assets/5aeffb7b-5377-4b27-b2d4-133e184ff9af)


#### PLOTTING THE DATA:

![image](https://github.com/user-attachments/assets/fee383d5-0785-444e-8e5e-db756db6ba15)


#### OVERAL REPRESENTATION:

![image](https://github.com/user-attachments/assets/5ab7c30b-0cd6-4022-9fe8-2e7fb918377d)



### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
