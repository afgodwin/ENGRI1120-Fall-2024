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

Substitute Eqn. {eq}`eqn-single-reaction-dni` into Eqn. {eq}`eqn-eq-condition-no-phase-no-reaction` and dividing by $d\epsilon_{1}$ gives:

```{math}
\sum_{i\in\mathcal{M}}G^{\circ}_{i}\sigma_{i1} + RT\sum_{i\in\mathcal{M}}\sigma_{i1}\ln\hat{a_{i}} = 0
```

which can be rearranged to give the expression:

```{math}
\sum_{i\in\mathcal{M}}\sigma_{i1}\ln\hat{a_{i}} = -\frac{\sum_{i\in\mathcal{M}}G^{\circ}_{i}\sigma_{i1}}{RT}
```



### Vapor-phase equilibrium constant
Fill me in.

### Liquid-phase equilibrium constant
Fill me in.

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