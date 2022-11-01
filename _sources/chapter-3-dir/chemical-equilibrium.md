# Introduction to Chemical Reaction Equilibrium

## Introduction

In this lecture, we will:
* {ref}`content:references:theory-of-cre`
* {ref}`content:references:cre-eq-closed-system`
* {ref}`content:references:cre-eq-multiple-reactions`

---

(content:references:theory-of-cre)=
## Theory of a Single Reaction
For a single reaction involving the chemical component set $\mathcal{M}$, the Gibbs energy can be written as the sum of the partial molar Gibbs energies (what we called G-bar) at constant T,P:

$$\hat{G} = \sum_{i\mathcal{M}}^{\mathcal{M}}\bar{G}_{i}n_{i}$$

where $\hat{G}$ denotes the total Gibbs energy for the reaction mixture (units: kJ), $\bar{G}_{i}$ denotes the partial molar Gibbs energy for chemical component $i$ (units: kJ/mol) and $n_{i}$ denotes the number of mols of chemical component $i$. From classical thermodynamics we know that the partial molar Gibbs energy for chemical species $i$ is given by:

$$\bar{G}_{i} = G_{i}^{\circ} + RT\ln\hat{a}_{i}$$

where $G_{i}^{\circ}$ denotes the Gibbs energy for pure component $i$ at a reference state, and $\hat{a}_{i}$ denotes the ratio of fugacities (mixture at reaction T,P/pure component $i$ at reference conditions);  the facgacity models are the same expressions that we developed in our disucssion of [phase equilibrium](../chapter-2-dir/chapter-2-intro.md).

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