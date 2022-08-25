# Systems, Surroundings and Balance Equations

## Introduction
Chemical Engineering is all about designing the state and operation of a system so that it does what we want. For example, designing a biochemical process to produce the [COVID19 mRNA vaccine that meets quality and financial constraints](https://engineering.virginia.edu/news/2022/02/chemical-engineering-alumnus-paul-mensah-elected-national-academy-engineering), 
or developing a [process to heat the Cornell campus using geothermal energy](https://earthsourceheat.cornell.edu).

Balance equations are at the center of Chemical Engineering, whether it is for molecular or giant scale processes. If the language of Chemical Engineering is mathematics, then our grammar is balance equations. Balance equations describe the state and operation of a system and its surrondings. We use balance equations to design processes and process operations.

In this lecture, we will introduce three key concepts:

* The idea of an {ref}`content:references:open-system-and-surrondings`
* The definition of a {ref}`content:references:steady-state-systems`
* The decomposition of {ref}`content:references:dynamic-systems`

---

(content:references:open-system-and-surrondings)=
## Open System and Surroundings

```{figure} ./figs/Fig-System-Surrondings.pdf
---
height: 300px
name: fig-system-surroundings
---
Schematic of an open system and it's surrondings.  
```

Consider an idealized system and its surroundings ({numref}`fig-system-surroundings`).
Streams of _stuff_ (e.g., material, energy, money, information, etc.) enter (exit) a system from the surroundings; streams cross the system boundary, transporting _stuff_ into or from the system. A system is said to be _open_  if _material stuff_ can enter or exit the system; otherwise, a system is _closed_. For physical systems, streams can be pipes in which material flows into or from the system at some rate.
In other cases, streams into (from) a system can carry other types of _stuff_ such as information (e.g., bits) or money (e.g., $\$$, $\def\euro{\unicode{x20AC}} \euro$, bitcoin, etc).

Regardless if a system is open or closed and whatever _stuff_ is, within the system, 
_stuff_ can accumulate and be generated, e.g., via a chemical reaction or by an interest process such as a savings account or treasury bond in the case of money. Whatever the system is, and whatever _stuff_ is, the time behavior of the system can always be described by these _four_ types of terms: inputs, outputs, generation, and accumulation. 

Putting all these ideas together, gives the open _stuff_ balance ({prf:ref}`defn-open-continuous-stuff-balances`):

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

(content:references:steady-state-systems)=
## Steady-State Systems
If the amount of stuff in an open system is not changing with time, then that system is said to be at a [steady-state](https://en.wikipedia.org/wiki/Steady_state). In actuality, steady-state is a mathematical construct that is often only approximated by real systems. However, steady-state is a useful abstraction (or limiting case) to consider when designing a chemical manufacturing process.

````{prf:definition} Steady State Systems
:label: defn-discrete-open-continuous-stuff-balances-ss

When a system is at steady-state, the accumulation terms are equal to zero. Transport into and from the system is balanced by the generation (e.g., reaction) terms:

```{math}
:label: ss-eq-euler-decomposition
\sum_{s\in\mathcal{S}}\nu_{s}\dot{x}_{s} + \dot{x}_{gen} = 0
```

The steady-state property is a characteristic of the system. Steady-state is not the same thing as equilibrium (which only applies to a _closed_ system).

````

Let's consider a simple example of a _steady state_ stuff balance equation:

````{prf:example} Steady-state stuff balance
:label: example-steady-state-stuff-balance

Consider a system with two input streams ($s=1$ and $s=2$), and a single output stream ($s=3$). Further, let's assume the system is at a steady state. Write the steady-state stuff balance for this system.

The set of streams $\mathcal{S}$ for this example is $\mathcal{S}=\left\{1,2,3\right\}$, where the direction coefficients will be $\left(\nu_{1},\nu_{2},\nu_{3}\right)=\left(+1,+1,-1\right)$. Then, the steady-state stuff balance equation is given by:

```{math}
:label: eqn-ss-stuff-balance-eqn
\dot{x}_{1}+\dot{x}_{2} - \dot{x}_{3} + \dot{x}_{gen} = 0
```

In the absence of any generation of stuff inside the system ($\dot{x}_{gen}=0$), Eqn. {eq}`eqn-ss-stuff-balance-eqn` becomes:

```{math}
:label: eqn-conservation-of-stuff
\dot{x}_{1}+\dot{x}_{2} = \dot{x}_{3}
```

````

Eqn. {eq}`eqn-conservation-of-stuff`, while seemingly simple, illustrates a much deeper principle, namely, the _conservation of stuff__:

````{prf:observation} Conservation of Stuff
:label: obs-conservation-of-stuff

In the absence of generation terms, the amount of stuff that comes into a system at a steady state equals the amount that leaves a system. Thus, 

$$\text{rate of stuff in} = \text{rate of stuff out}$$ 

The conservation of stuff principle is true for mass and energy, but interestingly not for money.
````

(content:references:dynamic-systems)=
## Dynamic Systems
In cases where the system is not at steady-state, we need to solve the _stuff_ balance equations for 
the amount of stuff. However, stuff balances are typically initial value problems with no analytical solution; systems of (non-linear) ordinary differential equations with time as the independent variable.  Thus, we need to develop tools to approximate the solution to _stuff_ balance equations that we can use in our design calculations. 

### Finite Difference and the Euler Method
One of the most straightforward techniques to create approximate solutions to _stuff_ balances is discretizing the derivative term using a [finite difference approach](https://en.wikipedia.org/wiki/Finite_difference). 

Suppose we are interested in computing the amount of _stuff_ in a system over some time horizon $t_{1},t_{2},\dots,T$. Further, suppose we broke this time horizon into many small equal length segments, $h = t_{i+1}-t_{i},~i=1,2,\dots, T-1$. Then, a finite difference approach approximates the accumulation term (the $dx/dt$ term) in _stuff_ balances between time $t_{i}\rightarrow{t_{i+1}}$ as:

```{math}
:label: eqn-forward-diff
\frac{dx}{dt}\simeq\frac{x_{i+1}-x_{i}}{h}\qquad{i=1,2,\dots,T-1}
```

where $x_{\star}$ is the approximate value of the solution to the _stuff_ balances at time $\star$. Eqn. {eq}`eqn-forward-diff` is called a [forward finite difference approximation](https://en.wikipedia.org/wiki/Finite_difference). This approximation forms the basis of the Forward-Euler method {prf:ref}`defn-discrete-open-continuous-stuff-balances`:

````{prf:definition} Forward-Euler Solution Stuff Balances
:label: defn-discrete-open-continuous-stuff-balances

Given a step-size $h>0$, the initial value $x_{1}$, and the values for the transport and generation terms for $t\in\left[t_{1},T\right]$, the discrete forward approximation of the open stuff balance solution is given by:

```{math}
:label: eq-euler-decomposition
x_{i+1} = x_{i} + h\left(\sum_{s\in\mathcal{S}}\nu_{s}\dot{x}_{s} + \dot{x}_{gen}\right)_{i}\qquad{i=1,2,\dots,T-1}
```

where $x_{i+1}$ denotes the amount of stuff at time point $i+1$, 
$x_{i}$ denotes the amount of stuff at time point $i$,  $T$ denotes the solution horizon and $h$ denotes the step size. The notation $\left(\star\right)_{i}$ denotes all terms are evaluated at time step $i$.
````


Let's consider a simple example of a _dyanmic_ stuff balance equation:

````{prf:example} Dynamic stuff balance equation
:label: example-dynamic-stuff-balance

Consider a dynamic system with two input streams ($s=1$ and $s=2$), and a single output stream ($s=3$). Let the flow rate of the output stream be proportional (with proportionality constant $\kappa$) to the amount of stuff in the system:

```{math}
:label: well-mixed-assumption
\dot{x}_{3,i} = \kappa{x_{i}}
```

where $x_{i}$ denotes the quanity of stuff in the system at time index $i$. Further, if assume there are no generation terms $\dot{x}_{gen} = 0$, then the approximate amount of stuff in the system as a function of time is given by:

```{math}
:label: dynamic-eq-euler-decomposition
x_{i+1} = (1-h\kappa)x_{i} + h\left(\dot{x}_{1} + \dot{x}_{2}\right)_{i}
```

If Eqn. {eq}`dynamic-eq-euler-decomposition` approaches steady state, then $x_{i+1}=x_{i}$, i.e., the difference between subsequent time goes to zero, then we get the steady state condition:

```{math}
x^{\star} = \frac{1}{\kappa}\left(\dot{x}_{1} + \dot{x}_{2}\right)
```
where $x^{\star}$ denotes the steady state quantity of stuff in the system.

````

Eqn. {eq}`well-mixed-assumption` in general is not valid, i.e., the rate of exit of stuff from the system is not a linear function of the amount of stuff in the system. However, there is one aspect of Eqn. {eq}`well-mixed-assumption` that we will _almost always_ assume:

````{prf:observation} Well Mixed Assumption
:label: obs-wma

Buried in Eqn. {eq}`well-mixed-assumption` is an interesting nugget; the quantity of stuff leaving the system is some function of the amount in the system. Further, the stuff in any exit stream is some function $g$ of the amount of stuff in the system:

```{math}
\dot{x}_{s\in\mathcal{S}^{-}} = g_{s}\left(x\right)
```

where $\mathcal{S}^{-}$ denotes the set of exit streams, and $g_{s}$ denotes the exit stream function for stream $s\in\mathcal{S}^{-}$.

This is called the Well Mixed Assumption (WMA). The WMA may not be apparent in the abstract context of _stuff_. However, when we make stuff more concrete, e.g., moles of compound $j$, it says the moles of compound $j$ in the reactor are the same as in the exit streams.   
````

---

## Summary

In this lecture, we introduced three key concepts:

* The idea of an {ref}`content:references:open-system-and-surrondings`
* The definition of a {ref}`content:references:steady-state-systems`
* The decomposition of {ref}`content:references:dynamic-systems`

In addition, we introduced the conservation of stuff principle ({prf:ref}`obs-conservation-of-stuff`) and the well-mixed assumption ({prf:ref}`obs-wma`), which will be critical throughout the rest of the course. 

Next time, we'll make the idea of _stuff_ more complete by thinking about _stuff_ as the quantity of material transported into or from a system and the amount of stuff that accumulates (or is generated) inside the system.