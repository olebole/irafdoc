.. _mktemp:

mktemp: Make a temporary (unique) file name
===========================================

**Package: language**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  mktemp root
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>root</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='root' Line='root' -->
  <dd><br>
  The root (prefix) for the generated filename.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  <i>Mktemp</i> returns a unique filename string which may be used to create
  a temporary file name.  The string is the concatenation of three elements: the
  input argument, the process id, and a final character which changes on
  each call.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Create a unique filename with the root <span style="font-family: monospace;">"sav"</span> in the logical
  directory <span style="font-family: monospace;">"tmp"</span>.
  </p>
  <p>
  	savefile = mktemp (<span style="font-family: monospace;">"tmp$sav"</span>)
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  Since some time may elapse between the creation of the filename and the
  creation of a file with that name, there is no guarantee that the name
  will still be unique when it is actually used, however the algorithm used
  to generate the name makes filename collisions unlikely.
  </p>
  
  <!-- EndSection:    'BUGS' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS'  -->
  
