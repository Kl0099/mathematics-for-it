# Mathematics for IT — Least Squares Problems and Linear Models
## M.Tech. 1st Semester — Theory Exam Study + Practice Notes

> **Scope:** This document is based only on the supplied syllabus material on **Least Squares Problems and Linear Models**.  
> Programming questions are intentionally excluded. The focus is on understanding, derivations, formulas, numerical practice, and exam-style theory questions.

---

# 1. What is this topic about?

Suppose we have several observations and want to find a mathematical relationship between them.

For example, we may have measurements such as:

- input: study hours
- output: marks

Ideally, one equation might pass exactly through every observation. In real data, however, measurements usually contain **noise and variation**.

Therefore, instead of asking:

\[
Ax=b
\]

we often ask:

\[
Ax\approx b
\]

and find the solution that makes the error as small as possible.

This is the main idea behind **least squares**.

The central problem is:

\[
\boxed{\min_x \|Ax-b\|^2}
\]

### Simple meaning

Least squares means:

> **Find the values of the unknown parameters that make the total squared error as small as possible.**

---

# 2. Overdetermined Systems

## 2.1 What is an overdetermined system?

Consider:

\[
Ax=b
\]

If matrix \(A\) has **more rows than columns**, then there are more equations than unknowns.

Such a system is called an **overdetermined system**.

### Example

\[
\begin{aligned}
x+y &= 2\\
x+2y &= 3\\
x+3y &= 5
\end{aligned}
\]

There are:

- 3 equations
- 2 unknowns

So the system is overdetermined.

---

## 2.2 Why may there be no exact solution?

Every equation imposes a condition on the unknowns.

When there are more equations than unknowns, all equations may not be simultaneously consistent.

Therefore, there may be no \(x\) such that:

\[
Ax=b
\]

exactly.

Least squares instead finds:

\[
\hat{x}
\]

such that:

\[
A\hat{x}
\]

is as close as possible to \(b\).

It does this by minimizing:

\[
\boxed{\|Ax-b\|^2}
\]

---

## Exam definition

**Overdetermined system:** A system \(Ax=b\) in which matrix \(A\) has more rows than columns, meaning there are more equations than unknowns. Such a system may be inconsistent, so least squares can be used to obtain the closest approximate solution.

---

# 3. Residual

Suppose \(\hat{x}\) is our approximate solution.

The predicted vector is:

\[
A\hat{x}
\]

The difference between the actual vector \(b\) and predicted vector \(A\hat{x}\) is called the **residual**.

\[
\boxed{r=b-A\hat{x}}
\]

For individual observations:

\[
\boxed{e_i=y_i-\hat y_i}
\]

### Remember

\[
\boxed{\text{Residual}=\text{Actual}-\text{Predicted}}
\]

---

## Example

Suppose:

\[
y=10,\qquad \hat y=8
\]

Then:

\[
e=y-\hat y=10-8=2
\]

If:

\[
y=8,\qquad \hat y=10
\]

then:

\[
e=8-10=-2
\]

The sign tells us whether the prediction is above or below the actual value.

---

# 4. SSE — Sum of Squared Errors

Residuals can be positive or negative.

If we simply added them, positive and negative errors could cancel.

Therefore, we square the residuals.

\[
\boxed{SSE=\sum_i(y_i-\hat y_i)^2}
\]

SSE is also called **RSS (Residual Sum of Squares)** in the supplied material.

### Meaning

SSE tells us the total squared prediction error.

A smaller SSE means the fitted values are closer to the observations.

---

## Small example

Actual values:

\[
y=[2,5,7]
\]

Predicted values:

\[
\hat y=[3,4,6]
\]

Residuals:

\[
e=[-1,1,1]
\]

Therefore:

\[
SSE=(-1)^2+1^2+1^2
\]

\[
\boxed{SSE=3}
\]

---

# 5. MSE — Mean Squared Error

SSE gives the total squared error.

MSE gives the **average squared error**.

\[
\boxed{MSE=\frac{1}{m}\sum_i(y_i-\hat y_i)^2}
\]

Since:

\[
SSE=\sum_i(y_i-\hat y_i)^2
\]

we can write:

\[
\boxed{MSE=\frac{SSE}{m}}
\]

where \(m\) is the number of observations.

---

# 6. RMSE — Root Mean Squared Error

RMSE is the square root of MSE.

\[
\boxed{RMSE=\sqrt{MSE}}
\]

Therefore:

\[
\boxed{RMSE=\sqrt{\frac{SSE}{m}}}
\]

An important point from the syllabus:

> RMSE has the same units as the response variable.

---

## SSE, MSE and RMSE together

Suppose:

\[
SSE=20,\qquad m=5
\]

Then:

\[
MSE=\frac{20}{5}=4
\]

and:

\[
RMSE=\sqrt4=2
\]

So:

\[
\boxed{SSE=20,\quad MSE=4,\quad RMSE=2}
\]

### Easy memory trick

- **SSE** → total squared error
- **MSE** → average squared error
- **RMSE** → square root of average squared error

---

# 7. Geometric Interpretation of Least Squares

This is one of the most important concepts.

