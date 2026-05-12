# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
Date: 12-05-2026

### AIM:
To Compute the AutoCorrelation Function (ACF) of the data for the first 35 lags to determine the model
type to fit the data.
### ALGORITHM:
1. Import the necessary packages
2. Find the mean, variance and then implement normalization for the data.
3. Implement the correlation using necessary logic and obtain the results
4. Store the results in an array
5. Represent the result in graphical representation as given below.
### PROGRAM:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Load CSV
file_path = ("/content/amazon_sales_data 2025.csv")

df = pd.read_csv(file_path)

# Use 'item_price' column as 'money' column is not found
data = df['Price'].values

# Number of lags
lags = range(35)

autocorr_values = []

# Mean and variance
mean_data = np.mean(data)
variance_data = np.var(data)
N = len(data)

# Calculate autocorrelation
for lag in lags:

    if lag == 0:
        autocorr_values.append(1)

    else:
        auto_cov = np.sum(
            (data[:-lag] - mean_data) *
            (data[lag:] - mean_data)
        ) / N

        autocorr = auto_cov / variance_data

        autocorr_values.append(autocorr)

# Plot graph
plt.figure(figsize=(10,6))

plt.stem(lags, autocorr_values)

plt.axhline(y=0, color='red', linestyle='--')

plt.title('Autocorrelation of amazon Sales (Item Price)')

plt.xlabel('Lag')

plt.ylabel('Autocorrelation')

plt.grid(True)

plt.show()
```

### OUTPUT:

<img width="792" height="492" alt="image" src="https://github.com/user-attachments/assets/779b9e73-8a36-443b-b7b4-e47d52559e02" />

### RESULT:
        Thus we have successfully implemented the auto correlation function in python.
