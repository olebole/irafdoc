.. _selftest:

selftest — Self test program to check DTOI transformation
=========================================================

**Package: dtoi**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  selftest -- test routine to verify <I>dtoi</I> transformation
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  selftest nbits
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>nbits = 12</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nbits' Line='nbits = 12'>
  <DD>Dymanic range of data to test.
  </DD>
  </DL>
  <DL>
  <DT><B>device = "<TT>stdgraph</TT>" </B></DT>
  <! Sec='PARAMETERS' Level=0 Label='device' Line='device = "stdgraph" '>
  <DD>Plotting device for graphical output.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>A table of density, intensity values is printed if <B>verbose</B> = yes.
  </DD>
  </DL>
  <DL>
  <DT><B>ceiling = 30000.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ceiling' Line='ceiling = 30000.'>
  <DD>Maximum intensity to output.
  </DD>
  </DL>
  <DL>
  <DT><B>max_raw = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='max_raw' Line='max_raw = 0'>
  <DD>The maximum raw data value.  Needed only if <I>nbits</I> equals something
  other than 12, 15 or 0.
  </DD>
  </DL>
  <DL>
  <DT><B>scale = 0.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='scale' Line='scale = 0.0'>
  <DD>The raw data value to density scale value.  Needed only if <I>nbits</I>
  equals something other than 12, 15, or 0.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Task <I>selftest</I> is a test program for the <I>dtoi</I> package.  Its 
  output can be examined to see if numerical errors are introduced during
  the density to intensity transformation.  It also evaluates truncation
  errors produced when an output image with integer pixels is written.  
  <P>
  Many different PDS setups can be investigated with task <B>selftest</B>.
  Setting parameter <I>nbits</I> = 12
  indicates PDS format data, with data range 0 to 3071.  Setting <I>nbits</I> = 15 
  indicates FITS format data, with data range 0 to 24575.  The special value of
  <I>nbits</I> = 0 means a small test data range from 1 to 144 is investigated.
  If any other value of <I>nbits</I> is entered, the user is queried for the
  max raw data values and the raw data to density scaling factor.
  <P>
  An intensity vector is generated from a density vector in two different ways.  
  The first method uses the density vector and known coefficients to compute
  the intensity.  The second method uses the curfit package to generate a
  look up table of intensities as done in task <B>HDTOI</B>.  The residual
  of the two intensity vectors is plotted.  Ideally, the difference between
  the 'known' intensities and 'calculated' intensities is zero.
  <P>
  The second plot output by <B>selftest</B> shows intensity as a function
  of density.  Two lines are overplotted; integer intensity versus density
  and real intensity versus density.  Because truncation errors are most
  pronounced at low density values, the plot covers only the lowest 5%
  of the density range.  The user should investigate the plot with the
  cursor zoom and expand capabilities to determine if truncation errors
  are significant.
  <P>
  In verbose mode, <B>selftest</B> produced a three column table of raw
  data value, density and calculated intensity. 
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  <PRE>
  Run task selftest for 12 bit data with plots appearing on the terminal.
  <P>
  	cl&gt; selftest
  <P>
  </PRE>
  Run selftest in verbose mode, spooling the output to file 'ditable'.  This
  file is then run through the 'fields' task to extract the density and intensity
  columns which are piped to plot.  The results in a plot of the look up table.
  <PRE>
  <P>
  	cl&gt; selftest ver+ &gt; ditable
  	cl&gt; fields ditable 2,3 | graph xlab=Density ylab=Intensity
  </PRE>
  </UL>
  <! EndSection:    'EXAMPLES'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES'  >
  
