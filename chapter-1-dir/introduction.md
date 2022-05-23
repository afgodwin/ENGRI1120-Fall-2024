(content:references:open-continuous-material-balances)=
# Stuff Balance Equations
Chemical Engineering is all about designing the state and operation of a system so that it does what we want. 
For example, designing a biochemical process to produce the [COVID19 mRNA vaccine that meets quality and financial constraints](https://engineering.virginia.edu/news/2022/02/chemical-engineering-alumnus-paul-mensah-elected-national-academy-engineering), 
or developing a [process to heat the Cornell campus using geothermal energy](https://earthsourceheat.cornell.edu).

Balance equations are at the center of Chemical Engineering, whether it is for molecular or giant scale processes. If the language of Chemical Engineering is mathematics, then our grammar is balance equations. Balance equations describe the state and operation of a system and its surrondings. We use balance equations to design processes and process operations.

In this lecture:
* We will introduce what we mean by {ref}`content:references:open-system-surrondings`
* We will introduce the four types of terms in {ref}`content:references:open-stuff-balances`
* We will introduce tools to develop {ref}`content:references:solving-open-stuff-balances`

---

(content:references:open-system-surrondings)=
## Open Systems and Surrondings

Consider the idealized schematic of a continuous open system and its surroundings shown in 
{numref}`fig-system-surroundings`.

```{figure} ./figs/Fig-System-Surrondings.pdf
---
height: 300px
name: fig-system-surroundings
---
Schematic of an open system and it's surrondings.
```

Streams of _stuff_ enter (and exit) a system from the surrondings. A system is said to be _open_ 
if _stuff_ (e.g., matter) is able to enter or exit the system, otherwise a system is said to be _closed_.
For physical systems, streams can be pipes in which material flows into or out of the system at some rate. 
There can also be chemical mechanisms bringing (or consuming) material in the system, e.g., something dissolving or a chemical reaction consuming something. 

(content:references:open-stuff-balances)=
## Open Stuff Balance Equations
Whatever the system is, it can always be described by _four_ types of terms: input, output, generation, and accumulation. Let's look at these terms for an _open_ system.

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

The open _stuff_ balance equation ({prf:ref}`defn-open-continuous-stuff-balances`) is an abstract quantity; we never use it directly. Instead, we specify what we mean by _stuff_, e.g., mass, moles, etc., and then expand the terms in that quantity.

(content:references:solving-open-stuff-balances)=
## Solution of Systems of Stuff Balances
Stuff balances are typically systems of non-linear ordinary differential equations (with time as the independent variable) that often do not have analytical solutions. Thus, we need to develop tools to solve stuff balances, or at least develop approximations of the actual solution that we can use in calculations. One of the most straightforward techniques to create approximate solutions to stuff balances is discretizing the derivative term using a [finite difference approach](https://en.wikipedia.org/wiki/Finite_difference).

### Finite Difference Solution of a Scalar Stuff Balances
Suppose we are interested in computing the amount of stuff in a system for some time horizon $t_{1}\rightarrow{T}$.
Further, suppose we broke this time horizon into many small segments, each with length $h$.
Then, a finite difference approach approximates the accumulation term (the $dx/dt$ term) using a ratio of finite differences on each of these smaller time segments.

To illustrate this idea, let's consider the first segment, namely $t_{1}\rightarrow{t_{2}}$. Then, the accumulation term can be approximated as:

```{math}
:label: eq-forward-difference
\frac{dx}{dt}\simeq\frac{\Delta{x}}{h}
```

where $\Delta{x} = x_{t_{2}} - x_{t_{1}}$ and $h = t_{2} - t_{1}$. 
Eqn. {eq}`eq-forward-difference` is called a forward difference (there are several different ways to approximate the derivative term, this is one of the simplest.) Given a forward difference approximation, the 
the open stuff balance equation ({prf:ref}`defn-open-continuous-stuff-balances`) becomes:

```{math}
x_{t_{2}} = x_{t_{1}} + \left(\sum_{s\in\mathcal{S}}\nu_{s}\dot{x}_{s} + \dot{x}_{gen}\right)h
```

Now that we have an estimate for $x_{t_{2}}$, we can take the next step $t_{2}\rightarrow{t_{3}}$, which gives us an estimate for $x_{t_{3}}$, and so forth until we reach the end of the time horizon $T$. 

````{prf:definition} Discrete Solution Open Stuff Balance
:label: defn-discrete-open-continuous-stuff-balances

Given a step-size $h>0$, the initial value $x_{1}$, and the values for the transport and generation terms
for $t\in\left[t_{1},T\right]$, the discrete forward approximation of the open stuff balance solution is given by:

```{math}
:label: eq-euler-decomposition
x_{i+1} = x_{i} + h\left(\sum_{s\in\mathcal{S}}\nu_{s}\dot{x}_{s} + \dot{x}_{gen}\right)_{i}\qquad{i=1,2,\dots,T-1}
```

where $x_{i+1}$ denotes the amount of stuff at time point $i+1$, 
$x_{i}$ denotes the amount of stuff at time point $i$,  $T$ denotes the solution horizon and $h$ denotes the step size. The notation $\left(\star\right)_{i}$ denotes all terms are evaluated at time step $i$.
````