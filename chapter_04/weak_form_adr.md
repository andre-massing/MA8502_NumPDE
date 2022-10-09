## Well-posedness of the Advection-Reaction-Diffusion problem

For now we assume homogenous Dirichlet boundary conditions. After multiplying $\mcA u$ with a
test function $v$ and integrating by parts the term
$-(\epsilon \Delta u , v)_{\Omega}$, we arrive at the following weak formulation of the ADR problem:

Find $u \in H^1_0(\Omega) = V$ s.t. for all $v \in V$
```{math}
:label: eq-weak-form-adr
a(u,v) := \epsilon(\nabla u, \nabla v)_{\Omega} + (b\cdot\nabla u, v)_{\Omega} + (c u , v)_{\Omega}
= (f, v)_{\Omega} =: l(v).
```

Here, we used the notation $(\alpha, \beta)_{U} = \int_{U} \alpha \beta \dU$. Now we want to apply
the {prf:ref}`Lax-Milgram Theorem<thm-lax-milgram>` to prove the weak formulation {eq}`eq-weak-form-adr`
is well-posed. 
As $l(\cdot)$ is defined exactly as in the Poisson problem discussed in
{ref}`sec:weak-form-pdes)`, the boundedness of $l$ is clear.
But in contrast to the previous cases, the bilinear form $a(\cdot,
\cdot)$ is not symmetric, and therefore it it less trivial to show
that the bilinear form $a(\cdot, \cdot)$ indeed is both bounded and
coercive.