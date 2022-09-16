(sec:function-spaces)
# A brief review on function spaces

In this chapter we collect some results on various function space we will
use throughout the book. One essential property of many function
space we will consider is that they are *complete*, i.e. they are either 
Banach or Hilbert space, see Section {ref}`sec:functioal-analysis`.

## Measure and integration theory, Lebesque spaces
Lebesque integration theory provides a powerful generalization
of the Riemann integral which makes sure that the set of so-called
Lebesque-integrable functions turns into a Banach space when
endowed with a suitable norm. Nowdays, in most standard text books,
Lebesque integration theory is presented as part of the
curriculum on *Measure and Integration theory*, see Chapter 9-10 in 
{cite}`Browder2012` for a quick introduction. 
To this end, 

````{prf:definition} Lebesque spaces
Let $\Omega \subset \RR^n$ be a open domain. Then
the Lebesque spaces $L^p(\Omega)$ are defined by
```{math}
:label: eq-lebesque-spaces
L^p(\Omega) = \{ f : \Omega \to \RR \text{ is measurable and } 
\|f\|_{L^p(\Omega)} 
:= \|f\|_{p,\Omega} 
:=  
\Bigl(
    \int_{\Omega} |f(x)|^p \dx
\Bigr)^{1/p} < \infty
 \}.
```
A function $f \in L^p(\Omega)$ is often called $L^p$-integrable. 

We also introduce the space of *locally* $L^p$-integrable functions on $\Omega$; that is,
functions that are $L^p$ integrable on every compact subset $K \Subset \Omega$,
```{math}
:label: eq-loc-lebesque-spaces
L^p_{\mrm{loc}}(\Omega) = \{ f: \Omega \to \RR | f \in L^p(K)  \; \forall K \Subset \Omega \}.
```
````


## Sobolev spaces

### Weak derivatives 

Let start with a motivating example. Let $u \in C^k(\Omega)$ and $\phi \in C^{\infty}_c(\Omega)$.
Using Green's theorem and taken into account that $\phi = 0$ on a open neighborhood of the boundary of $\Omega$, 
we see that
```{math}
:label: eq-weak-deriv-first
\int_{\Omega} \partial_{x_i} u \phi \dx = 
- \int_{\Omega} u \partial_{x_i} \phi \dx,
```
and iterating this formula, we observe that for any multiindex $\alpha
\in \NN^n$ with $\alpha \leqslant k$, it holds that
```{math}
:label: eq-weak-deriv-alpha
\int_{\Omega} \partial^{\alpha} u \phi \dx = 
(-1)^{|\alpha|} \int_{\Omega} u \partial^{\alpha} \phi \dx.
```

In this setting, $\phi$ is typically called a *test function*.
Note that the right-hand side of {eq}`eq-weak-deriv-alpha`



<!-- ```{prf:theorem}
:class: dropdown

This is an example of how to hide the content of a directive.
```

```{toggle}
This is a toggled content block!
```

:::{admonition} Click the title to toggle
:class: dropdown

This title was made into a dropdown admonition by adding `:class: dropdown` to it.
::: -->