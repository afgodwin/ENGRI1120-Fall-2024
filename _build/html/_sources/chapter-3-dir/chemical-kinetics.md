# Introduction to Chemical Reaction Kinetics

## Introduction
The _kinetics_ of a chemical reaction describes the _rate_ at which the reaction proceeds as a function of the conditions in the reactor vessel. Kinetic rate laws have units of $\star$mol/volume-time, and their mathematical form varies significantly with the type of reaction being considered. 

In this lecture, we will:

* Introduce {ref}`content:references:conc-balance-eq` and a {ref}`content:references:model-kinetics-general-model`
* Introduce {ref}`content:references:mass-action-kinetics`, which is a simplified kinetic model.
* Introduce {ref}`content:references:kinetic-e-catalyzed-rxn`. Enzymes are biological polymers that carry out a diverse array of biological functions, including unique chemistry.  

---

(content:references:conc-balance-eq)=
## Concentration balance equations
When describing systems with chemical reactions where we write reaction rate expressions in terms of 
concentration, e.g., mole per unit volume basis, it is inconvient to use mole or mass based units.
In these cases, we need a new type of balance equation, the concentration balance. 

Starting from [species mole balance equations](../chapter-1-dir/material-balances.md), we formulate the concentration balance by replacing moles with concentration units ({prf:ref}`defn-species-conc-balance`):

````{prf:definition} Open species concentration balance
:label: defn-species-conc-balance

Let $n_{i}$ denote the number of moles of chemical component $i$ in the system 
(units: $\star$moles, e.g., mmol or  $\mu$mol). Further, denote the chemical species in the system with the set $\mathcal{M}$, and the set of streams flowing into (or from) the system as $\mathcal{S}$. 

Then, the number of moles of chemical component $i$ in the system is described by an 
_open species mass balance equation_:

```{math}
\sum_{s\in\mathcal{S}}\nu_{s}\dot{n}_{s,i} + \dot{n}_{G,i} = \frac{dn_{i}}{dt}
\qquad\forall{i}\in\mathcal{M}
```

However, we can re-write the number of moles of species $i$ as:

```{math}
n_{i} = C_{i}V\qquad\forall{i}\in\mathcal{M}
```

where $C_{i}$ denotes the concentration of species $i$ (units: mole per volume), and $V$ (units: volume) denotes the volume of the system. Thus, we can re-write the species mole balance in concentration units as:

```{math}
:label: eqn-concentration-balance
\sum_{s\in\mathcal{S}}\nu_{s}C_{s,i}\dot{V}_{s} + \dot{C}_{G,i}V = \frac{d}{dt}\left(C_{i}V\right)\qquad\forall{i}\in\mathcal{M}
```

where $\dot{V}_{s}$ denotes the volumetric flow rate for stream $s$ (units: volume/time), $C_{s,i}$ denotes the concentration of component $i$ in stream $s$ (units: concentration), and $\dot{C}_{G,i}$ denotes the rate of generation of component $i$ by chemical reaction (units: concentration/time).

````

