# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm:
1. **Data Preprocessing**  
   Load the dataset using pandas and inspect for missing values or incorrect data types.

2. **Optimal Cluster Selection (Elbow Method)**  
   Calculate the Within-Cluster Sum of Squares (WCSS) for cluster counts ranging from 1 to 10 and plot the elbow graph to determine the optimal number of clusters.

3. **Model Training**  
   Apply the K-Means algorithm with the selected number of clusters on features such as *Annual Income* and *Spending Score* to segment customers.

4. **Visualization and Interpretation**  
   Visualize the clustered data using Matplotlib, assigning distinct colors to each cluster to interpret customer segments effectively.


## Program:
```python
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: DINESH KUMAR RAJENDRAN
RegisterNumber:  212224250005
*/

import pandas as pd
import matplotlib.pyplot as plt
df=pd.read_csv("Mall_Customers.csv")
df.head()

df.info()

df.isnull().sum()

from sklearn.cluster import KMeans
wcss=[]
for i in range(1,11):
    kmeans=KMeans(n_clusters=i,init="k-means++")
    kmeans.fit(df.iloc[:,3:])
    wcss.append(kmeans.inertia_)

plt.plot(range(1,11),wcss)
plt.xlabel("No of Cluster")
plt.ylabel("wcss")
plt.title("Elbow Method")

km=KMeans(n_clusters = 5)
km.fit(df.iloc[:,3:])
KMeans(n_clusters=5)

y_pred=km.predict(df.iloc[:,3:])
y_pred

df["cluster"]=y_pred
df0=df[df["cluster"]==0]
df1=df[df["cluster"]==1]
df2=df[df["cluster"]==2]
df3=df[df["cluster"]==3]
df4=df[df["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="yellow",label="cluster4")
plt.legend()
plt.title("Customer Segments")
```

## Output:
<img width="1001" height="158" alt="image" src="https://github.com/user-attachments/assets/4653a1a3-62c7-48c5-91c7-a2564d5933ed" />


<img width="1000" height="211" alt="image" src="https://github.com/user-attachments/assets/c539c3d1-cb81-4980-a667-21a8935d7c79" />


<img width="999" height="112" alt="image" src="https://github.com/user-attachments/assets/5359c941-ebcc-4463-930f-7956484d42a0" />


<img width="994" height="491" alt="image" src="https://github.com/user-attachments/assets/03d15b98-f84b-44fe-9e0a-6d0f9ff05a28" />


<img width="1007" height="17" alt="image" src="https://github.com/user-attachments/assets/53fb7d00-a6e1-4eaf-b7c9-ff2c49217990" />


<img width="998" height="181" alt="image" src="https://github.com/user-attachments/assets/c270fee0-566b-4e2b-aba1-ca301732aade" />


<img width="997" height="467" alt="image" src="https://github.com/user-attachments/assets/0622cdfb-cc03-47a7-9d24-cc50d23c6404" />



## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
