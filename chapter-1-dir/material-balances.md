# Material Balances

## Introduction
Suppose we have a process producing a critical component in a next-generation battery, a biofuel, or an mRNA vaccine. To model this process, we break it into two pieces, a system (where the chemistry or physical change is occurring) and its surroundings (system and surroundings are called the universe). Previously, we introdcued the idea of a _stuff balance_; equations that can be used to track the amount of _stuff_ in a system. But what is _stuff_?

To exlore this question, let's expand upon our previous discussion of stuff balances, and consider a particular type of stuff, namely the mass and moles of chemical compounds. 
For example, the mass (or number of moles) of active mRNA being produced by a system. 
Mass (or moles) are types of _material balances_, they allow us to track the amount of _material_ in a system as time evolves.

In this lecture:

* We will introduce {ref}`content:references:open-species-mass-balances`
* We will introduce {ref}`content:references:open-species-mole-balances`
---


<!-- Balance equations have their roots in physical conservation principles, such as the conservation of 
mass, momentum, energy, and number are at the center of Chemical Engineering.   -->
<!-- 
![fishy](./figs/Continuous.pdf) -->

(content:references:open-species-mass-balances)=
## Open Species and Total Mass Balance Equations

Suppose we interested in tracking the mass of each chemical component in a mixture of $\mathcal{M}$ components for a chemical reaction process e.g., the starting material, the final product and perhaps some by-products flowing into and from a chemical reactor unit. 


### Open species mass balances
If we are interested in the amount of each chemical species, we can let _stuff_ equal the mass of each of the chemical components; this choice gives the _open species mass balance_ ({prf:ref}`defn-open-species-mass-balance`):

````{prf:definition} Open Species Mass Balance
:label: defn-open-species-mass-balance

Let $m_{i}$ denote the mass of chemical component $i$ in the system (units: mass e.g., grams g).
Further, denote the number of chemical components in the system we want to track as $\mathcal{M}$, and the set of
streams flowing into (or from) the system as $\mathcal{S}$, where each stream 
$s\in\mathcal{S}$ has a direction parameter $\nu_{s}\in\left[-1,1\right]$. 

If stream $s$ _enters_ the system $\nu_{s} = +1$, however is stream $s$ _exits_ the system then $\nu_{s} = -1$.

Then, the mass of chemical component $i$ in the system as a function of time (units: g) is described by an _open species mass balance equation_:

```{math}
\sum_{s\in\mathcal{S}}\nu_{s}\dot{m}_{s,i} + \dot{m}_{G,i} = \frac{dm_{i}}{dt}
\qquad{i=1,2,\dots,\mathcal{M}}
```

The quantity $\dot{m}_{s,i}$ denotes the mass flow rate of component $i$ in stream $s$ (units: g $i$/time),
$\dot{m}_{G,i}$ denote the rate of generation of component $i$ in the system 
(units: g $i$/time), and $dm_{i}/dt$ denotes the rate of accumlation of mass of component $i$ in the system (units: g $i$/time).

````



<!-- When $\mathcal{M}>1$, then we have a _system_ of equations (one for each component in the 
$\mathcal{M}$ component mixture). When $\mathcal{M}$ becomes large, it is much more convient to represent the species mass balance equations in matrix-vector form:

```{math}
\mathbf{C}\dot{\mathbf{m}}+\dot{\mathbf{R}} = \frac{d\mathbf{m}}{dt}
```

where $\mathbf{C}$ denotes the $\mathcal{M}\times\left(\mathcal{M}\cdot\dim\mathcal{S}\right)$ 
_connectivity_ matrix,
$\dot{\mathbf{R}}$ denotes the $\mathcal{M}\times{1}$ vector of generation terms, and $d\mathbf{m}/dt$ 
denotes the $\mathcal{M}\times{1}$ vector of accumulation terms. To make matrix-vector form more 
understandable, let's consider a system with three components $\mathcal{M} = 3$ 
and three streams $\dim{S}=3$.

````{prf:example} Species mass balance 
:label: ex-species-mass-balance-3-3

```{figure} ./figs/Fig-Reactor-Example.pdf
---
height: 200px
name: directive-fig
---
```

Starting materials $A$ (stream 1) and $B$ (stream 2) flow into a chemical reactor. $A$ and $B$ react in the presence of enzyme $E$ to form product $P$. Enzyme $E$ is required for the formation of product $P$. The enzyme $E$ is covalently linked to the reactor, but the linkage is unstable. Thus, enzyme $E$, product $P$ and unreacted starting materials $A$ and $B$ flow can out of the reactor (stream 3). 

