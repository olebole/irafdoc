.. _rgb:

rgb — Select true color mode (red, green, and blue frames)
==========================================================

**Package: iis**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  rgb - select true color mode (red, green, and blue frames)
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  rgb red_frame green_frame blue_frame
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>red_frame</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='red_frame' Line='red_frame'>
  <DD>Frame to use for the red component.
  </DD>
  </DL>
  <DL>
  <DT><B>green_frame</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='green_frame' Line='green_frame'>
  <DD>Frame to use for the green component.
  </DD>
  </DL>
  <DL>
  <DT><B>blue_frame</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='blue_frame' Line='blue_frame'>
  <DD>Frame to use for the blue component.
  </DD>
  </DL>
  <DL>
  <DT><B>window = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='window' Line='window = no'>
  <DD>Window the rgb lookup tables?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Set the display monitor to display rgb colors by using three frames to
  drive the red, green, and blue guns of the color display monitor.
  Optionally, window the rgb lookup tables.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  	cl&gt; rgb 1 2 3
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  cv
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
