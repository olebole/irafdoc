.. _blkavg:

blkavg — Block average or sum a list of N-D images
==================================================

**Package: imgeom**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  blkavg -- block average or sum n-dimensional images
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage	</H3>
  <! BeginSection: 'USAGE	'>
  <UL>
  <PRE>
  blkavg input output b1 b2 b3 b4 b5 b6 b7
  </PRE>
  </UL>
  <! EndSection:   'USAGE	'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of images to be block averaged.  Image sections are allowed.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>List of output image names.  If the output image name is the same as the input
  image name then the block averaged image replaces the input image.
  </DD>
  </DL>
  <DL>
  <DT><B>b1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='b1' Line='b1'>
  <DD>The number of columns to be block averaged (dimension 1, or x).
  </DD>
  </DL>
  <DL>
  <DT><B>b2</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='b2' Line='b2'>
  <DD>The number of lines to be block averaged (dimension 2, or y).
  </DD>
  </DL>
  <DL>
  <DT><B>b3</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='b3' Line='b3'>
  <DD>The number of bands to be block averaged (dimension 3, or z).
  </DD>
  </DL>
  <DL>
  <DT><B>b4</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='b4' Line='b4'>
  <DD>The number of pixels to be block averaged in dimension 4 (... etc. for b5-b7).
  </DD>
  </DL>
  <DL>
  <DT><B>option = "<TT>average</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='option' Line='option = "average"'>
  <DD>Type of block average.  The choices are "<TT>average</TT>" and "<TT>sum</TT>".
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The list of input images are block averaged or summed to form the output images.
  The output image names are specified by the output list.  The number of
  output image names must be the same as the number of input images.
  An output image name may be the same
  as the corresponding input image in which case the block averaged image replaces
  the input image.  The last column, line, etc. of the output image may be
  a partial block.  The option parameter selects whether to block average
  or block sum.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Timings</H3>
  <! BeginSection: 'TIMINGS'>
  <UL>
  It requires approximately 10 cpu seconds to block average a 512 by 512
  short image by a factor of 8 in each direction (Vax 11/750 with fpa).
  </UL>
  <! EndSection:   'TIMINGS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. To block average a 2-d image in blocks of 2 by 3:
  <P>
      cl&gt; blkavg imagein imageout 2 3
  <P>
  2. To block sum two 2-d images in blocks of 5 by 5:
  <P>
      cl&gt; blkavg image1,image2 out1,out2 5 5 op=sum 
  <P>
  3. To block average a 3-d image by 4 in x and y and 2 in z:
  <P>
      cl&gt; blkavg imagein imageout 4 4 2
  <P>
  		or
  <P>
      cl&gt; blkavg imagein imageout b1=4 b2=4 b3=2
  </UL>
  <! EndSection:    'EXAMPLES'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'TIMINGS' 'EXAMPLES'  >
  