Let's write the species mass balance equations in index and matrix-vector form for the production of product $P$. 

* First, let's identify the system and the surroundings. The chemistry is occurring in the reactor, so let's make that the system; everything else will be the surroundings.
 
* Next, let's specify the system dimension; there are three streams, thus our stream set is given by $\mathcal{S}=\left\{1,2,3\right\}$. The are $\mathcal{M} = 4$ chemical components ($A$, $B$, $P$ and $E$).
```` -->

### Open total mass balances
Of course, we don't need to track the individual mass of each chemical compound in a mixture of $\mathcal{M}$ compounds; instead, we can track the _total mass_ of all $\mathcal{M}$ components collectively.
This choice gives the _open total mass balance_ ({prf:ref}`defn-open-total-mass-balance`):


````{prf:definition} Open Total Mass Balance
:label: defn-open-total-mass-balance

Let $m_{i}$ denote the mass of chemical component $i$ in the system (units: mass e.g., grams g).
Further, denote the number of chemical components in the system we want to track as $\mathcal{M}$, and the set of
streams flowing into (or from) the system as $\mathcal{S}$, where each stream 
$s\in\mathcal{S}$ has a direction parameter $\nu_{s}\in\left[-1,1\right]$. 

If stream $s$ _enters_ the system $\nu_{s} = +1$, however, if stream $s$ _exits_ the system then $\nu_{s} = -1$.

Then, the total mass of all chemical components in the system as a function of time (units: g) is described by an _open total mass balance equation_:

```{math}
\sum_{s\in\mathcal{S}}\nu_{s}\dot{m}_{s,T} = \frac{dm_{T}}{dt}
```

The quantity $\dot{m}_{s,T}$ denotes the _total_ mass flow rate of stream $s$ (units: g/time),
and $dm_{T}/dt$ denotes the rate of accumlation of total mass in the system (units: g/time).
````

