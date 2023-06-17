# Applications/Future Outlook

## Applications

- main problem: does not output full vector
- But some problems can be solved with this method:
    
    **Analyzing Large Sparse Electrical Networks ([link](https://arxiv.org/abs/1311.1851))**
    
    - electrical power system a lot of interconnected components, such as generators, transformers, transmission lines, and loads.
    - "sparse" relatively small number of direct connections or interactions between its components compared to the total number of possible connections.
    - compute expected value of inverse of a matrix to calculate the resistance in a network
    
    **ML least-square estimation ([link](https://arxiv.org/abs/1204.5242))**
    
    - Data fitting with least square fitting
    - by calculating an estimate of the inverse matrix
    
    **Estimating differential equations ([link](https://arxiv.org/abs/1701.03684))**
    
    - produces quantum state that is proportional to solution
    - problem is encoded as a sparse matrix that approximates the function

But still finding even more applications would be great as the constraints really are high.

## Variations?

- Modifications/improvements/optimization
    - Exponential improved depencdence on precision
    - No ancilla bit required (not probabilistic) under specific requirements ([link](https://arxiv.org/abs/2208.02200))
    - QRAM for preparing |b⟩  ([link](https://arxiv.org/abs/1603.08675))

## Perspective

- HHL algorithm has enormous influence especially in quantum machine learning
- But no real ground breaking applications yet like eg Shors algorithm for breaking RSA
- still lots of active discussion of the algorithm trying to find new variations
- HHL and later Algorithms show advances in the theory of quantum algorithms ([link](https://www.semanticscholar.org/paper/Quantum-Machine-Learning-Algorithms-%3A-Read-the-Fine-Aaronson/dfe4d76e3fc27304a984a5daf1be530401724c25))

- POC 4 qubit quantum computer with 96% fidelity

## It-security

Primarily designed for solving linear systems

not directly tied to it security applications

but has potential to be applied

- Solving Large-scale Linear Systems: The HHL algorithm's primary purpose is to efficiently solve large-scale linear systems of equations on quantum computers. In IT security, there are scenarios where solving such systems is required. For example, in cryptographic protocols like secure multi-party computation or zero-knowledge proofs, solving linear equations might be involved. The HHL algorithm can offer a quantum advantage in solving these equations faster than classical algorithms, potentially enhancing the efficiency and security of these protocols.
- Cryptographic Key Generation and Management: Security protocols often rely on the generation and management of cryptographic keys. The HHL algorithm can aid in key generation by solving linear equations that arise in key generation processes. It can help generate secure keys for encryption or authentication schemes, enhancing the security of cryptographic systems.

- Machine learning and big data analysis/pattern recognition
    - anomaly and fraud detection
    - general quantum algorithms for supervised and unsupervised machine learning ([link](https://arxiv.org/abs/1307.0411))
        - high dimensional vectors using tensor products
    - applied support vector machine (link)
        - optimized for non-/linear binary classifier for supervised training