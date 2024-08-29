# Discontinuous Galerkin methods for elliptic problems 

## Derivation of the Symmetric Interior Penalty method


Any norm $\|\cdot\|_{\mcP_h}$ used in this work which
involves a collection of geometric entities $\mcP_h$ should be
understood as broken norm defined by
$\|\cdot\|_{\mcP_h}^2 = \sum_{P\in\mcP_h} \|\cdot\|_P^2$ whenever
$\|\cdot\|_P$ is well-defined, with a similar convention for scalar
products $(\cdot,\cdot)_{\mcP_h}$.  Any set operations
involving $\mcP_h$ are also understood as element-wise operations,
e.g., $ \mcP_h \cap U = \{ P \cap U \st P \in \mcP_h \} $ and $
\partial \mcP_h = \{ \partial P \st P \in \mcP_h \} $ allowing for
compact short-hand notation such as
$ (v,w)_{\mcP_h \cap U} = \sum_{P\in\mcP_h} (v,w)_{P \cap U} $ and
$ \|\cdot\|_{\mcP_h\cap U} = \sqrt{\sum_{P\in\mcP_h} \|\cdot\|_{P\cap U}^2}$.


The final symmetric interior penalty for the Poisson problem is:

````{prf:definition} Symmetric Interior Penalty Method
:label: def-sip-final
Find $u_h \in V_h$ such that $\foralls v_h \in V_h$
```{math}
:label: eq-sip-final
  a_h(u_h,v_h) = l_h(v_h)
```
where the discrete bilinear form $a_h(\cdot, \cdot)$ and linear form $l_h(\cdot)$ are
defined by
```{math}
:label: eq-sip-form
  a_h(v,w) &= (\nabla v, \nabla w)_{\mcT_h} 
             - (\partial_n v, w)_{\Gamma}
             - (v, \partial_n w)_{\Gamma}
             + \beta (h^{-1} v,w)_{\Gamma} 
  \\                    
           &\qquad 
             - (\avg{\partial_n v }, \jump{w})_{\mcF_h}
             - (\jump{v}, \avg{\partial_n w })_{\mcF_h}
             + \beta (h^{-1}\jump{v},\jump{w})_{\mcF_h},
  \\           
l_h(v) &= (f,v)_{\mcT_h} - (\partial_n v, g)_{\Gamma}  
  +\beta (h^{-1} g, v)_{\Gamma},
```
respectively.
````

The theoretical analysis of the SIP method will be split into several parts.

## Norms

```{math}
\| v \|^2_{a_h} &= \| \nabla v \|^2_{\mcT_h} + \|h^{-1/2} [v] \|^2_{\mcF_h}
\\
\| v \|^2_{a_h, \ast} &= \| v \|_{a_h}^2 + \| h^{\onehalf} \avg{\partial_n v}\|_{\mcF_h}^2
```

## Discrete coercivity and boundedness

* Introduce norms
* Discuss Lax-Milgram
* Inverse trace inequalities
* Discrete coercivity

## Abstract error estimate

## Projection operators
* Abstract Cea's Lemma
* $L^2$ projection 
* Scaled trace inequality and error estimates

## A priori error analysis
* Energy error estimates
* Adjoint consistency, Aubin-Nitsche trick and $L^1$ error estimates

## Advantages and disadvantages of dG methods
