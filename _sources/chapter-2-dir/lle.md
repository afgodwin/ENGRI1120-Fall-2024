# Liquid Liquid Equilibrium

## Introduction
We rely on liquid-liquid Equilibrium (LLE) every day through separation processes that depend on liquid phase extraction to purify a chemical product or in everyday products such as foods, cosmetics, and other personal care products. 

Consider emulsions; an emulsion is a mixture of two or more liquids that are usually immiscible owing to liquid-liquid phase separation. However, the addition of a third stabilizing agent makes emulsions stable. For example, Mayonnaise is an oil-in-water emulsion stabilized with egg yolk lecithin, while butter and margarine are examples of water-in-fat emulsions. In pharmaceutics, hairstyling, personal hygiene, and cosmetics, emulsions are also frequently used, e.g., these emulsions may be called creams, ointments, liniments (balms), pastes, films, or liquids, depending primarily on their oil-to-water ratios. Thus, liquid-liquid equilibrium is a critical topic that impacts your daily life.

In this lecture, we will:
* Develop a {ref}`content:references:lle-general-model` that we can use, in combination with total and species mole balances, to design liquid-liquid equilibrium operations
* Develop {ref}`content:references:lle-activity-coefficients-section` which model the behavior of liquid solutions. In particular, we'll introduce {ref}`content:references:lle-two-suffix-marguels-model` for binary systems and {ref}`content:references:lle-multicomponet-model`.
* Develop models that describe various {ref}`content:references:lle-application-models`, e.g., single- and multiple-stage equilibrium extractions.

---

(content:references:lle-general-model)=
## General Liquid-Liquid Equilibrium model
[The fugacity matching condition](./single-component-phase-eq.md) given by {prf:ref}`defn-fugacity-matching-cond-eq`, in combination with phase specific fugacity models, gives us tools to design phase equilibrium processes. However, when considering liquid-liquid equilibrium we need to redefine the liquid-phase refernce condition. As a reminder, when considering vapor-liquid equilibrium, the liquild phase fugacity model was given by for a mixture with species set $\mathcal{M}$:

```{math}
\hat{f}^{l}_{i} = x_{i}\gamma_{i}f_{i}\qquad\forall{i}\in\mathcal{M}
```
where we assumed a particular form for the reference fugacity $f_{i}$, in particular, the Lewis-Randall reference state which turned the liquid state into an equivalent vapor state in equilibrium. However, there is no vapor state when considering liquid-liquid equilibrium. 


````{prf:definition} General Liquid-Liquid Equilibrium Model
:label: defn-gen-lle-conditions

Let’s consider a system with the composition set $\mathcal{M}$ in liquid-liquid equilibrium. The fugacity matching condition, along with the phase-specific models, gives the relationship between liquid phase $\alpha$ and $\beta$:

```{math}
\hat{\gamma}^{\alpha}_{i}x^{\alpha}_{i}f^{\alpha}_{i} = \hat{\gamma}^{\beta}_{i}x^{\beta}_{i}f^{\beta}_{i}\qquad\forall{i}\in\mathcal{M}
```

where the term $\hat{\gamma}^{\star}_{i}$ denotes the activity coefficient for component $i$, $x^{\star}_{i}$ is the mole fraction of component $i$, and $f^{\star}_{i}$ is the liquid reference state fugacity for liquid phase $\star$. The liquid reference state fugacity assumes a pure component $i$ reference state; thus, if pure component $i$ is a liquid at the equilibrium conditions, by convention, we let:

```{math}
:label: eqn-lle-liquid-ref-state
f^{\alpha}_{i} = f^{\beta}_{i} \qquad\forall{i}\in\mathcal{M}
```

Eqn. {eq}`eqn-lle-liquid-ref-state` says we model the reference state as an equilibrium between phases $\alpha$ and $\beta$ for pure component $i$. This reference state gives the liquid-liquid equilibrium design relationship:

```{math}
:label: eqn-lle-design-eqn
\hat{\gamma}^{\alpha}_{i}x^{\alpha}_{i} = \hat{\gamma}^{\beta}_{i}x^{\beta}_{i}\qquad\forall{i}\in\mathcal{M}
```
````

