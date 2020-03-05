# INF552: Programming Assignment 3

## Part 1: Implementation

The code is in ***Jiashi_Chen_Homework_3_Code.ipynb*** file.

### PCA

The directions of the first two principal components:

```python
[[ 0.86667137,-0.23276482, 0.441249689],  # the first principal components
 [-0.4962773, -0.492479,  0.71496368]]    # the second principal components
```

### FastMap

The words on a 2D plane: 

<img src="/Users/jiashichen/Study/INF 552/Homework/hw 3/images/output of fastmap.png" alt="output of fastmap" style="zoom:50%;" />



The **data structure** I use is array and matrix from numpy module and dataframe from pandas module.  Dataframe could help me store the orginal data. Array can be used to store the eigenvalues in PCA and new coordinates in fastmap. The matrix could store the eigenvectors and data which can be converted from dataframe.

The code-level **optimizations** I perform is that I used the two mature modules numpy and pandas to complete matrix operations and obtain eigenvectors and eigenvalues, which improves the efficiency a lot. In fastmap, I defined each step into each function, which is beneficial to my debugging and improvement in the future.

The **challenges** I face is that I spend a lot of time in figuring out how to get the new distances without computing and storing all of the old distances except the initial distance in the code.

## Part 2: Software Familiarization

**Sklearn package** offers a good implementation of the PCA algorithm

### How to use

```python
from sklearn.decomposition import PCA ## Obtain necessary package

pca=PCA(n_components=2)   #Choose the number of components to keep
newData=pca.fit_transform(data)  ## Obtain new data
```

I used this package to fit the data in **Jiashi_Chen_Homework_3_Code.ipynb** file too.





## Part 3: Applications

### PCA in detecting human face<sup>[1]</sup>

This paper presents a new idea for detecting an unknown human face in input imagery and recognizing his/her facial expression. The objective of this research is to develop highly intelligent machines or robots that are mind implemented. A Facial Expression Recognition system needs to solve the following problems: detection and location of faces in a cluttered scene, facial feature extraction, and facial expression classification. The universally accepted five principal emotions to be realized are: Angry, Happy, Sad, Disgust and Surprise along with neutral. Principal Component Analysis (PCA) is implemented with Singular value decomposition (SVD) for Feature Extraction to determine principal emotions. The experiments show that the proposed facial expression recognition framework yields relatively little degradation in recognition rate due to facial images wearing glasses or loss of feature points during tracking.



### fastmap in wireless sensor networks<sup>[2]</sup>

Node localization in wireless sensor networks (WSNs) has attracted much attention due to the increase of usage and applications of WSNs. Many algorithms and techniques for locating sensor nodes have been proposed in the literature. A recent algorithm, which is based on a given set of pairwise distance estimates among nodes and the target, generates a map of node locations. This algorithm, known as FastMap, uses projections onto orthogonal hyperplanes to find the coordinates successively. In this paper, we analytically study the performance of the FastMap algorithm for 2D positioning. Moreover a modified version of FastMap with better performance is proposed and analyzed. The analysis shows that the optimum anchor placement should be at the edge of the network.

## Reference

[1] Kaur M, Vashisht R, Neeru N. Recognition of Facial Expressions with Principal Component Analysis and Singular Value Decomposition[J]. 2011, 9(12):24-28.

[2]Waleed A. Saif, Mounir Ghogho, Desmond C. McLernon. A modified fastmap algorithm for node localization in Wireless Sensor Networks[C]// Signal Processing Advances in Wireless Communications, 2008. SPAWC 2008. IEEE 9th Workshop on. IEEE, 2008.

