.. _frmedian:

frmedian — Quantize and ring median filter a list of 1D or 2D images
====================================================================

**Package: imfilter**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  frmedian -- quantize and ring median filter a list of input images
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  frmedian input output rinner router
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
  the filtered images replaces the original image.
  </DD>
  </DL>
  <DL>
  <DT><B>rinner, router</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rinner' Line='rinner, router'>
  <DD>The inner and outer semi-major axes of the ring filter in pixels. If rinner
  is set to 0.0 then the ring filter becomes a circular filter.
  </DD>
  </DL>
  <DL>
  <DT><B>ratio = 1.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ratio' Line='ratio = 1.0'>
  <DD>The ratio of the semi-minor axis to the semi-major axes of the ring filter.
  If ratio is 1.0 the ring filter is circularly symmetric.
  </DD>
  </DL>
  <DL>
  <DT><B>theta = 0.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='theta' Line='theta = 0.0'>
  <DD>The position angle of the major axis of the ring filter. Theta is measured
  counter-clockwise in degrees from the x axis and must be between 0 and
  180 degrees.
  </DD>
  </DL>
  <DL>
  <DT><B>hmin = -32768, hmax = 32767</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='hmin' Line='hmin = -32768, hmax = 32767'>
  <DD>The histogram quantization parameters. Hmin and hmax define the minimum and
  maximum
  permitted values for the integer representation of the input image. The
  default values are those suitable for the 16 bit twos complement data
  produced by current CCDs. Hmin and hmax should be chosen so as to
  minimize the space required to store the image histogram.
  </DD>
  </DL>
  <DL>
  <DT><B>zmin = INDEF, zmax = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='zmin' Line='zmin = INDEF, zmax = INDEF'>
  <DD>The data quantization parameters. Zmin and zmax default to the minimum and
  maximum pixel values in the input image. Pixel values from zmin to zmax
  are linearly mapped to integer values from hmin to hmax. If zmin = hmin and
  zmax = hmax, the image pixels are converted directly to integers.
  Image values less than or greater than
  zmin or zmax will default to hmin and hmax respectively.
  </DD>
  </DL>
  <DL>
  <DT><B>zloreject = INDEF, zhireject = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='zloreject' Line='zloreject = INDEF, zhireject = INDEF'>
  <DD>The minimum and maximum good pixel values. Zloreject and zhireject default
  to zmin and zmax in the input data or hmin and hmax in the integer
  representation of the input image.
  </DD>
  </DL>
  <DL>
  <DT><B>unmap = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='unmap' Line='unmap = yes'>
  <DD>Frmedian rescale the integer values to numbers between zmin and zmax
  by default. If the user wishes to preserve  the mode of the quantized
  images, the unmap parameter should be set to no.
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
  FRMEDIAN takes a list of input images <I>input</I> and produces a set of filtered
  output images <I>output</I>. The filter consists of a sliding
  circular / elliptical or annular circular / elliptical window whose size
  and orientation is determined 
  by the <I>rinner</I>, <I>router</I>, <I>ratio</I>, and <I>theta</I> parameters.
  The center pixel in the window is replaced by the median of the pixels in the
  window, where the median of a sequence of numbers is defined to be
  the value of the (n + 1) / 2  number in the ordered sequence.
  Out of bounds pixel references are handled by setting the parameter
  <I>boundary</I>. The principal function of the circular / elliptical filters
  is to smooth an image using a circularly / elliptically symmetric filter.
  The principal function of the circular / elliptical ring filter is to
  remove objects from the image which have a scale length of rinner and
  replace them with an estimate of the local background value.
  <P>
  If <I>zmin</I> = <I>hmin</I> and <I>zmax</I> = <I>hmax</I>, FRMEDIAN converts
  the image pixels directly to
  integers.  This operation may result in truncation of the pixel values
  if the input image is not an integer image. Otherwise the
  input pixel values from zmin to zmax are linearly mapped to integer
  values from hmin to hmax. The histogram, median, and number of pixels less
  than the median, are computed for the first window position. These
  quantities are updated as the median filter moves one position.
  The <I>unmap</I> parameter is normally set so as to restore the output 
  pixel values to the range defined by zmin to zmax, but may be turned off
  if the user wishes to examine the quantized pixels. The precision of the
  median in integer space and pixel space is 1.0 and
  (zmax - zmin) / (hmax - hmin) respectively.
  <P>
  The <I>zloreject</I> and <I>zhireject</I> parameters may be used to reject
  bad data from the median filtering box.  If no good 
  data is left in a give filtering box, then the median is set to zloreject
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
  Transforms and Median Filters</TT>", Volume 43, 1981, Springer-Verlag, edited
  by T.S. Huang, page 209.
  <P>
  The properties of the ring median filter and its application to
  astronomical data analysis problems is summarized in the
  article "<TT>A Ring Median Filter  for Digital Images</TT>" (Secker, J., 1995,
  PASP, 107, 496-501) and reference therein.
  <P>
  </UL>
  <! EndSection:   'REFERENCES'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Median filter a 16 bit CCD image using a circular ring filter with an inner
  radius of 4 pixels and a width of 1 pixel.
  <P>
  <PRE>
     im&gt; frmedian input output 4.0 5.0 hmin=-32768 hmax=32767 \<BR>
     &gt;&gt;&gt; zmin=-32768.  zmax=32767.
  </PRE>
  <P>
  2. Median filter a KPNO PDS image using a circular ring filter of outer
  radius 3.
  <P>
  <PRE>
     im&gt; frmedian input output 0.0 3.0 hmin=0 hmax=4095 zmin=0. zmax=4095.
  </PRE>
  <P>
  3. Median filter an 8 bit image using the same filter used in example 2.
  <P>
  <PRE>
     im&gt; frmedian input output 0.0 3.0 hmin=0 hmax=255 zmin=0. zmax=255.
  </PRE>
  <P>
  4. Median filter an image with real values from 0.0 to 1.0 with a precision
  of .003 and leave the output pixels in integer format. Use a ring filter of
  inner radius 5.0 and width 0.5 pixels.
  <P>
  <PRE>
     im&gt; frmedian input output 5.0 5.5 unmap- hmin=0 hmax=1000 zmin=0. \<BR>
     &gt;&gt;&gt; zmax=1.
  </PRE>
  <P>
  5. Median filter the test image dev$pix rejecting any pixels &lt; 5 or
  greater than 19935 from the medianing process using a circular filter
  of outer radius 5.0.
  <P>
  <PRE>
      im&gt; frmedian dev$pix output 0.0 5.0 hmin=-1 hmax=20000 zmin=-1.0 \<BR>
      &gt;&gt;&gt; zmax=20000 zloreject=5 zhireject=20000
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  It requires approximately 30 and 22 cpu seconds to median filter a
  512 by 512 square integer image with a circular filter of radius 5 pixels
  and a ring filter of inner and outer radii of 4.0 and 5.0 pixels respectively.
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
  median, rmedian, fmedian
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'REFERENCES' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
