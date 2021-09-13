.. _findgain:

findgain — Estimate the gain and readnoise of a CCD
===================================================

**Package: obsutil**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  findgain -- calculate the gain and readout noise of a CCD
  </UL>
  <! EndSection:   'NAME'>
  <H3>Synopsis</H3>
  <! BeginSection: 'SYNOPSIS'>
  <UL>
  FINDGAIN uses Janesick's method for determining the gain and read noise
  in a CCD from a pair of dome flat exposures and a pair of zero frame
  exposures (zero length dark exposures).
  </UL>
  <! EndSection:   'SYNOPSIS'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  findgain flat1 flat2 zero1 zero2
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>flat1, flat2</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='flat1' Line='flat1, flat2'>
  <DD>First and second dome flats.
  </DD>
  </DL>
  <DL>
  <DT><B>zero1, zero2</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='zero1' Line='zero1, zero2'>
  <DD>First and second zero frames (zero length dark exposures).
  </DD>
  </DL>
  <DL>
  <DT><B>section = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='section' Line='section = ""'>
  <DD>The selected image section for the statistics.  This should be chosen
  to exclude bad columns or rows, cosmic rays and other blemishes, and
  the overscan region.  The flat field iillumination should be constant
  over this section.
  </DD>
  </DL>
  <DL>
  <DT><B>center = "<TT>mean</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='center' Line='center = "mean"'>
  <DD>The statistical measure of central tendency that is used to estimate
  the data level of each image.  This can have the values:  <B>mean</B>,
  <B>midpt</B>, or <B>mode</B>.  These are calculated using the same
  algorithm as the IMSTATISTICS task.
  </DD>
  </DL>
  <DL>
  <DT><B>nclip = 3</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nclip' Line='nclip = 3'>
  <DD>Number of sigma clipping iterations.  If the value is zero then no clipping
  is performed.
  </DD>
  </DL>
  <DL>
  <DT><B>lsigma = 4, usigma = 4</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lsigma' Line='lsigma = 4, usigma = 4'>
  <DD>Lower and upper sigma clipping factors used with the mean value and
  standard deviation to eliminate cosmic rays.
  Since <B>findgain</B> is sensitive to the statistics of the data the
  clipping factors should be symmetric (the same both above and below the
  mean) and should not bias the standard deviation.  Thus the values should
  not be made smaller than around 4 sigma otherwise the gain and readnoise
  estimates will be affected.
  </DD>
  </DL>
  <DL>
  <DT><B>binwidth = 0.1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='binwidth' Line='binwidth = 0.1'>
  <DD>The bin width of the histogram (in sigma) that is used to estimate the
  <B>midpt</B> or <B>mode</B> of the data section in each image.
  The default case of center=<B>mean</B> does not use this parameter.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Verbose output?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  FINDGAIN uses Janesick's method for determining the gain and read noise
  in a CCD from a pair of dome flat exposures and a pair of zero frame
  exposures (zero length dark exposures).
  The task requires that the flats and zeros be unprocessed and uncoadded so
  that the noise characteristics of the data are preserved.  Note, however,
  that the frames may be bias subtracted if the average of many zero frames
  is used, and that the overscan region may be removed prior to using this
  task.
  <P>
  Bad pixels should be eliminated to avoid affecting the statistics.
  This can be done with sigma clipping and/or an image section.
  The sigma clipping should not significantly affect the assumed gaussian
  distribution while eliminating outlyers due to cosmic rays and
  unmasked bad pixels.  This means that clipping factors should be
  symmetric and should have values four or more sigma from the mean.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Algorithm</H3>
  <! BeginSection: 'ALGORITHM'>
  <UL>
  The formulae used by the task are:
  <P>
  <PRE>
      flatdif = flat1 - flat2
  <P>
      zerodif = zero1 - zero2
  <P>
         gain = ((mean(flat1) + mean(flat2)) - (mean(zero1) + mean(zero2))) /
  	      ((sigma(flatdif))**2 - (sigma(zerodif))**2 )
  <P>
     readnoise = gain * sigma(zerodif) / sqrt(2)
  </PRE>
  <P>
  where the gain is given in electrons per ADU and the readnoise in
  electrons.  Pairs of each type of comparison frame are used to reduce
  the effects of gain variations from pixel to pixel.  The derivation
  follows from the definition of the gain (N(e) = gain * N(ADU)) and from
  simple error propagation.  Also note that the measured variance
  (sigma**2) is related to the exposure level and read-noise variance
  (sigma(readout)**2) as follows:
  <P>
  <PRE>
       variance(e) = N(e) + variance(readout)
  </PRE>
  <P>
  Where N(e) is the number of electrons (above the zero level) in a
  given duration exposure.
  <P>
  In our implementation, the <B>mean</B> used in the formula for the gain
  may actually be any of the <B>mean</B>, <B>midpt</B> (an estimate of the
  median), or <B>mode</B> as determined by the <B>center</B> parameter.
  For the <B>midpt</B> or <B>mode</B> choices only, the value of the
  <B>binwidth</B> parameter determines the bin width (in sigma) of the
  histogram that is used in the calculation.  <B>Findgain</B> uses the
  <B>imstatistics</B> task to compute the statistics.
  </UL>
  <! EndSection:   'ALGORITHM'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  To calculate the gain and readnoise within a 100x100 section:
  <P>
  <PRE>
      ms&gt; findgain flat1 flat2 zero1 zero2 section="[271:370,361:460]"
  </PRE>
  <P>
  To calculate the gain and readnoise using the mode to estimate the data
  level for each image section:
  <P>
  <PRE>
      ms&gt; findgain.section="[271:370,361:460]"
      ms&gt; findgain flat1 flat2 zero1 zero2 center=mode
  </PRE>
  <P>
  The effects of cosmic rays can be seen in the following example using
  artificial noise created with the <B>artdata.mknoise</B> package.  The
  images have a gain of 5 and a readnoise of 10 with 100 cosmic rays added
  over the 512x512 images.  The zero level images have means of zero and the
  flat field images have means of 1000.  The first execution uses the default
  clipping and the second turns off the clipping.
  <P>
  <PRE>
      cl&gt; findgain flat1 flat2 zero1 zero2
      FINDGAIN:
        center = mean, binwidth = 0.1
        nclip = 3, lclip = 4., uclip = 4.
  <P>
        Flats      = flat1 &amp;  flat2
        Zeros      = zero1 &amp;  zero2
        Gain       =  5.01 electrons per ADU
        Read noise = 10.00 electrons
      cl&gt; findgain flat1 flat2 zero1 zero2 nclip=0
      FINDGAIN:
        center = mean, binwidth = 0.1
        nclip = 0, lclip = 4., uclip = 4.
  <P>
        Flats      = flat1  &amp;  flat2
        Zeros      = zero1  &amp;  zero2
        Gain       =  2.86 electrons per ADU
        Read noise = 189.5 electrons
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  The image headers are not checked to see if the frames have been
  processed.
  <P>
  There is no provision for finding the "<TT>best</TT>" values and their errors
  from several flats and zeros.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>FINDGAIN - V2.12</B></DT>
  <! Sec='REVISIONS' Level=0 Label='FINDGAIN' Line='FINDGAIN - V2.12'>
  <DD>New task derived from MSCFINDGAIN.  This makes use of the new clipping
  feature in IMSTATISTICS.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imstatistics
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'SYNOPSIS' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'ALGORITHM' 'EXAMPLES' 'BUGS' 'REVISIONS' 'SEE ALSO'  >
  
