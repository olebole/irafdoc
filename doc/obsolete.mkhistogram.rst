.. _mkhistogram:

mkhistogram — List or plot the histogram of a data stream (noao.proto V2.9)
===========================================================================

**Package: obsolete**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  mkhistogram -- print or plot the histogram of a data stream
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  mkhistogram file
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>file</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='file' Line='file'>
  <DD>The name of the text file containing the data (may be STDIN).
  </DD>
  </DL>
  <DL>
  <DT><B>nbins</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nbins' Line='nbins'>
  <DD>The number of bins in the histogram.
  </DD>
  </DL>
  <DL>
  <DT><B>z1 = INDEF, z2 = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='z1' Line='z1 = INDEF, z2 = INDEF'>
  <DD>The minimum and maximum histogram intensity. Z1 and z2 default to the data
  minimum and maximum.
  </DD>
  </DL>
  <DL>
  <DT><B>listout = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='listout' Line='listout = yes'>
  <DD>List instead of plot the histogram.
  </DD>
  </DL>
  <DL>
  <DT><B>device = "<TT>stdgraph</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='device' Line='device = "stdgraph"'>
  <DD>The output graphics device.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  MKHISTOGRAM calculates the histogram of the data in the text
  file <I>file</I> using
  the parameters <I>nbins</I>, <I>z1</I> and <I>z2</I>. If the z1 or z2 are
  undefined the image min or max is used. If <I>listout</I> = no, the
  histogram is plotted on the graphics device specified by <I>device</I>.
  Otherwise the histogram is listed on the standard output.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Output the histogram of data to a file.
  <P>
  <PRE>
      cl&gt; mkhisto magsdata nbins=100 &gt; magsdata.hst
  </PRE>
  <P>
  2. Plot the histogram of data between the 12.0  and 26.0 with a binsize
     if 0.5 on standard graph. Notice that the extra bin will contain
     points for which z2 is exactly 26.
  <P>
  <PRE>
      cl&gt; mkhist magsdat nbins=29 z1=12.0 z2=26.0 li-
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>Use instead</H3>
  <! BeginSection: 'USE INSTEAD'>
  <UL>
  plot.phistogram
  </UL>
  <! EndSection:   'USE INSTEAD'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  images.imhistogram, fields
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'USE INSTEAD' 'SEE ALSO'  >
  
