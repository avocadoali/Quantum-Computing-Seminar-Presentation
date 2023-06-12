# Hermetian/Unitary Matrix

These are special types of matrices used for the Quantum Algorithms 

**Complex Matrices**

$$
A + i B
$$

$$
M= \begin{bmatrix}
3+3i & i & 6-4i\\
7 & 2-3i & -i
\end{bmatrix}
$$

**Complex conjugate** 

$$
A - i B
$$

$$
\overline M = \begin{bmatrix}
3-3i & -i & 6-4i\\
7 & 2+3i & i
\end{bmatrix}
$$

**Conjugate/Hermitian transpose**  

$$

M^H = M^\dagger =
\begin{bmatrix}
    3-3i & 7 \\
    -i & 2+3i \\
    6-4i & i \\
\end{bmatrix}

$$

**Hermitian Matrix** 

$$

M =
\begin{bmatrix}
    2 & 1-i \\
    1+i & 3 \\
\end{bmatrix} \\
=>^{complex_conjugate} 
\begin{bmatrix}
    2 & 1+i \\
    1-i & 3 \\
\end{bmatrix}\\
=>^{complex_transpose} 
\begin{bmatrix}
    2 & 1-i \\
    1+i & 3 \\
\end{bmatrix} 
= M
$$

**Orthogonal (real)**

columns form an orthonormal basis (transpose = inverse)

$$
A^T = A^{-1}
$$

**Unitary (complex)**

columns form orthonormal vectors (conjugate transpose = inverse)

$$
U^H = U^{-1}
$$

$$
U^H = e^{iH}
$$