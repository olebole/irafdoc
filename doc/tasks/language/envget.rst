.. _envget:

envget: Get the string value of an environment variable
=======================================================

**Package: language**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  envget varname
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>varname</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='varname' Line='varname' -->
  <dd>The environment variable whose value is to be returned.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  <i>Envget</i> returns the string value of the named environment variable.
  The user is prompted for the value if the variable has not yet been defined.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Construct a filename using the value of the environment variable
  <span style="font-family: monospace;">"editor"</span>, and page the file thus named.
  </p>
  <p>
  	cl&gt; page (<span style="font-family: monospace;">"dev$"</span> // envget (<span style="font-family: monospace;">"editor"</span>) // <span style="font-family: monospace;">".ed"</span>)
  </p>
  <p>
  2. Compute and print the center line on the terminal screen.
  </p>
  <p>
  	cl&gt; = ((int (envget (<span style="font-family: monospace;">"ttynlines"</span>)) + 1) / 2)
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  set, show
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
