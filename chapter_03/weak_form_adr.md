(sec-weak-formulation-adr)=
## Weak formulation and well-posedness of the advection-reaction-diffusion problem
<!-- Refer to the {prf:ref}`def-reduced-problem-adr` for the ADR problem. -->

For now we assume homogenous Dirichlet boundary conditions. After multiplying 
{eq}`eq-adr-problem` with a
test function $v$ and integrating by parts the term
$-(\epsilon \Delta u , v)_{\Omega}$, we arrive at the following weak formulation of the ADR problem:

Find $u \in H^1_0(\Omega) = V$ s.t. for all $v \in V$
```{math}
:label: eq-weak-form-adr
a(u,v) := \epsilon(\nabla u, \nabla v)_{\Omega} + (\bfb\cdot\nabla u, v)_{\Omega} + (c u , v)_{\Omega}
= (f, v)_{\Omega} =: l(v).
```

Here, we used the notation $(\alpha, \beta)_{U} = \int_{U} \alpha \beta \dU$. Now we want to apply
the {prf:ref}`Lax-Milgram Theorem<thm-lax-milgram>` to prove the weak formulation {eq}`eq-weak-form-adr`
is well-posed. 
As $l(\cdot)$ is defined exactly as in the Poisson problem discussed in
{ref}`sec:weak-form-pdes`, the boundedness of $l$ is clear.
But in contrast to the previous cases, the bilinear form 
$a(\cdot, \cdot)$ is not symmetric, and therefore it it less trivial to show
that the bilinear form $a(\cdot, \cdot)$ indeed is both coercive and bounded.

(ssec:coercivity-adr)=
### Coercivity of the bilinear form 

First, we want to show that there exists a constant $C_a > 0$ such that
$$
a(u, u) \geqslant \alpha \|u\|_{V}^2 \quad \foralls u \in V
$$
for a suitably chosen norm $\| \cdot \|_{V}$. Since we $V = H^1_0(\Omega)$, we pick
$\| \cdot \|_V = \| \nabla (\cdot) \|_{\Omega }$, which is equivalent to the $H^1$-norm,
thanks to the {prf:ref}`Poincare inequality<thm:poincare>`.
Now, we set $u=v$ in {eq}`eq-weak-form-adr` and obtain
$$
a(u,u) = \epsilon \|\nabla u\|_{\Omega}^2 + (\bfb\cdot\nabla u, u)_{\Omega} + (c u , u)_{\Omega}.
$$(eq-coerc-adr-form-step1)
Now the troublesome term is the nonsymmetric part
$
(b\cdot\nabla u, u)_{\Omega}
$  and to handle it, we first observe that
$$
\nabla\cdot (\bfb uv) = \bfb\cdot\nabla u v + \bfb\cdot\nabla v u + \nabla\cdot \bfb u v.
$$
and then use the famous the Gauß/Divergence theorem to see that
:::{math}
(\bfb\cdot \bfn u, v)_{\partial \Omega} = 
\int_{\Omega} \nabla\cdot (\bfb uv) dx
= (\bfb\cdot\nabla u, v)_{\Omega} 
+ (\bfb\cdot\nabla v, u)_{\Omega}
+ (\nabla\cdot\bfb v, u)_{\Omega}.
:::
So the term
$
(\bfb\cdot\nabla u, v)_{\Omega}
$
can be rewritten as
:::{math}
(\bfb\cdot\nabla u, v)_{\Omega} 
= 
- (u, \bfb\cdot\nabla v)_{\Omega}
- (\nabla\cdot\bfb v, u)_{\Omega}
+ (\bfb\cdot \bfn u, v)_{\partial \Omega}.
:::
For $u,v\in H^1_0(\Omega)$, the boundary term vanishes. Moreover,
in the typical case  $\nabla \cdot \bfb = 0$ case, we observe that
$(\bfb\cdot\nabla u, v)_{\Omega}$, i.e.
:::{math}
(\bfb\cdot\nabla u, v)_{\Omega}
-(u, \bfb\cdot\nabla v)_{\Omega}
:::
and thus $(\bfb\cdot\nabla u, u)_{\Omega} = 0$!

In the more general case where $\nabla \cdot \bfb \neq 0$, we can cleverly 
rewrite $(\bfb\cdot\nabla u, v)_{\Omega}$ as
:::{math}
(\bfb\cdot\nabla u, v)_{\Omega}
&=
\dfrac{1}{2}(\bfb\cdot\nabla u, v)_{\Omega} +
\dfrac{1}{2}(\bfb\cdot\nabla u, v)_{\Omega} 
\\
&=
\dfrac{1}{2}(\bfb\cdot\nabla u, v)_{\Omega}
- \dfrac{1}{2}(u, \bfb\cdot\nabla v)_{\Omega}
- \dfrac{1}{2}(\nabla\cdot\bfb u, v)_{\Omega}
+ \dfrac{1}{2}\underbrace{(\bfb\cdot \bfn u, v)_{\partial \Omega}}_{= 0}.
:::
Combining this expression with $(c u, v)_{\Omega}$  yields
:::{math}
(\bfb\cdot\nabla u, u)_{\Omega} 
+ (c u, u)_{\Omega} 
= 
((c - \tfrac{1}{2}\nabla\cdot\bfb) u, u)_{\Omega},
:::
and after recalling our general assumption that
$c(x) - \tfrac{1}{2}\nabla\cdot\bfb(x) \geqslant c_0 > 0$ for all $x\in \Omega$, 
we finally conclude that for all $u\in V$
:::{math}
a(u,u) &=
\epsilon \|\nabla u\|_{\Omega}^2
+ 
((c - \tfrac{1}{2}\nabla\cdot\bfb) u, u)_{\Omega}
\\
&\geqslant 
\epsilon \|\nabla u\|_{\Omega}^2
+ c_0 \|u\|_{\Omega}^2
\geqslant 
\epsilon \|\nabla u\|_{\Omega}^2.
:::
If one prefers to work with the $H^1$-norm, we could have replaced the last inequality by
$\geqslant \min\{\epsilon, c_0\} \|u\|_{H^1(\Omega)}$ or simply used the Poincare inequality.

