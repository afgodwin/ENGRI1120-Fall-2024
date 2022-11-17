# Introduction to Chemical Reaction Equilibrium

## Introduction
Chemical reactions are at the center of chemical engineering. The ability to transform molecular reaction events into valuable products is the defining component of the discipline. Chemical reactions are everywhere, from traditional processes, such as the manufacturing of plastics, to biological applications, such as the manufacturing of the COVID-19 mRNA vaccine. 

In this lecture, we look at chemical reactions from the energy perspective. In particular, we relate the extent of reaction to the Gibbs energy minimum for both closed and open systems. We start with defining a theoretical picture of the Gibbs energy in the presence of chemical reactions and then apply this theory to a single gas and liquid phase reaction in a closed system. We then extend these ideas to open systems with multiple coupled reactions. 

In this lecture, we will:
* Develop a {ref}`content:references:theory-of-cre` describing the Gibbs energy of a system with chemical reactions
* Develop expressions for the {ref}`content:references:cre-vapor-phase` and {ref}`content:references:cre-liquid-phase`
* Develop tools for computing extent of reaction for {ref}`content:references:cre-eq-closed-system` and {ref}`content:references:cre-eq-open-system`

---

(content:references:theory-of-cre)=
## Theory for closed systems
Suppose we have a well-mixed closed system, i.e., no flow into or from the system that has species set $\mathcal{M}$.
For chemical reactions in this system, the differential change in the Gibbs energy can be written as the sum of the partial molar Gibbs energies (what we call G-bar) at constant T,P:

```{math}
:label: eqn-total-gibbs-energy-sum
d\hat{G} = \sum_{i\in\mathcal{M}}\bar{G}_{i}dn_{i}
```

where $d\hat{G}$ denotes the differential change in the total Gibbs energy for the reaction mixture (units: kJ), $\bar{G}_{i}$ denotes the partial molar Gibbs energy for chemical component $i$ (units: kJ/mol) and $dn_{i}$ denotes the differential change in the number of mols of chemical component $i$. From classical thermodynamics, we know that the partial molar Gibbs energy for chemical species $i$ is given by:

```{math}
:label: eqn-g-bar-w-a
\bar{G}_{i} = G_{i}^{\circ} + RT\ln\hat{a}_{i}
```

where $G_{i}^{\circ}$ denotes the Gibbs energy for pure component $i$ at a reference state, and $\hat{a}_{i}$ denotes the ratio of fugacities (mixture at reaction T,P/pure component $i$ at reference conditions);  the fugacity models are the same expressions that we developed in our discussion of [phase equilibrium](../chapter-2-dir/chapter-2-intro.md).

However, let's assume the general case in which we could have either phase. In this case, we substitute the expression for the partial molar Gibbs energy (Eqn. {eq}`eqn-g-bar-w-a`) into the total Gibbs energy expression (Eqn. {eq}`eqn-total-gibbs-energy-sum`) and collect terms:

```{math}
:label: eqn-eq-condition-penultimate
d\hat{G} = \sum_{i\in\mathcal{M}}G^{\circ}_{i}dn_{i} + RT\sum_{i\in\mathcal{M}}dn_{i}\ln\hat{a_{i}}
```

At equilibrium, $d\hat{G} = 0$ which gives the equilibrium condition:

````{prf:definition} Chemical reaction equilibrium condition
:label: defn-eq-condition-dg-multiple-reactions

Suppose we have a well-mixed system with species set $\mathcal{M}$ in which one or more chemical reactions in the reaction set $\mathcal{R}$ are occurring. Further, the system is at constant temperature and pressure. 

Then, this system is at equilibrium (or the minimum energy-steady-state for an open system) when the differential change in the total Gibbs energy is zero:

```{math}
:label: eqn-eq-condition-no-phase-no-reaction
\sum_{i\in\mathcal{M}}G^{\circ}_{i}dn_{i} + RT\sum_{i\in\mathcal{M}}dn_{i}\ln\hat{a_{i}} = 0
```

where $G^{\circ}_{i}$ denotes the Gibbs energy for pure component $i$ at a reference state, $\hat{a}_{i}$ denotes the ratio of fugacity, $dn_{i}$ denotes the differential change in the number of moles of component $i$, $R$ denotes the ideal gas constant and $T$ denotes the system temperature.

````
{prf:ref}`defn-eq-condition-dg-multiple-reactions` is theoretically important, but a few items must be addressed to make it actionable. First, let's compute the change in the number of moles. The differential change in the number of moles of component $i$ is related to the extent of the reaction. Suppose we have a reaction set $\mathcal{R}$, then we can write $dn_{i}$ as:

