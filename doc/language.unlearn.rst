.. _unlearn:

unlearn — Restore the default parameters for a task or package
==============================================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  unlearn -- restore initial defaults for parameters
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  unlearn name [name ...]
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>name</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='name' Line='name'>
  <DD>An IRAF task or package name.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Normally when a task terminates the values of the query mode task parameters
  used are stored in the parameter file on disk, appearing as the new defaults
  the next time the task is run.  The <I>unlearn</I> command instructs the CL
  to forget any task parameters it might have learned and to use the initial
  default values the next time the task is run.  If a tasks parameters have
  been cached, then they are removed from the parameter cache.
  <P>
  If a package name is specified all the tasks in the package are unlearned.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Unlearn the parameters for the delete and plot.graph tasks.
  <P>
  	cl&gt; unlearn delete plot.graph
  <P>
  2. Unlearn the parameters for all tasks in the <I>dataio</I> package.
  <P>
  	cl&gt; unlearn dataio
  <P>
  3. To unlearn the parameters for all tasks in the system, log out of the
  CL and run <I>mkiraf</I>, or enter the following:
  <P>
  <PRE>
  	cl&gt; chdir uparm
  	cl&gt; delete *.par
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  It is possible for the parameter set for a task to become corrupted,
  e.g., if the CL is interrupted while it is updating the parameter file on
  disk, causing a truncated file to be written.  If this should occur one
  will get error messages complaining about illegal arguments or parameters
  not found when the task is run.  The fix is to "<TT>unlearn</TT>" the parameters
  for the task.
  <P>
  When the CL fetches the parameters for a task, it checks to see if the
  system defaults have been updated more recently than the user's copy of
  the parameter set, and uses the system copy if it is more recent, after
  printing a message to warn the user.  This is done by comparing the file
  dates for the system and user parameter sets.  On VMS, it is easy for the
  modify date of the system copy of the parameter set to become updated
  even though the file data has not been modified, causing an annoying warning
  message to be printed when the task is later run.  Should this occur,
  the best solution is to unlearn all affected parameter sets.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  cache, update, lparam, eparam
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
