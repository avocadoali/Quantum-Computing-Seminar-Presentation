# Evaluation

## Sources

White board dude (Iloyd): [https://youtu.be/KtIPAPyaPOg?t=488](https://youtu.be/KtIPAPyaPOg?t=488)

### Speed up of HHL

**Classical** 

Conjugate gradient descent (sparse matrices)

$$
\mathcal{O}(NlogN)
$$

$$
\mathcal{O}(\frac{\kappa s}{-log\epsilon}N logN)
$$

$s$ := is the sparseness

$\epsilon$ := is the accuracy

**Quantum**

HHL

$$
\mathcal{O}(logN)
$$

$$
\mathcal{O}(\frac{\kappa^2s^2}{\epsilon}logN)
$$

$\kappa$ := condition (Number of qubits grows logarithmically)

$N$ := is number of variables in linear system

Condition number (remindr NUMPROG, output = condition number * change in input)

$$
\kappa = \frac {\lambda_{max}}  {\lambda_{min}}
$$

**Takeaway**

- NlogN vs logN
- classical has better dependency on the error than the quantum version $\frac{\kappa s}{-log\epsilon}$ vs $\frac{\kappa^2s^2}{\epsilon}$

## Limitations

- easy state preparation of vector $\vec b$ to quantum state $\ket{b}$

- has to have a low condition number $\kappa$
- and has to be sparse

QPE has to generate the unitary $e^{iAt}$. efficiency depends on sparse and good conditioning

- You can’t read every entry of the result |x⟩
    - just an quantum state of log2n qubits that approximately encodes the entries as amplitudes
    - Can use statistical information (ratio, locations of large entries, approximate inner product)
    - Depending on the problem need to do post processing

- Resource requirements are very steep
    - Shor’s algorithm is very close to the HHL Algorithm (bc. of QPE)
    - gives us a lower bound of 4000 logical qubits (2048bit RSA)
    - millions of physical qubit (for error correction)
- 4 qubit quantum computer with 96% fidelity