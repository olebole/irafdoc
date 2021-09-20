.. _which:

which: locate a task in the package list
========================================

**Package: language**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <pre>
  which [task] [...]
  whereis [task] [...]
  </pre>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>task</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='task' Line='task' -->
  <dd>Name of task to be located.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The <i>which</i> command returns the first occurrence of a task in the currently
  loaded package list.  The <i>whereis</i> command returns all occurrences of that
  task in the package list.  More than one task may be supplied on the command
  line, unique abbreviations for task names are permitted.
  </p>
  <p>
  These commands are similar to the UNIX commands of the same name.  Users should
  note that <i>only</i> the currently loaded packages are searched.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1.  Find out which package contains the HEAD task.
  </p>
  <pre>
  
  	cl&gt; which head
  	system
  </pre>
  <p>
  2.  Find all currently loaded package which contain the SPLOT task.
  </p>
  <pre>
  
  	cl&gt; whereis splot
  	echelle onedspec
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
