# 📘 Mathematics for IT — Unit 1: Linear Algebra and Matrix Theory
### Complete Consolidated Notes with Worked Examples, Solved Exercises & Extra Conceptual Questions
**Course:** M.Tech. 1st Semester, IIIT Allahabad | **Instructor:** Dr. Mohammed Javed
**Reference:** Gilbert Strang, *Linear Algebra and Its Applications*, MIT Press (and course AI-generated material)

---

## Table of Contents

1. Systems of Linear Equations
2. Matrix Operations and Matrix Inverses
3. Determinants and Their Properties, Rank of a Matrix
4. Row Reduction and Echelon Forms
5. Linear Dependence/Independence, Vector Spaces, Subspaces, Basis, Dimension
6. Orthogonality and Projections, Gram–Schmidt
7. Least Squares Problems and Linear Models
8. Linear Algebra Applications in IT and Data Representation
9. Solved Exercises (from every topic)
10. Extra Important Conceptual Questions — with Solutions
11. Master Formula Sheet
12. References

---

# 1. Systems of Linear Equations

### 1.1 Definition
A **system of linear equations** is a collection of ≥2 linear equations in the same variables. A **solution** satisfies all equations simultaneously. For two variables:
$$a_1x+b_1y=c_1,\qquad a_2x+b_2y=c_2$$

### 1.2 Types of Systems

| Type | Graph | # Solutions | Rank condition |
|---|---|---|---|
| Consistent, independent | Intersecting lines | One | rank(A) = rank([A\|b]) = n |
| Inconsistent | Parallel lines | None | rank(A) < rank([A\|b]) |
| Consistent, dependent | Coincident lines | Infinite | rank(A) = rank([A\|b]) < n |

**Rule of thumb:** One intersection → one solution; parallel → none; same line → infinite.

### 1.3 Matrix Form
$$A\mathbf{x}=\mathbf{b}, \qquad \begin{bmatrix}a_1&b_1\\a_2&b_2\end{bmatrix}\begin{bmatrix}x\\y\end{bmatrix}=\begin{bmatrix}c_1\\c_2\end{bmatrix}$$
Square system: unique solution iff $\det(A)\neq0$.

### 1.4 Methods of Solving
- **Graphical** — plot lines, find intersection.
- **Substitution** — solve one variable, substitute.
- **Elimination** — add/subtract to cancel a variable.
- **Gaussian elimination** — row-reduce augmented matrix.
- **Inverse matrix** — $\mathbf{x}=A^{-1}\mathbf{b}$ (square, invertible A).

### 1.5 Worked Examples

**Example 1 (Unique solution).** Solve $x+y=3,\ x-y=-1$.
Add: $2x=2\Rightarrow x=1$; substitute: $1+y=3\Rightarrow y=2$.
**Solution:** $(x,y)=(1,2)$.

**Example 2 (No solution).** $y=2x+1,\ y=2x-3$. Same slope (2), different intercepts → parallel → subtracting gives $4=0$ (impossible). **Solution:** $\varnothing$.

**Example 3 (Infinite solutions).** $y=2x+1,\ 2y=4x+2$. Divide 2nd by 2: $y=2x+1$ — identical equations. **Solution:** $\{(x,y): y=2x+1\}$.

**Example 4 (Elimination).** Solve $2x+3y=13,\ x-y=1$.
Multiply 2nd by 3: $3x-3y=3$. Add to 1st: $5x=16\Rightarrow x=16/5$. Then $y=x-1=11/5$.
**Solution:** $(16/5,\ 11/5)=(3.2,\ 2.2)$.

### 1.6 Python
```python
import numpy as np
A = np.array([[2,3],[1,-1]], dtype=float); b=np.array([13,1],dtype=float)
x = np.linalg.solve(A,b)          # unique-solution case
# Singular case → check rank(A) vs rank([A|b]) to decide none/infinite
```

### 1.7 Key Takeaway
A singular coefficient matrix ($\det A=0$) does **not** automatically mean no solution — it may mean infinitely many; check the rank of $A$ vs. $[A|b]$.

---
# 2. Matrix Operations and Matrix Inverses

### 2.1 Matrix Basics
A matrix is a rectangular array; shape $m\times n$. Types: row, column, square, zero, identity ($I$, with $AI=IA=A$).

### 2.2 Operations
- **Addition/Subtraction:** element-wise, same shape required.
- **Scalar multiplication:** multiply every entry.
- **Matrix multiplication:** $A_{m\times n}B_{n\times q}=C_{m\times q}$ (inner dimensions must match). **Not commutative** ($AB\neq BA$ generally); **associative** and **distributive**.
- **Element-wise vs. matrix product (NumPy):** `A*B` (Hadamard) vs. `A@B` (matrix product).
- **Transpose** $A^T$: swap rows/columns. Property: $(AB)^T=B^TA^T$.
- **Trace:** sum of diagonal entries (square matrices only).

### 2.3 Determinant (2×2)
$$\det\begin{bmatrix}a&b\\c&d\end{bmatrix}=ad-bc$$
$A$ invertible $\iff \det(A)\neq 0$.

### 2.4 Matrix Inverse
$A^{-1}$ satisfies $AA^{-1}=A^{-1}A=I$. For 2×2, $ad-bc\neq0$:
$$A^{-1}=\frac{1}{ad-bc}\begin{bmatrix}d&-b\\-c&a\end{bmatrix}$$

**Gauss–Jordan method:** row-reduce $[A\mid I]\to[I\mid A^{-1}]$.

### 2.5 Inverse Properties
$$(A^{-1})^{-1}=A,\quad (AB)^{-1}=B^{-1}A^{-1},\quad (A^T)^{-1}=(A^{-1})^T,\quad I^{-1}=I,\quad \det(A^{-1})=\frac{1}{\det A}$$

### 2.6 Worked Examples

**Example 1.** $A=\begin{bmatrix}2&1\\3&4\end{bmatrix}$. $\det A = 2(4)-1(3)=5\neq0\Rightarrow$ invertible.
$$A^{-1}=\frac15\begin{bmatrix}4&-1\\-3&2\end{bmatrix}=\begin{bmatrix}0.8&-0.2\\-0.6&0.4\end{bmatrix}$$

