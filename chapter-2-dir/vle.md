# Vapor Liquid Equilibrium

## Introduction
Fill me in

---

(content:references:vle-model)=
## Simplifications
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

### Ideal binary phase diagrams
A [phase diagram](https://en.wikipedia.org/wiki/Phase_diagram) is a diagram that shows the conditions at which thermodynamically distinct phases (solid, liquid, or vapor states) occur and coexist at equilibrium. Equation {eq}`eqn-vle-design-eqn-ideal` is useful in calculating [binary phase diagrams](https://en.wikipedia.org/wiki/Phase_diagram#Binary_mixtures), i.e., the phase diagram for a mixture of two components. 

Binary mixtures are convenient because they can easily be visualized. We consider two types of binary phase diagrams:  {ref}`content:references:vle-pressure-composition` and {ref}`content:references:vle-temperature-composition`.

(content:references:vle-pressure-composition)=
#### Pressure composition diagrams
A binary pressure composition diagram, typically called a Pxy diagram, shows the relationship between the phases co-existing in equilibrium for different binary mixtures of components A and B at a fixed temperature and varying pressures. Pressure composition diagrams have two lines, a liquid, and a vapor line.

##### Ideal liquid line
The liquid line governs the composition of a mixture of the component set $\mathcal{M}$ in the liquid phase during vapor-liquid equilibrium. 

````{prf:observation} Derivation of the liquid line
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

````{prf:observation} Derivation of the liquid line
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

where the temperature $T$ has units of degree celcius $^{\circ}C$, and the constants $A$, $B$ and $C$ are tabulted in reference sources. Using Eqn. {eq}`eqn-binary-liquid-line` and Eqn. {eq}`eqn-binary-vapor-line` the Pxy diagram for the Acetone(1) and Water(2) is shown in Fig. ZZ.



```{figure} ./figs/Fig-Pxy-acetone-water-80C.pdf
---
height: 380px
name: example-acetone-water-binary-ideal-pxy
---
Ideal pressure composition (Pxy) diagram for a binary mixture of Acetone and Water at T = 80$^{\circ}$C. Antoine parameters were taken from Table B.2 of Smith, Van Ness, Abbott and Swihart 8th edition.
```

__source__: Fill me in

````

(content:references:vle-temperature-composition)=
#### Temperature composition diagrams
A binary temperature composition diagram, typically called a Txy diagram, shows the relationship between the phases co-existing in equilibrium for different binary mixtures of components A and B at a fixed pressure and varying temperature. 

The liquid line in a Txy diagram has the same functional form as Eqn. {eq}`eqn-binary-liquid-line` however, what is known versus unknown changes. In the case of a Txy diagram, the pressure and composition are _known_, but the temperature is _unknown_. Thus, we use the liquid model in Eqn. {eq}`eqn-binary-liquid-line` to solve for the temperature at different pressure composition pairs; the liquid line is a function of temperature because the saturation pressures $P_{i}^{sat}$ for each component are functions of temperature. 

(content:references:flash-separation-calculations)=
## Flash operations
Fill me in

(content:references:liquifaction)=
## Liquifaction
Fill me in.

---

## Summary
Fill me in