# Energy Balances

## Introduction 
The second foundational law of Chemical Engineering is the law of energy conservation: the total energy can neither be created nor destroyed, just transformed from one form to another. Let's build upon the law of conservation of energy, and our previous stuff balances discussion. Let _stuff_ equal the total energy $E$ (units: energy/mass or energy/mol) of working material, e.g., water in a system. 

Chemical Engineers are interested in the energy balance in two different types of systems, an open- and closed-system. An open system is one in which mass (or moles) can be transferred into or from the system across the boundary between the system and the surroundings. On the other hand, in a closed system, there is no mass (or mole) transfer between the surroundings.

This lecture will introduce two energy balances, open and closed energy balances, and some common simplifying assumptions applied to energy balances. Further, we'll present two critical examples of processes with an immense social benefit that come from the manipulation of the energetic state of a working material, namely, the [Rankine Cycle](https://en.wikipedia.org/wiki/Rankine_cycle), which is used for power generation, and the [vapor-compression refrigeration cycle](https://en.wikipedia.org/wiki/Vapor-compression_refrigeration) which is used for cooling. 

In particular, in this lecture, we will:

* Formulate the {ref}`content:references:coeb` equation which governs the energy of the working material in an open system
* Introduce the {ref}`content:references:first-law-thermo`, which governs the energy of the working material in a closed system
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
\frac{d}{dt}\left(mE\right) &=& \dot{Q}+\dot{W}+\sum_{s\in\mathcal{S}}v_{s}E_{s}\dot{m}_{s}\\\label{eqn:mass-balance}
\frac{dm}{dt} &=& \sum_{s\in\mathcal{S}}v_{s}\dot{m}_{s}
\end{eqnarray}
$$

The left-hand side(s) of these equations describe the rate of accumulation of total energy (or mass) in the system, where $E$ denotes the total energy per unit mass (units: energy/time or mass/time), while the right-hand side describes the various sources and sinks of energy (or mass):

 * The terms $\dot{Q}$ (units: energy/time) and $\dot{W}$ (units: energy/time) denote the rate of heat and work transferred to/from the system across the boundary from the surroundings, 
 * The terms $E_{s}$ denotes the total specific energy contained in stream $s$ (units: energy/mass), and $\dot{m}_{s}$ (units: mass/time) denote the mass flow rate in stream $s$. 

Lastly, the quantity $v_{s}$ denote direction parameters; $v_{\star}$ = 1 
if stream $s$ enters the system, while $v_{\star}$ = -1 if stream $s$. 
exits the system. 

Work follows the sign convention; work done _on the system_ from the surroundings is positive, while work done _by the system_ on the surroundings is negative. 
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
\frac{d}{dt}\left(mU\right) &=& \dot{Q}+\dot{W}+\sum_{s\in\mathcal{S}}v_{s}U_{s}\dot{m}_{s}\\
\frac{dm}{dt} &=& \sum_{s\in\mathcal{S}}v_{s}\dot{m}_{s}
\end{eqnarray}
$$(eqn-open-energy-U)
````

#### Simplifying the rate of work $\dot{W}$
The rate of work $\dot{W}$ is the sum of multiple types of work. 
However, in most chemical engineering systems, we'll consider only three types of works; shaft work, boundary work and flow work:

$$
\begin{equation}\label{eqn:work-expansion}
	\dot{W} = \dot{W}_{sh}+\dot{W}_{b}+\sum_{s\in\mathcal{S}}v_{s}\left(PV\right)_{s}\dot{m}_{s}
\end{equation}
$$
where the term $\dot{W}_{sh}$ denotes the rate of shaft work (units: energy/time). The term $\dot{W}_{b}$ denotes the rate of system boundary expansion work (units: energy/time), and the summation term in describes a special kind of work called flow work (units: energy/time). Shaft work $\dot{W}_{sh}$ is the work associated with agitators or other mechanical items acting upon the system. On the other hand, the rate of boundary work (otherwise known as pressure-volume expansion work) describes the work incurred when the system boundary expands against an external pressure:

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
	\frac{d}{dt}\left(mU\right) = \dot{Q}+\dot{W}_{sh}+\dot{W}_{b}+
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
	\frac{d}{dt}\left(mU\right) = \dot{Q}+\dot{W}_{sh}+\dot{W}_{b}+
	\sum_{s\in\mathcal{S}}v_{s}H_{s}\dot{m}_{s}