The columns of \(A\) span a subspace called:

\[
\mathrm{Col}(A)
\]

Every vector \(Ax\) lies inside this column space.

Suppose:

\[
b\notin \mathrm{Col}(A)
\]

Then there is no exact solution to:

\[
Ax=b
\]

because \(b\) cannot be produced by any combination of the columns of \(A\).

Least squares finds the point in the column space that is **closest to \(b\)**.

Therefore:

\[
\boxed{A\hat{x}=\mathrm{proj}_{\mathrm{Col}(A)}(b)}
\]

### Visual idea

Think of \(b\) as a point outside a plane.

Least squares drops a perpendicular from \(b\) onto that plane.

The point where the perpendicular meets the plane is:

\[
A\hat{x}
\]

That is the best approximation.

---

# 8. Why is the Residual Orthogonal?

The residual is:

\[
r=b-A\hat{x}
\]

At the least-squares solution:

\[
\boxed{A^T(b-A\hat{x})=0}
\]

Therefore:

\[
\boxed{A^Tr=0}
\]

This means the residual is orthogonal to the column space of \(A\).

### Intuition

The residual points from the fitted point \(A\hat{x}\) toward \(b\).

At the closest point, this direction must be perpendicular to the space containing the fitted point.

Otherwise, we could move slightly inside the column space and get even closer to \(b\).

---

# 9. Normal Equations

Starting with the orthogonality condition:

\[
A^T(b-A\hat{x})=0
\]

Expand:

\[
A^Tb-A^TA\hat{x}=0
\]

Move the second term:

\[
A^Tb=A^TA\hat{x}
\]

Therefore:

\[
\boxed{A^TA\hat{x}=A^Tb}
\]

These are called the **normal equations**.

---

## If \(A\) has linearly independent columns

Then:

\[
\boxed{\hat{x}=(A^TA)^{-1}A^Tb}
\]

This gives the least-squares solution.

### Important exam point

Do not confuse:

\[
A^TA\hat{x}=A^Tb
\]

with:

\[
A\hat{x}=b
\]

The first is the normal-equation system used to obtain the least-squares solution.

---

# 10. Derivation of the Normal Equations

This is a common **5-mark question**.

We want to minimize:

\[
J(\beta)=\|y-X\beta\|^2
\]

Write it using transpose:

\[
J(\beta)=(y-X\beta)^T(y-X\beta)
\]

Differentiate with respect to \(\beta\):

\[
\nabla_\beta J=-2X^T(y-X\beta)
\]

At the minimum:

\[
\nabla_\beta J=0
\]

Therefore:

\[
-2X^T(y-X\hat{\beta})=0
\]

Divide by \(-2\):

\[
X^T(y-X\hat{\beta})=0
\]

Expand:

\[
X^Ty-X^TX\hat{\beta}=0
\]

Hence:

\[
\boxed{X^TX\hat{\beta}=X^Ty}
\]

These are the normal equations.

---

# 11. Linear Models

A simple linear model is:

\[
\boxed{y=\beta_0+\beta_1x+\epsilon}
\]

where:

- \(\beta_0\) = intercept
- \(\beta_1\) = slope
- \(x\) = predictor/input
- \(y\) = response/output
- \(\epsilon\) = error

After fitting the model:

\[
\boxed{\hat y=\hat\beta_0+\hat\beta_1x}
\]

---

## What do intercept and slope mean?

### Intercept

\[
\beta_0
\]

is the predicted value of \(y\) when \(x=0\).

### Slope

\[
\beta_1
\]

describes how the fitted value of \(y\) changes with \(x\).

For example:

\[
\hat y=2+3x
\]

Here:

- intercept = 2
- slope = 3

If \(x\) increases by 1, the fitted \(y\) increases by 3.

---

# 12. Design Matrix

The design matrix is one of the most important ideas for linear models.

For:

\[
y=\beta_0+\beta_1x+\epsilon
\]

the design matrix is:

\[
\boxed{
X=
\begin{bmatrix}
1&x_1\\
1&x_2\\
\vdots&\vdots\\
1&x_m
\end{bmatrix}
}
\]

The matrix form is:

\[
\boxed{y=X\beta+\epsilon}
\]

where:

\[
\beta=
\begin{bmatrix}
\beta_0\\
\beta_1
\end{bmatrix}
\]

---

## Why is there a column of ones?

The first column contains ones because we need the intercept:

\[
\beta_0
\]

For each observation:

\[
1(\beta_0)+x_i(\beta_1)
\]

So the column of ones represents the intercept.

### Common mistake

Forgetting the column of ones when the model contains an intercept.

---

# 13. Fitted Values

Once the coefficients are estimated:

\[
\hat{\beta}
\]

the fitted values are:

\[
\boxed{\hat y=X\hat\beta}
\]

The residual vector is:

\[
\boxed{e=y-\hat y}
\]

Therefore:

\[
\boxed{e=y-X\hat\beta}
\]

---

# 14. Multiple Linear Models

If there are several predictors:

\[
\boxed{
y=\beta_0+\beta_1x_1+\cdots+\beta_px_p+\epsilon
}
\]

In matrix form:

