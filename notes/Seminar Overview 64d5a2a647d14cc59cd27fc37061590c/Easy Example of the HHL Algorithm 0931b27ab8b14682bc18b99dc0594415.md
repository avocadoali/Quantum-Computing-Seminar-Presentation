# Easy Example of the HHL Algorithm

### Step-by-step example

Matrix $A$ and vector $\vec{b}$:

$$
A = \begin{pmatrix}
1 & -\frac{1}{3}\\
-\frac{1}{3} & 1\\
\end{pmatrix}

$$

$$
\vec{b} = \begin{pmatrix}
0 \\
1\\
\end{pmatrix}

$$

Eigenvectors of $A$ are:

$$
\vec{u_0} = \begin{pmatrix}
 \frac{-1}{\sqrt{2}}\\
 \frac{-1}{\sqrt{2}}\\
\end{pmatrix}

$$

$$
\vec{u_1} = \begin{pmatrix}
 \frac{-1}{\sqrt{2}}\\
 \frac{1}{\sqrt{2}}\\
\end{pmatrix}

$$

For easier calculation we will cheat a bit to obtain an easy encoding of the eigenvalues. In the  encoding scheme $\widetilde{λ_j} = Nλ_jt/2π)$ we can choose t freely so that we can encode them in binary and not in some weird state. 

Eigenvalues of the eigenvectors:

$$
\widetilde{λ_j} = Nλ_jt/2π
$$

$$
N = 4 \\
t = 3\pi/4
$$

$$
λ_0 = \frac{2}{3}

$$

$$
λ_1 = \frac{4}{3}

$$

$$
\widetilde{λ_0} =\frac{4*\frac{2}{3}*\frac{3\pi}{4}}{2 \pi}
=\frac{4*2*3\pi}{3*4* 2 \pi} = 1

$$

$$
\widetilde{λ_1} =\frac{4*\frac{4}{3}*\frac{3\pi}{4}}{2 \pi}
=\frac{4*4*3\pi}{3*4* 2 \pi} = 2

$$

$$
|\widetilde{λ_0}⟩ = |01⟩
$$

Thats it for the preparation.

We can calculate the solution classically:

$$
|\widetilde{λ_1}⟩ = |10⟩
$$

$$

\vec{x} = \begin{pmatrix}
 \frac{3}{8}\\
 \frac{9}{8}\\
\end{pmatrix}

$$

the ration is:

$$
\frac{ |x_0|^2}{ |x_1|^2}=
\frac{\frac{9}{64}}{\frac{81}{64}} = \frac{1}{9}

$$

### State preparation

We need $log_2(N)$ qubits where $N$ is the number of elements in $\vec{b}$.

Meaning we need 1 qubit to represent $\vec{b}$.

The c-register which will store the eigenvalues need 2 qubits.

Number of qubits for c-register: n = 2

Number of components of $\vec{b}$ : $N_b = 2^{n_b}$

Number of  qubits for $\vec{b}$: $n_b = 1$ 

→ 4 qubits in total

$$
| Ψ_0⟩ = | 0⟩_b | 00⟩_c | 0⟩_a  =  |0000⟩
$$

Load  $\vec{b}$ will be encoded as a quantum state $\ket{b}$ by having the amplitudes correspond to the elements of $\vec{b}$. In this case it is pretty easy.

$$
\vec{b} =
\begin{pmatrix}
 0\\
 1\\
\end{pmatrix}
\Leftrightarrow
\ket{b} =
0 \ket{0} + 1 \ket{1} = \ket{1} 

$$

$$
|Ψ_1⟩ = |1⟩_b | 00⟩_c | 0⟩_a  =  |1000⟩
$$

### Quantum Phase Estimation

We perform QPE:

$$
|Ψ_4⟩ = \ket{b} | \widetilde{λ}_j⟩ |0⟩
=\sum_{j=0}^{2^{1}−1}
b_j |u_j⟩ | \widetilde{λ}_j⟩ |0⟩
$$

