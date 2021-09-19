.. _quadsplit:

quadsplit: Split quadformat data into individual single amplifier images
========================================================================

**Package: quadred**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  quadsplit -- Split quadformat data into single amplifier images
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  quadsplit input
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input' -->
  <dd>Image name of <i>quadformat</i> image to be split.  This task does not
  allow a list of input names.
  </dd>
  </dl>
  <dl>
  <dt><b>output = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='output' Line='output = ""' -->
  <dd>Output root name to which the AMPLIST amplifier identifiers will be
  appended to form the split images.  If no output name is given then
  the input name is used as the root name.
  </dd>
  </dl>
  <dl>
  <dt><b>clobber = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='clobber' Line='clobber = yes' -->
  <dd>Clobber any existing images?
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  Images in <tt>"quadformat"</tt> (see help topic <b>quadformat</b>) are separated
  into images containing data from only one amplifier.  The output images
  have a common root name and then an extension given by the amplifier
  labels in the AMPLIST keyword.  The output root name may be specified
  or default to the input name.
  </p>
  <p>
  In addition to producing the individual images keywords, are added that
  are understood by the standard <b>ccdproc</b> task for single amplifier
  CCD reductions.
  </p>
  <p>
  The task <b>quadjoin</b> may be used to rejoin images that were split
  by this task.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. To spit an image:
  </p>
  <pre>
      qu&gt; quadsplit quad0072
      qu&gt; dir quad0072*
      quad0072.11.imh     quad0072.21.imh     quad0072.imh        
      quad0072.12.imh     quad0072.22.imh     
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  quadformat, quadjoin
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
