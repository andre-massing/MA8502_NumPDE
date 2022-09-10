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
: A vector space $V$ equipped with a [norm](https://en.wikipedia.org/wiki/Norm_(mathematics)) 

```{math}
\| \cdot \| : V \to \RR
``` 

Every norm induces a natural metric $d(x, y) := \|x-y\|$.

[Banach space](https://en.wikipedia.org/wiki/Banach_space)
: A normed vector space which is complete with respect to the induced metric.

[Inner product space](https://en.wikipedia.org/wiki/Inner_product_space)
: A real (or complex) vector space $V$ equipped with a [inner product](https://en.wikipedia.org/wiki/Inner_product_space#Basic_properties)
    
```{math}
(\cdot, \cdot) : V \times V \to \RR \quad (\text{or } \CC )
``` 

Every inner product induces a natural norm $\| \cdot \| := \sqrt{(\cdot, \cdot)}$, and thereby a metric.

<!-- [Bounded linear operator](https://en.wikipedia.org/wiki/Operator_(mathematics)#Bounded_operators)
: For linear operators, the concept of continuity and boudnde 

Continuous functionals 
dual spaces
Riesz representation theorem
-->
>
````{prf:theorem} Riesz representation theorem

Let $H$ be a Hilbert space with a inner product $(\cdot, \cdot)$. Then for
every continuous functional $l:H \to \RR$, there is a unique vector $u_l \in H$
such that
```{math}
l(v) = (u_l ,v) \quad \forall v \in H.
```
````

```{prf:proof}
For a proof, we refer to {cite}`Brezis2011`. 
                         {cite}`Brezis2011`

```

For a proof, we refer to {cite}`Brezis2011`. 
                         {cite}`Brezis2011`

See, for example, Proposition 3.1.2 of {cite}`lasota1994chaos` or Lemma 8.2.3 of {cite}`stachurski2009economic`.