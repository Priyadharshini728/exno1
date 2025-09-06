
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
ds=pd.read_csv("SAMPLEIDS.csv")
ds
```
<img width="1127" height="827" alt="image" src="https://github.com/user-attachments/assets/ff2646ca-a2a4-4b0c-9718-c2f3abe69ca6" />

```
ds.head()
```




<img width="1028" height="258" alt="image" src="https://github.com/user-attachments/assets/0fb81fb0-c08d-4ff3-ad5b-e4ea28233b13" />




```
ds.tail()
```




<img width="1181" height="301" alt="image" src="https://github.com/user-attachments/assets/f2c0b89d-bd1c-40aa-bd72-49fee1618a2f" />





```
ds.isnull()
```





<img width="871" height="827" alt="image" src="https://github.com/user-attachments/assets/36276e36-ac5a-4013-8280-62df5e8a76e7" />

```
ds.notnull()
```





<img width="1032" height="828" alt="image" src="https://github.com/user-attachments/assets/918bff74-67f9-4f2e-bb75-8d79dd36c876" />



```
ds.isnull().sum()
```

<img width="182" height="560" alt="image" src="https://github.com/user-attachments/assets/40be3ecd-910e-461c-ae67-28d084383b42" />




```
ds.dropna(axis=0)
```





<img width="1047" height="577" alt="image" src="https://github.com/user-attachments/assets/d66a99a2-2e69-436e-9b21-8acb426fa1d0" />






```
ds.fillna(2)
```





<img width="1031" height="868" alt="image" src="https://github.com/user-attachments/assets/bc3e8d56-55d8-4af9-aee0-14163428422c" />






```
ds.dropna(axis=0)
```




<img width="1180" height="568" alt="image" src="https://github.com/user-attachments/assets/d89eeaa9-6c16-49ee-b7e5-952199db9713" />





```
ds.isnull().any()
```






<img width="350" height="575" alt="image" src="https://github.com/user-attachments/assets/9329e202-3e77-4804-9420-c8e62a921b06" />





```
ds.fillna(method='ffill')
```





<img width="1035" height="879" alt="image" src="https://github.com/user-attachments/assets/e6d4cac1-8875-4861-ad0a-207b7075be1c" />







```
ds.fillna(method='bfill')
```







<img width="1026" height="872" alt="image" src="https://github.com/user-attachments/assets/3b7388ad-471d-4b62-80a4-358ef339d479" />






```
ds.fillna({'GENDER':'FEMALE','NAME':'THANU'})
```





<img width="1022" height="944" alt="image" src="https://github.com/user-attachments/assets/25212520-2ace-4343-8914-0a642fd1a4cd" />






```
ir=pd.read_csv("iris.csv")
ir
```







<img width="667" height="515" alt="image" src="https://github.com/user-attachments/assets/882d9b60-a8a9-412a-beff-40fd280b6e15" />







```
ir.describe()
```







<img width="598" height="378" alt="image" src="https://github.com/user-attachments/assets/88b17642-19d5-4921-8822-2a68c8ae0d70" />






```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```




<img width="681" height="578" alt="image" src="https://github.com/user-attachments/assets/f1fb361c-6235-4f9a-ae13-ea5694f5f1bb" />






```
Q1=ir.sepal_width.quantile(0.25)
Q3=ir.sepal_width.quantile(0.75)
IQR=Q3-Q1
print(IQR)
```





<img width="414" height="44" alt="image" src="https://github.com/user-attachments/assets/3bdedca2-a82b-4ff5-925b-09d0a02ad09b" />





```
rid=ir[((ir.sepal_width<(Q1-1.5*IQR))|(ir.sepal_width>(Q3+1.5*IQR)))]
rid['sepal_width']
```







<img width="212" height="273" alt="image" src="https://github.com/user-attachments/assets/60ffd2f9-a2b4-466e-8374-f61fe05b366d" />






```
delid=ir[~((ir.sepal_width<(Q1-1.5*IQR))|(ir.sepal_width>(Q3+1.5*IQR)))]
delid
```





<img width="764" height="546" alt="image" src="https://github.com/user-attachments/assets/6f1685a5-691e-46c7-b92f-c3209419e95b" />






```
sns.boxplot(x='sepal_width',data=delid)
```





<img width="675" height="659" alt="image" src="https://github.com/user-attachments/assets/a185bbc5-31bd-4951-8880-bb5b32f36a64" />






```
import numpy as np
import scipy.stats as stats
z=np.abs(stats.zscore(ir['sepal_length']))
z
```




<img width="720" height="627" alt="image" src="https://github.com/user-attachments/assets/0c3f56ad-db2d-4d25-844b-b18fdd40501e" />






```
ir1=ir[z<3]
ir1
```

<img width="698" height="521" alt="image" src="https://github.com/user-attachments/assets/7fc27726-6d84-45b5-a133-88228418d4b9" />































# Result
          Thus ,the program for data cleaning using python has executed successfully.
