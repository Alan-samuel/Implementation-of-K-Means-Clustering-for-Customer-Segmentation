# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Select K Clusters: Decide the number of clusters (K) to divide the dataset into.
2. Initialize Centroids: Randomly choose K data points as the initial cluster centers.
3. Assign Data Points: Calculate the distance between each data point and the centroids; assign each point to the closest centroid.
4. Update Centroids: Compute the new centroid for each cluster by averaging the points assigned to it.
5. Repeat Until Convergence: Continue reassignment and centroid updating until centroids stop changing significantly.
6. Use the Elbow Method: Identify the optimal number of clusters by plotting Within-Cluster Sum of Squares (WCSS) for different values of K.
7. Train the Model: Apply K-Means clustering with the chosen K and fit it to the relevant features of the dataset.
8. Predict Clusters: Assign each customer to a cluster based on spending habits and annual income.
9. Visualize Clusters: Create a scatter plot to represent the segmentation, using different colors for different clusters.
10. Interpret Results: Analyze the clusters to extract meaningful insights about customer behavior and spending patterns.

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Alan Samuel Vedanayagam
RegisterNumber:  212223040012
*/
```
```
import pandas as pd 
import matplotlib.pyplot as plt 
data=pd.read_csv("Mall_Customers.csv") 
data.info
data.isnull().sum()
from sklearn.cluster import KMeans
wcss = []  #Within-Cluster sum of square. 
for i in range(1,11):
  kmeans=KMeans(n_clusters = i,init = "k-means++")
  kmeans.fit(data.iloc[:,3:])
  wcss.append(kmeans.inertia_)
plt.plot(range(1,11),wcss)
plt.xlabel("No of Clusters")
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
![image](https://github.com/user-attachments/assets/13462dce-ce65-4e9a-99ae-5977f98a7f54)
![image](https://github.com/user-attachments/assets/f6a0a576-86a4-4e33-aa00-657459aab651)
![image](https://github.com/user-attachments/assets/7a653c69-83bb-4a11-be5b-e2d702de2875)
![image](https://github.com/user-attachments/assets/ea80140e-5919-44b0-9d8d-98bb08900edd)
![image](https://github.com/user-attachments/assets/833dca74-b0d6-4fe5-905b-4e34e7d20abd)
![image](https://github.com/user-attachments/assets/601bb56e-d50f-445a-b202-459d4f09508d)
![image](https://github.com/user-attachments/assets/36b46631-bc6f-4b13-8f70-603b215b2964)



## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
