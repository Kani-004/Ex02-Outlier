# Ex02-Outlier

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR 

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

    (i) Using IQR detect weight outliers and print them

    (ii) Using IQR, detect height outliers and print them
Aim:
TO detect and remove the outliers in the given data set and save the final data.
Algorithm:
Step 1:
Import the required packages(pandas,numpy,scipy)
Step 2:
Read the given csv file
Step 3:
Convert the file into a dataframe and get information of the data
Step 4:
Remove the non numerical data columns using drop() method.
Step 5:
Detect the outliers in the data set using z scores method.
Step 6:
Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)
Step 7:
Check if the outliersare removed from data set using graphical methods.
step 8:
Save the final data set into the file
Program:
1) & (2) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe.
Program executed by:kanimozhi s
Register number:2122212200024
 import pandas as pd
import numpy as np
import seaborn as sns

df = pd.read_csv("/content/bhp.csv")
df

df.head()

df.describe()

df.info()

df.isnull().sum()

df.shape

sns.boxplot(x="price_per_sqft",data=df)

q1 = df['price_per_sqft'].quantile(0.25)
q3 = df['price_per_sqft'].quantile(0.75)
print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1
ul = q3+1.5*IQR
ll = q1-1.5*IQR

df1 =df[((df['price_per_sqft']>=ll)&(df['price_per_sqft']<=ul))]
df1

df1.shape

sns.boxplot(x="price_per_sqft",data=df1)
(3)Examine price_per_sqft column and use zscore of 3 to remove outliers.
from scipy import stats
z = np.abs(stats.zscore(df['price_per_sqft']))
df2 = df[(z<3)]
df2

print(df2.shape)
sns.boxplot(x="price_per_sqft",data=df2)
(4)(i) For the data set height_weight.csv detect weight outliers using IQR method.
df3 = pd.read_csv("height_weight.csv/")
df3

df3.head()

df3.info()

df3.describe()

df3.isnull().sum()

df3.shape

sns.boxplot(x="weight",data=df3)

q1 = df3['weight'].quantile(0.25)
q3 = df3['weight'].quantile(0.75)
print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1
ul = q3+1.5*IQR
ll = q1-1.5*IQR

df4 =df3[((df3['weight']>=ll)&(df3['weight']<=ul))]
df4

df4.shape

sns.boxplot(x="weight",data=df4)
(4)(ii) For the data set height_weight.csv detect height outliers using IQR method.
sns.boxplot(x="height",data=df3)
q1 = df3['height'].quantile(0.25)
q3 = df3['height'].quantile(0.75)
print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1
ul = q3+1.5*IQR
ll = q1-1.5*IQR

df5 =df3[((df3['height']>=ll)&(df3['height']<=ul))]
df5

df5.shape

sns.boxplot(x="height",data=df5)
Output:
(1)(2) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe.
Dataset:
image
Dataset Head:
image
Dataset Info:
image
Dataset Describe:
image
Null Values:
image
Dataset Shape:
image
Box plot of price_per_sqft column with outliers:
image
price_per_sqft - Dataset after removing outliers:
image
price_per_sqft - Shape of Dataset after removing outliers :
image
Box Plot of price_per_sqft column without outliers:
image
(3) Examine price_per_sqft column and use zscore of 3 to remove outliers.
Dataset after removal of outlier using z score:
image
Shape of Dataset after removal of outlier using z score:
image
(4) For the data set height_weight.csv detect weight and height outliers using IQR method:
 sns.boxplot(x="height",data=df3)
q1 = df3['height'].quantile(0.25)
q3 = df3['height'].quantile(0.75)
print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1
ul = q3+1.5*IQR
ll = q1-1.5*IQR

df5 =df3[((df3['height']>=ll)&(df3['height']<=ul))]
df5

df5.shape

