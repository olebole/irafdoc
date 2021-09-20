.. _boxcar:

boxcar: Boxcar smooth a list of 1 or 2-D images
===============================================

**Package: imfilter**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  boxcar -- boxcar smooth a list of images
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  boxcar input output xwindow ywindow
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input' -->
  <dd>List of images to be smoothed.
  </dd>
  </dl>
  <dl>
  <dt><b>output</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='output' Line='output' -->
  <dd>List of output images. The number of output images must equal the number of
  input images. If the input images name equals the output image name the
  smoothed image will replace the input image.
  </dd>
  </dl>
  <dl>
  <dt><b>xwindow, ywindow</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='xwindow' Line='xwindow, ywindow' -->
  <dd>The size of the smoothing window.
  </dd>
  </dl>
  <dl>
  <dt><b>boundary = <span style="font-family: monospace;">"nearest"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='boundary' Line='boundary = "nearest"' -->
  <dd>The boundary extension options are:
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
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  BOXCAR smooths the list of images specified by <i>input</i> with a
  flat-topped rectangular kernel of dimensions <i>xwindow</i> by <i>ywindow</i>
  and places the smoothed images in <i>output</i>. The type of boundary
  extension is optional and set by the <i>boundary</i> parameter.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Smooth an image using a 3 by 3 smoothing box and nearest neighbor boundary
     extension.
  </p>
  <pre>
      cl&gt; boxcar m82 m82.box 3 3
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Time requirements</h3>
  <!-- BeginSection: 'TIME REQUIREMENTS' -->
  <p>
  BOXCAR requires approximately 30 cpu seconds to smooth a
  512 square real image with a  5 by 5 kernel (VAX 11/750 with fpa).
  </p>
  <!-- EndSection:   'TIME REQUIREMENTS' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  convolve, gauss, laplace, gradient
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  -->
  
