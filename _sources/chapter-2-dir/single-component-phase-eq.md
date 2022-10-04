# Understanding Phase Eqilibrium

## Introduction
The key idea behind [thermodynamic equilibrium](https://en.wikipedia.org/wiki/Thermodynamic_equilibrium) is that the working material in a system is at a global energy minimum, with constant (and uniform) pressure, temperature and chemical composition. There is alot to unpack in this concept, however, the critical bit is the notion of energy of a chemical system. But what energy are talking about? 

When we we explored [energy balances](../chapter-1-dir/energy-balances.md) we looked at internal energy $U$, however, when thinking about phase equilbrium (and reaction) problems we use a different energy, the [Gibbs Energy](https://en.wikipedia.org/wiki/Gibbs_free_energy) given the symbol $G$. 

In this lecture we will:

* Introduce the {ref}`content:references:gibbs-energy-thermodynamics`
* Introduce the {ref}`content:references:equlibrium-mathching-conditions`
* Introduce the concept of {ref}`content:references:fugacity`

---

(content:references:gibbs-energy-thermodynamics)=
## Gibbs Energy of a Thermodynamic System
The Gibbs energy $G$ (units: energy) of the working material in the system, potentially composed of $\mathcal{M}$ chemical components, is a function of the temperature $T$, the pressure $P$, and the composition of the mixture:

$$G = G(T,P,n_{1},\dots,n_{\mathcal{M}})$$

Let's expand the energy function $G(T,P,n_{1},\dots,n_{\mathcal{M}})$ (using the [total derivative in differential form](https://en.wikipedia.org/wiki/Total_derivative)) around some operating point in the system:

$$dG = \left(\frac{\partial{G}}{\partial{T}}\right)_{P,n}dT + \left(\frac{\partial{G}}{\partial{P}}\right)_{T,n}dP +
\sum_{i\in\mathcal{M}}\left(\frac{\partial{G}}{\partial{n_{i}}}\right)_{T,P,n_{j}}dn_{i}$$

We need to do something with partial derivatives; we know from the [thermodynamic potentials](https://en.wikipedia.org/wiki/Thermodynamic_potential) and [Maxwell's relations](https://en.wikipedia.org/wiki/Maxwell_relations) that the partial derivative of the Gibbs energy with respect to the temperature at constant pressure and composition is the negative entropy $S$:

$$\left(\frac{\partial{G}}{\partial{T}}\right)_{P,n} = -S$$

while the partial derivative of the Gibbs energy with respect to the pressure at constant temperature and composition is the volume:

$$\left(\frac{\partial{G}}{\partial{P}}\right)_{T,n} = V$$

which gives:

$$dG = -SdT + VdP + \sum_{i\in\mathcal{M}}\left(\frac{\partial{G}}{\partial{n_{i}}}\right)_{T,P,n_{j}}dn_{i}$$

However, we still have the partial derivative of the Gibbs energy with respect to changes in the chemical composition of the mixture; we give this partial derivative a special name, the [partial molar Gibbs energy](https://en.wikipedia.org/wiki/Chemical_potential) and the symbol $\bar{G}_{i}$:

```{math}
:label: eqn-dG-full
dG = -SdT + VdP + \sum_{i\in\mathcal{M}}\bar{G}_{i}dn_{i}
```

Eqn. {eq}`eqn-dG-full` describes how the Gibbs energy changes with temperature $T$, pressure $P$, and the chemical composition of the working fluid in a system.

(content:references:equlibrium-mathching-conditions)=
## Equilibrium matching conditions
Several conditions must be true when a system is in phase equilibrium between phases $\alpha$ and $\beta$. First, the temperature is uniform, constant and equal in both phases, $T^{\alpha} = T^{\beta}$ (thermal equilibrium). Next, the pressure is uniform, constant and equal in both phases, $P^{\alpha} = P^{\beta}$ (mechanical equilibrium). Finally, the working material in the system is at an energy minimum which is represented by the condition:

$$\left(dG\right)_{T,P}\leq{0}$$

where the inequality becomes equality at exactly the equilibrium point. 

````{prf:definition} Equilibrium Matching Conditions
:label: defn-eq-matching-conditions

Let's imagine that we have a working material in a system that is a mixture of chemical components in [thermodynamic phase equilibrium](https://en.wikipedia.org/wiki/Thermodynamic_equilibrium) with phases $\alpha$ and $\beta$. Equilibrium requires constant temperature and pressure, thus, $dT=0$ and $dP=0$ in Eqn. {eq}`eqn-dG-full`.

Further, imagine that each chemical component $i$ in the set $\mathcal{M}$ has Gibbs energy $\bar{G}_{i}$ (units: energy/mol). Then the total amount of energy for the mixture is the weighted contribution of the energy of each component:

```{math}
:label: eqn-Gibbs-free-energy-for-a-mixture
G = \sum_{i\in\mathcal{M}}n_{i}\bar{G}_{i}
```

where $n_{i}$ denotes the number of moles of component $i$ in the mixture, and  $\bar{G}_{i}$ is called the [partial molar Gibbs energy or the chemical potential](https://en.wikipedia.org/wiki/Chemical_potential).
````

{prf:ref}`defn-eq-matching-conditions` describes the Gibbs energy at equilibrium. Still, it does it in terms of the partial molar Gibbs energy of the chemical components of the working fluid in the system. We don't have a Gibbs meter or another way to measure these quantities, so we have to relate these to things we can observe. This is where [Fugacity](https://en.wikipedia.org/wiki/Fugacity) comes into the picture. 


(content:references:fugacity)=
## Fugacity
[Fugacity](https://en.wikipedia.org/wiki/Fugacity) is a total hack, but it works, so we keep it. [Fugacity](https://en.wikipedia.org/wiki/Fugacity), initially developed by [Lewis](https://en.wikipedia.org/wiki/Gilbert_N._Lewis), is a hypothetical pressure that we can relate to partial molar Gibbs energy and simultaneously to other things we can measure like the real pressure or the chemical composition of the working fluid. Thus, fugacity bridges the hypothetical world of Gibbs’s energy and the real world of pressure, temperature, and composition. 

````{prf:definition} Fugacity
:label: defn-fugacity-pmge

The fugacity is related to the partial molar Gibbs energy of chemical component $i$ in phase $\star$, denoted by the symbol $\bar{G}^{\star}_{i}$, by the expression:

```{math}
:label: eqn-defn-fugacity-pmge

\bar{G}^{\star}_{i} = \bar{G}^{\star,\circ}_{i} + RT\ln\left(\frac{\hat{f}^{\star}_{i}}{\hat{f}^{\star,\circ}_{i}}\right)
```

where $\bar{G}^{\star,\circ}_{i}$ denotes the partial molar Gibbs energy for component $i$ in phase $\star$ at a reference state, 
$\hat{f}^{\star}_{i}$ denotes the fugacity of component $i$ in phase $\star$, and $\hat{f}^{\star,\circ}_{i}$ denotes the fugacity of component $i$ in phase $\star$ in a reference state. 

````

Finish me.

---

## Summary
In this lecture we:

* Introduced the {ref}`content:references:gibbs-energy-thermodynamics`
* Introduced the {ref}`content:references:equlibrium-mathching-conditions`
* Introduced the concept of {ref}`content:references:fugacity`

