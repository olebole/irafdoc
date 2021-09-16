.. _which:

which — locate a task in the package list
=========================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  <PRE>
  which -- locate a task in the package list
  whereis -- locate all occurrences of a task in the package list
  </PRE>
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  <PRE>
  which [task] [...]
  whereis [task] [...]
  </PRE>
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>task</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='task' Line='task'>
  <DD>Name of task to be located.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <I>which</I> command returns the first occurrence of a task in the currently
  loaded package list.  The <I>whereis</I> command returns all occurrences of that
  task in the package list.  More than one task may be supplied on the command
  line, unique abbreviations for task names are permitted.
  <P>
  These commands are similar to the UNIX commands of the same name.  Users should
  note that <I>only</I> the currently loaded packages are searched.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  Find out which package contains the HEAD task.
  <PRE>
  <P>
  	cl&gt; which head
  	system
  </PRE>
  <P>
  2.  Find all currently loaded package which contain the SPLOT task.
  <PRE>
  <P>
  	cl&gt; whereis splot
  	echelle onedspec
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