(content:references:lle-activity-coefficients-section)=
## Models for Activity Coefficients
To build models of the liquid-phase activity coefficients, we expand the excess Gibbs energy in terms of experimentally measurable quantities. 
The total excess Gibbs energy for a mixture of $\mathcal{M}$ components is given by:

```{math}
:label: eqn-total-gibbs-m-component-gamma
\frac{G^{E}}{RT} = \sum_{i\in\mathcal{M}}x_{i}\ln\hat{\gamma}_{i}
```

where $G^{E}$ is the total Gibbs excess energy for the liquid phase (units: energy/mole); the Gibbs excess energy $G^{E}$ is the energy difference between the real system and a hypothetical ideal reference state. However, Eqn. {eq}`eqn-total-gibbs-m-component-gamma` is not physical because we can’t measure $G^{E}$. Instead, we must propose _mathematical models_ for $G^{E}$ that are written in physical quantities and then match these models with the right-hand side of Eqn. {eq}`eqn-total-gibbs-m-component-gamma`

````{prf:remark} Can we use any mathematical model for $G^{E}$?
:label: remark-ge-conditions
Sort of. Mathematical models for $G^{E}$ can be _any_ model that satisfies two conditions. First, the Gibbs excess energy must disappear in a pure material, e.g., at the endpoints in a binary mixture:

$$
G^{E} = 
\begin{cases}
0 & x_{1} = 1 \\
0 & x_{2} = 1 \\ 
\end{cases}
$$

