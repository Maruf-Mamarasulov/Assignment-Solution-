# Assignment-Solution


# Computational Tools for Macroeconomics - Assignment Solution

## Introduction
This document outlines the solutions and approaches taken to complete the assignment on forecasting
using the FRED-MD dataset.

## Data Loading and Cleaning
Initially, the dataset is loaded using pandas, and preliminary cleaning is performed to remove any rows
with transformation codes and to reset the DataFrame index.

```python
import pandas as pd

df = pd.read_csv('~/Downloads/current.csv')
df_cleaned = df.drop(index=0)
df_cleaned.reset_index(drop=True, inplace=True)
```

## Data Transformation
Each series in the dataset requires specific transformations based on predefined codes. A function is defined
to apply these transformations accordingly.

```python
import numpy as np

def apply_transformation(series, code):
    if code == 1:
        return series
    elif code == 2:
        return series.diff()
    # Additional transformation cases here
    else:
        raise ValueError("Invalid transformation code")

# Applying transformations as per the transformation codes
for series_name, code in transformation_codes.values:
    df_cleaned[series_name] = apply_transformation(df_cleaned[series_name].astype(float), float(code))
```

## Data Plotting
Selected series are plotted to visualize the transformations applied. Matplotlib is utilized for plotting.

```python
import matplotlib.pyplot as plt
import matplotlib.dates as mdates

# Example plot for one series
plt.figure(figsize=(10, 6))
plt.plot(df_cleaned['sasdate'], df_cleaned['INDPRO'], label='Industrial Production')
plt.legend()
plt.xlabel('Date')
plt.ylabel('Value')
plt.title('Transformed Data Series')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
```

## Forecasting with ARX Models
The assignment further involves implementing ARX models for forecasting specific economic indicators. This section
will detail the steps taken to prepare the data, implement the model, and produce forecasts.

*Note: Specific code for ARX model implementation will be added based on assignment requirements.*

## Conclusion
This document provides an overview of the approaches taken to address the assignment's tasks, including data manipulation,
transformation, and initial steps towards forecasting with ARX models. 


