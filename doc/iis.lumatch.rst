.. _lumatch:

lumatch — Match the lookup tables of two frames
===============================================

**Package: iis**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  lumatch -- match lookup tables for two display frames
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  lumatch frame ref_frame
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>frame</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='frame' Line='frame'>
  <DD>Frame whose lookup table is to be adjusted.
  </DD>
  </DL>
  <DL>
  <DT><B>ref_frame</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ref_frame' Line='ref_frame'>
  <DD>Frame whose lookup table is to be matched.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The lookup tables mapping the display frame values to the grey levels
  on the display monitor are matched in one frame to a reference frame.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  To match the lookup tables in frame 3 to those in frame 1:
  <P>
  	cl&gt; lumatch 3 1
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  cv
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
