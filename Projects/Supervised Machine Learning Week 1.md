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
	- Python lab with how to do various NumPy operations like arrays
		- https://www.coursera.org/learn/machine-learning/ungradedLab/zadmO/optional-lab-python-numpy-and-vectorization/lab?path=%2Fnotebooks%2FC1_W2_Lab01_Python_Numpy_Vectorization_Soln.ipynb
	- Cost function
		- $J(w_1,..., w_n, b) = J(\vec{W}, b)$
	- Gradient descent
		- Repeat single feature
			- $w_j = w_j - \alpha \frac{\partial}{\partial w_j}J(w_1,\ldots,w_n,b) = w_j - \alpha \frac{\partial}{\partial w_j}J(\vec{W}, b)$
			- $b = b - \alpha \frac{\partial}{\partial b}J(w_1,\ldots,w_n,b) = b - \alpha \frac{\partial}{\partial b}J(\vec{W}, b)$
		- Multiple features
			- $w_1 = w_1 - \alpha \frac{1}{m}\sum_{i=1}^{m}(f_{\vec{w},b})(\vec{x}^{(i)}-y^{(i)})x_1^{(i)}$
			- $w_n = w_n - \alpha \frac{1}{m}\sum_{i=1}^{m}(f_{\vec{w},b})(\vec{x}^{(i)}-y^{(i)})x_n^{(i)}$
			- $b = b - \alpha \frac{1}{m}\sum_{i=1}^{m}\left(f_{\vec{w},b}\right)\left(\vec{x}^{(i)}-y^{(i)}\right)$
	- Normal equation
		- Only for linear regression
		- Doesn't generalize to other learning algorithms
		- Slow when number of features is large (> 10,000)
		- Is possibly implemented in some machine learning libraries
		- Gradient descent if the recommended method for finding parameters w,b
	- Feature scaling
		- Imagine you have features size in sqft and bedrooms. The first will range in the 300-2,000 range and the second will range in the 1 to 5 range.
		- You can do mean normalization
			- $x_n$ is feature n
			- $\mu_n$ is the average of the data for feature n
			- $Normalized\;x_n = \frac{x_n - \mu_n}{x_{max} - x_{min}}$
		- Z-score normalization
			- $x_n$ is feature n
			- $\mu_n$ is the average of the data for feature n
			- $\sigma_n$ is the standard deviation of the data for feature n
			- $Normalized\;x_n = \frac{x_n - \mu_n}{\sigma_n}$
		- Generally, you should rescale if certain features are orders of magnitude different than other features
		- Causes gradient descent to run a lot faster
	- Learning rate
		- Too small and can take forever
		- Too large and it might not converge
		- Can try a number of learning rates for a couple of iterations and see if the cost function is still dropping. If it is working at a low value, can try shifting to a higher value and see if things still are dropping
	- Feature engineering
		- Imagine you have width and depth of the lot as features. You could choose to create a feature area computed from the existing features and that might be more relevant and efficient than keeping these as separate features. Many times this will be intuitive.
	- Polynomial regression
		- You could basically use feature engineering to transform a feature x into $x^2$, $x^3$, $\sqrt{x}$.
		- It keeps things as linear regression but allows you to interpret the data in a way that makes more sense
		- If you do this, you will probably definitely want to do feature scaling to keep the data in a range that makes sense relative to other features.

# Classification
- Classification makes a decision like is this email spam, is this transaction fraudulent, or is this tumor malignant
- Binary classification is when there are two possible outcomes
- Generally, we will call 1 or true the positive class and 0 or false the negative class
- Logistic regression - the most common algorithm for classification
- We will use the sigmoid function (also known as the logistic function)
- The sigmoid function is .5 at the origin and approaches 0 as it moves to the left of the origin and 1 as moves to the right of the origin. It always produces values between 0 and 1
- Sigmoid function is $g(z) = \frac{1}{1+\epsilon^{-z}}$
	- As z gets huge $\epsilon^{-z}$ will become a tiny number which will make the expression get very close to 1
	- As z gets hugely negative $\epsilon^{-z}$ will become massive which will make the expression get very close to zero
	- At 0, it is $\frac{1}{2}$
