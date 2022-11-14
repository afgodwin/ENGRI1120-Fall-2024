# Introduction to Chemical Reaction Equilibrium

## Introduction

In this lecture, we will:
* {ref}`content:references:theory-of-cre`
* {ref}`content:references:cre-eq-closed-system`
* {ref}`content:references:cre-eq-multiple-reactions`

---

(content:references:theory-of-cre)=
## Theory
For chemical reactions involving the chemical component set $\mathcal{M}$, the diffrential change in the Gibbs energy can be written as the sum of the partial molar Gibbs energies (what we called G-bar) at constant T,P:

```{math}
:label: eqn-total-gibbs-energy-sum
d\hat{G} = \sum_{i\in\mathcal{M}}\bar{G}_{i}dn_{i}
```

where $d\hat{G}$ denotes the differential chnge in the total Gibbs energy for the reaction mixture (units: kJ), $\bar{G}_{i}$ denotes the partial molar Gibbs energy for chemical component $i$ (units: kJ/mol) and $dn_{i}$ denotes the differential change in the number of mols of chemical component $i$. From classical thermodynamics we know that the partial molar Gibbs energy for chemical species $i$ is given by:

```{math}
:label: eqn-g-bar-w-a
\bar{G}_{i} = G_{i}^{\circ} + RT\ln\hat{a}_{i}
```

where $G_{i}^{\circ}$ denotes the Gibbs energy for pure component $i$ at a reference state, and $\hat{a}_{i}$ denotes the ratio of fugacities (mixture at reaction T,P/pure component $i$ at reference conditions);  the facgacity models are the same expressions that we developed in our disucssion of [phase equilibrium](../chapter-2-dir/chapter-2-intro.md).

However, for now, let's assume the general case in which we could have either phase. In this case, we substitute the expression for the partial molar Gibbs energy (Eqn. {eq}`eqn-g-bar-w-a`) into the total Gibbs energy expression (Eqn. {eq}`eqn-total-gibbs-energy-sum`) and collect terms:

```{math}
:label: eqn-eq-condition-penultimate
d\hat{G} = \sum_{i\in\mathcal{M}}G^{\circ}_{i}dn_{i} + RT\sum_{i\in\mathcal{M}}dn_{i}\ln\hat{a_{i}}
```

At equilibrium (or the low energy steady-state for an open system), $d\hat{G} = 0$ which gives the equilibrium condition:

````{prf:definition} Chemical Reaction Equilibrium (CRE) condition
:label: defn-eq-condition-dg-multiple-reactions

Suppose we have a well-mixed system with species set $\mathcal{M}$ in which one or more chemical reactions in the reaction set $\mathcal{R}$ is occuring. Futher, the system is at constant temperature and pressure. 

Then, this system is at equlibrium (or the minimum energy-steafy-state for an open system) when the differential change in the total Gibbs energy is zero:

```{math}
:label: eqn-eq-condition-no-phase-no-reaction
\sum_{i\in\mathcal{M}}G^{\circ}_{i}dn_{i} + RT\sum_{i\in\mathcal{M}}dn_{i}\ln\hat{a_{i}} = 0
```

where $G^{\circ}_{i}$ denotes the Gibbs energy for pure component $i$ at a reference state, $\hat{a}_{i}$ denotes the ratio of fugacities, $dn_{i}$ denotes the differential change in the number of moles of component $i$, $R$ denotes the ideal gas constant and $T$ denotes the system temperature.

````

While {prf:ref}`defn-eq-condition-dg-multiple-reactions` is theoretically important, there are a few items that muct be addressed to make it actionable, i.e., something we can use to design the chemical reaction behavior in a system of interest. 
First, let's comopute the change in the number of moles. The differential change in the number of moles of component $i$ is related to the extent of reaction. Suppose we have a reaction set $\mathcal{R}$, then we can write $dn_{i}$ as:

```{math}
dn_{i} = \sum_{r\in\mathcal{R}}\sigma_{ir}d\epsilon_{r}\qquad\forall{i}\in\mathcal{M}
```

