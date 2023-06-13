# HHL-Algorithm

## HHL Step-by-Step

![Untitled](HHL-Algorithm%207ba46b86df47407a92db5fb10bb1ebb8/Untitled.png)

### State preparation

We start with all states being 0.

$$
|Ψ_0⟩ = |0⟩^{\otimes n_b}\ |0⟩^{\otimes n}\ |0⟩
$$

$$
|Ψ_0⟩ = |0...0⟩_b\ |0 · · · 0⟩_c\ |0⟩_a
$$

Now we $\vec{b}$ will be encoded as a quantum state $\ket{b}$, by having the amplitudes correspond to the elements of $\vec{b}$. 

![Untitled](HHL-Algorithm%207ba46b86df47407a92db5fb10bb1ebb8/Untitled%201.png)

$$
|Ψ1⟩ = |b⟩_b\ |0...0⟩_c\ |0⟩_a
$$

### Quantum Phase Estimation

$$
|Ψ_4⟩ =\sum_{j=0}^{2^{n_b}−1}
b_j |u_j⟩ | \widetilde{λ}_j⟩ |0⟩_a
$$

$$
|Ψ_4⟩ = \ket{b} | \widetilde{λ}_j⟩ |0⟩_a
$$

$$
\ket{b} = \sum_{j=0}^{2^{n_b}-1} b_j\ket{u_j}
$$

$\ket{b}$ is now represented in the basis formed by the eigenvectors of A

$| \widetilde{λ}_j⟩$ := eigenvalues of A

$|u_j⟩$ := eigenvectors of A

### Inversion of the eigenvalues and measurement of the ancilla qubit

We now have to rotate the ancilla bit $|0⟩_a$, based on the encoded eigenvalues $| \widetilde{λ}_j⟩$ with a constant $C$. Ancilla qubit is measured and will collapse to either $\ket{0}$ or $\ket{1}$.

- $\ket{0}$: result will be discarded, computation will be repeated
    - this is called amplitude amplification (like grover)
    - we have entangled qubits
- $\ket{1}$: result is accepted (TODO warum muss man das überhaupt test?? Hat es was mit Amplitude amplification zu tun???)

Rotate the ancilla qubit

$$
|Ψ5⟩ =
\sum_{j=0}^{2^{n_b}−1}
b_j |u_j⟩ | \widetilde{λ}_j⟩
(\sqrt{1-\frac{C^2}{\widetilde{λ}_j^2}}|0⟩_a + \frac{C}{\widetilde{λ}_j} |1⟩_a)

$$

$$
|Ψ_5⟩ = \ket{b} | \widetilde{λ}_j⟩ |0⟩_a
$$

Measure the ancilla qubit

$$
|Ψ6⟩ = \frac {1} {\sqrt{\sum_{j=0}^{2^{n_b}−1} | \frac{b_jC} {\widetilde{λ}_j}|2}}

\sum_{j=0}^{2^{n_b}−1} b_j |u_j⟩ | \widetilde{λ}_j⟩ \frac{C}{\widetilde{λ}_j} |1⟩_a

$$

$$
\ket{x} =  A^{-1} \ket{b} 
= 
\sum_{i=0}^{2^{n_b}-1} 
\lambda_i^{-1} b_j\ket{u_j}
$$

Resembles our answer. We can only obtain the correct result if the b-register is
measured in the eigenvector basis (i.e. $|u_j⟩$ instead of  |0⟩/|1⟩ ).

However, the b-register is entangled with the clock qubits, $| \widetilde{λ}_j⟩$.

This means that we cannot factorize the result into a tensor product of the c-register and b-
register. As a result, we cannot convert the b-register into the |0⟩ / |1⟩ measurement basis with the desired amplitudes. We will need to uncompute the state so that it gives the right results in the |0⟩ / |1⟩ measurement during which the b-register and c-register will be unentangled.

TODO Why is something entangled??

### Inverse Quantum Phase Estimation

$$
|Ψ9⟩ =
\frac {1} {\sqrt{\sum_{j=0}^{2^{n_b}−1} | \frac{b_jC} {\widetilde{λ}_j}|2}}
\sum_{j=0}^{2^{n_b}−1} \frac{b_jC} {λ_j} |u_j⟩ |0⟩^{⊗n} |1⟩_a
\\ =

\frac {C} {\sqrt{\sum_{j=0}^{2^{n_b}−1} | \frac{b_jC} {\widetilde{λ}_j}|2}}
| x⟩_b | 0⟩^{⊗n}_c | 1⟩_a

$$

After performing IQPE the c-register is reset to 0 again and the b-register stores |x⟩.

If C is real and because of the normalisation of the eigenvectors.

