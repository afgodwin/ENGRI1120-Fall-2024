# Understanding Phase Equilibrium

## Introduction
The key idea behind [thermodynamic equilibrium](https://en.wikipedia.org/wiki/Thermodynamic_equilibrium) is that the working material in a system is at a global energy minimum, with constant (and uniform) pressure, temperature and chemical composition. There is alot to unpack in this concept, however, the critical bit is the notion of energy of a chemical system. But what energy are talking about? 

When we we explored [energy balances](../chapter-1-dir/energy-balances.md) we looked at internal energy $U$, however, when thinking about phase equilbrium (and reaction) problems we use a different energy, the [Gibbs Energy](https://en.wikipedia.org/wiki/Gibbs_free_energy) given the symbol $G$. 

In this lecture we will:

* Introduce the {ref}`content:references:gibbs-energy-thermodynamics`. The Gibbs energy provides the theoretical basis for phase equilibrium calculations. 
* Introduce the {ref}`content:references:equlibrium-mathching-conditions`
* Introduce the concept of {ref}`content:references:fugacity`, the {ref}`content:references:fugacity-matching` and {ref}`content:references:fugacity-phase-models`. These tools provide the actionable basis for phase equilibrium calculations.

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

where the inequality becomes equality, i.e., $\left(dG\right)_{T,P}={0}$ at the equilibrium point. 

````{prf:definition} Equilibrium Matching Conditions
:label: defn-eq-matching-conditions

Let's imagine that we have a working material in a system that is a mixture of chemical components in [thermodynamic phase equilibrium](https://en.wikipedia.org/wiki/Thermodynamic_equilibrium) with phases $\alpha$ and $\beta$. Equilibrium requires constant temperature and pressure, thus, $dT=0$ and $dP=0$ in Eqn. {eq}`eqn-dG-full`.

Further, imagine that each chemical component $i$ in the set $\mathcal{M}$ has Gibbs energy $\bar{G}_{i}$ (units: energy/mol). Then the total amount of energy for the mixture is the weighted contribution of the energy of each component:

```{math}
:label: eqn-Gibbs-free-energy-for-a-mixture
G = \sum_{i\in\mathcal{M}}n_{i}\bar{G}_{i}
```

where $n_{i}$ denotes the number of moles of component $i$ in the mixture, and  $\bar{G}_{i}$ is called the [partial molar Gibbs energy or the chemical potential](https://en.wikipedia.org/wiki/Chemical_potential).

When a system with species set $\mathcal{M}$ is in phase equilibrium between phases $\alpha$ and $\beta$, the partial molar Gibbs energy for each component must match between the phases:

```{math}
:label: eqn-gibbs-matching-condition
\bar{G}^{\alpha}_{i} = \bar{G}^{\beta}_{i}\qquad{i\in\mathcal{M}}
```

Eqn {eq}`eqn-gibbs-matching-condition` is called the Gibbs matching condition; this condition forms the theoretical basis of modeling multicomponent phase equilibrium. 
````

{prf:ref}`defn-eq-matching-conditions` describes the Gibbs energy, and the partial molar Gibbs energy, at equilibrium. Still, it does it in terms of hypothetical quantities of the chemical components of the working fluid in the system. We don't have a Gibbs meter or another way to measure these quantities, so we have to relate these to things we can observe. This is where [Fugacity](https://en.wikipedia.org/wiki/Fugacity) comes into the picture. 


(content:references:fugacity)=
## Fugacity
[Fugacity](https://en.wikipedia.org/wiki/Fugacity), initially developed by [Lewis](https://en.wikipedia.org/wiki/Gilbert_N._Lewis), is a hypothetical pressure that we can relate to partial molar Gibbs energy and simultaneously to other things we can measure like the real pressure or the chemical composition of the working fluid.  Fugacity bridges the hypothetical world of Gibbs’s energy and the real world of pressure, temperature, and composition. 

````{prf:definition} Fugacity
:label: defn-fugacity-pmge

The fugacity is related to the partial molar Gibbs energy of chemical component $i$ in phase $\star$, denoted by the symbol $\bar{G}^{\star}_{i}$, by the expression:

```{math}
:label: eqn-defn-fugacity-pmge

\bar{G}^{\star}_{i} = \bar{G}^{\star,\circ}_{i} + RT\ln\left(\frac{\hat{f}^{\star}_{i}}{\hat{f}^{\star,\circ}_{i}}\right)\qquad\forall{i\in\mathcal{M}}
```

where $\bar{G}^{\star,\circ}_{i}$ denotes the partial molar Gibbs energy for component $i$ in phase $\star$ at a reference state, 
$\hat{f}^{\star}_{i}$ denotes the fugacity of component $i$ in phase $\star$, and $\hat{f}^{\star,\circ}_{i}$ denotes the fugacity of component $i$ in phase $\star$ in a reference state. 

````

{prf:ref}`defn-fugacity-pmge` has a lot to unpack. Let's start by thinking about the reference state. While we could choose any reference state, it is particularly convenient to select the easiest possible state, namely, an _ideal_ state. Thus, when phase $\star$ is a gas, the reference state would be an ideal gas, or when phase $\star$ is a liquid, we could use an ideal liquid model, etc. When seen through from this perspective Eqn {eq}`eqn-defn-fugacity-pmge` can be rewritten as:

```{math}
:label: eqn-gibbs-excess-model
\bar{G}_{i}^{E,\star} = RT\ln\left(\frac{\hat{f}^{\star}_{i}}{\hat{f}^{\star,\circ}_{i}}\right)
```

where $\bar{G}_{i}^{E,\star} = \bar{G}^{\star}_{i} - \bar{G}^{\star,\circ}_{i}$ is called the excess (or residual) partial molar Gibbs energy; another way to think about the excess (residual) Gibbs energy is that is is a measure of the distance from ideality of a system (and its components). 

```{prf:remark}
As a system moves toward ideality, the Gibbs excess (residual) energy moves toward zero (and the ratio of fugacity moves toward one). 
```

(content:references:fugacity-matching)=
### Fugacity Matching Condition
Now that we have models for fugacity let’s think about one additional issue, namely, the relationship of the fugacity for chemical components when the system is in phase equilibrium. To start this, we know from {prf:ref}`defn-eq-matching-conditions` that the partial molar Gibbs energy for each component must match when phase $\alpha$ and $\beta$ are in equilibrium. Thus, this gives us the expression:

```{math}
\bar{G}^{\beta,\circ}_{i} + RT\ln\left(\frac{\hat{f}^{\beta}_{i}}{\hat{f}^{\beta,\circ}_{i}}\right) = 
\bar{G}^{\alpha,\circ}_{i} + RT\ln\left(\frac{\hat{f}^{\alpha}_{i}}{\hat{f}^{\alpha,\circ}_{i}}\right)
```

which we can rearrange to give:

```{math}
\bar{G}^{\beta,\circ}_{i} - \bar{G}^{\alpha,\circ}_{i} = RT\ln\left(\frac{\hat{f}^{\beta,\circ}_{i}}{\hat{f}^{\alpha,\circ}_{i}}\right) - RT\ln\left(\frac{\hat{f}^{\beta}_{i}}{\hat{f}^{\alpha}_{i}}\right)
```

However, the second term on the right-hand side is _extra_ as the first three terms define fugacity. Thus

```{math}
RT\ln\left(\frac{\hat{f}^{\beta}_{i}}{\hat{f}^{\alpha}_{i}}\right) = 0
```

which implies $\hat{f}^{\beta}_{i}=\hat{f}^{\alpha}_{i}$.

````{prf:definition} Fugacity Matching condition
:label: defn-fugacity-matching-cond-eq

When a system with species set $\mathcal{M}$ is in phase equilibrium between phases $\alpha$ and $\beta$, the fugacity for each chemical component must match between the phases:

```{math}
:label: eqn-fugacity-matching-condition
\hat{f}^{\alpha}_{i} = \hat{f}^{\beta}_{i}\qquad{i\in\mathcal{M}}
```

Eqn {eq}`eqn-fugacity-matching-condition` is called the fugacity matching condition; this condition (along with fugacity models for different phases) forms the actionable basis for modeling multicomponent phase equilibrium and solution properties. 

````

(content:references:fugacity-phase-models)=
### Fugacity phase models
The challenge of {prf:ref}`defn-fugacity-matching-cond-eq` (and the excess Gibbs energy model) is that fugacity remains an abstract quantity; thus, while fugacity has units of pressure, e.g., kPa, you can't measure it directly. Instead, we develop models for the fugacity of components in a mixture that can be related to actual variables we can measure. 

#### Gas phase fugacity models
````{prf:definition} Fugacity Model Gas
:label: defn-fugacity-pmge-gas

Consider a gas phase system composed of the chemical species set $\mathcal{M}$. The fugacity of component $i$ in a mixture of $\mathcal{M}$ components, denoted as $\hat{f}^{v}_{i}$ is given by:

```{math}
:label: eqn-fugacity-gas-phase
\hat{f}^{v}_{i} = \hat{\phi}^{v}_{i}y_{i}P\qquad{\forall{i}\in\mathcal{M}}
```

where $\hat{\phi}^{v}_{i}$ is called the fugacity coefficient for compomnent $i$, $y_{i}$ denotes the mole fraction of component $i$ and $P$ denotes the system pressure. 

The fugacity coefficient $\hat{\phi}^{v}_{i}$ is a measure of the non-ideality of a system; if a system is ideal then the fugacity coefficient $\hat{\phi}^{v}_{i}={1}$, otherwise $\hat{\phi}^{v}_{i}>0$. 

````

In the gas phase we define our reference state fugacity as the ideal gas state; if the system is in the ideal gas state, the fugacity is just the partial pressure:

```{math}
\hat{f}^{v,\circ}_{i} = y_{i}P
```

where $y_{i}$ denotes the mole fraction of component $i$. Thus, we can write the excess (residual) Gibbs energy for chemical component $i$ in a gas phase system with the species set $\mathcal{M}$ as:

```{math}
\bar{G}_{i}^{E,v} = RT\ln\hat{\phi}^{v}_{i}\qquad{\forall{i}\in\mathcal{M}}
```

```{prf:observation}
:label: obs-gas-phase-ideality
As the gas phase moves toward ideality, the Gibbs excess (residual) energy $\bar{G}_{i}^{E,v}$ goes toward zero, which implies the fugacity coefficient $\hat{\phi}^{v}_{i}$ moves towards one. 
```

#### Liquid phase fugacity models
````{prf:definition} Fugacity Model Liquid
:label: defn-fugacity-pmge-liquid

Consider a liquid phase system composed of the chemical species set $\mathcal{M}$. The fugacity of component $i$ in a mixture of $\mathcal{M}$ components, denoted as $\hat{f}^{l}_{i}$, is given by:

```{math}
:label: eqn-fugacity-liquid-phase
\hat{f}^{l}_{i} = \hat{\gamma_{i}}x_{i}\phi^{sat}_{i}P^{sat}_{i}\qquad{\forall{i}\in\mathcal{M}}
```

where $\hat{\gamma_{i}}$ is called the activity coefficient for component $i$, $x_{i}$ denotes the mole fraction of component $i$, $P^{sat}_{i}$ denotes the saturation pressure for component $i$, and $\phi^{sat}_{i}$ denotes the vapor phase fugacity coefficient for pure component $i$ at the saturation pressure. 

As the liquid phase moves toward ideality, $\hat\gamma_{i}\rightarrow{1}$.

````

Modeling the liquid phase is difficult; it is a hard problem to model liquids (much harder than the gas phase or solids). Thus, when considering the liquid phase reference state, we turn the problem into one we can solve, namely a gas phase problem. Following the idea of the gas phase reference state, suppose we defined our liquid phase reference state as:

```{math}
\hat{f}^{l,\circ} = x_{i}f^{l}_{i}
```

where $x_{i}$ denotes the liquid phase mole fraction of component $i$, and $f^{l}_{i}$ denotes the reference fugacity of pure component $i$ in the liquid phase. However, suppose we think of pure component $i$ in the liquid as being in equilibrium with pure component $i$ in the vapor; then we can write:

```{math}
f^{l}_{i} = \phi^{sat}_{i}P^{sat}_{i}
```

using the fugacity matching condition. This approach to modeling the liquid reference state is called the Lewis-Randall reference state. 
Lewis-Randall assumes that like-like interactions are dominant and is typically better for concentrated solutions (one component in excess). Alternatively, we could have chosen the [Henry's law reference state](https://en.wikipedia.org/wiki/Henry's_law), which is better for dilute solutions. In any case, let's stick with Lewis-Randall. Putting all these ideas together gives the excess Gibbs energy expression for the liquid phase as:

```{math}
:label: eqn-liq-intro-pmge-gamma
\bar{G}_{i}^{E,l} = RT\ln\hat{\gamma}_{i}\qquad{\forall{i}\in\mathcal{M}}
```


```{prf:observation}
:label: obs-liquid-phase-ideality
As the liquid phase moves toward ideality, the Gibbs excess (residual) energy $\bar{G}_{i}^{E,l}$ goes toward zero, which implies the activity coefficient $\hat{\gamma}_{i}$ moves towards one. 
```

---

## Summary
This lecture introduced the theoretical and actionable basis for modeling multicomponent phase equilibrium. In particular we

* Introduced the {ref}`content:references:gibbs-energy-thermodynamics`. The Gibbs energy provides the theoretical basis for phase equilibrium calculations. 
* Introduced the {ref}`content:references:equlibrium-mathching-conditions`
* Introduced the concept of {ref}`content:references:fugacity`, the {ref}`content:references:fugacity-matching` and {ref}`content:references:fugacity-phase-models`. These tools provide the actionable basis for phase equilibrium calculations.

