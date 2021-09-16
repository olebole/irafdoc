.. _keep:

keep — Make recent set, task, etc. declarations permanent
=========================================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  keep -- keep memory after task termination
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  keep
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Normally when a script task terminates any tasks, packages, environment
  variables, etc. defined during the execution of that task are discarded
  (in other words, the memory used by the task is freed).
  The <I>keep</I> command instructs the CL to retain the definitions after
  script termination.  Only one level of "<TT>keep</TT>" is achieved, e.g.,
  if a script with a keep is called from a higher level script, then when
  the higher level script terminates the task definitions will still be lost
  (unless this higher level script also uses <I>keep</I>).
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Example</H3>
  <! BeginSection: 'EXAMPLE'>
  <UL>
  1. The most common use for <I>keep</I> is to retain a set of definitions
  in a script task.
  <P>
  <PRE>
  	set	pkdir = "home$hebrew/"
  	task	aleph, beth, kaph = hebrew.cl
  <P>
  	keep
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLE'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  task, package
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'EXAMPLE' 'SEE ALSO'  >
  
