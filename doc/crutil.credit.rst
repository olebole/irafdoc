.. _credit:

credit: Interactively edit cosmic rays using an image display
=============================================================

**Package: crutil**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  credit -- interactively edit cosmic rays using an image display
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage	</h3>
  <!-- BeginSection: 'USAGE	' -->
  <pre>
  credit input output
  </pre>
  <!-- EndSection:   'USAGE	' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <p>
  See parameters for <b>imedit</b>.
  </p>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  This task is a version of <b>imedit</b>.  See the help for that task
  for a description of the parameters and algorithms.
  </p>
  <p>
  For the purpose of editing cosmic rays the most useful editing option
  is <span style="font-family: monospace;">'b'</span> to replace cosmic rays in a circular annulus using local sky
  values.  This can be done interactively or using a list of positions
  along with the <i>default</i> parameter value.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1.  To replace cosmic rays interactively.
  </p>
  <pre>
      cl&gt; credit obj012 crobj012 crmask012
  </pre>
  <p>
  2.  To use a two column list of positions and remove the cosmic rays using
  the <span style="font-family: monospace;">'b'</span> key algorithm.
  </p>
  <pre>
      cl&gt; credit obj012 crobj012 cursor=crlist.dat display-
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  imedit, epix
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