$$
|Ψ_4⟩=\left(−\frac{1}{\sqrt{2}} |u_0⟩ |\widetilde{λ}_0⟩ +\frac{1}{\sqrt{2}}  |u_1⟩ |\widetilde{λ}_1⟩ \right) |0⟩
=
\left(−\frac{1}{\sqrt{2}} |u_0⟩ |01⟩ +\frac{1}{\sqrt{2}}  |u_1⟩ |10⟩\right) |0⟩

$$

a-register: ancilla qubit |0⟩

c-register: eigenvalues $|\widetilde{λ}_0⟩$ and $|\widetilde{λ}_1⟩$ encoded as  |01⟩ and |10⟩

b-register encodes $\ket{b}$ in eigenbasis of A: $|u_0⟩$ or $|u_1⟩$ 

and its respective eigenvalues: $b_0 =\frac{-1}{\sqrt{2}}$ and  $b_1 =\frac{1}{\sqrt{2}}$

$$
\ket{b} = \sum_{j=0}^{2^{n_b}-1} b_j\ket{u_j}
$$

TODO überall cba noch hinschreiben??

State 3 und 7 noch hinzufügen???

### Inversion of the eigenvalues and measurement of the ancilla qubit

We now Rotate the ancilla qubit:

$$
|Ψ_5⟩ =
\sum_{j=0}^{2^{1}−1}
b_j |u_j⟩ | \widetilde{λ}_j⟩
(\sqrt{1-\frac{C^2}{\widetilde{λ}_j^2}}|0⟩ + \frac{C}{\widetilde{λ}_j} |1⟩)
\\ =-\frac{1}{\sqrt{2}}|u_0⟩ |01⟩\left(\sqrt{1-\frac{1}{1^2}}|0⟩ + \frac{1}{1} |1⟩\right) +\frac{1}{\sqrt{2}}|u_1⟩ |10⟩ \left(\sqrt{1-\frac{1}{2^2}}|0⟩ + \frac{1}{2} |1⟩\right)

\\=-\frac{1}{\sqrt{2}}|u_0⟩ |01⟩\left(|0⟩ +|1⟩\right)
+\frac{1}{\sqrt{2}}|u_1⟩ |10⟩ \left(\sqrt{1-\frac{1}{4}}\ |0⟩ + \frac{1}{2} |1⟩\right)

$$

Lets say we measure $\ket{1}$ in the ancilla qubit, then:

$$
|Ψ_6⟩ =\sqrt{\frac{8}{5}}\left(-\frac{1}{\sqrt{2}}|u_0⟩|01⟩|1⟩ +\frac{1}{2\sqrt{2}}|u_1⟩ |10⟩ \right)|1⟩

$$

Say mark what is what 

eigenvectors

eigenvalues

### Inverse Quantum Phase Estimation

$$
|Ψ9⟩ =
| x⟩_b | 0⟩^{⊗2}_c | 1⟩_a

$$

$$
\ket{x}_b =  A^{-1} \ket{b} 
= 
\sum_{i=0}^{2^{1}-1} 
\lambda_i^{-1} b_i\ket{u_i}
\\= \lambda_0^{-1} b_0\ |u_0⟩ +  \lambda_1^{-1} b_1\ket{u_1}

\\=  -\frac{1}{\frac{2}{3}\sqrt{2}}|u_0⟩ +\frac{1}   {\frac{4}{3}\sqrt{2}} |u_1⟩
$$

$$
|Ψ9⟩ =

\frac{2}{3}\sqrt{\frac{8}{5}}
\left(
    -\frac{1}{\frac{2}{3}\sqrt{2}}|u_0⟩ +\frac{1}   {\frac{4}{3}\sqrt{2}} |u_1⟩

\right) 
|00⟩ | 1⟩
$$

After performing IQPE the c-register is reset to 0 again and the b-register stores |x⟩.

