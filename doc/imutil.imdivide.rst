.. _imdivide:

imdivide: Image division with zero checking and rescaling
=========================================================

**Package: imutil**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  imdivide -- image division with zero checking and rescaling
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage	</h3>
  <!-- BeginSection: 'USAGE	' -->
  <p>
  imdivide numerator denominator resultant
  </p>
  <!-- EndSection:   'USAGE	' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>numerator</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='numerator' Line='numerator' -->
  <dd>Numerator image.
  </dd>
  </dl>
  <dl>
  <dt><b>denominator</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='denominator' Line='denominator' -->
  <dd>Denominator image.
  </dd>
  </dl>
  <dl>
  <dt><b>resultant</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='resultant' Line='resultant' -->
  <dd>Resultant image.  This image will be of datatype real.
  </dd>
  </dl>
  <dl>
  <dt><b>title = <span style="font-family: monospace;">'*'</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='title' Line='title = '*'' -->
  <dd>Title for resultant image.  The special character <span style="font-family: monospace;">'*'</span> defaults the title
  to that of the numerator image.
  </dd>
  </dl>
  <dl>
  <dt><b>constant = 0</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='constant' Line='constant = 0' -->
  <dd>The constant value for the zero division constant option.
  </dd>
  </dl>
  <dl>
  <dt><b>rescale = norescale</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='rescale' Line='rescale = norescale' -->
  <dd>After the image division the resultant image may be rescaled with the following
  options:
  <dl>
  <dt><b>norescale</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='norescale' Line='norescale' -->
  <dd>Do not rescale the resultant image.
  </dd>
  </dl>
  <dl>
  <dt><b>mean</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='mean' Line='mean' -->
  <dd>Scale the resultant image to the specified mean value.
  </dd>
  </dl>
  <dl>
  <dt><b>numerator</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='numerator' Line='numerator' -->
  <dd>Scale the resultant image to have the same mean value as the numerator image.
  </dd>
  </dl>
  </dd>
  </dl>
  <dl>
  <dt><b>mean = 1</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='mean' Line='mean = 1' -->
  <dd>The mean value used rescale the resultant image under 'mean' option of
  <i>rescale</i>.
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no' -->
  <dd>Print the means of each image?
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The <i>numerator</i> image is divided by the <i>denominator</i> image to
  form the <i>resultant</i> image.  The division is checked for division by
  zero and replaces the result with the value of the parameter <i>constant</i>.
  After the division the resultant image may be rescaled.
  The rescaling option is selected with <i>rescale</i>.  The options are
  not to rescale, rescale to the specified <i>mean</i> value, and rescale to
  the mean of the numerator.  The means of the three images are calculated
  and may be printed with the verbose option.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. To divide a object image by a flat field and then rescale the division
  back to the mean of the object image:
  </p>
  <p>
      cl&gt; imdivide object image final rescale=numerator
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  imarith
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
