
# Project 1: Discontinuous Galerkin methods for advection-diffusion-reaction problems

In this project you are asked to formulate, analyze, implement and test a discontinuous Galerkin
based solver for the diffusion-advection problem 

$$
\begin{alignedat}{3}
-\epsilon \Delta u_{\epsilon} + \boldsymbol{b} \cdot \nabla u_{\epsilon} + c u_{\epsilon}&= f &&\quad \text{in } \Omega
\\
u_{\epsilon} &= u_D &&\quad \text{on } \partial \Omega.
\end{alignedat}
$$ (eq-convection-diffusion-problem-proj1)

where $\epsilon > 0$ is the diffusivity parameter, $\boldsymbol{b} \in \mathbb{R}^2$ is the advection field, $c \in \mathbb{R}$ is the reaction term, and $f$ is a source term. The boundary condition $u_D$ is a given Dirichlet boundary condition on the boundary $\partial \Omega$ of the domain $\Omega$.

+++


## Part 1: The symmetric interior penalty method

For this part, set $\boldsymbol{b} = 0$  in {eq}`eq-convection-diffusion-problem-proj1`.

### Task 1: Local conservation properties of the symmetric interior penalty method

**1)** Show that the solution $u$ to the diffusion
problem {eq}`eq-convection-diffusion-problem-proj1` with 
$\epsilon = 1$, $\boldsymbol{b}=0$
and $c=0$ satisfies the conservation property

$$
- \int_{\partial U} \partial_n u = \int_U f
$$ (conserv-prop-cont)

for any open domain $U \subset \Omega$. 
On each mesh facet $F \in \mathcal{F}$, define the **exact flux** $\Phi_F(u)$ by

$$
\Phi_F(u) = \partial_{n_F} u = -\nabla u \cdot \boldsymbol{n}_F
$$

and introduce the "facet normal orientation function" 

$$
\varepsilon_{T,F}(x) = \boldsymbol{n}_{\partial T}(x) \cdot \boldsymbol{n}_F(x)
$$

so that

$$
\varepsilon_{T,F}(x) \boldsymbol{n}_F(x) = \boldsymbol{n}_{\partial T}(x)
$$

holds. In particular, {eq}`conserv-prop-cont` means that $u$ satisfies 

$$
\sum_{F\in \mathcal{F}(T)} \varepsilon_{T,F} \Phi_F(u) = \int_T f.
$$

where 
$\mathcal{F}(T) = \{F \in \mathcal{F}_h \mid F \subset \partial T \}.$

**2)** Now, consider the corresponding symmetric interior penalty and try 
to find a **discrete flux** $\phi_F(u_h)$ which is uniquely defined for each 
facet such  

$$
\sum_{F\in \mathcal{F}(T)} \varepsilon_{T,F} \phi_F(u_h) = \int_T f.
$$

holds.

*Hints*

- It will turn out that the "natural" discrete $\phi_F(u_h)$ is *not equal* $\Phi_F(u_h) = -\partial_{n_F} u_h$!
- Find the correct flux function by testing the SIP formulation with $v_h = \chi_T \in  \mathbb{P}^k_{\mathrm{dc}}$. Which terms in the bilinear form $a_h$ will not vanish? 

### Task 2: Implementation and testing

+++


## Part 2: The

### Task 2: Derivation and analysis
Formulate a discontinuous Galerkin formulation for the advection-diffusion problem
{eq}`eq-convection-diffusion-problem-proj1`
which combines the *symmetric interior penalty* (SIP) method for elliptic problems
with the *upwind-flux/stabilized* discontinuous Galerkin we considered for the
pure advection-reaction problem.
Give a short justification of your final formulation.

Based on the a priori error estimates we derived individually for the SIP method 
and upwind flux formulation, what kind of a priori estimate do 
you expect for your formulation?

Prove the formulated a priori error estimate from Task 1 by combining the
approaches we used to prove a priori error estimates for the SIP and the upwind flux formulation.