where $\sigma_{ir}$ denotes the stoichiometric coefficient for component $i$ in reaction $r$, and $d\epsilon_{r}$ denotes the differential change in the extent of reaction for reaction $r$. 
Let's consider a single reaction, thus, the reaction set $\mathcal{R}$ contains only one element (say reaction 1) and the differential change in the moles of component $i$ is given by:

```{math}
:label: eqn-single-reaction-dni
dn_{i} = \sigma_{i1}d\epsilon_{1}
```

Substituting Eqn. {eq}`eqn-single-reaction-dni` into Eqn. {eq}`eqn-eq-condition-no-phase-no-reaction` and dividing by $d\epsilon_{1}$ gives:

```{math}
\sum_{i\in\mathcal{M}}G^{\circ}_{i}\sigma_{i1} + RT\sum_{i\in\mathcal{M}}\sigma_{i1}\ln\hat{a_{i}} = 0
```

which can be rearranged to give the expression:

```{math}
:label: eqn-eq-ex-almost
\sum_{i\in\mathcal{M}}\sigma_{i1}\ln\hat{a_{i}} = -\frac{\sum_{i\in\mathcal{M}}G^{\circ}_{i}\sigma_{i1}}{RT}
```

Equation {eq}`eqn-eq-ex-almost` can be further simplied to give an expression for the reaction equilibrium constant:

````{prf:definition} Equilibrium constant

Consider a single chemical reaction in a well-mixed system with species set $\mathcal{M}$, at constant temperature and pressure. Then, at equilibrium the total Gibbs energy is given by:

```{math}
:label: eqn-eq-ex-almost-ln
\ln\left(\prod_{i\in\mathcal{M}}\hat{a}^{\sigma_{i1}}_{i}\right) = -\frac{\sum_{i\in\mathcal{M}}G^{\circ}_{i}\sigma_{i1}}{RT}
```

where $\hat{a}_{i} = \hat{f}_{i}/f_{i}$. Equation {eq}`eqn-eq-ex-almost-ln` can be re-written in terms of the equilibrium constant $K$:

```{math}
:label: eqn-eq-constant
K \equiv \prod_{i\in\mathcal{M}}\hat{a}^{\sigma_{i1}}_{i}
```

which gives the familiar expression:

```{math}
K = \exp\left(-\frac{\sum_{i\in\mathcal{M}}G^{\circ}_{i}\sigma_{i1}}{RT}\right)
```
````


### Vapor-phase equilibrium constant
The vapor phase fugacity for compnent $i$ in chemical species set $\mathcal{M}$ is given by:

```{math}
\hat{f}^{v}_{i} = y_{i}\hat{\phi}_{i}P\qquad{i}\in\mathcal{M}
```

where $y_{i}$ denotes the mole fraction of component $i$, $\hat{\phi}_{i}$ denotes the fugacity coefficient for component $i$,  Subsituiting the vapur phase fugacity into Eqn. {eq}`eqn-eq-ex-almost-ln` gives using a standard pressure $P^{\circ}$ as the single component reference state gives:

```{math}
\ln\prod_{i\in\mathcal{M}}\left(\frac{y_{i}\hat{\phi}_{i}P}{P^{\circ}}\right)^{\sigma_{i1}} = -\frac{\sum_{i\in\mathcal{M}}G^{\circ}_{i}\sigma_{i1}}{RT}
```

````{prf:definition} Ideal Gas Phase Equilibrium Constant
:label: eqn-gas-phase-ideal-K

Suppose we have a single gas phase reaction occuring in a well-mixed closed chemical reactor containing species set $\mathcal{M}$. Further, suppose the gas phase is ideal. Then, the ideal gas phase equilibrium constant is given by:

```{math}
:label: eqn-ideal-gas-phase-reaction
K\left(\frac{P}{P^{\circ}}\right)^{-\sigma_{1}} = \prod_{i\in\mathcal{M}}\left(y_{i}\right)^{\sigma_{i1}}
```

