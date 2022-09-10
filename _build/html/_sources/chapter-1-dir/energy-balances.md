# Energy Balances

## Introduction 
The second foundational law of Chemical Engineering is the law of conservation of energy: the total energy can neither be created nor destroyed, just transformed from one form to another. Let's build upon the law of conservation of energy, and our previous stuff balances discussion. Let _stuff_ equal the total energy $E$ (units: energy/mass or energy/mol) of working material, e.g., water in a system. 

Chemical Engineers are interested in the energy balance in two different types of systems, an open- and closed-system. An open system is one in which mass (or moles) can be transferred into or from the system across the boundary between the system and the surroundings. On the other hand, in a closed system, there is no mass (or mole) transfer between the surroundings.

This lecture will introduce two energy balances, open and closed energy balances, and some common simplifying assumptions applied to energy balances. Further, we'll present two critical examples of processes with an immense social benefit that come from the manipulation of the energetic state of a working material, namely, the [Rankine Cycle](https://en.wikipedia.org/wiki/Rankine_cycle), which is used for power generation, and the [vapor-compression refrigeration cycle](https://en.wikipedia.org/wiki/Vapor-compression_refrigeration) which is used for cooling. 

In particular, in this lecture we will:

* Formulate the {ref}`content:references:coeb` equation which governs the energy of the working material in an open system
* Introduce the {ref}`content:references:first-law-thermo` which governs the energy of the working material in an close system
* Introduce two important applications of open energy balance equations, the {ref}`content:references:rc` and the {ref}`content:references:vcrc`

---

(content:references:coeb)=
## Continuous open energy balance
Let's start with the continuous open energy balance and then use that to develop
the energy balance for a closed system. Suppose we have a system separated from its surroundings by a boundary ({numref}`fig-system-surroundings-energy`).

```{figure} ./figs/Fig-EnergySchematic.pdf
---
height: 420px
name: fig-system-surroundings-energy
---
Schematic of an open system and its surroundings. $\mathcal{S}$ streams enter or exit from the system transfering both energy and mass with the surroundings. 
```

If the boundary is open, then just like stuff balances, the total energy balance has four terms;
energy can be transferred into or from the system by transport in the streams (or by other transfer processes), energy can be generated, and energy can accumulate inside the system. However, because of the conservation of total energy, the energy generation terms are equal to zero. 

````{prf:observation} What is Total Energy?
The _total energy_ (units: total energy per unit mass or mol) 
is the sum of different types of energy. In most chemical engineering systems,
we'll consider three types of energy: internal, potential and kinetic energy.
Thus, $E$ (or equivalently $E_{s}$ for the stream $s$) can be written as:

$$
\begin{equation}
E = U + \frac{1}{2}u^{2} + gz
\end{equation}
$$

The first term, the internal energy $U$ (units: energy/mass), describes the chemical energy of the system or stream. The second term describes the kinetic energy of the system or stream. In contrast, the last term represents the potential energy, where $u$ denotes the velocity,  $g$ denotes the gravitational constant, and $z$ denotes the system’s height or stream.
````

Putting these ideas together, we can write the time-dependent total energy and mass balance equations that describe the total energy (or mass) of the system shown in ({numref}`fig-system-surroundings-energy`):

````{prf:definition} Total Open Energy Balance
:label: defn-total-open-energy-balance

Suppose an open system is separated from its surroundings by a boundary that can be crossed by streams in the set $\mathcal{S}$. Further, suppose the system can transfer heat and work with its surroundings. 

Then, the total energy (and mass) of the system is described by the total open energy (mass) balance equations:

$$
\begin{eqnarray}\label{eqn:general-energy-balance}
\frac{d}{dt}\left(mE\right) &=& v_{Q}\dot{Q}+\dot{W}+\sum_{s\in\mathcal{S}}v_{s}E_{s}\dot{m}_{s}\\\label{eqn:mass-balance}
\frac{dm}{dt} &=& \sum_{s\in\mathcal{S}}v_{s}\dot{m}_{s}
\end{eqnarray}
$$

The left-hand side(s) of these equations describe the rate of accumulation of total energy (or mass) in the system, where $E$ denotes the total energy per unit mass (units: energy/time or mass/time), while the right-hand side describes the various sources and sinks of energy (or mass):

 * The terms $\dot{Q}$ (units: energy/time) and $\dot{W}$ (units: energy/time) denote the rate of heat and work transferred to/from the system across the boundary from the surroundings, 
 * The terms $E_{s}$ denotes the total specific energy contained in stream $s$ (units: energy/mass), and $\dot{m}_{s}$ (units: mass/time) denote the mass flow rate in stream $s$. 

Lastly, the quantity $v_{s}$, and $v_{Q}$ denote direction parameters; $v_{\star}$ = 1 
if stream $s$ (or heat or work) enters the system, while $v_{\star}$ = -1 if stream $s$ (or heat or work) 
exits the system. Work follows our convention, but the description uses different phrasing; work done _on the system_ from the surroundings has a direction parameter equal to one, while work done _by the system_ on the surroundings has a direction parameter equal to negative one. We handle work below. 
````

