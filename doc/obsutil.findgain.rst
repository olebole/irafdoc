.. _findgain:

findgain: Estimate the gain and readnoise of a CCD
==================================================

**Package: obsutil**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  findgain -- calculate the gain and readout noise of a CCD
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Synopsis</h3>
  <!-- BeginSection: 'SYNOPSIS' -->
  <p>
  FINDGAIN uses Janesick's method for determining the gain and read noise
  in a CCD from a pair of dome flat exposures and a pair of zero frame
  exposures (zero length dark exposures).
  </p>
  <!-- EndSection:   'SYNOPSIS' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  findgain flat1 flat2 zero1 zero2
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>flat1, flat2</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='flat1' Line='flat1, flat2' -->
  <dd>First and second dome flats.
  </dd>
  </dl>
  <dl>
  <dt><b>zero1, zero2</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='zero1' Line='zero1, zero2' -->
  <dd>First and second zero frames (zero length dark exposures).
  </dd>
  </dl>
  <dl>
  <dt><b>section = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='section' Line='section = ""' -->
  <dd>The selected image section for the statistics.  This should be chosen
  to exclude bad columns or rows, cosmic rays and other blemishes, and
  the overscan region.  The flat field iillumination should be constant
  over this section.
  </dd>
  </dl>
  <dl>
  <dt><b>center = <tt>"mean"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='center' Line='center = "mean"' -->
  <dd>The statistical measure of central tendency that is used to estimate
  the data level of each image.  This can have the values:  <b>mean</b>,
  <b>midpt</b>, or <b>mode</b>.  These are calculated using the same
  algorithm as the IMSTATISTICS task.
  </dd>
  </dl>
  <dl>
  <dt><b>nclip = 3</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='nclip' Line='nclip = 3' -->
  <dd>Number of sigma clipping iterations.  If the value is zero then no clipping
  is performed.
  </dd>
  </dl>
  <dl>
  <dt><b>lsigma = 4, usigma = 4</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='lsigma' Line='lsigma = 4, usigma = 4' -->
  <dd>Lower and upper sigma clipping factors used with the mean value and
  standard deviation to eliminate cosmic rays.
  Since <b>findgain</b> is sensitive to the statistics of the data the
  clipping factors should be symmetric (the same both above and below the
  mean) and should not bias the standard deviation.  Thus the values should
  not be made smaller than around 4 sigma otherwise the gain and readnoise
  estimates will be affected.
  </dd>
  </dl>
  <dl>
  <dt><b>binwidth = 0.1</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='binwidth' Line='binwidth = 0.1' -->
  <dd>The bin width of the histogram (in sigma) that is used to estimate the
  <b>midpt</b> or <b>mode</b> of the data section in each image.
  The default case of center=<b>mean</b> does not use this parameter.
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes' -->
  <dd>Verbose output?
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  FINDGAIN uses Janesick's method for determining the gain and read noise
  in a CCD from a pair of dome flat exposures and a pair of zero frame
  exposures (zero length dark exposures).
  The task requires that the flats and zeros be unprocessed and uncoadded so
  that the noise characteristics of the data are preserved.  Note, however,
  that the frames may be bias subtracted if the average of many zero frames
  is used, and that the overscan region may be removed prior to using this
  task.
  </p>
  <p>
  Bad pixels should be eliminated to avoid affecting the statistics.
  This can be done with sigma clipping and/or an image section.
  The sigma clipping should not significantly affect the assumed gaussian
  distribution while eliminating outlyers due to cosmic rays and
  unmasked bad pixels.  This means that clipping factors should be
  symmetric and should have values four or more sigma from the mean.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Algorithm</h3>
  <!-- BeginSection: 'ALGORITHM' -->
  <p>
  The formulae used by the task are:
  </p>
  <pre>
      flatdif = flat1 - flat2
  
      zerodif = zero1 - zero2
  
         gain = ((mean(flat1) + mean(flat2)) - (mean(zero1) + mean(zero2))) /
  	      ((sigma(flatdif))**2 - (sigma(zerodif))**2 )
  
     readnoise = gain * sigma(zerodif) / sqrt(2)
  </pre>
  <p>
  where the gain is given in electrons per ADU and the readnoise in
  electrons.  Pairs of each type of comparison frame are used to reduce
  the effects of gain variations from pixel to pixel.  The derivation
  follows from the definition of the gain (N(e) = gain * N(ADU)) and from
  simple error propagation.  Also note that the measured variance
  (sigma**2) is related to the exposure level and read-noise variance
  (sigma(readout)**2) as follows:
  </p>
  <pre>
       variance(e) = N(e) + variance(readout)
  </pre>
  <p>
  Where N(e) is the number of electrons (above the zero level) in a
  given duration exposure.
  </p>
  <p>
  In our implementation, the <b>mean</b> used in the formula for the gain
  may actually be any of the <b>mean</b>, <b>midpt</b> (an estimate of the
  median), or <b>mode</b> as determined by the <b>center</b> parameter.
  For the <b>midpt</b> or <b>mode</b> choices only, the value of the
  <b>binwidth</b> parameter determines the bin width (in sigma) of the
  histogram that is used in the calculation.  <b>Findgain</b> uses the
  <b>imstatistics</b> task to compute the statistics.
  </p>
  <!-- EndSection:   'ALGORITHM' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  To calculate the gain and readnoise within a 100x100 section:
  </p>
  <pre>
      ms&gt; findgain flat1 flat2 zero1 zero2 section="[271:370,361:460]"
  </pre>
  <p>
  To calculate the gain and readnoise using the mode to estimate the data
  level for each image section:
  </p>
  <pre>
      ms&gt; findgain.section="[271:370,361:460]"
      ms&gt; findgain flat1 flat2 zero1 zero2 center=mode
  </pre>
  <p>
  The effects of cosmic rays can be seen in the following example using
  artificial noise created with the <b>artdata.mknoise</b> package.  The
  images have a gain of 5 and a readnoise of 10 with 100 cosmic rays added
  over the 512x512 images.  The zero level images have means of zero and the
  flat field images have means of 1000.  The first execution uses the default
  clipping and the second turns off the clipping.
  </p>
  <pre>
      cl&gt; findgain flat1 flat2 zero1 zero2
      FINDGAIN:
        center = mean, binwidth = 0.1
        nclip = 3, lclip = 4., uclip = 4.
  
        Flats      = flat1 &amp;  flat2
        Zeros      = zero1 &amp;  zero2
        Gain       =  5.01 electrons per ADU
        Read noise = 10.00 electrons
      cl&gt; findgain flat1 flat2 zero1 zero2 nclip=0
      FINDGAIN:
        center = mean, binwidth = 0.1
        nclip = 0, lclip = 4., uclip = 4.
  
        Flats      = flat1  &amp;  flat2
        Zeros      = zero1  &amp;  zero2
        Gain       =  2.86 electrons per ADU
        Read noise = 189.5 electrons
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  The image headers are not checked to see if the frames have been
  processed.
  </p>
  <p>
  There is no provision for finding the <tt>"best"</tt> values and their errors
  from several flats and zeros.
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>Revisions</h3>
  <!-- BeginSection: 'REVISIONS' -->
  <dl>
  <dt><b>FINDGAIN - V2.12</b></dt>
  <!-- Sec='REVISIONS' Level=0 Label='FINDGAIN' Line='FINDGAIN - V2.12' -->
  <dd>New task derived from MSCFINDGAIN.  This makes use of the new clipping
  feature in IMSTATISTICS.
  </dd>
  </dl>
  <!-- EndSection:   'REVISIONS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  imstatistics
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'SYNOPSIS' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'ALGORITHM' 'EXAMPLES' 'BUGS' 'REVISIONS' 'SEE ALSO'  -->
  
