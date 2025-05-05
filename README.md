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

![img-1](https://github.com/user-attachments/assets/5294ca91-c1fd-45de-8784-696ef3657990)

```
dt.info()
```
![img-2](https://github.com/user-attachments/assets/394da69b-31a5-4e4a-aaff-b3aafa81a153)

```
dt.shape
```

![img-3](https://github.com/user-attachments/assets/619c5de7-5d10-4015-8293-8aed5a17df5d)

```
dt.set_index("PassengerId",inplace=True)
dt.describe()
```

![img-4](https://github.com/user-attachments/assets/19348d67-ed29-49d2-938a-0407037516a3)

```
dt.nunique()
```

![img-5](https://github.com/user-attachments/assets/7d676614-a7ce-496c-b4bc-9676df9ec488)

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

![img-8](https://github.com/user-attachments/assets/df63b1a0-434a-4777-aedd-5f17579f94aa)

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

![img-13](https://github.com/user-attachments/assets/2d35dcc7-ec12-4b43-8df1-6ee82a7d0ff8)

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
