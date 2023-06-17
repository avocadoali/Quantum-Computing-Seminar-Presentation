# Physical and mathematical constraints/prerequisites (How many qbits are needed, What form do the vectors have to be?)

## Sources

White board dude: [https://youtu.be/KtIPAPyaPOg?t=488](https://youtu.be/KtIPAPyaPOg?t=488)

## Assumptions

1. **We assume $A$ is the same as its Hermitian $A^\dagger$**
    
    $$
    
    A = A^\dagger
    
    $$
    
    If not:
    
    $$
    \begin{pmatrix}
        0 & A \\
        A^\dagger & 0 \\
    \end{pmatrix}
    *
    \begin{pmatrix}
        0 \\
        \vec{x} \\
    \end{pmatrix} 
    = 
    \begin{pmatrix}
        \vec{b} \\
        0 \\
    \end{pmatrix}
    $$
    
2. **A is sparse:**
    
    $$
    s << N \ (entries/row)
    $$
    
    Thus
    

$$
e^{-iAt} \ket{b}
$$

1. **Efficient Oracles for loading data, Hamiltonian Simulation, and function to compute solution**
2.