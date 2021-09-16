.. _gauss:

gauss — Convolve a list of 1 or 2-D images with an elliptical Gaussian
======================================================================

**Package: imfilter**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  gauss -- convolve a list of images with an elliptical Gaussian function
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  gauss input output sigma
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of images to be convolved with the elliptical Gaussian function.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>List of output images. The number of output images must equal the number of
  input images. If the input image name equals the output image name, the
  convolved image will replace the input image.
  </DD>
  </DL>
  <DL>
  <DT><B>sigma</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sigma' Line='sigma'>
  <DD>The sigma of the Gaussian function in pixels along the direction <I>theta</I>
  of the major axis of the Gaussian function.
  </DD>
  </DL>
  <DL>
  <DT><B>ratio = 1.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ratio' Line='ratio = 1.'>
  <DD>The ratio of the sigma in the minor axis direction to the sigma in the major
  axis direction of the Gaussian function.
  If <I>ratio</I> is 1 the Gaussian function is circular.
  </DD>
  </DL>
  <DL>
  <DT><B>theta = 0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='theta' Line='theta = 0.'>
  <DD>The position of the major axis of the elliptical Gaussian function.
  <I>Theta</I> is measured counter-clockwise from the x axis and must be between
  0 and 180 degrees.
  </DD>
  </DL>
  <DL>
  <DT><B>nsigma = 4.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nsigma' Line='nsigma = 4.0'>
  <DD>The distance along the major axis of the Gaussian function at which
  the kernel is truncated in <I>sigma</I> pixels.
  </DD>
  </DL>
  <DL>
  <DT><B>bilinear = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='bilinear' Line='bilinear = yes'>
  <DD>Use the fact that the Gaussian function is separable (bilinear) in x and y if
  <I>theta</I> = 0, 90, or 180, to compute the 2D convolution more efficiently?
  <I>Bilinear</I> is always set to "<TT>no</TT>" internally, if the position angle of
  the major axis of the Gaussian is other than 0, 90 or 180 degrees.
  </DD>
  </DL>
  <DL>
  <DT><B>boundary = "<TT>nearest</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='boundary' Line='boundary = "nearest"'>
  <DD>The algorithm used to compute the values of the out of bounds pixels. The
  options are:
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
  GAUSS convolves the list of images in <I>input</I> with the
  Gaussian kernel specified by <I>sigma</I>, <I>ratio</I>, <I>theta</I> and
  <I>nsigma</I> and places the convolved images in <I>output</I>.
  If the image names in <I>input</I> equal the image names in <I>output</I>
  the convolution is performed in place and the original images are
  overwritten. Out of bounds pixels are computed using the algorithm
  specified by <I>boundary</I>.
  <P>
  If <I>bilinear</I> is "<TT>yes</TT>" and the major axis of the Gaussian kernel
  is aligned along either the x or y axis, GAUSS uses the fact that
  the Gaussian function is mathematically separable (bilinear) in x and y
  to speed up the convolution process. A bilinear 2D convolution kernel
  in x and y is one which can be separated into two equivalent 1D
  convolution kernels in x and y respectively. 
  <P>
  Although the bilinear approximation and the full 2D convolution are
  mathematically equivalent, the user will actually see SMALL differences
  between an image convolved with the full 2D kernel and the same image
  convolved with the equivalent bilinear kernel.
  These differences are the result of the finite size of the convolution kernel
  (the integration does not extend to infinity in either direction),
  and the fact that off-axis kernel elements outside the <I>nsigma</I> limit
  cannot be set to 0 in the bilinear case as they are in the full 2D
  case. Therefore the bilinear kernel is less radially symmetric than
  the full 2D kernel.  In most cases the differences are small and more
  than made up for by the greatly decreased execution time.
  <P>
  The Gaussian kernel has an elliptical cross-section and Gaussian
  profile and is defined mathematically as follows.
  <P>
  <PRE>
  1. Circularly Symmetric Gaussian Function
  <P>
      ratio = 1   theta = 0.0   N = normalization factor
  <P>
      G = N * exp (-0.5 * (r / sigma) ** 2)
  <P>
  2. Elliptical Gaussian Function (Theta = 0, 90 or 180)
  <P>
      sigmax = sigma   sigmay = ratio * sigmax   N = normalization factor
  <P>
      A = cos (theta) ** 2 / sigmax ** 2 + sin (theta) ** 2 / sigmay ** 2
  <P>
      B = 0.0
  <P>
      C = sin (theta) ** 2 / sigmax ** 2 + cos (theta) ** 2 / sigmay ** 2
  <P>
      z = A * x ** 2 + B * x * y + C * y ** 2 
  <P>
      G = N * exp (-0.5 * z)
  <P>
  3. Elliptical Gaussian  Function (Arbitrary Theta)
  <P>
      sigmax = sigma   sigmay = ratio * sigmax   N=normalization factor
  <P>
      A = cos (theta) ** 2 / sigmax ** 2 + sin (theta) ** 2 / sigmay ** 2
  <P>
      B = 2 * (1 / sigmax ** 2 - 1 / sigmay ** 2) * sin (theta) * cos (theta)
  <P>
      C = sin (theta) ** 2 / sigmax ** 2 + cos (theta) ** 2 / sigmay ** 2
  <P>
      z = A * x ** 2 + B * x * y + C * y ** 2 
  <P>
      G = N * exp (-0.5 * z)
  </PRE>
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Convolve an image with a circular Gaussian function of sigma 2.0, and
  size 4.0 sigma using nearest neighbor boundary extension and the bilinear
  kernel.
  <P>
      cl&gt; gauss m83 m83.gau 2.0
  <P>
  2. Do the same convolution using the full 2D kernel.
  <P>
      cl&gt; gauss m83 m83.gau.2D 2.0 bilinear-
  <P>
  3. Convolve an image with an elliptical Gaussian function whose sigma in the
  major and minor axis direction is 2.0 and 1.5 respectively, and whose position
  angle is 45 degrees, using wrap around boundary extension. In this case the
  full 2D kernel is used by default.
  <P>
      cl&gt; gauss m84 m84.gau 2.0 ratio=.75 theta=45. bound=wrap
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  GAUSS requires approximately 30 and 8 cpu seconds to
  convolve a 512 square real image with circularly symmetric Gaussian function
  of sigma 2 pixels, using the full 2D kernel and the bilinear
  kernel respectively, on a Sparc Station 1.
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  convolve, gradient, laplace, boxcar
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
