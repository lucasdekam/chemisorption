
# Anderson-Newns-Grimley model

:::{tip} Key points
* defining the Hamiltonian in second-quantization language
* applying the Hartree-Fock approximation for electron-electron repulsion on the adatom
* solving for the energy levels (diagonalization) of the ANG Hamiltonian in the Hartree-Fock approximation
:::

The ANG Hamiltonian describes an adatom-substrate system with a single adatom state $a$ and substrate states $k$. The electrons can (de)localize over any of these states. Each state can be occupied by an up-spin electron ($\sigma=+$) and a down-spin electron ($\sigma=-$). 

On the adatom, this can optionally lead to Coulomb repulsion between the electrons. This repulsion is a two-body interaction, described by an operator
$$W = {1\over 2} \sum_{ijkl} w_{ijkl} c_i^\dag c_j^\dag c_k c_l$$
By the Pauli principle, the two electrons occupying the adatom state must have opposite spins. Thus we only have the matrix elements
$$w_{+-+-}=w_{-+-+}=U$$
so
$$W={1 \over2} U \left( c_+^\dag c_-^\dag c_-c_+ + c_-^\dag c_+^\dag c_+ c_- \right) $$

From the anticommutation relations of the creation and annihilation operators for different spins, it turns out that all these creation/annihilation operator pairs can be combined into number operators, so that

$$W = U n_+n_-.$$

This operator simply counts whether the adatom state is doubly occupied, and if so, assigns an energy penalty $U$. 

By adding up all the energy contributions, the Hamiltonian reads

$$H_\mathrm{ANG} = \sum_\sigma \left\{ \left[ \varepsilon_a n_{a\sigma} + \sum_k \left( \varepsilon_k n_{k\sigma} + V_{ak} c_{a\sigma}^\dag c_{k\sigma} + h.c. \right) \right] \right\} + U n_{a+}n_{a,-} \tag{4.33}$$

where $h.c.$ implies the Hermitian conjugate of the term before it. In summary, we have:
* the self-energy of electrons on the adatom state, $\varepsilon_a$, which is counted for each electron on the adatom;
* the self-energy on the substrate, $\varepsilon_k$;
* the interaction or hybridization between the substrate and adsorbate $V_{ak}$. Note that hybridization is unrelated to the spin: a spin-up electron can delocalize between adatom and substrate, and the spin-down electron can also do so, independently of one another;
* the electron-electron repulsion $U$ on the adatom, which is counted only if it is doubly occupied.

## Hartree-Fock approximation

In the **Hartree-Fock approximation**, the electron-electron repulsion is written as the **average** interaction with the opposite-spin electron. The e-e repulsion part of the Hamiltonian is written
$$U n_{a\sigma}n_{a,-\sigma}=U n_{a\sigma}\langle n_{a,-\sigma}\rangle + U n_{a,-\sigma} \langle n_{a,\sigma}\rangle - U \langle n_{a\sigma}\rangle\langle n_{a,-\sigma}\rangle$$

This approximation allows us to include the repulsion energy into the self-energy, as a spin-dependent self-energy:
$$\varepsilon_{a\sigma} = \varepsilon_a + U\langle n_{a,-\sigma} \rangle$$

Now, in the Hartree-Fock approximation, we can write the Hamiltonian as the sum of two decoupled Hamiltonians:
$$H_\mathrm{ANG}=\sum_\sigma H^\sigma$$
with
$$H^\sigma=\varepsilon_{a\sigma} n_{a\sigma}+ \sum_{k} \left[\varepsilon_k n_{k\sigma}+ \left(V_{ak} c_{a\sigma}^{\dagger} c_{k\sigma}+V_{ka}^{*} c_{k\sigma}^{\dagger} c_{a\sigma}
\right)
\right]
$$ 

**Important notes**: 
* There are only two possible values for $\sigma$, up (+) and down (-). Consider that the entire system is completely noninteracting, i.e., each state is occupied by two opposite-spin electrons but they do not interact. Then the total energy of the system can be obtained by solving the system where every state is occupied *once*, and then multiplying times two. Essentially, $H=H^\dag+H^-=2H^\dag$. Now we *do* say that there is an interaction, but only on the adatom. Because Hartree-Fock decouples $H^\dag$ and $H^-$, we can still solve $H^\dag$ and $H^-$ separately, but $H^\dag$ depends on the solution of $H^-$ and the other way around. The Hartree-Fock approximation will therefore eventually lead us to a self-consistent procedure.
* The total Hartree-Fock-approximated Hamiltonian now leaves out the term $- U \langle n_{a\sigma}\rangle\langle n_{a,-\sigma}\rangle$. Why? That's how people do Hartree-Fock: they want to consider the electrons separately. An up-spin electron sees the entire mean-field of the down-spin electron, and this entire energy -- not just half of it -- affects its energy level. Later on, we'll act like we're very surprised that the total energy and sum of eigenvalues differ by exactly that value.

