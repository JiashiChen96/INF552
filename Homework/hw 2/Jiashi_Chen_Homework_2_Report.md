## Part 1: Implementation

The code is in ***Jiashi_Chen_Homework_2_Code.ipynb*** file.

I use **two-dimensional arrays** to save the coordinates of the centroids in K-means. I use **arrays from the numpy package and matrices from the pandas package** to save the parameters of the Gaussian distribution in GMM algorithm.

Code-level optimizations I perform is that I try to **use matrixes to calculate data instead of loops**, increasing calculation efficiency. I also use functions to modularize the calculation process, which is helpful for debugging and management.

Challenges I face is that at the beginning I was a bit confused about the operation of matrices and arrays which leads to many wrong result. 

Since each 3 centroids in K-means and weights in GMM are random at beginning, the output is not always the exactly same, however they are always close to other runs. 
One of the **output** in **K-mean**s:
![Kmeas output](/Users/jiashichen/Study/INF 552/Homework/hw 2/images/Kmeans output.png)

**Visualized** the assignments:

<img src="/Users/jiashichen/Study/INF 552/Homework/hw 2/images/Kmeans graph.png" alt="Kmeans graph" style="zoom:50%;" />

One of the **output** in **GMM**:

![GMM output](/Users/jiashichen/Study/INF 552/Homework/hw 2/images/GMM output2.png)

**Visualized** the assignments:

<img src="/Users/jiashichen/Study/INF 552/Homework/hw 2/images/GMM graph2.png" alt="GMM graph" style="zoom:50%;" />

The output of the two algorithms are similar. However, due to the difference between randomness and the algorithms themselves, the output has a certain difference.

## Part 2: Software Familiarization

**Sklearn package** offers a good implementation of the decision tree learning algorithm.

```python
from sklearn.cluster import KMeans  ## obtain necessary package
from sklearn import mixture

estimator = KMeans(n_clusters=3)   ## K-means algorithm
estimator.fit(data)

modele = mixture.GaussianMixture(n_components=3, covariance_type='full')   ##GMM
modele.fit(data)
```

I used this package to fit the data in  ***Jiashi_Chen_Homework_2_Code.ipynb*** file too.

### Comparsion and Improvement

I found that when computing the probability of each sample from a Gaussian function, we need to input the samples into the corresponding Gaussian probability density function. The calculation of the Gaussian probability density function requires the values of the inverse matrix and the determinant. The sklearn package **uses cholesky** to improves the efficiency a lot. 

GaussianMixture has different options to constrain different types of estimated covariance: **spherical, diagonal, tied, full covariance.** So the model can be adjusted to fit more data.

Also the package considers many **exceptions** to make the code more applicable.

## Part 3: Applications

### K-means

K-means can help managers improve their customer base (working in their target area) and further segment customer categories based on customer purchase history, interest, or activity monitoring. Categorizing customers helps companies tailor specific advertisements to specific customer groups.

### GMM

GMM algorithm can achieve foreground segmentation. The GMM uses K (basically 3 to 5) Gaussian models to characterize the characteristics of each pixel in the image. After a new frame of image is obtained, the Gaussian Mixture Model is updated. Each pixel in the current image is used with the model. If model matching successfully, the point is determined as the background point, otherwise it is the foreground.