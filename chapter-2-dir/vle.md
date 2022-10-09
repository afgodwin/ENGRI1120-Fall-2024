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

````



### Bubble and dew point calculations
Fill me in.

### Phase diagrams
Fill me in.

#### Pressure composition diagram
Fill me in.

#### Temperature composition diagram
Fill me in.

(content:references:flash-separation-calculations)=
## Flash operations
Fill me in

(content:references:liquifaction)=
## Liquifaction
Fill me in.

---

## Summary
Fill me in