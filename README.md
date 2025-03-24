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
import matplotlib.pyplot as plt
import seaborn as sns
dt = pd.read_csv("titanic_dataset.csv")
print(dt.head())
```
![image](https://github.com/user-attachments/assets/f1811b2d-fecb-43e2-8a87-36b20e7a48a1)

```
dt.info()
```
![image](https://github.com/user-attachments/assets/ec448967-b989-4498-af12-746ad3b68508)

```
print(f"Number of rows: {dt.shape[0]}")
print(f"Number of columns: {dt.shape[1]}")
```
![image](https://github.com/user-attachments/assets/66ededbd-b5b3-4b92-9f8b-5d231b25c5ad)

```
dt.set_index('PassengerId', inplace=True)
print(dt.describe())
```
![image](https://github.com/user-attachments/assets/75df94b8-4770-42a4-b011-548c748a90f5)

```
print(dt['Sex'].value_counts())
print(dt['Embarked'].value_counts())
```
![image](https://github.com/user-attachments/assets/f7dd5af9-2df5-4c84-a48e-504e9d2fcd69)

```
plt.figure(figsize=(6, 4))
sns.countplot(x='Survived', data=dt, palette='coolwarm')
plt.title("Survival Count")
plt.show()
```
![image](https://github.com/user-attachments/assets/37da3e38-b904-4761-9a92-a29f5994c130)

```
print("Unique values in 'Pclass':", dt['Pclass'].unique())
```
![image](https://github.com/user-attachments/assets/81dbbb96-cb12-4d95-b7b6-49f0c4a13d40)

```
dt.rename(columns={'Sex': 'Gender'}, inplace=True)
print(dt.head())
```
![image](https://github.com/user-attachments/assets/21c3eb0c-5cd1-449c-96ac-795c9e182c81)

```
sns.catplot(x="Pclass", hue="Survived", data=dt, kind="count", palette="muted")
plt.title("Survival Count by Passenger Class")
plt.show()
```
![image](https://github.com/user-attachments/assets/6a905f68-f6fd-4fa5-b5c2-df1c1e025197)

```
fig, ax1 = plt.subplots(figsize=(8,5))
graph = sns.countplot(x="Gender", hue="Survived", data=dt, palette="pastel")
graph.set_xticklabels(graph.get_xticklabels())
for p in graph.patches:
    height = p.get_height()
    graph.text(p.get_x()+p.get_width()/2, height + 20.8,height ,ha="left")
```
![image](https://github.com/user-attachments/assets/63208699-c5d1-4353-8ecd-22fba47258e2)

```
plt.figure(figsize=(8, 5))
sns.boxplot(x='Survived', y='Age', data=dt, palette='coolwarm')
plt.title("Age Distribution by Survival")
plt.show()
```
![image](https://github.com/user-attachments/assets/c093bade-81e7-4853-b6f5-73eca432a1ac)

```
plt.figure(figsize=(10, 6))
sns.boxplot(x='Pclass', y='Age', hue='Gender', data=dt, palette='Set2')
plt.title("Age Distribution by Passenger Class and Gender")
plt.show()
```
![image](https://github.com/user-attachments/assets/e86ccbe1-fc1b-4db9-a72b-3d51cd386337)

```
sns.catplot(x='Pclass', hue='Survived', col='Gender', data=dt, kind='count', palette='coolwarm')
plt.show()
```
![image](https://github.com/user-attachments/assets/9780afff-8444-457b-bcf1-eb8ad8fc8198)

```
plt.figure(figsize=(10, 6))
sns.heatmap(dt.corr(), annot=True, cmap='coolwarm', linewidths=0.5)
plt.title("Feature Correlation Heatmap")
plt.show()
```
![image](https://github.com/user-attachments/assets/ac54e11a-d626-4f1e-a7f6-3622815885c8)

```
sns.pairplot(dt, hue='Survived', palette='coolwarm')
plt.show()
```
![image](https://github.com/user-attachments/assets/af9e0804-add7-4d79-a27e-3f65e7bfbe01)

# RESULT
Code are sucessfully executed.
