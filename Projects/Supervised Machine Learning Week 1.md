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
- The model is $f_{w,b}(x) = wx + b$
- w and b are parameters, coefficients, or weights
- $J_{(w,b)} = \frac{1}{2m}\sum_{i=1}^m(\hat{y}^{}(i))-y^{(i)})^2$
	- This is the squared error cost function
- Objective, minimize the cost function for w,b
- For linear regression, plotting w,b for the cost function three dimensionally will make a bowl

# Gradient descent
- Gradient descent algorithm
	- $w = w-\alpha \frac{d}{dw}J(w,b)$
	- $b = b - \alpha \frac{d}{db}J(w,b)$
	- $\alpha$ is the learning rate
	- Note that the equals sign is like a programming language statement where we are updating the value of w, not equality
	- Note that we do a simultaneous update of both variables and use the old value of each w and b for computing the new value
- Learning rate
	- If $\alpha$ is too small, it will converge but could take a really long time
	- If $\alpha$ is too big, you could skip past the local minimum and bounce to the other side and never hit the actual solution
- For linear regression models
	- $w = w-\alpha \frac{d}{dw}J(w,b) = \frac{1}{m}\sum_{i=1}^{m}(f_{w,b}(x^{(i)}) - y^{(i)})x^{(i)}$
	- $b = b - \alpha \frac{d}{db}J(w,b) = \frac{1}{m}\sum_{i=1}^{m}(f_{w,b}(x^{(i)}) - y^{(i)})$
- Multiple features (variables)
	- Say you have a bunch of features like size in sq ft, number of bedrooms, number of floors, age of home in years, and then the price in $1000ks
	- n is the number of features (n=4 in this example)
	- $\vec{X}^{(i)}$ = vector of the $i^{th}$ training example
	- $X_{j}^{(i)}$ = value of the feature j in the $i^{th}$ training example
		- For instance j would map to the column that would be 1 for size in sq ft, 2 for number of bedrooms, 3 number of floors, and 4 for age of the home in years
		- i would map to the row of training data (like the $i^{th}$ house's properties)
	- Linear regression for four features would look like:
		- $f_{w,b} = w_1X_1 + w_2X_2 + w_3X_3 + w_4X_4 + b$
		- $\vec{W} = [w_1\; w_2\; w_3\; ... w_n]$
		- $\vec{X} = [X_1\; X_2\; X_3\; ...X_n]$
		- $f_{\vec{W},b}(\vec{X}) = \vec{W}\cdot\vec{X} + b$
		- Multiple linear regression
		- Vectorization in Python
	```python
	w = np.array([1.0, 2.5, -3.3])
	b = 4.0
	x = np.array([10, 20, 30])
	f = np.dot(w, x) + b
	```
	
