# Mathematical background

## Hermitian Matrix

$$

A =
\begin{bmatrix}
    2 & 1-i \\
    1+i & 3 \\
\end{bmatrix} \\
=>^{complex_conjugate} 
\begin{bmatrix}
    2 & 1+i \\
    1-i & 3 \\
\end{bmatrix}\\
=>^{transpose} 
\begin{bmatrix}
    2 & 1-i \\
    1+i & 3 \\
\end{bmatrix} 
= A^\dagger
$$

Hermitian Matrix

$$
A = A^\dagger
$$

if $M$ is not Hermitian, then: 

$$

A' = 

\begin{pmatrix}
0 & A \\
A^\dagger & 0 
\end{pmatrix}

$$

## Spectral Decomposition

Lets say we have a Matrix A that we can diagonalize. Then we can describe it with its spectrum which is a matrix with the eigenvalues in the diagonal.

A:= is a matrix

D:= is diagonal matrix made of eigenvalues

U:= is made of eigenvectors of A

$$

A =  U D U^{\dagger}
=

\begin{bmatrix}
    U_1 &
    U_2 &
    ...&
    U_n
\end{bmatrix}

\begin{bmatrix}
    \lambda_1 & 0 & 0 & 0\\
     0 & \lambda_2 &0 & 0\\
     0 & 0 & ... & 0\\
     0 & 0 & 0& \lambda_n \\
\end{bmatrix}

\begin{bmatrix}
    U^\dagger_1 \\
    U^\dagger_2 \\
    ...\\
    U^\dagger_n
\end{bmatrix}

$$

Then we can: 

$$

A^{-1}
=  U^{\dagger} D^{-1} U=
U^\dagger
\begin{bmatrix}
    \lambda_1^{-1} & 0 & 0 & 0\\
    0 & \lambda_2^{-1} &0 & 0\\
    0 & 0 & ... & 0\\
    0 & 0 & 0& \lambda_n^{-1} \\
\end{bmatrix} U

$$

$$
=
\begin{bmatrix}
    \lambda_1^{-1} U^\dagger_1 \\
    \lambda_2^{-1} U^\dagger_2 \\
    ... \\
    \lambda_n^{-1} U^\dagger_n 
\end{bmatrix}
\begin{bmatrix}
    U_1 &
    U_2 &
    ...&
    U_n
\end{bmatrix}

$$

Classically this is horrendous as diagonalizing matrices is as slow as just calculating the inverse of $A$ but in the quantum version it is a very feasible solution.

## Kronecker delta

The Kronecker delta $\delta_{ij}$ is used with inner products $\braket{\psi | \phi}$.

dot product

- orthogonal vectors

$$
\vec{v} \cdot \vec{w} = |\vec{v}| |\vec{w}| \cos{\delta}  = 0 

$$

- length of a vector

$$
|\vec{v}| = \sqrt{\vec{v}^2_0 \cdot \vec{v}^2_1}  = \sqrt{\vec{v}\cdot \vec{v}}

$$

inner product

- orthogonal kets

$$
\braket{\psi|\phi} = 0

$$

- magnitude of a ket

$$
\sqrt{\braket {\psi |{\psi}}}

$$

Lets say we have an orthonormal basis$\ket{E_i}$, meaning all basis vectors are orthonormal.

$$
\braket{E_i|E_i} = 1\\
\braket{E_i|E_i} = 0, \ i\neq j

$$

$$
\braket{E_i|E_j} =
\delta_{ij} = 
\begin{cases}
    1 & \text{if } i=j\\
    0 & \text{if } i \neq j
\end{cases}
 
$$

## Entangled States

These states can not be represented as a tensor product of individual states

$$
\ket{\Phi} \neq \ket{\phi} \ket{\psi}
$$

Example: 

Not entangled

Entangled

$$
\ket{\Phi_1} = \frac{1}{\sqrt{2}} ( \ket{10} + \ket{11}) \\ = \ket{1}\otimes \frac{1}{\sqrt{2}} ( \ket{0} + \ket{1})\\
= \ket{1} \ket{+}
$$

