blkrep — Block replicate a list of N-D images
=============================================

**Package: imgeom**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>blkrep (Sep86)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>images.imgeom</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>blkrep (Sep86)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>blkrep</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  blkrep -- block replicate n-dimensional images
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage_">USAGE	</A></H2>
  <! BeginSection: 'USAGE	'>
  <UL>
  <PRE>
  blkrep input output b1 [b2 b3 b4 b5 b6 b7]
  </PRE>
  </UL>
  <! EndSection:   'USAGE	'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of images to be block replicated.  Image sections are allowed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>List of output image names.  If the output image name is the same as the input
  image name then the block replicated image replaces the input image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_b1">b1, b2, b3, b4, b5, b6, b7</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='b1' Line='b1, b2, b3, b4, b5, b6, b7'>
  <DD>Block replication factor for dimensions 1 - 7.  Only the block factors for
  the dimensions of the input image are required.  Dimension 1 is the column
  or x axis, dimension 2 is the line or y axis.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The list of input images are block replicated by the specified factors
  to form the output images.  The output image names are specified by the
  output list.  The number of output image names must be the same as the
  number of input images.  An output image name may be the same as the
  corresponding input image in which case the block averaged image
  replaces the input image.  Only the block factors for the dimensions
  of the input images are used.
  <P>
  This task is a complement to <B>blkavg</B> which block averages or sums
  images.  Another related task is <B>magnify</B> which interpolates
  images to arbitrary sizes.  This task, however, is only applicable to
  two dimensional images with at least two pixels in each dimension.
  Finally, in conjunction with <B>imstack</B> a lower dimensional image
  can be replicated to higher dimensions.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_timings">TIMINGS</A></H2>
  <! BeginSection: 'TIMINGS'>
  <UL>
  VAX 11/750 with FPA running UNIX 4.3BSD and IRAF V2.4:
  <P>
  <PRE>
         SIZE DATATYPE REPLICATION     CPU  CLOCK
          100    short           5    0.5s     1s
          100     real           5    0.5s     1s
      100x100    short         5x5    1.7s     5s
      100x100     real         5x5    2.1s     6s
    100x100x1     real       5x5x5    9.7s    33s
  </PRE>
  </UL>
  <! EndSection:   'TIMINGS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <DL>
  <DT><B><A NAME="l_1">1.</A></B></DT>
  <! Sec='EXAMPLES' Level=0 Label='1' Line='1.'>
  <DD>To block replicate a 1D image in blocks of 3:
  <P>
  cl&gt; blkrep imagein imageout 3
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_2">2.</A></B></DT>
  <! Sec='EXAMPLES' Level=0 Label='2' Line='2.'>
  <DD>To block replicate a 2D image in blocks of 2 by 3:
  <P>
  cl&gt; blkrep imagein imageout 2 3
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_3">3.</A></B></DT>
  <! Sec='EXAMPLES' Level=0 Label='3' Line='3.'>
  <DD>To block replicate two 2D images in blocks of 5 by 5:
  <P>
  cl&gt; blkrep image1,image2 out1,out2 5 5
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_4">4.</A></B></DT>
  <! Sec='EXAMPLES' Level=0 Label='4' Line='4.'>
  <DD>To block replicate a 3D image in place by factors of 2:
  <P>
  cl&gt; blkrep image1 image1 2 2 2
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_5">5.</A></B></DT>
  <! Sec='EXAMPLES' Level=0 Label='5' Line='5.'>
  <DD>To smooth an image by block averaging and expanding by a factor of 2:
  <P>
  <PRE>
  cl&gt; blkavg imagein imageout 2 2
  cl&gt; blkrep imageout imageout 2 2
  </PRE>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_6">6.</A></B></DT>
  <! Sec='EXAMPLES' Level=0 Label='6' Line='6.'>
  <DD>To take a 1D image and create a 2D image in which each line is the same:
  <P>
  <PRE>
  cl&gt; imstack image1d image2d
  cl&gt; blkrep image2d image2d 1 100
  </PRE>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_7">7.</A></B></DT>
  <! Sec='EXAMPLES' Level=0 Label='7' Line='7.'>
  <DD>To take a 1D image and create a 2D image in which each column is the same:
  <P>
  <PRE>
  cl&gt; imstack image1d image2d
  cl&gt; imtranspose image2d image2d
  cl&gt; blkrep image2d image2d 100 1
  </PRE>
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  blkavg, imstack, magnify
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'TIMINGS' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>