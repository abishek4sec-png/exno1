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

# Coding and Output
  ```
import pandas as pd
import numpy as np
```
```
df=pd.read_csv("/content/SAMPLEIDS.csv")
df
```
```
df.isnull()
df.notnull()
df.isnull().sum()
df.notnull().sum()
df.shape
df.describe()
df.info()
df.head(3)
df.tail(3)
df.dropna(how='any').shape
x=df.dropna(how='any')
x

total=df.dropna(subset=['TOTAL'],how='any')
total

tot = df.dropna(subset=['M1','M2','M3','M4'], how='any')
tot

s=df.fillna(0)
s

mn=df.TOTAL.mean()
mn

df.TOTAL.fillna(mn,inplace=True)
df

df.drop_duplicates(inplace=True)
df

df.shape
import seaborn as sns
sns.heatmap(df.isnull(),yticklabels=False,annot=True)
df.dropna(inplace=True)
sns.heatmap(df.isnull(),yticklabels=False,annot=True)
```
outlier detection IQR
```
import pandas as pd
import seaborn as sns
import numpy as np
```
```
age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af=pd.DataFrame(age)
af
```
```
sns.boxplot(data=af)
sns.scatterplot(data=af)
```
```
q1=af.quantile(0.25)
q2=af.quantile(0.50)
q3=af.quantile(0.75)
iqr=q3-q1
iqr
```
```
Q1= np.percentile(af,25)
Q3= np.percentile(af,75)
IQR=Q3-Q1
print(IQR)
```
```
lower_bound = Q1 - 1.5 * IQR
upper_bound = Q3 + 1.5 * IQR
print(lower_bound)
```
```
upper_bound

outlier=[x for x in age if  x<lower_bound or x>upper_bound]
outlier

af = af[(af > lower_bound) & (af < upper_bound)]
af

af.dropna()
sns.boxplot(data=af)
sns.scatterplot(data=af)
```
```
data=[1,2,2,2,3,1,1,15,2,2,3,1,1,2]
mean=np.mean(data)
std=np.std(data)
print("mean of the datasets", mean)
print("standard deviation of the datasets", std)
```
```
thresold =3
outlier=[]
for i in data:
  z=(i-mean)/std
  if z>thresold:
    outlier.append(i)
print("outlier of the datasets", outlier)
```
```
data={'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,
                66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]}
```
```
import numpy as np
import pandas as pd
import seaborn as sns
from scipy import stats
```
```
data={'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,
                66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]}

df=pd.DataFrame(data)
df
```

 <img width="887" height="590" alt="image" src="https://github.com/user-attachments/assets/46249ecd-84ff-47c2-95ca-5e369b7f1456" />
<img width="726" height="570" alt="image" src="https://github.com/user-attachments/assets/c1e9ec10-73fe-4581-8f78-5a75158b147a" />
<img width="697" height="172" alt="image" src="https://github.com/user-attachments/assets/554bf17e-8b84-435f-820f-f806a1e8655f" />

<img width="696" height="580" alt="image" src="https://github.com/user-attachments/assets/d86c938c-253f-4d85-b989-48e5b5d39edd" />
<img width="706" height="146" alt="image" src="https://github.com/user-attachments/assets/038ad0e5-dad3-42a6-9d5d-5c96c77eaa08" />

