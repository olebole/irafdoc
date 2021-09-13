binpairs — Bin pairs of (x,y) points in log separation
======================================================

**Package: nproto**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>binpairs (Oct84)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.nproto</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>binpairs (Oct84)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>binpairs</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  binpairs -- Bin pairs of (x,y) points in log separation
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage_">USAGE	</A></H2>
  <! BeginSection: 'USAGE	'>
  <UL>
  binpairs file1 file2 rmin rmax nbins
  </UL>
  <! EndSection:   'USAGE	'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_file1">file1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='file1' Line='file1'>
  <DD>File containing (x,y) points to be paired.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_file2">file2</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='file2' Line='file2'>
  <DD>File containing (x,y) points to be paired.  This file may be the same
  as file1.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_rmin">rmin</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rmin' Line='rmin'>
  <DD>The minimum separation to be binned.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_rmax">rmax</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rmax' Line='rmax'>
  <DD>The maximum separation to be binned.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nbins">nbins</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nbins' Line='nbins'>
  <DD>The number of log separation bins to be computed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>Print progress information?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The (x,y) points in the specified files are paired and the number of pairs
  in each bin of log separation is computed and output.  The two files may
  be the same.  There are
  <I>nbins</I> separation bins between the separations <I>rmin</I> and <I>rmax</I>.
  If the verbose parameter is yes then progress information is printed on the
  standard error output at intervals of 5% of the time.
  The output consists of the lower limit of the separation bin, the number of
  pairs in the bin, the number of pairs divided by the total number of pairs,
  and the annular area of the bin.
  <P>
  This task is useful for computing two point correlation functions.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  <PRE>
      cl&gt; binpairs data1 data2 .01 1 20 &gt;&gt; result
  <P>
  	    or
  <P>
      cl&gt; binpairs data data .01 1 20 &gt;&gt; result
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>