sns.boxplot(x="height",data=df5)
Output:
(1)(2) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe.
Dataset:
![image](https://user-images.githubusercontent.com/129577149/229769163-394d5d48-d6cb-45db-a3a0-d2dde205797c.png)
Dataset Head:
![image](https://user-images.githubusercontent.com/129577149/229769261-1f425cad-76f3-43df-b94d-5a44235e2e69.png)
Dataset Info:
![image](https://user-images.githubusercontent.com/129577149/229769361-76f238fa-10da-49bd-8f5c-96d0908273d2.png)
Dataset Describe:
![image](https://user-images.githubusercontent.com/129577149/229769463-590e5521-5f28-42bc-aabc-b5ec91febf23.png)
Null Values:
![image](https://user-images.githubusercontent.com/129577149/229769633-8fa442a6-2769-438d-92e8-74abb5af0521.png)
Dataset Shape:
![image](https://user-images.githubusercontent.com/129577149/229769720-93702d19-fad9-406b-9a50-f49a88474df3.png)
Box plot of price_per_sqft column with outliers:
![image](https://user-images.githubusercontent.com/129577149/229769829-76a9b53b-361d-469e-9b24-1e1b5812f355.png)
price_per_sqft - Dataset after removing outliers:
![image](https://user-images.githubusercontent.com/129577149/229769944-c8f3aa27-a95e-487d-b8f8-1f48218f6d94.png)
price_per_sqft - Shape of Dataset after removing outliers :
![image](https://user-images.githubusercontent.com/129577149/229770024-848e359e-7743-4937-9ba0-dfdc291a1593.png)
Box Plot of price_per_sqft column without outliers:
![image](https://user-images.githubusercontent.com/129577149/229770107-4a0105dc-d04c-417f-bffc-c1d6b95d9f44.png)
(3) Examine price_per_sqft column and use zscore of 3 to remove outliers.
Dataset after removal of outlier using z score:
![image](https://user-images.githubusercontent.com/129577149/229770253-874a8dcf-921a-4b95-a7e5-27f345e7cfae.png)
Shape of Dataset after removal of outlier using z score:
![image](https://user-images.githubusercontent.com/129577149/229770339-05d07c04-9717-4180-8dbc-62c8ae4b9637.png)
(4) For the data set height_weight.csv detect weight and height outliers using IQR method:
Dataset:
![image](https://user-images.githubusercontent.com/129577149/229770491-7dcfecd2-8587-4aaf-b091-10233ba86c92.png)
Dataset Head:
![image](https://user-images.githubusercontent.com/129577149/229770663-d9b52036-c614-44dc-bb7a-9dfc95b52d23.png)
Dataset Info:
![image](https://user-images.githubusercontent.com/129577149/229770745-f7d609a0-1d7b-4f16-82b3-a0c341892f46.png)
Datset Describe:
![image](https://user-images.githubusercontent.com/129577149/229771119-0a440901-7bed-47ab-abdc-6544b6dabe7d.png)
Null Values:
![image](https://user-images.githubusercontent.com/129577149/229771196-b334bb3e-d321-4bf0-945f-cfd3f75db04b.png)
Dataset Shape:
![image](https://user-images.githubusercontent.com/129577149/229771264-8891e53e-ec48-4e5d-9f01-86e19313d76e.png)
Weight -With Outliners:
![image](https://user-images.githubusercontent.com/129577149/229771304-1fb56e21-e03e-441c-8dc5-442caea08caa.png)
Weight - Dataset after removing Outliers using IQR method:
![image](https://user-images.githubusercontent.com/129577149/229771371-eee14514-43d3-434a-bc79-d99c84929983.png)
Weight - Shape of Dataset after removing Outliers using IQR method:
![image](https://user-images.githubusercontent.com/129577149/229771449-91e1413a-5d5a-424b-a1d0-b0dd40c730b9.png)
Weight - Without Outliers using IQR method:
![image](https://user-images.githubusercontent.com/129577149/229771528-d1366360-6f34-47a2-8243-58df0fc5b536.png)
Height - With outliers:
![image](https://user-images.githubusercontent.com/129577149/229771603-3abbfd42-0af8-4f84-9860-3ce273700d31.png)
Height - Dataset after removing Outliers using IQR method:
![image](https://user-images.githubusercontent.com/129577149/229771681-70f381eb-6c98-4537-8e8b-750d1d6e6515.png)
Height - Shape of Dataset after removing Outliers using IQR method:
![image](https://user-images.githubusercontent.com/129577149/229771747-e52ac768-3e86-4b5e-b127-77145d940efa.png)
Height - Without Outliers using IQR method:
![image](https://user-images.githubusercontent.com/129577149/229771821-d7d198a7-364a-4150-92ac-389d4899571c.png)
Result:
Thus the outliers are detected and removed in the given file and the final data set is saved into the file.




