(content:references:terms-simplification-total-e-bal)=
### Terms and Simplifications

#### Simplify the total energy $E$
In most (but not all) Chemical Engineering applications we make a critical simplfying assumption: the change in the kinetic and potential energy of the system and its streams is negligible compated to changes in the internal energy. 

````{prf:observation} Ignore Potential and Kinetic Energy
:label: obs-ignore-potential-ke

Let’s assume that the kinetic and potential energy changes in both the system and streams are negligible. This assumption is reasonable for a system as the center of mass of most chemical engineering systems is typically not moving. However, this assumption may not be valid for streams in some applications. 

If the total energy is approximately the internal energy $E\simeq~U$, the total energy (mass) balance is:

$$
\begin{eqnarray}
\frac{d}{dt}\left(mU\right) &=& v_{Q}\dot{Q}+\dot{W}+\sum_{s\in\mathcal{S}}v_{s}U_{s}\dot{m}_{s}\\
\frac{dm}{dt} &=& \sum_{s\in\mathcal{S}}v_{s}\dot{m}_{s}
\end{eqnarray}
$$(eqn-open-energy-U)
````

#### Simplifying the rate of work $\dot{W}$
The rate of work $\dot{W}$ is the sum of multiple types of work. 
However, in most chemical engineering systems, we'll consider only three types of works; shaft work, boundary work and flow work:

$$
\begin{equation}\label{eqn:work-expansion}
	\dot{W} = v_{W}\dot{W}_{sh}+\dot{W}_{b}+\sum_{s\in\mathcal{S}}v_{s}\left(PV\right)_{s}\dot{m}_{s}
\end{equation}
$$
where the term $\dot{W}_{sh}$ denotes the rate of shaft work (units: energy/time), where 
$v_{W}$ denotes a shaft work direction parameter ($+1$ in, $-1$ out.) The term $\dot{W}_{b}$ denotes the rate of system boundary expansion work (units: energy/time),and the summation term in describes a special kind of work called flow work (units: energy/time). 
Shaft work $\dot{W}_{sh}$ is the work associated with agitators or other mechanical items acting upon the system. On the other hand, the rate of boundary work (otherwise known as pressure-volume expansion work) describes the work incurred when the system boundary expands against an external pressure:

$$
\begin{equation}
	\dot{W}_{b} = -P_{\perp}\frac{dv}{dt}
\end{equation}
$$

where $v$ denotes the volume of the system (units: L), 
and $P_{\perp}$ denotes the pressure of the surroundings (units: Pa).
Lastly, flow work describes the work required to push molecules into or from the system in steam $s$, 
where $\left(PV\right)_{s}$ denotes the product of the pressure and volume of stream $s$.

````{prf:observation} Origin of Specific Enthalpy
:label: obs-specific-enthalpy

Substituting the shaft, system expansion and flow works terms into Eqn. {eq}`eqn-open-energy-U` gives the expression:

$$
\begin{equation}
	\frac{d}{dt}\left(mU\right) = v_{Q}\dot{Q}+v_{w}\dot{W}_{sh}+\dot{W}_{b}+
	\sum_{s\in\mathcal{S}}v_{s}\left(U+PV\right)_{s}\dot{m}_{s}
\end{equation}
$$(eqn-almost-E-bal)

where the terms $\left(U+PV\right)_{s}$ have a special name, the specific enthalpy $H_{s}$ (units: energy/mass):

$$
\begin{equation}
	H_{s}\equiv\left(U+PV\right)_{s}\qquad{s=1,2,\dots,\dim\mathcal{M}}
\end{equation}
$$

Substituting the definition of specific enthalpy Eqn. {eq}`eqn-almost-E-bal` gives the open energy balance:

$$
\begin{equation}
	\frac{d}{dt}\left(mU\right) = v_{Q}\dot{Q}+v_{W}\dot{W}_{sh}+\dot{W}_{b}+
	\sum_{s\in\mathcal{S}}v_{s}H_{s}\dot{m}_{s}
\end{equation}
$$
````

### Specific Open Enthalpy Balance
The specific enthalpy, defined as the sum of the system's internal energy and the product of its pressure and volume (see {prf:ref}`obs-specific-enthalpy`), is a property of the molecules of a system or stream. Internal energy is chemical energy, while the pressure-volume term measures the mechanical energy of the molecules in a system or stream.  In particular, the pressure-volume term expresses the work required to establish the system's physical dimensions, i.e., the energy needed to displace the surroundings. The pressure-volume term is minimal for solids and liquids under standard conditions and relatively small for gases. Thus, enthalpy (to a first approximation) can be considered a surrogate for the internal energy of the molecules that make up a system or stream.  

Putting all the simplifications together that were described in the {ref}`content:references:terms-simplification-total-e-bal` section, gives the open enthalpy balance:

````{prf:definition} Continuous Open Energy Balance
:label: defn-cont-open-energy-balance