Considering the normalization of the eigenvectors we can substitute $|u_0⟩ = \frac{-1}{\sqrt{2}}|0⟩ + \frac{-1}{\sqrt{2}}|1⟩$ and $|u_1⟩ = \frac{-1}{\sqrt{2}}|0⟩ + \frac{1}{\sqrt{2}}|1⟩$  

$$
| Ψ_9⟩ =
\frac{1}{2}\sqrt{\frac{2}{5}}
\left( |0⟩ + 3|1⟩
\right) |00⟩ | 1⟩

$$

$$
| Ψ_9⟩ = 
\left(\frac{1}{2}\sqrt{\frac{2}{5}}| 0⟩
+\frac{1}{2}\sqrt{\frac{2}{5}} * 3 | 1⟩ \right)|00⟩ | 1⟩

$$

### Measurement

To get the probability of $|u_0⟩$ and $|u_1⟩$ we have to square their coefficients

$$
c_0=\left|\frac{1}{2}\sqrt{\frac{2}{5}}*1\right|^2 = \frac{1}{20}

$$

$$
c_1=\left|\frac{1}{2}\sqrt{\frac{2}{5}}*3\right|^2 = \frac{9}{20}

$$

Ratio in b-register is $1:9$ as expected.

## Example complete

### State preparation

$$
| Ψ_0⟩ = | 0⟩_b | 00⟩_c | 0⟩_a  =  |0000⟩
$$

Load  $\vec{b}$ will be encoded as a quantum state $\ket{b}$ by having the amplitudes correspond to the elements of $\vec{b}$. 

$$
|Ψ_1⟩ = |1⟩_b | 00⟩_c | 0⟩_a  =  |1000⟩
$$

$$
\vec{b} =
\begin{pmatrix}
 0\\
 1\\
\end{pmatrix}
\\\Leftrightarrow\\
\ket{b} =
0 \ket{0} + 1 \ket{1} = \ket{1} 

$$

### Quantum Phase Estimation

Steps in between:

$$
|Ψ_2⟩ = I ⊗ H^{⊗n} ⊗ I |Ψ1⟩
\\
|Ψ_3⟩ = \frac{1} {2 \sqrt{2}} ((− |u0⟩ + |u1⟩) |00⟩ + (−i |u0⟩ − |u1⟩) |01⟩ + (|u0⟩ + |u1⟩) |10⟩ + (i |u0⟩ − |u1⟩) |11⟩) |0⟩

$$

$$
|Ψ_4⟩ =\sum_{j=0}^{2^{n_b}−1}
b_j |u_j⟩ | \widetilde{λ}_j⟩ |0⟩_a
$$

$$
|Ψ_4⟩ = IQFT |Ψ_3⟩
=\frac{1}{\sqrt{2}}(− |u_0⟩ |01⟩ + |u_1⟩ |10⟩) |0⟩

$$

We perform QPE:

$$
|Ψ_4⟩ =\sum_{j=0}^{2^{n_b}−1}
b_j |u_j⟩ | \widetilde{λ}_j⟩ |0⟩_a

\\ = IQFT |Ψ3⟩ = \frac{1}{4\sqrt{2}} \left(\left(− |u_0⟩ + |u_1⟩\right) \left(|00⟩ + |01⟩ + |10⟩ + |11⟩\right) \\+ \left(−i |u_0⟩ − |u_1⟩\right) \left(|00⟩ − i |01⟩ − |10⟩ + i |11⟩\right) \\ + \left(|u_0⟩ + |u_1⟩\right) \left(|00⟩ − |01⟩ + |10⟩ − |11⟩\right) \\ + \left(i |u_0⟩ − |u_1⟩\right) \left(|00⟩ + i |01⟩ − |10⟩ − i |11⟩\right) \right)|0⟩

$$