\end{equation}
$$
````

### Specific Open Enthalpy Balance
The specific enthalpy, defined as the sum of the system's internal energy and the product of its pressure and volume (see {prf:ref}`obs-specific-enthalpy`), is a property of the molecules of a system or stream. Internal energy is chemical energy, while the pressure-volume term measures the mechanical energy of the molecules in a system or stream.  In particular, the pressure-volume term expresses the work required to establish the system's physical dimensions, i.e., the energy needed to displace the surroundings. The pressure-volume term is minimal for solids and liquids under standard conditions and relatively small for gases. Thus, enthalpy (to a first approximation) can be considered a surrogate for the internal energy of the molecules that make up a system or stream.  

Putting all the simplifications together that were described in the {ref}`content:references:terms-simplification-total-e-bal` section, gives the open enthalpy balance:

````{prf:definition} Continuous Open Energy Balance
:label: defn-cont-open-energy-balance

Assume we have an open system with the stream set $\mathcal{S}$ flowing between it and the surroundings. Further, assume changes in kinetic and potential energy in the system and streams are negligible. Lastly, assume no chemical reactions occur in the system. 

Then, the continuous open energy and mass balance equations describing the internal energy $U$ and mass $m$ of working material in the system are given by:

$$
\begin{eqnarray}
\frac{d}{dt}\left(mU\right) &=& \dot{Q}+\dot{W}_{sh}+\dot{W}_{b}+
	\sum_{s\in\mathcal{S}}v_{s}H_{s}\dot{m}_{s}\\
\frac{dm}{dt} &=& \sum_{s\in\mathcal{S}}v_{s}\dot{m}_{s}
\end{eqnarray}
$$

where $\dot{Q}$ denotes the rate of heat input into or from the system (energy/time), $\dot{W}_{sh}$ denotes the rate of shaft work (units: energy/time), $\dot{W}_{b}$ denotes the rate of system boundary expansion work (units: energy/time) and $H_{s}$ denotes the specific enthalpy of stream $S$. The terms $\dot{m}_{s}$ (units: mass/time) denote the mass flow rate in stream $s$. Finally, $v_{\star}$ denote direction parameters; $v_{\star}$ = 1 if stream $s$ (or heat or work) enters the system, while $v_{\star}$ = -1 if stream $s$ (or heat or work) exits the system.

At steady-state, all time derivatives vanish giving the steady-state energy and mass balance equations:

$$
\begin{eqnarray}
\dot{Q}+\dot{W}_{sh}+\sum_{s\in\mathcal{S}}v_{s}H_{s}\dot{m}_{s}  &=&  0 \\
\sum_{s\in\mathcal{S}}v_{s}\dot{m}_{s} &=& 0
\end{eqnarray}
$$

````

