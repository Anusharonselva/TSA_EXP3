# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
Date:
Developed by: ANUSHARON.S
Register no.:212222240010

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
from statsmodels.graphics.tsaplots import plot_acf

df = pd.read_csv('/content/Paris 2024 Olympics Nations Medals.csv')

data = df['Total'].values

mean_data = np.mean(data)
var_data = np.var(data)

normalized_data = (data - mean_data) / np.sqrt(var_data)

def autocorrelation(x, lag):
    n = len(x)
    x_mean = np.mean(x)
    autocorr = np.correlate(x - x_mean, x - x_mean, mode='full')[n - 1:] / (n * np.var(x))
    return autocorr[:lag]

acf_values = autocorrelation(normalized_data, 35)

lags = np.arange(35)
plt.stem(lags, acf_values)
plt.title('ACF Plot for First 35 Lags - Total Medals')
plt.xlabel('Lags')
plt.ylabel('ACF Value')
plt.grid(True)
plt.show()

plot_acf(normalized_data, lags=35)
plt.show()



```

### OUTPUT:
![Screenshot 2024-09-14 092429](https://github.com/user-attachments/assets/fd5082d1-e714-4782-a531-9d6a19d9ae43)

![Screenshot 2024-09-14 092447](https://github.com/user-attachments/assets/cc199f3b-adcc-4dfe-96df-be3bf0bce789)


### RESULT:
        Thus the auto correlation function in python is successfully implemented.
