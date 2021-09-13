.. _fmode:

fmode — Quantize and box modal filter a list of 1D or 2D images
===============================================================

**Package: imfilter**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  fmode -- quantize and box modal filter a list of images
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  fmode input output xwindow ywindow
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of input images.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>List of filtered images. The number of input images must be the same as the
  number of output images. If the input image name equals the output image name
  the filtered image replaces the original image.
  </DD>
  </DL>
  <DL>
  <DT><B>xwindow, ywindow</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xwindow' Line='xwindow, ywindow'>
  <DD>The size of the modal filter. Xwindow and ywindow must be odd.
  Even values for xwindow or ywindow will be rounded up to the
  nearest odd integer.
  </DD>
  </DL>
  <DL>
  <DT><B>hmin = -32768, hmax = 32767</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='hmin' Line='hmin = -32768, hmax = 32767'>
  <DD>The histogram quantization parameters. Hmin and hmax define the minimum
  and maximum permitted values for the integer representation of the
  input image. The default values are those suitable for the 16 bit twos
  complement data produced by current CCDs. Hmin and hmax should be chosen
  so as to minimize the space required to store the image histogram.
  </DD>
  </DL>
  <DL>
  <DT><B>zmin = INDEF, zmax = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='zmin' Line='zmin = INDEF, zmax = INDEF'>
  <DD>The quantization parameters. Zmin and zmax default to the minimum and
  maximum pixel values in the input image. Pixel values from zmin to zmax
  are linearly mapped to integer values from hmin to hmax.
  If zmin = hmin and zmax = hmax, the image pixels are converted directly
  to integers. Image values less than or greater than
  zmin or zmax will default to hmin and hmax respectively.
  </DD>
  </DL>
  <DL>
  <DT><B>zloreject = INDEF, zhireject = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='zloreject' Line='zloreject = INDEF, zhireject = INDEF'>
  <DD>The minimum and maximum good pixel values. Zloreject and zhireject default
  to zmin and zmax in the input data or equivalently to hmin and hmax in the
  integer representation of the input image.
  </DD>
  </DL>
  <DL>
  <DT><B>unmap = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='unmap' Line='unmap = yes'>
  <DD>Fmode rescales the integer values to numbers between zmin and zmax
  by default. If the user wishes to preserve the mode of the quantized images,
  the <I>unmap</I> parameter should be set to no.
  </DD>
  </DL>
  <DL>
  <DT><B>boundary = "<TT>nearest</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='boundary' Line='boundary = "nearest"'>
  <DD>The type of boundary extension. The options are:
  <DL>
  <DT><B>nearest</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='nearest' Line='nearest'>
  <DD>Use the value of the nearest pixel.
  </DD>
  </DL>
  <DL>
  <DT><B>constant</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='constant' Line='constant'>
  <DD>Use a constant value.
  </DD>
  </DL>
  <DL>
  <DT><B>reflect</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='reflect' Line='reflect'>
  <DD>Reflect pixel values around the boundary.
  </DD>
  </DL>
  <DL>
  <DT><B>wrap</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='wrap' Line='wrap'>
  <DD>Wrap pixel values around the boundary.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>constant = 0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='constant' Line='constant = 0.'>
  <DD>The value for constant valued boundary extension.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print messages about actions taken by the task ?
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  FMODE takes a list of input images <I>input</I> and produces a set of filtered
  output images <I>output</I>. The filter consists of a sliding rectangular
  <I>xwindow</I> by <I>ywindow</I> window whose function is to replace the
  center pixel in the window with the mode of the pixels in the
  window. The mode is defined in the expression below.
  <P>
  <PRE>
  	mode = 3. * median - 2. * mean
  </PRE>
  <P>
  The median of a sequence of numbers is defined to be the value of the
  (n + 1) / 2 pixel in the ordered sequence. Out-of-bounds pixel references are
  handled by setting the parameter <I>boundary</I>.
  <P>
  If <I>zmin</I> = <I>hmin</I> and <I>zmax</I> = <I>hmax</I>, FMODE converts
  the image pixels directly
  to integers. This operation may result in truncation of the pixel
  values if the input image is not an integer image.
  Otherwise the input pixel values from zmin to zmax are linearly mapped
  to integer values from hmin to hmax.
  The histogram, median, and number of pixels less
  than the median, are computed for the first window position. These
  quantities are then updated as the median filter moves one position and
  the mode is recomputed. The <I>unmap</I> parameter is normally set so as to
  restore the output pixel values to the range defined by zmin and zmax,
  but may be turned off if the user wishes to examine the quantized pixels.
  The precision of the mode in integer space and pixel space is 1.0
  and (zmax - zmin) / (hmax - hmin) respectively.
  <P>
  The <I>zloreject</I> and <I>zhireject</I> parameters may be used to
  reject bad data from the modal filtering box. If no good
  data is left in a given filtering box, then the mode is set to zloreject
  if the majority of the pixels are less than zloreject, or to zhireject
  if the majority of pixels are greater than zhireject.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>References</H3>
  <! BeginSection: 'REFERENCES'>
  <UL>
  <P>
  A description of the fast median algorithm used here can be found in
  "<TT>Topics in Applied Physics: Two-Dimensional Digital Signal Processing II:
  Transforms and Median Filters</TT>", Volume 43, 1981, Springer-Verlag, edited by
  T.S. Huang, page 209.
  <P>
  A derivation of the expression for the mode used here can be found in 
  "<TT>Statistics in Theory and Practice</TT>", Robert Lupton, 1993, Princeton
  University Press, problem 2.
  <P>
  </UL>
  <! EndSection:   'REFERENCES'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Modal filter a 16 bit CCD image using a 5 by 5 window.
  <P>
  <PRE>
     im&gt; fmode input output 5 5 hmin=-32768 hmax=32767 zmin=-32768. \<BR>
     &gt;&gt;&gt; zmax=32767.
  </PRE>
  <P>
  2. Modal filter a KPNO PDS image using a 3 by 3 window.
  <P>
  <PRE>
     im&gt; fmode input output 3 3 hmin=0 hmax=4095 zmin=0. zmax=4095.
  </PRE>
  <P>
  3. Modal filter an 8 bit image using a 3 by 3 image.
  <P>
  <PRE>
     im&gt; fmode input output 3 3 hmin=0 hmax=255 zmin=0. zmax=255.
  </PRE>
  <P>
  4. Modal filter an image with real values from 0.0 to 1.0 with a precision
  of .003.
  <P>
  <PRE>
     im&gt; fmode input output 5 5  hmin=0 hmax=1000 zmin=0. \<BR>
     &gt;&gt;&gt; zmax=1.
  </PRE>
  <P>
  5. Modal filter the test image dev$pix rejecting any pixels &lt; 5 or
  greater than 19935 from the mode computing process.
  <P>
  <PRE>
      im&gt; fmode dev$pix output 5 5 hmin=-1 hmax=20000 zmin=-1.0 \<BR>
      &gt;&gt;&gt; zmax=20000 zloreject=5 zhireject=20000
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  It requires approximately 6.1 and 7.6 CPU seconds to modal filter a
  512 by 512 square integer image with a 5 by 5 and 7 by 7 window respectively
  (SPARCStation2).
  <P>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  This technique is most suitable for integer data and data which has not
  been calibrated. For non-integer data the calculated median is an
  approximation only.
  <P>
  If the  dynamic range of the data defined by hmin and hmax is large the
  memory requirements can become very large.
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  mode, rmode, frmode
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'REFERENCES' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
