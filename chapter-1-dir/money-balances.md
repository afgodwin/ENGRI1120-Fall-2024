# Financial Balances

## Introduction
The development of processes or products does not occur inside a mythical universe that is free 
from market forces. Instead, processes and products must be, at a minimum, financially neutral to be viable.
Processes and products that are not financially viable, while perhaps being technically 
innovative or otherwise advantageous, will not survive in the marketplace without external support e.g., local, state or federal government subsities. 

In this lecture we will:
Fill me in. 

---

## Abstract Assets

```{figure} ./figs/Fig-Asset-CashFlowDiagram.pdf
---
height: 240px
name: cash-flow-abstract-asset-fig
---
Abstract asset diagram. During each time period $t=1,2,\dots,T$ an asset has cash flow(s) $CF_{t}$. The value of the asset is some function $\mathcal{V}$ of these cash flows; the 
function $\mathcal{V}$ is the called the valuation operator.  
```

In abstract sense, an _asset_ is simply a sequence of current and future cash flows 
demarcated in some currency, for example, Euros, Dollars, Yuan, or cryptocurrencies such as Bitcoin.
Thus, the value of an asset can be determined using a valuation operator $\mathcal{V}$ applied to these current and future cash flows:


```{math}
:label: eq-asset-cash-flows
\mathcal{V}\left(Asset_{t}\right) = \mathcal{V}\left(CF_{t},CF_{t+1},\dots,CF_{t+T-1}\right)
```
where $CF_{t}$ denotes the cash flow in time period $t$ up to $T$ time periods in the future.
The most common (and intuitive) valuation operator $\mathcal{V}$ is the sum of net cash flows in each time period, i.e., we compute the net cash in each period (cash inflow - cash outflow in period $i$) and then sum these net cash flows over all $T-1$ periods. 
However, there is a critical and fundamental challenge to this intuition. 

```{prf:remark} Time value of Money
The value of money is _not_ conserved over time. One dollar today is not worth the same as one dollar tomorrow. The change in the value of money over time is called the _time value of money_.  
```