\[
\boxed{y=X\beta+\epsilon}
\]

For two predictors:

\[
X=
\begin{bmatrix}
1&x_{11}&x_{12}\\
1&x_{21}&x_{22}\\
\vdots&\vdots&\vdots\\
1&x_{m1}&x_{m2}
\end{bmatrix}
\]

The first column is again the intercept column.

---

# 15. Polynomial Models

A quadratic model is:

\[
\boxed{y=\beta_0+\beta_1x+\beta_2x^2+\epsilon}
\]

Its design matrix is:

\[
\boxed{
X=
\begin{bmatrix}
1&x_1&x_1^2\\
1&x_2&x_2^2\\
\vdots&\vdots&\vdots\\
1&x_m&x_m^2
\end{bmatrix}
}
\]

### Important exam concept

A polynomial model is **nonlinear in \(x\)**, but it is **linear in its parameters**:

\[
\beta_0,\beta_1,\beta_2
\]

Therefore, least squares can still be used.

---

# 16. Basis-Function Models

A more general model is:

\[
\boxed{
y\approx\beta_1\phi_1(x)+\cdots+\beta_p\phi_p(x)
}
\]

A basis function is simply a function used as a building block of the model.

Examples from the syllabus:

\[
1,\ x,\ x^2
\]

and:

\[
1,\ x,\ \sin x,\ \cos x
\]

The important idea is:

> We choose functions of \(x\), put their values into the design matrix, and estimate their coefficients using least squares.

---

# 17. Projection Matrix

If \(X\) has full column rank, the orthogonal projection matrix onto \(\mathrm{Col}(X)\) is:

\[
\boxed{P=X(X^TX)^{-1}X^T}
\]

The fitted values are:

\[
\boxed{\hat y=Py}
\]

The residual is:

\[
\boxed{e=(I-P)y}
\]

Two important properties of an orthogonal projection matrix are:

\[
\boxed{P^2=P}
\]

and:

\[
\boxed{P^T=P}
\]

### Meaning of \(P^2=P\)

Applying the projection twice gives the same result as applying it once.

---

# 18. Coefficient of Determination \(R^2\)

Another measure of model fit is:

\[
\boxed{R^2=1-\frac{SSE}{SST}}
\]

where:

\[
\boxed{SST=\sum_i(y_i-\bar y)^2}
\]

Here:

- SSE = unexplained squared error
- SST = total variation around the mean

The supplied material states that a high \(R^2\) indicates a strong **in-sample fit according to this measure**.

### Important warning

A high \(R^2\):

- does not prove causation
- does not guarantee good performance on new data

---

# 19. QR Decomposition

For numerical computation, directly using normal equations can be less desirable.

QR decomposition writes:

\[
\boxed{X=QR}
\]

Using QR, the least-squares problem leads to:

\[
\boxed{R\hat\beta=Q^Ty}
\]

### Why study QR?

The key syllabus point is:

> QR decomposition is often preferable to forming normal equations for numerical stability.

You should know:

1. What \(X=QR\) means.
2. The resulting equation:
   \[
   R\hat\beta=Q^Ty
   \]
3. That QR can be numerically more stable than forming normal equations.

---

# 20. SVD and Pseudoinverse

The Singular Value Decomposition is:

\[
\boxed{X=U\Sigma V^T}
\]

The pseudoinverse is:

\[
\boxed{X^+=V\Sigma^+U^T}
\]

A least-squares/minimum-norm solution can be written as:

\[
\boxed{\hat\beta=X^+y}
\]

### Why is SVD important?

The syllabus specifically highlights SVD as useful for:

> rank-deficient or nearly rank-deficient matrices.

So remember:

\[
\boxed{\text{SVD}\rightarrow\text{pseudoinverse}\rightarrow\text{least-squares/minimum-norm solution}}
\]

---

# 21. Rank and Multicollinearity

If \(X\) has **full column rank**, its columns are independent and the coefficient vector is unique.

If predictors are nearly linearly dependent, the problem can become ill-conditioned.

This situation is called:

\[
\boxed{\text{multicollinearity}}
\]

Example:

\[
x_2\approx2x_1
\]

The predictors contain nearly redundant information.

### Possible consequences

- unstable coefficients
- sensitivity to small changes in data

---

# 22. Weighted Least Squares

Not every observation may be equally reliable.

Weighted least squares gives different observations different weights.

It minimizes:

\[
\boxed{
\sum_i w_i(y_i-\hat y_i)^2
}
\]

In matrix form:

\[
\boxed{
(y-X\beta)^TW(y-X\beta)
}
\]

The weighted normal equations are:

\[
\boxed{
X^TWX\hat\beta=X^TWy
}
\]

### Main idea

Ordinary least squares treats observations equally.

Weighted least squares gives observations different importance according to their weights.

---

# 23. Least-Squares Workflow

A typical linear-model workflow is:

1. Collect data.
2. Select response and predictor variables.
3. Construct the design matrix.
4. Fit the model.
5. Generate predictions.
6. Calculate residuals.
7. Calculate error measures.
8. Inspect residual patterns.
9. Validate on new data when appropriate.

