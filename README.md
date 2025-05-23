# EXNO2DS
# AIM:
      To perform Exploratory Data Analysis on the given data set.
      
# EXPLANATION:
  The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
# ALGORITHM:
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

## CODING AND OUTPUT
```
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
dt = pd.read_csv("/content/titanic_dataset.csv")
dt
```

![image](https://github.com/user-attachments/assets/e4903e4a-354c-41d4-a42c-d85fec4ec9dc)


```
dt.info()
```
![image](https://github.com/user-attachments/assets/352fa5b1-99fd-4dfd-96b0-f81b678836ca)

```
dt.shape
```

![img-3](https://github.com/user-attachments/assets/619c5de7-5d10-4015-8293-8aed5a17df5d)

```
dt.set_index("PassengerId",inplace=True)
dt.describe()
```

![image](https://github.com/user-attachments/assets/9fbff76b-b2c3-424d-8c15-bf65fa49e202)

```
dt.nunique()
```

![image](https://github.com/user-attachments/assets/79a1d0d7-c51d-4a6b-a3e1-b5954bbe6dd2)


```
dt["Survived"].value_counts()
```

![img-6](https://github.com/user-attachments/assets/03bdbabd-0895-403e-bc17-205e8424a92b)

```
per=(dt["Survived"].value_counts()/dt.shape[0]*100).round(2)
per
```

![img-7](https://github.com/user-attachments/assets/ab5bf193-c718-4fcf-a389-3774c12c26de)

```
sns.countplot(data=dt,x="Survived")
```

![image](https://github.com/user-attachments/assets/82e6cfab-8a7b-469b-85cd-1b14a258a9ef)

```
dt
```

![img-9](https://github.com/user-attachments/assets/f93802c0-e75e-4e12-8dfd-e1a1a539e2e1)

```
dt.Pclass.unique()
```

![img-10](https://github.com/user-attachments/assets/046f98c9-01a3-4434-ba8c-a68a55369c40)

```
dt.rename(columns = {'Sex':'Gender'},inplace=True)
dt
```

![img-11](https://github.com/user-attachments/assets/ababd095-8893-44ce-a02c-7c3bd0a4e305)

```
sns.catplot(x="Gender",col="Survived",kind="count",data=dt,height=5,aspect=.7)
```

![img-12](https://github.com/user-attachments/assets/3dd3a71e-567c-4f02-833f-d9043776f228)

```
sns.catplot(x='Survived',hue='Gender',data=dt,kind='count')
```

![image](https://github.com/user-attachments/assets/a12537c6-32f8-44a3-82d0-7fa25153cb10)

```
dt.boxplot(column="Age",by="Survived")
```

![img-14](https://github.com/user-attachments/assets/84c170d4-1751-41f9-bd66-ab02287c3b40)

```
sns.scatterplot(x=dt["Age"],y=dt["Fare"])
```

![img-15](https://github.com/user-attachments/assets/143c3649-20de-4ed6-9c66-2a374c059126)

```
sns.jointplot(x="Age",y="Fare",data=dt)
```

![img-16](https://github.com/user-attachments/assets/945f497c-8180-49fa-81ea-7e0087325c72)

```
fig,ax1=plt.subplots(figsize=(8,5))
plt = sns.boxplot(ax=ax1,x='Pclass',y='Age',hue='Gender',data=dt)
```

![img-17](https://github.com/user-attachments/assets/d047cd4e-2318-43cb-b655-34fd01eed94f)

```
sns.catplot(data=dt,col='Survived',x='Gender',hue='Pclass',kind='count')
```

![img-18](https://github.com/user-attachments/assets/613f81d8-686c-468b-9c50-070745d8b5e5)

```
numerical_dt = dt.select_dtypes(include=np.number)
corr = numerical_dt.corr()
sns.heatmap(corr, annot=True)
```

![img-19](https://github.com/user-attachments/assets/7afa48fc-10fb-4715-bc55-0f46b4dc6466)

```
sns.pairplot(dt)
```

![img-20](https://github.com/user-attachments/assets/8dc87f7e-b40f-42fe-92bf-554779489df6)

# RESULT
    The Exploratory Data Analysis was successfully completed by examining data distribution, outliers, and anomalies.
