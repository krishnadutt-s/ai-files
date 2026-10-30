##  k- means clustering

k-means clustering is a method of vector quantization, originally from signal processing, that aims to partition n observations into k clusters in which each observation belongs to the cluster with the nearest mean (cluster centers or cluster centroid). This results in a partitioning of the data space into Voronoi cells. k-means clustering minimizes within-cluster variances (squared Euclidean distances), but not regular Euclidean distances, which would be the more difficult Weber problem: the mean optimizes squared errors, whereas only the geometric median minimizes Euclidean distances. For instance, better Euclidean solutions can be found using k-medians and k-medoids.
## `k-means` clustering on the Iris dataset using Python's scikit-learn library:
## Step 1: Loading libraries
```{python}
import numpy as np
import pandas as pd
from sklearn.cluster import KMeans
from sklearn.datasets import load_iris
import matplotlib.pyplot as plt
```
Loading the dataset
```{python}
# Load the Iris dataset
iris = load_iris()
X = iris.data # create only input data not target
```
```{python}
# Create a DataFrame from the Iris dataset (for visualization purpose only)
df = pd.DataFrame(X, columns=iris.feature_names)
```
df.head()
```{python}
# Visualize the clusters
plt.scatter(X[:, 0], X[:, 1])
#plt.scatter(centroids[:, 0], centroids[:, 1], marker='X', s=200, c='red')
plt.xlabel(iris.feature_names[0])
plt.ylabel(iris.feature_names[1])
plt.title('Distribution of Iris data')
plt.show()
```
# Finding the best value of k using elbow method+
# Initialize an empty list to store the within-cluster sum of squares
wcss = []

# Try different values of k
```{python}
for k in range(1, 11):
    kmeans = KMeans(n_clusters=k,n_init='auto', random_state=42)
    kmeans.fit(X)
    wcss.append(kmeans.inertia_)# here inertia calculate sum of square distance in each cluster
```
# Plot the within-cluster sum of squares for different values of k
```{python}
plt.plot(range(1, 11), wcss, marker='o')
plt.xlabel('Number of Clusters (k)')
plt.ylabel('Within-Cluster Sum of Squares (WCSS)')
plt.title('Elbow Method')
plt.show()
```
```{python}
## Using Gridsearch method
# Define the parameter grid
from sklearn.model_selection import GridSearchCV

param_grid = {'n_clusters': [2, 3, 4, 5, 6]}

# Create a KMeans object
kmeans = KMeans(n_init='auto',random_state=42)

# Create a GridSearchCV object
grid_search = GridSearchCV(kmeans, param_grid, cv=5)

# Perform grid search
grid_search.fit(X)

# Get the best parameters and the best score
best_params = grid_search.best_params_
best_score = grid_search.best_score_
```
```{python}
print("Best Parameters:", best_params)
print("Best Score:", best_score)
```


