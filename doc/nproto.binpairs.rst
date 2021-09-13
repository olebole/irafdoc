.. _binpairs:

binpairs — Bin pairs of (x,y) points in log separation
======================================================

**Package: nproto**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  binpairs -- Bin pairs of (x,y) points in log separation
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage	</H3>
  <! BeginSection: 'USAGE	'>
  <UL>
  binpairs file1 file2 rmin rmax nbins
  </UL>
  <! EndSection:   'USAGE	'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>file1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='file1' Line='file1'>
  <DD>File containing (x,y) points to be paired.
  </DD>
  </DL>
  <DL>
  <DT><B>file2</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='file2' Line='file2'>
  <DD>File containing (x,y) points to be paired.  This file may be the same
  as file1.
  </DD>
  </DL>
  <DL>
  <DT><B>rmin</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rmin' Line='rmin'>
  <DD>The minimum separation to be binned.
  </DD>
  </DL>
  <DL>
  <DT><B>rmax</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rmax' Line='rmax'>
  <DD>The maximum separation to be binned.
  </DD>
  </DL>
  <DL>
  <DT><B>nbins</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nbins' Line='nbins'>
  <DD>The number of log separation bins to be computed.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>Print progress information?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
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
  <H3>Examples</H3>
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
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
