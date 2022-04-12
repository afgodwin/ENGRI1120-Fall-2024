# Chemical Reaction Kinetics
The _kinetics_ of a chemical reaction describes the _rate_ at which the reaction proceeds as a function of the conditions in the reactor vessel. Kinetic rate laws have units of $\star$mol/volume-time, and their mathematical form varies significantly with the type of reaction being considered. Let's start by considering the simple non-enzymatic (no catalyst) _reversible_ reaction:

$$A+B\leftrightharpoons{C}$$

A general form for the _net_ rate of this reaction ($\hat{r}_{1}$) is given by:

$$\hat{r}_{1} = k_{1}\prod_{i=1}^{\mathcal{M}}\left[X_{i}\right]^{\alpha_{i1}} - k_{1}^{\prime}\prod_{j=1}^{\mathcal{M}}\left[X_{j}\right]^{\beta_{i1}}$$

where $\left[X_{i}\right]$ denotes the concentration of component $i=1,2,\dots,\mathcal{M}$, and $\alpha_{i1}$ and $\beta_{i1}$ denote the _reaction order_ of component $i$ in reaction $\hat{r}_{1}$. The values of the reation orders $\alpha_{i1}$ and $\beta_{i1}$ depend upon the reaction, and may _not_ always be integer values. 
Lastly, the quantities $k_{1}$ and $k_{1}^{\prime}$ denote the rate constant for the forward and reverse directions, respectively. Rate constants have various units depending upon the values of $\alpha_{i1}$
and $\beta_{i1}$. 

There is no requirement that $\alpha_{i1}$ and $\beta_{i1}$ be integers (or the stoichiometric coefficients). This is often only true when we have a complete (or simplified) picture of the chemistry that is occurring. In real-life, fractional values for $\alpha_{i1}$ and $\beta_{i1}$ are common in many application areas.  

Another way to think about the kinetic rate laws and rate constants is that the overall rate of a reaction is proportional to the concentrations of the species that are participating in the reaction (raised to some power). Given this perspective, the rate constants are then simply constants of proportionality for each direction of the rate. The reaction orders ($\alpha_{i1}$ and $\beta_{i1}$) depend upon our understanding of the chemistry that is occurring, but in a simplified universe we can assume the [Law of Mass Action](https://en.wikipedia.org/wiki/Law_of_mass_action).

### Mass action kinetics

The [law of mass action](https://en.wikipedia.org/wiki/Law_of_mass_action) assumes that the net rate of a chemical reaction is proportional to the concentration of the components raised to the $-{1}\times$ the stoichiometric coefficient of that component in _a particular reaction direction_. For example, for the reaction $A+B\leftrightharpoons{C}$, the mass action rate law would be:

$$\hat{r}_{1} = k_{1}\left[A\right]\left[B\right] - k^{\prime}_{1}\left[C\right]$$

Thus, a general statement of the law of mass action for reaction $j$ (that could involve autocatalysis) is given by:

$$\hat{r}_{j} = k_{j}\prod_{i=1}^{\mathcal{M}}\left[X_{i}\right]^{-\sigma_{ij}} - 
k^{\prime}_{j}\prod_{i=1}^{\mathcal{M}}\left[X_{i}\right]^{-\sigma_{ij}}$$
