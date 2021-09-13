.. _boxcar:

boxcar — Boxcar smooth a list of 1 or 2-D images
================================================

**Package: imfilter**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  boxcar -- boxcar smooth a list of images
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  boxcar input output xwindow ywindow
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of images to be smoothed.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>List of output images. The number of output images must equal the number of
  input images. If the input images name equals the output image name the
  smoothed image will replace the input image.
  </DD>
  </DL>
  <DL>
  <DT><B>xwindow, ywindow</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xwindow' Line='xwindow, ywindow'>
  <DD>The size of the smoothing window.
  </DD>
  </DL>
  <DL>
  <DT><B>boundary = "<TT>nearest</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='boundary' Line='boundary = "nearest"'>
  <DD>The boundary extension options are:
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
  <DD>Generate a value by reflecting around the boundary.
  </DD>
  </DL>
  <DL>
  <DT><B>wrap</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='wrap' Line='wrap'>
  <DD>Generate a value by wrapping around to the opposite side of the image.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>constant = 0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='constant' Line='constant = 0.'>
  <DD>The constant for constant-valued boundary extension.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  BOXCAR smooths the list of images specified by <I>input</I> with a
  flat-topped rectangular kernel of dimensions <I>xwindow</I> by <I>ywindow</I>
  and places the smoothed images in <I>output</I>. The type of boundary
  extension is optional and set by the <I>boundary</I> parameter.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Smooth an image using a 3 by 3 smoothing box and nearest neighbor boundary
     extension.
  <P>
  <PRE>
      cl&gt; boxcar m82 m82.box 3 3
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  <P>
  BOXCAR requires approximately 30 cpu seconds to smooth a
  512 square real image with a  5 by 5 kernel (VAX 11/750 with fpa).
  <P>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  convolve, gauss, laplace, gradient
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
