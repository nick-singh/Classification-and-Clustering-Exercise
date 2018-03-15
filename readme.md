# Comp6940 Assignment 3

##### Date Due: Friday 30th March, 11:59pm


## Classification and Clustering 


### Q1 Cleaning Data (20 marks)

You will use the [UCI Credit Approval Dataset](https://archive.ics.uci.edu/ml/datasets/Credit+Approval) where each record is a credit card application. All attribute names and values have been changed to meaningless symbols to maintain confidentiality. The dataset has been cleaned to remove missing attributes. The data is stored in a comma-separated file (csv) [here](https://github.com/nick-singh/Classification-and-Clustering-Exercise/tree/master/data). Each line describes an instance using 16 columns: the first 15 columns represent the attributes of the application, and the last column is the ground truth label for credit card approval. Note: The last column should not be treated as an attribute.

**Required**
1. Clean the dataset and do any type conversions necessary
2. Ensure there are no null values, (imputing any if encountered)
3. Encode all categorical attributes see examples [here](http://pbpython.com/categorical-encoding.html)
4. Scale the attributes of the dataset
5. Perform PCA to obtain attributes with which explains `95%` of the variance in the data.


### Q2 Random Forest Classifier (50 marks)

**Objective**:

You will perform binary classification on the dataset to determine if a credit card application is safe to
approve or not.

#### Essential Reading:

**Decision Trees**

To complete this question, you need to develop a good understanding of how decision trees work. You can refer to the [slides](http://poloclub.gatech.edu/cse6242/2017fall/slides/CSE6242-710-Classification.pdf). Specifically, you need to know how to select the splitting attribute and split point for the selected attribute. These [slides from CMU](http://www.cs.cmu.edu/afs/cs.cmu.edu/academic/class/15381-s06/www/DTs.pdf) provide an excellent example of how to construct a decision tree using Entropy and Information Gain.

**Random Forest**

In random forests, it is not necessary to perform explicit cross-validation or use a separate test set for performance evaluation (also discussed in [here](http://poloclub.gatech.edu/cse6242/2017fall/slides/CSE6242-730-Ensemble.pdf)). Out-of-bag (OOB) error estimate has shown to be reasonably accurate and unbiased. 

Each tree in the forest is constructed using a different bootstrap sample from the original data. Each bootstrap sample is constructed by randomly sampling from the original dataset with replacement (usually, a bootstrap sample has the same size as the original dataset). Statistically, about one-third of the cases are left out of the bootstrap sample and not used in the construction of the kth tree. For each record left out in the construction of the kth tree, it can be assigned a class by the kth tree. As a result,
each record will have a “test set” classification by the subset of trees that treat the record as an out-of-bag sample. The majority vote for that record will be its predicted class. The proportion of times that a predicted class is not equal to the true class of a record averaged over all records is the OOB error estimate.

**Required**

**Part 1:**  Using the RandomForest Classifier provided by the sklearn library 

1. Initialize the classifier with default arbitrary paramenters
2. Train the classifier 
3. Determine the recall score of the classifier 

**Part 2:** Using the RandomizedSearchCV module provided by the sklearn library 

1. Do parameter tuning to obtain the optimal parameters to initialize the RandomForest Classifier. The parameters to tune are as follow:
	1. n_estimators
	2. max_features
	3. max_depth
	4. min_samples_split
	5. min_sample_leaf
	6. bootstrap
	
2. Determine the recall score of the classifier 


### Q3 KNN Classifier (30 marks)

**Objective**:

You will perform binary classification on the dataset to determine if a credit card application is safe to
approve or not.

**Required**

**Part 1:**  Using the KNN Classifier provided by the sklearn library 

1. Initialize the classifier with default value for n_neighbors 
2. Train the classifier 
3. Determine the recall score of the classifier 

**Part 2:** Using the cross_val_score module provided by the sklearn library

1. Perform 10 fold cross validation to obtain the optimal value to use for n_neighbor
2. Retrain the classifier 
2. Determine the recall score of the classifier 


#### Submission Details:
Students should submit either the following:
* An exported Jupyter notebook of the assignment with notes
or
* A python script file with the assignments and appropriate comments 

###### Email submissions to: nchamansingh@gmail.com with the following subject format: < StudentID > COMP6940 Assignment 3


#### Late Submissions:
A daily penalty for late submissions of 15% per day or partial day
