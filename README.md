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

Developed by: S.LOKESH SAI DILEEP

RegisterNumber: 212221230111  
*/
```
import matplotlib.pyplot as plt

data = pd.read_csv("Mall_Customers.csv")

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

plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="yellow",label="cluster1")

plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="pink",label="cluster2")

plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster3")

plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="purple",label="cluster4")

plt.legend()
plt.title("Customer Segments")

## Output:
![image](https://user-images.githubusercontent.com/94883079/204543814-97f25ed0-a81a-40f6-8a72-9dec26973e26.png)
![image](https://user-images.githubusercontent.com/94883079/204543961-6faf8b10-1e48-4a34-bf6a-9c94fcd7ee0d.png)
![image](https://user-images.githubusercontent.com/94883079/204544054-8514f3bb-8210-4bc1-bbe0-abfec4e0f58f.png)
![image](https://user-images.githubusercontent.com/94883079/204544131-b9715f80-6586-4445-a147-54a538ea26fa.png)
![image](https://user-images.githubusercontent.com/94883079/204544204-fdfb4640-71ee-4161-b162-3c2adf286818.png)

## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
