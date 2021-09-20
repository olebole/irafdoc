.. _crgrow:

crgrow: Grow cosmic rays in cosmic ray masks
============================================

**Package: crutil**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  crgrow -- grow cosmic rays in cosmic ray masks
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage	</h3>
  <!-- BeginSection: 'USAGE	' -->
  <p>
  crgrow input output radius
  </p>
  <!-- EndSection:   'USAGE	' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input' -->
  <dd>List of cosmic ray masks to be modified.
  </dd>
  </dl>
  <dl>
  <dt><b>output</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='output' Line='output' -->
  <dd>List of output modified cosmic ray masks.  The input and output lists must
  match.  If the input and output cosmic ray masks are specified as the same
  then the input mask will be modified in place.
  </dd>
  </dl>
  <dl>
  <dt><b>radius = 1.</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='radius' Line='radius = 1.' -->
  <dd>Replacement radius around cosmic rays.
  If a pixel is within this distance of a cosmic ray pixel
  it is identified by a value of 1 in the output cosmic ray mask.  Distances are
  measured between pixel centers which are have integer coordinates.
  </dd>
  </dl>
  <dl>
  <dt><b>inval = INDEF</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='inval' Line='inval = INDEF' -->
  <dd>Mask value to be grown.  A value of INDEF will grow all non-zero values.
  </dd>
  </dl>
  <dl>
  <dt><b>outval = INDEF</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='outval' Line='outval = INDEF' -->
  <dd>Mask value for grown pixels.  A value of INDEF will use the value of the
  pixel being grown for the grown pixel value.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The cosmic ray pixels, identified by the <span style="font-family: monospace;">"inval"</span> parameter, in the input
  mask are located and all unmasked (zero valued) pixels within the specified
  grow radius are set to a value given by the <span style="font-family: monospace;">"outval"</span> parameter. The
  distance between pixels is measured as a cartisian logical pixel coordinate
  distance.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1.  A radius of 1 will grow cosmic rays in a <span style="font-family: monospace;">"plus"</span> pattern.
  </p>
  <pre>
      cl&gt; crgrow crmask1 crmask2 1
  </pre>
  <p>
  2.  A radius of 1.5 will grow cosmic rays in a box pattern.  The following
  will modify the input mask.
  </p>
  <pre>
      cl&gt; crgrow crmask crmask 1.5
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  imreplace
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
