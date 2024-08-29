(ch-adr-problems)=
# Advection-diffusion-reaction problems

In this chapter, we take a look at advection-diffusion-reaction (ADR) problems. We 
discuss briefly their well-posedness as  well the occurrence of
boundary layers which solution typically exhibits in the 
advection-dominated case, i.e. when the advection is much 
stronger than then diffusion. The section concludes 
with a short numerical example demonstrating the failure of
a straight-forward and simple finite element discretization
of an advection-dominant ADR problem. 

(sec-model-problem)=
## Model problem
Let $\Omega \subset \RR^d$ be an open and bounded domain. We try to find $u: \Omega \to \RR$ such that
```{math}
:nowrap: True
:label: eq-adr-problem
\begin{equation}
\left\{
\begin{alignedat}{2}
\mcA_{\epsilon} u = -\epsilon \Delta u + b\cdot\nabla u + c u &= f   & &\quad \text{in } \Omega, \\
                                                 u &= g_D & &\quad \text{on } \Gamma = \partial\Omega,
\end{alignedat}
\right.
\end{equation}
```
where
```{math}
:nowrap: True
\begin{alignat}{2}
& b: \Omega \to \RR^d &&\quad \text{ is the advection field}, \\
& c: \Omega \to \RR && \quad \text{ is the reaction term}, \\
& \epsilon > 0 && \quad\text{ is the diffusivity parameter.}
\end{alignat}
```

Typical assumptions are
1. $\epsilon \ll \|b\|_{\infty, \Omega}$ and $\|c\|_{\infty, \Omega}\| \ll \|b\|_{\infty, \Omega}$ (advection-dominant)
2. $\nabla\cdot b = 0 $ (flow field is incompressible) and $c \geqslant 0$
3. As an alternative to 2., one often requires that 
   $ \inf_{x \in \Omega} (c(x) - \tfrac{1}{2} \nabla \cdot b(x)) \geqslant c_0 > 0$


Later, we will need to distinguish between the inflow, outflow and characteristic parts of the boundary $\Gamma$.

````{prf:definition} Flow boundaries
```{math}
:nowrap: True 
\begin{alignat}{3}
&\text{Inflow boundary: }         && \quad \Gamma^- = \{ x \in \Gamma: b(x) \cdot n(x) < 0 \} \\
&\text{Outflow boundary: }        && \quad \Gamma^+ = \{ x \in \Gamma: b(x) \cdot n(x) > 0 \} \\
&\text{Characteristic boundary: } && \quad \Gamma^0 = \{ x \in \Gamma: b(x) \cdot n(x) = 0 \} \\
\end{alignat}
```
````

```{figure} ./relevant-flow-boundaries.jpeg
---
alt: Inflow, outflow and characteristic boundaries
align: center
width: 400px
name: flow-boundaries
---
The inflow, outflow and characteristic parts of the boundary $\Gamma$.
```

For $\epsilon \to 0$, we formally arrive at the **reduced problem**, which is of 
first order,
```{math}
b\cdot\nabla u + cu = f \quad \text{in } \Omega \quad \text{supplemented with suitable b.c.}
```
But what are proper b.c. in the reduced case? Let us recall the method of charateristics.

(sec-method-of-characteristics)=
## Method of characteristics

```{admonition} TODO
:class: :dropdown :danger
Discuss method of characteristics, boundary layers
```

Therefore, we conclude that for the reduced problem, we can only impose
Dirichlet b.c. on the inflow part of the boundary, i.e. $\Gamma^-$,

:::{prf:definition} Reduced problem for an advection-dominant ADR problem
:label: def-reduced-problem-adr
$$
b\cdot\nabla u + cu &= f_{\phantom{D}} \quad \text{in } \Omega,
\\
u &= g_D \quad \text{on } \Gamma^-.
$$
:::