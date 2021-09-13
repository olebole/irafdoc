.. _pseudocolor:

pseudocolor — Select pseudocolor enhancement
============================================

**Package: iis**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  pseudocolor -- select pseudocolor enhancement
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  pseudocolor
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>enhancement</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='enhancement' Line='enhancement'>
  <DD>Type of pseudocolor enhancement.  The types are:
  <DL>
  <DT><B>"<TT>random</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"random"'>
  <DD>A randomly chosen color is assigned to each display level.
  </DD>
  </DL>
  <DL>
  <DT><B>"<TT>linear</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"linear"'>
  <DD>The display levels are mapped into a spectrum.
  </DD>
  </DL>
  <DL>
  <DT><B>"<TT>8color</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"8color"'>
  <DD>Eight colors are chosen at random over the range of the display levels.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>window = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='window' Line='window = yes'>
  <DD>Window the lookup table for the frame after enabling the pseudocolor?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The display levels from the lookup table are mapped into various saturated
  colors to enhance an image.  There is a choice of three color mappings.
  After the pseudocolor enhancement is enabled on the display monitor the
  user may, optionally, adjust the frame lookup table.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <PRE>
  	cl&gt; pseudocolor random
  	cl&gt; pseudocolor 8color
  	cl&gt; pseudocolor linear
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  cv
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