### Easy memory chain

\[
\boxed{
\text{Data}
\rightarrow
\text{Design Matrix}
\rightarrow
\text{Fit}
\rightarrow
\text{Predict}
\rightarrow
\text{Residuals}
\rightarrow
\text{Error}
}
\]

---

# 24. The Main Conceptual Chain

This is one of the best things to memorize:

\[
\boxed{
\text{Linear Model}
\rightarrow
\text{Least Squares}
\rightarrow
\text{Projection}
\rightarrow
\text{Orthogonality}
\rightarrow
\text{Normal Equations}
}
\]

### In words

1. We have a **linear model**.
2. Real observations may not fit exactly.
3. We use **least squares** to minimize squared error.
4. Geometrically, this is an **orthogonal projection**.
5. The residual becomes **orthogonal** to the column space.
6. Orthogonality produces the **normal equations**.

---

# 25. Fully Worked Numerical Example

Consider:

\[
A=
\begin{bmatrix}
1&1\\
1&2\\
1&3
\end{bmatrix},
\qquad
b=
\begin{bmatrix}
2\\
3\\
5
\end{bmatrix}
\]

We want:

\[
\hat{x}=\arg\min_x\|Ax-b\|^2
\]

## Step 1: Calculate \(A^TA\)

\[
A^T=
\begin{bmatrix}
1&1&1\\
1&2&3
\end{bmatrix}
\]

Therefore:

\[
A^TA=
\begin{bmatrix}
1&1&1\\
1&2&3
\end{bmatrix}
\begin{bmatrix}
1&1\\
1&2\\
1&3
\end{bmatrix}
\]

\[
=
\begin{bmatrix}
3&6\\
6&14
\end{bmatrix}
\]

## Step 2: Calculate \(A^Tb\)

\[
A^Tb=
\begin{bmatrix}
1&1&1\\
1&2&3
\end{bmatrix}
\begin{bmatrix}
2\\
3\\
5
\end{bmatrix}
\]

\[
=
\begin{bmatrix}
10\\
23
\end{bmatrix}
\]

## Step 3: Normal equations

\[
\begin{bmatrix}
3&6\\
6&14
\end{bmatrix}
\hat{x}
=
\begin{bmatrix}
10\\
23
\end{bmatrix}
\]

So:

\[
3x_1+6x_2=10
\]

\[
6x_1+14x_2=23
\]

From the first equation:

\[
x_1=\frac{10-6x_2}{3}
\]

Substitute into the second:

\[
6\left(\frac{10-6x_2}{3}\right)+14x_2=23
\]

\[
20-12x_2+14x_2=23
\]

\[
2x_2=3
\]

\[
x_2=1.5
\]

Then:

\[
x_1=\frac{10-9}{3}=\frac13
\]

Therefore:

\[
\boxed{
\hat{x}=
\begin{bmatrix}
1/3\\
3/2
\end{bmatrix}
}
\]

## Step 4: Find fitted values

\[
A\hat{x}
=
\begin{bmatrix}
1&1\\
1&2\\
1&3
\end{bmatrix}
\begin{bmatrix}
1/3\\
3/2
\end{bmatrix}
\]

\[
=
\begin{bmatrix}
11/6\\
10/3\\
29/6
\end{bmatrix}
\]

Approximately:

\[
A\hat{x}
=
\begin{bmatrix}
1.833\\
3.333\\
4.833
\end{bmatrix}
\]

## Step 5: Residual

\[
r=b-A\hat{x}
\]

\[
=
\begin{bmatrix}
2\\3\\5
\end{bmatrix}
-
\begin{bmatrix}
1.833\\3.333\\4.833
\end{bmatrix}
\]

\[
\boxed{
r\approx
\begin{bmatrix}
0.167\\
-0.333\\
0.167
\end{bmatrix}
}
\]

Notice:

\[
A^Tr=0
\]

up to rounding.

This demonstrates the orthogonality condition.

---

# 26. Numerical Practice — Answers

## Question 1

For:

\[
A=
\begin{bmatrix}
1&1\\
1&2\\
1&3
\end{bmatrix},
\qquad
b=
\begin{bmatrix}
2\\
3\\
5
\end{bmatrix}
\]

find the least-squares solution.

### Answer

\[
A^TA=
\begin{bmatrix}
3&6\\
6&14
\end{bmatrix}
\]

\[
A^Tb=
\begin{bmatrix}
10\\
23
\end{bmatrix}
\]

Solving:

\[
(A^TA)\hat{x}=A^Tb
\]

gives:

\[
\boxed{
\hat{x}=
\begin{bmatrix}
1/3\\
3/2
\end{bmatrix}
}
\]

---

## Question 2

Using the previous answer, find the residual vector.

### Answer

\[
A\hat{x}
=
\begin{bmatrix}
11/6\\
10/3\\
29/6
\end{bmatrix}
\]

Therefore:

\[
r=b-A\hat{x}
\]

\[
\boxed{
r=
\begin{bmatrix}
1/6\\
-1/3\\
1/6
\end{bmatrix}
}
\]

---

## Question 3

Verify that:

\[
A^Tr=0
\]

