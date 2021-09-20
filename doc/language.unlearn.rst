.. _unlearn:

unlearn: Restore the default parameters for a task or package
=============================================================

**Package: language**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  unlearn -- restore initial defaults for parameters
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  unlearn name [name ...]
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>name</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='name' Line='name' -->
  <dd>An IRAF task or package name.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  Normally when a task terminates the values of the query mode task parameters
  used are stored in the parameter file on disk, appearing as the new defaults
  the next time the task is run.  The <i>unlearn</i> command instructs the CL
  to forget any task parameters it might have learned and to use the initial
  default values the next time the task is run.  If a tasks parameters have
  been cached, then they are removed from the parameter cache.
  </p>
  <p>
  If a package name is specified all the tasks in the package are unlearned.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Unlearn the parameters for the delete and plot.graph tasks.
  </p>
  <p>
  	cl&gt; unlearn delete plot.graph
  </p>
  <p>
  2. Unlearn the parameters for all tasks in the <i>dataio</i> package.
  </p>
  <p>
  	cl&gt; unlearn dataio
  </p>
  <p>
  3. To unlearn the parameters for all tasks in the system, log out of the
  CL and run <i>mkiraf</i>, or enter the following:
  </p>
  <pre>
  	cl&gt; chdir uparm
  	cl&gt; delete *.par
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  It is possible for the parameter set for a task to become corrupted,
  e.g., if the CL is interrupted while it is updating the parameter file on
  disk, causing a truncated file to be written.  If this should occur one
  will get error messages complaining about illegal arguments or parameters
  not found when the task is run.  The fix is to <span style="font-family: monospace;">"unlearn"</span> the parameters
  for the task.
  </p>
  <p>
  When the CL fetches the parameters for a task, it checks to see if the
  system defaults have been updated more recently than the user's copy of
  the parameter set, and uses the system copy if it is more recent, after
  printing a message to warn the user.  This is done by comparing the file
  dates for the system and user parameter sets.  On VMS, it is easy for the
  modify date of the system copy of the parameter set to become updated
  even though the file data has not been modified, causing an annoying warning
  message to be printed when the task is later run.  Should this occur,
  the best solution is to unlearn all affected parameter sets.
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  cache, update, lparam, eparam
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  -->
  
