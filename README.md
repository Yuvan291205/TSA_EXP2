# Ex.No: 02 LINEAR AND POLYNOMIAL TREND ESTIMATION
Date: 26.08.2025
### AIM:
To Implement Linear and Polynomial Trend Estiamtion Using Python.

### ALGORITHM:
Import necessary libraries (NumPy, Matplotlib)

Load the dataset

Calculate the linear trend values using least square method

Calculate the polynomial trend values using least square method

End the program
### PROGRAM:
A - LINEAR TREND ESTIMATION
```
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np


df = pd.read_csv("/content/Car Sales.xlsx - car_data.csv")  

df['Date'] = pd.to_datetime(df['Date'])


monthly_sales = df.groupby(df['Date'].dt.to_period("M"))['Price ($)'].mean().reset_index()
monthly_sales['Date'] = monthly_sales['Date'].dt.to_timestamp()


x = np.arange(len(monthly_sales))
y = monthly_sales['Price ($)'].values

linear_coeffs = np.polyfit(x, y, 1)
linear_trend = np.polyval(linear_coeffs, x)

plt.figure(figsize=(12,6))
plt.plot(monthly_sales['Date'], y, 'o-', label="Actual Avg Price")
plt.plot(monthly_sales['Date'], linear_trend, 'r--', label="Linear Trend")
plt.title("Car Price Trend Over Time - Linear Fit", fontsize=14)
plt.xlabel("Date")
plt.ylabel("Average Price ($)")
plt.legend()
plt.grid(True)
plt.show()
```

B- POLYNOMIAL TREND ESTIMATION
```
poly_coeffs = np.polyfit(x, y, 3)   
poly_trend = np.polyval(poly_coeffs, x)

plt.figure(figsize=(12,6))
plt.plot(monthly_sales['Date'], y, 'o-', label="Actual Avg Price")
plt.plot(monthly_sales['Date'], poly_trend, 'g-', label="Polynomial Trend (deg=3)")
plt.title("Car Price Trend Over Time - Polynomial Fit", fontsize=14)
plt.xlabel("Date")
plt.ylabel("Average Price ($)")
plt.legend()
plt.grid(True)
plt.show()
```
### OUTPUT
A - LINEAR TREND ESTIMATION
<img width="1047" height="548" alt="image" src="https://github.com/user-attachments/assets/e5e73ea7-804c-4847-9655-fcd2ecba87ac" />

B- POLYNOMIAL TREND ESTIMATION
<img width="1047" height="548" alt="image" src="https://github.com/user-attachments/assets/4e6493f7-fdf0-43cd-82f7-d5c34a5c0a76" />

## Result:
Thus the python program for linear and Polynomial Trend Estiamtion has been executed successfully.
### RESULT:
##Thus the python program for linear and Polynomial Trend Estiamtion has been executed successfully.
