.. _centerpars:

centerpars — Edit the centering parameters
==========================================

**Package: apphot**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  centerpars -- edit the centering algorithm parameters
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  centerpars
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>calgorithm = "<TT>centroid</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='calgorithm' Line='calgorithm = "centroid"'>
  <DD>The centering algorithm. The "<TT>gauss</TT>" and "<TT>ofilter</TT>" options depend critically
  on the value of the fwhmpsf parameter in the DATAPARS task. The centering
  options are:
  <DL>
  <DT><B>none</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='none' Line='none'>
  <DD>The initial positions are assumed to be the true centers. Users
  may select this option if the initial centers are know to be accurate,
  e.g. they were computed by DAOFIND task.
  </DD>
  </DL>
  <DL>
  <DT><B>centroid</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='centroid' Line='centroid'>
  <DD>The object centers are determined by computing the intensity weighted means
  of the marginal profiles in x and y.  This is the recommended default algorithm
  for APPHOT users.
  </DD>
  </DL>
  <DL>
  <DT><B>gauss</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='gauss' Line='gauss'>
  <DD>The object centers are computed by fitting a Gaussian of fixed fwhmpsf,
  specified by the DATAPARS fwhmpsf parameter, to the marginal profiles in
  x and y using non-linear least squares techniques.
  </DD>
  </DL>
  <DL>
  <DT><B>ofilter</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='ofilter' Line='ofilter'>
  <DD>The object centers are computed using optimal filtering techniques,
  a triangular weighting function of half width equal to fwhmpsf as
  specified by the DATAPARS fwhmpsf parameter, and the marginal distributions
  in x and y.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>cbox = 5.0  (scale units)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cbox' Line='cbox = 5.0  (scale units)'>
  <DD>The width of the subraster used for object centering in units of the
  DATAPARS scale parameter. Cbox must be big enough to include a reasonable
  number of pixels  for center determination but not so large so as to include
  a lot of noise. Recommended initial values are 2.5-4.0 * the FWHM of the PSF
  value.
  </DD>
  </DL>
  <DL>
  <DT><B>cthreshold = 0.0 (sigma units)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cthreshold' Line='cthreshold = 0.0 (sigma units)'>
  <DD>Pixels cthreshold * sigma above (emission features) or below (absorption
  features) the data minimum or maximum respectively are used by the centering
  algorithms where sigma is equal to the value of the DATAPARS sigma parameter. 
  Most APPHOT users should leave this value at 0.0 which invokes the appropriate
  default thresholding technique for each centering algorithm. Setting cthreshold
  to INDEF turns off thresholding altogether for all the centering algorithms.
  </DD>
  </DL>
  <DL>
  <DT><B>minsnratio = 1.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='minsnratio' Line='minsnratio = 1.0'>
  <DD>The minimum signal to noise ratio for object centering. If the estimated signal
  to noise ratio is less than minsnratio the computed center will be returned
  with an error flag.
  </DD>
  </DL>
  <DL>
  <DT><B>cmaxiter = 10</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cmaxiter' Line='cmaxiter = 10'>
  <DD>The maximum number of iterations performed by the centering algorithm.
  All the centering algorithms use this parameter.
  </DD>
  </DL>
  <DL>
  <DT><B>maxshift = 1.0  (scale units)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maxshift' Line='maxshift = 1.0  (scale units)'>
  <DD>The maximum permissible shift of the center with respect to the initial
  coordinates in units of the scale parameter. If the shift produced by the
  centering algorithms is larger than maxshift, the computed center is returned
  with an error flag.
  </DD>
  </DL>
  <DL>
  <DT><B>clean = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='clean' Line='clean = no'>
  <DD>Symmetry-clean the centering subrater before centering? APPHOT users should
  leave clean set to "<TT>no</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>rclean = 1.0  (scale units)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rclean' Line='rclean = 1.0  (scale units)'>
  <DD>The cleaning radius for the symmetry-clean algorithm in units of the scale
  parameter.
  </DD>
  </DL>
  <DL>
  <DT><B>rclip = 2.0  (scale units)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rclip' Line='rclip = 2.0  (scale units)'>
  <DD>The clipping radius for the symmetry-clean algorithm in units of the scale
  parameter.
  </DD>
  </DL>
  <DL>
  <DT><B>kclean = 3.0  (sigma)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='kclean' Line='kclean = 3.0  (sigma)'>
  <DD>The number of sky background standard deviations for the symmetry-clean
  algorithm where sigma is the value of the DATAPARS parameter sigma.
  </DD>
  </DL>
  <DL>
  <DT><B>mkcenter = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='mkcenter' Line='mkcenter = no'>
  <DD>Mark the fitted object centers on the displayed image ?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  The centering algorithm parameters control the action of the centering
  algorithms. The default parameters values have been proven to produce
  reasonable results in the majority of cases. Several of the centering
  parameters are defined in terms of the DATAPARS parameter <I>scale</I>,
  the scale of the image, and <I>sigma</I> the standard deviation of
  the sky pixels. 
  <P>
  For each object to be measured a subraster of data <I>cbox</I> / <I>scale</I>
  pixels wide around the initial position supplied by the user is extracted
  from the IRAF image. If scale is defined in units of the number
  the half-width half-maximum of the psf per pixel, then a single value of
  cbox can be used for centering objects in images with different psfs.
  <P>
  If <I>clean</I> is "<TT>yes</TT>" the symmetry-clean algorithm is applied to the
  centering subraster prior to centering. The cleaning algorithm attempts
  to correct defects in the centering subraster by assuming that the image
  is radially symmetric and comparing pixels on opposite sides of the center
  of symmetry.  The center of symmetry is assumed to be the maximum pixel
  in the subraster, unless the maximum pixel is more than <I>maxshift /
  scale</I> from the initial center, in which case the initial center is used
  as the center of symmetry.  Pixels inside the cleaning radius are not edited.
  Pairs of pixels in the cleaning region, r &gt; <I>rclean</I> / <I>scale</I>
  and r &lt;= <I>rclip</I> / <I>scale</I> and diametrically opposed about the
  center of symmetry are tested for equality. If the difference between the
  pixels is greater than <I>kclean * sigma</I>, the larger value is replaced
  by the smaller.  In the cleaning region the sigma is determined by the
  noise model assumed for the data. Pairs of pixels in the clipping region,
  r &gt; <I>rclip</I> / <I>scale</I> are tested in the same manner as those in
  the cleaning region. However the sigma employed is the sigma of the
  sky background. Most APPHOT users should leave clean set to "<TT>no</TT>".
  <P>
  New centers are computed using the centering algorithm specified by
  <I>calgorithm</I>, the data specified by <I>cbox / scale</I>, and pixels
  that are some threshold above (below) an estimate of the local minimum
  (maximum). <I>Cthreshold</I> values of 0.0, a positive number, and INDEF
  invoke the default thresholding algorithm, a threshold equal to the
  local minimum (maximum) plus  (minus) <I>datapars.sigma * cthreshold</I>,
  and a threshold exactly equal to the local minimum (maximum) respectively.
  <P>
  After thresholding the signal to noise ratio of the subraster is estimated. 
  If the SNR &lt; <I>minsnratio</I> the new center is still computed but an error
  flag is set.
  <P>
  The default centering algorithm is <I>centroid</I>. Centroid computes the
  intensity weighted mean and mean error of the centering box x and y marginal
  distributions using points in the marginal arrays above (below) the minimum
  (maximum) data pixel plus (minus) a threshold value.
  <P>
  The threshold value is either the mean, <I>datapars.sigma * cthreshold</I>
  above (below) the local minimum (maximum) if <I>cthreshold</I> is greater
  than zero, or zero above (below) the local minimum (maximum) if
  <I>cthreshold</I> is INDEF.  The centroid algorithm is similar to that
  by the old KPNO Mountain Photometry Code. Note that centroid is the only
  centering algorithm which does not depend on the value of
  <I>datapars.fwhmpsf</I>.
  <P>
  The centering algorithm <I>gauss</I> computes the new centers by fitting a
  1D Gaussian function to the marginal distributions in x and y using a
  fixed fwhmpsf set by <I>datapars.fwhmpsf</I>.  Initial guesses for the fit
  parameters are derived from the data. The gauss algorithm iterates until
  a best fit solution is achieved.
  <P>
  The final centering algorithm choice <I>ofilter</I> employs a variation of the
  optimal filtering technique in which the profile is simulated by a triangle
  function of width <I>datapars.fwhmpsf</I>.
  <P>
  The default thresholding algorithm for all centering algorithms other
  than "<TT>centroid</TT>" is no thresholding.
  <P>
  If the computed shift in either coordinate &gt; <I>maxshift</I> / <I>scale</I>,
  the new center is returned but an error flag is set.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. List the centering parameters.
  <P>
  <PRE>
  	ap&gt; lpar centerpars
  </PRE>
  <P>
  2. Edit the centering parameters
  <P>
  <PRE>
  	ap&gt; centerpars
  </PRE>
  <P>
  3. Edit the CENTERPARS parameters from with the PHOT task.
  <P>
  <PRE>
      da&gt; epar phot
  <P>
  	... edit a few phot parameters
  <P>
  	... move to the centerpars parameter and type :e
  <P>
  	... edit the centerpars parameters and type :wq
  <P>
  	... finish editing the phot parameters and type :wq
  </PRE>
  <P>
  4. Save the current CENTERPARS parameter set in a text file ctrnite1.par.
  This can also be done from inside a higher level task as in the
  previous example.
  <P>
  <PRE>
      da&gt; centerpars
  <P>
  	... edit the parameters
  <P>
  	... type ":w ctrnite1.par"  from within epar
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  center,phot,wphot,polyphot,radprof
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
