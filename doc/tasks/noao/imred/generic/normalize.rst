.. _normalize:

normalize: Normalize images
===========================

**Package: generic**

.. raw:: html

  <h3>Usage	</h3>
  <!-- BeginSection: 'USAGE	' -->
  <p>
  normalize images
  </p>
  <!-- EndSection:   'USAGE	' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>images</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='images' Line='images' -->
  <dd>Images to be normalized.
  </dd>
  </dl>
  <dl>
  <dt><b>norm = INDEF</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='norm' Line='norm = INDEF' -->
  <dd>Normalization factor to be used if not INDEF.  If INDEF the normalization
  factor is determined by sampling the images.
  </dd>
  </dl>
  <dl>
  <dt><b>sample_section = <span style="font-family: monospace;">"[]"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='sample_section' Line='sample_section = "[]"' -->
  <dd>Section of the image to be sampled in determining the image mean.
  </dd>
  </dl>
  <dl>
  <dt><b>lower = INDEF</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='lower' Line='lower = INDEF' -->
  <dd>Lower limit of pixel values for calculating the normalization.
  INDEF corresponds to the minimum possible pixel value.
  </dd>
  </dl>
  <dl>
  <dt><b>upper = INDEF</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='upper' Line='upper = INDEF' -->
  <dd>Upper limit of pixel values for calculating the normalization.
  INDEF corresponds to the maximum possible pixel value.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  Each of the images is normalized.  The normalization is specified by the
  parameter <i>norm</i>.  If the value of <i>norm</i> is INDEF then a normalization
  is determined by sampling the image.  The normalization is then the mean
  of the pixels in the sample section with values in the range <i>lower</i>
  to <i>upper</i>.  The default sample section selects all pixels in the image.
  The normalized images are of datatype <span style="font-family: monospace;">"real"</span> and replace the original images.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  To normalize a set of two dimensional images excluding deviant pixels below
  1000 and above 5000 and subsampling every fifth pixel in each dimension:
  </p>
  <p>
  	cl&gt; normalize frame* sample=[*:5,*:5] low=1000 up=5000
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  imstatistics, normflat
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
