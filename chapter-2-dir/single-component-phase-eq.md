# Single and Multiple Component Phase Eqilibrium

## Introduction
The key idea behind [thermodynamic equilibrium](https://en.wikipedia.org/wiki/Thermodynamic_equilibrium) is that the working material in a system is at a global energy minimum, with constant (and uniform) pressure, temperature and chemical composition. There is alot to unpack in this concept, however, the critical bit is the notion of energy of a chemical system.


---

### Gibbs Energy of a Thermodynamic System

#### Theory
One could imagine that the Gibbs energy $G$ (units: energy) of the working material in system, potentially composed of $\mathcal{M}$ chemical components, would be a function of the temperature $T$, the pressure $P$, and the compostion of the mixture:

$$G = G(T,P,n_{1},\dots,n_{\mathcal{M}})$$

Let's expand the energy function $G(T,P,n_{1},\dots,n_{\mathcal{M}})$ (using the [total derivative in differential form](https://en.wikipedia.org/wiki/Total_derivative)) around some operating point in the system:

$$dG = \left(\frac{\partial{G}}{\partial{T}}\right)_{P,n}dT + \left(\frac{\partial{G}}{\partial{P}}\right)_{T,n}dP +
\sum_{i\in\mathcal{M}}\left(\frac{\partial{G}}{\partial{n_{i}}}\right)_{T,P,n_{j}}dn_{i}$$

We need to do something with partial derivatives; we know from the [thermodynamic potentials](https://en.wikipedia.org/wiki/Thermodynamic_potential) and [Maxwell's relations](https://en.wikipedia.org/wiki/Maxwell_relations) that partial of the Gibbs energy with respect to the temperature at constant pressure and composition is the negative entropy $S$:

$$\left(\frac{\partial{G}}{\partial{T}}\right)_{P,n} = -S$$

while the partial of the Gibbs energy with respect to the pressure at constant temperature and composition is the volume:

$$\left(\frac{\partial{G}}{\partial{P}}\right)_{T,n} = V$$

which gives:

$$dG = -SdT + VdP + \sum_{i\in\mathcal{M}}\left(\frac{\partial{G}}{\partial{n_{i}}}\right)_{T,P,n_{j}}dn_{i}$$

However, we still have the partial of the Gibbs energy with respect to changes in the chemical composition of the mixture; we give this partial derivative a special name, the [partial molar Gibbs energy](https://en.wikipedia.org/wiki/Chemical_potential) and the symbol $\bar{G}_{i}$:

$$dG = -SdT + VdP + \sum_{i\in\mathcal{M}}\bar{G}_{i}dn_{i}$$

#### Equilibrium condtions
Several conditions must be true when a system is in phase equilibrium between phase $\alpha$ and $\beta$. First, the temperature is uniform, constant and equal in both phases, $T^{\alpha} = T^{\beta}$ (thermal equilibrium). Next, the pressure is uniform, constant and equal in both phases, $P^{\alpha} = P^{\beta}$ (mechanical equilibrium). Finally, the working material in the system is at an energy minimum which represent by the condition:

$$\left(dG\right)_{T,P}\leq{0}$$

where the inequality becomes equality at the equilibrium point.

````{prf:definition} Equilibrium conditions

Let's imagine that we have a working material in a system that is a mixture of $\mathcal{M}$ chemical components that are in [thermodynamic equilibrium](https://en.wikipedia.org/wiki/Thermodynamic_equilibrium). Further, imagine that each component $i=1,2,\dots,\mathcal{M}$ of the mixture has Gibbs energy $\bar{G}_{i}$ (units: energy/mol). Then the total amount of energy for the mixture is the weighted contribution of the energy of each component:

```{math}
:label: eqn-Gibbs-free-energy-for-a-mixture
G = \sum_{i\in\mathcal{M}}n_{i}\bar{G}_{i}
```

where $n_{i}$ denotes the number of moles of component $i$ in the mixture, and  $\bar{G}_{i}$ is called the [partial molar Gibbs energy or the chemical potential](https://en.wikipedia.org/wiki/Chemical_potential).

````



## Summary
Fill me in.