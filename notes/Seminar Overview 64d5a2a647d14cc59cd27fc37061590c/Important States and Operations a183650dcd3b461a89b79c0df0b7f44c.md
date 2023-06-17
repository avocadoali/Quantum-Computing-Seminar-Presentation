# Important States and Operations

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

## States

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
$$

$$
 \ket{-} = H \ket{1}
$$

**Entangled States** 

These states can not be represented as a tensor product of individual states

$$
\ket{\Phi} \neq \ket{\phi} \otimes \ket{\psi}
$$

Example: 

$$
\ket{\Phi_1} = \frac{1}{\sqrt{2}} ( \ket{10} + \ket{11}) \\ = \ket{1}\otimes \frac{1}{\sqrt{2}} ( \ket{0} + \ket{1})\\
= \ket{1} \otimes \ket{+}
$$