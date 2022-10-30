# Chemical Reaction Kinetics

## Introduction
The _kinetics_ of a chemical reaction describes the _rate_ at which the reaction proceeds as a function of the conditions in the reactor vessel. Kinetic rate laws have units of $\star$mol/volume-time, and their mathematical form varies significantly with the type of reaction being considered. 

In this lecture, we will:

* Introduce a {ref}`content:references:model-kinetics-general-model`
* Introduce {ref}`content:references:mass-action-kinetics`
* Introduce {ref}`content:references:kinetic-e-catalyzed-rxn`

---

(content:references:model-kinetics-general-model)=
## General model of chemical reaction kinetics
Let's start by considering the simple non-enzymatic (no catalyst) _reversible_ reaction:

$$A+B\leftrightharpoons{C}$$

A general form for the _net_ rate of this reaction ($\hat{r}_{1}$) is given by:

$$\hat{r}_{1} = k_{1}\prod_{i=1}^{\mathcal{M}}\left[X_{i}\right]^{\alpha_{i1}} - k_{1}^{\prime}\prod_{j=1}^{\mathcal{M}}\left[X_{j}\right]^{\beta_{i1}}$$

where $\left[X_{i}\right]$ denotes the concentration of component $i=1,2,\dots,\mathcal{M}$, and $\alpha_{i1}$ and $\beta_{i1}$ denote the _reaction order_ of component $i$ in reaction $\hat{r}_{1}$. The values of the reation orders $\alpha_{i1}$ and $\beta_{i1}$ depend upon the reaction, and may _not_ always be integer values. 
Lastly, the quantities $k_{1}$ and $k_{1}^{\prime}$ denote the rate constant for the forward and reverse directions, respectively. Rate constants have various units depending upon the values of $\alpha_{i1}$
and $\beta_{i1}$. 

There is no requirement that $\alpha_{i1}$ and $\beta_{i1}$ be integers (or the stoichiometric coefficients). This is often only true when we have a complete (or simplified) picture of the chemistry that is occurring. In real-life, fractional values for $\alpha_{i1}$ and $\beta_{i1}$ are common in many application areas.  

(content:references:mass-action-kinetics)=
## Mass action kinetics
Another way to think about the kinetic rate laws and rate constants is that the overall rate of a reaction is proportional to the concentrations of the species that are participating in the reaction (raised to some power). Given this perspective, the rate constants are then simply constants of proportionality for each direction of the rate. The reaction orders ($\alpha_{i1}$ and $\beta_{i1}$) depend upon our understanding of the chemistry that is occurring, but in a simplified universe we can assume the [Law of Mass Action](https://en.wikipedia.org/wiki/Law_of_mass_action).

The [law of mass action](https://en.wikipedia.org/wiki/Law_of_mass_action) assumes that the net rate of a chemical reaction is proportional to the concentration of the components raised to the $-{1}\times$ the stoichiometric coefficient of that component in _a particular reaction direction_. For example, for the reaction $A+B\leftrightharpoons{C}$, the mass action rate law would be:

$$\hat{r}_{1} = k_{1}\left[A\right]\left[B\right] - k^{\prime}_{1}\left[C\right]$$

Thus, a general statement of the law of mass action for reaction $j$ (that could involve autocatalysis) is given by:

$$\hat{r}_{j} = k_{j}\prod_{i=1}^{\mathcal{M}}\left[X_{i}\right]^{-\sigma_{ij}} - 
k^{\prime}_{j}\prod_{i=1}^{\mathcal{M}}\left[X_{i}\right]^{-\sigma_{ij}}$$

(content:references:kinetic-e-catalyzed-rxn)=
## Kinetic models of enzyme catalyzed reactions

### Michaelis–Menten kinetics
Let's assume we have a well-mixed test tube containing an enzyme $E$ (a protein that catalyzes chemical reactions), which converts substrate $S$ (the starting compound) 
into product $P$ according to three elementary reactions:

$$\begin{eqnarray}
	E+S&\rightleftharpoons&{E:S}\\
	{E:S}&\longrightarrow&E+P
\end{eqnarray}$$

The kinetics of each elementary step can be written using mass-action kinetics, i.e.,

$$\begin{eqnarray}
	r_{1} & = & k_{1}\left[E\right]\left[S\right]\\
	r_{2} & = & k_{2}\left[E:S\right]\\
	r_{3} & = & k_{3}\left[E:S\right]
\end{eqnarray}$$

where $\left[\cdot\right]$ denotes a species concentration, and $k_{j}$ denotes the rate constant governing the $jth$ elementary reaction:

* The rate $r_{1}$ describes the _association_ rate between the enzyme and substrate,
* The rate $r_{2}$ represents the rate of _dissociation_ of the enzyme-substrate complex, and
* The $r_{3}$ denotes the rate of _chemical conversion_ of the bound substrate into the product (we assume the dissociation of the product from the enzyme is fast).

The enzyme must obey the relationship:

$$\left[E_{T}\right] = \left[E\right] + \left[E:S\right]$$

where $\left[E_{T}\right]$ denotes the total enzyme concentration in the tube, 
$\left[E\right]$ denotes the free enzyme concentration (not bound to substrate) while
$\left[E:S\right]$ denotes the enzyme-substrate complex. 

To estimate the _overall_ rate $v$, we stipulate a single rate-limiting step out of the set of elementary reactions. Let's assume that the rate of chemical conversion ($r_{3}$) is the slowest step, i.e., the substrate bounces on/off the enzyme quickly with only a tiny fraction of these binding events resulting in a successful chemical transformation. Thus, the overall rate is then given by:

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

__Limiting cases:__
* when $S\gg{K}_{M}$, the rate becomes close to $V_{max}$.
* when $S\ll{K}_{M}$ the rate appears to be linear with respect to substrate concentration.
* when $K_{M}\simeq S$ the reaction rate equals $v\simeq 1/2V_{max}$. 

---

## Summary

In this lecture, we:

* Introduced a {ref}`content:references:model-kinetics-general-model`
* Introduced {ref}`content:references:mass-action-kinetics`
* Introduced {ref}`content:references:kinetic-e-catalyzed-rxn`
