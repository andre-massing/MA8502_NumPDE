# Seminar problems I

## Inverse inequalities

## Local trace inequalities

## Nitsche's method

## Discontinuous Galerkin methods for high-contrast elliptic interface problems
Let $\Omega$ be a bounded, closed domain which is divided into two non-overlapping
subdomains $\Omega_1$ and $\Omega_2$ by an interface $\Gamma = \partial \Omega_1 \cap \partial \Omega_2$.
Consider the following Poisson interface problem for the stationary heat equation:
```{math}
:label: eq-poisson-interface-problem-proj1
:nowrap: True
\begin{alignat*}{3}
  -\nabla \cdot (\kappa \nabla u) &= f &&\quad \text{in } \Omega_1
  \cup \Omega_2,
  \\
  u &= g &&\quad \text{on } \partial \Omega,
  \\
  \jump{u} &= g_D &&\quad \text{on } \Gamma,
  \\
  \jump{\kappa\partial_n u} &= g_N &&\quad \text{on } \Gamma,
\end{alignat*}
```
where the restricted diffusion coefficient
$\kappa_i  =  \kappa|_{\Omega_i}$ is supposed to be constant for $i=1,2$.
The interface normal $n$ is pointing outward with respect to $\Omega_1$,
the solution and normal flux jumps across $\Gamma$ are defined as usual by respectively 
\begin{align}
  \jump{u} = u_1|_{\Gamma} - u_2|_{\Gamma},
  \quad \text{and } \quad
\jump{\kappa \partial_n u} =  \kappa_1 \nabla u_1 \cdot n - \kappa_2 \nabla u_2 \cdot n.
\end{align}

We assume that the interface $\Gamma$ matches the mesh,
i.e. the is a collection of faces $\mcF_h^{\Gamma} \subset \mcF_h$
such that $\Gamma = \bigcup_{F\in\mcF_h^{\Gamma}} {F}$.

In this problem set you will be guided to derive, theoretically analyse and 
practically implement a SIP formulation for the 
{eq}`eq-poisson-interface-problem-proj1` which is also robust 
in the so-called *high-contrast case* where $\kappa_2/\kappa_1 \gg 1$.

### Task 1 Weighted averages
The weighted average of the normal flux along $\Gamma$
is given by 
```{math}
:label: eq-weighted-flux
  \wavg{\kappa \partial_n v}
  =
    \omega_1 \kappa_1 \partial_n v_1 + \kappa_2 \partial_n v_2,
```
where the weights satisfy $0\leqslant \omega_1,\omega_2 \leqslant 1$ and  $\omega_1 + \omega_2 = 1$.
In the following, we will also make use of the dual weighted average,
```{math}
:label: eq-weighted-dual-flux
\wavgd{v}
 =
\omega_2 v_1 + \omega_1 v_2.
```

Show that the following "magic formula" holds

```{math}
\jump{v w} = \wavg{v}\jump{w} + \jump{v}\wavgd{w}.
```

### Task 2 Derivation of the SIP formulation

### Task 3 Discrecte coercivity
To account for high contrast interface problems where the ratio
$ \tfrac{\kappa_1}{\kappa_2}$ can become arbitrary large or small, we will
employ harmonic weights
following
%~\cite{Dryja2003,ErnStephansenZunino2008,BurmanZunino2012}
and set the weights $\omega_i$ and the stability parameter~$\gamma$ to
\begin{gather}
  \omega_1 = \frac{\kappa_2}{\kappa_1+\kappa_2},
  \quad
  \omega_2 = \frac{\kappa_1}{\kappa_1+\kappa_2},
  \quad 
   \gamma(\kappa_1, \kappa_2) = \widetilde{\gamma}_{\Gamma} \dfrac{2 \kappa_1 \kappa_2}{\kappa_1 + \kappa_2},
 \end{gather}
 with $\widetilde{\gamma}_{\Gamma}$ independent of $\kappa$.

### Task 4 A priori error estimates