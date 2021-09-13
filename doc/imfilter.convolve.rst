.. _convolve:

convolve — Convolve a list of 1 or 2-D images with a rectangular filter
=======================================================================

**Package: imfilter**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  convolve -- convolve an image with an arbitrary rectangular kernel
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  convolve input output kernel
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of images to be convolved with the rectangular kernel.
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
  <DT><B>kernel</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='kernel' Line='kernel'>
  <DD>A text file name or a string listing the 2D kernel elements.
  The kernel elements are separated by whitespace or commas and the kernel rows
  are delimited by <I>row_delimiter</I>.
  In string entry mode the elements are assumed to be in row order.
  In text file entry mode the <I>last</I> row of the
  kernel is the <I>first</I> row of the text file.
  <I>Kernel</I> is requested if <I>bilinear</I> is "<TT>no</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>xkernel</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xkernel' Line='xkernel'>
  <DD>A text file or string containing the 1D x dimension component of the bilinear
  convolution kernel. The kernel elements are separated by whitespace
  or commas. <I>Xkernel</I> is requested if <I>bilinear</I> is "<TT>yes</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>ykernel</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ykernel' Line='ykernel'>
  <DD>A text file or string containing the 1D y dimension component of the bilinear
  convolution kernel. The kernel elements are separated by whitespace
  or commas. <I>Ykernel</I> is requested if <I>bilinear</I> is "<TT>yes</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>bilinear</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='bilinear' Line='bilinear'>
  <DD>Is the convolution kernel bilinear? If <I>bilinear</I> is yes, then the full 2D
  convolution kernel <I>kernel</I> can be expressed as two independent 1D
  convolutions <I>xkernel</I> and <I>ykernel</I>,
  and a more efficient convolution algorithm is used.
  </DD>
  </DL>
  <DL>
  <DT><B>radsym = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='radsym' Line='radsym = no'>
  <DD>Is the convolution kernel radially symmetric? If radsym "<TT>yes</TT>", a more efficient
  convolution algorithm is used.
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
  <DL>
  <DT><B>row_delimiter = "<TT>;</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='row_delimiter' Line='row_delimiter = ";"'>
  <DD>The row delimiter character for multi-row kernels.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  CONVOLVE convolves the list of images specified by <I>input</I> with an
  arbitrary user supplied rectangular kernel <I>kernel</I> (if <I>bilinear</I>
  is "<TT>no</TT>") or two equivalent 1D kernels <I>xkernel</I> and <I>ykernel</I>
  (if <I>bilinear</I> is "<TT>yes</TT>") and places the convolved images in <I>output</I>. 
  Out of bounds pixels are computed using the algorithm specified
  by <I>boundary</I>.
  <P>
  <I>Kernel</I> or alternatively <I>xkernel</I> and <I>ykernel</I>  is either a
  text file name or a short string listing the kernel elements. 
  The kernel elements are separated by whitespace or commas and the kernel rows
  are delimited by the character <I>row_delimiter</I>. 
  In string entry mode the elements are assumed to be in row order.
  In text file entry mode the <I>last</I> row of the
  kernel is the <I>first</I> row of the text file.
  <P>
  The parameters <I>bilinear</I> and <I>radsym</I> can be used to greatly
  speed up the convolution task for convolution kernels which have
  the appropriate mathematical form. Bilinear convolution kernels
  are those which define a function which is mathematically separable in
  the x and y dimension. In this case convolving each line of the input
  image with <I>xkernel</I> and then convolving each column of this intermediate
  image with <I>ykernel</I>, is operationally equivalent to convolving
  each point in the entire image  with the full 2D kernel <I>kernel</I>.
  Radially symmetric kernels are those which are symmetric about some
  central point.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  Examples 1 and 2 use the following kernel where -1 is element 1 of row 1.
  <P>
  <PRE>
  	          1.  1.  1.
  	 kernel = 0.  0.  0.
  	         -1. -1. -1.
  </PRE>
  <P>
  1. Convolve an image with the above kernel using string entry mode and wrap
  around boundary extension.
  <P>
  <PRE>
      cl&gt; convolve m82 m82.cnv "-1. -1. -1.; 0. 0. 0.; 1. 1. 1." bound=wrap
  </PRE>
  <P>
  2. Type the contents of the kernel file fdy on the terminal. Convolve an image
  with the kernel in fdy using nearest neighbor boundary extension.
  <P>
  <PRE>
      cl&gt; type fdy
  <P>
          1. 1. 1.;
          0. 0. 0.;
          -1. -1. -1.;
  <P>
      cl&gt; convolve m74 m74.cnv fdy
  </PRE>
  <P>
  Example 3 uses the following bilinear kernel, where x# and y# are elements
  of xkernel and ykernel respectively.
  <P>
  <PRE>
  	xkernel = .2500  .5000  .2500
  <P>
  	ykernel = .2500  .5000  .2500
  <P>
  		  .0625  .1250  .0625      y1*x1  y1*x2  y1*x3
  	 kernel = .1250  .2500  .1250   =  y2*x1  y2*x2  y2*x3
  	          .0625  .1250  .0625      y3*x1  y3*x2  y3*x3
  <P>
  </PRE>
  <P>
  3. Convolve an image with the full 2D kernel and with the the equivalent 
  1D kernels xkernel and ykernel and compare the results.
  <P>
  <PRE>
      cl&gt; convolve m92 m92.1 kernel
  <P>
      cl&gt; convolve m92 m92.2 xkernel ykernel bilinear+
  <P>
      cl&gt; imarith m92.1 - m92.2 diff
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  CONVOLVE requires approximately 30 and 8 cpu seconds to convolve a
  512 square real image with 17 by 17 radially symmetric convolution kernel
  using the full 2D and bilinear kernels (if appropriate) respectively
  on a Sparc Station 1.
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
  gauss, laplace, gradient, boxcar
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