And any Gibbs excess model must also satisfy the [Gibbs-Duhem equation](https://en.wikipedia.org/wiki/Gibbs–Duhem_equation):

```{math}
:label: eqn-Gibbs-duhem
\sum_{i\in\mathcal{M}}x_{i}d\ln\hat{\gamma}_{i} = 0
```

Any model that satisfies these conditions can be used; however, whether it works well in practice is unknown until we try it. 

````

(content:references:lle-two-suffix-marguels-model)=
### Two-suffix Margules activity model
One model that satisfies the conditions outlined in {prf:ref}`remark-ge-conditions` is the [Margules activity model](https://en.wikipedia.org/wiki/Margules_activity_model). The [Margules activity model](https://en.wikipedia.org/wiki/Margules_activity_model) is a simple thermodynamic model for the excess Gibbs energy of a liquid mixture introduced in 1895 by [Max Margules](https://en.wikipedia.org/wiki/Max_Margules). Margules expressed the excess Gibbs energy as a power series in mole fraction (for the binary case):

```{math}
:label: eqn-margules-model
\frac{G^{E}}{RT} = x_{1}x_{2}\left(A_{12}x_{1}+A_{21}x_{2}\right)
```

where $A_{ij}$ (units: dimensionless) are parameters that deascribe the strength of interactions between molecules $i$ and $j$. 

````{prf:definition} Margules activity model
:label: obs-margules-activity
After some (magical) manipulation of Eqn. {eq}`eqn-margules-model` and the definition of partial molar Gibbs excess energy given in Eqn. {eq}`eqn-liq-intro-pmge-gamma`, the [Margules activity model](https://en.wikipedia.org/wiki/Margules_activity_model) gives (for a binary mixture):

$$
\begin{eqnarray}
\ln\hat{\gamma}_{1} &=& x_{2}^{2}\left(A_{12}+2\left(A_{21}-A_{12}\right)x_{1}\right)\\
\ln\hat{\gamma}_{2} &=& x_{1}^{2}\left(A_{21}+2\left(A_{12}-A_{21}\right)x_{2}\right)
\end{eqnarray}
$$

__Values for $A_{ij}$__: We can perform infinite dilution (thought) experiments to estimate the parameters $A_{ij}$ (and get a better understanding of their meaning).
For example, consider the case when $x_{1}\rightarrow{0}$ (but never reaches zero, say there is one molecule of type 1 left), then:

```{math}
\ln\hat{\gamma}_{1}^{\infty} = A_{12}
```

Conversely, when $x_{2}\rightarrow{0}$ (but never reaches zero), then:


```{math}
\ln\hat{\gamma}_{2}^{\infty} = A_{21}
```

Thus, the $A_{ij}$ parameters can be thought of as representing:
* The parameter $A_{12}$ describes the forces felt on molecules of type 1 by molecules of type 2 
* The parameter $A_{21}$ describes the forces felt on molecules of type 2 by molecules of type 1

````

(content:references:lle-multicomponet-model)=
### Activity Coefficients for Multicomponent Mixtures
When dealing with binary mixtures, we can use the {ref}`content:references:lle-two-suffix-marguels-model` to estimate the activity coefficients $\ln\hat{\gamma}_{i}$; where the $A_{ij}$ parameters that appear in these models are tabulated in reference books for various mixtures. 

However, in liquid-liquid extraction applications, or other applications such as stabilized emulsions, we immediately have a problem; we have _at least three components_ and all of our theory is for binary systems. For example, in the most straightforward liquid-liquid extraction, we have solvent one, solvent two, and the material dissolved in solvent one that we want to extract. Thus, the tools we developed for binary mixtures, e.g., the Margules model, are not applicable. 

To model multicomponent mixtures, let's introduce another approach, the [Wilson Model](https://pubs.acs.org/doi/abs/10.1021/ja01056a002), to compute the activity coefficients. While we focus on the [Wilson model](https://pubs.acs.org/doi/abs/10.1021/ja01056a002) here, many other prominent models drew inspiration from Wilson, such as the [Non-Random Two Liquid (NRTL)](https://en.wikipedia.org/wiki/Non-random_two-liquid_model) model, that are also widely used for multicomponent mixtures.

(content:references:lle-multicomponet-wilson-model)=
### Multicomponent Wilson Model
The Wilson model is a type of _local composition model_.
The local composition of a liquid solution differs from the overall bulk composition. The local composition is governed by short-range interactions, e.g., molecules in different molecular orientations, interactions between other-sized molecules, and intermolecular forces. The concept of modeling the behavior of solutions by accounting for these short-range interactions was pioneered by Wilson {cite}`Wilson1964`.

The excess Gibbs energy proposed by Wilson that accounts for the local composition (or short-range) interactions is given by the expression:

```{math}
:label: eqn-gibbs-energy-wilson-model
\frac{G^{E}}{RT} = -\sum_{i\in\mathcal{M}}x_{i}\ln\left(\sum_{j\in\mathcal{M}}x_{j}\Lambda_{ij}\right)
```

````{prf:definition} Multicomponent Wilson Activity Model
:label: defn-multicomponent-wilson-model

Starting from excess Gibbs energy expression postulated by Wilson shown in Eqn {eq}`eqn-gibbs-energy-wilson-model`, after some (magical) manipulation, we arrive at an expression for the activity coefficient for component $i$ in the species set $\mathcal{M}$

```{math}
:label: eqn-wilson-model-gamma
\displaystyle{
\ln\hat{\gamma}_{i} = 1 - \ln\left(\sum_{j\in\mathcal{M}}x_{j}\Lambda_{ij}\right) - \sum_{k\in\mathcal{M}}\frac{x_{k}\Lambda_{ki}}{\sum_{j\in\mathcal{M}}x_{j}\Lambda_{kj}}}
```

where the interaction term(s) $\Lambda_{ij}$ are given by:

$$
\Lambda_{ij} = \frac{V_{j}}{V_{i}}\exp\left(\frac{-a_{ij}}{RT}\right)
$$

````

(content:references:lle-application-models)=
## Liquid-Liquid Equilibrium Applications
Fill me in for Thursday's lecture.

---

## Summary
In this lecture, we:
* Developed a {ref}`content:references:lle-general-model` that we can use, in combination with total and species mole balances, to design liquid-liquid equilibrium operations
* Developed {ref}`content:references:lle-activity-coefficients-section` which model the behavior of liquid solutions. In particular, we introduced {ref}`content:references:lle-two-suffix-marguels-model` for binary systems and {ref}`content:references:lle-multicomponet-model`.
* Developed models that described various {ref}`content:references:lle-application-models`, e.g., single- and multiple-stage equilibrium extractions.