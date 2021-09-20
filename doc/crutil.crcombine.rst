.. _crcombine:

crcombine: Combine multiple exposures to eliminate cosmic rays
==============================================================

**Package: crutil**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  crcombine -- combine multiple exposures to eliminate cosmic rays
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage	</h3>
  <!-- BeginSection: 'USAGE	' -->
  <pre>
  crcombine input output
  </pre>
  <!-- EndSection:   'USAGE	' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <p>
  See parameters for <b>imcombine</b>.
  </p>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  This task is a version of <b>imcombine</b>.  See the help for that task
  for a description of the parameters and algorithms.
  </p>
  <p>
  For the purpose of removing cosmic rays the most useful options
  are the <span style="font-family: monospace;">"crreject"</span> algorithm and/or combining with a median.  Many other
  options may work as well.  The best use of this task depends on the
  number of images available.  If there are more than a few images the
  images should be combined with an <span style="font-family: monospace;">"average"</span> and using a rejection
  algorithm.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1.  To combine two images using the gain and read noise parameters in
  the image header:
  </p>
  <pre>
      cl&gt; crcombine obj012,obj013 abc gain=gain rdnoise=rdnoise 
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  imcombine
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
