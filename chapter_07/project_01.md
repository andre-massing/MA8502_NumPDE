# Project 1

## Project 1: Discontinuous Galerkin methods for advection-diffusion-reaction problems

In this project you are asked to formulate, analyze, implement and test a discontinuous Galerkin
based solver for the diffusion-advection problem 
```{math}
:label: eq-convection-diffusion-problem-proj1
:nowrap: True
\begin{equation}
\begin{alignedat}{3}
-\epsilon \Delta u_{\epsilon} + \bfb \cdot \nabla u_{\epsilon} + c u_{\epsilon}&= f &&\quad \text{in } \Omega
\\
u_{\epsilon} &= u_D &&\quad \text{on } \partial \Omega.
\end{alignedat}
\end{equation}
```

### Task 1: Derivation and analysis
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
with the velocity field $\bfb = (0,1)$ and $c = 0.1$.
to conduct the following convergence studies
for **both the upwind-flux and the central flux** formulation:

Generate a series of meshes $\{\mcT_i\}_{k=0}^{N}$ with $N \geqslant 3$ and maximum mesh sizes $h_{k} =  0.2 \cdot 2^{-k}$. 
On each mesh you solve the advection-diffusion-reaction problem numerically and 
compute the norm of the error $e_k := u-u_k$ in the following norms
* $ \epsilon^{\onehalf}\|\nabla \cdot\|_{\Omega}$
* $ c_0^{\onehalf} \|\cdot\|_{\Omega} $
* $ \|h^{-\onehalf} [\cdot] \|_{\mcF_h}$
* $ \| |\bfb\cdot\bfn_F|^{\onehalf} [\cdot] \|_{\mcF_h}$
* $\| (\tfrac{h}{b_c})^{\onehalf} \bfb \cdot \nabla (\cdot) \|_{\Omega}$

Here, $u_k$ refers to the discrete solution $u_h$ on mesh $\mcT_k$.
Note, that we did not prove any error estimate for *scaled stream-line derivative norm*
$\| h^{\onehalf}/b_c \bfb \cdot \nabla (\cdot) \|_{\Omega}$, but one can prove
that the solution $u_h \in \PP^k_{\mrm{dc}}(\mcT_h)$ to the upwind-flux formulation also satisfies

$$
\| (\tfrac{h}{b_c})^{\onehalf} \bfb \cdot \nabla (u-u_h) \|_{\Omega} \lesssim h^{k+\onehalf} |u|_{k+1, \Omega}
$$


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
