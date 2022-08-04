# Energy Balances

## Introduction 
Thermodynamics is the study of the physical and energetic properties of chemical systems, and how we can exploit these properties for technological or societal benefit. At the center of thermodynamics, are energy balance equations. In this lecture, we'll introduce two energy balances, open and closed energy balances and some common simplifying assumptions applied to energy balances.

In particular, we will:

* Introduce the {ref}`content:references:coeb` principle
* Using the conservation of energy, formulate the {ref}`content:references:coeb` equation which governs the energy of the working material in an open system
* Introduce the {ref}`content:references:first-law-thermo` which governs the energy of the working material in an close system

---

(content:references:coe)=
## Conservation of Energy
A second foundational law of Chemical Engineering is the conservation of total energy $E$: 
total energy can neither be created nor destroyed, just transformed from one form to another:

$$
\begin{equation}
	\Delta{E}_{\mathrm{universe}} = \Delta{E}_{\mathrm{system}}+\Delta{E}_{\mathrm{surroundings}} = 0
\end{equation}
$$

where $\Delta\star$ denotes the difference operator. In this lecture, we build upon our previous stuff balances discussion. We let stuff equal the total energy $E$ (units: energy/mass or energy/mol) of working material, e.g., water in a system. In particular, Chemical Engineers are interested in the energy balance in two different systems, an open- and closed-system: 

* An open system is one in which mass (or moles) can be transferred into or from the system across the boundary between the system and the surroundings. 
* On the other hand, in a closed system, there is no mass (or mole) transfer between the surroundings.

We'll start with the continuous open energy balance and then use that equation to develop
the energy balance for a closed system. 

(content:references:coeb)=
## Continuous open energy balance

```{figure} ./figs/Fig-EnergySchematic.pdf
---
height: 420px
name: fig-system-surroundings-energy
---
Schematic of an open system and its surroundings. $\mathcal{S}$ streams enter or exit from the system transfering both energy and mass with the surroundings. 
```

Suppose we have a thermodynamic system separated from its surroundings by a boundary ({numref}`fig-system-surroundings-energy`).
Just like stuff balances, total energy balances have four terms;
energy can be transferred into or from the system in streams, or by other transfer processes, and
energy can accumulate inside the system. However, because of the conservation of total energy, 
energy generation terms are equal to zero. 

Putting these ideas together, we can write the time dependent energy and mass balance equations which describe the energy (or mass) inputs and outputs shown in {numref}`fig-system-surroundings-energy`):

$$
\begin{eqnarray}\label{eqn:general-energy-balance}
\frac{d}{dt}\left(mE\right)\Bigr|_{sys} &=& v_{Q}\dot{Q}+\dot{W}+\sum_{s=1}^{\mathcal{S}}v_{s}E_{s}\dot{m}_{s}\\\label{eqn:mass-balance}
\frac{dm}{dt} &=& \sum_{s=1}^{\mathcal{S}}v_{s}\dot{m}_{s}
\end{eqnarray}
$$

The left-hand side(s) of these equations describe the rate of accumulation of total energy (or mass) in the system (units: energy/time or mass/time), while the right-hand sides describe the various sources and sinks of energy (or mass).
In particular, the term $E$ denotes the total energy of the system per unit mass (units: energy/mass), 
$\dot{Q}$ (energy/time) and $\dot{W}$ (energy/time) denote the rate of heat and work transferred to/from the system from the surroundings, $E_{s}$ denotes the total specific energy contained in stream $s$ (units: energy/mass),
and $\dot{m}_{s}$ (units: mass/time) denote the mass flow rate in stream $s$. 
Lastly, the quantity $v_{s}$ and $v_{q}$ denote direction parameters; $v_{\star}$ = 1 
if stream $s$ (or heat or work) enters the system, while $v_{\star}$ = -1 if stream $s$ (or heat or work) 
exits the system.

### What is the specific total energy $E$?
The _specific total energy_ (units: total energy per unit mass or mol) 
is the sum of different types of energy. In most chemical engineering systems,
we'll consider three types of energy: internal, potential and kinetic energy.
Thus, $E$ (or equivalently $E_{s}$ for the stream $s$) can be written as:

$$
\begin{equation}
E = U + \frac{1}{2}u^{2} + gz
\end{equation}
$$

The first term, which denotes the internal energy $U$ (units: energy/mass), describes
the chemical energy of the system or stream. The second term describes the kinetic energy of the system or stream,
while the last term describes the potential energy, where $u$ denote the velocity, 
$g$ denotes the gravitational constant and $z$ denotes the height of the 
system or stream. 

````{note}

