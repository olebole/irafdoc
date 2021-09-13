mkhistogram — List or plot the histogram of a data stream (noao.proto V2.9)
===========================================================================

**Package: obsolete**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>mkhistogram (Feb88)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>obsolete</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>mkhistogram (Feb88)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>mkhistogram</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  mkhistogram -- print or plot the histogram of a data stream
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  mkhistogram file
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_file">file</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='file' Line='file'>
  <DD>The name of the text file containing the data (may be STDIN).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nbins">nbins</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nbins' Line='nbins'>
  <DD>The number of bins in the histogram.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_z1">z1 = INDEF, z2 = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='z1' Line='z1 = INDEF, z2 = INDEF'>
  <DD>The minimum and maximum histogram intensity. Z1 and z2 default to the data
  minimum and maximum.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_listout">listout = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='listout' Line='listout = yes'>
  <DD>List instead of plot the histogram.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_device">device = "<TT>stdgraph</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='device' Line='device = "stdgraph"'>
  <DD>The output graphics device.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
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
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
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
  <H2><A NAME="s_time_requirements">TIME REQUIREMENTS</A></H2>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_use_instead">USE INSTEAD</A></H2>
  <! BeginSection: 'USE INSTEAD'>
  <UL>
  plot.phistogram
  </UL>
  <! EndSection:   'USE INSTEAD'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  images.imhistogram, fields
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'USE INSTEAD' 'SEE ALSO'  >
  
  </BODY>
  </HTML>