### Time value of money
The value of money is not conserved; one dollar T years from now is worth _less than_ one dollar today. The change in the value of money over time is called the _time value of money_. The time value of money is an [empirical observation that has been seen over hundreds of years](https://en.wikipedia.org/wiki/Time_value_of_money#History). But why is this the case? 

The short answer: money given to us today has a greater utility than the same amount tomorrow; because we have an extra day to invest that money. 

````{prf:observation} Why does that value of money chnage over time?
:label: obs-time-value-of-money

Hypothetically, suppose a _risk-free_ investment was guaranteed to return $i>0$ in some period. If we invested $P$ dollars today in this risk-free investment, then at the end of the investment period, we are _guaranteed_ to get $F$ dollars back (because the investment is risk-free) where $F$ is given by:

```{math}
F = (1+i)\cdot{P}
```

Thus, if given a choice between $P$ dollars today, or the same $P$ dollars one investment period in the future, you would _always_ choose (assuming you were a rational investor) to take the $P$ now; you could invest those $P$ dollars now in a risk-free product and get $F = (1+i)\cdot{C}$ back, where $F>C$. The only case where it makes sense to take the future money is if $i=0$, i.e., $F = P$ (which is forbidden by the condition $i>0$).

This explanation assumes that a _risk-free_ investment exists that always returns $i>0$. Does such an investment exist? [Unfortunately no, the _risk-free_ investment is only a theoretical concept](https://www.investopedia.com/terms/r/risk-freerate.asp). However, the _risk-free rate of return_ $i$ is often approximated by the [yield on 10-year US Treasury bonds](https://www.bloomberg.com/markets/rates-bonds/government-bonds/us). 

````

Unfortunately, our intuitive valuation operator (net cash flows) does not implicitly consider (yet) the time of value of money. 

### Exchange rate model
A useful mental model for the time value of money is to think of money from different time periods 
as being in different currencies (e.g., $\$$ and $\def\euro{\unicode{x20AC}} \euro$) that must be exchanged. Thus, to compare money or cash flows from different time periods we formulate the equivalent of an exchange rate.

#### Discrete one-period conversion
For example, suppose we wanted to convert the value of a cash flow from one time period in the future 
into today's dollars (or vice-versa, we want to compute the value of a future cash flow to a current value). To do this, we use a one-period discrete conversion:

````{prf:definition} One Period Discrete Conversion
:label: defn-one-perod-discrete-conversion
For any one-period ($t\rightarrow{t+1}$),  the present value of cash flow, denoted as $CF_{t}$, and the future value of cash-flow, denoted by $CF_{t+1}$, there exists a one time-step discrete conversion:

```{math}
:label: eq-cash-flow-1-period
CF_{t+1} = \left(1+r_{t+1,t}\right)\cdot{CF_{t}}
```
where $r_{t+1,t}>{0}$ is called the rate of return between periods $t$ and $t+1$. The term $(1+r_{t+1,t})$, which denotes the hypothetical exchange rate between time period $t$ and $t+1$, is called the _discrete discount factor_. Because $r_{t+1,t}>{0}$, the _discrete discount factor_ is always greater than one, thus $CF_{t+1}>{CF_{t}}$ for any $t$. 
````

Let's do a few examples to illustrate one-period conversions.

````{prf:example} One Period Conversion

Prof. Varner offers to buy you a coffee tommorrow (one time period in the future) for $CF_{2} = \$ 3.35$. How much is the future coffee worth today if $r_{21}=0.10$? 

Let's put some numbers into Eqn. {eq}`eq-cash-flow-1-period` to answer this.  Rearraninging Eqn. {eq}`eq-cash-flow-1-period` for $CF_{1}$ gives:

```{math}
CF_{1} = \frac{CF_{2}}{1+r_{21}}
```

Subsutituing $r_{21} = 0.10$ and $CF_{2}=\$ 3.35$ says the current value of your future coffee is: $CF_{1} = \$ 3.05$.
````

#### Discrete multiple-period conversion
Suppose, instead of a single period, we are interested in an asset that will be active over multiple periods, e.g., a multi-year project or some other transaction that occurs over many years. In this case, we develop a multi-year conversion that is easily constructed by sequentially applying many one-period calculations.

To see this idea, let's start with period one to period two:
```{math}
CF_{2} = \left(1+r_{21}\right)\cdot{CF_{1}}
```
Then, period two to period three is given by:

```{math}
CF_{3} = \left(1+r_{32}\right)\cdot{CF_{2}}
```

but we can substiture $CF_{2}$ into the expression above to give:

```{math}
CF_{3} = \Bigl[\left(1+r_{32}\right)\left(1+r_{21}\right)\Bigr]\cdot{CF_{1}}
```

If we do this computation between 3 and 4, and then 4 to 5, etc, we develop a relationship between the current value of cash flow ($t=1$) and the future ($t>1$) value of cash flows:

````{prf:definition} Multiple Period Discrete Conversion
:label: defn-multi-perod-discrete-conversion

Let $CF_{1}$ denote the cash-flow in period 1 (current value), and $CF_{t}$ the cash-flow in period $t>1$ (future value). Futher, let $r_{j+1,j}$ denote the rate of return between discrete time period $j$ and $j+1$. Then: 

```{math}
:label: eq-cash-flow-multiple-period
CF_{t} = \left[\prod_{j=1}^{t-1}\left(1+r_{j+1,j}\right)\right]\cdot{CF_{1}}\qquad{t=2,3,\dots,T}
```
````

The product term (the $\prod\star$ in the brackets) in Eqn. {eq}`eq-cash-flow-multiple-period` is called the _multi-period discount factor_ and given the symbol $\mathcal{D}$. Thus, Eqn. {eq}`eq-cash-flow-multiple-period` can be written in a more compact form as:

```{math}
	CF_{t} = \mathcal{D}_{t,1}\cdot{CF_{1}}\qquad{t=2,3,\dots,T}
```

In the particular case where the rates of return $r_{\star}$ are equal in each period (let's call this value $\bar{r}$), the _multi-period discount factor_ is given by:

```{math}
\mathcal{D}_{t,1} = (1+\bar{r})^{t-1}\qquad{t=2,3,\dots,T}
```

Let's do some multi-period discounting examples to better understand {prf:ref}`defn-multi-perod-discrete-conversion`. 

````{prf:example} What is \$1 collected T time periods in the future worth today? 
:label: ex-future-value-discrete


The value of money today is the present value, whereas the value of money in the $T$ time units from now is the future  value.
In terms of the asset model, $CF_{1}$ denotes the present value (i = 1 denotes now), 
while $CF_{i},i=2,3,\dots,T$ denotes future value. Thus, to compute the present value of \$1 collected $T$ time units into the future, we solve Eqn. {eq}`eq-cash-flow-multiple-period` 
for $CF_{1}$ in terms of the future value $CF_{i},i=2,\dots,T$ and the discount factor 
$\mathcal{D}$:

```{math}
CF_{1} = \mathcal{D}_{i1}^{-1}CF_{i}\qquad{i=2,3,\dots,T}
```

where $\mathcal{D}_{i1}^{-1}$ is given by:

```{math}
\mathcal{D}_{i1}^{-1} = \frac{1}{(1+r)^{i-1}}\qquad{i=2,3,\dots,T}
```

We have assumed a constant discount rate $r$ between now (i = 1) and $i = T$ time units into the future. 
Given that we are looking at the present value of \$1, we can set $CF_{i}$ = 1, which gives:


```{math}
CF_{1} = \frac{1}{(1+r)^{i-1}}\qquad{i=2,3,\dots,T}
```

````

#### Continuous compounding
When we formulated Eqn. {eq}`eq-cash-flow-1-period` we used a finite discrete-time difference, e.g., days, weeks, or maybe even years. However, suppose the time difference between $t\rightarrow{t+1}$ were infetesimmaly small, i.e., the time difference was continuous. In this case, we have [continuous compounding](https://www.investopedia.com/terms/c/continuouscompounding.asp) where the discount factor 
$\mathcal{D}$ is defined as:


```{math}
\mathcal{D}(r,t) = \exp\left(rt\right)
```

A continuous discount factor gives a future value expression of the form:

```{math}
:label: eq-cont-exchange-tvm
CF(t) = \exp\left(rt\right)CF(t_{o})
```

where $r$ denotes the _instantaneous_ discount rate.  Of course there is a relationship between the discrete and continous cases because we know that:

```{math}
\exp\left(x\right) = \sum_{k=0}^{\infty} \frac{x^{k}}{k!} = 1+x+\frac{x^{2}}{2}+\frac{x^{3}}{6}+\dots
```

````{prf:example} What is \$1 collected today worth T years from now? 
:label: ex-future-value-continuous

Let's consider the opposite case as the previous example. Suppose we are given \$1 dollar today. What is the future value of \$1 in T years from now for a 2.0\% instantaneous annualized discount factor. 

````

## Net Present Value (NPV)
```{figure} ./figs/Fig-FinanicalNode-Schematic.pdf
---
height: 220px
name: cash-financial-node-flow-fig
---
Node cash-flow balance diagram. During time $t=k$ monety flows enter (revenues) and exit (expenses) the time-node.  
```

Now that we have tools to account for the time value of money, we can return to the question of how to value an asset. The most intuitive aproach is to compute the net cash flow at every node. Imagine at node $t=k$ we have $\mathcal{S}^{t=k}$ cash streams, denoted as $\dot{C}_{s}$, entering (or exiting) the asset node. Then, the net cash would at node $t=k$ is given by:

```{math}
CF_{k} = \sum_{s\in\mathcal{S}^{t=k}}\nu_{s}\dot{C}_{s}
```

where $\nu_{s}$ denotes a direction parameter; $\nu_{s}=+1$ is stream $s$ enters node $t=k$, $\nu_{s}=-1$ is stream $s$ exists node $t=k$. Finally, to value an asset, we could imagine adding up all the current and future cash flows, converted to some shared basis, e.g., current dollars. This sum is called the Net Present Value (NPV); NPV is a widespread method for asset valuation. As well shall see, NPV is also a widely used tool for financial decision-making.   

````{prf:definition} Discrete Net Present Value
:label: net-present-value-defn

The Net Present Value (NPV) is the sum of current and future cash flows, corrected to current dollars:

```{math}
\text{NPV} = CF_{1} + \sum_{t=2}^{T}CF_{t}^{(1)}
```

where $CF_{1}$ denotes current cash flows, and $CF_{t>1}^{(1)}$ denotes the future value of cash flow
written on the basis of current dollars. However, we can convert future dollars to current dollars using the discrete discount multistep discount factor $\mathcal{D}_{t,1}$, which gives the NPV expression:

```{math}
\text{NPV} = CF_{1} + \sum_{t=2}^{T}{\mathcal{D}_{t,1}^{-1}}\cdot{CF_{t}}
```

where the value of each cash flow at time $\star$, denoted by $CF_{\star}$, is the net cash flow:

```{math}
CF_{\star} = \sum_{s\in\mathcal{S}^{t=\star}}\nu_{s}\dot{C}_{s}
```

````

---

## Summary
Fill me in.
