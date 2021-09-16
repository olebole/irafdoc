.. _bye:

bye — Exit a task or package
============================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  bye -- terminate task execution
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  bye
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <I>bye</I> command terminates the task from which it is executed.
  This is exactly equivalent to the CL reading end of file (EOF) when
  executing a task.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. The most common usage of <I>bye</I> occurs when it is typed by the user to
  exit a package; in this case, <I>bye</I> terminates the package script task.
  <P>
  <PRE>
  	cl&gt; plot
  	pl&gt; bye
  	cl&gt;
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  clbye, return
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
