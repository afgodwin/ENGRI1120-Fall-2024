# Systems, Surroundings and Stuff Balances

## Summary
Chemical Engineers use balance equations to describe, design, and troubleshoot products 
and processes. Balance equations describe the amount of _stuff_ (e.g., mass, the concentration of a particular chemical component, energy, etc.) in a _system_ that interacts with its _surroundings_.
Systems can be physical things like tanks or chemical reactors, or they can also be logical items such as a savings
account or a stage in a multistage decision process. 
_Stuff_ can also be a physical thing such as energy or the
mass of a material or a non-physical quantity such as information or financial value. Regardless of
what the _systems_ and _stuff_ are, the basic form of the balance equation remains the same. 
Thus, if we learn that basic form, we can describe, simulate or design all the products and processes, we are interested in.  

At the end of this lecture module, students will be able to:
* Describe the terms that appear in discrete and continuous _stuff_ balance equations
* Write discrete and continuous balances for a system to arbitrary _stuff_ balance equations

## Introduction
Suppose we take a process, for example, the production of a critical component in a next-generation battery, a biofuel, or an mRNA vaccine, and we break it apart into a system and its surroundings (which is called a universe).
In this example scenario, the system can be a physical thing, e.g., a chemical reactor, turbine, pump, or downstream separation unit such as a distillation column that can exchange mass and energy with its surroundings. 
However, a system can also be logical, e.g., the value of an investment or an opinion about a future price of a 
commodity. When considering a logical system, we are not exchanging mass or energy with the surroundings but instead are 
transferring perhaps money, contracts, or information. Regardless of its actual makeup, the properties of a 
system and its surroundings can be described using balance equations. 
Balance equations have their roots in physical conservation principles, such as the conservation of 
mass, momentum, energy, and number are at the center of Chemical Engineering.  

![fishy](./figs/Continuous.pdf)

## Continous Open System Stuff Balances
Consider an idealized schematic of a continuous open system and its surroundings.
In the continuous case, streams of stuff numbered $s=1,2,\dots{\mathcal{S}}$ enter and exit the system.
In this case, the system is called open because it can exchange stuff with it's surrondings. 
For a physical system, these streams can be pipes in which stuff is flowing into or out off the 
system at some rate, or they conductive transport mechanisms e.g., touching something hot. 
However, whatever the systems is, there are always four types of terms in a continuous stuff balance: input, output, generation and accumulation.

The input and output terms describe the rate of transport (convective or conductive) into and from the system.
Inside the system, we could also imagine there is some process in which stuff 
is being created or destroyed; these terms are called generation terms. 
Lastly, stuff can accumulate or be depleted over time in the system; accumulation or depletion is described by accumulation terms. 
Putting these four types of terms together gives the continuous total stuff balance equation:  

$$\sum_{s~=~1}^{\mathcal{S}}v_{s}\dot{x}_{s} + \dot{x}_{gen} = \frac{dx}{dt}$$

### Input and output terms
The summation (the $\sum\star$ symbol) in the continuous total \textit{stuff} balance equation Eqn \eqref{eqn-total-stuff}:

$$ \sum_{s~=~1}^{\mathcal{S}}v_{s}\dot{x}_{s} $$

describes the net rate of stuff flowing into and from the system, where $v_{s}$ is a direction parameter, 
and the subscript $s$ denotes the stream index.  We'll use the convention that streams _entering_ the system have
positive direction parameters ($v_{s} = 1$), while streams _exiting_ the system ($s^{*}$) have negative direction parameters 
($v_{s^{*}} = -1$). The quantity $\dot{x}_{s}$ denotes the rate of stuff flowing in stream $s$ (units of the quantity of stuff per time e.g., kg/hr); we'll use the $\dot{\star}$ to denote rate. 

### Generation terms:
The term $\dot{x}_{gen}$ in Eqn \eqref{eqn-total-stuff} describes the rate of stuff generation inside the system.
The generation of stuff inside the system is used to describe chemical reactions, heat sources or sinks or other abstract
quantities such as interest or the return on an investment. If stuff is being constructed (destroyed), 
the $\dot{x}_{gen}$ terms will be positive (negative). 

### Accumulation terms:
On the right hand side of Eqn \eqref{eqn-total-stuff} we have the $dx/dt$ or accumulation terms.
These terms describe rate of stuff accumulation inside the system. Often we'll consider a 
special case in which the inputs, outputs and generation terms are balanced and not changing in time.
This special case is called a steady-state, in a steady-state all accumulation terms are equal to 0.  