$$
|Ψ9⟩ =
\frac {1} {\sqrt{\sum_{j=0}^{2^{n_b}−1} | \frac{b_j} {\widetilde{λ}_j}|2}}
 \ |x⟩_b  |0⟩^{⊗n}_c |1⟩_a
\\ =| x⟩_b | 0⟩^{⊗n}_c | 1⟩_a

$$

Normalization of the |b⟩ and eigenvectors $|u_i⟩$

$$
\sum_{j=0}^{2^{n_b}−1}
| b_j |^2 = 1
$$

$$
\sum_{i=0}^{2^{n_b}−1}
| λ^{−1}_i b_i |^2 = 1
$$

## Short overview

We have 5 Phases:

1. State Preparation
2. Quantum Phase Estimation
3. Ancilla Bit Rotation - add auxiliary qubit
4. Inverse Quantum Phase Estimation
5. Measurement

This is the quantum circuit we will be working with:

![Untitled](HHL-Algorithm%207ba46b86df47407a92db5fb10bb1ebb8/Untitled%202.png)

We are working with 3 sets of inputs

1. a-register
    - “helper” qbit
    - shows if states are entangled - if yes then recalculated until valid solution is found
2. c-register
    - relates to time (clock) in the controlled rotation in the QPE part
3. b-register 
    - This encodes the b vector into |b> which
    - In the end this will contain our solution for vector x

You are probably wondering where A is used. A is a Hamiltonian matrix which can be encoded as the Hamiltonian of a unitary gate in the QPE phase.

LSB: least significant bit

MSB: most significant bit

## The Algorithm

### State Preparation

1. At first all states are zero $n_b + n + 1$
2. $\vec{b}$ will be encoded as a quantum state $\ket{b}$, by having the amplitudes correspond to the elements of $\vec{b}$.

![Untitled](HHL-Algorithm%207ba46b86df47407a92db5fb10bb1ebb8/Untitled%203.png)

![Untitled](HHL-Algorithm%207ba46b86df47407a92db5fb10bb1ebb8/Untitled%204.png)

### QPE

We already extensively heard of the QPE today. What we basically can achieve is that we can estimates the phase of the eigenvalues of the unitary rotation matrix $U=e^{i \theta}$. These are proportional to the Eigenvalues of the rotation $\theta$.

We will later see that we can also determine the eigenvectors as well

For the HHL Algorithm we will encode $A$ into our unitary $U$. Because $A$ is Hermitian, its unitary is $U = e^{iAt}$. This way can obtain an estimation of the Eigenvalues of $A$.

### Rotation/inversion of Eigenvalues on basis of ancilla qubit

Ancilla qubit is measured and will collapse to either $\ket{0}$ or $\ket{1}$.

- $\ket{0}$: result will be discarded, computation will be repeated
    - this is called amplitude amplification (like grover)
    - we have entangled qubits
- $\ket{1}$: result is accepted

Here we invert the Eigenvalues so that we can use them later to calculate $A^{-1}$

### IQPE

Reverse the IQPE to achieve the result

### Measurement

The problem here is that the solution here cant be read out the exact entries of $\ket{x}$ , as $\ket{x}$ only has $\log_2N$  qubits/entries, whereas  $\vec{b}$ as $N$ entries.

We have to measure it by using an $M$ to observe the properties of $\ket{x}$. 

$$
F(x) := \bra{x}M\ket{x}
$$

## Mathematical Summary

To be solved:

$$
A \vec{x} = \vec{b}
$$

$$
\vec{x} = A^{-1}\vec{b}
$$

Quantum version:

$$
A \ket{x} = \ket{b}\\

$$

$$
\ket{x} = A^{-1}\ket{b}
$$

A is Hermitian, thus we can describe it as a Hamiltonian:

$$
\ket{x} = e^{-iAt}\ket{b}
$$

We can now evaluate $\ket{x}$:

$$
F(x) := \bra{x}M\ket{x}
$$

Sidenotes

