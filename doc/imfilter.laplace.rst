.. _laplace:

laplace — Laplacian filter a list of 1 or 2-D images
====================================================

**Package: imfilter**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  laplace -- convolve a list of images with a Laplacian filter
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  laplace input output
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of images to be convolved.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>List of output images. The number of output images must equal the number of
  input images. If the input image name equals the output image name the
  convolved image will replace the input image.
  </DD>
  </DL>
  <DL>
  <DT><B>laplace = "<TT>xycentral</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='laplace' Line='laplace = "xycentral"'>
  <DD>The Laplacian filters are a set of four three by three kernels which
  approximate the Laplacian operator, where a Laplacian operator is defined
  as the sum of the partial second derivatives in x and y.
  The elements of the four Laplacian kernels are shown in detail below.
  <DL>
  <DT><B>xycentral</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='xycentral' Line='xycentral'>
  <DD>The elements of the central column and row of a 3 by 3 image subraster are
  combined to estimate the Laplacian at the position of the central pixel.
  </DD>
  </DL>
  <DL>
  <DT><B>diagonals</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='diagonals' Line='diagonals'>
  <DD>The elements of the two diagonals of a 3 by 3 image subraster are combined
  to estimate the Laplacian at the position of the central pixel.
  </DD>
  </DL>
  <DL>
  <DT><B>xyall</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='xyall' Line='xyall'>
  <DD>The three columns and rows of a three by three image subraster are averaged
  to estimate the Laplacian at the position of the central pixel.
  </DD>
  </DL>
  <DL>
  <DT><B>xydiagonals</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='xydiagonals' Line='xydiagonals'>
  <DD>The central row and column and the two diagonals of a three by three image
  subraster are combined to estimate the Laplacian at the position of the
  central pixel.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>boundary = "<TT>nearest</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='boundary' Line='boundary = "nearest"'>
  <DD>The algorithm used to compute the values of the out of bounds pixels.
  The options are:
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
  LAPLACE convolves the list of images specified by <I>input</I> with one of
  four 3 by 3 Laplacian kernels specified by <I>laplace</I>
  and places the convolved images in <I>output</I>. If the image names
  in <I>output</I> equal the image names in <I>input</I> the Laplacian
  operation is performed in place and the original images are overwritten.
  Out of bounds pixels are computed using the algorithm specified by
  <I>boundary</I>.
  <P>
  The Laplacian filters are high-pass filters which act as a local edge detector.
  A characteristic of the Laplacian is that it is zero at points where the
  gradient is a maximum or a minimum. Therefore points detected as gradient
  edges would generally not be detected as edge points with the Laplacian
  filter. Another characteristic of Laplacian operators is that a single
  grey level transition may produce two distinct peaks one positive and
  one negative in the Laplacian which may be offset from the gradient location.
  <P>
  The four Laplacian filters are listed below. The I[*,*] are the elements of the
  input image and the O[*,*] are the elements of the output image.
  <P>
  <PRE>
      			xycenter
  <P>
  	     0*I[-1,1]  + 1*I[0,1]  + 0*I[1,1]  +
      O[0,0] = 1*I[-1,0]  - 4*I[0,0]  + 1*I[1,0]  +
               0*I[-1,-1] + 1*I[0,-1] + 0*I[1,-1]
  <P>
  <P>
  		       diagonals
  <P>
            I[-1,1]/sqrt(2)  + I[0,1]*0         +  I[1,1]/sqrt(2) +
  O[0,0] =  I[-1,0]*0        - I[0,0]*4/sqrt(2) +  I[1,0]*0       +
  	  I[-1,-1]/sqrt(2) + I[0,-1]*0        +  I[1,-1]/sqrt(2) 
  <P>
  		         xyall
  <P>
  	       2/3*I[-1,1]  -  1/3*I[0,1]  + 2/3*I[1,1]  +
      O[0,0] = - 1/3*I[-1,0]  -  4/3*I[0,0]  - 1/3*I[1,0]  +
                 2/3*I[-1,-1] -  1/3*I[0,-1] + 2/3*I[1,-1]
  <P>
  		       xydiagonals
  <P>
            I[-1,1]/sqrt(2)/2  + I[0,1]/2           + I[1,1]/sqrt(2)/2 +
  O[0,0] =  I[-1,0]/2          - I[0,0]*(2-sqrt(2)) + I[1,0]/2         +
  	  I[-1,-1]/sqrt(2)/2 + I[0,-1]/2          + I[1,-1]/sqrt(2) 
  <P>
  </PRE>
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Convolve an image with the Laplacian filter xyall using nearest neighbor
  boundary extension.
  <P>
      cl&gt; laplace m83 m83.lap xyall
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  <P>
  LAPLACE requires approximately 1.7 cpu seconds to convolve a
  512 square real image with a 3 by 3 Laplacian kernel on a Sparc
  Station 1.
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
  convolve, gauss, gradient, boxcar
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
