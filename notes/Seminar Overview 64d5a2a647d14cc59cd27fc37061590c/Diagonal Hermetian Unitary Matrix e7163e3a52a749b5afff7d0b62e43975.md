# Diagonal/Hermetian/Unitary Matrix

**Bra-Ket** 

kets are linear (scalars can be moved)

bras are anti linear (scalars are conjugated)

→bra is the complex conjugate transpose of ket and vice versa

**Diagonal Matrices**

$$
A = XDX^{-1}\\
X^{-1} A X = XX^{-1}DX^{-1}X \\
X^{-1} A X = D
$$

- A has unique eigenvalues
- A can have duplicate eigenvalues if they have linearly independent eigenvectors
- D is made of eigenvalues of A
- X is made of eigenvectors of A

Say A has the eigenvalues $\lambda_1,  \lambda_2 …  \lambda_n$, then

$$
A = \begin{pmatrix}
\lambda_1 & 0 & 0 & 0\\
 0 & \lambda_2 &0 & 0\\
 0 & 0 & ... & 0\\
 0 & 0 & 0& \lambda_n \\
\end{pmatrix}

$$

Say A has eigenvectors of A $\vec{x_1},\vec{x_2},…,\vec{x_n}$, then

$$
X = \begin{bmatrix}
\vec{x_1}&\vec{x_2}&…&\vec{x_n}

\end{bmatrix}
$$

**For HHL**

So if we can diagonalize A:

$$
 U A U^{\dagger}=  \begin{bmatrix}
\lambda_1 & 0 & 0 & 0\\
 0 & \lambda_2 &0 & 0\\
 0 & 0 & ... & 0\\
 0 & 0 & 0& \lambda_n \\
\end{bmatrix}
$$

Then we can: 

$$
A^{-1} = 
U^\dagger 
\begin{bmatrix}
\lambda_1^{-1} & 0 & 0 & 0\\
 0 & \lambda_2^{-1} &0 & 0\\
 0 & 0 & ... & 0\\
 0 & 0 & 0& \lambda_n^{-1} \\
\end{bmatrix} U
$$

Classically this is horrendous as diagonalizing matrices is as slow as just calculating the inverse of $A$.

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
= M^H
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

Sidenote: All quantum gates is represented as an unitary matrixxx

**Inner product**

 ⟨x| M |x⟩