### Answer

\[
A^T=
\begin{bmatrix}
1&1&1\\
1&2&3
\end{bmatrix}
\]

and:

\[
r=
\begin{bmatrix}
1/6\\
-1/3\\
1/6
\end{bmatrix}
\]

Therefore:

\[
A^Tr=
\begin{bmatrix}
1/6-1/3+1/6\\
1/6-2/3+3/6
\end{bmatrix}
\]

\[
=
\begin{bmatrix}
0\\
0
\end{bmatrix}
\]

Hence:

\[
\boxed{A^Tr=0}
\]

So the residual is orthogonal to the column space.

---

## Question 4

For actual values:

\[
y=[2,5,7]
\]

and predicted values:

\[
\hat y=[3,4,6]
\]

find SSE, MSE and RMSE.

### Answer

Residuals:

\[
e=[-1,1,1]
\]

SSE:

\[
SSE=(-1)^2+1^2+1^2=3
\]

MSE:

\[
MSE=\frac{3}{3}=1
\]

RMSE:

\[
RMSE=\sqrt1=1
\]

Therefore:

\[
\boxed{SSE=3,\quad MSE=1,\quad RMSE=1}
\]

---

## Question 5

Construct the design matrix for:

\[
y=\beta_0+\beta_1x+\epsilon
\]

when:

\[
x=[2,4,6]
\]

### Answer

The design matrix contains a column of ones and a column of \(x\):

\[
\boxed{
X=
\begin{bmatrix}
1&2\\
1&4\\
1&6
\end{bmatrix}
}
\]

---

## Question 6

Construct the design matrix for:

\[
y=\beta_0+\beta_1x+\beta_2x^2+\epsilon
\]

when:

\[
x=[1,2,3]
\]

### Answer

\[
X=
\begin{bmatrix}
1&1&1\\
1&2&4\\
1&3&9
\end{bmatrix}
\]

Therefore:

\[
\boxed{
X=
\begin{bmatrix}
1&1&1\\
1&2&4\\
1&3&9
\end{bmatrix}
}
\]

---

## Question 7

If:

\[
SSE=25,\qquad m=10
\]

find MSE and RMSE.

### Answer

\[
MSE=\frac{SSE}{m}
=\frac{25}{10}
=2.5
\]

Therefore:

\[
RMSE=\sqrt{2.5}
\]

\[
\boxed{RMSE\approx1.581}
\]

---

## Question 8

If:

\[
SSE=10,\qquad SST=50
\]

find \(R^2\).

### Answer

\[
R^2=1-\frac{SSE}{SST}
\]

\[
=1-\frac{10}{50}
\]

\[
=1-0.2
\]

\[
\boxed{R^2=0.8}
\]

---

# 27. Exam-Style 3-Mark Questions

These are designed for short-answer preparation.

---

## 3-Mark Q1. Define an overdetermined system.

### Answer

An overdetermined system is a system:

\[
Ax=b
\]

where matrix \(A\) has more rows than columns. Thus, there are more equations than unknowns. Such a system may be inconsistent, so least squares can be used to find an approximate solution.

---

## 3-Mark Q2. Define residual and write its formula.

### Answer

The residual is the difference between the actual vector and the predicted vector.

\[
\boxed{r=b-A\hat{x}}
\]

For scalar observations:

\[
\boxed{e_i=y_i-\hat y_i}
\]

It represents the prediction error.

---

## 3-Mark Q3. What does least squares minimize?

### Answer

Least squares minimizes the squared norm of the residual:

\[
\boxed{\|Ax-b\|^2}
\]

For a linear model:

\[
\boxed{\|y-X\beta\|^2}
\]

Thus, it chooses the parameters that give the smallest total squared error.

---

## 3-Mark Q4. What is SSE?

### Answer

SSE stands for Sum of Squared Errors.

\[
\boxed{SSE=\sum_i(y_i-\hat y_i)^2}
\]

It represents the total squared difference between observed and fitted values.

---

## 3-Mark Q5. State the normal equations.

### Answer

The normal equations are:

\[
\boxed{A^TA\hat{x}=A^Tb}
\]

For linear regression:

\[
\boxed{X^TX\hat\beta=X^Ty}
\]

They result from the orthogonality of the least-squares residual to the column space.

---

## 3-Mark Q6. What is a design matrix?

### Answer

A design matrix is the matrix that organizes the predictor variables and basis functions used in a linear model.

For:

\[
y=\beta_0+\beta_1x+\epsilon
\]

it is:

\[
\boxed{
X=
\begin{bmatrix}
1&x_1\\
1&x_2\\
\vdots&\vdots\\
1&x_m
\end{bmatrix}
}
\]

The column of ones represents the intercept.

---

## 3-Mark Q7. What is multicollinearity?

### Answer

Multicollinearity occurs when predictor variables are nearly linearly dependent.

For example:

\[
x_2\approx2x_1
\]

It can make the problem ill-conditioned and can cause unstable coefficients that are sensitive to small changes in the data.

---

# 28. Exam-Style 4-Mark Questions

---

## 4-Mark Q1. Explain the geometric interpretation of least squares.

### Answer

