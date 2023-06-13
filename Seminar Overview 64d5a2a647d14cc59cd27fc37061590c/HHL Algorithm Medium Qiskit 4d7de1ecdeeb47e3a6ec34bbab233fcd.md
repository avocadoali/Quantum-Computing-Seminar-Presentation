# HHL Algorithm Medium/Qiskit

## Short overview

We have 5 Phases:

1. State Preparation
2. Quantum Phase Estimation
3. Ancilla Bit Rotation - add auxiliary qubit
4. Inverse Quantum Phase Estimation
5. Measurement

![Untitled](HHL%20Algorithm%20Medium%20Qiskit%204d7de1ecdeeb47e3a6ec34bbab233fcd/Untitled.png)

We are working with 3 sets of inputs

3 quantum registers all initialized to |0⟩ state, 

- auxiliary qubit whose purpose will be explained a little later.
- nl register will be used to store the eigenvalues of A (in binary)
- nb register will contain the vector solution.

### The Algorithm

## Preparation

1. Represent **b** as a quantum state |b⟩. This can be done by:

[https://miro.medium.com/v2/resize:fit:124/0*5TVc2EV33c-LZTgy](https://miro.medium.com/v2/resize:fit:124/0*5TVc2EV33c-LZTgy)

2. Use Hamiltonian simulation to transform the Hermitian matrix A into a unitary operator (U).

[https://miro.medium.com/v2/resize:fit:393/0*zjreb-Pm3NmonRf6](https://miro.medium.com/v2/resize:fit:393/0*zjreb-Pm3NmonRf6)

|uⱼ⟩: the j-th eigenvector of A, 

λⱼ: the j-th eigenvalue of A

3. Load the quantum state |b⟩ to the $n_b$ register

### QPE

4. Use Quantum Phase Estimation (QPE) to decompose |b⟩ in the eigenbasis of A. This will yield the state:

[https://miro.medium.com/v2/resize:fit:249/0*35Rg66I_h-aqX7ge](https://miro.medium.com/v2/resize:fit:249/0*35Rg66I_h-aqX7ge)

|λⱼ⟩: λⱼ represented in binary in the nₗ register

### Eigenvalue inversion

5. Add an auxiliary qubit and rotate conditioned on |λⱼ⟩ to give:

[https://miro.medium.com/v2/resize:fit:595/0*_qOGRRJUJTdGJQas](https://miro.medium.com/v2/resize:fit:595/0*_qOGRRJUJTdGJQas)

C = normalization constant)

### IQPE

6. Undo the Quantum Phase Estimation using IQPE✝ to uncompute |λⱼ⟩ back to |0⟩.

[https://miro.medium.com/v2/resize:fit:562/0*_xXzIsOk8F6hvzIz](https://miro.medium.com/v2/resize:fit:562/0*_xXzIsOk8F6hvzIz)

7. Measure the auxiliary qubit.

- If 1 is measured, we are left with the resulting state that corresponds to the solution |x⟩, up to normalization:
- If 1 is not measured, repeat Steps 4 through 7.
    
    [https://miro.medium.com/v2/resize:fit:547/0*stodbEjafwHjj-K5](https://miro.medium.com/v2/resize:fit:547/0*stodbEjafwHjj-K5)
    

## Measurement

8. With the state of the system proportional to |x⟩, perform the desired measurement with operator M to estimate ⟨x|M|x⟩.

#