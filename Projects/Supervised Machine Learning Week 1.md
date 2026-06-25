---
fileClass: Project
Category: LessonNotes
Status: Active
Course: SupervisedMachineLearning
Author: Mason Bendixen
Last Updated: 6/23/2026
Version: 0.1
tags:
---
# Overview of Machine Learning
- https://www.coursera.org/learn/machine-learning/lecture/iYR2y/welcome-to-machine-learning
- Machine learning is a subset of artificial intelligence
- AI & ML is expected to add 30 trillion dollars to the economy by 2030
- There is a community forum to discuss stuff
	- https://community.deeplearning.ai/top?period=monthly

# Supervised vs. Unsupervised Machine Learning
- Supervised learning has regression and classification
	- Regression is a continuous function like mapping square footage to expected sale price
	- Classification has things like tumor size and malignant or spam versus not spam
- Google news is an example of unsupervised learning
	- For instance, it might find a lot of articles about panda twins born in a Japanese zoo. It didn't know to relate these or that it was relevant but it sees a bunch of related articles with the same unusual keywords (panda twin tokyo zoo)
	- Genome mapping can use this
	- Grouping customers by finding common traits to classify them
	- Data without labels that are grouped into attempts at related clusters
- Anomaly detection is looking for unusual events
- Dimensionality reduction
	- Compress data into a smaller number of attributes

# Jupyter Notebooks
- SHIFT + ENTER in a code cell will run the code
- Double click on a markdown cell to convert it to markdown. Hit SHIFT + ENTER to convert it back to formatted text

# Linear regression
- For mapping real estate square footage to sale price:
	- You would call the square footage x or an input variable feature.
	- You would call the sale price y or the output or target variable
	- m would be the number of training examples
	- (x, y) is a single training example
	- (x<sup>(i)</sup>, y<sup>(i)</sup>) is the i<sup>th</sup> training example
	- You feed the training set of data through a learning algorithm to create a hypothesis / model / function that given an input outputs a predicted / estimated target ($\hat{y}$ vs the actual target y)
	- How do we represent f? For a linear model we could do f<sub>w,b</sub>=wx+b

# Cost function

