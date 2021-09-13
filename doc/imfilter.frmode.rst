frmode — Quantize and ring modal filter a list of 1D or 2D images
=================================================================

**Package: imfilter**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>frmode (May95)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>images.imfilter</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>frmode (May95)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>frmode</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  frmode -- quantize and ring modal filter a list of images
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  frmode input output rinner router
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of input images.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>List of filtered images. The number of input images must be the same as the
  number of output images. If the input image name equals the output image name
  the filtered image replaces the original image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_rinner">rinner, router</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rinner' Line='rinner, router'>
  <DD>The inner and outer semi-major axes of the ring filter in pixels. If rinner
  is set to 0.0 then the ring filter becomes a circular filter.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ratio">ratio = 1.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ratio' Line='ratio = 1.0'>
  <DD>The ratio of the semi-minor axis to the semi-major axis of the ring filter.
  If ratio is 1.0 the ring filter is circularly symmetric.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_theta">theta = 0.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='theta' Line='theta = 0.0'>
  <DD>The position angle of the major axis of the ring filter. Theta is measured
  in degrees counter-clockwise from the x axis and must be between 0 and 180
  degrees.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_hmin">hmin = -32768, hmax = 32767</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='hmin' Line='hmin = -32768, hmax = 32767'>
  <DD>The histogram quantization parameters. Hmin and hmax define the minimum
  and maximum permitted values for the integer representation of the input image.
  The default values are those suitable for the 16 bit twos complement data
  produced by current CCDs. Hmin and hmax should be chosen so as to
  minimize the space required to store the image histogram.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_zmin">zmin = INDEF, zmax = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='zmin' Line='zmin = INDEF, zmax = INDEF'>
  <DD>The data quantization parameters. Zmin and zmax default to the minimum and
  maximum pixel values in the input image. Pixel values from zmin to zmax
  are linearly mapped to integers from hmin to hmax.
  If zmin = hmin and zmax = hmax, the image pixels are converted directly to
  integers.  Image values less than or greater than
  zmin or zmax will default to hmin and hmax respectively.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_zloreject">zloreject = INDEF, zhireject = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='zloreject' Line='zloreject = INDEF, zhireject = INDEF'>
  <DD>The minimum and maximum good pixel values. Zloreject and zhireject default
  to zmin and zmax in the input data or hmin and hmax in the integer
  representation of the input image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_unmap">unmap = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='unmap' Line='unmap = yes'>
  <DD>Frmode rescales the integer values to numbers between zmin and zmax
  by default. If the user wishes to preserve the mode of the quantized images,
  the <I>unmap</I> parameter should be set to no.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_boundary">boundary = "<TT>nearest</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='boundary' Line='boundary = "nearest"'>
  <DD>The type of boundary extension. The options are:
  <DL>
  <DT><B><A NAME="l_nearest">nearest</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='nearest' Line='nearest'>
  <DD>Use the value of the nearest pixel.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_constant">constant</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='constant' Line='constant'>
  <DD>Use a constant value.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_reflect">reflect</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='reflect' Line='reflect'>
  <DD>Reflect pixel values around the boundary.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_wrap">wrap</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='wrap' Line='wrap'>
  <DD>Wrap pixel values around the boundary.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_constant">constant = 0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='constant' Line='constant = 0.'>
  <DD>The value for constant valued boundary extension.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print messages about actions taken by the task ?
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  FRMODE takes a list of input images <I>input</I> and produces a set of filtered
  output images <I>output</I>. The filter consists of a sliding 
  circular / elliptical or annular circular / elliptical window whose size
  and orientation is determined by the <I>rinner</I>, <I>router</I>, <I>ratio</I>,
  and <I>theta</I> parameters.  The center pixel of the window is replaced by
  the mode of the pixels in the window, where the mode is defined as follows.
  <P>
  <PRE>
  	mode = 3. * median - 2. * mean
  </PRE>
  <P>
  The median of a sequence of numbers is defined to be the value of the
  (n + 1) / 2 number in the ordered sequence. Out of bounds pixel references
  are handled by setting the parameter boundary. The principal function of
  the circular / elliptical filters is to smooth an image using a 
  circularly / elliptically symmetric filter. The principal function of the
  circular / elliptical ring filter is to remove objects from the image
  which have a scale length or rinner and replace them with an estimate of
  the local background value.
  <P>
  If <I>zmin</I> = <I>hmin</I> and <I>zmax</I> = <I>hmax</I>,
  FRMODE converts the image pixels directly to integers.
  This operation may result in truncation of the pixel values of the
  input image is not an integer image.
  Otherwise the input image values from zmin to zmax are linearly mapped to
  integer values from hmin to hmax.
  The histogram, median, and number of pixels less
  than the median are computed for the first window position. These
  quantities are updated as the median filter moves one position and
  the mode is computed.  The <I>unmap</I> parameter is normally set
  so as to restore the output pixel values to the range defined by
  zmin and zmax, but may be turned off if the user wishes to
  examine the quantized pixels.
  The precision of the mode in integer space and pixel space
  is 1.0 and (zmax - zmin) / (hmax - hmin) respectively.
  <P>
  The <I>zloreject</I> and <I>zhireject</I> parameters may be used to reject
  bad data from the modal filtering box.  If no good
  data is left in the filtering box, then the mode is set to zloreject
  if the majority of the pixels are less than zloreject, or to zhireject
  if the majority of pixels are greater than zhireject.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_references">REFERENCES</A></H2>
  <! BeginSection: 'REFERENCES'>
  <UL>
  <P>
  A description of the fast median algorithm used here can be found in
  "<TT>Topics in Applied Physics: Two-Dimensional Digital Signal Processing II:
  Transforms and Median Filters</TT>", Volume 43, 1981, Springer-Verlag,
  edited by T.S. Huang, page 209.
  <P>
  The properties of the ring median filter and its application to
  astronomical data analysis problems is summarized in the
  article "<TT>A Ring Median Filter  for Digital Images</TT>" (Secker, J., 1995,
  PASP, 107, 496-501) and references therein.
  <P>
  </UL>
  <! EndSection:   'REFERENCES'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Modal filter a 16 bit CCD image using a circular ring filter with an
  inner radius of 4 pixels and a width of 1 pixel.
  <P>
  <PRE>
     im&gt; frmode input output 4.0 5.0 hmin=-32768 hmax=32767 zmin=-32768. \<BR>
     &gt;&gt;&gt; zmax=32767.
  </PRE>
  <P>
  2. Modal filter a KPNO PDS image using a circular filter of outer radius
  3.0.
  <P>
  <PRE>
     im&gt; frmode input output 0.0 3.0 hmin=0 hmax=4095 zmin=0. zmax=4095.
  </PRE>
  <P>
  3. Modal filter an 8 bit image using the same filter as example 2.
  <P>
  <PRE>
     im&gt; frmode input output 0.0 3.0 hmin=0 hmax=255 zmin=0. zmax=255.
  </PRE>
  <P>
  4. Modal filter an image with real values from 0.0 to 1.0 with a precision
  of .003 and leave the output pixels in integer format. Use a ring filter
  of inner radius 5.0 and width 0.5 pixels.
  <P>
  <PRE>
     im&gt; frmode input output 5.0 0.5 unmap- hmin=0 hmax=1000 zmin=0. \<BR>
     &gt;&gt;&gt; zmax=1.
  </PRE>
  <P>
  5. Modal filter the test image dev$pix rejecting any pixels &lt; 5 or
  greater than 19935 from the mode computing process using a circular
  filter of outer radius 5.0.
  <P>
  <PRE>
      im&gt; frmode dev$pix output 0.0 5.0 hmin=-1 hmax=20000 zmin=-1.0 \<BR>
      &gt;&gt;&gt; zmax=20000 zloreject=5 zhireject=20000
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_time_requirements">TIME REQUIREMENTS</A></H2>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  It requires approximately 39 and 27 CPU seconds to modal filter a
  512 by 512 square integer image with a circular filter of radius 5 pixels
  and a ring filter of inner and outer radii of 4.0 and 5.0 pixels
  respectively (SPARCStation2).
  <P>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
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
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  mode, rmode, fmode
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'REFERENCES' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>