# Evaluation

## Sources

White board dude (Iloyd): [https://youtu.be/KtIPAPyaPOg?t=488](https://youtu.be/KtIPAPyaPOg?t=488)

### Speed up of HHL

**Classical** 

Conjugate gradient descent (sparse matrices)

$$
\mathcal{O}(\kappa s log{\left(\frac 1 \epsilon\right)} N )
$$

$N$ := is number of variables in linear system

$s$ := is the sparseness                                                                   

$\epsilon$ := is the accuracy                                                            

$\kappa$ := condition (Number of qubits grows logarithmically)

$$
\mathcal{O}( N )
$$

**Quantum**

HHL

$$
\mathcal{O}(\frac{\kappa^2s^2}{\epsilon}logN)
$$

s-sparse matrix: each row has at most s nonzero entries

Condition number: $\kappa = \frac {\lambda_{max}} {\lambda_{min}}$

- reminder NUMPROG, output = condition number * change in input

$$
\mathcal{O}(logN)
$$

**Takeaway**

- exponential speed up NlogN vs logN
- classical has better dependency on the error than the quantum version $\frac{\kappa s}{-log\epsilon}$ vs $\frac{\kappa^2s^2}{\epsilon}$

## Graph of runtime!!!

TODO!!!!

## Limitations

What are the runtimes

- easy state preparation of vector $\vec b$ to quantum state $\ket{b}$
    - if you have to read/write |b> classically the speed up is gone as |b> has N entries
    - → qram

- has to have a low condition number $\kappa$
- and has to be sparse

QPE has to generate the unitary $e^{iAt}$. efficiency depends on sparseness and good conditioning

proving that something has a good condition number is difficult

bc sometimes you dont know the matrices explicitely ([link](https://arxiv.org/abs/1808.09266))

 

- You can’t read every entry of the result |x⟩
    - Depending on the problem need to do post processing
    - just an quantum state of log2n qubits that approximately encodes the entries as amplitudes
    - Can use statistical information (ratio, locatioWns of large entries, approximate inner product)
    - so we have to find applications where this solution is enough

- Resource requirements are very steep
    - Shor’s algorithm is very close to the HHL Algorithm (bc. of QPE)
    - gives us a lower bound of 4000 logical qubits (2048bit RSA)
    - millions of physical qubit (for error correction)