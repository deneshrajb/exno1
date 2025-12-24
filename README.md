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
import numpy as np
import pandas as pd
dt=pd.read_csv("SAMPLEIDS.csv")
dt
<img width="820" height="646" alt="image" src="https://github.com/user-attachments/assets/40c158bb-1c90-4f99-b6bd-e20c7aa17afb" />

``` dt.head() ```
<img width="812" height="201" alt="image" src="https://github.com/user-attachments/assets/7ccf2114-534b-4c68-8bb5-a4e5e257d3c1" />

``` dt.tail() ```
<img width="815" height="192" alt="image" src="https://github.com/user-attachments/assets/7e84f3ac-d321-4e81-a67a-e5d4ebbe369e" />

dt.isnull()
<img width="699" height="657" alt="image" src="https://github.com/user-attachments/assets/fbebe55f-2328-4b96-88e4-38d281b890f0" />

dt.notnull()
<img width="702" height="652" alt="image" src="https://github.com/user-attachments/assets/63512277-051e-428d-9d56-88e306614856" />

dt.dropna(axis=1)
<img width="243" height="641" alt="image" src="https://github.com/user-attachments/assets/2d60beb1-c7f7-4327-8038-f09d602cd556" />

dt.dropna(axis=0)
<img width="827" height="431" alt="image" src="https://github.com/user-attachments/assets/78bf57dc-2fa7-48f2-9ac4-a82845fd0c36" />

dt.fillna(0)
<img width="822" height="652" alt="image" src="https://github.com/user-attachments/assets/faf6cf95-3950-4143-8974-867c84e99aa9" />

dt.fillna(method='ffill')
<img width="824" height="647" alt="image" src="https://github.com/user-attachments/assets/f91117ef-8610-4d54-9d97-6f231516f73b" />

ir=pd.read_csv("iris.csv")
ir
<img width="490" height="400" alt="image" src="https://github.com/user-attachments/assets/d1d3ca54-a183-4945-bafc-ecd93ab5562e" />

import seaborn as sns
sns.boxplot(x="sepal_width",data=ir)
<img width="649" height="536" alt="image" src="https://github.com/user-attachments/assets/6ec112f2-933c-4d36-93ba-58a17b5d466d" />

q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iqr=q3-q1
rid=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid['sepal_width']
<img width="406" height="121" alt="image" src="https://github.com/user-attachments/assets/077b4178-b0ab-4026-ad99-d5884c9b8307" />

rid=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid
<img width="509" height="403" alt="image" src="https://github.com/user-attachments/assets/776bb746-8ae6-424d-93dc-10f8287ecd5c" />

rid=ir[((ir.sepal_width>(q1-1.5*iqr))&(ir.sepal_width<(q3+1.5*iqr)))]
rid['sepal_width']
<img width="471" height="248" alt="image" src="https://github.com/user-attachments/assets/b90a2ae5-7a28-468d-b3ba-d53d4104a5b7" />

import scipy.stats as stats
z=np.abs(stats.zscore(ir.sepal_width))
z
<img width="529" height="242" alt="image" src="https://github.com/user-attachments/assets/15a9c9f1-7eda-4383-a232-33ed60a0fc4e" />

# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