The columns of \(A\) span the column space:

\[
\mathrm{Col}(A)
\]

Every vector \(Ax\) lies in this space. If \(b\) is not in the column space, the equation:

\[
Ax=b
\]

has no exact solution.

Least squares finds the point in \(\mathrm{Col}(A)\) closest to \(b\):

\[
\boxed{A\hat{x}=\mathrm{proj}_{\mathrm{Col}(A)}(b)}
\]

The residual:

\[
r=b-A\hat{x}
\]

is perpendicular to the column space.

---

## 4-Mark Q2. Explain SSE, MSE and RMSE.

### Answer

### SSE

\[
\boxed{SSE=\sum_i(y_i-\hat y_i)^2}
\]

It is the total squared error.

### MSE

\[
\boxed{MSE=\frac{SSE}{m}}
\]

It is the average squared error.

### RMSE

\[
\boxed{RMSE=\sqrt{MSE}}
\]

It is the square root of the mean squared error and has the same units as the response variable.

---

## 4-Mark Q3. Explain the role of the design matrix in simple linear regression.

### Answer

For:

\[
y=\beta_0+\beta_1x+\epsilon
\]

the design matrix is:

\[
X=
\begin{bmatrix}
1&x_1\\
1&x_2\\
\vdots&\vdots\\
1&x_m
\end{bmatrix}
\]

It allows the model to be written compactly as:

\[
\boxed{y=X\beta+\epsilon}
\]

The first column of ones represents the intercept, while the second column contains the predictor values.

After estimating \(\hat\beta\):

\[
\boxed{\hat y=X\hat\beta}
\]

---

## 4-Mark Q4. Explain QR decomposition in least squares.

### Answer

QR decomposition expresses the design matrix as:

\[
\boxed{X=QR}
\]

Instead of solving least squares through normal equations, the problem can be reduced to:

\[
\boxed{R\hat\beta=Q^Ty}
\]

QR decomposition is often preferred because it provides better numerical stability than explicitly forming the normal equations.

---

## 4-Mark Q5. Explain polynomial regression and why it is still a linear model.

### Answer

A quadratic model is:

\[
y=\beta_0+\beta_1x+\beta_2x^2+\epsilon
\]

Its design matrix contains:

\[
1,\quad x,\quad x^2
\]

Although the model is nonlinear as a function of \(x\), it is linear in the unknown parameters:

\[
\beta_0,\beta_1,\beta_2
\]

Therefore, least squares can be used to estimate these parameters.

---

# 29. Exam-Style 5-Mark Questions

---

## 5-Mark Q1. Derive the normal equations.

### Answer

Consider the least-squares objective:

\[
J(\beta)=\|y-X\beta\|^2
\]

Writing it using transpose:

\[
J(\beta)=(y-X\beta)^T(y-X\beta)
\]

Differentiate with respect to \(\beta\):

\[
\nabla_\beta J=-2X^T(y-X\beta)
\]

At the minimum:

\[
\nabla_\beta J=0
\]

Therefore:

\[
X^T(y-X\hat\beta)=0
\]

Expanding:

\[
X^Ty-X^TX\hat\beta=0
\]

Hence:

\[
\boxed{X^TX\hat\beta=X^Ty}
\]

These are the normal equations.

If \(X\) has linearly independent columns:

\[
\boxed{\hat\beta=(X^TX)^{-1}X^Ty}
\]

---

## 5-Mark Q2. Explain least squares using orthogonal projection.

### Answer

For the system:

\[
Ax=b
\]

every vector \(Ax\) belongs to the column space of \(A\).

If:

\[
b\notin\mathrm{Col}(A)
\]

then no exact solution exists.

Least squares finds the point in the column space closest to \(b\):

\[
\boxed{A\hat{x}=\mathrm{proj}_{\mathrm{Col}(A)}(b)}
\]

The residual is:

\[
r=b-A\hat{x}
\]

At the optimum, the residual is orthogonal to the column space:

\[
\boxed{A^Tr=0}
\]

Therefore:

\[
A^T(b-A\hat{x})=0
\]

which leads to:

\[
\boxed{A^TA\hat{x}=A^Tb}
\]

Thus, geometric projection and the normal equations describe the same least-squares solution from two different viewpoints.

---

## 5-Mark Q3. Explain ordinary least squares, QR and SVD approaches.

### Answer

The least-squares problem is:

\[
\min_\beta\|y-X\beta\|^2
\]

### Normal equations

They are:

\[
\boxed{X^TX\hat\beta=X^Ty}
\]

and, when the columns are independent:

\[
\boxed{\hat\beta=(X^TX)^{-1}X^Ty}
\]

### QR decomposition

Write:

\[
X=QR
\]

Then solve:

\[
\boxed{R\hat\beta=Q^Ty}
\]

QR is often preferable for numerical stability.

### SVD

Write:

\[
X=U\Sigma V^T
\]

The pseudoinverse is:

\[
X^+=V\Sigma^+U^T
\]

and:

\[
\boxed{\hat\beta=X^+y}
\]

SVD is especially useful for rank-deficient or nearly rank-deficient matrices.

---