To go from a species perspective i.e., where we track the mass of each chemical component in a 
mixture of $\mathcal{M}$ components, to the total mass balance we use the [Law of Conservation of Mass](https://en.wikipedia.org/wiki/Conservation_of_mass). The [Law of Conservation of Mass](https://en.wikipedia.org/wiki/Conservation_of_mass) says that mass can neither be created nor destroyed, just rearranged or transformed. 

````{prf:observation} Total Mass Balance using the Law of Conservation of Mass

Suppose we have a system with $\mathcal{M}$ chemical components. Further suppose we write a species balance around
_each_ of the $i=1,2,\dots,\mathcal{M}$ components:

```{math}
\begin{eqnarray}
\sum_{s\in\mathcal{S}}\nu_{s}\dot{m}_{s,1} + \dot{m}_{G,1} &=& \frac{dm_{1}}{dt}\\
& \vdots & \\
\sum_{s\in\mathcal{S}}\nu_{s}\dot{m}_{s,\mathcal{M}} + \dot{m}_{G,\mathcal{M}} &=& \frac{dm_{\mathcal{M}}}{dt}\\
\end{eqnarray}
```

Then, we can _sum_ the $\mathcal{M}$ species mass balances to arrive at the total mass balance equation i.e., we take advantage of the summation relationship(s):

```{math}
:label: eqn-total-mass-sum-rule
m_{T} = \sum_{i=1}^{\mathcal{M}}m_{i}
```

and

```{math}
:label: eqn-total-mass-flow-rate
\dot{m}_{s,T} = \sum_{i=1}^{\mathcal{M}}\dot{m}_{s,i}
``` 

for some stream $s$. Let's use the summation relationships in Eqn. {eq}`eqn-total-mass-sum-rule` 
and Eqn. {eq}`eqn-total-mass-flow-rate` to explore each term of the total mass balance:

* __Accumulation terms__: The accumulation term for the total mass balance is simply the time-derivative of the sum of the accumulation terms for each component:

```{math}
\frac{dm_{T}}{dt} = \frac{d}{dt}\left(\sum_{i=1}^{\mathcal{M}}m_{i}\right)
```

* __Transport terms__: The total mass flow rate in stream $s$ can be calculated using Eqn. {eq}`eqn-total-mass-flow-rate`:

```{math}
\sum_{s\in\mathcal{S}}\nu_{s}\dot{m}_{s,T} = \sum_{s\in\mathcal{S}}\nu_{s}\left(\sum_{i=1}^{\mathcal{M}}\dot{m}_{s,i}\right)
```

* __Generation terms__: There are no generation terms in the total mass balance. However, the Law of Conservation of Mass
says that mass is not created or destroyed, just transformed from one form to another; if we consume 
component $j$, then the amount of mass consumed must show up in the other components. 
Thus, the sum of the individual species mass generation terms must be equal to zero: 

```{math}
\sum_{i=1}^{\mathcal{M}}\dot{m}_{G,i} = 0
```
````

(content:references:open-species-mole-balances)=
## Open Species and Total Mole Balance Equations
Mass-based units are generally convenient for systems that do not involve chemical reactions. 
However, it is often easier to use mole-based units when chemical reactions occur. 
The principles of mole-based balance equations are similar to their mass-based equivalents, i.e., we can write species mole balances or total mole balances, and they play an equivalent role as their 
mass-based equivalents. 

However, there is one key exception between a mass and mole description of the material in a system: moles are _NOT_ conserved; thus, there is _NO Law of the Conservation of Moles_.

### Open species mole balances
If we are interested in the number of moles of each chemical species, we can write the _open species mole balance_ 
({prf:ref}`defn-open-species-mole-balance`):

````{prf:definition} Open Species Mole Balance
:label: defn-open-species-mole-balance

Let $m_{i}$ denote the number of moles of chemical component $i$ in the system 
(units: $\star$moles, e.g., mmol or  $\mu$mol).
Further, denote the number of chemical components in the system we want to track as $\mathcal{M}$, and the set of
streams flowing into (or from) the system as $\mathcal{S}$, where each stream 
$s\in\mathcal{S}$ has a direction parameter $\nu_{s}\in\left[-1,1\right]$. 

If stream $s$ _enters_ the system $\nu_{s} = +1$, however is stream $s$ _exits_ the system then $\nu_{s} = -1$.

Then, the number of moles of chemical component $i$ in the system as a function of time is described by an 
_open species mass balance equation_:

```{math}
\sum_{s\in\mathcal{S}}\nu_{s}\dot{n}_{s,i} + \dot{n}_{G,i} = \frac{dn_{i}}{dt}
\qquad{i=1,2,\dots,\mathcal{M}}
```

The quantity $\dot{n}_{s,i}$ denotes the mole flow rate of component $i$ in stream $s$ (units: $\star$mol $i$/time),
$\dot{n}_{gen,i}$ denote the rate of generation of component $i$ in the system 
(units: $\star$mol $i$/time), and $dn_{i}/dt$ denotes the rate of accumlation of the number of moles of component $i$ in the system (units: $\star$mol $i$/time). Notice, that unlike the total mass balance, the generation terms do
not vanish in the total mole balance.

````

### Open total mole balances
Of course, if we don't need to track the individual number of moles of each chemical compound in an $\mathcal{M}$ mixture, we can track the _total number of moles_ of all $\mathcal{M}$ components collectively.
This choice gives the _open total mole balance_ ({prf:ref}`defn-open-total-mole-balance`):


````{prf:definition} Open Total Mole Balance
:label: defn-open-total-mole-balance

Let $n_{i}$ denote the number of moles of chemical component $i$ in the system (units: $\star$mol e.g., $\mu$mol or mmol, etc). Further, denote the number of chemical components in the system we want to track as $\mathcal{M}$, and the set of streams flowing into (or from) the system as $\mathcal{S}$, where each stream 
$s\in\mathcal{S}$ has a direction parameter $\nu_{s}\in\left[-1,1\right]$. 

If stream $s$ _enters_ the system $\nu_{s} = +1$, however, if stream $s$ _exits_ the system then $\nu_{s} = -1$.

Then, the total number of moles of all chemical components in the system as a function of time 
is described by an _open total mole balance equation_:

```{math}
\sum_{s\in\mathcal{S}}\nu_{s}\dot{n}_{s,T} +\dot{n}_{G,T} = \frac{dn_{T}}{dt}
```

The quantity $\dot{n}_{s,T}$ denotes the _total_ mole flow rate of stream $s$ (units: $\star$mol/time),
$\dot{n}_{gen,T}$ denotes the total generation rate (units: $\star$mol/time),
and $dn_{T}/dt$ denotes the rate of accumlation of total moles in the system (units: $\star$mol/time).
````

To go from a species perspective i.e., where we track the moles of each chemical component in a 
mixture of $\mathcal{M}$ components, to the total mole balance we sum the species mole balances. 
However, unlike the mass frame of reference, __moles are not conserved__; thus, the sum of the 
generation terms in not zero.

````{prf:observation} Total Mole Balances
Suppose we have a system with $\mathcal{M}$ chemical components. Further suppose we write a species mole balance around
_each_ of the $i=1,2,\dots,\mathcal{M}$ components:

```{math}
\begin{eqnarray}
\sum_{s\in\mathcal{S}}\nu_{s}\dot{n}_{s,1} + \dot{n}_{G,1} &=& \frac{dn_{1}}{dt}\\
& \vdots & \\
\sum_{s\in\mathcal{S}}\nu_{s}\dot{n}_{s,\mathcal{M}} + \dot{n}_{G,\mathcal{M}} &=& \frac{dn_{\mathcal{M}}}{dt}\\
\end{eqnarray}
```

Then, we can _sum_ the $\mathcal{M}$ species mole balances to arrive at the total mole balance equation i.e., we take advantage of the summation relationship(s):

```{math}
:label: eqn-total-mole-sum-rule
n_{T} = \sum_{i=1}^{\mathcal{M}}n_{i}
```

and

```{math}
:label: eqn-total-mole-flow-rate
\dot{n}_{s,T} = \sum_{i=1}^{\mathcal{M}}\dot{n}_{s,i}
``` 

for some stream $s$. Let's use the summation relationships in Eqn. {eq}`eqn-total-mole-sum-rule` 
and Eqn. {eq}`eqn-total-mole-flow-rate` to explore each term of the total mole balance:

* __Accumulation terms__: The accumulation term for the total mole balance is simply the sum of time-derivatives of the the accumulation terms of each component:

```{math}
\frac{dn_{T}}{dt} = \frac{d}{dt}\left(\sum_{i=1}^{\mathcal{M}}n_{i}\right)
```

* __Transport terms__: The total mole flow rate in stream $s$ can be calculated using Eqn. {eq}`eqn-total-mole-flow-rate`:

```{math}
\sum_{s\in\mathcal{S}}\nu_{s}\dot{n}_{s,T} = \sum_{s\in\mathcal{S}}\nu_{s}\left(\sum_{i=1}^{\mathcal{M}}\dot{n}_{s,i}\right)
```

* __Generation terms__: 
Unlike the total mass balance, there are generation terms in the total mole balance (becuase moles are not conserved):
 
```{math}
\dot{n}_{G,T} = \sum_{i=1}^{\mathcal{M}}\dot{n}_{G,i}
```
````


## Summary
In this lecture, we introduced open mass and mole balances. These equations can be used to describe the 
amount of _material_ in a system; thus, they are often collectively called material balances. 

* We first introduced species mass balances that can be used to account for the mass of species 
$i=1,2,\dots,\mathcal{M}$ in a mixture of $\mathcal{M}$ species. 
* Next, we used the [Law of Conservation of Mass](https://en.wikipedia.org/wiki/Conservation_of_mass) to compute a total mass balance equation, which is the sum of the species mass balances. Because of the conservation of 
mass principle, the species generation terms must sum to zero when in the mass frame of reference.
* We then introduced total and species mole balances. We use these equations to track the number of moles
in a system, either at the individual level of the $i=1,2,\dots,\mathcal{M}$ chemical components in a mixture of $\mathcal{M}$ species or the total number of moles. 

<!-- The input and output terms describe the rate of transport (convective or conductive) into and from the system.
Inside the system, we could also imagine there is some process in which stuff 
is being created or destroyed; these terms are called generation terms. 
Lastly, stuff can accumulate or be depleted over time in the system; accumulation or depletion is described by accumulation terms. 
Putting these four types of terms together gives the continuous total stuff balance equation:  



### Input and output terms
The summation (the $\sum\star$ symbol) in the continuous total \textit{stuff} balance equation Eqn \eqref{eqn-total-stuff}:

$$ \sum_{s~=~1}^{\mathcal{S}}v_{s}\dot{x}_{s} $$

describes the net rate of stuff flowing into and from the system, where $v_{s}$ is a direction parameter, 
and the subscript $s$ denotes the stream index.  

### Generation terms:
The term $\dot{x}_{gen}$ in Eqn \eqref{eqn-total-stuff} describes the rate of stuff generation inside the system.
The generation of stuff inside the system is used to describe chemical reactions, heat sources or sinks or other abstract
quantities such as interest or the return on an investment. 

### Accumulation terms:
On the right hand side of Eqn \eqref{eqn-total-stuff} we have the $dx/dt$ or accumulation terms.
These terms describe rate of stuff accumulation inside the system. Often we'll consider a 
special case in which the inputs, outputs and generation terms are balanced and not changing in time.
This special case is called a steady-state, in a steady-state all accumulation terms are equal to 0.   -->