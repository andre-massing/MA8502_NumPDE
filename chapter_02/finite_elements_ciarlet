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

```{admonition} TODO
:class: :danger :dropdow
Add figures
```

### Meshes

### Ciarlet definition of finite elements

### Local interpolation operators

### Global interpolation operators