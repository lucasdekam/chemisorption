# Second quantization

:::{tip} Key points
* moving from keeping track of all electrons to just occupation of states
* creation and annihilation operators
* definition of other operators in terms of creation and annihilation operators
:::

*Literature: Schwabl, Advanced Quantum Mechanics, Chapter 1*

We are going to be dealing with many-body electron states: we have a Hamiltonian of the form

$$H = H(1, 2, ...)$$

where $1, 2,...$ denote the coordinates of particles 1, 2, etc. The wavefunction is 

$$\Psi = \Psi(1, 2,...).$$

For indistinguishable fermonic particles such as electrons, the wavefunction is **antisymmetric** under particle exchange: 

$$\psi(...,\alpha,...,\beta...) = -\psi(...,\beta...,\alpha,...)$$

For $N$ states and $N$ electrons, each electron with coordinates $\alpha$ can be in a state $i$; this is denoted as $|i\rangle_\alpha$. The many-electron wave function can be written as a determinant to satisfy antisymmetry. 

$$ 
\Psi(1,2,...,N)=
{1 \over \sqrt{N!}}
\begin{vmatrix}
|1\rangle_1 & |1\rangle_2 & \cdots & |1\rangle_N \\
|2\rangle_1 & |2\rangle_2 & \cdots & |2\rangle_N \\
\vdots & \vdots & \ddots & \vdots \\
|N\rangle_1 & |N\rangle_2 & \cdots & |N\rangle_N
\end{vmatrix}
$$

$$
={1 \over \sqrt{N!}} \left( |1\rangle_1 |2\rangle_2\cdots|N\rangle_N + \text{permut.} \right)
$$
where permut. denotes that we sum over all $N!$ permutations.

This notation is very cumbersome, so the idea of second quantization is to denote the many-electron wave function in terms of the occupation of energy levels:

$$\Psi(1, 2, ...) = |n_1n_2\cdots\rangle$$
where $n_i=0$ or $1$ is the occupation of state $\phi_i$. 

These wave functions can be thought of as vectors $[1 1 1 1 ... 0 0 0]$. The space of these vectors is called **Fock space**. 

## Creation and annihilation operators

Creation operators create an electron; annihilation operators remove one:
$$c_k^\dag |...,0_k,...\rangle = \theta_k |..., 1_k, ...\rangle$$
where $0_k$ and $1_k$ denote occupation 0 or 1 for state $k$. Actually $+$ should be a dagger symbol but this doesn't work in Markdown (?).
Similarly, annihilation operators remove an electron from a state:
$$c_k |...,1_k,...\rangle = \theta_k |..., 0_k, ...\rangle$$

Applying a creation operator to a level that is already 1 or an annihilation operator to a level that is already 0, yields zero. Using that property, the **number operator** can be defined in terms of creation/annihilation operators,
$$n_k = c_k^\dag c_k$$
which yields the occupation (0 or 1) of state $k$. 

Below we sometimes need to 'translate' between molecular orbital states and atomic orbital states. Let's say the creation operator $c_k^\dag$ creates a particle in atomic orbital $k$:
$$c_k^\dag |0\rangle = |k \rangle$$
The molecular orbitals $m$ are related to atomic orbitals $k$ as 
$$|m\rangle = \sum_k C_{mk} |k\rangle$$
where $C_{mk} = \langle m|k\rangle$ are the basis-change or LCAO coefficients. Thus, to create a particle in atomic orbital $m$, we need a creation operator
$$c_m^\dag|0\rangle = |m\rangle $$
or
$$c_m^\dag = \sum_k C_{mk} c_k^\dag.$$
Hence, the basis change carries over directly to second quantization.

## Operators in second quantization

The kinetic energy can be written as a sum of 1-particle operators $t_\alpha=p_\alpha^2/2m$:
$$T = \sum_\alpha t_\alpha$$

We can insert completeness relations / identity operators 
$$I=\sum_i |i\rangle_\alpha\langle i |_\alpha$$ 

Then $$T=\sum_\alpha t_\alpha = \sum_\alpha \sum_{i,j} | i \rangle_\alpha \langle i |_\alpha t_\alpha | j \rangle_\alpha \langle j |_\alpha$$

Then $t_{ij}=\langle i |_\alpha t_\alpha | j \rangle_\alpha$ (it's the same for all identical particles $\alpha$), and

$$T = \sum_{i,j} t_{ij} \sum_\alpha | i \rangle_\alpha \langle j |_\alpha.$$

The operator $\sum_\alpha | i \rangle_\alpha \langle j |_\alpha$ basically moves the electron in state $j$ to state $i$. To see this, we can apply it to a Slater determinant:

$$\sum_\alpha | i \rangle_\alpha \langle j |_\alpha\Psi(1,2,...) = \sum_\alpha | i \rangle_\alpha \langle j |_\alpha \left(\cdots |k\rangle_\alpha \cdots + \text{permut.}\right)$$

Every time the operator encounters particle $\alpha$ occupying state $j$, i.e., $|j\rangle_\alpha$, it 'annihilates' it ($\langle j | j\rangle=1)$ and replaces it with a particle $\alpha$ occupying state $i$, i.e., $|i\rangle_\alpha$. Otherwise, it returns zero. It does this for all particles $\alpha$. 

This operation is exactly equivalent to what the creation and annihilation operators do. In second quantization, we can therefore replace this logic with

$$\sum_\alpha | i \rangle_\alpha \langle j |_\alpha=c_i^\dagc_j$$

and we do not care about keeping track of the individual particles $\alpha$ anymore, because we operate on the occupation representation (Fock space). 

Thus, in second quantization, one-electron operators acting on all electrons in the system can be written as 
$$T = \sum_{i,j} t_{ij} c_i^\dag c_j$$

This directly holds for the kinetic energy; the potential energy can also be written in this form following exactly the same argument:
$$V = \sum_{i,j} V_{ij} c_i^\dag c_j$$

A similar logic can be applied to two-particle operators, such as:

$$W = \frac{1}{2} \sum_{ijkm} w_{ijkl} c_i^\dag c_j^\dag c_m c_k $$
which removes two particles from the states $k$ and $m$, and adds them into states $i$ and $j$.  Here, $w_{ijkl}=\langle i, j | w | k, m \rangle$ is the matrix element of the two-electron operator. The factor 1/2 is necessary because if you count a two-electron interaction for each of the electrons involved, you're overcounting the total energy by a factor 2.

For the next part, we choose $|i\rangle$ to be eigenfunctions of $t=p^2/{2m}$. These are plane waves, a common basis choice for a periodic crystal:
$$|i\rangle = e^{i \mathbf{k}_i \cdot \mathbf{r}}$$
In this eigenbasis, the $t$-operator is diagonal:
$$t_{ij}=\varepsilon_i\delta_{ij}$$
with eigenvalues
$$\varepsilon_i = \frac{\hbar^2 k_i^2}{2m}.$$