- Logistic regression
	- $z = \vec{W} \cdot \vec{X} + b$
	- $g(z) = \frac{1}{1+\epsilon^{-z}}$
	- $f_{\vec{W},b}(\vec{X}) = g(\vec{W}\cdot\vec{X}+b) = \frac{1}{1 + \epsilon^{-(\vec{W}\cdot\vec{X} + b)}}$
- Squared error cost function is non-convex for logistic regression so you can get multiple local minimums
- Logistic loss function
$$
L(f_{\vec{W},b}(\vec{X}^{(i)}), y^{(i)}) = 
\begin{cases}
-\log(f_{\vec{W},b}(\vec{X}^{(i)})) & \text{if }y^{(i)} = 1 \\
-\log(1 - f_{\vec{W},b}(\vec{X}^{(i)})) & \text{if }y^{(i)} = 0
\end{cases}
$$
- Logistic loss function (Continued)
	- For the $y^{(i)} = 1$ case, the curve starts at 1 at the origin and drops down to zero at a value of 1. This makes sense since there is no error at 1 but a maximum error value for predicting a zero.
	- For the $y^{(i)} = 0$ case, the curve starts at 0 at the origin and curves up to 1 at the value of 1. This makes sense since there is no error at the origin but a maximum value for predicting a 1.
	- Compared to a line, a value of .5 is penalized less with a log. Predictions close to the correct values are barely penalized at all compared to a line.
	- The bigger win is that this cost function IS convex so gradient descent will converge
- Simplified loss function
	- $L(f_{\vec{W},b}(\vec{X}^{(i)}), y^{(i)}) = -y^{(i)}\log(f_{\vec{W},b}(\vec{X}^{(i)})) -(1 - y^{(i)})\log(1 - f_{\vec{W},b}(\vec{X}^{(i)}))$
	- Since the y values are 1 or 0, one of other component of the equation will disappear without needing cases
	- This makes the cost function:
		- $J(\vec{W},b) = \frac{1}{m}\sum_{i=1}^{m}[L(f_{\vec{W},b}(\vec{X}^{(i)}), y^{(i)})]$
		- $J(\vec{W},b) = -\frac{1}{m}\sum_{i=1}^{m}[y^{(i)}\log(f_{\vec{W},b}(\vec{X}^{(i)})) + (1 - y^{(i)})\log(1 - f_{\vec{W},b}(\vec{X}^{(i)}))]$
		- This is called maximum likelihood estimation
- Overfitting
	- When you create a solution too focused on your data that doesn't generalize for other data
	- You can address it by adding more training data or possibly omitting certain features through feature selection. Feature selection is sometimes a matter of intuition
	- Regularization is a middle ground with feature selection where you keep all your features but reduce the effect on some of them to have a more general result
		- $J(\vec{W}, b) = \frac{1}{2m}\sum_{i=1}^m(f_{\vec{w},b}(\vec{X}^{(i)}) - y^{(i)})^2 + \frac{\lambda}{2m}\sum_{j=1}^{n}w_{j}^{2}$
		- By adding the weights in as another factor to be minimized, it makes the weights that substantially reduce the cost shine over those that might be just encouraging overfitting
		- $\lambda$ is the gateway for deciding how much we want to value fitting the curve versus minimizing the size of the weights. It is called the regularization parameter
		- Implementing gradient descent turns into:
			- $w_j = w_j - \alpha [\frac{1}{m}\sum_{i=1}^{m}[(f_{\vec{w},b}(\vec{x}^{(i)})-y^{(i)})x_j^{(i)}] + \frac{\lambda}{m}w_j]$
			- $b = b - \alpha \frac{1}{m}\sum_{i=1}^{m}(f_{\vec{w},b})(\vec{x}^{(i)}-y^{(i)})$
			- We can rewrite the first as:
				- $w_j = 1w_j - \alpha \frac{\lambda}{m}w_j - \alpha \frac{1}{m}\sum_{i=1}^{m}(f_{\vec{w},b}(\vec{x}^{(i)}) -y^{(i)})x_j^{(i)}$
				- Because $\alpha$ and $\lambda$ are both relatively small, the term $-\alpha \frac{\lambda}{m}w_j$ will really minimize the affect of $w_j$ as far as regularization is concerned. Making $\lambda$ larger will obviously cause much larger regularization.