$A$ is Hermitian an can be written as a linear combination of outer products of its eigenvectors $\ket{u_i}\bra{u_i}$ weighted by its eigenvalues $\lambda_i$. ([Hermitian operators/Spectral theorem](https://www.youtube.com/watch?v=da1rH0Hq62Q&t=526s)).

$$
A = \sum_{i=0}^{2^{n_b}-1} \lambda_i \ket{u_i}\bra{u_i}
$$

$$
A^{-1} = \sum_{i=0}^{2^{n_b}-1} \lambda_i^{-1} \ket{u_i}\bra{u_i}
$$

This conversion step has a probability to fail, as this operation is not unitary. 

$\vec{b}$ can be also expressed in the basis formed by the eigenvectors of A

$$
\ket{b} = \sum_{j=0}^{2^{n_b}-1} b_j\ket{u_j}
$$

Therefore

$$
\ket{x} = A^{-1} \ket{b} = 
\left(
    \sum_{i=0}^{2^{n_b}-1} \lambda_i^{-1} \ket{u_i}\bra{u_i} 
\right)
\left(
    \sum_{j=0}^{2^{n_b}-1} b_j\ket{u_j}
\right)

$$

$$
\ket{x}=
\sum_{i=0}^{2^{n_b}-1} 
\sum_{j=0}^{2^{n_b}-1} 
\lambda_i^{-1} \ket{u_i}\bra{u_i} 
b_j\ket{u_j}
$$

$$
\ket{x}=
\sum_{i=0}^{2^{n_b}-1} 
\sum_{j=0}^{2^{n_b}-1} 
\lambda_i^{-1} b_j\ket{u_i}\braket{u_i| u_j} 
$$

$$
\ket{x} =
\sum_{i=0}^{2^{n_b}-1} 
\sum_{j=0}^{2^{n_b}-1} 
\lambda_i^{-1} b_j\ket{u_i}\delta_{ij}
$$

$$
\ket{x} =  A^{-1} \ket{b} = 
\sum_{i=0}^{2^{n_b}-1} 
\lambda_i^{-1} b_j\ket{u_j}
$$

Kronecker delta 

$$
\delta_{ij} = 
\begin{cases}
    1 & \text{if } i=j\\
    0 & \text{if } i \neq j
\end{cases}
 
$$

### Important Questions to be answered

1. What does the QPE do?
2. What does the IPQFT do?
3. We have heard of QPE how can we get an answer for vector x?
4. What does the RY operation do?
5. What does the IQFE do?

## Wiki

### State Preperation

![Untitled](HHL-Algorithm%207ba46b86df47407a92db5fb10bb1ebb8/Untitled%205.png)

### Quantum Phase Estimation

![Untitled](HHL-Algorithm%207ba46b86df47407a92db5fb10bb1ebb8/Untitled%206.png)

### Ancilla Bit Rotation - add auxiliary qubit

![Untitled](HHL-Algorithm%207ba46b86df47407a92db5fb10bb1ebb8/Untitled%207.png)

The linear mapping operation is not unitary and thus will require a number of repetitions as it has some probability of failing.

### Inverse Quantum Phase Estimation

![Untitled](HHL-Algorithm%207ba46b86df47407a92db5fb10bb1ebb8/Untitled%208.png)

### Measurement

To read out all components of *x* would require the procedure be repeated at least *N* times. However, it is often the case that one is not interested in $x$  itself, but rather some expectation value of a linear operator *M* acting on *x*. By mapping *M* to a quantum-mechanical operator and performing the quantum measurement corresponding to *M*, we obtain an estimate of the expectation value ⟨x|M|x⟩.
    

## Qiskit

### State Preperation

- Loads data

### Quantum Phase Estimation

### Ancilla Bit Rotation - add auxiliary qubit

### Inverse Quantum Phase Estimation

- applies QPE^t

### Measurement

Measury auxiliary Qubit
Apply observabel M to calculate F(x):= <x|M|x>

## GPT

### Quantum State Preparation

### Unitary Transformation

### Quantum Phase Estimation

### Inverse Quantum Fourier Transformation

### Apply QPE

$$
U = e^{iAt} = \sum_{j=0}^{N-1} e^{iλ_jt} |u_j⟩⟨u_j|
$$

### Invert Eigenvalues

![Untitled](HHL-Algorithm%207ba46b86df47407a92db5fb10bb1ebb8/Untitled%209.png)

### Apply IQPE

### Measure aux qubit

### Apply observable

### Measurement and Post-processing

- Load data
- Apply QPE
- Add auxiliary qubit
- Apply $QPE^t$
- Measury auxiliary Qubit
- Apply observabel $M$ to calculate $F(x):= <x|M|x>$.

## Quellen

Ronald de Wolf Talk: [https://www.youtube.com/watch?v=XEgBdWQdvfk](https://www.youtube.com/watch?v=XEgBdWQdvfk)

Whiteboard: [https://www.youtube.com/watch?v=KtIPAPyaPOg](https://www.youtube.com/watch?v=KtIPAPyaPOg)

Blackboard: [https://www.youtube.com/watch?v=hQpdPM-6wtU&t=137s](https://www.youtube.com/watch?v=hQpdPM-6wtU&t=137s)

Medium article: [https://medium.com/mit-6-s089-intro-to-quantum-computing/hhl-algorithm-solving-systems-of-linear-equations-e4d82d340951](https://medium.com/mit-6-s089-intro-to-quantum-computing/hhl-algorithm-solving-systems-of-linear-equations-e4d82d340951)