where $\sigma_{1}$ denotes the sum of the stoichiometric coefficients for reaction 1, $y_{i}$ denotes the mole fraction of component $i$ and $\sigma_{i1}$ denotes the stoichiometric coefficient for component $i$ in reaction 1. 


````

### Liquid-phase equilibrium constant
The liquid phase fugacity for compnent $i$ in chemical species set $\mathcal{M}$ is given by:

```{math}
\hat{f}_{i}^l = x_{i}\hat{\gamma}_{i}f^{l}_{i}
```

where $x_{i}$ denotes the liquid mole fraction of component $i$, $\hat{\gamma}_{i}$ denotes the activity coefficient for component $i$ (describes lquid phase non-ideality) and $f^{l}_{i}$ denotes the reference fugacity for pure component $i$ in the liquid phase. Substiuting the fugacity into the equilibrium expression (and cancelling the reference states) gives:

```{math}
\ln\prod_{i\in\mathcal{M}}\left(x_{i}\hat{\gamma}_{i}\right)^{\sigma_{i1}} = -\frac{\sum_{i\in\mathcal{M}}G^{\circ}_{i}\sigma_{i1}}{RT}
```

````{prf:definition} Ideal Liquid Phase Equilibrium Constant
:label: eqn-liquid-phase-ideal-K

Suppose we have a single liquid phase reaction occuring in a well-mixed closed chemical reactor containing species set $\mathcal{M}$. Further, suppose the liquid phase is ideal. Then, the ideal liquid phase equilibrium constant is given by:

```{math}
:label: eqn-ideal-liquid-phase-reaction
K = \prod_{i\in\mathcal{M}}\left(x_{i}\right)^{\sigma_{i1}}
```

where $x_{i}$ denotes the mole fraction of component $i$ in the liquid and $\sigma_{i1}$ denotes the stoichiometric coefficient for component $i$ in reaction 1. 

````


(content:references:cre-eq-closed-system)=
## Equilibrium calculations for a closed system
We can subsitute $\bar{G}_{i}$ into the expression for $\hat{G}$, and after some algebraic magic, we get:

$$\frac{1}{RT}\left(\hat{G}-\sum_{i=1}^{\mathcal{M}}n_{i}^{\circ}G_{i}^{\circ}\right) = 
\epsilon_{1}\frac{\Delta{G}^{\circ}}{RT}+\sum_{i=1}^{\mathcal{M}}n_{i}\ln\hat{a}_{i}$$

The first term on the right-hand side is the extent of reaction times the scaled Gibbs energy of reaction; we can think of this term as how much of the Gibbs energy of reaction we recover as the reaction proceeds to the right. The second term describes how the overall Gibbs energy changes as the composition changes (at a fixed T, P). In particular, we know that:

$$n_{i} = n_{i}^{\circ}+\sigma_{i1}\epsilon_{1}\qquad{i=1,2,\dots,\mathcal{M}}$$

and (for an ideal liquid reaction mixture) we know that $\hat{a}_{i}=x_{i}$ where:

$$x_{i} = \frac{n_{i}}{\sum_{j=1}^{\mathcal{M}}n_{j}}\qquad{i=1,2,\dots,\mathcal{M}}$$

Thus, we need to search for $\epsilon_{1}$ (subject to bounds on permissible values of the extent) such that the total Gibbs energy $\hat{G}$ is at a minimum. Once we have the equilibrium extent of reaction, we can compute the equilibrium constant (for an ideal liquid phase reaction at moderate pressures):

$$K_{eq} = \prod_{i=1}^{\mathcal{M}}x_{i}^{\sigma_{i1}}$$

(content:references:cre-eq-open-system)=
## Minimum energy calculations for an open system
Fill me in.

(content:references:cre-eq-multiple-reactions)=
## Extension to multiple reactions
Fill me in.

---

## Summary
Fill me in.