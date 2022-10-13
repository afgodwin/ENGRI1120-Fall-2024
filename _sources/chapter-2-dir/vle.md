# Vapor Liquid Equilibrium

## Introduction
Vapor-liquid equilibrium (VLE) describes the distribution of a chemical species between the vapor phase and a liquid phase in multicomponent phase equilibrium. Vapor-liquid equilibrium information is helpful in designing distillation processes, a fundamental chemical engineering separation technique; distillation is used to separate or partially separate components in a mixture by boiling (vaporization) followed by condensation. However, other types of separation processes rely on vapor-liquid equilibrium. For example, flash separation occurs when a saturated liquid stream undergoes a reduction in pressure by passing through a throttling valve, which gives a mixture in vapor-liquid equilibrium. Finally, liquefaction is a process that generates a liquid from a gas. Major commercial applications of liquefaction are the liquefaction of air, which allows the separation of constituents, such as oxygen, nitrogen, and noble gases, or the conversion of vapor fuels, such as methane, into a liquid form which is more convenient for transport. In all these applications, vapor-liquid equilibrium plays a critical role. 

In this lecture we will:

* Build upon our previous discussion of [multicomponent phase equilibrium](./single-component-phase-eq.md) and develop an {ref}`content:references:ideal-vle-model` and {ref}`content:references:vle-ideal-phase-diagrams`.
* Next, we'll use the {ref}`content:references:ideal-vle-model` to design {ref}`content:references:flash-separation-calculations`
* Finally, we'll use the {ref}`content:references:ideal-vle-model` to design {ref}`content:references:liquifaction`

---

(content:references:ideal-vle-model)=
## Ideal Vapor-Liquid Equilibrium model
[The fugacity matching condition](./single-component-phase-eq.md) given by {prf:ref}`defn-fugacity-matching-cond-eq`, in combination with phase specific fugacity models, gives us tools to design phase equilibrium processes. 

````{prf:definition} General Vapor Liquid Equlibrium

In vapor-liquid equilibrium, let’s consider a system with the composition set $\mathcal{M}$. The fugacity matching condition, along with the phase-specific models, gives the relationship:

```{math}
:label: eqn-vle-design-eqn
\hat{\phi}^{v}_{i}y_{i}P = \hat{\gamma}_{i}x_{i}\phi^{sat}_{i}P^{sat}_{i}\qquad\forall{i}\in\mathcal{M}
```

On the vapor side of Eqn. {eq}`eqn-vle-design-eqn`, the term $\hat{\phi}^{v}_{i}$ denotes the fugacity coefficient for component $i$, $y_{i}$ denotes the mole fraction of component $i$ in the vapor phase, and $P$ denotes the system pressure. 

On the liquid side of Eqn. {eq}`eqn-vle-design-eqn`, the term $\hat{\gamma_{i}}$ denotes the activity coefficient for component $i$, $x_{i}$ denotes the mole fraction of component $i$ in the liquid, $P^{sat}_{i}$ denotes the saturation pressure for component $i$, and $\phi^{sat}_{i}$ denotes the vapor phase fugacity coefficient for pure component $i$ at the saturation pressure.

````

The fugacity coefficient $\hat{\phi}_{i}^{v}$ and the activity coefficient $\hat{\gamma}_{i}$ describe the vapor and liquid phase non-ideality. There are a variety of models that can be used to capture the molecular interactions that are responsible for non-ideality. However, for now, we make an essential simplifying assumption typically not valid for a real system; namely, both the vapor and liquid are ideal. 

````{prf:observation} Ideal vapor and liquid phases
For ideal vapor or liquid phases, the fugacity and activity coefficients go to one; the Gibbs excess (resdiudal) energy is zero. Thus, Eqn. {eq}`eqn-vle-design-eqn` for ideal phases is given by:

```{math}
:label: eqn-vle-design-eqn-ideal
y_{i}P = x_{i}P^{sat}_{i}\qquad\forall{i}\in\mathcal{M}
```
where $x_{i}$ is a liquid-phase mole fraction, $y_{i}$ is a vapor-phase mole fraction, and $P_{i}^{sat}$ is the saturation pressure of pure species $i$ at the system temperature.
````