**Example 2 (solve system via inverse).** $2x+y=5,\ x+3y=6\Rightarrow A=\begin{bmatrix}2&1\\1&3\end{bmatrix},\ b=\begin{bmatrix}5\\6\end{bmatrix}$.
$\det A=5$; $A^{-1}=\frac15\begin{bmatrix}3&-1\\-1&2\end{bmatrix}$.
$x=A^{-1}b=\frac15\begin{bmatrix}3(5)-1(6)\\-1(5)+2(6)\end{bmatrix}=\frac15\begin{bmatrix}9\\7\end{bmatrix}=\begin{bmatrix}1.8\\1.4\end{bmatrix}$.

**Example 3 (singular check).** $B=\begin{bmatrix}1&2\\2&4\end{bmatrix}$: $\det B=1(4)-2(2)=0$ → singular, **no inverse** (rows/cols are dependent, $R_2=2R_1$).

### 2.7 Python
```python
import numpy as np
A = np.array([[2,1],[3,4]], dtype=float)
np.linalg.det(A); np.linalg.inv(A); np.linalg.solve(A,b)   # prefer solve() over inv()@b
```

### 2.8 Applications
Computer graphics (transformations), image filtering, ML models ($Y=XW+b$), network adjacency matrices, embeddings (Transformer attention uses linear maps — *Attention Is All You Need*).

---

# 3. Determinants and Their Properties, Rank of a Matrix

### 3.1 Determinant — Definitions
- 2×2: $\det(A)=ad-bc$.
- 3×3 (cofactor expansion along row 1):
$$\det(A)=a(ei-fh)-b(di-fg)+c(dh-eg)$$
- Triangular matrix: $\det(A)=\prod_i a_{ii}$ (product of diagonal entries).
- **Minor** $M_{ij}$: determinant after deleting row $i$, column $j$. **Cofactor** $C_{ij}=(-1)^{i+j}M_{ij}$.

### 3.2 Geometric Meaning
$|\det(A)|$ = area (2D) / volume (3D) scaling factor of the unit square/cube under the transformation $A$. Negative sign ⇒ orientation reversed. $\det(A)=0$ ⇒ transformation collapses dimension.

### 3.3 Key Properties
$$\det(I)=1,\quad \det(A^T)=\det(A),\quad \det(AB)=\det(A)\det(B),\quad \det(A^{-1})=\frac1{\det A},\quad \det(cA)=c^n\det(A)$$
Row swap → sign flips; row scale by $c$ → det scales by $c$; row replacement ($R_i\leftarrow R_i+cR_j$) → det unchanged.

### 3.4 Singular vs Nonsingular
$\det(A)=0\Rightarrow$ singular (not invertible, dependent columns, nontrivial null space).
$\det(A)\neq0\Rightarrow$ nonsingular (invertible, independent columns).

### 3.5 Rank
**Rank** = max number of linearly independent rows/columns = $\dim(\text{Col}(A))=\dim(\text{Row}(A))$ (row rank = column rank). Equals the number of pivots in RREF.

Special cases: $\text{rank}(0)=0$; $\text{rank}(I_n)=n$; for $m\times n$ matrix, $\text{rank}(A)\le\min(m,n)$.

### 3.6 Determinant–Rank–Invertibility (n×n matrix)
$$\boxed{\det(A)\ne0 \iff \text{rank}(A)=n \iff A^{-1}\text{ exists} \iff \text{columns independent}}$$

### 3.7 Rank–Nullity Theorem
$$\text{rank}(A)+\text{nullity}(A)=n\ (\text{number of columns})$$

### 3.8 Rank and Linear Systems ($Ax=b$)
| Condition | Type |
|---|---|
| rank(A)=rank([A\|b])=n | Unique solution |
| rank(A)=rank([A\|b])<n | Infinite solutions |
| rank(A)<rank([A\|b]) | No solution |

### 3.9 Worked Examples

**Example 1 (3×3 determinant).** $A=\begin{bmatrix}1&2&3\\0&4&5\\1&0&6\end{bmatrix}$.
$\det A = 1(4\cdot6-5\cdot0) - 2(0\cdot6-5\cdot1) + 3(0\cdot0-4\cdot1)=1(24)-2(-5)+3(-4)=24+10-12=22$.
*(Recomputed carefully: $24+10-12=22$.)*

**Example 2 (rank via row reduction).** $A=\begin{bmatrix}1&2&3\\2&4&6\\1&1&2\end{bmatrix}$. $R_2\leftarrow R_2-2R_1$ gives zero row; RREF has 2 pivot rows ⇒ **rank = 2**.

**Example 3 (rank 1).** $A=\begin{bmatrix}2&4\\1&2\end{bmatrix}$: column 2 = 2×column 1 ⇒ dependent ⇒ **rank = 1**.

### 3.10 Python
```python
np.linalg.det(A); np.linalg.matrix_rank(A); np.linalg.svd(A, compute_uv=False)  # singular values
```

---
# 4. Row Reduction and Echelon Forms

### 4.1 Elementary Row Operations
1. **Row replacement:** $R_i\leftarrow R_i+cR_j$
2. **Row interchange:** $R_i\leftrightarrow R_j$
3. **Row scaling:** $R_i\leftarrow cR_i,\ c\neq0$

These preserve the solution set of a linear system.

### 4.2 Pivots, REF, RREF
**Leading entry** = first nonzero entry of a row; used as pivot during elimination.

**Row Echelon Form (REF):** zero rows at bottom; each pivot right of the one above; zeros below each pivot.

**Reduced REF (RREF):** REF + every pivot = 1 + pivot is the only nonzero entry in its column. RREF is **unique**; REF is not.

| Feature | REF | RREF |
|---|---|---|
| Zero rows at bottom | ✔ | ✔ |
| Pivots move right | ✔ | ✔ |
| Zeros below pivot | ✔ | ✔ |
| Pivots = 1 | ✗ | ✔ |
| Zeros above pivot | ✗ | ✔ |

### 4.3 Gaussian vs Gauss–Jordan Elimination
- **Gaussian elimination:** reduce to REF, then **back-substitute**.
- **Gauss–Jordan elimination:** reduce all the way to RREF — solution read off directly.

### 4.4 Worked Example
Solve $x+2y-z=3,\ 2x+5y+z=8,\ -x+y+2z=1$.

