.. _show:

show: Show an environment variable
==================================

**Package: language**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  show -- show the current value of an IRAF environment variable
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  show [varname]
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>varname</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='varname' Line='varname' -->
  <dd>The name of the environment variable to be displayed.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The <i>show</i> command shows the current values of all defined environment
  variables if called with no arguments, or the value of a specific variable
  if an argument is given.  Unlike <i>set</i>, only current values are shown,
  not the entire history of the definitions of environment variables.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Show the current default printer device.
  	
  	cl&gt; show printer
  </p>
  <p>
  2. Show all <span style="font-family: monospace;">"std"</span> (standard i/o stream) related variables.
  </p>
  <p>
  	cl&gt; show | match std
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  set
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