Nueral Networks
- A neural network has an input layer, and output layer, and one or more hidden layers
- Each neuron takes a set of input parameters, has a set of weights, and outputs an activation value
- A hidden layer is composed of a set of neurons
- Looking at a hidden layer
	- There is a set of inputs $\vec{X}$
	- Each neuron has a set of weights ($\vec{W}_1$, $\vec{W}_2$, ... $\vec{W}_n$)
	- Each neuron has an output activation value ($a_1$, $a_2$, ... $a_n$)
	- $a_n = g(\vec{W}_n \cdot \vec{X}_n + b_n)$
	- $g(\vec{W}_n \cdot \vec{X}_n + b_n) = \frac{1}{1 - \epsilon^{-(\vec{W}_n \cdot \vec{X}_n + b_n)}}$
		- g is called the activation function
- Multiple layers
	- The input layer is referred to as layer 0
	- Each additional layer is 1, 2, and so forth (there can be hundreds of hidden layers)
	- You add an upper square bracket to denote the layer (m)
		- $a_n^{[m]} = g(\vec{W}_n^{[m]} \cdot \vec{X}_n^{[m]} + b_n^{[m]})$
		- $a_n^{[m]} = g(\vec{W}_n^{[m]} \cdot \vec{a}_{n}^{[m-1]} + b_n^{[m]})$
	- Note the the output of layer m ($a_n^{[m]}$) is the input to layer m+1 ($a_n^{[m]} = \vec{X}_n^{[m+1]}$)
	- One option you can do for each layer is to either output the raw scalar or apply a filter like $\ge0$ to make the output boolean / binary.
	- The routing of activation variables from one layer to inputs of the next is called forward propagation
- Example neural network
	- 8x8 grid of 255 or 0 pixels. Determine if each image is a 1 or 0 (printed)
	- Layer 1 has 25 neurons, layer 2 has 15, and layer 3 has one neuron that outputs a 1 or 0
- Data in tensorflow
	- Everything is a matrix. Even a vector is specified as x = np.array(\[\[200.0, 17.0\]\]) so it is essentially a row vector matrix.
		- You should convert this to a tensor with a1 = layer_1(x)
	- In tensorflow, you would say tf.Tensor(\[\[0.2 0.7 0.3\]\], shape=(1, 3), dtype=float32)
	- You can call a1.numpy() to get back to the numpy version
	- When you read tensor, think matrix
```python
x = np.array([[200.0, 17.0]])
layer_1 = Dense(units=3, activation="sigmoid")
a1 = layer_1(x)
layer_2 = Dense(units=1, activation="sigmoid")
a2 = layer_2(a1)
```
Alternative approach is:
```python
layer_1 = Dense(units=3, activation="sigmoid")
layer_2 = Dense(units=1, activation="sigmoid")
model = Sequential([layer_1, layer_2])
x = np.array([
	[200.0, 17.0],
	[120.0, 5.0],
	[425.0, 20.0],
	[212.0, 18.0]
])
y = np.array([1,0,0,1])
model.compile(...) -- Details to come
model.fit(x, y)
model.predict(x_new)
```
A simplified approach would be:
```python
model = Sequential([
	Dense(units=3, activation="sigmoid"),
	Dense(units=1, activation="sigmoid")
])
```