(content:references:vle-ideal-phase-diagrams)=
### Ideal binary phase diagrams
A [phase diagram](https://en.wikipedia.org/wiki/Phase_diagram) is a diagram that shows the conditions at which thermodynamically distinct phases (solid, liquid, or vapor states) occur and coexist at equilibrium. Equation {eq}`eqn-vle-design-eqn-ideal` is useful in calculating [binary phase diagrams](https://en.wikipedia.org/wiki/Phase_diagram#Binary_mixtures), i.e., the phase diagram for a mixture of two components. 

Binary mixtures are convenient because they can easily be visualized. We consider two types of binary phase diagrams:  {ref}`content:references:vle-pressure-composition` and {ref}`content:references:vle-temperature-composition`.

(content:references:vle-pressure-composition)=
#### Pressure composition diagrams (Pxy)
A binary pressure composition diagram, typically called a Pxy diagram, shows the relationship between the phases co-existing in equilibrium for different binary mixtures of components A and B at a fixed temperature and varying pressures. Pressure composition diagrams have two lines, a liquid, and a vapor line.

##### Ideal liquid line
The liquid line governs the composition of a mixture of the component set $\mathcal{M}$ in the liquid phase during vapor-liquid equilibrium. 

````{prf:observation} Derivation of the liquid line Pxy
:label: obs-derivation-liquid-line

Suppose we have a system composed of the species set $\mathcal{M}$ with $\dim\mathcal{M} = M$, in vapor-liquid equilibrium. Further, suppose both the vapor and liquid phases are ideal. 

To derive the liquid equilibrium line, we sum the equilibrium matching conditions, given by Eqn {eq}`eqn-vle-design-eqn-ideal`, over the species set $\mathcal{M}$:

$$
\begin{eqnarray}
y_{1}P &=& x_{1}P^{sat}_{1}\\
y_{2}P &=& x_{2}P^{sat}_{2}\\
& \vdots &  \\
y_{M}P &=& x_{M}P^{sat}_{M}
\end{eqnarray}
$$

which gives:

$$\left(y_{1}+y_{2}+\dots+y_{M}\right)P = x_{1}P^{sat}_{1}+x_{2}P^{sat}_{2}+\dots+x_{M}P^{sat}_{M}$$

However, we know that $\left(y_{1}+y_{2}+\dots+y_{M}\right)=1$, thus the liquid equilibrium line is given by:

```{math}
:label: eqn-liquid-eq-line
P = \sum_{i\in\mathcal{M}}x_{i}P^{sat}_{i}
```

````

For a binary system $\dim\mathcal{M}=2$ the liquid line given by Eqn {eq}`eqn-liquid-eq-line` is a sum over two components:

```{math}
:label: eqn-binary-liquid-line
P = x_{1}P_{1}^{sat} + (1-x_{1})P_{2}^{sat}
```

where we take advantage of the summation property of mole fraction, i.e., $\sum_{i\in\mathcal{M}}x_{i} = 1$. The ideal binary liquid line described by Eqn. {eq}`eqn-binary-liquid-line` is line connecting the saturation pressures $P^{sat}_{1}$ and $P^{sat}_{2}$ in the P-xy plane. 

##### Ideal vapor line
The vapor line governs the composition of a mixture of the component set $\mathcal{M}$ in the vapor phase during vapor-liquid equilibrium.  

````{prf:observation} Derivation of the vapor line
:label: obs-derivation-vapor-line

Suppose we have a system composed of the species set $\mathcal{M}$ with $\dim\mathcal{M} = M$, in vapor-liquid equilibrium. Further, suppose both the vapor and liquid phases are ideal.

To derive the vapor line, which governs the composition of the vapor phase, we solve Eqn. {eq}`eqn-vle-design-eqn-ideal` for the mole fraction of component $i$ in the vapor phase:

$$y_{i} = \frac{x_{i}P^{sat}_{i}}{P}$$

However, we know the pressure $P$ is governed by Eqn. {eq}`eqn-binary-liquid-line`, thus, the vapor phase mole fraction of component $i$ is given by:

```{math}
:label: eqn-vapor-mol-frac
y_{i} = \frac{x_{i}P^{sat}_{i}}{\displaystyle{\sum_{j\in\mathcal{M}}x_{j}P^{sat}_{j}}}\qquad\forall{i\in\mathcal{M}}
```
````

For a binary system $\dim\mathcal{M}=2$ the demoninator of the vapor line given by Eqn {eq}`eqn-vapor-mol-frac` is a sum over two components:

```{math}
:label: eqn-binary-vapor-line
y_{i} = \frac{x_{i}P^{sat}_{i}}{x_{1}P_{1}^{sat} + (1-x_{1})P_{2}^{sat}}\qquad{i=1,2}
```

The ideal binary vapor line described by Eqn. {eq}`eqn-binary-vapor-line` is a concave upward curve that connects the saturation pressures $P^{sat}_{1}$ and $P^{sat}_{2}$ in the P-xy plane. 

````{prf:example} Ideal Pxy diagram binary Acetone-Water mixture at T = 80$^{\circ}$C

Let's compute the pressure composition (Pxy) diagram for a binary mixture of Acetone(1) and Water(2) at T = 80$^{\circ}$C. Assume both the liquid and vapor phases are ideal and the saturation pressures for pure component $i$ are described by the [Antoine equation](https://en.wikipedia.org/wiki/Antoine_equation):

$$\ln{P_{i}^{sat}} = A - \frac{B}{T+C}$$

where the temperature $T$ has units of degree celcius $^{\circ}C$, and the constants $A$, $B$ and $C$ are tabulted in reference sources. Using Eqn. {eq}`eqn-binary-liquid-line` and Eqn. {eq}`eqn-binary-vapor-line` the Pxy diagram for the Acetone(1) and Water(2) is shown in Fig. {numref}`example-acetone-water-binary-ideal-pxy`.



```{figure} ./figs/Fig-Pxy-acetone-water-80C.pdf
---
height: 380px
name: example-acetone-water-binary-ideal-pxy
---
Ideal pressure composition (Pxy) diagram for a binary mixture of Acetone and Water at T = 80$^{\circ}$C. Antoine parameters were taken from Table B.2 of Smith, Van Ness, Abbott and Swihart 8th edition.
```

__source__: Fill me in

````

##### Equilibrium Tie-line on Pxy diagram

Pressure composition diagrams (Pxy) are useful because they map regions of liquid, vapor or liquid-vapor equilibrium. For example, consider the binary Acetone(1) - Water(2) system at P $\simeq$ 130 kPa and T = 80$^{\circ}$C ({numref}`example-acetone-water-binary-ideal-pxy-labels`).

```{figure} ./figs/Fig-Pxy-Diagram-Labels.pdf
---
height: 380px
name: example-acetone-water-binary-ideal-pxy-labels
---
Ideal pressure composition (Pxy) diagram for a binary mixture of Acetone(1) and Water(2) at T = 80$^{\circ}$C. Antoine parameters were taken from Table B.2 of Smith, Van Ness, Abbott, and Swihart 8th edition. Nomenclature: $x_{1}^{eq}$ denotes the equilibrium composition in the liquid; $y_{1}^{eq}$ denotes the equilibrium composition in the vapor.
```

We can draw a horizontal line of constant pressure, e.g., at P $\simeq$ 130 kPa, and estimate the compositions of Acetone(1)-Water(2) that exist as a liquid, a vapor or a mixed system in vapor-liquid equilibrium. The intersection of the pressure line with the liquid line gives the equilibrium composition of the liquid, denoted as $x^{eq}_{1}$. Likewise, the intersection of the constant pressure line with the vapor line gives the equilibrium composition in the vapor, denoted as $y^{eq}_{1}$.

The constant pressure line that connects the equilibrium liquid and vapor compositions is called the __constant pressure equilibrium tie-line__.


(content:references:vle-temperature-composition)=
#### Temperature composition diagrams (Txy)
A binary temperature composition diagram, typically called a Txy diagram, shows the relationship between the phases co-existing in equilibrium for different binary mixtures of components A and B at a fixed pressure and varying temperature. 

##### Ideal liquid line
The liquid line in a Txy diagram has the same functional form as Eqn. {eq}`eqn-liquid-eq-line` however, what is known versus unknown changes. In the case of a Txy diagram, the pressure and composition are _known_, but the temperature is _unknown_. Thus, we use the liquid model in Eqn. {eq}`eqn-liquid-eq-line` to solve for the temperature at different pressure composition pairs; the liquid line is a function of temperature because the saturation pressures $P_{i}^{sat}$ for each component are functions of temperature. 

````{prf:observation} Estimation of temperature Txy diagram
:label: obs-derivation-liquid-line-txy

Suppose we have a system composed of the species set $\mathcal{M}$ with $\dim\mathcal{M} = M$, in vapor-liquid equilibrium. Further, suppose both the vapor and liquid phases are ideal.

To estimate the temperature-composition relationship for the liquid phase components, when given the pressure, we minimize the squared difference between the pressure estimated by Eqn {eq}`eqn-liquid-eq-line` which we denote as $\hat{P}$ and the known system pressure:

```{math}
\min_{T} \left(P-\hat{P}\right)^{2}
```

subject to bounds on the temperature $0\leq{T}\leq\infty$. We solve this optimization problem for each liquid phase composition, i.e., for each value of $x_{i}$.

````



##### Ideal vapor line
The hard work when constructing a Txy diagram is done when computing the liquid line, i.e., repeadtly solving the optimization problem shown in {prf:ref}`obs-derivation-liquid-line-txy`. Once this is done, we can easily solve (at least in the ideal case) for the vapor phase composition.

````{prf:observation} Derivation of the vapor line Txy


Suppose we have a system composed of the species set $\mathcal{M}$ with $\dim\mathcal{M} = M$, in vapor-liquid equilibrium. Further, suppose both the vapor and liquid phases are ideal, and we have computed the liquid line.

Then, the vapor phase composition can be estimate for components $i=1,2,\dots,M$ from:

$$y_{i} = \frac{x_{i}P^{sat}_{i}}{P}\qquad\forall{i}\in\mathcal{M}$$

where the system pressure $P$ is known, and the $\left(x_{i},T_{i}\right)$ data from liquid line is used to compute the numerator.

````


````{prf:example} Ideal Txy diagram binary Acetone-Water mixture at P = 125 kPa

Let's compute the temperature composition (Txy) diagram for a binary mixture of Acetone(1) and Water(2) at P = 125 kPa. Assume both the liquid and vapor phases are ideal and the saturation pressures for pure component $i$ are described by the [Antoine equation](https://en.wikipedia.org/wiki/Antoine_equation):

$$\ln{P_{i}^{sat}} = A - \frac{B}{T+C}$$

where the temperature $T$ has units of degree celcius $^{\circ}C$, and the constants $A$, $B$ and $C$ are tabulted in reference sources.


```{figure} ./figs/Fig-Txy-acetone-water-P125Pka.pdf
---
height: 380px
name: example-acetone-water-binary-ideal-txy
---
Ideal temperature composition (Txy) diagram for a binary mixture of Acetone and Water at P = 125 kPa. Antoine parameters were taken from Table B.2 of Smith, Van Ness, Abbott and Swihart 8th edition.
```

__source__: Fill me in.

````

##### Equilibrium Tie-line on Txy diagram

Temperature composition diagrams (Pxy) are also useful because they map regions of liquid, vapor or liquid-vapor equilibrium at a fixed pressure for different temperatures. For example, consider the binary Acetone(1) - Water(2) system at P = 125 kPa and T $\simeq$ 83$^{\circ}$C ({numref}`example-acetone-water-binary-ideal-Txy-labels`).

```{figure} ./figs/Fig-Txy-Diagram-Labels.pdf
---
height: 380px
name: example-acetone-water-binary-ideal-Txy-labels
---
Ideal temperature composition (Txy) diagram for a binary mixture of Acetone(1) and Water(2) at P = 125 kPa. Antoine parameters were taken from Table B.2 of Smith, Van Ness, Abbott, and Swihart 8th edition. Nomenclature: $x_{1}^{eq}$ denotes the equilibrium composition in the liquid; $y_{1}^{eq}$ denotes the equilibrium composition in the vapor.
```

We can draw a horizontal line of constant temperature, e.g., at T $\simeq$ 83$^{\circ}C$, and estimate the compositions of Acetone(1)-Water(2) that exist as a liquid, a vapor or a mixed system in vapor-liquid equilibrium. The intersection of the temperature line with the liquid line gives the equilibrium composition of the liquid, denoted as $x^{eq}_{1}$. Likewise, the intersection of the constant temperature line with the vapor line gives the equilibrium composition in the vapor, denoted as $y^{eq}_{1}$.

The constant temperature line that connects the equilibrium liquid and vapor compositions is called the __constant temperature equilibrium tie-line__.

(content:references:flash-separation-calculations)=
## Flash separation processes

In a Flash separation process, a multicomponent saturated liquid composed of the species set $\mathcal{M}$ enters the Flash drum (at some temperature and pressure). Inside the drum the pressure is rapidly decreased leading to [flash vaporization](https://en.wikipedia.org/wiki/Flash_evaporation), and a liquid and vapor streams exit the drum ({numref}`fig-schematic-flash-sep-drum`). 


```{figure} ./figs/Fig-Flash-Sep-Schematic.pdf
---
height: 380px
name: fig-schematic-flash-sep-drum
---
Schematic of a Flash separation process. Nomenclature: $\dot{F}$ total mole flow into the unit (units: mol/time); $\dot{L}$ total mole flow rate of the liquid stream exiting the unit (units: mol/time); $\dot{V}$ total mole flow rate of the vapor stream exiting the unit (units: mol/time).
```

```{prf:remark} Flash equilibrium assumption
The key assumptions we make when modeling a Flash separation process are:
* The flash drum is well-mixed
* The contents of the drum are in vapor-liquid equilibrium, and hence, the vapor and liquid streams that exit the drum are in vapor-liquid equilibrium
* Equilibrium is instantaneous inside the drum
```

### Total and Species mole balance Flash drum
There are no chemical reactions occuring in the Flash drum, thus, the number of moles is conserved. The total mole balance around the Flash drum is given by:

```{math}
:label: eqn-total-mol-balance-flash-drum
\dot{F} = \dot{L} + \dot{V}
```

where $\dot{F}$ denotes the total mole flow into the unit (units: mol/time), $\dot{L}$ denotes the total mole flow rate of the liquid stream exiting the unit (units: mol/time), and $\dot{V}$ represents the total mole flow rate of the vapor stream leaving the unit (units: mol/time). 

Similarly, we can write a species mole balance around all the species in the species set $\mathcal{M}$:

```{math}
:label: eqn-species-mol-balance-flash-drum
\dot{F}z_{i} = \dot{L}x_{i} + \dot{V}y_{i}\qquad\forall{i}\in\mathcal{M}
```

where $z_{i}$ denotes the mole fraction of component $i$ in the input stream (we use $z$ to avoid confusion with the liquid stream exiting the unit), $x_{i}$ denotes the mole fraction of component $i$ in the liquid stream exiting the unit, and $y_{i}$ represents the mole fraction of component $i$ leaving the unit in the vapor stream. 

(content:references:liquifaction)=
## Liquifaction processes
Fill me in.

---

## Summary

In this lecture we:

* Built upon our previous discussion of [multicomponent phase equilibrium](./single-component-phase-eq.md) and developed an {ref}`content:references:ideal-vle-model` and {ref}`content:references:vle-ideal-phase-diagrams`.
* Second, we used the {ref}`content:references:ideal-vle-model` to design {ref}`content:references:flash-separation-calculations`
* Finally, we used the {ref}`content:references:ideal-vle-model` to design {ref}`content:references:liquifaction`