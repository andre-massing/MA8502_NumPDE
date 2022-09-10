# Tips and tricks I stumbled across

* Convert pdf files (not only images) to png via
```{code}
> pdftoppm {input.pdf} {output.file} -png
```
or
```{code}
> pdftoppm -png myfile.pdf > myfile.png
```

* You cannot use e.g. align directly within another directive, e.g in ```{prf:proof}. 
  You need to use ```{math} directive which usually wraps math formula into an combined equation/split environment.
  To avoid this e.g. if you still want to use align instead, you need to set the :nowrap: True option.
* Remember to include 
 > ```bibliograpgy
 > ```
 if you have citations, otherwise they won't be found.


# Things that need to be fixed

* Set up building tasks for jupyter book builds (DONE)
* Set up snippets for myst/md files
* Labels in math environment and references to them are really annoying/not working!
* `$$` do not work in LaTeX output 
* Find out how you can define new admonitions