## 5-Mark Q4. Explain SSE, MSE, RMSE and \(R^2\).

### Answer

### SSE

\[
\boxed{SSE=\sum_i(y_i-\hat y_i)^2}
\]

It measures total squared error.

### MSE

\[
\boxed{MSE=\frac{SSE}{m}}
\]

It measures average squared error.

### RMSE

\[
\boxed{RMSE=\sqrt{MSE}}
\]

It is in the same units as the response variable.

### \(R^2\)

\[
\boxed{R^2=1-\frac{SSE}{SST}}
\]

where:

\[
\boxed{SST=\sum_i(y_i-\bar y)^2}
\]

A high \(R^2\) indicates a strong in-sample fit according to this measure, but it does not prove causation or guarantee good performance on new data.

---

# 30. Mixed Exam Practice — Try Before Looking at Answers

## 3 Marks

### Q1
What is the difference between \(Ax=b\) and \(Ax\approx b\) in the context of least squares?

### Q2
Write the formula for the residual vector.

### Q3
What is the role of the column of ones in a design matrix?

### Q4
State the formula for RMSE.

---

## 4 Marks

### Q5
Explain why the least-squares residual is orthogonal to the column space.

### Q6
Explain the difference between ordinary linear regression and multiple linear regression.

### Q7
Explain why polynomial regression is linear in parameters.

### Q8
Explain multicollinearity and give one mathematical example.

---

## 5 Marks

### Q9
Derive the normal equations starting from:

\[
J(\beta)=\|y-X\beta\|^2
\]

### Q10
Explain the geometric interpretation of least squares and connect it to the normal equations.

### Q11
Explain the role of QR and SVD in numerical least squares.

### Q12
Explain weighted least squares and derive its normal equations.

---

# 31. Answers to Mixed Exam Practice

## Answer 1

\(Ax=b\) asks for an exact solution.

\(Ax\approx b\) accepts an approximate solution because the observations may be inconsistent.

Least squares finds the approximate solution that minimizes:

\[
\boxed{\|Ax-b\|^2}
\]

---

## Answer 2

\[
\boxed{r=b-A\hat{x}}
\]

For scalar observations:

\[
\boxed{e_i=y_i-\hat y_i}
\]

---

## Answer 3

The column of ones represents the intercept term.

For:

\[
y=\beta_0+\beta_1x+\epsilon
\]

the design matrix contains:

\[
[1,\ x_i]
\]

so that the first column multiplies \(\beta_0\).

---

## Answer 4

\[
\boxed{RMSE=\sqrt{MSE}}
\]

or:

\[
\boxed{RMSE=\sqrt{\frac{SSE}{m}}}
\]

---

## Answer 5

At the least-squares solution:

\[
A^T(b-A\hat{x})=0
\]

Since:

\[
r=b-A\hat{x}
\]

we have:

\[
\boxed{A^Tr=0}
\]

Therefore, the residual is orthogonal to every column of \(A\), and hence to the column space of \(A\).

---

## Answer 6

Simple linear regression has one predictor:

\[
y=\beta_0+\beta_1x+\epsilon
\]

Multiple linear regression has several predictors:

\[
y=\beta_0+\beta_1x_1+\cdots+\beta_px_p+\epsilon
\]

Both can be written in the matrix form:

\[
\boxed{y=X\beta+\epsilon}
\]

and fitted using least squares.

---

## Answer 7

A polynomial model such as:

\[
y=\beta_0+\beta_1x+\beta_2x^2+\epsilon
\]

is nonlinear in \(x\), but the unknown parameters occur linearly:

\[
\beta_0,\beta_1,\beta_2
\]

Therefore, it is linear in its parameters and can be fitted using least squares.

---

## Answer 8

Multicollinearity occurs when predictors are nearly linearly dependent.

For example:

\[
x_2\approx2x_1
\]

This can make the problem ill-conditioned and can cause unstable coefficients that are sensitive to small changes in the data.

---

## Answer 9

Start with:

\[
J(\beta)=\|y-X\beta\|^2
\]

Write:

\[
J(\beta)=(y-X\beta)^T(y-X\beta)
\]

Differentiate:

\[
\nabla_\beta J=-2X^T(y-X\beta)
\]

At the minimum:

\[
X^T(y-X\hat\beta)=0
\]

Therefore:

\[
X^Ty-X^TX\hat\beta=0
\]

Hence:

\[
\boxed{X^TX\hat\beta=X^Ty}
\]

---

## Answer 10

The columns of \(X\) form the column space \(\mathrm{Col}(X)\).

The vector \(X\beta\) must lie in this space. If \(y\) does not lie in the space, the exact equation cannot be satisfied.

Least squares chooses the point in the column space closest to \(y\):

\[
\boxed{X\hat\beta=\mathrm{proj}_{\mathrm{Col}(X)}(y)}
\]

The residual:

\[
e=y-X\hat\beta
\]

is orthogonal to the column space:

\[
X^Te=0
\]

Therefore:

\[
X^T(y-X\hat\beta)=0
\]

which gives:

\[
\boxed{X^TX\hat\beta=X^Ty}
\]

---

## Answer 11

