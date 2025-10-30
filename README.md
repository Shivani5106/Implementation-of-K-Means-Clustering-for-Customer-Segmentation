# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1.Import the necessary packages using import statement.
2.Read the given csv file using read_csv() method and print the number of contents to be displayed using df.head().
3.Import KMeans and use for loop to cluster the data.
4.Predict the cluster and plot data graphs.
5.Print the outputs and end the program.
 

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: SHIVANI M
RegisterNumber: 212224040313  
*/
```
```
import pandas as pd
import matplotlib.pyplot as plt
data=pd.read_csv(r'Mall_Customers.csv')

data.head()
data.info()
data.isnull().sum()

from sklearn.cluster import KMeans
wcss = []
for i in range(1,11):
    kmeans = KMeans(n_clusters = i,init = "k-means++")
    kmeans.fit(data.iloc[:,3:])
    wcss.append(kmeans.inertia_)
plt.plot(range(1,11),wcss)
plt.xlabel("No. of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")

km = KMeans(n_clusters = 5)
km.fit(data.iloc[:,3:])

y_pred = km.predict(data.iloc[:,3:])
y_pred

data["cluster"] = y_pred
df0 = data[data["cluster"]==0]
df1 = data[data["cluster"]==1]
df2 = data[data["cluster"]==2]
df3 = data[data["cluster"]==3]
df4 = data[data["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="magenta",label="cluster4")
plt.legend()
plt.title("Customer Segments")

```

## Output:

### ELBOW METHOD

<img width="1016" height="739" alt="image" src="https://github.com/user-attachments/assets/de2b09a1-eeca-4e9d-8c95-6b49b6854c25" />

### K-MEANS CLUSTERING

<img width="262" height="102" alt="image" src="https://github.com/user-attachments/assets/0235071b-e7c7-4aa1-897a-51507cf1a311" />

### Y PREDICTION 
<img width="899" height="278" alt="image" src="https://github.com/user-attachments/assets/9973dfb6-4f00-4150-b2ad-1c366a2aae96" />

### CUSTOMER SEGMENT
<img width="880" height="728" alt="image" src="https://github.com/user-attachments/assets/69643430-1558-47e1-8b0c-65f35ccdbf93" />



## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
