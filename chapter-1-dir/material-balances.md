# Material Balances

## Introduction
Suppose we have a process producing a critical component in a next-generation battery, a biofuel, or an mRNA vaccine. To model this process, we break it into two pieces, a system (where the chemistry or physical change is occurring) and its surroundings (system and surroundings are called the universe). Previously, we introdcued the idea of a _stuff balance_; equations that can be used to track the amount of _stuff_ in a system. But what is _stuff_?

To exlore this question, let's expand upon our previous discussion of stuff balances, and consider a particular type of stuff, namely the mass and moles of chemical compounds. 
For example, the mass (or number of moles) of active mRNA being produced by a system. 
Mass (or moles) are types of _material balances_, they allow us to track the amount of _material_ in a system as time evolves.

In this lecture:

* We will introduce {ref}`content:references:open-species-mass-balances`
* We will introduce {ref}`content:references:open-species-mole-balances`
* We will introduce the {ref}`content:references:open-extent-of-reaction`. 
---


<!-- Balance equations have their roots in physical conservation principles, such as the conservation of 
mass, momentum, energy, and number are at the center of Chemical Engineering.   -->
<!-- 
![fishy](./figs/Continuous.pdf) -->

(content:references:open-species-mass-balances)=
## Species and Total Mass Balance Equations

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
:label: eqn-species-mass-i-dynamic
\sum_{s\in\mathcal{S}}\nu_{s}\dot{m}_{s,i} + \dot{m}_{G,i} = \frac{dm_{i}}{dt}
\qquad\forall{i}\in\mathcal{M}
```

The quantity $\dot{m}_{s,i}$ denotes the mass flow rate of component $i$ in stream $s$ (units: g $i$/time),
$\dot{m}_{G,i}$ denote the rate of generation of component $i$ in the system 
(units: g $i$/time), and $dm_{i}/dt$ denotes the rate of accumlation of mass of component $i$ in the system (units: mass of $i$ per time).

At steady state, the accumulation term vanishes; thus, the the steady state species mass balances are given by:

```{math}
:label: eqn-species-mass-i-steady-state
\sum_{s\in\mathcal{S}}\nu_{s}\dot{m}_{s,i} + \dot{m}_{G,i} = 0
\qquad\forall{i}\in\mathcal{M}
```

where we have one balance per chemical species. 
````

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
:label: eqn-dynamic-total-mass-balance
\sum_{s\in\mathcal{S}}\nu_{s}\dot{m}_{s,T} = \frac{dm_{T}}{dt}
```

The quantity $\dot{m}_{s,T}$ denotes the _total_ mass flow rate of stream $s$ (units: g/time),
and $dm_{T}/dt$ denotes the rate of accumlation of total mass in the system (units: g/time).

At steady-state, the accumulation terms vanish in Eqn {eq}`eqn-dynamic-total-mass-balance`; thus, the steady state total mass balance equation is given by:

```{math}
:label: eqn-steady-state-total-mass-balance
\sum_{s\in\mathcal{S}}\nu_{s}\dot{m}_{s,T} = 0
```
````

#### Relationship between the species and total mass balance

