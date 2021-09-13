.. _shutcor:

shutcor — Shutter correction from images of varying exposure times
==================================================================

**Package: obsutil**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  shutcor -- shutter correction from images of varying exposure
  </UL>
  <! EndSection:   'NAME'>
  <H3>Synopsis</H3>
  <! BeginSection: 'SYNOPSIS'>
  <UL>
  SHUTCOR calculate the shutter correction for a detector given a
  sequence of overscan corrected images of varying durations.  Typically
  these would be flat field exposures.  The shutter correction is the
  intercept on a plot of exposure duration versus exposure level.
  </UL>
  <! EndSection:   'SYNOPSIS'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  shutcor images
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>images</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>List of overscan corrected images.  These would usually be flat
  field exposures.
  </DD>
  </DL>
  <DL>
  <DT><B>section = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='section' Line='section = ""'>
  <DD>The selected image section for the statistics.  This should be chosen
  to exclude bad columns or rows, cosmic rays, and other non-linear
  features.
  </DD>
  </DL>
  <DL>
  <DT><B>center = "<TT>mode</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='center' Line='center = "mode"'>
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
  mean).
  </DD>
  </DL>
  <DL>
  <DT><B>exposure = "<TT>exptime</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='exposure' Line='exposure = "exptime"'>
  <DD>Keyword giving the exposure time.
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
  SHUTCOR calculate the shutter correction for a detector given a
  sequence of overscan corrected images of varying durations.  Typically
  these would be flat field exposures.  The shutter correction is the
  intercept on a plot of exposure duration versus exposure level.
  <P>
  The images must contain the keyword OVERSCAN otherwise and error will
  be given.
  <P>
  Bad pixels should be eliminated to avoid affecting the statistics.
  This can be done with sigma clipping and/or an image section.
  The sigma clipping should not significantly affect the assumed gaussian
  distribution while eliminating outlyers due to cosmic rays and
  unmasked bad pixels.  This means that clipping factors should be
  symmetric.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  A sequence of flat fields with varying exposure times are taken and
  processed to subtract the overscan.
  <P>
  <PRE>
      cl&gt; shutcor flat*
  <P>
      Shutter correction = 0.538 +/- 0.043 seconds
  <P>
      Information about the mode versus exptime fit:
  <P>
  	   intercept        slope     (and errors)
  	    5.347105      9.933618
  	   0.4288701    0.01519613
  	
  	chi sqr:  0.2681   ftest: 419428.   correlation:      1.
  	 nr pts:      4.   std dev res: 0.422769
  	
  	x(data)     y(calc)     y(data)     sigy(data)
  	     3.      35.148     34.6725          0.
  	    12.     124.551     125.015          0.
  	    27.     273.555     273.778          0.
  	    48.     482.161     481.949          0.
  </PRE>
  </DD>
  </DL>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imstatistics
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'SYNOPSIS' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