$$
\ket{\Phi_2} = \frac{1}{\sqrt{2}} ( \ket{00} + \ket{11}) \neq \ket{\alpha}\ket{\beta}

$$

## Types of encoding

### Hamiltonian Encoding

$$
U = e^{iAt}

$$

### Amplitude Encoding

### Basis Encoding

Decimal

$$
\begin{bmatrix}
0 \\
3
\end{bmatrix}

$$

to binary to quantum state 

$$

\begin{bmatrix}
00 \\
11
\end{bmatrix}

= \ket{0011}

$$

## Scaling of Lambda

 
$\widetilde{λ_j} = Nλ_jt/2π)$

## Operations on Qubits

**Tensor product**

$$
\begin{pmatrix}
a \\
b 
\end{pmatrix}
\otimes
\begin{pmatrix}
c \\
d 
\end{pmatrix}
=
\begin{pmatrix}
a \begin{pmatrix}c\\d\end{pmatrix}\\
b \begin{pmatrix}c\\d\end{pmatrix}\\
\end{pmatrix}
$$

$$
\begin{pmatrix}
1 \\
2 
\end{pmatrix}
\otimes
\begin{pmatrix}
3 \\
4 
\end{pmatrix}
=
\begin{pmatrix}
1 \begin{pmatrix}3\\4\end{pmatrix}\\
2 \begin{pmatrix}3\\4\end{pmatrix}\\
\end{pmatrix}
= 
\begin{pmatrix}
1 * 3 \\
1 * 4 \\
2 * 3 \\
2 * 4 
\end{pmatrix}
= 
\begin{pmatrix}
3 \\
4 \\
6 \\
8 
\end{pmatrix}

$$

**Multiple qbits**

$$
\ket{00} = \ket{0} \otimes \ket{0} = \begin{pmatrix}
1 \\
0 
\end{pmatrix}
\otimes
\begin{pmatrix}
1 \\
0 
\end{pmatrix}
= 
\begin{pmatrix}
1 \\
0 \\
0 \\
0 
\end{pmatrix}

$$

$$
\ket{4} = \ket{100} = \ket{1} \otimes \ket{0} \otimes \ket{0}= \begin{pmatrix}
0 \\
1 
\end{pmatrix}
\otimes
\begin{pmatrix}
1 \\
0 
\end{pmatrix}
\otimes
\begin{pmatrix}
1 \\
0 
\end{pmatrix}
= 
\begin{pmatrix}
0 \\
0 \\
0 \\
0 \\
1 \\
0 \\
0 \\
0 
\end{pmatrix}
$$

## Basics

**Bra-Ket** 

kets are linear (scalars can be moved)

bras are anti linear (scalars are conjugated)

→bra is the complex conjugate transpose of ket and vice versa

**Zero- and One-state**

$$
\ket{0} = 
\begin{pmatrix}
1 \\
0 
\end{pmatrix}
$$

$$
\ket{1} = 
\begin{pmatrix}
0 \\
1 
\end{pmatrix}
$$

**Hadamard Gate**

$$
H= \frac{1}{\sqrt{2}} \begin{pmatrix}
1 & 1 \\
1 & -1 
\end{pmatrix}
$$

**Hadamard State**

$$
 \ket{+} = H \ket{0}
 = \frac 1{ \sqrt 2}\ket{0} + \frac 1{ \sqrt 2} \ket{1}=
 = \frac 1{ \sqrt 2} \left(\ket{0} - \ket{1}\right)

$$

$$
 \ket{-} = H \ket{1}
 = \frac 1{ \sqrt 2}\ket{0} - \frac 1{ \sqrt 2} \ket{1}=
 = \frac 1{ \sqrt 2} \left(\ket{0} - \ket{1}\right)
$$

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

Sidenote: All quantum gates is represented as an unitary matrix