The concentration generation terms in Eqn. {eq}`eqn-concentration-balance` describe the impact of chemical reactions. Previously, we described reactions using the [open extent of reaction](https://varnerlab.github.io/ENGRI-1120-IntroToChemE-Book/chapter-1-dir/material-balances.html#content-references-open-extent-of-reaction) $\dot{\epsilon}_{i}$ to describe chemical reactions. However, we've never defined what $\dot{\epsilon}_{i}$. 

### Open extent and the reaction rate
The [open extent of reaction](https://varnerlab.github.io/ENGRI-1120-IntroToChemE-Book/chapter-1-dir/material-balances.html#content-references-open-extent-of-reaction) $\dot{\epsilon}_{i}$ has two interpretations, a [steady-state thermodynamic interpretation](./chemical-equilibrium.md), and a time-dependent kinetic one in which $\dot{\epsilon}_{i}$ is related to the rate of reaction; let's start with the kinetic interpretation. 

````{prf:definition} Concentration generation terms
:label: defn-conc-gen-terms

Let the set of species $\mathcal{M}$ participate in the chemical reaction set $\mathcal{R}$. Further, define the extent of reaction for reaction $j$ as:

```{math}
:label: eqn-extent-kinetic-model
\epsilon_{j}\equiv\hat{r}_{j}V\qquad\forall{j}\in\mathcal{R}
```

where $\hat{r}_{j}$ denotes the reaction rate for reaction $j$ (units: mole/volume-time). Then, the generation terms for species $i$ in the concentration balance equation can be written as:

```{math}
:label: eqn-concentration-gen-terms
\dot{C}_{G,i}V = \sum_{j\in\mathcal{R}}\sigma_{ij}\hat{r}_{j}V\qquad\forall{i}\in\mathcal{M}
```

where $\hat{r}_{j}$ denotes the rate of reaction $j$ (units: mol/volume-time) and
$\sigma_{ij}$ denotes the stoichiometric coefficient for species $i$ in reaction $j$:
* If $\sigma_{ij}>0$ then species $i$ is _produced_ by reaction $j$, i.e., species $i$ is a product of reaction $j$ 
* If $\sigma_{ij}=0$ then species $i$ is _not connected to_ reaction $j$
* If $\sigma_{ij}<0$ then species $i$ is _consumed_ by reaction $j$, i.e., species $i$ is a reactant of reaction $j$.

````

(content:references:model-kinetics-general-model)=
## General model of chemical reaction kinetics
The rate of a chemical reaction can be dependent upon the concentration of both the reactants, and potnetially the products as well as constants called rate constants. Thus, a general model for the _net_ rate of reaction, involving the species set $\mathcal{M}$, is given by:

```{math}
:label: eqn-general-model-rate-1
\hat{r}_{1} = k_{1}\prod_{i\in\mathcal{M}}\left[X_{i}\right]^{\alpha_{i1}} - k_{1}^{\prime}\prod_{j\in\mathcal{M}}\left[X_{j}\right]^{\beta_{j1}}
```

The first product term in Eqn. {eq}`eqn-general-model-rate-1` describes the forward rate (reactants $\rightarrow$ products), while second product term decribes the reverse rate (prodcuts $\rightarrow$ reactants). The terms $\left[X_{i}\right]$ denotes the concentration of component $i\in\mathcal{M}$, and $\alpha_{i1}$ and $\beta_{i1}$ denote the _reaction order_ of component $i$ in reaction $\hat{r}_{1}$. The values of the reation orders $\alpha_{i1}$ and $\beta_{i1}$ depend upon the reaction, and may _not_ always be integer values. Finally, the quantities $k_{1}$ and $k_{1}^{\prime}$ denote the rate constant for the forward and reverse directions, respectively. Rate constants have various units depending upon the values of $\alpha_{i1}$ and $\beta_{i1}$. 

```{prf:remark} Are reaction orders integers?
:label: remark-reaction-orders-no-integers

There is no requirement that $\alpha_{i1}$ and $\beta_{i1}$ be integers (or the stoichiometric coefficients). This is often only true when we have a complete (or simplified) picture of the chemistry that is occurring. In real-life, fractional values for $\alpha_{i1}$ and $\beta_{i1}$ are common in many application areas.
```  

<!-- Let's start by considering the simple non-enzymatic (no catalyst) _reversible_ reaction:

$$A+B\leftrightharpoons{C}$$ -->

(content:references:mass-action-kinetics)=
### Mass action kinetics
Let's consider a simplification to the general rate law in Eqn. {eq}`eqn-general-model-rate-1`. Assume the forward and reverse reactions are [elementary reactions](https://en.wikipedia.org/wiki/Elementary_reaction); an elementary reaction is a chemical reaction in which one or more chemical species react directly to form products in a single reaction step where no reaction intermediates are required to describe the reaction on a molecular scale. 

Elementary reactions can be described by the [law of mass action](https://en.wikipedia.org/wiki/Law_of_mass_action). The [law of mass action](https://en.wikipedia.org/wiki/Law_of_mass_action) assumes that the net rate of a chemical reaction is proportional to the concentration of the components participating in the reaction raised to the $-{1}\times$ the stoichiometric coefficient of that component in _a particular reaction direction_:

````{prf:definition} Mass action kinetics
:label: defn-mass-action-rate-law

Let the set of species $\mathcal{M}$ participate in a reversible elementary reaction with the rate $\hat{r}_{j}$. 
Further, let the reactants of $\hat{r}_{j}$ be in set $\mathcal{M}^{-}$ and the products of $\hat{r}_{j}$ be in set $\mathcal{M}^{+}$, where $\mathcal{M}^{-}\cup\mathcal{M}^{+} = \mathcal{M}$.

Then, the law of mass action for reaction $j$ (that could involve autocatalysis) is given by:

```{math}
:label: eqn-rate-of-mass-action
\hat{r}_{j} = k_{j}\prod_{i\in\mathcal{M}^{-}}\left[X_{i}\right]^{-\sigma_{ij}} - 
k^{\prime}_{j}\prod_{k\in\mathcal{M}^{+}}\left[X_{k}\right]^{\sigma_{kj}}
```

where $k_{j}$ and $k^{\prime}_{j}$ are the forward and reverse rate constants, 
$\left[X_{i}\right]$ is the concentration of species $i$, and $\sigma_{kj}$ is the stoichiometric coefficient governing the species $k$ in reaction $j$.

````

Let's consider an example of a simple mass action reaction in a well-mixed closed system ({prf:ref}`example-mass-action-reaction`):

````{prf:example} Mass action simulation
:label: example-mass-action-reaction

Consider the reaction $A+B\leftrightharpoons{C}$. For this reaction $\mathcal{M} = \left\{A,B,C\right\}$, where $\mathcal{M}^{-} = \left\{A,B\right\}$ and $\mathcal{M}^{+} = \left\{C\right\}$. Then, the mass action rate law would be:

$$\hat{r}_{1} = k_{1}\left[A\right]\left[B\right] - k^{\prime}_{1}\left[C\right]$$

The forward and reverse rate constants $k_{1}$ and $k^{\prime}_{1}$ in a mass action kinetic expression are constants of proportionality for each direction of the rate. To describe the time evolution of this system, we solve the system of differential equations:

$$
\begin{eqnarray}
\frac{d}{dt}\left([A]V\right) & = & -\hat{r}_{1}V\\
\frac{d}{dt}\left([B]V\right) & = & -\hat{r}_{1}V\\
\frac{d}{dt}\left([C]V\right) & = & \hat{r}_{1}V\\
\end{eqnarray}
$$

Solving the system of differential equations numerically (using a method similar to the {ref}`content:references:dynamic-systems-euler` described earlier) gives the solution shown in {numref}`fig-mass-action-kinetics-simple-example`


```{figure} ./figs/Fig-MAK-Example.pdf
---
height: 360px
name: fig-mass-action-kinetics-simple-example
---
Solution of the concentration balance equations for a closed system in which the reaction $A+B\leftrightharpoons{C}$ is described using mass action kinetics. Parameters: $k_{1} = 1.0$ units: 1/concentration$^{2}$-time and $k^{\prime}_{1} = 0.1$ units: 1/time. Initial conditions: $\left(A_{\circ},B_{\circ},C_{\circ}\right) = (2.0, 1.0, 0.0)$ units: concentration.
```

__source__: [Jupyter notebook in the notebooks-jupyter directory of the course GitHub site](https://github.com/varnerlab/ENGRI-1120-IntroToChemE-Example-Notebooks)
````

(content:references:kinetic-e-catalyzed-rxn)=
## Enzyme catalyzed reactions
Enzymes are biological polymers, largely composed of the [20 naturally occurring amino acid building](https://en.wikipedia.org/wiki/Amino_acid), that catalyze biochemical reactions. There are seven classes of enzymes, and each enzyme class can carry out a specific type of chemistry: 

| Name | Reaction | Description |
| :--- | --- | ---|
| Oxidoreductases | $A_{o}$ + $B_{r}$ $\rightarrow$ $A_{r}$ + $B_{o}$ | Catalyze redox reactions
| Transferases | A-B + C $\rightarrow$ A + C-B| Catalyze the transfer of groups between substrates
| Hydrolases | A-B + H2O $\rightarrow$ A-H + B-OH | Catalyze the hydrolysis of substrates
| Lyases | A-B $\rightarrow$ A + B | Catalyzes the removal of a group from a substrate
| Isomerases | A-B-C $\rightarrow$ A-C-B | Catalyzes the formation of isomers
| Ligases | A + B + ATP $\rightarrow$ A-B + ADP + Pi | Catalyze the joining of two substrates
| Translocases | A-out $\rightarrow$ A-in | Catalyze the movement of ions or molecules across membranes

In general, the kinetics of enzyme-catalyzed reactions is complex. However, there is a simple theoretical model, the [Michaelis–Menten kinetic model](https://en.wikipedia.org/wiki/Michaelis–Menten_kinetics), that is a helpful starting point for broadly understanding the factors that control the rate of an enzyme-catalyzed reaction.

### Michaelis–Menten kinetics
Let's assume we have a well-mixed test tube containing an enzyme $E$ (a protein that catalyzes chemical reactions), which converts substrate $S$ (the starting compound) into product $P$ according to three elementary reactions:

$$\begin{eqnarray}
	E+S&\rightleftharpoons&{E:S}\\
	{E:S}&\longrightarrow&E+P
\end{eqnarray}$$

where enzyme must obey the relationship:

$$\left[E_{T}\right] = \left[E\right] + \left[E:S\right]$$

The term $\left[E_{T}\right]$ denotes the total enzyme concentration in the tube, 
$\left[E\right]$ denotes the free enzyme concentration (not bound to substrate) while
$\left[E:S\right]$ denotes the enzyme-substrate complex. 

We can describe the binding, unbinding and catalysis steps as three elementary reactions: 

```{prf:observation} Michaelis–Menten elementary steps.

The kinetics of each elementary step can be written using mass-action kinetics, i.e.,

$$\begin{eqnarray}
	r_{1} & = & k_{1}\left[E\right]\left[S\right]\\
	r_{2} & = & k_{2}\left[E:S\right]\\
	r_{3} & = & k_{3}\left[E:S\right]
\end{eqnarray}$$

where $\left[\cdot\right]$ denotes a species concentration, and $k_{j}$ denotes the rate constant governing the jth elementary reaction:

* The elementary rate $r_{1}$ describes the _association_ rate between the enzyme and substrate
* The elementary rate $r_{2}$ represents the rate of _dissociation_ of the enzyme-substrate complex
* The elementary $r_{3}$ denotes the rate of _chemical conversion_ of the bound substrate into the product (we assume the product dissociation from the enzyme is fast).
```

#### Derivation
To estimate the _overall_ rate of reaction $v$, we propose a single rate-limiting step out of the set of elementary reactions. Let's assume that the chemical conversion rate $r_{3}$ is the slowest step, i.e., the substrate bounces on/off the enzyme quickly, with only a tiny fraction of these binding events resulting in a successful chemical transformation. Thus, the overall rate is then given by:

$$v = k_{3}\left[E:S\right]$$

Let's also assume that we already know (or can estimate) the rate constants $k_{1},k_{2}$ and $k_{3}$. When this is true, the only unknown is $\left[E:S\right]$.
However, we can relate $\left[E:S\right]$ to variables we know ($E_{T}$ and at least initially $S$) through the enzyme balance, and the _pseudo-steady-state assumption_ for the reaction intermediate 
$\left[E:S\right]$:

$$\frac{d\left[E:S\right]}{dt} = k_{1}\left[E\right]\left[S\right] - k_{2}\left[E:S\right] - k_{3}\left[E:S\right]\simeq{0}$$

Rearranging and solving for $\left[E:S\right]$ gives the relationship:

$$\left[E:S\right]\simeq\frac{k_{1}}{k_{2}+k_{3}}\left[E\right]\left[S\right]$$

where the ratio of constants is defined as the Michaelis-Menten saturation coefficient or $K_{M}$:

$$\frac{1}{K_{M}}\equiv\frac{k_{1}}{k_{2}+k_{3}}$$

Substituting the definition of $K_{M}$ into the overall rate yields:

$$v = k_{3}\frac{\left[E\right]\left[S\right]}{K_{M}}$$

However, we do not know the free enzyme concentration of $\left[E\right]$; to find $\left[E\right]$
we subsitute $\left[E:S\right]$ into the enzyme balance and solving for $\left[E\right]$:

$$\left[E\right] = \frac{\left[E_T\right]K_{M}}{K_{M}+\left[S\right]}$$

Lastly, we substitute $\left[E\right]$ into the overall rate to arrive at the final expression for $v$:

$$v = V_{max}\frac{\left[S\right]}{K_{M}+\left[S\right]}$$

where $V_{max}\equiv{k_{3}}\left[E_{T}\right]$. 

````{prf:definition} Michaelis–Menten Kinetics
:label: defn-mm-enzyme-kinetics

Suppose we have an enzyme $E$ that converts substrate $S$ (the starting compound) into product $P$ in a well-mixed reaction. Then, the overall reaction rate for the conversion of substrate $S$ to product $P$ is given by:

```{math}
:label: eqn-mm-e-kinetics
v = V_{max}\frac{\left[S\right]}{K_{M}+\left[S\right]}
```

where $K_{M}$ is the saturation constant for enzyme $E$ and substrate $S$, while $V_{max}$ is the maximum rate of reaction:

```{math}
:label: eqn-vmax
V_{max}\equiv{k_{3}}\left[E_{T}\right]
```

where $k_{3}$ is called the turn-over number of the enzyme $E$ (units: 1/time) and $\left[E_{T}\right]$ denotes the concentration of enzyme $E$.

__Limiting cases:__
* If $S\gg{K}_{M}$, the rate $v\simeq{V_{max}}$.
* If $S\ll{K}_{M}$, the rate $v$ appears to be linear with respect to substrate concentration.
* If $K_{M}\simeq S$, the rate $v\simeq 1/2~V_{max}$. 

````

### Well-mixed assumption
Now that we have introduced kinetic expressions, let's introduce one final key concept in this section, the Well Mixed Assumption (WMA). To understand the benefit (and cost) of the well mixed assumption, let's manupilate the species concentration balance equations given in {prf:ref}`defn-species-conc-balance`. 

#### Constant volume, steady-state concentration balances
Suppose we have a reaction set $\mathcal{R}$ involving the species set $\mathcal{M}$ that is occurring in a well-mixed chemical reactor with stream set $\mathcal{S}$. Then the concentration of component $i\in\mathcal{M}$ is given by:

$$\frac{d}{dt}\left(C_{i}V\right) = \sum_{s\in\mathcal{S}}v_{s}C_{s,i}\dot{V}_{s} + \sum_{r\in\mathcal{R}}\sigma_{ir}\hat{r}_{r}V\qquad\forall{i}\in\mathcal{M}$$

where $C_{s,i}$ denotes the concentration of component $i\in\mathcal{M}$ in stream $s\in\mathcal{S}$, $\sigma_{ir}$ denotes the stoichiometric coefficient for component $i\in\mathcal{M}$ in reaction $r\in\mathcal{R}$, $\dot{V}_{s}$ denotes the volumetric flow rate of stream $s\in\mathcal{S}$, $V$ denotes the volume of the reaction mixture in the reactor unit, $v_{s}$ denotes the direction parameter for stream $s\in\mathcal{S}$ and the quantity $C_{i}$ denotes the concentration of component $i\in\mathcal{M}$ in the reaction vessel. Finally, the terms $\hat{r}_{r}$ denote the _reaction rate per unit volume_ for reaction $r\in\mathcal{R}$ that is occurring in the reaction vessel. 

When the reaction is at constant volume, we can pull the volume $V$ out of the accumulation term and divide by the volume to give:

$$\frac{dC_{i}}{dt} = \sum_{s\in\mathcal{S}}v_{s}C_{s,i}D_{s} + \sum_{r\in\mathcal{R}}\sigma_{ir}\hat{r}_{r}\qquad\forall{i}\in\mathcal{M}$$

where $D_{s}$ is called the _dilution rate_ for stream $s\in\mathcal{S}$; the dilution rate has units of inverse time. Finally, at steady-state, all accumulation terms vanish, giving:

$$\sum_{s\in\mathcal{S}}v_{s}C_{s,i}D_{s} + \sum_{r\in\mathcal{R}}\sigma_{ir}\hat{r}_{r} = 0\qquad\forall{i}\in\mathcal{M}$$

If a reactor is well mixed, then the concentration of component $i\in\mathcal{M}$ in the reactor is the same as the concentration of component $i\in\mathcal{M}$ in the exit streams. 

````{prf:definition} Well mixed concentration balance
Suppose we have a reaction set $\mathcal{R}$ involving the species set $\mathcal{M}$ that is occurring in a well-mixed chemical reactor with stream set $\mathcal{S}$; partition the streams into the subsets $\mathcal{S}^{+}$ and $\mathcal{S}^{-}$, where
$\mathcal{S}^{+}$ denotes the subset of streams that enter the reactor, and $\mathcal{S}^{-}$ represents the subset of streams that exit the reactor.

Then, the constant volume well-mixed concentration balance for component $i\in\mathcal{M}$ is given by:

```{math}
:label: eqn-wma-concentration-balance

\frac{dC_{i}}{dt} = \sum_{s\in\mathcal{S^{+}}}v_{s}C_{s,i}D_{s} - C_{i}\sum_{s\in\mathcal{S}^{-}}v_{s}D_{s} +  \sum_{r\in\mathcal{R}}\sigma_{ir}\hat{r}_{r}\qquad\forall{i}\in\mathcal{M}
```

where $C_{i}$ denotes the concentration of component $i\in\mathcal{M}$ in the reactor, and the kinetic model for the reaction rate $\hat{r}_{r}$ is evaluated at composition $C_{i}$. 

At steady-state, the accumulation terms in Eqn. {eq}`eqn-wma-concentration-balance` are zero, which gives the well-mixed steady-state constant volume concentration balance:

```{math}
:label: eqn-wma-steady-state-concentration-balance
\sum_{s\in\mathcal{S^{+}}}v_{s}C_{s,i}D_{s} - C_{i}\sum_{s\in\mathcal{S}^{-}}v_{s}D_{s} +  \sum_{r\in\mathcal{R}}\sigma_{ir}\hat{r}_{r} = 0\qquad\forall{i}\in\mathcal{M}
```
````

---

## Summary

In this lecture, we:

* Introduced a {ref}`content:references:model-kinetics-general-model`
* Introduced {ref}`content:references:mass-action-kinetics`
* Introduced {ref}`content:references:kinetic-e-catalyzed-rxn`
