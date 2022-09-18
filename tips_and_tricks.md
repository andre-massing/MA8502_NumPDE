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
 > ```bibliography
 > ```
 if you have citations, otherwise they won't be found.



# Things that need to be fixed/found out

* Set up building tasks for jupyter book builds (DONE)
* Set up snippets for myst/md files
* Snippets already provided do not work as expected, e.g tab does not work.
* Labels in math environment and references to them are really annoying/not working!
* `$$` do not work in LaTeX output 
* Find out how you can define new admonitions
* How can we add verbatim text?
* The :dropdown: role does not work in proofs
* The ```prf:assumption``` from sphinx-proof is not available in myst, gives error
  > WARNING: Unknown directive type "prf:assumption".
* If one has an Myst file in the book directory which uses directives from sphinx-proof
  but the file is **not included** in _toc.yaml, a very confusing error message appears
  > writing output... [ 37%] chapter_01_preliminaries/test_sphinx_proof                                                       
  > Exception occurred:
  >   File "/home/andre/.local/lib/python3.10/site-packages/sphinx_proof/nodes.py", line 38, in depart_enumerable_node
  >     idx = self.body.index(f"{typ} {number} ")
  > ValueError: 'axiom  ' is not in list
  > The full traceback has been saved in /tmp/sphinx-err-3km5lkzy.log, if you want to report the issue to the developers.
  > Please also report this if it was a user error, so that a better error message can be provided next time.
  > A bug report can be filed in the tracker at <https://github.com/sphinx-doc/sphinx/issues>. Thanks!
  > Traceback (most recent call last):
  >   File "/home/andre/.local/lib/python3.10/site-packages/jupyter_book/sphinx.py", line 171, in build_sphinx
  >     app.build(force_all, filenames)
  >   File "/usr/lib/python3/dist-packages/sphinx/application.py", line 338, in build
  >     self.builder.build_update()
  >   File "/usr/lib/python3/dist-packages/sphinx/builders/__init__.py", line 294, in build_update
  >     self.build(to_build,
  >   File "/usr/lib/python3/dist-packages/sphinx/builders/__init__.py", line 358, in build
  >     self.write(docnames, list(updated_docnames), method)
  >   File "/usr/lib/python3/dist-packages/sphinx/builders/__init__.py", line 532, in write
  >     self._write_serial(sorted(docnames))
  >   File "/usr/lib/python3/dist-packages/sphinx/builders/__init__.py", line 542, in _write_serial
  >     self.write_doc(docname, doctree)
  >   File "/usr/lib/python3/dist-packages/sphinx/builders/html/__init__.py", line 626, in write_doc
  >     self.docwriter.write(doctree, destination)
  >   File "/usr/lib/python3/dist-packages/docutils/writers/__init__.py", line 78, in write
  >     self.translate()
  >   File "/usr/lib/python3/dist-packages/sphinx/writers/html.py", line 71, in translate
  >     self.document.walkabout(visitor)
  >   File "/usr/lib/python3/dist-packages/docutils/nodes.py", line 227, in walkabout
  >     if child.walkabout(visitor):
  >   File "/usr/lib/python3/dist-packages/docutils/nodes.py", line 227, in walkabout
  >     if child.walkabout(visitor):
  >   File "/usr/lib/python3/dist-packages/docutils/nodes.py", line 240, in walkabout
  >     visitor.dispatch_departure(self)
  >   File "/usr/lib/python3/dist-packages/sphinx/util/docutils.py", line 494, in dispatch_departure
  >     method(node)
  >   File "/home/andre/.local/lib/python3.10/site-packages/sphinx_proof/nodes.py", line 38, in depart_enumerable_node
  >     idx = self.body.index(f"{typ} {number} ")
  > ValueError: 'axiom  ' is not in list
  > 
  > The above exception was the direct cause of the following exception:
  > 
  > Traceback (most recent call last):
  >   File "/home/andre/.local/bin/jb", line 8, in <module>
  >     sys.exit(main())
  >   File "/usr/lib/python3/dist-packages/click/core.py", line 1128, in __call__
  >     return self.main(*args, **kwargs)
  >   File "/usr/lib/python3/dist-packages/click/core.py", line 1053, in main
  >     rv = self.invoke(ctx)
  >   File "/usr/lib/python3/dist-packages/click/core.py", line 1659, in invoke
  >     return _process_result(sub_ctx.command.invoke(sub_ctx))
  >   File "/usr/lib/python3/dist-packages/click/core.py", line 1395, in invoke
  >     return ctx.invoke(self.callback, **ctx.params)
  >   File "/usr/lib/python3/dist-packages/click/core.py", line 754, in invoke
  >     return __callback(*args, **kwargs)
  >   File "/home/andre/.local/lib/python3.10/site-packages/jupyter_book/cli/main.py", line 323, in build
  >     builder_specific_actions(
  >   File "/home/andre/.local/lib/python3.10/site-packages/jupyter_book/cli/main.py", line 531, in builder_specific_actions
  >     raise RuntimeError(_message_box(msg, color="red", doprint=False)) from result
  > RuntimeError: 
  > ===============================================================================
  > 
  > There was an error in building your book. Look above for the cause.
  > 
  > ===============================================================================

