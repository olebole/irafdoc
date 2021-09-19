.. _mode:

mode: Modal box filter a list of 1D or 2D images
================================================

**Package: imfilter**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  mode -- modal filter a list of images
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  mode input output xwindow ywindow
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input' -->
  <dd>List of input images.
  </dd>
  </dl>
  <dl>
  <dt><b>output</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='output' Line='output' -->
  <dd>List of filtered images. The number of input images must be the same as
  the number of output images. If the input image name is the same as the
  output image name the original image is replaced by the filtered image.
  </dd>
  </dl>
  <dl>
  <dt><b>xwindow, ywindow</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='xwindow' Line='xwindow, ywindow' -->
  <dd>The size of the modal filter. Xwindow and ywindow are assumed to be
  odd integers. Even values will be rounded up to the nearest odd integer.
  </dd>
  </dl>
  <dl>
  <dt><b>zloreject = INDEF, zhireject = INDEF</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='zloreject' Line='zloreject = INDEF, zhireject = INDEF' -->
  <dd>The minimum and maximum good data values. Zloreject and zhireject default
  to -MAX_REAL and MAX_REAL respectively.
  </dd>
  </dl>
  <dl>
  <dt><b>boundary = <tt>"nearest"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='boundary' Line='boundary = "nearest"' -->
  <dd>The type of boundary extension. The options are:
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
  <dd>Reflect pixel values around the boundary.
  </dd>
  </dl>
  <dl>
  <dt><b>wrap</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='wrap' Line='wrap' -->
  <dd>Wrap pixel values around the boundary.
  </dd>
  </dl>
  </dd>
  </dl>
  <dl>
  <dt><b>constant = 0.</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='constant' Line='constant = 0.' -->
  <dd>The value for constant value boundary extension.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  MODE takes a list of input images <i>input</i> and produces a set of filtered
  output images <i>output</i>. The modal filter consists of a sliding
  rectangular window  of dimensions <i>xwindow</i>
  by <i>ywindow</i>. The center pixel of the window is replaced by the mode
  of all the pixels in the window where the mode of a sequence of numbers
  is defined below.
  </p>
  <pre>
  		mode = 3. * median - 2. * mean
  </pre>
  <p>
  The median of a sequence of pixels is defined as the value of the
  (n + 1) / 2 number in the ordered sequence.
  Out of bounds pixel references are handled by setting the parameter
  <i>boundary</i>.
  </p>
  <p>
  The <i>zloreject</i> and <i>zhireject</i> parameters may be used to reject
  bad data from the modal filtering box.  If no good 
  data is left in the filtering box, then the mode is set to zloreject
  if the majority of the pixels are less than zloreject, or to zhireject
  if the majority of pixels are greater than zhireject.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>References</h3>
  <!-- BeginSection: 'REFERENCES' -->
  <p>
  A derivation of the expression for the mode used here can be found in
  <tt>"Statistics in Theory and Practice"</tt>, Robert Lupton, 1993, Princeton
  University Press, problem 2.
  </p>
  <!-- EndSection:   'REFERENCES' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Modal filter an image using a 5 by 5 window and nearest pixel boundary
  extension.
  </p>
  <pre>
     im&gt; mode m74 m74.5by5 5 5
  </pre>
  <p>
  2. Modal filter an image using a 3 by 3 window and constant boundary
  extension.
  </p>
  <pre>
     im&gt; mode m74 m74.5by5 3 3 boun=const const=0.
  </pre>
  <p>
  3. Modal filter the test image, rejecting pixels &lt; 5 and &gt; 19935 from the
  modal filter.
  </p>
  <pre>
      im&gt; mode dev$pix pix77 7 7 zlo=5 zhi=19935
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Time requirements</h3>
  <!-- BeginSection: 'TIME REQUIREMENTS' -->
  <p>
  Mode requires approximately 11 and 19 CPU seconds to filter a 512 by
  512 integer image using a 5 by 5 and 7 by 7 filter window respectively
  (SPARCStation2).
  </p>
  <!-- EndSection:   'TIME REQUIREMENTS' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  The sort routine for the smaller kernels has been optimized. It may be
  desirable to optimize higher order kernels in future.
  </p>
  <p>
  The IRAF task FMODE is significantly more efficient than MODE
  and should be used if the data can be quantized.
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  fmode, rmode, frmode
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'REFERENCES' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  -->
  