Assume we have an open system with $\mathcal{S}$ streams flowing between it and the surroundings. Further, assume that we neglect changes in kinetic and potential energy in the system and streams. Lastly, assume we have no chemical reactions occurring in the system. 

Then, the continuous open energy and mass balance equationws describing the internal energy $U$ and mass $m$ of working material in the system are given by:

$$
\begin{eqnarray}
\frac{d}{dt}\left(mU\right) &=& v_{Q}\dot{Q}+v_{W}\dot{W}_{sh}+\dot{W}_{b}+
	\sum_{s\in\mathcal{S}}v_{s}H_{s}\dot{m}_{s}\\
\frac{dm}{dt} &=& \sum_{s\in\mathcal{S}}v_{s}\dot{m}_{s}
\end{eqnarray}
$$

where $\dot{Q}$ denotes the rate of heat input into or from the system (energy/time), $\dot{W}_{sh}$ denotes the rate of shaft work (units: energy/time), $\dot{W}_{b}$ denotes the rate of system boundary expansion work (units: energy/time) and $H_{s}$ denotes the specific enthalpy of stream $S$. The terms $\dot{m}_{s}$ (units: mass/time) denote the mass flow rate in stream $s$. Finally, 
$v_{\star}$ denote direction parameters; $v_{\star}$ = 1 if stream $s$ (or heat or work) enters the system, while $v_{\star}$ = -1 if stream $s$ (or heat or work) exits the system.

At steady-state, all time derivatives vanish giving the steady-state energy and mass balance equations:

$$
\begin{eqnarray}
v_{Q}\dot{Q}+v_{W}\dot{W}_{sh}+
	\sum_{s\in\mathcal{S}}v_{s}H_{s}\dot{m}_{s}  &=&  0 \\
\sum_{s\in\mathcal{S}}v_{s}\dot{m}_{s} &=& 0
\end{eqnarray}
$$

````

The open enthalpy balance described in {prf:ref}`defn-cont-open-energy-balance` is one of the main tools we use to design the operation of the [Rankine Cycle](https://en.wikipedia.org/wiki/Rankine_cycle), which is used for power generation, and the [vapor-compression refrigeration cycle](https://en.wikipedia.org/wiki/Vapor-compression_refrigeration) which is used for cooling. 

However, before considering the power generation and cooling cycles, let's look at the closed case, i.e., there is no transfer of energy (or mass) because of streams.

(content:references:first-law-thermo)=
## First Law of Thermodynamics
The closed form of the energy balance (where we assume negligible kinetic and potential energy changes) can be derived starting from {prf:ref}`defn-cont-open-energy-balance`. 

First, in a closed system there is no mass transport across the system boundary i.e., no inflow or outlflow streams ($\dot{m}_{s} = 0$). Next, the total mass $m$ inside a closed system is constant. Lastly, let's treat the time derivatives as infinitesimals; thus, we can multiply both sides of open energy balance by $dt$. Putting all these ideas together gives the closed energy balances, also called the First Law of Thermodynamics:

````{prf:definition} Closed Energy Balance
:label: defn-closed-energy-balance-first-law

The first law of thermodynamics is given by:

$$
\begin{equation}
	mdU = v_{Q}\dot{Q}dt+\dot{W}dt
\end{equation}
$$

In a closed system, there is no flow into or from the system, thus, the flow work is zero.
Moreover, let's assume there is no shaft work to consider. Thus, we only have boundary work or:

$$
\begin{equation}
	mdU = v_{Q}\dot{Q}dt - P_{\perp}dv
\end{equation}
$$

Dividing both sides both sides by the mass $m$ gives the closed energy balance (also called teh First Law of Thermodynamics):

$$
\begin{equation}\label{eqn:first-law}
	dU = v_{Q}\delta{Q} - P_{\perp}dV
\end{equation}
$$

where $V$ denotes the volume per unit mass (units: L/kg), and $\delta{Q}$ denotes the heat transfer per unit mass (units: J/kg) and is given by:

$$
\begin{equation}
	\delta{Q} = \frac{v_{Q}\dot{Q}dt}{m}
\end{equation}
$$
````

The closed energy balance described in {prf:ref}`defn-closed-energy-balance-first-law` is also known by a much fancier name: [The First Law of Thermodynamics](https://en.wikipedia.org/wiki/First_law_of_thermodynamics). The first law describes the pathways by which energy can be transferred in a closed system; it is a tremendously important theoretical tool but has little practical design significance as most actual systems are open. 

## Applications

### Pressure Enthalpy Diagrams
Fill me in. 

(content:references:rc)=
### Rankine Cycle
Fill me in.

(content:references:vcrc)=
### Vapor Compression Refrigeration Cycle
Fill me in.

---

# Summary
In this lecture: 

* We developed the open energy balance equations in which we neglected 
changes in kinetic and potential energy of the system and the streams. 
* We introduced the concept of specific enthalpy which is a 
special grouping of terms (the sum of the internal energy and pressure times volume) in both
the system and streams. 
* Starting from the open energy balance, we derived the closed ebergy balance which is also known as the First Law of Thermodynamics.