The open enthalpy balance described in {prf:ref}`defn-cont-open-energy-balance` is one of the main tools we use to design the operation of the [Rankine Cycle](https://en.wikipedia.org/wiki/Rankine_cycle), which is used for power generation, and the [vapor-compression refrigeration cycle](https://en.wikipedia.org/wiki/Vapor-compression_refrigeration) which is used for cooling. 



(content:references:first-law-thermo)=
## Closed Engergy Balance: First Law of Thermodynamics
Before considering the power generation and cooling cycles, let's look at the closed energy balance case, i.e., there is no transfer of energy (or mass) because of streams. The closed form of the energy balance (where we assume negligible kinetic and potential energy changes) can be derived starting from {prf:ref}`defn-cont-open-energy-balance`. First, in a closed system there is no mass transport across the system boundary i.e., no inflow or outlflow streams ($\dot{m}_{s} = 0$). Next, the total mass $m$ inside a closed system is constant. Lastly, let's treat the time derivatives as infinitesimals; thus, we can multiply both sides of open energy balance by $dt$. 

Putting all these ideas together gives the closed energy balances, also called the First Law of Thermodynamics:

````{prf:definition} Closed Energy Balance
:label: defn-closed-energy-balance-first-law

The first law of thermodynamics is given by:

$$
\begin{equation}
	mdU = \dot{Q}dt+\dot{W}dt
\end{equation}
$$

In a closed system, there is no flow into or from the system, thus, the flow work is zero.
Moreover, let's assume there is no shaft work to consider. Thus, we only have boundary work or:

$$
\begin{equation}
	mdU = \dot{Q}dt - P_{\perp}dv
\end{equation}
$$

Dividing both sides both sides by the mass $m$ gives the closed energy balance (also called teh First Law of Thermodynamics):

$$
\begin{equation}\label{eqn:first-law}
	dU = \delta{Q} - P_{\perp}dV
\end{equation}
$$

where $V$ denotes the volume per unit mass (units: L/kg), and $\delta{Q}$ denotes the heat transfer per unit mass (units: J/kg) and is given by:

$$
\begin{equation}
	\delta{Q} = \frac{\dot{Q}dt}{m}
\end{equation}
$$
````

The closed energy balance described in {prf:ref}`defn-closed-energy-balance-first-law` is also known by a much fancier name: [The First Law of Thermodynamics](https://en.wikipedia.org/wiki/First_law_of_thermodynamics). The first law describes the pathways by which energy can be transferred in a closed system; it is a tremendously important theoretical tool but has little practical design significance as most actual systems are open. 

## Applications

### Real versus Ideal Processes
A key concept in when studying applications such as power generation, cooling, or other processes involving turbines, compressors, throttle valves, etc., is the notion of real versus ideal operation. The analogy we use to explain this distinction is friction; in physics, we often do various problems assuming a frictionless system and then correct this ideal picture by including a description of frictional losses. In processes, we take a similar approach, except it is not friction we neglect; it is the generation of [Entropy](https://en.wikipedia.org/wiki/Entropy).

```{prf:remark} What is Entropy?
:label: remark-entropy-defn

[Entropy](https://en.wikipedia.org/wiki/Entropy) measures a system’s state of disorder, randomness, or uncertainty. However, [entropy](https://en.wikipedia.org/wiki/Entropy) has many interpretations in different contexts. In the process context, when dealing with compressors, pumps, and turbines, [entropy](https://en.wikipedia.org/wiki/Entropy) is related to process non-ideality.

One interesting thing about [Entropy](https://en.wikipedia.org/wiki/Entropy): the total amount of [Entropy](https://en.wikipedia.org/wiki/Entropy) in the universe must remain the same or increase; this is the [second law of thermodynamics](https://en.wikipedia.org/wiki/Second_law_of_thermodynamics).
```

For process steps involving expansion or contraction, e.g., turbines, compressors/pumps, or throttle valves, an ideal system is called reversible, while a non-ideal system is called irreversible. While not physically real, a reversible expansion or contraction process is a useful theoretical tool. Reversible transformations are made using infinitesimally small steps, so small that each step can be modeled as a being in equilibrium. Thus, a reversible process can be considered as a sequence of equilibrium steps. On the other hand, irreversible processes are actual (not equilibrium steps). 

In the context of process equipment such as turbines, compressors/pumps, or throttle valves, a transformation has constant entropy if it is reversible and adiabatic, while an irreversible process generates entropy (even if it is adiabatic):

* Transformations in ideal (reversible) turbines, compressors/pumps are constant entropy, or [isoentropic](https://en.wikipedia.org/wiki/Isentropic_process). An [isoentropic process](https://en.wikipedia.org/wiki/Isentropic_process) is both reversible and adiabatic.
* Throttle values are adiabatic but irreversible by design; thus, throttle valves generate entropy.

Let's consider an example of a reversible (ideal) versus irreversible (actual) turbine.

````{prf:example} Reversible and Irreversible Turbine
:class: dropdown
:label: example-real-vs-ideal-work

Superheated steam at operating point $O_{1}$ passes through an adiabatic [steam turbine](https://en.wikipedia.org/wiki/Steam_turbine) where energy is extracted in the form of shaft work $\dot{W}_{sh}$. At the outlet of the [steam turbine](https://en.wikipedia.org/wiki/Steam_turbine), the working fluid is at operating point $O_{2}$. The [steam turbine](https://en.wikipedia.org/wiki/Steam_turbine) has a single input and a single output. 

What is the expression for work if the [steam turbine](https://en.wikipedia.org/wiki/Steam_turbine) operates at steady-state?

__Reversible__:
If the [steam turbine](https://en.wikipedia.org/wiki/Steam_turbine) operates reversibly, the maximum amount of work is captured in the process. Starting from open energy and mass balances, we get the system:

$$
\begin{eqnarray}
\dot{W}_{T} + \dot{m}_{1}H_{1} - \dot{m}_{2}H_{2} &=& 0\\
\dot{m}_{1} - \dot{m}_{2} &=& 0
\end{eqnarray}
$$(eqn-ss-oe-tm-p12-example)

The total mass balance says that rate of mass in equals the rate of mass out, i.e., $\dot{m}_{1} = \dot{m}_{2}\equiv\dot{m}$. Then the expression of work is:

```{math}
:label: eqn-work-rev-example
\dot{W}_{T} = \dot{m}\left(H_{2} - H_{1}\right)
```

__Irreversible__:
If the [steam turbine](https://en.wikipedia.org/wiki/Steam_turbine) operates irreversibly, then _less than the maximum amount of work_ is captured in the process (and entropy is generated). Starting from the open energy and mass balances, we get the work expression:

```{math}
:label: eqn-work-irr-example
\dot{W}^{*}_{T} = \dot{m}\left(H_{2}^{*} - H_{1}\right)
```

where $H_{2}^{*}$ denotes the actual enthalpy observed after passing through the [steam turbine](https://en.wikipedia.org/wiki/Steam_turbine); we know that $H_{2}^{*}>H_{2}$ because less work was recovered. Unfortunately, we (typically) can't know $H_{2}^{*}$ beforehand. 

__Turbine Efficiency__:
We quantify the expected versus actual work recovered as the efficiency of the turbine $\eta_{T}$:

```{math}
:label: eqn-turbine-eff
\eta_{T} = \frac{\dot{W}^{*}_{sh}}{\dot{W}_{sh}}
```

Thus, a hypothetical totally reversible turbine has an efficiency $\eta_{T} = 1$, while actual [steam turbines](https://en.wikipedia.org/wiki/Steam_turbine) have $\eta_{T}<1$. When doing process calculations, we first assume all [steam turbines](https://en.wikipedia.org/wiki/Steam_turbine) are perfectly efficient; then, we correct these hypothetical _happy path_ values using the measured efficiencies. 

````


### Pressure Enthalpy (PH) Diagrams

In process calculations, we need the enthalpies at the various operating points $O_{\star}$; where do we get them?

```{figure} ./figs/Fig-PH-R508B.pdf
---
height: 520px
name: fig-ph-diagram-R508B
---
Pressure enthalpy diagram for the refrigerant [R-508B](https://en.wikipedia.org/wiki/List_of_refrigerants). 
```

For the different working materials, enthalpies have been computed using a combination of experimental measurements and [equation of state mathematical models](https://en.wikipedia.org/wiki/Equation_of_state) as a function of pressure and temperature. These values are plotted on Pressure-Enthalpy (PH) diagrams; an example PH-diagram for the refrigerant [R-508B](https://en.wikipedia.org/wiki/List_of_refrigerants) is shown in {numref}`fig-ph-diagram-R508B`.

Pressure enthalpy diagrams not only show the enthalpy values (horizontal axis) versus the pressure (vertical axis), they often show lines of constant temperature, lines of constant entropy, lines of constant specific (molar) volume, and the saturation dome. Thus, they are handy diagrams. 

(content:references:rc)=
### Ideal Rankine Cycle
The Rankine cycle is an open four step cyclic process used to generate power ({numref}`fig-rc-diagram`). Traditionally the working fluid of the [Rankine Cycle](https://en.wikipedia.org/wiki/Rankine_cycle) is [water](https://en.wikipedia.org/wiki/Water), however other working fluids can also be used, e.g., [the organic rankine cycle](https://en.wikipedia.org/wiki/Organic_Rankine_cycle) which uses organic, high molecular mass fluid.


```{figure} ./figs/Fig-RC-Labeled-F22.pdf
---
height: 380px
name: fig-rc-diagram
---
Piping and instrumentation diagram (PID) for the Rankine Cycle (RC) operating between the operating points $O_{\star}$. 
```

In the cycle, the path $\mathcal{P}_{ij}$ connects operating point $O_{i}$ to $O_{j}$:

* Path $\mathcal{P}_{12}$ from $O_{1}~\rightarrow~O_2$ the working fluid undergoes adiabatic expansion in a turbine. The working fluid moves from a superheated vapor at $O_{1}$ to a mixture of liquid and vapor at $O_{2}$. Work is generated on this path.
* Path $\mathcal{P}_{23}$ from $O_2~\rightarrow~O_3$ the working fluid undergoes isobaric cooling in a condenser unit. The working fluid moves from mixture of liquid and vapor at $O_{2}$ to a saturated liquid at $O_{3}$.  
* Path $\mathcal{P}_{34}$ from $O_3~\rightarrow~O_4$ the working fluid is adiabatically compressed in a pump.
* Path $\mathcal{P}_{41}$ from $O_4~\rightarrow~O_1$ the working fluid undergoes isobaric heating in a boiler unit from a saturated liquid at $O_{4}$ to a superheated vapor at $O_{1}$.

#### Steady-state analysis of the RC
To understand the opertion of the Rankine Cycle (RC), and to compute the {ref}`content:references:rc-efficiency`, we write the energy and mass balances around each one of the process units; each path $\mathcal{P}_{ij}$ is a path through a process unit. In particular, for each path apply the steady-state open energy and total mass balance equations:

$$
\begin{eqnarray}
\dot{Q}+\dot{W}_{sh}+\sum_{s\in\mathcal{S}}v_{s}H_{s}\dot{m}_{s}  &=&  0 \\
\sum_{s\in\mathcal{S}}v_{s}\dot{m}_{s} &=& 0
\end{eqnarray}
$$

##### Path $\mathcal{P}_{12}$: Turbine unit
The turbine has a single input and a single output. Further, while there is no heat flow from the compressor unit (adiabatic), there is a shaft work stream from the cycle at the rate $\dot{W}_{T}$. Thus, the energy and mass balances become:

$$
\begin{eqnarray}
\dot{W}_{T} + \dot{m}_{1}H_{1} - \dot{m}_{2}H_{2} &=& 0\\
\dot{m}_{1} - \dot{m}_{2} &=& 0
\end{eqnarray}
$$(eqn-ss-oe-tm-p12-rc)

````{prf:observation} Turbine work $\dot{W}_{T}$ expession
:label: obs-rc-turbine-work

Starting from the steady-state energy and mass balances around the turnine unit given by Eqn. {eq}`eqn-ss-oe-tm-p12-rc`, we can solve for the steady-state rate of work output into the turbine (units: energy per time):

```{math}
\dot{W}_{T} = \dot{m}\left(H_{2} - H_{1}\right)
```

where $H_{\star}$ denotes the enthalpy (units: energy per mass) at operating point $O_{\star}$ and $\dot{m}$ denotes the mass flow rate of working fluid through the process unit (units: mass per time).

````

##### Path $\mathcal{P}_{23}$: Condenser unit
The condenser has a single input and a single output. Further, while there is a heat flow from the condenser unit $\dot{Q_{C}}$, which exits the cycle, there is no shaft work stream. Thus, the energy and mass balances become:

$$
\begin{eqnarray}
\dot{Q}_{C} + \dot{m}_{2}H_{2} - \dot{m}_{3}H_{3} &=& 0\\
\dot{m}_{2} - \dot{m}_{3} &=& 0
\end{eqnarray}
$$(eqn-ss-oe-tm-p23-rc)

````{prf:observation} Condenser heat $\dot{Q}_{C}$ expession
:label: obs-rc-condenser-heat

Starting from the steady-state energy and mass balances around the condenser unit given by Eqn. {eq}`eqn-ss-oe-tm-p23-rc`, we can solve for the steady-state rate of heat output from the condenser (units: energy per time):

```{math}
\dot{Q}_{C} = \dot{m}\left(H_{3} - H_{2}\right)
```

where $H_{\star}$ denotes the enthalpy (units: energy per mass) at operating point $O_{\star}$ and $\dot{m}$ denotes the mass flow rate of working fluid through the process unit (units: mass per time).

````

##### Path $\mathcal{P}_{34}$: Pump unit
The pump has a single input and a single output. Further, while there is no heat flow to/from the pump unit (adiabatic), there is a shaft work stream into the cycle at the rate $\dot{W}_{P}$. Thus, the energy and mass balances become:

$$
\begin{eqnarray}
\dot{W}_{P} + \dot{m}_{3}H_{3} - \dot{m}_{4}H_{4} &=& 0\\
\dot{m}_{3} - \dot{m}_{4} &=& 0
\end{eqnarray}
$$(eqn-ss-oe-tm-p34-rc)

````{prf:observation} Pump work $\dot{W}_{P}$ expession
:label: obs-rc-pump-work

Starting from the steady-state energy and mass balances around the compressor unit given by Eqn. {eq}`eqn-ss-oe-tm-p34-rc`, we can solve for the steady-state rate of work input into the pump (units: energy per time):

```{math}
\dot{W}_{P} = \dot{m}\left(H_{4} - H_{3}\right)
```

where $H_{\star}$ denotes the enthalpy (units: energy per mass) at operating point $O_{\star}$ and $\dot{m}$ denotes the mass flow rate of working fluid through the process unit (units: mass per time).
````

##### Path $\mathcal{P}_{41}$: Boiler unit
Finally, superheated vapor is regenerated in the boiler unit. High pressure liquid at operating point $O_{4}$ is heated at constant pressure to a superheated vapor at operating point $O_{1}$. While the boiler has no shaft work, heat input is required to move from $O_{4}$ to $O_{1}$; let $\dot{Q}_{B}$ denote the rate of heat input into the boiler. Thus, the energy and mass balances around the boiler are:

$$
\begin{eqnarray}
\dot{Q}_{B} + \dot{m}_{4}H_{4} - \dot{m}_{1}H_{1} &=& 0\\
\dot{m}_{4} - \dot{m}_{1} &=& 0
\end{eqnarray}
$$(eqn-ss-oe-tm-p41-rc)

````{prf:observation} Boiler heat $\dot{Q}_{B}$ expession
:label: obs-rc-heat-rc

Starting from the steady-state energy and mass balances around the boiler unit given by Eqn. {eq}`eqn-ss-oe-tm-p41-rc`, we can solve for the steady-state rate of heat input into the boiler (units: energy per time):

```{math}
\dot{Q}_{B} = \dot{m}\left(H_{1} - H_{4}\right)
```

where $H_{\star}$ denotes the enthalpy (units: energy per mass) at operating point $O_{\star}$ and $\dot{m}$ denotes the mass flow rate of working fluid through the process unit (units: mass per time).
````

(content:references:rc-efficiency)=
#### Efficiency of the ideal RC
The efficiency of the [Rankine Cycle](https://en.wikipedia.org/wiki/Rankine_cycle) is defined as the ratio of the net work produced by the cycle to the heat input to the boiler:

````{prf:definition} Rankine Cycle Efficiency:
:label: defn-rc-efficency 

The efficiency of the [Rankine Cycle](https://en.wikipedia.org/wiki/Rankine_cycle) is defined as the ratio of the net work produced by the cycle to the heat input to the boiler:

```{math}
\eta = - \frac{\dot{W}_{T} - \dot{W}_{P}}{\dot{Q}_{B}}
```

However, in most applications, the work generated by the turbine is much larger than the pump work, i.e., $\dot{W}_{T}\gg\dot{W}_{P}$, thus, the efficiency $\eta$ is often approximated as:

```{math}
:label: eqn-rankine-eff-approx
\eta \simeq - \frac{\dot{W}_{T}}{\dot{Q}_{B}}
```

````

(content:references:vcrc)=
### Ideal Vapor Compression Refrigeration Cycle

The vapor compression refrigeration cycle (VCRC) is a four step open cyclic process to cool systems ({numref}`fig-vcrc-diagram`). Heat is removed from a cold system, and rejected to the surrondings on the hot side of the cycle. 
The working fluid in a vapor compression refrigeration cycle is called a [refrigerant](https://en.wikipedia.org/wiki/Refrigerant). 

```{figure} ./figs/Fig-VCRC-Labeled-F22.pdf
---
height: 380px
name: fig-vcrc-diagram
---
Piping and instrumentation diagram (PID) for the vapor compression refrigeration cycle (VCRC) operating between the operating points $O_{\star}$. The VCRC moves heat from cold to hot, which is not spontaneously possible; thus, it requires work input.  
```

In the vapor compression refrigeration cycle, the path $\mathcal{P}_{ij}$ connects operating point $O_{i}$ to $O_{j}$:
* Path $\mathcal{P}_{12}$: from $O_{1}~\rightarrow~O_{2}$ the working fluid undergoes [isobaric](https://en.wikipedia.org/wiki/Isobaric_process) heating in an evaporator unit. The working fluid moves from a mixture of liquid and vapor at $O_{1}$ to a saturated vapor at $O_{2}$, i.e., there is a phase change. 
* Path $\mathcal{P}_{23}$: from $O_{2}~\rightarrow~O_{3}$ the working fluid undergoes an [adiabatic](https://en.wikipedia.org/wiki/Adiabatic_process) compression in a compressor unit. The cool, saturated vapor at $O_{2}$ is compressed, and the pressure and the temperature increase in this path to reach $O_{3}$. Path $\mathcal{P}_{23}$ is a [constant entropy path](https://en.wikipedia.org/wiki/Isentropic_process). 
* Path $\mathcal{P}_{34}$: from $O_{3}~\rightarrow~O_{4}$ the working fluid undergoes an [isobaric cooling](https://en.wikipedia.org/wiki/Isobaric_process)) step in a condenser unit. High pressure, hot vapor at $O_{3}$ is condensed back to a saturated liquid at $O_{4}$.
* Path $\mathcal{P}_{41}$: from $O_{4}~\rightarrow~O_{1}$ the working fluid undergoes an [adiabatic](https://en.wikipedia.org/wiki/Adiabatic_process) and [isoenthalpic](https://en.wikipedia.org/wiki/Isenthalpic_process) irreversible expansion step in a throttle valve to move from a saturated liquid at $O_{4}$ to a mixture of vapor and liquid at $O_{1}$. Entropy is created in path $\mathcal{P}_{41}$.


#### Steady-state analysis of the ideal VCRC
To understand the opertion of the vapor compression refrigeration cycle, and to compute the {ref}`content:references:vcrc-efficiency`, we write the energy and mass balances around each one of the process units; each path $\mathcal{P}_{ij}$ is a path through a process unit. In particular, for each path apply the steady-state open energy and total mass balance equations:

$$
\begin{eqnarray}
\dot{Q}+\dot{W}_{sh}+\sum_{s\in\mathcal{S}}v_{s}H_{s}\dot{m}_{s}  &=&  0 \\
\sum_{s\in\mathcal{S}}v_{s}\dot{m}_{s} &=& 0
\end{eqnarray}
$$


##### Path $\mathcal{P}_{12}$: Evaporator unit
The evaporator has a single input and a single output. Further, while there is heat flow into the cycle at the rate $\dot{Q}_{E}$, there is no shaft work. Thus, the energy and mass balances become:

$$
\begin{eqnarray}
\dot{Q}_{E} + \dot{m}_{1}H_{1} - \dot{m}_{2}H_{2} &=& 0\\
\dot{m}_{1} - \dot{m}_{2} &=& 0
\end{eqnarray}
$$(eqn-ss-oe-tm-p12-vcrc)

````{prf:observation} Evaporator heat $\dot{Q}_{E}$ expession
:label: obs-vcrc-evap-heat

Starting from the steady-state energy and mass balances around the evaporator unit given by Eqn. {eq}`eqn-ss-oe-tm-p12-vcrc`, we can solve for the steady-state rate of heat input into the evaporator (units: energy per time):

```{math}
\dot{Q}_{E} = \dot{m}\left(H_{2} - H_{1}\right)
```

where $H_{\star}$ denotes the enthalpy (units: energy per mass) at operating point $O_{\star}$ and $\dot{m}$ denotes the mass flow rate of working fluid (units: mass per time).

````

##### Path $\mathcal{P}_{23}$: Compressor unit
The compressor has a single input and a single output. Further, while there is no heat flow from the compressor unit (adiabatic), there is a shaft work stream into the cycle at the rate $\dot{W}_{C}$. Thus, the energy and mass balances become:

$$
\begin{eqnarray}
\dot{W}_{C} + \dot{m}_{2}H_{2} - \dot{m}_{3}H_{3} &=& 0\\
\dot{m}_{2} - \dot{m}_{3} &=& 0
\end{eqnarray}
$$(eqn-ss-oe-tm-p23-vcrc)

````{prf:observation} Compressor work $\dot{W}_{C}$ expession
:label: obs-vcrc-compressor-work

Starting from the steady-state energy and mass balances around the compressor unit given by Eqn. {eq}`eqn-ss-oe-tm-p23-vcrc`, we can solve for the steady-state rate of work input into the compressor (units: energy per time):

```{math}
\dot{W}_{C} = \dot{m}\left(H_{3} - H_{2}\right)
```

where $H_{\star}$ denotes the enthalpy (units: energy per mass) at operating point $O_{\star}$ and $\dot{m}$ denotes the mass flow rate of working fluid through the process unit (units: mass per time).

````


##### Path $\mathcal{P}_{34}$: Condenser unit
The condenser has a single input and a single output. Further, while there is a heat flow from the condenser unit $\dot{Q_{C}}$, which exits the cycle, there is no shaft work stream. Thus, the energy and mass balances become:

$$
\begin{eqnarray}
\dot{Q}_{C} + \dot{m}_{3}H_{3} - \dot{m}_{4}H_{4} &=& 0\\
\dot{m}_{3} - \dot{m}_{4} &=& 0
\end{eqnarray}
$$(eqn-ss-oe-tm-p34-vcrc)

````{prf:observation} Condenser heat $\dot{Q}_{C}$ expession
:label: obs-vcrc-condenser-heat

Starting from the steady-state energy and mass balances around the condenser unit given by Eqn. {eq}`eqn-ss-oe-tm-p34-vcrc`, we can solve for the steady-state rate of heat output from the condenser (units: energy per time):

```{math}
\dot{Q}_{C} = \dot{m}\left(H_{4} - H_{3}\right)
```

where $H_{\star}$ denotes the enthalpy (units: energy per mass) at operating point $O_{\star}$ and $\dot{m}$ denotes the mass flow rate of working fluid through the process unit (units: mass per time).

````

##### Path $\mathcal{P}_{41}$: Throttle valve
Finally, the throttle valve has no moving parts; hence there is no shaft work. Further, the throttle valve is both adiabatic and constant enthalpy. Thus, the energy balance is identically zero while the mass balance is:

```{math}
\dot{m}_{4} - \dot{m}_{1} = 0
```



(content:references:vcrc-efficiency)=
#### Efficiency of the VCRC
The efficiency of the vapor compression refrigeration cycle is called the [coefficient of performance (COP)](https://en.wikipedia.org/wiki/Coefficient_of_performance).

````{prf:definition} Coefficient of Performance VCRC
The [coefficient of performance (COP)](https://en.wikipedia.org/wiki/Coefficient_of_performance) for the vapor compression refrigeration cycle is the ratio of the heat moved by the system $\dot{Q}_{E}$ to the shaft work paid to drive that heat $\dot{W}_{C}$.

```{math}
\text{COP} = \frac{\dot{Q}_{E}}{\dot{W}_{C}}
```

Substituting expression for $\dot{Q}_{W}$ and $\dot{W}_{C}$ from the steady-state open energy balances gives the expression:

```{math}
\text{COP} = \frac{\Delta{H}_{21}}{\Delta{H}_{32}}
```

where $\Delta{H}_{ij} = H_{i} - H_{j}$. The bigger the value of the COP, the more efficient the VCRC, i.e., we want the numerator to be as large as possible and the denominator as small as possible for an efficient cycle. 

````

#### Irreversibilities in the VCRC
In much the same way as the Rankine cycle, the vapor compression refrigeration cycle can have process irreversibilities. In particular, the transformation in the compressor unit can operate irreversibly, i.e., generate entropy. However, in this case, the entropy generation does not lead to less work captured. Instead, it results in more work required to compress the working fluid from operating points $\mathcal{O}_{2}\rightarrow\mathcal{O}_{3}$.

We account for the process irreversibilities in the vapor compression refrigeration cycle, and in particular the compressor step, by formulating a compressor efficiency $\eta_{C}$:

```{math}
\eta_{C} = \frac{\dot{W}_{C}}{\dot{W}^{\star}_{C}}
```

where $\dot{W}_{C}$ denotes the rate of _ideal_ work, and $\dot{W}^{\star}_{C}$ represents the rate of _actual_ work required to compress the working fluid from operating points $\mathcal{O}_{2}\rightarrow\mathcal{O}_{3}$. If $\eta_{C}$ = 1, then we have a completely reversible operation; if $\eta_{C}<1$, then the amount of work required to compress the working fluid from $\mathcal{O}_{2}\rightarrow\mathcal{O}_{3}$ is _larger_ that the ideal case.

The other process unit in the vapor compression refrigeration cycle that is irreversible is the throttle valve; however, this is by design. The throttle valve is an exciting operation with many applications, as we shall see. 


---

# Summary
In this lecture: 

* We developed the open energy balance equations in which we neglected 
changes in kinetic and potential energy of the system and the streams. 
* We introduced the concept of specific enthalpy which is a 
special grouping of terms (the sum of the internal energy and pressure times volume) in both
the system and streams. 
* Starting from the open energy balance, we derived the closed ebergy balance which is also known as the First Law of Thermodynamics.