$$
 |Ψ_4⟩=\left(−\frac{1}{\sqrt{2}} |u_0⟩ |01⟩ +\frac{1}{\sqrt{2}}  |u_1⟩ |10⟩\right) |0⟩

$$

b-register encodes the eigenvectors:$|u_0⟩$ or $|u_1⟩$ 

with the respective eigenvalues: $b_0 =\frac{-1}{\sqrt{2}}$ and  $b_1 =\frac{1}{\sqrt{2}}$

We can clearly see entanglement here:$|u_0⟩ |01⟩$ and $|u1⟩|10⟩$

### Inversion of the eigenvalues and measurement of the ancilla qubit

We now Rotate the ancilla qubit:

$$
|Ψ_5⟩ =
\sum_{j=0}^{2^{1}−1}
b_j |u_j⟩ | \widetilde{λ}_j⟩
(\sqrt{1-\frac{C^2}{\widetilde{λ}_j^2}}|0⟩ + \frac{C}{\widetilde{λ}_j} |1⟩)
\\ =-\frac{1}{\sqrt{2}}|u_0⟩ |01⟩\left(\sqrt{1-\frac{1}{1^2}}|0⟩ + \frac{1}{1} |1⟩\right) +\frac{1}{\sqrt{2}}|u_1⟩ |10⟩ \left(\sqrt{1-\frac{1}{2^2}}|0⟩ + \frac{1}{2} |1⟩\right)

$$

$$
|Ψ_5⟩ = \ket{b} | \widetilde{λ}_j⟩ |0⟩_a
$$

TODO: mark c-b-anc-register

Lets say we measure $\ket{1}$ in the ancilla qubit, then:

TODO maybe more steps in between???

$$
|Ψ_6⟩ =\sqrt{\frac{8}{5}}\left(-\frac{1}{\sqrt{2}}|u_0⟩|01⟩|1⟩ +\frac{1}{2\sqrt{2}}|u_1⟩ |10⟩ |1⟩\right)

$$

b-register encodes the eigenvalues: $|01⟩$ or $|10⟩$

c-register: $|u_0⟩$ or $|u_1⟩$

ancillary qubit: $|0⟩$

### Inverse Quantum Phase Estimation

$$
|Ψ9⟩ =
\frac {1} {\sqrt{\sum_{j=0}^{2^{n_b}−1} | \frac{b_j} {\widetilde{λ}_j}|2}}
 \ |x⟩_b  |0⟩^{⊗n}_c |1⟩_a
\\ =| x⟩_b | 0⟩^{⊗n}_c | 1⟩_a

\\=\frac{2}{3}\sqrt{\frac{8}{5}}
\left(
    -\frac{1}{\frac{2}{3}\sqrt{2}}|u_0⟩ +\frac{1}{\frac{4}{3}\sqrt{2}} |u_1⟩

\right) |00⟩ | 1⟩

$$

After performing IQPE the c-register is reset to 0 again and the b-register stores |x⟩.

Considering the normalization of the eigenvectors we can substitute $|u_0⟩ = \frac{-1}{\sqrt{2}}|0⟩ + \frac{-1}{\sqrt{2}}|1⟩$ and $|u_1⟩ = \frac{-1}{\sqrt{2}}|0⟩ + \frac{1}{\sqrt{2}}|1⟩$  

$$
| Ψ_9⟩ =
\frac{1}{2}\sqrt{\frac{2}{5}}
\left( |0⟩ + 3|1⟩
\right) |00⟩ | 1⟩

$$

To get the probability of $|u_0⟩$ and $|u_1⟩$ we have to square their coefficients

$$
c_{|u_0⟩}=\left|\frac{1}{2}\sqrt{\frac{2}{5}}*1\right|^2 = \frac{1}{20}

$$

$$
c_{|u_1⟩}=\left|\frac{1}{2}\sqrt{\frac{2}{5}}*3\right|^2 = \frac{9}{20}

$$

Ratio in b-register is $1:9$ as expected.