*Hints:*
Be clever and don't repeat step by step the entire theoretical analysis we developed
for the DG methods previously, but rather try combine them:
* To prove that the resulting bilinear form for the
  advection-diffusion-reaction is coercive with
  respect to a certain norm, use the discrete coercivity results we
  derived for SIP and for upwind flux formulation separately to 1) find
  the right norms form the combined bilinear form and 2) to give a quick
  proof of its coercivity.
* To establish an a priori error estimate, use the "orthogonal subscale" argument 
  to handle the advection-reaction part in the total bilinear form.  

### Task 2: Implementation and testing
Implement the DG formulation in either Gridap or ngsolve
which solves {eq}`eq-convection-diffusion-problem-proj1`
on the domain $\Omega = [0,1]^2$.
In your implementation allow for the possibility to switch between the
upwind-flux and central-flux formulations in the advective part.

Use the manufactured solution

\begin{align*}
 u_{\epsilon} = \cos(\pi x)\dfrac{1-e^{(y-1)/\epsilon}}{1-e^{-2/\epsilon}}
 + 0.5 \cos(\pi x)\sin(\pi y) \quad \text{in } \Omega
\end{align*}

with the velocity field $\boldsymbol{b} = (0,1)$ and $c = 0.1$
to conduct the following convergence studies
for **both the upwind-flux and the central flux** formulation:

Generate a series of meshes $\{\mathcal{T}_i\}_{k=0}^{N}$ with $N \geqslant 3$ and maximum mesh sizes $h_{k} =  0.2 \cdot 2^{-k}$. 
On each mesh you solve the advection-diffusion-reaction problem numerically and 
compute the norm of the error $e_k := u-u_k$ in the following norms
* $ \epsilon^{1/2}\|\nabla \cdot\|_{\Omega}$
* $ c_0^{1/2} \|\cdot\|_{\Omega} $
* $ \|h^{-1/2} [\cdot] \|_{\mathcal{F}_h}$
* $ \| |\boldsymbol{b}\cdot\boldsymbol{n}_F|^{1/2} [\cdot] \|_{\mathcal{F}_h}$
* $\| (\tfrac{h}{b_c})^{1/2} \boldsymbol{b} \cdot \nabla (\cdot) \|_{\Omega}$

Here, $u_k$ refers to the discrete solution $u_h$ on mesh $\mathcal{T}_k$.
Note, that we did not prove any error estimate for *scaled stream-line derivative norm*
$\| h^{1/2}/b_c \boldsymbol{b} \cdot \nabla (\cdot) \|_{\Omega}$, but one can prove
that the solution $u_h \in \mathbb{P}^k_{\mathrm{dc}}(\mathcal{T}_h)$ to the upwind-flux formulation also satisfies

$$
\| (\tfrac{h}{b_c})^{1/2} \boldsymbol{b} \cdot \nabla (u-u_h) \|_{\Omega} \lesssim h^{k+1/2} |u|_{k+1, \Omega}
$$

+++

For each computed error norm $E_k$, calculate the experimental order
of convergence defined by

$$
EOC(k) = \dfrac{\log(E_{k-1}/E_k)}{\log(h_{k-1}/h_k)}
$$

by either tabulating or plotting  the error norm contribution
$E_k$ as function of the mesh size in a $\log$-$\log$ plot.
Do such a convergence study for 
$\epsilon \in \epsilon = 1, 10^{-1}, 10^{-3}, 10^{-5}$.

Describe you observations, in particular 
* Comment on the observed EOC vs.  the theoretically predicted one
* Discuss the impact of $\epsilon$ on the observed EOC rates
* Discuss any significant difference between the central-flux and upwind-flux based solutions.

*Hints:*
Both ngsolve and gridap provide examples for various DG formulations,
see the [DG tutorial for ngsolve](https://docu.ngsolve.org/latest/i-tutorials/unit-2.8-DG/DG.html) and the [DG-tutorial for Gridap](https://gridap.github.io/Tutorials/dev/pages/t006_dg_discretization/#Tutorial-6:-Poisson-equation-(with-DG)-1).
