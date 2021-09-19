.. _lumatch:

lumatch: Match the lookup tables of two frames
==============================================

**Package: iis**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  lumatch -- match lookup tables for two display frames
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  lumatch frame ref_frame
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>frame</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='frame' Line='frame' -->
  <dd>Frame whose lookup table is to be adjusted.
  </dd>
  </dl>
  <dl>
  <dt><b>ref_frame</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='ref_frame' Line='ref_frame' -->
  <dd>Frame whose lookup table is to be matched.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The lookup tables mapping the display frame values to the grey levels
  on the display monitor are matched in one frame to a reference frame.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  To match the lookup tables in frame 3 to those in frame 1:
  </p>
  <p>
  	cl&gt; lumatch 3 1
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  cv
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