Lets _ignore_ changes in the kinetic and potential energy in both the system and streams. 

This assumption is reasonable for a system as the center of mass of most chemical engineering systems is typically not moving. 
However, for streams, this may not be valid in some applications. 

If the total energy is approximately the internal energy $E\simeq~U$, then the energy balance is:

```{math}
:label: eqn-open-energy-U
\frac{d}{dt}\left(mU\right) = v_{Q}\dot{Q}+\dot{W}+\sum_{s\in\mathcal{S}}v_{s}U_{s}\dot{m}_{s}
```
````


### What is work $\dot{W}$?
The rate of work $\dot{W}$ is the sum of multiple types of work. 
However, in most chemical engineering systems, we'll consider only three types of works; shaft work, boundary work and flow work:

$$
\begin{equation}\label{eqn:work-expansion}
	\dot{W} = v_{W}\dot{W}_{sh}+\dot{W}_{b}+\sum_{s=1}^{\mathcal{S}}v_{s}\left(PV\right)_{s}\dot{m}_{s}
\end{equation}
$$
where the term $\dot{W}_{sh}$ denotes the rate of shaft work (units: energy/time), where 
$v_{W}$ denotes a shaft work direction parameter ($+1$ in, $-1$ out.) The term $\dot{W}_{b}$ denotes the rate of system boundary expansion work (units: energy/time),
and the summation term in describes a special kind of work called flow work (units: energy/time). Shaft work $\dot{W}_{sh}$ is the work associated with agitators or other mechanical items acting upon the system. On the other hand, the rate of boundary work (otherwise known as pressure-volume expansion work) describes the work incurred when the system boundary expands against an external pressure:

$$
\begin{equation}
	\dot{W}_{b} = -P_{\perp}\frac{dv}{dt}
\end{equation}
$$
where $v$ denotes the volume of the system (units: L), 
and $P_{\perp}$ denotes the pressure of the surroundings (units: Pa).
Lastly, flow work describes the work required to push molecules into or from the system in steam $s$, 
where $\left(PV\right)_{s}$ denotes the product of the pressure and volume of stream $s$.

```{note}
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
	H_{s}\equiv\left(U+PV\right)_{s}\qquad{s=1,2,\dots,\mathcal{M}}
\end{equation}
$$

Substituting the definition of specific enthalpy Eqn. {eq}`eqn-almost-E-bal` gives the open energy balance:

$$
\begin{equation}
	\frac{d}{dt}\left(mU\right) = v_{Q}\dot{Q}+v_{W}\dot{W}_{sh}+\dot{W}_{b}+
	\sum_{s\in\mathcal{S}}v_{s}H_{s}\dot{m}_{s}
\end{equation}
$$
```

### What is the Specific Enthalpy?
Enthalpy is a property of the molecules of a system or stream and is defined as the sum of the system's 
internal energy and the product of its pressure and volume. Internal energy is the chemical energy, while the pressure-volume term measures the mechanical energy of the molecules in a system or stream.  In particular, the pressure-volume term expresses the work required to establish the system's physical dimensions, i.e., the energy needed to displace the surroundings. The pressure-volume term is minimal for solids and liquids under standard conditions and relatively small for gases. Thus, enthalpy (to a first approximation) can be considered a surrogate for the internal energy of 
the molecules that make up a system or stream. 

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

(content:references:first-law-thermo)=
## Closed energy balances and the First Law of Thermodynamics
The closed form of the energy balance (where we assume negligible kinetic and potential energy changes) can be derived starting from {prf:ref}`defn-cont-open-energy-balance`. First, in a closed system there is no mass transport across the system boundary i.e., 
no inflow or outlflow streams ($\dot{m}_{s} = 0$). Next, the total mass $m$ inside a closed system is constant. 
Lastly, let's treat the time derivatives as infinitesimals; thus, we can multiply both sides of open energy balance by $dt$ to give:

Putting all these ideas together gives the closed energy balances, also called the First Law of Thermodynamics:

````{prf:definition} First Law of Thermodynamics
:label: defn-closed-energy-balance

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

Equation \eqref{eqn:first-law} is also known by a much fancier name: The First Law of Thermodynamics. 
The first law describes the pathways by which energy can be transferred.
````

---

# Summary
In this lecture: 

* We developed the open energy balance equations in which we neglected 
changes in kinetic and potential energy of the system and the streams. 
* We introduced the concept of specific enthalpy which is a 
special grouping of terms (the sum of the internal energy and pressure times volume) in both
the system and streams. 
* Starting from the open energy balance, we derived the closed ebergy balance which is also known as the First Law of Thermodynamics.