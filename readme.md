# Comp6490 Assignment 3

## Classification and Clustering 


### Q1 Random Forest Classifier 

You will use the [UCI Credit Approval Dataset](https://archive.ics.uci.edu/ml/datasets/Credit+Approval) where each record is a credit card application. All attribute names and values have been changed to meaningless symbols to maintain confidentiality. The dataset has been cleaned to remove missing attributes. The data is stored in a comma-separated file (csv) here. Each line describes an instance using 16 columns: the first 15 columns represent the attributes of the application, and the last column is the ground truth label for credit card approval. Note: The last column should not be treated as an attribute.

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

#### Resources:
1. [Hyperparameter Tuning the Random Forest in Python](https://towardsdatascience.com/hyperparameter-tuning-the-random-forest-in-python-using-scikit-learn-28d2aa77dd74)
2. [Tuning the parameters of your Random Forest model](https://www.analyticsvidhya.com/blog/2015/06/tuning-random-forest-model/)

#### What will you implement

Below, we have summarized what you will implement to solve this question. 

1. Determine the optimal max features
2. Number of estimators
3. min_sample_leaf
4. min_sample_split
5. Max_depth
6. Should bootstrapping be used or not 
