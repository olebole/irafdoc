.. _median:

median — Median box filter a list of 1D or 2D images
====================================================

**Package: imfilter**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  median -- median filter a list of images
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  median input output xwindow ywindow
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
  <DD>List of filtered images. The number of input images must be the same as
  the number of output images. If the input image name is the same as the
  output image name the original image is replaced by the filtered image.
  </DD>
  </DL>
  <DL>
  <DT><B>xwindow, ywindow</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xwindow' Line='xwindow, ywindow'>
  <DD>The size of the median filter. Xwindow and ywindow are assumed to be
  odd integers. If either xwindow or ywindow are even they will be rounded
  up to the nearest odd integer.
  </DD>
  </DL>
  <DL>
  <DT><B>zloreject = INDEF, zhireject = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='zloreject' Line='zloreject = INDEF, zhireject = INDEF'>
  <DD>The minimum and maximum good pixel values. Zloreject and zhireject default to 
  -MAX_REAL and MAX_REAL respectively.
  </DD>
  </DL>
  <DL>
  <DT><B>boundary = "<TT>nearest</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='boundary' Line='boundary = "nearest"'>
  <DD>The type of boundary extension. The options are:
  <DL>
  <DT><B>nearest</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='nearest' Line='nearest'>
  <DD>Use the value of the nearest boundary pixel.
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
  <DD>The value for constant value boundary extension.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  MEDIAN takes a list of input images <I>input</I> and produces a set of filtered
  output images <I>output</I>. The median filter consists of a sliding
  rectangular window  of dimensions <I>xwindow</I>
  by <I>ywindow</I>. The center pixel in the window is replaced by the median
  of all the pixels in the
  window, where the median of a sequence of numbers is defined to be  the value
  of the (n + 1) /2 pixel.  If even the window dimensions are rounded up
  to odd integers.  Out of bounds
  pixel references are handled by setting the parameter <I>boundary</I>.
  <P>
  The <I>zloreject</I> and <I>zhireject</I> parameters may be used to reject
  bad data from the median filtering box. If no good 
  data is left in the filtering box, the median is set to zloreject
  if the majority of the pixels are less than zloreject, or to zhireject
  if the majority of pixels are greater than zhireject.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Median filter an image using a 5 by 5 window and nearest pixel boundary
  extension.
  <P>
  <PRE>
     im&gt; median m74 m74.5by5 5 5
  </PRE>
  <P>
  2. Median filter an image using a 3 by 3 window and constant boundary extension.
  <P>
  <PRE>
     im&gt; median m74 m74.5by5 3 3 boun=const const=0.
  </PRE>
  <P>
  3. Median filter the test image dev$pix, removing all pixels less than 5 or
  greater than 19935 from the filtering box.
  <P>
  <PRE>
     im&gt; median dev$pix pix77 7 7 zlo=5 zhi=19935
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  <P>
  Median requires approximately 11 and 19 CPU seconds to filter a 512 by
  512 integer image using a 5 by 5 and 7 by 7 filter window respectively
  (SPARCStation2).
  <P>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  <P>
  The sort routine for the smaller kernels has been optimized. It may be
  desirable to optimize higher order kernels in future.
  <P>
  The IRAF task FMEDIAN is significantly more efficient than MEDIAN
  and should be used if the image is integer or can be quantized without
  significant loss of precision. 
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  <P>
  fmedian, rmedian, frmedian
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