```{math}
dn_{i} = \sum_{r\in\mathcal{R}}\sigma_{ir}d\epsilon_{r}\qquad\forall{i}\in\mathcal{M}
```


where $\sigma_{ir}$ denotes the stoichiometric coefficient for component $i$ in reaction $r$, and $d\epsilon_{r}$ represents the differential change in the extent of the reaction for reaction $r$. Let's consider a single reaction; thus, the reaction set $\mathcal{R}$ contains only one element (say reaction 1), and the differential change in the moles of component $i$ is given by:

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
\sum_{i\in\mathcal{M}}\sigma_{i1}\ln\hat{a_{i}} = -\frac{1}{RT}\left(\sum_{i\in\mathcal{M}}G^{\circ}_{i}\sigma_{i1}\right)
```

Equation {eq}`eqn-eq-ex-almost` can be further simplified to give an expression for the reaction equilibrium constant:

````{prf:definition} Equilibrium constant

Consider a single chemical reaction in a well-mixed system with species set $\mathcal{M}$ at constant temperature and pressure. Then, at equilibrium, the total Gibbs energy is given by:

```{math}
:label: eqn-eq-ex-almost-ln
\ln\left(\prod_{i\in\mathcal{M}}\hat{a}^{\sigma_{i1}}_{i}\right) = -\frac{1}{RT}\left(\sum_{i\in\mathcal{M}}G^{\circ}_{i}\sigma_{i1}\right)
```

where $\hat{a}_{i} = \hat{f}_{i}/f_{i}$. Equation {eq}`eqn-eq-ex-almost-ln` can be re-written in terms of the equilibrium constant $K$:

```{math}
:label: eqn-eq-constant
K \equiv \prod_{i\in\mathcal{M}}\hat{a}^{\sigma_{i1}}_{i}
```

which gives the familiar expression:

```{math}
K = \exp\left[-\frac{1}{RT}\left(\sum_{i\in\mathcal{M}}G^{\circ}_{i}\sigma_{i1}\right)\right]
```
````

### Example
* [Single liquid phase reaction from Glycolysis in _E.coli_. Download the ENGRI-1120-DGM-SingleReaction-Ideal-Liquid.ipynb notebook from GitHub](https://github.com/varnerlab/ENGRI-1120-IntroToChemE-Example-Notebooks)

(content:references:cre-vapor-phase)=
## Vapor-phase equilibrium constant
The vapor phase fugacity for compnent $i$ in chemical species set $\mathcal{M}$ is given by:

```{math}
\hat{f}^{v}_{i} = y_{i}\hat{\phi}_{i}P\qquad{i}\in\mathcal{M}
```

where $y_{i}$ denotes the mole fraction of component $i$, $\hat{\phi}_{i}$ denotes the fugacity coefficient for component $i$,  Subsituiting the vapur phase fugacity into Eqn. {eq}`eqn-eq-ex-almost-ln` gives using a standard pressure $P^{\circ}$ as the single component reference state gives:

```{math}
\ln\prod_{i\in\mathcal{M}}\left(\frac{y_{i}\hat{\phi}_{i}P}{P^{\circ}}\right)^{\sigma_{i1}} = -\frac{1}{RT}\left(\sum_{i\in\mathcal{M}}G^{\circ}_{i}\sigma_{i1}\right)
```

````{prf:definition} Ideal Gas Phase Equilibrium Constant
:label: eqn-gas-phase-ideal-K

Suppose we have a single gas phase reaction occurring in a well-mixed closed chemical reactor containing species set $\mathcal{M}$. Further, suppose the gas phase is ideal. Then, the ideal gas phase equilibrium constant is given by:

```{math}
:label: eqn-ideal-gas-phase-reaction
K\left(\frac{P}{P^{\circ}}\right)^{-\sigma_{1}} = \prod_{i\in\mathcal{M}}\left(y_{i}\right)^{\sigma_{i1}}
```

where $\sigma_{1}$ denotes the sum of the stoichiometric coefficients for reaction 1, $y_{i}$ denotes the mole fraction of component $i$, and $\sigma_{i1}$ represents the stoichiometric coefficient for component $i$ in reaction 1. 

````

### Extent and the gas-phase equilibrium constant
In the case of vapor phase reactions, the extent of the reaction is related to the equilibrium constant through the mole fraction.
Consider a single gas phase reaction with extent $\epsilon_{i}$ (units: mol). We know from the definition of the gas phase mole fraction for component $i$ (in a system with species set $\mathcal{M}$) given by:

```{math}
y_{i} = \frac{n_{i}}{\displaystyle\sum_{j\in\mathcal{M}}n_{j}}\qquad\forall{i}\in\mathcal{M}
```

that moles of component $i$ are related to the extent of the reaction:

```{math}
n_{i} = n^{\circ}_{i}+\sigma_{i1}\epsilon_{1}\qquad\forall{i}\in\mathcal{M}
```

where $n^{\circ}_{i}$ is the number of moles of component $i$ initially (before the reaction), $\sigma_{i1}$ denotes the 
stoichiometric coefficient for component $i$ in reaction $1$, and $\epsilon_{1}$ denotes the extent of reaction 1. 
Substituting the moles of component $i$ into the mole fraction expression gives:

```{math}
:label: eqn-mol-frac-extent-vapor
y_{i} = \frac{n^{\circ}_{i}+\sigma_{i1}\epsilon_{1}}{\displaystyle\sum_{j\in\mathcal{M}}n^{\circ}_{j}+\sigma_{j1}\epsilon_{1}}
```

````{prf:observation} Ideal gas phase equilibrium constant in terms of the extent
:label: obs-vapor-phase-eq-constant-extent

Substituting the mole fraction given in Eqn. {eq}`eqn-mol-frac-extent-vapor` into the ideal vapor phase equilibrium constant in Eqn. {eq}`eqn-ideal-gas-phase-reaction` gives an expression that relates the equilibrium constant with the extent of the reaction:

```{math}
K\left(\frac{P}{P^{\circ}}\right)^{-\sigma_{1}} = \prod_{i\in\mathcal{M}}\left[\frac{n^{\circ}_{i}+\sigma_{i1}\epsilon_{1}}{\displaystyle\sum_{j\in\mathcal{M}}
\left(n^{\circ}_{j}+\sigma_{j1}\epsilon_{1}\right)}\right]^{\sigma_{i1}}
```

The system pressure will also be a function of the extent of the reaction. Thus, we need an equation of state (EOS) that relates the moles in a system to the pressure.
````


(content:references:cre-liquid-phase)=
## Liquid-phase equilibrium constant
The liquid phase fugacity for component $i$ in chemical species set $\mathcal{M}$ is given by:

```{math}
\hat{f}_{i}^l = x_{i}\hat{\gamma}_{i}f^{l}_{i}
```

where $x_{i}$ denotes the liquid mole fraction of component $i$, $\hat{\gamma}_{i}$ denotes the activity coefficient for component $i$ (describes liquid phase non-ideality) and $f^{l}_{i}$ denotes the reference fugacity for pure component $i$ in the liquid phase. Substituting the fugacity into the equilibrium expression (and canceling the reference states) gives:

```{math}
\ln\prod_{i\in\mathcal{M}}\left(x_{i}\hat{\gamma}_{i}\right)^{\sigma_{i1}} = -\frac{1}{RT}\left(\sum_{i\in\mathcal{M}}G^{\circ}_{i}\sigma_{i1}\right)
```

````{prf:definition} Ideal Liquid Phase Equilibrium Constant
:label: eqn-liquid-phase-ideal-K

Suppose we have a single liquid phase reaction occurring in a well-mixed closed chemical reactor containing species set $\mathcal{M}$. Further, suppose the liquid phase is ideal. Then, the ideal liquid phase equilibrium constant is given by:

```{math}
:label: eqn-ideal-liquid-phase-reaction
K = \prod_{i\in\mathcal{M}}\left(x_{i}\right)^{\sigma_{i1}}
```

where $x_{i}$ denotes the mole fraction of component $i$ in the liquid and $\sigma_{i1}$ denotes the stoichiometric coefficient for component $i$ in reaction 1. 
````

### Extent and the liquid-phase equilibrium constant
In the case of liquid phase reactions, the extent of the reaction is related to the equilibrium constant through the mole fraction.
Consider a single liquid phase reaction with extent $\epsilon_{i}$ (units: mol). We know from the definition of the liquid phase mole fraction for component $i$ (in a system with species set $\mathcal{M}$) given by:

```{math}
x_{i} = \frac{n_{i}}{\displaystyle\sum_{j\in\mathcal{M}}n_{j}}\qquad\forall{i}\in\mathcal{M}
```

that the moles of component $i$ are related to the extent of the reaction:

```{math}
n_{i} = n^{\circ}_{i}+\sigma_{i1}\epsilon_{1}\qquad\forall{i}\in\mathcal{M}
```

where $n^{\circ}_{i}$ is the number of moles of component $i$ initially (before the reaction), $\sigma_{i1}$ denotes the 
stoichiometric coefficient for component $i$ in reaction $1$, and $\epsilon_{1}$ denotes the extent of reaction 1. 
Substituting the moles of component $i$ into the mole fraction expression gives:

```{math}
:label: eqn-mol-frac-extent
x_{i} = \frac{n^{\circ}_{i}+\sigma_{i1}\epsilon_{1}}{\displaystyle\sum_{j\in\mathcal{M}}n^{\circ}_{j}+\sigma_{j1}\epsilon_{1}}
```

````{prf:observation} Ideal liquid phase equilibrium constant in terms of the extent
:label: obs-liquid-phase-eq-constant-extent

Substituting the mole fraction given in Eqn. {eq}`eqn-mol-frac-extent` into the ideal liquid phase equilibrium constant in Eqn. {eq}`eqn-ideal-liquid-phase-reaction` gives an expression that relates the equilibrium constant with the extent of the reaction:

```{math}
K = \prod_{i\in\mathcal{M}}\left[\frac{n^{\circ}_{i}+\sigma_{i1}\epsilon_{1}}{\displaystyle\sum_{j\in\mathcal{M}}n^{\circ}_{j}+\sigma_{j1}\epsilon_{1}}\right]^{\sigma_{i1}}
```

for a single ideal liquid phase reaction.

````

<!-- ## Equilibrium calculations for a closed system
We can subsitute $\bar{G}_{i}$ into the expression for $\hat{G}$, and after some algebraic magic, we get:

$$\frac{1}{RT}\left(\hat{G}-\sum_{i=1}^{\mathcal{M}}n_{i}^{\circ}G_{i}^{\circ}\right) = 
\epsilon_{1}\frac{\Delta{G}^{\circ}}{RT}+\sum_{i=1}^{\mathcal{M}}n_{i}\ln\hat{a}_{i}$$

The first term on the right-hand side is the extent of reaction times the scaled Gibbs energy of reaction; we can think of this term as how much of the Gibbs energy of reaction we recover as the reaction proceeds to the right. The second term describes how the overall Gibbs energy changes as the composition changes (at a fixed T, P). In particular, we know that:

$$n_{i} = n_{i}^{\circ}+\sigma_{i1}\epsilon_{1}\qquad{i=1,2,\dots,\mathcal{M}}$$

and (for an ideal liquid reaction mixture) we know that $\hat{a}_{i}=x_{i}$ where:

$$x_{i} = \frac{n_{i}}{\sum_{j=1}^{\mathcal{M}}n_{j}}\qquad{i=1,2,\dots,\mathcal{M}}$$

Thus, we need to search for $\epsilon_{1}$ (subject to bounds on permissible values of the extent) such that the total Gibbs energy $\hat{G}$ is at a minimum. Once we have the equilibrium extent of reaction, we can compute the equilibrium constant (for an ideal liquid phase reaction at moderate pressures):

$$K_{eq} = \prod_{i=1}^{\mathcal{M}}x_{i}^{\sigma_{i1}}$$ -->

(content:references:cre-eq-closed-system)=
## Closed systems and multiple coupled reactions
Suppose we have the species set $\mathcal{M}$ and the reaction set $\mathcal{R}$ in a closed system.
For multiple reactions in a closed system, the total Gibbs energy expression:

$$\hat{G} = \sum_{i\in\mathcal{M}}\bar{G}_{i}n_{i}$$

becomes:

```{math}
:label: eqn-closed-DGM-multiple-reactions
\frac{1}{RT}\left(\hat{G}-\sum_{i\in\mathcal{M}}n_{i}^{\circ}G_{i}^{\circ}\right) = \sum_{j\in\mathcal{R}}\epsilon_{j}\left(\frac{\Delta{G}_{j}^{\circ}}{RT}\right) + \sum_{i\in\mathcal{M}}n_{i}\ln\hat{a}_{i}
```

where the number of mol for species _i_ is given by:

```{math}
n_{i} = n_{i}^{\circ} + \sum_{r\in\mathcal{R}}\sigma_{ir}\epsilon_{r}
```

The quantity $\Delta{G}^{\circ}_{j}$ denotes the Gibbs energy of reaction for reaction _j_ (units: kJ/mmol), and $\hat{a}_{i}$ denotes the ratio of fugacity for component _i_. In an ideal liquid solution $\hat{a}_{i}$ reduces to:

```{math}
\ln\hat{a}_{i} = \ln{x_{i}}
```

where $x_{i}$ denotes the mole fraction of component _i_ in the liquid. For an ideal gas phase reaction, $\hat{a}_{i}$ reduces to:

```{math}
\ln\hat{a}_{i} = \ln{y_{i}}
```

where $y_{i}$ denotes the mole fraction of component _i_ in the gas.

### Solution approach
To estimate the $\mathcal{R}\times{1}$ equilibrium extent _vector_, we need to solve a _constrained optimization problem_. In particular, we minimize the Gibbs energy expression given in Eqn. {eq}`eqn-closed-DGM-multiple-reactions`, subject to constraints. Our decision variables (what we are looking for) are the extents of reaction $\epsilon_{i},\forall{i}\in\mathcal{R}$ while the constraints are bounds on each extent $\epsilon_{i}\in\left[0,\star\right],\forall{i}$ and physical constants on the number of moles $n_{i}\geq{0},\forall{i}$ (the number of moles must be non-negative).

### Example
* [Multiple coupled reactions in Glycolysis in _E.coli_. Download the ENGRI-1120-DGM-MultipleReaction-Ideal-Liquid.ipynb notebook from GitHub](https://github.com/varnerlab/ENGRI-1120-IntroToChemE-Example-Notebooks)

(content:references:cre-eq-open-system)=
## Open systems and multiple coupled reactions
For an open system, instead of thinking about the equilibrium extent $\epsilon$, we'll compute the open extent of reaction $\dot{\epsilon}$ (units: mol/t) that gives the lowest energy. The Gibbs energy for the species set $\mathcal{M}$ in a well-mixed open system is given by:

```{math}
:label: eqn-total-gibbs-energy-sum-open
\hat{G} = \sum_{i\in\mathcal{M}}\bar{G}_{i}\dot{n}_{i}
```

where $\hat{G}$ is the overall open Gibbs energy (units: energy/time), $\bar{G}_{i}$ is the partial molar Gibbs energy for component $i$ (units: energy/mol), and $\dot{n}_{i}$ denotes the species mole flow rate of component $i$ (units: mole/time). Substituting the partial molar Gibbs energy Eqn {eq}`eqn-g-bar-w-a` into the open Gibbs expression gives two terms:

```{math}
\hat{G} = \sum_{i\in\mathcal{M}}\dot{n}_{i}G_{i}^{\circ}+ RT\sum_{i\in\mathcal{M}}\dot{n}_{i}\ln\hat{a}_{i}
```

where $\hat{a}_{i}$ is the ratio of fugacity for component $i$, $G_{i}^{\circ}$ denotes the Gibbs energy for pure component $i$ at the reference state and $\dot{n}_{i}$ denotes the species mole flow rate for component $i$.

From our previous discussion of [species mole balances equations](../chapter-1-dir/material-balances.md), we know the relationship between the number of moles of species $i$ and the open extent of reaction $\dot{\epsilon}_{j}$ in a well-mixed system at steady-state:

```{math}
\dot{n}_{i} = -\frac{1}{\displaystyle\sum_{s\in\mathcal{S}^{-}}v_{s}}\cdot\left(\sum_{s\in\mathcal{S}^{+}}\nu_{s}\dot{n}_{s,i} + \sum_{r\in\mathcal{R}}\sigma_{ir}\dot{\epsilon}_{r} \right)
```

where we partitioned the stream set into streams entering the system $\mathcal{S}^{+}$ and steams exiting the system $\mathcal{S}^{-}$.

---

## Summary
In this lecture, we looked at chemical reactions from the energy perspective. In particular, we related the extent of reaction to the Gibbs energy minimum for both an open and closed system. We started by defining a theoretical picture of the Gibbs energy in the presence of chemical reactions and then applied this theory to a single gas and liquid phase reaction. Finally, we
explored the case of open systems and multiple coupled reactions. 

In particular, in this lecture we:
* Developed a {ref}`content:references:theory-of-cre` describing the Gibbs energy of a system with chemical reactions
* Developed expressions for the {ref}`content:references:cre-vapor-phase` and {ref}`content:references:cre-liquid-phase`
* Developed tools for computing extent of reaction for {ref}`content:references:cre-eq-closed-system` and {ref}`content:references:cre-eq-open-system`