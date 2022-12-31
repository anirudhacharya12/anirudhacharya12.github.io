---
layout: post
title: "Testing Latex Output"
date: 2017-01-22
---

Site powered by [Jekyll](http://jekyllrb.com) and uses Markdown to author my posts.

## Testing CSS Stylesheet Latex Output - Multivariate Linear Regression

This post deals with simple multivariate linear regression problem.

F = Number of Features

N = Number of test cases.
$h(x^{(i)}) = w_0 x_0^{(i)} + w_1 x_1^{(i)} + w_2 x_2^{(i)} ... + w_m x_m^{(i)}$

$ h = w.A^T$

$where,$

$w = 1 \times (F+1)$ row-matrix, with the weights given for each feature

$A = N \times (F+1)$ matrix, contains the feature matrix with an extra column of 1s to account for the bias parameter.
hence $h$ will be $1 \times N$ matrix, containing the estimated housing prices for the given features and the current weights.

$B = N \times 1$ matrix containing the actual house prices.

The error cost metric which is sum of squares of the difference is -

$J = \frac{\sum_{i=0}^{i=N}(h(x^{(i)}) - B^{(i)})^2}{2 \times N}$

We need to minimize this squared error with consecutive iterations of the gradient descent algorithm. This is achieved by iteratively changing the values of the weight vector $w$ such that the squared error $J$ decreases with each iteration.

$w_i := w_i - \alpha \times \frac{\partial J}{\partial w_i}$

$w_i := w_i - \alpha \times \frac{\sum_{j=0}^{j=N}(h(x^{(j)}) - B^{(j)}) \times x_i^{(j)}}{N}$


```python
import numpy as np
F,N = [int(i) for i in raw_input().split(' ')]
B = np.zeros(N)
A = np.zeros((N,F))

for i in range(N):
    line = raw_input().split(' ')
    B[i] = line[-1]
    A[i] = line[:F]

T = int(raw_input())
test = np.zeros((T,F))
for i in range(T):
    line = raw_input().split(' ')
    test[i] = line

test = np.column_stack((np.ones(T),test))
A = np.column_stack((np.ones(N),A))

w = np.ones(F+1)
alpha = 0.1
j = 0
h = np.dot(w,A.T)
J = sum((h-B)**2)/(2*N)

while True:
    dJ = (h - B)/N
    for i in range(F+1):
        w[i] = w[i] - alpha*sum(dJ * A[:,i])    
    prevJ = J
    h = np.dot(w,A.T)
    J = sum((h-B)**2)/(2*N)    
    if abs(J-prevJ) < 0.0001:
        break

for i in range(T):
    y = np.dot(w,test.T)

for val in y:
    print val
```
