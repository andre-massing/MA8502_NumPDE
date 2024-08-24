---
jupytext:
  formats: md:myst
  text_representation:
    extension: .md
    format_name: myst
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---

## The finite element method

Finite element methods are specific realizations of
the Galerkin method.
In a nutshell, the basis functions of the discrete
function spaces are constructed from in three steps:

1. Generation of mesh $\mcT_h = \{T\}$ which is a partition of the domain $\Omega$ into smaller subunits $T$, the mesh elements.
2. On each mesh element, a (local) finite dimensional function space $V_T$ is constructed which has a fixed dimension.
3. The global discrete function space $V_h$ is patched together suitably from the local, 
element-wise define function spaces. How the local function spaces 
are patched together will determine the resulting conformity of the
global function space $V_h$, e.g. whether $V_h \subset L^2(\Omega)$
or $V_h \subset H^1(\Omega)$. 
We start with the simplest 1D example
to illustrate the most import concepts, before we formalize and extend those to cover the plethora of finite element families which exist out there today.

### Finite element in 1D
Consider a the finite interval $\Omega = (a, b)$. To create a mesh, we introduce $N+2$
**nodes** or **vertices** $\{x_i\}_{i=0}^{N+1}$ such that
$a = x_0 < x_1 < \ldots < x_N < x_{N+1} = b$. 
Then the corresponding **mesh** $\mcT_h = \{T_i\}_{i=1}^{N+1}$
is simply the finite collection of the $N+1$ subelements 
$T_i = [x_{i-1}, x_i]$ which are the **mesh elements**.
We set mesh size $h_T$
\begin{align}
\text{Local mesh size}\; &h_T = \diam(T) \text{ for } T \in \mcT_h 
\\
\text{Global mesh size}\;  &h = \max_{T \in \mcT_h} h_T
\end{align}
As usual, for a set $U \subset \RR^n$, we set $\diam(U) := \sup \{\| \bfx - \bfy \| : \bfx, \bfy \in U  \}$, 
which for our particular case means that
$\diam(T_i) = |x_i - x_{i-1}|$.

{.bg}
#### Continuous piecewise linear elements
Next, we construct continuous, piecewise linear finite elements defined on $\mcT_h$
```{math}
\PPc_1(\mcT_h)= \{ v \in C(\Omega) : v|_T \in \PP_1(T)\; \forall T \in \mcT_h \}
```
A typical function $u_h \in \PPc_1(\mcT_h)$ approximating some function $u$ is shown in the figure below.
```{image} ./fem_1d.png
:align: center
```

```{admonition} TODO
:class: :danger :dropdow
Improve figure, denotes nodes and elements. 
```

This global discrete function space can be constructed by defining suitably chosen basis functions
for the space $\PP_1(T_i)$
on each mesh element $T_i$ and then patching them together to form a global basis for $V_h$.
Let's focus on some element $ T = T_i = [x_{i-1}, x_i]$ for the moment and
introduce the interpolation nodes $\xi_0 = x_{i-1}$ and $\xi_1 = x_i$, 
then our beloved Lagrange basis functions $\{\phi_j^T\}_{j=1}^2$ are defined as
the unique linear functions which satisfy

```{math}
:label: lagrange_basis_1d
\phi_j^T(\xi_k) = \delta_{jk} \quad \text{for } j, k = 0, 1.
```

```{code-cell} ipython3

import ipywidgets as widgets
widgets.IntSlider(
    value=1,
    min=1,
    max=5,
    step=1,
    description='Element order:',
    disabled=False,
    continuous_update=False,
    orientation='horizontal',
    readout=True,
    readout_format='d'
)
```

```{admonition} TODO
:class: :danger :dropdow
Add code with slider which shows the basis functions for different elements orders,
both locally and the resulting functions in the global space.
```

### Meshes

### Ciarlet definition of finite elements

### Local interpolation operators

### Global interpolation operators