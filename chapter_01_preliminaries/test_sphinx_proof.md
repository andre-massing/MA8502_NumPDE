# Illustrating sphinx-proof

<!-- 
```{prf:assumption}
:label: my-assumption

This is a dummy assumption directive.
``` 

```{prf:axiom} Completeness of $\mathbb{R}$
:label: my-axiom

Every Cauchy sequence on the real line is convergent.
```

````{prf:criterion} Weyl's criterion
:label: weyls-criterion

Weyl's criterion states that the sequence $a_n$ is equidistributed modulo $1$ if
and only if for all non-zero integers $m$,

```{math}
\lim_{n \rightarrow \infty} \frac{1}{n} \sum_{j=1}^{n} \exp^{2 \pi i m a_j} = 0
```
````

````{prf:remark}
:label: my-remark

More generally there is a class of density functions
that possesses this feature, i.e.

```{math}
\exists g: \mathbb{R}_+ \mapsto \mathbb{R}_+ \ \ \text{ and } \ \ c \geq 0,
\ \ \text{s.t.  the density } \ \ f \ \ \text{of} \ \ Z  \ \
\text{ has the form } \quad f(z) = c g(z\cdot z)
```

This property is called **spherical symmetry** (see p 81. in Leamer
(1978))
````

```{prf:conjecture} Fake $\gamma$ conjecture
:label: my-conjecture

This is a dummy conjecture to illustrate that one can use math in titles.
```

```{prf:corollary}
:label: my-corollary

If $A$ is a convergent matrix, then there exists a matrix norm such
that $\vert \vert A \vert \vert < 1$.
```

```{prf:algorithm} Ford–Fulkerson
:label: my-algorithm

**Inputs** Given a Network $G=(V,E)$ with flow capacity $c$, a source node $s$, and a sink node $t$

**Output** Compute a flow $f$ from $s$ to $t$ of maximum value

1. $f(u, v) \leftarrow 0$ for all edges $(u,v)$
2. While there is a path $p$ from $s$ to $t$ in $G_{f}$ such that $c_{f}(u,v)>0$
	for all edges $(u,v) \in p$:

	1. Find $c_{f}(p)= \min \{c_{f}(u,v):(u,v)\in p\}$
	2. For each edge $(u,v) \in p$

		1. $f(u,v) \leftarrow f(u,v) + c_{f}(p)$ *(Send flow along the path)*
		2. $f(u,v) \leftarrow f(u,v) - c_{f}(p)$ *(The flow might be "returned" later)*
```

````{prf:example}
:label: my-example

Next, we shut down randomness in demand and assume that the demand shock
$\nu_t$ follows a deterministic path:


```{math}
\nu_t = \alpha + \rho \nu_{t-1}
```

Again, we’ll compute and display outcomes in some figures

```python
ex2 = SmoothingExample(C2=[[0], [0]])

x0 = [0, 1, 0]
ex2.simulate(x0)
```
````

```{prf:property}
:label: my-property

This is a dummy property to illustrate the directive.
```

```{prf:observation}
:label: my-observation

This is a dummy observation directive.
```

```{prf:proposition}
:label: my-proposition

This is a dummy proposition directive.
```
-->