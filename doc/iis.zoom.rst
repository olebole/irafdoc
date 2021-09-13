.. _zoom:

zoom — Zoom in on the image (change magnification)
==================================================

**Package: iis**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  zoom - zoom in on the image (change magnification)
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  zoom
  <DL>
  <DT><B>zoom_factor</B></DT>
  <! Sec='USAGE' Level=0 Label='zoom_factor' Line='zoom_factor'>
  <DD>Zoom factor by the display is to be expanded.  The factors are powers
  of 2; 1 = no zoom, 2 = factor of 2, 3 = factor of 4, and 4 = factor of 8.
  </DD>
  </DL>
  <DL>
  <DT><B>window = no</B></DT>
  <! Sec='USAGE' Level=0 Label='window' Line='window = no'>
  <DD>Window the enlarged image?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The display is zoomed by the specified factor.  A zoom factor of 1 is no
  magnification and higher factors correspond to factors of 2.  The zoom
  replicates pixels on the monitor and only a part of the display frame
  centered on the display cursor is visible.  The window option allows
  the user to adjust interactively with the cursor the part of the zoomed
  frame.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  To magnify the displayed frame by a factor of 2:
  <P>
  	cl&gt; zoom 2
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  cv
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
