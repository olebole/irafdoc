.. _mode:

mode — Modal box filter a list of 1D or 2D images
=================================================

**Package: imfilter**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  mode -- modal filter a list of images
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  mode input output xwindow ywindow
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
  <DD>The size of the modal filter. Xwindow and ywindow are assumed to be
  odd integers. Even values will be rounded up to the nearest odd integer.
  </DD>
  </DL>
  <DL>
  <DT><B>zloreject = INDEF, zhireject = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='zloreject' Line='zloreject = INDEF, zhireject = INDEF'>
  <DD>The minimum and maximum good data values. Zloreject and zhireject default
  to -MAX_REAL and MAX_REAL respectively.
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
  MODE takes a list of input images <I>input</I> and produces a set of filtered
  output images <I>output</I>. The modal filter consists of a sliding
  rectangular window  of dimensions <I>xwindow</I>
  by <I>ywindow</I>. The center pixel of the window is replaced by the mode
  of all the pixels in the window where the mode of a sequence of numbers
  is defined below.
  <P>
  <PRE>
  		mode = 3. * median - 2. * mean
  </PRE>
  <P>
  The median of a sequence of pixels is defined as the value of the
  (n + 1) / 2 number in the ordered sequence.
  Out of bounds pixel references are handled by setting the parameter
  <I>boundary</I>.
  <P>
  The <I>zloreject</I> and <I>zhireject</I> parameters may be used to reject
  bad data from the modal filtering box.  If no good 
  data is left in the filtering box, then the mode is set to zloreject
  if the majority of the pixels are less than zloreject, or to zhireject
  if the majority of pixels are greater than zhireject.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>References</H3>
  <! BeginSection: 'REFERENCES'>
  <UL>
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
  1. Modal filter an image using a 5 by 5 window and nearest pixel boundary
  extension.
  <P>
  <PRE>
     im&gt; mode m74 m74.5by5 5 5
  </PRE>
  <P>
  2. Modal filter an image using a 3 by 3 window and constant boundary
  extension.
  <P>
  <PRE>
     im&gt; mode m74 m74.5by5 3 3 boun=const const=0.
  </PRE>
  <P>
  3. Modal filter the test image, rejecting pixels &lt; 5 and &gt; 19935 from the
  modal filter.
  <P>
  <PRE>
      im&gt; mode dev$pix pix77 7 7 zlo=5 zhi=19935
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  <P>
  Mode requires approximately 11 and 19 CPU seconds to filter a 512 by
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
  The IRAF task FMODE is significantly more efficient than MODE
  and should be used if the data can be quantized.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  fmode, rmode, frmode
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'REFERENCES' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
