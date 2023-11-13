# Ex02-Outlier
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them

### CODE
```
Developed by : Niraunjana Gayathri G R
Reg No.      : 212222230096
```
```
bhp.csv:
```
```
import pandas as pd
import seaborn as sns
import numpy as np
from scipy import stats
from google.colab import files
uploaded=files.upload()
df=pd.read_csv('bhp.csv')
df.info()
print(df.describe())
df.head()
#BEFORE REMOVING OUTLIER
sns.boxplot(y='price_per_sqft',data=df)

# PERFORMING IQR METHOD
q1=df['price_per_sqft'].quantile(0.25)
q3=df['price_per_sqft'].quantile(0.75)
IQR=q3-q1
low=q1-1.5*IQR
high=q3+1.5*IQR
new=df[((df['price_per_sqft']>=low)&(df['price_per_sqft']<=high))]

#AFTER REMOVING OUTLIER using IQR method
sns.boxplot(y='price_per_sqft',data=new)

# PERFORMING Zscore METHOD
z=np.abs(stats.zscore(df['price_per_sqft']))
new2=df[(z<3)]

#AFTER REMOVING OUTLIER using Zscore method
sns.boxplot(y="price_per_sqft",data=new2)
```
```
height_weight.csv:
```
```
import pandas as pd
import seaborn as sns
import numpy as np

df=pd.read_csv("/content/heights.csv")
df
#BEFORE REMOVING OUTLIER in HEIGHT
sns.boxplot(data=df)

sns.scatterplot(data=df)

max=df['height'].quantile(0.75)
min=df['height'].quantile(0.25)

max

min

iqr

df=df[((df['height']>=min)&(df['height']<=max))]
df

iqr=max-min
low=min-1.5*iqr
high=max+1.5*iqr

low

high
#AFTER REMOVING OUTLIER in HEIGHT
sns.boxplot(data=df)

sns.scatterplot(data=df)
```
### OUTPUT
```
bhp.csv:
```
![image](https://github.com/niraunjana/ODD2023---Datascience---Ex-02/assets/119395610/72c9a159-de91-428f-ad80-3a2521e1956f)
![image](https://github.com/niraunjana/ODD2023---Datascience---Ex-02/assets/119395610/e62ab5d3-c439-4aad-ac00-c28f384aea5a)
![image](https://github.com/niraunjana/ODD2023---Datascience---Ex-02/assets/119395610/268dc92d-96ed-41ed-8afa-9656208bfa0f)
![image](https://github.com/niraunjana/ODD2023---Datascience---Ex-02/assets/119395610/c419f53b-2ac1-4ca6-bb52-e9e02266a66d)
![image](https://github.com/niraunjana/ODD2023---Datascience---Ex-02/assets/119395610/4b8442ae-af1c-4bb1-970b-40939d1cbfc1)

```
height_weight.csv:
```
![image](https://github.com/niraunjana/ODD2023---Datascience---Ex-02/assets/119395610/e86a821e-4fe0-4e9a-aca9-fe287c3b0d5d)
![image](https://github.com/niraunjana/ODD2023---Datascience---Ex-02/assets/119395610/9485e876-aa37-4ef7-87db-c42967420cc1)
![image](https://github.com/niraunjana/ODD2023---Datascience---Ex-02/assets/119395610/47add19f-d02e-405b-b414-39233f17e91d)
![image](https://github.com/niraunjana/ODD2023---Datascience---Ex-02/assets/119395610/08954965-325e-4abd-bd6e-7fb6ccf409e7)
![image](https://github.com/niraunjana/ODD2023---Datascience---Ex-02/assets/119395610/d3a23e9f-5e96-4671-abce-497f3fd554eb)
![image](https://github.com/niraunjana/ODD2023---Datascience---Ex-02/assets/119395610/45353c68-a00a-4c3e-9908-d0611a25ab66)
![image](https://github.com/niraunjana/ODD2023---Datascience---Ex-02/assets/119395610/92ecf6a2-f3d1-4788-b1f2-22d75e153e15)

### RESULT
Hence the given set of data is read and the outliers are removed using the IQR method and Zscore method.


