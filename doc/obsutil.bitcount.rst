.. _bitcount:

bitcount: Accumulate the bit statistics for a list of images
============================================================

**Package: obsutil**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  bitcount - accumulate the bit statistics for a list of images
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  bitcount images
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>images</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='images' Line='images' -->
  <dd>A list of image names whose bit statistics will be counted.  The
  statistics can either be reported for each individual image (the
  default) or as a grand total over all the images.
  </dd>
  </dl>
  <dl>
  <dt><b>grandtotal = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='grandtotal' Line='grandtotal = no' -->
  <dd>If <i>grandtotal</i> = yes, accumulate a grand total over all the
  images.  If <i>grandtotal</i> = no (the default), report the statistics
  individually for each image in turn.
  </dd>
  </dl>
  <dl>
  <dt><b>leftzeroes = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='leftzeroes' Line='leftzeroes = yes' -->
  <dd>If <i>leftzeroes</i> = yes, leftmost zeroes are counted into the
  statistics (the default).  If <i>leftzeroes</i> = no, leftmost zeroes
  (those past the most significant digit for each individual pixel)
  are omitted from the statistics.
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes' -->
  <dd>If <i>verbose</i> = no, only the raw bit counts will be reported.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  <i>Bitcount</i> will report the absolute and relative proportions
  of zeroes and ones populating each bit plane of a list of images.
  This is useful for diagnosing problems with a CCD's A/D converter,
  especially when an input image is supplied that contains a linear
  ramp in exposure across the range of the A/D.
  </p>
  <p>
  The statistics for the list of images can be accumulated either
  individually for each image, or as a grand total over all of the
  images depending on the value of the <i>grandtotal</i> parameter.
  A single linear exposure ramp can be mimiced by a grand total
  over a list of progressively more exposed images.  Care should
  be taken to arrange that the exposures sample all parts of the
  A/D's range.
  </p>
  <p>
  The <i>leftzeroes</i> parameter is used to correct a problem seen
  with the ctio.bitstat task.  Bitstat under-reports zeroes for the
  more significant bits since only pixels with values greater than
  the bit being currently counted participate in that count.  The
  severity and precise nature of this problem depends on the exposure
  level of a particular test image.  <i>Leftzeroes</i> may be set to
  <span style="font-family: monospace;">"no"</span> if there is some reason to restore this behavior.
  </p>
  <p>
  The <i>verbose</i> parameter may be set to <span style="font-family: monospace;">"no"</span> in order to pass
  the raw bit counts on to some other task.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  To report the bit statistics for a test exposure ramp:
  </p>
  <pre>
      nl&gt; bitcount testramp
  </pre>
  <p>
  To accumulate a grand total over a list of images:
  </p>
  <pre>
      nl&gt; bitcount a001*.imh grandtotal+
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  A warning will be issued when accumulating a grand total over a list
  of images whose datatypes vary.  In this case, the totals for each bit
  will be correct - to the extent that some images may not populate some
  bits - but the datatype of the final image in the list will control the
  range of bitplanes included in the output report.  The interpretation
  of the most significant bit as a sign bit will also depend on the
  datatype of this final image.
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  imstatistics, ctio.bitstat
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  -->
  
