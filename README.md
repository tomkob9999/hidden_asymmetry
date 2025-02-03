# Hidden Asymmetry of Eigenvalues in Row/Column Swapped Matrix

This paper reveals a hidden asymmetry in iterative linear systems constructed from equations that are algebraically reciprocal and identical when considered in isolation. While the row and column swaps of matrices are generally considered trivial, we demonstrate that, under repeated iterations, they introduce structural imbalances that cause divergent scaling effects. These scaling effects, quantified by the eigenvalues of the corresponding transformation matrices, reflect the system’s loss of duality and balance over time. The analysis highlights how local reciprocity fails to guarantee global convergence, with implications for dynamical systems, iterative algorithms, and eigenvalue-driven processes.

---

## 1. Introduction

Linear systems and their iterative behaviors are central to a wide range of applications in mathematics, physics, and computer science. Traditional analyses often treat row and column swaps as algebraic manipulations that do not alter the system's essence. However, when applied to iterative systems, these swaps can introduce subtle but profound differences. This paper explores how systems constructed from algebraically identical equations lose their reciprocal nature under iteration, leading to scaling imbalances dictated by eigenvalues.

We start by defining the system of equations and demonstrating their reciprocity when evaluated locally. We then examine the system under repeated iterations and show how the column and row swaps alter the scaling behavior. Finally, we derive the role of eigenvalues in quantifying this long-term imbalance.

---

## 2. The Iterative System and Initial Setup

Consider the following two systems of equations:

### System A:

$$
\begin{cases}
2x + 3y = x_1 \\
4x + 6y = y_1
\end{cases}
$$

This can be represented as the matrix transformation:

$$
A = \begin{bmatrix} 2 & 3 \\ 4 & 6 \end{bmatrix}
$$

### System B:

$$
\begin{cases}
3x + 2y = x_1 \\
6x + 4y = y_1
\end{cases}
$$

This is represented by:

$$
B = \begin{bmatrix} 3 & 2 \\ 6 & 4 \end{bmatrix}
$$

Both systems share the property that the second equation is a scalar multiple of the first, indicating algebraic redundancy and suggesting that the row/column spaces of the matrices should be identical. However, when these systems are used iteratively, the differences become pronounced.

---

## 3. Iterative Execution and Scaling Effects

We initialize the system with the vector $[x_0, y_0] = [1, 1]$and compute the next iterations using:

$$
\mathbf{v}_{n+1} = A \mathbf{v}_n \quad \text{and} \quad \mathbf{w} _{n+1} = B \mathbf{w} _n
$$

We observe the following iterative process:

1. **Local reciprocity:** Each equation, when considered in isolation, is reciprocal. For example, the equations $2x + 3y = x_1$ and $3x + 2y = x_1$ are algebraically invertible and preserve balance locally.
2. **Loss of duality under iteration:** When the outputs of each equation are fed into the next iteration, the feedback loop introduces asymmetry. The second equation compounds the imbalance caused by the first, leading to exponential divergence in scaling.
3. **Eigenvalue-driven divergence:** The eigenvalues of the transformation matrices $A$ and $B$ determine the long-term scaling behavior when seeing the matrices as system of difference equations. Despite the identical column spaces, the eigenvalues differ:
   - $A$ has eigenvalues $0$ and $26$.
   - $B$ has eigenvalues $0$ and $34$.

The reciprocal behavior observed for the first iteration is highly sensitive to initial conditions. For symmetric input vectors, such as $[1, 1]$, the first iteration behaves identically due to balanced contributions from both variables. However, for non-symmetric inputs, the structural asymmetry of the system—where next $x$ is solely derived from row 1 and next $y$ from row 2—quickly leads to divergent scaling effects dominated by the system's eigenvalues.

---

## 4. Geometric Interpretation of the Imbalance

The key to understanding the divergence lies in the interplay between the column and row swaps and their impact on the eigenvectors. While the column spaces remain identical, the row-column interactions alter the eigenvector alignment. Geometrically:

- **Matrix A:** The iterative application scales the initial vector along eigenvector directions associated with its eigenvalues.
- **Matrix B:** The column swap mirrors the transformation, creating a feedback loop that amplifies the scaling difference.

The result is an exponential divergence in the magnitudes of the transformed vectors, as shown by the difference in eigenvalue scaling.

---

## 5. Analytical Derivation of Scaling Effects

Let $\mathbf{v}_n$ be the vector after $n$ iterations under matrix $A$. Then:

$$
\mathbf{v} _n = A^n \mathbf{v} _0
$$

The norm of $\mathbf{v}_n$ grows approximately as:

$$
\| \mathbf{v} _n \| \propto 
\lambda _{\max}^n
$$


where $\lambda_{\max}$ is the largest eigenvalue of $A$. Similarly, for matrix $B$, we have:

$$
\| \mathbf{w} _ n \| \propto \mu _ {\max}^n
$$

where $\mu_{\max}$ is the largest eigenvalue of $B$.

Since $\mu_{\max} = 34$ and $\lambda_{\max} = 26$, the iterative process under $B$ exhibits faster growth, reflecting the cumulative effect of the imbalance.

---

## 6. Implications and Applications

This analysis reveals that:
- **Local symmetry does not imply global duality:** Systems that appear reciprocal locally can exhibit significant asymmetries under iteration due to cumulative feedback effects.
- **Eigenvalues capture global behavior:** The long-term scaling effects are determined by the eigenvalues, highlighting the importance of understanding their sensitivity to structural changes such as column and row swaps.

### Potential applications:
- **Dynamical systems:** Understanding how small structural changes lead to divergent behavior can inform the design of stable systems.
- **Iterative algorithms:** In optimization and numerical methods, recognizing when iterative processes may diverge due to structural imbalances is crucial.
- **Control theory:** Feedback loops that lose balance over time can lead to instability, which can be mitigated by analyzing eigenvalue-driven growth.

---

## 7. Conclusion
This paper has demonstrated that iterative systems constructed from algebraically identical equations can exhibit significant differences in scaling behavior due to the interplay between column and row swaps. The key insight is that the eigenvalues reflect the cumulative impact of this asymmetry, leading to divergent scaling effects over time. Understanding this phenomenon has practical implications for dynamical systems, optimization, and control theory.

Further research could explore generalizations to higher-dimensional systems and nonlinear transformations, where similar feedback-driven imbalances may arise.
