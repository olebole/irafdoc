.. _colbias:

colbias: Fit and subtract an average column bias
================================================

**Package: bias**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  colbias -- Fit and subtract an average column bias
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage	</h3>
  <!-- BeginSection: 'USAGE	' -->
  <pre>
  colbias input output
  </pre>
  <!-- EndSection:   'USAGE	' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input' -->
  <dd>Images to be bias subtracted.  The images may not contain image sections.
  </dd>
  </dl>
  <dl>
  <dt><b>output</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='output' Line='output' -->
  <dd>Output bias subtracted images.  An output images may be the same as its
  matching input image.  The output pixel type will be real regardless
  of the input pixel type.
  </dd>
  </dl>
  <dl>
  <dt><b>bias = <tt>"[]"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='bias' Line='bias = "[]"' -->
  <dd>Bias section appended to the input image to define the bias region.
  The default section or an empty string will use the full image.
  </dd>
  </dl>
  <dl>
  <dt><b>trim = <tt>"[]"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='trim' Line='trim = "[]"' -->
  <dd>Trim section appended to the input image to define the region to be
  bias subtracted and output.  The default section or an empty string
  will use the full image.
  </dd>
  </dl>
  <dl>
  <dt><b>median = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='median' Line='median = no' -->
  <dd>Take the median of the bias columns?  If no then the bias
  columns are averaged.
  </dd>
  </dl>
  <dl>
  <dt><b>function = <tt>"spline3"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='function' Line='function = "spline3"' -->
  <dd>The function fit to the average bias line.  The functions are <tt>"legendre"</tt>,
  <tt>"chebyshev"</tt>, <tt>"spline1"</tt>, or <tt>"spline3"</tt>.  Abbreviations are allowed.
  </dd>
  </dl>
  <dl>
  <dt><b>order</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='order' Line='order' -->
  <dd>The order (number of terms or number of spline pieces) in the function.
  </dd>
  </dl>
  <dl>
  <dt><b>low_reject = 3.0</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='low_reject' Line='low_reject = 3.0' -->
  <dd>The low sigma rejection factor.
  </dd>
  </dl>
  <dl>
  <dt><b>high_reject = 3.0</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='high_reject' Line='high_reject = 3.0' -->
  <dd>The high sigma rejection factor.
  </dd>
  </dl>
  <dl>
  <dt><b>niterate = 1</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='niterate' Line='niterate = 1' -->
  <dd>The maximum number of rejection iterations.
  </dd>
  </dl>
  <dl>
  <dt><b>interactive = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = yes' -->
  <dd>Fit the average bias line interactively?
  </dd>
  </dl>
  <dl>
  <dt><b>logfiles = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='logfiles' Line='logfiles = ""' -->
  <dd>List of log files.  If no file name is given then no log file is kept.
  </dd>
  </dl>
  <dl>
  <dt><b>graphics = <tt>"stdgraph"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = "stdgraph"' -->
  <dd>Graphics output device for interactive graphics.
  </dd>
  </dl>
  <dl>
  <dt><b>cursor = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='cursor' Line='cursor = ""' -->
  <dd>Graphics cursor input
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  For each input image in the input image list an average or median bias
  column is determined from the bias region.  The bias region is defined by
  the bias section applied to the input image.  A function of the image lines
  is fit to the average bias column.  This function is subtracted from each
  image column in the trim region.  The trim region is defined by the trim
  section applied to the input image.  The bias subtracted and trimmed image
  is output to the output image.  The input and output images may not contain
  sections and the number of images in each list must be the same.
  </p>
  <p>
  If the interactive flag is set then the user may interactively examine
  and fit the average bias column.  The interactive fitting is done using the
  interactive curve fitting routine (see icfit).  Before each image is
  processed a prompt of the form <tt>"colbias image (yes)? "</tt> is given.
  A response of yes allows interactive fitting for the specified image
  while a response of no uses the last defined fitting parameters.
  The default value is accepted with a carriage return.  The possible
  responses are <tt>"yes"</tt>, <tt>"no"</tt>, <tt>"YES"</tt>, or <tt>"NO"</tt>.  The capitalized responses
  permanently set the response to yes or no and the prompt is not
  issued again for the remaining images.  Thus, a response of NO processes
  the remaining images non-interactively while a response of YES processes
  the remaining image interactively without prompting.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  The bias region for a set of images occupies columns 801 to 832 and lines
  1 to 800.  To subtract the bias and remove the bias region:
  </p>
  <pre>
  	cl&gt; colbias.bias = "[801:832,*]"
  	cl&gt; colbias.trim = "[1:800,*]"
  	cl&gt; colbias ccd* ccd*
  	colbias ccd001 (yes)? yes
  	colbias ccd002 (yes)?
  	colbias ccd003 (no)? NO
  </pre>
  <p>
  The first two lines set the bias and trim parameters.  These parameters
  could be temporarily set on the command line but generally these parameters
  are only changed when new instruments are used.  The first image
  is interactively fit and the fitting order is change to 2.  The
  second image is examined and the fit found to be acceptable.  All remaining
  image are then fit non-interactively using the same fitting parameters.
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Revisions</h3>
  <!-- BeginSection: 'REVISIONS' -->
  <dl>
  <dt><b>COLBIAS V2.10.3</b></dt>
  <!-- Sec='REVISIONS' Level=0 Label='COLBIAS' Line='COLBIAS V2.10.3' -->
  <dd>The output pixel type is now real instead of preserving the pixel type
  of the input image.
  </dd>
  </dl>
  <!-- EndSection:   'REVISIONS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  icfit
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  -->
  