## Eigenvalues of $H^\sigma$

The Schrödinger equation in terms of $H^\sigma$ and the ground state $\Phi_0^\sigma$ is 
$$H^\sigma \Phi_0^\sigma = \varepsilon_0 \Phi_0^\sigma \tag{4.36}$$
where $\varepsilon_0$ is the ground-state energy.  Recall that $\Phi_0^\sigma$ in the occupation representation is something like $[111\cdots00]$. 

By the Hartree-Fock approximation, we can now solve this Schrödinger equation for a single spin state. The Hamiltonian $H^\sigma$ describes all energy levels in the system, but each state is occupied by at most one electron. All electrons have spin $\sigma$. Or, equivalently, because we do not consider electron-electron repulsion anywhere other than the adatom, we can say that this is the Hamiltonian where the electron on the adatom has spin $\sigma$. 

In the discussion below, we drop the sub/superscript $\sigma$, and solve for this non-interacting electron system with Hamiltonian
$$H=\varepsilon_{a} n_{a}+ \sum_{k} \left[\varepsilon_k n_{k}+ \left(V_{ak} c_{a}^{\dagger} c_{k}+V_{ka}^{*} c_{k}^{\dagger} c_{a}
\right)
\right]
$$ 
We can always add $\sigma$ back in by remembering that $\varepsilon_a$ is actually $\varepsilon_{a\sigma}$, and all states in the system can have $\sigma=+,-$.

If we add one more electron in a state $m$, we get an additional energy $\varepsilon_{m\sigma}$:
$$H c^\dag_{m} \Phi_0 = (\varepsilon_0 + \varepsilon_{m}) c_m^\dag \Phi_0.$$
By subtracting Eq. (4.36) $\times c^\dag_{m}$ we get 
$$[H, c^\dag_{m}] \Phi_0 = \varepsilon_{m} c_m^\dag \Phi_0 \tag{4.39}$$
where $[.,.]$ is a commutator bracket. 

The energy levels $m$ are some unspecified energy levels of the perturbed system (adatom plus substrate). They could be the set of substrate states plus the adatom state ($m=k$ or $a$), or a set of new molecular orbitals of the combined system. Either way, the change of basis can be written in terms of creation operators as
$$c_m^\dag = \langle m | a \rangle c^\dag_a + \sum_k \langle m|k \rangle c^\dag_k \tag{4.41}$$
By commuting this operator with $H$ and doing some algebra with the (anti)commutator properties of creation/annihilation operators, one gets
$$[H, c_k^\dag] = \varepsilon_k c_k^\dag + V_{ak} c_a^\dag \quad\text{for $m=k$}$$
$$[H, c_a^\dag] = \varepsilon_a c_a^\dag + \sum_k V^*_{ka} c_k^\dag \quad\text{for $m=a$}$$

On the other hand, one can put (4.41) directly into (4.39), and using the above commutators one gets 
$$
\begin{aligned}
&\left( \langle m|a \rangle \varepsilon_{a} + \sum_k \langle m|k \rangle V_{ak} \right) c_{a}^\dagger \\
&+ \sum_k \left( \langle m|a \rangle V_{ka}^* + \langle m|k \rangle \varepsilon_k \right) c_{k}^\dagger \\
&= \left( \langle m|a \rangle c_{a}^\dagger + \sum_k \langle m|k \rangle c_{k}^\dagger \right) \varepsilon_{m}
\end{aligned}
\tag{4.46}
$$

The coefficients in front of $c_a^\dag$ and $c_k^\dag$ should be equal, so
$$\varepsilon_m \langle m|a \rangle = \varepsilon_a \langle m|a \rangle + \sum_k V_{ak} \langle m|k\rangle $$
$$\varepsilon_m \langle m|k \rangle = \varepsilon_k \langle m|k \rangle + V_{ka}^* \langle m|a\rangle $$
These equations are also referred to as "equations of motion" (?).

Since $|\langle m|a \rangle|^2+\sum_k|\langle m|k \rangle|^2=1$ (an electron must be *somewhere*), we can multiply the above equations by $\langle a|m\rangle$ and $\langle k|m \rangle$, and add them, to obain

