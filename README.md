# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
Date: 

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

```c
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd

```
```c
df = pd.read_csv("/content/IOT-temp.xls")
data = df['temp'].dropna().values  
```
#Lags
```c
N = len(data)
lags = range(35)
```
#Pre-allocate autocorrelation table
```c
autocorr_values = []
```
#Mean
```c
mean_data = np.mean(data)

```
#Variance
```c
variance_data = np.var(data)
```

#Normalized data
```c
normalized_data = (data mean_data) / np.sqrt(variance_data)
```

#Go through lag components one-by-one
```c
for lag in lags:
    if lag == 0:
        autocorr_values.append(1)
    else:
        auto_cov = np.sum((data[:-lag] - mean_data) * (data[lag:] - mean_data)) / N
        autocorr_values.append(auto_cov / variance_data)
```
#display the graph
```c
plt.figure(figsize=(10, 6))
plt.stem(lags, autocorr_values)
plt.title('Autocorrelation of IoT Temperature Data')
plt.xlabel('Lag')
plt.ylabel('Autocorrelation')
plt.grid(True)
plt.show()
```
### OUTPUT:
![download](https://github.com/user-attachments/assets/95533530-9a66-4c1a-a8b6-2613fa9d12b2)


### RESULT:
        Thus we have successfully implemented the auto correlation function in python.
