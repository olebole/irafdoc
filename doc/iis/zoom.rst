.. _zoom:

zoom: Zoom in on the image (change magnification)
=================================================

**Package: iis**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  zoom
  </p>
  <dl>
  <dt><b>zoom_factor</b></dt>
  <!-- Sec='USAGE' Level=0 Label='zoom_factor' Line='zoom_factor' -->
  <dd>Zoom factor by the display is to be expanded.  The factors are powers
  of 2; 1 = no zoom, 2 = factor of 2, 3 = factor of 4, and 4 = factor of 8.
  </dd>
  </dl>
  <dl>
  <dt><b>window = no</b></dt>
  <!-- Sec='USAGE' Level=0 Label='window' Line='window = no' -->
  <dd>Window the enlarged image?
  </dd>
  </dl>
  <!-- EndSection:   'USAGE' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The display is zoomed by the specified factor.  A zoom factor of 1 is no
  magnification and higher factors correspond to factors of 2.  The zoom
  replicates pixels on the monitor and only a part of the display frame
  centered on the display cursor is visible.  The window option allows
  the user to adjust interactively with the cursor the part of the zoomed
  frame.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  To magnify the displayed frame by a factor of 2:
  </p>
  <p>
  	cl&gt; zoom 2
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  cv
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
