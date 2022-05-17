# Material Balance Equations

Suppose we have a process producing a critical component in a next-generation battery, a biofuel, or an mRNA vaccine. To model this process, we break it into two pieces, a system (where the chemistry or physical change is occurring) and its surroundings (system and surroundings are called the universe).

The system can be a physical thing, e.g., a [chemical reactor](https://en.wikipedia.org/wiki/Chemical_reactor), a [turbine](https://en.wikipedia.org/wiki/Turbine), a [pump](https://en.wikipedia.org/wiki/Pump), or a separation unit such as a [distillation column](https://en.wikipedia.org/wiki/Fractionating_column) that can exchange mass and energy with its surroundings. 
However, a system can also be logical, e.g., the value of an investment or an opinion about a future price of a commodity. For logical systems, we are not exchanging mass or energy with the surroundings but instead are transferring perhaps money, contracts, or information. 

The surrondings are the world around the system. Material, energy, information (whatever it is) flows from the surrondings into the system, and from the system back back to the surrondings. Regardless of its actual makeup, the properties of a system and its surroundings can be described using balance equations. 

In this lecture we will:

* Introduce the terms in the {ref}`content:references:open-continuous-material-balances`
* Introduce the terms in the {ref}`content:references:open-discrete-material-balances`
* Introduce the terms in the {ref}`content:references:closed-material-balances`

---


<!-- Balance equations have their roots in physical conservation principles, such as the conservation of 
mass, momentum, energy, and number are at the center of Chemical Engineering.   -->
<!-- 
![fishy](./figs/Continuous.pdf) -->

(content:references:open-continuous-material-balances)=
## Open Continous Stuff Balance Equations
Consider an idealized schematic of a continuous open system and its surroundings.
Streams of material  enter and exit the system from the surrondings.
Thus, the system is _open_: the system is _open_ because it can exchange stuff with it's surrondings. 

For a physical system, streams can be pipes in which material flows into or out of the system at some rate. 
There can also be chemical mechanisms bringing (or consuming) material in the system, e.g., something dissolving or a reaction consuming something. Whatever the system is, it can always be described by _four_ types of terms: input, output, generation, and accumulation:

````{prf:definition} Open Continuous Stuff Balance
:label: defn-open-continuous-stuff-balances

Denote the amount of _stuff_ in a system as $x(t)$ where $t$ denotes time.
Let the [set of streams](https://en.wikipedia.org/wiki/Set_(mathematics)) carrying _stuff_ into and from the system be denoted by the symbol $\mathcal{S}$. Then, the amount of _stuff_ within the system as a function of time $t$ is governed by a _stuff_ balance equation of the form:

```{math}
\sum_{s\in\mathcal{S}}\nu_{s}\dot{x}_{s} + \dot{x}_{gen} = \frac{dx}{dt}
```

where $\nu_{s}\in\left[-1,1\right]$ is a direction parameter, and the subscript $s$ denotes the stream index in the stream set $\mathcal{S}$. We'll use the convention that streams _entering_ the system have
positive direction parameters ($\nu_{s} = 1$), while streams _exiting_ the system ($s^{*}$) have negative direction parameters ($\nu_{s^{*}} = -1$). 

The quantity $\dot{x}_{s}$ denotes the rate of _stuff_ flowing in stream $s$ (units material per time e.g., kg/hr); we'll use the $\dot{\star}$ notation to denote rate.

The terms $\dot{x}_{gen}$ (units: stuff per time) describes the net rate of generation of _stuff_ inside the system.

__Terms__
* The summation (the $\sum\star$ symbol) describes the net rate of material flowing into and from the system; these are the _transport terms_. 
* The $\dot{x}_{gen}$ terms (units: material per time) denotes the net rate of material generation in the system by chemical reactions or other processes; these are the _generation terms_. If material is being formed (consumed), the $\dot{x}_{gen}$ terms will be positive (negative). 
* The $d{x}/dt$ term denotes the rate of accumulation of material within the system; these are _accumulation terms_. 

````

The open _stuff_ balance equation ({prf:ref}`defn-open-continuous-stuff-balances`) is an abstract quantity; we never use it directly. Instead, we specify what we mean by _stuff_, e.g., mass, moles, etc., and then expand the terms in that quantity. Let's start by letting _stuff_ be mass.

### Open Total and Species Mass Balance Equations
Suppose we interested in tracking the mass of each chemical component in a mixture of $\mathcal{M}$ components for a chemical reaction process e.g., the starting material, the final product and some by-products flowing into and from a chemical reactor unit. 

In this case, we let _stuff_ equal the mass of each of these chemical components; this choice gives the _open species mass balance_ ({prf:ref}`defn-open-species-mass-balance`):

````{prf:definition} Open Species Mass Balance
:label: defn-open-species-mass-balance

Let $m_{i}$ denote the mass of chemical component $i$ in the system (units: mass e.g., kg).
Further, denote the number of chemical components in the system as $\mathcal{M}$, and the set of
streams flowing into and from the system as $\mathcal{S}$, where each stream 
$s\in\mathcal{S}$ has a direction parameter $\nu_{s}\in\left[-1,1\right]$. 

Then, the mass of chemical component $i$ in the system as a function of time (units: kg) is described by an _open species mass balance equation_:

```{math}
\sum_{s\in\mathcal{S}}\nu_{s}\dot{m}_{s,i} + \dot{m}_{gen,i} = \frac{dm_{i}}{dt}
\qquad{i=1,2,\dots,\mathcal{M}}
```

The quantity $\dot{m}_{s,i}$ denotes the mass flow rate of component $i$ in stream $s$ (units: kg $i$/time),
$\dot{m}_{gen,i}$ denote the rate of generation of component $i$ in the system (units: kg $i$/time),
and $dm_{i}/dt$ denotes the rate of accumlation of mass of component $i$ in the system (units: kg $i$/time).

````

When $\mathcal{M}>1$, then we have a _system_ of equations (one for each component in the 
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

````{prf:example} Matrix vector species mass balance 
:label: ex-species-mass-balance-3-3

```{figure} ./figs/Fig-Reactor-Example.pdf
---
height: 200px
name: directive-fig
---
```

Starting materials $A$ (stream 1) and $B$ (stream 2) flow into a chemical reactor. $A$ and $B$ react in the presence of enzyme $E$ to form product $P$. Enzyme $E$ is required for the formation of product $P$. The enzyme $E$ is covalently linked to the reactor, but the linkage is unstable. Thus, enzyme $E$, product $P$ and unreacted starting materials $A$ and $B$ flow can out of the reactor (stream 3)

````




### Open Total and Species Mole Balance Equations
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