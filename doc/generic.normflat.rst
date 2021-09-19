.. _normflat:

normflat: Create a flat field by normalizing and replacing low values
=====================================================================

**Package: generic**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  normflat -- Create a flat field by normalizing a calibration image
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage	</h3>
  <!-- BeginSection: 'USAGE	' -->
  <p>
  normflat image flatfield
  </p>
  <!-- EndSection:   'USAGE	' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>image</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='image' Line='image' -->
  <dd>Calibration image to be used.
  </dd>
  </dl>
  <dl>
  <dt><b>flatfield</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='flatfield' Line='flatfield' -->
  <dd>Flat field to be created.
  </dd>
  </dl>
  <dl>
  <dt><b>norm = INDEF</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='norm' Line='norm = INDEF' -->
  <dd>Normalization factor to be used if not INDEF.  If INDEF the normalization
  factor is automatically determined.
  </dd>
  </dl>
  <dl>
  <dt><b>minflat = INDEF</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='minflat' Line='minflat = INDEF' -->
  <dd>Minimum data value to be used in determining the normalization and in
  creating the flat field.  Values less than or equal to this value are
  replaced with a flat field value of 1.
  </dd>
  </dl>
  <dl>
  <dt><b>sample_section = <tt>"[]"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='sample_section' Line='sample_section = "[]"' -->
  <dd>Section of the image to be sampled in determining the normalization if
  norm = INDEF.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  A flat field is created from a calibration image by normalizing the calibration
  image.  The normalization is specified with the parameter <i>norm</i>.  If the
  value of <i>norm</i> is INDEF then the normalization is determined by sampling
  the pixels in the sample section with values greater than <i>minflat</i>.
  This task differs from the task <b>normalize</b> in that data values less
  than or equal to <i>minflat</i> are replaced with unity in the normalized
  flat field.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  To create a flat field from a calibration image <tt>"quartz"</tt> using pixels
  above 1000 and selecting the normalization to be 3500:
  </p>
  <p>
  	cl&gt; normflat quartz flat norm=3500 minflat=1000
  </p>
  <p>
  To determine a normalization from the pixels above 1000 and sampling
  every fifth pixel in each dimension:
  </p>
  <pre>
  	cl&gt; normflat quartz flat minflat=1000 sample=[*:5,*:5]
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  normalize
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
