# Exno:2
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

```py
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
dt=pd.read_csv("titanic.csv")
dt
```
![Screenshot 2024-03-25 081010](https://github.com/guru14789/EXNO2DS/assets/151705853/13cef5d1-79b9-487f-966c-823757706d8e)

```py
dt.info()
```
![Screenshot 2024-03-25 081307](https://github.com/guru14789/EXNO2DS/assets/151705853/c39aa977-79bd-425e-8fcb-76ef521c9f72)

```py
dt.shape
```
![Screenshot 2024-03-25 081621](https://github.com/guru14789/EXNO2DS/assets/151705853/9170c8f9-49db-4c2e-8d0d-784fa621be81)

```py
dt.set_index('PassengerId',inplace=True)
dt.describe()
```
![Screenshot 2024-03-25 081708](https://github.com/guru14789/EXNO2DS/assets/151705853/95bc835f-2e57-4a60-b000-1dee4c8765bf)

### CATEGORICAL DATA ANALYSIS
```py
dt.nunique()
```
![Screenshot 2024-03-25 081831](https://github.com/guru14789/EXNO2DS/assets/151705853/df913cb1-cb51-4bf4-a3b0-3e7d67e654e1)

```py
dt["Survived"].value_counts()
```
![Screenshot 2024-03-25 081911](https://github.com/guru14789/EXNO2DS/assets/151705853/27509706-96c0-441a-8980-d2ee59ba11f1)

```py
per=(dt["Survived"].value_counts()/dt.shape[0]*100).round(2)
per
```

![Screenshot 2024-03-25 082008](https://github.com/guru14789/EXNO2DS/assets/151705853/1427a56f-3cf5-4ed4-b92a-7725853d166b)

### UNIVARIATE ANALYSIS

```py
sns.countplot(data=dt,x="Survived")
```
![Screenshot 2024-03-25 082150](https://github.com/guru14789/EXNO2DS/assets/151705853/450c44e0-68b1-4610-86c5-47d24761b208)

```py
dt.Pclass.unique()
```
![Screenshot 2024-03-25 082221](https://github.com/guru14789/EXNO2DS/assets/151705853/9935c39c-b940-455f-b580-1421398b42de)

```py
dt.rename(columns={'Sex':'Gender'},inplace=True)
dt
```
![Screenshot 2024-03-25 082326](https://github.com/guru14789/EXNO2DS/assets/151705853/b5e11950-b6e5-4f8f-83b5-82fe5e4940b5)


### BIVARIATE ANALYSIS

```py
sns.catplot(x="Gender",col="Survived",kind="count",data=dt,height=5,aspect=.7)
```
![Screenshot 2024-03-25 082820](https://github.com/guru14789/EXNO2DS/assets/151705853/84053a73-40d8-474c-9522-14565751ee18)

```py
sns.catplot(x='Survived',hue="Gender",data=dt,kind="count")
```
![Screenshot 2024-03-25 082917](https://github.com/guru14789/EXNO2DS/assets/151705853/81efb417-b044-4324-b9a6-5e1f81c7af6d)

```py
dt.boxplot(column="Age",by="Survived")
```
![Screenshot 2024-03-25 082943](https://github.com/guru14789/EXNO2DS/assets/151705853/e73a4624-6cdf-419d-ab47-d3443f019311)

```py
sns.scatterplot(x=dt["Age"],y=dt["Fare"])
```
![Screenshot 2024-03-25 083012](https://github.com/guru14789/EXNO2DS/assets/151705853/3d9b7a05-202b-46dc-a1ca-9d00237692b2)

```py
sns.jointplot(x=dt["Age"],y=dt["Fare"],data=dt)
```
![Screenshot 2024-03-25 083044](https://github.com/guru14789/EXNO2DS/assets/151705853/6e7b2c64-0dfa-46ee-ac84-bc4eece553e1)

### MULTIVARIATE ANALYSIS

```py
fig,ax1=plt.subplots(figsize=(8,5))
pt=sns.boxplot(ax=ax1,x='Pclass',y='Age',hue='Gender',data=dt)
```
![Screenshot 2024-03-25 083112](https://github.com/guru14789/EXNO2DS/assets/151705853/fa730f14-ca39-4c65-8448-6bf2327f2c08)

```py
sns.catplot(data=dt,col="Survived",x="Gender",hue="Pclass",kind="count")
```
![Screenshot 2024-03-25 083144](https://github.com/guru14789/EXNO2DS/assets/151705853/2dab79f7-beac-44e9-ba23-14d33e6069f8)

```py
corr=dt.corr()
sns.heatmap(corr,annot=True)
```
![Screenshot 2024-03-25 083338](https://github.com/guru14789/EXNO2DS/assets/151705853/d4b2e45d-c3ae-4216-b6da-bff2510eb0c1)

```py
sns.pairplot(dt)
```
![Screenshot 2024-03-25 083525](https://github.com/guru14789/EXNO2DS/assets/151705853/77546f59-1fd7-4446-ab3f-a25c916d2e66)

# RESULT

Thus, Data Analysis on the given dataset was executed successfully.