To go from a species perspective i.e., where we track the mass of each chemical component in a 
mixture of $\mathcal{M}$ components, to the total mass balance we use the [Law of Conservation of Mass](https://en.wikipedia.org/wiki/Conservation_of_mass). The [Law of Conservation of Mass](https://en.wikipedia.org/wiki/Conservation_of_mass) says that mass can neither be created nor destroyed, just rearranged or transformed. 

````{prf:observation} Total Mass Balance using the Law of Conservation of Mass

Suppose we have a system with the chemical species set $\mathcal{M}$ that has dimension $|\mathcal{M}|$. 
Further suppose we write a species balance around
_each_ of the elements of the species set $\mathcal{M}$, where we index the species from $j=1,2,\dots,|\mathcal{M}|$:

```{math}
\begin{eqnarray}
\sum_{s\in\mathcal{S}}\nu_{s}\dot{m}_{s,1} + \dot{m}_{G,1} &=& \frac{dm_{1}}{dt}\\
& \vdots & \\
\sum_{s\in\mathcal{S}}\nu_{s}\dot{m}_{s,|\mathcal{M}|} + \dot{m}_{G,|\mathcal{M}|} &=& \frac{dm_{|\mathcal{M}|}}{dt}\\
\end{eqnarray}
```

Then, we can _sum_ the individual $j=1,2,\dots,|\mathcal{M}|$ species mass balances to arrive at the total mass balance equation, i.e., we take advantage of the summation relationship(s):

```{math}
:label: eqn-total-mass-sum-rule
m_{T} = \sum_{i\in\mathcal{M}}m_{i}
```

and

```{math}
:label: eqn-total-mass-flow-rate
\dot{m}_{s,T} = \sum_{i\in\mathcal{M}}\dot{m}_{s,i}
``` 

for some stream $s$. Let's use the summation relationships in Eqn. {eq}`eqn-total-mass-sum-rule` 
and Eqn. {eq}`eqn-total-mass-flow-rate` to explore each term of the total mass balance:

* __Accumulation terms__: The accumulation term for the total mass balance is simply the time-derivative of the sum of the accumulation terms for each component:

```{math}
\frac{dm_{T}}{dt} = \frac{d}{dt}\left(\sum_{i\in\mathcal{M}}m_{i}\right)
```

* __Transport terms__: The total mass flow rate in stream $s$ can be calculated using Eqn. {eq}`eqn-total-mass-flow-rate`:

```{math}
\sum_{s\in\mathcal{S}}\nu_{s}\dot{m}_{s,T} = \sum_{s\in\mathcal{S}}\nu_{s}\left(\sum_{i\in\mathcal{M}}\dot{m}_{s,i}\right)
```

* __Generation terms__: There are no generation terms in the total mass balance. However, the Law of Conservation of Mass
says that mass is not created or destroyed, just transformed from one form to another; if we consume 
component $j$, then the amount of mass consumed must show up in the other components. 
Thus, the sum of the individual species mass generation terms must be equal to zero: 

```{math}
\sum_{i\in\mathcal{M}}\dot{m}_{G,i} = 0
```
````

#### Mass fraction 
Often it is not convenient to use the mass of component $i$ directly when doing calculations. Instead, we use an analogous quantity called the _mass fraction_:


````{prf:definition} Mass fraction
:label: defn-mass-fraction
Suppose we have a stream (or system) composed of the species in the set $\mathcal{M}$. Then the mass flow rate of stream $s$ can be written as:

```{math}
\dot{m}_{s,T} = \sum_{i\in\mathcal{M}}\dot{m}_{s,i}
```

Dividing both sides by $\dot{m}_{s,T}$ gives:


```{math}
 \sum_{i\in\mathcal{M}}\left(\frac{\dot{m}_{s,i}}{\dot{m}_{s,T}}\right) = 1
```

or 

```{math}
 \sum_{i\in\mathcal{M}}w_{s,i} = 1
```

where $w_{s,i} \equiv \dot{m}_{s,i}/\dot{m}_{s,T}$ is the mass fraction of component $i$ in stream $s$. An analogous expression can be written for the mass fraction of component $i$ inside the system.

````

Using {prf:ref}`defn-mass-fraction`, we can re-write the species mass balance in terms of the mass fraction of component $i$:

```{math}
:label: eqn-species-mass-balance-mass-frac
\sum_{s\in\mathcal{S}}\nu_{s}\dot{m}_{s}w_{s,i} + \dot{m}_{G,i} = \frac{d}{dt}\left(w_{i}m_{T}\right)\qquad\forall{i}\in\mathcal{M}
```

where $w_{s,i}$ denotes the mass fraction of component $i$ in stream $s$, $w_{i}$ denotes the mass fraction of component $i$ in the system, $\dot{m}_{s}$ denotes the mass flow rate of stream $s$ and $\dot{m}_{G,i}$ denotes the rate of mass generation for species $i$.

(content:references:open-species-mole-balances)=
## Species and Total Mole Balance Equations
Mass-based units are generally convenient for systems that do not involve chemical reactions. 
However, it is often easier to use mole-based units when chemical reactions occur. 
The principles of mole-based balance equations are similar to their mass-based equivalents, i.e., we can write species mole balances or total mole balances, and they play an equivalent role as their 
mass-based equivalents. 

However, there is one key difference between a mass and mole description of the material in a system: moles are _NOT_ conserved in the presence of generation terms; thus, there is _NO Law of the Conservation of Moles_ when a system has generation terem.

### Open species mole balances
If we are interested in the number of moles of each chemical species, we can write the _open species mole balance_ ({prf:ref}`defn-open-species-mole-balance`):

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
:label: eqn-species-mol-balance
\sum_{s\in\mathcal{S}}\nu_{s}\dot{n}_{s,i} + \dot{n}_{G,i} = \frac{dn_{i}}{dt}
\qquad\forall{i}\in\mathcal{M}
```

The quantity $\dot{n}_{s,i}$ denotes the mole flow rate of component $i$ in stream $s$ (units: $\star$mol $i$/time),
$\dot{n}_{gen,i}$ denote the rate of generation of component $i$ in the system 
(units: $\star$mol $i$/time), and $dn_{i}/dt$ denotes the rate of accumlation of the number of moles of component $i$ in the system (units: $\star$mol $i$/time). 

At steady state, all the accumulation terms vanish; thus, the steady state system of species mole balances is given by:

```{math}
:label: eqn-species-mol-balance-ss
\sum_{s\in\mathcal{S}}\nu_{s}\dot{n}_{s,i} + \dot{n}_{G,i} = 0
\qquad\forall{i}\in\mathcal{M}
```
````

### Open total mole balances
Of course, if we don't need to track the individual number of moles of each chemical compound in an $\mathcal{M}$ mixture, we can track the _total number of moles_ of all $\mathcal{M}$ components collectively. This choice gives the _open total mole balance_ ({prf:ref}`defn-open-total-mole-balance`):


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

At steady state, the accumulation terms vanish; thus, the steady state total mole balance is given by:

```{math}
:label: eqn-steady-state-total-mole
\sum_{s\in\mathcal{S}}\nu_{s}\dot{n}_{s,T} + \dot{n}_{G,T} = 0
```
````

#### Relationship between the species and total mole balance
To go from a species perspective i.e., where we track the moles of each chemical component in a 
mixture of $\mathcal{M}$ components, to the total mole balance we sum the species mole balances. 
However, unlike the mass frame of reference, __moles are not always conserved__ in the presence of the generation terms; thus, the sum of the generation terms in not zero.

````{prf:observation} Total Mole Balances
Suppose we have a system with the chemical species set $\mathcal{M}$ that has dimension $|\mathcal{M}|$. 
Further suppose we write a species mole balance around
_each_ of the elements of the species set $\mathcal{M}$, where we index the species from $j=1,2,\dots,|\mathcal{M}|$:

```{math}
\begin{eqnarray}
\sum_{s\in\mathcal{S}}\nu_{s}\dot{n}_{s,1} + \dot{n}_{G,1} &=& \frac{dn_{1}}{dt}\\
& \vdots & \\
\sum_{s\in\mathcal{S}}\nu_{s}\dot{n}_{s,|\mathcal{M}|} + \dot{n}_{G,|\mathcal{M}|} &=& \frac{dn_{|\mathcal{M}|}}{dt}\\
\end{eqnarray}
```

Then, we can _sum_ the individual $j=1,2,\dots,|\mathcal{M}|$ species mole balances to arrive at the total mole balance equation, i.e., we take advantage of the summation relationship(s):

```{math}
:label: eqn-total-mole-sum-rule
n_{T} = \sum_{i\in\mathcal{M}}n_{i}
```

and

```{math}
:label: eqn-total-mole-flow-rate
\dot{n}_{s,T} = \sum_{i\in\mathcal{M}}\dot{n}_{s,i}
``` 

for some stream $s$. Let's use the summation relationships in Eqn. {eq}`eqn-total-mole-sum-rule` 
and Eqn. {eq}`eqn-total-mole-flow-rate` to explore each term of the total mole balance:

* __Accumulation terms__: The accumulation term for the total mole balance is simply the sum of time-derivatives of the the accumulation terms of each component:

```{math}
\frac{dn_{T}}{dt} = \frac{d}{dt}\left(\sum_{i\in\mathcal{M}}n_{i}\right)
```

* __Transport terms__: The total mole flow rate in stream $s$ can be calculated using Eqn. {eq}`eqn-total-mole-flow-rate`:

```{math}
\sum_{s\in\mathcal{S}}\nu_{s}\dot{n}_{s,T} = \sum_{s\in\mathcal{S}}\nu_{s}\left(\sum_{i\in\mathcal{M}}\dot{n}_{s,i}\right)
```

* __Generation terms__: 
Unlike the total mass balance, there are generation terms in the total mole balance (becuase moles are not conserved):
 
```{math}
\dot{n}_{G,T} = \sum_{i\in\mathcal{M}}\dot{n}_{G,i}
```
````

#### Mole fraction 
Often it is not convenient to use the moles of species $i$ directly when doing calculations. Instead, we use an analogous quantity called the _mole fraction_:


````{prf:definition} Mole fraction
:label: defn-mol-fraction
Suppose we have a stream (or system) composed of species in the set $\mathcal{M}$. Then the total mole flow rate of stream $s$ can be written as:

```{math}
\dot{n}_{s,T} = \sum_{i\in\mathcal{M}}\dot{n}_{s,i}
```

Dividing both sides by $\dot{n}_{s,T}$ gives:


```{math}
 \sum_{i\in\mathcal{M}}\left(\frac{\dot{n}_{s,i}}{\dot{n}_{s,T}}\right) = 1
```

or 

```{math}
 \sum_{i\in\mathcal{M}}x_{s,i} = 1
```

where $x_{s,i} \equiv \dot{n}_{s,i}/\dot{n}_{s,T}$ is the mole fraction of component $i$ in stream $s$. An analogous expression can be written for the mole fraction of component $i$ inside the system. 

When dealing with liquid streams, the symbol $x_{\star}$ is used for mole fraction; however, for vapor streams, we use the symbol $y_{\star}$.

````

Using {prf:ref}`defn-mol-fraction`, we can re-write the species mole balance in terms of the mole fraction of component $i$:

```{math}
:label: eqn-species-mass-balance-mole-frac
\sum_{s\in\mathcal{S}}\nu_{s}\dot{n}_{s}x_{s,i} + \dot{n}_{G,i} = \frac{d}{dt}\left(x_{i}n_{T}\right)\qquad\forall{i}\in\mathcal{M}
```

where $x_{s,i}$ denotes the mole fraction of component $i$ in stream $s$, $x_{i}$ denotes the mole fraction of component $i$ in the system, $\dot{n}_{s}$ denotes the mole flow rate of stream $s$ and $\dot{n}_{G,i}$ denotes the rate of mole generation for species $i$ (units: mole per time).

(content:references:open-extent-of-reaction)=
## Open Extent of Reaction
Finally, let's discuss the generation terms. Generation terms describe the impact of chemical reactions; theoretically, we can describe reactions using a mass or mole basis. However, typically we operate on a mole basis when dealing with chemical reactions. 

In the absence of kinetic rate laws, which describe how the rate of a chemical reaction changes with the concentration of the reactants (and sometimes products) of a reaction, we can describe how far the reaction has proceeded using the [extent of reaction](https://en.wikipedia.org/wiki/Extent_of_reaction). 

The open extent of reaction describes how far a chemical reaction has proceeded toward completion in an open system:

````{prf:definition} Open Extent of Reaction
Suppose we have chemical species set $\mathcal{M}$; further, suppose the chemical species in set $\mathcal{M}$ participate in the chemical reaction set $\mathcal{R}$. Then, the species generation rate $\dot{n}_{G,i}$ can be written in terms of the open extent of reaction:

```{math}
:label: eqn-open-extent-species
\dot{n}_{G,i} = \sum_{r\in\mathcal{R}}\sigma_{ir}\dot{\epsilon}_{r}
```

where $\dot{\epsilon}_{r}$ denotes the open extent of reaction $r$ (units: mol per time). The quantity $\sigma_{ir}$ denotes the stoichiometric coefficient for species $i$ in reaction $r$:
* If $\sigma_{ir}>0$ then species $i$ is _produced_ by reaction $r$, i.e., species $i$ is a product of reaction $r$ 
* If $\sigma_{ir}=0$ then species $i$ is _not connected to_ reaction $r$
* If $\sigma_{ir}<0$ then species $i$ is _consumed_ by reaction $r$, i.e., species $i$ is a reactant of reaction $r$.

Putting these ideas together, we can rewrite the dynamic species mole balance as:

```{math}
:label: eqn-dynamic-smb-with-extent
\sum_{s\in\mathcal{S}}\nu_{s}\dot{n}_{s,i} + \sum_{r\in\mathcal{R}}\sigma_{ir}\dot{\epsilon}_{r} = \frac{dn_{i}}{dt}\qquad\forall{i\in\mathcal{M}}
```

and the dynamic total mole balance as:

```{math}
:label: eqn-dynamic-tmb-with-extent
\sum_{s\in\mathcal{S}}\nu_{s}\dot{n}_{s,T} + \sum_{i\in\mathcal{M}}\sum_{r\in\mathcal{R}}\sigma_{ir}\dot{\epsilon}_{r} = \frac{dn_{T}}{dt}
```
````

---

## Summary
In this lecture, we introduced open mass and mole balances. These equations can be used to describe the 
amount of _material_ in a system; thus, they are often collectively called material balances. 

* We first introduced species mass balances that can be used to account for the mass of species 
$i\in\mathcal{M}$. 
* Next, we used the [Law of Conservation of Mass](https://en.wikipedia.org/wiki/Conservation_of_mass) to compute a total mass balance equation, which is the sum of the species mass balances. Because of the conservation of mass principle, the species generation terms must sum to zero when in the mass frame of reference.
* We then introduced total and species mole balances. We use these equations to track the number of moles
in a system, either at the individual level of the $i=1,2,\dots,\mathcal{M}$ chemical components in a mixture of $\mathcal{M}$ species or the total number of moles. 
* Finally, we introduced the open extent of reaction. The open extent of reaction describes how far a chemical reaction has gone in an open system.

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