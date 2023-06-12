# HHL-Algorithm

## Short overview

To be solved:

$$
A \vec{x} = \vec{b}
$$

We have 5 Phases:

1. State Preperation
2. Quantum Phase Estimation
3. Ancilla Bit Rotation - add auxiliary qubit
4. Inverse Quantum Phase Estimation
5. Measurement

This is the quantum circuit we will be working with:

![Untitled](HHL-Algorithm%207ba46b86df47407a92db5fb10bb1ebb8/Untitled.png)

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

### State Preperation

1. At first all states are zero $n_b + n + 1$
2. $\vec{b}$ will be encoded as a quantum state $\ket{b}$, by having the amplitudes correspond to the elements of $\vec{b}$.

![Untitled](HHL-Algorithm%207ba46b86df47407a92db5fb10bb1ebb8/Untitled%201.png)

![Untitled](HHL-Algorithm%207ba46b86df47407a92db5fb10bb1ebb8/Untitled%202.png)

### QPE

We already extensively heard of the QPE today. What we basically can achieve is that we can estimates the phase of the eigenvalues of the unitary rotation matrix $U=e^{i \theta}$.

These are proportional to the Eigenvalues of the rotation $\theta$.

For the HHL Algorithm we will encode $A$ into our unitary to obtain its eigenvalues. Because $A$ is Hermitian, its unitary is $U = e^{iAt}$. With this we can obtain an estimation of the Eigenvalues of $A$.

We try to decompose $\ket{b}$ into the Eigenbasis of $A$ using quantum phase estimation, to find the eigenvalues $\lambda_j$ 

### Rotation of Eigenvalues on basis of ancilla qubit

Ancilla qubit is measured and will collaps to either $\ket{0}$ or $\ket{1}$.

- $\ket{0}$: result will be discarded, computation will be repeated
- $\ket{1}$: result is accepted

## TODO Rest unten

### IQPE

Reverse the IQPE to achieve the result

### Measurement

## Notes

### Important Questions to be answered

1. What does the QPE do?
2. What does the IPQFT do?
3. We have heard of QPE how can we get an answer for vector x?
4. What does the RY operation do?
5. What does the IQFE do?

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