QR decomposition represents:

\[
X=QR
\]

and leads to:

\[
\boxed{R\hat\beta=Q^Ty}
\]

It is often preferable to forming normal equations because of numerical stability.

SVD represents:

\[
X=U\Sigma V^T
\]

and gives the pseudoinverse:

\[
X^+=V\Sigma^+U^T
\]

so that:

\[
\boxed{\hat\beta=X^+y}
\]

SVD is especially useful for rank-deficient or nearly rank-deficient matrices.

---

## Answer 12

Weighted least squares is used when observations have different reliability.

It minimizes:

\[
\boxed{
\sum_iw_i(y_i-\hat y_i)^2
}
\]

In matrix form, the objective is:

\[
(y-X\beta)^TW(y-X\beta)
\]

Differentiating and setting the gradient to zero gives the weighted normal equations:

\[
\boxed{
X^TWX\hat\beta=X^TWy
}
\]

---

# 32. High-Priority Exam Revision List

Before the exam, make sure you can explain all of these without looking at notes:

### Core concepts

- Overdetermined system
- Approximate solution
- Residual
- SSE
- MSE
- RMSE
- Column space
- Orthogonal projection
- Orthogonality of residual
- Normal equations
- Linear model
- Intercept
- Slope
- Design matrix
- Multiple linear model
- Polynomial model
- Basis functions
- Projection matrix
- \(R^2\)
- QR decomposition
- SVD
- Pseudoinverse
- Rank
- Multicollinearity
- Weighted least squares

### Core formulas

\[
\boxed{\min_x\|Ax-b\|^2}
\]

\[
\boxed{r=b-A\hat{x}}
\]

\[
\boxed{A^Tr=0}
\]

\[
\boxed{A^TA\hat{x}=A^Tb}
\]

\[
\boxed{\hat{x}=(A^TA)^{-1}A^Tb}
\]

\[
\boxed{y=X\beta+\epsilon}
\]

\[
\boxed{\hat y=X\hat\beta}
\]

\[
\boxed{SSE=\sum_i(y_i-\hat y_i)^2}
\]

\[
\boxed{MSE=\frac{SSE}{m}}
\]

\[
\boxed{RMSE=\sqrt{MSE}}
\]

\[
\boxed{R^2=1-\frac{SSE}{SST}}
\]

\[
\boxed{P=X(X^TX)^{-1}X^T}
\]

\[
\boxed{X=QR}
\]

\[
\boxed{R\hat\beta=Q^Ty}
\]

\[
\boxed{X=U\Sigma V^T}
\]

\[
\boxed{X^+=V\Sigma^+U^T}
\]

\[
\boxed{\hat\beta=X^+y}
\]

\[
\boxed{X^TWX\hat\beta=X^TWy}
\]

---

# 33. Final One-Page Mental Revision

Think of the entire chapter like this:

### Problem

Real observations are noisy, so:

\[
Ax=b
\]

may have no exact solution.

### Solution

Use least squares:

\[
\boxed{\min_x\|Ax-b\|^2}
\]

### Error

\[
\boxed{r=b-A\hat{x}}
\]

### Geometry

Find the closest point in the column space:

\[
\boxed{A\hat{x}=\mathrm{proj}_{\mathrm{Col}(A)}(b)}
\]

### Orthogonality

\[
\boxed{A^Tr=0}
\]

### Normal equations

\[
\boxed{A^TA\hat{x}=A^Tb}
\]

### Linear regression

\[
\boxed{y=X\beta+\epsilon}
\]

### Prediction

\[
\boxed{\hat y=X\hat\beta}
\]

### Error measures

\[
\boxed{SSE,\ MSE,\ RMSE}
\]

### Fit measure

\[
\boxed{R^2=1-\frac{SSE}{SST}}
\]

### Numerical methods

\[
\boxed{\text{Normal Equations}\quad\rightarrow\quad\text{QR}\quad\rightarrow\quad\text{SVD}}
\]

with QR useful for numerical stability and SVD particularly useful for rank-deficient or nearly rank-deficient problems.

### Overall chain

\[
\boxed{
\text{Linear Model}
\rightarrow
\text{Least Squares}
\rightarrow
\text{Projection}
\rightarrow
\text{Orthogonality}
\rightarrow
\text{Normal Equations}
}
\]

---

# 34. Exam Answer-Writing Strategy

For a **3-mark question**:

1. Give the definition.
2. Write the main formula.
3. Add one important interpretation.

For a **4-mark question**:

1. Define the concept.
2. Write the formula.
3. Explain the meaning.
4. Give a small example or consequence.

For a **5-mark question**:

1. Start with the objective/problem.
2. Show the important equations step by step.
3. Explain what each step means.
4. End with the final boxed result.
5. Add the geometric or practical interpretation when relevant.

### Most important advice

Do not only memorize:

\[
A^TA\hat{x}=A^Tb
\]

Understand the chain:

\[
\boxed{
\text{Minimize squared error}
\rightarrow
\text{Residual}
\rightarrow
\text{Orthogonality}
\rightarrow
\text{Normal Equations}
}
\]

That connection is the central idea of this topic.
