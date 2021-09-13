.. _radplt:

radplt — Plot the radial profile of an object (noao.proto V2.9)
===============================================================

**Package: obsolete**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  radplt -- plot a radial profile of a stellar image
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  radplt input x_init y_init
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>the list of images which contain the star whose profile is to be plotted
  </DD>
  </DL>
  <DL>
  <DT><B>x_init</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='x_init' Line='x_init'>
  <DD>the approximate column coordinate as a starting point for the centering
  </DD>
  </DL>
  <DL>
  <DT><B>y_init</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='y_init' Line='y_init'>
  <DD>the approximate line (row) coordinate as a starting point for the centering
  </DD>
  </DL>
  <DL>
  <DT><B>cboxsize = 5</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cboxsize' Line='cboxsize = 5'>
  <DD>the size of the extraction box to be used during the centering process
  </DD>
  </DL>
  <DL>
  <DT><B>rboxsize = 21</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rboxsize' Line='rboxsize = 21'>
  <DD>the size of the extraction box to be used for the radial profile. The
  profile will extend to sqrt(2) * rboxsize / 2. This is the length
  of the diagonal from the box center to a corner, and corresponds to about
  14 pixels for the default value.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Given the approximate coordinates of the center of a star, (x_init, y_init),
  RADPLT will compute a more accurate center using the algorithms described in
  the Kitt Peak publication "<TT>Stellar Magnitudes from Digital Images</TT>" under
  the Mountain Photometry Code section and then plot the intensity values
  in the profile extraction box as a function of distance from the center.
  This is effectively a radial profile.
  <P>
  The values for both box sizes should be odd.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  The following example plots the profile of a star near (123, 234):
  <BR>
  <PRE>
  cl&gt; radplt m92red 123 234
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  The routine will probably fail if the desired star is within 2 or 3 pixels
  of the image boundary.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>Use instead</H3>
  <! BeginSection: 'USE INSTEAD'>
  <UL>
  plot.pradprof
  </UL>
  <! EndSection:   'USE INSTEAD'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imcntr
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'USE INSTEAD' 'SEE ALSO'  >
  
