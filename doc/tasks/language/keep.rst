.. _keep:

keep: Make recent set, task, etc. declarations permanent
========================================================

**Package: language**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  keep
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  Normally when a script task terminates any tasks, packages, environment
  variables, etc. defined during the execution of that task are discarded
  (in other words, the memory used by the task is freed).
  The <i>keep</i> command instructs the CL to retain the definitions after
  script termination.  Only one level of <span style="font-family: monospace;">"keep"</span> is achieved, e.g.,
  if a script with a keep is called from a higher level script, then when
  the higher level script terminates the task definitions will still be lost
  (unless this higher level script also uses <i>keep</i>).
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Example</h3>
  <!-- BeginSection: 'EXAMPLE' -->
  <p>
  1. The most common use for <i>keep</i> is to retain a set of definitions
  in a script task.
  </p>
  <pre>
  	set	pkdir = "home$hebrew/"
  	task	aleph, beth, kaph = hebrew.cl
  
  	keep
  </pre>
  <!-- EndSection:   'EXAMPLE' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  task, package
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'EXAMPLE' 'SEE ALSO'  -->
  
