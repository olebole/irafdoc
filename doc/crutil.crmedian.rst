.. _crmedian:

crmedian — Detect and replace cosmic rays with median filter
============================================================

**Package: crutil**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  crmedian -- detect, fix, and flag cosmic rays using median filtering
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage   </H3>
  <! BeginSection: 'USAGE   '>
  <UL>
  <PRE>
  crmedian input output
  </PRE>
  </UL>
  <! EndSection:   'USAGE   '>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>Input image in which to detect cosmic rays.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>Output image in which cosmic rays are replaced by the median value.
  If no output image name is given then no output image will be created.
  </DD>
  </DL>
  <DL>
  <DT><B>crmask = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='crmask' Line='crmask = ""'>
  <DD>Output cosmic ray mask.  Detected cosmic rays (and other deviant pixels)
  are identified in the mask with values of one and good pixels with a values
  of zero.  If no output cosmic ray mask is given then no mask will be
  created.
  </DD>
  </DL>
  <DL>
  <DT><B>median = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='median' Line='median = ""'>
  <DD>Output median filtered image.  If no image name is given then no output will be
  created.
  </DD>
  </DL>
  <DL>
  <DT><B>sigma = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sigma' Line='sigma = ""'>
  <DD>Output sigma image.  If no image name is given then no output will be
  created.
  </DD>
  </DL>
  <DL>
  <DT><B>residual = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='residual' Line='residual = ""'>
  <DD>Output residual image.  This is the input image minus the median filtered
  image divided by the sigma image.  Thresholds in this image determine the
  cosmic rays detected.  If no image name is given then no output will be
  created.
  </DD>
  </DL>
  <DL>
  <DT><B>var0 = 0., var1 = 0., var2 = 0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='var0' Line='var0 = 0., var1 = 0., var2 = 0.'>
  <DD>Variance coefficients for the variance model.  The variance model is
  <P>
  <PRE>
      variance = var0 + var1 * data + var2 * data^2
  </PRE>
  <P>
  where data is the maximum of zero and median pixel value and the variance
  is in data numbers.  All the coefficients must be positive or zero.  If
  they are all zero then empirical data sigmas are estimated by a percentile
  method in boxes of size given by <I>ncsig</I> and <I>nlsig</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>lsigma = 10, hsigma = 3</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lsigma' Line='lsigma = 10, hsigma = 3'>
  <DD>Positive sigma factors to use for selecting pixels below and above
  the median level based on the local percentile sigma.  Cosmic rays will
  appear above the median level.
  </DD>
  </DL>
  <DL>
  <DT><B>ncmed = 5, nlmed = 5</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ncmed' Line='ncmed = 5, nlmed = 5'>
  <DD>The column and line size of a moving median rectangle used to estimate the
  uncontaminated local image.
  </DD>
  </DL>
  <DL>
  <DT><B>ncsig = 25, nlsig = 25</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ncsig' Line='ncsig = 25, nlsig = 25'>
  <DD>The column and line size of regions used to estimate the uncontaminated
  local sigma using a percentile.  The size of the box should contain
  of order 100 pixels or more.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <B>Crmedian</B> detects cosmic rays from pixels deviating by a specified
  statistical amount from the median at each pixel.  It outputs and set of
  the following: a copy of the input image with cosmic rays replaced by the
  median value, a cosmic ray mask identifying the cosmic rays, the median
  filtered image, a sigma image where each pixel has the estimated sigma, and
  the residual image used in detecting the cosmic rays.
  <P>
  The residual image is computed by subtracting a median filtered version
  of the input data from the unfiltered input data and dividing by an
  estimate of the pixel sigmas.  The median filter
  box size is given by the <I>ncmed</I> and <I>nlmed</I> parameters.
  If a name for the median image is specified the median filtered image
  will be output.  The variance at each pixel is determined either from
  a variance model or empirically.  If a name for the sigma image is specified
  then the sigma values (the square root of the variance) will be output.
  If a name for the residual image is given then the residual image
  will be output.
  <P>
  The empirical variance model is given by the formula
  <P>
  <PRE>
      variance = var0 + var1 * data + var2 * data^2
  </PRE>
  <P>
  where data is the maximum of zero and median pixel value and the variance
  is in data numbers.  This model can be related to common detector
  parameters.  For CCDs var0 is the readout noise expressed as a variance in
  data numbers and var1 is the inverse gain (DN/electrons).  The second order
  coefficient has the interpretation of flat field introduced variance.
  <P>
  If all the coefficients are zero then an empirical sigma is estimated
  as follows.  The input image is divided into blocks of size
  <I>ncsig</I> and <I>nlsig</I>.  The pixel values in a block are sorted
  and the pixel values nearest the 15.9 and 84.1 percentiles are
  selected.  These are the one sigma points in a Gaussian distribution.
  The sigma estimate is the difference of these two values divided by
  two.  This algorithm is used to avoid contamination of the sigma
  estimate by the bad pixel values.  The block size must be at least 10
  pixels in each dimension to provide sufficient pixels for a good estimate
  of the percentile points.  The sigma estimate for a pixel is the sigma
  from the nearest block.  A moving box is not used for efficiency.
  <P>
  The residual image is divided by the sigma estimate at each pixel.
  Cosmic rays are identified by finding those pixels in the
  residual image which have values greater than <I>hsigma</I> and bad
  pixels with values below <I>lsigma</I> are also identified.
  <P>
  If an output image name is specified then the output image is produced as a
  copy of the input image but with the identified cosmic ray pixels replaced
  by the median value.  If an output cosmic ray mask is specified a cosmic
  ray mask will be produced with values of zero for good pixels and one for
  bad pixels.  The cosmic ray mask is used to display the cosmic ray
  positions found and the cosmic rays can be replaced by interpolation (as
  opposed to the median value) using the task <I>crfix</I>.
  <P>
  The <B>crmedian</B> detections are very simple and do not take into account
  real structure with scales of a pixel.  Thus this may clip the cores of
  stars and narrow nebular features in the data.  More sophisticated
  algorithms are found in <B>cosmicrays</B>, <I>craverage</I>, and
  <B>crnebula</B>.  The median, sigma, and residual images are available as
  output to evaluate the various aspects of the algorithm.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  This example illustrates using the <B>crmedian</B> task to
  give a cosmic ray removed image and examining the results with an image
  display.  The image is a CCD image with a readout noise of 5 electrons
  and a gain of 3 electrons per data number.  This implies variance
  model coefficients of
  <P>
  <PRE>
      var0 = (5/3)^2 = 2.78
      var1 = 1/3 = 0.34
  </PRE>
  <P>
  <PRE>
      cl&gt; display obj001 1                  # Display in first frame
      cl&gt; # Determine output image, cosmic ray mask, and residual image
      cl&gt; crmedian obj001 crobj001 crmask=mask001 resid=res001\<BR>
      &gt;&gt;&gt; var0=2.78 var1=0.34
      cl&gt; display crobj001 2                # Display final image
      cl&gt; display mask001 3 zs- zr- z1=-1 z2=2 # Display mask
      cl&gt; display res001 4 zs- zr- z1=-5 z2=5  # Display residuals
  </PRE>
  <P>
  By looking at the residual image the sigma clippig threshold can be
  adjusted and the noise parameters can be tweaked to minimize clipping
  of real extended structure.
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  cosmicrays, craverage, crnebula, median, crfix, crgrow
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE   ' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