# Vectorization in hardware
- Loop based approach
```python
x = np.array([200, 17])
W = np.array([
	[1, -3, 5],
	[-2, 4, -6]])
b = np.array([-1, 1, 2])

def dense(a_in, W, b):
	units = W.shape[1]
	a_out = np.zeros(units)
	for j in range(units):
		w = W[:,j]
		z = np.dot(w, a_in) + b[j]
		a_out[j] = g(z)
	return a_out
```
- Vectorized approach
```python
x = np.array([[200, 17]])
W = np.array([
	[1, -3, 5],
	[-2, 4, -6]])
b = np.array([[-1, 1, 2]])

def dense(A_in, W, b):
	Z = np.matmul(A_in, W) + B
	A_out = g(Z)
	return A_out
```

Matrix multiplication
- Dot product of two vectors is the summation of the pairwise multiplication of the same position element in both vectors
- Transposing a matrix means turning each row into a column so a 3x2 matrix turns into a 2x3 matrix.
	- Since a n element vector vector is really a 1xn matrix, transposing a vector creates a nx1 matrix
	- $z = \vec{a} \cdot \vec{W}$ is the same as $z = \vec{a}^T \vec{W}$ where the second is degenerate matrix multiplication
	- If you have a matrix A in numpy, you can generate the transpose by calling A.T
- General matrix multiplication for an nxp matrix A by a pxm matrix B for an output nxm matrix C is, repeat for i = 0 to n
	- for j = 0 to m
		- C[i, j] = dot_product(row i of A, column j of B)
	- In python, you can do matrix multiplication with np.matmul(mat1, mat2)
		- This will use available vector hardware
- Training a model in tensorflow looks like:
```python
import tensorflow as tf
from tensorflow.keras import Sequential
from tensorflow.keras.layers import Dense
model = Sequential([
	Dense(units=25, activation='sigmoid'),
	Dense(units=15, activation='sigmoid'),
	Dense(units=1, activation='sigmoid')
	])
from tensorflow.keras.losses import BinaryCrossentropy
model.compile(loss=BinaryCrossentropy)
model.fit(X, Y, epochs=100)
```
Training models
- Logistic regression
	- Compute the output given x, w, and b
		- $z = np.dot(w, x) + b$
		- f_x = 1 / (1 + np.exp(-z))
	- Specify cost and loss
		- loss = -y * np.log(f_x) - (1-y) * np.log(1-f_x)
		- $J(\vec{W}, b) = \frac{1}{m} \sum_{i=1}^m L(f_{\vec{W},b}\vec{X}^{(i)}, y^{(i)})$
	- Train on data to minimize cost function J with gradient descent
		- w = w - alpha * dj_dw
		- b = b - alpha * dj_db
- Neural networks
	- Compute the output given input parameters
		- model = Sequential([Dense(...), Dense(...), ...])
	- Binary cross entropy
		- model.compile(loss=BinaryCrossentropy())
		- model.fit(x, y, epochs=100)
	- For creating the model in tensorflow
	```python
	import tensorflow as tf
	from tensorflow.keras import Sequential
	from tensorflow.keras.layers import Dense
	
	model = Sequential([
		Dense(units=25, activation='sigmoid'),
		Dense(units=15, activation='sigmoid'),
		Dense(units=1, activation='sigmoid')
		])
	```
	- Loss and cost functions
		- Loss function(L) is generally this for binary classification
			- $L(f(\vec{X}), y) = -y \log(f(\vec{X})) - (1 - y) \log(1 - f(\vec{X}))$
			- BinaryCrossentropy()
		- For regression problems you would use:
			- MeanSquaredError()
		- Cost is J
		- Tensorflow computes the partial derivatives for gradient descent using "back propagation"
			- You do this via model.fit(X, y, epochs=100)
- Alternatives t0o the sigmoid activation function
	- Sigmoid is $z(f(x)) = \frac{1}{1 - \epsilon^{1-f(x)}}$