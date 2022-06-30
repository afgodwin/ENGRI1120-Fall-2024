# Material Balances

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


### Species mass balances
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
\sum_{s\in\mathcal{S}}\nu_{s}\dot{m}_{s,i} + \dot{m}_{gen,i} = \frac{dm_{i}}{dt}
\qquad{i=1,2,\dots,\mathcal{M}}
```

The quantity $\dot{m}_{s,i}$ denotes the mass flow rate of component $i$ in stream $s$ (units: g $i$/time),
$\dot{m}_{gen,i}$ denote the rate of generation of component $i$ in the system 
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

### Total mass balances
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

The quantity $\dot{m}_{s,T}$ denotes the _total_ mass flow rate of stream $s$ (units: g $i$/time),
and $dm_{T}/dt$ denotes the rate of accumlation of total mass in the system (units: g $i$/time).
````


(content:references:open-species-mole-balances)=
## Open Species and Total Mole Balance Equations
Fill me in.

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

(content:references:open-discrete-material-balances)=
## Open Discrete Material Balance Equations


(content:references:closed-material-balances)=
## Closed Material Balance Equations