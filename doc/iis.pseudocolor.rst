.. _pseudocolor:

pseudocolor: Select pseudocolor enhancement
===========================================

**Package: iis**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  pseudocolor -- select pseudocolor enhancement
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  pseudocolor
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>enhancement</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='enhancement' Line='enhancement' -->
  <dd>Type of pseudocolor enhancement.  The types are:
  <dl>
  <dt><b><tt>"random"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='' Line='"random"' -->
  <dd>A randomly chosen color is assigned to each display level.
  </dd>
  </dl>
  <dl>
  <dt><b><tt>"linear"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='' Line='"linear"' -->
  <dd>The display levels are mapped into a spectrum.
  </dd>
  </dl>
  <dl>
  <dt><b><tt>"8color"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='' Line='"8color"' -->
  <dd>Eight colors are chosen at random over the range of the display levels.
  </dd>
  </dl>
  </dd>
  </dl>
  <dl>
  <dt><b>window = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='window' Line='window = yes' -->
  <dd>Window the lookup table for the frame after enabling the pseudocolor?
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The display levels from the lookup table are mapped into various saturated
  colors to enhance an image.  There is a choice of three color mappings.
  After the pseudocolor enhancement is enabled on the display monitor the
  user may, optionally, adjust the frame lookup table.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <pre>
  	cl&gt; pseudocolor random
  	cl&gt; pseudocolor 8color
  	cl&gt; pseudocolor linear
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  cv
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
