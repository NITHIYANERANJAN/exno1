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
            <<include your coding and its corressponding output screen shots here>>
```
import pandas as pd
from google.colab import drive
drive.mount('/content/drive')
import pandas as pd
df=pd.read_csv('/content/drive/My Drive/SAMPLEIDS.csv')
df
```
![image](https://github.com/user-attachments/assets/812e7a2f-1aca-4d1a-8cf1-c6d1965031de)

```
df.info()
```
![image](https://github.com/user-attachments/assets/94033722-d02c-44a3-a118-26103f5f038d)

```
df.isnull()
```
![image](https://github.com/user-attachments/assets/0ba2a0dd-431a-4256-b94e-616d8948262b)
```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/54dae6f3-a037-4624-b116-891f7df7dda6)
```
df.dropna()
```
![image](https://github.com/user-attachments/assets/38cb35ea-4eef-4a32-9434-63252a025160)
```
df.fillna(0)
```
![image](https://github.com/user-attachments/assets/54705fc2-66af-46f0-976b-0140e28f99c0)
```
df.fillna(method = 'ffill')
```
![image](https://github.com/user-attachments/assets/e8723980-cf03-4c42-a244-e7335cea9494)
```
df.fillna(method = 'bfill')
```
![image](https://github.com/user-attachments/assets/08e22ffd-1d2b-4602-aafa-9d4e48a2f7b0)
```
df_dropped = df.dropna()
df_dropped
```
![image](https://github.com/user-attachments/assets/7ee7256b-5fb2-44a9-b7cc-17375532a1d2)

#IQR(INTER QUARTILE RANGE)
```
q1=af.quantile(0.25)
q3=af.quantile(0.75)
iqr=q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/a09ca64a-262a-4759-9fc9-755317adba58)
```
q1=np.quantile(age,0.25)
q3=np.quantile(age,0.75)
iqr=q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/2c6bd1a4-9905-47bd-8afa-ae4a0e998d6d)
```
lower_bound=q1-1.5*iqr
upper_bound=q3+1.5*iqr
print(lower_bound)
print(upper_bound)
```
![image](https://github.com/user-attachments/assets/b3874d22-1cec-4945-9ae0-4301363292c3)
```
outliers=[x for x in age if x<lower_bound or x>upper_bound]
print("Q1:",q1)
print("Q3:",q3)
print("IQR:",iqr)
print("Lower Bound:",lower_bound)
print("Upper Bound:",upper_bound)
print("Outliers:",outliers)
```
![image](https://github.com/user-attachments/assets/a7c74e43-a0d5-4b6b-b6fb-f4e11e48bece)
```
af=af[((af>=lower_bound)&(af<=upper_bound))]
af
```
![image](https://github.com/user-attachments/assets/f60c1c10-14dc-4ca4-bece-f1126da0a7c1)
```
af.dropna()
```
![image](https://github.com/user-attachments/assets/dc3d4b30-f712-4e1a-9efe-16a184af0aea)
```
sns.boxplot(af)
```
![image](https://github.com/user-attachments/assets/7b300f00-3deb-461d-bd86-954e993d7733)
```
mean = np.mean(data)
std = np.std(data)
print("Mean: ",mean)
print("std. deviation: ",std)
```
![image](https://github.com/user-attachments/assets/00d971cc-07db-4462-96cd-7c607b770352)
```
threshold = 3
outliers = []
for x in data:
  z_score = (x - mean) / std
  if np.abs(z_score) > threshold:
    outliers.append(x)
print("Outliers: ",outliers)
```
![image](https://github.com/user-attachments/assets/85d61da9-4b9a-43b8-bee9-5d0b452712d0)
```
z=np.abs(stats.zscore(df))
print(df[z['values']>3])
```
![image](https://github.com/user-attachments/assets/ebd6b42e-c59a-44cf-9d14-392fb13733b3)
```
def do(data):
  mean = np.mean(data)
  std = np.std(data)
  threshold = 3
  out=[]
  for x in data:
    z_score = (x - mean) / std
    if np.abs(z_score) > threshold:
      out.append(x)
  return out
op = do(data)
print(op)
```
![image](https://github.com/user-attachments/assets/0ad5e259-f7fb-43c5-90e6-04b7676219b9)
```
no_outliers=df[(z<3).all(axis=1)]
no_outliers
```
![image](https://github.com/user-attachments/assets/201f68cb-6c9c-49e7-b575-edde3fd70f18)
```
sns.boxplot(no_outliers)
```
![image](https://github.com/user-attachments/assets/abf50989-6338-4992-bcc9-d4d1b0de3b79)



# Result
Thus the given data  successfully performed data cleaning and saved the cleaned data to a file.
