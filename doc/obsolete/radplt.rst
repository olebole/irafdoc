.. _radplt:

radplt: Plot the radial profile of an object (noao.proto V2.9)
==============================================================

**Package: obsolete**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  radplt input x_init y_init
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input' -->
  <dd>the list of images which contain the star whose profile is to be plotted
  </dd>
  </dl>
  <dl>
  <dt><b>x_init</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='x_init' Line='x_init' -->
  <dd>the approximate column coordinate as a starting point for the centering
  </dd>
  </dl>
  <dl>
  <dt><b>y_init</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='y_init' Line='y_init' -->
  <dd>the approximate line (row) coordinate as a starting point for the centering
  </dd>
  </dl>
  <dl>
  <dt><b>cboxsize = 5</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='cboxsize' Line='cboxsize = 5' -->
  <dd>the size of the extraction box to be used during the centering process
  </dd>
  </dl>
  <dl>
  <dt><b>rboxsize = 21</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='rboxsize' Line='rboxsize = 21' -->
  <dd>the size of the extraction box to be used for the radial profile. The
  profile will extend to sqrt(2) * rboxsize / 2. This is the length
  of the diagonal from the box center to a corner, and corresponds to about
  14 pixels for the default value.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  Given the approximate coordinates of the center of a star, (x_init, y_init),
  RADPLT will compute a more accurate center using the algorithms described in
  the Kitt Peak publication <span style="font-family: monospace;">"Stellar Magnitudes from Digital Images"</span> under
  the Mountain Photometry Code section and then plot the intensity values
  in the profile extraction box as a function of distance from the center.
  This is effectively a radial profile.
  </p>
  <p>
  The values for both box sizes should be odd.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  The following example plots the profile of a star near (123, 234):
  <br>
  </p>
  <pre>
  cl&gt; radplt m92red 123 234
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  The routine will probably fail if the desired star is within 2 or 3 pixels
  of the image boundary.
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>Use instead</h3>
  <!-- BeginSection: 'USE INSTEAD' -->
  <p>
  plot.pradprof
  </p>
  <!-- EndSection:   'USE INSTEAD' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  imcntr
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'USE INSTEAD' 'SEE ALSO'  -->
  
