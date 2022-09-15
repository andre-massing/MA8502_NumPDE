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
````
## Sobolev spaces

A short summary of Sobolev spaces


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