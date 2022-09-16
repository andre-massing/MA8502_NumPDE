(sec:function-spaces)
# A brief review on function spaces

In this chapter we collect some results on various function space we will
use throughout the book. One essential property of many function
space we will consider is that they are *complete*, i.e. they are either 
Banach or Hilbert space, see Section {ref}`sec:functioal-analysis`.


```{note}
This section barely scratches at the surface of the topic, we will
only summarize (and not even prove) the most essential results we need
later one in this course.

Also, this chapter will be a work in progress during the entire course,
as we will add relevant results here whenever we need them elsewhere.
```

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

````{prf:lemma} Determining uniqueness through testing
:label: lem:uniqueness-by-testing
Let $u_1, u_2 \in L^1_{\mrm{loc}}(\Omega)$ and assume that
```{math}
\int_{\Omega} (u_1 - u_2) \phi \dx = 0  \quad \forall \phi \in C^{\infty}_c(\Omega).
```
Then $u_1 = u_2$ almost every in $\Omega$; that is, up to set of measure $0$.
````

```{prf:remark}
In this setting, $\phi$ is typically called a *test function*. 
When determining 
whether two functions are equal,
the previous lemma roughly states that you can do this
by comparing their "actions" on suitable test functions $\phi$
instead of comparing their values at (almost) every point.

Here, the "action" is simply the resulting number computed from multiplying the functions in question with the test function $\phi$
and integrating over $\Omega$. 
```

## Sobolev spaces

### Weak derivatives 

Let start with a motivating example. Let $u \in C^k(\Omega)$ and $\phi \in C^{\infty}_c(\Omega)$.
Using Green's theorem and taking into account that $\phi = 0$ on a open neighborhood of the boundary of $\Omega$, 
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

Note that the integral expression on the right-hand side of {eq}`eq-weak-deriv-alpha` makes perfectly
sense even for $u\in L^1_{\mrm{loc}}$ and not only $u\in C^k(\Omega)$.
This leads to a possibility to generalize or weakened the classical definition of derivatives. 

````{prf:definition} Weak derivative
Let $\alpha \in \NN^n$ be a multiindex and $u, u_{\alpha} \in L^1_{\mrm{loc}}(\Omega)$.
We say that $u_{\alpha}$ is *$\alpha$-th weak derivative* of $u$ if
```{math}
\int_{\Omega}  u_{\alpha} \phi \dx = 
(-1)^{|\alpha|} \int_{\Omega} u \partial^{\alpha} \phi \dx
```
holds for all $\phi \in C^{\infty}_c(\Omega)$.
````

```{prf:lemma} Uniqueness of weak derivatives
If $u \in L^1_{\mrm{loc}}(\Omega)$ possesses an $\alpha$-th weak derivative, it is uniquely defined
in $L^1_{\mrm{loc}}(\Omega)$.
```

````{prf:proof}
For
two weak derivatives $u_{\alpha}$ and $\tilde{u}_{\alpha}$ we have that
```{math}
:nowrap: True
\begin{align}
\int_{\Omega} u_{\alpha} \phi &= (-1)^{|\alpha|} \int_{\Omega} u \partial^{\alpha} \phi dx
\\
\int_{\Omega} \tilde{u}_{\alpha} \phi &= (-1)^{|\alpha|} \int_{\Omega} u \partial^{\alpha} \phi dx
\end{align}
```
and by substracting the second from the first inequality, we obtain that 
```{math}
\int_{\Omega}
(u_{\alpha} - \tilde{u}_{\alpha} ) \phi dx =  0 \quad \forall \phi \in C_c^{\infty}(\Omega),
```
and thus $u_{\alpha} = \tilde{u}_{\alpha}$ almost everywhere
by {prf:ref}`lem:uniqueness-by-testing`.
````

````{prf:exercise} Relation between the modulus function and the Heaviside function
Let $\Omega = (-1,1)$ and set
```{math}
u(x) &= x \\
H(x) &= \begin{cases} -1 &\quad x \in (-1,0) \\ 
                      1  &\quad x \in [0, 1)
        \end{cases}
```
By simply using the definition of the weak derivative, show that
$H(x)$ is the weak derivative of $u$.
````

````{prf:definition} Sobolev spaces
* $W^{k,p}(\Omega) := 
  \{
  u \in L^p(\Omega) |\, \partial^{\alpha}u \text{ exists and belongs to } L^p(\Omega) 
  \, \forall \alpha \text{ with } |\alpha| \leqslant k
  \}
  $
* For $p=2$, we usually write
  ```{math}
  H^k(\Omega) := W^{k,2}(\Omega)
  ```
* For $u \in W^{k,p}(\Omega)$, we set 
  ```{math}
  \| u \|_{W^{k,p}({\Omega})} := \|u\|_{k,p,\Omega} 
  :=
  \begin{cases}
  \Bigl( 
    \sum_{|\alpha| \leqslant k} \| \partial^{\alpha} u \|_{L^p(\Omega)}^p
  \Bigr)^{1/p} 
  & 1\leqslant p <  \infty
  \\
    \sum_{|\alpha| \leqslant k} \| \partial^{\alpha} u \|_{L^{\infty}(\Omega)}
  & p =  \infty
  \end{cases}
  ```
````





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