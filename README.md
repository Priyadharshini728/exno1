
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
df= pd.read_csv("/content/SAMPLEIDS.csv")
df
```
<img width="1138" height="872" alt="image" src="https://github.com/user-attachments/assets/1acc3172-0d20-4658-89a3-ba9b046b3197" />


```
df.head()
```
<img width="1140" height="248" alt="image" src="https://github.com/user-attachments/assets/9b57992a-6435-46d7-9ee5-090a9d3a42e1" />





```
df.tail()
```


<img width="1242" height="351" alt="image" src="https://github.com/user-attachments/assets/330f76c3-2e4c-4e65-8c94-94cedc3cbd3a" />







```
df.isnull()
```



<img width="944" height="867" alt="image" src="https://github.com/user-attachments/assets/05f48695-08f0-4fea-b96a-a76ad3d28396" />




```
df.notnull()
```





<img width="951" height="865" alt="image" src="https://github.com/user-attachments/assets/147e0152-5967-4a34-bf4f-6f74023d8243" />




```
df.isnull().sum()
```

<img width="290" height="571" alt="image" src="https://github.com/user-attachments/assets/e9784fc6-a735-4031-81ce-7a73bae3d787" />




```
df.dropna(axis=0)
```





<img width="1186" height="580" alt="image" src="https://github.com/user-attachments/assets/db2ef402-bdb3-477b-bf29-83adf93a63d7" />





```
df.fillna(5)
```





<img width="1131" height="857" alt="image" src="https://github.com/user-attachments/assets/aecaef2d-25a9-4871-b15a-2371798bb01f" />






```
df.dropna(axis=1)
```




<img width="402" height="868" alt="image" src="https://github.com/user-attachments/assets/d7baf9c8-a203-443d-ba66-40bb43c633af" />






```
df.isnull().any()
```





<img width="302" height="596" alt="image" src="https://github.com/user-attachments/assets/feb0db24-bd08-47c7-8afa-0ccfd4c24c2b" />





```
df.fillna(method='ffill')
```





<img width="1089" height="877" alt="image" src="https://github.com/user-attachments/assets/6c9eb14e-fb88-4a71-b96a-4c238ee08601" />








```
df.fillna(method='bfill')
```







<img width="1034" height="855" alt="image" src="https://github.com/user-attachments/assets/880e2a1e-e34c-4533-b250-84715bc9c27d" />






```
df.fillna({'GENDER':'MALE','NAME':'PRIYA','ADDRESS':'CHENNAI','M1':'SCORE1','M2':'SCORE2'})
```





<img width="1148" height="860" alt="image" src="https://github.com/user-attachments/assets/ca62a965-0ce4-4333-9ba3-42772ccd14b1" />






```
ir=pd.read_csv('/content/iris.csv')
ir
```







<img width="719" height="499" alt="image" src="https://github.com/user-attachments/assets/07db7703-d157-4634-9175-0e52f4ab7c7e" />







```
ir.describe()
```







<img width="633" height="362" alt="image" src="https://github.com/user-attachments/assets/06874e4d-653a-43a3-a18d-178f35f9b1fe" />






```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```




<img width="797" height="590" alt="image" src="https://github.com/user-attachments/assets/3b4ee398-63ae-4a12-b607-20f0223f415d" />






```
Q1=ir.sepal_width.quantile(0.25)
Q3=ir.sepal_width.quantile(0.75)
IQR=Q3-Q1
print(IQR)
```


<img width="89" height="39" alt="image" src="https://github.com/user-attachments/assets/666fda3c-dbf5-4e8b-a7e4-7684ee6ec355" />








```
rid=ir[((ir.sepal_width<(Q1-1.5*IQR))|(ir.sepal_width>(Q3+1.5*IQR)))]
rid['sepal_width']
```







<img width="250" height="249" alt="image" src="https://github.com/user-attachments/assets/da0b73ee-3d75-4310-b062-4bc15027739a" />






```
delid=ir[~((ir.sepal_width<(Q1-1.5*IQR))|(ir.sepal_width>(Q3+1.5*IQR)))]
delid
```





<img width="704" height="505" alt="image" src="https://github.com/user-attachments/assets/24b42939-ff92-4b53-be40-66e5007a2ce3" />







```
sns.boxplot(x='sepal_width',data=delid)
```





<img width="720" height="591" alt="image" src="https://github.com/user-attachments/assets/8e2f2cb4-e247-48a3-9044-6a2f47c4f3f5" />







```
import numpy as np
import scipy.stats as stats
z=np.abs(stats.zscore(ir['sepal_length']))
z
```




<img width="789" height="684" alt="image" src="https://github.com/user-attachments/assets/281bf32b-a259-4fda-a763-f56027d602ba" />





```
ir1=ir[z<3]
ir1
```

<img width="687" height="526" alt="image" src="https://github.com/user-attachments/assets/0c39b920-cd91-4cd0-881f-12dbe2debdb2" />































# Result
          Thus ,the program for data cleaning using python has executed successfully.
