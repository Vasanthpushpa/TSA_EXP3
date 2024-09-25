### NAME: VASANTH P
### REGISTER NO:212222240113
### DATE:25/09/2024

# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)


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


# Load the dataset to examine its structure
file_path = '/content/daily-minimum-temperatures-in-me.csv'
data = pd.read_csv(file_path)

# Display the first few rows of the dataset to understand its structure
data.head()


# Extract the 'Daily minimum temperatures' column and convert to numeric
temperature_data = pd.to_numeric(data['Daily minimum temperatures'], errors='coerce')

# Drop NaN values
temperature_data = temperature_data.dropna().values

# Calculate mean and variance
mean_temp = np.mean(temperature_data)
var_temp = np.var(temperature_data)

# Normalize the data (subtract mean and divide by standard deviation)
normalized_temp = (temperature_data - mean_temp) / np.sqrt(var_temp)

# Compute the ACF for the first 35 lags
lags = range(35)
acf_values = [
    np.corrcoef(normalized_temp[:-lag], normalized_temp[lag:])[0, 1] if lag != 0 else 1
    for lag in lags
]

# Plot the ACF results
plt.figure(figsize=(10, 6))
plt.stem(lags, acf_values, use_line_collection=True)
plt.title('Autocorrelation Function (ACF) for Daily Minimum Temperatures')
plt.xlabel('Lag')
plt.ylabel('ACF')
plt.grid(True)
plt.show()

```

### OUTPUT:
![image](https://github.com/user-attachments/assets/9e3eac8a-762f-47d7-915d-9342c07d1aec)
![image](https://github.com/user-attachments/assets/6fb26dd9-0fb9-4528-bf01-4e790e758258)



### RESULT:
Thus we have successfully implemented the auto correlation function in python.