<img width="181" height="460" alt="image" src="https://github.com/user-attachments/assets/882377d9-98f3-4109-81ca-cbbc7362827b" />
<img width="206" height="462" alt="image" src="https://github.com/user-attachments/assets/19a0a01a-b879-4379-9686-0bf24e6f8454" />
<img width="818" height="497" alt="image" src="https://github.com/user-attachments/assets/9cdbefb9-6438-4acd-92d3-fe1d0454bb9e" />
<img width="452" height="397" alt="image" src="https://github.com/user-attachments/assets/3218cb72-2d00-42bc-8ede-3ab47bb91814" />
<img width="827" height="233" alt="image" src="https://github.com/user-attachments/assets/f59af8f6-27a8-4c87-a354-503087bc8d31" />
<img width="836" height="155" alt="image" src="https://github.com/user-attachments/assets/9c9a8949-d2d7-47a8-a8b2-6b3f0697613a" />
<img width="847" height="582" alt="image" src="https://github.com/user-attachments/assets/b94cbb94-8107-410a-b532-32ce2515457e" />
<img width="843" height="542" alt="image" src="https://github.com/user-attachments/assets/a2d773b1-2904-4bba-8f61-9824c849e76b" />
<img width="848" height="451" alt="image" src="https://github.com/user-attachments/assets/5a7d5494-ea71-4518-974b-09066a07d8ff" />
<img width="857" height="577" alt="image" src="https://github.com/user-attachments/assets/d5d1004d-f25e-47f0-ad68-1aba13baf681" />
<img width="852" height="153" alt="image" src="https://github.com/user-attachments/assets/5a1dc93a-5c5c-4b3d-aac9-1673b6748b55" />
<img width="857" height="562" alt="image" src="https://github.com/user-attachments/assets/32589cf7-1484-4cfd-a608-b6e8bcec193d" />
<img width="838" height="128" alt="image" src="https://github.com/user-attachments/assets/cb93d65a-9105-4598-9651-da4af0112df4" />
<img width="840" height="568" alt="image" src="https://github.com/user-attachments/assets/c09d502d-4e4f-4e3d-96e5-4002db7f561b" />
<img width="857" height="147" alt="image" src="https://github.com/user-attachments/assets/e84f06b0-da1a-4031-ada6-2fec2cfb09ab" />
<img width="491" height="471" alt="image" src="https://github.com/user-attachments/assets/27dc648e-63ff-4c59-b7c3-d2dd1c692e42" />
<img width="520" height="471" alt="image" src="https://github.com/user-attachments/assets/0fb7f61b-9c49-46dd-b28f-26e48ba6ad67" />
<img width="167" height="505" alt="image" src="https://github.com/user-attachments/assets/e2bc54d3-e9e2-46ca-926b-243abb298005" />
<img width="543" height="413" alt="image" src="https://github.com/user-attachments/assets/e40943e1-ba13-4cca-bc2f-4d4be939d2f5" />
<img width="543" height="413" alt="image" src="https://github.com/user-attachments/assets/ebf98dad-b4ac-40e6-8722-c749dc07a21c" />
<img width="287" height="487" alt="image" src="https://github.com/user-attachments/assets/2ab5a381-fa48-489f-bdb7-667cd7a521a7" />
<img width="137" height="367" alt="image" src="https://github.com/user-attachments/assets/6e365943-5403-45da-87ae-7878c47cb512" />
<img width="543" height="413" alt="image" src="https://github.com/user-attachments/assets/bd8fe3c4-fd92-44ec-af09-5492bbbeded8" />
<img width="543" height="413" alt="image" src="https://github.com/user-attachments/assets/c9f52720-df87-4bbe-983b-4e9a131a8983" />

<img width="457" height="65" alt="image" src="https://github.com/user-attachments/assets/2fa13b90-6068-4926-9e3b-c119b8a89ba9" />


<img width="272" height="52" alt="image" src="https://github.com/user-attachments/assets/7a097e14-25e2-43a6-ae0d-6b10e1fe3c86" />


<img width="165" height="582" alt="image" src="https://github.com/user-attachments/assets/4ebf4097-4ff3-42d2-91d3-910bd8cbd2e0" />


<img width="142" height="540" alt="image" src="https://github.com/user-attachments/assets/432f29f1-fe35-4ce2-a7f6-39c53440508b" />




# Result
Thus, the given dataset was successfully cleaned by handling missing values, detecting and removing outliers using the IQR and Z-score methods, and the cleaned data was prepared for further analysis.
