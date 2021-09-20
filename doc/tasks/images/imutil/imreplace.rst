.. _imreplace:

imreplace: Replace a range of pixel values with a constant
==========================================================

**Package: imutil**

.. raw:: html

  <h3>Usage	</h3>
  <!-- BeginSection: 'USAGE	' -->
  <p>
  imreplace images value lower upper
  </p>
  <!-- EndSection:   'USAGE	' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>images</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='images' Line='images' -->
  <dd>Images in which the pixels are to be replaced.
  </dd>
  </dl>
  <dl>
  <dt><b>value</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='value' Line='value' -->
  <dd>Replacement value for pixels in the window.
  </dd>
  </dl>
  <dl>
  <dt><b>imaginary = 0.</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='imaginary' Line='imaginary = 0.' -->
  <dd>Replacement value for pixels in the windoe for the imaginary part of
  complex data.
  </dd>
  </dl>
  <dl>
  <dt><b>lower = INDEF</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='lower' Line='lower = INDEF' -->
  <dd>Lower limit of window for replacing pixels.  If INDEF then all pixels
  are above <i>lower</i>.  For complex images this is the magnitude
  of the pixel values.  For integer images the value is rounded up
  to the next higher integer.
  </dd>
  </dl>
  <dl>
  <dt><b>upper = INDEF</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='upper' Line='upper = INDEF' -->
  <dd>Upper limit of window for replacing pixels.  If INDEF then all pixels
  are below <i>upper</i>.  For complex images this is the magnitude
  of the pixel values.  For integer images the value is rounded down
  to the next lower integer.
  </dd>
  </dl>
  <dl>
  <dt><b>radius = 0.</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='radius' Line='radius = 0.' -->
  <dd>Additional replacement radius around pixels which are in the replacement
  window.  If a pixel is within this distance of a pixel within the replacement
  window it is also replaced with the replacement value.  Distances are
  measured between pixel centers which are have integer coordinates.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The pixels in the <i>images</i> between <i>lower</i> and <i>upper</i>,
  and all other pixels with a distance given by <i>radius</i>,
  are replaced by the constant <i>value</i>.  The special value INDEF in
  <i>lower</i> and <i>upper</i> corresponds to the minimum and maximum
  possible pixel values, respectively.
  </p>
  <p>
  For complex images the replacement value is specified as separate
  real and imaginary and the thresholds are the magnitude.  For
  integer images the thresholds are used as inclusive limits
  so that, for example, the range 5.1-9.9 affets pixels 6-9.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. In a flat field calibration which has been scaled to unit mean replace
  all response values less than or equal to 0.8 by 1.
  </p>
  <p>
      cl&gt; imreplace calib 1 upper=.8
  </p>
  <p>
  2. Set all pixels to zero within a section of an image.
  </p>
  <p>
      cl&gt; imreplace image[1:10,5:100] 0
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Revisions</h3>
  <!-- BeginSection: 'REVISIONS' -->
  <dl>
  <dt><b>IMREPLACE V2.11.1</b></dt>
  <!-- Sec='REVISIONS' Level=0 Label='IMREPLACE' Line='IMREPLACE V2.11.1' -->
  <dd>A replacement radius to replace additional pixels was added.
  </dd>
  </dl>
  <dl>
  <dt><b>IMREPLACE V2.11</b></dt>
  <!-- Sec='REVISIONS' Level=0 Label='IMREPLACE' Line='IMREPLACE V2.11' -->
  <dd>The lower value is now rounded up for integer images so that a range
  like 5.1-9.9 affects pixels 6-9 instead of 5-9.
  </dd>
  </dl>
  <!-- EndSection:   'REVISIONS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  imexpr
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  -->
  