Augmented matrix → $R_2\leftarrow R_2-2R_1,\ R_3\leftarrow R_3+R_1$:
$$\begin{bmatrix}1&2&-1&|&3\\0&1&3&|&2\\0&3&1&|&4\end{bmatrix}$$
$R_3\leftarrow R_3-3R_2$:
$$\begin{bmatrix}1&2&-1&|&3\\0&1&3&|&2\\0&0&-8&|&-2\end{bmatrix}$$
Back-substitute: $-8z=-2\Rightarrow z=1/4$; $y+3(1/4)=2\Rightarrow y=5/4$; $x+2(5/4)-1/4=3\Rightarrow x=1/2$.
**Solution:** $(x,y,z)=(1/2,\ 5/4,\ 1/4)$.

### 4.5 Pivot vs Free Variables
$$\begin{bmatrix}1&0&2&|&5\\0&1&-1&|&3\\0&0&0&|&0\end{bmatrix}$$
Columns 1,2 have pivots → $x_1,x_2$ pivot variables; column 3 is free → $x_3=t$.
$x_1=5-2t,\ x_2=3+t$. **General solution:** $(5-2t,\ 3+t,\ t)$.

### 4.6 Consistency Table
| Row-reduction result | Conclusion |
|---|---|
| Pivot in every variable column, no contradiction | Unique solution |
| Free variable(s), no contradiction | Infinite solutions |
| Contradiction row $[0\ 0\ \cdots\ 0\mid b],\ b\neq0$ | No solution |

### 4.7 Python
```python
def rref(matrix, tol=1e-12):
    A=[list(map(float,r)) for r in matrix]; rows,cols=len(A),len(A[0]); pr=0; piv=[]
    for c in range(cols):
        if pr>=rows: break
        br=max(range(pr,rows), key=lambda r: abs(A[r][c]))
        if abs(A[br][c])<tol: continue
        A[pr],A[br]=A[br],A[pr]; A[pr]=[x/A[pr][c] for x in A[pr]]
        for r in range(rows):
            if r!=pr and abs(A[r][c])>tol:
                A[r]=[A[r][k]-A[r][c]*A[pr][k] for k in range(cols)]
        piv.append(c); pr+=1
    return A, piv
```

---

# 5. Linear Dependence/Independence, Vector Spaces, Subspaces, Basis, Dimension

### 5.1 Linear Combination & Span
A linear combination: $c_1v_1+c_2v_2+\cdots+c_kv_k$. The **span** is the set of *all* linear combinations of a vector set — a line (1 vector), plane (2 independent vectors in $\mathbb{R}^3$), etc.

### 5.2 Linear Dependence / Independence
**Dependent:** $\exists\, c_i$ not all zero with $c_1v_1+\cdots+c_kv_k=0$ (redundant vector exists).
**Independent:** the *only* solution is $c_1=\cdots=c_k=0$.

**Test:** stack vectors as columns of $A$; independent $\iff \text{rank}(A)=$ (number of vectors) $\iff$ (square case) $\det(A)\neq0$.

**Key facts:**
- Any set containing $\mathbf 0$ is dependent.
- >$n$ vectors in $\mathbb{R}^n$ must be dependent.
- Removing a vector from an independent set keeps it independent; adding one may break independence.

### 5.3 Vector Spaces
A set with **addition** + **scalar multiplication** obeying closure, commutativity, associativity, zero vector, additive inverses, scalar identity, distributivity. Examples: $\mathbb{R}^n$, polynomials $P_n$, $m\times n$ matrices, function spaces.

### 5.4 Subspaces
A subset $W\subseteq V$ is a subspace iff:
1. $u+v\in W$ for all $u,v\in W$ (closed under addition)
2. $cu\in W$ for all scalars $c$ (closed under scalar mult.)

