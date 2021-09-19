.. _convolve:

convolve: Convolve a list of 1 or 2-D images with a rectangular filter
======================================================================

**Package: imfilter**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  convolve -- convolve an image with an arbitrary rectangular kernel
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  convolve input output kernel
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input' -->
  <dd>List of images to be convolved with the rectangular kernel.
  </dd>
  </dl>
  <dl>
  <dt><b>output</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='output' Line='output' -->
  <dd>List of output images. The number of output images must equal the number of
  input images. If the input image name equals the output image name the
  convolved image will replace the input image.
  </dd>
  </dl>
  <dl>
  <dt><b>kernel</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='kernel' Line='kernel' -->
  <dd>A text file name or a string listing the 2D kernel elements.
  The kernel elements are separated by whitespace or commas and the kernel rows
  are delimited by <i>row_delimiter</i>.
  In string entry mode the elements are assumed to be in row order.
  In text file entry mode the <i>last</i> row of the
  kernel is the <i>first</i> row of the text file.
  <i>Kernel</i> is requested if <i>bilinear</i> is <tt>"no"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>xkernel</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='xkernel' Line='xkernel' -->
  <dd>A text file or string containing the 1D x dimension component of the bilinear
  convolution kernel. The kernel elements are separated by whitespace
  or commas. <i>Xkernel</i> is requested if <i>bilinear</i> is <tt>"yes"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>ykernel</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='ykernel' Line='ykernel' -->
  <dd>A text file or string containing the 1D y dimension component of the bilinear
  convolution kernel. The kernel elements are separated by whitespace
  or commas. <i>Ykernel</i> is requested if <i>bilinear</i> is <tt>"yes"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>bilinear</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='bilinear' Line='bilinear' -->
  <dd>Is the convolution kernel bilinear? If <i>bilinear</i> is yes, then the full 2D
  convolution kernel <i>kernel</i> can be expressed as two independent 1D
  convolutions <i>xkernel</i> and <i>ykernel</i>,
  and a more efficient convolution algorithm is used.
  </dd>
  </dl>
  <dl>
  <dt><b>radsym = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='radsym' Line='radsym = no' -->
  <dd>Is the convolution kernel radially symmetric? If radsym <tt>"yes"</tt>, a more efficient
  convolution algorithm is used.
  </dd>
  </dl>
  <dl>
  <dt><b>boundary = <tt>"nearest"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='boundary' Line='boundary = "nearest"' -->
  <dd>The algorithm used to compute the values of the out of bounds pixels. The
  options are:
  <dl>
  <dt><b>nearest</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='nearest' Line='nearest' -->
  <dd>Use the value of the nearest boundary pixel.
  </dd>
  </dl>
  <dl>
  <dt><b>constant</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='constant' Line='constant' -->
  <dd>Use a constant value.
  </dd>
  </dl>
  <dl>
  <dt><b>reflect</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='reflect' Line='reflect' -->
  <dd>Generate a value by reflecting around the boundary.
  </dd>
  </dl>
  <dl>
  <dt><b>wrap</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='wrap' Line='wrap' -->
  <dd>Generate a value by wrapping around to the opposite side of the image.
  </dd>
  </dl>
  </dd>
  </dl>
  <dl>
  <dt><b>constant = 0.</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='constant' Line='constant = 0.' -->
  <dd>The constant for constant-valued boundary extension.
  </dd>
  </dl>
  <dl>
  <dt><b>row_delimiter = <tt>";"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='row_delimiter' Line='row_delimiter = ";"' -->
  <dd>The row delimiter character for multi-row kernels.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  CONVOLVE convolves the list of images specified by <i>input</i> with an
  arbitrary user supplied rectangular kernel <i>kernel</i> (if <i>bilinear</i>
  is <tt>"no"</tt>) or two equivalent 1D kernels <i>xkernel</i> and <i>ykernel</i>
  (if <i>bilinear</i> is <tt>"yes"</tt>) and places the convolved images in <i>output</i>. 
  Out of bounds pixels are computed using the algorithm specified
  by <i>boundary</i>.
  </p>
  <p>
  <i>Kernel</i> or alternatively <i>xkernel</i> and <i>ykernel</i>  is either a
  text file name or a short string listing the kernel elements. 
  The kernel elements are separated by whitespace or commas and the kernel rows
  are delimited by the character <i>row_delimiter</i>. 
  In string entry mode the elements are assumed to be in row order.
  In text file entry mode the <i>last</i> row of the
  kernel is the <i>first</i> row of the text file.
  </p>
  <p>
  The parameters <i>bilinear</i> and <i>radsym</i> can be used to greatly
  speed up the convolution task for convolution kernels which have
  the appropriate mathematical form. Bilinear convolution kernels
  are those which define a function which is mathematically separable in
  the x and y dimension. In this case convolving each line of the input
  image with <i>xkernel</i> and then convolving each column of this intermediate
  image with <i>ykernel</i>, is operationally equivalent to convolving
  each point in the entire image  with the full 2D kernel <i>kernel</i>.
  Radially symmetric kernels are those which are symmetric about some
  central point.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  Examples 1 and 2 use the following kernel where -1 is element 1 of row 1.
  </p>
  <pre>
  	          1.  1.  1.
  	 kernel = 0.  0.  0.
  	         -1. -1. -1.
  </pre>
  <p>
  1. Convolve an image with the above kernel using string entry mode and wrap
  around boundary extension.
  </p>
  <pre>
      cl&gt; convolve m82 m82.cnv "-1. -1. -1.; 0. 0. 0.; 1. 1. 1." bound=wrap
  </pre>
  <p>
  2. Type the contents of the kernel file fdy on the terminal. Convolve an image
  with the kernel in fdy using nearest neighbor boundary extension.
  </p>
  <pre>
      cl&gt; type fdy
  
          1. 1. 1.;
          0. 0. 0.;
          -1. -1. -1.;
  
      cl&gt; convolve m74 m74.cnv fdy
  </pre>
  <p>
  Example 3 uses the following bilinear kernel, where x# and y# are elements
  of xkernel and ykernel respectively.
  </p>
  <pre>
  	xkernel = .2500  .5000  .2500
  
  	ykernel = .2500  .5000  .2500
  
  		  .0625  .1250  .0625      y1*x1  y1*x2  y1*x3
  	 kernel = .1250  .2500  .1250   =  y2*x1  y2*x2  y2*x3
  	          .0625  .1250  .0625      y3*x1  y3*x2  y3*x3
  
  </pre>
  <p>
  3. Convolve an image with the full 2D kernel and with the the equivalent 
  1D kernels xkernel and ykernel and compare the results.
  </p>
  <pre>
      cl&gt; convolve m92 m92.1 kernel
  
      cl&gt; convolve m92 m92.2 xkernel ykernel bilinear+
  
      cl&gt; imarith m92.1 - m92.2 diff
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Time requirements</h3>
  <!-- BeginSection: 'TIME REQUIREMENTS' -->
  <p>
  CONVOLVE requires approximately 30 and 8 cpu seconds to convolve a
  512 square real image with 17 by 17 radially symmetric convolution kernel
  using the full 2D and bilinear kernels (if appropriate) respectively
  on a Sparc Station 1.
  </p>
  <!-- EndSection:   'TIME REQUIREMENTS' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  gauss, laplace, gradient, boxcar
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  -->
  
