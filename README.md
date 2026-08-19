# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding
```python

import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
from scipy import stats

from google.colab import files
uploaded = files.upload()

import pandas as pd

df = pd.read_csv("Data_set.csv")
df.head()

print("Dataset Information")
df.info()

print("\nStatistical Summary")
print(df.describe(include='all'))

print("\nFirst 5 Rows")
print(df.head())

print("\nLast 5 Rows")
print(df.tail())

print("Null Values")
print(df.isnull())

print("\nNull Count")
print(df.isnull().sum())

print("\nAfter Dropping Null Values")
print(df.dropna())

print("\nFill Null Values with 'O'")
print(df.fillna("O"))

print("\nForward Fill")
print(df.fillna(method="ffill"))

print("\nBackward Fill")
print(df.fillna(method="bfill"))

mean_df = df.copy()

numeric_columns = mean_df.select_dtypes(include=np.number).columns

for col in numeric_columns:
    mean_df[col].fillna(mean_df[col].mean(), inplace=True)

print(mean_df)

print("\nAfter Dropping Remaining Null Values")
print(mean_df.dropna())

age = [1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af = pd.DataFrame(age, columns=["Age"])

sns.boxplot(y=af["Age"])
plt.title("Before Removing Outliers")
plt.show()

Q1 = af["Age"].quantile(0.25)
Q3 = af["Age"].quantile(0.75)

IQR = Q3 - Q1

lower = Q1 - 1.5 * IQR
upper = Q3 + 1.5 * IQR

print("Lower Limit:", lower)
print("Upper Limit:", upper)

outliers = af[(af["Age"] < lower) | (af["Age"] > upper)]

print("\nOutliers")
print(outliers)

af_clean = af[(af["Age"] >= lower) & (af["Age"] <= upper)]

print("\nAfter Removing Outliers")
print(af_clean)

sns.boxplot(y=af_clean["Age"])
plt.title("After Removing Outliers")
plt.show()

data = [1,12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,72,75,78,81,84,87,90,93,96,99,158]

df2 = pd.DataFrame(data, columns=["Data"])

sns.boxplot(y=df2["Data"])
plt.title("Before Removing Outliers")
plt.show()

z = np.abs(stats.zscore(df2["Data"]))

print("Z Scores")
print(z)

outliers = df2[z > 3]

print("\nOutliers")
print(outliers)

df2_clean = df2[z <= 3]

print("\nAfter Removing Outliers")
print(df2_clean)

sns.boxplot(y=df2_clean["Data"])
plt.title("After Removing Outliers")
plt.show()
```

# Output
## Dataset Information
<img width="426" height="247" alt="image" src="https://github.com/user-attachments/assets/0e19a881-8c60-4746-b108-95c77360c888" />

## Statistical Summary
<img width="426" height="465" alt="image" src="https://github.com/user-attachments/assets/4f53f3ea-34dd-4ebd-bed1-7b9e1a09f04b" />

## First 5 rows
<img width="459" height="261" alt="image" src="https://github.com/user-attachments/assets/01582ede-fb64-4e17-91f2-281206c8e300" />

## Last 5 rows
<img width="495" height="256" alt="image" src="https://github.com/user-attachments/assets/3c86ae1e-fcde-4e72-846b-f4d0d8afe211" />

## Null Values
<img width="477" height="336" alt="image" src="https://github.com/user-attachments/assets/1f3e275d-0804-4c99-877e-9b1e50eae8e5" />

## Null Count
<img width="276" height="166" alt="image" src="https://github.com/user-attachments/assets/e5247d2c-627d-4308-9056-a8bbff5f550d" />

## After Dropping Null Values
<img width="468" height="484" alt="image" src="https://github.com/user-attachments/assets/6423f106-80f0-43de-b602-0f2e4b561b9b" />

## Fill Null Values with '0'
<img width="520" height="485" alt="image" src="https://github.com/user-attachments/assets/8e56d562-4f5d-4a33-91bf-f2348a2db438" />

## Forward fill
<img width="556" height="487" alt="image" src="https://github.com/user-attachments/assets/155bb547-76b9-4001-bd57-0ab829eb48ea" />

## Backward fill
<img width="450" height="481" alt="image" src="https://github.com/user-attachments/assets/e25fd73b-8723-4a30-b70a-a1087c194565" />

## After Dropping Remaining Null Values
<img width="472" height="482" alt="image" src="https://github.com/user-attachments/assets/3625a5dd-88e6-4404-afcc-0df989f3fef2" />

## Before Removing Outliers
<img width="385" height="287" alt="image" src="https://github.com/user-attachments/assets/a1332c26-4969-4574-8566-1a0de5a8ff10" />

## After Removing Outliers
<img width="216" height="282" alt="image" src="https://github.com/user-attachments/assets/6ce5a1cd-5288-489b-9c8d-cb2a8c6b3538" />
<img width="384" height="281" alt="image" src="https://github.com/user-attachments/assets/a4433347-5153-4ae8-b072-5d1195ef9f3a" />

## Before Removing Outliers
<img width="401" height="290" alt="image" src="https://github.com/user-attachments/assets/4786e9cb-960f-41c8-9a1e-d38176777ca3" />

## Z scores
<img width="372" height="96" alt="image" src="https://github.com/user-attachments/assets/6d7fea9f-56b8-41a4-9edf-5d2b89db071a" />

## After Removing Outliers
<img width="216" height="435" alt="image" src="https://github.com/user-attachments/assets/15ca74dd-455d-47cb-b7d5-0e61044f8036" />
<img width="393" height="287" alt="image" src="https://github.com/user-attachments/assets/ea193b87-57da-45cd-bf80-3938a437ce10" />


# Result
Thus, the given dataset was successfully cleaned by handling missing values, detecting and removing outliers using the IQR and Z-score methods, and the cleaned data was prepared for further analysis.