$$\varepsilon_m = \varepsilon_a |\langle m|a\rangle|^2 + \sum_k \left[ \varepsilon_k |\langle m|k\rangle|^2 + (V_{ak} \langle m|k\rangle \langle a|m\rangle + h.c.) \right] $$

Now, we're going to bring back the spin. We take the noninteracting system with energy levels $\varepsilon_m$, fill each level with two electrons, and set the energy on the adatom to $\varepsilon_a\to\varepsilon_a +  U\langle n_{a,-\sigma}\rangle=\varepsilon_{a\sigma}$. Bringing back this electron-electron interaction also makes the (still unspecified) energy levels change as $\varepsilon_m\to\varepsilon_{m\sigma}$ since they may depend on the adatom state. 

Summing over all the energy states, and including electrons with both spins,

$$
\begin{aligned}
\sum_{m,\sigma} \varepsilon_{m\sigma} 
&= \sum_{m,\sigma} \bigg[ \sum_q \varepsilon_q |\langle m\sigma|q\sigma\rangle|^2 \\
&+ \sum_k(V_{ak}\langle m\sigma|k\sigma\rangle\langle a\sigma|m\sigma\rangle + h.c.) \bigg] \\
&+ U\sum_\sigma \langle n_{a,-\sigma}\rangle \sum_m |\langle m\sigma|a\sigma\rangle|^2
\end{aligned}
$$
where $q$ runs over all $k$ and $a$; $\varepsilon_q$ are the state 'self-energies' i.e. plane-wave energies (also for the adatom (?)). Now, $\sum_m |\langle m\sigma|a\sigma\rangle|^2$ is the sum of probabilities over all states $m$ that an electron localizes on the $a$-state. Hence it is simply equal to $\langle n_{a\sigma} \rangle$.

So, surprise: writing out the two terms for $\sigma=-,+$, we now get two times the mean e-e repulsion term: 
$$
\begin{aligned}
\sum_{m,\sigma} \varepsilon_{m\sigma} 
&= \sum_{m,\sigma} \bigg[ \sum_q \varepsilon_q |\langle m\sigma|q\sigma\rangle|^2 \\
&+ \sum_k(V_{ak}\langle m\sigma|k\sigma\rangle\langle a\sigma|m\sigma\rangle + h.c.) \bigg] \\
&+ 2 U\langle n_{a,-}\rangle \langle n_{a+} \rangle
\end{aligned}
$$
The sum of energies of occupied states should give us the total system energy, right?

To check this we take the expectation of $H_\mathrm{ANG}$, which also yields the total energy of the system:
$$
E =\langle \Psi_0 | H_\mathrm{ANG} | \Psi_0 \rangle
$$
Here $\Psi_0$ is the Slater determinant of single-particle states $|n\sigma\rangle$. To take the expectation of $H_\mathrm{ANG}$ in second-quantization notation, we write 

$$
\begin{align}
\langle \Psi_0 | H_\mathrm{ANG} | \Psi_0 \rangle &= \sum_{n,\sigma}  \langle n\sigma | H_\mathrm{ANG} | n\sigma \rangle \\
&= \sum_{n,\sigma} \sum_{q,q'} \langle n\sigma |q\sigma\rangle\langle q\sigma| H_\mathrm{ANG} |q'\sigma\rangle \langle q'\sigma | n\sigma \rangle 
\end{align}
$$

For example, there are terms like $\langle q\sigma | c^\dag_{k\sigma} c_{a\sigma} |q'\sigma\rangle=\delta_{q'a} \delta_{qk}$. To see this, one may write $c_{a\sigma}=|0\rangle\langle a|$, and $c^\dag_{k\sigma}=|k\rangle\langle0|$. In this way, the term $\varepsilon_a n_{a\sigma}$ for example has expectation 

$$
\sum_{n} \varepsilon_a |\langle n\sigma|a \sigma\rangle|^2
$$

Continuing like this, we can write

$$
\begin{align}
E &=\sum_{n,\sigma} \bigg[ \sum_q \varepsilon_q |\langle n\sigma | q\sigma\rangle|^2 \\
&+ \sum_k(V_{ak}\langle n\sigma | k\sigma\rangle \langle a\sigma | n\sigma\rangle + h.c.)\bigg] \\
&+U\langle n_{a-}\rangle \langle n_{a+} \rangle
\end{align}
$$

which (wow!) differs from $\sum_{m\sigma}\varepsilon_{m\sigma}$ by a term $U\langle n_{a,-\sigma}\rangle \langle n_{a\sigma} \rangle$.

In conclusion,
$$E = \sum_{m\sigma}\varepsilon_{m\sigma} - U\langle n_{a,-}\rangle \langle n_{a+} \rangle.$$
