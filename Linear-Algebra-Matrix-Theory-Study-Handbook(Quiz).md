# Linear Algebra & Matrix Theory — Complete Study Handbook

### Units 1 & 2 | Theory · Plain-English Intuition · Solved Examples · Graded Numericals

---

## How to use this handbook

Every chapter follows the same four-part rhythm:

| Section | What it does |
|---|---|
| **Explain Like I'm Five** | The idea stripped of all notation. A story, a picture, an analogy. Read this first, always. |
| **The Formal Theory** | Definitions, theorems, and the precise statements you need for the exam. |
| **Solved Examples** | Full worked solutions with the reasoning shown, not just the answer. |
| **Practice Numericals** | Problems tagged **[Easy] [Medium] [Hard] [Very Hard]**, with complete solutions at the end of each chapter. |

**Difficulty tags mean:**

- **[Easy]** — one concept, one short computation. If you can't do these, re-read the theory.
- **[Medium]** — two or three steps chained, or a small twist in the setup. Standard exam fare.
- **[Hard]** — multi-part, requires choosing the right tool, or algebra that will punish carelessness.
- **[Very Hard]** — proof-flavoured, or a trap hidden in the phrasing, or long enough that bookkeeping itself is the challenge. These separate a 70 from a 95.

**Notation used throughout:**

- Matrices: capital letters `A`, `B`. Vectors: bold-ish lowercase `v`, `x`. Scalars: `c`, `λ`.
- A matrix is written row by row in brackets: `A = [[1, 2], [3, 4]]` means row 1 is (1, 2), row 2 is (3, 4).
- `Aᵀ` is the transpose, `A⁻¹` the inverse, `Iₙ` the n×n identity, `det(A)` or `|A|` the determinant.
- `ℝⁿ` is the set of all n-component real vectors. `Col(A)`, `Row(A)`, `Nul(A)` are column, row, and null spaces.
- `⟨u, v⟩` or `u · v` is the dot product. `‖v‖` is the length (norm).
- `~` between matrices means "row equivalent to".
- `≐` means "approximately equal to".

---

## Study plan — if your quiz is soon

**If you have 3 days:** Chapters 2, 3, 7, 9, 10, 13. These are where marks concentrate.

**If you have 1 week:** Everything, but do the [Easy] and [Medium] problems only. Come back for [Hard] on the last day.

**If you have 2+ weeks:** Everything including [Very Hard], plus the Mixed Examination Papers in Part III.

**The night before:** Appendix A (formula sheet) and Appendix B (the ten mistakes that cost the most marks).

---

## Table of Contents

**PART I — UNIT 1: LINEAR ALGEBRA AND MATRIX THEORY**

1. Systems of Linear Equations
2. Row Reduction and Echelon Forms
3. Matrix Operations and Matrix Inverses
4. Linear Dependence, Vector Spaces, Subspaces, Basis and Dimension
5. Orthogonality and Projections — Orthogonal Bases, Gram–Schmidt
6. Least Squares Problems and Linear Models
7. Determinants and Their Properties, Rank of a Matrix
8. Applications of Linear Algebra in IT and Data Representation

**PART II — UNIT 2: EIGEN ANALYSIS AND MATRIX DECOMPOSITION**

9. Eigenvalues, Eigenvectors and the Characteristic Equation
10. Diagonalization of Matrices
11. Symmetric Matrices, Positive Definite Matrices, Similar Matrices
12. Linear Transformations
13. Singular Value Decomposition, Low-Rank Approximation, Matrix Factorization
14. Applications — Data Compression, Recommender Systems, Image Representation, ML

**PART III — EXAMINATION PRACTICE**

15. Mixed Problem Sets by Difficulty
16. Full-Length Mock Papers with Solutions

**APPENDICES**

- A. Master Formula Sheet
- B. The Ten Most Expensive Mistakes
- C. Glossary of Every Term Used
- D. Answer Index

---
# PART I — UNIT 1: LINEAR ALGEBRA AND MATRIX THEORY

---

# Chapter 1 — Systems of Linear Equations

---

## 1.1 Explain Like I'm Five

Imagine you're at a shop. You don't know the price of a pencil or the price of an eraser. But you know two facts:

- Two pencils and three erasers cost ₹13.
- One pencil and one eraser cost ₹5.

You can figure out both prices from these two clues. That's it. That's a system of linear equations — a bunch of clues about some unknown numbers, where every clue is "fair" in a specific sense.

**What makes a clue "fair" (linear)?** The unknowns are only ever *added* and *multiplied by ordinary numbers*. Never multiplied by each other, never squared, never inside a square root or a sine. So:

- `2x + 3y = 13` — fair. Linear.
- `xy = 6` — not fair. The unknowns multiply each other.
- `x² + y = 4` — not fair. Squared.
- `√x = 3` — not fair.

**Why does linear matter so much?** Because linear systems always behave predictably. Geometrically, each linear equation in two unknowns is a *straight line*. Solving the system means finding where the lines cross. And two straight lines can only do three things:

1. **Cross at exactly one point** → one unique solution.
2. **Be parallel and never touch** → no solution. The clues contradict each other.
3. **Be the same line lying on top of each other** → infinitely many solutions. One clue was just a repeat of the other in disguise.

That's the whole story. There is no fourth option. You can never have exactly two solutions or exactly seventeen solutions to a linear system. This is the single most important structural fact in the subject, and it stays true in 3 dimensions (planes instead of lines) and in 300 dimensions.

In 3D, each equation is a *plane*. Three planes can meet at a point (unique), meet along a line (infinite), or have no common point (inconsistent — like three planes forming a triangular prism).

---

## 1.2 The Formal Theory

### 1.2.1 Definitions

A **linear equation** in variables x₁, x₂, ..., xₙ is an equation of the form

> a₁x₁ + a₂x₂ + ... + aₙxₙ = b

where a₁, ..., aₙ and b are real (or complex) constants. The aᵢ are called **coefficients** and b the **constant term**.

A **system of linear equations** (or **linear system**) is a finite collection of linear equations in the same variables:

```
a₁₁x₁ + a₁₂x₂ + ... + a₁ₙxₙ = b₁
a₂₁x₁ + a₂₂x₂ + ... + a₂ₙxₙ = b₂
   ⋮
aₘ₁x₁ + aₘ₂x₂ + ... + aₘₙxₙ = bₘ
```

A **solution** is an ordered list (s₁, s₂, ..., sₙ) which, when substituted for (x₁, ..., xₙ), makes every equation true simultaneously. The **solution set** is the set of all solutions.

Two systems are **equivalent** if they have the same solution set.

### 1.2.2 The Fundamental Theorem on Solution Sets

> **Theorem 1.1.** A system of linear equations has either
> (a) no solution, or
> (b) exactly one solution, or
> (c) infinitely many solutions.

A system is **consistent** if it has at least one solution (cases a is excluded), and **inconsistent** if it has none.

*Why exactly three?* Suppose a system has two distinct solutions u and v. Consider w = u + t(v − u) for any scalar t. Substituting into the i-th equation, and writing the left side as a function Lᵢ that is linear:

Lᵢ(w) = Lᵢ(u) + t·Lᵢ(v − u) = bᵢ + t(bᵢ − bᵢ) = bᵢ

So w is a solution for *every* real t — infinitely many. Hence "two solutions" immediately forces "infinitely many". There is no middle ground.

### 1.2.3 Matrix Form

Every linear system can be packaged three ways. Take the system

```
x₁ − 2x₂ +  x₃ =  0
    2x₂ − 8x₃ =  8
5x₁      − 5x₃ = 10
```

**(i) Coefficient matrix** — just the coefficients:

```
A = [[1, −2,  1],
     [0,  2, −8],
     [5,  0, −5]]
```

**(ii) Augmented matrix** — coefficients plus the right-hand side, separated conceptually by a bar:

```
[A | b] = [[1, −2,  1 |  0],
           [0,  2, −8 |  8],
           [5,  0, −5 | 10]]
```

**(iii) Vector/matrix equation** — `Ax = b`, where x = (x₁, x₂, x₃)ᵀ and b = (0, 8, 10)ᵀ.

All three say the same thing. The augmented matrix is the working form for solving; `Ax = b` is the conceptual form for theory.

### 1.2.4 Elementary Row Operations

Three operations on the rows of an augmented matrix that **never change the solution set**:

1. **Replacement** — add a multiple of one row to another row. `Rᵢ → Rᵢ + cRⱼ`
2. **Interchange** — swap two rows. `Rᵢ ↔ Rⱼ`
3. **Scaling** — multiply a row by a *nonzero* constant. `Rᵢ → cRᵢ`, c ≠ 0

Each is reversible, which is the reason the solution set survives them. Matrices connected by a chain of these are **row equivalent**, written A ~ B.

> **Theorem 1.2.** If the augmented matrices of two systems are row equivalent, the systems have the same solution set.

**Critical caution:** the scaling operation requires c ≠ 0. Multiplying a row by 0 destroys information and can turn an inconsistent system into a consistent-looking one. This is a classic exam trap.

### 1.2.5 The Two Fundamental Questions

For any linear system, ask:

1. **Existence** — is the system consistent? Does at least one solution exist?
2. **Uniqueness** — if a solution exists, is it the only one?

Everything in Chapters 1–4 is machinery for answering these two questions efficiently.

### 1.2.6 Geometric Interpretation Table

| Number of unknowns | Each equation is a... | Unique solution means... | Infinite solutions means... | No solution means... |
|---|---|---|---|---|
| 2 | line in ℝ² | lines cross at one point | lines coincide | lines are parallel, distinct |
| 3 | plane in ℝ³ | three planes meet at one point | planes share a line or a whole plane | no common point (e.g. prism arrangement) |
| n | hyperplane in ℝⁿ | hyperplanes meet at one point | intersection is a line/plane/higher flat | empty intersection |

---

## 1.3 Solved Examples

### Example 1.1 — [Easy] Unique solution by elimination

Solve:
```
x + y = 5
2x + 3y = 13
```

**Solution.** Multiply the first equation by 2: `2x + 2y = 10`. Subtract from the second:

(2x + 3y) − (2x + 2y) = 13 − 10 → y = 3.

Back-substitute into `x + y = 5`: x = 2.

**Check:** 2 + 3 = 5 ✓ and 2(2) + 3(3) = 4 + 9 = 13 ✓

**Answer:** (x, y) = (2, 3). Unique solution. (This is the pencil–eraser problem from §1.1: pencil ₹2, eraser ₹3.)

---

### Example 1.2 — [Easy] Detecting inconsistency

Determine whether the following has a solution:
```
x − 2y = 3
−2x + 4y = 1
```

**Solution.** Multiply the first equation by 2: `2x − 4y = 6`. Add to the second:

(−2x + 4y) + (2x − 4y) = 1 + 6 → 0 = 7.

This is false regardless of x and y. The system is **inconsistent**.

**Geometric reading:** both lines have slope 1/2, but different intercepts — they are parallel and distinct, so they never meet.

**Answer:** No solution.

---

### Example 1.3 — [Medium] Full 3×3 system via augmented matrix

Solve:
```
x₁ − 2x₂ +  x₃ =  0
    2x₂ − 8x₃ =  8
5x₁      − 5x₃ = 10
```

**Solution.** Augmented matrix:

```
[[1, −2,  1 |  0],
 [0,  2, −8 |  8],
 [5,  0, −5 | 10]]
```

**Step 1:** Eliminate the 5 in position (3,1). `R₃ → R₃ − 5R₁`:

Row 3 becomes (5 − 5, 0 + 10, −5 − 5 | 10 − 0) = (0, 10, −10 | 10).

```
[[1, −2,  1 |  0],
 [0,  2, −8 |  8],
 [0, 10, −10 | 10]]
```

**Step 2:** Scale row 2 for convenience. `R₂ → (1/2)R₂`:

```
[[1, −2,  1 |  0],
 [0,  1, −4 |  4],
 [0, 10, −10| 10]]
```

**Step 3:** Eliminate the 10 in position (3,2). `R₃ → R₃ − 10R₂`:

Row 3 becomes (0, 0, −10 + 40 | 10 − 40) = (0, 0, 30 | −30).

```
[[1, −2,  1 |  0],
 [0,  1, −4 |  4],
 [0,  0, 30 | −30]]
```

**Step 4:** `R₃ → (1/30)R₃` gives x₃ = −1.

**Back-substitution:** From row 2: x₂ − 4(−1) = 4 → x₂ + 4 = 4 → x₂ = 0.
From row 1: x₁ − 2(0) + (−1) = 0 → x₁ = 1.

**Check in original equation 3:** 5(1) − 5(−1) = 5 + 5 = 10 ✓

**Answer:** (x₁, x₂, x₃) = (1, 0, −1).

---

### Example 1.4 — [Medium] Infinitely many solutions, parametric form

Solve:
```
x + 2y − 3z = 4
2x + 4y − 6z = 8
−x − 2y + 3z = −4
```

**Solution.** Notice immediately that equation 2 is 2× equation 1, and equation 3 is −1× equation 1. All three equations carry the *same* information.

Augmented matrix and reduce:
```
[[ 1,  2, −3 |  4],
 [ 2,  4, −6 |  8],
 [−1, −2,  3 | −4]]
```
`R₂ → R₂ − 2R₁` and `R₃ → R₃ + R₁`:
```
[[1, 2, −3 | 4],
 [0, 0,  0 | 0],
 [0, 0,  0 | 0]]
```

One surviving equation: `x + 2y − 3z = 4`. Here x is the leading (basic) variable; y and z are **free**.

Set y = s, z = t. Then x = 4 − 2s + 3t.

**Answer (parametric vector form):**

(x, y, z) = (4, 0, 0) + s(−2, 1, 0) + t(3, 0, 1), for all s, t ∈ ℝ.

Geometrically this is a **plane** in ℝ³ — the solution set is 2-dimensional, passing through (4,0,0) with direction vectors (−2,1,0) and (3,0,1).

---

### Example 1.5 — [Hard] Parameter determines the solution type

For which values of k does the system have (i) a unique solution, (ii) no solution, (iii) infinitely many solutions?

```
 x +  y +  z = 2
2x + 3y + 2z = 5
2x + 3y + (k² − 1)z = k + 1
```

**Solution.** Augmented matrix:
```
[[1, 1,  1       | 2    ],
 [2, 3,  2       | 5    ],
 [2, 3, k²−1     | k+1  ]]
```

`R₂ → R₂ − 2R₁`, `R₃ → R₃ − 2R₁`:
```
[[1, 1,  1       | 2    ],
 [0, 1,  0       | 1    ],
 [0, 1, k²−3     | k−3  ]]
```

`R₃ → R₃ − R₂`:
```
[[1, 1,  1       | 2    ],
 [0, 1,  0       | 1    ],
 [0, 0, k²−3     | k−4  ]]
```

The final row reads `(k² − 3)z = k − 4`.

**Case (i): k² − 3 ≠ 0**, i.e. k ≠ ±√3. Then z = (k−4)/(k²−3) is determined, and back-substitution gives unique y and x. **Unique solution.**

**Case (ii): k² − 3 = 0 and k − 4 ≠ 0.** Since k = ±√3 makes k − 4 ≠ 0 automatically (√3 ≈ 1.73 ≠ 4), we get the row `0 = k − 4 ≠ 0`. **Inconsistent — no solution** for k = √3 and k = −√3.

**Case (iii):** would need k² − 3 = 0 *and* k − 4 = 0 simultaneously — impossible. **No value of k gives infinitely many solutions.**

**Answer:** Unique for k ≠ ±√3; no solution for k = ±√3; never infinitely many.

---

### Example 1.6 — [Hard] A system with a symbolic right-hand side

Find conditions on (b₁, b₂, b₃) so that the system `Ax = b` is consistent, where

A = [[1, −2, 1], [2, −3, 4], [1, −1, 3]].

**Solution.** Row reduce the augmented matrix `[A | b]`:
```
[[1, −2, 1 | b₁],
 [2, −3, 4 | b₂],
 [1, −1, 3 | b₃]]
```
`R₂ → R₂ − 2R₁`, `R₃ → R₃ − R₁`:
```
[[1, −2, 1 | b₁          ],
 [0,  1, 2 | b₂ − 2b₁    ],
 [0,  1, 2 | b₃ − b₁     ]]
```
`R₃ → R₃ − R₂`:
```
[[1, −2, 1 | b₁                    ],
 [0,  1, 2 | b₂ − 2b₁              ],
 [0,  0, 0 | b₃ − b₁ − b₂ + 2b₁    ]]
```
The last entry simplifies to `b₁ − b₂ + b₃`.

For consistency we need the last row not to read "0 = nonzero". Hence:

**Answer:** The system is consistent if and only if **b₁ − b₂ + b₃ = 0**. When this holds, there is one free variable (x₃), so there are infinitely many solutions.

*Interpretation:* Col(A) is the plane in ℝ³ defined by b₁ − b₂ + b₃ = 0. A is rank 2.

---

### Example 1.7 — [Very Hard] Network flow

Traffic flows through a one-way road network. At each intersection, flow in = flow out. Given the diagram data below, find the general solution and the minimum possible value of x₄ if all flows must be non-negative.

Intersections give:
```
A:  x₁ + 100 = x₂ + 40
B:  x₂ + 50  = x₃ + 60
C:  x₃ + 120 = x₄ + 90
D:  x₄ + 30  = x₁ + 110
```

**Solution.** Rewrite each:
```
x₁ − x₂ = −60
x₂ − x₃ = 10
x₃ − x₄ = −30
−x₁ + x₄ = 80
```

Augmented matrix:
```
[[ 1, −1,  0,  0 | −60],
 [ 0,  1, −1,  0 |  10],
 [ 0,  0,  1, −1 | −30],
 [−1,  0,  0,  1 |  80]]
```
`R₄ → R₄ + R₁`:
```
[[1, −1,  0,  0 | −60],
 [0,  1, −1,  0 |  10],
 [0,  0,  1, −1 | −30],
 [0, −1,  0,  1 |  20]]
```
`R₄ → R₄ + R₂`:
```
[[1, −1,  0,  0 | −60],
 [0,  1, −1,  0 |  10],
 [0,  0,  1, −1 | −30],
 [0,  0, −1,  1 |  30]]
```
`R₄ → R₄ + R₃`: last row becomes all zeros with RHS 0. Consistent, with x₄ free.

Back-substitute with x₄ = t:
- Row 3: x₃ = t − 30
- Row 2: x₂ = x₃ + 10 = t − 20
- Row 1: x₁ = x₂ − 60 = t − 80

**General solution:** (x₁, x₂, x₃, x₄) = (t − 80, t − 20, t − 30, t).

**Non-negativity:** need t − 80 ≥ 0, t − 20 ≥ 0, t − 30 ≥ 0, t ≥ 0. The binding constraint is t ≥ 80.

**Answer:** minimum x₄ = 80, at which point (x₁, x₂, x₃, x₄) = (0, 60, 50, 80).

*Note the structural lesson:* the rows summed to zero because total flow into the network equals total flow out — a conservation law showing up as a linear dependence among the equations.

---

## 1.4 Practice Numericals — Chapter 1

**[Easy]**

**P1.1** Solve: `3x + 2y = 12`, `x − y = 1`.

**P1.2** Determine whether (2, −1, 3) is a solution of:
`x + y + z = 4`, `2x − y + z = 8`, `x + 2y − z = −3`.

**P1.3** Write the augmented matrix for:
`4x₁ − 5x₂ + 7x₃ = 1`, `3x₁ + 2x₂ = 0`, `x₂ − 9x₃ = −4`.

**P1.4** Solve `2x − 4y = 6`, `−3x + 6y = −9`. State the type of solution set.

**P1.5** State which of the following are linear equations in x, y, z: (a) `3x − 2y + z = 0`, (b) `x + yz = 1`, (c) `2^x + y = 5`, (d) `πx − √2 y = e`.

**[Medium]**

**P1.6** Solve the system:
`x + 2y + 3z = 6`, `2x + 5y + 2z = 4`, `3x − y − z = 2`.

**P1.7** Find the parametric solution of:
`x₁ + 3x₂ − 5x₃ = 4`, `x₁ + 4x₂ − 8x₃ = 7`, `−3x₁ − 7x₂ + 9x₃ = −6`.

**P1.8** Balance the chemical equation using a linear system:
`C₃H₈ + O₂ → CO₂ + H₂O`.

**P1.9** Three numbers sum to 30. The second is twice the first. The third exceeds the sum of the first two by 6. Find the numbers.

**P1.10** For what value of h is the following system consistent?
`x₁ − 3x₂ = 1`, `2x₁ − 6x₂ = h`.

**[Hard]**

**P1.11** Determine all values of a and b for which the system
`x + 2y = 3`, `2x + ay = b`
has (i) unique solution, (ii) no solution, (iii) infinitely many.

**P1.12** Find conditions on b₁, b₂, b₃ for consistency of `Ax = b` where
A = [[1, 2, −1], [2, 5, 1], [1, 3, 2]].

**P1.13** Solve the 4×4 system:
```
x₁ + x₂ + x₃ + x₄ = 6
2x₁ + 3x₂ − x₃ + x₄ = 5
3x₁ + 2x₂ + 2x₃ − x₄ = 3
x₁ − x₂ + 2x₃ + 3x₄ = 8
```

**P1.14** A polynomial p(t) = a₀ + a₁t + a₂t² passes through (1, 12), (2, 15), (3, 16). Find it.

**[Very Hard]**

**P1.15** For the system
```
λx +  y +  z = 1
 x + λy +  z = λ
 x +  y + λz = λ²
```
discuss the nature of the solution for all values of λ, and find the solution in each case.

**P1.16** A network of one-way streets has flows x₁, ..., x₅ satisfying
```
x₁ + x₂ = 300,  x₂ − x₃ + x₄ = 100,  x₄ + x₅ = 400,  x₁ + x₃ + x₅ = 600.
```
Find the general solution, determine the number of free variables, and find the range of x₄ under non-negativity.

**P1.17** Prove that if a homogeneous system `Ax = 0` with m equations and n unknowns satisfies n > m, then it has a nontrivial solution. Then exhibit a nontrivial solution for
`x₁ + 2x₂ − x₃ + 3x₄ = 0`, `2x₁ + 4x₂ + x₃ − x₄ = 0`.

---

## 1.5 Solutions to Chapter 1 Practice

**S1.1** From the second, x = y + 1. Substitute: 3(y+1) + 2y = 12 → 5y = 9 → y = 9/5, x = 14/5.
**Answer:** (14/5, 9/5).

**S1.2** Check each: 2 + (−1) + 3 = 4 ✓; 2(2) − (−1) + 3 = 4 + 1 + 3 = 8 ✓; 2 + 2(−1) − 3 = 2 − 2 − 3 = −3 ✓. **Yes, it is a solution.**

**S1.3**
```
[[4, −5,  7 |  1],
 [3,  2,  0 |  0],
 [0,  1, −9 | −4]]
```
Note the *zero* coefficient for x₃ in equation 2 and x₁ in equation 3 — missing variables must be written as 0, not skipped.

**S1.4** Equation 2 = (−3/2) × equation 1. So there is really only one equation: `2x − 4y = 6`, i.e. `x = 3 + 2y`.
**Answer:** infinitely many solutions, (x, y) = (3 + 2t, t), t ∈ ℝ. The two lines coincide.

**S1.5** (a) linear. (b) not linear — product yz. (c) not linear — exponential in x. (d) linear — π, √2, e are just constants.

**S1.6** Augmented:
```
[[1,  2,  3 | 6],
 [2,  5,  2 | 4],
 [3, −1, −1 | 2]]
```
`R₂ → R₂ − 2R₁`, `R₃ → R₃ − 3R₁`:
```
[[1,  2,  3 |  6],
 [0,  1, −4 | −8],
 [0, −7, −10| −16]]
```
`R₃ → R₃ + 7R₂`:
```
[[1, 2,  3  |   6],
 [0, 1, −4  |  −8],
 [0, 0, −38 | −72]]
```
z = 72/38 = 36/19. y = −8 + 4(36/19) = (−152 + 144)/19 = −8/19.
x = 6 − 2(−8/19) − 3(36/19) = (114 + 16 − 108)/19 = 22/19.
**Answer:** (22/19, −8/19, 36/19).

**S1.7** Augmented:
```
[[ 1,  3, −5 |  4],
 [ 1,  4, −8 |  7],
 [−3, −7,  9 | −6]]
```
`R₂ → R₂ − R₁`, `R₃ → R₃ + 3R₁`:
```
[[1, 3, −5 |  4],
 [0, 1, −3 |  3],
 [0, 2, −6 |  6]]
```
`R₃ → R₃ − 2R₂` gives a zero row. Then `R₁ → R₁ − 3R₂`:
```
[[1, 0,  4 | −5],
 [0, 1, −3 |  3],
 [0, 0,  0 |  0]]
```
x₃ = t free. x₁ = −5 − 4t, x₂ = 3 + 3t.
**Answer:** (x₁, x₂, x₃) = (−5, 3, 0) + t(−4, 3, 1).

**S1.8** Let `x₁C₃H₈ + x₂O₂ → x₃CO₂ + x₄H₂O`.
- Carbon: 3x₁ = x₃
- Hydrogen: 8x₁ = 2x₄
- Oxygen: 2x₂ = 2x₃ + x₄

Set x₁ = 1: x₃ = 3, x₄ = 4, then 2x₂ = 6 + 4 = 10 → x₂ = 5.
**Answer:** C₃H₈ + 5O₂ → 3CO₂ + 4H₂O.

**S1.9** Let the numbers be x, y, z.
`x + y + z = 30`, `y = 2x`, `z = x + y + 6`.
Substitute: z = x + 2x + 6 = 3x + 6. Then x + 2x + 3x + 6 = 30 → 6x = 24 → x = 4.
**Answer:** 4, 8, 18.

**S1.10** Row reduce: `R₂ → R₂ − 2R₁` gives `0 = h − 2`. Consistent only when **h = 2** (then infinitely many solutions).

**S1.11** Reduce:
```
[[1, 2 | 3],
 [2, a | b]]  →  R₂ − 2R₁ →  [[1, 2 | 3], [0, a−4 | b−6]]
```
- (i) **Unique:** a ≠ 4 (any b).
- (ii) **No solution:** a = 4 and b ≠ 6.
- (iii) **Infinitely many:** a = 4 and b = 6.

**S1.12**
```
[[1, 2, −1 | b₁],
 [2, 5,  1 | b₂],
 [1, 3,  2 | b₃]]
```
`R₂ → R₂ − 2R₁`, `R₃ → R₃ − R₁`:
```
[[1, 2, −1 | b₁        ],
 [0, 1,  3 | b₂ − 2b₁  ],
 [0, 1,  3 | b₃ − b₁   ]]
```
`R₃ → R₃ − R₂`: RHS becomes b₃ − b₁ − b₂ + 2b₁ = b₁ − b₂ + b₃.
**Answer:** consistent iff **b₁ − b₂ + b₃ = 0**.

**S1.13** Augmented:
```
[[1,  1,  1,  1 | 6],
 [2,  3, −1,  1 | 5],
 [3,  2,  2, −1 | 3],
 [1, −1,  2,  3 | 8]]
```
`R₂ − 2R₁`, `R₃ − 3R₁`, `R₄ − R₁`:
```
[[1,  1,  1,  1 |   6],
 [0,  1, −3, −1 |  −7],
 [0, −1, −1, −4 | −15],
 [0, −2,  1,  2 |   2]]
```
`R₃ + R₂`, `R₄ + 2R₂`:
```
[[1, 1,  1,  1 |   6],
 [0, 1, −3, −1 |  −7],
 [0, 0, −4, −5 | −22],
 [0, 0, −5,  0 | −12]]
```
From row 4: x₃ = 12/5. Substitute into row 3: −4(12/5) − 5x₄ = −22 → −48/5 − 5x₄ = −22 → 5x₄ = −48/5 + 22 = 62/5 → x₄ = 62/25.
Row 2: x₂ = −7 + 3(12/5) + 62/25 = −7 + 36/5 + 62/25 = (−175 + 180 + 62)/25 = 67/25.
Row 1: x₁ = 6 − 67/25 − 60/25 − 62/25 = (150 − 189)/25 = −39/25.
**Answer:** (−39/25, 67/25, 12/5, 62/25).

**S1.14** Conditions:
`a₀ + a₁ + a₂ = 12`, `a₀ + 2a₁ + 4a₂ = 15`, `a₀ + 3a₁ + 9a₂ = 16`.
Subtract consecutive: `a₁ + 3a₂ = 3` and `a₁ + 5a₂ = 1`. Subtracting: `2a₂ = −2` → a₂ = −1, a₁ = 6, a₀ = 12 − 6 + 1 = 7.
**Answer:** p(t) = 7 + 6t − t².
*(This is a Vandermonde system — always uniquely solvable for distinct nodes.)*

**S1.15** Coefficient matrix determinant:
det = λ(λ² − 1) − 1(λ − 1) + 1(1 − λ) = λ³ − λ − λ + 1 + 1 − λ = λ³ − 3λ + 2 = (λ − 1)²(λ + 2).

- **λ ≠ 1 and λ ≠ −2:** det ≠ 0, **unique solution**. Solving (by symmetry or Cramer) gives
 x = −(λ+1)/(λ+2), y = 1/(λ+2), z = (λ+1)²/(λ+2).
 *(Verify for λ = 0: x = −1/2, y = 1/2, z = 1/2. Check eq 1: 0 + 1/2 + 1/2 = 1 ✓)*
- **λ = 1:** all three equations become `x + y + z = 1`. **Infinitely many solutions**, a plane: (x, y, z) = (1 − s − t, s, t).
- **λ = −2:** equations become `−2x + y + z = 1`, `x − 2y + z = −2`, `x + y − 2z = 4`. Adding all three gives `0 = 3`. **Inconsistent — no solution.**

**S1.16** Augmented:
```
[[1, 1, 0, 0, 0 | 300],
 [0, 1, −1, 1, 0 | 100],
 [0, 0, 0, 1, 1 | 400],
 [1, 0, 1, 0, 1 | 600]]
```
`R₄ → R₄ − R₁`:
```
[[1, 1,  0, 0, 0 | 300],
 [0, 1, −1, 1, 0 | 100],
 [0, 0,  0, 1, 1 | 400],
 [0, −1, 1, 0, 1 | 300]]
```
`R₄ → R₄ + R₂`:
```
[[1, 1,  0, 0, 0 | 300],
 [0, 1, −1, 1, 0 | 100],
 [0, 0,  0, 1, 1 | 400],
 [0, 0,  0, 1, 1 | 400]]
```
`R₄ → R₄ − R₃` → zero row. Pivots in columns 1, 2, 4. **Free variables: x₃ and x₅ (2 free variables).**

Let x₃ = s, x₅ = u.
- x₄ = 400 − u
- x₂ = 100 + x₃ − x₄ = 100 + s − 400 + u = s + u − 300
- x₁ = 300 − x₂ = 600 − s − u

**Range of x₄:** x₄ = 400 − u with u = x₅ ≥ 0, and x₄ ≥ 0. So 0 ≤ x₄ ≤ 400. But we also need x₂ ≥ 0, i.e. s + u ≥ 300, and x₁ ≥ 0, i.e. s + u ≤ 600. These constrain s, not x₄ directly, and s can absorb them for any u ∈ [0, 400].
**Answer:** 0 ≤ x₄ ≤ 400.

**S1.17** *Proof.* Row reduce A to echelon form. The number of pivots r is at most the number of rows m. Number of free variables = n − r ≥ n − m > 0. So at least one free variable exists; assigning it a nonzero value yields a nontrivial solution. A homogeneous system is always consistent (x = 0 works), so this solution genuinely exists. ∎

*Example.* n = 4 > m = 2.
```
[[1, 2, −1,  3 | 0],
 [2, 4,  1, −1 | 0]]
```
`R₂ → R₂ − 2R₁`: `[[1, 2, −1, 3 | 0], [0, 0, 3, −7 | 0]]`.
Free: x₂, x₄. Take x₂ = 0, x₄ = 3: then 3x₃ = 21 → x₃ = 7, and x₁ = x₃ − 3x₄ − 2x₂ = 7 − 9 = −2.
**Nontrivial solution:** (−2, 0, 7, 3). *(Check eq 2: −4 + 0 + 7 − 3 = 0 ✓)*

---
# Chapter 2 — Row Reduction and Echelon Forms

---

## 2.1 Explain Like I'm Five

Imagine a messy pile of clues about some unknown numbers. Row reduction is a **tidying algorithm**. You keep swapping, scaling, and combining the clues until the pile becomes a neat staircase, where each new clue tells you about fewer unknowns than the one above it.

The staircase looks like this:

```
* ■ ■ ■ ■
0 * ■ ■ ■
0 0 0 * ■
0 0 0 0 0
```

Each `*` is the first nonzero number in its row — the **pivot**, the corner of a stair step. Notice the rule: each stair corner sits strictly to the *right* of the one above it. Rows that are completely empty sink to the bottom.

Why is this useful? Because once you have the staircase, the *bottom* row involves the fewest unknowns, so you can solve it easily, then climb upward substituting as you go. That's called **back-substitution**.

**The two levels of tidiness:**

- **Echelon form** — you have the staircase. Good enough to read off the answer with some back-substitution work.
- **Reduced echelon form (RREF)** — you went further: made every pivot equal to 1, and cleared out everything *above* each pivot too, not just below. Now the answer is literally sitting there; you read it straight off with no substitution at all.

The extra work of RREF buys you a free answer. For hand computation on small systems, echelon + back-substitution is usually faster. For theory and for anything you need to be 100% certain about, RREF is safer because **the RREF of a matrix is unique** — two people who both do it correctly always land on the identical matrix. Plain echelon form is *not* unique; different people get different-looking staircases.

**One more idea: free variables.** After tidying, some columns have pivots and some don't. A variable whose column has a pivot is *pinned down* — it's a **basic variable**. A variable whose column has no pivot is *free* — you can set it to anything you want, and the pinned variables will adjust around it. Each free variable is one dimension of wiggle room in the answer.

---

## 2.2 The Formal Theory

### 2.2.1 Echelon Form

A rectangular matrix is in **echelon form** (or **row echelon form, REF**) if:

1. All nonzero rows are above any rows of all zeros.
2. Each leading entry (first nonzero entry) of a row is in a column strictly to the right of the leading entry of the row above it.
3. All entries in a column below a leading entry are zero.

*(Condition 3 actually follows from 2, but it is stated for emphasis.)*

A matrix is in **reduced echelon form** (**RREF**) if additionally:

4. The leading entry in each nonzero row is 1.
5. Each leading 1 is the *only* nonzero entry in its column.

**Examples.**

In echelon form but not reduced:
```
[[2, −3, 2,  1],
 [0,  1, −4, 8],
 [0,  0, 0,  5]]
```

In reduced echelon form:
```
[[1, 0, 0,  4],
 [0, 1, 0,  7],
 [0, 0, 1, −1]]
```

Not in echelon form (leading entry of row 3 is not right of row 2's):
```
[[1, 2, 3],
 [0, 0, 4],
 [0, 5, 6]]
```

### 2.2.2 Pivots

> **Definition.** A **pivot position** in a matrix A is a location that corresponds to a leading 1 in the RREF of A. A **pivot column** is a column containing a pivot position. The **pivot** is the nonzero number in a pivot position used to create zeros below it.

> **Theorem 2.1 (Uniqueness of RREF).** Each matrix is row equivalent to one and only one reduced echelon matrix.

Consequence: **pivot positions are determined by the matrix alone**, independent of the sequence of row operations used. This is why "number of pivots" is a well-defined quantity — it's the **rank** (Chapter 7).

### 2.2.3 The Row Reduction Algorithm (Gaussian / Gauss–Jordan Elimination)

**Forward Phase** (produces echelon form):

- **Step 1.** Begin with the leftmost nonzero column. This is a pivot column; the pivot position is at the top.
- **Step 2.** Select a nonzero entry in this column as pivot. If necessary, interchange rows to move it to the pivot position. *(For numerical stability on a computer, choose the entry of largest absolute value — "partial pivoting". By hand, choose 1 or the entry that keeps arithmetic clean.)*
- **Step 3.** Use row replacement to create zeros in all positions **below** the pivot.
- **Step 4.** Ignore the row containing the pivot and all rows above it. Apply Steps 1–3 to the remaining submatrix. Repeat until no nonzero rows remain to process.

**Backward Phase** (produces RREF):

- **Step 5.** Beginning with the **rightmost** pivot and working up and left, create zeros **above** each pivot. Scale each pivot row to make the pivot equal to 1.

**Gaussian elimination** = forward phase only, then back-substitute.
**Gauss–Jordan elimination** = forward + backward phase, giving RREF directly.

**Operation count.** For an n×n system, Gaussian elimination costs roughly (2/3)n³ arithmetic operations; Gauss–Jordan costs roughly n³. This is why Gaussian elimination with back-substitution is the standard for numerical work. Cramer's rule, by contrast, costs on the order of n! — catastrophically worse and never used computationally.

### 2.2.4 Basic and Free Variables

After reduction of the augmented matrix `[A | b]`:

- Variables corresponding to **pivot columns of A** are **basic** (leading, dependent).
- Variables corresponding to **non-pivot columns of A** are **free**.

> **Theorem 2.2 (Existence and Uniqueness).** A linear system is **consistent** if and only if the rightmost column of the augmented matrix is **not** a pivot column — equivalently, the echelon form has **no row of the form [0 0 ... 0 | c] with c ≠ 0**.
>
> If consistent, the solution set has
> - a **unique** solution when there are no free variables;
> - **infinitely many** solutions when there is at least one free variable.

### 2.2.5 Parametric Vector Form

To describe an infinite solution set properly:

1. Reduce to RREF.
2. Solve each basic variable in terms of the free variables.
3. Write the general solution as a vector, then split it into a constant part plus a linear combination of vectors — one vector per free variable.

**Template:** x = p + s₁v₁ + s₂v₂ + ... + s_k v_k

where p is a **particular solution** and the v's span the solution set of the associated homogeneous system `Ax = 0`.

> **Theorem 2.3 (Structure of Solution Sets).** If `Ax = b` is consistent with particular solution p, then the complete solution set is
> { p + h : h is any solution of `Ax = 0` }.

This is a hugely important idea: the solution set of an inhomogeneous system is a *translate* of the solution set of the homogeneous one. Same shape, shifted off the origin.

### 2.2.6 Homogeneous Systems

`Ax = 0` is **always consistent** — x = 0 (the **trivial solution**) always works. The only question is whether nontrivial solutions exist.

> **Theorem 2.4.** `Ax = 0` has a nontrivial solution ⟺ the system has at least one free variable ⟺ A has a non-pivot column.

**Corollary.** If A is m×n with n > m (more unknowns than equations), `Ax = 0` always has a nontrivial solution, because there can be at most m pivots but there are n columns.

---

## 2.3 Solved Examples

### Example 2.1 — [Easy] Identify the forms

Classify each matrix as (i) echelon but not reduced, (ii) reduced echelon, or (iii) neither.

(a) `[[1, 2, 0], [0, 0, 1], [0, 0, 0]]`
(b) `[[1, 3, 5], [0, 2, 4], [0, 0, 0]]`
(c) `[[0, 1, 2], [1, 0, 3], [0, 0, 0]]`
(d) `[[1, 0, 0, 5], [0, 1, 0, 2], [0, 0, 0, 0], [0, 0, 1, 3]]`

**Solution.**
(a) Leading entries are 1, and each is alone in its column. Zeros at the bottom. **Reduced echelon.**
(b) Staircase is correct, but the leading entry of row 2 is 2, not 1. **Echelon, not reduced.**
(c) Row 2's leading entry (column 1) is to the *left* of row 1's (column 2). Violates condition 2. **Neither.**
(d) A zero row sits *above* a nonzero row. Violates condition 1. **Neither.**

---

### Example 2.2 — [Easy] Full reduction to RREF

Reduce to RREF:
```
[[1, 2, −1 | 3],
 [2, 5,  1 | 7]]
```

**Solution.**
`R₂ → R₂ − 2R₁`:
```
[[1, 2, −1 | 3],
 [0, 1,  3 | 1]]
```
That's echelon form. Now backward phase: `R₁ → R₁ − 2R₂`:
```
[[1, 0, −7 | 1],
 [0, 1,  3 | 1]]
```
**RREF achieved.** Pivots in columns 1 and 2; column 3 has no pivot, so x₃ is free.

x₁ = 1 + 7x₃, x₂ = 1 − 3x₃.

**Parametric form:** x = (1, 1, 0) + t(7, −3, 1).

---

### Example 2.3 — [Medium] Complete solution in parametric vector form

Solve `Ax = b` where the augmented matrix is
```
[[ 1,  3, −5,  1,  5 |  4],
 [ 0,  1, −4,  2,  0 |  7],
 [ 0,  0,  0,  1, −1 |  2],
 [ 0,  0,  0,  0,  0 |  0]]
```

**Solution.** Already in echelon form. Pivots in columns 1, 2, 4. So x₁, x₂, x₄ are basic; **x₃ and x₅ are free**.

Backward phase. Clear above pivot in column 4. `R₂ → R₂ − 2R₃`:
Row 2: (0, 1, −4, 0, 0 − 2(−1) | 7 − 4) = (0, 1, −4, 0, 2 | 3).
`R₁ → R₁ − R₃`: Row 1: (1, 3, −5, 0, 5 + 1 | 4 − 2) = (1, 3, −5, 0, 6 | 2).

Now clear above pivot in column 2. `R₁ → R₁ − 3R₂`:
Row 1: (1, 0, −5 + 12, 0, 6 − 6 | 2 − 9) = (1, 0, 7, 0, 0 | −7).

RREF:
```
[[1, 0,  7, 0,  0 | −7],
 [0, 1, −4, 0,  2 |  3],
 [0, 0,  0, 1, −1 |  2],
 [0, 0,  0, 0,  0 |  0]]
```

Read off: x₁ = −7 − 7x₃; x₂ = 3 + 4x₃ − 2x₅; x₄ = 2 + x₅.

Let x₃ = s, x₅ = t:

**Answer:**
```
x = (−7, 3, 0, 2, 0) + s(−7, 4, 1, 0, 0) + t(0, −2, 0, 1, 1)
```

The solution set is a 2-dimensional plane in ℝ⁵, translated away from the origin by the particular solution (−7, 3, 0, 2, 0).

---

### Example 2.4 — [Medium] Homogeneous system, null space basis

Find all solutions of `Ax = 0` where A = [[3, −6, 6, 3, −9], [6, −12, 13, 9, −3], [6, −12, 14, 15, 3]].

**Solution.** (For a homogeneous system, the augmented column stays 0 throughout, so we may work with A alone.)

`R₂ → R₂ − 2R₁`, `R₃ → R₃ − 2R₁`:
```
[[3, −6,  6,  3, −9],
 [0,  0,  1,  3, 15],
 [0,  0,  2,  9, 21]]
```
`R₃ → R₃ − 2R₂`:
```
[[3, −6,  6,  3, −9],
 [0,  0,  1,  3, 15],
 [0,  0,  0,  3, −9]]
```
Scale: `R₁ → (1/3)R₁`, `R₃ → (1/3)R₃`:
```
[[1, −2,  2,  1, −3],
 [0,  0,  1,  3, 15],
 [0,  0,  0,  1, −3]]
```
Backward: `R₂ → R₂ − 3R₃` → (0,0,1,0, 15+9) = (0,0,1,0,24). `R₁ → R₁ − R₃` → (1,−2,2,0,−3+3) = (1,−2,2,0,0). Then `R₁ → R₁ − 2R₂` → (1,−2,0,0,−48).

RREF:
```
[[1, −2, 0, 0, −48],
 [0,  0, 1, 0,  24],
 [0,  0, 0, 1,  −3]]
```
Pivots: columns 1, 3, 4. Free: x₂ = s, x₅ = t.

x₁ = 2s + 48t, x₃ = −24t, x₄ = 3t.

**Answer:** x = s(2, 1, 0, 0, 0) + t(48, 0, −24, 3, 1).

The null space is 2-dimensional with basis {(2,1,0,0,0), (48,0,−24,3,1)}.

---

### Example 2.5 — [Hard] Reduction with a parameter

For what values of h and k does the system have no solution, a unique solution, or infinitely many?
```
 x₁ + 3x₂ =  2
3x₁ + hx₂ =  k
```

**Solution.** `R₂ → R₂ − 3R₁`:
```
[[1, 3   | 2    ],
 [0, h−9 | k−6  ]]
```
- If **h ≠ 9**: pivot in column 2, no free variables → **unique solution** for every k.
- If **h = 9 and k ≠ 6**: row reads `0 = k − 6 ≠ 0` → **no solution**.
- If **h = 9 and k = 6**: row is all zeros; x₂ is free → **infinitely many solutions**.

---

### Example 2.6 — [Hard] Existence for all b

Determine whether the columns of A = [[1, 3, 0, 3], [−1, −1, −1, 1], [0, −4, 2, −8], [2, 0, 3, −1]] span ℝ⁴. Equivalently, does `Ax = b` have a solution for every b?

**Solution.** By Theorem 2.2, `Ax = b` is solvable for all b ⟺ A has a pivot in **every row**.

Reduce A:
`R₂ → R₂ + R₁`, `R₄ → R₄ − 2R₁`:
```
[[1,  3,  0,  3],
 [0,  2, −1,  4],
 [0, −4,  2, −8],
 [0, −6,  3, −7]]
```
`R₃ → R₃ + 2R₂`, `R₄ → R₄ + 3R₂`:
```
[[1, 3,  0,  3],
 [0, 2, −1,  4],
 [0, 0,  0,  0],
 [0, 0,  0,  5]]
```
Swap `R₃ ↔ R₄`:
```
[[1, 3,  0, 3],
 [0, 2, −1, 4],
 [0, 0,  0, 5],
 [0, 0,  0, 0]]
```
Pivots in rows 1, 2, 3 only — **row 4 has no pivot**.

**Answer:** The columns do **not** span ℝ⁴. There exist vectors b for which `Ax = b` is inconsistent. (Rank is 3, so Col(A) is a 3-dimensional subspace of ℝ⁴.)

---

### Example 2.7 — [Very Hard] Reconstructing a matrix from its RREF data

A 3×5 matrix A has RREF
```
[[1, −2, 0, 4, 0],
 [0,  0, 1, 3, 0],
 [0,  0, 0, 0, 1]]
```
Given that the first, third, and fifth columns of A are a₁ = (1, 2, 3)ᵀ, a₃ = (0, 1, 1)ᵀ, a₅ = (2, 0, 1)ᵀ, find columns a₂ and a₄.

**Solution.** **Key principle:** row operations preserve *linear relationships among columns*. If in RREF column 2 equals −2 times column 1, then in A the same relation holds: a₂ = −2a₁.

From the RREF:
- Column 2 = −2 × (column 1). So **a₂ = −2(1, 2, 3) = (−2, −4, −6)ᵀ**.
- Column 4 = 4 × (column 1) + 3 × (column 3). So **a₄ = 4(1,2,3) + 3(0,1,1) = (4, 8, 12) + (0, 3, 3) = (4, 11, 15)ᵀ**.

**Answer:** a₂ = (−2, −4, −6)ᵀ, a₄ = (4, 11, 15)ᵀ.

So A = [[1, −2, 0, 4, 2], [2, −4, 1, 11, 0], [3, −6, 1, 15, 1]].

*Why the principle is true:* Row operations are left-multiplication by invertible matrices. If EA = R and a relation Rc = 0 holds among columns of R, then EAc = 0, and since E is invertible, Ac = 0. Same relation, same coefficients.

---

### Example 2.8 — [Very Hard] Counting possible RREFs

How many distinct 2×3 matrices in reduced echelon form are there, if we treat any nonzero entry in a non-pivot position as a "free" value (i.e. count the *patterns*)?

**Solution.** Enumerate by rank.

**Rank 0:** all zeros. → 1 pattern.

**Rank 1:** one pivot. The pivot can be in column 1, 2, or 3.
- Pivot in col 1: `[[1, *, *], [0,0,0]]` — 1 pattern
- Pivot in col 2: `[[0, 1, *], [0,0,0]]` — 1 pattern
- Pivot in col 3: `[[0, 0, 1], [0,0,0]]` — 1 pattern
→ 3 patterns.

**Rank 2:** two pivots, in columns i < j chosen from {1,2,3}: pairs (1,2), (1,3), (2,3).
- (1,2): `[[1, 0, *], [0, 1, *]]`
- (1,3): `[[1, *, 0], [0, 0, 1]]`
- (2,3): `[[0, 1, 0], [0, 0, 1]]`
→ 3 patterns.

**Answer:** 1 + 3 + 3 = **7 distinct RREF patterns**.

*Generalization:* the number of RREF patterns for an m×n matrix equals the sum over r of C(n, r) for r = 0 to min(m, n) — the number of ways to choose which columns are pivot columns. Here: C(3,0) + C(3,1) + C(3,2) = 1 + 3 + 3 = 7 ✓

---

## 2.4 Practice Numericals — Chapter 2

**[Easy]**

**P2.1** Reduce to echelon form: `[[1, 2, 3], [2, 5, 8], [3, 8, 14]]`.

**P2.2** Is `[[1, 0, 2, 0], [0, 1, −3, 0], [0, 0, 0, 1]]` in RREF? Identify pivot columns and free variables (treating the last column as part of the coefficient matrix).

**P2.3** Find the RREF of `[[2, 4], [1, 3]]`.

**P2.4** Solve using row reduction: `x + y = 3`, `2x + 4y = 8`.

**P2.5** How many pivots does `[[0, 0, 0], [0, 0, 0]]` have? What is the solution set of the corresponding homogeneous system in ℝ³?

**[Medium]**

**P2.6** Find the RREF and the general solution of
```
[[1,  2, −3, 1 | 2],
 [2,  4, −4, 6 | 10],
 [3,  6, −6, 9 | 15]]
```

**P2.7** Solve the homogeneous system and write the answer in parametric vector form:
`x₁ + 3x₂ + x₃ − x₄ = 0`, `2x₁ + 6x₂ + 3x₃ + x₄ = 0`.

**P2.8** Determine the values of a for which the system has infinitely many solutions:
`x + 2y + z = 1`, `2x + ay + 2z = 2`, `x + y + z = 0`.

**P2.9** Find a particular solution and the homogeneous solution set for
`[[1, −3, 0, 2 | 5], [0, 0, 1, 4 | 3]]`, then combine them.

**P2.10** Show that the vectors (1,2,3), (4,5,6), (7,8,9) are linearly dependent by row reducing the matrix with these as rows.

**[Hard]**

**P2.11** Find all values of h such that the following system is consistent, and describe the solution set in each case:
```
 x₁ − 3x₂ + 2x₃ = 1
2x₁ − 6x₂ + 5x₃ = 3
3x₁ − 9x₂ + hx₃ = 4
```

**P2.12** A 4×6 matrix A has rank 3. How many free variables does `Ax = 0` have? What is the maximum possible dimension of Col(A)? Can `Ax = b` be consistent for every b ∈ ℝ⁴? Justify.

**P2.13** The RREF of a 3×4 matrix B is `[[1, 0, −3, 0], [0, 1, 2, 0], [0, 0, 0, 1]]`. Given that b₁ = (2, 1, 4)ᵀ and b₂ = (1, 3, 0)ᵀ and b₄ = (0, 0, 1)ᵀ, reconstruct B.

**P2.14** Solve the system over the field of rationals and state the dimension of the solution set:
```
x₁ + x₂ − x₃ + 2x₄ − x₅ = 3
2x₁ + 3x₂ − x₃ + 5x₄ = 8
x₁ + 2x₂        + 3x₄ + x₅ = 5
```

**[Very Hard]**

**P2.15** Prove that if A is m×n and every column of A is a pivot column, then `Ax = b` has at most one solution for each b. Conversely, if `Ax = b` has at most one solution for some b for which it is consistent, show every column is a pivot column.

**P2.16** Let A be a 5×5 matrix whose RREF is the identity. Prove that for **any** b ∈ ℝ⁵ the system `Ax = b` has exactly one solution, and give an argument for why the same conclusion fails if even one column of A is a non-pivot column.

**P2.17** Consider the system with augmented matrix
```
[[1,  a,  a² | a³],
 [1,  b,  b² | b³],
 [1,  c,  c² | c³]]
```
with a, b, c distinct. Show the system has a unique solution and find it. (Hint: this is a Vandermonde system — think about a polynomial with known roots.)

**P2.18** How many distinct 3×3 matrices in reduced echelon form exist (counting patterns, as in Example 2.8)? Verify your answer against the binomial-sum formula.

---

## 2.5 Solutions to Chapter 2 Practice

**S2.1** `R₂ → R₂ − 2R₁`, `R₃ → R₃ − 3R₁`:
```
[[1, 2, 3],
 [0, 1, 2],
 [0, 2, 5]]
```
`R₃ → R₃ − 2R₂`:
```
[[1, 2, 3],
 [0, 1, 2],
 [0, 0, 1]]
```
Echelon form, 3 pivots. (In fact this matrix is invertible.)

**S2.2** Yes, it is in RREF: leading 1s in columns 1, 2, 4, each alone in its column, staircase descending. **Pivot columns: 1, 2, 4. Free: column 3.**

**S2.3** Swap to get a leading 1: `R₁ ↔ R₂` → `[[1, 3], [2, 4]]`. `R₂ → R₂ − 2R₁` → `[[1, 3], [0, −2]]`. `R₂ → −(1/2)R₂` → `[[1, 3], [0, 1]]`. `R₁ → R₁ − 3R₂` → `[[1, 0], [0, 1]]`.
**RREF = I₂.**

**S2.4** `[[1, 1 | 3], [2, 4 | 8]]`. `R₂ − 2R₁` → `[[1,1|3],[0,2|2]]`. So y = 1, x = 2.
**Answer:** (2, 1).

**S2.5** **Zero pivots.** Every variable is free, so the solution set of the homogeneous system is **all of ℝ³** — dimension 3.

**S2.6** `R₂ → R₂ − 2R₁`, `R₃ → R₃ − 3R₁`:
```
[[1, 2, −3, 1 | 2],
 [0, 0,  2, 4 | 6],
 [0, 0,  3, 6 | 9]]
```
`R₂ → (1/2)R₂` → (0,0,1,2|3). `R₃ → R₃ − 3R₂` → zero row.
`R₁ → R₁ + 3R₂` → (1, 2, 0, 1+6 | 2+9) = (1, 2, 0, 7 | 11).
**RREF:**
```
[[1, 2, 0, 7 | 11],
 [0, 0, 1, 2 |  3],
 [0, 0, 0, 0 |  0]]
```
Free: x₂ = s, x₄ = t. x₁ = 11 − 2s − 7t, x₃ = 3 − 2t.
**Answer:** x = (11, 0, 3, 0) + s(−2, 1, 0, 0) + t(−7, 0, −2, 1).

**S2.7**
```
[[1, 3, 1, −1],
 [2, 6, 3,  1]]
```
`R₂ − 2R₁` → (0, 0, 1, 3). `R₁ → R₁ − R₂` → (1, 3, 0, −4).
Free: x₂ = s, x₄ = t. x₁ = −3s + 4t, x₃ = −3t.
**Answer:** x = s(−3, 1, 0, 0) + t(4, 0, −3, 1).

**S2.8**
```
[[1, 2, 1 | 1],
 [2, a, 2 | 2],
 [1, 1, 1 | 0]]
```
`R₂ − 2R₁` → (0, a−4, 0 | 0). `R₃ − R₁` → (0, −1, 0 | −1).
Swap so the −1 row is second:
```
[[1,  2,   1 |  1],
 [0, −1,   0 | −1],
 [0, a−4,  0 |  0]]
```
From row 2: y = 1. Row 3: (a−4)(1) = 0 requires **a = 4** for consistency of that row... careful: row 3 reads (a−4)y = 0, and y = 1, so we need a = 4.
- If a = 4: row 3 vanishes. Then y = 1, and x + z = 1 − 2 = −1 with z free. **Infinitely many solutions.**
- If a ≠ 4: row 3 gives (a−4) = 0, contradiction → **no solution**.

**Answer:** a = 4.

**S2.9** RREF already (pivots in columns 1 and 3). Free: x₂ = s, x₄ = t.
x₁ = 5 + 3s − 2t, x₃ = 3 − 4t.
**Particular:** p = (5, 0, 3, 0).
**Homogeneous:** span{(3, 1, 0, 0), (−2, 0, −4, 1)}.
**Combined:** x = (5,0,3,0) + s(3,1,0,0) + t(−2,0,−4,1).

**S2.10**
```
[[1, 2, 3],
 [4, 5, 6],
 [7, 8, 9]]
```
`R₂ − 4R₁`, `R₃ − 7R₁`:
```
[[1,  2,   3],
 [0, −3,  −6],
 [0, −6, −12]]
```
`R₃ − 2R₂` → zero row. Only **2 pivots** for 3 vectors → **linearly dependent**. Indeed v₁ − 2v₂ + v₃ = (1−8+7, 2−10+8, 3−12+9) = (0,0,0).

**S2.11**
```
[[1, −3, 2 | 1],
 [2, −6, 5 | 3],
 [3, −9, h | 4]]
```
`R₂ − 2R₁`, `R₃ − 3R₁`:
```
[[1, −3, 2   | 1],
 [0,  0, 1   | 1],
 [0,  0, h−6 | 1]]
```
`R₃ → R₃ − (h−6)R₂`: RHS becomes 1 − (h−6) = 7 − h. Row 3 is `0 = 7 − h`.
- **h = 7:** consistent. Then x₃ = 1, x₁ = 1 + 3x₂ − 2 = 3x₂ − 1, x₂ free.
 Solution set: x = (−1, 0, 1) + s(3, 1, 0) — a **line** in ℝ³.
- **h ≠ 7:** **inconsistent.**

**S2.12** rank 3 → 3 pivots. n = 6 columns, so **free variables = 6 − 3 = 3**.
dim Col(A) = rank = **3**.
`Ax = b` consistent for every b ∈ ℝ⁴ would require a pivot in every one of the 4 rows, i.e. rank 4. Since rank is 3, **no** — there exist b making the system inconsistent. Col(A) is a proper 3-dimensional subspace of ℝ⁴.

**S2.13** Relations from RREF: column 3 = −3(col 1) + 2(col 2).
b₃ = −3(2, 1, 4) + 2(1, 3, 0) = (−6, −3, −12) + (2, 6, 0) = (−4, 3, −12)ᵀ.
**B = [[2, 1, −4, 0], [1, 3, 3, 0], [4, 0, −12, 1]].**

**S2.14**
```
[[1, 1, −1, 2, −1 | 3],
 [2, 3, −1, 5,  0 | 8],
 [1, 2,  0, 3,  1 | 5]]
```
`R₂ − 2R₁`, `R₃ − R₁`:
```
[[1, 1, −1, 2, −1 | 3],
 [0, 1,  1, 1,  2 | 2],
 [0, 1,  1, 1,  2 | 2]]
```
`R₃ − R₂` → zero row. `R₁ − R₂`:
```
[[1, 0, −2, 1, −3 | 1],
 [0, 1,  1, 1,  2 | 2],
 [0, 0,  0, 0,  0 | 0]]
```
Pivots: columns 1, 2. Free: x₃ = r, x₄ = s, x₅ = t → **3 free variables**.
x₁ = 1 + 2r − s + 3t, x₂ = 2 − r − s − 2t.
**Answer:** x = (1,2,0,0,0) + r(2,−1,1,0,0) + s(−1,−1,0,1,0) + t(3,−2,0,0,1).
**Dimension of solution set = 3.**

**S2.15**
*Forward.* If every column is a pivot column, there are no free variables. Suppose u and v both solve `Ax = b`. Then A(u − v) = b − b = 0, so u − v solves the homogeneous system. But with no free variables the homogeneous system has only the trivial solution, so u − v = 0, i.e. u = v. At most one solution. ∎

*Converse.* Suppose some column j is not a pivot column. Then `Ax = 0` has a nontrivial solution h ≠ 0 (set x_j = 1). If `Ax = b` is consistent with solution p, then p + h is a *different* solution, since h ≠ 0. So there would be at least two solutions — contradicting "at most one". Hence every column must be a pivot column. ∎

**S2.16** RREF(A) = I₅ means A has 5 pivots — one in every row and every column.
- Pivot in every **row** ⟹ the augmented matrix can never have a row `[0...0 | c≠0]` ⟹ consistent for every b (Theorem 2.2).
- Pivot in every **column** ⟹ no free variables ⟹ unique when it exists.
Together: exactly one solution for every b. ∎

If one column were non-pivot, then since A is square with 5 columns, only ≤ 4 pivots exist, so some row lacks a pivot too. That row produces a possible `0 = c ≠ 0` for suitable b, so consistency fails for some b; and the non-pivot column gives a free variable, so when consistent the solution is non-unique. Both conclusions break simultaneously. ∎

**S2.17** Write the system as: for each root r ∈ {a, b, c},
`x₀ + x₁r + x₂r² = r³`.

Define the polynomial q(r) = r³ − x₂r² − x₁r − x₀. The three equations say precisely that q(a) = q(b) = q(c) = 0.

Since q is monic of degree 3 with three distinct roots a, b, c:

q(r) = (r − a)(r − b)(r − c) = r³ − (a+b+c)r² + (ab+bc+ca)r − abc.

Matching coefficients:
- −x₂ = −(a+b+c) → **x₂ = a + b + c**
- −x₁ = ab + bc + ca → **x₁ = −(ab + bc + ca)**
- −x₀ = −abc → **x₀ = abc**

Uniqueness: the coefficient matrix is the Vandermonde matrix with determinant (b−a)(c−a)(c−b) ≠ 0 since a, b, c are distinct. Nonzero determinant ⟹ unique solution. ∎

**S2.18** By the pivot-column-selection argument: choose which columns are pivot columns, with rank r ≤ min(3,3) = 3.
- r = 0: C(3,0) = 1
- r = 1: C(3,1) = 3
- r = 2: C(3,2) = 3
- r = 3: C(3,3) = 1

**Total = 1 + 3 + 3 + 1 = 8 distinct RREF patterns.**

Formula check: Σ_{r=0}^{3} C(3, r) = 2³ = 8 ✓ (For m×n with m ≥ n, the total is 2ⁿ.)

---
# Chapter 3 — Matrix Operations and Matrix Inverses

---

## 3.1 Explain Like I'm Five

A matrix is a **machine that takes a vector in and spits a vector out**. Feed it an arrow, it hands you back a (usually different) arrow.

**Adding matrices** is easy — it's like adding two shopping lists item by item. You can only do it if the lists have the same shape.

**Multiplying a matrix by a number** scales every entry. Also easy.

**Multiplying two matrices** is the strange one, and here's why it's defined the way it is: `AB` means *"do B first, then do A."* It's the machine you get by bolting two machines together in a row. Because of that, the number of outputs of B must equal the number of inputs of A — that's the rule that (n×**p**) times (**p**×m) works, and the inner numbers must match.

**Order matters.** Putting on socks then shoes is not the same as shoes then socks. So `AB ≠ BA` in general. This is the single biggest difference from ordinary number arithmetic, and it breaks a lot of habits. `(A + B)² ≠ A² + 2AB + B²` because you can't merge `AB` and `BA` into `2AB`.

**The identity matrix `I`** is the do-nothing machine. Feed it an arrow, get the same arrow back. It has 1s down the diagonal and 0s everywhere else. It plays the role that the number 1 plays for ordinary multiplication.

**The inverse `A⁻¹`** is the *undo* machine. If A stretches and rotates your arrow, A⁻¹ un-stretches and un-rotates it, giving you back exactly what you started with: `A⁻¹A = I`.

**Not every machine can be undone.** If A squashes all of 3D space flat onto a plane, information is lost forever — two different input arrows landed on the same output arrow, and no machine can un-mix them. Such a matrix is called **singular** or **non-invertible**. The determinant (Chapter 7) is exactly the number that detects whether squashing happened: det = 0 means squashed.

**The transpose `Aᵀ`** just flips the matrix across its main diagonal — rows become columns. It looks like a trivial bookkeeping operation but it turns out to encode something deep about dot products: `(Ax) · y = x · (Aᵀy)`.

---

## 3.2 The Formal Theory

### 3.2.1 Basic Operations

Let A = [aᵢⱼ] and B = [bᵢⱼ] be m×n matrices, c a scalar.

- **Sum:** (A + B)ᵢⱼ = aᵢⱼ + bᵢⱼ. Defined only when shapes match.
- **Scalar multiple:** (cA)ᵢⱼ = c·aᵢⱼ.
- **Zero matrix 0:** all entries zero; A + 0 = A.

**Algebraic laws (all straightforward):**
1. A + B = B + A
2. (A + B) + C = A + (B + C)
3. A + 0 = A
4. c(A + B) = cA + cB
5. (c + d)A = cA + dA
6. c(dA) = (cd)A

### 3.2.2 Matrix Multiplication

If A is m×n and B is n×p, then AB is m×p with

> (AB)ᵢⱼ = Σₖ aᵢₖ bₖⱼ = (row i of A) · (column j of B)

**Three equivalent views — know all three:**

**(1) Entry-by-entry (dot product view).** Entry (i,j) is row i of A dotted with column j of B.

**(2) Column view.** AB = A[b₁ b₂ ... b_p] = [Ab₁ Ab₂ ... Ab_p]. Each column of AB is A applied to the corresponding column of B. *This is the most useful view for theory.*

**(3) Composition view.** If A and B represent linear maps T_A and T_B, then AB represents T_A ∘ T_B.

Also useful: **Ax is a linear combination of the columns of A**, with weights from x:

> A x = x₁a₁ + x₂a₂ + ... + xₙaₙ

This single identity converts every question about `Ax = b` into a question about linear combinations of columns.

**Properties of multiplication (A is m×n):**
1. A(BC) = (AB)C — associative
2. A(B + C) = AB + AC — left distributive
3. (B + C)A = BA + CA — right distributive
4. c(AB) = (cA)B = A(cB)
5. Iₘ A = A = A Iₙ

**Properties that FAIL — memorize these:**
1. **AB ≠ BA** in general (non-commutative).
2. **AB = AC does NOT imply B = C** (no cancellation law).
3. **AB = 0 does NOT imply A = 0 or B = 0** (zero divisors exist).

*Counterexamples:*
- A = [[1,0],[0,0]], B = [[0,1],[0,0]]: AB = [[0,1],[0,0]] but BA = [[0,0],[0,0]]. So AB ≠ BA.
- A = [[1,0],[0,0]], B = [[0,0],[0,1]]: AB = 0 though neither is zero.

### 3.2.3 Powers and Special Matrices

`Aᵏ = A·A···A` (k factors), defined only for square A. By convention A⁰ = I.

| Type | Definition |
|---|---|
| **Diagonal** | aᵢⱼ = 0 for i ≠ j |
| **Upper triangular** | aᵢⱼ = 0 for i > j |
| **Lower triangular** | aᵢⱼ = 0 for i < j |
| **Symmetric** | Aᵀ = A |
| **Skew-symmetric** | Aᵀ = −A (forces zero diagonal) |
| **Orthogonal** | AᵀA = I, i.e. A⁻¹ = Aᵀ |
| **Idempotent** | A² = A |
| **Nilpotent** | Aᵏ = 0 for some k ≥ 1 |
| **Involutory** | A² = I |

### 3.2.4 Transpose

(Aᵀ)ᵢⱼ = aⱼᵢ. If A is m×n, Aᵀ is n×m.

**Rules:**
1. (Aᵀ)ᵀ = A
2. (A + B)ᵀ = Aᵀ + Bᵀ
3. (cA)ᵀ = cAᵀ
4. **(AB)ᵀ = Bᵀ Aᵀ** ← the order reverses. Most commonly botched rule in the subject.
5. (A⁻¹)ᵀ = (Aᵀ)⁻¹

**Useful facts:** For any A, both AᵀA and AAᵀ are symmetric. Any square matrix splits uniquely as symmetric + skew-symmetric:

> A = ½(A + Aᵀ) + ½(A − Aᵀ)

### 3.2.5 The Inverse

> **Definition.** A square n×n matrix A is **invertible** (or **nonsingular**) if there exists an n×n matrix C with `AC = CA = Iₙ`. Then C is unique, written A⁻¹.

*Uniqueness proof:* If B and C both work, B = BI = B(AC) = (BA)C = IC = C. ∎

**2×2 formula.** For A = [[a, b], [c, d]] with det A = ad − bc ≠ 0:

> A⁻¹ = (1/(ad − bc)) · [[d, −b], [−c, a]]

(Swap the diagonal entries, negate the off-diagonal ones, divide by the determinant.) If ad − bc = 0, A is **not** invertible.

**Rules for inverses:**
1. (A⁻¹)⁻¹ = A
2. **(AB)⁻¹ = B⁻¹A⁻¹** ← order reverses again
3. (Aᵀ)⁻¹ = (A⁻¹)ᵀ
4. (cA)⁻¹ = (1/c)A⁻¹ for c ≠ 0
5. (Aᵏ)⁻¹ = (A⁻¹)ᵏ

**Solving with the inverse.** If A is invertible, `Ax = b` has the unique solution `x = A⁻¹b`.

*Caution:* this is a theoretical statement, not a computational recipe. Computing A⁻¹ then multiplying costs about 3× more than Gaussian elimination and is numerically less stable. Never invert a matrix on a computer just to solve one system.

### 3.2.6 Computing the Inverse by Row Reduction

**Algorithm.** Form the augmented block matrix `[A | I]`. Row reduce. If A reduces to I, then

> [A | I] ~ [I | A⁻¹]

If A cannot be reduced to I (a zero row appears), A is **not invertible**.

*Why it works:* row reducing is left-multiplication by elementary matrices E₁, E₂, ..., E_k. If E_k···E₁A = I, then E_k···E₁ = A⁻¹, and those same operations applied to I produce exactly E_k···E₁I = A⁻¹.

### 3.2.7 Elementary Matrices

An **elementary matrix** E is obtained by performing a single elementary row operation on I. Performing that operation on any matrix A is the same as computing EA.

Every elementary matrix is invertible, and its inverse is the elementary matrix of the reverse operation.

> **Theorem 3.1.** A is invertible ⟺ A is a product of elementary matrices.

### 3.2.8 The Invertible Matrix Theorem

This is the central theorem of Unit 1. **Memorize it.** For an n×n matrix A, the following are **equivalent** — all true together or all false together:

> **(a)** A is invertible.
> **(b)** A is row equivalent to Iₙ.
> **(c)** A has n pivot positions.
> **(d)** `Ax = 0` has only the trivial solution.
> **(e)** The columns of A are linearly independent.
> **(f)** The linear transformation x ↦ Ax is one-to-one (injective).
> **(g)** `Ax = b` has at least one solution for every b ∈ ℝⁿ.
> **(h)** The columns of A span ℝⁿ.
> **(i)** x ↦ Ax maps ℝⁿ onto ℝⁿ (surjective).
> **(j)** There is an n×n matrix C with CA = I.
> **(k)** There is an n×n matrix D with AD = I.
> **(l)** Aᵀ is invertible.
> **(m)** det A ≠ 0.
> **(n)** rank A = n.
> **(o)** Nul A = {0}, i.e. nullity = 0.
> **(p)** Col A = ℝⁿ.
> **(q)** 0 is **not** an eigenvalue of A.
> **(r)** The columns of A form a basis of ℝⁿ.

**Critical caveat:** this theorem applies **only to square matrices**. For non-square matrices, "one-to-one" and "onto" come apart completely.

**A powerful consequence:** for square A, a one-sided inverse is automatically two-sided. If AD = I with both square, then D = A⁻¹ and DA = I follows for free. (This fails for non-square matrices.)

### 3.2.9 Partitioned (Block) Matrices

Matrices can be split into blocks and multiplied blockwise, provided the partitions are conformable:

```
[[A₁₁, A₁₂],   [[B₁₁, B₁₂],     [[A₁₁B₁₁ + A₁₂B₂₁ ,  A₁₁B₁₂ + A₁₂B₂₂],
 [A₂₁, A₂₂]] ·  [B₂₁, B₂₂]]  =   [A₂₁B₁₁ + A₂₂B₂₁ ,  A₂₁B₁₂ + A₂₂B₂₂]]
```

**Block diagonal inverse:** if A = diag(A₁, A₂) with each Aᵢ invertible, then A⁻¹ = diag(A₁⁻¹, A₂⁻¹).

**Block upper-triangular inverse:**
```
[[A, B],      [[A⁻¹, −A⁻¹BC⁻¹],
 [0, C]]⁻¹ =   [0,    C⁻¹     ]]
```

### 3.2.10 LU Factorization

If A can be reduced to echelon form using only row-replacement operations that add multiples of a row to rows *below* it, then

> A = LU

where L is **unit lower triangular** (1s on the diagonal) and U is the echelon form (upper triangular).

**Building L:** the (i,j) entry of L (for i > j) is the *negative of the multiplier* used to eliminate position (i,j). If you did `Rᵢ → Rᵢ − 3Rⱼ`, then Lᵢⱼ = 3.

**Why it matters:** to solve `Ax = b`, write `LUx = b`, then
1. Solve `Ly = b` by forward substitution (cheap, O(n²)).
2. Solve `Ux = y` by back substitution (cheap, O(n²)).

The expensive O(n³) factorization is done **once**; every subsequent right-hand side costs only O(n²). This is the standard workhorse of numerical linear algebra.

If row interchanges are needed, one gets `PA = LU` with P a permutation matrix.

---

## 3.3 Solved Examples

### Example 3.1 — [Easy] Basic products

Given A = [[2, 1], [3, −1]], B = [[1, 0, 2], [−1, 3, 1]], compute AB. Is BA defined?

**Solution.** A is 2×2, B is 2×3. Inner dimensions match (2 = 2), so AB is **2×3**.

Row 1 of A is (2, 1):
- with col 1 of B (1, −1): 2(1) + 1(−1) = 1
- with col 2 (0, 3): 2(0) + 1(3) = 3
- with col 3 (2, 1): 2(2) + 1(1) = 5

Row 2 of A is (3, −1):
- col 1: 3(1) + (−1)(−1) = 4
- col 2: 3(0) + (−1)(3) = −3
- col 3: 3(2) + (−1)(1) = 5

**AB = [[1, 3, 5], [4, −3, 5]].**

BA: B is 2×3, A is 2×2. Inner dimensions 3 ≠ 2. **BA is not defined.**

---

### Example 3.2 — [Easy] 2×2 inverse

Find the inverse of A = [[4, 7], [2, 6]].

**Solution.** det A = (4)(6) − (7)(2) = 24 − 14 = 10 ≠ 0, so A is invertible.

A⁻¹ = (1/10)[[6, −7], [−2, 4]] = **[[0.6, −0.7], [−0.2, 0.4]]**.

**Check:** A·A⁻¹ = (1/10)[[4(6)+7(−2), 4(−7)+7(4)], [2(6)+6(−2), 2(−7)+6(4)]] = (1/10)[[10, 0], [0, 10]] = I ✓

---

### Example 3.3 — [Medium] Inverse by row reduction

Find A⁻¹ for A = [[1, 2, 3], [2, 5, 3], [1, 0, 8]].

**Solution.** Form [A | I]:
```
[[1, 2, 3 | 1, 0, 0],
 [2, 5, 3 | 0, 1, 0],
 [1, 0, 8 | 0, 0, 1]]
```
`R₂ → R₂ − 2R₁`, `R₃ → R₃ − R₁`:
```
[[1,  2,  3 |  1, 0, 0],
 [0,  1, −3 | −2, 1, 0],
 [0, −2,  5 | −1, 0, 1]]
```
`R₃ → R₃ + 2R₂`:
```
[[1, 2,  3 |  1, 0, 0],
 [0, 1, −3 | −2, 1, 0],
 [0, 0, −1 | −5, 2, 1]]
```
`R₃ → −R₃`:
```
[[1, 2,  3 |  1,  0,  0],
 [0, 1, −3 | −2,  1,  0],
 [0, 0,  1 |  5, −2, −1]]
```
`R₂ → R₂ + 3R₃`: (0,1,0 | −2+15, 1−6, 0−3) = (0,1,0 | 13, −5, −3).
`R₁ → R₁ − 3R₃`: (1,2,0 | 1−15, 0+6, 0+3) = (1,2,0 | −14, 6, 3).
`R₁ → R₁ − 2R₂`: (1,0,0 | −14−26, 6+10, 3+6) = (1,0,0 | −40, 16, 9).

```
[[1, 0, 0 | −40,  16,   9],
 [0, 1, 0 |  13,  −5,  −3],
 [0, 0, 1 |   5,  −2,  −1]]
```

**A⁻¹ = [[−40, 16, 9], [13, −5, −3], [5, −2, −1]].**

**Check (row 1 of A times column 1 of A⁻¹):** 1(−40) + 2(13) + 3(5) = −40 + 26 + 15 = 1 ✓

---

### Example 3.4 — [Medium] Matrix equation manipulation

Solve for X: `AXB = C`, where A and B are invertible.

**Solution.** Left-multiply by A⁻¹ and right-multiply by B⁻¹ — **and keep the sides straight**:

A⁻¹(AXB)B⁻¹ = A⁻¹CB⁻¹
(A⁻¹A)X(BB⁻¹) = A⁻¹CB⁻¹
IXI = A⁻¹CB⁻¹

**X = A⁻¹CB⁻¹.**

Note that writing `X = C/(AB)` is meaningless — there is no matrix division, and the answer is *not* (AB)⁻¹C.

---

### Example 3.5 — [Medium] Transpose gymnastics

Simplify `(AᵀB)ᵀ − Bᵀ(A + A)ᵀ + 2(BA)ᵀ` assuming all products are defined and A, B are n×n.

**Solution.**
- `(AᵀB)ᵀ = Bᵀ(Aᵀ)ᵀ = BᵀA`
- `(A + A)ᵀ = (2A)ᵀ = 2Aᵀ`, so `Bᵀ(A+A)ᵀ = 2BᵀAᵀ`
- `(BA)ᵀ = AᵀBᵀ`, so `2(BA)ᵀ = 2AᵀBᵀ`

Total: `BᵀA − 2BᵀAᵀ + 2AᵀBᵀ`.

No further simplification is possible in general — `BᵀAᵀ` and `AᵀBᵀ` are different matrices unless A and B commute. **Answer: BᵀA − 2BᵀAᵀ + 2AᵀBᵀ.**

---

### Example 3.6 — [Hard] Proving invertibility algebraically

Suppose A satisfies `A² − 3A + 2I = 0`. Show A is invertible and find A⁻¹ in terms of A.

**Solution.** Rearrange: `A² − 3A = −2I`, so `A(A − 3I) = −2I`, hence

`A · [−(1/2)(A − 3I)] = I`.

Since A is square and we have found D with AD = I, by the Invertible Matrix Theorem (part k), A is invertible with

**A⁻¹ = −(1/2)(A − 3I) = (1/2)(3I − A).**

**Sanity check via eigenvalues:** the relation says λ² − 3λ + 2 = 0 for every eigenvalue, so λ ∈ {1, 2}. Neither is 0, confirming invertibility (IMT part q). And 1/λ = (3 − λ)/2 gives 1/1 = 1 ✓ and 1/2 = 1/2 ✓.

---

### Example 3.7 — [Hard] LU factorization

Find the LU factorization of A = [[2, 4, −1], [4, 9, −3], [−2, −3, 7]] and use it to solve `Ax = (5, 8, 3)ᵀ`.

**Solution.**

**Step 1 — Reduce to U, recording multipliers.**

`R₂ → R₂ − 2R₁` (multiplier 2), `R₃ → R₃ − (−1)R₁` i.e. `R₃ → R₃ + R₁` (multiplier −1):
```
[[2, 4, −1],
 [0, 1, −1],
 [0, 1,  6]]
```
`R₃ → R₃ − 1·R₂` (multiplier 1):
```
U = [[2, 4, −1],
     [0, 1, −1],
     [0, 0,  7]]
```

**Step 2 — Assemble L** from the multipliers (entry Lᵢⱼ = multiplier used to kill position (i,j)):

```
L = [[ 1, 0, 0],
     [ 2, 1, 0],
     [−1, 1, 1]]
```

**Verify:** LU row 3 = −1·(2,4,−1) + 1·(0,1,−1) + 1·(0,0,7) = (−2, −4+1, 1−1+7) = (−2, −3, 7) ✓

**Step 3 — Solve `Ly = b` (forward substitution), b = (5, 8, 3)ᵀ.**
- y₁ = 5
- 2y₁ + y₂ = 8 → y₂ = 8 − 10 = −2
- −y₁ + y₂ + y₃ = 3 → −5 − 2 + y₃ = 3 → y₃ = 10

**Step 4 — Solve `Ux = y` (back substitution), y = (5, −2, 10)ᵀ.**
- 7x₃ = 10 → x₃ = 10/7
- x₂ − x₃ = −2 → x₂ = −2 + 10/7 = −4/7
- 2x₁ + 4x₂ − x₃ = 5 → 2x₁ − 16/7 − 10/7 = 5 → 2x₁ = 5 + 26/7 = 61/7 → x₁ = 61/14

**Answer:** x = (61/14, −4/7, 10/7)ᵀ.

---

### Example 3.8 — [Very Hard] Block matrix inverse

Let M = [[A, B], [0, C]] where A is p×p invertible, C is q×q invertible, B is p×q. Find M⁻¹.

**Solution.** Guess the same block-triangular shape: M⁻¹ = [[X, Y], [0, Z]]. Then

```
[[A, B], [0, C]] · [[X, Y], [0, Z]] = [[AX, AY + BZ], [0, CZ]]
```

Set equal to [[I_p, 0], [0, I_q]]:
- AX = I_p → **X = A⁻¹**
- CZ = I_q → **Z = C⁻¹**
- AY + BZ = 0 → AY = −BC⁻¹ → **Y = −A⁻¹BC⁻¹**

**Answer:**
```
M⁻¹ = [[A⁻¹, −A⁻¹BC⁻¹],
       [0,    C⁻¹      ]]
```

**Numerical instance.** A = [[2]], B = [[3]], C = [[5]] (all 1×1):
M = [[2, 3], [0, 5]]. Formula gives M⁻¹ = [[1/2, −(1/2)(3)(1/5)], [0, 1/5]] = [[1/2, −3/10], [0, 1/5]].
Check against the 2×2 formula: det = 10, so M⁻¹ = (1/10)[[5, −3], [0, 2]] = [[1/2, −3/10], [0, 1/5]] ✓

---

### Example 3.9 — [Very Hard] Sherman–Morrison style rank-one update

Let A be invertible n×n and let u, v be column vectors with `1 + vᵀA⁻¹u ≠ 0`. Show that

> (A + uvᵀ)⁻¹ = A⁻¹ − (A⁻¹u vᵀ A⁻¹)/(1 + vᵀA⁻¹u)

**Solution.** Write α = 1 + vᵀA⁻¹u (a **scalar**). Let B denote the proposed inverse. Multiply:

(A + uvᵀ)B = (A + uvᵀ)[A⁻¹ − (A⁻¹uvᵀA⁻¹)/α]

Expand the four terms:
1. `A·A⁻¹ = I`
2. `−A·(A⁻¹uvᵀA⁻¹)/α = −(uvᵀA⁻¹)/α`
3. `uvᵀA⁻¹`
4. `−uvᵀ(A⁻¹uvᵀA⁻¹)/α = −u(vᵀA⁻¹u)vᵀA⁻¹/α = −(α−1)·uvᵀA⁻¹/α`

*(In term 4 we used that `vᵀA⁻¹u` is a 1×1 scalar and can be pulled out, and it equals α − 1.)*

Sum terms 2, 3, 4:
uvᵀA⁻¹ · [−1/α + 1 − (α−1)/α] = uvᵀA⁻¹ · [(−1 + α − α + 1)/α] = uvᵀA⁻¹ · 0 = 0.

So (A + uvᵀ)B = I. Since everything is square, B = (A + uvᵀ)⁻¹. ∎

**Why this is useful:** updating a model with one new data point changes A by a rank-one term. Rather than re-inverting from scratch at O(n³), this formula updates the inverse at O(n²). It is the engine behind recursive least squares and the Kalman filter.

---

## 3.4 Practice Numericals — Chapter 3

**[Easy]**

**P3.1** A = [[1, −2], [3, 4]], B = [[0, 5], [−1, 2]]. Compute A + B, 3A, AB, BA. Verify AB ≠ BA.

**P3.2** Find the inverse of [[3, 5], [1, 2]].

**P3.3** Compute Aᵀ and verify (AB)ᵀ = BᵀAᵀ for A = [[1, 2], [0, 1]], B = [[2, 0], [1, 3]].

**P3.4** Determine whether [[2, 4], [1, 2]] is invertible.

**P3.5** If A = diag(2, −3, 5), find A⁻¹ and A³.

**[Medium]**

**P3.6** Find the inverse of [[1, 0, 2], [2, −1, 3], [4, 1, 8]] by row reduction.

**P3.7** Solve for X: `AX + B = 3X`, given A = [[2, 0], [0, 2]], B = [[1, 1], [1, 1]].

**P3.8** Show that if A and B are symmetric n×n matrices, then AB is symmetric **if and only if** AB = BA.

**P3.9** Find all 2×2 matrices A with A² = I.

**P3.10** Compute the LU factorization of [[1, 2], [3, 8]] and solve `Ax = (3, 13)ᵀ`.

**P3.11** If A is 3×3 with A³ = 0, show that I − A is invertible and find its inverse.

**[Hard]**

**P3.12** Let A = [[1, 1], [0, 1]]. Find a formula for Aⁿ and prove it by induction.

**P3.13** Find the LU factorization of A = [[2, −1, 1], [4, 1, 0], [−2, 5, 3]] and use it to solve `Ax = (1, 3, 5)ᵀ`.

**P3.14** Prove: if A is m×n and AᵀA is invertible, then the columns of A are linearly independent. Is the converse true?

**P3.15** Let A be n×n with A² = A (idempotent) and A ≠ I. Show A is not invertible.

**P3.16** Suppose A, B are n×n and AB is invertible. Prove both A and B are invertible. Show by counterexample that this fails if A and B are not square.

**[Very Hard]**

**P3.17** Let A = [[0, 1, 0], [0, 0, 1], [0, 0, 0]]. Compute A², A³. Show I + A + A² is the inverse of I − A, and generalize to any nilpotent N with N^k = 0.

**P3.18** Find the inverse of the n×n matrix with 1s on and above the diagonal and 0s below (the "upper-triangular all-ones" matrix). Do it for n = 4 explicitly, then state the general pattern.

**P3.19** Prove the block formula for the inverse of [[A, B], [C, D]] when A and the **Schur complement** S = D − CA⁻¹B are both invertible:
```
[[A, B], [C, D]]⁻¹ = [[A⁻¹ + A⁻¹BS⁻¹CA⁻¹, −A⁻¹BS⁻¹],
                      [−S⁻¹CA⁻¹,            S⁻¹      ]]
```
Then apply it to [[1, 2, 0], [3, 4, 1], [0, 1, 2]] partitioned with A the top-left 2×2 block.

**P3.20** Let A be a 3×3 matrix with `A⁴ = 2A³ − A²`. Determine all possible values of det A, and state whether A must be singular.

---

## 3.5 Solutions to Chapter 3 Practice

**S3.1**
- A + B = [[1, 3], [2, 6]]
- 3A = [[3, −6], [9, 12]]
- AB: row1 = (1(0) + (−2)(−1), 1(5) + (−2)(2)) = (2, 1); row2 = (3(0)+4(−1), 3(5)+4(2)) = (−4, 23).
 **AB = [[2, 1], [−4, 23]]**
- BA: row1 = (0(1)+5(3), 0(−2)+5(4)) = (15, 20); row2 = (−1(1)+2(3), −1(−2)+2(4)) = (5, 10).
 **BA = [[15, 20], [5, 10]]**
Clearly AB ≠ BA. ✓

**S3.2** det = 3(2) − 5(1) = 1. Inverse = (1/1)[[2, −5], [−1, 3]] = **[[2, −5], [−1, 3]]**.

**S3.3** Aᵀ = [[1, 0], [2, 1]]. AB = [[1(2)+2(1), 1(0)+2(3)], [0(2)+1(1), 0(0)+1(3)]] = [[4, 6], [1, 3]].
(AB)ᵀ = [[4, 1], [6, 3]].
BᵀAᵀ = [[2, 1], [0, 3]]·[[1, 0], [2, 1]] = [[2+2, 0+1], [0+6, 0+3]] = [[4, 1], [6, 3]] ✓

**S3.4** det = 2(2) − 4(1) = 0. **Not invertible.** (Row 2 is half of row 1.)

**S3.5** A⁻¹ = diag(1/2, −1/3, 1/5). A³ = diag(8, −27, 125).
*(For diagonal matrices, every operation acts entrywise on the diagonal — this is exactly why diagonalization is so powerful.)*

**S3.6** [A | I]:
```
[[1,  0, 2 | 1, 0, 0],
 [2, −1, 3 | 0, 1, 0],
 [4,  1, 8 | 0, 0, 1]]
```
`R₂ − 2R₁`, `R₃ − 4R₁`:
```
[[1,  0,  2 |  1, 0, 0],
 [0, −1, −1 | −2, 1, 0],
 [0,  1,  0 | −4, 0, 1]]
```
`R₃ + R₂`:
```
[[1,  0,  2 |  1, 0, 0],
 [0, −1, −1 | −2, 1, 0],
 [0,  0, −1 | −6, 1, 1]]
```
`R₂ → −R₂`, `R₃ → −R₃`:
```
[[1, 0,  2 | 1,  0,  0],
 [0, 1,  1 | 2, −1,  0],
 [0, 0,  1 | 6, −1, −1]]
```
`R₂ − R₃` → (0,1,0 | −4, 0, 1). `R₁ − 2R₃` → (1,0,0 | 1−12, 2, 2) = (1,0,0 | −11, 2, 2).
**A⁻¹ = [[−11, 2, 2], [−4, 0, 1], [6, −1, −1]].**
*Check row 1 of A × col 1 of A⁻¹: 1(−11) + 0(−4) + 2(6) = −11 + 12 = 1 ✓*

**S3.7** `AX + B = 3X` → `AX − 3X = −B` → `(A − 3I)X = −B`.
A − 3I = [[−1, 0], [0, −1]] = −I. So `−IX = −B` → **X = B = [[1, 1], [1, 1]]**.

**S3.8** (AB)ᵀ = BᵀAᵀ = BA (using symmetry of both).
- If AB is symmetric: (AB)ᵀ = AB, so BA = AB. ✓
- If AB = BA: then (AB)ᵀ = BA = AB, so AB is symmetric. ✓
Both directions shown. ∎

**S3.9** Let A = [[a, b], [c, d]]. A² = I means A⁻¹ = A, so A is involutory.
Approach via trace/determinant: eigenvalues satisfy λ² = 1, so λ ∈ {1, −1}.
- Both eigenvalues 1 and A diagonalizable → A = I.
- Both −1 → A = −I.
- One of each → tr A = 0 and det A = −1. Then a + d = 0 and ad − bc = −1, i.e. d = −a and −a² − bc = −1, so **a² + bc = 1**.

**Answer:** A = ±I, or A = [[a, b], [c, −a]] with a² + bc = 1.
*Examples:* [[1,0],[0,−1]], [[0,1],[1,0]], [[3, 4], [−2, −3]] (9 − 8 = 1 ✓).

**S3.10** `R₂ → R₂ − 3R₁` (multiplier 3): U = [[1, 2], [0, 2]], L = [[1, 0], [3, 1]].
`Ly = b`: y₁ = 3; 3(3) + y₂ = 13 → y₂ = 4.
`Ux = y`: 2x₂ = 4 → x₂ = 2; x₁ + 2(2) = 3 → x₁ = −1.
**Answer:** x = (−1, 2)ᵀ.

**S3.11** Note the identity `(I − A)(I + A + A²) = I − A³ = I − 0 = I`.
Since everything is square, **(I − A)⁻¹ = I + A + A²**. ∎

**S3.12** A² = [[1, 2], [0, 1]], A³ = [[1, 3], [0, 1]].
**Claim:** Aⁿ = [[1, n], [0, 1]].
*Base case n = 1:* true by definition.
*Inductive step:* assume Aᵏ = [[1, k], [0, 1]]. Then
Aᵏ⁺¹ = Aᵏ·A = [[1, k], [0, 1]]·[[1, 1], [0, 1]] = [[1·1 + k·0, 1·1 + k·1], [0, 1]] = [[1, k+1], [0, 1]] ✓
By induction, true for all n ≥ 1. ∎
*(This also holds for negative n: A⁻¹ = [[1, −1], [0, 1]].)*

**S3.13** `R₂ → R₂ − 2R₁` (mult 2), `R₃ → R₃ + R₁` (mult −1):
```
[[2, −1, 1],
 [0,  3, −2],
 [0,  4, 4]]
```
`R₃ → R₃ − (4/3)R₂` (mult 4/3):
```
U = [[2, −1,  1],
     [0,  3, −2],
     [0,  0,  4 + 8/3]] = [[2,−1,1],[0,3,−2],[0,0,20/3]]
```
```
L = [[ 1,   0,  0],
     [ 2,   1,  0],
     [−1, 4/3,  1]]
```
`Ly = (1, 3, 5)ᵀ`: y₁ = 1; 2(1) + y₂ = 3 → y₂ = 1; −1 + (4/3)(1) + y₃ = 5 → y₃ = 5 + 1 − 4/3 = 14/3.
`Ux = y`: (20/3)x₃ = 14/3 → x₃ = 14/20 = 7/10.
3x₂ − 2(7/10) = 1 → 3x₂ = 1 + 7/5 = 12/5 → x₂ = 4/5.
2x₁ − 4/5 + 7/10 = 1 → 2x₁ = 1 + 4/5 − 7/10 = (10 + 8 − 7)/10 = 11/10 → x₁ = 11/20.
**Answer:** x = (11/20, 4/5, 7/10)ᵀ.

**S3.14** Suppose Ax = 0 for some x. Then AᵀAx = 0. Since AᵀA is invertible, x = (AᵀA)⁻¹0 = 0. So Nul A = {0}, meaning the columns of A are linearly independent. ∎

**Converse is also true.** If the columns of A are independent and AᵀAx = 0, then xᵀAᵀAx = 0, i.e. ‖Ax‖² = 0, so Ax = 0, so x = 0 by independence. Hence Nul(AᵀA) = {0} and AᵀA (being square) is invertible. ∎
**So: columns of A independent ⟺ AᵀA invertible.** This is the key fact behind least squares (Chapter 6).

**S3.15** Suppose A were invertible. From A² = A, multiply both sides by A⁻¹:
A⁻¹A² = A⁻¹A → A = I.
This contradicts A ≠ I. **Hence A is not invertible.** ∎
*(The only invertible idempotent matrix is I.)*

**S3.16** Let C = (AB)⁻¹, so ABC = I and CAB = I.
- From `A(BC) = I` with A square: by IMT(k), **A is invertible**.
- From `(CA)B = I` with B square: by IMT(j), **B is invertible**. ∎

*Counterexample for non-square.* A = [[1, 0]] (1×2), B = [[1], [0]] (2×1). AB = [[1]] = I₁, invertible. But neither A nor B is square, hence neither is invertible. (Indeed BA = [[1,0],[0,0]] ≠ I₂.)

**S3.17**
A² = [[0, 0, 1], [0, 0, 0], [0, 0, 0]], A³ = **0**.

(I − A)(I + A + A²) = I + A + A² − A − A² − A³ = I − A³ = I − 0 = **I**. ∎

**General:** if N^k = 0, then `(I − N)⁻¹ = I + N + N² + ... + N^(k−1)`, since the telescoping product gives I − N^k = I. This is a finite geometric series that terminates exactly because N is nilpotent.

**S3.18** For n = 4, A = [[1,1,1,1],[0,1,1,1],[0,0,1,1],[0,0,0,1]]. Note A = I + N + N² + N³ where N is the superdiagonal shift. Row reduce [A | I]:
`R₁ − R₂`, `R₂ − R₃`, `R₃ − R₄`:
```
[[1, 0, 0, 0 | 1, −1,  0,  0],
 [0, 1, 0, 0 | 0,  1, −1,  0],
 [0, 0, 1, 0 | 0,  0,  1, −1],
 [0, 0, 0, 1 | 0,  0,  0,  1]]
```
**A⁻¹ = [[1,−1,0,0],[0,1,−1,0],[0,0,1,−1],[0,0,0,1]]** — the "difference" matrix.

**General pattern:** A⁻¹ has 1 on the diagonal, −1 on the superdiagonal, 0 elsewhere. Interpretation: A is the cumulative-sum operator; its inverse is the finite-difference operator.

**S3.19** *Proof sketch.* Verify by direct block multiplication. Let the proposed inverse be M. Compute the (1,1) block of [[A,B],[C,D]]·M:

A(A⁻¹ + A⁻¹BS⁻¹CA⁻¹) + B(−S⁻¹CA⁻¹) = I + BS⁻¹CA⁻¹ − BS⁻¹CA⁻¹ = I ✓

(1,2) block: A(−A⁻¹BS⁻¹) + B(S⁻¹) = −BS⁻¹ + BS⁻¹ = 0 ✓

(2,1) block: C(A⁻¹ + A⁻¹BS⁻¹CA⁻¹) + D(−S⁻¹CA⁻¹) = CA⁻¹ + CA⁻¹BS⁻¹CA⁻¹ − DS⁻¹CA⁻¹
= CA⁻¹ − (D − CA⁻¹B)S⁻¹CA⁻¹ = CA⁻¹ − SS⁻¹CA⁻¹ = CA⁻¹ − CA⁻¹ = 0 ✓

(2,2) block: C(−A⁻¹BS⁻¹) + DS⁻¹ = (D − CA⁻¹B)S⁻¹ = SS⁻¹ = I ✓ ∎

*Application.* A = [[1,2],[3,4]], B = [[0],[1]], C = [[0, 1]], D = [[2]].
A⁻¹ = (1/(4−6))[[4,−2],[−3,1]] = [[−2, 1], [3/2, −1/2]].
A⁻¹B = [[−2,1],[3/2,−1/2]]·[[0],[1]] = [[1], [−1/2]].
CA⁻¹B = [0, 1]·[[1],[−1/2]] = −1/2.
S = D − CA⁻¹B = 2 + 1/2 = 5/2, S⁻¹ = 2/5.
CA⁻¹ = [0,1]·A⁻¹ = [3/2, −1/2].
- Bottom-right: 2/5
- Bottom-left: −(2/5)[3/2, −1/2] = [−3/5, 1/5]
- Top-right: −A⁻¹B S⁻¹ = −[[1],[−1/2]](2/5) = [[−2/5],[1/5]]
- Top-left: A⁻¹ + A⁻¹B S⁻¹ C A⁻¹ = [[−2,1],[3/2,−1/2]] + [[1],[−1/2]](2/5)[3/2, −1/2]
 = [[−2,1],[3/2,−1/2]] + [[3/5, −1/5], [−3/10, 1/10]] = [[−7/5, 4/5], [6/5, −2/5]]

**Full inverse:**
```
[[−7/5,  4/5, −2/5],
 [ 6/5, −2/5,  1/5],
 [−3/5,  1/5,  2/5]]
```
*Verification, row 1 × col 1 of original: (−7/5)(1) + (4/5)(3) + (−2/5)(0) = −7/5 + 12/5 = 1 ✓*

**S3.20** `A⁴ − 2A³ + A² = 0` → `A²(A² − 2A + I) = 0` → `A²(A − I)² = 0`.

Take determinants: det(A²)·det((A−I)²) = 0, so (det A)²·(det(A − I))² = 0.

Therefore **det A = 0 or det(A − I) = 0**.

However, det(A − I) = 0 means 1 is an eigenvalue, which places no constraint on det A being zero. So consider the minimal polynomial: it divides x²(x−1)², so every eigenvalue λ satisfies λ ∈ {0, 1}.

det A = product of eigenvalues ∈ {0, 1} — it is 1 only when all three eigenvalues equal 1.

**Answer: det A ∈ {0, 1}.** A need **not** be singular: A = I satisfies I − 2I + I = 0 ✓ and det I = 1.
*(But if any eigenvalue is 0, det A = 0. Both cases genuinely occur.)*

---
# Chapter 4 — Linear Dependence and Independence, Vector Spaces, Subspaces, Basis and Dimension

---

## 4.1 Explain Like I'm Five

**Vectors** are arrows, but forget arrows for a moment. A vector is anything you can *add to another one* and *scale by a number*, where those operations behave sensibly. Lists of numbers qualify. So do polynomials (you can add two polynomials and double a polynomial). So do functions, and so do matrices. A **vector space** is just a playground where adding and scaling are allowed and well-behaved.

**Span.** Give me a few arrows. Everything I can reach by stretching them and adding them up is called their *span*. One arrow spans a line. Two arrows pointing in different directions span a plane. Two arrows pointing along the *same* line only span a line — the second one was useless.

**Linear independence** is the question: *is any one of my arrows useless?* If I can build one of the arrows out of the others, that arrow is redundant — the set is **dependent**. If nobody is redundant, the set is **independent**.

A picture: three arrows in 3D space. If they all happen to lie flat in one plane, they're dependent — you can reach the third by combining the first two, and together they only get you a plane, not the whole space. If they poke out in three genuinely different directions, they're independent and they span everything.

**Basis.** A basis is the Goldilocks set: *just enough* arrows to reach everything (spanning), with *nothing wasted* (independent). Not too few, not too many. Think of it as a minimal set of building blocks, or a coordinate system.

**Dimension** is how many blocks your basis needs. And here's the beautiful part — **every basis for the same space has exactly the same number of vectors**. You can't build ℝ³ from 2 blocks, and if you use 4 you've wasted one. Dimension is a property of the *space*, not of your particular choice of blocks.

**Subspace.** A smaller playground sitting inside a bigger one, which is still a complete playground on its own. Concretely: it must contain the origin, and if you add or scale anything inside it, you must stay inside it. A line through the origin is a subspace of ℝ². A line *not* through the origin is not — scaling a point on it by 0 pops you out of the line.

---

## 4.2 The Formal Theory

### 4.2.1 Vector Space Axioms

A **vector space** over ℝ is a nonempty set V with two operations (addition, scalar multiplication) satisfying, for all u, v, w ∈ V and c, d ∈ ℝ:

1. u + v ∈ V (**closure under addition**)
2. u + v = v + u
3. (u + v) + w = u + (v + w)
4. There is 0 ∈ V with u + 0 = u
5. For each u there is −u with u + (−u) = 0
6. cu ∈ V (**closure under scalar multiplication**)
7. c(u + v) = cu + cv
8. (c + d)u = cu + du
9. c(du) = (cd)u
10. 1u = u

**Standard examples:** ℝⁿ; Pₙ (polynomials of degree ≤ n); M_{m×n} (all m×n matrices); C[a,b] (continuous functions on [a,b]); the set of all real sequences.

**Non-examples:** the set of polynomials of degree *exactly* n (not closed under addition — the leading terms can cancel); the first quadrant of ℝ² (not closed under negative scalars); any set missing the zero vector.

### 4.2.2 Subspaces

> **Definition.** H ⊆ V is a **subspace** if
> (i) 0 ∈ H,
> (ii) u, v ∈ H ⟹ u + v ∈ H,
> (iii) u ∈ H, c ∈ ℝ ⟹ cu ∈ H.

These three checks replace all ten axioms — the rest are inherited from V.

**Shortcut test:** H is a subspace ⟺ H is nonempty and closed under *linear combinations*: `u, v ∈ H, c, d ∈ ℝ ⟹ cu + dv ∈ H`.

> **Theorem 4.1.** For any v₁, ..., v_p ∈ V, the set Span{v₁, ..., v_p} is a subspace of V — indeed the *smallest* subspace containing all the vᵢ.

### 4.2.3 The Four Fundamental Subspaces

For an m×n matrix A:

| Subspace | Definition | Lives in | Dimension |
|---|---|---|---|
| **Column space** Col(A) | span of columns = {Ax : x ∈ ℝⁿ} | ℝᵐ | rank r |
| **Null space** Nul(A) | {x : Ax = 0} | ℝⁿ | n − r (nullity) |
| **Row space** Row(A) = Col(Aᵀ) | span of rows | ℝⁿ | rank r |
| **Left null space** Nul(Aᵀ) | {y : Aᵀy = 0} | ℝᵐ | m − r |

**Orthogonality relations (Chapter 5 will use these):**
- Row(A) ⊥ Nul(A), and together they fill ℝⁿ.
- Col(A) ⊥ Nul(Aᵀ), and together they fill ℝᵐ.

### 4.2.4 Linear Combinations, Span, Independence

A **linear combination** of v₁, ..., v_p with weights c₁, ..., c_p is `c₁v₁ + ... + c_pv_p`.

> **Definition.** {v₁, ..., v_p} is **linearly independent** if the vector equation
> `c₁v₁ + c₂v₂ + ... + c_pv_p = 0`
> has *only* the trivial solution c₁ = c₂ = ... = c_p = 0.
> It is **linearly dependent** if some nontrivial choice of weights gives 0.

**Practical test in ℝⁿ:** form the matrix A with the vᵢ as columns. Then
> independent ⟺ `Ax = 0` has only x = 0 ⟺ A has a pivot in **every column** ⟺ rank = p.

**Useful facts:**
1. A set containing the **zero vector is always dependent** (take the coefficient of 0 to be 1).
2. Two vectors are dependent ⟺ one is a scalar multiple of the other.
3. **Any set of more than n vectors in ℝⁿ is automatically dependent.** (More unknowns than equations.)
4. A single nonzero vector is always independent.

> **Theorem 4.2 (Characterization of Dependence).** A set of two or more vectors is linearly dependent ⟺ at least one vector is a linear combination of the others. If the set is dependent and v₁ ≠ 0, then some vⱼ (j > 1) is a combination of the preceding vectors.

### 4.2.5 Basis

> **Definition.** B = {b₁, ..., b_p} is a **basis** for a subspace H if
> (i) B is linearly independent, and
> (ii) Span(B) = H.

**Standard basis for ℝⁿ:** e₁ = (1,0,...,0), e₂ = (0,1,0,...,0), ..., eₙ.
**Standard basis for Pₙ:** {1, t, t², ..., tⁿ} — so dim Pₙ = n + 1.
**Standard basis for M_{2×2}:** the four matrices with a single 1 — so dim = 4.

> **Theorem 4.3 (Spanning Set Theorem).** Let S = {v₁, ..., v_p} span H. If some vₖ is a linear combination of the others, then S \ {vₖ} still spans H. Repeating, any spanning set can be pruned down to a basis.

> **Theorem 4.4 (Pivot Column Theorem).** The **pivot columns of A** (that is, the columns of the *original* A corresponding to pivot positions) form a basis for Col(A).

**Critical warning:** use the **original** columns, not the reduced ones. Row reduction changes the column space! It preserves *which* columns are dependent on which, but not the columns themselves. (Row reduction *does* preserve the row space, so for Row(A) you may use the nonzero rows of the RREF.)

### 4.2.6 Coordinates

> **Theorem 4.5 (Unique Representation).** If B = {b₁, ..., bₙ} is a basis for V, then every x ∈ V has **exactly one** expression x = c₁b₁ + ... + cₙbₙ.

The weights form the **coordinate vector** [x]_B = (c₁, ..., cₙ)ᵀ.

The map x ↦ [x]_B is an **isomorphism** V → ℝⁿ — a one-to-one, onto linear map. This is why every n-dimensional real vector space "is" ℝⁿ in disguise.

**Change of coordinates.** If B = {b₁,...,bₙ} is a basis of ℝⁿ and P_B = [b₁ b₂ ... bₙ], then

> x = P_B [x]_B and [x]_B = P_B⁻¹ x

To convert between two bases B and C: `[x]_C = P_{C←B} [x]_B` where the columns of P_{C←B} are the B-vectors written in C-coordinates.

### 4.2.7 Dimension

> **Theorem 4.6.** If V has a basis of n vectors, then **every** basis of V has exactly n vectors.

*Proof idea:* if one basis had p vectors and another q with p > q, then p vectors would live in a space spanned by q < p vectors — forcing dependence (by fact 3 above), contradicting basis-hood.

> **Definition.** dim V = number of vectors in any basis. dim{0} = 0. If no finite basis exists, V is infinite-dimensional.

> **Theorem 4.7 (The Basis Theorem).** Let V be p-dimensional, p ≥ 1. Then
> - Any **p linearly independent** vectors in V automatically form a basis.
> - Any **p vectors that span** V automatically form a basis.

This is enormously labour-saving: once you know the dimension, you only need to check *one* of the two conditions, not both.

> **Theorem 4.8.** If H is a subspace of V then dim H ≤ dim V, with equality ⟺ H = V.

### 4.2.8 The Rank–Nullity Theorem

> **Theorem 4.9 (Rank–Nullity / Dimension Theorem).** For any m×n matrix A,
>
> **rank(A) + nullity(A) = n** (the number of *columns*)
>
> where rank(A) = dim Col(A) = number of pivots, and nullity(A) = dim Nul(A) = number of free variables.

Also: **rank(A) = rank(Aᵀ)** — the row rank equals the column rank. A deeply non-obvious fact with a short proof via RREF.

**Bounds:** rank(A) ≤ min(m, n). A matrix achieving this is said to have **full rank**.

---

## 4.3 Solved Examples

### Example 4.1 — [Easy] Subspace or not?

Which of the following are subspaces of ℝ³?
(a) H = {(a, b, 0) : a, b ∈ ℝ}
(b) K = {(a, b, 1) : a, b ∈ ℝ}
(c) L = {(a, b, c) : a + b + c = 0}
(d) M = {(a, b, c) : a ≥ 0}

**Solution.**
(a) Contains 0 = (0,0,0) ✓. Sum of two such vectors has third coordinate 0 ✓. Scalar multiple keeps third coordinate 0 ✓. **Subspace** (the xy-plane, dim 2).
(b) Does not contain (0,0,0) since the third coordinate is forced to 1. **Not a subspace.**
(c) 0 satisfies 0+0+0 = 0 ✓. If a+b+c = 0 and a'+b'+c' = 0, the sum satisfies (a+a')+(b+b')+(c+c') = 0 ✓. Scaling: c(a+b+c) = 0 ✓. **Subspace** (a plane, dim 2).
(d) Take (1,0,0) ∈ M and scalar −1: (−1,0,0) ∉ M. **Not a subspace** (not closed under negative scalars).

---

### Example 4.2 — [Easy] Testing independence

Are v₁ = (1, 2, 3), v₂ = (2, 4, 6), v₃ = (1, 0, 1) independent?

**Solution.** Immediately: v₂ = 2v₁. So 2v₁ − v₂ + 0v₃ = 0 is a nontrivial dependence.

**Answer: linearly dependent.** (You didn't even need to look at v₃ — a dependent subset makes the whole set dependent.)

---

### Example 4.3 — [Medium] Basis for column space and null space

Let A = [[1, 2, 0, 4], [2, 4, −1, 3], [3, 6, 2, 22]]. Find bases for Col(A), Nul(A), Row(A), and verify rank–nullity.

**Solution.** Reduce:
`R₂ → R₂ − 2R₁`, `R₃ → R₃ − 3R₁`:
```
[[1, 2,  0,  4],
 [0, 0, −1, −5],
 [0, 0,  2, 10]]
```
`R₃ → R₃ + 2R₂` → zero row. `R₂ → −R₂`:
```
[[1, 2, 0, 4],
 [0, 0, 1, 5],
 [0, 0, 0, 0]]
```
This is the RREF. **Pivot columns: 1 and 3.**

**Basis for Col(A):** the *original* columns 1 and 3:
> {(1, 2, 3)ᵀ, (0, −1, 2)ᵀ}. So rank = 2.

**Basis for Row(A):** nonzero rows of the RREF:
> {(1, 2, 0, 4), (0, 0, 1, 5)}. Dimension 2 ✓ (row rank = column rank).

**Basis for Nul(A):** free variables x₂ = s, x₄ = t.
x₁ = −2s − 4t, x₃ = −5t.
> x = s(−2, 1, 0, 0) + t(−4, 0, −5, 1). Basis: {(−2,1,0,0), (−4,0,−5,1)}. Nullity = 2.

**Rank–nullity check:** 2 + 2 = 4 = number of columns ✓

---

### Example 4.4 — [Medium] Independence in a polynomial space

Are p₁(t) = 1 + t, p₂(t) = 1 − t, p₃(t) = 2 + t² independent in P₂?

**Solution.** Use coordinates relative to the standard basis {1, t, t²}:
- [p₁] = (1, 1, 0)
- [p₂] = (1, −1, 0)
- [p₃] = (2, 0, 1)

Form the matrix with these as columns and compute the determinant:
```
| 1  1  2 |
| 1 −1  0 |
| 0  0  1 |
```
Expand along row 3: = 1·det([[1, 1], [1, −1]]) = 1(−1 − 1) = −2 ≠ 0.

**Answer: linearly independent.** Since dim P₂ = 3 and we have 3 independent vectors, by the Basis Theorem they also form a **basis** for P₂.

---

### Example 4.5 — [Medium] Coordinate vectors

Let B = {b₁, b₂} with b₁ = (1, 1), b₂ = (1, −1). Find [x]_B for x = (5, 1).

**Solution.** Solve c₁(1,1) + c₂(1,−1) = (5,1):
```
c₁ + c₂ = 5
c₁ − c₂ = 1
```
Adding: 2c₁ = 6 → c₁ = 3, c₂ = 2.

**Answer:** [x]_B = (3, 2)ᵀ.

**Via the matrix:** P_B = [[1, 1], [1, −1]], P_B⁻¹ = (1/(−2))[[−1,−1],[−1,1]] = [[1/2, 1/2],[1/2, −1/2]].
[x]_B = P_B⁻¹(5,1)ᵀ = (5/2 + 1/2, 5/2 − 1/2) = (3, 2) ✓

---

### Example 4.6 — [Hard] Extend an independent set to a basis

Extend {(1, 1, 0, 0), (0, 1, 1, 0)} to a basis of ℝ⁴.

**Solution.** Strategy: append the standard basis vectors and prune using the Pivot Column Theorem.

Form the matrix with columns v₁, v₂, e₁, e₂, e₃, e₄:
```
[[1, 0, 1, 0, 0, 0],
 [1, 1, 0, 1, 0, 0],
 [0, 1, 0, 0, 1, 0],
 [0, 0, 0, 0, 0, 1]]
```
`R₂ → R₂ − R₁`:
```
[[1, 0,  1, 0, 0, 0],
 [0, 1, −1, 1, 0, 0],
 [0, 1,  0, 0, 1, 0],
 [0, 0,  0, 0, 0, 1]]
```
`R₃ → R₃ − R₂`:
```
[[1, 0,  1, 0, 0, 0],
 [0, 1, −1, 1, 0, 0],
 [0, 0,  1, −1, 1, 0],
 [0, 0,  0,  0, 0, 1]]
```
Pivots in columns **1, 2, 3, 6**.

**Answer:** {(1,1,0,0), (0,1,1,0), e₁ = (1,0,0,0), e₄ = (0,0,0,1)} is a basis for ℝ⁴.

*Verification of independence:* the four vectors form the matrix [[1,0,1,0],[1,1,0,0],[0,1,0,0],[0,0,0,1]] whose determinant expands (along the last row and column) to det([[1,0,1],[1,1,0],[0,1,0]]) = 1(0 − 0) − 0 + 1(1 − 0) = 1 ≠ 0 ✓

---

### Example 4.7 — [Hard] Dimension of a subspace defined by equations

Find a basis and the dimension of
H = {(a, b, c, d) ∈ ℝ⁴ : a − 2b + 5c − d = 0 and −a + b + c + d = 0}.

**Solution.** This is Nul(A) with A = [[1, −2, 5, −1], [−1, 1, 1, 1]].

`R₂ → R₂ + R₁`:
```
[[1, −2, 5, −1],
 [0, −1, 6,  0]]
```
`R₂ → −R₂` → (0, 1, −6, 0). `R₁ → R₁ + 2R₂` → (1, 0, 5 − 12, −1) = (1, 0, −7, −1).

RREF: `[[1, 0, −7, −1], [0, 1, −6, 0]]`. Pivots: columns 1, 2. Free: c, d.

a = 7c + d, b = 6c.

**Basis:** {(7, 6, 1, 0), (1, 0, 0, 1)}. **dim H = 2.**

*Sanity check:* 2 constraints on ℝ⁴, both independent, leaving 4 − 2 = 2 dimensions ✓

---

### Example 4.8 — [Very Hard] Rank inequalities

Let A be m×n and B be n×p. Prove:
(a) rank(AB) ≤ min(rank A, rank B)
(b) **Sylvester's inequality:** rank(A) + rank(B) − n ≤ rank(AB)

**Solution.**

**(a)** Every column of AB is A times the corresponding column of B, so every column of AB lies in Col(A). Hence Col(AB) ⊆ Col(A), giving rank(AB) ≤ rank(A).

For the other bound, apply the same argument to transposes: (AB)ᵀ = BᵀAᵀ, so Col((AB)ᵀ) ⊆ Col(Bᵀ), giving rank((AB)ᵀ) ≤ rank(Bᵀ). Since rank M = rank Mᵀ, this says rank(AB) ≤ rank(B). ∎

**(b)** Consider the linear map B: ℝᵖ → ℝⁿ followed by A: ℝⁿ → ℝᵐ.

Restrict A to the subspace Col(B) ⊆ ℝⁿ. By rank–nullity applied to this restricted map:

dim Col(B) = dim(A(Col B)) + dim(Nul(A) ∩ Col(B))

Now A(Col B) = Col(AB), so dim(A(Col B)) = rank(AB). And Nul(A) ∩ Col(B) ⊆ Nul(A), so its dimension is at most nullity(A) = n − rank(A). Therefore:

rank(B) ≤ rank(AB) + (n − rank A)

Rearranging: **rank(A) + rank(B) − n ≤ rank(AB)** ∎

**Illustration.** A = [[1,0],[0,0]], B = [[0,0],[0,1]], n = 2. rank A = rank B = 1. AB = 0, rank 0.
Sylvester: 1 + 1 − 2 = 0 ≤ 0 ✓ (the bound is tight here).

---

### Example 4.9 — [Very Hard] A dimension-counting proof

Let U and W be subspaces of a finite-dimensional vector space V. Prove

> **dim(U + W) = dim U + dim W − dim(U ∩ W)**

where U + W = {u + w : u ∈ U, w ∈ W}.

**Solution.** Let dim(U ∩ W) = k and choose a basis {v₁, ..., v_k} for U ∩ W.

Extend it to a basis of U: {v₁, ..., v_k, u₁, ..., u_p} where dim U = k + p.
Extend it to a basis of W: {v₁, ..., v_k, w₁, ..., w_q} where dim W = k + q.

**Claim:** S = {v₁,...,v_k, u₁,...,u_p, w₁,...,w_q} is a basis for U + W.

*Spanning.* Any element of U + W is u + w; expand u in the U-basis and w in the W-basis — every term lies in span(S). ✓

*Independence.* Suppose
`Σaᵢvᵢ + Σbⱼuⱼ + Σc_lw_l = 0`.

Let z = Σc_lw_l = −Σaᵢvᵢ − Σbⱼuⱼ. The right side is in U; the left is in W. So z ∈ U ∩ W.

Therefore z can be written in the {vᵢ} basis: z = Σdᵢvᵢ. But z = Σc_lw_l, so

Σdᵢvᵢ − Σc_lw_l = 0.

Since {v₁,...,v_k, w₁,...,w_q} is a basis for W (hence independent), all dᵢ = 0 and **all c_l = 0**.

With all c_l = 0, the original relation becomes Σaᵢvᵢ + Σbⱼuⱼ = 0, and since {vᵢ, uⱼ} is a basis for U, all aᵢ = 0 and all bⱼ = 0. ✓

So dim(U + W) = k + p + q = (k + p) + (k + q) − k = dim U + dim W − dim(U ∩ W). ∎

**Application.** Two 2-dimensional planes through the origin in ℝ³. dim(U + W) ≤ 3, so
3 ≥ 2 + 2 − dim(U ∩ W) → dim(U ∩ W) ≥ 1. **Two distinct planes through the origin in ℝ³ always intersect in at least a line** — they can never meet only at the origin.

---

## 4.4 Practice Numericals — Chapter 4

**[Easy]**

**P4.1** Is {(1, 0), (0, 1), (1, 1)} linearly independent in ℝ²? Justify without computation.

**P4.2** Determine whether W = {(x, y) : xy = 0} is a subspace of ℝ².

**P4.3** Find the dimension of the subspace spanned by (1, 2), (2, 4), (3, 6).

**P4.4** Write the coordinate vector of p(t) = 3 − 2t + t² with respect to the standard basis of P₂.

**P4.5** State the dimension of: (a) ℝ⁵, (b) P₄, (c) M_{3×2}, (d) the space of 3×3 symmetric matrices.

**[Medium]**

**P4.6** Find a basis for Col(A) and Nul(A) for A = [[1, 3, 2, −1], [2, 6, 5, 0], [1, 3, 3, 1]]. Verify rank–nullity.

**P4.7** Determine whether {1 + t, t + t², 1 + t²} is a basis for P₂.

**P4.8** Let H = span{(1,2,1), (2,1,3)}. Is (4, 5, 5) in H? Is (1, 1, 1)?

**P4.9** Find a basis for the subspace of ℝ⁴ consisting of all vectors whose coordinates sum to zero. What is its dimension?

**P4.10** Given B = {(2, 1), (−1, 1)}, find [x]_B for x = (1, 5). Then find the change-of-coordinates matrix from B to the standard basis and back.

**P4.11** Show that the set of all 2×2 matrices with trace 0 is a subspace of M_{2×2} and find its dimension and a basis.

**[Hard]**

**P4.12** Let A be 5×7 with nullity 3. Find rank(A), dim Row(A), dim Nul(Aᵀ). Can the columns of A span ℝ⁵?

**P4.13** Determine all values of k for which {(1, 2, 3), (2, k, 6), (3, 6, 9)} is linearly dependent.

**P4.14** Find a basis for the intersection of U = span{(1,1,0,0), (0,1,1,0)} and W = span{(1,0,−1,0), (0,0,1,1)} in ℝ⁴, then verify the dimension formula dim(U+W) = dim U + dim W − dim(U∩W).

**P4.15** Prove that if {v₁, v₂, v₃} is linearly independent, then so is {v₁ + v₂, v₂ + v₃, v₃ + v₁}. Does the analogous statement hold for {v₁ − v₂, v₂ − v₃, v₃ − v₁}?

**P4.16** Let A be n×n. Show that rank(A²) = rank(A) if and only if Col(A) ∩ Nul(A) = {0}.

**[Very Hard]**

**P4.17** Prove that the functions {1, cos t, cos 2t, cos 3t} are linearly independent in C[0, 2π]. (Hint: differentiate repeatedly and evaluate, or use orthogonality integrals.)

**P4.18** Let V be the vector space of all real sequences. Show that V is infinite-dimensional by exhibiting, for each n, a linearly independent set of size n.

**P4.19** Let A be m×n with rank r. Prove that A can be written as a sum of exactly r rank-one matrices, and that it cannot be written as a sum of fewer.

**P4.20** Let W₁, W₂, W₃ be 2-dimensional subspaces of ℝ³ that are pairwise distinct. Prove that W₁ ∩ W₂ ∩ W₃ is either a line or {0}, and give an example of each case.

---

## 4.5 Solutions to Chapter 4 Practice

**S4.1** **No.** Three vectors in ℝ² — any set of more than n vectors in ℝⁿ is automatically dependent (fact 3, §4.2.4). Explicitly: (1,1) = (1,0) + (0,1).

**S4.2** **Not a subspace.** (1, 0) ∈ W and (0, 1) ∈ W, but their sum (1, 1) has xy = 1 ≠ 0. Not closed under addition. *(It is the union of the two axes — a union of subspaces, which is rarely a subspace.)*

**S4.3** All three are multiples of (1,2). **Dimension 1** (a line).

**S4.4** Standard basis {1, t, t²}. **[p] = (3, −2, 1)ᵀ.**

**S4.5** (a) 5. (b) 5 (basis 1, t, t², t³, t⁴). (c) 6. (d) 6 — a 3×3 symmetric matrix is determined by the 3 diagonal and 3 above-diagonal entries: n(n+1)/2 = 6.

**S4.6** `R₂ − 2R₁`, `R₃ − R₁`:
```
[[1, 3, 2, −1],
 [0, 0, 1,  2],
 [0, 0, 1,  2]]
```
`R₃ − R₂` → zero. `R₁ − 2R₂` → (1, 3, 0, −5).
RREF: `[[1,3,0,−5],[0,0,1,2],[0,0,0,0]]`. Pivots in columns 1, 3.

**Col(A) basis:** original columns 1 and 3: {(1,2,1)ᵀ, (2,5,3)ᵀ}. rank = 2.
**Nul(A):** free x₂ = s, x₄ = t. x₁ = −3s + 5t, x₃ = −2t.
Basis: {(−3,1,0,0), (5,0,−2,1)}. nullity = 2.
**Check:** 2 + 2 = 4 ✓

**S4.7** Coordinates w.r.t. {1, t, t²}: (1,1,0), (0,1,1), (1,0,1).
det of [[1,0,1],[1,1,0],[0,1,1]] = 1(1−0) − 0(1−0) + 1(1−0) = 1 + 1 = 2 ≠ 0.
**Yes — independent, and being 3 vectors in the 3-dimensional P₂, a basis** (Basis Theorem).

**S4.8** Solve c₁(1,2,1) + c₂(2,1,3) = (4,5,5):
```
c₁ + 2c₂ = 4
2c₁ + c₂ = 5
c₁ + 3c₂ = 5
```
From the first two: multiply eq1 by 2: 2c₁ + 4c₂ = 8; subtract eq2: 3c₂ = 3 → c₂ = 1, c₁ = 2.
Check eq3: 2 + 3 = 5 ✓ **Yes, (4,5,5) ∈ H.**

For (1,1,1): c₁ + 2c₂ = 1, 2c₁ + c₂ = 1 → c₁ = c₂ = 1/3. Check eq3: 1/3 + 1 = 4/3 ≠ 1. **No, (1,1,1) ∉ H.**

**S4.9** W = {x ∈ ℝ⁴ : x₁+x₂+x₃+x₄ = 0} = Nul([1 1 1 1]). One pivot, three free variables.
x₁ = −x₂ − x₃ − x₄.
**Basis:** {(−1,1,0,0), (−1,0,1,0), (−1,0,0,1)}. **dim = 3.**

**S4.10** Solve c₁(2,1) + c₂(−1,1) = (1,5):
2c₁ − c₂ = 1, c₁ + c₂ = 5. Adding: 3c₁ = 6 → c₁ = 2, c₂ = 3.
**[x]_B = (2, 3)ᵀ.**
P_B = [[2, −1], [1, 1]] converts B-coords → standard. det = 3.
P_B⁻¹ = (1/3)[[1, 1], [−1, 2]] converts standard → B.
*Check:* (1/3)[[1,1],[−1,2]](1,5)ᵀ = (1/3)(6, 9) = (2, 3) ✓

**S4.11** Let W = {A ∈ M_{2×2} : tr A = 0}.
- 0 matrix has trace 0 ✓
- tr(A + B) = tr A + tr B = 0 ✓
- tr(cA) = c·tr A = 0 ✓
**Subspace.** ✓
General element: [[a, b], [c, −a]] — three free parameters.
**Basis:** {[[1,0],[0,−1]], [[0,1],[0,0]], [[0,0],[1,0]]}. **dim = 3.**

**S4.12** n = 7 columns. rank = 7 − 3 = **4**.
dim Row(A) = rank = **4**.
dim Nul(Aᵀ) = m − rank = 5 − 4 = **1**.
Columns span ℝ⁵ would require rank 5. Since rank = 4, **no** — Col(A) is a proper 4-dimensional subspace of ℝ⁵.

**S4.13** Note (3,6,9) = 3(1,2,3) already. So v₁ and v₃ are dependent **for every k**.

**Answer: the set is dependent for all k ∈ ℝ.**

*(A trap: students often set the determinant to 0 and solve for k. Doing so: det of [[1,2,3],[2,k,6],[3,6,9]] — columns 1 and 3 of the *matrix formed with these as rows*… either way, rows 1 and 3 are proportional, so the determinant is identically 0 regardless of k. The answer is "all k".)*

**S4.14** Let x ∈ U ∩ W. Then x = a(1,1,0,0) + b(0,1,1,0) = c(1,0,−1,0) + d(0,0,1,1).

Componentwise:
- coord 1: a = c
- coord 2: a + b = 0 → b = −a
- coord 3: b = −c + d → −a = −a + d → **d = 0**
- coord 4: 0 = d ✓ (consistent)

So d = 0, c = a, b = −a, with a free.
x = a(1,1,0,0) − a(0,1,1,0) = a(1, 0, −1, 0).

**Basis for U ∩ W: {(1, 0, −1, 0)}. dim(U ∩ W) = 1.**

Check formula: dim U = 2, dim W = 2. Predicted dim(U + W) = 2 + 2 − 1 = 3.
Verify: U + W is spanned by (1,1,0,0), (0,1,1,0), (1,0,−1,0), (0,0,1,1). The third is the difference of the first two, so it is redundant. Remaining three: (1,1,0,0), (0,1,1,0), (0,0,1,1) — clearly independent (echelon-like staircase). **dim(U+W) = 3 ✓**

**S4.15** Suppose a(v₁+v₂) + b(v₂+v₃) + c(v₃+v₁) = 0. Group:
(a + c)v₁ + (a + b)v₂ + (b + c)v₃ = 0.
By independence of the vᵢ: a + c = 0, a + b = 0, b + c = 0.
From the first two: c = −a, b = −a. Substituting into the third: −a − a = −2a = 0 → a = 0, hence b = c = 0.
**Independent.** ∎

For the differences: note **(v₁−v₂) + (v₂−v₃) + (v₃−v₁) = 0** — a nontrivial dependence with all coefficients 1.
**So no, the analogous statement fails: {v₁−v₂, v₂−v₃, v₃−v₁} is always dependent.**

*(Underlying reason: the coefficient matrix [[1,0,1],[1,1,0],[0,1,1]] has det 2 ≠ 0 for the sums, while [[1,0,−1],[−1,1,0],[0,−1,1]] has det 0 for the differences.)*

**S4.16**
(⇐) Suppose Col(A) ∩ Nul(A) = {0}. Consider A restricted to Col(A), mapping Col(A) → Col(A²). Its kernel is Col(A) ∩ Nul(A) = {0}, so the restriction is injective, hence
rank(A²) = dim Col(A²) = dim Col(A) = rank(A).

(⇒) Suppose rank(A²) = rank(A). By rank–nullity on the restriction of A to Col(A):
rank(A) = dim Col(A) = dim(A·Col A) + dim(Col A ∩ Nul A) = rank(A²) + dim(Col A ∩ Nul A).
Since rank(A²) = rank(A), we get dim(Col A ∩ Nul A) = 0, so the intersection is {0}. ∎

*Example where it fails:* A = [[0,1],[0,0]]. rank A = 1, A² = 0 so rank A² = 0. Col(A) = span{(1,0)} = Nul(A) — intersection is not {0} ✓

**S4.17** Suppose a + b cos t + c cos 2t + d cos 3t = 0 for all t ∈ [0, 2π].

*Method 1 — evaluate at convenient points.*
- t = 0: a + b + c + d = 0
- t = π: a − b + c − d = 0
- t = π/2: cos(π/2)=0, cos π = −1, cos(3π/2)=0 → a − c = 0
- t = π/3: cos(π/3)=1/2, cos(2π/3)=−1/2, cos π = −1 → a + b/2 − c/2 − d = 0

From (3): a = c. Adding (1) and (2): 2a + 2c = 0 → a + c = 0. With a = c: 2a = 0 → **a = c = 0**.
Then (1) gives b + d = 0 and (4) gives b/2 − d = 0 → b = 2d. So 2d + d = 3d = 0 → d = 0, b = 0.
All coefficients zero. **Independent.** ∎

*Method 2 — orthogonality.* ∫₀^{2π} cos(mt)cos(nt) dt = 0 for m ≠ n, and = π for m = n ≥ 1 (= 2π for m = n = 0). Multiplying the relation by cos(kt) and integrating isolates the k-th coefficient and forces it to be 0.

**S4.18** For each n, consider the sequences
e₁ = (1,0,0,0,...), e₂ = (0,1,0,0,...), ..., eₙ = (0,...,0,1,0,...).

Suppose c₁e₁ + ... + cₙeₙ = 0 (the zero sequence). Looking at the k-th term of the sum gives cₖ = 0 for each k. So {e₁, ..., eₙ} is independent for every n.

If V had finite dimension d, no independent set could have more than d elements — but we have independent sets of every size n. **Contradiction. V is infinite-dimensional.** ∎

**S4.19** Let rank(A) = r. By the pivot-column theorem, Col(A) has a basis u₁, ..., u_r. Every column aⱼ of A is a combination aⱼ = Σᵢ cᵢⱼ uᵢ. Writing C = [cᵢⱼ] (r×n), we get **A = UC** where U = [u₁ ... u_r] is m×r.

Then A = UC = Σ_{i=1}^{r} uᵢ · (row i of C), and each term uᵢ·rᵢᵀ is an **outer product**, i.e. a rank-one matrix. So A is a sum of r rank-one matrices. ✓

*Cannot be fewer.* Suppose A = Σ_{i=1}^{k} xᵢyᵢᵀ with k < r. Each term has rank ≤ 1, and rank is subadditive: rank(M + N) ≤ rank M + rank N. So rank(A) ≤ k < r, contradiction. ∎

*(This is precisely the "rank-r factorization" that SVD makes canonical in Chapter 13.)*

**S4.20** Each Wᵢ is a plane through the origin in ℝ³, so dim Wᵢ = 2.

By S/Example 4.9, for distinct planes W₁ ≠ W₂:
dim(W₁ ∩ W₂) = dim W₁ + dim W₂ − dim(W₁ + W₂) = 2 + 2 − 3 = **1** (since W₁ + W₂ ⊆ ℝ³ and must be all of ℝ³, as it properly contains the 2-dimensional W₁).

So W₁ ∩ W₂ is a **line** L. Now intersect with W₃:
- If L ⊆ W₃, then W₁ ∩ W₂ ∩ W₃ = L, a **line**.
- If L ⊄ W₃, then L ∩ W₃ is a proper subspace of the 1-dimensional L, hence **{0}**.
No other possibilities. ∎

*Example (line).* W₁ = {z = 0}, W₂ = {y = 0}, W₃ = {y = z}. All three contain the x-axis. Intersection = x-axis.
*Example ({0}).* W₁ = {z = 0}, W₂ = {y = 0}, W₃ = {x = 0}. W₁ ∩ W₂ = x-axis, which meets W₃ = {x=0} only at the origin.

---
# Chapter 5 — Orthogonality and Projections: Orthogonal Bases, Orthogonal Projections, Gram–Schmidt

---

## 5.1 Explain Like I'm Five

**The dot product measures agreement.** Take two arrows. Multiply matching components and add them up. If the answer is a big positive number, the arrows mostly point the same way. If it's negative, they mostly point opposite. If it's **exactly zero**, they're at right angles — they have nothing to do with each other. That's **orthogonality**.

**Why are right angles such a big deal?** Because perpendicular directions don't interfere. If you're describing a point using a north–south measurement and an east–west measurement, changing one doesn't mess up the other. But if your two directions were "north" and "north-northeast", they'd overlap, and figuring out coordinates would require solving a messy system. Orthogonal directions make coordinates **free** — just take a dot product and divide.

**Projection.** Imagine the sun directly overhead and a stick leaning against the ground. Its **shadow** on the ground is the projection. Formally: the projection of v onto a subspace W is the point of W *closest* to v. The leftover piece (from the shadow's tip back up to the stick's tip) is perpendicular to the ground. That's the whole idea:

> **v = (the part inside W) + (the part perpendicular to W)**

and this splitting is unique. The perpendicular leftover is the *error* you can't avoid, and its length is the shortest possible distance from v to W. That single fact powers all of least squares (Chapter 6).

**Gram–Schmidt** is a machine for turning a crooked set of directions into a right-angled set that spans the same thing. Take the first vector as-is. Take the second, and subtract off whatever part of it agrees with the first — what's left is perpendicular. Take the third, subtract off its agreement with both previous ones. Keep going. You end up with a perfectly square coordinate frame for the same space.

**Orthonormal** means orthogonal *and* every vector has length 1. Then the arithmetic becomes trivial: no dividing, no normalizing, and the matrix Q with those columns satisfies QᵀQ = I — the transpose *is* the inverse.

---

## 5.2 The Formal Theory

### 5.2.1 Inner Product, Length, Distance

For u, v ∈ ℝⁿ, the **inner (dot) product** is

> u · v = uᵀv = u₁v₁ + u₂v₂ + ... + uₙvₙ

**Properties:** (i) u·v = v·u; (ii) (u+v)·w = u·w + v·w; (iii) (cu)·v = c(u·v); (iv) u·u ≥ 0 with equality ⟺ u = 0.

**Norm (length):** ‖v‖ = √(v·v) = √(v₁² + ... + vₙ²). Note ‖cv‖ = |c|·‖v‖.

A vector with ‖v‖ = 1 is a **unit vector**. **Normalizing** v means forming u = v/‖v‖.

**Distance:** dist(u, v) = ‖u − v‖.

**Angle:** cos θ = (u·v)/(‖u‖‖v‖).

> **Cauchy–Schwarz inequality:** |u·v| ≤ ‖u‖‖v‖
> **Triangle inequality:** ‖u + v‖ ≤ ‖u‖ + ‖v‖

### 5.2.2 Orthogonality

u and v are **orthogonal** if u·v = 0. Written u ⊥ v.

> **Pythagorean Theorem.** u ⊥ v ⟺ ‖u + v‖² = ‖u‖² + ‖v‖².

**Orthogonal complement.** For a subspace W ⊆ ℝⁿ,

> W⊥ = {z ∈ ℝⁿ : z · w = 0 for all w ∈ W}

W⊥ is itself a subspace, and:
1. z ∈ W⊥ ⟺ z is orthogonal to every vector in *any spanning set* of W (you needn't test infinitely many).
2. (W⊥)⊥ = W.
3. **dim W + dim W⊥ = n.**
4. W ∩ W⊥ = {0}.

> **Theorem 5.1 (Fundamental Subspaces).** For any m×n matrix A:
> **(Row A)⊥ = Nul A** and **(Col A)⊥ = Nul Aᵀ**

*Proof of the first:* Ax = 0 means each row of A dotted with x equals 0, which means x ⊥ every row, hence x ⊥ Row(A). ∎

### 5.2.3 Orthogonal Sets and Bases

A set {u₁, ..., u_p} is an **orthogonal set** if uᵢ·uⱼ = 0 for all i ≠ j. It is **orthonormal** if additionally ‖uᵢ‖ = 1 for all i.

> **Theorem 5.2.** An orthogonal set of **nonzero** vectors is automatically linearly independent.

*Proof:* If Σcᵢuᵢ = 0, dot both sides with uⱼ: cⱼ(uⱼ·uⱼ) = 0. Since uⱼ ≠ 0, uⱼ·uⱼ > 0, so cⱼ = 0. ∎

> **Theorem 5.3 (Easy coordinates).** If {u₁, ..., u_p} is an **orthogonal basis** for W, then any y ∈ W has
>
> **y = Σᵢ (y·uᵢ)/(uᵢ·uᵢ) · uᵢ**
>
> If the basis is **orthonormal**, this simplifies to **y = Σᵢ (y·uᵢ) uᵢ**.

*This is the payoff of orthogonality:* no linear system to solve. Compare with a general basis, where finding coordinates requires inverting a matrix.

### 5.2.4 Orthogonal Projection

**Onto a single vector u:**
> proj_u(y) = ((y·u)/(u·u)) u

The scalar (y·u)/(u·u) is the **component of y along u**. The leftover z = y − proj_u(y) satisfies z ⊥ u.

**Onto a subspace W with orthogonal basis {u₁,...,u_p}:**
> **proj_W(y) = Σᵢ ((y·uᵢ)/(uᵢ·uᵢ)) uᵢ**

> **Theorem 5.4 (Orthogonal Decomposition Theorem).** Let W be a subspace of ℝⁿ. Every y ∈ ℝⁿ can be written **uniquely** as
> **y = ŷ + z** with ŷ ∈ W and z ∈ W⊥.
> Here ŷ = proj_W(y), and z = y − ŷ is called the **component of y orthogonal to W**.

> **Theorem 5.5 (Best Approximation Theorem).** ŷ = proj_W(y) is the **closest point in W to y**: for every other v ∈ W,
> **‖y − ŷ‖ < ‖y − v‖**

*Proof:* y − v = (y − ŷ) + (ŷ − v). The first term is in W⊥, the second in W, so they're orthogonal. Pythagoras gives ‖y−v‖² = ‖y−ŷ‖² + ‖ŷ−v‖² ≥ ‖y−ŷ‖², with equality only when v = ŷ. ∎

**This theorem is the reason projections matter.** "Closest point" = "least error" = least squares.

### 5.2.5 Projection Matrices

If the columns of U form an **orthonormal** basis for W, then

> **proj_W(y) = UUᵀ y**

So P = UUᵀ is the **projection matrix** onto W. Properties:
- **P² = P** (idempotent — projecting twice is the same as once)
- **Pᵀ = P** (symmetric)
- eigenvalues of P are only 0 and 1
- rank(P) = dim W = trace(P)
- I − P is the projection onto W⊥

For a **general** (not necessarily orthonormal) basis in the columns of A with independent columns:

> **P = A(AᵀA)⁻¹Aᵀ**

### 5.2.6 Orthogonal Matrices

A square matrix Q with **orthonormal columns** satisfies QᵀQ = I, hence **Q⁻¹ = Qᵀ**. Such Q is called **orthogonal**.

**Key properties (Q orthogonal):**
1. ‖Qx‖ = ‖x‖ — **preserves length** (isometry)
2. (Qx)·(Qy) = x·y — **preserves angles**
3. det Q = ±1
4. Rows of Q are also orthonormal
5. Product of orthogonal matrices is orthogonal

Geometrically, orthogonal matrices are exactly the **rotations** (det = +1) and **reflections/improper rotations** (det = −1).

*Terminology note:* for a non-square m×n matrix U with orthonormal columns, UᵀU = Iₙ but UUᵀ ≠ Iₘ. Such a U is said to have orthonormal columns but is not called "orthogonal" (that term is reserved for square matrices).

### 5.2.7 The Gram–Schmidt Process

**Input:** a basis {x₁, ..., x_p} for W. **Output:** an orthogonal basis {v₁, ..., v_p} for W with

> Span{v₁,...,v_k} = Span{x₁,...,x_k} for every k.

**Algorithm:**
```
v₁ = x₁
v₂ = x₂ − ((x₂·v₁)/(v₁·v₁)) v₁
v₃ = x₃ − ((x₃·v₁)/(v₁·v₁)) v₁ − ((x₃·v₂)/(v₂·v₂)) v₂
⋮
v_k = x_k − Σ_{j<k} ((x_k·v_j)/(v_j·v_j)) v_j
```

In words: at each step, take the next input vector and **subtract off its projection onto everything you've built so far**.

To get an **orthonormal** basis, normalize at the end: uᵢ = vᵢ/‖vᵢ‖.

**Practical tip:** after computing each vᵢ, you may rescale it by any nonzero constant (to clear fractions) without breaking orthogonality. This saves enormous arithmetic pain. Do it.

### 5.2.8 QR Factorization

> **Theorem 5.6.** If A is m×n with **linearly independent columns**, then A = QR where
> - Q is m×n with orthonormal columns (from Gram–Schmidt on A's columns),
> - R is n×n upper triangular with **positive diagonal entries**, and R = QᵀA.

**How to build it:** run Gram–Schmidt to get Q. Then R = QᵀA. Since Span{q₁,...,q_k} = Span{a₁,...,a_k}, the entry Rᵢⱼ = qᵢ·aⱼ is zero whenever i > j, giving the triangular shape automatically.

**Uses:** solving least squares stably (`Rx = Qᵀb`), and the QR algorithm for computing eigenvalues (Chapter 9).

---

## 5.3 Solved Examples

### Example 5.1 — [Easy] Dot products, norms, angle

For u = (1, 2, −2) and v = (3, 0, 4), compute u·v, ‖u‖, ‖v‖, the angle between them, and dist(u, v).

**Solution.**
- u·v = 1(3) + 2(0) + (−2)(4) = 3 − 8 = **−5**
- ‖u‖ = √(1 + 4 + 4) = √9 = **3**
- ‖v‖ = √(9 + 0 + 16) = √25 = **5**
- cos θ = −5/(3·5) = −1/3, so θ = arccos(−1/3) ≈ **109.47°** (obtuse, as the negative dot product predicted)
- u − v = (−2, 2, −6); dist = √(4 + 4 + 36) = √44 = **2√11 ≈ 6.63**

---

### Example 5.2 — [Easy] Projection onto a line

Find the orthogonal projection of y = (7, 6) onto u = (4, 2), and the perpendicular component.

**Solution.**
y·u = 28 + 12 = 40. u·u = 16 + 4 = 20.

ŷ = (40/20)(4, 2) = 2(4, 2) = **(8, 4)**

z = y − ŷ = (7 − 8, 6 − 4) = **(−1, 2)**

**Check orthogonality:** z·u = −4 + 4 = 0 ✓
**Check decomposition:** (8,4) + (−1,2) = (7,6) ✓
**Distance from y to the line:** ‖z‖ = √5.

---

### Example 5.3 — [Medium] Coordinates in an orthogonal basis

Verify that {u₁, u₂, u₃} with u₁ = (3, 1, 1), u₂ = (−1, 2, 1), u₃ = (−1/2, −2, 7/2) is an orthogonal basis of ℝ³, and express y = (6, 1, −8) in it.

**Solution.**
**Orthogonality check:**
- u₁·u₂ = −3 + 2 + 1 = 0 ✓
- u₁·u₃ = −3/2 − 2 + 7/2 = 0 ✓
- u₂·u₃ = 1/2 − 4 + 7/2 = 0 ✓

Three nonzero orthogonal vectors in ℝ³ → independent → basis ✓

**Coordinates** via Theorem 5.3:
- y·u₁ = 18 + 1 − 8 = 11; u₁·u₁ = 9+1+1 = 11 → c₁ = 1
- y·u₂ = −6 + 2 − 8 = −12; u₂·u₂ = 1+4+1 = 6 → c₂ = −2
- y·u₃ = −3 − 2 − 28 = −33; u₃·u₃ = 1/4 + 4 + 49/4 = 50/4 + 4 = 33/2 → c₃ = −33/(33/2) = −2

**Answer:** y = 1·u₁ − 2·u₂ − 2·u₃.

*Verify:* (3,1,1) − 2(−1,2,1) − 2(−1/2,−2,7/2) = (3+2+1, 1−4+4, 1−2−7) = (6, 1, −8) ✓

Note how no linear system was solved — that is the entire advantage of an orthogonal basis.

---

### Example 5.4 — [Medium] Projection onto a plane

Let W = Span{u₁, u₂} with u₁ = (1, 1, 0, −1), u₂ = (1, 0, 1, 1). Find proj_W(y) for y = (2, 3, 1, 4), and the distance from y to W.

**Solution.** First confirm orthogonality: u₁·u₂ = 1 + 0 + 0 − 1 = 0 ✓

- y·u₁ = 2 + 3 + 0 − 4 = 1; u₁·u₁ = 1+1+0+1 = 3 → coefficient 1/3
- y·u₂ = 2 + 0 + 1 + 4 = 7; u₂·u₂ = 1+0+1+1 = 3 → coefficient 7/3

ŷ = (1/3)(1,1,0,−1) + (7/3)(1,0,1,1) = (1/3 + 7/3, 1/3, 7/3, −1/3 + 7/3)
= **(8/3, 1/3, 7/3, 2)**

z = y − ŷ = (2 − 8/3, 3 − 1/3, 1 − 7/3, 4 − 2) = (−2/3, 8/3, −4/3, 2)

**Check:** z·u₁ = −2/3 + 8/3 + 0 − 2 = 6/3 − 2 = 0 ✓; z·u₂ = −2/3 + 0 − 4/3 + 2 = −2 + 2 = 0 ✓

**Distance** = ‖z‖ = √(4/9 + 64/9 + 16/9 + 4) = √(84/9 + 36/9) = √(120/9) = **(2√30)/3 ≈ 3.65**

---

### Example 5.5 — [Hard] Gram–Schmidt, full

Apply Gram–Schmidt to x₁ = (1, 1, 1, 1), x₂ = (0, 1, 1, 1), x₃ = (0, 0, 1, 1) to produce an orthogonal (then orthonormal) basis.

**Solution.**

**v₁ = x₁ = (1, 1, 1, 1).** v₁·v₁ = 4.

**v₂:** x₂·v₁ = 0 + 1 + 1 + 1 = 3.
v₂ = (0,1,1,1) − (3/4)(1,1,1,1) = (−3/4, 1/4, 1/4, 1/4).
*Rescale by 4:* **v₂ = (−3, 1, 1, 1).** v₂·v₂ = 9+1+1+1 = 12.

**v₃:** x₃·v₁ = 0+0+1+1 = 2. x₃·v₂ = 0 + 0 + 1 + 1 = 2.
v₃ = (0,0,1,1) − (2/4)(1,1,1,1) − (2/12)(−3,1,1,1)
= (0,0,1,1) − (1/2,1/2,1/2,1/2) − (−1/2, 1/6, 1/6, 1/6)
= (0 − 1/2 + 1/2, 0 − 1/2 − 1/6, 1 − 1/2 − 1/6, 1 − 1/2 − 1/6)
= (0, −2/3, 1/3, 1/3).
*Rescale by 3:* **v₃ = (0, −2, 1, 1).** v₃·v₃ = 0+4+1+1 = 6.

**Verify all pairs:**
- v₁·v₂ = −3+1+1+1 = 0 ✓
- v₁·v₃ = 0−2+1+1 = 0 ✓
- v₂·v₃ = 0−2+1+1 = 0 ✓

**Orthonormal basis:**
- q₁ = (1/2)(1,1,1,1)
- q₂ = (1/√12)(−3,1,1,1) = (1/(2√3))(−3,1,1,1)
- q₃ = (1/√6)(0,−2,1,1)

---

### Example 5.6 — [Hard] QR factorization

Find the QR factorization of A = [[1, 0], [1, 1], [1, 2]].

**Solution.** Columns: a₁ = (1,1,1), a₂ = (0,1,2).

**Gram–Schmidt.**
v₁ = (1,1,1), ‖v₁‖ = √3 → **q₁ = (1/√3)(1,1,1)**.

a₂·v₁ = 0+1+2 = 3; v₁·v₁ = 3. So
v₂ = (0,1,2) − 1·(1,1,1) = (−1, 0, 1), ‖v₂‖ = √2 → **q₂ = (1/√2)(−1, 0, 1)**.

```
Q = [[ 1/√3, −1/√2],
     [ 1/√3,   0  ],
     [ 1/√3,  1/√2]]
```

**Compute R = QᵀA:**
- R₁₁ = q₁·a₁ = (1+1+1)/√3 = 3/√3 = **√3**
- R₁₂ = q₁·a₂ = (0+1+2)/√3 = 3/√3 = **√3**
- R₂₁ = q₂·a₁ = (−1+0+1)/√2 = **0** ✓ (must be 0 — triangular)
- R₂₂ = q₂·a₂ = (0 + 0 + 2)/√2 = 2/√2 = **√2**

```
R = [[√3, √3],
     [0,  √2]]
```

**Verify:** QR column 2 = √3·q₁ + √2·q₂ = (1,1,1) + (−1,0,1) = (0,1,2) ✓ = a₂

---

### Example 5.7 — [Very Hard] Projection matrix from a non-orthogonal basis

Let W = Col(A) with A = [[1, 1], [1, 2], [1, 3]]. Find the projection matrix P onto W, verify P² = P, and compute proj_W((1, 2, 4)ᵀ).

**Solution.** Use P = A(AᵀA)⁻¹Aᵀ.

**AᵀA:**
```
AᵀA = [[1,1,1],[1,2,3]] · [[1,1],[1,2],[1,3]]
    = [[3, 6], [6, 14]]
```
det = 42 − 36 = 6. So (AᵀA)⁻¹ = (1/6)[[14, −6], [−6, 3]].

**A(AᵀA)⁻¹:**
```
= (1/6)·[[1,1],[1,2],[1,3]]·[[14,−6],[−6,3]]
= (1/6)·[[14−6, −6+3], [14−12, −6+6], [14−18, −6+9]]
= (1/6)·[[8, −3], [2, 0], [−4, 3]]
```

**P = A(AᵀA)⁻¹Aᵀ:**
```
= (1/6)·[[8,−3],[2,0],[−4,3]] · [[1,1,1],[1,2,3]]
```
Row 1: (8−3, 8−6, 8−9) = (5, 2, −1)
Row 2: (2+0, 2+0, 2+0) = (2, 2, 2)
Row 3: (−4+3, −4+6, −4+9) = (−1, 2, 5)

```
P = (1/6)·[[ 5, 2, −1],
           [ 2, 2,  2],
           [−1, 2,  5]]
```

**Checks:**
- **Symmetric?** ✓ (visibly)
- **trace(P)** = (5 + 2 + 5)/6 = 12/6 = 2 = dim W ✓ (rank of a projection = its trace)
- **P² = P?** Compute row 1 of P·P: (1/36)[(25+4+1), (10+4−2), (−5+4−5)] = (1/36)(30, 12, −6) = (1/6)(5, 2, −1) ✓ matches row 1 of P.

**Projection of y = (1, 2, 4):**
Py = (1/6)(5+4−4, 2+4+8, −1+4+20) = (1/6)(5, 14, 23) = **(5/6, 7/3, 23/6)**

**Residual:** y − Py = (1/6, −2/6, 1/6) = (1/6)(1, −2, 1).
*Check it's orthogonal to both columns of A:* (1,−2,1)·(1,1,1) = 0 ✓ and (1,−2,1)·(1,2,3) = 1 − 4 + 3 = 0 ✓

---

### Example 5.8 — [Very Hard] Orthogonal complement and the fundamental theorem

Let A = [[1, 2, 1, 3], [2, 4, 3, 5]]. Find bases for all four fundamental subspaces and verify the orthogonality relations and the dimension counts.

**Solution.** Reduce A: `R₂ → R₂ − 2R₁` → [[1, 2, 1, 3], [0, 0, 1, −1]]. Then `R₁ → R₁ − R₂` → [[1, 2, 0, 4], [0, 0, 1, −1]].

rank = 2. m = 2, n = 4.

**Row(A)** (dim 2): basis from nonzero RREF rows: **{(1,2,0,4), (0,0,1,−1)}**

**Col(A)** (dim 2): original pivot columns 1 and 3: **{(1,2)ᵀ, (1,3)ᵀ}**. Since dim = 2 = m, Col(A) = ℝ².

**Nul(A)** (dim n − r = 2): free x₂ = s, x₄ = t. x₁ = −2s − 4t, x₃ = t.
**Basis: {(−2, 1, 0, 0), (−4, 0, 1, 1)}**

**Nul(Aᵀ)** (dim m − r = 2 − 2 = **0**): only the zero vector. **Basis: ∅** (Aᵀ has independent columns).

**Verification of Row(A) ⊥ Nul(A):**
- (1,2,0,4)·(−2,1,0,0) = −2 + 2 = 0 ✓
- (1,2,0,4)·(−4,0,1,1) = −4 + 0 + 0 + 4 = 0 ✓
- (0,0,1,−1)·(−2,1,0,0) = 0 ✓
- (0,0,1,−1)·(−4,0,1,1) = 1 − 1 = 0 ✓

**Dimension counts:**
- dim Row + dim Nul = 2 + 2 = 4 = n ✓
- dim Col + dim Nul(Aᵀ) = 2 + 0 = 2 = m ✓

---

## 5.4 Practice Numericals — Chapter 5

**[Easy]**

**P5.1** Compute u·v, ‖u‖, and determine whether u ⊥ v for u = (2, −1, 3), v = (1, 5, 1).

**P5.2** Normalize the vector (3, −4, 12).

**P5.3** Find proj_u(y) for y = (4, 3), u = (1, 0). Interpret geometrically.

**P5.4** Verify that Q = [[cos θ, −sin θ], [sin θ, cos θ]] is orthogonal for every θ. Compute det Q.

**P5.5** Find all vectors in ℝ³ orthogonal to both (1, 0, 1) and (0, 1, 1).

**[Medium]**

**P5.6** Apply Gram–Schmidt to {(1, 2, 2), (2, 2, 1)} and normalize.

**P5.7** Find the orthogonal projection of (1, 1, 1) onto W = Span{(1, 0, 1), (1, 1, −1)}, having first checked the spanning vectors are orthogonal.

**P5.8** Find a basis for W⊥ where W = Span{(1, 2, 3, 4)} ⊆ ℝ⁴.

**P5.9** Find the QR factorization of A = [[1, 1], [0, 1], [1, 0]].

**P5.10** Show that if P is a projection matrix onto W, then I − P is the projection onto W⊥. Verify for P = (1/2)[[1,1],[1,1]].

**P5.11** Find the distance from the point (1, 2, 3) to the plane spanned by (1, 1, 0) and (0, 1, 1).

**[Hard]**

**P5.12** Apply Gram–Schmidt to the columns of A = [[1, 1, 1], [1, 1, 0], [1, 0, 0]] and write the QR factorization.

**P5.13** Find the projection matrix onto the line through (2, −1, 2) in ℝ³, verify idempotence and symmetry, and give its rank and trace.

**P5.14** Let W = Nul(A) for A = [[1, −1, 2, 0], [0, 1, −1, 1]]. Find a basis for W and for W⊥, and verify dim W + dim W⊥ = 4.

**P5.15** Use Gram–Schmidt on {1, t, t²} in P₂ with the inner product ⟨f, g⟩ = ∫₋₁¹ f(t)g(t) dt to obtain the first three **Legendre polynomials** (up to scaling).

**P5.16** Prove that a square matrix Q is orthogonal if and only if ‖Qx‖ = ‖x‖ for every x.

**[Very Hard]**

**P5.17** Let W be a subspace of ℝⁿ with orthonormal basis {u₁,...,u_p}, and let U = [u₁ ... u_p]. Prove UUᵀ is the projection onto W and UᵀU = I_p. Explain precisely why UUᵀ ≠ Iₙ unless p = n.

**P5.18** **(Bessel's inequality)** Let {u₁,...,u_p} be an orthonormal set in ℝⁿ (not necessarily a basis). Prove that for any y,
Σᵢ (y·uᵢ)² ≤ ‖y‖², with equality iff y ∈ Span{u₁,...,u_p}.

**P5.19** Let A be m×n with independent columns, and P = A(AᵀA)⁻¹Aᵀ. Prove P² = P, Pᵀ = P, rank P = n, and that P is independent of which basis of Col(A) is used to build it. (Hint: replace A by AM for invertible M.)

**P5.20** **(Householder reflection.)** For a unit vector v ∈ ℝⁿ, define H = I − 2vvᵀ. Prove H is symmetric and orthogonal, that H² = I, and that Hv = −v while Hw = w for every w ⊥ v. Compute H for v = (1/√2)(1, −1) and describe its geometric effect.

---

## 5.5 Solutions to Chapter 5 Practice

**S5.1** u·v = 2 − 5 + 3 = **0** → **orthogonal** ✓. ‖u‖ = √(4+1+9) = **√14**.

**S5.2** ‖(3,−4,12)‖ = √(9 + 16 + 144) = √169 = 13. **Unit vector: (3/13, −4/13, 12/13).**

**S5.3** y·u = 4, u·u = 1. proj = **(4, 0)**. Geometrically: the shadow of y on the x-axis — it keeps the x-component and discards the y-component.

**S5.4** QᵀQ = [[cos θ, sin θ],[−sin θ, cos θ]]·[[cos θ, −sin θ],[sin θ, cos θ]]
= [[cos²+sin², −cos sin + sin cos],[−sin cos + cos sin, sin² + cos²]] = [[1,0],[0,1]] = I ✓
det Q = cos²θ + sin²θ = **1** → a **rotation** by angle θ.

**S5.5** Need x·(1,0,1) = 0 and x·(0,1,1) = 0:
x₁ + x₃ = 0, x₂ + x₃ = 0. Let x₃ = t: x₁ = −t, x₂ = −t.
**Answer:** span{(−1, −1, 1)} (equivalently the cross product (1,0,1)×(0,1,1) = (−1,−1,1)).

**S5.6** v₁ = (1,2,2), v₁·v₁ = 9.
x₂·v₁ = 2 + 4 + 2 = 8.
v₂ = (2,2,1) − (8/9)(1,2,2) = (2 − 8/9, 2 − 16/9, 1 − 16/9) = (10/9, 2/9, −7/9).
Rescale by 9: **v₂ = (10, 2, −7)**. Check: (1,2,2)·(10,2,−7) = 10 + 4 − 14 = 0 ✓
‖v₁‖ = 3; ‖v₂‖ = √(100 + 4 + 49) = √153 = 3√17.
**Orthonormal:** q₁ = (1/3)(1,2,2), q₂ = (1/(3√17))(10, 2, −7).

**S5.7** Check: (1,0,1)·(1,1,−1) = 1 + 0 − 1 = 0 ✓ orthogonal.
y = (1,1,1). y·u₁ = 1 + 0 + 1 = 2; u₁·u₁ = 2 → coefficient 1.
y·u₂ = 1 + 1 − 1 = 1; u₂·u₂ = 1+1+1 = 3 → coefficient 1/3.
proj = 1(1,0,1) + (1/3)(1,1,−1) = **(4/3, 1/3, 2/3)**.
*Residual:* (1,1,1) − (4/3,1/3,2/3) = (−1/3, 2/3, 1/3). Check ⊥ u₁: −1/3 + 1/3 = 0 ✓

**S5.8** W⊥ = {x : x₁ + 2x₂ + 3x₃ + 4x₄ = 0} = Nul([1 2 3 4]). Three free variables.
x₁ = −2x₂ − 3x₃ − 4x₄.
**Basis:** {(−2,1,0,0), (−3,0,1,0), (−4,0,0,1)}. dim W⊥ = 3 = 4 − 1 ✓

**S5.9** a₁ = (1,0,1), a₂ = (1,1,0).
v₁ = (1,0,1), ‖v₁‖ = √2 → q₁ = (1/√2)(1,0,1).
a₂·v₁ = 1 + 0 + 0 = 1; v₁·v₁ = 2.
v₂ = (1,1,0) − (1/2)(1,0,1) = (1/2, 1, −1/2). Rescale by 2: (1, 2, −1), ‖·‖ = √6.
q₂ = (1/√6)(1, 2, −1).
```
Q = [[1/√2,  1/√6],
     [0,     2/√6],
     [1/√2, −1/√6]]
```
R₁₁ = q₁·a₁ = 2/√2 = √2. R₁₂ = q₁·a₂ = 1/√2. R₂₂ = q₂·a₂ = (1 + 2 + 0)/√6 = 3/√6.
```
R = [[√2, 1/√2],
     [0,  3/√6]]
```

**S5.10** Since y = proj_W(y) + proj_{W⊥}(y) = Py + (I−P)y, and the decomposition is unique with the second piece in W⊥, we get proj_{W⊥} = I − P. ✓
Formally: (I−P)² = I − 2P + P² = I − 2P + P = I − P ✓ (idempotent), and (I−P)ᵀ = I − P ✓ (symmetric), and Col(I − P) = Nul(P) = W⊥.
For P = (1/2)[[1,1],[1,1]] (projection onto the line y = x): I − P = (1/2)[[1,−1],[−1,1]], which projects onto the line y = −x ✓ — indeed perpendicular.

**S5.11** u₁ = (1,1,0), u₂ = (0,1,1). **Not orthogonal** (u₁·u₂ = 1), so Gram–Schmidt first.
v₁ = (1,1,0), v₁·v₁ = 2.
v₂ = (0,1,1) − (1/2)(1,1,0) = (−1/2, 1/2, 1) → rescale by 2: **v₂ = (−1, 1, 2)**, v₂·v₂ = 6.
y = (1,2,3). y·v₁ = 1 + 2 = 3. y·v₂ = −1 + 2 + 6 = 7.
proj = (3/2)(1,1,0) + (7/6)(−1,1,2) = (3/2 − 7/6, 3/2 + 7/6, 14/6) = (2/6·... let's compute: 9/6 − 7/6 = 2/6 = 1/3; 9/6 + 7/6 = 16/6 = 8/3; 7/3)
proj = (1/3, 8/3, 7/3).
Residual z = (1 − 1/3, 2 − 8/3, 3 − 7/3) = (2/3, −2/3, 2/3).
**Distance** = ‖z‖ = (2/3)√3 = **2/√3 ≈ 1.155**
*Check:* z·u₁ = 2/3 − 2/3 = 0 ✓; z·u₂ = −2/3 + 2/3 = 0 ✓

**S5.12** a₁ = (1,1,1), a₂ = (1,1,0), a₃ = (1,0,0).
v₁ = (1,1,1), v₁·v₁ = 3, ‖v₁‖ = √3.
a₂·v₁ = 2. v₂ = (1,1,0) − (2/3)(1,1,1) = (1/3, 1/3, −2/3) → rescale ×3: **(1, 1, −2)**, norm √6.
a₃·v₁ = 1; a₃·v₂ = 1 (using v₂ = (1,1,−2), v₂·v₂ = 6).
v₃ = (1,0,0) − (1/3)(1,1,1) − (1/6)(1,1,−2) = (1 − 1/3 − 1/6, −1/3 − 1/6, −1/3 + 1/3)
= (1/2, −1/2, 0) → rescale ×2: **(1, −1, 0)**, norm √2.
```
Q = [[1/√3,  1/√6,  1/√2],
     [1/√3,  1/√6, −1/√2],
     [1/√3, −2/√6,   0  ]]
```
R = QᵀA:
- R₁₁ = 3/√3 = √3; R₁₂ = 2/√3; R₁₃ = 1/√3
- R₂₂ = q₂·a₂ = (1+1+0)/√6 = 2/√6; R₂₃ = q₂·a₃ = 1/√6
- R₃₃ = q₃·a₃ = 1/√2
```
R = [[√3, 2/√3, 1/√3],
     [0,  2/√6, 1/√6],
     [0,  0,    1/√2]]
```

**S5.13** u = (2,−1,2), u·u = 4+1+4 = 9.
P = uuᵀ/(uᵀu) = (1/9)[[4, −2, 4], [−2, 1, −2], [4, −2, 4]].
**Symmetric** ✓ visibly.
**Idempotent:** P² = uuᵀuuᵀ/81 = u(9)uᵀ/81 = uuᵀ/9 = P ✓
**rank P = 1** (projection onto a line). **trace P = (4 + 1 + 4)/9 = 1** ✓ = rank.

**S5.14** Reduce A: `R₁ → R₁ + R₂` → [[1, 0, 1, 1], [0, 1, −1, 1]]. Pivots cols 1, 2; free x₃ = s, x₄ = t.
x₁ = −s − t, x₂ = s − t.
**W = Nul(A) basis: {(−1, 1, 1, 0), (−1, −1, 0, 1)}.** dim W = 2.
**W⊥ = (Nul A)⊥ = Row(A)**, basis **{(1, 0, 1, 1), (0, 1, −1, 1)}**. dim = 2.
**2 + 2 = 4 ✓**
*Spot check:* (1,0,1,1)·(−1,1,1,0) = −1 + 0 + 1 + 0 = 0 ✓

**S5.15** Inner product ⟨f,g⟩ = ∫₋₁¹ fg dt.
**p₀ = 1.** ⟨1,1⟩ = ∫₋₁¹ dt = 2.
**p₁:** ⟨t, 1⟩ = ∫₋₁¹ t dt = 0 (odd function). So p₁ = t − 0 = **t**. ⟨t,t⟩ = ∫₋₁¹ t² dt = 2/3.
**p₂:** ⟨t², 1⟩ = ∫₋₁¹ t² dt = 2/3. ⟨t², t⟩ = ∫₋₁¹ t³ dt = 0 (odd).
p₂ = t² − (2/3)/(2)·1 − 0 = **t² − 1/3**.

**Answer:** {1, t, t² − 1/3} — the Legendre polynomials P₀, P₁, and (2/3)P₂ up to scaling (the standard normalization P₂(t) = (3t² − 1)/2 = (3/2)(t² − 1/3)).

**S5.16**
(⇒) If QᵀQ = I: ‖Qx‖² = (Qx)ᵀ(Qx) = xᵀQᵀQx = xᵀx = ‖x‖² ✓

(⇐) Suppose ‖Qx‖ = ‖x‖ for all x. Then xᵀ(QᵀQ − I)x = 0 for all x. Let M = QᵀQ − I, which is **symmetric**. For a symmetric M, xᵀMx = 0 for all x forces M = 0:
take x = eᵢ → Mᵢᵢ = 0; take x = eᵢ + eⱼ → Mᵢᵢ + Mⱼⱼ + 2Mᵢⱼ = 0 → Mᵢⱼ = 0.
So QᵀQ = I. ∎

**S5.17**
**UᵀU = I_p:** the (i,j) entry is uᵢ·uⱼ = δᵢⱼ by orthonormality ✓

**UUᵀ is the projection:** for any y,
UUᵀy = U(Uᵀy) = U(y·u₁, ..., y·u_p)ᵀ = Σᵢ (y·uᵢ)uᵢ,
which is exactly the formula for proj_W(y) with an orthonormal basis (Theorem 5.4). ∎

**Why UUᵀ ≠ Iₙ when p < n:** rank(UUᵀ) ≤ rank(U) = p < n, so UUᵀ is singular and cannot equal the identity. Concretely, any z ∈ W⊥ (which is nonzero when p < n) satisfies UUᵀz = proj_W(z) = 0 ≠ z. The two products differ because **UᵀU contracts then expands** (p→n→p, fully recovering), while **UUᵀ expands then contracts** (n→p→n, losing the W⊥ component).

**S5.18** Let ŷ = Σᵢ(y·uᵢ)uᵢ = proj_W(y) where W = Span{uᵢ}, and z = y − ŷ ∈ W⊥.

By Pythagoras (ŷ ⊥ z):
‖y‖² = ‖ŷ‖² + ‖z‖² ≥ ‖ŷ‖².

Now ‖ŷ‖² = ‖Σ(y·uᵢ)uᵢ‖² = Σᵢ(y·uᵢ)² by orthonormality (cross terms vanish).

Therefore **Σᵢ(y·uᵢ)² ≤ ‖y‖²** ✓

Equality holds ⟺ ‖z‖ = 0 ⟺ y = ŷ ⟺ y ∈ W. ∎

**S5.19** Write G = AᵀA (invertible since columns of A are independent — see S3.14).

**P² = A G⁻¹Aᵀ A G⁻¹Aᵀ = A G⁻¹ (AᵀA) G⁻¹Aᵀ = A G⁻¹ G G⁻¹ Aᵀ = A G⁻¹Aᵀ = P** ✓

**Pᵀ = (AG⁻¹Aᵀ)ᵀ = A (G⁻¹)ᵀ Aᵀ.** Since G is symmetric, so is G⁻¹. Hence Pᵀ = AG⁻¹Aᵀ = P ✓

**rank P:** Col(P) ⊆ Col(A). Conversely, for any x, P(Ax) = AG⁻¹AᵀAx = AG⁻¹Gx = Ax, so every vector of Col(A) is fixed by P and lies in Col(P). Hence **Col(P) = Col(A)** and rank P = n ✓

**Basis independence.** Replace A by B = AM with M invertible n×n (this is exactly a change of basis for Col(A), since Col(B) = Col(A)). Then
BᵀB = MᵀAᵀAM = MᵀGM, so (BᵀB)⁻¹ = M⁻¹G⁻¹(Mᵀ)⁻¹.
B(BᵀB)⁻¹Bᵀ = AM·M⁻¹G⁻¹(Mᵀ)⁻¹·MᵀAᵀ = A G⁻¹ Aᵀ = P ✓
**P depends only on the subspace, not the basis.** ∎

**S5.20** With ‖v‖ = 1 so vᵀv = 1:

**Symmetric:** Hᵀ = (I − 2vvᵀ)ᵀ = I − 2(vvᵀ)ᵀ = I − 2vvᵀ = H ✓

**H² = I:** H² = (I − 2vvᵀ)(I − 2vvᵀ) = I − 4vvᵀ + 4v(vᵀv)vᵀ = I − 4vvᵀ + 4vvᵀ = I ✓

**Orthogonal:** HᵀH = H·H = I ✓ (symmetric + involutory ⟹ orthogonal)

**Hv = v − 2v(vᵀv) = v − 2v = −v** ✓ (v is flipped)
**For w ⊥ v (vᵀw = 0): Hw = w − 2v(vᵀw) = w − 0 = w** ✓ (w is fixed)

So H reflects across the hyperplane v⊥. Eigenvalues: −1 (once, eigenvector v) and +1 (n−1 times). det H = −1.

**For v = (1/√2)(1, −1):**
vvᵀ = (1/2)[[1, −1], [−1, 1]].
H = I − 2(1/2)[[1,−1],[−1,1]] = [[1,0],[0,1]] − [[1,−1],[−1,1]] = **[[0, 1], [1, 0]]**.

**Geometric effect:** H swaps the two coordinates — it is the reflection across the line **y = x**. Check: v = (1,−1)/√2 is perpendicular to that line, and H(1,−1) = (−1, 1) = −v ✓; the line's direction (1,1) satisfies H(1,1) = (1,1) ✓ fixed.

*Householder reflections are the standard numerical tool for computing QR factorizations — more stable than Gram–Schmidt.*

---
# Chapter 6 — Least Squares Problems and Linear Models

---

## 6.1 Explain Like I'm Five

Sometimes a system of equations has **no solution** — the clues genuinely contradict each other. In real life this happens constantly, because measurements have noise. You measure the same thing five times and get five slightly different numbers. No single answer fits all five perfectly.

So you give up on "perfect" and ask a better question: **what answer is least wrong?**

Picture it. You have a target vector **b** floating somewhere in space, and you have a *plane* (or a line, or some flat subspace) consisting of everything you can actually reach — that's Col(A), all the vectors of the form Ax. If b isn't on the plane, no x gives Ax = b exactly.

So you drop a perpendicular from b down to the plane. The foot of that perpendicular — the shadow, the projection — is the closest reachable point. Call it b̂. Then solve `Ax̂ = b̂`, which *does* have a solution because b̂ is on the plane by construction.

That x̂ is the **least squares solution**. It's the answer that makes the leftover error `‖b − Ax‖` as small as possible. We square the error before adding (hence "least squares") because squaring makes all errors positive and makes the calculus clean.

**The magic trick.** You never actually have to compute the projection. Because the error vector must be perpendicular to the plane, it must be perpendicular to every column of A. Writing that down gives

> Aᵀ(b − Ax̂) = 0, i.e. **AᵀAx̂ = Aᵀb**

These are the **normal equations**. They're an ordinary square system you can just solve. That's the whole method.

**Line fitting.** When someone says "fit a straight line to this data", they mean: find the slope and intercept that make the total squared vertical distance from points to line as small as possible. That's a least squares problem where A's columns are a column of 1s and a column of x-values.

---

## 6.2 The Formal Theory

### 6.2.1 The Least Squares Problem

Given A (m×n) and b ∈ ℝᵐ, the system `Ax = b` may be **inconsistent** (typically when m > n — more equations than unknowns, an *overdetermined* system).

> **Definition.** A **least squares solution** of `Ax = b` is a vector x̂ ∈ ℝⁿ such that
> **‖b − Ax̂‖ ≤ ‖b − Ax‖ for all x ∈ ℝⁿ.**

The vector **r = b − Ax̂** is the **residual**; ‖r‖ is the **least squares error**.

### 6.2.2 Derivation of the Normal Equations

Since Ax ranges over exactly Col(A) as x ranges over ℝⁿ, minimizing ‖b − Ax‖ means finding the point of Col(A) closest to b. By the Best Approximation Theorem (Thm 5.5), that point is

> b̂ = proj_{Col A}(b)

and `Ax̂ = b̂` is consistent. The residual b − b̂ lies in (Col A)⊥ = Nul(Aᵀ), so

Aᵀ(b − Ax̂) = 0 ⟹ **AᵀAx̂ = Aᵀb**

> **Theorem 6.1.** The set of least squares solutions of `Ax = b` coincides exactly with the nonempty solution set of the **normal equations** `AᵀAx = Aᵀb`.

Note the normal equations are *always consistent*, even when the original system is not.

### 6.2.3 Uniqueness

> **Theorem 6.2.** The following are equivalent:
> (a) `Ax = b` has a **unique** least squares solution for every b;
> (b) the columns of A are **linearly independent**;
> (c) **AᵀA is invertible**.
>
> In that case
> **x̂ = (AᵀA)⁻¹Aᵀb**
> and the projection is b̂ = Ax̂ = A(AᵀA)⁻¹Aᵀb = Pb, matching §5.2.5.

The matrix **A⁺ = (AᵀA)⁻¹Aᵀ** is the **Moore–Penrose pseudoinverse** for full-column-rank A. It acts like an inverse for non-square matrices: A⁺A = Iₙ, though AA⁺ = P ≠ Iₘ.

If the columns are **dependent**, there are infinitely many least squares solutions (differing by elements of Nul A), all giving the *same* projection b̂. The **minimum-norm** one is then selected by the general pseudoinverse (Chapter 13, via SVD).

### 6.2.4 Solving via QR (the numerically preferred route)

> **Theorem 6.3.** If A = QR with Q having orthonormal columns and R invertible upper triangular, then the unique least squares solution is
>
> **x̂ = R⁻¹Qᵀb**, obtained by back-substitution on `Rx̂ = Qᵀb`.

*Why:* AᵀA = RᵀQᵀQR = RᵀR, so AᵀAx = Aᵀb becomes RᵀRx = RᵀQᵀb; cancel the invertible Rᵀ.

**Why QR beats the normal equations numerically:** the condition number of AᵀA is the *square* of that of A. Forming AᵀA can destroy half your significant digits. QR avoids ever forming AᵀA.

### 6.2.5 Linear Models

The general setup: given data points (x₁, y₁), ..., (x_m, y_m), fit a model

> y = β₀f₀(x) + β₁f₁(x) + ... + β_kf_k(x)

The model is called **linear** because it is linear **in the parameters β**, not necessarily in x. Fitting a parabola is still a linear model.

**Design matrix X, observation vector y, parameter vector β, residual ε:**

> **y = Xβ + ε**, solved by **XᵀXβ̂ = Xᵀy**

**(a) Least squares line** y = β₀ + β₁x:

```
X = [[1, x₁],      y = [y₁,
     [1, x₂],           y₂,
      ⋮   ⋮             ⋮
     [1, x_m]]          y_m]
```

Explicit formulas from the normal equations:

> **β₁ = (m·Σxy − Σx·Σy) / (m·Σx² − (Σx)²)**
> **β₀ = (Σy − β₁Σx)/m = ȳ − β₁x̄**

**(b) Polynomial fit** y = β₀ + β₁x + β₂x²: columns of X are 1, x, x².

**(c) Multiple regression** y = β₀ + β₁u + β₂v: columns 1, u, v.

**(d) Linearizable nonlinear models:**
- y = Ce^{kx} → take logs: ln y = ln C + kx (linear in ln C and k)
- y = Cx^k → log–log: ln y = ln C + k ln x
- y = 1/(a + bx) → 1/y = a + bx

*Caution:* transforming changes which errors get minimized. Minimizing squared error in ln y is not the same as in y. Good enough for exams; be aware in practice.

### 6.2.6 Goodness of Fit

- **SSE** (residual sum of squares) = ‖y − Xβ̂‖² = Σ(yᵢ − ŷᵢ)²
- **SST** (total) = Σ(yᵢ − ȳ)²
- **SSR** (regression) = Σ(ŷᵢ − ȳ)²
- **SST = SSR + SSE** (a Pythagorean identity — the decomposition is orthogonal!)
- **Coefficient of determination:** R² = SSR/SST = 1 − SSE/SST, with 0 ≤ R² ≤ 1.

R² = 1 means a perfect fit; R² = 0 means the model does no better than the mean.

---

## 6.3 Solved Examples

### Example 6.1 — [Easy] Small inconsistent system

Find the least squares solution of `Ax = b` where A = [[1, 1], [1, 2], [1, 3]] and b = (1, 2, 4)ᵀ. Also find the residual and the error.

**Solution.**

**AᵀA** = [[3, 6], [6, 14]] (computed in Example 5.7).
**Aᵀb** = [[1,1,1],[1,2,3]]·(1,2,4)ᵀ = (1+2+4, 1+4+12) = (7, 17)ᵀ.

Normal equations:
```
3β₀ + 6β₁ = 7
6β₀ + 14β₁ = 17
```
Multiply the first by 2: 6β₀ + 12β₁ = 14. Subtract from the second: 2β₁ = 3 → **β₁ = 3/2**.
Then 3β₀ = 7 − 9 = −2 → **β₀ = −2/3**.

**x̂ = (−2/3, 3/2)ᵀ.**

**Fitted values** Ax̂: (−2/3 + 3/2, −2/3 + 3, −2/3 + 9/2) = (5/6, 7/3, 23/6).
*(This matches Example 5.7's projection of (1,2,4) — as it must.)*

**Residual** r = b − Ax̂ = (1 − 5/6, 2 − 7/3, 4 − 23/6) = (1/6, −1/3, 1/6).

**Error** ‖r‖ = √(1/36 + 4/36 + 1/36) = √(6/36) = **1/√6 ≈ 0.408**

---

### Example 6.2 — [Easy] Least squares line by formula

Fit a least squares line to the data (1, 1), (2, 2), (3, 2), (4, 3).

**Solution.** m = 4.
- Σx = 1+2+3+4 = 10, x̄ = 2.5
- Σy = 1+2+2+3 = 8, ȳ = 2
- Σxy = 1 + 4 + 6 + 12 = 23
- Σx² = 1 + 4 + 9 + 16 = 30

β₁ = (4(23) − 10(8))/(4(30) − 100) = (92 − 80)/(120 − 100) = 12/20 = **0.6**
β₀ = 2 − 0.6(2.5) = 2 − 1.5 = **0.5**

**Answer: y = 0.5 + 0.6x**

**Fitted values:** 1.1, 1.7, 2.3, 2.9. **Residuals:** −0.1, 0.3, −0.3, 0.1.
*(Residuals sum to 0 — always true when the model includes an intercept.)*
**SSE** = 0.01 + 0.09 + 0.09 + 0.01 = **0.20**
**SST** = 1 + 0 + 0 + 1 = 2. **R² = 1 − 0.2/2 = 0.90.**

---

### Example 6.3 — [Medium] Quadratic fit

Fit y = β₀ + β₁x + β₂x² to (−1, 2), (0, 1), (1, 2), (2, 5).

**Solution.** Design matrix and observations:
```
X = [[1, −1, 1],       y = [2,
     [1,  0, 0],            1,
     [1,  1, 1],            2,
     [1,  2, 4]]            5]
```

**XᵀX:** Let's compute the needed sums: Σ1 = 4, Σx = 2, Σx² = 6, Σx³ = 8, Σx⁴ = 18.
```
XᵀX = [[4, 2, 6],
       [2, 6, 8],
       [6, 8, 18]]
```
**Xᵀy:** Σy = 10, Σxy = −2 + 0 + 2 + 10 = 10, Σx²y = 2 + 0 + 2 + 20 = 24.
```
Xᵀy = (10, 10, 24)ᵀ
```

Solve:
```
4β₀ + 2β₁ + 6β₂ = 10
2β₀ + 6β₁ + 8β₂ = 10
6β₀ + 8β₁ + 18β₂ = 24
```
Simplify: divide eq1 by 2 → 2β₀ + β₁ + 3β₂ = 5. Divide eq2 by 2 → β₀ + 3β₁ + 4β₂ = 5. Divide eq3 by 2 → 3β₀ + 4β₁ + 9β₂ = 12.

From (i) 2β₀ + β₁ + 3β₂ = 5 and (ii) β₀ + 3β₁ + 4β₂ = 5:
(i) − 2(ii): 2β₀ + β₁ + 3β₂ − 2β₀ − 6β₁ − 8β₂ = 5 − 10 → −5β₁ − 5β₂ = −5 → **β₁ + β₂ = 1**.

From (iii) 3β₀ + 4β₁ + 9β₂ = 12 and (ii)×3: 3β₀ + 9β₁ + 12β₂ = 15.
Subtract: −5β₁ − 3β₂ = −3 → **5β₁ + 3β₂ = 3**.

From β₁ = 1 − β₂: 5(1 − β₂) + 3β₂ = 3 → 5 − 2β₂ = 3 → **β₂ = 1**, **β₁ = 0**.
From (ii): β₀ + 0 + 4 = 5 → **β₀ = 1**.

**Answer: y = 1 + x²**

**Check the data:** x=−1 → 2 ✓; x=0 → 1 ✓; x=1 → 2 ✓; x=2 → 5 ✓.
All four points lie exactly on the curve — the "least squares" fit is exact here, SSE = 0, R² = 1. (Four points, three parameters, and it still fit perfectly — that means the data really were quadratic.)

---

### Example 6.4 — [Medium] Least squares via QR

Solve the least squares problem for A = [[1, 0], [1, 1], [1, 2]], b = (6, 0, 0)ᵀ using QR.

**Solution.** From Example 5.6:
```
Q = [[1/√3, −1/√2],      R = [[√3, √3],
     [1/√3,   0  ],           [0,  √2]]
     [1/√3,  1/√2]]
```

**Qᵀb:**
- q₁·b = (6 + 0 + 0)/√3 = 6/√3 = 2√3
- q₂·b = (−6 + 0 + 0)/√2 = −6/√2 = −3√2

Solve `Rx̂ = Qᵀb` by back-substitution:
- √2·x₂ = −3√2 → **x₂ = −3**
- √3·x₁ + √3(−3) = 2√3 → x₁ − 3 = 2 → **x₁ = 5**

**x̂ = (5, −3)ᵀ.**

**Verify via normal equations:** AᵀA = [[3, 3], [3, 5]], Aᵀb = (6, 0)ᵀ.
3x₁ + 3x₂ = 6 and 3x₁ + 5x₂ = 0. Subtracting: 2x₂ = −6 → x₂ = −3, x₁ = 5 ✓

**Residual:** Ax̂ = (5, 2, −1); r = (1, −2, 1); ‖r‖ = √6.

---

### Example 6.5 — [Hard] Multiple regression

Fit z = β₀ + β₁x + β₂y to the data:
(x, y, z) = (0, 0, 1), (1, 0, 2), (0, 1, 4), (1, 1, 6).

**Solution.**
```
X = [[1, 0, 0],       z = [1,
     [1, 1, 0],            2,
     [1, 0, 1],            4,
     [1, 1, 1]]            6]
```
Sums: Σ1 = 4, Σx = 2, Σy = 2, Σx² = 2, Σy² = 2, Σxy = 1.
```
XᵀX = [[4, 2, 2],
       [2, 2, 1],
       [2, 1, 2]]
```
Xᵀz: Σz = 13; Σxz = 0 + 2 + 0 + 6 = 8; Σyz = 0 + 0 + 4 + 6 = 10.
```
Xᵀz = (13, 8, 10)ᵀ
```
Solve:
```
4β₀ + 2β₁ + 2β₂ = 13   ... (i)
2β₀ + 2β₁ +  β₂ =  8   ... (ii)
2β₀ +  β₁ + 2β₂ = 10   ... (iii)
```
(i) − (ii)×2: 4β₀ + 2β₁ + 2β₂ − 4β₀ − 4β₁ − 2β₂ = 13 − 16 → −2β₁ = −3 → **β₁ = 3/2**.
(i) − (iii)×2: 4β₀ + 2β₁ + 2β₂ − 4β₀ − 2β₁ − 4β₂ = 13 − 20 → −2β₂ = −7 → **β₂ = 7/2**.
From (ii): 2β₀ + 3 + 7/2 = 8 → 2β₀ = 8 − 13/2 = 3/2 → **β₀ = 3/4**.

**Answer: z = 0.75 + 1.5x + 3.5y**

**Fitted:** 0.75, 2.25, 4.25, 5.75. **Residuals:** 0.25, −0.25, −0.25, 0.25. SSE = 4(0.0625) = **0.25**.
*(Residuals sum to zero ✓, and are orthogonal to the x and y columns: 0(0.25) + 1(−0.25) + 0(−0.25) + 1(0.25) = 0 ✓)*

---

### Example 6.6 — [Hard] Linearizing an exponential model

Fit y = Ce^{kt} to the data (0, 3.0), (1, 5.0), (2, 8.1), (3, 13.5).

**Solution.** Take natural logs: ln y = ln C + kt. Let Y = ln y, β₀ = ln C, β₁ = k.

| t | y | Y = ln y |
|---|---|---|
| 0 | 3.0 | 1.0986 |
| 1 | 5.0 | 1.6094 |
| 2 | 8.1 | 2.0919 |
| 3 | 13.5 | 2.6027 |

m = 4, Σt = 6, ΣY = 7.4026, Σt² = 14, ΣtY = 0 + 1.6094 + 4.1838 + 7.8081 = 13.6013.

β₁ = (4(13.6013) − 6(7.4026))/(4(14) − 36) = (54.4052 − 44.4156)/20 = 9.9896/20 = **0.4995**
β₀ = (7.4026 − 0.4995(6))/4 = (7.4026 − 2.9970)/4 = 4.4056/4 = **1.1014**

C = e^{1.1014} = **3.008**, k = **0.4995 ≈ 0.5**

**Answer: y ≈ 3.01 e^{0.50t}**

**Check:** at t = 3, 3.01e^{1.5} = 3.01(4.4817) = 13.49 ✓ (data value 13.5).
*Note that e^{0.5} ≈ 1.6487, so the data are essentially multiplying by 1.65 each step: 3.0 → 4.95 → 8.16 → 13.46 ✓*

---

### Example 6.7 — [Very Hard] Weighted least squares and its geometry

Suppose measurement i has known standard deviation σᵢ, so more precise measurements should count for more. The **weighted least squares** problem minimizes

> Σᵢ wᵢ(bᵢ − (Ax)ᵢ)² with wᵢ = 1/σᵢ²

Derive the weighted normal equations, and solve for A = [[1],[1],[1]], b = (10, 12, 20)ᵀ with weights w = (4, 4, 1).

**Solution.**

**Derivation.** Let W = diag(w₁, ..., w_m) and D = W^{1/2} = diag(√w₁, ..., √w_m). Then

Σwᵢrᵢ² = rᵀWr = (Dr)ᵀ(Dr) = ‖Dr‖² = ‖D(b − Ax)‖² = ‖Db − (DA)x‖²

This is an *ordinary* least squares problem with matrix DA and vector Db. Its normal equations are

(DA)ᵀ(DA)x̂ = (DA)ᵀ(Db)
AᵀDᵀDAx̂ = AᵀDᵀDb

Since DᵀD = W:

> **AᵀWAx̂ = AᵀWb** (the weighted normal equations)

**Solution of the instance.** A = column of three 1s means we're estimating a single common value μ.
- AᵀWA = Σwᵢ = 4 + 4 + 1 = 9
- AᵀWb = Σwᵢbᵢ = 4(10) + 4(12) + 1(20) = 40 + 48 + 20 = 108

μ̂ = 108/9 = **12**

**Compare with unweighted:** the plain mean is (10 + 12 + 20)/3 = 14.

The weighted estimate 12 is pulled away from the imprecise third measurement (20, weight 1) toward the two precise ones. **This is exactly the correct statistical behaviour** — the weighted mean is the maximum-likelihood estimate under Gaussian noise with known variances.

**General fact:** for A = column of ones, the weighted least squares estimate is the **weighted mean** Σwᵢbᵢ/Σwᵢ.

---

### Example 6.8 — [Very Hard] Rank-deficient least squares

Find all least squares solutions of `Ax = b` for
A = [[1, 1, 0], [1, 1, 0], [1, 1, 1], [1, 1, 1]], b = (1, 3, 8, 2)ᵀ.
Identify the minimum-norm solution.

**Solution.** Columns 1 and 2 of A are **identical** — dependent. So AᵀA is singular and there will be infinitely many least squares solutions.

**AᵀA:**
- Row 1: (a₁·a₁, a₁·a₂, a₁·a₃) = (4, 4, 2)
- Row 2: (4, 4, 2)
- Row 3: (2, 2, 2)
```
AᵀA = [[4, 4, 2],
       [4, 4, 2],
       [2, 2, 2]]
```
**Aᵀb:** a₁·b = 1+3+8+2 = 14; a₂·b = 14; a₃·b = 8 + 2 = 10.
```
Aᵀb = (14, 14, 10)ᵀ
```
Normal equations:
```
4x₁ + 4x₂ + 2x₃ = 14
4x₁ + 4x₂ + 2x₃ = 14   (duplicate)
2x₁ + 2x₂ + 2x₃ = 10
```
Reduce: from row 3, x₁ + x₂ + x₃ = 5. From row 1 (÷2), 2x₁ + 2x₂ + x₃ = 7.
Subtracting twice row 3 from row 1: (2x₁+2x₂+x₃) − 2(x₁+x₂+x₃) = 7 − 10 → −x₃ = −3 → **x₃ = 3**.
Then x₁ + x₂ = 2.

**All least squares solutions:** x̂ = (t, 2 − t, 3) for any t ∈ ℝ.
Equivalently x̂ = (0, 2, 3) + t(1, −1, 0), where (1, −1, 0) spans Nul(A) ✓

**All give the same projection:** Ax̂ = (t + 2 − t, same, t + 2 − t + 3, same) = (2, 2, 5, 5). ✓ independent of t.

**Residual:** b − Ax̂ = (−1, 1, 3, −3), ‖r‖ = √20 = 2√5.

**Minimum-norm solution.** Minimize ‖x̂‖² = t² + (2−t)² + 9 over t.
d/dt: 2t − 2(2 − t) = 4t − 4 = 0 → **t = 1**.

**Minimum-norm least squares solution: x̂ = (1, 1, 3)ᵀ**, with ‖x̂‖ = √11.

*Geometric check:* the minimum-norm solution must be orthogonal to Nul(A) = span{(1,−1,0)}. Indeed (1,1,3)·(1,−1,0) = 1 − 1 = 0 ✓ This is exactly what the SVD-based pseudoinverse A⁺b returns.

---

## 6.4 Practice Numericals — Chapter 6

**[Easy]**

**P6.1** Find the least squares solution of A = [[1, 0], [0, 1], [1, 1]], b = (1, 1, 0)ᵀ.

**P6.2** Fit a least squares line to (0, 1), (1, 3), (2, 4), (3, 6).

**P6.3** Given AᵀA = [[5, 10], [10, 30]] and Aᵀb = (20, 50)ᵀ, solve the normal equations.

**P6.4** For the line y = 2 + 3x fitted to points (1, 6), (2, 7), compute the residuals and SSE.

**P6.5** Explain in one or two sentences why the normal equations are always consistent even when `Ax = b` is not.

**[Medium]**

**P6.6** Fit a least squares line to (2, 3), (3, 2), (5, 1), (6, 0) and compute R².

**P6.7** Find the least squares solution of A = [[1, 1], [1, 2], [1, 3], [1, 4]], b = (2, 3, 5, 6)ᵀ, and the least squares error.

**P6.8** Fit y = β₀ + β₁x + β₂x² to (0, 0), (1, 1), (2, 4), (3, 8).

**P6.9** Fit a model of the form y = Cx^k to (1, 2), (2, 5.6), (3, 10.4), (4, 16) by log–log regression.

**P6.10** Given data with Σx = 20, Σy = 35, Σxy = 120, Σx² = 90, m = 5, find the least squares line.

**P6.11** For A with orthonormal columns (AᵀA = I), show the least squares solution reduces to x̂ = Aᵀb and the projection to AAᵀb.

**[Hard]**

**P6.12** Solve the least squares problem for A = [[1, 1, 0], [1, 0, 1], [0, 1, 1], [1, 1, 1]], b = (1, 2, 3, 4)ᵀ. Report x̂, the residual, and the error.

**P6.13** Use the QR factorization from Chapter 5 P5.12 to solve the least squares problem with A = [[1,1,1],[1,1,0],[1,0,0]] and b = (3, 2, 1)ᵀ.

**P6.14** The following data record a spring's extension x (cm) under load F (N): (2, 5), (4, 11), (6, 14), (8, 21), (10, 24). Fit F = kx (no intercept — Hooke's law) by least squares and find k. Then fit F = a + kx and compare SSE.

**P6.15** Prove that if x̂ is a least squares solution of `Ax = b`, then the residual r = b − Ax̂ satisfies Aᵀr = 0, and hence the residual is orthogonal to Col(A). Interpret geometrically.

**P6.16** Weighted least squares: fit a line to (1, 2), (2, 3), (3, 10) with weights 3, 3, 1. Compare to the unweighted fit and explain the difference.

**[Very Hard]**

**P6.17** Let A be m×n with rank r < n. Show the least squares solution set is x̂₀ + Nul(A) for any particular solution x̂₀, and that the minimum-norm element is the unique one lying in Row(A).

**P6.18** Derive the closed-form least squares line formulas β₁ = S_xy/S_xx and β₀ = ȳ − β₁x̄ directly from the normal equations, where S_xy = Σ(xᵢ−x̄)(yᵢ−ȳ) and S_xx = Σ(xᵢ−x̄)².

**P6.19** Prove the ANOVA decomposition SST = SSR + SSE for a model containing an intercept, and explain why it is a statement of the Pythagorean theorem.

**P6.20** **(Ridge regression.)** Show that minimizing ‖b − Ax‖² + λ‖x‖² (λ > 0) leads to the normal equations (AᵀA + λI)x̂ = Aᵀb, that AᵀA + λI is always invertible for λ > 0 even when A is rank-deficient, and compute x̂ for the rank-deficient A of Example 6.8 with λ = 1.

---

## 6.5 Solutions to Chapter 6 Practice

**S6.1** AᵀA = [[1+0+1, 0+0+1],[0+0+1, 0+1+1]] = [[2, 1],[1, 2]]. Aᵀb = (1+0+0, 0+1+0) = (1, 1)ᵀ.
2x₁ + x₂ = 1, x₁ + 2x₂ = 1. By symmetry x₁ = x₂ = 1/3.
**x̂ = (1/3, 1/3)ᵀ.** Residual: Ax̂ = (1/3, 1/3, 2/3); r = (2/3, 2/3, −2/3); ‖r‖ = 2/√3.

**S6.2** m = 4, Σx = 6, Σy = 14, Σxy = 0 + 3 + 8 + 18 = 29, Σx² = 0+1+4+9 = 14.
β₁ = (4(29) − 6(14))/(4(14) − 36) = (116 − 84)/20 = 32/20 = **1.6**
β₀ = (14 − 1.6(6))/4 = (14 − 9.6)/4 = **1.1**
**y = 1.1 + 1.6x**

**S6.3** 5x₁ + 10x₂ = 20 → x₁ + 2x₂ = 4. 10x₁ + 30x₂ = 50 → x₁ + 3x₂ = 5.
Subtracting: x₂ = 1, x₁ = 2. **x̂ = (2, 1)ᵀ.**

**S6.4** Predicted: at x=1, 5; at x=2, 8. Residuals: 6−5 = **1**, 7−8 = **−1**. **SSE = 1 + 1 = 2.**

**S6.5** `Ax = b` is inconsistent when b ∉ Col(A). The normal equations instead ask for Ax = proj_{Col A}(b), and the projection **always lies in Col(A)** by construction, so that system always has a solution. Equivalently, Aᵀb ∈ Col(AᵀA) always holds because Col(AᵀA) = Col(Aᵀ) = Row(A).

**S6.6** m = 4, Σx = 16, Σy = 6, Σxy = 6 + 6 + 5 + 0 = 17, Σx² = 4 + 9 + 25 + 36 = 74.
β₁ = (4(17) − 16(6))/(4(74) − 256) = (68 − 96)/(296 − 256) = −28/40 = **−0.7**
β₀ = (6 − (−0.7)(16))/4 = (6 + 11.2)/4 = **4.3**
**y = 4.3 − 0.7x**
Fitted: 2.9, 2.2, 0.8, 0.1. Residuals: 0.1, −0.2, 0.2, −0.1. SSE = 0.01+0.04+0.04+0.01 = **0.10**.
ȳ = 1.5. SST = (1.5)² + (0.5)² + (0.5)² + (1.5)² = 2.25+0.25+0.25+2.25 = 5.
**R² = 1 − 0.1/5 = 0.98.**

**S6.7** Σx = 10, Σy = 16, Σxy = 2 + 6 + 15 + 24 = 47, Σx² = 30, m = 4.
β₁ = (4(47) − 10(16))/(120 − 100) = (188 − 160)/20 = 28/20 = **1.4**
β₀ = (16 − 14)/4 = **0.5**
**x̂ = (0.5, 1.4)ᵀ**, i.e. y = 0.5 + 1.4x.
Fitted: 1.9, 3.3, 4.7, 6.1. Residuals: 0.1, −0.3, 0.3, −0.1. **Error ‖r‖ = √0.20 ≈ 0.447.**

**S6.8** Sums: Σ1 = 4, Σx = 6, Σx² = 14, Σx³ = 36, Σx⁴ = 98.
Σy = 13, Σxy = 0 + 1 + 8 + 24 = 33, Σx²y = 0 + 1 + 16 + 72 = 89.
```
[[4,  6,  14],   [β₀]   [13]
 [6, 14,  36], · [β₁] = [33]
 [14,36,  98]]   [β₂]   [89]
```
From eq1: 4β₀ + 6β₁ + 14β₂ = 13.
eq2 − 1.5×eq1: 6β₀ + 14β₁ + 36β₂ − 6β₀ − 9β₁ − 21β₂ = 33 − 19.5 → 5β₁ + 15β₂ = 13.5
eq3 − 3.5×eq1: 14β₀ + 36β₁ + 98β₂ − 14β₀ − 21β₁ − 49β₂ = 89 − 45.5 → 15β₁ + 49β₂ = 43.5
From the first of these: β₁ = (13.5 − 15β₂)/5 = 2.7 − 3β₂.
Substituting: 15(2.7 − 3β₂) + 49β₂ = 43.5 → 40.5 − 45β₂ + 49β₂ = 43.5 → 4β₂ = 3 → **β₂ = 0.75**
β₁ = 2.7 − 2.25 = **0.45**
4β₀ = 13 − 6(0.45) − 14(0.75) = 13 − 2.7 − 10.5 = −0.2 → **β₀ = −0.05**
**y = −0.05 + 0.45x + 0.75x²**
*Check at x=3: −0.05 + 1.35 + 6.75 = 8.05 ≈ 8 ✓*

**S6.9** Take logs. X = ln x, Y = ln y.

| x | y | X = ln x | Y = ln y |
|---|---|---|---|
| 1 | 2 | 0 | 0.6931 |
| 2 | 5.6 | 0.6931 | 1.7228 |
| 3 | 10.4 | 1.0986 | 2.3418 |
| 4 | 16 | 1.3863 | 2.7726 |

ΣX = 3.1780, ΣY = 7.5303, ΣX² = 0 + 0.4804 + 1.2069 + 1.9218 = 3.6091
ΣXY = 0 + 1.1940 + 2.5728 + 3.8438 = 7.6106

k = (4(7.6106) − 3.1780(7.5303))/(4(3.6091) − 3.1780²) = (30.4424 − 23.9313)/(14.4364 − 10.0997) = 6.5111/4.3367 = **1.5014**
ln C = (7.5303 − 1.5014(3.1780))/4 = (7.5303 − 4.7715)/4 = 0.6897 → C = **1.993**

**Answer: y ≈ 2x^{1.5}** (essentially exact: 2(4^1.5) = 2(8) = 16 ✓, 2(2^1.5) = 5.657 ≈ 5.6 ✓)

**S6.10** β₁ = (5(120) − 20(35))/(5(90) − 400) = (600 − 700)/(450 − 400) = −100/50 = **−2**
β₀ = (35 − (−2)(20))/5 = 75/5 = **15**
**y = 15 − 2x**

**S6.11** With AᵀA = I, the normal equations AᵀAx̂ = Aᵀb become **Ix̂ = Aᵀb**, so **x̂ = Aᵀb** — no system to solve, just a matrix-vector product.
Projection: b̂ = Ax̂ = **AAᵀb** ✓ matching §5.2.5 with U = A.
*This is why orthonormalizing (QR) before solving is so attractive.*

**S6.12**
**AᵀA:** columns a₁ = (1,1,0,1), a₂ = (1,0,1,1), a₃ = (0,1,1,1).
- a₁·a₁ = 3, a₁·a₂ = 1+0+0+1 = 2, a₁·a₃ = 0+1+0+1 = 2
- a₂·a₂ = 3, a₂·a₃ = 0+0+1+1 = 2
- a₃·a₃ = 3
```
AᵀA = [[3, 2, 2],
       [2, 3, 2],
       [2, 2, 3]]
```
**Aᵀb** with b = (1,2,3,4):
- a₁·b = 1 + 2 + 0 + 4 = 7
- a₂·b = 1 + 0 + 3 + 4 = 8
- a₃·b = 0 + 2 + 3 + 4 = 9
```
Aᵀb = (7, 8, 9)ᵀ
```
Solve. Subtract eq1 from eq2: x₁ + ... let's do it: (2x₁+3x₂+2x₃) − (3x₁+2x₂+2x₃) = 8 − 7 → −x₁ + x₂ = 1.
(2x₁+2x₂+3x₃) − (3x₁+2x₂+2x₃) = 9 − 7 → −x₁ + x₃ = 2.
So x₂ = x₁ + 1, x₃ = x₁ + 2. Substitute into eq1:
3x₁ + 2(x₁+1) + 2(x₁+2) = 7 → 7x₁ + 6 = 7 → **x₁ = 1/7**.
x₂ = 8/7, x₃ = 15/7.
**x̂ = (1/7, 8/7, 15/7)ᵀ.**

**Ax̂:** row1 = x₁+x₂ = 9/7; row2 = x₁+x₃ = 16/7; row3 = x₂+x₃ = 23/7; row4 = x₁+x₂+x₃ = 24/7.
**Residual** r = (1 − 9/7, 2 − 16/7, 3 − 23/7, 4 − 24/7) = (−2/7, −2/7, −2/7, 4/7).
**Error** ‖r‖ = (1/7)√(4+4+4+16) = √28/7 = 2√7/7 = **2/√7 ≈ 0.756**
*Check Aᵀr = 0: a₁·r = (−2−2+0+4)/7 = 0 ✓*

**S6.13** From P5.12:
```
Q = [[1/√3,  1/√6,  1/√2],      R = [[√3, 2/√3, 1/√3],
     [1/√3,  1/√6, −1/√2],           [0,  2/√6, 1/√6],
     [1/√3, −2/√6,   0  ]]           [0,  0,    1/√2]]
```
b = (3, 2, 1)ᵀ. **Qᵀb:**
- q₁·b = (3+2+1)/√3 = 6/√3 = 2√3
- q₂·b = (3 + 2 − 2)/√6 = 3/√6
- q₃·b = (3 − 2 + 0)/√2 = 1/√2

Back-substitute `Rx̂ = Qᵀb`:
- (1/√2)x₃ = 1/√2 → **x₃ = 1**
- (2/√6)x₂ + (1/√6)(1) = 3/√6 → 2x₂ + 1 = 3 → **x₂ = 1**
- √3x₁ + (2/√3)(1) + (1/√3)(1) = 2√3 → multiply by √3: 3x₁ + 2 + 1 = 6 → **x₁ = 1**

**x̂ = (1, 1, 1)ᵀ.** Since A is square and invertible here, Ax̂ = (3, 2, 1) = b exactly — the residual is zero.

**S6.14**
**Model F = kx (no intercept).** A = (2,4,6,8,10)ᵀ, b = (5,11,14,21,24)ᵀ.
AᵀA = 4 + 16 + 36 + 64 + 100 = 220.
Aᵀb = 10 + 44 + 84 + 168 + 240 = 546.
**k = 546/220 = 2.4818**
Fitted: 4.964, 9.927, 14.891, 19.855, 24.818. Residuals: 0.036, 1.073, −0.891, 1.145, −0.818.
**SSE₁** = 0.0013 + 1.1513 + 0.7939 + 1.3110 + 0.6691 = **3.927**

**Model F = a + kx.** m = 5, Σx = 30, Σb = 75, Σxb = 546, Σx² = 220.
k = (5(546) − 30(75))/(5(220) − 900) = (2730 − 2250)/(1100 − 900) = 480/200 = **2.4**
a = (75 − 2.4(30))/5 = (75 − 72)/5 = **0.6**
Fitted: 5.4, 10.2, 15.0, 19.8, 24.6. Residuals: −0.4, 0.8, −1.0, 1.2, −0.6.
**SSE₂** = 0.16 + 0.64 + 1.00 + 1.44 + 0.36 = **3.60**

**Comparison:** SSE₂ = 3.60 < SSE₁ = 3.93. The two-parameter model fits better, as it must (adding a parameter can never increase SSE). But the intercept a = 0.6 N is small and physically ought to be zero for an ideal spring — the improvement is marginal and likely just absorbing noise. **Physics favours the one-parameter model; k ≈ 2.48 N/cm.**

**S6.15** By definition x̂ minimizes ‖b − Ax‖, so Ax̂ = proj_{Col A}(b) (Best Approximation Theorem). Hence r = b − Ax̂ = b − proj_{Col A}(b) is the component of b orthogonal to Col(A), i.e. **r ∈ (Col A)⊥ = Nul(Aᵀ)**, so **Aᵀr = 0** ✓

Since Aᵀr = 0 means every column of A dotted with r is zero, r ⊥ Col(A). ∎

**Geometric interpretation:** the shortest path from a point to a plane is along the perpendicular. The residual is that perpendicular; it "sticks out" of the reachable space in a direction no choice of x can touch. That is why it is irreducible error.

**S6.16** Weights w = (3, 3, 1); W = diag(3,3,1). X = [[1,1],[1,2],[1,3]], y = (2, 3, 10)ᵀ.

**XᵀWX:**
- (1,1) entry: Σwᵢ = 7
- (1,2) = (2,1): Σwᵢxᵢ = 3(1) + 3(2) + 1(3) = 12
- (2,2): Σwᵢxᵢ² = 3(1) + 3(4) + 1(9) = 24
```
XᵀWX = [[7, 12], [12, 24]]
```
**XᵀWy:**
- Σwᵢyᵢ = 6 + 9 + 10 = 25
- Σwᵢxᵢyᵢ = 3(1)(2) + 3(2)(3) + 1(3)(10) = 6 + 18 + 30 = 54
```
XᵀWy = (25, 54)ᵀ
```
Solve: 7β₀ + 12β₁ = 25; 12β₀ + 24β₁ = 54 → β₀ + 2β₁ = 4.5.
From the second: β₀ = 4.5 − 2β₁. Substituting: 7(4.5 − 2β₁) + 12β₁ = 25 → 31.5 − 2β₁ = 25 → β₁ = 3.25, β₀ = 4.5 − 6.5 = −2.
**Weighted fit: y = −2 + 3.25x**

**Unweighted:** Σx = 6, Σy = 15, Σxy = 2 + 6 + 30 = 38, Σx² = 14, m = 3.
β₁ = (3(38) − 6(15))/(3(14) − 36) = (114 − 90)/6 = **4**
β₀ = (15 − 24)/3 = **−3**
**Unweighted fit: y = −3 + 4x**

**Explanation.** The third point (3, 10) is far above the trend of the first two. With weight 1 versus 3, it pulls the line less than in the unweighted fit, giving a gentler slope (3.25 vs 4). Down-weighting is how one handles a measurement known to be less reliable — or a suspected outlier.

**S6.17**
**Solution set structure.** x̂ is a least squares solution ⟺ AᵀAx̂ = Aᵀb. If x̂₀ is one solution and x̂ another, then AᵀA(x̂ − x̂₀) = 0, so x̂ − x̂₀ ∈ Nul(AᵀA) = Nul(A) (these are equal: Ax = 0 ⟹ AᵀAx = 0; and AᵀAx = 0 ⟹ xᵀAᵀAx = ‖Ax‖² = 0 ⟹ Ax = 0). Hence the set is **x̂₀ + Nul(A)** ✓

**Minimum norm.** Decompose ℝⁿ = Row(A) ⊕ Nul(A) (orthogonal complements, Thm 5.1). Write x̂₀ = p + h with p ∈ Row(A), h ∈ Nul(A). Then every solution is p + h' for h' ∈ Nul(A), and by Pythagoras

‖p + h'‖² = ‖p‖² + ‖h'‖² ≥ ‖p‖²

with equality only when h' = 0. So the **unique minimum-norm solution is p ∈ Row(A)** ✓ ∎

**S6.18** Normal equations for X = [1 | x]:
```
mβ₀ + (Σx)β₁ = Σy       ... (i)
(Σx)β₀ + (Σx²)β₁ = Σxy  ... (ii)
```
From (i): **β₀ = ȳ − β₁x̄** (dividing by m) ✓

Substitute into (ii): (Σx)(ȳ − β₁x̄) + (Σx²)β₁ = Σxy.
Since Σx = mx̄ and Σy = mȳ:
mx̄ȳ − β₁mx̄² + β₁Σx² = Σxy
β₁(Σx² − mx̄²) = Σxy − mx̄ȳ

Now note the standard identities:
- Σx² − mx̄² = Σ(xᵢ − x̄)² = **S_xx**
- Σxy − mx̄ȳ = Σ(xᵢ − x̄)(yᵢ − ȳ) = **S_xy**

*(Proof of the second: Σ(xᵢ−x̄)(yᵢ−ȳ) = Σxᵢyᵢ − x̄Σyᵢ − ȳΣxᵢ + mx̄ȳ = Σxy − mx̄ȳ − mx̄ȳ + mx̄ȳ = Σxy − mx̄ȳ ✓)*

Hence **β₁ = S_xy/S_xx** ✓ ∎

**S6.19** Let ŷ = Xβ̂ be the fitted values and r = y − ŷ the residual. Write the identity

y − ȳ1 = (ŷ − ȳ1) + (y − ŷ) = (ŷ − ȳ1) + r

**Key claim: (ŷ − ȳ1) ⊥ r.**
- r ⊥ Col(X) by S6.15.
- ŷ ∈ Col(X) by definition.
- The constant vector 1 ∈ Col(X) **because the model has an intercept** (1 is a column of X).
- Hence ŷ − ȳ1 ∈ Col(X), so it is orthogonal to r ✓

By Pythagoras:
‖y − ȳ1‖² = ‖ŷ − ȳ1‖² + ‖r‖²

i.e. **SST = SSR + SSE** ∎

**Why Pythagorean:** the data vector, measured from the mean, is split into two perpendicular pieces — the part the model explains (inside Col X) and the part it cannot (orthogonal to Col X). Squared lengths add exactly because the pieces are perpendicular. R² = SSR/SST is then the squared cosine of the angle between (y − ȳ1) and the model space.

*Note the necessity of the intercept: without a column of 1s in X, 1 ∉ Col(X), the orthogonality fails, and SST ≠ SSR + SSE. This is why R² can be negative for no-intercept models.*

**S6.20**
**Derivation.** Let f(x) = ‖b − Ax‖² + λ‖x‖² = (b−Ax)ᵀ(b−Ax) + λxᵀx.
Expand: f(x) = bᵀb − 2bᵀAx + xᵀAᵀAx + λxᵀx.
Gradient: ∇f = −2Aᵀb + 2AᵀAx + 2λx = 0
⟹ **(AᵀA + λI)x̂ = Aᵀb** ✓

**Invertibility.** For any x ≠ 0:
xᵀ(AᵀA + λI)x = ‖Ax‖² + λ‖x‖² ≥ λ‖x‖² > 0.
So AᵀA + λI is **positive definite**, hence invertible, for every λ > 0 — regardless of A's rank ✓
*(This is exactly why ridge regression is used when features are collinear.)*

**Computation for Example 6.8's A** with λ = 1:
```
AᵀA + I = [[5, 4, 2],
           [4, 5, 2],
           [2, 2, 3]]
```
Solve with Aᵀb = (14, 14, 10)ᵀ:
```
5x₁ + 4x₂ + 2x₃ = 14
4x₁ + 5x₂ + 2x₃ = 14
2x₁ + 2x₂ + 3x₃ = 10
```
Subtract eq2 from eq1: x₁ − x₂ = 0 → **x₁ = x₂**.
Substituting into eq1: 9x₁ + 2x₃ = 14. Into eq3: 4x₁ + 3x₃ = 10.
From the first: x₃ = (14 − 9x₁)/2. Substituting: 4x₁ + (42 − 27x₁)/2 = 10 → 8x₁ + 42 − 27x₁ = 20 → −19x₁ = −22 → **x₁ = 22/19**.
x₂ = 22/19, x₃ = (14 − 198/19)/2 = (266/19 − 198/19)/2 = (68/19)/2 = **34/19**.

**x̂_ridge = (22/19, 22/19, 34/19)ᵀ ≈ (1.158, 1.158, 1.789)ᵀ**

**Comparison with Example 6.8's minimum-norm solution (1, 1, 3):** ridge also breaks the tie symmetrically between the two identical columns (x₁ = x₂, as it must by symmetry), but shrinks all coefficients toward zero — ‖x̂_ridge‖ ≈ 2.36 versus ‖(1,1,3)‖ = √11 ≈ 3.32. As λ → 0⁺, the ridge solution converges to the minimum-norm least squares solution; as λ → ∞, it goes to 0.

---
# Chapter 7 — Determinants and Their Properties, Rank of a Matrix

---

## 7.1 Explain Like I'm Five

### The determinant

Think of a matrix as a machine that stretches and squishes space. The **determinant is the stretch factor for area (in 2D) or volume (in 3D)**.

Take the unit square — corners at (0,0), (1,0), (0,1), (1,1). Feed its corners through the matrix. You get a parallelogram. **The determinant is the area of that parallelogram.** If det = 3, the machine triples areas. If det = 1/2, it halves them.

**What if det = 0?** Then the square got squashed completely flat — into a line or a point. Area zero. And a flattened thing can never be un-flattened, which is exactly why **det = 0 means no inverse exists**. The determinant is a single number that answers "did this machine destroy information?"

**What about a negative determinant?** It means the machine flipped space over, like a mirror. Area is still |det|; the sign records the flip. In 2D, a negative determinant means the machine turned a counterclockwise loop into a clockwise one.

### Rank

**Rank counts genuine directions.** If you have five arrows in 3D but they all lie in one plane, you really only have two independent directions. Rank = 2. The rank tells you how "fat" the output of a matrix is — the dimension of everything the machine can produce.

Rank and determinant are two views of the same thing for square matrices: **full rank ⟺ nonzero determinant ⟺ invertible**.

---

## 7.2 The Formal Theory

### 7.2.1 Definition by Cofactor Expansion

For a 1×1 matrix, det[a] = a.

For n ≥ 2, define the **(i,j) minor** Mᵢⱼ = determinant of the (n−1)×(n−1) matrix obtained by deleting row i and column j. The **(i,j) cofactor** is

> Cᵢⱼ = (−1)^{i+j} Mᵢⱼ

> **Cofactor expansion along row i:** det A = aᵢ₁Cᵢ₁ + aᵢ₂Cᵢ₂ + ... + aᵢₙCᵢₙ
> **Cofactor expansion along column j:** det A = a₁ⱼC₁ⱼ + a₂ⱼC₂ⱼ + ... + aₙⱼCₙⱼ

**Theorem:** every row and every column expansion gives the same value.

**Sign pattern** (the checkerboard):
```
+ − + − ...
− + − + ...
+ − + − ...
```

**Strategy:** expand along the row or column with the **most zeros**. This is the single biggest time-saver.

### 7.2.2 Small Cases

**2×2:** det [[a, b], [c, d]] = **ad − bc**

**3×3 (Sarrus' rule — 3×3 ONLY):**
```
| a b c |
| d e f |  = aei + bfg + cdh − ceg − afh − bdi
| g h i |
```
Mnemonic: add the three "down-right" diagonals, subtract the three "down-left" ones. **This does not generalize to 4×4 — do not try.**

### 7.2.3 Properties of Determinants

Let A be n×n.

| # | Property |
|---|---|
| 1 | **Row replacement** (Rᵢ → Rᵢ + cRⱼ) **does not change** det A |
| 2 | **Row interchange multiplies det A by −1** |
| 3 | **Scaling a row by c multiplies det A by c** |
| 4 | If A is **triangular** (upper, lower, or diagonal), det A = product of diagonal entries |
| 5 | **det Aᵀ = det A** (so every row property holds for columns too) |
| 6 | **det(AB) = (det A)(det B)** — multiplicative |
| 7 | **det(cA) = cⁿ det A** (not c·det A!) |
| 8 | **det(A⁻¹) = 1/det A** |
| 9 | If A has a **zero row or column**, det A = 0 |
| 10 | If two rows (or columns) are **equal or proportional**, det A = 0 |
| 11 | **det(A + B) ≠ det A + det B** in general — determinants are NOT additive |
| 12 | det(Aᵏ) = (det A)ᵏ |

> **Theorem 7.1.** A is invertible ⟺ **det A ≠ 0**.

**Computing determinants efficiently:** reduce to echelon form using row operations, tracking the effect:

> det A = (−1)^{number of row swaps} × (product of pivots) ÷ (product of scaling factors used)

This is O(n³) versus O(n!) for blind cofactor expansion. For n = 20, cofactor expansion would take longer than the age of the universe.

### 7.2.4 Geometric Interpretation

> **Theorem 7.2.** If A is 2×2, the area of the parallelogram determined by the columns of A is **|det A|**. If A is 3×3, the volume of the parallelepiped determined by the columns is **|det A|**.

> **Theorem 7.3.** Let T(x) = Ax be a linear transformation, and S a region in ℝⁿ. Then
> **vol(T(S)) = |det A| · vol(S)**

This holds for *any* measurable region, not just parallelograms — it's the change-of-variables Jacobian factor from multivariable calculus.

### 7.2.5 Cramer's Rule and the Adjugate

> **Theorem 7.4 (Cramer's Rule).** If A is invertible n×n, the unique solution of `Ax = b` has
>
> **xᵢ = det(Aᵢ(b)) / det(A)**
>
> where Aᵢ(b) is A with its i-th column replaced by b.

**The adjugate (classical adjoint):** adj A = the **transpose** of the cofactor matrix, i.e. (adj A)ᵢⱼ = Cⱼᵢ.

> **Theorem 7.5.** A·(adj A) = (adj A)·A = (det A)·I, hence
> **A⁻¹ = (1/det A) · adj A**

*Warning:* both Cramer's rule and the adjugate formula are theoretically elegant and computationally terrible (O(n!) or O(n⁴)). Use them for 2×2, 3×3, and symbolic work only.

**Useful identity:** det(adj A) = (det A)^{n−1}.

### 7.2.6 Rank

> **Definition.** rank(A) = dim Col(A) = the number of pivot positions = the number of linearly independent columns.

**Equivalent characterizations:**
1. rank(A) = number of nonzero rows in any echelon form of A
2. rank(A) = dim Row(A) (row rank = column rank)
3. rank(A) = **the size of the largest square submatrix with nonzero determinant** (the "minor" definition — common in Indian university syllabi)
4. rank(A) = number of nonzero singular values (Chapter 13)

**Properties:**
- 0 ≤ rank(A) ≤ min(m, n)
- rank(A) = rank(Aᵀ) = rank(AᵀA) = rank(AAᵀ)
- rank(A + B) ≤ rank(A) + rank(B)
- rank(AB) ≤ min(rank A, rank B)
- **Sylvester:** rank(A) + rank(B) − n ≤ rank(AB) for A (m×n), B (n×p)
- rank(PAQ) = rank(A) for invertible P, Q
- **Rank–Nullity:** rank(A) + nullity(A) = n

**Full rank terminology:**
- **Full row rank:** rank = m (rows independent; `Ax = b` always consistent)
- **Full column rank:** rank = n (columns independent; solution unique when it exists)
- **Full rank** (square): rank = n (invertible)

### 7.2.7 Normal Form / Rank Factorization

> **Theorem 7.6 (Normal form).** Every m×n matrix A of rank r is equivalent (via invertible P, Q) to
> ```
> PAQ = [[I_r, 0],
>        [0,   0]]
> ```

> **Theorem 7.7 (Rank factorization).** Every rank-r matrix factors as **A = BC** with B (m×r) of full column rank and C (r×n) of full row rank.

---

## 7.3 Solved Examples

### Example 7.1 — [Easy] 2×2 and 3×3

Compute (a) det [[3, 1], [4, 2]], (b) det [[1, 2, 3], [4, 5, 6], [7, 8, 10]].

**Solution.**
(a) 3(2) − 1(4) = 6 − 4 = **2**.

(b) By Sarrus:
= 1(5)(10) + 2(6)(7) + 3(4)(8) − 3(5)(7) − 1(6)(8) − 2(4)(10)
= 50 + 84 + 96 − 105 − 48 − 80
= 230 − 233 = **−3**

*Cross-check by cofactor expansion along row 1:*
= 1·det[[5,6],[8,10]] − 2·det[[4,6],[7,10]] + 3·det[[4,5],[7,8]]
= 1(50 − 48) − 2(40 − 42) + 3(32 − 35)
= 2 + 4 − 9 = **−3** ✓

---

### Example 7.2 — [Easy] Using zeros

Compute det of
```
A = [[3, 0, 0, 0],
     [7, 2, 0, 0],
     [1, 5, 4, 0],
     [9, 6, 8, 1]]
```

**Solution.** A is **lower triangular**. By property 4:

det A = 3 × 2 × 4 × 1 = **24**

*(No expansion needed. Always check for triangularity first.)*

---

### Example 7.3 — [Medium] Determinant by row reduction

Compute det A for A = [[2, −8, 6, 8], [3, −9, 5, 10], [−3, 0, 1, −2], [1, −4, 0, 6]].

**Solution.** Swap R₁ and R₄ to get a leading 1 (one swap → factor of −1):
```
[[ 1, −4, 0,  6],
 [ 3, −9, 5, 10],
 [−3,  0, 1, −2],
 [ 2, −8, 6,  8]]
```
`R₂ − 3R₁`, `R₃ + 3R₁`, `R₄ − 2R₁` (replacements — no change to det):
```
[[1, −4,  0,   6],
 [0,  3,  5,  −8],
 [0, −12, 1,  16],
 [0,  0,  6,  −4]]
```
`R₃ + 4R₂`:
```
[[1, −4, 0,   6],
 [0,  3, 5,  −8],
 [0,  0, 21, −16],
 [0,  0, 6,  −4]]
```
`R₄ − (6/21)R₃ = R₄ − (2/7)R₃`: new (4,4) entry = −4 − (2/7)(−16) = −4 + 32/7 = 4/7.
```
[[1, −4, 0,   6],
 [0,  3, 5,  −8],
 [0,  0, 21, −16],
 [0,  0, 0,  4/7]]
```
Product of diagonal: 1 × 3 × 21 × (4/7) = 63 × 4/7 = 36.

Account for the single swap: **det A = (−1)(36) = −36.**

---

### Example 7.4 — [Medium] Property-based reasoning

Given det A = 5 for a 4×4 matrix A, find:
(a) det(2A), (b) det(A⁻¹), (c) det(Aᵀ A), (d) det(A³), (e) det(adj A), (f) det(−A).

**Solution.**
(a) det(2A) = 2⁴ det A = 16(5) = **80**
(b) det(A⁻¹) = 1/5 = **0.2**
(c) det(AᵀA) = det(Aᵀ)det(A) = 5 × 5 = **25**
(d) det(A³) = 5³ = **125**
(e) det(adj A) = (det A)^{n−1} = 5³ = **125**
(f) det(−A) = (−1)⁴(5) = **5**

*(Part (a) and (f) are the classic traps — the scalar is raised to the power n.)*

---

### Example 7.5 — [Medium] Cramer's rule

Solve using Cramer's rule:
```
3x₁ − 2x₂ =  6
−5x₁ + 4x₂ = 8
```

**Solution.** A = [[3, −2], [−5, 4]], det A = 12 − 10 = 2 ≠ 0.

A₁(b) = [[6, −2], [8, 4]] → det = 24 + 16 = 40.
A₂(b) = [[3, 6], [−5, 8]] → det = 24 + 30 = 54.

x₁ = 40/2 = **20**, x₂ = 54/2 = **27**

**Check:** 3(20) − 2(27) = 60 − 54 = 6 ✓; −5(20) + 4(27) = −100 + 108 = 8 ✓

---

### Example 7.6 — [Hard] Determinant with a parameter, and rank

For A = [[1, 2, 3], [2, k, 6], [3, 6, 9]], find det A, determine rank(A) for each value of k, and state when A is invertible.

**Solution.** Note **row 3 = 3 × row 1**, for every k.

Therefore **det A = 0 for all k**, and A is **never invertible**.

**Rank analysis.** Reduce:
`R₂ − 2R₁`, `R₃ − 3R₁`:
```
[[1, 2,   3],
 [0, k−4, 0],
 [0, 0,   0]]
```
- If **k ≠ 4:** two pivots → **rank = 2**.
- If **k = 4:** row 2 vanishes too → **rank = 1** (all rows are multiples of (1,2,3)).

**Summary:** rank = 2 for k ≠ 4; rank = 1 for k = 4; A is singular for every k.

---

### Example 7.7 — [Hard] Vandermonde determinant

Prove that
```
| 1  a  a² |
| 1  b  b² |  = (b − a)(c − a)(c − b)
| 1  c  c² |
```

**Solution.** `R₂ → R₂ − R₁` and `R₃ → R₃ − R₁` (no change to det):
```
| 1   a        a²       |
| 0  b−a    b² − a²     |
| 0  c−a    c² − a²     |
```
Expand along column 1:
= 1 · det [[b−a, b²−a²], [c−a, c²−a²]]

Factor (b−a) from row 1 and (c−a) from row 2, using b²−a² = (b−a)(b+a):
= (b−a)(c−a) · det [[1, b+a], [1, c+a]]
= (b−a)(c−a) · [(c+a) − (b+a)]
= **(b−a)(c−a)(c−b)** ∎

**Consequence:** the Vandermonde matrix is invertible ⟺ a, b, c are **distinct**. This is why polynomial interpolation through n distinct points always has a unique solution (Example P1.14).

**General n×n Vandermonde:** det = Π_{i<j}(xⱼ − xᵢ).

---

### Example 7.8 — [Hard] Rank of a product and Sylvester's bound

Let A = [[1, 2], [2, 4], [3, 6]] and B = [[1, 1, 1], [2, 2, 2]]. Find rank A, rank B, rank(AB), and check the rank inequalities.

**Solution.**
**rank A:** column 2 = 2 × column 1 → **rank A = 1**.
**rank B:** row 2 = 2 × row 1 → **rank B = 1**.

**AB** (3×2 times 2×3 = 3×3):
Row 1 of AB: (1)(1,1,1) + (2)(2,2,2) = (5, 5, 5)
Row 2: (2)(1,1,1) + (4)(2,2,2) = (10, 10, 10)
Row 3: (3)(1,1,1) + (6)(2,2,2) = (15, 15, 15)
```
AB = [[5, 5, 5], [10, 10, 10], [15, 15, 15]]
```
All rows are multiples of (1,1,1) → **rank(AB) = 1**.

**Checks:**
- rank(AB) ≤ min(1, 1) = 1 ✓ (equality)
- Sylvester (with n = 2, the inner dimension): rank A + rank B − n = 1 + 1 − 2 = 0 ≤ 1 ✓

*Contrast:* had we chosen B = [[1, 0, 0], [0, 0, 0]] (rank 1) with the same A, AB = [[1,0,0],[2,0,0],[3,0,0]], still rank 1. Sylvester's lower bound of 0 is not tight here, but it *is* achieved when Col(B) ⊆ Nul(A).

---

### Example 7.9 — [Very Hard] Block determinant

Let M = [[A, B], [0, D]] with A (p×p) and D (q×q) square. Prove det M = (det A)(det D). Then evaluate
```
M = [[2, 1, 5, 7],
     [3, 4, 8, 9],
     [0, 0, 1, 2],
     [0, 0, 3, 4]]
```

**Solution.**

**Proof sketch.** Factor M as a product:
```
[[A, B], [0, D]] = [[A, 0], [0, I_q]] · [[I_p, A⁻¹B], [0, D]]
```
(assuming A invertible; the singular case follows by continuity or by noting both sides are 0).

The first factor is block-diagonal with determinant det A (expand repeatedly along the last rows). The second is block upper-triangular with I_p on the diagonal; expanding along the first p columns (each having a single 1) reduces it to det D.

By multiplicativity: **det M = (det A)(det D)** ∎

*Alternative proof:* perform cofactor expansion along the first column repeatedly. Because the bottom-left block is 0, the expansion never "sees" D until A is exhausted.

**Evaluation.**
A = [[2, 1], [3, 4]], det A = 8 − 3 = 5.
D = [[1, 2], [3, 4]], det D = 4 − 6 = −2.

**det M = 5 × (−2) = −10.**

**Important caution:** this formula requires a **zero block**. For a general [[A,B],[C,D]] it is **false** that det = det(A)det(D) − det(B)det(C). The correct general formula uses the Schur complement: det M = det(A)·det(D − CA⁻¹B).

---

### Example 7.10 — [Very Hard] Rank via minors, and rank factorization

Determine rank(A) using the minor definition, then write a rank factorization A = BC, for

A = [[1, 2, 3, 4], [2, 4, 6, 8], [1, 3, 5, 7]].

**Solution.**

**Step 1 — Is rank 3?** A 3×3 minor requires det of a 3×3 submatrix. But **row 2 = 2 × row 1**, so *every* 3×3 submatrix has two proportional rows → all 3×3 minors are 0. **rank ≤ 2.**

**Step 2 — Is rank 2?** Take the submatrix from rows 1, 3 and columns 1, 2:
det [[1, 2], [1, 3]] = 3 − 2 = 1 ≠ 0. **rank ≥ 2.**

**Therefore rank(A) = 2.**

**Step 3 — Rank factorization.** Reduce A:
`R₂ − 2R₁`, `R₃ − R₁`:
```
[[1, 2, 3, 4],
 [0, 0, 0, 0],
 [0, 1, 2, 3]]
```
Swap R₂ ↔ R₃, then `R₁ − 2R₂`:
```
RREF = [[1, 0, −1, −2],
        [0, 1,  2,  3],
        [0, 0,  0,  0]]
```
Pivot columns: **1 and 2**.

**B = the pivot columns of the original A:**
```
B = [[1, 2],
     [2, 4],
     [1, 3]]      (3×2, full column rank)
```
**C = the nonzero rows of the RREF:**
```
C = [[1, 0, −1, −2],
     [0, 1,  2,  3]]    (2×4, full row rank)
```

**Verify A = BC.**
Row 1 of BC: 1(1,0,−1,−2) + 2(0,1,2,3) = (1, 2, 3, 4) ✓
Row 2: 2(1,0,−1,−2) + 4(0,1,2,3) = (2, 4, 6, 8) ✓
Row 3: 1(1,0,−1,−2) + 3(0,1,2,3) = (1, 3, 5, 7) ✓

**A = BC with rank 2** ✓

*(This decomposition — pivot columns times RREF rows — is the standard constructive rank factorization, and is the discrete analogue of the SVD's rank-r truncation.)*

---

## 7.4 Practice Numericals — Chapter 7

**[Easy]**

**P7.1** Compute det [[5, 2], [3, 4]] and det [[1, 0, 2], [0, 3, 0], [4, 0, 5]].

**P7.2** For det A = 7 (3×3), find det(3A), det(A⁻¹), det(A²).

**P7.3** Compute the determinant of [[2,0,0],[5,3,0],[1,7,4]].

**P7.4** Find the rank of [[1, 2], [2, 4]].

**P7.5** Without computing, state det of a matrix with two identical rows. Why?

**[Medium]**

**P7.6** Compute det [[1, 3, 1, 5], [2, 7, 0, 4], [0, 0, 1, 0], [0, 0, 2, 1]] by expanding along a good row.

**P7.7** Find the area of the parallelogram with vertices (0,0), (3,1), (1,4), (4,5).

**P7.8** Solve by Cramer's rule: `2x + y − z = 3`, `x − y + z = 0`, `3x + 2y + z = 7`.

**P7.9** Find rank of [[1, 2, 3], [2, 4, 6], [1, 1, 1]].

**P7.10** Find all k such that [[k, 1, 1], [1, k, 1], [1, 1, k]] is singular.

**P7.11** Compute A⁻¹ using the adjugate for A = [[1, 2], [3, 5]].

**[Hard]**

**P7.12** Compute the 4×4 determinant
```
| 1  2  3  4 |
| 2  3  4  1 |
| 3  4  1  2 |
| 4  1  2  3 |
```

**P7.13** Prove that for an n×n skew-symmetric matrix with n odd, det A = 0.

**P7.14** Find rank of A = [[1, −1, 2, 3], [2, 1, 1, 4], [3, 0, 3, 7], [1, 2, −1, 1]] and a basis for Nul(A).

**P7.15** Let A be 3×3 with det A = 4. Compute det(2A⁻¹ (adj A)ᵀ).

**P7.16** Find the volume of the parallelepiped spanned by (1,0,2), (2,1,0), (0,3,1), and determine whether the three vectors form a right-handed system.

**P7.17** Evaluate the n×n determinant with a on the diagonal and b everywhere else. (Hint: add all rows to row 1.)

**[Very Hard]**

**P7.18** Prove det(AB) = det(A)det(B) for 2×2 matrices by direct expansion, then explain why the general proof uses elementary matrices instead.

**P7.19** Let A be n×n with rank(A) = r. Prove:
(a) rank(adj A) = n if r = n;
(b) rank(adj A) = 1 if r = n − 1;
(c) rank(adj A) = 0 if r < n − 1.

**P7.20** Evaluate the **circulant** determinant
```
| a  b  c |
| c  a  b |
| b  c  a |
```
and factor it completely. Relate the factors to cube roots of unity.

**P7.21** Let A be m×n and B be n×m with m > n. Prove det(AB) = 0.

---

## 7.5 Solutions to Chapter 7 Practice

**S7.1** det[[5,2],[3,4]] = 20 − 6 = **14**.
For the 3×3, expand along row 2 (has two zeros): = 3·det[[1,2],[4,5]] = 3(5 − 8) = **−9**.

**S7.2** det(3A) = 3³(7) = **189**. det(A⁻¹) = **1/7**. det(A²) = 49.

**S7.3** Lower triangular: 2 × 3 × 4 = **24**.

**S7.4** Row 2 = 2 × row 1 → **rank 1**.

**S7.5** **det = 0.** Swapping the two identical rows leaves the matrix unchanged but multiplies det by −1, so det = −det, forcing det = 0. (Alternatively: identical rows means the rows are dependent, so rank < n.)

**S7.6** Expand along row 3 = (0, 0, 1, 0). Only the (3,3) entry contributes, with sign (−1)^{3+3} = +:
det = 1 · det [[1, 3, 5], [2, 7, 4], [0, 0, 1]]
Now expand this 3×3 along its row 3 = (0,0,1), sign (−1)^{3+3} = +:
= 1 · det [[1, 3], [2, 7]] = 7 − 6 = **1**

**S7.7** Edge vectors from the origin: u = (3,1), v = (1,4).
Area = |det [[3, 1], [1, 4]]| = |12 − 1| = **11**.
*(Check that (4,5) = u + v ✓ confirming it is a parallelogram.)*

**S7.8** A = [[2, 1, −1], [1, −1, 1], [3, 2, 1]], b = (3, 0, 7).
det A = 2(−1−2) − 1(1−3) + (−1)(2+3) = −6 + 2 − 5 = **−9**.
A₁(b) = [[3,1,−1],[0,−1,1],[7,2,1]]: = 3(−1−2) − 1(0−7) + (−1)(0+7) = −9 + 7 − 7 = −9.
A₂(b) = [[2,3,−1],[1,0,1],[3,7,1]]: = 2(0−7) − 3(1−3) + (−1)(7−0) = −14 + 6 − 7 = −15.
A₃(b) = [[2,1,3],[1,−1,0],[3,2,7]]: = 2(−7−0) − 1(7−0) + 3(2+3) = −14 − 7 + 15 = −6.
**x = −9/−9 = 1, y = −15/−9 = 5/3, z = −6/−9 = 2/3.**
*Check eq1: 2(1) + 5/3 − 2/3 = 2 + 1 = 3 ✓*

**S7.9** Row 2 = 2 × row 1. Rows 1 and 3 are not proportional. **rank = 2.**

**S7.10** det = k(k²−1) − 1(k−1) + 1(1−k) = k³ − k − k + 1 + 1 − k = k³ − 3k + 2 = (k−1)²(k+2).
**Singular for k = 1 and k = −2.**
*(At k = 1 all rows are equal → rank 1. At k = −2 the rows sum to zero → rank 2.)*

**S7.11** det = 5 − 6 = −1. Cofactors: C₁₁ = 5, C₁₂ = −3, C₂₁ = −2, C₂₂ = 1.
adj A = transpose of [[5, −3], [−2, 1]] = [[5, −2], [−3, 1]].
A⁻¹ = (1/−1)[[5,−2],[−3,1]] = **[[−5, 2], [3, −1]]**.
*Check: [[1,2],[3,5]]·[[−5,2],[3,−1]] = [[−5+6, 2−2],[−15+15, 6−5]] = [[1,0],[0,1]] ✓*

**S7.12** Every row sums to 10. Add columns 2, 3, 4 to column 1 (`C₁ → C₁+C₂+C₃+C₄`, a valid replacement):
```
| 10  2  3  4 |
| 10  3  4  1 |
| 10  4  1  2 |
| 10  1  2  3 |
```
Factor 10 out of column 1:
```
10 · | 1  2  3  4 |
     | 1  3  4  1 |
     | 1  4  1  2 |
     | 1  1  2  3 |
```
Now `R₂−R₁`, `R₃−R₁`, `R₄−R₁`:
```
10 · | 1  2   3   4 |
     | 0  1   1  −3 |
     | 0  2  −2  −2 |
     | 0 −1  −1  −1 |
```
Expand along column 1: = 10 · det [[1, 1, −3], [2, −2, −2], [−1, −1, −1]].
`R₂ − 2R₁`, `R₃ + R₁`:
= 10 · det [[1, 1, −3], [0, −4, 4], [0, 0, −4]]
= 10 · (1)(−4)(−4) = 10 · 16 = **160**

**S7.13** Skew-symmetric means Aᵀ = −A. Taking determinants:
det(Aᵀ) = det(−A)
det(A) = (−1)ⁿ det(A)
For **n odd**, (−1)ⁿ = −1, so det A = −det A → 2 det A = 0 → **det A = 0** ∎
*(For n even this argument gives nothing, and indeed det can be nonzero — e.g. [[0,1],[−1,0]] has det 1.)*

**S7.14** Reduce:
```
[[1, −1,  2,  3],
 [2,  1,  1,  4],
 [3,  0,  3,  7],
 [1,  2, −1,  1]]
```
`R₂ − 2R₁`, `R₃ − 3R₁`, `R₄ − R₁`:
```
[[1, −1,  2,  3],
 [0,  3, −3, −2],
 [0,  3, −3, −2],
 [0,  3, −3, −2]]
```
`R₃ − R₂`, `R₄ − R₂` → two zero rows.
```
[[1, −1,  2,  3],
 [0,  3, −3, −2],
 [0,  0,  0,  0],
 [0,  0,  0,  0]]
```
**rank = 2.** Nullity = 4 − 2 = 2.

RREF: `R₂ → (1/3)R₂` → (0, 1, −1, −2/3); `R₁ + R₂` → (1, 0, 1, 3 − 2/3) = (1, 0, 1, 7/3).
Free: x₃ = s, x₄ = t. x₁ = −s − (7/3)t, x₂ = s + (2/3)t.
**Nul(A) basis: {(−1, 1, 1, 0), (−7, 2, 0, 3)}** (second scaled by 3).

**S7.15** det(2A⁻¹(adj A)ᵀ) = det(2A⁻¹) · det((adj A)ᵀ)
- det(2A⁻¹) = 2³ · (1/4) = 8/4 = 2
- det((adj A)ᵀ) = det(adj A) = (det A)^{n−1} = 4² = 16

**Answer: 2 × 16 = 32.**

**S7.16** Volume = |det [[1, 2, 0], [0, 1, 3], [2, 0, 1]]| (vectors as columns).
det = 1(1·1 − 3·0) − 2(0·1 − 3·2) + 0 = 1 − 2(−6) = 1 + 12 = **13**.
**Volume = 13.** Since det = +13 > 0, the ordered triple **is right-handed** ✓

**S7.17** Let D_n = det of the matrix with a on the diagonal, b off-diagonal.

Every row sums to a + (n−1)b. Add all other columns to column 1:
```
| a+(n−1)b   b   b  ... |
| a+(n−1)b   a   b  ... |
|    ⋮                  |
```
Factor out [a + (n−1)b] from column 1 — every entry there is now 1.

Now subtract row 1 from every other row. Column 1 becomes 0 below the top. Each other column j gets (b − a) in row i ≠ 1 at position j=i and 0 elsewhere... more precisely the result is upper triangular with (a − b) repeated (n−1) times on the diagonal below the first.

**D_n = [a + (n−1)b] · (a − b)^{n−1}**

*Check n = 2:* (a + b)(a − b) = a² − b² ✓ matches det[[a,b],[b,a]].
*Check n = 3, a = k, b = 1:* (k + 2)(k − 1)² ✓ matches S7.10.

**S7.18** **Direct 2×2.** A = [[a,b],[c,d]], B = [[e,f],[g,h]].
AB = [[ae+bg, af+bh], [ce+dg, cf+dh]].
det(AB) = (ae+bg)(cf+dh) − (af+bh)(ce+dg)
= acef + adeh + bcfg + bdgh − acef − adfg − bceh − bdgh
= adeh + bcfg − adfg − bceh
= ad(eh − fg) − bc(eh − fg)
= (ad − bc)(eh − fg) = det(A)det(B) ✓ ∎

**Why the general proof differs.** For n×n, direct expansion involves n!² terms — combinatorially unmanageable. The standard proof instead:
1. Shows det(EB) = det(E)det(B) for each of the three **elementary matrices** E (each is a one-line check against the row-operation properties).
2. If A is singular, both sides are 0 (AB is singular too, since rank(AB) ≤ rank A < n).
3. If A is invertible, write A = E₁E₂···E_k as a product of elementary matrices (Theorem 3.1), and apply step 1 repeatedly.

This reduces an n!-sized problem to three small verifications plus induction.

**S7.19** Recall **A·adj(A) = (det A)·I**.

**(a) r = n.** det A ≠ 0, so adj A = (det A)A⁻¹ is a nonzero scalar times an invertible matrix → **rank(adj A) = n** ✓

**(b) r = n − 1.** Then det A = 0, so A·adj(A) = 0, meaning **Col(adj A) ⊆ Nul(A)**, which has dimension n − r = 1. So rank(adj A) ≤ 1.
Also, rank A = n − 1 means some (n−1)×(n−1) minor is nonzero, so at least one cofactor is nonzero, so adj A ≠ 0, giving rank ≥ 1.
**rank(adj A) = 1** ✓

**(c) r < n − 1.** Then **every** (n−1)×(n−1) submatrix has rank < n − 1 (since rank of a submatrix ≤ rank A < n−1), so every such minor is 0. Hence **every cofactor is 0**, so adj A = 0 and **rank(adj A) = 0** ✓ ∎

**S7.20** Add columns 2 and 3 to column 1 — every entry becomes a + b + c:
```
| a+b+c  b  c |
| a+b+c  a  b |
| a+b+c  c  a |
```
Factor out (a+b+c):
```
(a+b+c) · | 1  b  c |
          | 1  a  b |
          | 1  c  a |
```
`R₂ − R₁`, `R₃ − R₁`:
```
(a+b+c) · | 1   b     c   |
          | 0  a−b   b−c  |
          | 0  c−b   a−c  |
```
= (a+b+c)[(a−b)(a−c) − (b−c)(c−b)]
= (a+b+c)[a² − ac − ab + bc + (b−c)²]
= (a+b+c)[a² − ac − ab + bc + b² − 2bc + c²]
= (a+b+c)(a² + b² + c² − ab − bc − ca)

**det = (a + b + c)(a² + b² + c² − ab − bc − ca)**

**Full factorization over ℂ.** Let ω = e^{2πi/3} be a primitive cube root of unity (ω³ = 1, 1 + ω + ω² = 0). Then

> **det = (a + b + c)(a + bω + cω²)(a + bω² + cω)**

*Verification of the structure:* the vectors (1, 1, 1), (1, ω, ω²), (1, ω², ω) are eigenvectors of the circulant matrix, with eigenvalues a + b + c, a + bω + cω², a + bω² + cω respectively. The determinant is the product of eigenvalues.

*Check the real form:* (a + bω + cω²)(a + bω² + cω) = a² + b² + c² − ab − bc − ca (using ω + ω² = −1, ω³ = 1) ✓

**Corollary:** det = 0 ⟺ a + b + c = 0 or a = b = c.

**S7.21** AB is m×m, but rank(AB) ≤ rank(A) ≤ min(m, n) = **n** (since m > n).

So rank(AB) ≤ n < m, meaning the m×m matrix AB is **not full rank**, hence singular.

**Therefore det(AB) = 0.** ∎

*Intuition:* the map goes ℝᵐ → ℝⁿ → ℝᵐ. It squeezes through a space of dimension n < m, so it must flatten — volume is destroyed and the determinant vanishes. This is the **Cauchy–Binet** boundary case.

---
# Chapter 8 — Applications of Linear Algebra in Information Technology and Data Representation

---

## 8.1 Explain Like I'm Five

Everything a computer handles is secretly a list of numbers, and a list of numbers is a vector.

- A **photo** is a grid of brightness values → a matrix.
- A **song** is a list of air-pressure samples → a vector.
- A **web page** is a bag of word counts → a vector.
- A **social network** is a table of who-knows-whom → a matrix of 0s and 1s.
- A **document collection** is a matrix: one row per word, one column per document.

Once your data is a matrix, every tool in this course becomes a tool for working with data. Rank tells you how much *genuine* information is there versus repetition. Projections tell you how to compress. Solving `Ax = b` tells you how to decode a corrupted message. Eigenvectors tell you what direction the data "mostly points".

The whole of data science is essentially this observation, taken seriously.

---

## 8.2 Data as Matrices

### 8.2.1 The Data Matrix Convention

The standard layout in statistics and machine learning:

> **X is m×n: m rows = observations (samples), n columns = features (variables)**

Row i is the feature vector of sample i. Column j is the value of feature j across all samples.

**Mean-centering:** subtract each column's mean. The centered matrix X_c = X − 1x̄ᵀ has columns summing to zero. This is required before PCA (Chapter 14).

**Standardizing:** divide each centered column by its standard deviation, giving each feature comparable scale. Essential when features have different units (age in years vs income in rupees).

**Covariance matrix:** C = (1/(m−1))X_cᵀX_c, an n×n symmetric positive semidefinite matrix whose (i,j) entry is the covariance of features i and j.

### 8.2.2 Images

A grayscale image of height h and width w is an h×w matrix with entries in [0, 255].

A colour image is three such matrices (R, G, B) — a **tensor** of shape h×w×3 — or a single h×(3w) matrix if flattened.

**Operations as matrix algebra:**
- **Brightness:** A + c·J (J = all-ones matrix)
- **Contrast:** cA
- **Negative:** 255·J − A
- **Transpose:** Aᵀ is the image reflected across the main diagonal
- **Horizontal flip:** AP where P is the reversal permutation matrix
- **Downsampling:** SA where S selects every k-th row

**Convolution/filtering** (blur, sharpen, edge detection) applies a small kernel over sliding windows. Written as a matrix operation, it becomes multiplication by a large **Toeplitz** (constant-diagonal) matrix — which is why convolutional neural networks are still, at heart, linear algebra.

### 8.2.3 Text: The Term–Document Matrix

Given a vocabulary of V terms and D documents, form the V×D matrix A where

> Aᵢⱼ = (weight of term i in document j)

**Weighting schemes:**
- **Binary:** 1 if the term appears, else 0
- **Term frequency (tf):** raw count
- **TF–IDF:** tfᵢⱼ × log(D/dfᵢ), where dfᵢ is the number of documents containing term i. This downweights common words ("the") and upweights distinctive ones.

**Document similarity = cosine similarity** between columns:

> sim(dⱼ, dₖ) = (aⱼ · aₖ)/(‖aⱼ‖‖aₖ‖)

Cosine, not Euclidean distance, because document *length* shouldn't matter — only the *direction* of the word-usage profile. This is exactly the angle formula from Chapter 5.

**Latent Semantic Analysis (LSA)** applies a truncated SVD to this matrix to find "topics" — see Chapter 13.

### 8.2.4 Graphs and Networks

For a graph with n vertices, the **adjacency matrix** A is n×n with Aᵢⱼ = 1 if there is an edge i→j, else 0.

> **Key theorem:** the (i,j) entry of **Aᵏ** equals the number of **walks of length k** from vertex i to vertex j.

*Why:* (A²)ᵢⱼ = Σₖ AᵢₖAₖⱼ counts intermediate vertices k adjacent to both. Induction extends this.

**Degree matrix** D = diag(deg(v₁), ..., deg(vₙ)).
**Graph Laplacian** L = D − A. Properties:
- L is symmetric positive semidefinite
- L·1 = 0, so 0 is always an eigenvalue
- **The multiplicity of eigenvalue 0 equals the number of connected components**
- The second-smallest eigenvalue (the **Fiedler value**) measures how well-connected the graph is; its eigenvector gives a good bipartition (spectral clustering)

**Incidence matrix** for a directed graph with m edges: an n×m matrix with −1 at the tail, +1 at the head. Then L = MMᵀ.

### 8.2.5 Error-Correcting Codes

Over the field 𝔽₂ = {0, 1} (arithmetic mod 2), a **linear code** of length n and dimension k is a k-dimensional subspace C ⊆ 𝔽₂ⁿ.

- **Generator matrix** G (k×n): codewords are c = xG for message x ∈ 𝔽₂ᵏ. So C = Row(G).
- **Parity check matrix** H ((n−k)×n): c ∈ C ⟺ **Hcᵀ = 0**. So C = Nul(H).
- **Syndrome** of a received word r: s = Hrᵀ. If s = 0, no (detectable) error. Otherwise s identifies the error pattern.

**Hamming(7,4) code.** k = 4, n = 7, corrects any single-bit error. Its parity check matrix has as columns all 7 nonzero vectors of 𝔽₂³:
```
H = [[0, 0, 0, 1, 1, 1, 1],
     [0, 1, 1, 0, 0, 1, 1],
     [1, 0, 1, 0, 1, 0, 1]]
```
The syndrome, read as a binary number, gives the **position of the flipped bit** directly. Beautifully simple, and it is nothing but "solve Hx = s".

### 8.2.6 Cryptography — the Hill Cipher

Encode letters as numbers mod 26. Choose an invertible n×n key matrix K over ℤ₂₆.

> **Encryption:** c = Kp mod 26 **Decryption:** p = K⁻¹c mod 26

K is invertible mod 26 ⟺ gcd(det K, 26) = 1 ⟺ det K is odd and not divisible by 13.

**Modular inverse:** K⁻¹ = (det K)⁻¹ · adj(K) mod 26, where (det K)⁻¹ is the multiplicative inverse of det K mod 26.

### 8.2.7 Computer Graphics — Homogeneous Coordinates

Translation is **not** a linear map (it moves the origin). Trick: embed ℝ² in ℝ³ by appending a 1.

> (x, y) ↦ (x, y, 1)

Then:

| Transformation | 3×3 matrix |
|---|---|
| Translation by (t₁, t₂) | [[1, 0, t₁], [0, 1, t₂], [0, 0, 1]] |
| Scaling by (s₁, s₂) | [[s₁, 0, 0], [0, s₂, 0], [0, 0, 1]] |
| Rotation by θ | [[cos θ, −sin θ, 0], [sin θ, cos θ, 0], [0, 0, 1]] |
| Shear (horizontal, factor k) | [[1, k, 0], [0, 1, 0], [0, 0, 1]] |
| Reflection in x-axis | [[1, 0, 0], [0, −1, 0], [0, 0, 1]] |

Composing transformations = multiplying matrices. **Order matters** — rotate-then-translate ≠ translate-then-rotate. Every GPU on Earth does exactly this, billions of times per second.

For 3D graphics the same trick uses 4×4 matrices, with the fourth coordinate also enabling **perspective projection**.

### 8.2.8 Markov Chains

A **stochastic matrix** P has non-negative entries and columns summing to 1 (or rows, depending on convention). It describes probabilities of moving between states.

State evolution: x_{k+1} = Px_k, so x_k = Pᵏx₀.

> **Theorem.** If P is **regular** (some power has all positive entries), there is a unique **steady-state vector** q with Pq = q, Σqᵢ = 1, and x_k → q for every starting x₀.

q is the eigenvector of P for eigenvalue 1 — the link to Chapter 9. **PageRank** is precisely this computation on the web graph.

### 8.2.9 Computational Cost Summary

| Operation | Cost |
|---|---|
| Matrix–vector product (n×n) | O(n²) |
| Matrix–matrix product | O(n³) (Strassen: O(n^2.807)) |
| Gaussian elimination / LU | O(n³), specifically ~(2/3)n³ |
| Solving after LU (per RHS) | O(n²) |
| Gram–Schmidt / QR | O(mn²) |
| Determinant by elimination | O(n³) |
| Determinant by cofactors | O(n!) — never do this |
| Full SVD | O(min(m,n)²·max(m,n)) |
| Matrix inverse | ~2n³ |

**Sparse matrices** (mostly zeros) get special storage and algorithms — a web graph with 10⁹ nodes has ~10¹⁰ nonzeros out of 10¹⁸ possible entries, so only the nonzeros are stored.

---

## 8.3 Solved Examples

### Example 8.1 — [Easy] Walks in a graph

For the graph with adjacency matrix
```
A = [[0, 1, 1],
     [1, 0, 1],
     [1, 1, 0]]
```
find the number of walks of length 2 from vertex 1 to vertex 3, and the number of triangles.

**Solution.**
```
A² = [[0,1,1],[1,0,1],[1,1,0]]²
```
Row 1 of A²: (0,1,1)·col1 = (0)(0)+(1)(1)+(1)(1) = 2; ·col2 = 0+0+1 = 1; ·col3 = 0+1+0 = 1.
By symmetry:
```
A² = [[2, 1, 1],
      [1, 2, 1],
      [1, 1, 2]]
```
**(A²)₁₃ = 1** — exactly one walk of length 2 from vertex 1 to vertex 3 (namely 1→2→3).

**Triangles:** the number of closed walks of length 3 at vertex i is (A³)ᵢᵢ.
A³ = A²·A. Diagonal entry (1,1): row 1 of A² = (2,1,1) dotted with column 1 of A = (0,1,1): = 0 + 1 + 1 = 2.
trace(A³) = 3(2) = 6. Each triangle is counted once per starting vertex (3) and per direction (2), so

**number of triangles = 6/6 = 1** ✓ (the graph is a single triangle K₃).

---

### Example 8.2 — [Medium] Hill cipher

Encrypt "HELP" using the key K = [[3, 3], [2, 5]] mod 26, then decrypt to verify.

**Solution.** Letters: A=0, ..., Z=25. H=7, E=4, L=11, P=15.

Blocks: (7, 4) and (11, 15).

**Encryption of (7,4):**
```
K·(7,4)ᵀ = (3(7) + 3(4), 2(7) + 5(4)) = (21 + 12, 14 + 20) = (33, 34)
mod 26 → (7, 8) → H, I
```
**Encryption of (11,15):**
```
K·(11,15)ᵀ = (33 + 45, 22 + 75) = (78, 97)
mod 26 → 78 = 3(26) = 0; 97 = 3(26) + 19 = 19 → (0, 19) → A, T
```

**Ciphertext: "HIAT"**

**Decryption.** det K = 15 − 6 = 9. gcd(9, 26) = 1 ✓ invertible.
Find 9⁻¹ mod 26: 9 × 3 = 27 ≡ 1 ✓ so 9⁻¹ = 3.
adj K = [[5, −3], [−2, 3]].
K⁻¹ = 3 · [[5, −3], [−2, 3]] mod 26 = [[15, −9], [−6, 9]] ≡ **[[15, 17], [20, 9]]** mod 26.

*Verify:* K⁻¹K = [[15(3)+17(2), 15(3)+17(5)], [20(3)+9(2), 20(3)+9(5)]] = [[45+34, 45+85], [60+18, 60+45]] = [[79, 130], [78, 105]].
mod 26: 79 = 3(26)+1 = 1 ✓; 130 = 5(26) = 0 ✓; 78 = 0 ✓; 105 = 4(26)+1 = 1 ✓ → I ✓

**Decrypt (7, 8):** K⁻¹(7,8)ᵀ = (105 + 136, 140 + 72) = (241, 212).
241 mod 26: 26(9) = 234, so 7 ✓ (H). 212 mod 26: 26(8) = 208, so 4 ✓ (E).
**Recovered "HE"** ✓

---

### Example 8.3 — [Medium] Hamming code error correction

A Hamming(7,4) codeword was transmitted and received as r = (1, 0, 1, 1, 0, 1, 1). Using
```
H = [[0, 0, 0, 1, 1, 1, 1],
     [0, 1, 1, 0, 0, 1, 1],
     [1, 0, 1, 0, 1, 0, 1]]
```
find and correct the error.

**Solution.** Compute the syndrome s = Hrᵀ over 𝔽₂ (addition = XOR).

**Row 1** · r = (0)(1) + (0)(0) + (0)(1) + (1)(1) + (1)(0) + (1)(1) + (1)(1) = 0+0+0+1+0+1+1 = 3 ≡ **1** (mod 2)

**Row 2** · r = 0 + 0 + 1 + 0 + 0 + 1 + 1 = 3 ≡ **1**

**Row 3** · r = 1 + 0 + 1 + 0 + 0 + 0 + 1 = 3 ≡ **1**

**Syndrome s = (1, 1, 1)ᵀ.**

Reading (s₁s₂s₃) as binary 111 = **7**. The columns of H are the binary representations of 1 through 7 in order, so the syndrome matches **column 7**.

**Therefore bit 7 is flipped.** Correct it:

**Corrected codeword: c = (1, 0, 1, 1, 0, 1, 0)**

*Verify:* Hcᵀ — row 1: 0+0+0+1+0+1+0 = 2 ≡ 0 ✓; row 2: 0+0+1+0+0+1+0 = 2 ≡ 0 ✓; row 3: 1+0+1+0+0+0+0 = 2 ≡ 0 ✓
Syndrome is zero — valid codeword ✓

---

### Example 8.4 — [Hard] Graph Laplacian and connectivity

For the graph with edges {1−2, 2−3, 4−5}, build the Laplacian and use it to determine the number of connected components.

**Solution.** Vertices 1–5.

Degrees: deg(1)=1, deg(2)=2, deg(3)=1, deg(4)=1, deg(5)=1.

```
A = [[0,1,0,0,0],       D = diag(1,2,1,1,1)
     [1,0,1,0,0],
     [0,1,0,0,0],
     [0,0,0,0,1],
     [0,0,0,1,0]]
```
```
L = D − A = [[ 1, −1,  0,  0,  0],
             [−1,  2, −1,  0,  0],
             [ 0, −1,  1,  0,  0],
             [ 0,  0,  0,  1, −1],
             [ 0,  0,  0, −1,  1]]
```

**Finding Nul(L).** L is block diagonal with blocks for {1,2,3} and {4,5}.

Block 1: [[1,−1,0],[−1,2,−1],[0,−1,1]]. Reduce: `R₂ + R₁` → (0,1,−1); `R₃ + R₂'` → (0,0,0). Rank 2, nullity 1, null vector (1,1,1).

Block 2: [[1,−1],[−1,1]]. Rank 1, nullity 1, null vector (1,1).

**dim Nul(L) = 1 + 1 = 2**, with basis {(1,1,1,0,0), (0,0,0,1,1)} — the indicator vectors of the two components.

**Answer: 2 connected components**, namely {1,2,3} and {4,5}. ✓

*(This is the general theorem: the multiplicity of eigenvalue 0 in L equals the number of components, and the null space is spanned by the components' indicator vectors.)*

---

### Example 8.5 — [Hard] Markov chain steady state

A user browsing three pages moves according to the stochastic matrix (columns sum to 1)
```
P = [[0.5, 0.2, 0.3],
     [0.3, 0.6, 0.3],
     [0.2, 0.2, 0.4]]
```
Find the long-run distribution.

**Solution.** Solve Pq = q, i.e. (P − I)q = 0, with Σqᵢ = 1.

```
P − I = [[−0.5,  0.2,  0.3],
         [ 0.3, −0.4,  0.3],
         [ 0.2,  0.2, −0.6]]
```
Multiply by 10 to clear decimals:
```
[[−5,  2,  3],
 [ 3, −4,  3],
 [ 2,  2, −6]]
```
`R₃ → R₃ ÷ 2` → (1, 1, −3). Swap to the top:
```
[[1, 1, −3],
 [−5, 2, 3],
 [3, −4, 3]]
```
`R₂ + 5R₁` → (0, 7, −12). `R₃ − 3R₁` → (0, −7, 12).
`R₃ + R₂` → zero row ✓ (as expected — the matrix is singular).

From row 2: 7q₂ = 12q₃ → q₂ = (12/7)q₃.
From row 1: q₁ = 3q₃ − q₂ = 3q₃ − (12/7)q₃ = (9/7)q₃.

Normalize: q₁ + q₂ + q₃ = (9/7 + 12/7 + 7/7)q₃ = (28/7)q₃ = 4q₃ = 1 → q₃ = 1/4.

**q = (9/28, 12/28, 7/28) = (9/28, 3/7, 1/4) ≈ (0.321, 0.429, 0.250)**

**Verify Pq = q, first component:** 0.5(0.321) + 0.2(0.429) + 0.3(0.250) = 0.1607 + 0.0857 + 0.075 = 0.321 ✓

**Interpretation:** in the long run, roughly 32% of visits land on page 1, 43% on page 2, 25% on page 3 — regardless of where the user started. This is PageRank in miniature.

---

### Example 8.6 — [Very Hard] Graphics transformation composition

Derive the 3×3 homogeneous matrix that rotates the plane by 90° **about the point (2, 3)**, and apply it to the point (4, 3).

**Solution.** Rotation about an arbitrary point is not a single rotation matrix — the origin must first be moved.

**Decompose into three steps:**
1. Translate by (−2, −3) so the pivot goes to the origin: T₋
2. Rotate by 90° about the origin: R
3. Translate back by (+2, +3): T₊

**M = T₊ · R · T₋** (rightmost acts first)

```
T₋ = [[1, 0, −2],      R = [[0, −1, 0],      T₊ = [[1, 0, 2],
      [0, 1, −3],           [1,  0, 0],            [0, 1, 3],
      [0, 0,  1]]           [0,  0, 1]]            [0, 0, 1]]
```
*(cos 90° = 0, sin 90° = 1.)*

**Step A: R·T₋**
```
= [[0,−1,0],[1,0,0],[0,0,1]] · [[1,0,−2],[0,1,−3],[0,0,1]]
```
Row 1: (0, −1, 0)·columns → (0, −1, 0(−2) + (−1)(−3) + 0(1)) = (0, −1, 3)
Row 2: (1, 0, 0) → (1, 0, −2)
Row 3: (0, 0, 1)
```
R·T₋ = [[0, −1,  3],
        [1,  0, −2],
        [0,  0,  1]]
```

**Step B: T₊·(R·T₋)**
```
= [[1,0,2],[0,1,3],[0,0,1]] · [[0,−1,3],[1,0,−2],[0,0,1]]
```
Row 1: (1, 0, 2)·cols = (0 + 0 + 0, −1 + 0 + 0, 3 + 0 + 2) = (0, −1, 5)
Row 2: (0, 1, 3)·cols = (0 + 1 + 0, 0 + 0 + 0, 0 − 2 + 3) = (1, 0, 1)
Row 3: (0, 0, 1)

```
M = [[0, −1, 5],
     [1,  0, 1],
     [0,  0, 1]]
```

**Apply to (4, 3) → homogeneous (4, 3, 1):**
M(4,3,1)ᵀ = (0(4) − 1(3) + 5(1), 1(4) + 0(3) + 1(1), 1) = (2, 5, 1)

**Answer: (4, 3) ↦ (2, 5)**

**Sanity check.** The point (4,3) is 2 units to the **right** of the pivot (2,3). Rotating 90° counterclockwise should place it 2 units **above** the pivot: (2, 3+2) = (2, 5) ✓

**Fixed point check:** M(2,3,1)ᵀ = (−3 + 5, 2 + 1, 1) = (2, 3, 1) ✓ the pivot is unmoved, as it must be.

---

### Example 8.7 — [Very Hard] Cosine similarity and TF–IDF

Three documents over the vocabulary {data, model, linear}:
- d₁: "data data model"
- d₂: "model linear model"
- d₃: "data linear linear"

Build the tf matrix, apply TF–IDF weighting, and find which two documents are most similar.

**Solution.**

**Term frequency matrix** (rows = terms, columns = documents):
```
        d₁  d₂  d₃
data  [[ 2,  0,  1],
model [  1,  2,  0],
linear[  0,  1,  2]]
```

**Document frequencies (D = 3):**
- "data" appears in d₁, d₃ → df = 2 → idf = log(3/2) = 0.4055
- "model" appears in d₁, d₂ → df = 2 → idf = 0.4055
- "linear" appears in d₂, d₃ → df = 2 → idf = 0.4055

All idf values are equal here, so TF–IDF is just a uniform scaling of tf — **it does not change any cosine similarity**. (An instructive outcome: idf only helps when terms differ in commonness.)

**Cosine similarities using the columns:**
- a₁ = (2, 1, 0), ‖a₁‖ = √5
- a₂ = (0, 2, 1), ‖a₂‖ = √5
- a₃ = (1, 0, 2), ‖a₃‖ = √5

sim(d₁, d₂) = (0 + 2 + 0)/(√5·√5) = 2/5 = **0.40**
sim(d₁, d₃) = (2 + 0 + 0)/5 = 2/5 = **0.40**
sim(d₂, d₃) = (0 + 0 + 2)/5 = 2/5 = **0.40**

**All three pairs are equally similar (0.40).** The data is perfectly symmetric — each document uses exactly two terms with counts 2 and 1, and each term pair is shared by exactly one document pair.

**Now break the symmetry.** Suppose d₄ = "data data data linear" is added, so "data" now appears in 3 of 4 documents:
- idf(data) = log(4/3) = 0.288
- idf(model) = log(4/2) = 0.693
- idf(linear) = log(4/3) = 0.288

Weighted columns:
- w₁ = (2(0.288), 1(0.693), 0) = (0.575, 0.693, 0), ‖w₁‖ = 0.901
- w₂ = (0, 2(0.693), 1(0.288)) = (0, 1.386, 0.288), ‖w₂‖ = 1.416
- w₃ = (0.288, 0, 2(0.288)) = (0.288, 0, 0.575), ‖w₃‖ = 0.643

sim(d₁, d₂) = (0 + 0.961 + 0)/(0.901 × 1.416) = 0.961/1.276 = **0.753**
sim(d₁, d₃) = (0.166 + 0 + 0)/(0.901 × 0.643) = 0.166/0.579 = **0.286**
sim(d₂, d₃) = (0 + 0 + 0.166)/(1.416 × 0.643) = 0.166/0.910 = **0.182**

**Now d₁ and d₂ are clearly most similar** — because they share "model", which IDF has identified as the *distinctive* term. Sharing the common word "data" earns much less credit.

**This is the entire point of TF–IDF**, and it is pure linear algebra: rescale the coordinate axes, then measure angles.

---

## 8.4 Practice Numericals — Chapter 8

**[Easy]**

**P8.1** For A = [[0,1,0],[0,0,1],[1,0,0]] (a directed 3-cycle), compute A² and A³. Interpret.

**P8.2** Write the homogeneous matrix for translation by (5, −2) followed by scaling by 3.

**P8.3** A grayscale image matrix is A = [[100, 150], [200, 50]]. Write the matrix for its photographic negative.

**P8.4** Encode "AB" using the Hill cipher key [[1, 2], [0, 1]] mod 26.

**P8.5** Is P = [[0.7, 0.4], [0.3, 0.6]] a stochastic matrix? Find P·(1, 0)ᵀ and interpret.

**[Medium]**

**P8.6** Build the term–document matrix for d₁ = "cat dog cat", d₂ = "dog bird", d₃ = "cat bird bird" over {cat, dog, bird} and compute all pairwise cosine similarities.

**P8.7** Find the steady state of P = [[0.9, 0.5], [0.1, 0.5]].

**P8.8** For the path graph 1−2−3−4, write the Laplacian and verify L·1 = 0.

**P8.9** Compose: rotate by 45° then translate by (1, 1). Write the single 3×3 matrix and apply it to (√2, 0).

**P8.10** Determine whether K = [[2, 3], [1, 4]] is a valid Hill cipher key mod 26.

**P8.11** For a 6×4 data matrix X, state the shapes of X_c, XᵀX, XXᵀ, and the covariance matrix. Which is the covariance matrix?

**[Hard]**

**P8.12** A Hamming(7,4) received word is r = (0, 1, 1, 0, 1, 0, 1). Find the syndrome, locate and correct the error, and extract the message bits (positions 3, 5, 6, 7).

**P8.13** For the graph with adjacency matrix A = [[0,1,1,0],[1,0,1,1],[1,1,0,1],[0,1,1,0]], count walks of length 3 from vertex 1 to vertex 4, and compute the number of triangles.

**P8.14** Derive the 3×3 homogeneous matrix that reflects points across the line y = x + 2.

**P8.15** Decrypt "RGWT" given the Hill key K = [[5, 8], [17, 3]] mod 26. (First verify K is invertible mod 26.)

**P8.16** Show that if P is a column-stochastic matrix, then 1ᵀP = 1ᵀ, and deduce that 1 is always an eigenvalue of Pᵀ, hence of P.

**[Very Hard]**

**P8.17** Prove that the (i,j) entry of Aᵏ counts the number of walks of length k from i to j, by induction on k.

**P8.18** For the Laplacian L of a connected graph on n vertices, prove rank(L) = n − 1 and that Nul(L) = span{1}.

**P8.19** A linear code has generator matrix G = [[1,0,0,1,1], [0,1,0,1,0], [0,0,1,0,1]] over 𝔽₂. Find the parity check matrix H, list all 8 codewords, determine the minimum distance, and state how many errors the code can detect and correct.

**P8.20** Prove that a regular stochastic matrix has a unique steady-state vector with strictly positive entries. (Outline the Perron–Frobenius argument; a full proof is not expected, but state precisely which properties are used.)

---

## 8.5 Solutions to Chapter 8 Practice

**S8.1** A sends 1→2, 2→3, 3→1.
A² = [[0,0,1],[1,0,0],[0,1,0]] — walks of length 2: 1→3, 2→1, 3→2.
A³ = **I** — after three steps you are back where you started ✓ (a 3-cycle has period 3).

**S8.2** Scaling applied **after** translation, so S·T:
```
S·T = [[3,0,0],[0,3,0],[0,0,1]] · [[1,0,5],[0,1,−2],[0,0,1]]
    = [[3, 0, 15], [0, 3, −6], [0, 0, 1]]
```
*(Note: the translation gets scaled too. If you wanted translate-after-scale, you'd get [[3,0,5],[0,3,−2],[0,0,1]] — different matrix.)*

**S8.3** Negative = 255J − A = [[255−100, 255−150],[255−200, 255−50]] = **[[155, 105], [55, 205]]**.

**S8.4** A=0, B=1. Block (0, 1).
K(0,1)ᵀ = (1(0) + 2(1), 0(0) + 1(1)) = (2, 1) → **C, B** → **"CB"**.

**S8.5** Columns: 0.7 + 0.3 = 1 ✓, 0.4 + 0.6 = 1 ✓, all entries ≥ 0 ✓. **Yes, column-stochastic.**
P(1,0)ᵀ = (0.7, 0.3). **Interpretation:** starting in state 1 with certainty, after one step there is a 70% chance of being in state 1 and 30% in state 2.

**S8.6** Term–document matrix:
```
        d₁  d₂  d₃
cat   [[ 2,  0,  1],
dog   [  1,  1,  0],
bird  [  0,  1,  2]]
```
- a₁ = (2,1,0), ‖a₁‖ = √5 ≈ 2.236
- a₂ = (0,1,1), ‖a₂‖ = √2 ≈ 1.414
- a₃ = (1,0,2), ‖a₃‖ = √5 ≈ 2.236

sim(d₁,d₂) = (0 + 1 + 0)/(√5√2) = 1/3.162 = **0.316**
sim(d₁,d₃) = (2 + 0 + 0)/(√5√5) = 2/5 = **0.400**
sim(d₂,d₃) = (0 + 0 + 2)/(√2√5) = 2/3.162 = **0.632**

**Most similar pair: d₂ and d₃** (0.632), since "bird" dominates both.

**S8.7** Solve (P − I)q = 0: P − I = [[−0.1, 0.5], [0.1, −0.5]].
−0.1q₁ + 0.5q₂ = 0 → q₁ = 5q₂.
Normalize: 5q₂ + q₂ = 1 → q₂ = 1/6, q₁ = 5/6.
**q = (5/6, 1/6) ≈ (0.833, 0.167)**
*Check: 0.9(5/6) + 0.5(1/6) = 0.75 + 0.0833 = 0.8333 ✓*

**S8.8** Degrees: 1, 2, 2, 1.
```
L = [[ 1, −1,  0,  0],
     [−1,  2, −1,  0],
     [ 0, −1,  2, −1],
     [ 0,  0, −1,  1]]
```
L·1: row sums are 1−1 = 0; −1+2−1 = 0; −1+2−1 = 0; −1+1 = 0. **L·1 = 0 ✓**
*(Always true: each diagonal entry is the degree, and the off-diagonal −1s in that row number exactly the degree.)*

**S8.9** cos 45° = sin 45° = 1/√2 = 0.7071.
```
R = [[0.7071, −0.7071, 0], [0.7071, 0.7071, 0], [0, 0, 1]]
T = [[1, 0, 1], [0, 1, 1], [0, 0, 1]]
```
Rotate first, then translate: **M = T·R**
```
M = [[0.7071, −0.7071, 1],
     [0.7071,  0.7071, 1],
     [0,       0,      1]]
```
Apply to (√2, 0, 1): (0.7071(√2) − 0 + 1, 0.7071(√2) + 0 + 1, 1) = (1 + 1, 1 + 1, 1) = **(2, 2)**
*Check: rotating (√2, 0) by 45° gives (1, 1); translating by (1,1) gives (2,2) ✓*

**S8.10** det K = 2(4) − 3(1) = 5. gcd(5, 26) = 1 ✓
**Yes, valid.** (5⁻¹ mod 26 = 21, since 5×21 = 105 = 4(26) + 1 ✓)

**S8.11** X is 6×4 (6 samples, 4 features).
- **X_c: 6×4** (same shape, columns centered)
- **XᵀX: 4×4**
- **XXᵀ: 6×6**
- **Covariance matrix C = X_cᵀX_c/(m−1): 4×4** — it is the **4×4 one**, since covariance is between *features*, and there are 4 features.
*(The 6×6 matrix XXᵀ is the Gram matrix of similarities between samples — useful for kernel methods, but not the covariance.)*

**S8.12** r = (0, 1, 1, 0, 1, 0, 1).
```
H = [[0,0,0,1,1,1,1],
     [0,1,1,0,0,1,1],
     [1,0,1,0,1,0,1]]
```
Row 1 · r = 0+0+0+0+1+0+1 = 2 ≡ **0**
Row 2 · r = 0+1+1+0+0+0+1 = 3 ≡ **1**
Row 3 · r = 0+0+1+0+1+0+1 = 3 ≡ **1**

**Syndrome = (0, 1, 1) = binary 011 = 3.**

**Bit 3 is flipped.** Corrected: **c = (0, 1, 0, 0, 1, 0, 1)**.
*Verify:* row 2 · c = 0+1+0+0+0+0+1 = 2 ≡ 0 ✓; row 3 · c = 0+0+0+0+1+0+1 = 2 ≡ 0 ✓; row 1 · c = 0+0+0+0+1+0+1 = 2 ≡ 0 ✓

**Message bits** (positions 3, 5, 6, 7) = **(0, 1, 0, 1)**.

**S8.13**
```
A = [[0,1,1,0],
     [1,0,1,1],
     [1,1,0,1],
     [0,1,1,0]]
```
**A²:** Row 1 = (0,1,1,0):
- ·col1 = 0+1+1+0 = 2; ·col2 = 0+0+1+0 = 1; ·col3 = 0+1+0+0 = 1; ·col4 = 0+1+1+0 = 2
Row 2 = (1,0,1,1): ·col1 = 0+0+1+0 = 1; ·col2 = 1+0+1+1 = 3; ·col3 = 1+0+0+1 = 2; ·col4 = 0+0+1+0 = 1
Row 3 = (1,1,0,1): ·col1 = 0+1+0+0 = 1; ·col2 = 1+0+0+1 = 2; ·col3 = 1+1+0+1 = 3; ·col4 = 0+1+0+0 = 1
Row 4 = (0,1,1,0): same as row 1 = (2, 1, 1, 2)
```
A² = [[2,1,1,2],
      [1,3,2,1],
      [1,2,3,1],
      [2,1,1,2]]
```
**(A³)₁₄** = row 1 of A² dotted with column 4 of A = (2,1,1,2)·(0,1,1,0) = 0 + 1 + 1 + 0 = **2**.
So there are **2 walks of length 3 from vertex 1 to vertex 4** (namely 1→2→3→4 and 1→3→2→4).

**Triangles:** trace(A³) = Σᵢ (row i of A²)·(col i of A).
- i=1: (2,1,1,2)·(0,1,1,0) = 2
- i=2: (1,3,2,1)·(1,0,1,1) = 1+0+2+1 = 4
- i=3: (1,2,3,1)·(1,1,0,1) = 1+2+0+1 = 4
- i=4: (2,1,1,2)·(0,1,1,0) = 2
trace(A³) = 2 + 4 + 4 + 2 = 12.
**Triangles = 12/6 = 2** ✓ (namely {1,2,3} and {2,3,4}).

**S8.14** The line y = x + 2 has direction (1,1)/√2 and passes through (0, 2).

**Decompose:** translate the line to pass through the origin, reflect across y = x, translate back.
1. T₋: translate by (0, −2) → line becomes y = x
2. R: reflect across y = x → matrix [[0,1],[1,0]]
3. T₊: translate by (0, +2)

```
T₋ = [[1,0,0],[0,1,−2],[0,0,1]]
R  = [[0,1,0],[1,0,0],[0,0,1]]
T₊ = [[1,0,0],[0,1,2],[0,0,1]]
```
**R·T₋:**
Row 1 of R is (0,1,0) → picks row 2 of T₋ = (0, 1, −2)
Row 2 of R is (1,0,0) → picks row 1 of T₋ = (1, 0, 0)
Row 3 = (0,0,1)
```
R·T₋ = [[0, 1, −2], [1, 0, 0], [0, 0, 1]]
```
**T₊·(R·T₋):** T₊ adds 2 to the third column of row 2:
```
M = [[0, 1, −2],
     [1, 0,  2],
     [0, 0,  1]]
```
**Check:** the point (0, 2) is on the line and must be fixed: M(0,2,1)ᵀ = (2 − 2, 0 + 2, 1) = (0, 2) ✓
**Check:** (0, 0) should reflect to (−2, 2): M(0,0,1)ᵀ = (−2, 2, 1) ✓ — and indeed the midpoint of (0,0) and (−2,2) is (−1, 1), which satisfies y = x + 2 ✓

**S8.15** det K = 5(3) − 8(17) = 15 − 136 = −121. mod 26: −121 + 130 = **9**. gcd(9, 26) = 1 ✓
9⁻¹ mod 26 = 3 (since 27 ≡ 1).
adj K = [[3, −8], [−17, 5]] ≡ [[3, 18], [9, 5]] mod 26.
K⁻¹ = 3·[[3, 18], [9, 5]] = [[9, 54], [27, 15]] ≡ **[[9, 2], [1, 15]]** mod 26.

*Verify K⁻¹K:* [[9(5)+2(17), 9(8)+2(3)], [1(5)+15(17), 1(8)+15(3)]] = [[45+34, 72+6],[5+255, 8+45]] = [[79, 78],[260, 53]].
mod 26: 79 ≡ 1 ✓, 78 ≡ 0 ✓, 260 ≡ 0 ✓, 53 ≡ 1 ✓

**Decrypt "RGWT":** R=17, G=6, W=22, T=19. Blocks (17,6) and (22,19).

Block 1: K⁻¹(17,6)ᵀ = (9(17) + 2(6), 1(17) + 15(6)) = (153 + 12, 17 + 90) = (165, 107).
165 mod 26: 26(6) = 156 → **9** = J. 107 mod 26: 26(4) = 104 → **3** = D.

Block 2: K⁻¹(22,19)ᵀ = (9(22) + 2(19), 22 + 15(19)) = (198 + 38, 22 + 285) = (236, 307).
236 mod 26: 26(9) = 234 → **2** = C. 307 mod 26: 26(11) = 286 → **21** = V.

**Plaintext: "JDCV"**
*(Not a meaningful word — this illustrates that without knowing the correct key you cannot recognize success, and confirms the arithmetic rather than the semantics. Encrypting "JDCV" back with K should return "RGWT": K(9,3)ᵀ = (45+24, 153+9) = (69, 162); 69 mod 26 = 17 = R ✓; 162 mod 26 = 162 − 156 = 6 = G ✓)*

**S8.16** Column-stochastic means each column of P sums to 1, i.e. Σᵢ Pᵢⱼ = 1 for every j.

The j-th entry of the row vector 1ᵀP is Σᵢ 1·Pᵢⱼ = Σᵢ Pᵢⱼ = 1.

So **1ᵀP = 1ᵀ** ✓

Transposing: **Pᵀ1 = 1**, which says **1 is an eigenvector of Pᵀ with eigenvalue 1**.

Since a matrix and its transpose have the **same characteristic polynomial** (det(Pᵀ − λI) = det((P − λI)ᵀ) = det(P − λI)), they have the same eigenvalues. **Hence 1 is an eigenvalue of P.** ∎

*(Note: 1 is an eigen*value* of P, but the corresponding eigen*vector* of P is the steady-state q, not 1.)*

**S8.17** *Proof by induction on k.*

**Base case k = 1.** (A¹)ᵢⱼ = Aᵢⱼ, which is 1 if there is an edge i→j and 0 otherwise — exactly the number of walks of length 1 ✓

**Inductive step.** Assume (Aᵏ)ᵢⱼ = number of walks of length k from i to j.

Every walk of length k+1 from i to j consists of a walk of length k from i to some vertex l, followed by a single edge l→j. These decompositions are in bijection with such walks, and the choices for different l are disjoint. So

(number of walks of length k+1 from i to j) = Σ_l (walks of length k from i to l) × (edges from l to j)
= Σ_l (Aᵏ)ᵢ_l · A_lⱼ
= (Aᵏ · A)ᵢⱼ = (A^{k+1})ᵢⱼ ✓

By induction the claim holds for all k ≥ 1. ∎

**S8.18** Let L = D − A for a **connected** graph on n vertices.

**Step 1: 1 ∈ Nul(L).** Row i of L has dᵢ on the diagonal and −1 in each of the dᵢ positions of neighbours. Its sum is dᵢ − dᵢ = 0 ✓ So L1 = 0.

**Step 2: Nul(L) ⊆ span{1}.** The key identity is the **quadratic form**:

> xᵀLx = Σ_{(i,j) ∈ E} (xᵢ − xⱼ)²

*(Proof: xᵀDx = Σᵢdᵢxᵢ² and xᵀAx = 2Σ_{(i,j)∈E}xᵢxⱼ; subtracting and noting each vertex i appears in dᵢ edges gives the sum of squared differences.)*

If Lx = 0 then xᵀLx = 0, so **(xᵢ − xⱼ)² = 0 for every edge**, i.e. xᵢ = xⱼ for all adjacent i, j.

Since the graph is connected, any two vertices are joined by a path, and equality propagates along it. Hence **all coordinates of x are equal**, so x = c·1 for some scalar c.

**Therefore Nul(L) = span{1}, dim = 1, and rank(L) = n − 1** by rank–nullity ✓ ∎

*(For a graph with c components, the same argument gives dim Nul(L) = c, the indicator vectors of the components forming a basis — Example 8.4.)*

**S8.19** G = [I₃ | P] with P = [[1,1],[1,0],[0,1]] (k = 3, n = 5).

**Parity check matrix.** For a systematic code G = [I_k | P], the standard form is **H = [Pᵀ | I_{n−k}]** (over 𝔽₂, where −1 = 1):
```
H = [[1, 1, 0, 1, 0],
     [1, 0, 1, 0, 1]]
```
*Verify GHᵀ = 0:* row 1 of G is (1,0,0,1,1). Dot with row 1 of H: 1+0+0+1+0 = 2 ≡ 0 ✓ With row 2: 1+0+0+0+1 = 2 ≡ 0 ✓

**All 8 codewords** (c = xG for x ∈ 𝔽₂³):
| x | codeword c |
|---|---|
| 000 | 00000 |
| 100 | 10011 |
| 010 | 01010 |
| 001 | 00101 |
| 110 | 11001 |
| 101 | 10110 |
| 011 | 01111 |
| 111 | 11100 |

**Minimum distance.** For a linear code, d_min = the minimum **weight** (number of 1s) of a nonzero codeword.
Weights: 10011→3, 01010→2, 00101→2, 11001→3, 10110→3, 01111→4, 11100→3.

**d_min = 2.**

**Error handling.** A code with minimum distance d can:
- **detect** up to d − 1 = **1 error**
- **correct** up to ⌊(d−1)/2⌋ = ⌊1/2⌋ = **0 errors**

**Conclusion:** this code detects any single-bit error but **cannot correct any**. To correct one error you need d ≥ 3 (as Hamming(7,4) has).

*Consistency check via H: d_min equals the smallest number of columns of H that are linearly dependent. Columns of H: (1,1), (1,0), (0,1), (1,0), (0,1). Columns 2 and 4 are identical → two dependent columns → d_min = 2 ✓*

**S8.20** *Outline (Perron–Frobenius).*

Let P be **regular**: some power Pᵏ has all entries strictly positive.

**Properties used:**
1. **1 is an eigenvalue** (S8.16).
2. **All eigenvalues satisfy |λ| ≤ 1.** *Reason:* if Px = λx, look at the coordinate i with largest |xᵢ|. Then |λ||xᵢ| = |Σⱼ PᵢⱼX...| — using row-stochasticity of Pᵀ, or more carefully in the ‖·‖₁ norm: P preserves the sum of entries and is non-negative, so ‖Px‖₁ ≤ ‖x‖₁, giving the spectral radius ≤ 1.
3. **Perron's theorem for positive matrices:** if all entries of a matrix M are strictly positive, then its spectral radius r is a **simple** eigenvalue (algebraic multiplicity 1), its eigenvector can be chosen with **all entries positive**, and every other eigenvalue has modulus **strictly less than** r.
4. Applying (3) to Pᵏ (which is positive by regularity) gives: 1 is a simple eigenvalue of Pᵏ, so the eigenvalue 1 of P is simple, and every other eigenvalue of P satisfies |λ| < 1.

**Consequences.**
- **Existence and uniqueness:** eigenvalue 1 has a one-dimensional eigenspace, containing exactly one vector with entries summing to 1. Call it q.
- **Positivity:** q has all entries > 0 (from Perron).
- **Convergence:** decompose x₀ = q + (components in the other eigenspaces). Applying Pᵏ leaves q fixed and shrinks the rest by factors |λ|ᵏ → 0. Hence **Pᵏx₀ → q** for every probability vector x₀ ✓ ∎

*The rate of convergence is governed by |λ₂|, the second-largest eigenvalue modulus — called the* **spectral gap**. *A large gap means fast mixing. This is precisely the quantity that determines how many iterations PageRank needs.*

---
# PART II — UNIT 2: EIGEN ANALYSIS AND MATRIX DECOMPOSITION

---

# Chapter 9 — Eigenvalues, Eigenvectors and the Characteristic Equation

---

## 9.1 Explain Like I'm Five

A matrix takes an arrow and usually does two things to it: **turns it** and **stretches it**.

But some special arrows refuse to turn. Feed them to the matrix and they come back pointing in exactly the same direction — only longer, shorter, or flipped backwards. Those stubborn arrows are the **eigenvectors**, and the amount they got stretched by is the **eigenvalue**.

```
A v = λ v
```

"Applying the matrix" and "multiplying by a single number" do the same thing to v. That's the whole definition.

**Why does anyone care?** Because if you can find enough of these stubborn directions to describe all of space, then the matrix stops being complicated. In those directions, the matrix is *just multiplication by a number*. Complicated becomes simple. Applying the matrix a hundred times becomes "raise each number to the hundredth power" instead of doing a hundred matrix multiplications.

**How do you find them?** Rewrite `Av = λv` as `Av − λv = 0`, i.e. `(A − λI)v = 0`. We want a **nonzero** v solving this, which means the matrix `A − λI` must squash something to zero — it must be singular. And singular means:

> **det(A − λI) = 0**

That's the **characteristic equation**. Solve it for λ, and you have the eigenvalues. Then for each λ, find the null space of `A − λI` and you have the eigenvectors.

**A subtlety about "how many".** An eigenvalue can show up more than once as a root of the polynomial (its **algebraic multiplicity**), but the space of eigenvectors for it may be smaller than that (its **geometric multiplicity**). When they don't match, the matrix is "defective" and can't be fully simplified. Understanding when they match is the whole content of Chapter 10.

---

## 9.2 The Formal Theory

### 9.2.1 Definitions

> **Definition.** Let A be n×n. A scalar λ is an **eigenvalue** of A if there exists a **nonzero** vector v with
> **Av = λv**.
> Such a v is an **eigenvector** corresponding to λ.

**Why must v be nonzero?** If v = 0 were allowed, then A0 = λ0 holds for *every* λ, and every scalar would be an eigenvalue. The definition would be vacuous.

**Eigenvalues may be zero**, however. λ = 0 is an eigenvalue ⟺ Av = 0 for some v ≠ 0 ⟺ Nul(A) ≠ {0} ⟺ **A is singular**.

### 9.2.2 Eigenspaces

> **Definition.** For an eigenvalue λ of A, the **eigenspace** is
> **E_λ = Nul(A − λI) = {v : Av = λv}**

E_λ contains all eigenvectors for λ **together with the zero vector**. That inclusion of 0 is what makes E_λ a genuine subspace (a subspace must contain 0).

*Verification that it is a subspace:* if Av = λv and Aw = λw then A(cv + dw) = cλv + dλw = λ(cv + dw) ✓

**Key facts:**
- Eigenspaces for **distinct** eigenvalues intersect only at 0. (If v ∈ E_λ ∩ E_μ with λ ≠ μ, then λv = μv → (λ−μ)v = 0 → v = 0.)
- Geometrically E_λ is a line, plane, hyperplane, or all of ℝⁿ — the set of directions A doesn't rotate.

### 9.2.3 The Characteristic Equation

> λ is an eigenvalue of A ⟺ (A − λI) is singular ⟺ **det(A − λI) = 0**

> **Definition.** p(λ) = det(A − λI) is the **characteristic polynomial**. It is a polynomial of degree exactly n in λ, with leading term (−1)ⁿλⁿ. The equation p(λ) = 0 is the **characteristic equation**.

Some texts use det(λI − A), which gives the monic version λⁿ − ... . Roots are identical; only an overall sign may differ.

**For 2×2:** p(λ) = λ² − (tr A)λ + det A, where tr A = a₁₁ + a₂₂.

**For 3×3:** p(λ) = −λ³ + (tr A)λ² − (M₁₁ + M₂₂ + M₃₃)λ + det A, where the middle coefficient is the sum of the three **principal 2×2 minors**.

### 9.2.4 Multiplicities

> **Algebraic multiplicity** AM(λ) = the multiplicity of λ as a root of the characteristic polynomial.
> **Geometric multiplicity** GM(λ) = dim E_λ = dim Nul(A − λI) = n − rank(A − λI).

> **Theorem 9.1.** For every eigenvalue λ:
> **1 ≤ GM(λ) ≤ AM(λ) ≤ n**, and **Σ AM(λᵢ) = n** (over ℂ, counting all roots).

The lower bound GM ≥ 1 holds because an eigenvalue always has at least one eigenvector by definition.

> **Definition.** A is **defective** if GM(λ) < AM(λ) for some λ. Otherwise A is **non-defective** (equivalently, **diagonalizable**).

**Standard example of defect:** A = [[3, 1], [0, 3]]. Characteristic polynomial (3−λ)², so AM(3) = 2. But A − 3I = [[0,1],[0,0]] has rank 1, so GM(3) = 2 − 1 = 1 < 2. **Defective.**

### 9.2.5 Properties of Eigenvalues

Let A be n×n with eigenvalues λ₁, ..., λₙ (with multiplicity).

| Property | Statement |
|---|---|
| **Trace** | λ₁ + λ₂ + ... + λₙ = **tr(A)** |
| **Determinant** | λ₁λ₂···λₙ = **det(A)** |
| **Triangular** | eigenvalues of a triangular matrix are its **diagonal entries** |
| **Powers** | eigenvalues of Aᵏ are λᵢᵏ (same eigenvectors) |
| **Inverse** | if A invertible, eigenvalues of A⁻¹ are 1/λᵢ (same eigenvectors) |
| **Shift** | eigenvalues of A + cI are λᵢ + c (same eigenvectors) |
| **Scalar** | eigenvalues of cA are cλᵢ |
| **Transpose** | A and Aᵀ have the **same eigenvalues** (but generally different eigenvectors) |
| **Polynomial** | if q is a polynomial, eigenvalues of q(A) are q(λᵢ) |
| **Similarity** | similar matrices (B = P⁻¹AP) have the same characteristic polynomial, hence same eigenvalues |
| **Products** | AB and BA have the same **nonzero** eigenvalues |

**Warning:** eigenvalues of A + B are **not** λᵢ(A) + λᵢ(B) in general, and eigenvalues of AB are not products of eigenvalues. Only the special cases above work.

> **Theorem 9.2 (Independence).** Eigenvectors corresponding to **distinct** eigenvalues are linearly independent.

*Proof sketch:* Suppose {v₁,...,v_p} is a minimal dependent set of eigenvectors with distinct eigenvalues. Write v_p = Σ_{i<p} cᵢvᵢ. Apply A: λ_p v_p = Σcᵢλᵢvᵢ. Also λ_p v_p = Σcᵢλ_p vᵢ. Subtracting: Σcᵢ(λᵢ − λ_p)vᵢ = 0 with the first p−1 vectors independent (by minimality), so cᵢ(λᵢ − λ_p) = 0 for each i, forcing cᵢ = 0 since λᵢ ≠ λ_p. Then v_p = 0, contradicting v_p ≠ 0. ∎

**Corollary.** If an n×n matrix has **n distinct eigenvalues**, it is diagonalizable.

### 9.2.6 Complex Eigenvalues

A real matrix can have complex eigenvalues, which occur in **conjugate pairs** λ = a ± bi with conjugate eigenvectors.

**Example:** the rotation matrix R = [[0, −1], [1, 0]] has p(λ) = λ² + 1, eigenvalues ±i. Geometrically obvious: a 90° rotation leaves **no real direction** unchanged.

For λ = a + bi with eigenvector v, the real 2×2 block equivalent is

> C = [[a, −b], [b, a]] = r·[[cos φ, −sin φ], [sin φ, cos φ]], r = |λ| = √(a²+b²)

So complex eigenvalues encode **rotation by angle φ = arg(λ) combined with scaling by r = |λ|**. In dynamical systems, |λ| < 1 gives an inward spiral, |λ| > 1 an outward spiral, |λ| = 1 a closed orbit.

### 9.2.7 The Cayley–Hamilton Theorem

> **Theorem 9.3 (Cayley–Hamilton).** Every square matrix satisfies its own characteristic equation: if p(λ) = det(A − λI), then **p(A) = 0** (the zero matrix).

**Uses:**
1. Express A⁻¹ as a polynomial in A.
2. Reduce high powers of A to combinations of I, A, ..., A^{n−1}.

**Example.** For 2×2, p(λ) = λ² − (tr A)λ + det A, so
> **A² = (tr A)·A − (det A)·I**
and if det A ≠ 0,
> **A⁻¹ = (1/det A)[(tr A)I − A]**

### 9.2.8 Computing Eigenvalues in Practice

Root-finding on the characteristic polynomial is **numerically disastrous** for n beyond about 4 — the roots of a polynomial are extremely sensitive to its coefficients. Real software uses:

- **Power iteration:** x_{k+1} = Ax_k/‖Ax_k‖ converges to the dominant eigenvector. Simple, and the basis of PageRank.
- **Inverse iteration** with shifts: finds eigenvalues near a target.
- **The QR algorithm:** repeatedly factor A_k = Q_kR_k and set A_{k+1} = R_kQ_k. This converges to (quasi-)triangular form, revealing all eigenvalues. Note A_{k+1} = Q_kᵀA_kQ_k is similar to A_k, so the eigenvalues are preserved throughout. This is what LAPACK actually runs.

---

## 9.3 Solved Examples

### Example 9.1 — [Easy] 2×2 eigenvalues and eigenvectors

Find the eigenvalues and eigenvectors of A = [[4, 1], [2, 3]].

**Solution.**
p(λ) = det[[4−λ, 1], [2, 3−λ]] = (4−λ)(3−λ) − 2 = λ² − 7λ + 12 − 2 = λ² − 7λ + 10 = (λ−5)(λ−2).

**Eigenvalues: λ₁ = 5, λ₂ = 2.**

*Check:* tr A = 7 = 5 + 2 ✓; det A = 12 − 2 = 10 = 5 × 2 ✓

**For λ = 5:** A − 5I = [[−1, 1], [2, −2]]. Row reduce → [[1, −1], [0, 0]].
So v₁ = v₂; **eigenvector (1, 1)**.

**For λ = 2:** A − 2I = [[2, 1], [2, 1]] → [[2, 1], [0, 0]].
So 2v₁ + v₂ = 0 → **eigenvector (1, −2)**.

**Verify:** A(1,1)ᵀ = (5, 5) = 5(1,1) ✓; A(1,−2)ᵀ = (4−2, 2−6) = (2, −4) = 2(1,−2) ✓

---

### Example 9.2 — [Easy] Triangular matrix

Find the eigenvalues of A = [[2, 7, −3], [0, 5, 1], [0, 0, −4]].

**Solution.** A is **upper triangular**, so det(A − λI) is also triangular with diagonal (2−λ, 5−λ, −4−λ):
p(λ) = (2−λ)(5−λ)(−4−λ).

**Eigenvalues: 2, 5, −4** — just the diagonal entries.

*(Three distinct eigenvalues ⟹ A is diagonalizable, by the corollary to Theorem 9.2.)*

---

### Example 9.3 — [Medium] 3×3 with a repeated eigenvalue

Find all eigenvalues, eigenvectors, and the multiplicities for
A = [[4, −1, 6], [2, 1, 6], [2, −1, 8]].

**Solution.**
p(λ) = det [[4−λ, −1, 6], [2, 1−λ, 6], [2, −1, 8−λ]]

Expand along row 1:
= (4−λ)[(1−λ)(8−λ) + 6] + 1[2(8−λ) − 12] + 6[−2 − 2(1−λ)]
= (4−λ)[8 − 9λ + λ² + 6] + [16 − 2λ − 12] + 6[−2 − 2 + 2λ]
= (4−λ)(λ² − 9λ + 14) + (4 − 2λ) + (12λ − 24)
= (4−λ)(λ−2)(λ−7) + 10λ − 20
= (4−λ)(λ−2)(λ−7) + 10(λ−2)
= (λ−2)[(4−λ)(λ−7) + 10]
= (λ−2)[4λ − 28 − λ² + 7λ + 10]
= (λ−2)(−λ² + 11λ − 18)
= −(λ−2)(λ² − 11λ + 18)
= −(λ−2)(λ−2)(λ−9)
= **−(λ−2)²(λ−9)**

**Eigenvalues: λ = 2 (AM = 2), λ = 9 (AM = 1).**

*Check:* tr A = 4 + 1 + 8 = 13 = 2 + 2 + 9 ✓

**Eigenspace for λ = 2.** A − 2I = [[2, −1, 6], [2, −1, 6], [2, −1, 6]].
All rows identical → rank 1 → **GM(2) = 3 − 1 = 2**.
Solve 2x − y + 6z = 0 → y = 2x + 6z. Free: x, z.
**Basis: {(1, 2, 0), (0, 6, −1)}** *(taking x=1,z=0 and x=0,z=−1)*. This is a **plane**.

**Eigenspace for λ = 9.** A − 9I = [[−5, −1, 6], [2, −8, 6], [2, −1, −1]].
`R₂ → R₂ − R₃`: (0, −7, 7) → simplify to (0, 1, −1) → **y = z**.
From R₃: 2x − y − z = 0 → 2x = y + z = 2z → x = z.
**Eigenvector: (1, 1, 1).** GM(9) = 1 = AM(9) ✓

**Summary:** AM = GM for both eigenvalues (2 = 2 and 1 = 1), so **A is diagonalizable**.

---

### Example 9.4 — [Medium] A defective matrix

Show that A = [[5, 1, 0], [0, 5, 1], [0, 0, 5]] is defective.

**Solution.** A is upper triangular → p(λ) = (5−λ)³, so **λ = 5 with AM = 3**.

A − 5I = [[0,1,0],[0,0,1],[0,0,0]]. This has **rank 2** (rows 1 and 2 are independent).

**GM(5) = 3 − 2 = 1.**

Since GM(5) = 1 < 3 = AM(5), **A is defective** and not diagonalizable. ✓

The single eigenvector direction: (A−5I)v = 0 requires v₂ = 0 and v₃ = 0, leaving **v = (1, 0, 0)** as the only eigendirection.

*(This is a Jordan block — the canonical example of maximal defect.)*

---

### Example 9.5 — [Medium] Complex eigenvalues

Find the eigenvalues and eigenvectors of A = [[1, −2], [1, 3]] and describe the geometric action.

**Solution.**
p(λ) = (1−λ)(3−λ) + 2 = λ² − 4λ + 5.
λ = [4 ± √(16 − 20)]/2 = [4 ± 2i]/2 = **2 ± i**.

**For λ = 2 + i:** A − (2+i)I = [[−1−i, −2], [1, 1−i]].
From the second row: v₁ + (1−i)v₂ = 0 → v₁ = −(1−i)v₂.
Take v₂ = 1: **v = (−1+i, 1)**.

*Check with row 1:* (−1−i)(−1+i) + (−2)(1) = (1 − i + i − i²) − 2 = (1 + 1) − 2 = 0 ✓

**For λ = 2 − i:** conjugate eigenvector **v̄ = (−1−i, 1)**.

**Geometric description.** |λ| = √(4 + 1) = **√5**, and arg(λ) = arctan(1/2) ≈ **26.57°**.

So A acts (in a suitable real basis) as a **rotation by about 26.57° combined with a scaling by √5 ≈ 2.236**. Since |λ| > 1, iterating A sends points **spiralling outward**.

---

### Example 9.6 — [Hard] Eigenvalue properties chained

Let A be 3×3 with eigenvalues 1, 2, −3. Compute:
(a) det A, (b) tr A, (c) eigenvalues of A², (d) eigenvalues of A⁻¹, (e) eigenvalues of A + 4I, (f) eigenvalues of 2A³ − A + I, (g) det(A² + 2A).

**Solution.**
(a) det A = 1 × 2 × (−3) = **−6**
(b) tr A = 1 + 2 − 3 = **0**
(c) eigenvalues of A²: 1, 4, 9 → **{1, 4, 9}**
(d) eigenvalues of A⁻¹: **{1, 1/2, −1/3}**
(e) eigenvalues of A + 4I: **{5, 6, 1}**
(f) apply q(λ) = 2λ³ − λ + 1:
- q(1) = 2 − 1 + 1 = 2
- q(2) = 16 − 2 + 1 = 15
- q(−3) = −54 + 3 + 1 = −50
→ **{2, 15, −50}**
(g) A² + 2A = q(A) with q(λ) = λ² + 2λ. Eigenvalues: q(1) = 3, q(2) = 8, q(−3) = 9 − 6 = 3.
det = 3 × 8 × 3 = **72**

---

### Example 9.7 — [Hard] Cayley–Hamilton in action

For A = [[1, 2], [3, 4]], verify Cayley–Hamilton, then use it to find A⁻¹ and A⁴.

**Solution.**
tr A = 5, det A = 4 − 6 = −2. So **p(λ) = λ² − 5λ − 2**.

**Verify p(A) = 0.**
A² = [[1,2],[3,4]]² = [[1+6, 2+8], [3+12, 6+16]] = [[7, 10], [15, 22]].
5A = [[5, 10], [15, 20]]. 2I = [[2, 0], [0, 2]].
A² − 5A − 2I = [[7−5−2, 10−10−0], [15−15−0, 22−20−2]] = [[0,0],[0,0]] ✓

**Inverse.** From A² − 5A − 2I = 0: A² − 5A = 2I → A(A − 5I) = 2I → A⁻¹ = (1/2)(A − 5I).
A − 5I = [[−4, 2], [3, −1]].
**A⁻¹ = (1/2)[[−4, 2], [3, −1]] = [[−2, 1], [1.5, −0.5]]**
*Check against the 2×2 formula:* (1/−2)[[4, −2], [−3, 1]] = [[−2, 1], [1.5, −0.5]] ✓

**A⁴ via reduction.** From A² = 5A + 2I:
A³ = A·A² = A(5A + 2I) = 5A² + 2A = 5(5A + 2I) + 2A = 27A + 10I
A⁴ = A·A³ = A(27A + 10I) = 27A² + 10A = 27(5A + 2I) + 10A = **145A + 54I**

**A⁴ = 145[[1,2],[3,4]] + 54I = [[145+54, 290], [435, 580+54]] = [[199, 290], [435, 634]]**

*Verify directly:* A⁴ = (A²)² = [[7,10],[15,22]]² = [[49+150, 70+220], [105+330, 150+484]] = [[199, 290], [435, 634]] ✓

*(Notice how Cayley–Hamilton turned a matrix power into a scalar recursion — the same trick makes computing A^1000 feasible.)*

---

### Example 9.8 — [Very Hard] Eigenvalues of a rank-one perturbation

Let J be the n×n all-ones matrix. Find all eigenvalues and eigenvectors of J, and then of A = aI + bJ.

**Solution.**

**Eigenvalues of J.** Note J = 11ᵀ where 1 = (1,1,...,1)ᵀ. So rank(J) = 1.

**λ = n:** J1 = 11ᵀ1 = 1(n) = n·1. So **1 is an eigenvector with λ = n** ✓

**λ = 0:** rank(J) = 1 means nullity(J) = n − 1, so **λ = 0 has GM = n−1**. Its eigenspace is
Nul(J) = {x : 1ᵀx = 0} = the hyperplane of vectors whose entries sum to zero.
A basis: {e₁ − e₂, e₂ − e₃, ..., e_{n−1} − eₙ}.

**Total multiplicity:** 1 + (n−1) = n ✓ so these are all the eigenvalues.

**Check:** tr J = n = n + 0(n−1) ✓ ; det J = 0 (since n ≥ 2 gives repeated rows) = n · 0^{n−1} ✓

**Eigenvalues of A = aI + bJ.** By the shift property, eigenvalues of bJ are bn and 0 (multiplicity n−1); adding aI shifts everything by a:

> **Eigenvalues of A: a + bn (once, eigenvector 1), and a (multiplicity n−1)**

**Consequences.**
- **det A = (a + bn)·a^{n−1}** — this **rederives S7.17's formula** for the "a on the diagonal, b elsewhere" determinant! (There, the matrix was aI + b(J − I) = (a−b)I + bJ, giving det = (a − b + bn)(a−b)^{n−1} = [a + (n−1)b](a−b)^{n−1} ✓ exactly matching.)
- **A is always diagonalizable**, since GM = AM for both eigenvalues (A is symmetric — see Chapter 11).
- A is singular ⟺ a = 0 or a = −bn.

---

### Example 9.9 — [Very Hard] AB and BA share nonzero eigenvalues

Prove that for any n×n matrices A and B, AB and BA have the same eigenvalues (including multiplicities). Then show the "nonzero" caveat is essential for non-square matrices.

**Solution.**

**Case 1: A invertible.** Then BA = A⁻¹(AB)A, so AB and BA are **similar**, hence have identical characteristic polynomials and identical eigenvalues with multiplicities ✓

**Case 2: A singular.** Use a continuity/perturbation argument. The matrix A + εI is invertible for all but finitely many ε (namely ε ≠ −λᵢ(A)). For such ε, by Case 1:

det((A + εI)B − λI) = det(B(A + εI) − λI)

Both sides are **polynomials in ε** (and λ). Two polynomials agreeing at infinitely many values of ε are identical, so the equality holds at ε = 0 too:

det(AB − λI) = det(BA − λI) ✓ ∎

**Direct proof of the nonzero-eigenvalue claim.** If ABx = λx with λ ≠ 0 and x ≠ 0, set y = Bx. Then
- y ≠ 0, because if y = 0 then λx = ABx = A0 = 0, forcing x = 0 (as λ ≠ 0) — contradiction.
- BA y = BABx = B(λx) = λ(Bx) = λy ✓

So y is an eigenvector of BA with the same eigenvalue λ. The map x ↦ Bx is a bijection between the corresponding eigenspaces (with inverse y ↦ (1/λ)Ay), so multiplicities match ✓

**Non-square case.** Let A be m×n and B be n×m with m ≠ n. Then AB is m×m and BA is n×n — **different sizes**, so they cannot have the same characteristic polynomial.

**Example.** A = [[1, 0]] (1×2), B = [[1], [0]] (2×1).
- AB = [[1]] — eigenvalue **1**.
- BA = [[1, 0], [0, 0]] — eigenvalues **1 and 0**.

The **nonzero** eigenvalues coincide (both have exactly one eigenvalue 1), but BA carries an extra 0 of multiplicity n − m = 1.

**General relation:** det(λI_m − AB)·λⁿ = det(λI_n − BA)·λᵐ. The larger matrix simply has extra zero eigenvalues. ∎

---

## 9.4 Practice Numericals — Chapter 9

**[Easy]**

**P9.1** Find the eigenvalues of [[3, 0], [0, −2]] and [[6, −1], [2, 3]].

**P9.2** Is (1, 2) an eigenvector of [[5, 1], [2, 4]]? If so, find the eigenvalue.

**P9.3** Find the eigenvalues of the triangular matrix [[1, 5, 9], [0, 2, 6], [0, 0, 3]].

**P9.4** If the eigenvalues of a 3×3 matrix are 2, −1, 4, find its trace and determinant.

**P9.5** Explain in one sentence why λ = 0 being an eigenvalue means A is singular.

**[Medium]**

**P9.6** Find eigenvalues and eigenvectors of A = [[2, 3], [3, 2]].

**P9.7** Find the eigenvalues and a basis for each eigenspace of A = [[1, 0, 0], [0, 2, 1], [0, 1, 2]].

**P9.8** Determine whether A = [[2, 1], [0, 2]] is diagonalizable. Give AM and GM.

**P9.9** Find the eigenvalues of A = [[0, −1], [1, 0]] and interpret geometrically.

**P9.10** If A has eigenvalue 3 with eigenvector v, what are the eigenvalues and eigenvectors of A² − 2A + 5I?

**P9.11** Verify the Cayley–Hamilton theorem for A = [[2, 1], [1, 2]] and use it to compute A⁻¹.

**[Hard]**

**P9.12** Find all eigenvalues, AM, GM for A = [[3, 1, 0], [0, 3, 0], [0, 0, 4]]. Is A diagonalizable?

**P9.13** Find the characteristic polynomial and eigenvalues of A = [[1, 1, 1], [1, 1, 1], [1, 1, 1]] using the structure of the matrix.

**P9.14** Show that if λ is an eigenvalue of an **orthogonal** matrix Q, then |λ| = 1.

**P9.15** Let A be a 3×3 matrix with A³ = I and A ≠ I. What are the possible eigenvalues of A? Must A be diagonalizable over ℂ?

**P9.16** Find the eigenvalues of the 4×4 matrix with 2s on the diagonal and 1s on the sub- and super-diagonal (a tridiagonal Toeplitz matrix). [Hint: the general formula is λ_k = a + 2√(bc)·cos(kπ/(n+1)).]

**P9.17** Prove that if A is nilpotent (Aᵏ = 0 for some k), then every eigenvalue of A is 0, and A is diagonalizable **only if** A = 0.

**[Very Hard]**

**P9.18** Let A be n×n with all row sums equal to s. Prove that s is an eigenvalue. Find the corresponding eigenvector. Does the same hold for column sums?

**P9.19** Prove that a matrix and its transpose have the same eigenvalues but may have different eigenvectors, and give an explicit 2×2 example where the eigenvectors differ.

**P9.20** Let A be a real 3×3 matrix. Prove that A must have at least one real eigenvalue. Generalize to odd n, and show it fails for even n.

**P9.21** **(Gershgorin's circle theorem.)** State and prove that every eigenvalue of A lies in at least one of the discs
Dᵢ = {z ∈ ℂ : |z − aᵢᵢ| ≤ Σ_{j≠i}|aᵢⱼ|}.
Apply it to A = [[10, 1, 0], [1, 5, 1], [0, 1, 2]] to bound the eigenvalues, and verify that A is invertible without computing det A.

---

## 9.5 Solutions to Chapter 9 Practice

**S9.1** Diagonal → eigenvalues **3, −2**.
For [[6,−1],[2,3]]: p(λ) = λ² − 9λ + (18 + 2) = λ² − 9λ + 20 = (λ−4)(λ−5). **Eigenvalues 4, 5.**

**S9.2** A(1,2)ᵀ = (5 + 2, 2 + 8) = (7, 10). Is (7, 10) = λ(1, 2)? That needs λ = 7 and λ = 5 — contradiction.
**No, not an eigenvector.**

**S9.3** Upper triangular → **eigenvalues 1, 2, 3**.

**S9.4** trace = 2 − 1 + 4 = **5**. det = 2(−1)(4) = **−8**.

**S9.5** λ = 0 means Av = 0 for some v ≠ 0, so Nul(A) ≠ {0}, so A cannot be invertible (IMT part d).

**S9.6** p(λ) = (2−λ)² − 9 = λ² − 4λ − 5 = (λ−5)(λ+1). **λ = 5, −1.**
λ=5: A − 5I = [[−3,3],[3,−3]] → v₁ = v₂ → **(1, 1)**.
λ=−1: A + I = [[3,3],[3,3]] → v₁ = −v₂ → **(1, −1)**.
*(Note the eigenvectors are orthogonal — A is symmetric, see Chapter 11.)*

**S9.7** Block structure: [1] ⊕ [[2,1],[1,2]].
From the 1×1 block: **λ = 1** with eigenvector **(1, 0, 0)**.
From the 2×2 block (as in S9.6 shifted): eigenvalues 2 ± 1 = **3 and 1**.
λ=3: (0, 1, 1). λ=1 (from the block): (0, 1, −1).

**Eigenvalues: λ = 1 (AM = 2), λ = 3 (AM = 1).**
**E₁ basis: {(1,0,0), (0,1,−1)}** — GM = 2 ✓
**E₃ basis: {(0,1,1)}** — GM = 1 ✓
Diagonalizable ✓

**S9.8** p(λ) = (2−λ)², **λ = 2 with AM = 2**.
A − 2I = [[0,1],[0,0]], rank 1 → **GM = 2 − 1 = 1**.
GM < AM → **not diagonalizable (defective)**.

**S9.9** p(λ) = λ² + 1 → **λ = ±i**. No real eigenvalues.
**Geometric interpretation:** A is rotation by 90°, which leaves **no real direction** unchanged — every arrow gets turned. |λ| = 1 means lengths are preserved.

**S9.10** Apply q(λ) = λ² − 2λ + 5: q(3) = 9 − 6 + 5 = **8**.
**Eigenvalue 8, with the same eigenvector v.** *(Polynomials in A preserve eigenvectors.)*

**S9.11** tr = 4, det = 4 − 1 = 3 → p(λ) = λ² − 4λ + 3.
A² = [[4+1, 2+2],[2+2, 1+4]] = [[5, 4], [4, 5]].
A² − 4A + 3I = [[5−8+3, 4−4], [4−4, 5−8+3]] = [[0,0],[0,0]] ✓
From A² − 4A = −3I: A(A − 4I) = −3I → **A⁻¹ = −(1/3)(A − 4I) = (1/3)(4I − A) = (1/3)[[2, −1], [−1, 2]]**.
*Check: (1/3)[[2,−1],[−1,2]]·[[2,1],[1,2]] = (1/3)[[4−1, 2−2],[−2+2, −1+4]] = (1/3)[[3,0],[0,3]] = I ✓*

**S9.12** Triangular → p(λ) = (3−λ)²(4−λ). **λ = 3 (AM 2), λ = 4 (AM 1).**
A − 3I = [[0,1,0],[0,0,0],[0,0,1]] → rank 2 → **GM(3) = 1**.
A − 4I = [[−1,1,0],[0,−1,0],[0,0,0]] → rank 2 → **GM(4) = 1** ✓ = AM.
Since GM(3) = 1 < 2 = AM(3), **A is NOT diagonalizable**.

**S9.13** A = J (the 3×3 all-ones matrix). By Example 9.8 with n = 3:
**Eigenvalues: 3 (AM 1, eigenvector (1,1,1)) and 0 (AM = GM = 2).**
p(λ) = −λ²(λ − 3), or equivalently λ²(3 − λ) up to sign.
*Check: tr = 3 ✓, det = 0 ✓, rank = 1 so nullity = 2 ✓*

**S9.14** Let Qv = λv with v ≠ 0. Since Q is orthogonal, it preserves length:
‖Qv‖ = ‖v‖.
But ‖Qv‖ = ‖λv‖ = |λ|‖v‖.
So |λ|‖v‖ = ‖v‖, and ‖v‖ ≠ 0, giving **|λ| = 1** ✓ ∎
*(This holds for complex eigenvalues too, with the Hermitian norm. So all eigenvalues of an orthogonal matrix lie on the unit circle.)*

**S9.15** A³ = I means every eigenvalue satisfies λ³ = 1, so λ ∈ {1, ω, ω²} where ω = e^{2πi/3}.

Since A is real, non-real eigenvalues come in conjugate pairs. With n = 3 the possibilities are:
- **{1, 1, 1}:** then A would satisfy... if A were diagonalizable it would be I, excluded. A non-diagonalizable matrix with all eigenvalues 1 satisfies (A−I)³ = 0 but then A³ = I forces A = I (the Jordan block J₃(1) has J³ ≠ I). So this case gives only A = I, excluded.
- **{1, ω, ω²}:** three distinct eigenvalues ✓ This is the general case, e.g. a rotation by 120°.

**Answer: eigenvalues are {1, ω, ω²} with ω = e^{2πi/3}.**

**Must A be diagonalizable?** **Yes.** The polynomial x³ − 1 annihilates A, and x³ − 1 = (x−1)(x−ω)(x−ω²) has **distinct roots**. A matrix annihilated by a polynomial with distinct roots is always diagonalizable (its minimal polynomial divides that polynomial, hence also has distinct roots). ∎

**S9.16** Here a = 2 (diagonal), b = c = 1 (off-diagonals), n = 4.
λ_k = 2 + 2√(1·1)·cos(kπ/5) = **2 + 2cos(kπ/5)**, k = 1, 2, 3, 4.

- cos(π/5) = (1+√5)/4 ≈ 0.8090 → λ₁ ≈ **3.618**
- cos(2π/5) ≈ 0.3090 → λ₂ ≈ **2.618**
- cos(3π/5) ≈ −0.3090 → λ₃ ≈ **1.382**
- cos(4π/5) ≈ −0.8090 → λ₄ ≈ **0.382**

*Check trace:* sum = 8 + 2(0.809 + 0.309 − 0.309 − 0.809) = 8 + 0 = 8 = 4 × 2 ✓
*All eigenvalues are positive, so this matrix is positive definite (Chapter 11).*

**S9.17** Let Av = λv with v ≠ 0. Then Aᵏv = λᵏv. But Aᵏ = 0, so λᵏv = 0, and since v ≠ 0, **λᵏ = 0 → λ = 0** ✓

So all eigenvalues are 0, and the characteristic polynomial is (−1)ⁿλⁿ.

**Diagonalizability.** If A were diagonalizable, then A = PDP⁻¹ with D containing all the eigenvalues, i.e. **D = 0**. Then A = P·0·P⁻¹ = **0**.

So a nilpotent matrix is diagonalizable **only when it is the zero matrix** ✓ ∎
*(Every nonzero nilpotent matrix is maximally defective — GM < AM always.)*

**S9.18** Let the row sums all equal s. Consider the vector **1 = (1, 1, ..., 1)ᵀ**.

The i-th entry of A1 is Σⱼ aᵢⱼ = s. So **A1 = s·1** ✓

Hence **s is an eigenvalue with eigenvector 1** ∎

**Column sums.** If all **column** sums equal s, then all row sums of Aᵀ equal s, so s is an eigenvalue of Aᵀ. Since A and Aᵀ have the same eigenvalues, **s is still an eigenvalue of A** — but the eigenvector is generally **not** 1.

*Example:* A = [[0, 2], [1, 1]] has column sums 1 and 3 — not constant. Try A = [[0, 1], [1, 0]]... Instead take A = [[0.5, 0.8],[0.5, 0.2]]: column sums both 1, so λ = 1 is an eigenvalue. But A1 = (1.3, 0.7) ≠ 1. The eigenvector for λ=1 is the steady state (8/13, 5/13) ✓

**S9.19** **Same eigenvalues.** det(Aᵀ − λI) = det((A − λI)ᵀ) = det(A − λI) (property 5 of determinants). So A and Aᵀ have **identical characteristic polynomials**, hence identical eigenvalues with identical algebraic multiplicities ✓

*(Geometric multiplicities also match, since rank(Aᵀ − λI) = rank(A − λI).)*

**Example with different eigenvectors.** A = [[1, 1], [0, 2]].
Eigenvalues: 1, 2 (triangular).
- For A, λ=1: (A−I) = [[0,1],[0,1]] → v₂ = 0 → eigenvector **(1, 0)**.
- For Aᵀ = [[1, 0], [1, 2]], λ=1: (Aᵀ−I) = [[0,0],[1,1]] → v₁ = −v₂ → eigenvector **(1, −1)**.

**Different eigenvectors, same eigenvalue** ✓ ∎

*(In general the eigenvectors of Aᵀ are the "left eigenvectors" of A: wᵀA = λwᵀ.)*

**S9.20** The characteristic polynomial p(λ) = det(A − λI) is a **real** polynomial of degree 3 (odd).

As λ → +∞, p(λ) → −∞ (leading term −λ³). As λ → −∞, p(λ) → +∞.

Since p is continuous and takes both positive and negative values, by the **Intermediate Value Theorem** it has a real root ✓

**Therefore A has at least one real eigenvalue.** ∎

**Generalization to odd n:** identical argument — a real polynomial of odd degree always has a real root, since non-real roots of real polynomials come in conjugate pairs, so the number of non-real roots is even and cannot account for all n roots when n is odd.

**Failure for even n:** the rotation matrix [[0, −1], [1, 0]] has p(λ) = λ² + 1 with **no real roots** — eigenvalues ±i. More generally, a rotation in ℝ² (by an angle that is not a multiple of π) has no real eigenvalue at all.

**S9.21**

**Statement (Gershgorin).** Let Rᵢ = Σ_{j≠i}|aᵢⱼ| (the i-th off-diagonal row sum). Every eigenvalue λ of A lies in the union of the discs
Dᵢ = {z : |z − aᵢᵢ| ≤ Rᵢ}.

**Proof.** Let Av = λv with v ≠ 0. Choose the index i with the **largest** |vᵢ| (so vᵢ ≠ 0). The i-th row of Av = λv reads

Σⱼ aᵢⱼvⱼ = λvᵢ

Separating the j = i term:

aᵢᵢvᵢ + Σ_{j≠i} aᵢⱼvⱼ = λvᵢ
(λ − aᵢᵢ)vᵢ = Σ_{j≠i} aᵢⱼvⱼ

Take absolute values and use the triangle inequality:

|λ − aᵢᵢ||vᵢ| ≤ Σ_{j≠i}|aᵢⱼ||vⱼ| ≤ Σ_{j≠i}|aᵢⱼ||vᵢ| = Rᵢ|vᵢ|

*(using |vⱼ| ≤ |vᵢ| by the choice of i)*

Divide by |vᵢ| > 0: **|λ − aᵢᵢ| ≤ Rᵢ**, i.e. λ ∈ Dᵢ ✓ ∎

**Application to A = [[10, 1, 0], [1, 5, 1], [0, 1, 2]]:**
- D₁: centre 10, radius |1| + |0| = 1 → **[9, 11]**
- D₂: centre 5, radius |1| + |1| = 2 → **[3, 7]**
- D₃: centre 2, radius |0| + |1| = 1 → **[1, 3]**

*(A is symmetric, so all eigenvalues are real — Chapter 11 — and the discs reduce to intervals.)*

**Eigenvalues lie in [9,11] ∪ [3,7] ∪ [1,3].**

**Invertibility without computing det A.** None of the three intervals contains 0 (the closest approach is D₃'s lower end at 1 > 0). Therefore **0 is not an eigenvalue**, so by IMT(q), **A is invertible** ✓

*(This is the classic corollary: a **strictly diagonally dominant** matrix — |aᵢᵢ| > Rᵢ for every i — is always invertible, because no Gershgorin disc can reach the origin. Here 10 > 1, 5 > 2, 2 > 1 ✓)*

---
# Chapter 10 — Diagonalization of Matrices

---

## 10.1 Explain Like I'm Five

Suppose you want to apply a matrix a hundred times: A¹⁰⁰. Doing a hundred matrix multiplications is miserable.

But imagine the matrix were **diagonal** — numbers down the diagonal, zeros everywhere else. Then A¹⁰⁰ is trivial: just raise each diagonal number to the hundredth power. Done.

**Diagonalization is the art of pretending your matrix is diagonal**, by choosing better coordinates.

Here's the idea. The eigenvectors are the directions where A does nothing but stretch. If you rewrite everything in terms of the eigenvector directions instead of the usual x-y-z axes, then A *becomes* a pure stretch — a diagonal matrix. You've changed your point of view, and the ugly matrix turned simple.

The recipe is:
1. Move into eigenvector coordinates (that's P⁻¹)
2. Stretch by the eigenvalues (that's D)
3. Move back to normal coordinates (that's P)

> **A = PDP⁻¹**

And then A¹⁰⁰ = PD¹⁰⁰P⁻¹ — because all the inner P⁻¹P pairs cancel like a telescope collapsing.

**When does this fail?** When you don't have enough independent eigenvectors to make a full coordinate system. The matrix [[3,1],[0,3]] has only one eigendirection, so you can't build a basis out of eigenvectors, and the trick doesn't work. Such a matrix is *defective*, and it genuinely does something a diagonal matrix can't — it shears.

---

## 10.2 The Formal Theory

### 10.2.1 Definition

> **Definition.** An n×n matrix A is **diagonalizable** if there exists an invertible matrix P and a diagonal matrix D with
> **A = PDP⁻¹** (equivalently **P⁻¹AP = D**).

### 10.2.2 The Diagonalization Theorem

> **Theorem 10.1 (The Diagonalization Theorem).** An n×n matrix A is diagonalizable **⟺ A has n linearly independent eigenvectors.**
>
> In that case, A = PDP⁻¹ where
> - the **columns of P** are the n independent eigenvectors v₁, ..., vₙ,
> - D = diag(λ₁, ..., λₙ) with λᵢ the eigenvalue for vᵢ,
> - **the order must match**: the i-th column of P pairs with the i-th diagonal entry of D.

*Proof.* (⇐) Let P = [v₁ ... vₙ] with Avᵢ = λᵢvᵢ. Then
AP = [Av₁ ... Avₙ] = [λ₁v₁ ... λₙvₙ] = PD.
Since the vᵢ are independent, P is invertible, so A = PDP⁻¹ ✓
(⇒) Reverse the steps: A = PDP⁻¹ gives AP = PD, so each column of P is an eigenvector, and P invertible means they are independent ✓ ∎

**Equivalent statement:** A is diagonalizable ⟺ ℝⁿ (or ℂⁿ) has a **basis of eigenvectors of A** — an **eigenbasis**.

### 10.2.3 Practical Criteria

> **Theorem 10.2.** A is diagonalizable ⟺ for **every** eigenvalue λ, **GM(λ) = AM(λ)**.
> Equivalently, Σ_λ dim E_λ = n.

> **Theorem 10.3 (Sufficient condition).** If A has **n distinct eigenvalues**, then A is diagonalizable.

**Important:** Theorem 10.3 is sufficient but **not necessary**. The identity matrix has only one distinct eigenvalue yet is already diagonal. Repeated eigenvalues do not doom you — they merely require a check.

**Decision procedure:**
```
1. Compute the characteristic polynomial and find all eigenvalues with AM.
2. If all n eigenvalues are distinct → diagonalizable. Stop.
3. Otherwise, for each repeated λ, compute GM(λ) = n − rank(A − λI).
4. If GM(λ) = AM(λ) for every λ → diagonalizable.
   If GM(λ) < AM(λ) for even one λ → NOT diagonalizable.
```

### 10.2.4 The Diagonalization Algorithm

**Step 1.** Find the eigenvalues by solving det(A − λI) = 0.
**Step 2.** For each λ, find a basis of E_λ = Nul(A − λI).
**Step 3.** Check that the eigenvectors total n. If not, A is not diagonalizable — stop.
**Step 4.** Form P from the eigenvectors (as columns) and D from the eigenvalues (in the matching order).
**Step 5.** Verify: check AP = PD (easier than computing P⁻¹).

**Non-uniqueness.** P and D are **not unique**. Reordering the eigenvectors reorders D correspondingly; scaling any eigenvector by a nonzero constant gives another valid P. What *is* unique is the multiset of eigenvalues.

### 10.2.5 Powers and Functions of Matrices

If A = PDP⁻¹ then

> **Aᵏ = PDᵏP⁻¹** where Dᵏ = diag(λ₁ᵏ, ..., λₙᵏ)

*Proof:* A² = PDP⁻¹PDP⁻¹ = PD(P⁻¹P)DP⁻¹ = PD²P⁻¹; induct. ∎

This extends to **any function** defined by a power series:

> **f(A) = P f(D) P⁻¹** where f(D) = diag(f(λ₁), ..., f(λₙ))

- **Matrix exponential:** e^A = P diag(e^{λ₁}, ..., e^{λₙ}) P⁻¹ — solves the ODE system x' = Ax as x(t) = e^{At}x₀.
- **Square root:** A^{1/2} = P diag(√λᵢ) P⁻¹ (requires λᵢ ≥ 0 for a real answer).
- **Inverse:** A⁻¹ = P diag(1/λᵢ) P⁻¹ (requires all λᵢ ≠ 0).

### 10.2.6 Dynamical Systems and Long-Run Behaviour

For x_{k+1} = Ax_k with x₀ = c₁v₁ + ... + cₙvₙ (expanding in the eigenbasis):

> **x_k = c₁λ₁ᵏv₁ + c₂λ₂ᵏv₂ + ... + cₙλₙᵏvₙ**

**This decoupling is the whole point.** The behaviour is governed by the largest |λᵢ|:

| Condition | Long-run behaviour |
|---|---|
| All \|λᵢ\| < 1 | x_k → 0. The origin is an **attractor** (stable) |
| All \|λᵢ\| > 1 | \|\|x_k\|\| → ∞. The origin is a **repeller** |
| Some \|λᵢ\| < 1, some > 1 | **Saddle point** — motion toward 0 along some directions, away along others |
| Largest \|λ\| = 1, others < 1 | x_k → (a multiple of the dominant eigenvector) — **steady state** |

The eigenvector for the largest |λ| is the **dominant** direction: for large k, x_k points essentially along it, whatever x₀ was (provided c₁ ≠ 0). This is exactly what power iteration exploits.

### 10.2.7 Similarity

> **Definition.** A and B are **similar** if B = P⁻¹AP for some invertible P.

Similar matrices represent **the same linear transformation in different bases**. Similarity preserves:
- characteristic polynomial, hence **eigenvalues** and their algebraic multiplicities
- geometric multiplicities
- **trace, determinant, rank, nullity**
- diagonalizability, minimal polynomial, Jordan form

Similarity does **not** preserve: eigenvectors themselves (they transform as v ↦ P⁻¹v), entries, symmetry, orthogonality of columns.

**Caution:** same eigenvalues does **not** imply similar. I₂ and [[1,1],[0,1]] both have eigenvalues {1,1} but are not similar (one is diagonalizable, the other isn't).

Diagonalizable = **similar to a diagonal matrix**.

### 10.2.8 When Diagonalization Fails: the Jordan Form

Every complex square matrix is similar to a **Jordan canonical form** — block diagonal, with each block

```
J_k(λ) = [[λ, 1, 0, ..., 0],
          [0, λ, 1, ..., 0],
          [       ⋱   ⋱   ],
          [0, 0, ..., 0, λ]]
```

A is diagonalizable ⟺ all Jordan blocks are 1×1. The number of Jordan blocks for λ equals **GM(λ)**; the total size of those blocks equals **AM(λ)**.

Jordan form is usually beyond a first course's computation requirements, but the concept explains exactly *what* is missing in a defective matrix.

### 10.2.9 The Minimal Polynomial

The **minimal polynomial** m(λ) is the monic polynomial of least degree with m(A) = 0.

- m(λ) divides the characteristic polynomial (Cayley–Hamilton).
- m(λ) has the **same roots** as the characteristic polynomial (all eigenvalues appear).
- **A is diagonalizable ⟺ m(λ) has no repeated roots.**

This is often the fastest theoretical test. For instance, if A² = A, then m(λ) divides λ² − λ = λ(λ−1), which has distinct roots → **every idempotent matrix is diagonalizable**.

---

## 10.3 Solved Examples

### Example 10.1 — [Easy] Diagonalize a 2×2

Diagonalize A = [[1, 6], [5, 2]].

**Solution.**
p(λ) = (1−λ)(2−λ) − 30 = λ² − 3λ + 2 − 30 = λ² − 3λ − 28 = (λ−7)(λ+4).
**λ = 7, −4** (distinct → diagonalizable ✓)

**λ = 7:** A − 7I = [[−6, 6], [5, −5]] → v₁ = v₂ → **v = (1, 1)**.
**λ = −4:** A + 4I = [[5, 6], [5, 6]] → 5v₁ + 6v₂ = 0 → **v = (6, −5)**.

```
P = [[1, 6],      D = [[7,  0],
     [1, −5]]          [0, −4]]
```

**Verify AP = PD.**
AP: column 1 = A(1,1)ᵀ = (1+6, 5+2) = (7, 7) ✓ = 7·(1,1).
column 2 = A(6,−5)ᵀ = (6 − 30, 30 − 10) = (−24, 20) ✓ = −4·(6,−5).
PD = [[7, −24], [7, 20]] ✓ matches.

**A = PDP⁻¹** with P⁻¹ = (1/(−5−6))[[−5, −6], [−1, 1]] = (−1/11)[[−5,−6],[−1,1]] = (1/11)[[5, 6], [1, −1]].

---

### Example 10.2 — [Easy] Recognizing non-diagonalizability fast

Is A = [[6, −1], [9, 0]] diagonalizable?

**Solution.** p(λ) = λ² − 6λ + 9 = (λ−3)². **λ = 3, AM = 2.**

A − 3I = [[3, −1], [9, −3]]. Row 2 = 3 × Row 1 → **rank 1** → GM = 2 − 1 = **1**.

GM(3) = 1 < 2 = AM(3) → **NOT diagonalizable.**

---

### Example 10.3 — [Medium] 3×3 with a repeated eigenvalue that still works

Diagonalize A = [[2, 4, 3], [−4, −6, −3], [3, 3, 1]].

**Solution.** Characteristic polynomial. Expanding (or using tr A = −3, det A = ...):

p(λ) = −(λ+2)²(λ−1)

*(Verification via trace: −2 − 2 + 1 = −3 ✓ matches tr A = 2 − 6 + 1 = −3.)*

**Eigenvalues: λ = −2 (AM 2), λ = 1 (AM 1).**

**λ = −2:** A + 2I = [[4, 4, 3], [−4, −4, −3], [3, 3, 3]].
`R₂ + R₁` → zero row. `R₃ → R₃/3` → (1, 1, 1). Then `R₁ − 4R₃` → (0, 0, −1).
RREF: [[1, 1, 0], [0, 0, 1], [0, 0, 0]]. **rank 2 → GM = 1.**

**GM(−2) = 1 < 2 = AM(−2), so A is NOT diagonalizable.**

*(Instructive: a repeated eigenvalue is a warning sign, not a guarantee of failure — but here it does fail.)*

**Let's instead diagonalize a matrix that works:** B = [[4, −3, −3], [3, −2, −3], [−1, 1, 2]].

p(λ) = −(λ−1)²(λ−2). *(tr B = 4 − 2 + 2 = 4 = 1 + 1 + 2 ✓)*

**λ = 1:** B − I = [[3, −3, −3], [3, −3, −3], [−1, 1, 1]].
All rows are multiples of (1, −1, −1) → **rank 1 → GM = 2** ✓ = AM
Solve x − y − z = 0 → x = y + z. Free: y, z.
**Basis: {(1, 1, 0), (1, 0, 1)}**

**λ = 2:** B − 2I = [[2, −3, −3], [3, −4, −3], [−1, 1, 0]].
From row 3: x = y. Substituting into row 1: 2y − 3y − 3z = 0 → −y = 3z → y = −3z.
Take z = −1: y = 3, x = 3. **Eigenvector (3, 3, −1)**.
*Check row 2: 3(3) − 4(3) − 3(−1) = 9 − 12 + 3 = 0 ✓*

```
P = [[1, 1,  3],       D = [[1, 0, 0],
     [1, 0,  3],            [0, 1, 0],
     [0, 1, −1]]            [0, 0, 2]]
```
**Check P is invertible:** det P = 1(0·(−1) − 3·1) − 1(1(−1) − 0) + 3(1 − 0) = 1(−3) − 1(−1) + 3 = −3 + 1 + 3 = 1 ≠ 0 ✓

**B = PDP⁻¹.**

---

### Example 10.4 — [Medium] Computing a high power

Given A = [[1, 6], [5, 2]] from Example 10.1, compute A⁵ using diagonalization.

**Solution.** A = PDP⁻¹ with P = [[1,6],[1,−5]], D = diag(7, −4), P⁻¹ = (1/11)[[5, 6], [1, −1]].

D⁵ = diag(7⁵, (−4)⁵) = diag(16807, −1024).

A⁵ = P D⁵ P⁻¹ = (1/11)·[[1, 6], [1, −5]]·[[16807, 0], [0, −1024]]·[[5, 6], [1, −1]]

**Step 1:** P·D⁵ = [[16807, −6144], [16807, 5120]]

**Step 2:** multiply by (1/11)[[5, 6], [1, −1]]:
- (1,1): (16807(5) + (−6144)(1))/11 = (84035 − 6144)/11 = 77891/11 = **7081**
- (1,2): (16807(6) + (−6144)(−1))/11 = (100842 + 6144)/11 = 106986/11 = **9726**
- (2,1): (16807(5) + 5120(1))/11 = (84035 + 5120)/11 = 89155/11 = **8105**
- (2,2): (16807(6) + 5120(−1))/11 = (100842 − 5120)/11 = 95722/11 = **8702**

**A⁵ = [[7081, 9726], [8105, 8702]]**

*Check via trace:* tr(A⁵) should equal 7⁵ + (−4)⁵ = 16807 − 1024 = 15783. And 7081 + 8702 = **15783** ✓
*Check via determinant:* det(A⁵) = (det A)⁵ = (2 − 30)⁵ = (−28)⁵ = −17210368. And 7081(8702) − 9726(8105) = 61618862 − 78829230 = −17210368 ✓

---

### Example 10.5 — [Hard] Dynamical system

A population of owls (O) and rats (R) evolves as
```
O_{k+1} = 0.5 O_k + 0.4 R_k
R_{k+1} = −p O_k + 1.1 R_k
```
For p = 0.104, determine the long-run behaviour starting from (O₀, R₀) = (10, 200).

**Solution.** A = [[0.5, 0.4], [−0.104, 1.1]].

p(λ) = (0.5−λ)(1.1−λ) + 0.0416 = λ² − 1.6λ + 0.55 + 0.0416 = λ² − 1.6λ + 0.5916

λ = [1.6 ± √(2.56 − 2.3664)]/2 = [1.6 ± √0.1936]/2 = [1.6 ± 0.44]/2

**λ₁ = 1.02, λ₂ = 0.58**

**λ₁ = 1.02:** A − 1.02I = [[−0.52, 0.4], [−0.104, 0.08]].
Row 2 = 0.2 × Row 1 ✓ consistent. From row 1: 0.52v₁ = 0.4v₂ → v₁/v₂ = 0.4/0.52 = 10/13.
**v₁ = (10, 13)**

**λ₂ = 0.58:** A − 0.58I = [[−0.08, 0.4], [−0.104, 0.52]].
Row 1: 0.08v₁ = 0.4v₂ → v₁ = 5v₂. **v₂ = (5, 1)**

**Expand x₀ = (10, 200) in the eigenbasis:** solve c₁(10, 13) + c₂(5, 1) = (10, 200).
```
10c₁ + 5c₂ = 10
13c₁ + c₂ = 200
```
From the second: c₂ = 200 − 13c₁. Substituting: 10c₁ + 1000 − 65c₁ = 10 → −55c₁ = −990 → **c₁ = 18**, c₂ = 200 − 234 = **−34**.

**Solution:** x_k = 18(1.02)ᵏ(10, 13) − 34(0.58)ᵏ(5, 1)

**Long-run behaviour.** Since 0.58ᵏ → 0 and 1.02ᵏ → ∞:

> x_k ≈ 18(1.02)ᵏ(10, 13) for large k

**Both populations grow at about 2% per period, and the ratio of owls to rats approaches 10 : 13.** The system is unstable (growing), but the *ratio* stabilizes — that ratio is the dominant eigenvector direction.

*Sanity check at k = 1:* x₁ = A(10,200) = (5 + 80, −1.04 + 220) = (85, 218.96).
Formula: 18(1.02)(10,13) − 34(0.58)(5,1) = 18.36(10,13) − 19.72(5,1) = (183.6, 238.68) − (98.6, 19.72) = (85.0, 218.96) ✓

---

### Example 10.6 — [Hard] Matrix exponential

Solve the differential equation system x' = Ax with A = [[1, 2], [2, 1]] and x(0) = (3, 1)ᵀ.

**Solution.** **Diagonalize A.** p(λ) = (1−λ)² − 4 = λ² − 2λ − 3 = (λ−3)(λ+1). **λ = 3, −1.**

λ=3: A − 3I = [[−2, 2], [2, −2]] → **v = (1, 1)**
λ=−1: A + I = [[2, 2], [2, 2]] → **v = (1, −1)**

The general solution of x' = Ax for a diagonalizable A is

> **x(t) = c₁e^{λ₁t}v₁ + c₂e^{λ₂t}v₂**

*(Each eigendirection decouples into a scalar ODE y' = λy with solution y = ce^{λt}.)*

x(t) = c₁e^{3t}(1, 1) + c₂e^{−t}(1, −1)

**Apply the initial condition:** c₁(1,1) + c₂(1,−1) = (3, 1).
c₁ + c₂ = 3, c₁ − c₂ = 1 → **c₁ = 2, c₂ = 1**.

**Answer:**
> **x(t) = 2e^{3t}(1, 1) + e^{−t}(1, −1)**
> i.e. x₁(t) = 2e^{3t} + e^{−t}, x₂(t) = 2e^{3t} − e^{−t}

**Check:** x(0) = (2+1, 2−1) = (3, 1) ✓
x₁' = 6e^{3t} − e^{−t}. And (Ax)₁ = x₁ + 2x₂ = (2e^{3t} + e^{−t}) + 2(2e^{3t} − e^{−t}) = 6e^{3t} − e^{−t} ✓

**Long-run:** the e^{3t} term dominates, so the trajectory aligns with the (1,1) direction and blows up. The origin is an **unstable node**.

---

### Example 10.7 — [Very Hard] Simultaneous diagonalization

Prove that if A and B are diagonalizable and **AB = BA**, then they are **simultaneously diagonalizable** — there is a single P with both P⁻¹AP and P⁻¹BP diagonal.

**Solution.**

**Step 1: B preserves the eigenspaces of A.**
Let v ∈ E_λ(A), so Av = λv. Then
A(Bv) = (AB)v = (BA)v = B(Av) = B(λv) = λ(Bv)
So **Bv ∈ E_λ(A)** ✓ — B maps each eigenspace of A into itself. (Such a subspace is called *B-invariant*.)

**Step 2: Diagonalize B within each eigenspace.**
Since A is diagonalizable, ℝⁿ = E_{λ₁} ⊕ E_{λ₂} ⊕ ... ⊕ E_{λ_r} (the eigenspaces of A span everything).

Restrict B to E_{λᵢ}. This restriction, call it B|ᵢ, is a linear operator on E_{λᵢ} by Step 1.

**Claim: B|ᵢ is diagonalizable.** Since B is diagonalizable, its minimal polynomial m_B has distinct roots. But m_B also annihilates B|ᵢ (as B|ᵢ is a restriction), so the minimal polynomial of B|ᵢ divides m_B and therefore also has distinct roots. Hence B|ᵢ is diagonalizable ✓

**Step 3: Assemble.**
Choose a basis of E_{λᵢ} consisting of eigenvectors of B|ᵢ. Every such vector is:
- an eigenvector of A (it lies in E_{λᵢ}), **and**
- an eigenvector of B (by construction).

Collecting these bases over all i gives a basis of ℝⁿ of **common eigenvectors**. Let P be the matrix of these vectors.

Then **P⁻¹AP and P⁻¹BP are both diagonal** ✓ ∎

**Converse.** If A = PD₁P⁻¹ and B = PD₂P⁻¹ with the *same* P, then
AB = PD₁D₂P⁻¹ = PD₂D₁P⁻¹ = BA
(diagonal matrices always commute). So **commuting is also necessary** ✓

**Illustration.** A = [[2, 1], [1, 2]], B = [[3, 1], [1, 3]]. Check AB = [[7, 5], [5, 7]] = BA ✓
Both have eigenvectors (1,1) and (1,−1). With P = [[1,1],[1,−1]]:
P⁻¹AP = diag(3, 1) and P⁻¹BP = diag(4, 2) ✓ One P, both diagonalized.

*(This theorem is the mathematical content of "compatible observables" in quantum mechanics — commuting operators can be measured simultaneously because they share an eigenbasis.)*

---

### Example 10.8 — [Very Hard] Fibonacci via diagonalization

Use diagonalization to derive Binet's formula for the Fibonacci numbers F₀ = 0, F₁ = 1, F_{n+1} = F_n + F_{n−1}.

**Solution.** Write the recurrence as a matrix system. Let x_n = (F_{n+1}, F_n)ᵀ. Then

```
(F_{n+2}, F_{n+1}) = (F_{n+1} + F_n, F_{n+1})
```
so x_{n+1} = A x_n with **A = [[1, 1], [1, 0]]** and x₀ = (F₁, F₀) = (1, 0).

Hence **x_n = Aⁿ x₀**.

**Diagonalize A.** p(λ) = λ² − λ − 1. Roots:
λ = (1 ± √5)/2. Write **φ = (1+√5)/2 ≈ 1.618** (golden ratio) and **ψ = (1−√5)/2 ≈ −0.618**.

Note φψ = −1 and φ + ψ = 1.

**Eigenvectors.** A − λI = [[1−λ, 1], [1, −λ]]. From the second row: v₁ = λv₂.
**v = (λ, 1)**. So eigenvectors are **(φ, 1)** and **(ψ, 1)**.

```
P = [[φ, ψ],      D = [[φ, 0],
     [1, 1]]           [0, ψ]]
```
det P = φ − ψ = √5. **P⁻¹ = (1/√5)[[1, −ψ], [−1, φ]]**.

**Compute x_n = PDⁿP⁻¹x₀** with x₀ = (1, 0)ᵀ:

P⁻¹x₀ = (1/√5)(1, −1)ᵀ

Dⁿ(P⁻¹x₀) = (1/√5)(φⁿ, −ψⁿ)ᵀ

P·that = (1/√5)·(φ·φⁿ − ψ·ψⁿ, φⁿ − ψⁿ)ᵀ = (1/√5)(φ^{n+1} − ψ^{n+1}, φⁿ − ψⁿ)ᵀ

Reading the **second** component (which is F_n):

> **F_n = (φⁿ − ψⁿ)/√5 = [((1+√5)/2)ⁿ − ((1−√5)/2)ⁿ]/√5**

**This is Binet's formula.** ∎

**Verification.**
- n=1: (φ − ψ)/√5 = √5/√5 = 1 ✓
- n=2: (φ² − ψ²)/√5 = (φ+ψ)(φ−ψ)/√5 = (1)(√5)/√5 = 1 ✓
- n=5: φ⁵ ≈ 11.0902, ψ⁵ ≈ −0.0902. (11.0902 + 0.0902)/2.2361 = 11.1803/2.2361 = **5** ✓

**Bonus insight.** Since |ψ| ≈ 0.618 < 1, the term ψⁿ → 0, so

> **F_n ≈ φⁿ/√5** (rounded to the nearest integer, exactly F_n for all n ≥ 0)

and **F_{n+1}/F_n → φ**, the golden ratio — which is just the statement that the dominant eigenvalue governs the long-run growth rate (§10.2.6).

---

## 10.4 Practice Numericals — Chapter 10

**[Easy]**

**P10.1** Diagonalize A = [[3, 0], [0, 5]] (trivial case — state P and D).

**P10.2** Is A = [[1, 1], [0, 1]] diagonalizable? Justify with AM and GM.

**P10.3** Given A = PDP⁻¹ with D = diag(2, 3), compute the eigenvalues of A³.

**P10.4** Diagonalize A = [[5, 3], [0, 2]].

**P10.5** If A is 4×4 with 4 distinct eigenvalues, is it diagonalizable? Why?

**[Medium]**

**P10.6** Diagonalize A = [[1, 3], [4, 2]] and compute A⁴.

**P10.7** Determine whether A = [[2, 0, 0], [1, 2, 0], [0, 0, 3]] is diagonalizable.

**P10.8** Diagonalize A = [[0, 1], [1, 0]] and use it to find A^{100}.

**P10.9** A 3×3 matrix has eigenvalues 1, 1, 4 with dim E₁ = 2. Is it diagonalizable? What is rank(A − I)?

**P10.10** Diagonalize A = [[7, 2], [−4, 1]].

**P10.11** For A = [[0.6, 0.3], [0.4, 0.7]], find the eigenvalues and determine lim_{k→∞} Aᵏ x₀ for x₀ = (1, 0)ᵀ.

**[Hard]**

**P10.12** Diagonalize A = [[1, 2, 2], [2, 1, 2], [2, 2, 1]] and compute A⁵.

**P10.13** Show that if A is diagonalizable and every eigenvalue is ±1, then A² = I.

**P10.14** Solve the system x' = Ax for A = [[3, −2], [1, 0]] with x(0) = (1, 1)ᵀ.

**P10.15** Let A = [[a, b], [0, a]] with b ≠ 0. Prove A is not diagonalizable for any a, and compute Aⁿ directly.

**P10.16** Find all values of c for which A = [[1, c], [0, 1]] ... and separately for which A = [[2, c], [0, 3]] is diagonalizable.

**P10.17** Let A be a 3×3 matrix satisfying A² = A with rank 2. Find all eigenvalues with multiplicities, prove A is diagonalizable, and write D.

**[Very Hard]**

**P10.18** Solve the recurrence a_{n+1} = 5a_n − 6a_{n−1}, a₀ = 1, a₁ = 4, using diagonalization.

**P10.19** Prove that A is diagonalizable if and only if its minimal polynomial factors into distinct linear factors. Use this to show that any A with A³ = A is diagonalizable.

**P10.20** Let A and B be n×n with A diagonalizable. Prove that if AB = BA and B has n distinct eigenvalues, then A is a polynomial in B.

**P10.21** Prove that if A is diagonalizable with eigenvalues λᵢ, then Aᵏ → 0 as k → ∞ if and only if |λᵢ| < 1 for all i. Give an example showing the "diagonalizable" hypothesis can be dropped (the result holds for all matrices, via the spectral radius), and one showing why |λᵢ| ≤ 1 is not enough.

---

## 10.5 Solutions to Chapter 10 Practice

**S10.1** Already diagonal. Take **P = I₂, D = A = diag(3, 5)** ✓ (Any invertible diagonal P also works.)

**S10.2** p(λ) = (1−λ)², **λ = 1, AM = 2**.
A − I = [[0,1],[0,0]], rank 1 → **GM = 1**.
1 < 2 → **not diagonalizable**.

**S10.3** Eigenvalues of A are 2, 3 → eigenvalues of A³ are **8 and 27**.

**S10.4** Triangular → **λ = 5, 2** (distinct → diagonalizable).
λ=5: A − 5I = [[0,3],[0,−3]] → v₂ = 0 → **(1, 0)**
λ=2: A − 2I = [[3,3],[0,0]] → v₁ = −v₂ → **(1, −1)**
**P = [[1, 1], [0, −1]], D = diag(5, 2)**
*Check: A(1,−1)ᵀ = (5−3, −2) = (2, −2) = 2(1,−1) ✓*

**S10.5** **Yes.** Eigenvectors for distinct eigenvalues are independent (Thm 9.2), so 4 distinct eigenvalues give 4 independent eigenvectors — a basis of ℝ⁴ — which is exactly the diagonalizability criterion (Thm 10.1).

**S10.6** p(λ) = (1−λ)(2−λ) − 12 = λ² − 3λ − 10 = (λ−5)(λ+2). **λ = 5, −2.**
λ=5: [[−4,3],[4,−3]] → 4v₁ = 3v₂ → **(3, 4)**
λ=−2: [[3,3],[4,4]] → v₁ = −v₂ → **(1, −1)**
**P = [[3, 1], [4, −1]], D = diag(5, −2).** det P = −3 − 4 = −7.
P⁻¹ = (−1/7)[[−1, −1], [−4, 3]] = (1/7)[[1, 1], [4, −3]].

A⁴ = P diag(625, 16) P⁻¹.
P·diag(625,16) = [[1875, 16], [2500, −16]].
Multiply by (1/7)[[1,1],[4,−3]]:
- (1,1): (1875 + 64)/7 = 1939/7 = **277**
- (1,2): (1875 − 48)/7 = 1827/7 = **261**
- (2,1): (2500 − 64)/7 = 2436/7 = **348**
- (2,2): (2500 + 48)/7 = 2548/7 = **364**

**A⁴ = [[277, 261], [348, 364]]**
*Check trace: 277 + 364 = 641 = 625 + 16 ✓*

**S10.7** Block structure. The top-left 2×2 block [[2,0],[1,2]] is a Jordan block for λ=2.
Eigenvalues: 2 (AM 2), 3 (AM 1).
A − 2I = [[0,0,0],[1,0,0],[0,0,1]] → rank 2 → **GM(2) = 1 < 2**.
**Not diagonalizable.**

**S10.8** p(λ) = λ² − 1 → **λ = 1, −1**.
λ=1: **(1, 1)**. λ=−1: **(1, −1)**.
P = [[1,1],[1,−1]], P⁻¹ = (1/2)[[1,1],[1,−1]] (P is symmetric with P² = 2I).
A^{100} = P·diag(1, 1)·P⁻¹ = P·I·P⁻¹ = **I**.
*(Obvious in hindsight: A swaps coordinates, so A² = I and every even power is I.)*

**S10.9** Eigenvalue 1 has AM = 2 and GM = dim E₁ = 2 ✓; eigenvalue 4 has AM = GM = 1 ✓
**Yes, diagonalizable.**
rank(A − I) = 3 − dim Nul(A − I) = 3 − 2 = **1**.

**S10.10** p(λ) = λ² − 8λ + (7 + 8) = λ² − 8λ + 15 = (λ−3)(λ−5). **λ = 3, 5.**
λ=3: [[4,2],[−4,−2]] → 2v₁ = −v₂ → **(1, −2)**
λ=5: [[2,2],[−4,−4]] → v₁ = −v₂ → **(1, −1)**
**P = [[1, 1], [−2, −1]], D = diag(3, 5)**
*Check: A(1,−1)ᵀ = (7−2, −4−1) = (5, −5) = 5(1,−1) ✓*

**S10.11** Columns sum to 1 → column-stochastic → λ = 1 is an eigenvalue.
p(λ) = λ² − 1.3λ + (0.42 − 0.12) = λ² − 1.3λ + 0.30. Roots: λ = [1.3 ± √(1.69 − 1.2)]/2 = [1.3 ± 0.7]/2.
**λ = 1 and λ = 0.3.**
λ=1: A − I = [[−0.4, 0.3], [0.4, −0.3]] → 4v₁ = 3v₂ → **v = (3, 4)**. Normalize to sum 1: **(3/7, 4/7)**.
Since |0.3| < 1, the second mode dies out.
**lim Aᵏ(1, 0)ᵀ = (3/7, 4/7) ≈ (0.4286, 0.5714)**
*(The limit is the steady state, independent of the starting vector as long as it is a probability vector.)*

**S10.12** A = J + ... note A = 2J − I where J is the 3×3 all-ones matrix? Check: 2J − I has diagonal 2−1 = 1 ✓ and off-diagonal 2 ✓ **Yes, A = 2J − I.**

By Example 9.8, J has eigenvalues 3 (eigenvector (1,1,1)) and 0 (multiplicity 2).
So A = 2J − I has eigenvalues **2(3) − 1 = 5** and **2(0) − 1 = −1** (multiplicity 2).

**λ = 5:** eigenvector **(1, 1, 1)**
**λ = −1:** eigenspace = Nul(J) = {x : x₁+x₂+x₃ = 0}, basis **{(1,−1,0), (1,0,−1)}**

GM(−1) = 2 = AM ✓ **Diagonalizable.**
```
P = [[1, 1,  1],       D = diag(5, −1, −1)
     [1, −1, 0],
     [1, 0, −1]]
```
**A⁵.** Eigenvalues become 5⁵ = 3125 and (−1)⁵ = −1.
Since A⁵ has the same eigenvectors, and A⁵ must also be of the form aI + bJ by symmetry:
- On (1,1,1): a + 3b = 3125
- On Nul(J): a = −1

So b = (3125 + 1)/3 = 1042.
**A⁵ = −I + 1042J = [[1041, 1042, 1042], [1042, 1041, 1042], [1042, 1042, 1041]]**
*Check trace: 3(1041) = 3123 = 3125 + (−1) + (−1) = 3123 ✓*

**S10.13** A = PDP⁻¹ with D = diag(±1). Then D² = I (each entry squared is 1).
A² = PD²P⁻¹ = PIP⁻¹ = PP⁻¹ = **I** ✓ ∎
*(Such matrices are exactly the "involutions" — reflections and their generalizations.)*

**S10.14** p(λ) = λ² − 3λ + 2 = (λ−1)(λ−2). **λ = 1, 2.**
λ=1: A − I = [[2,−2],[1,−1]] → v₁ = v₂ → **(1, 1)**
λ=2: A − 2I = [[1,−2],[1,−2]] → v₁ = 2v₂ → **(2, 1)**

x(t) = c₁e^{t}(1,1) + c₂e^{2t}(2,1).
Initial condition: c₁(1,1) + c₂(2,1) = (1,1) → c₁ + 2c₂ = 1, c₁ + c₂ = 1 → **c₂ = 0, c₁ = 1**.

**x(t) = e^{t}(1, 1)**, i.e. x₁ = x₂ = e^t.
*(The initial vector happened to be an eigenvector, so the motion stays on that eigendirection forever.)*
*Check: x' = e^t(1,1); Ax = e^t(3−2, 1) = e^t(1,1) ✓*

**S10.15** p(λ) = (a−λ)² → **λ = a, AM = 2**.
A − aI = [[0, b], [0, 0]] with b ≠ 0 → **rank 1** → GM = 1 < 2.
**Not diagonalizable for any a** ✓ ∎

**Aⁿ directly.** Write A = aI + N with N = [[0,b],[0,0]], N² = 0. Since aI and N commute, use the binomial theorem:
Aⁿ = (aI + N)ⁿ = Σ C(n,k)(aI)^{n−k}N^k = aⁿI + n a^{n−1}N (all higher terms vanish)

**Aⁿ = [[aⁿ, n·a^{n−1}·b], [0, aⁿ]]**
*Check n=2: [[a², 2ab],[0,a²]]. Direct: [[a,b],[0,a]]² = [[a², ab+ab],[0,a²]] ✓*

**S10.16** **A = [[1, c], [0, 1]]:** λ = 1 with AM 2. A − I = [[0, c],[0,0]].
- If c ≠ 0: rank 1 → GM = 1 < 2 → **not diagonalizable**.
- If c = 0: A = I, already diagonal → **diagonalizable**.
**Answer: only c = 0.**

**A = [[2, c], [0, 3]]:** eigenvalues 2 and 3 are **distinct for every c**.
**Answer: diagonalizable for all c ∈ ℝ.**
*(Lesson: repeated eigenvalues are what create the risk; distinct eigenvalues are always safe.)*

**S10.17** A² = A means the minimal polynomial divides λ² − λ = λ(λ−1), so **every eigenvalue is 0 or 1**.

rank(A) = 2 → dim Col(A) = 2. For an idempotent matrix, **Col(A) = E₁** (if x ∈ Col A, x = Ay, then Ax = A²y = Ay = x ✓) and **Nul(A) = E₀**.

So GM(1) = 2 and GM(0) = 3 − 2 = 1. Total = 3 ✓

**Eigenvalues: 1 (AM = GM = 2), 0 (AM = GM = 1).**

**Diagonalizable ✓** — either because GM = AM for both, or immediately because λ(λ−1) has distinct roots (§10.2.9).

**D = diag(1, 1, 0)**

*(This says every rank-2 projection in ℝ³ is similar to the coordinate projection onto the xy-plane — geometrically obvious once stated.)*

**S10.18** Write x_n = (a_{n+1}, a_n)ᵀ. Then
a_{n+2} = 5a_{n+1} − 6a_n, so **A = [[5, −6], [1, 0]]** and x_{n+1} = Ax_n, x₀ = (4, 1)ᵀ.

p(λ) = λ² − 5λ + 6 = (λ−2)(λ−3). **λ = 2, 3.**
Eigenvectors: from row 2 of (A − λI) = [[5−λ, −6],[1, −λ]]: v₁ = λv₂ → **v = (λ, 1)**.
So **(2, 1)** and **(3, 1)**.

**General solution:** a_n = c₁·2ⁿ + c₂·3ⁿ.

Apply initial conditions:
- n=0: c₁ + c₂ = 1
- n=1: 2c₁ + 3c₂ = 4

Subtracting twice the first: c₂ = 2, then **c₁ = −1**.

**Answer: a_n = −2ⁿ + 2·3ⁿ = 2·3ⁿ − 2ⁿ**

**Check:** a₀ = 2 − 1 = 1 ✓; a₁ = 6 − 2 = 4 ✓; a₂ = 18 − 4 = 14, and 5(4) − 6(1) = 14 ✓; a₃ = 54 − 8 = 46, and 5(14) − 6(4) = 70 − 24 = 46 ✓

**S10.19**
**(⇒)** If A = PDP⁻¹ with D = diag(λ₁,...,λₙ) and distinct values μ₁,...,μ_r among them, let q(λ) = Π(λ − μⱼ). Then q(D) = 0 (each diagonal entry gives a zero factor), so q(A) = Pq(D)P⁻¹ = 0. Hence the minimal polynomial divides q, which has **distinct linear factors** ✓

**(⇐)** Suppose m(λ) = (λ−μ₁)···(λ−μ_r) with distinct μⱼ and m(A) = 0.
Use the partial-fraction / Lagrange interpolation identity: there exist polynomials such that
Σⱼ Lⱼ(λ) = 1, where Lⱼ(λ) = Π_{k≠j}(λ − μ_k)/(μⱼ − μ_k).
Set Pⱼ = Lⱼ(A). Then ΣPⱼ = I, and (A − μⱼI)Pⱼ = c·m(A) = 0, so Col(Pⱼ) ⊆ E_{μⱼ}.
Since ΣPⱼ = I, every x = ΣPⱼx decomposes into eigenvectors. So the eigenspaces span ℝⁿ → **A is diagonalizable** ✓ ∎

**Application:** A³ = A means A³ − A = 0, so the minimal polynomial divides
λ³ − λ = λ(λ−1)(λ+1),
which has **three distinct roots**. Hence the minimal polynomial has distinct linear factors and **A is diagonalizable**, with eigenvalues drawn from {0, 1, −1} ✓

**S10.20** Since B has n distinct eigenvalues μ₁, ..., μₙ, it is diagonalizable with an eigenbasis {w₁, ..., wₙ}, each eigenspace one-dimensional.

**Step 1.** AB = BA means A preserves each eigenspace of B (same argument as Example 10.7 Step 1): if Bwᵢ = μᵢwᵢ then B(Awᵢ) = A(Bwᵢ) = μᵢ(Awᵢ), so Awᵢ ∈ E_{μᵢ}(B).

**Step 2.** But dim E_{μᵢ}(B) = 1 (eigenvalues are distinct), so **Awᵢ = νᵢwᵢ** for some scalar νᵢ. Thus the wᵢ are eigenvectors of A too.

**Step 3.** In the basis {wᵢ}, both become diagonal: P⁻¹BP = diag(μᵢ), P⁻¹AP = diag(νᵢ).

**Step 4.** Since the μᵢ are distinct, **Lagrange interpolation** gives a polynomial q of degree ≤ n−1 with q(μᵢ) = νᵢ for every i:
q(λ) = Σᵢ νᵢ · Π_{k≠i} (λ − μ_k)/(μᵢ − μ_k)

Then q(P⁻¹BP) = diag(q(μᵢ)) = diag(νᵢ) = P⁻¹AP, so

**A = q(B)** — A is a polynomial in B ✓ ∎

**S10.21**
**(⇒)** Suppose Aᵏ → 0. If |λ| ≥ 1 for some eigenvalue with eigenvector v, then Aᵏv = λᵏv has ‖Aᵏv‖ = |λ|ᵏ‖v‖ ≥ ‖v‖ ≠ 0, so Aᵏ cannot tend to 0 ✓

**(⇐)** If all |λᵢ| < 1 and A = PDP⁻¹, then Aᵏ = PDᵏP⁻¹ and Dᵏ = diag(λᵢᵏ) → 0 entrywise. Hence Aᵏ → P·0·P⁻¹ = 0 ✓ ∎

**Dropping diagonalizability.** The result still holds in general: the criterion is the **spectral radius** ρ(A) = max|λᵢ| < 1. For a Jordan block J_k(λ) one computes
(J_k(λ))ᵐ entries look like C(m, j)λ^{m−j},
and since polynomial growth C(m,j) ~ m^j is beaten by geometric decay |λ|^m whenever |λ| < 1, these still → 0.

**Example:** A = [[0.5, 1], [0, 0.5]] (not diagonalizable, λ = 0.5 twice).
Aᵐ = [[0.5ᵐ, m(0.5)^{m−1}], [0, 0.5ᵐ]]. At m = 20: 0.5²⁰ ≈ 9.5×10⁻⁷ and 20(0.5)¹⁹ ≈ 3.8×10⁻⁵ → both → 0 ✓

**Why |λ| ≤ 1 is not enough.**
- A = I has all |λ| = 1 and Aᵏ = I ↛ 0.
- Worse, A = [[1, 1], [0, 1]] has |λ| = 1 but Aᵏ = [[1, k],[0,1]] which **diverges** ✓

So the strict inequality is essential, and the defective case can even blow up at the boundary.

---
# Chapter 11 — Symmetric Matrices, Positive Definite Matrices, Similar Matrices

---

## 11.1 Explain Like I'm Five

### Symmetric matrices

A matrix is **symmetric** if it looks the same when you flip it across the diagonal: Aᵀ = A. The entry in row 2 column 5 equals the entry in row 5 column 2.

This sounds like a minor bookkeeping property. It is actually the single most important special case in the entire subject, because symmetric matrices are **perfectly behaved**:

1. All their eigenvalues are **real** — no complex numbers ever appear.
2. Eigenvectors for different eigenvalues are automatically **perpendicular**.
3. They are **always diagonalizable** — no defective cases, ever.

Put together: a symmetric matrix can always be described as "stretch by different amounts along a set of mutually perpendicular axes." That's it. No rotation, no shearing, no weirdness. Just a clean set of perpendicular stretch directions. This is the **Spectral Theorem**, and it is the reason PCA, SVD, and half of machine learning work.

**Why do symmetric matrices show up everywhere?** Because covariance matrices are symmetric. Distance matrices are symmetric. Graph adjacency matrices for undirected graphs are symmetric. AᵀA is symmetric for *any* A. Energy and cost functions produce symmetric matrices. Nature is full of them.

### Positive definite

Take a symmetric matrix and ask: does the quadratic expression **xᵀAx** always come out positive (for x ≠ 0)? If yes, A is **positive definite**.

The picture: xᵀAx is a bowl-shaped surface. Positive definite means the bowl opens **upward** in every direction — there's a genuine lowest point at the origin. If it opened downward in some direction, you'd have a saddle or a dome instead.

The clean test: **A is positive definite ⟺ all its eigenvalues are positive.** Because in the eigenbasis, xᵀAx = λ₁y₁² + λ₂y₂² + ..., which is positive for all nonzero y exactly when all the λ's are.

This matters because "is this a minimum?" is the central question of optimization, and the answer is always "is the Hessian positive definite?"

### Similar matrices

Two matrices are **similar** if they're the same transformation seen in different coordinate systems: B = P⁻¹AP. Like the same building photographed from two angles — different pictures, same building. Everything intrinsic (eigenvalues, rank, determinant, trace) is shared; everything coordinate-dependent (the actual entries) is not.

---

## 11.2 The Formal Theory

### 11.2.1 Symmetric Matrices

> **Definition.** A is **symmetric** if Aᵀ = A. (Complex analogue: **Hermitian**, A* = A, where A* = conjugate transpose.)

> **Theorem 11.1.** If A is symmetric, **eigenvectors for distinct eigenvalues are orthogonal**.

*Proof.* Let Av₁ = λ₁v₁, Av₂ = λ₂v₂ with λ₁ ≠ λ₂. Then
λ₁(v₁·v₂) = (Av₁)ᵀv₂ = v₁ᵀAᵀv₂ = v₁ᵀAv₂ = v₁ᵀ(λ₂v₂) = λ₂(v₁·v₂)
So (λ₁ − λ₂)(v₁·v₂) = 0, and since λ₁ ≠ λ₂, **v₁·v₂ = 0** ✓ ∎

> **Theorem 11.2.** All eigenvalues of a real symmetric matrix are **real**.

*Proof.* Let Av = λv with possibly complex λ, v ≠ 0. Take the conjugate transpose:
v*Av = λ(v*v) = λ‖v‖².
But also v*Av = (v*Av)* since it's a 1×1 matrix equal to its own conjugate transpose:
(v*Av)* = v*A*v = v*Aᵀv = v*Av (using A real symmetric).
So v*Av is **real**. Since ‖v‖² > 0 is real, **λ must be real** ✓ ∎

### 11.2.2 The Spectral Theorem

> **Theorem 11.3 (Spectral Theorem for Symmetric Matrices).** An n×n matrix A is symmetric **⟺** it is **orthogonally diagonalizable**:
>
> **A = QDQᵀ** where Q is orthogonal (QᵀQ = I) and D is real diagonal.
>
> Equivalently, ℝⁿ has an **orthonormal basis consisting of eigenvectors of A**.

Moreover, for a symmetric A:
- all eigenvalues are real,
- **GM(λ) = AM(λ) for every λ** (never defective),
- the eigenspaces are mutually orthogonal and together span ℝⁿ.

**The (⟸) direction is easy:** if A = QDQᵀ then Aᵀ = (QDQᵀ)ᵀ = QDᵀQᵀ = QDQᵀ = A ✓
**The (⟹) direction** requires more work (usually Schur's theorem or induction), but the statement is what you need.

> **Spectral decomposition.** Writing Q = [q₁ ... qₙ],
>
> **A = λ₁q₁q₁ᵀ + λ₂q₂q₂ᵀ + ... + λₙqₙqₙᵀ**
>
> A sum of rank-one **projection** matrices, weighted by the eigenvalues. Each qᵢqᵢᵀ projects onto the i-th eigendirection.

**Procedure for orthogonal diagonalization:**
1. Find the eigenvalues.
2. Find a basis for each eigenspace.
3. **Apply Gram–Schmidt within each eigenspace** (needed only for repeated eigenvalues; distinct eigenvalues give orthogonal vectors automatically).
4. Normalize everything.
5. Assemble Q.

### 11.2.3 Quadratic Forms

> **Definition.** A **quadratic form** on ℝⁿ is Q(x) = xᵀAx with A symmetric.

Expanded: Q(x) = Σᵢ aᵢᵢxᵢ² + 2Σ_{i<j} aᵢⱼxᵢxⱼ.

**To build A from a formula:** the coefficient of xᵢ² goes in position (i,i); the coefficient of xᵢxⱼ is **split in half** between positions (i,j) and (j,i).

*Example:* Q = 5x₁² + 3x₂² − 4x₁x₂ → A = [[5, −2], [−2, 3]].

> **Theorem 11.4 (Principal Axes Theorem).** If A is symmetric with A = QDQᵀ, the change of variable **x = Qy** transforms
>
> **xᵀAx = yᵀDy = λ₁y₁² + λ₂y₂² + ... + λₙyₙ²**
>
> — a form with **no cross-product terms**.

The columns of Q are the **principal axes**. Geometrically, the level set xᵀAx = c is a conic/quadric whose axes of symmetry are exactly these eigenvector directions, with semi-axis lengths √(c/λᵢ).

### 11.2.4 Classification of Quadratic Forms

| Type | Definition | Eigenvalue test |
|---|---|---|
| **Positive definite** | Q(x) > 0 for all x ≠ 0 | all λᵢ > 0 |
| **Positive semidefinite** | Q(x) ≥ 0 for all x | all λᵢ ≥ 0 |
| **Negative definite** | Q(x) < 0 for all x ≠ 0 | all λᵢ < 0 |
| **Negative semidefinite** | Q(x) ≤ 0 for all x | all λᵢ ≤ 0 |
| **Indefinite** | Q takes both signs | some λᵢ > 0, some < 0 |

**Sylvester's Criterion (leading principal minors test).** Let Δ_k be the determinant of the top-left k×k submatrix.

> A is **positive definite ⟺ Δ₁ > 0, Δ₂ > 0, ..., Δₙ > 0** (all leading principal minors positive).
> A is **negative definite ⟺ the signs alternate**: Δ₁ < 0, Δ₂ > 0, Δ₃ < 0, ...

*Warning:* for **semi**definiteness, the leading principal minors are not enough — you must check **all** principal minors (not just the leading ones). Classic counterexample: A = [[0, 0], [0, −1]] has Δ₁ = 0, Δ₂ = 0, yet A is negative semidefinite, not positive semidefinite.

**Other equivalent characterizations of positive definiteness (A symmetric):**
1. All eigenvalues positive
2. All leading principal minors positive
3. **A = BᵀB for some B with independent columns**
4. **A = LLᵀ** for a unique lower-triangular L with positive diagonal (**Cholesky factorization**)
5. All pivots in Gaussian elimination (without row swaps) are positive

**Useful facts:**
- If A is positive definite, so is A⁻¹ (eigenvalues 1/λᵢ > 0).
- For **any** m×n matrix A, **AᵀA is positive semidefinite**; it is positive definite ⟺ A has independent columns.
- A positive definite ⟹ aᵢᵢ > 0 for all i (take x = eᵢ), and det A > 0.

### 11.2.5 Cholesky Factorization

For positive definite A, there is a unique lower-triangular L with positive diagonal and **A = LLᵀ**. Computation (2×2 illustration):

```
[[a, b], [b, c]] = [[l₁₁, 0], [l₂₁, l₂₂]]·[[l₁₁, l₂₁], [0, l₂₂]]
```
gives l₁₁ = √a, l₂₁ = b/l₁₁, l₂₂ = √(c − l₂₁²).

Cholesky is about **twice as fast** as LU and is the standard method for solving positive definite systems (which is what least squares produces).

### 11.2.6 Constrained Optimization (Rayleigh Quotient)

> **Theorem 11.5.** For symmetric A with eigenvalues λ₁ ≥ λ₂ ≥ ... ≥ λₙ:
>
> **max_{‖x‖=1} xᵀAx = λ₁**, attained at the unit eigenvector for λ₁
> **min_{‖x‖=1} xᵀAx = λₙ**, attained at the unit eigenvector for λₙ

The ratio R(x) = (xᵀAx)/(xᵀx) is the **Rayleigh quotient**; it always lies in [λₙ, λ₁].

Further: the max of xᵀAx subject to ‖x‖ = 1 **and** x ⊥ q₁ is λ₂, attained at q₂. This nested structure is exactly what makes PCA work — each principal component is the best direction orthogonal to all the previous ones.

### 11.2.7 Similar Matrices

> **Definition.** A ~ B (similar) if B = P⁻¹AP for some invertible P.

Similarity is an **equivalence relation**: reflexive (P = I), symmetric (A = (P⁻¹)⁻¹B P⁻¹), transitive.

**Invariants (shared by similar matrices):**
characteristic polynomial · eigenvalues with AM · geometric multiplicities · trace · determinant · rank · nullity · minimal polynomial · Jordan form · diagonalizability

**Not invariants:** the entries, eigenvectors (they transform), symmetry, orthogonality of columns, singular values.

**Orthogonal similarity** (B = QᵀAQ with Q orthogonal) is stronger and additionally preserves symmetry, singular values, and the Frobenius norm.

**Congruence** (B = PᵀAP, P invertible but not necessarily orthogonal) preserves **signs of eigenvalues** but not their values:

> **Sylvester's Law of Inertia.** Congruent symmetric matrices have the same **inertia** — the same number of positive, negative, and zero eigenvalues.

---

## 11.3 Solved Examples

### Example 11.1 — [Easy] Orthogonal diagonalization, distinct eigenvalues

Orthogonally diagonalize A = [[3, 1], [1, 3]].

**Solution.** p(λ) = (3−λ)² − 1 = λ² − 6λ + 8 = (λ−4)(λ−2). **λ = 4, 2.**

λ=4: A − 4I = [[−1, 1], [1, −1]] → **v = (1, 1)**
λ=2: A − 2I = [[1, 1], [1, 1]] → **v = (1, −1)**

**Check orthogonality:** (1,1)·(1,−1) = 0 ✓ (automatic, by Theorem 11.1).

Normalize: q₁ = (1/√2)(1,1), q₂ = (1/√2)(1,−1).

```
Q = (1/√2)[[1,  1],       D = [[4, 0],
           [1, −1]]            [0, 2]]
```

**Verify A = QDQᵀ.**
QD = (1/√2)[[4, 2], [4, −2]].
QDQᵀ = (1/2)[[4, 2],[4,−2]]·[[1, 1],[1,−1]] = (1/2)[[4+2, 4−2],[4−2, 4+2]] = (1/2)[[6, 2],[2, 6]] = [[3,1],[1,3]] ✓

**Spectral decomposition:**
A = 4·q₁q₁ᵀ + 2·q₂q₂ᵀ = 4·(1/2)[[1,1],[1,1]] + 2·(1/2)[[1,−1],[−1,1]] = [[2,2],[2,2]] + [[1,−1],[−1,1]] = [[3,1],[1,3]] ✓

---

### Example 11.2 — [Easy] Definiteness by eigenvalues and by minors

Classify Q(x) = 2x₁² + 5x₂² + 4x₁x₂.

**Solution.** A = [[2, 2], [2, 5]].

**Method 1 — eigenvalues.** p(λ) = λ² − 7λ + (10 − 4) = λ² − 7λ + 6 = (λ−1)(λ−6). **λ = 1, 6** — both positive → **positive definite**.

**Method 2 — Sylvester.** Δ₁ = 2 > 0 ✓; Δ₂ = det A = 10 − 4 = 6 > 0 ✓ → **positive definite** ✓

**Confirmation by completing the square:**
2x₁² + 4x₁x₂ + 5x₂² = 2(x₁² + 2x₁x₂) + 5x₂² = 2(x₁ + x₂)² − 2x₂² + 5x₂² = **2(x₁+x₂)² + 3x₂²**
A sum of positive multiples of squares, zero only when x₂ = 0 and x₁ + x₂ = 0, i.e. x = 0 ✓

---

### Example 11.3 — [Medium] Repeated eigenvalue — Gram–Schmidt required

Orthogonally diagonalize A = [[3, −2, 4], [−2, 6, 2], [4, 2, 3]].

**Solution.** Characteristic polynomial. tr A = 12. One finds

p(λ) = −(λ−7)²(λ+2)

*(Check: 7 + 7 − 2 = 12 ✓)*

**λ = −2:** A + 2I = [[5, −2, 4], [−2, 8, 2], [4, 2, 5]].
Row reduce: `R₂ → 5R₂ + 2R₁` → (0, 36, 18) → simplify (0, 2, 1).
`R₃ → 5R₃ − 4R₁` → (0, 18, 9) → (0, 2, 1) — same row.
From (0,2,1): 2v₂ + v₃ = 0 → v₃ = −2v₂.
From row 1: 5v₁ − 2v₂ + 4(−2v₂) = 0 → 5v₁ = 10v₂ → v₁ = 2v₂.
Take v₂ = 1: **v = (2, 1, −2)**. ‖v‖ = 3.
**q₃ = (1/3)(2, 1, −2)**

**λ = 7:** A − 7I = [[−4, −2, 4], [−2, −1, 2], [4, 2, −4]].
All rows are multiples of (2, 1, −2) → rank 1 → **GM = 2 ✓** (matches AM)
Solve 2v₁ + v₂ − 2v₃ = 0. Free: v₁, v₃ (say). v₂ = 2v₃ − 2v₁.
Basis: taking (v₁,v₃) = (1,0) → **u₁ = (1, −2, 0)**; taking (0,1) → **u₂ = (0, 2, 1)**.

These two are **not orthogonal**: u₁·u₂ = 0 − 4 + 0 = −4 ≠ 0. **Apply Gram–Schmidt.**

w₁ = u₁ = (1, −2, 0), w₁·w₁ = 5.
w₂ = u₂ − (−4/5)w₁ = (0,2,1) + (4/5)(1,−2,0) = (4/5, 2 − 8/5, 1) = (4/5, 2/5, 1).
Scale by 5: **w₂ = (4, 2, 5)**.
*Check w₁·w₂ = 4 − 4 + 0 = 0 ✓*

Norms: ‖w₁‖ = √5, ‖w₂‖ = √(16+4+25) = √45 = 3√5.

**q₁ = (1/√5)(1, −2, 0), q₂ = (1/(3√5))(4, 2, 5), q₃ = (1/3)(2, 1, −2)**

*Cross-check q₃ ⊥ q₁:* (2,1,−2)·(1,−2,0) = 2 − 2 = 0 ✓
*q₃ ⊥ q₂:* (2,1,−2)·(4,2,5) = 8 + 2 − 10 = 0 ✓

```
Q = [[1/√5,   4/(3√5),  2/3],
     [−2/√5,  2/(3√5),  1/3],
     [0,      5/(3√5), −2/3]]

D = diag(7, 7, −2)
```

**A = QDQᵀ** ✓

---

### Example 11.4 — [Medium] Principal axes of a conic

Identify and sketch the conic 5x₁² − 4x₁x₂ + 5x₂² = 48.

**Solution.** A = [[5, −2], [−2, 5]].

p(λ) = (5−λ)² − 4 = λ² − 10λ + 21 = (λ−3)(λ−7). **λ = 3, 7** — both positive → an **ellipse**.

λ=3: A − 3I = [[2,−2],[−2,2]] → **v = (1, 1)** → q₁ = (1/√2)(1,1)
λ=7: A − 7I = [[−2,−2],[−2,−2]] → **v = (1, −1)** → q₂ = (1/√2)(1,−1)

With x = Qy the equation becomes **3y₁² + 7y₂² = 48**, i.e.

> y₁²/16 + y₂²/(48/7) = 1

**Semi-axes:** a = 4 along the q₁ = (1,1)/√2 direction; b = √(48/7) = 4√(3/7) ≈ 2.619 along q₂ = (1,−1)/√2.

**Answer:** an **ellipse** with major axis of length 8 along the line y = x, minor axis of length ≈ 5.24 along y = −x, centred at the origin. The principal axes are rotated 45° from the coordinate axes — exactly the information the cross term −4x₁x₂ was encoding.

*Verification:* the point 4q₁ = (4/√2)(1,1) = (2√2, 2√2) should be on the conic:
5(8) − 4(8) + 5(8) = 40 − 32 + 40 = 48 ✓

---

### Example 11.5 — [Hard] Classification with a parameter

For which values of k is Q(x) = x₁² + kx₂² + 3x₃² + 2x₁x₂ − 4x₁x₃ positive definite?

**Solution.** The symmetric matrix (cross-coefficients halved):
```
A = [[ 1,  1, −2],
     [ 1,  k,  0],
     [−2,  0,  3]]
```

**Apply Sylvester's criterion.**

**Δ₁ = 1 > 0** ✓ (always)

**Δ₂ = det [[1, 1], [1, k]] = k − 1 > 0 → k > 1**

**Δ₃ = det A.** Expand along row 3:
= −2·det[[1, −2], [k, 0]] − 0 + 3·det[[1, 1], [1, k]]

Careful with signs: cofactor expansion along row 3, entries (−2, 0, 3):
- C₃₁ = (+1)^{3+1}·det[[1, −2],[k, 0]] = (0 + 2k) = 2k
- C₃₂ = (−1)^{3+2}·det[[1, −2],[1, 0]] = −(0 + 2) = −2
- C₃₃ = (+1)^{3+3}·det[[1, 1],[1, k]] = k − 1

det A = (−2)(2k) + (0)(−2) + (3)(k − 1) = −4k + 3k − 3 = **−k − 3**

For positive definiteness we need **−k − 3 > 0 → k < −3**.

**Conflict!** We need k > 1 (from Δ₂) **and** k < −3 (from Δ₃) simultaneously — **impossible**.

**Answer: there is NO value of k making Q positive definite.**

*Verification of the obstruction.* Look at the x₁–x₃ part: Q contains x₁² + 3x₃² − 4x₁x₃, whose matrix [[1, −2], [−2, 3]] has determinant 3 − 4 = −1 < 0 — already indefinite, and **no choice of k touches those terms**. Setting x₂ = 0, x₁ = 2, x₃ = 1 gives Q = 4 + 3 − 8 = **−1 < 0** regardless of k ✓

*(Lesson: a principal submatrix that fails the test cannot be rescued by the remaining variables. Always look for such a sub-obstruction before grinding through determinants.)*

---

### Example 11.6 — [Hard] Cholesky factorization

Find the Cholesky factorization of A = [[4, 2, −2], [2, 5, 1], [−2, 1, 6]], after verifying A is positive definite.

**Solution.**

**Verify positive definiteness (Sylvester).**
Δ₁ = 4 > 0 ✓
Δ₂ = det[[4,2],[2,5]] = 20 − 4 = 16 > 0 ✓
Δ₃ = det A: expand along row 1
= 4(30 − 1) − 2(12 + 2) + (−2)(2 + 10) = 4(29) − 2(14) − 2(12) = 116 − 28 − 24 = **64 > 0** ✓
**Positive definite** ✓

**Compute L** with A = LLᵀ, L lower triangular:
```
L = [[l₁₁, 0,   0  ],
     [l₂₁, l₂₂, 0  ],
     [l₃₁, l₃₂, l₃₃]]
```

Matching entries of LLᵀ to A:

**Column 1:**
- (1,1): l₁₁² = 4 → **l₁₁ = 2**
- (2,1): l₂₁l₁₁ = 2 → **l₂₁ = 1**
- (3,1): l₃₁l₁₁ = −2 → **l₃₁ = −1**

**Column 2:**
- (2,2): l₂₁² + l₂₂² = 5 → 1 + l₂₂² = 5 → **l₂₂ = 2**
- (3,2): l₃₁l₂₁ + l₃₂l₂₂ = 1 → (−1)(1) + 2l₃₂ = 1 → 2l₃₂ = 2 → **l₃₂ = 1**

**Column 3:**
- (3,3): l₃₁² + l₃₂² + l₃₃² = 6 → 1 + 1 + l₃₃² = 6 → **l₃₃ = 2**

```
L = [[ 2, 0, 0],
     [ 1, 2, 0],
     [−1, 1, 2]]
```

**Verify LLᵀ:**
Row 3 · Row 3 = 1 + 1 + 4 = 6 ✓
Row 2 · Row 3 = (1)(−1) + (2)(1) + 0 = 1 ✓
Row 1 · Row 3 = (2)(−1) = −2 ✓
**A = LLᵀ** ✓

*Note det A = (det L)² = (2·2·2)² = 64 ✓ matching Δ₃.*

**Using it to solve Ax = (2, 7, 9)ᵀ:**
Forward-solve Ly = b: 2y₁ = 2 → y₁ = 1; 1 + 2y₂ = 7 → y₂ = 3; −1 + 3 + 2y₃ = 9 → y₃ = 3.5.
Back-solve Lᵀx = y: 2x₃ = 3.5 → x₃ = 1.75; 2x₂ + 1(1.75) = 3 → x₂ = 0.625; 2x₁ + 1(0.625) − 1(1.75) = 1 → 2x₁ = 2.125 → x₁ = 1.0625.
**x = (1.0625, 0.625, 1.75)ᵀ**

---

### Example 11.7 — [Very Hard] Rayleigh quotient and constrained optimization

For A = [[6, −2, −1], [−2, 6, −1], [−1, −1, 5]], find the maximum and minimum of xᵀAx subject to ‖x‖ = 1, and the maximizing/minimizing vectors. Then find the maximum subject to the additional constraint that x is orthogonal to the maximizer.

**Solution.**

**Find eigenvalues.** Guess structure: rows 1 and 2 are symmetric under swapping coordinates 1 and 2.

Try v = (1, −1, 0): Av = (6+2, −2−6, −1+1) = (8, −8, 0) = 8v ✓ **λ = 8**

Try v = (1, 1, c): Av = (6 − 2 − c, −2 + 6 − c, −1 − 1 + 5c) = (4 − c, 4 − c, 5c − 2).
For this to equal λ(1,1,c): λ = 4 − c and λc = 5c − 2.
Substituting: (4−c)c = 5c − 2 → 4c − c² = 5c − 2 → c² + c − 2 = 0 → (c+2)(c−1) = 0.
- c = 1: λ = 3, **v = (1, 1, 1)**
- c = −2: λ = 6, **v = (1, 1, −2)**

**Eigenvalues: 8, 6, 3.** *(Check trace: 8 + 6 + 3 = 17 = 6 + 6 + 5 ✓)*

**Orthogonality check:** (1,−1,0)·(1,1,1) = 0 ✓; (1,−1,0)·(1,1,−2) = 0 ✓; (1,1,1)·(1,1,−2) = 1+1−2 = 0 ✓

**Answers.**
- **Maximum of xᵀAx on ‖x‖=1 is λ_max = 8**, attained at **x = ±(1/√2)(1, −1, 0)**.
- **Minimum is λ_min = 3**, attained at **x = ±(1/√3)(1, 1, 1)**.

*Verification of the max:* x = (1/√2)(1,−1,0). xᵀAx = (1/2)(1,−1,0)·A(1,−1,0)ᵀ = (1/2)(1,−1,0)·(8,−8,0) = (1/2)(8 + 8) = 8 ✓

**With the extra constraint x ⊥ q₁ where q₁ = (1,−1,0)/√2:**

By the nested version of Theorem 11.5, the maximum over the orthogonal complement of the top eigenvector is the **second-largest eigenvalue**:

**Maximum = 6**, attained at **x = ±(1/√6)(1, 1, −2)** ✓

*Check that this vector is orthogonal to q₁:* (1,1,−2)·(1,−1,0) = 0 ✓
*Check the value:* A(1,1,−2)ᵀ = (6 − 2 + 2, −2 + 6 + 2, −1 − 1 − 10) = (6, 6, −12) = 6(1,1,−2) ✓
xᵀAx = (1/6)(1,1,−2)·(6,6,−12) = (1/6)(6 + 6 + 24) = 36/6 = 6 ✓

*(This nested maximization is precisely the definition of successive principal components in PCA.)*

---

### Example 11.8 — [Very Hard] Sylvester's Law of Inertia

Let A = [[1, 2], [2, 1]] and P = [[1, 1], [0, 1]]. Compute B = PᵀAP. Verify that A and B have different eigenvalues but the same inertia. Then explain the general principle.

**Solution.**

**Eigenvalues of A:** p(λ) = (1−λ)² − 4 = λ² − 2λ − 3 = (λ−3)(λ+1). **λ = 3, −1.**
**Inertia of A: (n₊, n₋, n₀) = (1, 1, 0)** — one positive, one negative. A is **indefinite**.

**Compute B = PᵀAP.**
```
Pᵀ = [[1, 0], [1, 1]]
AP = [[1,2],[2,1]]·[[1,1],[0,1]] = [[1, 1+2], [2, 2+1]] = [[1, 3], [2, 3]]
B = PᵀAP = [[1,0],[1,1]]·[[1,3],[2,3]] = [[1, 3], [1+2, 3+3]] = [[1, 3], [3, 6]]
```
B is symmetric ✓ (as it must be: (PᵀAP)ᵀ = PᵀAᵀP = PᵀAP).

**Eigenvalues of B:** p(λ) = λ² − 7λ + (6 − 9) = λ² − 7λ − 3.
λ = [7 ± √(49 + 12)]/2 = [7 ± √61]/2.
√61 ≈ 7.810 → **λ ≈ 7.405 and λ ≈ −0.405.**

**Comparison:**
| | A | B |
|---|---|---|
| eigenvalues | 3, −1 | 7.405, −0.405 |
| trace | 2 | 7 |
| determinant | −3 | −3 |
| **inertia** | **(1, 1, 0)** | **(1, 1, 0)** ✓ |

The eigenvalues are **completely different** — so A and B are **not similar**. But the *number* of positive and negative eigenvalues is the same ✓

**The general principle (Sylvester's Law of Inertia).**

> If A is symmetric and P invertible, then A and PᵀAP (called **congruent**) have the same number of positive, negative, and zero eigenvalues.

*Why this is the right invariant.* Congruence corresponds to a **change of variables** x = Py in the quadratic form:
Q(x) = xᵀAx becomes yᵀ(PᵀAP)y.
A change of variables cannot change **whether** the form is positive, negative, or zero on a given vector — it only relabels which vector we call it. So the *signs* survive while the *magnitudes* do not.

**Formal argument.** Let n₊(A) = max dimension of a subspace on which Q is positive definite. This description makes no reference to coordinates, only to the form itself. Since x ↦ P⁻¹x is a bijection between subspaces of the same dimension, n₊ is preserved by congruence. Same for n₋ and n₀ = nullity ✓ ∎

**Consequence.** Every symmetric matrix is congruent to a **diagonal matrix of ±1s and 0s**:
```
diag(1, ..., 1, −1, ..., −1, 0, ..., 0)
      n₊ times   n₋ times   n₀ times
```
and the triple (n₊, n₋, n₀) is a **complete invariant** for congruence. Two real symmetric matrices are congruent ⟺ they have the same inertia.

*Check for our example:* A has inertia (1,1,0), so A is congruent to diag(1, −1). And indeed completing the square:
x₁² + 4x₁x₂ + x₂² = (x₁ + 2x₂)² − 3x₂² = u² − 3v² → signs (+, −) ✓

---

## 11.4 Practice Numericals — Chapter 11

**[Easy]**

**P11.1** Is A = [[2, 3], [3, 5]] symmetric? Find its eigenvalues and verify they are real.

**P11.2** Write the symmetric matrix for Q(x) = 4x₁² − 6x₁x₂ + x₂².

**P11.3** Classify Q(x) = 3x₁² + 2x₂² using eigenvalues.

**P11.4** Orthogonally diagonalize A = [[1, 2], [2, 1]].

**P11.5** State whether A = [[1, 0], [0, −3]] is positive definite, negative definite, or indefinite.

**[Medium]**

**P11.6** Orthogonally diagonalize A = [[5, −4], [−4, 5]] and write the spectral decomposition.

**P11.7** Determine the definiteness of A = [[2, −1, 0], [−1, 2, −1], [0, −1, 2]] using Sylvester's criterion.

**P11.8** Find the Cholesky factorization of A = [[9, 3], [3, 5]].

**P11.9** Identify the conic 2x₁² + 4x₁x₂ + 2x₂² = 8 (note the repeated eigenvalue possibility).

**P11.10** Show that AᵀA is always symmetric and positive semidefinite, for any m×n matrix A.

**P11.11** Are A = [[1, 2], [0, 3]] and B = [[3, 0], [0, 1]] similar? Justify.

**[Hard]**

**P11.12** Orthogonally diagonalize A = [[2, 1, 1], [1, 2, 1], [1, 1, 2]].

**P11.13** Find max and min of xᵀAx on ‖x‖ = 1 for A = [[4, 1], [1, 4]], and the optimizing vectors.

**P11.14** For which values of a is A = [[a, 1, 0], [1, a, 1], [0, 1, a]] positive definite?

**P11.15** Classify the quadratic form Q = x₁² + 2x₂² + 3x₃² − 2x₁x₂ + 2x₂x₃ and write it as a sum/difference of squares.

**P11.16** Prove that if A is symmetric positive definite, then every diagonal entry is positive, and det A > 0. Is the converse true?

**P11.17** Show that two matrices with the same characteristic polynomial need not be similar, and give the minimal 2×2 counterexample.

**[Very Hard]**

**P11.18** Prove the spectral theorem in the 2×2 case: every real symmetric 2×2 matrix is orthogonally diagonalizable. Do this explicitly by finding the rotation angle that eliminates the off-diagonal entry.

**P11.19** Let A be symmetric with eigenvalues λ₁ ≥ ... ≥ λₙ. Prove that for any x, λₙ‖x‖² ≤ xᵀAx ≤ λ₁‖x‖², and characterize the equality cases.

**P11.20** Prove that a symmetric matrix A is positive semidefinite if and only if A = BᵀB for some matrix B. Construct B explicitly from the spectral decomposition.

**P11.21** **(Simultaneous diagonalization of quadratic forms.)** Let A be symmetric positive definite and B symmetric. Prove there is an invertible P with PᵀAP = I and PᵀBP diagonal. Apply this to A = [[2, 1], [1, 2]], B = [[1, 0], [0, −1]].

---

## 11.5 Solutions to Chapter 11 Practice

**S11.1** Aᵀ = [[2,3],[3,5]] = A ✓ **symmetric.**
p(λ) = λ² − 7λ + (10 − 9) = λ² − 7λ + 1.
λ = [7 ± √45]/2 = [7 ± 3√5]/2 ≈ **6.854 and 0.146** — both real ✓ (guaranteed by Theorem 11.2).

**S11.2** Coefficient of x₁x₂ is −6, so off-diagonal entries are −3.
**A = [[4, −3], [−3, 1]]**

**S11.3** A = diag(3, 2). Eigenvalues 3, 2 — both positive → **positive definite**.

**S11.4** p(λ) = (1−λ)² − 4 → λ² − 2λ − 3 = (λ−3)(λ+1). **λ = 3, −1.**
λ=3: **(1,1)**; λ=−1: **(1,−1)**. Orthogonal ✓
**Q = (1/√2)[[1, 1], [1, −1]], D = diag(3, −1)**

**S11.5** Eigenvalues 1 and −3 — **indefinite** (mixed signs).

**S11.6** p(λ) = (5−λ)² − 16 = λ² − 10λ + 9 = (λ−1)(λ−9). **λ = 9, 1.**
λ=9: A − 9I = [[−4,−4],[−4,−4]] → **(1, −1)**
λ=1: A − I = [[4,−4],[−4,4]] → **(1, 1)**
**Q = (1/√2)[[1, 1], [−1, 1]], D = diag(9, 1)**

**Spectral decomposition:**
A = 9·(1/2)[[1,−1],[−1,1]] + 1·(1/2)[[1,1],[1,1]]
= [[4.5, −4.5],[−4.5, 4.5]] + [[0.5, 0.5],[0.5, 0.5]] = [[5, −4],[−4, 5]] ✓

**S11.7** Δ₁ = 2 > 0 ✓
Δ₂ = det[[2,−1],[−1,2]] = 4 − 1 = 3 > 0 ✓
Δ₃ = det A = 2(4−1) − (−1)(−2 − 0) + 0 = 6 − 2 = **4 > 0** ✓
**Positive definite.**
*(This is the discrete second-difference matrix; by S9.16's formula its eigenvalues are 2 + 2cos(kπ/4) = 2 ± √2 and 2, all positive ✓)*

**S11.8** l₁₁ = √9 = 3. l₂₁ = 3/3 = 1. l₂₂ = √(5 − 1) = 2.
**L = [[3, 0], [1, 2]]**
*Check LLᵀ = [[9, 3], [3, 1 + 4]] = [[9,3],[3,5]] ✓*

**S11.9** A = [[2, 2], [2, 2]]. p(λ) = λ² − 4λ + 0 = λ(λ−4). **λ = 4, 0.**
One eigenvalue is **zero** → the form is positive **semi**definite, and the conic is **degenerate**.
In principal coordinates: 4y₁² = 8 → y₁ = ±√2 — **a pair of parallel lines**, not an ellipse.
In original coordinates: 2(x₁+x₂)² = 8 → x₁ + x₂ = ±2. ✓ **Two parallel lines.**

**S11.10** **Symmetry:** (AᵀA)ᵀ = Aᵀ(Aᵀ)ᵀ = AᵀA ✓
**Positive semidefiniteness:** for any x,
xᵀ(AᵀA)x = (Ax)ᵀ(Ax) = **‖Ax‖² ≥ 0** ✓
Equality holds ⟺ Ax = 0. So AᵀA is **positive definite ⟺ Nul(A) = {0} ⟺ columns of A are independent** ✓ ∎

**S11.11** Both are triangular with eigenvalues **{1, 3}** — same characteristic polynomial.
A has 2 distinct eigenvalues → **diagonalizable** → similar to diag(1,3) = ... and B is already diag(3,1), which is similar to diag(1,3) by a permutation.
**Yes, A and B are similar.** ✓
Explicitly: eigenvectors of A are (1,0) for λ=1 and (1,1) for λ=3. With P = [[1,1],[0,1]], P⁻¹AP = diag(1,3), which is a permutation-similarity away from B.

**S11.12** A = J + I where J is the 3×3 all-ones matrix.
By Example 9.8: J has eigenvalues 3 (eigenvector (1,1,1)) and 0 (multiplicity 2).
**A = J + I has eigenvalues 4 and 1 (multiplicity 2).**

λ=4: **(1, 1, 1)** → q₁ = (1/√3)(1,1,1)
λ=1: eigenspace Nul(J) = {x : Σxᵢ = 0}. Basis {(1,−1,0), (1,0,−1)} — not orthogonal (dot = 1).
**Gram–Schmidt:** w₁ = (1,−1,0), w₁·w₁ = 2.
w₂ = (1,0,−1) − (1/2)(1,−1,0) = (1/2, 1/2, −1) → scale ×2: **(1, 1, −2)**.
Check: (1,−1,0)·(1,1,−2) = 0 ✓
Norms: √2 and √6.

**q₂ = (1/√2)(1,−1,0), q₃ = (1/√6)(1,1,−2)**
```
Q = [[1/√3,  1/√2,  1/√6],
     [1/√3, −1/√2,  1/√6],
     [1/√3,  0,    −2/√6]]
D = diag(4, 1, 1)
```

**S11.13** p(λ) = (4−λ)² − 1 = λ² − 8λ + 15 = (λ−3)(λ−5). **λ = 5, 3.**
**Max = 5** at x = ±(1/√2)(1, 1) *(eigenvector for λ=5: A−5I = [[−1,1],[1,−1]] → (1,1) ✓)*
**Min = 3** at x = ±(1/√2)(1, −1)

**S11.14** Δ₁ = a > 0 → **a > 0**
Δ₂ = a² − 1 > 0 → **|a| > 1**, combined with a > 0 gives **a > 1**
Δ₃ = det A. Expand along row 1:
= a(a² − 1) − 1(a − 0) + 0 = a³ − a − a = **a³ − 2a = a(a² − 2)**
Need a(a² − 2) > 0 with a > 0 → a² > 2 → **a > √2**

**Answer: a > √2** (the binding constraint).
*Sanity check with eigenvalues: using the tridiagonal formula (S9.16), λ_k = a + 2cos(kπ/4) for k=1,2,3, i.e. a + √2, a, a − √2. All positive ⟺ a > √2 ✓ — a perfect match.*

**S11.15**
```
A = [[ 1, −1,  0],
     [−1,  2,  1],
     [ 0,  1,  3]]
```
**Sylvester:** Δ₁ = 1 > 0; Δ₂ = 2 − 1 = 1 > 0; Δ₃ = 1(6−1) + 1(−3 − 0) + 0 = 5 − 3 = **2 > 0** ✓
**Positive definite.**

**Sum of squares (completing the square / Lagrange's method):**
Q = x₁² − 2x₁x₂ + 2x₂² + 2x₂x₃ + 3x₃²
= (x₁ − x₂)² − x₂² + 2x₂² + 2x₂x₃ + 3x₃²
= (x₁ − x₂)² + x₂² + 2x₂x₃ + 3x₃²
= (x₁ − x₂)² + (x₂ + x₃)² − x₃² + 3x₃²
= **(x₁ − x₂)² + (x₂ + x₃)² + 2x₃²**

All three coefficients positive → **positive definite** ✓ (consistent), and the inertia is (3, 0, 0).

**S11.16**
**Diagonal entries.** Take x = eᵢ. Then eᵢᵀAeᵢ = aᵢᵢ > 0 ✓

**Determinant.** det A = Πλᵢ, and all λᵢ > 0, so **det A > 0** ✓

**Converse is FALSE.** Counterexample: A = [[−1, 0], [0, −2]].
- Diagonal entries: both negative — so this fails the diagonal condition too. Better counterexample:
A = [[1, 3], [3, 1]]: diagonal entries 1, 1 both positive; det = 1 − 9 = −8 < 0 — fails det.
Try A = [[−1, 0], [0, −1]]: det = 1 > 0 ✓ but diagonal entries negative.

**Best counterexample satisfying BOTH conditions yet not positive definite:** need n ≥ 3.
A = diag(1, −1, −1): all... no, diagonal has negatives.

Use **A = [[1, 0, 0], [0, −1, 0], [0, 0, −1]]** — det = 1 > 0 but diagonal entries include negatives.

For a genuine counterexample with positive diagonal and positive determinant:
**A = [[1, 2, 0], [2, 1, 0], [0, 0, −1]]**: diagonal (1, 1, −1) — still has a negative.

The cleanest: **A = [[1, 0, 0], [0, 2, 3], [0, 3, 2]]** — all diagonal entries positive (1, 2, 2); det = 1(4 − 9) = **−5 < 0**. Fails det.

**Definitive counterexample:** **A = [[2, 3, 0], [3, 2, 0], [0, 0, −5]]**. Hmm, diagonal has −5.

Take **A = [[1, 2], [2, 1]] ⊕ [[1, 2], [2, 1]]** (4×4 block diagonal): all diagonal entries are 1 > 0; det = (1−4)(1−4) = 9 > 0 ✓; but eigenvalues are 3, −1, 3, −1 → **indefinite** ✓

**Conclusion: positive diagonal + positive determinant does NOT imply positive definite.** You need **all** leading principal minors positive, not just the first and last.

**S11.17** **Counterexample:** A = I₂ = [[1,0],[0,1]] and B = [[1, 1], [0, 1]].

Both have characteristic polynomial **(λ − 1)²** ✓

But they are **not similar**: for any invertible P,
P⁻¹IP = P⁻¹P = I ≠ B.
So I is similar only to itself, while B ≠ I. ∎

**Structural reason:** GM(1) = 2 for A but GM(1) = 1 for B, and geometric multiplicity is a similarity invariant. Equivalently, their minimal polynomials differ: (λ−1) versus (λ−1)².

**This is the minimal counterexample** — for 1×1 matrices the characteristic polynomial determines the matrix entirely.

**S11.18** Let A = [[a, b], [b, c]] be real symmetric. Take
Q = [[cos θ, −sin θ], [sin θ, cos θ]] and compute B = QᵀAQ.

The off-diagonal entry of B is
b₁₂ = (c − a)sin θ cos θ + b(cos²θ − sin²θ) = ((c−a)/2)sin 2θ + b cos 2θ

**Set b₁₂ = 0:**
((c−a)/2)sin 2θ = −b cos 2θ
**tan 2θ = 2b/(a − c)**

Such a θ always exists:
- If a ≠ c, take θ = (1/2)arctan(2b/(a−c)).
- If a = c and b ≠ 0, the equation becomes b cos 2θ = 0 → **2θ = π/2 → θ = 45°**.
- If a = c and b = 0, A is already diagonal — take θ = 0.

**In every case a rotation angle exists**, so QᵀAQ is diagonal with Q orthogonal ✓ ∎

*Example:* A = [[3,1],[1,3]] has a = c, b ≠ 0 → θ = 45°, giving Q = (1/√2)[[1,−1],[1,1]] ✓ matching Example 11.1 (up to column order/sign).

**Note:** the resulting diagonal entries are the eigenvalues (½)[(a+c) ± √((a−c)² + 4b²)], both real since the discriminant is a sum of squares — which also **reproves** that symmetric 2×2 matrices have real eigenvalues.

**S11.19** By the spectral theorem, A = QDQᵀ. Substitute y = Qᵀx (so ‖y‖ = ‖x‖, as Q is orthogonal):

xᵀAx = xᵀQDQᵀx = yᵀDy = Σᵢ λᵢyᵢ²

**Upper bound:** Σλᵢyᵢ² ≤ λ₁Σyᵢ² = λ₁‖y‖² = **λ₁‖x‖²** ✓
**Lower bound:** Σλᵢyᵢ² ≥ λₙΣyᵢ² = **λₙ‖x‖²** ✓ ∎

**Equality cases.**
- Upper equality requires Σ(λ₁ − λᵢ)yᵢ² = 0. Since every term is ≥ 0, each must vanish: yᵢ = 0 whenever λᵢ < λ₁. So **y is supported on the λ₁-eigenspace**, meaning **x ∈ E_{λ₁}** ✓
- Similarly, lower equality holds ⟺ **x ∈ E_{λₙ}** ✓

*(Dividing through by ‖x‖² gives Theorem 11.5 on the Rayleigh quotient.)*

**S11.20**
**(⇐)** If A = BᵀB then xᵀAx = ‖Bx‖² ≥ 0, so A is positive semidefinite ✓ (and symmetric, by S11.10).

**(⇒)** Suppose A is symmetric positive semidefinite. By the spectral theorem A = QDQᵀ with D = diag(λ₁,...,λₙ), all λᵢ ≥ 0.

Since each λᵢ ≥ 0, the **square root** D^{1/2} = diag(√λ₁, ..., √λₙ) is real. Define

> **B = D^{1/2}Qᵀ**

Then
BᵀB = (D^{1/2}Qᵀ)ᵀ(D^{1/2}Qᵀ) = Q D^{1/2}D^{1/2} Qᵀ = QDQᵀ = **A** ✓ ∎

**Bonus:** taking B = QD^{1/2}Qᵀ instead gives the unique **symmetric positive semidefinite square root** A^{1/2}, with (A^{1/2})² = A.

*Example:* A = [[5, 4], [4, 5]] has eigenvalues 9, 1 with Q = (1/√2)[[1,1],[1,−1]].
A^{1/2} = Q diag(3, 1) Qᵀ = (1/2)[[3+1, 3−1],[3−1, 3+1]] = **[[2, 1], [1, 2]]**.
*Check:* [[2,1],[1,2]]² = [[5, 4],[4, 5]] ✓

**S11.21**
**Construction.** Since A is symmetric positive definite, write A = QDQᵀ with all λᵢ > 0. Set

> **P₁ = QD^{−1/2}**

Then P₁ᵀAP₁ = D^{−1/2}Qᵀ(QDQᵀ)QD^{−1/2} = D^{−1/2}DD^{−1/2} = **I** ✓

Now let C = P₁ᵀBP₁. Since B is symmetric, so is C. By the spectral theorem, C = RΛRᵀ with R orthogonal and Λ diagonal.

Set **P = P₁R**. Then:
- **PᵀAP** = Rᵀ(P₁ᵀAP₁)R = RᵀIR = RᵀR = **I** ✓
- **PᵀBP** = Rᵀ(P₁ᵀBP₁)R = RᵀCR = RᵀRΛRᵀR = **Λ** (diagonal) ✓ ∎

*(Note: this is not orthogonal similarity — P is not orthogonal — so the diagonal entries of Λ are **not** the eigenvalues of B. They are the eigenvalues of A⁻¹B, the "generalized eigenvalues" of the pencil (B, A).)*

**Application.** A = [[2, 1], [1, 2]], B = [[1, 0], [0, −1]].

**Diagonalize A:** eigenvalues 3 and 1, eigenvectors (1,1) and (1,−1).
Q = (1/√2)[[1, 1], [1, −1]], D = diag(3, 1).
D^{−1/2} = diag(1/√3, 1).
**P₁ = QD^{−1/2} = (1/√2)[[1/√3, 1], [1/√3, −1]]**

**Compute C = P₁ᵀBP₁.**
BP₁ = (1/√2)[[1/√3, 1], [−1/√3, 1]]
P₁ᵀ = (1/√2)[[1/√3, 1/√3], [1, −1]]
C = (1/2)[[1/√3, 1/√3],[1,−1]]·[[1/√3, 1],[−1/√3, 1]]
- (1,1): (1/3 − 1/3) = 0
- (1,2): (1/√3 + 1/√3) = 2/√3
- (2,1): (1/√3 + 1/√3) = 2/√3
- (2,2): (1 − 1) = 0
**C = (1/2)[[0, 2/√3], [2/√3, 0]] = [[0, 1/√3], [1/√3, 0]]**

**Diagonalize C:** eigenvalues **±1/√3**, eigenvectors (1,1)/√2 and (1,−1)/√2.
**R = (1/√2)[[1, 1], [1, −1]]**, Λ = diag(1/√3, −1/√3).

**P = P₁R = (1/√2)[[1/√3, 1], [1/√3, −1]]·(1/√2)[[1,1],[1,−1]]**
= (1/2)[[1/√3 + 1, 1/√3 − 1], [1/√3 − 1, 1/√3 + 1]]

**Result:** PᵀAP = I and PᵀBP = diag(1/√3, −1/√3) ✓

**Check the inertia:** B has inertia (1, 1, 0), and so does diag(1/√3, −1/√3) ✓ — consistent with Sylvester's Law (Example 11.8).

*(The generalized eigenvalues ±1/√3 are the roots of det(B − μA) = 0: det[[1−2μ, −μ],[−μ, −1−2μ]] = −(1−2μ)(1+2μ) − μ² = −1 + 4μ² − μ² = 3μ² − 1 = 0 → μ = ±1/√3 ✓)*

---
# Chapter 12 — Linear Transformations

---

## 12.1 Explain Like I'm Five

A **transformation** is a rule that takes a vector in and gives a vector out. Think of it as a machine.

Most machines are unpredictable. But a **linear** machine obeys two promises:

1. **It doesn't care whether you add before or after.** Put in u + v, and you get the same thing as putting in u, putting in v, and adding the results afterwards.
2. **It doesn't care whether you scale before or after.** Double the input, and the output doubles.

That's the entire definition:
> T(u + v) = T(u) + T(v) and T(cu) = cT(u)

**Why is that such a strong promise?** Because it means the machine is completely determined by what it does to just a handful of inputs. If you tell me where T sends e₁, e₂, and e₃, I can compute T of *anything* in ℝ³ — because every vector is a combination of those three, and linearity lets me push T through the combination. Three answers determine infinitely many.

That's why every linear transformation on ℝⁿ **is** a matrix. The matrix is just a table recording where the basis vectors go. Matrices and linear transformations are two names for the same thing: one is the machine, the other is the instruction manual written in a particular coordinate system.

**Two questions you always ask about a machine:**

- **What gets crushed to zero?** That's the **kernel** (or null space). A machine with an empty kernel (only zero maps to zero) loses no information — it's *one-to-one*.
- **What can come out?** That's the **range** (or image). A machine whose range is the whole target space misses nothing — it's *onto*.

And these two are linked by an accounting law: **dimensions in = dimensions crushed + dimensions surviving**. That's Rank–Nullity again, wearing different clothes.

**Change of basis.** The same machine looks different depending on which coordinate system you describe it in. A rotation looks messy in a skewed coordinate system and beautifully simple in a well-chosen one. Diagonalization (Chapter 10) is exactly the search for the coordinate system in which the machine looks as simple as possible.

---

## 12.2 The Formal Theory

### 12.2.1 Definition

> **Definition.** Let V and W be vector spaces. A map T : V → W is a **linear transformation** (or **linear map**) if for all u, v ∈ V and all scalars c:
> **(i) T(u + v) = T(u) + T(v)** (additivity)
> **(ii) T(cu) = cT(u)** (homogeneity)

**Equivalent single condition:** T(cu + dv) = cT(u) + dT(v) for all scalars c, d.

**Immediate consequences:**
- **T(0) = 0** (take c = 0). *This is the fastest test for non-linearity: if T(0) ≠ 0, T is not linear.*
- T(−v) = −T(v)
- T(c₁v₁ + ... + c_kv_k) = c₁T(v₁) + ... + c_kT(v_k) — T "passes through" any linear combination

**Terminology.** When V = W, T is called a **linear operator**. When W = ℝ, T is a **linear functional**.

**Examples of linear maps:**
- T(x) = Ax for any fixed matrix A
- Differentiation D : Pₙ → P_{n−1}, D(p) = p′
- Integration I : C[a,b] → ℝ, I(f) = ∫ₐᵇ f
- Transpose T : M_{m×n} → M_{n×m}, T(A) = Aᵀ
- Trace tr : M_{n×n} → ℝ
- Projection, rotation, reflection, scaling, shear in ℝⁿ

**Examples that are NOT linear:**
- T(x) = x + b for b ≠ 0 (translation — T(0) = b ≠ 0). This is **affine**, not linear.
- T(x) = ‖x‖ (fails T(−x) = −T(x))
- T(x) = x² or T(A) = A² or T(A) = det A (for n ≥ 2)
- T(x₁, x₂) = (x₁x₂, x₁)

### 12.2.2 The Matrix of a Linear Transformation

> **Theorem 12.1 (Standard matrix).** Every linear transformation T : ℝⁿ → ℝᵐ is given by T(x) = Ax where
>
> **A = [T(e₁) T(e₂) ... T(eₙ)]**
>
> — the columns of A are the images of the standard basis vectors. A is called the **standard matrix** of T, and it is unique.

*Proof.* Write x = x₁e₁ + ... + xₙeₙ. Then
T(x) = x₁T(e₁) + ... + xₙT(eₙ) = [T(e₁) ... T(eₙ)]·x = Ax ✓ ∎

**General bases.** If B = {b₁,...,bₙ} is a basis for V and C = {c₁,...,c_m} for W, the **matrix of T relative to B and C** is

> **[T]_{C←B} = [ [T(b₁)]_C  [T(b₂)]_C  ...  [T(bₙ)]_C ]**

and it satisfies

> **[T(x)]_C = [T]_{C←B} · [x]_B**

For an operator T : V → V with a single basis B, we write **[T]_B**, the **B-matrix of T**.

### 12.2.3 Common Geometric Transformations in ℝ²

| Transformation | Standard matrix |
|---|---|
| Rotation by θ (counterclockwise) | [[cos θ, −sin θ], [sin θ, cos θ]] |
| Reflection in the x-axis | [[1, 0], [0, −1]] |
| Reflection in the y-axis | [[−1, 0], [0, 1]] |
| Reflection in the line y = x | [[0, 1], [1, 0]] |
| Reflection in the line y = −x | [[0, −1], [−1, 0]] |
| Reflection in the line through origin at angle θ | [[cos 2θ, sin 2θ], [sin 2θ, −cos 2θ]] |
| Horizontal shear by k | [[1, k], [0, 1]] |
| Vertical shear by k | [[1, 0], [k, 1]] |
| Scaling by (s₁, s₂) | [[s₁, 0], [0, s₂]] |
| Projection onto the x-axis | [[1, 0], [0, 0]] |
| Projection onto the line spanned by unit u | uuᵀ |

**Composition = multiplication:** if S has matrix A and T has matrix B, then **S ∘ T has matrix AB**. Note the order — the rightmost matrix acts first.

### 12.2.4 Kernel and Range

> **Definition.**
> **ker(T) = {v ∈ V : T(v) = 0}** — the **kernel** (null space)
> **range(T) = {T(v) : v ∈ V} ⊆ W** — the **range** (image)

> **Theorem 12.2.** ker(T) is a subspace of V; range(T) is a subspace of W.

For T(x) = Ax: **ker(T) = Nul(A)** and **range(T) = Col(A)**.

> **Definition.** rank(T) = dim range(T), nullity(T) = dim ker(T).

> **Theorem 12.3 (Rank–Nullity for transformations).** If V is finite-dimensional,
> **rank(T) + nullity(T) = dim V**

### 12.2.5 One-to-One and Onto

> **Definition.**
> T is **one-to-one (injective)** if T(u) = T(v) ⟹ u = v.
> T is **onto (surjective)** if range(T) = W.
> T is an **isomorphism** if it is both (bijective).

> **Theorem 12.4.** T is one-to-one **⟺ ker(T) = {0}** ⟺ nullity(T) = 0.

*Proof.* If ker(T) = {0} and T(u) = T(v), then T(u−v) = 0 so u − v ∈ ker(T) = {0}, giving u = v ✓ Conversely if T is one-to-one and T(v) = 0 = T(0), then v = 0 ✓ ∎

**For T(x) = Ax with A an m×n matrix:**

| Property | Condition |
|---|---|
| one-to-one | columns of A independent; rank = n; **pivot in every column** |
| onto | columns of A span ℝᵐ; rank = m; **pivot in every row** |
| isomorphism | m = n and A invertible |

**Dimension constraints:**
- T : V → W one-to-one ⟹ dim V ≤ dim W
- T : V → W onto ⟹ dim V ≥ dim W
- If **dim V = dim W** (finite), then **one-to-one ⟺ onto ⟺ isomorphism**. (This is the general form of the "square matrix" part of the IMT.)

> **Theorem 12.5.** V and W are isomorphic ⟺ **dim V = dim W**.

**Consequence:** every real n-dimensional vector space is isomorphic to ℝⁿ, via the coordinate map x ↦ [x]_B. This is why studying ℝⁿ loses no generality.

### 12.2.6 Change of Basis

> **Theorem 12.6.** Let B and C be bases of V. The **change-of-coordinates matrix** P_{C←B} whose columns are [b₁]_C, ..., [bₙ]_C satisfies
> **[x]_C = P_{C←B}[x]_B**
> and P_{C←B} is invertible, with (P_{C←B})⁻¹ = P_{B←C}.

**For ℝⁿ with the standard basis E:** if B = {b₁,...,bₙ}, let P_B = [b₁ ... bₙ]. Then
> x = P_B[x]_B and [x]_B = P_B⁻¹x
and for two bases B, C of ℝⁿ: **P_{C←B} = P_C⁻¹ P_B**.

> **Theorem 12.7 (Similarity as change of basis).** For an operator T : V → V and bases B, C,
>
> **[T]_C = P_{C←B} [T]_B P_{C←B}⁻¹**
>
> So the matrices of a single operator in different bases are exactly the **similar** matrices.

**This is the conceptual meaning of Chapter 10.** Diagonalizing A = PDP⁻¹ says: the operator x ↦ Ax, when viewed in the eigenvector basis, is just the diagonal scaling D. Choosing better coordinates simplified the machine.

### 12.2.7 Invertible Transformations

T : V → W is **invertible** if there is S : W → V with S∘T = I_V and T∘S = I_W. Then S = T⁻¹ is also linear, and

> **[T⁻¹] = [T]⁻¹**

For T(x) = Ax with A invertible: T⁻¹(x) = A⁻¹x.

---

## 12.3 Solved Examples

### Example 12.1 — [Easy] Testing linearity

Determine which of the following are linear:
(a) T(x₁, x₂) = (2x₁ − x₂, x₁ + 3x₂)
(b) T(x₁, x₂) = (x₁ + 1, x₂)
(c) T(x₁, x₂) = (x₁x₂, x₁)
(d) T(A) = Aᵀ on M_{2×2}

**Solution.**

**(a) Linear.** It is T(x) = Ax with A = [[2, −1], [1, 3]], and every matrix map is linear ✓

**(b) NOT linear.** T(0,0) = (1, 0) ≠ (0,0). A translation. ✗

**(c) NOT linear.** T(1,1) = (1, 1) but T(2,2) = (4, 2) ≠ 2(1,1) = (2,2). Homogeneity fails ✗

**(d) Linear.** (A + B)ᵀ = Aᵀ + Bᵀ ✓ and (cA)ᵀ = cAᵀ ✓

---

### Example 12.2 — [Easy] Finding the standard matrix

Find the standard matrix of T : ℝ³ → ℝ² given by T(x₁, x₂, x₃) = (x₁ − 2x₃, 3x₂ + x₃).

**Solution.** Compute T on each standard basis vector:
- T(e₁) = T(1,0,0) = (1, 0)
- T(e₂) = T(0,1,0) = (0, 3)
- T(e₃) = T(0,0,1) = (−2, 1)

**A = [[1, 0, −2], [0, 3, 1]]** (2×3) ✓

*Check:* A(2, 1, −1)ᵀ = (2 + 2, 3 − 1) = (4, 2). Direct: (2 − 2(−1), 3(1) + (−1)) = (4, 2) ✓

---

### Example 12.3 — [Medium] Kernel, range, injectivity, surjectivity

For T : ℝ⁴ → ℝ³ with standard matrix A = [[1, 2, 0, 3], [2, 4, 1, 7], [1, 2, 1, 4]], find bases for ker(T) and range(T), and determine whether T is one-to-one or onto.

**Solution.** Row reduce A:
`R₂ − 2R₁`, `R₃ − R₁`:
```
[[1, 2, 0, 3],
 [0, 0, 1, 1],
 [0, 0, 1, 1]]
```
`R₃ − R₂` → zero row.
```
RREF = [[1, 2, 0, 3],
        [0, 0, 1, 1],
        [0, 0, 0, 0]]
```
**rank = 2**, pivots in columns 1 and 3.

**range(T) = Col(A):** the *original* columns 1 and 3:
> **Basis: {(1, 2, 1)ᵀ, (0, 1, 1)ᵀ}**, dim = 2.

**ker(T) = Nul(A):** free x₂ = s, x₄ = t. x₁ = −2s − 3t, x₃ = −t.
> **Basis: {(−2, 1, 0, 0), (−3, 0, −1, 1)}**, dim = 2.

**Rank–nullity:** 2 + 2 = 4 = dim ℝ⁴ ✓

**One-to-one?** nullity = 2 ≠ 0 → **NO**.
**Onto?** rank = 2 < 3 = dim ℝ³ → **NO**. The range is a plane inside ℝ³.

---

### Example 12.4 — [Medium] Composition of geometric maps

Find the matrix of "rotate 90° counterclockwise, then reflect in the line y = x". Then do them in the opposite order and compare.

**Solution.**
```
R = [[0, −1], [1, 0]]   (rotation 90°)
F = [[0,  1], [1, 0]]   (reflection in y = x)
```

**Rotate then reflect:** S = F ∘ R, matrix **FR**:
```
FR = [[0,1],[1,0]]·[[0,−1],[1,0]] = [[1, 0], [0, −1]]
```
This is **reflection in the x-axis**.

**Reflect then rotate:** matrix **RF**:
```
RF = [[0,−1],[1,0]]·[[0,1],[1,0]] = [[−1, 0], [0, 1]]
```
This is **reflection in the y-axis**.

**FR ≠ RF** ✓ — order matters, and the two orders give genuinely different maps (reflections in perpendicular lines).

*Check FR on e₁ = (1,0):* rotate → (0,1); reflect in y=x → (1,0). And FR(1,0) = (1,0) ✓
*Check RF on e₁:* reflect → (0,1); rotate → (−1, 0). And RF(1,0) = (−1,0) ✓

---

### Example 12.5 — [Medium] Matrix relative to a non-standard basis

Let T : ℝ² → ℝ² be T(x) = Ax with A = [[4, −2], [1, 1]]. Let B = {b₁, b₂} with b₁ = (1, 1), b₂ = (2, 1). Find [T]_B.

**Solution.** Compute T(b₁) and T(b₂), then express each in the B-basis.

T(b₁) = A(1,1)ᵀ = (4 − 2, 1 + 1) = **(2, 2)**
T(b₂) = A(2,1)ᵀ = (8 − 2, 2 + 1) = **(6, 3)**

**Express (2,2) in B:** c₁(1,1) + c₂(2,1) = (2,2).
c₁ + 2c₂ = 2, c₁ + c₂ = 2 → subtracting: c₂ = 0, c₁ = 2.
**[T(b₁)]_B = (2, 0)ᵀ**

**Express (6,3) in B:** c₁ + 2c₂ = 6, c₁ + c₂ = 3 → c₂ = 3, c₁ = 0.
**[T(b₂)]_B = (0, 3)ᵀ**

```
[T]_B = [[2, 0],
         [0, 3]]
```

**The B-matrix is diagonal!** That is because b₁ and b₂ happen to be eigenvectors: Ab₁ = 2b₁ and Ab₂ = 3b₂ ✓

*Verification via similarity:* P_B = [[1,2],[1,1]], det = −1, P_B⁻¹ = [[−1, 2], [1, −1]].
P_B⁻¹AP_B = [[−1,2],[1,−1]]·[[4,−2],[1,1]]·[[1,2],[1,1]]
First: [[−1,2],[1,−1]]·[[4,−2],[1,1]] = [[−4+2, 2+2],[4−1, −2−1]] = [[−2, 4],[3, −3]].
Then: [[−2,4],[3,−3]]·[[1,2],[1,1]] = [[−2+4, −4+4],[3−3, 6−3]] = [[2, 0],[0, 3]] ✓

---

### Example 12.6 — [Hard] Differentiation as a matrix

Let D : P₃ → P₃ be the differentiation operator D(p) = p′, with basis B = {1, t, t², t³}. Find [D]_B, its kernel, range, rank, and show D is nilpotent.

**Solution.** Apply D to each basis element and record coordinates:
- D(1) = 0 → [0, 0, 0, 0]ᵀ
- D(t) = 1 → [1, 0, 0, 0]ᵀ
- D(t²) = 2t → [0, 2, 0, 0]ᵀ
- D(t³) = 3t² → [0, 0, 3, 0]ᵀ

```
[D]_B = [[0, 1, 0, 0],
         [0, 0, 2, 0],
         [0, 0, 0, 3],
         [0, 0, 0, 0]]
```

**ker(D):** solve [D]_B c = 0 → c₂ = 0, 2c₃ = 0, 3c₄ = 0, so c₂ = c₃ = c₄ = 0, c₁ free.
**ker(D) = span{1}** — the constant polynomials ✓ (obviously: the derivative kills exactly the constants). **nullity = 1.**

**range(D):** pivots in columns 2, 3, 4 → rank = **3**. Range = span{1, t, t²} = **P₂** ✓

**Rank–nullity:** 3 + 1 = 4 = dim P₃ ✓

**D is not one-to-one** (kernel is nontrivial) and **not onto P₃** (range is only P₂). It *is* onto P₂.

**Nilpotency.** [D]_B is strictly upper triangular, so all eigenvalues are 0. Compute:
- D² sends t³ ↦ 6t, t² ↦ 2, t ↦ 0, 1 ↦ 0
- D³ sends t³ ↦ 6, everything else ↦ 0
- **D⁴ = 0** ✓

Indeed, differentiating a cubic four times gives zero. **[D]_B⁴ = 0**, so D is nilpotent of index 4, and (by S9.17) it is **not diagonalizable** unless it is zero — which it isn't.

---

### Example 12.7 — [Hard] Change of basis between two non-standard bases

Let B = {(1, 0), (1, 1)} and C = {(2, 1), (1, 2)} be bases of ℝ². Find P_{C←B}, and use it to convert [x]_B = (3, −1)ᵀ into C-coordinates. Verify directly.

**Solution.**

**Method: P_{C←B} = P_C⁻¹ P_B.**
```
P_B = [[1, 1], [0, 1]]       P_C = [[2, 1], [1, 2]]
```
det P_C = 4 − 1 = 3, so P_C⁻¹ = (1/3)[[2, −1], [−1, 2]].

```
P_{C←B} = (1/3)[[2,−1],[−1,2]] · [[1,1],[0,1]]
```
- (1,1): (2(1) + (−1)(0))/3 = 2/3
- (1,2): (2(1) + (−1)(1))/3 = 1/3
- (2,1): (−1(1) + 2(0))/3 = −1/3
- (2,2): (−1(1) + 2(1))/3 = 1/3

```
P_{C←B} = (1/3)[[2, 1], [−1, 1]]
```

**Convert [x]_B = (3, −1):**
[x]_C = (1/3)[[2,1],[−1,1]]·(3,−1)ᵀ = (1/3)(6 − 1, −3 − 1) = (1/3)(5, −4) = **(5/3, −4/3)ᵀ**

**Verify directly.** From [x]_B = (3,−1): x = 3(1,0) − 1(1,1) = (3−1, 0−1) = **(2, −1)**.
Now express (2,−1) in C: c₁(2,1) + c₂(1,2) = (2,−1).
2c₁ + c₂ = 2, c₁ + 2c₂ = −1. Multiply the second by 2: 2c₁ + 4c₂ = −2. Subtracting: 3c₂ = −4 → c₂ = −4/3, and c₁ = 2 − c₂·... from the first: 2c₁ = 2 + 4/3 = 10/3 → c₁ = 5/3.
**[x]_C = (5/3, −4/3)ᵀ** ✓ matches.

---

### Example 12.8 — [Very Hard] The dimension theorem proved

Prove Theorem 12.3: for a linear map T : V → W with dim V = n finite,
**dim ker(T) + dim range(T) = n**.

**Solution.**

Let k = dim ker(T) and choose a basis {u₁, ..., u_k} for ker(T).

Since ker(T) is a subspace of V, extend this to a basis of V:
> **{u₁, ..., u_k, v₁, ..., v_{n−k}}**

**Claim: {T(v₁), ..., T(v_{n−k})} is a basis for range(T).**

**(i) It spans range(T).** Any element of range(T) is T(x) for some x ∈ V. Write
x = Σaᵢuᵢ + Σbⱼvⱼ.
Apply T, using T(uᵢ) = 0:
T(x) = Σaᵢ·0 + Σbⱼ T(vⱼ) = Σbⱼ T(vⱼ) ✓
So every element of the range is a combination of the T(vⱼ).

**(ii) It is linearly independent.** Suppose Σcⱼ T(vⱼ) = 0. By linearity,
T(Σcⱼvⱼ) = 0,
so **Σcⱼvⱼ ∈ ker(T)**. Hence it can be written in the kernel basis:
Σcⱼvⱼ = Σdᵢuᵢ
Rearranging: Σcⱼvⱼ − Σdᵢuᵢ = 0.
But {u₁,...,u_k, v₁,...,v_{n−k}} is a basis of V, hence independent, so **all cⱼ = 0** (and all dᵢ = 0) ✓

So the set is a basis of range(T), giving **dim range(T) = n − k**.

Therefore **dim ker(T) + dim range(T) = k + (n − k) = n** ✓ ∎

**Corollaries.**
1. If dim V > dim W, T cannot be one-to-one (nullity ≥ dim V − dim W > 0).
2. If dim V < dim W, T cannot be onto (rank ≤ dim V < dim W).
3. If dim V = dim W, then one-to-one ⟺ onto — the abstract source of the Invertible Matrix Theorem's square-matrix magic.

---

### Example 12.9 — [Very Hard] Invariant subspaces and triangularization

Let T : ℝ³ → ℝ³ have matrix A = [[2, 1, 0], [0, 2, 0], [1, 0, 3]]. Find all one-dimensional T-invariant subspaces, and explain the connection to triangular form.

**Solution.**

> A subspace U is **T-invariant** if T(U) ⊆ U.

A **one-dimensional** invariant subspace is a line span{v} with T(v) ∈ span{v}, i.e. Av = λv. **So one-dimensional invariant subspaces are exactly the eigenspaces' lines.**

**Find eigenvalues.** A is block lower-triangular-ish; compute directly:
det(A − λI) = det [[2−λ, 1, 0], [0, 2−λ, 0], [1, 0, 3−λ]]

Expand along **column 3** (entries 0, 0, 3−λ):
= (3−λ)·det[[2−λ, 1], [0, 2−λ]] = (3−λ)(2−λ)²

**Eigenvalues: λ = 3 (AM 1), λ = 2 (AM 2).**

**λ = 3:** A − 3I = [[−1, 1, 0], [0, −1, 0], [1, 0, 0]].
Row 2: −v₂ = 0 → v₂ = 0. Row 3: v₁ = 0. Row 1: −0 + 0 = 0 ✓, v₃ free.
**Eigenvector (0, 0, 1).**

**λ = 2:** A − 2I = [[0, 1, 0], [0, 0, 0], [1, 0, 1]].
Row 1: v₂ = 0. Row 3: v₁ + v₃ = 0 → v₃ = −v₁.
**Eigenvector (1, 0, −1).** rank(A − 2I) = 2 → **GM(2) = 1 < 2 = AM(2)**.

**Answer: exactly two one-dimensional invariant subspaces:**
> **span{(0, 0, 1)}** (λ = 3) and **span{(1, 0, −1)}** (λ = 2)

**Connection to triangular form.** Since GM(2) = 1 < AM(2) = 2, **A is not diagonalizable** — there is no basis of eigenvectors, so no basis makes [T] diagonal.

However, A is **triangularizable**. Build a **flag** of nested invariant subspaces
{0} ⊂ U₁ ⊂ U₂ ⊂ ℝ³ with dim Uᵢ = i and each T-invariant.

Take U₁ = span{w₁} with w₁ = (1, 0, −1) (the λ=2 eigenvector). For U₂, we need a generalized eigenvector: solve (A − 2I)w₂ = w₁:
```
[[0,1,0],[0,0,0],[1,0,1]]·w₂ = (1, 0, −1)
```
Row 1: (w₂)₂ = 1. Row 2: 0 = 0 ✓. Row 3: (w₂)₁ + (w₂)₃ = −1. Take (w₂)₁ = 0, (w₂)₃ = −1.
**w₂ = (0, 1, −1).** Then U₂ = span{w₁, w₂} is invariant, since Aw₂ = 2w₂ + w₁ ∈ U₂ ✓

Take w₃ = (0, 0, 1) (the λ=3 eigenvector). In the basis {w₁, w₂, w₃}:
- T(w₁) = 2w₁ → column (2, 0, 0)
- T(w₂) = w₁ + 2w₂ → column (1, 2, 0)
- T(w₃) = 3w₃ → column (0, 0, 3)

```
[T]_{w} = [[2, 1, 0],
           [0, 2, 0],
           [0, 0, 3]]
```
**Upper triangular — in fact the Jordan form** (a 2×2 Jordan block for λ=2, plus a 1×1 block for λ=3).

*(General theorem: every complex square matrix is triangularizable — Schur's theorem guarantees this even with an *orthonormal* basis. Diagonalizability is the stronger property that can fail; triangularizability never does.)*

---

## 12.4 Practice Numericals — Chapter 12

**[Easy]**

**P12.1** Determine whether T(x₁, x₂) = (3x₁, x₁ − x₂) is linear. If so, give its standard matrix.

**P12.2** Find the standard matrix of the rotation by 180° in ℝ².

**P12.3** Is T(x) = ‖x‖ from ℝ² to ℝ linear? Justify.

**P12.4** For T(x) = Ax with A = [[1, 2], [2, 4]], find ker(T).

**P12.5** State the standard matrix for reflection in the line y = x, and compute its square.

**[Medium]**

**P12.6** Find bases for ker(T) and range(T) for A = [[1, 3, 2], [2, 6, 4]]. Is T one-to-one? Onto ℝ²?

**P12.7** Find the standard matrix of T : ℝ² → ℝ² that rotates by 60° and then scales by 2.

**P12.8** Let T : P₂ → P₂ be T(p)(t) = p(t) + p′(t). Find [T]_B for B = {1, t, t²} and determine whether T is invertible.

**P12.9** Let B = {(1, 2), (3, 5)}. Find P_B, P_B⁻¹, and [x]_B for x = (1, 1).

**P12.10** T : ℝ³ → ℝ² is given by T(e₁) = (1, 2), T(e₂) = (0, 1), T(e₃) = (−1, 3). Find T(2, −1, 4) and the standard matrix.

**P12.11** Show that the trace map tr : M_{2×2} → ℝ is linear, and find its kernel and its dimension.

**[Hard]**

**P12.12** Let A = [[3, 1], [0, 3]] represent T. Find [T]_B for B = {(1, 0), (1, 1)} and verify the similarity relation.

**P12.13** Let T : ℝ⁴ → ℝ³ be onto. What are the possible values of nullity(T)? Justify using rank–nullity.

**P12.14** Let T : V → V with T² = T (a projection). Prove V = ker(T) ⊕ range(T).

**P12.15** Find the matrix of the reflection in the line through the origin making angle 30° with the x-axis, and verify it is orthogonal with determinant −1.

**P12.16** Let S, T : ℝⁿ → ℝⁿ be linear with S∘T = I. Prove T∘S = I and both are isomorphisms. Show this fails for maps between spaces of different dimensions.

**P12.17** Let T : P₃ → ℝ⁴ be T(p) = (p(0), p(1), p(2), p(3)). Prove T is an isomorphism.

**[Very Hard]**

**P12.18** Let T : V → W be linear with dim V = n, dim W = m. Prove that there exist bases of V and W in which the matrix of T is [[I_r, 0], [0, 0]] with r = rank(T). (This is the *normal form* of Theorem 7.6, proved transformationally.)

**P12.19** Let D : P_n → P_n be differentiation. Prove D is nilpotent of index exactly n+1, find all eigenvalues, and determine dim ker(Dᵏ) for each k.

**P12.20** Prove that a linear operator T on a finite-dimensional space V satisfies: T is invertible ⟺ 0 is not an eigenvalue of T ⟺ det[T]_B ≠ 0 for any (hence every) basis B.

**P12.21** Let T : ℝ³ → ℝ³ be rotation by angle θ about the axis spanned by a unit vector n. Derive **Rodrigues' formula**
R = I + (sin θ)K + (1 − cos θ)K²,
where K is the skew-symmetric "cross-product matrix" of n. Apply it with n = (0,0,1) and verify it gives the standard z-rotation.

---

## 12.5 Solutions to Chapter 12 Practice

**S12.1** T(e₁) = (3, 1), T(e₂) = (0, −1). Both defining conditions hold since each output coordinate is a linear combination of inputs.
**Linear, A = [[3, 0], [1, −1]].**

**S12.2** θ = 180°: cos = −1, sin = 0. **A = [[−1, 0], [0, −1]] = −I.**

**S12.3** **Not linear.** T(−x) = ‖−x‖ = ‖x‖ = T(x), but linearity requires T(−x) = −T(x). For x ≠ 0 these differ ✗
*(Also T(2x) = 2‖x‖ works, but T(u+v) ≤ T(u)+T(v) with strict inequality in general.)*

**S12.4** Ax = 0: x₁ + 2x₂ = 0 (row 2 is a multiple of row 1). So x₁ = −2x₂.
**ker(T) = span{(−2, 1)}**, dimension 1.

**S12.5** A = [[0, 1], [1, 0]]. A² = [[1, 0], [0, 1]] = **I** ✓
*(Reflecting twice returns you to the start — every reflection is an involution.)*

**S12.6** Row reduce: `R₂ − 2R₁` → [[1, 3, 2], [0, 0, 0]]. **rank = 1.**
**range(T) = Col(A) = span{(1, 2)ᵀ}** — a line in ℝ².
**ker(T):** x₁ = −3x₂ − 2x₃, free x₂, x₃.
**Basis: {(−3, 1, 0), (−2, 0, 1)}**, nullity = 2.
Check: 1 + 2 = 3 ✓
**One-to-one? No** (nullity ≠ 0). **Onto ℝ²? No** (rank 1 < 2).

**S12.7** Rotation by 60°: cos 60° = 1/2, sin 60° = √3/2.
R = [[1/2, −√3/2], [√3/2, 1/2]]. Scale by 2: multiply by 2I.
**A = 2R = [[1, −√3], [√3, 1]]**
*Check det = 1 + 3 = 4 = 2² ✓ (area scales by 4, as a doubling in 2D should).*

**S12.8** T(1) = 1 + 0 = 1 → (1, 0, 0)ᵀ
T(t) = t + 1 → (1, 1, 0)ᵀ
T(t²) = t² + 2t → (0, 2, 1)ᵀ
```
[T]_B = [[1, 1, 0],
         [0, 1, 2],
         [0, 0, 1]]
```
Upper triangular with all diagonal entries 1 → **det = 1 ≠ 0 → invertible** ✓
*(Indeed T = I + D and D is nilpotent, so T⁻¹ = I − D + D² — see S3.17.)*

**S12.9** P_B = [[1, 3], [2, 5]], det = 5 − 6 = −1.
**P_B⁻¹ = (1/−1)[[5, −3], [−2, 1]] = [[−5, 3], [2, −1]]**
[x]_B = P_B⁻¹(1,1)ᵀ = (−5 + 3, 2 − 1) = **(−2, 1)ᵀ**
*Check: −2(1,2) + 1(3,5) = (−2+3, −4+5) = (1, 1) ✓*

**S12.10** **A = [[1, 0, −1], [2, 1, 3]]**
T(2,−1,4) = 2(1,2) − 1(0,1) + 4(−1,3) = (2, 4) − (0, 1) + (−4, 12) = **(−2, 15)**
*Check via A: A(2,−1,4)ᵀ = (2 + 0 − 4, 4 − 1 + 12) = (−2, 15) ✓*

**S12.11** tr(A + B) = tr A + tr B ✓ and tr(cA) = c·tr A ✓ → **linear**.
**ker(tr) = {A : a₁₁ + a₂₂ = 0}** = the trace-zero matrices.
One linear constraint on a 4-dimensional space → **dim ker = 3**.
Basis: {[[1,0],[0,−1]], [[0,1],[0,0]], [[0,0],[1,0]]} ✓ (matching S4.11)
*Rank–nullity: 3 + 1 = 4 ✓ (the range is all of ℝ, dim 1).*

**S12.12** b₁ = (1,0), b₂ = (1,1).
T(b₁) = A(1,0)ᵀ = (3, 0). In B: c₁(1,0) + c₂(1,1) = (3,0) → c₂ = 0, c₁ = 3 → **(3, 0)ᵀ**
T(b₂) = A(1,1)ᵀ = (3+1, 3) = (4, 3). In B: c₂ = 3, c₁ + 3 = 4 → c₁ = 1 → **(1, 3)ᵀ**
```
[T]_B = [[3, 1],
         [0, 3]]
```
**Verify similarity [T]_B = P_B⁻¹ A P_B:** P_B = [[1,1],[0,1]], P_B⁻¹ = [[1,−1],[0,1]].
P_B⁻¹A = [[1,−1],[0,1]]·[[3,1],[0,3]] = [[3, 1−3],[0,3]] = [[3,−2],[0,3]].
Times P_B: [[3,−2],[0,3]]·[[1,1],[0,1]] = [[3, 3−2],[0, 3]] = [[3, 1],[0, 3]] ✓
*(Interesting: the matrix is unchanged. A Jordan block stays a Jordan block under this particular change of basis.)*

**S12.13** T onto ℝ³ means **rank(T) = 3**.
By rank–nullity with dim V = 4: nullity = 4 − 3 = **1**.
**Only one possible value: nullity(T) = 1.**

**S12.14** Let T² = T.

**Step 1: ker(T) ∩ range(T) = {0}.** Let x ∈ range(T) ∩ ker(T). Since x ∈ range(T), x = T(y) for some y. Then
x = T(y) = T²(y) = T(T(y)) = T(x) = 0 (as x ∈ ker T) ✓

**Step 2: V = ker(T) + range(T).** For any v ∈ V write
v = (v − T(v)) + T(v).
The second piece is in range(T) ✓. For the first:
T(v − T(v)) = T(v) − T²(v) = T(v) − T(v) = 0,
so v − T(v) ∈ ker(T) ✓

**Therefore V = ker(T) ⊕ range(T)** ✓ ∎
*(Geometrically: a projection splits space into "what survives" and "what gets flattened", and these are complementary.)*

**S12.15** Reflection in the line at angle θ has matrix [[cos 2θ, sin 2θ], [sin 2θ, −cos 2θ]].
θ = 30° → 2θ = 60°: cos 60° = 1/2, sin 60° = √3/2.
```
A = [[1/2,  √3/2],
     [√3/2, −1/2]]
```
**Orthogonal?** Column 1 · Column 1 = 1/4 + 3/4 = 1 ✓; Column 2 · Column 2 = 3/4 + 1/4 = 1 ✓; Column 1 · Column 2 = √3/4 − √3/4 = 0 ✓ **Yes.**
**det A** = (1/2)(−1/2) − (√3/2)(√3/2) = −1/4 − 3/4 = **−1** ✓ (reflections reverse orientation).
*Check the fixed direction:* the line at 30° has direction (cos30°, sin30°) = (√3/2, 1/2).
A(√3/2, 1/2)ᵀ = (√3/4 + √3/4, 3/4 − 1/4) = (√3/2, 1/2) ✓ fixed, as it should be.

**S12.16** Let A, B be the standard matrices of S, T, both n×n. S∘T = I means **AB = I**.

Since A and B are **square** with AB = I, by IMT(k) A is invertible with A⁻¹ = B. Then
BA = A⁻¹A = **I** ✓, so **T∘S = I** ✓

Both A and B are invertible → **both S and T are isomorphisms** ✓ ∎

**Failure across different dimensions.** Let T : ℝ² → ℝ³ be T(x₁,x₂) = (x₁, x₂, 0) and S : ℝ³ → ℝ² be S(y₁,y₂,y₃) = (y₁, y₂).
Then **S∘T = I_{ℝ²}** ✓
But T∘S(y₁,y₂,y₃) = (y₁, y₂, 0) ≠ (y₁,y₂,y₃) whenever y₃ ≠ 0. **T∘S ≠ I_{ℝ³}** ✗
Neither map is an isomorphism (T isn't onto; S isn't one-to-one).

**S12.17** dim P₃ = 4 = dim ℝ⁴, so by the dimension theorem it suffices to show T is **one-to-one**.

Suppose T(p) = 0, i.e. p(0) = p(1) = p(2) = p(3) = 0.

Then p is a polynomial of degree ≤ 3 with **four distinct roots**. A nonzero polynomial of degree d has at most d roots, so a degree-≤3 polynomial with 4 roots must be the **zero polynomial**.

**ker(T) = {0}** → T is one-to-one → (equal dimensions) → **T is an isomorphism** ✓ ∎

*(Equivalently: the matrix of T in the standard basis is the 4×4 Vandermonde matrix on nodes 0,1,2,3, whose determinant Π_{i<j}(xⱼ − xᵢ) ≠ 0 for distinct nodes — Example 7.7.)*

**S12.18** Let r = rank(T), k = nullity(T), so r + k = n.

**Build the basis of V.** Take a basis {u₁, ..., u_k} of ker(T) and extend to a basis of V:
> B = {v₁, ..., v_r, u₁, ..., u_k}
*(ordering the non-kernel vectors first)*

By the proof of Example 12.8, **{T(v₁), ..., T(v_r)} is a basis of range(T)** ✓

**Build the basis of W.** Since range(T) ⊆ W, extend {T(v₁), ..., T(v_r)} to a basis of W:
> C = {T(v₁), ..., T(v_r), w_{r+1}, ..., w_m}

**Compute [T]_{C←B}.**
- For j ≤ r: T(vⱼ) is the j-th vector of C, so [T(vⱼ)]_C = eⱼ.
- For the uᵢ: T(uᵢ) = 0, so the column is 0.

Hence
```
[T]_{C←B} = [[I_r, 0],
             [0,   0]]
```
of size m×n ✓ ∎

*(This is the "normal form" — every linear map, stripped of coordinates, is just "keep r coordinates, discard the rest". All the apparent complexity of a matrix lives in the choice of basis, not in the map.)*

**S12.19** dim P_n = n + 1, basis {1, t, ..., tⁿ}.

**Nilpotency.** D lowers degree by exactly 1 on any nonconstant polynomial. So D^{n+1} applied to tⁿ gives:
tⁿ → n t^{n−1} → n(n−1)t^{n−2} → ... → n! → **0** after n+1 applications ✓
So **D^{n+1} = 0.**

**Index is exactly n+1**, not less: Dⁿ(tⁿ) = n! ≠ 0, so **Dⁿ ≠ 0** ✓

**Eigenvalues.** By S9.17, a nilpotent operator has **all eigenvalues equal to 0**. Directly: D(p) = λp with p ≠ 0 forces deg(p′) = deg(p), impossible unless λ = 0, and then p is constant ✓

**dim ker(Dᵏ).** Dᵏ(p) = 0 means the k-th derivative vanishes, i.e. **p has degree ≤ k − 1**.
> **ker(Dᵏ) = P_{k−1}**, so **dim ker(Dᵏ) = k** for 1 ≤ k ≤ n+1,
and dim ker(Dᵏ) = n + 1 (everything) for k ≥ n+1 ✓

*(The kernels form a strictly increasing chain {0} ⊂ P₀ ⊂ P₁ ⊂ ... ⊂ P_n, each step adding exactly one dimension — the signature of a single Jordan block of size n+1.)*

**S12.20** Let B be any basis of V, A = [T]_B.

**(i) T invertible ⟺ A invertible.** If T⁻¹ exists, then [T⁻¹]_B[T]_B = [T⁻¹∘T]_B = [I]_B = I, so A is invertible. Conversely if A is invertible, the map with matrix A⁻¹ is a two-sided inverse of T ✓

**(ii) A invertible ⟺ det A ≠ 0** — IMT(m) ✓

**(iii) A invertible ⟺ 0 is not an eigenvalue** — IMT(q). Directly: 0 is an eigenvalue ⟺ T(v) = 0 for some v ≠ 0 ⟺ ker(T) ≠ {0} ⟺ T not one-to-one ⟺ (finite dim) T not invertible ✓

**(iv) Independence of basis.** If B and C are two bases, [T]_C = P[T]_BP⁻¹ (Theorem 12.7), so
det[T]_C = det(P)det([T]_B)det(P⁻¹) = det[T]_B ✓
The determinant is a **similarity invariant**, so "det ≠ 0" holds in one basis exactly when it holds in every basis ✓ ∎

**S12.21** Let n = (n₁, n₂, n₃) be a unit vector and
```
K = [[ 0,  −n₃,  n₂],
     [ n₃,  0,  −n₁],
     [−n₂,  n₁,  0 ]]
```
so that **Kx = n × x** for every x.

**Set-up.** Decompose any x into components parallel and perpendicular to n:
> x = x_∥ + x_⊥, where x_∥ = (n·x)n and x_⊥ = x − (n·x)n

Rotation about the n-axis **fixes x_∥** and **rotates x_⊥ by θ within the plane perpendicular to n**.

In that plane, {x_⊥, n × x_⊥} is an orthogonal pair of equal length (since ‖n × x_⊥‖ = ‖n‖‖x_⊥‖ sin 90° = ‖x_⊥‖). So rotating x_⊥ by θ gives

> R(x_⊥) = cos θ · x_⊥ + sin θ · (n × x_⊥)

Therefore
> **R(x) = x_∥ + cos θ · x_⊥ + sin θ · (n × x)**
*(using n × x = n × x_⊥, since n × x_∥ = 0)*

**Convert to matrix form.** Two identities:
- **Kx = n × x** by definition
- **K²x = n × (n × x) = (n·x)n − (n·n)x = x_∥ − x** *(BAC–CAB rule, with ‖n‖ = 1)*
 So **x_⊥ = x − x_∥ = −K²x** and **x_∥ = x + K²x**.

Substituting:
R(x) = (x + K²x) + cos θ(−K²x) + sin θ(Kx)
= x + (1 − cos θ)K²x + sin θ·Kx

**R = I + (sin θ)K + (1 − cos θ)K²** ✓ ∎

**Verification with n = (0, 0, 1).**
```
K = [[0, −1, 0],
     [1,  0, 0],
     [0,  0, 0]]
K² = [[−1, 0, 0],
      [0, −1, 0],
      [0,  0, 0]]
```
R = I + sin θ·K + (1−cos θ)K²
- (1,1): 1 + 0 + (1−cos θ)(−1) = cos θ ✓
- (1,2): 0 + sin θ(−1) + 0 = −sin θ ✓
- (2,1): 0 + sin θ(1) + 0 = sin θ ✓
- (2,2): 1 + 0 − (1−cos θ) = cos θ ✓
- (3,3): 1 + 0 + 0 = 1 ✓
- all other entries 0 ✓

```
R = [[cos θ, −sin θ, 0],
     [sin θ,  cos θ, 0],
     [0,      0,     1]]
```
**Exactly the standard rotation about the z-axis** ✓

*(Rodrigues' formula is what every robotics and graphics library uses internally to convert an axis–angle rotation into a matrix. Note also that K³ = −K, which is why the series for e^{θK} collapses into just sin and cos terms — R = e^{θK}, the matrix exponential of a skew-symmetric matrix.)*

---
# Chapter 13 — Singular Value Decomposition, Low-Rank Approximation, Matrix Factorization

---

## 13.1 Explain Like I'm Five

Diagonalization was wonderful, but it had two problems: it only works for **square** matrices, and even then it sometimes **fails** (defective matrices).

The **SVD fixes both**. Every matrix — square or not, invertible or not, ugly or not — has an SVD. No exceptions. It is the most reliable tool in linear algebra.

**The idea.** Take the unit circle (or sphere) and push it through your matrix A. What comes out? Always an **ellipse** (or ellipsoid). Never anything weirder. Squashed flat sometimes, sure, but always an ellipse.

The SVD reads off that ellipse:
- **How long are the ellipse's axes?** Those lengths are the **singular values** σ₁ ≥ σ₂ ≥ ... ≥ 0.
- **Which directions do the axes point in?** Those are the **left singular vectors** u₁, u₂, ...
- **Which input directions got mapped to those axes?** Those are the **right singular vectors** v₁, v₂, ...

So A does exactly three things, in order:
1. **Rotate** the input (that's Vᵀ)
2. **Stretch** along the axes by σ₁, σ₂, ... (that's Σ)
3. **Rotate** again into the output space (that's U)

> **A = UΣVᵀ** — rotate, stretch, rotate. That's *every* matrix, ever.

**Why is this the crown jewel?** Because the singular values are sorted biggest-first, and they tell you **how much of the matrix lives in each direction**. If σ₁ = 100 and σ₂ = 0.01, then the second direction is basically noise — you can throw it away and barely change the matrix.

That's **low-rank approximation**: keep the big singular values, discard the small ones. You get a much simpler matrix that's almost identical to the original. It's how images are compressed, how recommender systems guess what you'd like, and how noisy data gets cleaned up. And a theorem (Eckart–Young) guarantees this is the *best possible* approximation of that rank — you cannot do better by any other method.

---

## 13.2 The Formal Theory

### 13.2.1 Singular Values

Let A be an m×n real matrix. Then **AᵀA is n×n, symmetric, and positive semidefinite** (S11.10), so by the Spectral Theorem it has an orthonormal eigenbasis {v₁, ..., vₙ} with real eigenvalues λ₁ ≥ λ₂ ≥ ... ≥ λₙ ≥ 0.

> **Definition.** The **singular values** of A are
> **σᵢ = √λᵢ**, i = 1, ..., n,
> arranged in decreasing order σ₁ ≥ σ₂ ≥ ... ≥ σₙ ≥ 0.

**Key identity:** ‖Avᵢ‖² = (Avᵢ)ᵀ(Avᵢ) = vᵢᵀAᵀAvᵢ = λᵢvᵢᵀvᵢ = λᵢ.
So **‖Avᵢ‖ = σᵢ** — the singular values are the *lengths of the images of the orthonormal eigenvectors of AᵀA*. They are the ellipse's semi-axes.

> **Theorem 13.1.** If A has r nonzero singular values, then **rank(A) = r**, and {Av₁, ..., Av_r} is an **orthogonal basis for Col(A)**.

*Proof of orthogonality:* (Avᵢ)·(Avⱼ) = vᵢᵀAᵀAvⱼ = λⱼ(vᵢ·vⱼ) = 0 for i ≠ j ✓

**Also:** σ₁ = max_{‖x‖=1}‖Ax‖ = ‖A‖₂ (the **spectral norm**), by the Rayleigh quotient theorem applied to AᵀA.

### 13.2.2 The Singular Value Decomposition

> **Theorem 13.2 (SVD).** Every m×n matrix A can be written
>
> **A = UΣVᵀ**
>
> where
> - **U** is m×m **orthogonal** — columns are the **left singular vectors**
> - **V** is n×n **orthogonal** — columns are the **right singular vectors**
> - **Σ** is m×n "diagonal" with entries σ₁ ≥ σ₂ ≥ ... ≥ σ_r > 0 on the diagonal and zeros elsewhere

**Construction:**
1. Compute AᵀA; find its eigenvalues λᵢ and an orthonormal eigenbasis v₁, ..., vₙ. These are the columns of V.
2. Set σᵢ = √λᵢ, sorted descending. Build Σ.
3. For each i ≤ r (σᵢ > 0), set **uᵢ = Avᵢ/σᵢ**. These are orthonormal.
4. If r < m, extend {u₁, ..., u_r} to an orthonormal basis of ℝᵐ (any orthonormal basis of Nul(Aᵀ) will complete it).

**Verification that it works:** AV = [Av₁ ... Avₙ] = [σ₁u₁ ... σ_ru_r 0 ... 0] = UΣ, so A = UΣVᵀ ✓

**Key relations:**
> **Avᵢ = σᵢuᵢ** and **Aᵀuᵢ = σᵢvᵢ** (for i ≤ r)

**Eigenvalue connections:**
- Eigenvalues of **AᵀA** are σᵢ² (with vᵢ as eigenvectors)
- Eigenvalues of **AAᵀ** are σᵢ² (with uᵢ as eigenvectors)
- For a **symmetric positive semidefinite** A: singular values = eigenvalues, and U = V
- For a general symmetric A: **σᵢ = |λᵢ|** (absolute values of the eigenvalues)

**Reduced (economy) SVD:** A = U_rΣ_rV_rᵀ where U_r is m×r, Σ_r is r×r, V_r is n×r. Discards the parts multiplied by zeros — much more efficient in practice.

### 13.2.3 SVD and the Four Fundamental Subspaces

The SVD gives orthonormal bases for **all four** fundamental subspaces at once:

| Subspace | Orthonormal basis | Dimension |
|---|---|---|
| **Col(A)** | u₁, ..., u_r | r |
| **Nul(Aᵀ)** | u_{r+1}, ..., u_m | m − r |
| **Row(A)** | v₁, ..., v_r | r |
| **Nul(A)** | v_{r+1}, ..., vₙ | n − r |

This is often called the **fundamental theorem of linear algebra in picture form**. Nothing else gives you all four bases simultaneously, orthonormally.

### 13.2.4 Outer Product Form and Low-Rank Approximation

> **Theorem 13.3 (Spectral/outer-product expansion).**
>
> **A = σ₁u₁v₁ᵀ + σ₂u₂v₂ᵀ + ... + σ_ru_rv_rᵀ**

Each term σᵢuᵢvᵢᵀ is a **rank-one** matrix. So A is a weighted sum of r rank-one pieces, ordered from most important to least.

> **Definition.** The **rank-k truncation** is
> **A_k = Σ_{i=1}^{k} σᵢuᵢvᵢᵀ** for k ≤ r.

> **Theorem 13.4 (Eckart–Young–Mirsky).** A_k is the **best rank-k approximation** to A in both the spectral and Frobenius norms:
>
> **min_{rank(B) ≤ k} ‖A − B‖₂ = ‖A − A_k‖₂ = σ_{k+1}**
>
> **min_{rank(B) ≤ k} ‖A − B‖_F = ‖A − A_k‖_F = √(σ_{k+1}² + ... + σ_r²)**

**Norms used:**
- **Spectral norm:** ‖A‖₂ = σ₁ (largest stretch)
- **Frobenius norm:** ‖A‖_F = √(Σᵢⱼ aᵢⱼ²) = **√(σ₁² + ... + σ_r²)**

**Energy captured** by the rank-k truncation:
> **(σ₁² + ... + σ_k²)/(σ₁² + ... + σ_r²)**

Choosing k so this is, say, 95% is the standard rule for compression and dimensionality reduction.

**Compression arithmetic.** Storing A takes mn numbers. Storing A_k takes k(m + n + 1) numbers (k columns of U, k columns of V, k singular values). The saving is large whenever k ≪ min(m,n).

### 13.2.5 The Pseudoinverse

> **Definition.** For A = UΣVᵀ with reduced form A = U_rΣ_rV_rᵀ, the **Moore–Penrose pseudoinverse** is
>
> **A⁺ = V_rΣ_r⁻¹U_rᵀ** = Σ_{i=1}^{r} (1/σᵢ)vᵢuᵢᵀ

**Properties (the four Penrose conditions, which characterize A⁺ uniquely):**
1. AA⁺A = A
2. A⁺AA⁺ = A⁺
3. (AA⁺)ᵀ = AA⁺
4. (A⁺A)ᵀ = A⁺A

**Special cases:**
- A invertible → **A⁺ = A⁻¹**
- A full column rank → **A⁺ = (AᵀA)⁻¹Aᵀ** (Chapter 6's least squares matrix)
- A full row rank → A⁺ = Aᵀ(AAᵀ)⁻¹

> **Theorem 13.5.** **x̂ = A⁺b** is the **minimum-norm least squares solution** of `Ax = b`. That is, among all x minimizing ‖b − Ax‖, it is the one of smallest length.

This resolves the rank-deficient case left open in Chapter 6 (Example 6.8).

**Also:** AA⁺ = projection onto Col(A), and A⁺A = projection onto Row(A).

### 13.2.6 Condition Number

> **Definition.** For an invertible (or full-rank) A, the **condition number** is
> **κ(A) = σ₁/σ_r = σ_max/σ_min**

It measures how much relative error in b can be amplified in the solution of Ax = b:

> ‖Δx‖/‖x‖ ≤ κ(A) · ‖Δb‖/‖b‖

- κ near 1 → **well-conditioned**, safe to solve numerically
- κ very large → **ill-conditioned**, expect to lose about log₁₀κ significant digits
- κ = ∞ → singular

**Key fact:** κ(AᵀA) = κ(A)². This is exactly why the normal equations are numerically inferior to QR for least squares (§6.2.4).

### 13.2.7 Comparison of the Major Factorizations

| Factorization | Form | Requirements | Main use |
|---|---|---|---|
| **LU** | A = LU | square, no zero pivots | solving Ax = b repeatedly |
| **QR** | A = QR | independent columns | least squares, eigenvalue algorithms |
| **Cholesky** | A = LLᵀ | symmetric positive definite | fast solving, sampling |
| **Diagonalization** | A = PDP⁻¹ | square, non-defective | powers, dynamics, e^A |
| **Spectral** | A = QDQᵀ | **symmetric** | quadratic forms, PCA |
| **SVD** | A = UΣVᵀ | **none — always exists** | compression, pseudoinverse, rank, PCA |
| **Rank factorization** | A = BC | none | structural/theoretical |
| **NMF** | A ≈ WH, W,H ≥ 0 | non-negative A | interpretable topics/parts |

---

## 13.3 Solved Examples

### Example 13.1 — [Easy] Singular values of a small matrix

Find the singular values of A = [[3, 0], [0, −2]].

**Solution.** AᵀA = [[9, 0], [0, 4]].
Eigenvalues: **9 and 4**. Singular values: √9 = **3** and √4 = **2**.

**Note:** the eigenvalues of A itself are 3 and −2, but the singular values are 3 and 2 — **absolute values**. Singular values are never negative.

---

### Example 13.2 — [Easy] Singular values versus eigenvalues

For A = [[0, 1], [0, 0]], find the eigenvalues and singular values. Comment.

**Solution.**
**Eigenvalues:** A is triangular → both eigenvalues are **0**. (A is nilpotent.)

**Singular values:** AᵀA = [[0,0],[1,0]]·[[0,1],[0,0]] = [[0, 0], [0, 1]].
Eigenvalues of AᵀA: 0 and 1 → **singular values 1 and 0**.

**Comment.** A nonzero matrix can have all eigenvalues zero, but it can **never** have all singular values zero — σ₁ = 0 would force ‖Ax‖ = 0 for all x, i.e. A = 0. Singular values detect the actual size of a matrix; eigenvalues can lie about it. This is one reason numerical software prefers the SVD.

---

### Example 13.3 — [Medium] Full SVD of a 2×2

Find the SVD of A = [[3, 2], [2, 3]].

**Solution.** A is symmetric positive definite, which makes this quick, but let's do it by the general recipe.

**Step 1: AᵀA.** A is symmetric, so AᵀA = A² = [[9+4, 6+6], [6+6, 4+9]] = [[13, 12], [12, 13]].

**Step 2: eigenvalues of AᵀA.** p(λ) = (13−λ)² − 144 = λ² − 26λ + 169 − 144 = λ² − 26λ + 25 = (λ−25)(λ−1).
**λ = 25, 1** → **σ₁ = 5, σ₂ = 1.**

**Step 3: eigenvectors of AᵀA.**
λ=25: [[−12, 12], [12, −12]] → v = (1,1) → **v₁ = (1/√2)(1, 1)**
λ=1: [[12, 12], [12, 12]] → v = (1,−1) → **v₂ = (1/√2)(1, −1)**

**Step 4: left singular vectors.**
Av₁ = (1/√2)(3+2, 2+3) = (1/√2)(5, 5) = 5·(1/√2)(1,1). So **u₁ = (1/√2)(1, 1)** ✓ (and ‖Av₁‖ = 5 = σ₁ ✓)
Av₂ = (1/√2)(3−2, 2−3) = (1/√2)(1, −1) = 1·(1/√2)(1,−1). So **u₂ = (1/√2)(1, −1)** ✓

**SVD:**
```
U = (1/√2)[[1,  1],    Σ = [[5, 0],    V = (1/√2)[[1,  1],
           [1, −1]]         [0, 1]]              [1, −1]]
```
**A = UΣVᵀ** with U = V here (as expected for a symmetric positive definite matrix — the SVD coincides with the spectral decomposition).

**Verify:** UΣ = (1/√2)[[5, 1], [5, −1]]. Times Vᵀ = (1/√2)[[1,1],[1,−1]]:
= (1/2)[[5+1, 5−1], [5−1, 5+1]] = (1/2)[[6, 4],[4, 6]] = [[3, 2],[2, 3]] ✓

---

### Example 13.4 — [Medium] SVD of a non-square matrix

Find the SVD of A = [[1, 1], [0, 1], [1, 0]] (3×2).

**Solution.**

**Step 1: AᵀA** (2×2):
- (1,1): 1 + 0 + 1 = 2
- (1,2): 1 + 0 + 0 = 1
- (2,2): 1 + 1 + 0 = 2
```
AᵀA = [[2, 1], [1, 2]]
```

**Step 2:** eigenvalues (2−λ)² − 1 = 0 → λ = 3, 1. **σ₁ = √3, σ₂ = 1.**

**Step 3:** eigenvectors:
λ=3: [[−1,1],[1,−1]] → **v₁ = (1/√2)(1, 1)**
λ=1: [[1,1],[1,1]] → **v₂ = (1/√2)(1, −1)**

**Step 4: left singular vectors.**
Av₁ = (1/√2)(1+1, 0+1, 1+0) = (1/√2)(2, 1, 1). ‖Av₁‖ = (1/√2)√6 = √3 ✓ = σ₁
**u₁ = Av₁/σ₁ = (1/(√2·√3))(2,1,1) = (1/√6)(2, 1, 1)**

Av₂ = (1/√2)(1−1, 0−1, 1−0) = (1/√2)(0, −1, 1). ‖Av₂‖ = (1/√2)√2 = 1 ✓ = σ₂
**u₂ = (1/√2)(0, −1, 1)**

**Step 5: extend to a basis of ℝ³.** Need u₃ ⊥ u₁, u₂. This is a basis for Nul(Aᵀ).
Solve (2,1,1)·x = 0 and (0,−1,1)·x = 0.
From the second: x₂ = x₃. Substituting: 2x₁ + 2x₂ = 0 → x₁ = −x₂.
**u₃ = (1/√3)(−1, 1, 1)**
*Check: (−1,1,1)·(2,1,1) = −2+1+1 = 0 ✓; (−1,1,1)·(0,−1,1) = 0 −1+1 = 0 ✓*

**Full SVD:**
```
U = [[2/√6,  0,     −1/√3],       Σ = [[√3, 0],
     [1/√6, −1/√2,   1/√3],            [0,  1],
     [1/√6,  1/√2,   1/√3]]            [0,  0]]

V = (1/√2)[[1,  1],
           [1, −1]]
```

**Checks:** rank(A) = 2 (two nonzero singular values) ✓; ‖A‖_F² = 1+1+0+1+1+0 = 4 and σ₁²+σ₂² = 3+1 = 4 ✓

---

### Example 13.5 — [Hard] Low-rank approximation

Given A with SVD having σ₁ = 10, σ₂ = 5, σ₃ = 1, σ₄ = 0.1, and

u₁ = (1/√2)(1,1,0,0)ᵀ, v₁ = (1/√2)(1,0,1,0)ᵀ,

(a) compute ‖A‖₂ and ‖A‖_F; (b) find the error ‖A − A₂‖₂ and ‖A − A₂‖_F; (c) what fraction of the energy does rank 2 capture? (d) write down the rank-1 approximation.

**Solution.**

**(a)** ‖A‖₂ = σ₁ = **10**
‖A‖_F = √(100 + 25 + 1 + 0.01) = √126.01 = **11.225**

**(b)** ‖A − A₂‖₂ = σ₃ = **1**
‖A − A₂‖_F = √(σ₃² + σ₄²) = √(1 + 0.01) = √1.01 = **1.005**

**(c)** Energy captured = (σ₁² + σ₂²)/Σσᵢ² = (100 + 25)/126.01 = 125/126.01 = **0.9920 → 99.20%**

*Rank 3 would capture 126/126.01 = 99.992%. The fourth component carries essentially nothing — a clear signal that the "true" rank is 3 and σ₄ = 0.1 is probably noise.*

**(d)** A₁ = σ₁u₁v₁ᵀ = 10 · (1/√2)(1,1,0,0)ᵀ · (1/√2)(1,0,1,0)
= (10/2)·(1,1,0,0)ᵀ(1,0,1,0)
```
A₁ = 5·[[1, 0, 1, 0],
        [1, 0, 1, 0],
        [0, 0, 0, 0],
        [0, 0, 0, 0]]
   = [[5, 0, 5, 0],
      [5, 0, 5, 0],
      [0, 0, 0, 0],
      [0, 0, 0, 0]]
```
**Check:** ‖A₁‖_F = √(4 × 25) = 10 = σ₁ ✓ (a rank-1 matrix has Frobenius norm equal to its single singular value).

---

### Example 13.6 — [Hard] Pseudoinverse and minimum-norm solution

Let A = [[1, 1], [1, 1]]. Find A⁺ via the SVD, and use it to solve the least squares problem for b = (2, 4)ᵀ.

**Solution.**

**SVD of A.** AᵀA = [[2, 2], [2, 2]], eigenvalues **4 and 0** → **σ₁ = 2, σ₂ = 0**, so **rank(A) = 1**.

λ=4: [[−2,2],[2,−2]] → **v₁ = (1/√2)(1, 1)**
λ=0: **v₂ = (1/√2)(1, −1)**

Av₁ = (1/√2)(2, 2) = 2·(1/√2)(1,1) → **u₁ = (1/√2)(1, 1)** ✓

**Pseudoinverse:**
A⁺ = (1/σ₁)v₁u₁ᵀ = (1/2)·(1/√2)(1,1)ᵀ·(1/√2)(1,1)
= (1/2)(1/2)[[1,1],[1,1]] = **(1/4)[[1, 1], [1, 1]]**

**Verify Penrose condition 1:** AA⁺A = [[1,1],[1,1]]·(1/4)[[1,1],[1,1]]·[[1,1],[1,1]]
AA⁺ = (1/4)[[2,2],[2,2]] = (1/2)[[1,1],[1,1]].
Times A: (1/2)[[2,2],[2,2]] = [[1,1],[1,1]] = A ✓

**Solve with b = (2, 4).**
x̂ = A⁺b = (1/4)[[1,1],[1,1]]·(2,4)ᵀ = (1/4)(6, 6) = **(1.5, 1.5)ᵀ**

**Checks.**
- **Fitted values:** Ax̂ = (1.5+1.5, 1.5+1.5) = (3, 3). Residual = (2−3, 4−3) = (−1, 1), with ‖r‖ = √2.
- **Is (3,3) the projection of (2,4) onto Col(A) = span{(1,1)}?** proj = ((2+4)/2)(1,1) = 3(1,1) = (3,3) ✓
- **Minimum norm?** All least squares solutions are x̂ + Nul(A) = (1.5, 1.5) + t(1, −1). Norm² = (1.5+t)² + (1.5−t)² = 4.5 + 2t², minimized at **t = 0** ✓ So (1.5, 1.5) is indeed the shortest ✓
- **Is x̂ ⊥ Nul(A)?** (1.5,1.5)·(1,−1) = 0 ✓ — as Theorem 13.5 requires.

---

### Example 13.7 — [Hard] Condition number

For A = [[1, 1], [1, 1.0001]], compute the singular values, the condition number, and demonstrate the ill-conditioning by solving Ax = b for b = (2, 2.0001) and for b = (2, 2.0002).

**Solution.**

**Singular values.** AᵀA = [[2, 2.0001], [2.0001, 2.00020001]].
Rather than grinding, use: σ₁σ₂ = |det A| and σ₁² + σ₂² = ‖A‖_F².
- det A = 1(1.0001) − 1 = **0.0001**
- ‖A‖_F² = 1 + 1 + 1 + 1.00020001 = 4.00020001

So σ₁² + σ₂² = 4.0002 and σ₁σ₂ = 0.0001.
Then σ₁² ≈ 4.0002 (since σ₂ is tiny), σ₁ ≈ **2.00005**, and σ₂ = 0.0001/2.00005 ≈ **0.00005**.

**Condition number:** κ(A) = σ₁/σ₂ ≈ 2.00005/0.00005 ≈ **40001 ≈ 4 × 10⁴**

**Ill-conditioning demonstration.**

**Solve Ax = (2, 2.0001):**
x₁ + x₂ = 2; x₁ + 1.0001x₂ = 2.0001.
Subtracting: 0.0001x₂ = 0.0001 → x₂ = 1, x₁ = 1.
**x = (1, 1)**

**Solve Ax = (2, 2.0002):**
Subtracting: 0.0001x₂ = 0.0002 → x₂ = 2, x₁ = 0.
**x = (0, 2)**

**Analysis.** The right-hand side changed by ‖Δb‖ = 0.0001 (a relative change of about 0.0001/2.83 ≈ 3.5 × 10⁻⁵). The solution changed from (1,1) to (0,2), i.e. ‖Δx‖ = √2 — a relative change of √2/√2 = **100%**.

**Amplification factor** ≈ 1/(3.5 × 10⁻⁵) ≈ 2.8 × 10⁴, comfortably within the bound κ(A) ≈ 4 × 10⁴ ✓

**Practical meaning.** Working in double precision (~16 significant digits), solving this system loses about log₁₀(4×10⁴) ≈ 4.6 digits — leaving about 11 reliable digits. If κ were 10¹⁶, no digits would survive. This is why condition numbers are reported alongside numerical solutions.

---

### Example 13.8 — [Very Hard] Image compression by SVD

A 4×4 grayscale block is
```
A = [[10, 10, 10, 10],
     [10, 10, 10, 10],
     [20, 20, 20, 20],
     [20, 20, 20, 20]]
```
Find its rank, its exact SVD, and explain why compression is so effective here. Then perturb one entry and discuss.

**Solution.**

**Step 1: rank.** Every column is identical: (10, 10, 20, 20)ᵀ. So **rank(A) = 1**.

**Step 2: write A as an outer product directly.**
A = c·dᵀ where c = (10, 10, 20, 20)ᵀ and d = (1, 1, 1, 1)ᵀ.

Normalize each:
- ‖c‖ = √(100 + 100 + 400 + 400) = √1000 = 10√10. **u₁ = (1/√10)(1, 1, 2, 2)**
- ‖d‖ = 2. **v₁ = (1/2)(1, 1, 1, 1)**

Then A = (10√10)(2) · u₁v₁ᵀ = **20√10 · u₁v₁ᵀ**.

**σ₁ = 20√10 ≈ 63.246, and σ₂ = σ₃ = σ₄ = 0.**

*Check:* ‖A‖_F² = 8(100) + 8(400)... careful: entries are 10 (8 of them) and 20 (8 of them).
= 8(100) + 8(400) = 800 + 3200 = 4000. And σ₁² = 400(10) = 4000 ✓

**Step 3: compression accounting.**
- Storing A directly: **16 numbers**
- Storing the rank-1 SVD: 4 (for u₁) + 4 (for v₁) + 1 (for σ₁) = **9 numbers**
- Reconstruction is **exact** — zero error, since rank(A) = 1 = k.

**Why so effective?** The image has enormous **redundancy** — every column is the same, every row is constant. Real images are like this in miniature: neighbouring pixels are strongly correlated, so the singular values decay rapidly, and a small k captures almost everything.

**Step 4: perturb one entry.** Change a₁₁ from 10 to 11:
```
A' = [[11, 10, 10, 10],
      [10, 10, 10, 10],
      [20, 20, 20, 20],
      [20, 20, 20, 20]]
```
Now **rank(A') = 2** — the first column (11,10,20,20) is no longer proportional to the others.

The new singular values are approximately σ₁ ≈ 63.4 and σ₂ ≈ 0.79, with σ₃ = σ₄ = 0.

*(Estimate: ‖A'‖_F² = 4000 + (121 − 100) = 4021, and det-based reasoning on the 2-dimensional row space gives σ₂ small.)*

**Energy in the first component:** σ₁²/4021 ≈ 63.4²/4021 = 4019/4021 ≈ **99.95%**.

**Interpretation.** The rank-1 truncation A'₁ still reproduces the image to within about 0.05% of its energy. The single perturbed pixel shows up as a tiny second singular value — exactly what a compression algorithm would discard as noise. **This is why JPEG-style and SVD-based compression works:** real data is *approximately* low rank, and the small singular values carry the fine detail (and the noise) that the eye barely notices.

**General rule of thumb.** For an m×n image compressed to rank k:
> **compression ratio = mn / [k(m + n + 1)]**
A 512×512 image at k = 50: 262144/(50 × 1025) = 262144/51250 ≈ **5.1×** compression, typically with visually acceptable quality.

---

## 13.4 Practice Numericals — Chapter 13

**[Easy]**

**P13.1** Find the singular values of A = [[4, 0], [0, 3]] and of A = [[0, 5], [0, 0]].

**P13.2** If A has singular values 6, 3, 0, what is rank(A)? What is ‖A‖₂? What is ‖A‖_F?

**P13.3** For a symmetric matrix with eigenvalues 4, −7, state the singular values.

**P13.4** Explain in one sentence why every matrix has an SVD but not every matrix has an eigendecomposition.

**P13.5** If A is 5×3 with rank 3, what are the dimensions of U, Σ, V in the full SVD?

**[Medium]**

**P13.6** Find the SVD of A = [[2, 0], [0, 1], [0, 0]].

**P13.7** Compute AᵀA and the singular values of A = [[1, 2], [2, 4]]. What is the rank?

**P13.8** Given σ₁ = 8, σ₂ = 4, σ₃ = 2, σ₄ = 1, find the fraction of energy captured by rank-2 truncation and the Frobenius error.

**P13.9** Find A⁺ for A = [[2, 0], [0, 0]].

**P13.10** Compute the condition number of A = [[2, 0], [0, 0.5]].

**P13.11** Show that A and Aᵀ have the same singular values.

**[Hard]**

**P13.12** Find the full SVD of A = [[1, 0, 1], [0, 1, 1]].

**P13.13** Find the SVD of A = [[2, 2], [−1, 1]] and use it to describe the image of the unit circle.

**P13.14** For A = [[1, 2], [2, 4], [3, 6]], find the rank, the SVD, and the pseudoinverse. Then find the minimum-norm least squares solution for b = (1, 1, 1)ᵀ.

**P13.15** Prove that the nonzero eigenvalues of AᵀA and AAᵀ are identical, and deduce that A and Aᵀ have the same nonzero singular values.

**P13.16** Prove ‖A‖_F² = Σσᵢ², and that ‖A‖₂ = σ₁.

**P13.17** Let A be invertible n×n with SVD UΣVᵀ. Find the SVD of A⁻¹ and prove κ(A⁻¹) = κ(A).

**[Very Hard]**

**P13.18** Prove the Eckart–Young theorem in the spectral norm: for any B with rank(B) ≤ k, ‖A − B‖₂ ≥ σ_{k+1}. (Hint: dimension count on Nul(B) and span{v₁,...,v_{k+1}}.)

**P13.19** Prove that x̂ = A⁺b is a least squares solution of Ax = b and that it has the minimum norm among all least squares solutions.

**P13.20** Let A be m×n with rank r. Prove that the **polar decomposition** A = QP exists when m = n, with Q orthogonal and P symmetric positive semidefinite, and that P = (AᵀA)^{1/2}. Compute it for A = [[3, 2], [2, 3]].

**P13.21** The matrix A = [[3, 1, 1], [−1, 3, 1]] is 2×3. Compute AAᵀ, find its eigenvalues and thereby the singular values of A, and verify Σσᵢ² = ‖A‖_F². Then find A⁺ and the minimum-norm solution of Ax = (1, 0)ᵀ.

---

## 13.5 Solutions to Chapter 13 Practice

**S13.1** For [[4,0],[0,3]]: AᵀA = diag(16, 9) → **σ = 4, 3**.
For [[0,5],[0,0]]: AᵀA = [[0,0],[0,25]] → eigenvalues 0, 25 → **σ = 5, 0**.
*(Note the second matrix has both eigenvalues 0 but a nonzero singular value — see Example 13.2.)*

**S13.2** **rank = 2** (two nonzero singular values). ‖A‖₂ = σ₁ = **6**. ‖A‖_F = √(36 + 9) = **√45 = 3√5 ≈ 6.708**.

**S13.3** For symmetric A, σᵢ = |λᵢ|. **Singular values: 7 and 4** (sorted descending).

**S13.4** The SVD is built from AᵀA, which is **always symmetric positive semidefinite** and therefore always orthogonally diagonalizable by the Spectral Theorem; eigendecomposition of A itself requires A to be square *and* non-defective, which can fail.

**S13.5** Full SVD of a 5×3 matrix: **U is 5×5, Σ is 5×3, V is 3×3.**
*(Reduced: U_r 5×3, Σ_r 3×3, V_r 3×3.)*

**S13.6** AᵀA = [[4, 0], [0, 1]]. Eigenvalues 4, 1 → **σ₁ = 2, σ₂ = 1**.
v₁ = (1,0), v₂ = (0,1) → **V = I₂**.
Av₁ = (2, 0, 0) → u₁ = (1, 0, 0). Av₂ = (0, 1, 0) → u₂ = (0, 1, 0).
Extend: u₃ = (0, 0, 1).
```
U = I₃,   Σ = [[2, 0], [0, 1], [0, 0]],   V = I₂
```
*(A was already in "SVD form" — a diagonal matrix with positive entries needs no rotation.)*

**S13.7** AᵀA = [[1,2],[2,4]]·[[1,2],[2,4]] = [[1+4, 2+8],[2+8, 4+16]] = [[5, 10], [10, 20]].
Eigenvalues: tr = 25, det = 100 − 100 = 0 → **λ = 25, 0**.
**σ₁ = 5, σ₂ = 0 → rank(A) = 1** ✓
*(Indeed row 2 = 2 × row 1.)*
*Check: ‖A‖_F² = 1 + 4 + 4 + 16 = 25 = σ₁² ✓*

**S13.8** Total energy = 64 + 16 + 4 + 1 = 85.
Rank-2 energy = 64 + 16 = 80. **Fraction = 80/85 = 16/17 ≈ 0.941 → 94.1%.**
**Frobenius error** = √(σ₃² + σ₄²) = √(4 + 1) = **√5 ≈ 2.236**.

**S13.9** A = [[2,0],[0,0]] is already diagonal with σ₁ = 2, σ₂ = 0.
Invert the nonzero singular value, leave the zero alone, transpose the shape:
**A⁺ = [[1/2, 0], [0, 0]]**
*Check AA⁺A = [[2,0],[0,0]]·[[0.5,0],[0,0]]·[[2,0],[0,0]] = [[1,0],[0,0]]·[[2,0],[0,0]] = [[2,0],[0,0]] = A ✓*

**S13.10** Diagonal with positive entries → singular values are 2 and 0.5.
**κ(A) = 2/0.5 = 4.** Well-conditioned.

**S13.11** The singular values of A are the square roots of the eigenvalues of AᵀA; those of Aᵀ are the square roots of the eigenvalues of (Aᵀ)ᵀAᵀ = **AAᵀ**.

By Example 9.9 (AB and BA share nonzero eigenvalues, with B = Aᵀ), **AᵀA and AAᵀ have the same nonzero eigenvalues** ✓

Hence A and Aᵀ have the same nonzero singular values (the numbers of trailing zeros may differ, reflecting the different sizes). ∎

*Equivalently, from the SVD: A = UΣVᵀ ⟹ Aᵀ = VΣᵀUᵀ, which is an SVD of Aᵀ with the same diagonal entries.*

**S13.12** A = [[1, 0, 1], [0, 1, 1]] (2×3). Easier to start with **AAᵀ** (2×2) since m < n.

AAᵀ = [[1+0+1, 0+0+1], [0+0+1, 0+1+1]] = [[2, 1], [1, 2]].
Eigenvalues: 3 and 1 → **σ₁ = √3, σ₂ = 1**.

**Left singular vectors** (eigenvectors of AAᵀ):
λ=3: **u₁ = (1/√2)(1, 1)**; λ=1: **u₂ = (1/√2)(1, −1)**

**Right singular vectors** from vᵢ = Aᵀuᵢ/σᵢ:
Aᵀu₁ = (1/√2)·[[1,0],[0,1],[1,1]]·(1,1)ᵀ = (1/√2)(1, 1, 2). Divide by √3:
**v₁ = (1/√6)(1, 1, 2)**
Aᵀu₂ = (1/√2)(1, −1, 0). Divide by 1:
**v₂ = (1/√2)(1, −1, 0)**

**v₃** spans Nul(A): solve x₁ + x₃ = 0, x₂ + x₃ = 0 → x₁ = x₂ = −x₃.
**v₃ = (1/√3)(1, 1, −1)**
*Check v₃·v₁ = (1 + 1 − 2)/√18 = 0 ✓; v₃·v₂ = (1 − 1 + 0)/√6 = 0 ✓*

```
U = (1/√2)[[1,  1],       Σ = [[√3, 0, 0],
           [1, −1]]            [0,  1, 0]]

V = [[1/√6,  1/√2,  1/√3],
     [1/√6, −1/√2,  1/√3],
     [2/√6,  0,    −1/√3]]
```
*Check: ‖A‖_F² = 1+0+1+0+1+1 = 4 = 3 + 1 ✓*

**S13.13** A = [[2, 2], [−1, 1]].
AᵀA = [[4+1, 4−1], [4−1, 4+1]] = [[5, 3], [3, 5]].
Eigenvalues: 5±3 → **8 and 2** → **σ₁ = 2√2 ≈ 2.828, σ₂ = √2 ≈ 1.414**.

λ=8: [[−3,3],[3,−3]] → **v₁ = (1/√2)(1, 1)**
λ=2: **v₂ = (1/√2)(1, −1)**

Av₁ = (1/√2)(4, 0) = (2√2)·(1, 0) → **u₁ = (1, 0)**
Av₂ = (1/√2)(0, −2) = √2·(0, −1) → **u₂ = (0, −1)**

```
U = [[1, 0], [0, −1]]    Σ = [[2√2, 0], [0, √2]]    V = (1/√2)[[1, 1], [1, −1]]
```

**Image of the unit circle.** A maps the unit circle to an **ellipse** with
- **semi-major axis 2√2 ≈ 2.83** along the direction u₁ = (1, 0) (the x-axis)
- **semi-minor axis √2 ≈ 1.41** along u₂ = (0, −1) (the y-axis)

**Area of the ellipse** = π·σ₁·σ₂ = π(2√2)(√2) = **4π**.
*Check: area scaling factor = |det A| = |2(1) − 2(−1)| = 4, and the unit disc has area π → image area 4π ✓*

The input directions achieving the extremes are v₁ = (1,1)/√2 (maximally stretched, to 2.83) and v₂ = (1,−1)/√2 (least stretched, to 1.41).

**S13.14** A = [[1,2],[2,4],[3,6]]. Column 2 = 2 × column 1 → **rank(A) = 1**.

AᵀA = [[1+4+9, 2+8+18], [2+8+18, 4+16+36]] = [[14, 28], [28, 56]].
Eigenvalues: tr = 70, det = 784 − 784 = 0 → **λ = 70, 0** → **σ₁ = √70 ≈ 8.367, σ₂ = 0**.

λ=70: [[−56, 28],[28, −14]] → 2v₁ = v₂ → **v₁ = (1/√5)(1, 2)**
λ=0: **v₂ = (1/√5)(2, −1)**

Av₁ = (1/√5)(1+4, 2+8, 3+12) = (1/√5)(5, 10, 15) = √5(1, 2, 3).
‖Av₁‖ = √5·√14 = √70 ✓ = σ₁
**u₁ = (1/√14)(1, 2, 3)**

**Pseudoinverse:** A⁺ = (1/σ₁)v₁u₁ᵀ
= (1/√70)·(1/√5)(1,2)ᵀ·(1/√14)(1,2,3)
= (1/(√70·√70))(1,2)ᵀ(1,2,3)
= (1/70)·[[1, 2, 3], [2, 4, 6]]

```
A⁺ = (1/70)[[1, 2, 3],
            [2, 4, 6]]
```

**Minimum-norm least squares solution for b = (1,1,1)ᵀ:**
x̂ = A⁺b = (1/70)(1+2+3, 2+4+6) = (1/70)(6, 12) = **(3/35, 6/35)ᵀ ≈ (0.0857, 0.1714)**

**Checks.**
- Ax̂ = (3/35 + 12/35, 6/35 + 24/35, 9/35 + 36/35) = (15/35, 30/35, 45/35) = (3/7, 6/7, 9/7).
- Is this the projection of (1,1,1) onto span{(1,2,3)}? proj = ((1+2+3)/14)(1,2,3) = (6/14)(1,2,3) = (3/7, 6/7, 9/7) ✓
- **Minimum norm?** x̂ ⊥ Nul(A) = span{(2,−1)}: (3/35, 6/35)·(2,−1) = (6 − 6)/35 = 0 ✓

**S13.15** Let λ ≠ 0 be an eigenvalue of AᵀA with eigenvector x ≠ 0:
AᵀAx = λx.

Set **y = Ax**. Then y ≠ 0 (if y = 0 then λx = Aᵀ0 = 0, forcing x = 0 since λ ≠ 0).

Compute:
AAᵀy = AAᵀAx = A(λx) = λ(Ax) = **λy** ✓

So λ is an eigenvalue of AAᵀ. The reverse inclusion follows by symmetry (swap the roles of A and Aᵀ).

Moreover x ↦ Ax is a bijection between the λ-eigenspaces (inverse y ↦ (1/λ)Aᵀy), so **multiplicities match** ✓

**Deduction.** Singular values of A = √(nonzero eigenvalues of AᵀA); singular values of Aᵀ = √(nonzero eigenvalues of AAᵀ). These sets are equal, so **A and Aᵀ have the same nonzero singular values** ✓ ∎

**S13.16**
**Frobenius.** ‖A‖_F² = tr(AᵀA). Substituting A = UΣVᵀ:
AᵀA = VΣᵀUᵀUΣVᵀ = VΣᵀΣVᵀ
tr(AᵀA) = tr(VΣᵀΣVᵀ) = tr(ΣᵀΣVᵀV) = tr(ΣᵀΣ) *(using tr(XY) = tr(YX))*
ΣᵀΣ is diagonal with entries σᵢ², so
**‖A‖_F² = Σσᵢ²** ✓

**Spectral.** ‖A‖₂ = max_{‖x‖=1}‖Ax‖. Since ‖Ax‖² = xᵀAᵀAx and AᵀA is symmetric with largest eigenvalue σ₁², Theorem 11.5 gives
max_{‖x‖=1} xᵀAᵀAx = σ₁²
Hence **‖A‖₂ = σ₁** ✓, attained at x = v₁ ∎

**S13.17** From A = UΣVᵀ with all σᵢ > 0:
A⁻¹ = (UΣVᵀ)⁻¹ = (Vᵀ)⁻¹Σ⁻¹U⁻¹ = **VΣ⁻¹Uᵀ**

Σ⁻¹ = diag(1/σ₁, ..., 1/σₙ). But an SVD requires the singular values in **decreasing** order, and
1/σ₁ ≤ 1/σ₂ ≤ ... ≤ 1/σₙ
so we must **reverse the order**. Let J be the reversal permutation matrix. Then

> **A⁻¹ = (VJ)(JΣ⁻¹J)(UJ)ᵀ**

is a valid SVD, with singular values **1/σₙ ≥ 1/σ_{n−1} ≥ ... ≥ 1/σ₁**.

**Condition number:**
κ(A⁻¹) = (largest singular value of A⁻¹)/(smallest) = (1/σₙ)/(1/σ₁) = **σ₁/σₙ = κ(A)** ✓ ∎

*(Makes sense: A and A⁻¹ describe the same "distortion", so they are equally hard to work with numerically.)*

**S13.18** Let B have rank(B) ≤ k, so **dim Nul(B) ≥ n − k**.

Let W = span{v₁, v₂, ..., v_{k+1}}, which has **dim W = k + 1**.

**Dimension count.** dim Nul(B) + dim W ≥ (n − k) + (k + 1) = n + 1 > n.
Since both are subspaces of ℝⁿ, they must intersect nontrivially:
> **there exists x ∈ Nul(B) ∩ W with ‖x‖ = 1**

**Estimate ‖(A − B)x‖.** Since Bx = 0,
‖(A − B)x‖ = ‖Ax‖.

Write x = Σ_{i=1}^{k+1} cᵢvᵢ with Σcᵢ² = 1 (as x ∈ W and the vᵢ are orthonormal). Then
Ax = Σ_{i=1}^{k+1} cᵢAvᵢ = Σ_{i=1}^{k+1} cᵢσᵢuᵢ

Since the uᵢ are orthonormal:
‖Ax‖² = Σ_{i=1}^{k+1} cᵢ²σᵢ² ≥ σ_{k+1}² Σcᵢ² = **σ_{k+1}²**
*(using σᵢ ≥ σ_{k+1} for i ≤ k+1)*

Therefore
‖A − B‖₂ = max_{‖y‖=1}‖(A−B)y‖ ≥ ‖(A−B)x‖ = ‖Ax‖ ≥ **σ_{k+1}** ✓

**Attainment.** For B = A_k:
A − A_k = Σ_{i=k+1}^{r} σᵢuᵢvᵢᵀ,
which is itself in SVD form with largest singular value σ_{k+1}. So ‖A − A_k‖₂ = σ_{k+1} ✓

**Hence A_k achieves the minimum** ∎

**S13.19**
**Step 1: x̂ = A⁺b is a least squares solution.**
Using the reduced SVD A = U_rΣ_rV_rᵀ and A⁺ = V_rΣ_r⁻¹U_rᵀ:
**Ax̂ = U_rΣ_rV_rᵀV_rΣ_r⁻¹U_rᵀb = U_rU_rᵀb**

But U_rU_rᵀ is exactly the **orthogonal projection onto Col(A)** (since u₁,...,u_r is an orthonormal basis of Col(A) — §5.2.5).

So Ax̂ = proj_{Col A}(b), which by the Best Approximation Theorem minimizes ‖b − Ax‖ ✓

**Step 2: minimum norm.**
Note x̂ = V_rΣ_r⁻¹U_rᵀb ∈ **Col(V_r) = Row(A)**.

Every least squares solution has the form x = x̂ + h with h ∈ Nul(A) (S6.17). Since **Row(A) ⊥ Nul(A)**, we have x̂ ⊥ h, so by Pythagoras:

‖x‖² = ‖x̂‖² + ‖h‖² ≥ ‖x̂‖²

with equality **only when h = 0** ✓

**Therefore x̂ = A⁺b is the unique minimum-norm least squares solution** ∎

**S13.20**
**Existence.** Let A = UΣVᵀ (square, so U, V both n×n orthogonal). Insert VᵀV = I:

A = UΣVᵀ = (UVᵀ)(VΣVᵀ)

Define **Q = UVᵀ** and **P = VΣVᵀ**.
- Q is a product of orthogonal matrices → **orthogonal** ✓
- P = VΣVᵀ is symmetric (Pᵀ = VΣᵀVᵀ = VΣVᵀ = P ✓) with eigenvalues σᵢ ≥ 0 → **positive semidefinite** ✓

**A = QP** ✓

**Identifying P.** AᵀA = PᵀQᵀQP = PᵀP = P², and P is positive semidefinite, so
**P = (AᵀA)^{1/2}** ✓ (the unique positive semidefinite square root) ∎

*Interpretation:* every linear map is a **pure stretch followed by a pure rotation** — the matrix analogue of writing a complex number as z = re^{iθ}.

**Computation for A = [[3, 2], [2, 3]].**
From Example 13.3: U = V = (1/√2)[[1,1],[1,−1]], Σ = diag(5, 1).

**Q = UVᵀ = VVᵀ = I** (since V is orthogonal) → **Q = I₂**
**P = VΣVᵀ** = (1/2)[[1,1],[1,−1]]·diag(5,1)·[[1,1],[1,−1]]
= (1/2)[[5, 1],[5, −1]]·[[1,1],[1,−1]]
= (1/2)[[5+1, 5−1],[5−1, 5+1]] = (1/2)[[6,4],[4,6]] = **[[3, 2], [2, 3]] = A**

**A = I·A** ✓ — trivially true here, because A was already symmetric positive definite, so it *is* its own "stretch" with no rotation needed. (This is the general rule: A = QP with Q = I exactly when A is symmetric positive semidefinite.)

**S13.21** A = [[3, 1, 1], [−1, 3, 1]] (2×3). Use **AAᵀ** (2×2).

**AAᵀ:**
- (1,1): 9 + 1 + 1 = 11
- (1,2): −3 + 3 + 1 = 1
- (2,2): 1 + 9 + 1 = 11
```
AAᵀ = [[11, 1], [1, 11]]
```

**Eigenvalues:** 11 ± 1 = **12 and 10**.
**Singular values: σ₁ = √12 = 2√3 ≈ 3.464, σ₂ = √10 ≈ 3.162.**

**Check Σσᵢ² = ‖A‖_F²:** 12 + 10 = 22. And ‖A‖_F² = 9+1+1+1+9+1 = **22** ✓

**Left singular vectors** (eigenvectors of AAᵀ):
λ=12: [[−1,1],[1,−1]] → **u₁ = (1/√2)(1, 1)**
λ=10: [[1,1],[1,1]] → **u₂ = (1/√2)(1, −1)**

**Right singular vectors:** vᵢ = Aᵀuᵢ/σᵢ.
Aᵀu₁ = (1/√2)·[[3,−1],[1,3],[1,1]]·(1,1)ᵀ = (1/√2)(2, 4, 2) = √2(1, 2, 1).
‖·‖ = √2·√6 = √12 ✓ = σ₁.
**v₁ = (1/√6)(1, 2, 1)**

Aᵀu₂ = (1/√2)(3+1, 1−3, 1−1) = (1/√2)(4, −2, 0) = √2(2, −1, 0).
‖·‖ = √2·√5 = √10 ✓ = σ₂.
**v₂ = (1/√5)(2, −1, 0)**

**Pseudoinverse:** A⁺ = (1/σ₁)v₁u₁ᵀ + (1/σ₂)v₂u₂ᵀ

Term 1: (1/√12)·(1/√6)(1,2,1)ᵀ·(1/√2)(1,1) = (1/(√12·√12))(1,2,1)ᵀ(1,1) = (1/12)[[1,1],[2,2],[1,1]]
Term 2: (1/√10)·(1/√5)(2,−1,0)ᵀ·(1/√2)(1,−1) = (1/10)[[2,−2],[−1,1],[0,0]]

```
A⁺ = (1/12)[[1, 1], [2, 2], [1, 1]] + (1/10)[[2, −2], [−1, 1], [0, 0]]
```
Common denominator 60:
```
A⁺ = (1/60)[[5, 5], [10, 10], [5, 5]] + (1/60)[[12, −12], [−6, 6], [0, 0]]
   = (1/60)[[17, −7],
            [ 4, 16],
            [ 5,  5]]
```

**Minimum-norm solution of Ax = (1, 0)ᵀ:**
x̂ = A⁺(1,0)ᵀ = (1/60)(17, 4, 5) = **(17/60, 1/15, 1/12)ᵀ ≈ (0.2833, 0.0667, 0.0833)**

**Verification.**
Ax̂ = (3(17/60) + 1(4/60) + 1(5/60), −1(17/60) + 3(4/60) + 1(5/60))
= ((51 + 4 + 5)/60, (−17 + 12 + 5)/60) = (60/60, 0/60) = **(1, 0)** ✓

The system is **exactly solvable** (A has full row rank 2, so it is onto ℝ²) — there are infinitely many solutions, and A⁺b picks the shortest one.

**Confirm minimum norm:** Nul(A) is 1-dimensional. Solve Ax = 0: from v₁, v₂ orthogonality, Nul(A) = span{v₃} where v₃ ⊥ v₁, v₂.
v₃ ∝ (1,2,1) × (2,−1,0) = (2(0) − 1(−1), 1(2) − 1(0), 1(−1) − 2(2)) = (1, 2, −5).
*Check: A(1,2,−5)ᵀ = (3 + 2 − 5, −1 + 6 − 5) = (0, 0) ✓*
**x̂ ⊥ Nul(A)?** (17, 4, 5)·(1, 2, −5) = 17 + 8 − 25 = **0** ✓ Minimum norm confirmed.

---
# Chapter 14 — Applications in Data Compression, Recommendation Systems, Image Representation and Machine Learning

---

## 14.1 Explain Like I'm Five

Here's the single idea that all of this chapter rests on:

> **Real data is never as complicated as it looks.**

A 1000×1000 photograph has a million numbers in it. But neighbouring pixels are almost the same, edges run in straight lines, and the sky is all one colour. The *true* complexity is far smaller than a million. In matrix language: the matrix is **approximately low rank**, and the SVD finds exactly how low.

The same is true everywhere:
- A survey with 50 questions might really be measuring 4 underlying traits. → **PCA**
- A million users rating a thousand movies might really come down to a dozen taste dimensions (action-vs-drama, old-vs-new, mainstream-vs-arthouse). → **Recommender systems**
- Ten thousand documents using a hundred thousand words might really be about 20 topics. → **Latent Semantic Analysis**

In every case the recipe is the same: **write the data as a matrix, find the few directions that carry most of the variation, and throw away the rest.** What you throw away is mostly noise and redundancy. What you keep is the signal.

That's it. PCA, SVD, LSA, collaborative filtering, image compression, and the core of dimensionality reduction in machine learning are all the same theorem wearing different clothes.

---

## 14.2 Principal Component Analysis (PCA)

### 14.2.1 Set-up

Let X be an m×n **data matrix**: m observations (rows), n features (columns).

**Step 1 — Centre.** Compute the column means x̄ and form
> **X_c = X − 1x̄ᵀ**
Every column of X_c now has mean zero. **This step is mandatory** — skipping it makes the first principal component point at the data's centroid rather than at its direction of spread.

**Step 2 — Covariance matrix.**
> **S = (1/(m−1)) X_cᵀX_c** (n×n, symmetric, positive semidefinite)

Entry Sᵢⱼ is the sample covariance of features i and j; Sᵢᵢ is the variance of feature i.

**Step 3 — Diagonalize.** By the Spectral Theorem, S = QΛQᵀ with orthonormal eigenvectors q₁, ..., qₙ and eigenvalues λ₁ ≥ λ₂ ≥ ... ≥ λₙ ≥ 0.

> **The qᵢ are the principal components (principal directions).**
> **λᵢ is the variance of the data along direction qᵢ.**

**Step 4 — Project.** The **scores** (coordinates in the new basis) are
> **Y = X_c Q**, or for a k-dimensional reduction, **Y_k = X_c Q_k** with Q_k = [q₁ ... q_k].

### 14.2.2 Why PCA Works — The Optimization View

By Theorem 11.5 (Rayleigh quotient), the unit vector w maximizing the variance of the projected data,
> Var(X_c w) = wᵀSw,
is exactly **q₁**, with maximum value λ₁. The next-best direction **orthogonal to q₁** is q₂, and so on.

**So PCA = "find the directions of maximum variance, one at a time, each perpendicular to the last."** The Spectral Theorem guarantees such a set exists and is orthogonal.

**Explained variance ratio:**
> **λ_k / (λ₁ + ... + λₙ)** for component k
> **(λ₁ + ... + λ_k)/(λ₁ + ... + λₙ)** cumulative for the first k

Note Σλᵢ = tr(S) = total variance. Choosing k so the cumulative ratio exceeds 90–95% is standard. A **scree plot** (λᵢ versus i) shows where the "elbow" is.

### 14.2.3 PCA via SVD

Compute the SVD of the **centred** matrix directly: X_c = UΣVᵀ. Then

> X_cᵀX_c = VΣᵀΣVᵀ

so the **right singular vectors V are the principal components** and the eigenvalues are

> **λᵢ = σᵢ²/(m − 1)**

The scores are **Y = X_cV = UΣ**.

**Always do it this way numerically** — forming X_cᵀX_c squares the condition number (§13.2.6), losing accuracy. The SVD route never forms the covariance matrix at all.

### 14.2.4 Practical Notes

- **Standardize** (divide each centred column by its standard deviation) when features have different units; otherwise the feature with the largest numerical range dominates. Standardized PCA = eigen-analysis of the **correlation** matrix.
- PCA is **unsupervised** — it ignores any labels. The direction of greatest variance is not necessarily the most useful for classification. (LDA is the supervised counterpart.)
- Principal components are **linear combinations of all original features**, which can hurt interpretability.
- **Whitening:** rescale each score by 1/√λᵢ to make the transformed covariance equal to I.

---

## 14.3 Image Representation and Compression

### 14.3.1 SVD Image Compression

An image is an m×n matrix A. Compute A = UΣVᵀ and truncate to rank k:

> **A_k = Σ_{i=1}^{k} σᵢuᵢvᵢᵀ**

By Eckart–Young (Theorem 13.4), this is the **best possible** rank-k approximation.

**Storage:**
| | Numbers stored |
|---|---|
| Original A | mn |
| Rank-k SVD | k(m + n + 1) |
| **Compression ratio** | **mn / [k(m+n+1)]** |

Compression is worthwhile whenever k < mn/(m+n+1), roughly k < min(m,n)/2 for a square image.

**Relative error:** ‖A − A_k‖_F/‖A‖_F = √(Σ_{i>k}σᵢ²)/√(Σ_iσᵢ²).

**Why images compress well:** natural images have rapidly decaying singular values because of spatial correlation. Typical photographs retain 95%+ of their Frobenius energy at k ≈ 5–10% of full rank.

### 14.3.2 Other Linear-Algebraic Image Operations

- **Convolution** (blur, sharpen, edge detect) = multiplication by a banded **Toeplitz** matrix; separable kernels factor as an outer product kh·kvᵀ, which is exactly a rank-1 structure allowing a 2-pass instead of a full 2-D pass.
- **Discrete Cosine Transform (DCT)** — the basis of JPEG — is multiplication by a fixed orthogonal matrix C, applied blockwise as CACᵀ on 8×8 blocks. Unlike SVD, the basis is fixed (no need to transmit U and V), which is why JPEG is practical.
- **Eigenfaces:** PCA applied to a database of face images; each face becomes a short vector of coordinates in the top-k "eigenface" basis. This was the first practical face recognition method.

### 14.3.3 SVD versus DCT/JPEG

| | SVD | DCT (JPEG) |
|---|---|---|
| Basis | adapted to the specific image | fixed, universal |
| Optimality | provably best rank-k (Eckart–Young) | not optimal, but close for natural images |
| Cost | O(mn·min(m,n)) per image | O(mn log n), blockwise |
| Must transmit basis? | **yes** (U and V) | **no** |
| Used in practice | rarely for photos; common for data | universal |

---

## 14.4 Recommendation Systems

### 14.4.1 The Setup

Let R be an m×n **rating matrix**: m users, n items, Rᵤᵢ = rating of item i by user u. **Most entries are missing** — real matrices are 95–99% empty.

**Goal:** predict the missing entries.

**Key assumption:** R is approximately **low rank**. A few hidden "taste factors" explain most ratings.

### 14.4.2 Matrix Factorization

Model:
> **R ≈ PQᵀ**

where P is m×k (**user factors**) and Q is n×k (**item factors**), with k ≪ min(m,n).

The predicted rating is the inner product:
> **r̂ᵤᵢ = pᵤ · qᵢ**

**Interpretation.** If k = 2 with factors "amount of action" and "amount of romance", then qᵢ describes how much of each the film has, and pᵤ describes how much the user likes each. Their dot product predicts enjoyment.

**Training.** Minimize squared error over the **observed** entries only, with regularization:

> **min_{P,Q} Σ_{(u,i) ∈ observed} (rᵤᵢ − pᵤ·qᵢ)² + λ(‖P‖_F² + ‖Q‖_F²)**

The regularization term λ(...) is exactly ridge regression (P6.20) applied to both factors; it prevents overfitting on users with few ratings.

**Why not just use the SVD?** Because the SVD requires a **complete** matrix. With missing entries the problem becomes non-convex and is solved by:
- **ALS (Alternating Least Squares):** fix Q, solve for P by ordinary least squares (a convex problem!); fix P, solve for Q; repeat. Each step is exactly Chapter 6's normal equations. Highly parallelizable.
- **SGD (Stochastic Gradient Descent):** update pᵤ and qᵢ after each observed rating.

**Bias terms.** A better model adds offsets:
> **r̂ᵤᵢ = μ + bᵤ + bᵢ + pᵤ·qᵢ**
where μ is the global mean, bᵤ the user's tendency to rate high or low, bᵢ the item's overall quality. These alone explain a surprising amount of the variance.

### 14.4.3 Neighbourhood Methods

Instead of factorizing, measure similarity directly, using **cosine similarity** (Chapter 5):

> **sim(u, v) = (rᵤ · r_v)/(‖rᵤ‖‖r_v‖)**

computed over commonly-rated items. Then predict by a similarity-weighted average of similar users' (or items') ratings:

> **r̂ᵤᵢ = Σ_v sim(u,v)·r_{vi} / Σ_v |sim(u,v)|**

**Item-based** filtering (similarity between items rather than users) is usually preferred in practice — item similarities are more stable over time and there are usually fewer items than users.

### 14.4.4 Evaluation

- **RMSE** = √((1/N)Σ(rᵤᵢ − r̂ᵤᵢ)²) — the classic metric (used in the Netflix Prize)
- **MAE** = (1/N)Σ|rᵤᵢ − r̂ᵤᵢ|
- Ranking metrics (Precision@k, NDCG) are more relevant in production, since users see a ranked list, not predicted numbers.

**Known difficulties:** the **cold-start problem** (new users/items have no data), popularity bias, and the fact that missing ratings are not missing at random.

---

## 14.5 Latent Semantic Analysis

Apply a truncated SVD to the term–document matrix A (V terms × D documents, TF–IDF weighted — §8.2.3):

> **A ≈ A_k = U_kΣ_kV_kᵀ**

- Columns of **U_k** = term vectors in "topic space"
- Columns of **V_k** = document vectors in "topic space"
- Each of the k dimensions is a **latent topic** — a weighted combination of co-occurring words

**What this buys you:**
- **Synonymy handled:** "car" and "automobile" rarely co-occur but appear in similar contexts, so they land near each other in topic space. Raw keyword matching misses this entirely.
- **Polysemy partly handled:** "bank" gets split across a finance topic and a river topic.
- **Dimension reduction:** documents become k-dimensional (k ≈ 100–300) instead of 100,000-dimensional.

**Querying:** map a query q into topic space as **q̂ = Σ_k⁻¹U_kᵀq**, then rank documents by cosine similarity with the columns of V_k.

**Modern descendants:** LSA is the linear-algebraic ancestor of word2vec, GloVe, and transformer embeddings. All of them share the idea of representing meaning as a **dense vector in a low-dimensional space where similarity is an angle**.

---

## 14.6 Linear Algebra in Machine Learning

### 14.6.1 Linear Regression

Already Chapter 6. Given design matrix X and targets y:
> **ŵ = (XᵀX)⁻¹Xᵀy** (normal equations)
> **ŵ_ridge = (XᵀX + λI)⁻¹Xᵀy** (ridge/Tikhonov — always invertible, P6.20)

### 14.6.2 Neural Networks

A feedforward layer is
> **h = σ(Wx + b)**

— a matrix multiply, a vector add, and an elementwise nonlinearity. A deep network is a composition of these. **Without the nonlinearity σ, the whole network would collapse into a single matrix** (composition of linear maps is linear), which is why σ is essential.

**Backpropagation** is the chain rule expressed with **Jacobian matrices**; training is a sequence of matrix-matrix products, which is precisely why GPUs (built for exactly that operation) transformed the field.

### 14.6.3 Where Each Tool Appears

| Linear algebra concept | ML application |
|---|---|
| Least squares (Ch 6) | linear/polynomial regression |
| Pseudoinverse (Ch 13) | rank-deficient regression, minimum-norm solutions |
| Ridge = (AᵀA + λI)⁻¹ | regularization; also fixes collinearity |
| Eigenvalues of the Hessian (Ch 11) | second-order optimization; convexity; saddle detection |
| Positive definiteness | valid kernels (Gram matrix must be PSD) |
| SVD / low rank | PCA, compression, model compression (LoRA) |
| Orthogonal matrices | stable weight initialization; normalizing flows |
| Condition number | why feature scaling speeds up gradient descent |
| Markov chains (Ch 8) | PageRank, MCMC, reinforcement learning |
| Graph Laplacian (Ch 8) | spectral clustering, graph neural networks |
| Projections (Ch 5) | attention as weighted projection; residual connections |

### 14.6.4 Why Condition Number Governs Gradient Descent

For a quadratic loss f(x) = ½xᵀAx − bᵀx with A symmetric positive definite, gradient descent with optimal step size converges at the rate

> **‖x_k − x*‖ ≤ [(κ − 1)/(κ + 1)]ᵏ ‖x₀ − x*‖**, where κ = λ_max/λ_min

- κ = 1 (perfectly round bowl) → converges in **one step**
- κ = 100 (long narrow valley) → factor 99/101 ≈ 0.980 per step — needs ~350 steps for 10⁻³ accuracy
- κ = 10⁴ → glacial

**This is the mathematical reason feature standardization matters.** Features on wildly different scales produce a large κ, so gradient descent zig-zags down a narrow valley. Standardizing makes the level sets rounder, shrinking κ, and training speeds up dramatically. Adam and other adaptive methods approximate a per-coordinate rescaling for the same reason.

---

## 14.7 Solved Examples

### Example 14.1 — [Easy] Centring and covariance

Given the data matrix
```
X = [[2, 4],
     [4, 6],
     [6, 8],
     [8, 10]]
```
compute the mean vector, the centred matrix, and the covariance matrix.

**Solution.**
**Column means:** x̄₁ = (2+4+6+8)/4 = 5; x̄₂ = (4+6+8+10)/4 = 7. **x̄ = (5, 7).**

**Centred:**
```
X_c = [[−3, −3],
       [−1, −1],
       [ 1,  1],
       [ 3,  3]]
```

**X_cᵀX_c:**
- (1,1): 9 + 1 + 1 + 9 = 20
- (1,2): 9 + 1 + 1 + 9 = 20
- (2,2): 20
```
X_cᵀX_c = [[20, 20], [20, 20]]
```
**S = (1/(4−1))·[[20, 20], [20, 20]] = [[20/3, 20/3], [20/3, 20/3]]**

**Observation:** S is **singular** (det = 0). The two features are perfectly correlated — indeed x₂ = x₁ + 2 exactly. The data lies on a **line**, so its intrinsic dimension is 1, and PCA will find exactly one nonzero eigenvalue.

---

### Example 14.2 — [Easy] Explained variance

A PCA yields eigenvalues λ = (12, 5, 2, 0.8, 0.2). How many components are needed for 90% of the variance?

**Solution.** Total = 12 + 5 + 2 + 0.8 + 0.2 = **20**.

| k | cumulative | ratio |
|---|---|---|
| 1 | 12 | 60.0% |
| 2 | 17 | 85.0% |
| 3 | 19 | **95.0%** ✓ |
| 4 | 19.8 | 99.0% |
| 5 | 20 | 100% |

**Answer: 3 components** (95% ≥ 90%; two components give only 85%).

*The gap between λ₃ = 2 and λ₄ = 0.8 is the natural "elbow", confirming 3 as the sensible cut.*

---

### Example 14.3 — [Medium] Full PCA on a small dataset

Perform PCA on
```
X = [[1, 2],
     [3, 3],
     [5, 4],
     [7, 7]]
```
Find the principal components, the explained variance, and the 1-D scores.

**Solution.**

**Means:** x̄₁ = 16/4 = 4; x̄₂ = 16/4 = 4.

**Centred:**
```
X_c = [[−3, −2],
       [−1, −1],
       [ 1,  0],
       [ 3,  3]]
```

**X_cᵀX_c:**
- (1,1): 9 + 1 + 1 + 9 = 20
- (1,2): 6 + 1 + 0 + 9 = 16
- (2,2): 4 + 1 + 0 + 9 = 14
```
X_cᵀX_c = [[20, 16], [16, 14]]
S = (1/3)[[20, 16], [16, 14]]
```

**Eigenvalues of [[20,16],[16,14]]:** p(λ) = λ² − 34λ + (280 − 256) = λ² − 34λ + 24.
λ = [34 ± √(1156 − 96)]/2 = [34 ± √1060]/2 = [34 ± 32.558]/2
**λ = 33.279 and 0.721** (for X_cᵀX_c); dividing by 3 gives **S-eigenvalues 11.093 and 0.240**.

**First principal component.** Solve ([[20,16],[16,14]] − 33.279I)v = 0:
[[−13.279, 16], [16, −19.279]]. From row 1: 13.279v₁ = 16v₂ → v₁/v₂ = 16/13.279 = 1.2049.
Take v = (1.2049, 1), normalize: ‖v‖ = √(1.4518 + 1) = √2.4518 = 1.5658.
**q₁ = (0.7695, 0.6386)**

**Second:** orthogonal to q₁ → **q₂ = (−0.6386, 0.7695)**

**Explained variance:** λ₁/(λ₁+λ₂) = 33.279/34 = **97.88%**

**1-D scores** Y = X_c q₁:
- row 1: (−3)(0.7695) + (−2)(0.6386) = −2.3085 − 1.2772 = **−3.586**
- row 2: (−1)(0.7695) + (−1)(0.6386) = **−1.408**
- row 3: (1)(0.7695) + 0 = **0.770**
- row 4: 3(0.7695) + 3(0.6386) = 3(1.4081) = **4.224**

**Check:** scores sum to −3.586 − 1.408 + 0.770 + 4.224 = 0.000 ✓ (must be zero after centring)
**Check variance:** Σy² = 12.86 + 1.98 + 0.59 + 17.84 = 33.27 ≈ λ₁ = 33.279 ✓

**Interpretation.** Nearly 98% of the structure is captured by a single direction — roughly "both features increase together". The data is essentially one-dimensional with a small amount of scatter.

---

### Example 14.4 — [Medium] Compression arithmetic

A 512×512 grayscale image is compressed by SVD to rank 40. Find the compression ratio and the storage saving. If the singular values satisfy Σ_{i=1}^{40}σᵢ² = 0.97Σ_{i}σᵢ², find the relative Frobenius error.

**Solution.**

**Original storage:** 512 × 512 = **262,144** numbers.

**Rank-40 storage:** k(m + n + 1) = 40(512 + 512 + 1) = 40 × 1025 = **41,000** numbers.

**Compression ratio:** 262144/41000 = **6.39×**
**Space saved:** 1 − 41000/262144 = **84.4%**

**Relative error:**
‖A − A₄₀‖_F/‖A‖_F = √(Σ_{i>40}σᵢ²/Σσᵢ²) = √(1 − 0.97) = √0.03 = **0.1732 → 17.3%**

**Comment.** Capturing 97% of the *energy* still leaves 17% relative error in the *norm*, because the error is a square root. This is why "97% variance explained" sounds better than it looks. Visually, however, 17% Frobenius error on a photograph is often barely noticeable, since the error is spread over fine detail rather than concentrated.

---

### Example 14.5 — [Hard] Collaborative filtering by matrix factorization

Four users rate three movies (— means unrated):
```
        M1   M2   M3
U1       5    3    —
U2       4    —    2
U3       —    1    1
U4       5    3    2
```
Using a rank-1 model r̂ᵤᵢ = pᵤqᵢ, estimate the factors by an ALS-style computation initialized at q = (1, 0.6, 0.4), and predict the missing entries.

**Solution.**

**Step 1 — Fix q, solve for each pᵤ by least squares over observed entries.**
For a rank-1 model with q fixed, the least squares solution for user u over their observed set Oᵤ is
> pᵤ = (Σ_{i∈Oᵤ} rᵤᵢqᵢ)/(Σ_{i∈Oᵤ} qᵢ²)

- **U1** (M1, M2): numerator = 5(1) + 3(0.6) = 6.8; denominator = 1 + 0.36 = 1.36 → **p₁ = 5.000**
- **U2** (M1, M3): 4(1) + 2(0.4) = 4.8; 1 + 0.16 = 1.16 → **p₂ = 4.138**
- **U3** (M2, M3): 1(0.6) + 1(0.4) = 1.0; 0.36 + 0.16 = 0.52 → **p₃ = 1.923**
- **U4** (all): 5(1) + 3(0.6) + 2(0.4) = 7.6; 1 + 0.36 + 0.16 = 1.52 → **p₄ = 5.000**

**Step 2 — Fix p, solve for each qᵢ.**
> qᵢ = (Σ_{u∈Oᵢ} rᵤᵢpᵤ)/(Σ_{u∈Oᵢ} pᵤ²)

- **M1** (U1, U2, U4): numerator = 5(5) + 4(4.138) + 5(5) = 25 + 16.552 + 25 = 66.552;
 denominator = 25 + 17.123 + 25 = 67.123 → **q₁ = 0.9915**
- **M2** (U1, U3, U4): 3(5) + 1(1.923) + 3(5) = 15 + 1.923 + 15 = 31.923;
 25 + 3.698 + 25 = 53.698 → **q₂ = 0.5945**
- **M3** (U2, U3, U4): 2(4.138) + 1(1.923) + 2(5) = 8.276 + 1.923 + 10 = 20.199;
 17.123 + 3.698 + 25 = 45.821 → **q₃ = 0.4408**

**Step 3 — Predictions.** r̂ᵤᵢ = pᵤqᵢ with p = (5.000, 4.138, 1.923, 5.000), q = (0.9915, 0.5945, 0.4408).

```
          M1      M2      M3
U1      4.96    2.97   [2.20]
U2      4.10   [2.46]   1.82
U3     [1.91]   1.14    0.85
U4      4.96    2.97    2.20
```
*(Bracketed entries are the predictions for the missing ratings.)*

**Predicted missing ratings:**
- **U1 on M3: 2.20**
- **U2 on M2: 2.46**
- **U3 on M1: 1.91**

**Fit quality on observed entries.** Residuals: U1-M1: 0.04; U1-M2: 0.03; U2-M1: −0.10; U2-M3: 0.18; U3-M2: −0.14; U3-M3: 0.15; U4-M1: 0.04; U4-M2: 0.03; U4-M3: −0.20.
SSE ≈ 0.0016 + 0.0009 + 0.01 + 0.0324 + 0.0196 + 0.0225 + 0.0016 + 0.0009 + 0.04 ≈ **0.130**
**RMSE = √(0.130/9) = √0.01444 ≈ 0.120** — an excellent fit.

**Interpretation.** The single latent factor behaves like "overall enthusiasm crossed with movie popularity": U1 and U4 are enthusiastic raters (p ≈ 5), U3 is a harsh rater (p ≈ 1.9); M1 is the most popular movie (q ≈ 0.99), M3 the least (q ≈ 0.44). The model correctly infers that harsh rater U3 would give M1 a low score (1.91) despite M1 being popular overall — **exactly the kind of personalization a global average could never produce**.

---

### Example 14.6 — [Hard] PCA versus SVD route

For the centred data
```
X_c = [[2, 0],
       [0, 1],
       [−2, 0],
       [0, −1]]
```
compute PCA both via the covariance matrix and via the SVD, and verify λᵢ = σᵢ²/(m−1).

**Solution.**

**Route 1 — covariance matrix.**
X_cᵀX_c:
- (1,1): 4 + 0 + 4 + 0 = 8
- (1,2): 0 + 0 + 0 + 0 = 0
- (2,2): 0 + 1 + 0 + 1 = 2
```
X_cᵀX_c = [[8, 0], [0, 2]]
S = (1/3)[[8, 0], [0, 2]] = [[8/3, 0], [0, 2/3]]
```
Already diagonal → **eigenvalues λ₁ = 8/3 ≈ 2.667, λ₂ = 2/3 ≈ 0.667**, with principal components **q₁ = (1, 0), q₂ = (0, 1)**.

**Explained variance:** λ₁/(λ₁+λ₂) = (8/3)/(10/3) = **80%**.

**Route 2 — SVD of X_c.**
We need the eigenvalues of X_cᵀX_c = [[8,0],[0,2]]: they are 8 and 2.
**σ₁ = √8 = 2√2 ≈ 2.828, σ₂ = √2 ≈ 1.414.**

Right singular vectors: **v₁ = (1,0), v₂ = (0,1)** ✓ same as q₁, q₂.

Left singular vectors:
X_cv₁ = (2, 0, −2, 0)ᵀ, norm = √8 = σ₁ ✓ → **u₁ = (1/√2)(1, 0, −1, 0)**
X_cv₂ = (0, 1, 0, −1)ᵀ, norm = √2 = σ₂ ✓ → **u₂ = (1/√2)(0, 1, 0, −1)**

**Verify λᵢ = σᵢ²/(m−1):**
- σ₁²/3 = 8/3 = λ₁ ✓
- σ₂²/3 = 2/3 = λ₂ ✓

**Scores.** Y = X_cV = X_c (since V = I here) = X_c itself. Also Y = UΣ:
UΣ = (1/√2)[[1,0],[0,1],[−1,0],[0,−1]]·diag(2√2, √2) = [[2, 0],[0,1],[−2,0],[0,−1]] ✓ matches X_c.

**Geometric picture.** The data forms a "plus sign": two points at distance 2 along the x-axis, two at distance 1 along the y-axis. PCA correctly identifies the x-axis as the direction of greatest spread, with 4× the variance of the y-direction (8 versus 2) ✓

---

### Example 14.7 — [Very Hard] Why PCA maximizes variance — full derivation

Prove that the first principal component q₁ is the unit vector maximizing the sample variance of the projected data, and that the k-th maximizes it subject to orthogonality with the first k−1. Then prove that PCA simultaneously **minimizes reconstruction error**.

**Solution.**

**Part A — maximum variance.**

Let w be a unit vector. The projections of the centred data onto w are the entries of X_cw. Their sample variance is

Var(X_cw) = (1/(m−1))‖X_cw‖² = (1/(m−1)) wᵀX_cᵀX_cw = **wᵀSw**

*(The mean of X_cw is (1/m)1ᵀX_cw = 0 since X_c is centred, so no mean-subtraction is needed.)*

By Theorem 11.5 (Rayleigh quotient for the symmetric matrix S):
> max_{‖w‖=1} wᵀSw = **λ₁**, attained at **w = q₁** ✓

For the k-th component, the nested version of the same theorem gives:
> max{wᵀSw : ‖w‖ = 1, w ⊥ q₁, ..., q_{k−1}} = **λ_k**, attained at **q_k** ✓ ∎

**Part B — minimum reconstruction error.**

Let W_k be any k-dimensional subspace, with orthonormal basis in the columns of an n×k matrix B (so BᵀB = I_k). Projecting each data row onto W_k and reconstructing gives X_cBBᵀ. The total squared reconstruction error is

E(B) = ‖X_c − X_cBBᵀ‖_F²

Expand, using ‖M‖_F² = tr(MᵀM):
E(B) = tr[(X_c − X_cBBᵀ)ᵀ(X_c − X_cBBᵀ)]
= tr[X_cᵀX_c] − 2tr[BBᵀX_cᵀX_c] + tr[BBᵀX_cᵀX_cBBᵀ]

Using BᵀB = I, the last term simplifies: tr[BBᵀX_cᵀX_cBBᵀ] = tr[BᵀX_cᵀX_cB] (cyclic property and BᵀB = I). Similarly the middle term is 2tr[BᵀX_cᵀX_cB]. So

> **E(B) = ‖X_c‖_F² − tr(BᵀX_cᵀX_cB)**

Since ‖X_c‖_F² is a constant, **minimizing E is the same as maximizing tr(BᵀX_cᵀX_cB)** — that is, maximizing the **retained variance**.

By the **Ky Fan / trace-maximization theorem** (the matrix generalization of the Rayleigh quotient), for BᵀB = I_k:
> max tr(BᵀMB) = λ₁ + λ₂ + ... + λ_k for symmetric M,
attained when the columns of B span the top-k eigenspace of M.

**Hence B = Q_k = [q₁ ... q_k] simultaneously:**
- maximizes retained variance (λ₁ + ... + λ_k), **and**
- minimizes reconstruction error, which equals **λ_{k+1} + ... + λₙ** (in X_cᵀX_c-scaled units) ✓ ∎

**The two views are the same theorem.** Total variance splits as

> **(total) = (variance you keep) + (variance you lose to reconstruction error)**

so maximizing one is identical to minimizing the other. This is once more the Pythagorean decomposition of Chapter 5 (y = ŷ + z with ŷ ⊥ z), applied to every data point at once.

**Connection to Eckart–Young.** In SVD language, X_cQ_kQ_kᵀ is exactly the rank-k truncation (X_c)_k. So Part B is a restatement of Theorem 13.4 in the Frobenius norm — **PCA is Eckart–Young applied to centred data** ✓

---

### Example 14.8 — [Very Hard] Condition number and gradient descent

For the quadratic loss f(x) = ½xᵀAx − bᵀx with A = [[10, 0], [0, 1]] and b = (0, 0)ᵀ, analyze gradient descent from x₀ = (1, 1)ᵀ. Compare with the standardized problem A' = I.

**Solution.**

**Set-up.** ∇f(x) = Ax − b = Ax. The minimum is at x* = A⁻¹b = **0**.

Gradient descent: x_{k+1} = x_k − α∇f(x_k) = x_k − αAx_k = **(I − αA)x_k**.

Since A is diagonal, each coordinate evolves independently:
> x₁^{(k)} = (1 − 10α)ᵏ · 1, x₂^{(k)} = (1 − α)ᵏ · 1

**Convergence requires** |1 − 10α| < 1 and |1 − α| < 1, i.e. **0 < α < 0.2**. (Exceeding α = 0.2 makes the first coordinate diverge — the "learning rate too high" failure.)

**Optimal step size.** Minimize max(|1 − 10α|, |1 − α|). The two are balanced when
10α − 1 = 1 − α → 11α = 2 → **α* = 2/11 ≈ 0.1818**

At α*, both factors have magnitude |1 − 10(2/11)| = |1 − 20/11| = 9/11 ≈ **0.818**.

**Convergence rate.** ‖x_k‖ ≈ (9/11)ᵏ‖x₀‖.

Note (κ−1)/(κ+1) with **κ = 10/1 = 10** gives 9/11 ✓ exactly matching the theory in §14.6.4.

**Iterations for 10⁻³ accuracy:** (0.818)ᵏ ≤ 10⁻³ → k ≥ ln(10⁻³)/ln(0.818) = (−6.908)/(−0.2007) = 34.4 → **k = 35 iterations**.

**Standardized problem A' = I (κ = 1).**
x_{k+1} = (1 − α)x_k. Choosing **α = 1** gives x₁ = 0 — **convergence in exactly one step** ✓
Rate factor: (κ−1)/(κ+1) = 0/2 = 0 ✓ consistent.

**Comparison table.**

| | κ | best rate factor | iterations to 10⁻³ |
|---|---|---|---|
| A = diag(10, 1) | 10 | 0.818 | 35 |
| A = diag(100, 1) | 100 | 0.980 | **342** |
| A = diag(10⁴, 1) | 10⁴ | 0.9998 | **~34,500** |
| A' = I | 1 | 0 | **1** |

**The lesson.** The iteration count scales roughly **linearly in κ**. A feature measured in metres alongside one measured in millimetres creates κ ≈ 10⁶ and makes plain gradient descent hopeless.

**Geometric picture.** The level sets of f are ellipses with axis ratio √κ. Gradient descent always steps **perpendicular to the level set**, which in a long narrow valley points mostly *across* the valley rather than *along* it — producing the characteristic zig-zag. Standardizing turns the ellipses into circles, where the gradient points straight at the minimum.

**Remedies in practice:** feature standardization, preconditioning (multiply by an approximate A⁻¹), momentum (reduces the dependence from κ to √κ), and adaptive methods like Adam (per-coordinate scaling that approximates a diagonal preconditioner).

---

## 14.8 Practice Numericals — Chapter 14

**[Easy]**

**P14.1** For X = [[1, 3], [3, 5], [5, 7]], find the mean vector and the centred matrix.

**P14.2** PCA gives eigenvalues (10, 6, 3, 1). What percentage of variance do the first two components explain?

**P14.3** A 256×256 image is compressed to rank 20. How many numbers are stored, and what is the compression ratio?

**P14.4** In a rank-2 recommender, user factors pᵤ = (1.5, −0.5) and item factors qᵢ = (2, 3). Predict the rating.

**P14.5** State in one sentence why data must be centred before PCA.

**[Medium]**

**P14.6** Perform PCA on X = [[0, 0], [2, 1], [4, 2], [6, 3]]. Find the principal components and explained variance.

**P14.7** Compute the cosine similarity between users with rating vectors (5, 3, 0, 1) and (4, 0, 0, 1).

**P14.8** A term–document matrix has singular values (9, 4, 2, 1, 0.5). How many latent topics capture 95% of the energy?

**P14.9** For X_c with X_cᵀX_c = [[6, 2], [2, 3]] and m = 5, find the covariance matrix, its eigenvalues, and the explained variance ratios.

**P14.10** Explain why standardizing features changes the results of PCA, and give a two-feature example where it matters.

**P14.11** Given a rating matrix with global mean μ = 3.5, user bias bᵤ = 0.4, item bias bᵢ = −0.7, and pᵤ·qᵢ = 0.3, predict the rating.

**[Hard]**

**P14.12** Perform full PCA on
```
X = [[4, 2], [2, 4], [6, 6], [8, 4]]
```
reporting the mean, covariance matrix, both principal components, explained variance, and the 1-D scores.

**P14.13** A 4×3 rating matrix has all entries observed:
```
R = [[5, 4, 1], [4, 3, 1], [1, 1, 5], [1, 2, 4]]
```
Compute RᵀR, find its eigenvalues, and determine how many latent factors are needed for 95% of the energy. Interpret.

**P14.14** Show that for a rank-1 recommender model r̂ᵤᵢ = pᵤqᵢ, the ALS update for pᵤ with q fixed is the ordinary least squares solution of a one-variable regression, and derive the formula.

**P14.15** Prove that the principal components are orthogonal and that the scores Y = X_cQ have diagonal covariance matrix. Interpret this as "decorrelating the data".

**P14.16** For a 2-feature dataset with covariance matrix S = [[4, 3], [3, 4]], find the principal components, the whitening transformation, and verify that the whitened data has identity covariance.

**P14.17** An image A of size m×n has singular values σᵢ = 100/i for i = 1,...,50 and 0 thereafter. Find the smallest k capturing 95% of the Frobenius energy. (Use Σ1/i² ≈ π²/6 for large ranges, or compute partial sums.)

**[Very Hard]**

**P14.18** Prove that PCA on the **correlation** matrix is equivalent to PCA on the covariance matrix of standardized data, and show by explicit example that the two give different principal directions on the *original* scale.

**P14.19** Derive the ridge regression solution ŵ = (XᵀX + λI)⁻¹Xᵀy using the SVD of X, express it as ŵ = Σᵢ [σᵢ/(σᵢ² + λ)](uᵢᵀy)vᵢ, and explain how λ controls the "shrinkage" of each singular direction. What happens as λ → 0 and λ → ∞?

**P14.20** Prove that the Gram matrix K with Kᵢⱼ = k(xᵢ, xⱼ) must be positive semidefinite for k to be a valid kernel, and verify this for the linear kernel k(x,y) = xᵀy and the polynomial kernel k(x,y) = (xᵀy + 1)².

**P14.21** **(LoRA — low-rank adaptation.)** A neural network weight matrix W is d×d with d = 4096. Fine-tuning replaces W with W + ΔW where ΔW = BA with B of size d×r and A of size r×d. For r = 8, compute the number of trainable parameters versus full fine-tuning, the reduction factor, and explain — using Eckart–Young — why a low-rank update is a reasonable modelling assumption.

---

## 14.9 Solutions to Chapter 14 Practice

**S14.1** Means: x̄₁ = (1+3+5)/3 = 3; x̄₂ = (3+5+7)/3 = 5. **x̄ = (3, 5).**
```
X_c = [[−2, −2],
       [ 0,  0],
       [ 2,  2]]
```

**S14.2** Total = 10 + 6 + 3 + 1 = 20. First two = 16. **16/20 = 80%.**

**S14.3** k(m+n+1) = 20(256 + 256 + 1) = 20 × 513 = **10,260 numbers.**
Original: 256² = 65,536. **Compression ratio = 65536/10260 ≈ 6.39×** (84.4% saved).

**S14.4** r̂ = pᵤ·qᵢ = 1.5(2) + (−0.5)(3) = 3 − 1.5 = **1.5**.

**S14.5** Without centring, the first "principal component" points from the origin toward the data's centroid rather than along the direction of greatest **spread**, so it measures the mean rather than the variance.

**S14.6** Means: x̄₁ = 12/4 = 3; x̄₂ = 6/4 = 1.5.
```
X_c = [[−3, −1.5],
       [−1, −0.5],
       [ 1,  0.5],
       [ 3,  1.5]]
```
X_cᵀX_c:
- (1,1): 9+1+1+9 = 20
- (1,2): 4.5 + 0.5 + 0.5 + 4.5 = 10
- (2,2): 2.25 + 0.25 + 0.25 + 2.25 = 5
```
X_cᵀX_c = [[20, 10], [10, 5]]
```
det = 100 − 100 = **0** → rank 1. Eigenvalues: tr = 25, det = 0 → **λ = 25 and 0**.
**Explained variance: 100% by the first component** — the data lies exactly on a line ✓ (indeed x₂ = x₁/2).

First PC: ([[20,10],[10,5]] − 25I)v = 0 → [[−5, 10],[10,−20]] → v₁ = 2v₂ → v = (2, 1).
**q₁ = (1/√5)(2, 1)**, q₂ = (1/√5)(−1, 2).

**S14.7** u = (5,3,0,1), v = (4,0,0,1).
u·v = 20 + 0 + 0 + 1 = 21.
‖u‖ = √(25+9+0+1) = √35 ≈ 5.916; ‖v‖ = √(16+0+0+1) = √17 ≈ 4.123.
**cos = 21/(5.916 × 4.123) = 21/24.39 = 0.861**
Strong similarity — the users agree on the items they both rated.

**S14.8** Energies: 81, 16, 4, 1, 0.25. Total = **102.25**.
| k | cumulative | ratio |
|---|---|---|
| 1 | 81 | 79.2% |
| 2 | 97 | 94.9% |
| 3 | 101 | **98.8%** ✓ |

Two topics give 94.9% — just short. **3 latent topics** are needed for ≥95%.

**S14.9** S = (1/(5−1))[[6,2],[2,3]] = **[[1.5, 0.5], [0.5, 0.75]]**.
Eigenvalues of [[6,2],[2,3]]: p(λ) = λ² − 9λ + (18 − 4) = λ² − 9λ + 14 = (λ−7)(λ−2). → **7 and 2**.
S-eigenvalues: **7/4 = 1.75 and 2/4 = 0.5**.
**Explained variance: 7/9 = 77.8% and 2/9 = 22.2%.**

**S14.10** PCA finds directions of maximum **variance**, and variance depends on units. A feature measured in large numbers dominates the covariance matrix regardless of its actual importance.

**Example.** Features: height in **millimetres** (values ~1700, variance ~10,000) and weight in **kilograms** (values ~70, variance ~100). The covariance matrix is dominated by the height entry, so q₁ points essentially along the height axis and the weight information is nearly discarded — even if weight is the more informative variable.

After standardizing (each feature to variance 1), both contribute equally and the principal direction reflects their genuine correlation rather than an accident of units. Changing height to **metres** would flip the answer entirely — a clear sign that unstandardized PCA is unit-dependent.

**S14.11** r̂ = μ + bᵤ + bᵢ + pᵤ·qᵢ = 3.5 + 0.4 − 0.7 + 0.3 = **3.5**.

**S14.12** Means: x̄₁ = (4+2+6+8)/4 = 5; x̄₂ = (2+4+6+4)/4 = 4.
```
X_c = [[−1, −2],
       [−3,  0],
       [ 1,  2],
       [ 3,  0]]
```
X_cᵀX_c:
- (1,1): 1 + 9 + 1 + 9 = 20
- (1,2): 2 + 0 + 2 + 0 = 4
- (2,2): 4 + 0 + 4 + 0 = 8
```
X_cᵀX_c = [[20, 4], [4, 8]]
S = (1/3)[[20, 4], [4, 8]]
```
**Eigenvalues of [[20,4],[4,8]]:** p(λ) = λ² − 28λ + (160 − 16) = λ² − 28λ + 144.
λ = [28 ± √(784 − 576)]/2 = [28 ± √208]/2 = [28 ± 14.422]/2
**λ = 21.211 and 6.789** → S-eigenvalues **7.070 and 2.263**.

**q₁:** ([[20,4],[4,8]] − 21.211I)v = 0 → [[−1.211, 4],[4, −13.211]].
From row 1: 1.211v₁ = 4v₂ → v₁ = 3.303v₂. Take v = (3.303, 1), ‖v‖ = √(10.91 + 1) = 3.451.
**q₁ = (0.9571, 0.2898)**
**q₂ = (−0.2898, 0.9571)**

**Explained variance:** 21.211/28 = **75.75%** and 6.789/28 = **24.25%**.

**1-D scores** Y = X_cq₁:
- (−1)(0.9571) + (−2)(0.2898) = −0.9571 − 0.5796 = **−1.537**
- (−3)(0.9571) + 0 = **−2.871**
- (1)(0.9571) + (2)(0.2898) = **1.537**
- (3)(0.9571) + 0 = **2.871**

**Check:** sum = 0 ✓. Σy² = 2.36 + 8.24 + 2.36 + 8.24 = 21.20 ≈ λ₁ = 21.211 ✓

**S14.13** R = [[5,4,1],[4,3,1],[1,1,5],[1,2,4]].

**RᵀR:**
- (1,1): 25 + 16 + 1 + 1 = 43
- (1,2): 20 + 12 + 1 + 2 = 35
- (1,3): 5 + 4 + 5 + 4 = 18
- (2,2): 16 + 9 + 1 + 4 = 30
- (2,3): 4 + 3 + 5 + 8 = 20
- (3,3): 1 + 1 + 25 + 16 = 43
```
RᵀR = [[43, 35, 18],
       [35, 30, 20],
       [18, 20, 43]]
```
**trace = 116** = ‖R‖_F² *(check: 25+16+1+16+9+1+1+1+25+1+4+16 = 116 ✓)*

**Eigenvalues.** Characteristic polynomial (computed): the dominant eigenvalue is near the row sums (~96, 85, 81), so λ₁ ≈ 85. Numerically the eigenvalues are approximately

**λ₁ ≈ 85.36, λ₂ ≈ 28.97, λ₃ ≈ 1.67**

*(Check: sum ≈ 116.0 ✓)*

**Energy fractions:**
| k | cumulative | ratio |
|---|---|---|
| 1 | 85.36 | 73.6% |
| 2 | 114.33 | **98.6%** ✓ |
| 3 | 116 | 100% |

**Two latent factors suffice** for ≥95%.

**Interpretation.** Singular values are √85.36 ≈ 9.24, √28.97 ≈ 5.38, √1.67 ≈ 1.29. The sharp drop after the second confirms rank ≈ 2. Looking at R, users 1–2 like items 1–2 and dislike item 3, while users 3–4 do the reverse — **two taste groups**, exactly the two latent factors. The third factor (1.4% of energy) is individual noise.

**S14.14** Fix q. For user u with observed set Oᵤ, the objective restricted to that user is

J(pᵤ) = Σ_{i∈Oᵤ} (rᵤᵢ − pᵤqᵢ)²

This is an ordinary least squares problem `Ax = b` with the single "feature column" A = (qᵢ)_{i∈Oᵤ}, unknown scalar x = pᵤ, and target b = (rᵤᵢ)_{i∈Oᵤ}.

**Normal equations** AᵀA pᵤ = Aᵀb give:

> **pᵤ = (Σ_{i∈Oᵤ} rᵤᵢqᵢ)/(Σ_{i∈Oᵤ} qᵢ²)** ✓

*Derivation by calculus:* dJ/dpᵤ = −2Σqᵢ(rᵤᵢ − pᵤqᵢ) = 0 → pᵤΣqᵢ² = Σrᵤᵢqᵢ ✓ same answer.

**With ridge regularization** λ‖pᵤ‖²:
> **pᵤ = (Σrᵤᵢqᵢ)/(Σqᵢ² + λ)**

This is why ALS is attractive: **each half-step is a convex least squares problem with a closed-form solution**, even though the joint problem in (P, Q) is non-convex. ∎

**S14.15**
**Orthogonality.** The principal components are eigenvectors of the **symmetric** matrix S. By Theorem 11.1 (and the Spectral Theorem for repeated eigenvalues), they can always be chosen **orthonormal** ✓

**Covariance of the scores.** Y = X_cQ. Since Y's columns have mean zero (X_c is centred and Q is a fixed linear map), the sample covariance of Y is

Cov(Y) = (1/(m−1))YᵀY = (1/(m−1))QᵀX_cᵀX_cQ = Qᵀ S Q

But S = QΛQᵀ, so
Qᵀ S Q = Qᵀ(QΛQᵀ)Q = (QᵀQ)Λ(QᵀQ) = **Λ** — diagonal ✓ ∎

**Interpretation — decorrelation.** The off-diagonal entries of a covariance matrix are covariances between features. Cov(Y) = Λ being diagonal means **every pair of principal components has zero covariance**: the new features are completely uncorrelated.

The original features may be tangled up with each other; PCA rotates the coordinate frame so that they become independent (in the second-moment sense). The diagonal entries λᵢ are the variances, sorted largest-first.

*(This is also why PCA is sometimes called the Karhunen–Loève transform, and why it is the ideal preprocessing step for methods that assume uncorrelated inputs.)*

**S14.16** S = [[4, 3], [3, 4]].
p(λ) = (4−λ)² − 9 = λ² − 8λ + 7 = (λ−7)(λ−1). **λ₁ = 7, λ₂ = 1.**

λ=7: [[−3,3],[3,−3]] → **q₁ = (1/√2)(1, 1)**
λ=1: **q₂ = (1/√2)(1, −1)**

**Whitening transformation.** We want a map W with Cov(Wᵀx) = I. Take

> **W = QΛ^{−1/2}** i.e. **z = Λ^{−1/2}Qᵀx**

Here Λ^{−1/2} = diag(1/√7, 1/√1) = diag(0.3780, 1).

```
W_whiten = Λ^{−1/2}Qᵀ = diag(1/√7, 1)·(1/√2)[[1, 1], [1, −1]]
         = [[1/√14,  1/√14],
            [1/√2,  −1/√2]]
```

**Verification.** The covariance of z = W_whiten x is
Cov(z) = W_whiten S W_whitenᵀ = Λ^{−1/2}Qᵀ(QΛQᵀ)QΛ^{−1/2} = Λ^{−1/2}ΛΛ^{−1/2} = **I** ✓ ∎

**Numerically:** W S Wᵀ, first entry = (1/14)[[1,1]]·[[4,3],[3,4]]·[[1],[1]] = (1/14)(1,1)·(7,7) = 14/14 = 1 ✓
Off-diagonal = (1/√28)(1,1)·[[4,3],[3,4]]·(1,−1)ᵀ = (1/√28)(1,1)·(1,−1) = 0 ✓

**Geometric meaning.** Whitening turns the elliptical data cloud into a spherical one of unit radius: it removes both the correlation (via the rotation Qᵀ) and the unequal scales (via Λ^{−1/2}). It sets κ = 1, which by §14.6.4 makes gradient descent converge optimally.

**S14.17** σᵢ = 100/i, so σᵢ² = 10000/i².

**Total energy:** Σ_{i=1}^{50} 10000/i² = 10000 · Σ_{i=1}^{50} 1/i².

Σ_{i=1}^{∞}1/i² = π²/6 ≈ 1.644934. The tail Σ_{i=51}^{∞}1/i² ≈ 1/50 = 0.02 (more precisely ≈ 0.0198).
So Σ_{i=1}^{50}1/i² ≈ 1.6449 − 0.0198 = **1.6251**.
**Total ≈ 16,251.**

**Target:** 95% of 16251 = **15,438**.

**Partial sums of 10000/i²:**
| i | 10000/i² | cumulative |
|---|---|---|
| 1 | 10000 | 10000 (61.5%) |
| 2 | 2500 | 12500 (76.9%) |
| 3 | 1111 | 13611 (83.8%) |
| 4 | 625 | 14236 (87.6%) |
| 5 | 400 | 14636 (90.1%) |
| 6 | 278 | 14914 (91.8%) |
| 7 | 204 | 15118 (93.0%) |
| 8 | 156 | 15274 (94.0%) |
| 9 | 123 | 15397 (94.7%) |
| 10 | 100 | **15497 (95.4%)** ✓ |

**Answer: k = 10.**

**Comment.** Ten components out of fifty — a 5× reduction in rank — capture 95% of the energy. The 1/i² decay is typical of natural images (and is exactly why they compress well). Note also how slowly the tail accumulates: going from 95% to 99% would require roughly k = 30, a much worse trade.

**S14.18**
**Equivalence.** Let Z be the standardized data: Z = X_c D⁻¹ where D = diag(s₁, ..., sₙ) holds the feature standard deviations.

The covariance matrix of Z is
Cov(Z) = (1/(m−1))ZᵀZ = (1/(m−1))D⁻¹X_cᵀX_cD⁻¹ = **D⁻¹ S D⁻¹**

The (i,j) entry is Sᵢⱼ/(sᵢsⱼ) = **the correlation coefficient rᵢⱼ**.

So **Cov(standardized data) = correlation matrix of the original data** ✓ ∎
Hence eigen-analysis of the correlation matrix = PCA on standardized data.

**Example showing they differ.** Take two features with
S = [[100, 9], [9, 1]]
(feature 1 has variance 100, feature 2 variance 1, covariance 9).

**Covariance PCA.** p(λ) = λ² − 101λ + (100 − 81) = λ² − 101λ + 19.
λ = [101 ± √(10201 − 76)]/2 = [101 ± 100.62]/2 → **λ₁ = 100.81, λ₂ = 0.19**.
First PC: (100 − 100.81)v₁ + 9v₂ = 0 → −0.81v₁ + 9v₂ = 0 → v₁ = 11.1v₂.
**q₁ ≈ (0.996, 0.0898)** — essentially the **first feature's axis**. Explained variance 99.8%.

**Correlation PCA.** Correlation matrix:
r₁₂ = 9/(10 × 1) = 0.9, so C = [[1, 0.9], [0.9, 1]].
Eigenvalues: 1 ± 0.9 → **λ₁ = 1.9, λ₂ = 0.1**.
**q₁ = (1/√2)(1, 1)** — the **45° diagonal**. Explained variance 95%.

**The two answers are completely different:** (0.996, 0.090) versus (0.707, 0.707).

**Why.** The covariance version is dominated by feature 1's huge variance and essentially reports "the data varies along feature 1". The correlation version, having removed the scale difference, reports the genuine finding: **the two features are 90% correlated and move together**.

**Which to use?** Correlation PCA (standardized) whenever features have different units or wildly different scales — which is almost always. Covariance PCA only when all features share a meaningful common unit (e.g. pixel intensities). ∎

**S14.19**
**Derivation via SVD.** Let X = UΣVᵀ (m×n, reduced form with r nonzero singular values). Then
XᵀX = VΣ²Vᵀ, and XᵀX + λI = V(Σ² + λI)Vᵀ + λ(projection onto Nul(X))…

Working with the full SVD (V is n×n orthogonal):
XᵀX + λI = V(Σᵀ Σ + λI)Vᵀ, where ΣᵀΣ = diag(σ₁², ..., σₙ²) (with zeros for i > r).

So
(XᵀX + λI)⁻¹ = V·diag(1/(σᵢ² + λ))·Vᵀ

And Xᵀy = VΣᵀUᵀy, whose i-th component in the V-basis is σᵢ(uᵢᵀy).

Therefore
> **ŵ = (XᵀX + λI)⁻¹Xᵀy = Σᵢ [σᵢ/(σᵢ² + λ)] (uᵢᵀy) vᵢ** ✓ ∎

**Shrinkage interpretation.** Compare with the ordinary least squares solution (λ = 0):
> ŵ_OLS = Σᵢ [1/σᵢ](uᵢᵀy)vᵢ

The ridge **filter factor** for direction i is
> **fᵢ = σᵢ²/(σᵢ² + λ)** ∈ (0, 1)

so that ŵ_ridge = Σᵢ fᵢ · [1/σᵢ](uᵢᵀy)vᵢ.

| Direction | Behaviour |
|---|---|
| **σᵢ² ≫ λ** (strong, well-determined) | fᵢ ≈ 1 — barely shrunk |
| **σᵢ² ≈ λ** | fᵢ ≈ 0.5 — halved |
| **σᵢ² ≪ λ** (weak, noisy) | fᵢ ≈ 0 — **suppressed** |

**Ridge selectively damps the directions that the data determines poorly** — exactly the directions where OLS's 1/σᵢ would blow up and amplify noise. This is why ridge is the standard cure for multicollinearity.

**Limits.**
- **λ → 0⁺:** fᵢ → 1 for all σᵢ > 0, so ŵ → Σ_{σᵢ>0}(1/σᵢ)(uᵢᵀy)vᵢ = **X⁺y**, the minimum-norm least squares solution (Theorem 13.5) — *not* the unstable "1/0" blow-up, because directions with σᵢ = 0 contribute 0/(0+λ) = 0 throughout ✓
- **λ → ∞:** every fᵢ → 0, so **ŵ → 0**. Maximum regularization = predict the (centred) mean and nothing else.

**The bias–variance trade-off** lives in this formula: increasing λ increases bias (coefficients shrink away from the truth) but decreases variance (noise in the small-σ directions is suppressed). Cross-validation picks the λ balancing the two.

**S14.20**
**Necessity of PSD.** Suppose k is a valid kernel, meaning there is a feature map φ with
> k(x, y) = ⟨φ(x), φ(y)⟩

Let K be the Gram matrix, Kᵢⱼ = k(xᵢ, xⱼ) = ⟨φ(xᵢ), φ(xⱼ)⟩.

For any vector c ∈ ℝⁿ:
cᵀKc = Σᵢ Σⱼ cᵢcⱼ⟨φ(xᵢ), φ(xⱼ)⟩ = ⟨Σᵢcᵢφ(xᵢ), Σⱼcⱼφ(xⱼ)⟩ = **‖Σᵢcᵢφ(xᵢ)‖² ≥ 0** ✓

So **K is positive semidefinite** ✓ (It is also symmetric, since inner products are.) ∎

*(The converse — Mercer's theorem — says any symmetric PSD kernel arises from some feature map, possibly infinite-dimensional.)*

**Linear kernel k(x,y) = xᵀy.**
Feature map: φ(x) = x (the identity). Then K = XXᵀ where X has the xᵢ as rows.
By S11.10, **XXᵀ is positive semidefinite** ✓
Directly: cᵀKc = cᵀXXᵀc = ‖Xᵀc‖² ≥ 0 ✓

**Polynomial kernel k(x,y) = (xᵀy + 1)².**
Expand for x, y ∈ ℝ²:
(x₁y₁ + x₂y₂ + 1)² = x₁²y₁² + x₂²y₂² + 1 + 2x₁y₁x₂y₂ + 2x₁y₁ + 2x₂y₂

This is ⟨φ(x), φ(y)⟩ with the explicit feature map
> **φ(x) = (x₁², x₂², √2 x₁x₂, √2 x₁, √2 x₂, 1)** ∈ ℝ⁶

*Verify:* ⟨φ(x),φ(y)⟩ = x₁²y₁² + x₂²y₂² + 2x₁x₂y₁y₂ + 2x₁y₁ + 2x₂y₂ + 1 ✓ matches.

Since an explicit feature map exists, the kernel is valid and **every Gram matrix it produces is PSD** ✓ ∎

*(The point of the "kernel trick": computing k(x,y) = (xᵀy+1)² costs O(d) operations, while explicitly forming φ(x) in the O(d²)-dimensional space and taking an inner product costs O(d²). The kernel gives the same answer at a fraction of the cost — and works even when φ is infinite-dimensional, as for the Gaussian kernel.)*

**S14.21**
**Parameter counts.** d = 4096, r = 8.

**Full fine-tuning:** all of W is trainable:
> d² = 4096² = **16,777,216 parameters**

**LoRA:** only B (d×r) and A (r×d) are trainable:
> 2dr = 2 × 4096 × 8 = **65,536 parameters**

**Reduction factor:** 16,777,216/65,536 = **256×**
Equivalently, LoRA trains **0.39%** of the parameters.

*(General formula: the reduction factor is d²/(2dr) = d/(2r). Here 4096/16 = 256 ✓)*

**Why a low-rank update is reasonable — the Eckart–Young argument.**

Fine-tuning asks for an update ΔW that adapts a pretrained model to a narrower task. Two observations justify restricting ΔW to low rank:

**1. The best rank-r approximation is provably optimal.** By Eckart–Young (Theorem 13.4), if the "true" optimal update ΔW* has singular values σ₁ ≥ σ₂ ≥ ..., then the best achievable rank-r approximation has error

> ‖ΔW* − (ΔW*)_r‖_F = √(σ_{r+1}² + ... + σ_d²)

So **the quality loss is governed entirely by the tail of ΔW*'s singular value spectrum.** If those tail values are small, a rank-r update loses almost nothing.

**2. Empirically, that spectrum decays fast.** Adaptation to a specific task is a *small, structured* change to an already-capable model — it does not require rewriting the weight matrix in all 4096 directions. The measured **intrinsic rank** of fine-tuning updates is typically in the range 1–64, far below d. So σ_{r+1} onwards are tiny, and by point 1 the approximation error is negligible.

**Additional practical advantages:**
- **Memory:** optimizer state (Adam stores 2 extra copies per parameter) shrinks by the same 256×.
- **Storage:** a task-specific adapter is 65K parameters (~0.25 MB) rather than 16.8M (~64 MB), so hundreds of task adapters can be stored and hot-swapped against one frozen base model.
- **No inference cost:** at deployment, compute W + BA **once** and fold it into W. The forward pass is then identical in speed to the original.
- **Initialization:** set B = 0 and A random, so ΔW = BA = 0 at the start — training begins exactly at the pretrained model, guaranteeing no initial degradation.

**The whole method is Chapter 13's rank-r truncation, applied to a weight update instead of an image** ✓

---
# PART III — EXAMINATION PRACTICE

---

# Chapter 15 — Mixed Problem Sets by Difficulty

These sets deliberately **do not tell you which chapter a problem comes from**. In a real exam, half the work is recognizing which tool applies. Work through each set in order; the solutions follow each set.

---

## 15.1 Set A — [Easy] Twenty Warm-Ups

**A1.** Solve `3x + 2y = 7`, `x − y = 1`.

**A2.** Find the inverse of [[2, 5], [1, 3]].

**A3.** Compute det [[1, 2, 3], [0, 4, 5], [0, 0, 6]].

**A4.** Find the rank of [[1, 2, 3], [2, 4, 6]].

**A5.** Are (1, 2) and (3, 6) linearly independent?

**A6.** Find ‖(2, −3, 6)‖ and normalize it.

**A7.** Find the eigenvalues of [[5, 2], [0, 3]].

**A8.** Is W = {(x, y) : y = 2x} a subspace of ℝ²?

**A9.** Compute the projection of (3, 4) onto (1, 0).

**A10.** If det A = 3 for a 3×3 matrix, find det(2A).

**A11.** Find the singular values of [[6, 0], [0, 8]].

**A12.** Is T(x, y) = (x + y, 2x) linear? Give its standard matrix.

**A13.** State the dimension of the space of 4×4 symmetric matrices.

**A14.** Find a basis for Nul([[1, 1, 1]]).

**A15.** Verify that (1, 1) is an eigenvector of [[3, 1], [1, 3]] and find its eigenvalue.

**A16.** Classify the quadratic form Q = 2x² + 3y².

**A17.** Find the standard matrix of the reflection in the y-axis.

**A18.** For A = [[1, 2], [3, 4]], compute tr(A) and verify it equals the sum of eigenvalues.

**A19.** Is [[1, 2], [2, 4]] invertible?

**A20.** Find the angle between (1, 0) and (1, 1).

---

### Solutions to Set A

**A1.** x = y + 1 → 3(y+1) + 2y = 7 → 5y = 4 → y = 4/5, x = 9/5. **(9/5, 4/5).**

**A2.** det = 6 − 5 = 1. **A⁻¹ = [[3, −5], [−1, 2]].**

**A3.** Upper triangular → 1 × 4 × 6 = **24.**

**A4.** Row 2 = 2 × Row 1 → **rank 1.**

**A5.** (3,6) = 3(1,2) → **dependent.**

**A6.** ‖·‖ = √(4+9+36) = **7**. Unit vector **(2/7, −3/7, 6/7).**

**A7.** Triangular → **5 and 3.**

**A8.** Contains (0,0) ✓; closed under addition and scaling (it's a line through the origin) ✓ **Yes, a subspace of dimension 1.**

**A9.** ((3,4)·(1,0)/1)(1,0) = **(3, 0).**

**A10.** det(2A) = 2³(3) = **24.**

**A11.** Diagonal with positive entries → singular values are the absolute diagonal entries, sorted: **8 and 6.**

**A12.** Linear ✓. T(e₁) = (1, 2), T(e₂) = (1, 0). **A = [[1, 1], [2, 0]].**

**A13.** n(n+1)/2 = 4(5)/2 = **10.**

**A14.** x₁ = −x₂ − x₃. **Basis {(−1, 1, 0), (−1, 0, 1)}**, dimension 2.

**A15.** A(1,1)ᵀ = (3+1, 1+3) = (4, 4) = 4(1,1) ✓ **Eigenvalue 4.**

**A16.** A = diag(2, 3), both eigenvalues positive → **positive definite.**

**A17.** **[[−1, 0], [0, 1]].**

**A18.** tr = 1 + 4 = **5.** p(λ) = λ² − 5λ − 2, sum of roots = 5 ✓

**A19.** det = 4 − 6... careful: det = 1(4) − 2(2) = 0. **Not invertible.**

**A20.** cos θ = 1/(1·√2) = 1/√2 → θ = **45°.**

---

## 15.2 Set B — [Medium] Eighteen Standard Exam Questions

**B1.** Solve and express in parametric vector form:
`x₁ + 2x₂ − x₃ + 3x₄ = 4`, `2x₁ + 4x₂ − x₃ + 8x₄ = 11`.

**B2.** Find a basis for Col(A) and Nul(A) for A = [[1, 2, 1, 3], [2, 4, 3, 7], [1, 2, 2, 4]], and verify rank–nullity.

**B3.** Apply Gram–Schmidt to {(1, 1, 0), (1, 0, 1)} and normalize.

**B4.** Fit a least squares line to (1, 2), (2, 3), (3, 5), (4, 6) and compute R².

**B5.** Compute det [[2, −1, 3], [1, 4, −2], [3, 2, 1]] by cofactor expansion.

**B6.** Diagonalize A = [[4, 1], [2, 3]] and compute A³.

**B7.** Orthogonally diagonalize A = [[2, 2], [2, 5]].

**B8.** Find the SVD of A = [[1, 0], [1, 1]].

**B9.** Determine whether A = [[1, 1, 0], [0, 1, 0], [0, 0, 2]] is diagonalizable. State AM and GM for each eigenvalue.

**B10.** Find the LU factorization of A = [[2, 1], [6, 5]] and solve `Ax = (3, 13)ᵀ`.

**B11.** Let T : ℝ³ → ℝ² have standard matrix [[1, 0, 2], [0, 1, −1]]. Find ker(T) and range(T). Is T onto?

**B12.** Classify Q = 3x₁² + 2x₁x₂ + 3x₂² and find its principal axes.

**B13.** Find the steady state of the stochastic matrix [[0.8, 0.3], [0.2, 0.7]].

**B14.** Find the projection matrix onto the line spanned by (3, 4) and verify P² = P.

**B15.** For which k is {(1, 2, 3), (2, 5, 7), (1, 3, k)} a basis of ℝ³?

**B16.** Perform PCA on X = [[1, 1], [2, 3], [3, 5]] and give the first principal component with its explained variance.

**B17.** Find A⁺ for A = [[1, 1], [1, 1], [1, 1]] and solve the least squares problem for b = (3, 3, 6)ᵀ.

**B18.** Verify Cayley–Hamilton for A = [[0, 1], [−2, −3]] and use it to find A⁻¹.

---

### Solutions to Set B

**B1.** Augmented:
```
[[1, 2, −1, 3 |  4],
 [2, 4, −1, 8 | 11]]
```
`R₂ − 2R₁` → (0, 0, 1, 2 | 3). Then `R₁ + R₂` → (1, 2, 0, 5 | 7).
```
RREF = [[1, 2, 0, 5 | 7],
        [0, 0, 1, 2 | 3]]
```
Free: x₂ = s, x₄ = t. x₁ = 7 − 2s − 5t, x₃ = 3 − 2t.
**x = (7, 0, 3, 0) + s(−2, 1, 0, 0) + t(−5, 0, −2, 1).**

**B2.** `R₂ − 2R₁`, `R₃ − R₁`:
```
[[1, 2, 1, 3],
 [0, 0, 1, 1],
 [0, 0, 1, 1]]
```
`R₃ − R₂` → zero. `R₁ − R₂` → (1, 2, 0, 2).
Pivots: columns 1, 3. **rank = 2.**
**Col(A) basis (original columns 1, 3): {(1, 2, 1)ᵀ, (1, 3, 2)ᵀ}**
**Nul(A):** free x₂ = s, x₄ = t. x₁ = −2s − 2t, x₃ = −t.
**Basis: {(−2, 1, 0, 0), (−2, 0, −1, 1)}**, nullity 2.
**Check: 2 + 2 = 4 ✓**

**B3.** v₁ = (1,1,0), v₁·v₁ = 2.
x₂·v₁ = 1. v₂ = (1,0,1) − (1/2)(1,1,0) = (1/2, −1/2, 1) → scale ×2: **(1, −1, 2)**.
*Check: (1,1,0)·(1,−1,2) = 0 ✓*
Norms: √2 and √6.
**q₁ = (1/√2)(1, 1, 0), q₂ = (1/√6)(1, −1, 2).**

**B4.** m = 4, Σx = 10, Σy = 16, Σxy = 2 + 6 + 15 + 24 = 47, Σx² = 30.
β₁ = (4(47) − 10(16))/(4(30) − 100) = (188 − 160)/20 = **1.4**
β₀ = (16 − 14)/4 = **0.5**
**y = 0.5 + 1.4x**
Fitted: 1.9, 3.3, 4.7, 6.1. Residuals: 0.1, −0.3, 0.3, −0.1. SSE = 0.20.
ȳ = 4. SST = 4 + 1 + 1 + 4 = 10. **R² = 1 − 0.2/10 = 0.98.**

**B5.** Expand along row 1:
= 2·det[[4,−2],[2,1]] − (−1)·det[[1,−2],[3,1]] + 3·det[[1,4],[3,2]]
= 2(4 + 4) + 1(1 + 6) + 3(2 − 12)
= 16 + 7 − 30 = **−7**

**B6.** p(λ) = λ² − 7λ + (12 − 2) = λ² − 7λ + 10 = (λ−5)(λ−2). **λ = 5, 2.**
λ=5: [[−1,1],[2,−2]] → **(1, 1)**
λ=2: [[2,1],[2,1]] → **(1, −2)**
P = [[1, 1], [1, −2]], D = diag(5, 2), det P = −3, P⁻¹ = (1/−3)[[−2,−1],[−1,1]] = (1/3)[[2, 1],[1, −1]].
A³ = P diag(125, 8) P⁻¹.
P·diag(125,8) = [[125, 8], [125, −16]].
Times (1/3)[[2,1],[1,−1]]:
- (1,1): (250 + 8)/3 = **86**
- (1,2): (125 − 8)/3 = **39**
- (2,1): (250 − 16)/3 = **78**
- (2,2): (125 + 16)/3 = **47**
**A³ = [[86, 39], [78, 47]]**
*Check trace: 86 + 47 = 133 = 125 + 8 ✓*

**B7.** p(λ) = λ² − 7λ + (10 − 4) = λ² − 7λ + 6 = (λ−6)(λ−1). **λ = 6, 1.**
λ=6: [[−4, 2],[2,−1]] → 2v₁ = v₂ → **(1, 2)**
λ=1: [[1,2],[2,4]] → v₁ = −2v₂ → **(2, −1)**
Orthogonal ✓ Normalize by √5.
**Q = (1/√5)[[1, 2], [2, −1]], D = diag(6, 1).**

**B8.** AᵀA = [[1,1],[0,1]]·[[1,0],[1,1]] = [[2, 1], [1, 1]].
p(λ) = λ² − 3λ + 1 → λ = (3 ± √5)/2. **λ₁ = 2.618, λ₂ = 0.382.**
**σ₁ = 1.618, σ₂ = 0.618** (these are φ and 1/φ, the golden ratio!)
λ₁: [[2−2.618, 1],[1, 1−2.618]] = [[−0.618, 1],[1,−1.618]] → v₁ ∝ (1, 0.618), normalize: ‖·‖ = 1.176.
**v₁ = (0.851, 0.526)**
**v₂ = (−0.526, 0.851)**
Av₁ = (0.851, 0.851+0.526) = (0.851, 1.377). ‖·‖ = 1.618 ✓
**u₁ = (0.526, 0.851)**
Av₂ = (−0.526, −0.526+0.851) = (−0.526, 0.325). ‖·‖ = 0.618 ✓
**u₂ = (−0.851, 0.526)**
```
U ≈ [[0.526, −0.851], [0.851, 0.526]], Σ = diag(1.618, 0.618), V ≈ [[0.851, −0.526],[0.526, 0.851]]
```
*Check: σ₁σ₂ = 1 = |det A| ✓; σ₁² + σ₂² = 2.618 + 0.382 = 3 = ‖A‖_F² ✓*

**B9.** Block structure. Eigenvalues: **λ = 1 (AM 2), λ = 2 (AM 1).**
A − I = [[0,1,0],[0,0,0],[0,0,1]] → rank 2 → **GM(1) = 1 < 2.**
A − 2I = [[−1,1,0],[0,−1,0],[0,0,0]] → rank 2 → **GM(2) = 1 = AM ✓**
**Not diagonalizable.**

**B10.** `R₂ − 3R₁` (multiplier 3): U = [[2, 1], [0, 2]], **L = [[1, 0], [3, 1]]**.
Ly = (3, 13): y₁ = 3; 9 + y₂ = 13 → y₂ = 4.
Ux = y: 2x₂ = 4 → x₂ = 2; 2x₁ + 2 = 3 → x₁ = 1/2.
**x = (1/2, 2)ᵀ**

**B11.** Rank = 2 (pivots in columns 1, 2). **Onto ℝ²? Yes** (rank = 2 = dim ℝ²).
**range(T) = ℝ².**
**ker(T):** x₁ = −2x₃, x₂ = x₃. **Basis {(−2, 1, 1)}**, nullity 1.
*Check: 2 + 1 = 3 ✓*

**B12.** A = [[3, 1], [1, 3]]. p(λ) = λ² − 6λ + 8 = (λ−4)(λ−2). **λ = 4, 2** — both positive → **positive definite.**
**Principal axes:** λ=4 → (1, 1)/√2; λ=2 → (1, −1)/√2.
In principal coordinates: Q = 4y₁² + 2y₂².

**B13.** (P − I)q = 0: [[−0.2, 0.3], [0.2, −0.3]] → 0.2q₁ = 0.3q₂ → q₁ = 1.5q₂.
Normalize: 1.5q₂ + q₂ = 1 → q₂ = 0.4, q₁ = 0.6.
**q = (0.6, 0.4)**
*Check: 0.8(0.6) + 0.3(0.4) = 0.48 + 0.12 = 0.6 ✓*

**B14.** u = (3,4), u·u = 25.
**P = uuᵀ/25 = (1/25)[[9, 12], [12, 16]]**
P² = uuᵀuuᵀ/625 = u(25)uᵀ/625 = uuᵀ/25 = **P** ✓
*trace P = (9+16)/25 = 1 = rank ✓*

**B15.** Compute the determinant of the matrix with these as rows:
```
| 1  2  3 |
| 2  5  7 |
| 1  3  k |
```
`R₂ − 2R₁`, `R₃ − R₁`:
```
| 1  2    3   |
| 0  1    1   |
| 0  1  k−3   |
```
`R₃ − R₂` → (0, 0, k−4). det = **k − 4**.
**Basis ⟺ det ≠ 0 ⟺ k ≠ 4.**

**B16.** Means: x̄₁ = 2, x̄₂ = 3.
```
X_c = [[−1, −2], [0, 0], [1, 2]]
```
X_cᵀX_c = [[1+0+1, 2+0+2], [2+0+2, 4+0+4]] = [[2, 4], [4, 8]].
det = 0 → eigenvalues **10 and 0**.
**First PC:** ([[2,4],[4,8]] − 10I)v = 0 → [[−8,4],[4,−2]] → 2v₁ = v₂ → **q₁ = (1/√5)(1, 2)**.
**Explained variance: 100%** — the data lies exactly on the line x₂ = 2x₁ − 1.

**B17.** A is 3×2 with both columns equal to (1,1,1)ᵀ → **rank 1.**
AᵀA = [[3, 3], [3, 3]]. Eigenvalues 6, 0 → **σ₁ = √6.**
v₁ = (1/√2)(1, 1). Av₁ = (√2, √2, √2), ‖·‖ = √6 ✓ → **u₁ = (1/√3)(1,1,1).**
A⁺ = (1/√6)v₁u₁ᵀ = (1/√6)(1/√2)(1,1)ᵀ(1/√3)(1,1,1) = (1/6)[[1,1,1],[1,1,1]].
**A⁺ = (1/6)[[1, 1, 1], [1, 1, 1]]**
x̂ = A⁺(3,3,6)ᵀ = (1/6)(12, 12) = **(2, 2)ᵀ**
*Check: Ax̂ = (4, 4, 4); projection of (3,3,6) onto span{(1,1,1)} = (12/3)(1,1,1) = (4,4,4) ✓*
*Minimum norm: x̂ ⊥ Nul(A) = span{(1,−1)}: (2,2)·(1,−1) = 0 ✓*

**B18.** tr A = −3, det A = 0(−3) − 1(−2) = 2. **p(λ) = λ² + 3λ + 2.**
A² = [[0,1],[−2,−3]]² = [[−2, −3], [6, 7]].
A² + 3A + 2I = [[−2+0+2, −3+3+0], [6−6+0, 7−9+2]] = [[0,0],[0,0]] ✓
From A² + 3A = −2I: A(A + 3I) = −2I → **A⁻¹ = −(1/2)(A + 3I) = −(1/2)[[3, 1],[−2, 0]] = [[−1.5, −0.5], [1, 0]]**
*Check: [[0,1],[−2,−3]]·[[−1.5,−0.5],[1,0]] = [[1, 0], [3−3, 1+0]] = [[1,0],[0,1]] ✓*

---

## 15.3 Set C — [Hard] Fifteen Multi-Step Problems

**C1.** For the matrix A = [[1, 2, 0, 1], [2, 4, 1, 4], [3, 6, 2, 7], [1, 2, 1, 3]], find rank, a basis for each of the four fundamental subspaces, and verify the orthogonality relations.

**C2.** Determine all values of a and b for which the system
`x + y + z = 1`, `x + 2y + 4z = b`, `x + 4y + az = b²`
has (i) no solution, (ii) unique solution, (iii) infinitely many.

**C3.** Let A = [[2, −1, 0], [−1, 2, −1], [0, −1, 2]]. Show A is positive definite, find its Cholesky factorization, and compute its eigenvalues exactly.

**C4.** Find the least squares quadratic fit to (−2, 3), (−1, 1), (0, 0), (1, 1), (2, 4) and compute SSE and R².

**C5.** Let T : P₂ → P₂ be T(p)(t) = p(2t − 1). Find [T]_B for B = {1, t, t²}, determine whether T is invertible, and find its eigenvalues.

**C6.** Compute the SVD of A = [[1, 1, 0], [0, 1, 1]] and use it to find the pseudoinverse and the minimum-norm solution of `Ax = (2, 3)ᵀ`.

**C7.** Let A be 4×4 with characteristic polynomial (λ−2)³(λ−5). Given rank(A − 2I) = 2, determine whether A is diagonalizable, find all eigenvalue multiplicities, and state the Jordan structure.

**C8.** Find the matrix of the linear transformation on ℝ² that projects onto the line y = 2x, then verify it is symmetric, idempotent, and has trace 1.

**C9.** Prove that if A is m×n with rank r, then A can be written as A = BC with B of size m×r and C of size r×n, both of full rank. Then do it explicitly for A = [[1, 2, 3], [2, 4, 6], [1, 1, 1]].

**C10.** The 3×3 matrix A satisfies A³ = 4A. Find all possible eigenvalues, state whether A must be diagonalizable, and find all possible values of det A.

**C11.** Solve the system of differential equations x′ = Ax with A = [[1, 1], [4, 1]] and x(0) = (2, 0)ᵀ. Describe the long-run behaviour.

**C12.** Given the data matrix X = [[2, 1], [4, 3], [6, 4], [8, 8]], perform PCA: find the covariance matrix, both principal components, the explained variance ratios, and the 1-D reconstruction error.

**C13.** Find all 2×2 real matrices A with A² = [[1, 0], [0, 4]].

**C14.** Let A = [[3, 1, 1], [1, 3, 1], [1, 1, 3]]. Find all eigenvalues and eigenvectors using the structure A = 2I + J, orthogonally diagonalize A, and compute A^{10}.

**C15.** A Markov chain on 3 states has transition matrix
P = [[0.5, 0.25, 0.25], [0.25, 0.5, 0.25], [0.25, 0.25, 0.5]].
Find the eigenvalues, the steady state, and the rate of convergence.

---

### Solutions to Set C

**C1.** Row reduce A:
`R₂ − 2R₁`, `R₃ − 3R₁`, `R₄ − R₁`:
```
[[1, 2, 0, 1],
 [0, 0, 1, 2],
 [0, 0, 2, 4],
 [0, 0, 1, 2]]
```
`R₃ − 2R₂`, `R₄ − R₂` → two zero rows. `R₁ − 0·R₂` (already 0 in column 3).
```
RREF = [[1, 2, 0, 1],
        [0, 0, 1, 2],
        [0, 0, 0, 0],
        [0, 0, 0, 0]]
```
**rank = 2.** Pivots: columns 1, 3.

**Col(A)** (original columns 1, 3): **{(1, 2, 3, 1)ᵀ, (0, 1, 2, 1)ᵀ}**, dim 2.
**Row(A)** (nonzero RREF rows): **{(1, 2, 0, 1), (0, 0, 1, 2)}**, dim 2.
**Nul(A):** free x₂ = s, x₄ = t. x₁ = −2s − t, x₃ = −2t.
**Basis: {(−2, 1, 0, 0), (−1, 0, −2, 1)}**, dim 2.
**Nul(Aᵀ):** solve Aᵀy = 0, i.e. y ⊥ every column of A. Columns are c₁ = (1,2,3,1), c₃ = (0,1,2,1) (and c₂ = 2c₁, c₄ = c₁ + 2c₃).
So need y·c₁ = 0 and y·c₃ = 0:
y₁ + 2y₂ + 3y₃ + y₄ = 0 and y₂ + 2y₃ + y₄ = 0.
From the second: y₂ = −2y₃ − y₄. Substituting: y₁ − 4y₃ − 2y₄ + 3y₃ + y₄ = 0 → y₁ = y₃ + y₄.
Free: y₃ = s, y₄ = t. **Basis: {(1, −2, 1, 0), (1, −1, 0, 1)}**, dim 2 ✓ (m − r = 4 − 2 = 2)

**Verify orthogonality.**
Row(A) ⊥ Nul(A): (1,2,0,1)·(−2,1,0,0) = −2+2 = 0 ✓; (1,2,0,1)·(−1,0,−2,1) = −1+0+0+1 = 0 ✓;
(0,0,1,2)·(−2,1,0,0) = 0 ✓; (0,0,1,2)·(−1,0,−2,1) = −2+2 = 0 ✓
Col(A) ⊥ Nul(Aᵀ): (1,2,3,1)·(1,−2,1,0) = 1−4+3 = 0 ✓; (0,1,2,1)·(1,−1,0,1) = −1+0+1 = 0 ✓
**Dimension checks:** 2 + 2 = 4 = n ✓ and 2 + 2 = 4 = m ✓

**C2.** Augmented:
```
[[1, 1, 1 | 1  ],
 [1, 2, 4 | b  ],
 [1, 4, a | b² ]]
```
`R₂ − R₁`, `R₃ − R₁`:
```
[[1, 1,   1  | 1    ],
 [0, 1,   3  | b−1  ],
 [0, 3, a−1  | b²−1 ]]
```
`R₃ − 3R₂`:
```
[[1, 1,  1   | 1                ],
 [0, 1,  3   | b−1              ],
 [0, 0, a−10 | b²−1−3(b−1)      ]]
```
Simplify the last RHS: b² − 1 − 3b + 3 = **b² − 3b + 2 = (b−1)(b−2)**.

Last row: **(a − 10)z = (b−1)(b−2)**

- **(ii) Unique solution:** a ≠ 10 (any b).
- **(i) No solution:** a = 10 and (b−1)(b−2) ≠ 0, i.e. **a = 10, b ∉ {1, 2}**.
- **(iii) Infinitely many:** a = 10 and (b−1)(b−2) = 0, i.e. **a = 10 and b = 1 or b = 2**.

**C3.** **Positive definiteness (Sylvester).**
Δ₁ = 2 > 0 ✓
Δ₂ = 4 − 1 = 3 > 0 ✓
Δ₃ = 2(4−1) − (−1)(−2 − 0) + 0 = 6 − 2 = **4 > 0** ✓ **Positive definite.**

**Cholesky.**
- l₁₁ = √2
- l₂₁ = −1/√2
- l₂₂ = √(2 − 1/2) = √(3/2)
- l₃₁ = 0/√2 = 0
- l₃₂ = (−1 − 0)/√(3/2) = −1/√(3/2) = −√(2/3)
- l₃₃ = √(2 − 0 − 2/3) = √(4/3)
```
L = [[ √2,      0,        0     ],
     [−1/√2,  √(3/2),     0     ],
     [ 0,    −√(2/3),   √(4/3)  ]]
```
*Check det: (det L)² = 2 · (3/2) · (4/3) = 4 = Δ₃ ✓*

**Eigenvalues.** This is the tridiagonal Toeplitz matrix with a = 2, b = c = −1, n = 3. By the formula λ_k = a + 2√(bc)cos(kπ/(n+1)):
λ_k = 2 + 2cos(kπ/4), k = 1, 2, 3.
- k=1: 2 + 2(√2/2) = **2 + √2 ≈ 3.414**
- k=2: 2 + 0 = **2**
- k=3: 2 − √2 ≈ **0.586**

*Check trace: (2+√2) + 2 + (2−√2) = 6 ✓; det: (2+√2)(2)(2−√2) = 2(4−2) = 4 ✓*
All positive ✓ confirming positive definiteness independently.

**C4.** Fit y = β₀ + β₁x + β₂x² to (−2,3), (−1,1), (0,0), (1,1), (2,4).
Sums: m = 5, Σx = 0, Σx² = 4+1+0+1+4 = 10, Σx³ = 0, Σx⁴ = 16+1+0+1+16 = 34.
Σy = 9, Σxy = −6 −1 + 0 + 1 + 8 = 2, Σx²y = 12 + 1 + 0 + 1 + 16 = 30.
```
[[5,  0, 10],   [β₀]   [ 9]
 [0, 10,  0], · [β₁] = [ 2]
 [10, 0, 34]]   [β₂]   [30]
```
From row 2: **β₁ = 0.2**.
Rows 1 and 3: 5β₀ + 10β₂ = 9; 10β₀ + 34β₂ = 30.
Multiply row 1 by 2: 10β₀ + 20β₂ = 18. Subtract: 14β₂ = 12 → **β₂ = 6/7 ≈ 0.8571**.
5β₀ = 9 − 60/7 = (63 − 60)/7 = 3/7 → **β₀ = 3/35 ≈ 0.0857**.

**y = 0.0857 + 0.2x + 0.8571x²**

**Fitted values:**
- x=−2: 0.0857 − 0.4 + 3.4286 = 3.1143
- x=−1: 0.0857 − 0.2 + 0.8571 = 0.7429
- x=0: 0.0857
- x=1: 0.0857 + 0.2 + 0.8571 = 1.1429
- x=2: 0.0857 + 0.4 + 3.4286 = 3.9143

**Residuals:** −0.1143, 0.2571, −0.0857, −0.1429, 0.0857
**SSE** = 0.01306 + 0.06612 + 0.00735 + 0.02041 + 0.00735 = **0.1143**
ȳ = 1.8. SST = (1.2)² + (0.8)² + (1.8)² + (0.8)² + (2.2)² = 1.44 + 0.64 + 3.24 + 0.64 + 4.84 = **10.8**
**R² = 1 − 0.1143/10.8 = 0.9894**

**C5.** T(p)(t) = p(2t − 1).
- T(1) = 1 → (1, 0, 0)ᵀ
- T(t) = 2t − 1 → (−1, 2, 0)ᵀ
- T(t²) = (2t−1)² = 4t² − 4t + 1 → (1, −4, 4)ᵀ
```
[T]_B = [[1, −1,  1],
         [0,  2, −4],
         [0,  0,  4]]
```
Upper triangular → **det = 1(2)(4) = 8 ≠ 0 → invertible** ✓
**Eigenvalues: 1, 2, 4** (the diagonal entries) — three distinct, so T is **diagonalizable**.

*Sanity check:* the eigenvalues are 2⁰, 2¹, 2² — as expected, since T scales the degree-k part by 2ᵏ.

**C6.** A = [[1, 1, 0], [0, 1, 1]] (2×3). Use **AAᵀ:**
- (1,1): 1 + 1 + 0 = 2
- (1,2): 0 + 1 + 0 = 1
- (2,2): 0 + 1 + 1 = 2
```
AAᵀ = [[2, 1], [1, 2]]
```
Eigenvalues **3, 1** → **σ₁ = √3, σ₂ = 1.**
**u₁ = (1/√2)(1, 1), u₂ = (1/√2)(1, −1).**

vᵢ = Aᵀuᵢ/σᵢ:
Aᵀu₁ = (1/√2)[[1,0],[1,1],[0,1]]·(1,1)ᵀ = (1/√2)(1, 2, 1). Divide by √3: **v₁ = (1/√6)(1, 2, 1)**
Aᵀu₂ = (1/√2)(1, 0, −1). Divide by 1: **v₂ = (1/√2)(1, 0, −1)**
v₃ spans Nul(A): x₁ + x₂ = 0, x₂ + x₃ = 0 → x₁ = −x₂ = x₃. **v₃ = (1/√3)(1, −1, 1)**

**Pseudoinverse:** A⁺ = (1/σ₁)v₁u₁ᵀ + (1/σ₂)v₂u₂ᵀ
Term 1: (1/√3)(1/√6)(1,2,1)ᵀ(1/√2)(1,1) = (1/6)[[1,1],[2,2],[1,1]]
Term 2: (1)(1/√2)(1,0,−1)ᵀ(1/√2)(1,−1) = (1/2)[[1,−1],[0,0],[−1,1]]
```
A⁺ = (1/6)[[1,1],[2,2],[1,1]] + (1/6)[[3,−3],[0,0],[−3,3]]
   = (1/6)[[ 4, −2],
           [ 2,  2],
           [−2,  4]]
   = (1/3)[[ 2, −1],
           [ 1,  1],
           [−1,  2]]
```

**Minimum-norm solution for b = (2, 3):**
x̂ = A⁺(2,3)ᵀ = (1/3)(4 − 3, 2 + 3, −2 + 6) = (1/3)(1, 5, 4) = **(1/3, 5/3, 4/3)ᵀ**

**Check:** Ax̂ = (1/3 + 5/3, 5/3 + 4/3) = (6/3, 9/3) = (2, 3) ✓ exact.
**Minimum norm:** x̂ ⊥ Nul(A) = span{(1,−1,1)}: (1, 5, 4)·(1,−1,1) = 1 − 5 + 4 = **0** ✓

**C7.** AM: **λ=2 has AM 3; λ=5 has AM 1.**
GM(2) = 4 − rank(A − 2I) = 4 − 2 = **2.**
GM(5) = 1 (an eigenvalue always has GM ≥ 1, and GM ≤ AM = 1) → **GM(5) = 1 = AM ✓**

Since **GM(2) = 2 < 3 = AM(2)**, **A is NOT diagonalizable.**

**Jordan structure for λ = 2:** the number of Jordan blocks equals GM = 2; their total size equals AM = 3. The only partition of 3 into 2 parts is **2 + 1**.
```
J = [[2, 1, 0, 0],
     [0, 2, 0, 0],
     [0, 0, 2, 0],
     [0, 0, 0, 5]]
```
One 2×2 block and one 1×1 block for λ=2, plus a 1×1 block for λ=5.
**Minimal polynomial: (λ−2)²(λ−5).**

**C8.** The line y = 2x has direction u = (1, 2), u·u = 5.
**P = uuᵀ/5 = (1/5)[[1, 2], [2, 4]]**

**Symmetric?** ✓ visibly.
**Idempotent?** P² = uuᵀuuᵀ/25 = u(5)uᵀ/25 = uuᵀ/5 = **P** ✓
**Trace?** (1 + 4)/5 = **1** ✓ = rank (a rank-1 projection).

*Check: P(1,2)ᵀ = (1/5)(1+4, 2+8) = (1, 2) ✓ fixes the line. P(2,−1)ᵀ = (1/5)(2−2, 4−4) = (0,0) ✓ kills the perpendicular.*

**C9.** **Proof.** Let rank(A) = r. By the Pivot Column Theorem, choose the r pivot columns of A to form the m×r matrix **B**; they are independent, so rank(B) = r (full column rank).

Every column aⱼ of A lies in Col(A) = Col(B), so aⱼ = B·cⱼ for a unique cⱼ ∈ ℝʳ. Assembling, **A = BC** with C = [c₁ ... cₙ] of size r×n.

Since rank(A) = r and rank(A) ≤ rank(C), we get rank(C) ≥ r; also rank(C) ≤ r since C has r rows. So **rank(C) = r** (full row rank) ✓ ∎

*(Constructively, C is exactly the matrix of nonzero rows of the RREF of A.)*

**Explicit computation** for A = [[1, 2, 3], [2, 4, 6], [1, 1, 1]]:
`R₂ − 2R₁`, `R₃ − R₁`:
```
[[1,  2,  3],
 [0,  0,  0],
 [0, −1, −2]]
```
Swap R₂ ↔ R₃, scale: [[1, 2, 3], [0, 1, 2], [0,0,0]]. Then `R₁ − 2R₂`:
```
RREF = [[1, 0, −1],
        [0, 1,  2],
        [0, 0,  0]]
```
**rank = 2.** Pivot columns 1, 2.
```
B = [[1, 2],      C = [[1, 0, −1],
     [2, 4],           [0, 1,  2]]
     [1, 1]]
```
**Verify A = BC.**
Row 1: 1(1,0,−1) + 2(0,1,2) = (1, 2, 3) ✓
Row 2: 2(1,0,−1) + 4(0,1,2) = (2, 4, 6) ✓
Row 3: 1(1,0,−1) + 1(0,1,2) = (1, 1, 1) ✓

**C10.** A³ = 4A → A³ − 4A = 0 → A(A² − 4I) = 0 → A(A−2I)(A+2I) = 0.

The minimal polynomial divides **λ(λ−2)(λ+2)**, which has **three distinct roots**.

**Possible eigenvalues: 0, 2, −2.**

**Diagonalizable?** Yes — the minimal polynomial has distinct linear factors (§10.2.9), so **A is always diagonalizable** ✓

**Possible det A.** det A = product of the three eigenvalues, each drawn from {0, 2, −2}.
- If any eigenvalue is 0 → **det A = 0**
- Otherwise all three are ±2, giving products **±8**

Enumerating the sign patterns of three values from {2, −2}:
(+,+,+) → 8; (+,+,−) → −8; (+,−,−) → 8; (−,−,−) → −8.

**Answer: det A ∈ {0, 8, −8}.**

**C11.** p(λ) = (1−λ)² − 4 = λ² − 2λ − 3 = (λ−3)(λ+1). **λ = 3, −1.**
λ=3: A − 3I = [[−2, 1], [4, −2]] → 2v₁ = v₂ → **(1, 2)**
λ=−1: A + I = [[2,1],[4,2]] → v₂ = −2v₁ → **(1, −2)**

x(t) = c₁e^{3t}(1,2) + c₂e^{−t}(1,−2).
Initial: c₁ + c₂ = 2; 2c₁ − 2c₂ = 0 → c₁ = c₂ = **1**.

**x(t) = e^{3t}(1, 2) + e^{−t}(1, −2)**
i.e. x₁ = e^{3t} + e^{−t}, x₂ = 2e^{3t} − 2e^{−t}.

*Check: x(0) = (2, 0) ✓. x₁′ = 3e^{3t} − e^{−t}; (Ax)₁ = x₁ + x₂ = e^{3t} + e^{−t} + 2e^{3t} − 2e^{−t} = 3e^{3t} − e^{−t} ✓*

**Long-run behaviour.** The e^{−t} term decays to 0; the e^{3t} term dominates. So

> x(t) ≈ e^{3t}(1, 2) for large t

The trajectory **grows without bound**, asymptotically aligning with the direction (1, 2). The origin is an **unstable node** (both eigenvalues real, opposite signs → actually a **saddle point**: motion decays along (1,−2) and grows along (1,2)).

**C12.** Means: x̄₁ = (2+4+6+8)/4 = 5; x̄₂ = (1+3+4+8)/4 = 4.
```
X_c = [[−3, −3],
       [−1, −1],
       [ 1,  0],
       [ 3,  4]]
```
X_cᵀX_c:
- (1,1): 9 + 1 + 1 + 9 = 20
- (1,2): 9 + 1 + 0 + 12 = 22
- (2,2): 9 + 1 + 0 + 16 = 26
```
X_cᵀX_c = [[20, 22], [22, 26]]
S = (1/3)[[20, 22], [22, 26]]
```
**Eigenvalues of [[20,22],[22,26]]:** p(λ) = λ² − 46λ + (520 − 484) = λ² − 46λ + 36.
λ = [46 ± √(2116 − 144)]/2 = [46 ± √1972]/2 = [46 ± 44.407]/2
**λ₁ = 45.203, λ₂ = 0.797** → S-eigenvalues **15.068 and 0.266**.

**q₁:** (20 − 45.203)v₁ + 22v₂ = 0 → −25.203v₁ + 22v₂ = 0 → v₁ = 0.8729v₂.
v = (0.8729, 1), ‖v‖ = √(0.762 + 1) = 1.3274.
**q₁ = (0.6576, 0.7534)**, **q₂ = (−0.7534, 0.6576)**

**Explained variance:** 45.203/46 = **98.27%** and 0.797/46 = **1.73%**.

**1-D reconstruction error** = λ₂ portion of X_cᵀX_c = **0.797** (in sum-of-squares units).
Equivalently ‖X_c − X_cq₁q₁ᵀ‖_F² = 0.797, so the **RMS reconstruction error per entry** = √(0.797/8) = **0.316**.

**C13.** Seek real A with A² = D = diag(1, 4).

**Approach 1 — diagonal solutions.** A = diag(a, d) with a² = 1, d² = 4 gives **four solutions**:
diag(1,2), diag(1,−2), diag(−1,2), diag(−1,−2).

**Approach 2 — are there non-diagonal ones?** Suppose A² = D. Then A commutes with D:
AD = A·A² = A²·A = DA ✓
Since D = diag(1, 4) has **distinct** diagonal entries, any matrix commuting with it must be **diagonal**.
*(Proof: (AD)ᵢⱼ = aᵢⱼdⱼ and (DA)ᵢⱼ = dᵢaᵢⱼ. Equality forces aᵢⱼ(dⱼ − dᵢ) = 0, so aᵢⱼ = 0 whenever dᵢ ≠ dⱼ.)*

**Therefore A must be diagonal, and there are exactly four solutions:**
> **diag(1, 2), diag(1, −2), diag(−1, 2), diag(−1, −2)**

*(Contrast: if D had a repeated eigenvalue, say D = I, there would be infinitely many square roots — every reflection squares to I, as in S3.9.)*

**C14.** A = [[3,1,1],[1,3,1],[1,1,3]] = **2I + J** where J is the all-ones matrix.

By Example 9.8, J has eigenvalues **3** (eigenvector (1,1,1)) and **0** (multiplicity 2, eigenspace {x : Σxᵢ = 0}).

**A = 2I + J has eigenvalues 2 + 3 = 5 and 2 + 0 = 2 (multiplicity 2).**

**λ = 5:** eigenvector **(1, 1, 1)** → q₁ = (1/√3)(1,1,1)
**λ = 2:** eigenspace {x : x₁+x₂+x₃ = 0}. Basis {(1,−1,0), (1,0,−1)} — not orthogonal.
Gram–Schmidt: w₁ = (1,−1,0). w₂ = (1,0,−1) − (1/2)(1,−1,0) = (1/2, 1/2, −1) → ×2: **(1, 1, −2)**.
*Check: (1,−1,0)·(1,1,−2) = 0 ✓*
**q₂ = (1/√2)(1,−1,0), q₃ = (1/√6)(1,1,−2)**

```
Q = [[1/√3,  1/√2,  1/√6],
     [1/√3, −1/√2,  1/√6],
     [1/√3,  0,    −2/√6]]
D = diag(5, 2, 2)
```

**A^{10}.** Eigenvalues become 5¹⁰ = 9,765,625 and 2¹⁰ = 1024.
Since A^{10} must also have the form aI + bJ (it shares the eigenvectors and the structure):
- On (1,1,1): a + 3b = 5¹⁰ = 9765625
- On Nul(J): a = 2¹⁰ = 1024

So 3b = 9765625 − 1024 = 9764601 → **b = 3254867**.

```
A^{10} = 1024·I + 3254867·J
       = [[3255891, 3254867, 3254867],
          [3254867, 3255891, 3254867],
          [3254867, 3254867, 3255891]]
```
*Check trace: 3(3255891) = 9767673 = 9765625 + 1024 + 1024 ✓*

**C15.** P = 0.25·J + 0.25·I where J is the 3×3 all-ones matrix.
*Check: 0.25J has all entries 0.25; adding 0.25I gives diagonal 0.5 ✓*

**Eigenvalues.** J has eigenvalues 3, 0, 0. So P = 0.25J + 0.25I has eigenvalues
- 0.25(3) + 0.25 = **1** (eigenvector (1,1,1))
- 0.25(0) + 0.25 = **0.25** (multiplicity 2)

*Check trace: 1 + 0.25 + 0.25 = 1.5 = 3(0.5) ✓*

**Steady state.** The eigenvector for λ = 1 is (1, 1, 1); normalizing to sum 1:
> **q = (1/3, 1/3, 1/3)**

*Check: Pq = (0.5 + 0.25 + 0.25)/3 = 1/3 ✓ for each component.*

By symmetry this is obvious — the chain treats all three states identically.

**Rate of convergence.** The second-largest eigenvalue modulus is **|λ₂| = 0.25**, so the error decays as

> ‖x_k − q‖ ≈ C(0.25)ᵏ

**Spectral gap = 1 − 0.25 = 0.75** — very large, so the chain **mixes extremely fast**.

**Iterations for 10⁻⁶ accuracy:** (0.25)ᵏ ≤ 10⁻⁶ → k ≥ 6/log₁₀4 = 6/0.602 = 9.97 → **k = 10 steps.**

*(Contrast with a chain having λ₂ = 0.99: it would need ln(10⁻⁶)/ln(0.99) ≈ 1375 steps. The spectral gap is everything.)*

---

## 15.4 Set D — [Very Hard] Ten Challenge Problems

**D1.** Let A be an n×n matrix with A² = A (idempotent). Prove that **rank(A) = tr(A)**.

**D2.** Let A be m×n and B be n×m with m > n. Prove that AB is singular, and that the nonzero eigenvalues of AB and BA coincide with multiplicity.

**D3.** Prove that for any square A, **rank(A^{k+1}) = rank(Aᵏ)** for some k ≤ n, and that the ranks stabilize thereafter.

**D4.** Let A be a real symmetric n×n matrix with eigenvalues λ₁ ≥ ... ≥ λₙ, and let B be the (n−1)×(n−1) matrix obtained by deleting the last row and column. Prove the **interlacing inequalities** λ₁ ≥ μ₁ ≥ λ₂ ≥ μ₂ ≥ ... ≥ μ_{n−1} ≥ λₙ, where μᵢ are B's eigenvalues. (Prove the outer inequalities at minimum.)

**D5.** Prove that every orthogonal 3×3 matrix with determinant +1 is a rotation about some axis, and that the axis is the eigenvector for eigenvalue 1.

**D6.** Let A be n×n with all entries positive and all column sums equal to 1. Prove that 1 is a simple eigenvalue and that every other eigenvalue has modulus strictly less than 1.

**D7.** Show that the set of n×n matrices commuting with a fixed diagonalizable A with **distinct** eigenvalues forms a vector space of dimension exactly n, and identify a basis.

**D8.** Prove **Hadamard's inequality**: for any n×n matrix A with columns a₁, ..., aₙ,
|det A| ≤ ‖a₁‖ · ‖a₂‖ · ... · ‖aₙ‖,
with equality iff the columns are orthogonal or some column is zero.

**D9.** Let A be m×n with singular values σ₁ ≥ ... ≥ σ_r > 0. Prove that for any unit vectors x and y,
|yᵀAx| ≤ σ₁, and that equality is attained exactly at x = ±v₁, y = ±u₁.

**D10.** **(Courant–Fischer min-max theorem.)** For a symmetric n×n matrix A with eigenvalues λ₁ ≥ ... ≥ λₙ, prove
λ_k = max_{dim S = k} min_{x ∈ S, ‖x‖=1} xᵀAx.
Use it to prove that adding a positive semidefinite matrix can only increase each eigenvalue.

---

### Solutions to Set D

**D1.** By S10.17/§10.2.9, A² = A means the minimal polynomial divides λ(λ−1), which has **distinct roots**, so **A is diagonalizable** with all eigenvalues in {0, 1}.

Let r = the number of eigenvalues equal to 1 (with multiplicity). Then A = PDP⁻¹ with D = diag(1,...,1,0,...,0) having r ones.

- **rank(A) = rank(D) = r** (rank is a similarity invariant)
- **tr(A) = tr(D) = r** (trace is a similarity invariant, and tr D is the count of ones)

**Therefore rank(A) = tr(A)** ✓ ∎

*(Geometrically: an idempotent matrix is a projection onto Col(A) along Nul(A), and the trace of a projection is the dimension of the space it projects onto.)*

**D2.** **Singularity of AB.** AB is m×m. By the rank inequality,
rank(AB) ≤ rank(A) ≤ min(m, n) = **n** (since m > n).
So rank(AB) ≤ n < m, meaning the m×m matrix AB is **not full rank** → **singular**, det(AB) = 0 ✓

**Nonzero eigenvalues coincide.** Suppose ABx = λx with λ ≠ 0, x ≠ 0. Set **y = Bx**.
- y ≠ 0: if y = 0 then λx = A0 = 0, forcing x = 0 (as λ ≠ 0) — contradiction ✓
- BA y = B(ABx) = B(λx) = λ(Bx) = λy ✓

So λ is an eigenvalue of BA. The map x ↦ Bx is a linear bijection from the λ-eigenspace of AB onto that of BA (inverse y ↦ (1/λ)Ay: check A(Bx)/λ = ABx/λ = x ✓), so **geometric multiplicities match**.

For **algebraic** multiplicities, use the determinant identity
> **λⁿ·det(λI_m − AB) = λᵐ·det(λI_n − BA)**

which holds by the block-matrix computation: compute det of [[λI_m, A], [B, I_n]] two ways using Schur complements. Comparing factorizations of both sides shows the nonzero roots have identical multiplicities, and AB carries an extra λ^{m−n} factor ✓ ∎

**D3.** The chain of null spaces is **nested and increasing**:
> Nul(A) ⊆ Nul(A²) ⊆ Nul(A³) ⊆ ...

*(If Aᵏx = 0 then A^{k+1}x = A(Aᵏx) = 0 ✓)*

Hence the dimensions n₁ ≤ n₂ ≤ n₃ ≤ ... are a non-decreasing sequence of integers **bounded above by n**. Such a sequence must stop increasing: there is a smallest k ≤ n with **n_{k+1} = n_k**.

By rank–nullity, rank(Aⁱ) = n − nᵢ, so **rank(A^{k+1}) = rank(Aᵏ)** ✓

**Stabilization.** Claim: once Nul(A^{k+1}) = Nul(Aᵏ), then Nul(A^{k+2}) = Nul(A^{k+1}) too.
*Proof:* Let x ∈ Nul(A^{k+2}), so A^{k+1}(Ax) = 0, i.e. Ax ∈ Nul(A^{k+1}) = Nul(Aᵏ). Then Aᵏ(Ax) = 0, i.e. A^{k+1}x = 0, so x ∈ Nul(A^{k+1}) ✓

By induction the null spaces (and hence the ranks) are **constant for all exponents ≥ k** ✓ ∎

**Bound on k:** since n₁ ≥ 1 whenever A is singular, and each strict increase adds at least 1 to a quantity capped at n, we get **k ≤ n** ✓
*(This k is the index of nilpotency of the nilpotent part; the stable subspace Col(Aᵏ) and Nul(Aᵏ) give the Fitting decomposition ℝⁿ = Nul(Aᵏ) ⊕ Col(Aᵏ).)*

**D4.** Write A in block form with B the leading (n−1)×(n−1) block:
```
A = [[B,   c],
     [cᵀ,  d]]
```
Let the eigenvalues of A be λ₁ ≥ ... ≥ λₙ and of B be μ₁ ≥ ... ≥ μ_{n−1}.

**Proof of λ₁ ≥ μ₁.** Let w be a unit eigenvector of B for μ₁, and embed it as x = (w, 0)ᵀ ∈ ℝⁿ (unit norm). Then
xᵀAx = wᵀBw = μ₁.
By Theorem 11.5, λ₁ = max_{‖x‖=1}xᵀAx ≥ μ₁ ✓

**Proof of μ_{n−1} ≥ λₙ.** Symmetrically, with w the unit eigenvector for μ_{n−1}:
λₙ = min_{‖x‖=1}xᵀAx ≤ (w,0)ᵀA(w,0) = μ_{n−1} ✓

**General interlacing** (using Courant–Fischer, Problem D10):
λ_k = max_{dim S = k} min_{x∈S, ‖x‖=1} xᵀAx.

**λ_k ≥ μ_k:** take S to be the k-dimensional subspace of ℝⁿ obtained by embedding the top-k eigenspace of B (as vectors with last coordinate 0). On this subspace, xᵀAx = wᵀBw ≥ μ_k. So λ_k ≥ μ_k ✓

**μ_k ≥ λ_{k+1}:** apply the min-max form to A. Let S be any (k+1)-dimensional subspace of ℝⁿ realizing λ_{k+1}; intersecting with the hyperplane {xₙ = 0} (dimension n−1) gives a subspace of dimension ≥ k inside ℝ^{n−1}. On it, wᵀBw = xᵀAx ≥ λ_{k+1}, so μ_k ≥ λ_{k+1} ✓ ∎

**Example check.** A = [[2, 1], [1, 2]] has λ = 3, 1. B = [2] has μ = 2.
Interlacing: 3 ≥ 2 ≥ 1 ✓

**D5.** Let Q be 3×3 orthogonal with det Q = +1.

**Step 1: 1 is an eigenvalue.**
det(Q − I) = det(Q − QQᵀ) = det(Q(I − Qᵀ)) = det(Q)·det(I − Qᵀ)
= 1·det((I − Q)ᵀ) = det(I − Q) = **(−1)³det(Q − I) = −det(Q − I)**

So det(Q − I) = −det(Q − I) → **det(Q − I) = 0** → **1 is an eigenvalue** ✓

Let **n** be a unit eigenvector: Qn = n. This is the **axis**.

**Step 2: Q acts as a rotation in n⊥.**
The plane n⊥ is Q-invariant: if w ⊥ n then
(Qw)·n = (Qw)·(Qn) = w·n = 0 ✓ (Q preserves inner products)

So Q restricted to the 2-dimensional plane n⊥ is an orthogonal 2×2 map. Its determinant is det(Q)/1 = **+1**, so it is a **rotation** (not a reflection) of that plane — every 2×2 orthogonal matrix with determinant +1 is [[cos θ, −sin θ],[sin θ, cos θ]].

**Conclusion:** Q fixes the axis n and rotates the perpendicular plane by some angle θ — that is precisely a **rotation about the axis spanned by n** ✓ ∎

**Finding the angle.** tr(Q) = 1 + 2cos θ (the fixed direction contributes 1, the rotation block contributes 2cos θ), so
> **θ = arccos((tr Q − 1)/2)**

*(This, with Rodrigues' formula from P12.21, is the complete axis–angle correspondence used throughout robotics and graphics. The other case, det Q = −1, gives improper rotations: a rotation composed with a reflection.)*

**D6.** Let A be n×n with all entries **strictly positive** and column sums 1 (column-stochastic).

**Step 1: 1 is an eigenvalue.** By S8.16, 1ᵀA = 1ᵀ, so 1 is an eigenvalue of Aᵀ and hence of A ✓

**Step 2: every eigenvalue satisfies |λ| ≤ 1.** Let Aᵀw = λw *(work with Aᵀ, which is row-stochastic)*. Pick the index i maximizing |wᵢ|. Then
|λ||wᵢ| = |Σⱼ(Aᵀ)ᵢⱼwⱼ| ≤ Σⱼ(Aᵀ)ᵢⱼ|wⱼ| ≤ |wᵢ|Σⱼ(Aᵀ)ᵢⱼ = |wᵢ|
So **|λ| ≤ 1** ✓

**Step 3: |λ| = 1 forces λ = 1.** Suppose |λ| = 1. Then every inequality above is an **equality**. Equality in Σ(Aᵀ)ᵢⱼ|wⱼ| ≤ |wᵢ|Σ(Aᵀ)ᵢⱼ requires **|wⱼ| = |wᵢ| for every j with (Aᵀ)ᵢⱼ > 0** — which, by strict positivity, means **for every j**. So all |wⱼ| are equal, say equal to c > 0.

Equality in the triangle inequality |Σ(Aᵀ)ᵢⱼwⱼ| = Σ(Aᵀ)ᵢⱼ|wⱼ| requires all the wⱼ to have the **same complex argument**. Combined with equal moduli, **all wⱼ are equal**: w = c·1 (up to a unit scalar).

Then Aᵀw = w gives λ = **1** ✓

**Step 4: λ = 1 is simple.** From Step 3, any eigenvector for an eigenvalue of modulus 1 is a multiple of **1**, so the eigenspace of Aᵀ for λ = 1 is **one-dimensional**, i.e. GM(1) = 1.

For **algebraic** simplicity: suppose AM(1) > 1. Then there would be a generalized eigenvector v with (Aᵀ − I)v = 1. Multiplying on the left by 1ᵀ:
1ᵀ(Aᵀ − I)v = 1ᵀ1 = n.
But 1ᵀAᵀ = (A1)ᵀ... using column-stochasticity differently: for row-stochastic Aᵀ, Aᵀ1 = 1, so 1ᵀ(Aᵀ)ᵀ = 1ᵀA. Hmm — instead use the left eigenvector: the positive vector q with Aq = q satisfies qᵀ(Aᵀ − I) = 0, so
0 = qᵀ(Aᵀ − I)v = qᵀ1 = Σqᵢ > 0 — **contradiction** ✓

**Therefore AM(1) = GM(1) = 1, and every other eigenvalue has |λ| < 1** ✓ ∎

*(This is the Perron–Frobenius theorem for positive stochastic matrices, and is precisely what guarantees PageRank converges to a unique answer.)*

**D7.** Let A = PDP⁻¹ with D = diag(λ₁, ..., λₙ) and the λᵢ **distinct**.

**Step 1: reduce to the diagonal case.** B commutes with A ⟺ (P⁻¹BP) commutes with D.
*(AB = BA ⟺ PDP⁻¹B = BPDP⁻¹ ⟺ D(P⁻¹BP) = (P⁻¹BP)D ✓)*
Conjugation by P is a linear bijection on matrices, so the two commutant spaces have the **same dimension**.

**Step 2: what commutes with D?** Let C = P⁻¹BP. Then
(DC)ᵢⱼ = λᵢcᵢⱼ and (CD)ᵢⱼ = cᵢⱼλⱼ.
Equality forces **cᵢⱼ(λᵢ − λⱼ) = 0**. Since the λᵢ are distinct, λᵢ ≠ λⱼ for i ≠ j, so **cᵢⱼ = 0 for all i ≠ j**.

So C must be **diagonal**, and every diagonal C does commute with D ✓

**Step 3: dimension and basis.**
The space of diagonal n×n matrices has dimension **n**, with basis {E₁₁, E₂₂, ..., Eₙₙ} (the matrix units).

Pulling back through P, the commutant of A is
> **{P diag(c₁,...,cₙ) P⁻¹ : cᵢ ∈ ℝ}**, with basis **{Pᵢ := P Eᵢᵢ P⁻¹}** for i = 1,...,n.

Each Pᵢ = vᵢwᵢᵀ where vᵢ is the i-th column of P (right eigenvector) and wᵢᵀ the i-th row of P⁻¹ (left eigenvector) — these are exactly the **spectral projections** of A.

**Dimension = n** ✓ ∎

**Alternative basis.** {I, A, A², ..., A^{n−1}} also works: these are n matrices, all commute with A, and they are **independent** because the Vandermonde matrix on the distinct eigenvalues is invertible (Example 7.7). So **every matrix commuting with A is a polynomial in A** — recovering P10.20 ✓

**D8.** **Hadamard's inequality:** |det A| ≤ Π‖aⱼ‖.

**Case 1: columns dependent.** det A = 0, and the right side is ≥ 0, so the inequality holds ✓ (and equality requires some ‖aⱼ‖ = 0, i.e. a zero column).

**Case 2: columns independent.** Apply **Gram–Schmidt / QR**: write A = QR with Q orthogonal and R upper triangular with positive diagonal entries r₁₁, ..., rₙₙ.

Then |det A| = |det Q||det R| = 1 · Πrⱼⱼ = **Πrⱼⱼ**.

Now relate rⱼⱼ to ‖aⱼ‖. From A = QR, the j-th column is
aⱼ = Σ_{i≤j} rᵢⱼqᵢ,
and since the qᵢ are orthonormal:
‖aⱼ‖² = Σ_{i≤j} rᵢⱼ² ≥ **rⱼⱼ²**

So **rⱼⱼ ≤ ‖aⱼ‖** for every j, giving

|det A| = Πrⱼⱼ ≤ Π‖aⱼ‖ ✓ ∎

**Equality condition.** Equality requires rⱼⱼ = ‖aⱼ‖ for every j, i.e. Σ_{i<j}rᵢⱼ² = 0, i.e. **rᵢⱼ = 0 for all i < j**. So R is **diagonal**, meaning A = QR has **orthogonal columns** ✓

**Geometric meaning.** |det A| is the volume of the parallelepiped spanned by the columns; Π‖aⱼ‖ is the volume of the rectangular box with the same edge lengths. A skewed box always has **less** volume than the right-angled box with the same edges — and equality holds exactly when the box is already right-angled.

**Corollary (bound for entries in [−1,1]):** if all |aᵢⱼ| ≤ 1, then ‖aⱼ‖ ≤ √n, so **|det A| ≤ n^{n/2}**. Matrices attaining this bound are **Hadamard matrices**.

**D9.** Let A = UΣVᵀ, with x, y unit vectors.

**Upper bound.** By Cauchy–Schwarz:
|yᵀAx| ≤ ‖y‖·‖Ax‖ = ‖Ax‖.

And ‖Ax‖ ≤ σ₁‖x‖ = σ₁ by §13.2.4 / S13.16 (‖A‖₂ = σ₁).

**Therefore |yᵀAx| ≤ σ₁** ✓

**Direct computation confirming this.** Write x = Σcᵢvᵢ with Σcᵢ² = 1, and y = Σdᵢuᵢ with Σdᵢ² = 1. Then
Ax = Σᵢ cᵢσᵢuᵢ, so
yᵀAx = Σᵢ dᵢcᵢσᵢ.

By Cauchy–Schwarz on the sequences (dᵢ√σᵢ) and (cᵢ√σᵢ)... more simply:
|Σdᵢcᵢσᵢ| ≤ σ₁Σ|dᵢ||cᵢ| ≤ σ₁·√(Σdᵢ²)√(Σcᵢ²) = **σ₁** ✓

**Equality analysis.** Equality in the second Cauchy–Schwarz requires **|cᵢ| = |dᵢ|** for all i. Equality in the first (pulling out σ₁) requires cᵢdᵢ = 0 whenever σᵢ < σ₁.

If σ₁ is a **simple** singular value, both conditions force c = ±e₁ and d = ±e₁ with matching signs, i.e.
> **x = ±v₁ and y = ±u₁** (same sign for the maximum +σ₁) ✓ ∎

*(If σ₁ is repeated with multiplicity m, equality is attained on the whole pair of m-dimensional top singular subspaces, with y determined by x.)*

**Interpretation.** σ₁ = max_{‖x‖=‖y‖=1} yᵀAx is a **variational characterization of the largest singular value** — the matrix analogue of the Rayleigh quotient, and the basis of the power method for computing σ₁.

**D10.** **Courant–Fischer (max-min form).** For symmetric A with eigenvalues λ₁ ≥ ... ≥ λₙ and orthonormal eigenvectors q₁, ..., qₙ:

> **λ_k = max_{dim S = k} min_{x ∈ S, ‖x‖=1} xᵀAx**

**Proof, part 1 (≥): exhibit a subspace achieving λ_k.**
Take **S₀ = span{q₁, ..., q_k}**, which has dimension k. For any unit x ∈ S₀, write x = Σ_{i≤k}cᵢqᵢ with Σcᵢ² = 1. Then
xᵀAx = Σ_{i≤k}λᵢcᵢ² ≥ λ_k Σcᵢ² = **λ_k**
*(using λᵢ ≥ λ_k for i ≤ k)*

So min over S₀ is ≥ λ_k, and hence max over all S is ≥ λ_k ✓
*(The min equals exactly λ_k, attained at x = q_k.)*

**Proof, part 2 (≤): no subspace can beat λ_k.**
Let S be **any** k-dimensional subspace. Let **T = span{q_k, q_{k+1}, ..., qₙ}**, of dimension n − k + 1.

Dimension count: dim S + dim T = k + (n − k + 1) = n + 1 > n, so **S ∩ T contains a unit vector x**.

Since x ∈ T, write x = Σ_{i≥k}cᵢqᵢ with Σcᵢ² = 1. Then
xᵀAx = Σ_{i≥k}λᵢcᵢ² ≤ λ_k Σcᵢ² = **λ_k**
*(using λᵢ ≤ λ_k for i ≥ k)*

So for every k-dimensional S, min_{x∈S}xᵀAx ≤ λ_k ✓

Combining: **the max over all S equals exactly λ_k** ✓ ∎

**Application: monotonicity under PSD perturbation.**

> **Claim.** If B is positive semidefinite, then λ_k(A + B) ≥ λ_k(A) for every k.

*Proof.* For any unit x, since B is PSD, xᵀBx ≥ 0, so
xᵀ(A + B)x = xᵀAx + xᵀBx ≥ **xᵀAx**

Therefore, for any fixed k-dimensional subspace S:
min_{x∈S,‖x‖=1} xᵀ(A+B)x ≥ min_{x∈S,‖x‖=1} xᵀAx

Taking the maximum over all k-dimensional S on both sides preserves the inequality:
**λ_k(A + B) ≥ λ_k(A)** ✓ ∎

**Consequences.**
- **Weyl's inequality:** λ_k(A) + λₙ(B) ≤ λ_k(A + B) ≤ λ_k(A) + λ₁(B), so eigenvalues of symmetric matrices are **1-Lipschitz** in the spectral norm — a stability guarantee absent for general matrices.
- **Ridge regression:** adding λI (which is PSD) raises every eigenvalue of AᵀA by exactly λ, so the smallest goes from possibly 0 to λ > 0 — making the matrix invertible and capping the condition number at (σ₁² + λ)/λ. This **rigorously explains why ridge regularization stabilizes ill-conditioned problems** (P6.20, S14.19).

---
# Chapter 16 — Full-Length Mock Papers with Solutions

Each paper is designed for **3 hours**, total **70 marks**, covering both units. Attempt under exam conditions — no notes, no calculator beyond basic arithmetic — before looking at the solutions.

---

# MOCK PAPER I

**Time: 3 hours | Maximum marks: 70**
*Section A is compulsory. Attempt any FOUR from Section B and any TWO from Section C.*

---

## Section A — Short Answer (10 × 2 = 20 marks)

**1(a)** State the condition on the augmented matrix for a linear system to be inconsistent.

**1(b)** If A is 5×8 with nullity 3, find rank(A) and dim Row(A).

**1(c)** Give an example of a 2×2 matrix that is not diagonalizable, with justification.

**1(d)** If det A = −2 for a 4×4 matrix, find det(3A) and det(A⁻¹).

**1(e)** State the Spectral Theorem for real symmetric matrices.

**1(f)** Find the singular values of A = [[3, 0], [0, −4]].

**1(g)** Define the orthogonal complement W⊥ and state dim W + dim W⊥ for W ⊆ ℝⁿ.

**1(h)** When is a quadratic form xᵀAx positive definite? State two equivalent criteria.

**1(i)** State the rank–nullity theorem and give the condition for a linear map T : ℝⁿ → ℝᵐ to be one-to-one.

**1(j)** Write the normal equations for the least squares problem and state when the solution is unique.

---

## Section B — Medium Answer (4 × 7.5 = 30 marks)

**2.** Solve the system and express the answer in parametric vector form:
```
x₁ + 2x₂ − 3x₃ + x₄ = 2
2x₁ + 4x₂ − 5x₃ + 4x₄ = 7
x₁ + 2x₂ − 2x₃ + 3x₄ = 5
```

**3.** For A = [[1, 2, 2], [2, 1, 2], [2, 2, 1]], find all eigenvalues and eigenvectors, and determine whether A is diagonalizable.

**4.** Apply the Gram–Schmidt process to {(1, 1, 1), (1, 2, 0), (1, 0, 2)} and hence write the QR factorization of the matrix with these as columns.

**5.** Fit a least squares line to the data (1, 1), (2, 3), (3, 4), (4, 6), (5, 8) and compute SSE and R².

**6.** Prove that for any m×n matrix A, the columns of A are linearly independent if and only if AᵀA is invertible. Use this to explain when the normal equations have a unique solution.

**7.** Find the inverse of A = [[2, 1, 1], [1, 2, 1], [1, 1, 2]] by row reduction, and verify using the fact A = I + J.

---

## Section C — Long Answer (2 × 10 = 20 marks)

**8.** (a) Find the singular value decomposition of A = [[2, 1], [1, 2], [0, 0]]. **(6)**
(b) Hence find A⁺ and the minimum-norm least squares solution of Ax = (1, 2, 3)ᵀ. **(4)**

**9.** (a) Orthogonally diagonalize A = [[5, 2], [2, 2]] and classify the quadratic form Q = 5x₁² + 4x₁x₂ + 2x₂². **(5)**
(b) Identify the conic 5x₁² + 4x₁x₂ + 2x₂² = 6, find its principal axes and semi-axis lengths. **(5)**

**10.** A data matrix is X = [[1, 2], [3, 3], [5, 6], [7, 9]].
(a) Compute the mean vector, the centred matrix and the covariance matrix. **(4)**
(b) Find both principal components and the explained variance ratios. **(4)**
(c) Compute the 1-D scores and the reconstruction error. **(2)**

---

# SOLUTIONS — MOCK PAPER I

## Section A

**1(a)** The system is inconsistent ⟺ the echelon form of the augmented matrix contains a row of the form **[0 0 ... 0 | c] with c ≠ 0** ⟺ the **rightmost column is a pivot column**.

**1(b)** n = 8 columns. rank = 8 − 3 = **5**. dim Row(A) = rank = **5**.
*(Note rank = 5 = m, so A has full row rank and Ax = b is consistent for every b.)*

**1(c)** **A = [[1, 1], [0, 1]].** Characteristic polynomial (1−λ)², so λ = 1 with **AM = 2**. But A − I = [[0,1],[0,0]] has rank 1, so **GM = 2 − 1 = 1 < 2**. Since GM < AM, A is defective and not diagonalizable.

**1(d)** det(3A) = 3⁴(−2) = 81(−2) = **−162**. det(A⁻¹) = 1/(−2) = **−1/2**.

**1(e)** **Spectral Theorem.** A real n×n matrix A is symmetric ⟺ it is orthogonally diagonalizable, i.e. **A = QDQᵀ** with Q orthogonal (QᵀQ = I) and D real diagonal. Consequently all eigenvalues are real, eigenvectors for distinct eigenvalues are orthogonal, and ℝⁿ has an orthonormal basis of eigenvectors of A (so A is never defective).

**1(f)** AᵀA = diag(9, 16). Eigenvalues 16 and 9 → singular values **4 and 3** (sorted descending).
*Note they are |λᵢ|, not λᵢ — singular values are never negative.*

**1(g)** **W⊥ = {z ∈ ℝⁿ : z·w = 0 for every w ∈ W}** — the set of vectors orthogonal to every vector in W. It is a subspace, and **dim W + dim W⊥ = n**.

**1(h)** xᵀAx (A symmetric) is **positive definite** ⟺ xᵀAx > 0 for all x ≠ 0. Two equivalent criteria:
(i) **all eigenvalues of A are positive**;
(ii) **all leading principal minors are positive** (Sylvester's criterion): Δ₁ > 0, Δ₂ > 0, ..., Δₙ > 0.
*(Also: A = BᵀB with B of full column rank; or A = LLᵀ with L lower triangular with positive diagonal.)*

**1(i)** **Rank–nullity:** rank(T) + nullity(T) = n (the dimension of the **domain**).
**T is one-to-one ⟺ ker(T) = {0} ⟺ nullity(T) = 0 ⟺ rank(T) = n** ⟺ the standard matrix has a pivot in every column.

**1(j)** **Normal equations: AᵀAx̂ = Aᵀb.**
The solution is **unique ⟺ the columns of A are linearly independent ⟺ AᵀA is invertible**, in which case x̂ = (AᵀA)⁻¹Aᵀb. (The normal equations are always *consistent*, even when Ax = b is not.)

---

## Section B

**Q2.** Augmented:
```
[[1, 2, −3, 1 | 2],
 [2, 4, −5, 4 | 7],
 [1, 2, −2, 3 | 5]]
```
`R₂ − 2R₁`, `R₃ − R₁`:
```
[[1, 2, −3, 1 | 2],
 [0, 0,  1, 2 | 3],
 [0, 0,  1, 2 | 3]]
```
`R₃ − R₂` → zero row. `R₁ + 3R₂`:
```
RREF = [[1, 2, 0, 7 | 11],
        [0, 0, 1, 2 |  3],
        [0, 0, 0, 0 |  0]]
```
Pivots: columns 1, 3. **Free: x₂ = s, x₄ = t.**
x₁ = 11 − 2s − 7t, x₃ = 3 − 2t.

> **x = (11, 0, 3, 0) + s(−2, 1, 0, 0) + t(−7, 0, −2, 1)**

*Check in equation 3 with s = t = 0: 11 + 0 − 6 + 0 = 5 ✓*

**Q3.** Observe **A = J + ... ** check: J (all ones) has diagonal 1; we need diagonal 1 and off-diagonal 2. So A = 2J − I ✓ (diagonal 2 − 1 = 1 ✓, off-diagonal 2 ✓).

By the all-ones structure, **J has eigenvalues 3 (eigenvector (1,1,1)) and 0 (multiplicity 2)**.

**A = 2J − I has eigenvalues 2(3) − 1 = 5 and 2(0) − 1 = −1 (multiplicity 2).**

*Check trace: 5 − 1 − 1 = 3 = 1 + 1 + 1 ✓*

**λ = 5:** eigenvector **(1, 1, 1)**. GM = 1 = AM ✓

**λ = −1:** eigenspace = Nul(J) = {x : x₁ + x₂ + x₃ = 0}.
A + I = [[2,2,2],[2,2,2],[2,2,2]] has **rank 1**, so **GM(−1) = 3 − 1 = 2 = AM** ✓
**Basis: {(1, −1, 0), (1, 0, −1)}**

**Since GM = AM for every eigenvalue, A is diagonalizable.** ✓
*(Also immediate: A is symmetric, so the Spectral Theorem guarantees it.)*

```
P = [[1, 1,  1],       D = diag(5, −1, −1)
     [1, −1, 0],
     [1, 0, −1]]
```

**Q4.** x₁ = (1,1,1), x₂ = (1,2,0), x₃ = (1,0,2).

**v₁ = (1, 1, 1)**, v₁·v₁ = 3, ‖v₁‖ = √3 → **q₁ = (1/√3)(1,1,1)**

x₂·v₁ = 1 + 2 + 0 = 3.
v₂ = (1,2,0) − (3/3)(1,1,1) = **(0, 1, −1)**, ‖v₂‖ = √2 → **q₂ = (1/√2)(0, 1, −1)**

x₃·v₁ = 1 + 0 + 2 = 3. x₃·v₂ = 0 + 0 − 2 = −2, v₂·v₂ = 2.
v₃ = (1,0,2) − 1·(1,1,1) − (−2/2)(0,1,−1) = (1,0,2) − (1,1,1) + (0,1,−1) = **(0, 0, 0)**

**v₃ = 0** — so x₃ is **linearly dependent** on x₁ and x₂!
*Check: x₃ = 2x₁ − x₂ = (2,2,2) − (1,2,0) = (1, 0, 2) ✓*

**Conclusion:** the three vectors are dependent (rank 2), so a full 3-column QR does not exist with independent columns. The orthonormal basis for their span is **{q₁, q₂}**.

**Reduced QR** for the matrix A = [x₁ x₂] (dropping the redundant third column):
```
Q = [[1/√3,   0   ],      R = [[√3, √3],
     [1/√3,  1/√2 ],           [0,  √2]]
     [1/√3, −1/√2 ]]
```
- R₁₁ = q₁·x₁ = 3/√3 = √3 ✓
- R₁₂ = q₁·x₂ = 3/√3 = √3 ✓
- R₂₂ = q₂·x₂ = (0 + 2 − 0)/√2 = √2 ✓

*(If the exam intended independent columns, note the answer: recognizing the dependence is the key insight and earns full marks.)*

**Q5.** m = 5, Σx = 15, Σy = 22, Σxy = 1 + 6 + 12 + 24 + 40 = 83, Σx² = 55.

β₁ = (5(83) − 15(22))/(5(55) − 225) = (415 − 330)/(275 − 225) = 85/50 = **1.7**
β₀ = (22 − 1.7(15))/5 = (22 − 25.5)/5 = −3.5/5 = **−0.7**

> **y = −0.7 + 1.7x**

**Fitted:** 1.0, 2.7, 4.4, 6.1, 7.8
**Residuals:** 0, 0.3, −0.4, −0.1, 0.2
*(Sum = 0 ✓)*

**SSE** = 0 + 0.09 + 0.16 + 0.01 + 0.04 = **0.30**

ȳ = 22/5 = 4.4. **SST** = (3.4)² + (1.4)² + (0.4)² + (1.6)² + (3.6)²
= 11.56 + 1.96 + 0.16 + 2.56 + 12.96 = **29.2**

> **R² = 1 − 0.30/29.2 = 0.9897**

**Q6.** **Claim:** columns of A independent ⟺ AᵀA invertible.

**(⟸)** Suppose AᵀA is invertible. If Ax = 0, then AᵀAx = 0, so
x = (AᵀA)⁻¹(AᵀA)x = (AᵀA)⁻¹0 = **0**.
Hence Nul(A) = {0}, i.e. the columns are independent ✓

**(⟹)** Suppose the columns are independent, so Nul(A) = {0}. Let AᵀAx = 0. Then
xᵀAᵀAx = 0 → (Ax)ᵀ(Ax) = 0 → **‖Ax‖² = 0** → Ax = 0 → x = 0 (by independence).
So Nul(AᵀA) = {0}, and since AᵀA is **square** (n×n), it is invertible by the IMT ✓ ∎

**Application to least squares.** The normal equations are AᵀAx̂ = Aᵀb. They are always consistent, but:
- If the columns of A are **independent**, AᵀA is invertible, so the solution is **unique**: x̂ = (AᵀA)⁻¹Aᵀb.
- If the columns are **dependent**, AᵀA is singular and there are **infinitely many** least squares solutions, differing by elements of Nul(A). They all give the same projection Ax̂ = proj_{Col A}(b). The minimum-norm one is A⁺b.

**Q7.** [A | I]:
```
[[2, 1, 1 | 1, 0, 0],
 [1, 2, 1 | 0, 1, 0],
 [1, 1, 2 | 0, 0, 1]]
```
Swap R₁ ↔ R₂ for a leading 1:
```
[[1, 2, 1 | 0, 1, 0],
 [2, 1, 1 | 1, 0, 0],
 [1, 1, 2 | 0, 0, 1]]
```
`R₂ − 2R₁`, `R₃ − R₁`:
```
[[1,  2,  1 |  0,  1, 0],
 [0, −3, −1 |  1, −2, 0],
 [0, −1,  1 |  0, −1, 1]]
```
Swap R₂ ↔ R₃, then scale:
```
[[1,  2,  1 |  0,  1, 0],
 [0, −1,  1 |  0, −1, 1],
 [0, −3, −1 |  1, −2, 0]]
```
`R₂ → −R₂` → (0, 1, −1 | 0, 1, −1).
`R₃ + 3R₂` → (0, 0, −4 | 1, 1, −3).
`R₃ → −(1/4)R₃` → (0, 0, 1 | −1/4, −1/4, 3/4).
`R₂ + R₃` → (0, 1, 0 | −1/4, 3/4, −1/4).
`R₁ − R₃` → (1, 2, 0 | 1/4, 5/4, −3/4).
`R₁ − 2R₂` → (1, 0, 0 | 1/4 + 1/2, 5/4 − 3/2, −3/4 + 1/2) = (1, 0, 0 | 3/4, −1/4, −1/4).

> **A⁻¹ = (1/4)[[3, −1, −1], [−1, 3, −1], [−1, −1, 3]]**

**Verification via A = I + J.**
J has eigenvalues 3 and 0 (×2), so **A = I + J has eigenvalues 4 and 1 (×2)**.
A⁻¹ therefore has eigenvalues 1/4 and 1 (×2), and must itself be of the form **aI + bJ**:
- On (1,1,1): a + 3b = 1/4
- On Nul(J): a = 1

So 3b = 1/4 − 1 = −3/4 → **b = −1/4**.
**A⁻¹ = I − (1/4)J = (1/4)(4I − J) = (1/4)[[3,−1,−1],[−1,3,−1],[−1,−1,3]]** ✓ **matches exactly.**

*Check: A·A⁻¹ row 1 = (1/4)[2(3) + 1(−1) + 1(−1), 2(−1)+1(3)+1(−1), 2(−1)+1(−1)+1(3)] = (1/4)(4, 0, 0) = (1,0,0) ✓*

---

## Section C

**Q8(a).** A = [[2, 1], [1, 2], [0, 0]] (3×2).

**AᵀA:**
- (1,1): 4 + 1 + 0 = 5
- (1,2): 2 + 2 + 0 = 4
- (2,2): 1 + 4 + 0 = 5
```
AᵀA = [[5, 4], [4, 5]]
```
**Eigenvalues:** 5 ± 4 → **9 and 1** → **σ₁ = 3, σ₂ = 1.**

**Right singular vectors.**
λ=9: [[−4, 4],[4,−4]] → **v₁ = (1/√2)(1, 1)**
λ=1: [[4,4],[4,4]] → **v₂ = (1/√2)(1, −1)**

**Left singular vectors.**
Av₁ = (1/√2)(2+1, 1+2, 0) = (1/√2)(3, 3, 0). ‖·‖ = 3 ✓ = σ₁
**u₁ = (1/√2)(1, 1, 0)**
Av₂ = (1/√2)(2−1, 1−2, 0) = (1/√2)(1, −1, 0). ‖·‖ = 1 ✓ = σ₂
**u₂ = (1/√2)(1, −1, 0)**

Extend to ℝ³: **u₃ = (0, 0, 1)** (orthogonal to both ✓).

```
U = [[1/√2,  1/√2, 0],     Σ = [[3, 0],     V = (1/√2)[[1,  1],
     [1/√2, −1/√2, 0],          [0, 1],                [1, −1]]
     [0,     0,    1]]          [0, 0]]
```

*Check: ‖A‖_F² = 4+1+1+4 = 10 = 9 + 1 ✓*

**Q8(b).** **Pseudoinverse:** A⁺ = V_rΣ_r⁻¹U_rᵀ (r = 2, so A⁺ is 2×3).

A⁺ = (1/3)v₁u₁ᵀ + (1)v₂u₂ᵀ
Term 1: (1/3)(1/√2)(1,1)ᵀ(1/√2)(1,1,0) = (1/6)[[1,1,0],[1,1,0]]
Term 2: (1/√2)(1,−1)ᵀ(1/√2)(1,−1,0) = (1/2)[[1,−1,0],[−1,1,0]]

```
A⁺ = (1/6)[[1,1,0],[1,1,0]] + (1/6)[[3,−3,0],[−3,3,0]]
   = (1/6)[[ 4, −2, 0],
           [−2,  4, 0]]
   = (1/3)[[ 2, −1, 0],
           [−1,  2, 0]]
```

**Minimum-norm least squares solution for b = (1, 2, 3)ᵀ:**
x̂ = A⁺b = (1/3)(2(1) − 1(2) + 0, −1(1) + 2(2) + 0) = (1/3)(0, 3) = **(0, 1)ᵀ**

**Checks.**
- Ax̂ = (0 + 1, 0 + 2, 0) = **(1, 2, 0)**.
- Residual r = (1,2,3) − (1,2,0) = **(0, 0, 3)**, ‖r‖ = 3.
- Is r ⊥ Col(A)? Col(A) consists of vectors with third coordinate 0, and r = (0,0,3) ⊥ all such ✓
- The columns of A are independent (σ₂ = 1 ≠ 0), so this is the **unique** least squares solution.

*Cross-check via normal equations:* AᵀAx̂ = Aᵀb. Aᵀb = (2+2+0, 1+4+0) = (4, 5).
[[5,4],[4,5]]x = (4,5): 5x₁ + 4x₂ = 4; 4x₁ + 5x₂ = 5. Subtracting: x₁ − x₂ = −1. Adding: 9x₁ + 9x₂ = 9 → x₁ + x₂ = 1. So x₁ = 0, x₂ = 1 ✓

**Q9(a).** A = [[5, 2], [2, 2]].
p(λ) = λ² − 7λ + (10 − 4) = λ² − 7λ + 6 = (λ−6)(λ−1). **λ = 6, 1.**

λ=6: A − 6I = [[−1, 2], [2, −4]] → v₁ = 2v₂ → **(2, 1)**
λ=1: A − I = [[4, 2], [2, 1]] → 2v₁ = −v₂ → **(1, −2)**

Orthogonal ✓ *(as guaranteed for a symmetric matrix)*. Both have norm √5.

```
Q = (1/√5)[[2,  1],       D = [[6, 0],
           [1, −2]]            [0, 1]]
```
**A = QDQᵀ** ✓

**Classification:** both eigenvalues (6 and 1) are **positive** → the quadratic form is **positive definite**.
*Sylvester check: Δ₁ = 5 > 0, Δ₂ = 6 > 0 ✓*

**Q9(b).** With x = Qy, the conic becomes **6y₁² + y₂² = 6**, i.e.

> **y₁²/1 + y₂²/6 = 1**

**Both coefficients positive → an ELLIPSE.**

**Semi-axes:**
- Along **q₁ = (1/√5)(2, 1)**: semi-axis **a = √(6/6) = 1**
- Along **q₂ = (1/√5)(1, −2)**: semi-axis **b = √(6/1) = √6 ≈ 2.449**

So the **major axis** (length 2√6 ≈ 4.90) lies along the direction (1, −2), and the **minor axis** (length 2) along (2, 1).

**Principal axes:** the lines through the origin with directions (2, 1) and (1, −2) — i.e. y = x/2 and y = −2x.

*Verification.* The point √6·q₂ = (√6/√5)(1, −2) = (1.0954, −2.1909) should lie on the conic:
5(1.1999) + 4(1.0954)(−2.1909) + 2(4.7999) = 5.9995 − 9.5998 + 9.5998 = 6.00 ✓

*(Note the counterintuitive pairing: the **larger** eigenvalue 6 goes with the **shorter** semi-axis. Semi-axis length = √(c/λ), so bigger λ means a tighter constraint.)*

**Q10(a).** X = [[1, 2], [3, 3], [5, 6], [7, 9]].

**Means:** x̄₁ = (1+3+5+7)/4 = 4; x̄₂ = (2+3+6+9)/4 = 5. **x̄ = (4, 5).**

**Centred:**
```
X_c = [[−3, −3],
       [−1, −2],
       [ 1,  1],
       [ 3,  4]]
```

**X_cᵀX_c:**
- (1,1): 9 + 1 + 1 + 9 = 20
- (1,2): 9 + 2 + 1 + 12 = 24
- (2,2): 9 + 4 + 1 + 16 = 30
```
X_cᵀX_c = [[20, 24], [24, 30]]
```
> **S = (1/3)[[20, 24], [24, 30]] = [[6.667, 8.000], [8.000, 10.000]]**

**Q10(b).** Eigenvalues of [[20, 24], [24, 30]]:
p(λ) = λ² − 50λ + (600 − 576) = λ² − 50λ + 24.
λ = [50 ± √(2500 − 96)]/2 = [50 ± √2404]/2 = [50 ± 49.031]/2

**λ₁ = 49.515, λ₂ = 0.485** → S-eigenvalues **16.505 and 0.162**.

**q₁:** (20 − 49.515)v₁ + 24v₂ = 0 → −29.515v₁ + 24v₂ = 0 → v₁ = 0.8131v₂.
v = (0.8131, 1), ‖v‖ = √(0.6611 + 1) = 1.2889.
> **q₁ = (0.6309, 0.7759)**
> **q₂ = (−0.7759, 0.6309)**

**Explained variance ratios:**
- PC1: 49.515/50 = **99.03%**
- PC2: 0.485/50 = **0.97%**

*(Total = 50 = trace of X_cᵀX_c ✓)*

**Q10(c).** **Scores** Y = X_c q₁:
- row 1: (−3)(0.6309) + (−3)(0.7759) = −1.8927 − 2.3277 = **−4.220**
- row 2: (−1)(0.6309) + (−2)(0.7759) = −0.6309 − 1.5518 = **−2.183**
- row 3: (1)(0.6309) + (1)(0.7759) = **1.407**
- row 4: (3)(0.6309) + (4)(0.7759) = 1.8927 + 3.1036 = **4.996**

*Check: sum = −4.220 − 2.183 + 1.407 + 4.996 = 0.000 ✓*
*Check: Σy² = 17.81 + 4.77 + 1.98 + 24.96 = 49.52 ≈ λ₁ = 49.515 ✓*

**Reconstruction error** (sum of squares) = λ₂ = **0.485**
**Relative error** = √(0.485/50) = √0.0097 = **9.85%** in Frobenius norm
**RMS error per entry** = √(0.485/8) = **0.246**

**Interpretation.** Over 99% of the structure is captured by one direction. The data is essentially one-dimensional: the points lie close to the line through (4,5) with direction (0.631, 0.776), i.e. roughly **x₂ ≈ 1.23x₁ + 0.08**.

---

# MOCK PAPER II

**Time: 3 hours | Maximum marks: 70**

---

## Section A — Short Answer (10 × 2 = 20 marks)

**1(a)** State four equivalent conditions from the Invertible Matrix Theorem.

**1(b)** Find the rank of [[1, 2, 3], [4, 5, 6], [7, 8, 9]].

**1(c)** If A is 3×3 with eigenvalues 1, 2, 4, find tr(A²) and det(A + I).

**1(d)** Give the formula for the orthogonal projection of y onto a subspace W with orthonormal basis {u₁,...,u_p}.

**1(e)** Define the condition number and state its significance.

**1(f)** State the Cayley–Hamilton theorem and use it to express A⁻¹ for a 2×2 invertible A.

**1(g)** What is the geometric multiplicity of an eigenvalue, and what inequality relates it to the algebraic multiplicity?

**1(h)** State the Eckart–Young theorem.

**1(i)** For A = [[1, 2], [2, 4]], find Nul(A) and Col(A).

**1(j)** Define an orthogonal matrix and state two of its properties.

---

## Section B — Medium Answer (4 × 7.5 = 30 marks)

**2.** Determine all values of λ for which the system has (i) no solution, (ii) unique solution, (iii) infinitely many solutions:
```
x + y + z = 1
x + 2y + 4z = λ
x + 4y + 10z = λ²
```

**3.** Find the LU factorization of A = [[1, 2, 4], [3, 8, 14], [2, 6, 13]] and solve Ax = (3, 13, 4)ᵀ.

**4.** Let W = span{(1, 1, 0, 1), (0, 1, 1, 0)}. Find the orthogonal projection of y = (2, 3, 1, 4) onto W and the distance from y to W.

**5.** Prove that eigenvectors corresponding to distinct eigenvalues are linearly independent, and deduce that a matrix with n distinct eigenvalues is diagonalizable.

**6.** Compute the determinant of the n×n matrix with 2 on the diagonal, 1 on the super- and sub-diagonal, and 0 elsewhere, for n = 4. Then find a recursion for general n.

**7.** For A = [[4, 0, 1], [−2, 1, 0], [−2, 0, 1]], find all eigenvalues and determine whether A is diagonalizable.

---

## Section C — Long Answer (2 × 10 = 20 marks)

**8.** (a) Prove that a symmetric matrix has real eigenvalues and orthogonal eigenvectors for distinct eigenvalues. **(5)**
(b) Orthogonally diagonalize A = [[3, −2, 4], [−2, 6, 2], [4, 2, 3]] given that its eigenvalues are 7, 7, −2. **(5)**

**9.** (a) A rating matrix for 3 users and 3 items is R = [[4, 3, 1], [3, 3, 1], [1, 1, 4]]. Compute RᵀR and its eigenvalues, and determine the number of latent factors needed for 95% energy. **(6)**
(b) Explain how a rank-k matrix factorization predicts missing ratings, and state the ALS update formula. **(4)**

**10.** (a) Find the matrix of the linear transformation T : ℝ² → ℝ² that first reflects in the line y = x, then rotates by 90° counterclockwise. Identify the resulting transformation. **(4)**
(b) Prove that the composition of two reflections in lines through the origin is a rotation, and determine its angle in terms of the angles of the two lines. **(6)**

---

# SOLUTIONS — MOCK PAPER II

## Section A

**1(a)** For an n×n matrix A, any four of:
(i) A is invertible; (ii) A is row equivalent to Iₙ; (iii) A has n pivot positions; (iv) Ax = 0 has only the trivial solution; (v) the columns of A are linearly independent; (vi) Ax = b has a solution for every b; (vii) the columns span ℝⁿ; (viii) det A ≠ 0; (ix) rank A = n; (x) 0 is not an eigenvalue of A.

**1(b)** `R₂ − 4R₁`, `R₃ − 7R₁` → [[1,2,3],[0,−3,−6],[0,−6,−12]]. `R₃ − 2R₂` → zero row.
**rank = 2.**

**1(c)** Eigenvalues of A² are 1, 4, 16 → **tr(A²) = 21**.
Eigenvalues of A + I are 2, 3, 5 → **det(A + I) = 30**.

**1(d)** **proj_W(y) = (y·u₁)u₁ + (y·u₂)u₂ + ... + (y·u_p)u_p = UUᵀy**, where U = [u₁ ... u_p].
*(For a merely orthogonal — not normalized — basis, divide each term by uᵢ·uᵢ.)*

**1(e)** **κ(A) = σ_max/σ_min** (ratio of largest to smallest singular value; for invertible A, κ = ‖A‖‖A⁻¹‖).
**Significance:** it bounds the amplification of relative error, ‖Δx‖/‖x‖ ≤ κ(A)·‖Δb‖/‖b‖. A large κ means the problem is ill-conditioned and roughly log₁₀κ significant digits are lost when solving numerically.

**1(f)** **Cayley–Hamilton:** every square matrix satisfies its own characteristic equation, p(A) = 0.
For 2×2, p(λ) = λ² − (tr A)λ + det A, so A² − (tr A)A + (det A)I = 0. Rearranging:
A[(tr A)I − A] = (det A)I, hence
> **A⁻¹ = [(tr A)I − A]/det A**

**1(g)** **GM(λ) = dim Nul(A − λI) = n − rank(A − λI)** — the dimension of the eigenspace.
Relation: **1 ≤ GM(λ) ≤ AM(λ)**. A is diagonalizable ⟺ GM = AM for every eigenvalue.

**1(h)** **Eckart–Young.** If A has SVD Σσᵢuᵢvᵢᵀ and A_k = Σ_{i≤k}σᵢuᵢvᵢᵀ, then for every matrix B with rank(B) ≤ k:
> ‖A − B‖₂ ≥ ‖A − A_k‖₂ = **σ_{k+1}**, and ‖A − B‖_F ≥ ‖A − A_k‖_F = **√(σ_{k+1}² + ... + σ_r²)**.
So the truncated SVD is the **best rank-k approximation** in both norms.

**1(i)** Row 2 = 2 × row 1 → rank 1.
**Nul(A):** x₁ + 2x₂ = 0 → **span{(−2, 1)}**.
**Col(A):** **span{(1, 2)ᵀ}**.
*Check: 1 + 1 = 2 ✓*

**1(j)** A square matrix Q is **orthogonal** if **QᵀQ = I**, equivalently its columns form an orthonormal basis, equivalently **Q⁻¹ = Qᵀ**.
Two properties: (i) **‖Qx‖ = ‖x‖** for all x (preserves length, hence angles); (ii) **det Q = ±1** (and all eigenvalues have modulus 1).

---

## Section B

**Q2.** Augmented:
```
[[1, 1,  1 | 1  ],
 [1, 2,  4 | λ  ],
 [1, 4, 10 | λ² ]]
```
`R₂ − R₁`, `R₃ − R₁`:
```
[[1, 1, 1 | 1     ],
 [0, 1, 3 | λ−1   ],
 [0, 3, 9 | λ²−1  ]]
```
`R₃ − 3R₂`:
```
[[1, 1, 1 | 1                    ],
 [0, 1, 3 | λ−1                  ],
 [0, 0, 0 | λ²−1−3(λ−1)          ]]
```
Simplify: λ² − 1 − 3λ + 3 = **λ² − 3λ + 2 = (λ−1)(λ−2)**.

Last row reads **0 = (λ−1)(λ−2)**.

Note the coefficient matrix has **rank 2 always** (column 3 = 3×column 2 − 2×column 1 pattern; there are only 2 pivots). So:

- **(ii) Unique solution: NEVER** — there is always a free variable (z), so the system can never have a unique solution.
- **(i) No solution:** (λ−1)(λ−2) ≠ 0, i.e. **λ ∉ {1, 2}**.
- **(iii) Infinitely many:** **λ = 1 or λ = 2**.

*For λ = 1:* z free, y = −3z, x = 1 − y − z = 1 + 2z. **x = (1, 0, 0) + t(2, −3, 1).**
*For λ = 2:* y = 1 − 3z, x = 1 − (1−3z) − z = 2z. **x = (0, 1, 0) + t(2, −3, 1).**

**Q3.** Reduce A = [[1, 2, 4], [3, 8, 14], [2, 6, 13]], recording multipliers.

`R₂ − 3R₁` (mult 3), `R₃ − 2R₁` (mult 2):
```
[[1, 2, 4],
 [0, 2, 2],
 [0, 2, 5]]
```
`R₃ − 1·R₂` (mult 1):
```
U = [[1, 2, 4],
     [0, 2, 2],
     [0, 0, 3]]
```
```
L = [[1, 0, 0],
     [3, 1, 0],
     [2, 1, 1]]
```
*Verify row 3 of LU: 2(1,2,4) + 1(0,2,2) + 1(0,0,3) = (2, 6, 13) ✓*

**Solve Ly = (3, 13, 4)ᵀ** (forward):
- y₁ = 3
- 3(3) + y₂ = 13 → y₂ = 4
- 2(3) + 1(4) + y₃ = 4 → y₃ = 4 − 10 = −6

**Solve Ux = (3, 4, −6)ᵀ** (backward):
- 3x₃ = −6 → **x₃ = −2**
- 2x₂ + 2(−2) = 4 → 2x₂ = 8 → **x₂ = 4**
- x₁ + 2(4) + 4(−2) = 3 → x₁ + 8 − 8 = 3 → **x₁ = 3**

> **x = (3, 4, −2)ᵀ**

*Check in row 2 of A: 3(3) + 8(4) + 14(−2) = 9 + 32 − 28 = 13 ✓*

**Q4.** u₁ = (1,1,0,1), u₂ = (0,1,1,0).
**Check orthogonality:** u₁·u₂ = 0 + 1 + 0 + 0 = **1 ≠ 0** — NOT orthogonal. Gram–Schmidt first.

v₁ = (1,1,0,1), v₁·v₁ = 3.
v₂ = u₂ − (1/3)v₁ = (0,1,1,0) − (1/3, 1/3, 0, 1/3) = (−1/3, 2/3, 1, −1/3) → scale ×3: **v₂ = (−1, 2, 3, −1)**, v₂·v₂ = 1 + 4 + 9 + 1 = 15.
*Check: v₁·v₂ = −1 + 2 + 0 − 1 = 0 ✓*

**Project y = (2, 3, 1, 4):**
y·v₁ = 2 + 3 + 0 + 4 = 9 → coefficient 9/3 = 3
y·v₂ = −2 + 6 + 3 − 4 = 3 → coefficient 3/15 = 1/5

ŷ = 3(1,1,0,1) + (1/5)(−1,2,3,−1)
= (3, 3, 0, 3) + (−0.2, 0.4, 0.6, −0.2)
> **ŷ = (2.8, 3.4, 0.6, 2.8)**

**Residual** z = y − ŷ = (2 − 2.8, 3 − 3.4, 1 − 0.6, 4 − 2.8) = **(−0.8, −0.4, 0.4, 1.2)**

*Check z·v₁ = −0.8 − 0.4 + 0 + 1.2 = 0 ✓; z·v₂ = 0.8 − 0.8 + 1.2 − 1.2 = 0 ✓*

**Distance** = ‖z‖ = √(0.64 + 0.16 + 0.16 + 1.44) = √2.40 = **1.549**

**Q5.** **Theorem.** If v₁, ..., v_p are eigenvectors of A for **distinct** eigenvalues λ₁, ..., λ_p, then {v₁, ..., v_p} is linearly independent.

*Proof by contradiction.* Suppose the set is dependent. Since v₁ ≠ 0, {v₁} is independent, so there is a **smallest** index k with v_k ∈ span{v₁, ..., v_{k−1}} — and {v₁,...,v_{k−1}} is independent.

Write
> v_k = c₁v₁ + c₂v₂ + ... + c_{k−1}v_{k−1}  … (∗)

**Apply A:**
λ_k v_k = c₁λ₁v₁ + ... + c_{k−1}λ_{k−1}v_{k−1}  … (i)

**Multiply (∗) by λ_k:**
λ_k v_k = c₁λ_k v₁ + ... + c_{k−1}λ_k v_{k−1}  … (ii)

**Subtract (ii) from (i):**
0 = c₁(λ₁ − λ_k)v₁ + ... + c_{k−1}(λ_{k−1} − λ_k)v_{k−1}

Since {v₁, ..., v_{k−1}} is independent, **every coefficient is 0**:
cᵢ(λᵢ − λ_k) = 0 for each i < k.

But the eigenvalues are **distinct**, so λᵢ − λ_k ≠ 0, forcing **cᵢ = 0 for all i**.

Then (∗) gives **v_k = 0** — contradicting that an eigenvector is nonzero. ∎

**Corollary.** If an n×n matrix A has **n distinct eigenvalues**, it has n eigenvectors that are (by the theorem) linearly independent. n independent vectors in ℝⁿ form a **basis**, so ℝⁿ has an eigenbasis, and by the Diagonalization Theorem **A is diagonalizable** ✓ ∎

**Q6.** Let D_n be the determinant of the n×n tridiagonal matrix with 2 on the diagonal and 1 on both off-diagonals.

**n = 4:**
```
| 2 1 0 0 |
| 1 2 1 0 |
| 0 1 2 1 |
| 0 0 1 2 |
```
**Recursion.** Expand along the first row:
D_n = 2·D_{n−1} − 1·det(M)
where M is the matrix obtained by deleting row 1, column 2. M has a 1 in position (1,1) and zeros elsewhere in its first column, so expanding again gives det(M) = 1·D_{n−2}.

> **D_n = 2D_{n−1} − D_{n−2}**, with D₁ = 2, D₂ = 4 − 1 = 3

**Compute:**
- D₁ = 2
- D₂ = 3
- D₃ = 2(3) − 2 = **4**
- **D₄ = 2(4) − 3 = 5**

> **D₄ = 5**

**Closed form.** The recursion D_n = 2D_{n−1} − D_{n−2} has characteristic equation r² − 2r + 1 = (r−1)² = 0, a repeated root r = 1. So D_n = (a + bn)(1)ⁿ = a + bn.
From D₁ = 2 and D₂ = 3: a + b = 2, a + 2b = 3 → b = 1, a = 1.

> **D_n = n + 1**

*Check: D₄ = 5 ✓, D₃ = 4 ✓*

*(Cross-check via eigenvalues: the eigenvalues are 2 + 2cos(kπ/(n+1)), and Π(2 + 2cos(kπ/(n+1))) = n+1 — a classical identity.)*

**Q7.** A = [[4, 0, 1], [−2, 1, 0], [−2, 0, 1]].

**Characteristic polynomial.** Expand det(A − λI) along **column 2** (entries 0, 1−λ, 0):
det(A − λI) = (1−λ)·(−1)^{2+2}·det[[4−λ, 1], [−2, 1−λ]]
= (1−λ)[(4−λ)(1−λ) + 2]
= (1−λ)[4 − 5λ + λ² + 2]
= (1−λ)(λ² − 5λ + 6)
= **(1−λ)(λ−2)(λ−3)**

**Eigenvalues: 1, 2, 3** — all **distinct**.

**Therefore A is diagonalizable** (Corollary to Q5) ✓

*Check trace: 4 + 1 + 1 = 6 = 1 + 2 + 3 ✓; det A = 1(2)(3) = 6. Direct: expand along column 2: 1·det[[4,1],[−2,1]] = 1(4+2) = 6 ✓*

**Eigenvectors (for completeness).**
**λ=1:** A − I = [[3,0,1],[−2,0,0],[−2,0,0]]. From row 2: x₁ = 0. From row 1: x₃ = 0. x₂ free. → **(0, 1, 0)**
**λ=2:** A − 2I = [[2,0,1],[−2,−1,0],[−2,0,−1]]. From row 1: x₃ = −2x₁. From row 2: x₂ = −2x₁. → **(1, −2, −2)**
**λ=3:** A − 3I = [[1,0,1],[−2,−2,0],[−2,0,−2]]. Row 1: x₃ = −x₁. Row 2: x₂ = −x₁. → **(1, −1, −1)**

```
P = [[0,  1,  1],      D = diag(1, 2, 3)
     [1, −2, −1],
     [0, −2, −1]]
```

---

## Section C

**Q8(a).** **Claim 1: eigenvalues of a real symmetric A are real.**

Let Av = λv with v ≠ 0, allowing λ ∈ ℂ and v ∈ ℂⁿ. Take the conjugate transpose of both sides multiplied appropriately:

Consider the scalar **v*Av** (where v* = v̄ᵀ).
- On one hand: v*Av = v*(λv) = λ(v*v) = **λ‖v‖²**
- On the other: taking conjugate transpose of the 1×1 matrix v*Av gives
 (v*Av)* = v*A*v = v*Aᵀv = **v*Av** (using A real and symmetric, so A* = Aᵀ = A)

A 1×1 matrix equal to its own conjugate transpose is **real**. So λ‖v‖² is real, and since ‖v‖² > 0 is real and positive, **λ is real** ✓ ∎

**Claim 2: eigenvectors for distinct eigenvalues are orthogonal.**

Let Av₁ = λ₁v₁ and Av₂ = λ₂v₂ with λ₁ ≠ λ₂. Then
λ₁(v₁·v₂) = (Av₁)ᵀv₂ = v₁ᵀAᵀv₂ = v₁ᵀAv₂ *(A symmetric)*
= v₁ᵀ(λ₂v₂) = λ₂(v₁·v₂)

So **(λ₁ − λ₂)(v₁·v₂) = 0**, and since λ₁ ≠ λ₂, we conclude **v₁·v₂ = 0** ✓ ∎

**Q8(b).** A = [[3, −2, 4], [−2, 6, 2], [4, 2, 3]], eigenvalues 7, 7, −2.

**λ = −2:** A + 2I = [[5, −2, 4], [−2, 8, 2], [4, 2, 5]].
`5R₂ + 2R₁` → (0, 36, 18) → simplify (0, 2, 1).
So 2v₂ + v₃ = 0 → v₃ = −2v₂.
Row 1: 5v₁ − 2v₂ + 4(−2v₂) = 0 → 5v₁ = 10v₂ → v₁ = 2v₂.
Take v₂ = 1: **v = (2, 1, −2)**, ‖v‖ = 3.
> **q₃ = (1/3)(2, 1, −2)**

**λ = 7:** A − 7I = [[−4, −2, 4], [−2, −1, 2], [4, 2, −4]].
All rows are multiples of (2, 1, −2) → **rank 1 → GM = 2 ✓** (matches AM).
Solve **2v₁ + v₂ − 2v₃ = 0**.
Take (v₁, v₃) = (1, 0): v₂ = −2 → **u₁ = (1, −2, 0)**
Take (v₁, v₃) = (0, 1): v₂ = 2 → **u₂ = (0, 2, 1)**

These are **not orthogonal**: u₁·u₂ = 0 − 4 + 0 = −4. **Apply Gram–Schmidt.**
w₁ = (1, −2, 0), w₁·w₁ = 5.
w₂ = (0,2,1) − (−4/5)(1,−2,0) = (0,2,1) + (4/5, −8/5, 0) = (4/5, 2/5, 1) → ×5: **w₂ = (4, 2, 5)**
*Check: (1,−2,0)·(4,2,5) = 4 − 4 + 0 = 0 ✓*

Norms: ‖w₁‖ = √5, ‖w₂‖ = √(16+4+25) = √45 = 3√5.

> **q₁ = (1/√5)(1, −2, 0), q₂ = (1/(3√5))(4, 2, 5)**

*Cross-checks:* q₃·q₁: (2,1,−2)·(1,−2,0) = 2 − 2 + 0 = 0 ✓
q₃·q₂: (2,1,−2)·(4,2,5) = 8 + 2 − 10 = 0 ✓

```
Q = [[ 1/√5,   4/(3√5),   2/3],
     [−2/√5,   2/(3√5),   1/3],
     [ 0,      5/(3√5),  −2/3]]

D = diag(7, 7, −2)
```
> **A = QDQᵀ** ✓

*Verification of the eigenvalues: trace A = 3 + 6 + 3 = 12 = 7 + 7 − 2 ✓; det A = 7(7)(−2) = −98.*

**Q9(a).** R = [[4, 3, 1], [3, 3, 1], [1, 1, 4]].

**RᵀR:**
- (1,1): 16 + 9 + 1 = 26
- (1,2): 12 + 9 + 1 = 22
- (1,3): 4 + 3 + 4 = 11
- (2,2): 9 + 9 + 1 = 19
- (2,3): 3 + 3 + 4 = 10
- (3,3): 1 + 1 + 16 = 18
```
RᵀR = [[26, 22, 11],
       [22, 19, 10],
       [11, 10, 18]]
```
**trace = 63** = ‖R‖_F²
*Check: 16+9+1+9+9+1+1+1+16 = 63 ✓*

**Eigenvalues.** The characteristic polynomial is λ³ − 63λ² + cλ − d. Computing the needed invariants:
- Sum of principal 2×2 minors:
 (26·19 − 484) + (26·18 − 121) + (19·18 − 100) = (494 − 484) + (468 − 121) + (342 − 100) = 10 + 347 + 242 = **599**
- det(RᵀR) = (det R)². Compute det R:
 det R = 4(12 − 1) − 3(12 − 1) + 1(3 − 3) = 44 − 33 + 0 = **11**
 So det(RᵀR) = 121.

**p(λ) = λ³ − 63λ² + 599λ − 121**

Numerically, the roots are approximately

> **λ₁ ≈ 52.63, λ₂ ≈ 10.16, λ₃ ≈ 0.21**

*(Check: sum ≈ 63.0 ✓; product ≈ 52.63 × 10.16 × 0.21 ≈ 112 ≈ 121 within rounding ✓)*

**Singular values:** σ₁ ≈ 7.255, σ₂ ≈ 3.188, σ₃ ≈ 0.458.

**Energy fractions:**
| k | cumulative | ratio |
|---|---|---|
| 1 | 52.63 | 83.5% |
| 2 | 62.79 | **99.7%** ✓ |
| 3 | 63.0 | 100% |

> **Two latent factors** capture 99.7% ≥ 95%.

**Interpretation.** Users 1 and 2 have nearly identical taste profiles (rows (4,3,1) and (3,3,1)) and both dislike item 3; user 3 has the opposite pattern. This is a **two-group structure**, which is exactly what the two dominant factors encode. The tiny third eigenvalue (0.3% of energy) is individual noise.

**Q9(b).** **How rank-k factorization predicts missing ratings.**

Model the rating matrix as **R ≈ PQᵀ**, where P is m×k (one row pᵤ per user) and Q is n×k (one row qᵢ per item). Each row is a vector of **latent factor** loadings — hidden dimensions such as "amount of action", "how mainstream", "how recent" — discovered from the data rather than specified in advance.

The predicted rating is the inner product

> **r̂ᵤᵢ = pᵤ · qᵢ**

Because k ≪ min(m, n), the model has far fewer parameters than the matrix has entries, so fitting it to the **observed** ratings forces it to find genuine structure rather than memorize. Once P and Q are fitted, **every** entry — including the unobserved ones — can be computed, which is the prediction.

The objective minimizes squared error over observed entries only, with ridge regularization:

> **min_{P,Q} Σ_{(u,i) ∈ Ω} (rᵤᵢ − pᵤ·qᵢ)² + λ(‖P‖_F² + ‖Q‖_F²)**

**ALS update formulas.** The joint problem is non-convex, but fixing one factor makes the other a **convex least squares problem** with a closed form. Alternating:

> **Fix Q, update each user:**
> **pᵤ = (Σ_{i ∈ Ωᵤ} qᵢqᵢᵀ + λI_k)⁻¹ (Σ_{i ∈ Ωᵤ} rᵤᵢqᵢ)**
>
> **Fix P, update each item:**
> **qᵢ = (Σ_{u ∈ Ωᵢ} pᵤpᵤᵀ + λI_k)⁻¹ (Σ_{u ∈ Ωᵢ} rᵤᵢpᵤ)**

where Ωᵤ is the set of items user u rated and Ωᵢ the set of users who rated item i. Each update is exactly the **ridge regression normal equation** (P6.20), and the λI_k term guarantees invertibility even for users with fewer than k ratings.

*(For k = 1 this reduces to pᵤ = Σrᵤᵢqᵢ/(Σqᵢ² + λ), as in Example 14.5.)*

**Q10(a).** Reflection in y = x: **F = [[0, 1], [1, 0]]**
Rotation by 90°: **R = [[0, −1], [1, 0]]**

"First reflect, then rotate" → the matrix is **RF** (rightmost acts first):
```
RF = [[0, −1], [1, 0]]·[[0, 1], [1, 0]]
```
- Row 1: (0, −1)·col1 = (0)(0) + (−1)(1) = −1; (0,−1)·col2 = 0 + 0 = 0
- Row 2: (1, 0)·col1 = 0; (1,0)·col2 = 1

> **RF = [[−1, 0], [0, 1]]**

**Identification.** This is the **reflection in the y-axis**.

*Verification:* det(RF) = −1 ✓ (orientation-reversing, so it is a reflection, not a rotation). Its fixed direction: (RF)(0,1)ᵀ = (0,1) ✓ the y-axis is fixed; (RF)(1,0)ᵀ = (−1,0) ✓ the x-axis is flipped.

*(Sanity check by tracking a point: (1,0) → reflect in y=x → (0,1) → rotate 90° → (−1, 0). And reflecting (1,0) in the y-axis gives (−1,0) ✓)*

**Q10(b).** **Claim.** The composition of two reflections in lines through the origin, at angles α and β to the x-axis, is a **rotation by 2(β − α)**.

**Proof.** The reflection in the line at angle θ has matrix

> **F_θ = [[cos 2θ, sin 2θ], [sin 2θ, −cos 2θ]]**

*(Derivation: rotate by −θ to bring the line to the x-axis, reflect in the x-axis, rotate back:
F_θ = R_θ · [[1,0],[0,−1]] · R_{−θ}, which multiplies out to the form above.)*

Compute the composition **F_β F_α** (reflect in the α-line first, then in the β-line):

```
F_β F_α = [[cos 2β,  sin 2β], · [[cos 2α,  sin 2α],
           [sin 2β, −cos 2β]]     [sin 2α, −cos 2α]]
```

- **(1,1):** cos2β cos2α + sin2β sin2α = **cos(2β − 2α)**
- **(1,2):** cos2β sin2α − sin2β cos2α = −(sin2β cos2α − cos2β sin2α) = **−sin(2β − 2α)**
- **(2,1):** sin2β cos2α − cos2β sin2α = **sin(2β − 2α)**
- **(2,2):** sin2β sin2α + cos2β cos2α = **cos(2β − 2α)**

```
F_β F_α = [[cos(2β−2α), −sin(2β−2α)],
           [sin(2β−2α),  cos(2β−2α)]]
```

This is exactly the **rotation matrix R_{2(β−α)}** ✓ ∎

> **The composition is a rotation by angle 2(β − α) — twice the angle between the two lines.**

**Consistency checks.**
- **Determinant:** det(F_βF_α) = (−1)(−1) = **+1** ✓ — a rotation, as required (each reflection reverses orientation; two reversals restore it).
- **Part (a):** there α = 45° (the line y = x) and the second map was a rotation, not a reflection — so instead verify the reverse: our answer RF was the reflection in the y-axis, i.e. F_{90°}. Indeed F_{90°}F_{45°} should be a rotation by 2(90 − 45) = 90° ✓ — consistent with R = F_{90°}F_{45°}, i.e. F_{90°} = R F_{45°}⁻¹ = R F_{45°} ✓ **exactly what part (a) computed.**
- **Special case α = β:** rotation by 0 = identity ✓ (reflecting twice in the same line returns you to the start).
- **Special case β − α = 90°:** rotation by 180° = −I ✓ (reflections in perpendicular lines compose to a point reflection).

*(This result generalizes: in 3D, the composition of two reflections in planes through the origin is a rotation about their line of intersection, by twice the dihedral angle — the foundation of the theory of reflection groups and of how rotations are represented in graphics as pairs of reflections.)*

---

# MOCK PAPER III — Rapid Revision Paper

**Time: 90 minutes | Maximum marks: 40**
*A condensed paper for the night before. All questions compulsory.*

---

**1.** (2 marks each, 10 total)
(a) Find the rank of [[2, 4], [3, 6]].
(b) If A is 4×4 with det A = 5, find det(adj A).
(c) State when a matrix is orthogonally diagonalizable.
(d) Find the eigenvalues of [[0, 2], [2, 0]].
(e) Give the formula for the pseudoinverse of a full-column-rank A.

**2.** (5 marks) Solve by Gaussian elimination and state the solution type:
`2x + y − z = 3`, `x − y + 2z = 1`, `3x + 3y − 4z = 7`.

**3.** (5 marks) Diagonalize A = [[2, 1], [1, 2]] and compute A⁶.

**4.** (5 marks) Find the least squares line through (0, 1), (1, 2), (2, 2), (3, 4) and state R².

**5.** (5 marks) Orthogonally diagonalize A = [[1, 3], [3, 1]] and classify the quadratic form x₁² + 6x₁x₂ + x₂².

**6.** (5 marks) Find the SVD of A = [[3, 0], [0, 0], [0, −2]] and state its rank, ‖A‖₂ and ‖A‖_F.

**7.** (5 marks) Let T : ℝ³ → ℝ³ be T(x) = Ax with A = [[1, 1, 1], [1, 1, 1], [1, 1, 1]]. Find ker(T), range(T), rank, nullity, and verify rank–nullity.

---

# SOLUTIONS — MOCK PAPER III

**1(a)** Row 2 = 1.5 × Row 1 → **rank 1**.

**1(b)** det(adj A) = (det A)^{n−1} = 5³ = **125**.

**1(c)** A is orthogonally diagonalizable (A = QDQᵀ with Q orthogonal, D diagonal) **⟺ A is symmetric** (Spectral Theorem).

**1(d)** p(λ) = λ² − 4 → **λ = 2, −2**.

**1(e)** **A⁺ = (AᵀA)⁻¹Aᵀ** (valid when the columns of A are linearly independent).

**2.** Augmented:
```
[[2,  1, −1 | 3],
 [1, −1,  2 | 1],
 [3,  3, −4 | 7]]
```
Swap R₁ ↔ R₂:
```
[[1, −1,  2 | 1],
 [2,  1, −1 | 3],
 [3,  3, −4 | 7]]
```
`R₂ − 2R₁`, `R₃ − 3R₁`:
```
[[1, −1,  2 |  1],
 [0,  3, −5 |  1],
 [0,  6, −10|  4]]
```
`R₃ − 2R₂` → (0, 0, 0 | 4 − 2 = **2**).

Last row reads **0 = 2** — false.

> **The system is INCONSISTENT — no solution.**

*(Geometrically: three planes with no common point. Note rows: eq3 = eq1 + eq2 would require 7 = 3 + 1 = 4, but 7 ≠ 4 — the coefficient rows are dependent while the constants are not.)*

**3.** p(λ) = (2−λ)² − 1 = λ² − 4λ + 3 = (λ−3)(λ−1). **λ = 3, 1.**
λ=3: A − 3I = [[−1, 1],[1,−1]] → **(1, 1)**
λ=1: A − I = [[1,1],[1,1]] → **(1, −1)**

```
P = [[1, 1], [1, −1]], D = diag(3, 1), P⁻¹ = (1/2)[[1, 1], [1, −1]]
```
*(P⁻¹ = P/2 since P² = 2I.)*

**A⁶ = P diag(3⁶, 1) P⁻¹ = P diag(729, 1) P⁻¹.**
P·diag(729, 1) = [[729, 1], [729, −1]].
Times (1/2)[[1,1],[1,−1]]:
- (1,1): (729 + 1)/2 = **365**
- (1,2): (729 − 1)/2 = **364**
- (2,1): (729 − 1)/2 = **364**
- (2,2): (729 + 1)/2 = **365**

> **A⁶ = [[365, 364], [364, 365]]**

*Check trace: 730 = 729 + 1 ✓; det = 365² − 364² = (365−364)(365+364) = 729 = 3⁶ · 1⁶ ✓*

**4.** m = 4, Σx = 6, Σy = 9, Σxy = 0 + 2 + 4 + 12 = 18, Σx² = 0 + 1 + 4 + 9 = 14.

β₁ = (4(18) − 6(9))/(4(14) − 36) = (72 − 54)/(56 − 36) = 18/20 = **0.9**
β₀ = (9 − 0.9(6))/4 = (9 − 5.4)/4 = **0.9**

> **y = 0.9 + 0.9x**

**Fitted:** 0.9, 1.8, 2.7, 3.6. **Residuals:** 0.1, 0.2, −0.7, 0.4 *(sum = 0 ✓)*
**SSE** = 0.01 + 0.04 + 0.49 + 0.16 = **0.70**
ȳ = 2.25. **SST** = (1.25)² + (0.25)² + (0.25)² + (1.75)² = 1.5625 + 0.0625 + 0.0625 + 3.0625 = **4.75**

> **R² = 1 − 0.70/4.75 = 0.8526**

**5.** A = [[1, 3], [3, 1]]. p(λ) = (1−λ)² − 9 = λ² − 2λ − 8 = (λ−4)(λ+2). **λ = 4, −2.**

λ=4: A − 4I = [[−3, 3],[3,−3]] → **(1, 1)**
λ=−2: A + 2I = [[3,3],[3,3]] → **(1, −1)**
Orthogonal ✓, both of norm √2.

```
Q = (1/√2)[[1,  1],       D = [[4,  0],
           [1, −1]]            [0, −2]]
```
> **A = QDQᵀ** ✓

**Classification:** eigenvalues 4 > 0 and −2 < 0 — **mixed signs** → the quadratic form is **INDEFINITE**.

*Confirmation by completing the square:*
x₁² + 6x₁x₂ + x₂² = (x₁ + 3x₂)² − 9x₂² + x₂² = **(x₁ + 3x₂)² − 8x₂²** — one positive square and one negative ✓
*(Inertia (1, 1, 0). The level set x₁² + 6x₁x₂ + x₂² = c is a **hyperbola**.)*

**6.** A = [[3, 0], [0, 0], [0, −2]] (3×2).

**AᵀA** = [[9, 0], [0, 4]]. Eigenvalues **9 and 4** → **σ₁ = 3, σ₂ = 2.**

**v₁ = (1, 0), v₂ = (0, 1)** → **V = I₂**

Av₁ = (3, 0, 0), ‖·‖ = 3 ✓ → **u₁ = (1, 0, 0)**
Av₂ = (0, 0, −2), ‖·‖ = 2 ✓ → **u₂ = (0, 0, −1)**
Extend: **u₃ = (0, 1, 0)** (orthogonal to both ✓)

```
U = [[1, 0, 0],      Σ = [[3, 0],      V = [[1, 0],
     [0, 0, 1],           [0, 2],           [0, 1]]
     [0, −1, 0]]          [0, 0]]
```
*Verify UΣVᵀ: column 1 = 3u₁ = (3,0,0) ✓; column 2 = 2u₂ = (0, 0, −2) ✓*

> **rank(A) = 2** (two nonzero singular values)
> **‖A‖₂ = σ₁ = 3**
> **‖A‖_F = √(9 + 4) = √13 ≈ 3.606**

*Check ‖A‖_F directly from the entries: √(9 + 0 + 0 + 0 + 0 + 4) = √13 ✓*

**7.** A = J (the 3×3 all-ones matrix). All rows identical → **rank(A) = 1**.

**range(T) = Col(A) = span{(1, 1, 1)ᵀ}**, dimension **1** — a line in ℝ³.

**ker(T) = Nul(A):** Ax = 0 reduces to the single equation **x₁ + x₂ + x₃ = 0**. Free: x₂, x₃.
> **Basis: {(−1, 1, 0), (−1, 0, 1)}**, **nullity = 2** — a plane through the origin.

**Rank–nullity:** rank + nullity = 1 + 2 = **3** = dim ℝ³ ✓

**Additional observations.**
- T is **neither one-to-one** (nullity ≠ 0) **nor onto** (rank 1 < 3).
- Note **ker(T) ⊥ range(T)**: (1,1,1)·(−1,1,0) = 0 ✓ and (1,1,1)·(−1,0,1) = 0 ✓ — expected, since A is symmetric, so Nul(A) = (Row A)⊥ = (Col A)⊥.
- Eigenvalues: **3** (eigenvector (1,1,1)) and **0** (multiplicity 2, eigenspace = ker T). A is diagonalizable ✓

---

## 16.4 Examination Strategy

**Before you start writing:**
1. Read the whole paper. Mark the questions you can definitely do.
2. Do those first. Momentum and secured marks matter more than order.
3. Budget time by marks: at 70 marks in 180 minutes, that is about **2.5 minutes per mark**.

**During:**
- **Always state the method** before computing. Partial marks are given for the right approach even with arithmetic slips.
- **Check as you go.** Trace = sum of eigenvalues; det = product; residuals sum to zero; Av = λv; P⁻¹AP = D. These checks cost seconds and catch most errors.
- If a determinant or inverse comes out ugly, **re-check the arithmetic** — exam problems are usually designed to be clean.
- For "determine whether" questions, **state the criterion first**, then verify it. This alone often earns half the marks.

**Common places marks are lost:**
- Using the reduced columns instead of the **original** columns for a basis of Col(A).
- Forgetting det(cA) = cⁿ det A.
- Forgetting (AB)ᵀ = BᵀAᵀ and (AB)⁻¹ = B⁻¹A⁻¹ — the **order reverses**.
- Not applying Gram–Schmidt **within** a repeated eigenspace when orthogonally diagonalizing.
- Forgetting to **centre** the data before PCA.
- Confusing eigenvalues with singular values (singular values are never negative).
- Not checking whether the given spanning vectors are already orthogonal before projecting.

---
# APPENDICES

---

# Appendix A — Master Formula Sheet

*Everything worth memorizing, in two pages.*

---

## A.1 Systems and Row Reduction

**Solution types:** exactly one of — no solution, unique solution, infinitely many. Never two, never seventeen.

**Consistent** ⟺ no row `[0 ... 0 | c]` with c ≠ 0 ⟺ rightmost column is not a pivot column.
**Unique** ⟺ consistent and **no free variables** ⟺ pivot in every column.
**Infinitely many** ⟺ consistent and at least one free variable.

**Number of free variables** = n − rank(A).

**Structure of solutions:** if `Ax = b` is consistent with particular solution p, the full set is **{p + h : Ah = 0}**.

---

## A.2 Matrix Algebra

| Rule | Statement |
|---|---|
| Transpose of product | **(AB)ᵀ = BᵀAᵀ** |
| Inverse of product | **(AB)⁻¹ = B⁻¹A⁻¹** |
| 2×2 inverse | A⁻¹ = (1/(ad−bc))[[d, −b], [−c, a]] |
| Inverse via adjugate | **A⁻¹ = (1/det A)·adj A** |
| Ax as combination | **Ax = x₁a₁ + x₂a₂ + ... + xₙaₙ** |
| Symmetric split | A = ½(A + Aᵀ) + ½(A − Aᵀ) |
| Nilpotent inverse | (I − N)⁻¹ = I + N + ... + N^{k−1} if N^k = 0 |
| Block triangular inverse | [[A,B],[0,C]]⁻¹ = [[A⁻¹, −A⁻¹BC⁻¹],[0, C⁻¹]] |

**Fails in general:** AB ≠ BA; AB = AC ⇏ B = C; AB = 0 ⇏ A = 0 or B = 0.

**LU:** A = LU, L unit lower triangular (entries = multipliers used), U echelon. Solve Ly = b then Ux = y.

---

## A.3 The Invertible Matrix Theorem (square A only)

All equivalent: A invertible · A ~ I · n pivots · Ax = 0 only trivially · columns independent · columns span ℝⁿ · Ax = b solvable for all b · x ↦ Ax bijective · CA = I for some C · AD = I for some D · Aᵀ invertible · **det A ≠ 0** · rank A = n · Nul A = {0} · **0 is not an eigenvalue** · columns form a basis of ℝⁿ.

---

## A.4 Vector Spaces

**Subspace test:** contains 0; closed under addition; closed under scalar multiplication.

**Four fundamental subspaces** (A is m×n, rank r):

| Subspace | Lives in | Dimension | Orthogonal to |
|---|---|---|---|
| Col(A) | ℝᵐ | r | Nul(Aᵀ) |
| Nul(A) | ℝⁿ | n − r | Row(A) |
| Row(A) | ℝⁿ | r | Nul(A) |
| Nul(Aᵀ) | ℝᵐ | m − r | Col(A) |

> **RANK–NULLITY: rank(A) + nullity(A) = n** (number of **columns**)

**Basis for Col(A):** the **ORIGINAL** pivot columns of A (never the reduced ones).
**Basis for Row(A):** the nonzero rows of the RREF.
**Basis for Nul(A):** one vector per free variable, from the parametric form.

**Basis Theorem:** in a p-dimensional space, any p independent vectors form a basis; so do any p spanning vectors.

**Dimension formula:** dim(U + W) = dim U + dim W − dim(U ∩ W).

**Standard dimensions:** dim ℝⁿ = n; dim Pₙ = n+1; dim M_{m×n} = mn; dim{n×n symmetric} = n(n+1)/2.

---

## A.5 Orthogonality

‖v‖ = √(v·v) · dist(u,v) = ‖u−v‖ · cos θ = (u·v)/(‖u‖‖v‖)

**Cauchy–Schwarz:** |u·v| ≤ ‖u‖‖v‖  **Pythagoras:** u ⊥ v ⟺ ‖u+v‖² = ‖u‖² + ‖v‖²

**Projection onto a vector:** proj_u(y) = ((y·u)/(u·u))u

**Projection onto a subspace** (orthogonal basis {uᵢ}): **proj_W(y) = Σᵢ ((y·uᵢ)/(uᵢ·uᵢ))uᵢ**

**Projection matrices:**
- orthonormal basis in U: **P = UUᵀ**
- any independent basis in A: **P = A(AᵀA)⁻¹Aᵀ**
- properties: **P² = P, Pᵀ = P**, rank P = tr P = dim W, and I − P projects onto W⊥

**Best Approximation:** proj_W(y) is the **closest** point of W to y.

**Gram–Schmidt:** v_k = x_k − Σ_{j<k} ((x_k·v_j)/(v_j·v_j))v_j *(rescale freely to clear fractions)*

**QR:** A = QR, Q from Gram–Schmidt, **R = QᵀA** (upper triangular automatically).

**Orthogonal matrix Q:** QᵀQ = I, Q⁻¹ = Qᵀ, ‖Qx‖ = ‖x‖, det Q = ±1.

**dim W + dim W⊥ = n**, **(Row A)⊥ = Nul A**, **(Col A)⊥ = Nul Aᵀ**.

---

## A.6 Least Squares

> **NORMAL EQUATIONS: AᵀAx̂ = Aᵀb**

Unique ⟺ columns of A independent ⟺ AᵀA invertible, then **x̂ = (AᵀA)⁻¹Aᵀb**.

**Via QR:** solve **Rx̂ = Qᵀb** by back-substitution (numerically preferred).

**Least squares line** y = β₀ + β₁x:
> **β₁ = (mΣxy − ΣxΣy)/(mΣx² − (Σx)²) = S_xy/S_xx**
> **β₀ = ȳ − β₁x̄**

**Goodness of fit:** SST = SSR + SSE, **R² = 1 − SSE/SST**

**Weighted:** AᵀWAx̂ = AᵀWb   **Ridge:** **(AᵀA + λI)x̂ = Aᵀb** (always invertible for λ > 0)

**Residual** r = b − Ax̂ satisfies **Aᵀr = 0** (r ⊥ Col A).

---

## A.7 Determinants

| Operation | Effect on det |
|---|---|
| Rᵢ → Rᵢ + cRⱼ | **unchanged** |
| Rᵢ ↔ Rⱼ | **×(−1)** |
| Rᵢ → cRᵢ | **×c** |

**det(AB) = det A · det B** · **det(Aᵀ) = det A** · **det(cA) = cⁿ det A** · **det(A⁻¹) = 1/det A** · **det(Aᵏ) = (det A)ᵏ** · **det(adj A) = (det A)^{n−1}**

**NOT additive:** det(A + B) ≠ det A + det B.

**Triangular:** det = product of diagonal entries.
**Zero if:** a zero row/column, or two proportional rows/columns.

**2×2:** ad − bc. **3×3:** Sarrus (3×3 only!).

**Cramer:** xᵢ = det(Aᵢ(b))/det(A).

**Geometric:** |det A| = area/volume scaling factor. **Vandermonde:** Π_{i<j}(xⱼ − xᵢ).

**Block:** det[[A, B],[0, D]] = det(A)det(D). **General:** det[[A,B],[C,D]] = det(A)·det(D − CA⁻¹B).

**Rank:** = number of pivots = dim Col = dim Row = size of the largest nonzero minor = number of nonzero singular values.

**rank(AB) ≤ min(rank A, rank B)** · **Sylvester:** rank A + rank B − n ≤ rank(AB) · rank(A) = rank(Aᵀ) = rank(AᵀA)

---

## A.8 Eigenvalues

> **Av = λv, v ≠ 0** ⟺ **det(A − λI) = 0** · **E_λ = Nul(A − λI)**

**Σλᵢ = tr(A)** · **Πλᵢ = det(A)** · triangular ⟹ eigenvalues are the diagonal entries

| Matrix | Eigenvalues | Eigenvectors |
|---|---|---|
| Aᵏ | λᵏ | same |
| A⁻¹ | 1/λ | same |
| A + cI | λ + c | same |
| cA | cλ | same |
| q(A) | q(λ) | same |
| Aᵀ | same λ | **different** |

**1 ≤ GM(λ) ≤ AM(λ)** · defective ⟺ GM < AM for some λ

**Eigenvectors for distinct eigenvalues are independent.** n distinct eigenvalues ⟹ diagonalizable.

**Cayley–Hamilton:** p(A) = 0. For 2×2: **A² = (tr A)A − (det A)I**.

**All-ones matrix J (n×n):** eigenvalues **n** (eigenvector 1) and **0** (multiplicity n−1, eigenspace {Σxᵢ = 0}).

**Gershgorin:** every eigenvalue lies in some disc |z − aᵢᵢ| ≤ Σ_{j≠i}|aᵢⱼ|.

**Tridiagonal Toeplitz** (a on diagonal, b and c off): λ_k = a + 2√(bc)·cos(kπ/(n+1)).

---

## A.9 Diagonalization

> **A = PDP⁻¹**, columns of P = eigenvectors, diagonal of D = matching eigenvalues

**Diagonalizable ⟺ n independent eigenvectors ⟺ GM(λ) = AM(λ) for all λ ⟺ minimal polynomial has distinct roots.**

**Aᵏ = PDᵏP⁻¹** · **f(A) = P f(D) P⁻¹**

**Dynamics x_{k+1} = Ax_k:** x_k = Σcᵢλᵢᵏvᵢ. Behaviour governed by max|λᵢ|:
all |λ| < 1 → 0 · all |λ| > 1 → ∞ · mixed → saddle · max|λ| = 1 → steady state

**ODEs x′ = Ax:** x(t) = Σcᵢe^{λᵢt}vᵢ

**Similar matrices** (B = P⁻¹AP) share: char. poly, eigenvalues, AM, GM, trace, det, rank, diagonalizability. They do **not** share eigenvectors or entries.

---

## A.10 Symmetric and Positive Definite

> **SPECTRAL THEOREM: A symmetric ⟺ A = QDQᵀ with Q orthogonal**

Consequences: eigenvalues **real**; eigenvectors for distinct eigenvalues **orthogonal**; **never defective**.

**Spectral decomposition:** A = Σλᵢqᵢqᵢᵀ

**Procedure:** find eigenspaces → **Gram–Schmidt WITHIN each repeated eigenspace** → normalize → assemble Q.

**Quadratic form** Q(x) = xᵀAx. Coefficient of xᵢxⱼ is **split in half** between (i,j) and (j,i).

| Type | Eigenvalues | Sylvester (leading principal minors) |
|---|---|---|
| Positive definite | all > 0 | all Δ_k > 0 |
| Negative definite | all < 0 | signs alternate: Δ₁<0, Δ₂>0, … |
| Indefinite | mixed signs | — |

**Also positive definite ⟺** A = BᵀB (B full column rank) ⟺ **A = LLᵀ** (Cholesky) ⟺ all pivots positive.

**AᵀA is always PSD**; positive definite ⟺ columns of A independent.

**Principal Axes:** x = Qy turns xᵀAx into λ₁y₁² + ... + λₙyₙ² (no cross terms).

**Rayleigh quotient:** **λₙ ≤ (xᵀAx)/(xᵀx) ≤ λ₁**, max at q₁, min at qₙ.

**Sylvester's Law of Inertia:** congruent symmetric matrices (B = PᵀAP) have the same numbers of positive, negative, and zero eigenvalues.

---

## A.11 Linear Transformations

**Linear:** T(u+v) = T(u) + T(v) and T(cu) = cT(u). **Quick test: T(0) must be 0.**

**Standard matrix:** **A = [T(e₁) T(e₂) ... T(eₙ)]**

**ker(T) = Nul(A)** · **range(T) = Col(A)** · **rank + nullity = dim(domain)**

**One-to-one ⟺ ker = {0} ⟺ pivot in every column**
**Onto ⟺ rank = m ⟺ pivot in every row**
**If dim V = dim W: one-to-one ⟺ onto ⟺ isomorphism**

**Change of basis:** [x]_C = P_{C←B}[x]_B, **P_{C←B} = P_C⁻¹P_B**, and **[T]_C = P[T]_BP⁻¹**.

**ℝ² geometry:**
rotation θ: [[cos θ, −sin θ],[sin θ, cos θ]] · reflection in line at angle θ: [[cos 2θ, sin 2θ],[sin 2θ, −cos 2θ]] · shear: [[1,k],[0,1]] · projection onto unit u: uuᵀ

**Homogeneous coordinates** (2D): translation by (t₁,t₂) = [[1,0,t₁],[0,1,t₂],[0,0,1]].

---

## A.12 SVD and Factorizations

> **A = UΣVᵀ** — exists for **every** matrix

**Construction:** V and σᵢ² from eigen-decomposition of **AᵀA**; **σᵢ = √λᵢ**; **uᵢ = Avᵢ/σᵢ**; extend U to an orthonormal basis.

**Avᵢ = σᵢuᵢ** · **Aᵀuᵢ = σᵢvᵢ** · rank(A) = number of nonzero σᵢ

**Four subspaces from SVD:** Col(A) = span{u₁..u_r}; Nul(Aᵀ) = span{u_{r+1}..u_m}; Row(A) = span{v₁..v_r}; Nul(A) = span{v_{r+1}..vₙ}

**Outer form:** A = Σσᵢuᵢvᵢᵀ. **Truncation** A_k = Σ_{i≤k}σᵢuᵢvᵢᵀ.

> **ECKART–YOUNG:** A_k is the best rank-k approximation.
> ‖A − A_k‖₂ = **σ_{k+1}** · ‖A − A_k‖_F = **√(σ_{k+1}² + ... + σ_r²)**

**Norms:** ‖A‖₂ = **σ₁** · ‖A‖_F = **√(Σσᵢ²)** = √(Σaᵢⱼ²)

**Pseudoinverse:** **A⁺ = VΣ⁻¹Uᵀ = Σ(1/σᵢ)vᵢuᵢᵀ**. **x̂ = A⁺b** is the **minimum-norm least squares solution**.
Full column rank ⟹ A⁺ = (AᵀA)⁻¹Aᵀ. Invertible ⟹ A⁺ = A⁻¹.

**Condition number:** **κ(A) = σ₁/σ_r**. Error amplification ‖Δx‖/‖x‖ ≤ κ·‖Δb‖/‖b‖. **κ(AᵀA) = κ(A)².**

**Factorization summary:**
LU (square) · QR (independent columns) · Cholesky LLᵀ (symmetric PD) · PDP⁻¹ (non-defective) · QDQᵀ (symmetric) · **UΣVᵀ (always)**

---

## A.13 Applications

**PCA:** centre → S = X_cᵀX_c/(m−1) → eigen-decompose → q₁ is the max-variance direction, λᵢ its variance.
Explained variance ratio = λ_k/Σλᵢ. Via SVD: **PCs = right singular vectors, λᵢ = σᵢ²/(m−1)**.

**Compression ratio (rank k):** mn/[k(m+n+1)]

**Recommender:** R ≈ PQᵀ, r̂ᵤᵢ = pᵤ·qᵢ. ALS: pᵤ = (Σqᵢqᵢᵀ + λI)⁻¹(Σrᵤᵢqᵢ).

**Cosine similarity:** (a·b)/(‖a‖‖b‖) — angle, not distance.

**Markov:** steady state q solves **(P − I)q = 0** with Σqᵢ = 1. Convergence rate governed by |λ₂|.

**Graph:** (Aᵏ)ᵢⱼ = number of walks of length k. **L = D − A**; multiplicity of eigenvalue 0 = number of components.

**Gradient descent rate:** [(κ−1)/(κ+1)]ᵏ — why feature scaling matters.

---

# Appendix B — The Ten Most Expensive Mistakes

**1. Using reduced columns for a basis of Col(A).**
Row reduction **changes the column space**. Always go back and take the **original** columns in the pivot positions. (Row space is different — there you may use the RREF rows.)

**2. det(cA) = c·det A.**
Wrong. It is **det(cA) = cⁿ det A**. Every one of the n rows gets scaled.

**3. Forgetting that transpose and inverse reverse the order.**
**(AB)ᵀ = BᵀAᵀ** and **(AB)⁻¹ = B⁻¹A⁻¹**. Writing AᵀBᵀ is the single most common algebra slip in the subject.

**4. Assuming a repeated eigenvalue means "not diagonalizable".**
It only means you must **check**. Compute GM = n − rank(A − λI) and compare with AM. Symmetric matrices with repeated eigenvalues are always diagonalizable.

**5. Not running Gram–Schmidt inside a repeated eigenspace.**
When orthogonally diagonalizing a symmetric matrix, eigenvectors from **different** eigenvalues are automatically orthogonal, but two eigenvectors from the **same** eigenspace usually are not. Orthogonalize within each eigenspace before assembling Q.

**6. Projecting onto a non-orthogonal basis with the orthogonal formula.**
The formula proj_W(y) = Σ((y·uᵢ)/(uᵢ·uᵢ))uᵢ **requires** the uᵢ to be mutually orthogonal. **Check first.** If they are not, either run Gram–Schmidt or use P = A(AᵀA)⁻¹Aᵀ.

**7. Confusing eigenvalues with singular values.**
Singular values are **never negative** and come from AᵀA. A matrix can have all eigenvalues 0 yet a large σ₁ (e.g. [[0,1],[0,0]]). For symmetric A, σᵢ = |λᵢ|.

**8. Forgetting to centre the data before PCA.**
Uncentred "PCA" finds the direction of the data's **mean**, not its **spread**. Subtract the column means first, every time.

**9. Treating det(A + B) as det A + det B, or eigenvalues of A+B as sums of eigenvalues.**
Neither is true. Determinants are multiplicative, not additive; eigenvalues do not add across matrices unless the matrices share eigenvectors.

**10. Applying the Invertible Matrix Theorem to a non-square matrix.**
The IMT is **only** for square matrices. For an m×n matrix, one-to-one (pivot in every column) and onto (pivot in every row) are completely independent conditions and can hold separately.

**Bonus: sign errors in cofactor expansion.** The checkerboard starts with **+** at position (1,1) and alternates. Always expand along the row or column with the most zeros.

---

# Appendix C — Glossary

**Adjugate (adj A)** — transpose of the cofactor matrix; A·adj(A) = (det A)I.
**Algebraic multiplicity (AM)** — multiplicity of λ as a root of the characteristic polynomial.
**Augmented matrix** — coefficient matrix with the constants column appended.
**Basis** — a linearly independent spanning set.
**Cayley–Hamilton** — every square matrix satisfies its own characteristic equation.
**Characteristic equation** — det(A − λI) = 0.
**Cholesky factorization** — A = LLᵀ for symmetric positive definite A.
**Cofactor** — Cᵢⱼ = (−1)^{i+j}Mᵢⱼ, where Mᵢⱼ is the (i,j) minor.
**Column space Col(A)** — span of the columns; equals {Ax}.
**Condition number κ(A)** — σ_max/σ_min; measures numerical sensitivity.
**Congruent** — B = PᵀAP with P invertible; preserves inertia.
**Consistent** — the system has at least one solution.
**Covariance matrix** — S = X_cᵀX_c/(m−1); symmetric positive semidefinite.
**Defective** — has an eigenvalue with GM < AM; equivalently not diagonalizable.
**Determinant** — the signed volume scaling factor; zero ⟺ singular.
**Diagonalizable** — A = PDP⁻¹ with D diagonal.
**Dimension** — number of vectors in any basis.
**Eckart–Young** — the truncated SVD is the best low-rank approximation.
**Eigenspace E_λ** — Nul(A − λI); all eigenvectors for λ, plus 0.
**Eigenvalue / Eigenvector** — Av = λv with v ≠ 0.
**Elementary matrix** — result of one row operation applied to I.
**Frobenius norm** — ‖A‖_F = √(Σaᵢⱼ²) = √(Σσᵢ²).
**Free variable** — one whose column has no pivot.
**Geometric multiplicity (GM)** — dim E_λ = n − rank(A − λI).
**Gram–Schmidt** — orthogonalization by subtracting projections onto previous vectors.
**Homogeneous system** — Ax = 0; always consistent.
**Idempotent** — A² = A; the projections.
**Inconsistent** — no solution exists.
**Inertia** — the triple (n₊, n₋, n₀) of eigenvalue signs.
**Invertible Matrix Theorem** — the list of equivalent conditions for square invertibility.
**Isomorphism** — a bijective linear map.
**Jordan form** — the near-diagonal canonical form; blocks of size >1 indicate defect.
**Kernel** — ker(T) = {v : T(v) = 0}; equals Nul(A).
**Laplacian** — L = D − A for a graph; nullity = number of components.
**Least squares solution** — minimizes ‖b − Ax‖; solves AᵀAx̂ = Aᵀb.
**Linear combination** — c₁v₁ + ... + c_kv_k.
**Linearly independent** — only the trivial combination gives 0.
**LU factorization** — A = LU with L unit lower triangular, U upper triangular.
**Markov / stochastic matrix** — non-negative with columns summing to 1.
**Minimal polynomial** — the monic polynomial of least degree annihilating A.
**Minor** — determinant of a submatrix formed by deleting a row and column.
**Nilpotent** — Aᵏ = 0 for some k; all eigenvalues 0.
**Normal equations** — AᵀAx̂ = Aᵀb.
**Null space Nul(A)** — {x : Ax = 0}.
**Nullity** — dim Nul(A).
**Orthogonal complement W⊥** — everything perpendicular to all of W.
**Orthogonal matrix** — square with QᵀQ = I; preserves lengths and angles.
**Orthonormal** — mutually orthogonal unit vectors.
**PCA** — eigen-analysis of the covariance matrix of centred data.
**Pivot** — the leading entry used to create zeros below it.
**Positive definite** — symmetric with xᵀAx > 0 for all x ≠ 0; all eigenvalues positive.
**Principal axes** — the eigenvector directions of a quadratic form's matrix.
**Projection** — the closest point of a subspace; P² = P and Pᵀ = P.
**Pseudoinverse A⁺** — VΣ⁻¹Uᵀ; gives the minimum-norm least squares solution.
**QR factorization** — A = QR with Q orthonormal-columned, R upper triangular.
**Quadratic form** — xᵀAx with A symmetric.
**Rank** — dim Col(A) = number of pivots = number of nonzero singular values.
**Rank–nullity** — rank + nullity = number of columns.
**Rayleigh quotient** — (xᵀAx)/(xᵀx); lies between λ_min and λ_max.
**RREF** — reduced row echelon form; **unique** for each matrix.
**Ridge regression** — (AᵀA + λI)x̂ = Aᵀb; always solvable for λ > 0.
**Row space Row(A)** — span of the rows; equals Col(Aᵀ).
**Similar** — B = P⁻¹AP; the same map in different coordinates.
**Singular** — not invertible; det = 0.
**Singular value** — σᵢ = √(eigenvalue of AᵀA); never negative.
**Span** — the set of all linear combinations.
**Spectral norm** — ‖A‖₂ = σ₁.
**Spectral Theorem** — symmetric ⟺ orthogonally diagonalizable.
**Steady state** — the probability vector q with Pq = q.
**Subspace** — contains 0 and is closed under addition and scaling.
**SVD** — A = UΣVᵀ; exists for every matrix.
**Sylvester's criterion** — positive definite ⟺ all leading principal minors positive.
**Trace** — sum of diagonal entries = sum of eigenvalues.
**Transpose** — Aᵀ with rows and columns swapped.
**Trivial solution** — x = 0.
**Vandermonde matrix** — rows (1, xᵢ, xᵢ², ...); determinant Π_{i<j}(xⱼ − xᵢ).

---

# Appendix D — Answer Index

*Quick lookup of final answers for self-checking. Full working is in each chapter's solutions section.*

**Chapter 1.** P1.1 (14/5, 9/5) · P1.2 yes · P1.4 infinite, (3+2t, t) · P1.6 (22/19, −8/19, 36/19) · P1.7 (−5,3,0)+t(−4,3,1) · P1.8 C₃H₈+5O₂→3CO₂+4H₂O · P1.9 4, 8, 18 · P1.10 h=2 · P1.11 unique a≠4; none a=4,b≠6; infinite a=4,b=6 · P1.12 b₁−b₂+b₃=0 · P1.13 (−39/25, 67/25, 12/5, 62/25) · P1.14 7+6t−t² · P1.15 unique λ∉{1,−2}; infinite λ=1; none λ=−2 · P1.16 0 ≤ x₄ ≤ 400

**Chapter 2.** P2.3 I₂ · P2.4 (2,1) · P2.5 zero pivots, all of ℝ³ · P2.6 (11,0,3,0)+s(−2,1,0,0)+t(−7,0,−2,1) · P2.7 s(−3,1,0,0)+t(4,0,−3,1) · P2.8 a=4 · P2.11 h=7 consistent (a line); else inconsistent · P2.12 3 free, dim Col = 3, no · P2.14 3 free variables · P2.17 x₀=abc, x₁=−(ab+bc+ca), x₂=a+b+c · P2.18 8

**Chapter 3.** P3.2 [[2,−5],[−1,3]] · P3.4 not invertible · P3.6 [[−11,2,2],[−4,0,1],[6,−1,−1]] · P3.7 X = B · P3.9 ±I or [[a,b],[c,−a]] with a²+bc=1 · P3.10 (−1,2) · P3.11 (I−A)⁻¹ = I+A+A² · P3.12 Aⁿ = [[1,n],[0,1]] · P3.13 (11/20, 4/5, 7/10) · P3.20 det A ∈ {0, 1}

**Chapter 4.** P4.3 dim 1 · P4.5 5, 5, 6, 6 · P4.6 rank 2, nullity 2 · P4.7 yes, a basis · P4.8 yes; no · P4.9 dim 3 · P4.10 (2,3) · P4.11 dim 3 · P4.12 rank 4, dim Row 4, dim Nul(Aᵀ) 1, no · P4.13 all k · P4.14 dim(U∩W) = 1, dim(U+W) = 3 · P4.15 independent; differences always dependent

**Chapter 5.** P5.1 orthogonal, √14 · P5.2 (3,−4,12)/13 · P5.5 span{(−1,−1,1)} · P5.6 q₂ ∝ (10,2,−7) · P5.7 (4/3, 1/3, 2/3) · P5.8 dim 3 · P5.11 distance 2/√3 · P5.13 rank 1, trace 1 · P5.15 {1, t, t²−1/3} · P5.20 H = [[0,1],[1,0]], reflection in y = x

**Chapter 6.** P6.1 (1/3, 1/3) · P6.2 y = 1.1 + 1.6x · P6.3 (2,1) · P6.4 SSE = 2 · P6.6 y = 4.3 − 0.7x, R² = 0.98 · P6.7 (0.5, 1.4), error ≈ 0.447 · P6.8 y = −0.05+0.45x+0.75x² · P6.9 y ≈ 2x^1.5 · P6.10 y = 15 − 2x · P6.12 (1/7, 8/7, 15/7) · P6.13 (1,1,1) · P6.14 k ≈ 2.48; SSE 3.93 vs 3.60 · P6.16 y = −2 + 3.25x · P6.20 (22/19, 22/19, 34/19)

**Chapter 7.** P7.1 14; −9 · P7.2 189, 1/7, 49 · P7.3 24 · P7.6 1 · P7.7 area 11 · P7.8 (1, 5/3, 2/3) · P7.9 rank 2 · P7.10 k = 1, −2 · P7.11 [[−5,2],[3,−1]] · P7.12 160 · P7.14 rank 2 · P7.15 32 · P7.16 volume 13, right-handed · P7.17 [a+(n−1)b](a−b)^{n−1} · P7.20 (a+b+c)(a²+b²+c²−ab−bc−ca)

**Chapter 8.** P8.1 A³ = I · P8.3 [[155,105],[55,205]] · P8.4 "CB" · P8.5 yes; (0.7, 0.3) · P8.6 d₂,d₃ most similar (0.632) · P8.7 (5/6, 1/6) · P8.9 (2,2) · P8.10 valid · P8.11 covariance is 4×4 · P8.12 bit 3, message (0,1,0,1) · P8.13 2 walks; 2 triangles · P8.14 [[0,1,−2],[1,0,2],[0,0,1]] · P8.15 "JDCV" · P8.19 d_min = 2; detects 1, corrects 0

**Chapter 9.** P9.1 3,−2; 4,5 · P9.2 no · P9.3 1,2,3 · P9.4 trace 5, det −8 · P9.6 λ=5,−1; (1,1),(1,−1) · P9.7 λ=1 (GM 2), λ=3 · P9.8 not diagonalizable · P9.9 ±i, rotation · P9.10 eigenvalue 8 · P9.11 A⁻¹ = (1/3)[[2,−1],[−1,2]] · P9.12 not diagonalizable · P9.13 λ = 3, 0, 0 · P9.15 {1, ω, ω²}, diagonalizable · P9.16 2 + 2cos(kπ/5) · P9.21 discs [9,11], [3,7], [1,3]; invertible

**Chapter 10.** P10.2 no · P10.3 8, 27 · P10.4 P=[[1,1],[0,−1]], D=diag(5,2) · P10.5 yes · P10.6 A⁴ = [[277,261],[348,364]] · P10.7 no · P10.8 A^{100} = I · P10.9 yes; rank(A−I) = 1 · P10.10 P=[[1,1],[−2,−1]], D=diag(3,5) · P10.11 (3/7, 4/7) · P10.12 A⁵ = −I + 1042J · P10.14 x(t) = e^t(1,1) · P10.15 Aⁿ = [[aⁿ, n a^{n−1}b],[0,aⁿ]] · P10.16 c = 0; all c · P10.17 D = diag(1,1,0) · P10.18 a_n = 2·3ⁿ − 2ⁿ

**Chapter 11.** P11.1 λ = (7±3√5)/2 · P11.2 [[4,−3],[−3,1]] · P11.3 positive definite · P11.5 indefinite · P11.6 λ = 9, 1 · P11.7 positive definite · P11.8 L = [[3,0],[1,2]] · P11.9 degenerate: two parallel lines · P11.12 λ = 4, 1, 1 · P11.13 max 5, min 3 · P11.14 a > √2 · P11.15 positive definite; (x₁−x₂)²+(x₂+x₃)²+2x₃² · P11.17 I₂ and [[1,1],[0,1]] · P11.21 generalized eigenvalues ±1/√3

**Chapter 12.** P12.1 A = [[3,0],[1,−1]] · P12.2 −I · P12.3 not linear · P12.4 span{(−2,1)} · P12.6 rank 1, nullity 2, neither · P12.7 [[1,−√3],[√3,1]] · P12.8 invertible, det 1 · P12.9 [x]_B = (−2,1) · P12.10 (−2, 15) · P12.11 dim ker = 3 · P12.12 [T]_B = [[3,1],[0,3]] · P12.13 nullity 1 · P12.15 det = −1 · P12.19 index n+1, dim ker(Dᵏ) = k

**Chapter 13.** P13.1 4,3; 5,0 · P13.2 rank 2, ‖A‖₂ = 6, ‖A‖_F = 3√5 · P13.3 7, 4 · P13.5 U 5×5, Σ 5×3, V 3×3 · P13.6 σ = 2, 1 · P13.7 σ₁ = 5, rank 1 · P13.8 94.1%, error √5 · P13.9 [[1/2,0],[0,0]] · P13.10 κ = 4 · P13.12 σ = √3, 1 · P13.13 ellipse, axes 2√2 and √2, area 4π · P13.14 x̂ = (3/35, 6/35) · P13.21 σ = 2√3, √10; x̂ = (17/60, 1/15, 1/12)

**Chapter 14.** P14.1 x̄ = (3,5) · P14.2 80% · P14.3 10,260 numbers, 6.39× · P14.4 1.5 · P14.6 100% on PC1, q₁ = (2,1)/√5 · P14.7 0.861 · P14.8 3 topics · P14.9 λ = 1.75, 0.5; 77.8%/22.2% · P14.11 3.5 · P14.12 98.27%/1.73% · P14.13 2 factors · P14.16 whitening W = Λ^{−1/2}Qᵀ · P14.17 k = 10 · P14.21 65,536 params, 256× reduction

**Chapter 15 Set A.** A1 (9/5,4/5) · A2 [[3,−5],[−1,2]] · A3 24 · A4 1 · A5 dependent · A6 7 · A7 5,3 · A8 yes · A9 (3,0) · A10 24 · A11 8,6 · A12 [[1,1],[2,0]] · A13 10 · A15 λ=4 · A16 positive definite · A17 [[−1,0],[0,1]] · A18 5 · A19 no · A20 45°

**Chapter 15 Set B.** B1 (7,0,3,0)+s(−2,1,0,0)+t(−5,0,−2,1) · B4 y = 0.5+1.4x, R²=0.98 · B5 −7 · B6 A³=[[86,39],[78,47]] · B7 λ=6,1 · B8 σ = φ, 1/φ · B9 not diagonalizable · B10 (1/2, 2) · B11 onto, nullity 1 · B12 λ=4,2 positive definite · B13 (0.6,0.4) · B15 k ≠ 4 · B16 100% · B17 x̂=(2,2) · B18 A⁻¹=[[−1.5,−0.5],[1,0]]

**Chapter 15 Set C.** C1 rank 2 · C2 unique a≠10 · C3 λ = 2±√2, 2 · C4 R² = 0.9894 · C5 λ = 1,2,4 · C6 x̂ = (1/3,5/3,4/3) · C7 not diagonalizable, blocks 2+1 · C8 P = (1/5)[[1,2],[2,4]] · C10 det A ∈ {0, 8, −8} · C11 saddle · C12 98.27% · C13 four diagonal solutions · C14 λ = 5, 2, 2 · C15 λ₂ = 0.25, q = (1/3,1/3,1/3)

**Mock I.** Q2 (11,0,3,0)+s(−2,1,0,0)+t(−7,0,−2,1) · Q3 λ = 5, −1, −1, diagonalizable · Q5 y = −0.7+1.7x, R² = 0.9897 · Q7 A⁻¹ = (1/4)(4I−J) · Q8 σ = 3,1; x̂ = (0,1) · Q9 ellipse, semi-axes 1 and √6 · Q10 99.03%/0.97%

**Mock II.** Q2 never unique; infinite for λ = 1, 2 · Q3 x = (3,4,−2) · Q4 distance 1.549 · Q6 D₄ = 5, D_n = n+1 · Q7 λ = 1,2,3, diagonalizable · Q8 λ = 7,7,−2 · Q9 2 factors (99.7%) · Q10 reflection in the y-axis; rotation by 2(β−α)

**Mock III.** 1(a) 1 · 1(b) 125 · 1(d) ±2 · 2 inconsistent · 3 A⁶ = [[365,364],[364,365]] · 4 y = 0.9+0.9x, R² = 0.8526 · 5 indefinite · 6 rank 2, ‖A‖₂ = 3, ‖A‖_F = √13 · 7 rank 1, nullity 2

---

*End of handbook.*
