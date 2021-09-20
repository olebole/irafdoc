.. _background:

background: Fit and subtract a line or column background
========================================================

**Package: kpnocoude**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  background -- Fit and subtract a line or column background
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage	</h3>
  <!-- BeginSection: 'USAGE	' -->
  <p>
  background input output
  </p>
  <!-- EndSection:   'USAGE	' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input' -->
  <dd>Images to be background subtracted.  The images may contain image sections.
  </dd>
  </dl>
  <dl>
  <dt><b>output</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='output' Line='output' -->
  <dd>Output images to be created and modified.  The number of output images must
  match the number of input images.
  </dd>
  </dl>
  <dl>
  <dt><b>axis = 1</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='axis' Line='axis = 1' -->
  <dd>Axis along which to fit the background and subtract.  Axis 1 fits and
  subtracts the background along the lines and axis 2 fits and subtracts
  the background along the columns.
  </dd>
  </dl>
  <dl>
  <dt><b>interactive = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = yes' -->
  <dd>Set the fitting parameters interactively?
  </dd>
  </dl>
  <dl>
  <dt><b>sample = <span style="font-family: monospace;">"*"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='sample' Line='sample = "*"' -->
  <dd>Lines or columns to be used in the background fits.  The default <span style="font-family: monospace;">"*"</span> selects
  all lines or columns.
  </dd>
  </dl>
  <dl>
  <dt><b>naverage = 1</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='naverage' Line='naverage = 1' -->
  <dd>Number of sample points to combined to create a fitting point.
  A positive value specifies an average and a negative value specifies
  a median.
  </dd>
  </dl>
  <dl>
  <dt><b>function = spline3</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='function' Line='function = spline3' -->
  <dd>Function to be fit to the image lines or columns.  The functions are
  <span style="font-family: monospace;">"legendre"</span> (legendre polynomial), <span style="font-family: monospace;">"chebyshev"</span> (chebyshev polynomial),
  <span style="font-family: monospace;">"spline1"</span> (linear spline), and <span style="font-family: monospace;">"spline3"</span> (cubic spline).  The functions
  may be abbreviated.
  </dd>
  </dl>
  <dl>
  <dt><b>order = 1</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='order' Line='order = 1' -->
  <dd>The order of the polynomials or the number of spline pieces.
  </dd>
  </dl>
  <dl>
  <dt><b>low_reject = 0., high_reject = 0.</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='low_reject' Line='low_reject = 0., high_reject = 0.' -->
  <dd>Low and high rejection limits in units of the residual sigma.
  </dd>
  </dl>
  <dl>
  <dt><b>niterate = 1</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='niterate' Line='niterate = 1' -->
  <dd>Number of rejection iterations.
  </dd>
  </dl>
  <dl>
  <dt><b>grow = 1.</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='grow' Line='grow = 1.' -->
  <dd>When a pixel is rejected, pixels within this distance of the rejected pixel
  are also rejected.
  </dd>
  </dl>
  <dl>
  <dt><b>graphics = <span style="font-family: monospace;">"stdgraph"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = "stdgraph"' -->
  <dd>Graphics device for interactive graphics output.
  </dd>
  </dl>
  <dl>
  <dt><b>cursor = <span style="font-family: monospace;">""</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='cursor' Line='cursor = ""' -->
  <dd>Graphics cursor input
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  For each line or column in the input images a function is fit to the columns
  or lines specified by the sample parameter.  This function is then subtracted
  from the entire line or column to create an output line or column.
  The function fitting parameters may be set interactively.
  This task is a script using <b>fit1d</b>.  For more discussion about
  the parameters see the help text for <b>icfit</b> and <b>fit1d</b>.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  A spectrum of an object runs down the center of a 500 x 500 image.  To
  subtract a constant background using columns 10 to 100 and 410 to 500:
  </p>
  <p>
  	cl&gt; background image image sample=<span style="font-family: monospace;">"10:100,410:500"</span>
  </p>
  <p>
  To subtract a quadratic background from the columns of an image in which
  the spectrum lies between lines 50 and 70:
  </p>
  <p>
  	cl&gt; background image image axis=2 sample=<span style="font-family: monospace;">"1:40,80:120"</span> o=3
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  fit1d, icfit
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