**Quick test:** a subspace must contain $\mathbf 0$. (E.g. line $x+y=1$ is **not** a subspace — doesn't pass through origin.)

Important subspaces of a matrix $A$: **Null space** $N(A)=\{x:Ax=0\}$; **Column space** $\text{Col}(A)=$ span of columns; **Row space**.

### 5.5 Basis & Dimension
**Basis** = linearly independent set that spans $V$. $\text{Basis}=\text{Spanning}+\text{Independence}$.
**Dimension** = number of vectors in any basis (well-defined — every basis of a finite-dim space has the same size).
$\dim(\mathbb{R}^2)=2,\ \dim(\mathbb{R}^3)=3$; plane through origin in $\mathbb{R}^3$ has dim 2; line has dim 1; $\{0\}$ has dim 0.

$$\text{rank}(A)=\dim(\text{Col}(A))=\dim(\text{Row}(A)),\qquad \text{rank}(A)+\text{nullity}(A)=n$$

### 5.6 Coordinates Relative to a Basis
If $v=c_1b_1+c_2b_2$, coordinates $[v]_B=(c_1,c_2)$ solve $B\mathbf{c}=v$ where $B=[b_1\ b_2]$.

### 5.7 Worked Examples

**Example 1 (dependence test).** $v_1=(1,2),\ v_2=(2,4)$: $v_2=2v_1\Rightarrow 2v_1-v_2=0$ (nonzero coeffs) → **dependent**.

**Example 2 (coordinates).** Basis $b_1=(1,1),b_2=(1,-1)$; $v=(3,1)$.
$c_1+c_2=3,\ c_1-c_2=1\Rightarrow c_1=2,c_2=1$. $[v]_B=(2,1)$.

**Example 3 (subspace).** $W=\{(x,y,z):x+y+z=0\}\subset\mathbb{R}^3$. Since $z=-x-y$: $W=\text{span}\{(1,0,-1),(0,1,-1)\}$ → subspace of dimension 2.

**Example 4 (basis extraction).** $v_1=(1,2,3),v_2=(2,4,6)=2v_1,v_3=(1,0,1)$. $v_2$ redundant → basis $\{v_1,v_3\}$, span has dimension 2.

### 5.8 Python
```python
np.linalg.matrix_rank(np.column_stack([v1,v2]))  # == #vectors -> independent
sp.Matrix(A).nullspace(); sp.Matrix(A).rref()      # SymPy: null space, pivot columns
```

---
# 6. Orthogonality and Projections, Gram–Schmidt

### 6.1 Dot Product & Orthogonality
$$u\cdot v=u^Tv=u_1v_1+\cdots+u_nv_n$$
$u\perp v \iff u^Tv=0$. Works in any $\mathbb{R}^n$, not just 2D.

### 6.2 Norm & Unit Vectors
$$\|v\|=\sqrt{v^Tv},\qquad \hat v=\frac{v}{\|v\|}\ (\text{unit vector, }\|\hat v\|=1)$$

### 6.3 Orthogonal vs Orthonormal
**Orthogonal set:** pairwise dot products = 0. **Orthonormal set:** orthogonal + every vector unit length ($q_i^Tq_j=\delta_{ij}$). If $Q$'s columns are orthonormal: $Q^TQ=I$.

### 6.4 Orthogonal Basis — Easy Coordinates
If $\{q_1,\ldots,q_n\}$ orthogonal basis, $x=\sum c_jq_j$ with
$$\boxed{c_j=\dfrac{q_j^Tx}{q_j^Tq_j}}\quad\text{(orthonormal: } c_j=q_j^Tx\text{)}$$

### 6.5 Projection onto a Vector
$$\boxed{\text{proj}_a(x)=\dfrac{x^Ta}{a^Ta}\,a}$$
Residual $r=x-\text{proj}_a(x)$ is orthogonal to $a$ ($a^Tr=0$); decomposition $x=\text{proj}_a(x)+r$.

### 6.6 Projection onto a Subspace
- Orthonormal basis $Q$: $\text{proj}_W(x)=QQ^Tx$, projection matrix $P=QQ^T$ ($P^2=P$, $P^T=P$ — idempotent & symmetric).
- General (independent, not necessarily orthonormal) basis $A$: $P=A(A^TA)^{-1}A^T$.

### 6.7 Gram–Schmidt Process
Given independent $v_1,\ldots,v_k$, build orthogonal $u_1,\ldots,u_k$:
$$u_1=v_1,\qquad u_j=v_j-\sum_{i=1}^{j-1}\text{proj}_{u_i}(v_j)\ (j\ge2)$$
Normalize: $q_j=u_j/\|u_j\|$ → orthonormal basis. Relates to **QR decomposition**: $A=QR$ ($Q$ orthonormal columns, $R$ upper triangular).

### 6.8 Least Squares Link
Least-squares solution $\hat b=\text{proj}_{\text{Col}(A)}(b)$; residual $r=b-\hat b\perp\text{Col}(A)\Rightarrow A^Tr=0\Rightarrow A^TA\hat x=A^Tb$ (normal equations).

### 6.9 Worked Examples

**Example 1 (orthogonality check).** $u=(3,1),v=(-1,3)$: $u^Tv=3(-1)+1(3)=0$ → orthogonal. ✔

**Example 2 (projection).** $x=(3,4),a=(2,0)$: $x^Ta=6,\ a^Ta=4\Rightarrow \text{proj}_a(x)=\frac64(2,0)=(3,0)$.

**Example 3 (Gram–Schmidt).** $v_1=(3,1),v_2=(2,3)$.
$u_1=(3,1)$. $v_2^Tu_1=9,\ u_1^Tu_1=10\Rightarrow \text{proj}=\frac{9}{10}(3,1)=(2.7,0.9)$.
$u_2=(2,3)-(2.7,0.9)=(-0.7,\,2.1)$. Check: $u_1^Tu_2=3(-0.7)+1(2.1)=0$ ✔ orthogonal.
Normalize: $\|u_1\|=\sqrt{10}\Rightarrow q_1=\frac1{\sqrt{10}}(3,1)$; $\|u_2\|=\sqrt{0.49+4.41}=\sqrt{4.9}\Rightarrow q_2=\frac1{\sqrt{4.9}}(-0.7,2.1)$.

### 6.10 Python
```python
Q,R = np.linalg.qr(A)              # Gram-Schmidt via QR
P = Q @ Q.T                        # projection matrix (orthonormal cols)
proj = (np.dot(x,a)/np.dot(a,a))*a # projection onto a vector
```

---

# 7. Least Squares Problems and Linear Models

### 7.1 Why Least Squares?
Noisy/overdetermined systems ($A$ has more rows than columns) usually have **no exact solution**. Least squares finds $\hat x$ minimizing
$$\boxed{\min_x\|Ax-b\|^2}$$

### 7.2 Residual & Error Measures
$$r=b-A\hat x,\qquad SSE=\sum_i(y_i-\hat y_i)^2,\qquad MSE=\frac{SSE}{m},\qquad RMSE=\sqrt{MSE}$$
$$R^2 = 1-\frac{SSE}{SST},\qquad SST=\sum_i(y_i-\bar y)^2$$

### 7.3 Normal Equations (Derivation)
Residual $\perp$ Col($A$): $A^T(b-A\hat x)=0 \Rightarrow \boxed{A^TA\hat x=A^Tb}$.
If $A^TA$ invertible: $\boxed{\hat x=(A^TA)^{-1}A^Tb}$ (numerically, prefer `lstsq`, QR, or SVD over explicit inverse).

### 7.4 Design Matrix & Linear Models
Simple model $y=\beta_0+\beta_1x+\epsilon$: design matrix $X=\begin{bmatrix}1&x_1\\ \vdots&\vdots\\1&x_m\end{bmatrix}$; $y=X\beta+\epsilon$, fitted $\hat y=X\hat\beta$.
**Multiple regression:** $y=\beta_0+\beta_1x_1+\cdots+\beta_px_p+\epsilon$.
**Polynomial regression:** nonlinear in $x$, but **linear in parameters** $\beta$.

### 7.5 Projection Matrix
$$P=X(X^TX)^{-1}X^T,\qquad \hat y=Py,\qquad P^2=P,\ P^T=P$$

### 7.6 QR & SVD Alternatives
$$X=QR\Rightarrow R\hat\beta=Q^Ty \qquad\qquad X=U\Sigma V^T\Rightarrow \hat\beta=X^+y=V\Sigma^+U^Ty$$
SVD/pseudoinverse handle rank-deficient (multicollinear) $X$.

### 7.7 Worked Example
$A=\begin{bmatrix}1&1\\1&2\\1&3\end{bmatrix},\ b=\begin{bmatrix}2\\2.8\\4.2\end{bmatrix}$.

$A^TA=\begin{bmatrix}3&6\\6&14\end{bmatrix}$ (sums: $\sum1=3,\sum x=6,\sum x^2=14$), $A^Tb=\begin{bmatrix}9\\20.2\end{bmatrix}$ (sums: $\sum b=9,\ \sum xb=2+5.6+12.6=20.2$).

Solve $\begin{bmatrix}3&6\\6&14\end{bmatrix}\hat x=\begin{bmatrix}9\\20.2\end{bmatrix}$: from row 1, $x_1+2x_2=3\Rightarrow x_1=3-2x_2$; substitute into row 2: $6(3-2x_2)+14x_2=20.2\Rightarrow18+2x_2=20.2\Rightarrow x_2=1.1,\ x_1=0.8$.
**Fitted line:** $y=0.8+1.1x$. Predictions: $\hat y(1)=1.9,\ \hat y(2)=3.0,\ \hat y(3)=4.1$. Residuals: $r=(0.1,\,-0.2,\,0.1)$, and indeed $A^Tr\approx0$ (orthogonality check).

### 7.8 Python
```python
beta,_,_,_ = np.linalg.lstsq(A, b, rcond=None)
y_hat = A @ beta; r = b - y_hat
SSE=np.sum(r**2); MSE=np.mean(r**2); RMSE=np.sqrt(MSE)
R2 = 1 - SSE/np.sum((b-b.mean())**2)
```

### 7.9 Common Mistakes
Assuming overdetermined ⇒ exact solution exists; forgetting intercept column of 1s; confusing residuals with predictions; needlessly forming $(A^TA)^{-1}$; treating high $R^2$ as proof of causation or of good generalization.

---
# 8. Linear Algebra Applications in IT and Data Representation

### 8.1 Core Idea
> Information (images, text, users, networks) is converted into **numbers**; linear algebra manipulates those numbers efficiently.

| Application | LA concept |
|---|---|
| Image representation | Matrices, tensors |
| Computer graphics | Matrix transformations |
| Search engines | Vector similarity |
| Recommenders | Matrix factorization |
| Machine learning | Vectors, matrices, optimization |
| Compression | Projection, SVD |
| NLP | Vector embeddings |
| Networks | Adjacency matrices |

### 8.2 Scalars, Vectors, Matrices as Data
A vector = one data record (e.g., a student's [age, math, programming] scores). A matrix = many records stacked (rows = observations, columns = features).

### 8.3 Similarity — Dot Product & Cosine
$$x\cdot y=\sum x_iy_i,\qquad \cos\theta=\frac{x\cdot y}{\|x\|\|y\|}$$
Used for document/user/search similarity. Cosine similarity is scale-invariant (unlike raw dot product).

### 8.4 Matrices as Transformations
$Ax$ scales/rotates/reflects vectors. 2D rotation matrix: $R(\theta)=\begin{bmatrix}\cos\theta&-\sin\theta\\\sin\theta&\cos\theta\end{bmatrix}$. Scaling matrix: $\text{diag}(s_x,s_y)$.

### 8.5 Images & Text as Numbers
- Grayscale image = matrix of pixel intensities (0=black,255=white).
- RGB image = $H\times W\times3$ tensor.
- Text (bag-of-words): vocabulary vector of 0/1 (or counts) per document.

### 8.6 Recommendation Systems
Ratings matrix $R$ (users × items); factorization $R\approx UV^T$ ($U$=user features, $V$=item features) estimates missing ratings.

### 8.7 Machine Learning & Linear Regression
Prediction: $y=w^Tx+b$. OLS: $\hat\beta=(X^TX)^{-1}X^Ty$ (see Part 7 for full treatment, incl. `lstsq`).

### 8.8 Dimensionality Reduction — PCA & SVD
**PCA:** finds directions of maximum variance; projects data to fewer dimensions while preserving structure.
**SVD:** $A=U\Sigma V^T$; low-rank approximation $A_k=U_k\Sigma_kV_k^T$ used for compression/denoising/recommenders.

### 8.9 Networks
Adjacency matrix $A_{ij}=1$ if node $i,j$ connected, else 0. Symmetric for undirected graphs.

### 8.10 Worked Example (Cosine Similarity)
Documents $d_1=(1,1,0,1),\ d_2=(1,0,1,1)$.
$d_1\cdot d_2 = 1+0+0+1=2$; $\|d_1\|=\sqrt3,\ \|d_2\|=\sqrt3$.
$$\cos\theta=\frac{2}{\sqrt3\cdot\sqrt3}=\frac23\approx0.667$$

### 8.11 Python
```python
np.dot(x,y)/(np.linalg.norm(x)*np.linalg.norm(y))   # cosine similarity
from sklearn.decomposition import PCA
X_reduced = PCA(n_components=k).fit_transform(X)
U,S,VT = np.linalg.svd(A); A_k = U[:,:k]@np.diag(S[:k])@VT[:k,:]
```

---
# 9. Solved Exercises (Practice Problems from Every Topic)

## 9.1 Systems of Linear Equations

**Q1. Solve $x+y=7,\ x-y=1$.**
Add: $2x=8\Rightarrow x=4$; then $y=3$. **Answer: $(4,3)$.**

**Q2. Determine type & solve $2x+4y=8,\ x+2y=4$.**
2nd × 2 = 1st exactly (same line) ⇒ **infinitely many solutions**: $x=4-2y$, i.e. $\{(4-2t,\,t):t\in\mathbb R\}$.

**Q3. Determine type: $y=3x+2,\ y=3x-5$.**
Same slope (3), different intercepts ⇒ parallel ⇒ **no solution**.

**Q4. Solve $3x+2y=12,\ x-y=1$ (via Python method, shown by hand).**
From 2nd: $x=1+y$. Sub: $3(1+y)+2y=12\Rightarrow3+5y=12\Rightarrow y=1.8,\ x=2.8$. **Answer: $(2.8,\,1.8)$.**

**Q5. Explain geometrically why coincident lines give infinite solutions.**
*Answer:* Both equations describe the *same* set of points, so every point on that line satisfies both simultaneously — there's no single unique intersection, but a whole line of common solutions.

## 9.2 Matrix Operations & Inverses

**Q1.** $\begin{bmatrix}1&2\\3&4\end{bmatrix}+\begin{bmatrix}5&6\\7&8\end{bmatrix}=\begin{bmatrix}6&8\\10&12\end{bmatrix}$

**Q2.** $3\begin{bmatrix}2&1\\4&5\end{bmatrix}=\begin{bmatrix}6&3\\12&15\end{bmatrix}$

**Q3.** $\begin{bmatrix}1&2\\3&4\end{bmatrix}\begin{bmatrix}2&0\\1&3\end{bmatrix}=\begin{bmatrix}1(2)+2(1)&1(0)+2(3)\\3(2)+4(1)&3(0)+4(3)\end{bmatrix}=\begin{bmatrix}4&6\\10&12\end{bmatrix}$

**Q4.** $\det\begin{bmatrix}4&3\\2&5\end{bmatrix}=4(5)-3(2)=14$

**Q5. Inverse of $\begin{bmatrix}2&1\\1&1\end{bmatrix}$.** $\det=2(1)-1(1)=1$. $A^{-1}=\frac11\begin{bmatrix}1&-1\\-1&2\end{bmatrix}=\begin{bmatrix}1&-1\\-1&2\end{bmatrix}$.

*(Q1–Q2 conceptual answers for this topic — what is a matrix / dimension / when addable / etc. — are covered in full in §1–2 theory above.)*

## 9.3 Determinants & Rank

**Q1.** $\det\begin{bmatrix}4&2\\1&3\end{bmatrix}=4(3)-2(1)=10$

**Q2.** $\det\begin{bmatrix}1&2&3\\0&4&5\\1&0&6\end{bmatrix}=1(24-0)-2(0-5)+3(0-4)=24+10-12=\mathbf{22}$
*(Note: the source material's worked example stated 10 for this matrix — that was an arithmetic slip; the correct value, verified by cofactor expansion and by NumPy, is 22.)*

**Q3. Rank of $\begin{bmatrix}1&2&3\\2&4&6\\1&1&2\end{bmatrix}$.** $R_2-2R_1\to(0,0,0)$; remaining independent rows: $(1,2,3),(1,1,2)$ ⇒ **rank = 2**.

**Q4. Is $\begin{bmatrix}3&6\\1&2\end{bmatrix}$ invertible?** $\det=3(2)-6(1)=0$ ⇒ **not invertible** (singular; row 2 × 3 = row 1).

**Q5. Verify $\det(AB)=\det(A)\det(B)$ for $A=\begin{bmatrix}1&2\\0&3\end{bmatrix},B=\begin{bmatrix}2&0\\1&1\end{bmatrix}$.**
$\det A=3,\ \det B=2\Rightarrow$ product $=6$. $AB=\begin{bmatrix}4&2\\3&3\end{bmatrix}$, $\det(AB)=12-6=6$. ✔ Matches.

**Q6. Verify $\det(A^T)=\det(A)$ for the same $A$.** $A^T=\begin{bmatrix}1&0\\2&3\end{bmatrix}$, $\det=3$. ✔ Equal to $\det A=3$.

**Q7. Nullity if rank=3, 5 columns.** nullity $=5-3=2$.

## 9.4 Row Reduction & Echelon Forms

**Q1. REF of $\begin{bmatrix}1&2&3\\2&4&7\\1&1&2\end{bmatrix}$.**
$R_2-2R_1\to(0,0,1)$; $R_3-R_1\to(0,-1,-1)$; swap to keep staircase: 
$$\begin{bmatrix}1&2&3\\0&-1&-1\\0&0&1\end{bmatrix}\ (\text{REF, rank}=3)$$

**Q2. RREF of $\begin{bmatrix}1&2&1\\2&4&2\\3&6&3\end{bmatrix}$.** All rows are multiples of row 1 ⇒ after reduction: $\begin{bmatrix}1&2&1\\0&0&0\\0&0&0\end{bmatrix}$ (**rank = 1**).

**Q3. Classify $x+y+z=3,\ 2x+2y+2z=6,\ x+y+z=4$.** Eq. 1 and 3 contradict directly ($3\neq4$ for the same LHS) ⇒ **inconsistent — no solution**.

**Q4. Pivot/free vars for $\begin{bmatrix}1&0&2&0&5\\0&1&-1&0&3\\0&0&0&1&4\end{bmatrix}$.** Pivot columns: 1,2,4 → $x_1,x_2,x_4$ pivot variables. Free: $x_3$ (column 3 has no pivot).

**Q5.** For $A=\begin{bmatrix}1&2&3&4\\2&4&7&8\\1&1&2&3\end{bmatrix}$, row reducing gives rank **3** (pivot columns 1,2,3 after elimination — verify with `rref()` from §4.7).

## 9.5 Linear (In)dependence, Vector Spaces, Basis, Dimension

**Q1.** $(1,2),(2,4)$: $2\times(1,2)=(2,4)$ ⇒ **dependent**.

**Q2.** $(1,0),(0,1)$: independent + span $\mathbb R^2$ ⇒ **yes, a basis**.

**Q3. Basis for $W=\{(x,y,z):x+y+z=0\}$.** $z=-x-y\Rightarrow$ basis $\{(1,0,-1),(0,1,-1)\}$ (dimension 2).

**Q4. Dimension of span$\{(1,2,3),(2,4,6),(1,0,1)\}$.** $(2,4,6)=2(1,2,3)$ redundant ⇒ independent set is $\{(1,2,3),(1,0,1)\}$ ⇒ **dimension 2**.

**Q5.** 7 columns, rank 4 ⇒ nullity $=7-4=3$.

## 9.6 Orthogonality & Projections

**Q1.** $u=(2,1),v=(1,-2)$: $u^Tv=2-2=0$ ⇒ **orthogonal**.

**Q2. Projection of $x=(3,4)$ onto $a=(2,1)$.** $x^Ta=6+4=10$, $a^Ta=5\Rightarrow\text{proj}=\frac{10}{5}(2,1)=(4,2)$.

**Q3. Residual & orthogonality check.** $r=x-\text{proj}=(3,4)-(4,2)=(-1,2)$. Check $a^Tr=2(-1)+1(2)=0$ ✔.

**Q4. Gram–Schmidt on $(1,1),(1,0)$.**
$u_1=(1,1)$. $v_2^Tu_1=1,\ u_1^Tu_1=2\Rightarrow\text{proj}=0.5(1,1)=(0.5,0.5)$.
$u_2=(1,0)-(0.5,0.5)=(0.5,-0.5)$. Check $u_1^Tu_2=0.5-0.5=0$ ✔.

**Q5. Normalize.** $\|u_1\|=\sqrt2\Rightarrow q_1=(1/\sqrt2,1/\sqrt2)$; $\|u_2\|=\sqrt{0.5}\Rightarrow q_2=(1/\sqrt2,-1/\sqrt2)$.

**Q6. Projection matrix onto span$\{(1,0,0),(0,1,0)\}$.** These are already orthonormal ⇒ $P=QQ^T=\begin{bmatrix}1&0&0\\0&1&0\\0&0&0\end{bmatrix}$ (projects onto the $xy$-plane, zeroing the $z$-component).

## 9.7 Least Squares

**Q1. Solve least-squares for $A=\begin{bmatrix}1&1\\1&2\\1&3\end{bmatrix},b=\begin{bmatrix}2\\3\\5\end{bmatrix}$.**
$A^TA=\begin{bmatrix}3&6\\6&14\end{bmatrix}$, $A^Tb=\begin{bmatrix}10\\23\end{bmatrix}$.
$x_1+2x_2=10/3\cdot... $ — solve directly: row1: $3x_1+6x_2=10\Rightarrow x_1+2x_2=10/3$. row2: $6x_1+14x_2=23$.
From row1: $x_1=10/3-2x_2$. Sub: $6(10/3-2x_2)+14x_2=23\Rightarrow20-12x_2+14x_2=23\Rightarrow2x_2=3\Rightarrow x_2=1.5,\ x_1=10/3-3=1/3$.
**$\hat x=(1/3,\ 1.5)$** → fitted line $y\approx0.333+1.5x$.

**Q2. Residual vector.** $\hat y=(0.333+1.5(1),\,0.333+1.5(2),\,0.333+1.5(3))=(1.833,\,3.333,\,4.833)$. $r=b-\hat y=(0.167,\,-0.333,\,0.167)$.

**Q3. Verify $A^Tr=0$.** $\sum r_i = 0.167-0.333+0.167=0.001\approx0$ ✔ (row of 1's). $\sum x_ir_i=1(0.167)+2(-0.333)+3(0.167)=0.167-0.667+0.5=0\approx0$ ✔.

**Q4. Fit a line to $(1,2),(2,4),(3,5),(4,8)$.**
$\sum x=10,\sum x^2=30,\sum y=19,\sum xy=1(2)+2(4)+3(5)+4(8)=2+8+15+32=57$, $m=4$.
Normal eqs: $4\beta_0+10\beta_1=19$; $10\beta_0+30\beta_1=57$.
From first: $\beta_0=(19-10\beta_1)/4$. Sub: $10(19-10\beta_1)/4+30\beta_1=57\Rightarrow(190-100\beta_1)/4+30\beta_1=57\Rightarrow47.5-25\beta_1+30\beta_1=57\Rightarrow5\beta_1=9.5\Rightarrow\beta_1=1.9,\ \beta_0=(19-19)/4=0$.
**Fitted:** $y=1.9x$ (intercept ≈ 0).

**Q5. SSE, RMSE for Q4.** $\hat y=(1.9,3.8,5.7,7.6)$; $r=(0.1,0.2,-0.7,0.4)$; $SSE=0.01+0.04+0.49+0.16=0.70$; $RMSE=\sqrt{0.70/4}=\sqrt{0.175}\approx0.418$.

**Q6/Q7 (construct design matrices).** Multiple predictors: add one column per predictor to $X$, plus a leading column of 1's for the intercept — see §7.4.

---
# 10. Extra Important Conceptual Questions — With Solutions

**Q1. Why does $\det(A)=0$ mean a matrix has "no inverse," intuitively?**
*A:* A zero determinant means the transformation collapses space into a lower dimension (area/volume → 0). An invertible map must be reversible/one-to-one; a collapsing map loses information (many inputs map to the same output), so it cannot be undone — hence no inverse exists.

**Q2. Why is `np.linalg.solve(A,b)` preferred over `np.linalg.inv(A) @ b`?**
*A:* Explicitly forming $A^{-1}$ is more computationally expensive and numerically less stable (it accumulates more floating-point error) than directly solving the system via LU/Gaussian-elimination-based solvers. `solve()` is faster and more accurate for the common case of just wanting $x$, not the full inverse.

**Q3. What's the difference between the row space and the null space of a matrix, and how are they related?**
*A:* The row space is spanned by $A$'s rows (dimension = rank); the null space is $\{x : Ax=0\}$ (dimension = nullity). They are **orthogonal complements** of each other in $\mathbb{R}^n$ — every vector in the row space is orthogonal to every vector in the null space, and together their dimensions add up to $n$ (rank–nullity theorem).

**Q4. Why is matrix multiplication not commutative, geometrically?**
*A:* Each matrix represents a transformation (rotate, scale, shear, etc.). Applying transformation $B$ then $A$ ($AB$) is generally a different combined transformation than applying $A$ then $B$ ($BA$) — e.g., rotate-then-stretch along an axis looks different from stretch-then-rotate. Order of operations matters spatially.

**Q5. Why is the residual in least squares always orthogonal to the column space of $A$ at the optimum?**
*A:* Because $\hat x$ minimizes $\|Ax-b\|^2$, the closest point $A\hat x$ to $b$ within Col($A$) is its orthogonal projection. If the residual $r=b-A\hat x$ had any component along Col($A$), we could reduce $\|r\|$ further by adjusting $\hat x$ — so at the true minimum, $r$ has zero component in Col($A$), i.e., $r\perp\text{Col}(A)$, giving $A^Tr=0$.

**Q6. What does it mean for two features in a dataset to be "linearly dependent," and why does it matter for regression?**
*A:* It means one feature is an exact linear combination of others (e.g., height in cm = 100 × height in m) — no new information. In regression this causes $X^TX$ to be singular (or near-singular under near-dependence/"multicollinearity"), so $(X^TX)^{-1}$ doesn't exist or is numerically unstable, making coefficient estimates non-unique or highly sensitive to small data changes. Remedies: drop redundant features, use pseudoinverse (SVD), or regularization (ridge regression).

**Q7. How does PCA relate to eigenvectors and SVD?**
*A:* PCA finds the eigenvectors of the data's covariance matrix, ordered by eigenvalue (variance explained); equivalently, it can be computed via the SVD of the (centered) data matrix — the right singular vectors $V$ are the principal component directions and the singular values relate to the variance along each direction.

**Q8. Why must a basis be both spanning AND independent — why isn't spanning alone enough?**
*A:* A spanning set alone may contain redundant vectors (e.g., 3 vectors spanning $\mathbb{R}^2$) — coordinates relative to it would not be unique. Independence guarantees every vector in the space has a *unique* representation as a linear combination of basis vectors, which is essential for coordinates to be well-defined.

**Q9. Give an intuitive reason why $\text{rank}(A)=\text{rank}(A^T)$ (row rank = column rank).**
*A:* This is a nontrivial but fundamental theorem: no matter whether you count independent directions among the rows or among the columns, you get the same count — because both measure the same thing, the dimension of the "true" information content in the matrix (the dimension of its image under linear transformation). It can be proven via RREF: pivot columns give column rank, and nonzero rows after reduction give row rank, and reduction preserves both counts as equal.

**Q10. Why does an overdetermined system $Ax=b$ (more equations than unknowns) usually have no exact solution, but a well-posed least-squares solution always exists?**
*A:* With more equations than unknowns, $b$ generically does not lie exactly in Col($A$) (a lower-dimensional subspace of $\mathbb{R}^m$), so no $x$ satisfies $Ax=b$ exactly. But the *projection* of $b$ onto Col($A$) always exists (every vector has a well-defined closest point in any subspace), so the least-squares $\hat x$ satisfying $A\hat x=\text{proj}_{\text{Col}(A)}(b)$ always exists (uniquely, if $A$ has full column rank).

**Q11. What is the geometric meaning of an idempotent, symmetric matrix $P$ ($P^2=P,\ P^T=P$)?**
*A:* $P$ is an **orthogonal projection matrix** onto some subspace. Idempotence ($P^2=P$) means projecting twice gives the same result as projecting once (once you're in the subspace, projecting again doesn't move you). Symmetry ensures the projection is *orthogonal* (perpendicular) rather than an oblique/skewed projection.

**Q12. Why do we normalize (scale) features before PCA or distance-based ML algorithms?**
*A:* Features with larger numeric ranges (e.g., salary in the tens of thousands vs. age in tens) dominate variance/distance calculations purely due to scale, not true importance. Normalizing (e.g., $\hat x = x/\|x\|$ or z-scoring) ensures each feature contributes comparably, so the resulting directions/distances reflect genuine structure in the data rather than arbitrary units.

**Q13. Explain, using rank, why a system with more unknowns than independent equations always has infinitely many solutions (if consistent).**
*A:* If rank($A$) = $r < n$ (number of unknowns) and the system is consistent, there are $n-r$ free variables. Each free variable can take any real value, generating a continuum of solutions — hence infinitely many.

**Q14. Why is $QR$ decomposition often preferred over the normal equations ($A^TA)^{-1}A^Tb$) for solving least squares numerically?**
*A:* Forming $A^TA$ squares the condition number of $A$, amplifying numerical errors — especially when columns of $A$ are nearly collinear. QR (or SVD) works directly with $A$, avoiding this squaring effect, and is therefore more numerically stable, especially for ill-conditioned or nearly rank-deficient problems.

**Q15. What's the difference between an eigenvector direction and a singular vector direction (conceptually), and when do they coincide?**
*A:* Eigenvectors are defined only for square matrices, where $Av=\lambda v$ — the transformation just scales the eigenvector, without rotating it. Singular vectors ($A=U\Sigma V^T$) are defined for any matrix and describe input/output orthonormal directions of maximum stretching. They coincide (up to sign) when $A$ is symmetric — in that special case, eigenvectors and singular vectors are the same, and eigenvalues equal singular values in magnitude.

---

# 11. Master Formula Sheet

| Topic | Formula |
|---|---|
| 2×2 determinant | $\det(A)=ad-bc$ |
| 3×3 determinant | $a(ei-fh)-b(di-fg)+c(dh-eg)$ |
| Triangular determinant | $\prod a_{ii}$ |
| Determinant properties | $\det(I)=1,\ \det(A^T)=\det A,\ \det(AB)=\det A\det B,\ \det(A^{-1})=1/\det A,\ \det(cA)=c^n\det A$ |
| 2×2 inverse | $A^{-1}=\frac1{ad-bc}\begin{bmatrix}d&-b\\-c&a\end{bmatrix}$ |
| Inverse properties | $(A^{-1})^{-1}=A,\ (AB)^{-1}=B^{-1}A^{-1},\ (A^T)^{-1}=(A^{-1})^T$ |
| Full-rank condition | $\det(A)\ne0 \iff \text{rank}(A)=n \iff A^{-1}$ exists |
| Rank–nullity | $\text{rank}(A)+\text{nullity}(A)=n$ |
| System type by rank | Unique: rank$(A)$=rank$([A\|b])=n$; Infinite: $<n$; None: rank$(A)<$rank$([A\|b])$ |
| Dot product | $u\cdot v=\sum u_iv_i=u^Tv$ |
| Norm | $\|v\|=\sqrt{v^Tv}$ |
| Cosine similarity | $\cos\theta=\dfrac{x\cdot y}{\|x\|\|y\|}$ |
| Projection onto vector | $\text{proj}_a(x)=\dfrac{x^Ta}{a^Ta}a$ |
| Projection onto orthonormal subspace | $QQ^Tx$ |
| General projection matrix | $A(A^TA)^{-1}A^T$ |
| Gram–Schmidt step | $u_j=v_j-\sum_{i<j}\text{proj}_{u_i}(v_j)$ |
| QR decomposition | $A=QR$ |
| Normal equations | $A^TA\hat x=A^Tb$ |
| Least-squares solution | $\hat x=(A^TA)^{-1}A^Tb$ (or `lstsq`/QR/SVD) |
| SSE / MSE / RMSE | $\sum r_i^2$ / $SSE/m$ / $\sqrt{MSE}$ |
| $R^2$ | $1-SSE/SST$ |
| SVD | $A=U\Sigma V^T$ |
| Rank-$k$ approximation | $A_k=U_k\Sigma_kV_k^T$ |

---

# 12. References

- **[R-01]** Gilbert Strang, *Linear Algebra and Its Applications*, MIT Press / Cengage.
- **[R-02]** Course material (Mathematics for IT, M.Tech. 1st Semester, IIIT Allahabad), Dr. Mohammed Javed, plus AI-generated examples/code accompanying each unit.
- **[R-03]** Vaswani et al., *Attention Is All You Need* (2017) — referenced in the course material for linear-transformation use in embeddings.
- NumPy, SciPy, and scikit-learn official documentation for the Python routines used throughout (`numpy.linalg`, `sklearn.decomposition.PCA`).

*Compiled and solved from eight course topic files covering Unit 1: Linear Algebra and Matrix Theory.*
