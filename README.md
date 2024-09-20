# Ex.No:04   FIT ARMA MODEL FOR TIME SERIES
# Date: 



### AIM:
To implement ARMA model in python.
### ALGORITHM:
1. Import necessary libraries.
2. Set up matplotlib settings for figure size.
3. Define an ARMA(1,1) process with coefficients ar1 and ma1, and generate a sample of 1000

data points using the ArmaProcess class. Plot the generated time series and set the title and x-
axis limits.

4. Display the autocorrelation and partial autocorrelation plots for the ARMA(1,1) process using
plot_acf and plot_pacf.
5. Define an ARMA(2,2) process with coefficients ar2 and ma2, and generate a sample of 10000

data points using the ArmaProcess class. Plot the generated time series and set the title and x-
axis limits.

6. Display the autocorrelation and partial autocorrelation plots for the ARMA(2,2) process using
plot_acf and plot_pacf.
### PROGRAM:
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.arima_process import ArmaProcess
from statsmodels.graphics.tsaplots import plot_acf, plot_pacf
import warnings
warnings.filterwarnings('ignore')

# Load the furniture store sales data (replace with your actual file and encoding if necessary)
file_path = '/content/Super_Store_data.csv'  # Path to the sales dataset
data = pd.read_csv(file_path, encoding='ISO-8859-1', nrows=200)  # Adjust encoding if necessary

# Print columns to identify the correct column for sales
print(data.columns)

# Use the correct sales column (Replace '<correct_column_name>' with the actual column name for sales)
sales_data = data['Order Date'].dropna()  # Replace with actual sales column name

# Plot settings
plt.rcParams['figure.figsize'] = [10, 7.5]

# Simulate ARMA(1,1) Process
ar1 = np.array([1, 0.33])
ma1 = np.array([1, 0.9])
ARMA_1 = ArmaProcess(ar1, ma1).generate_sample(nsample=len(sales_data))

# Plot the simulated ARMA(1,1) process
plt.plot(ARMA_1)
plt.title('Simulated ARMA(1,1) Process for Sales Data')
plt.xlim([0, 200])
plt.show()

# Plot ACF and PACF for ARMA(1,1)
plot_acf(ARMA_1)
plot_pacf(ARMA_1)

# Simulate ARMA(2,2) Process
ar2 = np.array([1, 0.33, 0.5])
ma2 = np.array([1, 0.9, 0.3])
ARMA_2 = ArmaProcess(ar2, ma2).generate_sample(nsample=len(sales_data) * 10)

# Plot the simulated ARMA(2,2) process
plt.plot(ARMA_2)
plt.title('Simulated ARMA(2,2) Process for Sales Data')
plt.xlim([0, 200])
plt.show()

# Plot ACF and PACF for ARMA(2,2)
plot_acf(ARMA_2)
plot_pacf(ARMA_2)


OUTPUT:
SIMULATED ARMA(1,1) PROCESS:
![Screenshot 2024-09-20 184558](https://github.com/user-attachments/assets/a474f2b4-1422-4ea1-9453-a094777b0476)

Partial Autocorrelation:
![Screenshot 2024-09-20 184608](https://github.com/user-attachments/assets/b4e958a6-d164-4bc8-8ce6-ddedbab8c560)

Autocorrelation:
![Screenshot 2024-09-20 184620](https://github.com/user-attachments/assets/eddc8068-0893-4a1d-8e21-63a8fd92c943)

SIMULATED ARMA(2,2) PROCESS:
![Screenshot 2024-09-20 184635](https://github.com/user-attachments/assets/dde96ba0-c276-4a89-ad19-343d851672d5)

Partial Autocorrelation:
![Screenshot 2024-09-20 184705](https://github.com/user-attachments/assets/ddde3176-b5e5-45a5-8d6a-ded86a7ac575)

Autocorrelation
![Screenshot 2024-09-20 184717](https://github.com/user-attachments/assets/cd264806-0902-408f-9cba-31468055cd8e)


RESULT:
Thus, a python program is created to fir ARMA Model successfully.
