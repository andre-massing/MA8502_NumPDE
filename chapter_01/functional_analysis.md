(sec:functioal-analysis)=
# Relevant concepts from functional analysis

Vector space
: A definition can be found on [wiki](https://en.wikipedia.org/wiki/Vector_space).

[Metric space](https://en.wikipedia.org/wiki/Metric_space)
: A metric space is a set $X$ which is equipped with a [distance function (or metric)](https://en.wikipedia.org/wiki/Metric_space#Definition)

```{math}
d(x,y): X \times X \to \RR.
```

[Complete metric space](https://en.wikipedia.org/wiki/Complete_metric_space)
: A metric space is called *complete* if every [Cauchy sequence](https://en.wikipedia.org/wiki/Cauchy_sequence#In_a_metric_space)
converges to some $x \in X$.

[Normed vector space](https://en.wikipedia.org/wiki/Metric_space)
: A vector space $(V, \|\cdot\|_V)$ consist of a vector space $V$ which is 
equipped with a [norm](https://en.wikipedia.org/wiki/Norm_(mathematics)) 

```{math}
\| \cdot \|_V : V \to \RR
``` 

Note that every norm induces a natural metric $d(x, y) := \|x-y\|_V$.
Typically we do not use the verbose notation $(V, \|\cdot\|_V)$, instead
we simply speak of a normed vector space $V$, and we omit the subscript $_V$
in the norm symbol when the norm is clear from
the context.

[Banach space](https://en.wikipedia.org/wiki/Banach_space)
: A normed vector space which is complete with respect to the induced metric.

[Inner product space](https://en.wikipedia.org/wiki/Inner_product_space)
: An inner product space $\bigl(V, (\cdot, \cdot)\bigr)_V$ is a real 
(or complex) vector space $V$ equipped with a [inner product](https://en.wikipedia.org/wiki/Inner_product_space#Basic_properties)
    
```{math}
(\cdot, \cdot)_V : V \times V \to \RR \quad (\text{or } \CC )
``` 

Every inner product induces a natural norm $\| \cdot \| := \sqrt{(\cdot, \cdot)}$, and thereby a metric. 
Again, we typically do not use the verbose notation $\bigl(V, (\cdot,
\cdot)\bigr)$, instead we simply speak of a inner product space $V$,
and we often omit the subscript $_V$
in $(\cdot, \cdot)_V$ symbol when the inner product is clear from
the context.

Inner products satisfy the *Cauchy-Schwarz inequality:*
```{math}
(u,v)_V \leqslant \|u\|_V \|v\|_V.
```
<!-- and inequality only holds -->


[Bounded linear operator](https://en.wikipedia.org/wiki/Operator_(mathematics)#Bounded_operators)
: A linear operator $L: V \to W$ between two normed vector spaces 
$(V, \|\cdot\|_V)$ and $(W, \|\cdot\|_W)$
is call bounded if there is a constant $C \in \RR^+_0$ such that
```{math}
\| L v \|_W \leqslant C \|v\|_V.
```

The *operator norm* $\|L\|_{V\to W}$ of $T$ is then the smallest such constant given by 
```{math}
\|L\|
&= \inf \{C \in \RR^+_0 : \|L v \|_W \leqslant \|v\|_V \, \forall v \in V\} \\
& = \sup_{v \in V \setminus \{0\}} \dfrac{\|L v \|_W}{\|v\|_V} \\
& = \sup_{v \in V, \|v\|_V = 1} \|L v \|_W.
```
It can be shown that the the following statements are equivalent for **linear operators**:
* $L: V \to W$ is bounded
* $L: V \to W$ is continuous

<!-- See {cite}`Brezis2011` for a proof. -->

```{exercise} 
Before you look up the proof, try to prove the previous claim yourself.
```

A linear operator $l : V \to \RR \; (\text{or } \CC )$ is often called
a *linear functional* or a *linear form* on $V$.

Dual space
: The dual space $V^*$ for a normed vector space $(V, \|\cdot\|)$ consist
of all **continuous** linear functionals defined on $V$.

Note that for inner product spaces $V$, every $u \in V$ give rise to a 
continuous linear functional $l_u$ defined by
```{math}
l_u(v) := (v, u)_V \quad \forall v \in V.
```

For Hilbert space $H$, that is in essence all the continuous linear functionals
you can construct on $H$ thanks to the following theorem.

Riesz representation theorem 
````{prf:theorem} Riesz representation theorem

Let $H$ be a Hilbert space with a inner product $(\cdot, \cdot)$. Then for
every continuous functional $l:H \to \RR$, there is a unique vector $u_l \in H$
such that
```{math}
l(v) = (v, u_l) \quad \forall v \in H,
```
and we have that
```{math}
\| l_u \|_{V^*} = \| u \|_{V}.
```
````

```{prf:proof}
For a proof, we refer to Section 5.2 in {cite}`Brezis2011`. 
```

Later, when we have introduced the concept of weak formulation of partial differential equations, we will make heavily use of the  Lax-Milgram theorem.

````{prf:theorem} Lax-Milgram
:label: thm-lax-milgram
Given a Hilbert space $(V,\| \cdot\|)$, a bilinear form
$a(\cdot, \cdot): V \times V \to \RR$ (or $\CC$), and a linear form 
$l(\cdot): V \to \RR$ (or $\CC$). Then the problem: Find $u \in V$ such 
that 
```{math}
:label: eq:lax-milgram-problem
a(u, v) = l(v) \quad \forall v\in V
```
possesses solution a solution $u \in V$ if the following assumptions are satisfied.
1. The linear form $l$ is bounded, i.e. there exists a constant $C_l \geqslant 0$ such that
    ```{math}
    :label: eq:lax-milgram-bounded-l
    | l(v) | \leqslant C_l \| v\| \quad \forall v \in V.
    ```
2. The bilinear form $a$ is bounded, i.e. there exists a constant $C_a \geqslant 0$ such that
    ```{math}
    :label: eq:lax-milgram-bounded-a
    | a(v, w) | \leqslant C_a \| v\| \|w\| \quad \forall v,w \in V.
    ```
3. The bilinear form $a$ is coercive, i.e. there is a constant $\alpha > 0$ such that
    ```{math}
    :label: eq:lax-milgram-coerc
    a(v, v)  \geqslant \alpha \|v\|^2 \quad \forall v \in V.
    ```
Moreover, the solution $u$ satisfies the stability (or a priori) estimate
```{math}
:label: eq:lax-milgram-stab
\|u\| \leqslant \dfrac{C_l}{\alpha}
```
and is (therefore!) uniquely defined.
````

````{prf:proof}
For a complete proof in particular the existence of a solution $u$, we
refer to the nice presentation in {cite}`Evans2010`.
Here, we only show to derive {eq}`eq:lax-milgram-stab`
and uniqueness of $u$.

Assume $u$ solves {eq}`eq:lax-milgram-problem`. Then set $v=u$ and
successively employ the coercivity of $a$ and boundedness of $l$ to see that
```{math}
\alpha \|u\|^2 \leqslant a(u, u) = l(u) \leqslant C_l \|u\|.
```
Dividing the previous chain of inequalities by $\alpha$ and $\|u\|$ if $\| u \| \neq 0$
yields {eq}`eq:lax-milgram-stab`. For $\|u\| = 0$ the stability estimate is trivially satisfied.

If $u_1$ and $u_2$
both satisfy problem {eq}`eq:lax-milgram-problem`, then
thanks to linearity of $a$ in the first slot,
the difference $u_1-u_2$ satisfies problem~{eq}`eq:lax-milgram-problem` but with $f =  0$
instead. In that case $C_l = 0$ and thus $0\leqslant\|u_1 - u_2 \| \leqslant \tfrac{0}{\alpha} = 0$, and thus $u_1 = u_2$.
````

```{prf:remark}
The {prf:ref}`Lax-Milgram theorem<thm-lax-milgram>` ensures that 
problem {eq}`eq:lax-milgram-problem`
is well-posed, i.e.,
* **Existence** of a solution
* **Uniquessness** of the solution
* **Continuous dependency on the data** (or **Stability**) of the solution.
  In the particular case of {prf:ref}`Lax-Milgram theorem<thm-lax-milgram>`, stability is guaranteed through {eq}`eq:lax-milgram-stab` which implies that
  "small changes" in $a$ and $l$ will only lead to small changes in the solution $u$.
```