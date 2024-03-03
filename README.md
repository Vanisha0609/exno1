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
            Data Cleaning
```
import pandas as pd
import numpy as np
import seaborn as sns
import os 
df=pd.read_csv("SAMPLEIDS.csv")
df
```
![image](https://github.com/Vanisha0609/exno1/assets/119104009/b4a63d26-4e98-4503-9c6b-0c831a453164)
```
df.isnull().sum()
```
![image](https://github.com/Vanisha0609/exno1/assets/119104009/b73a58b9-a3b7-4b6e-9260-32178dd92a35)
```
df.isnull().any()
```
![image](https://github.com/Vanisha0609/exno1/assets/119104009/6c0ee64b-171f-46ae-8c3b-3608575acd79)
```
df.dropna()
```
![image](https://github.com/Vanisha0609/exno1/assets/119104009/f6e7500a-a6c0-4c77-8d34-e573f06c8541)
```
df.fillna(0)
```
![image](https://github.com/Vanisha0609/exno1/assets/119104009/6712ec53-e2c1-49c6-a189-301e6ae8a563)
```
df.fillna(method = 'ffill')
```
![image](https://github.com/Vanisha0609/exno1/assets/119104009/06632d28-0c06-46a6-adc5-18fd26e0cdee)
```
df.fillna(method = 'bfill')
```
![image](https://github.com/Vanisha0609/exno1/assets/119104009/13b13584-662a-4760-b684-8bb4048f76c0)
```
df_dropped = df.dropna()
df_dropped
```
![image](https://github.com/Vanisha0609/exno1/assets/119104009/d4e068d9-05e9-436b-9d06-08cf5a04d91d)
```
df.fillna({'GENDER':'FEMALE','NAME':'PRIYU','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![image](https://github.com/Vanisha0609/exno1/assets/119104009/2b0a9567-b4eb-46b8-9738-b59359f79bc5)

IQR(Inter Quartile Range)
import pandas as pd
ir=pd.read_csv('iris.csv')
ir
image

ir.describe()
image

import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
image

c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
image

rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
image

delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
image

sns.boxplot(x='sepal_width',data=delid)
image

Z-Score
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("heights.csv")
dataset
image

df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
iqr = q3-q1
iqr
image

low = q1 - 1.5*iqr
low
image

high = q3 + 1.5*iqr
high
image

df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
image

z = np.abs(stats.zscore(df['height']))
z
image

df1 = df[z<3]
df1
image


# Result
Hence the data was cleaned , outliers were detected and removed.
