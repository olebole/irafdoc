.. _findpars:

findpars — Edit the star detection parameters
=============================================

**Package: daophot**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  findpars -- edit the object detection parameters
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  findpars
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>threshold = 4.0 (sigma)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='threshold' Line='threshold = 4.0 (sigma)'>
  <DD>The object detection threshold above local background in units of
  <I>datapars.sigma</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>nsigma = 1.5</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nsigma' Line='nsigma = 1.5'>
  <DD>The semi-major axis of the Gaussian convolution kernel used to computed the
  density enhancement and mean density images in Gaussian sigma. This semi-
  major axis is equal to min (2.0, 0.42466 * <I>nsigma</I> *
  <I>datapars.fwhmpsf</I> / <I>datapars.scale</I>) pixels.
  </DD>
  </DL>
  <DL>
  <DT><B>ratio = 1.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ratio' Line='ratio = 1.0'>
  <DD>The ratio of the sigma of the Gaussian convolution kernel along the minor axis
  direction to the sigma along the major axis direction.  <I>Ratio</I> defaults
  to 1.0 in which case the image is convolved with a circular Gaussian.
  </DD>
  </DL>
  <DL>
  <DT><B>theta = 0.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='theta' Line='theta = 0.0'>
  <DD>The position of the major axis of the elliptical Gaussian. <I>Theta</I> is
  measured counter-clockwise from the x axis.
  </DD>
  </DL>
  <DL>
  <DT><B>sharplo = .2, sharphi = 1.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sharplo' Line='sharplo = .2, sharphi = 1.0'>
  <DD><I>Sharplo</I> and <I>sharphi</I> are numerical cutoffs on the image sharpness
  statistic chosen to eliminate brightness maxima which are due to bad pixels
  rather than to astronomical objects.
  </DD>
  </DL>
  <DL>
  <DT><B>roundlo = -1.0 roundhi = 1.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='roundlo' Line='roundlo = -1.0 roundhi = 1.0'>
  <DD><I>Roundlo</I> and <I>roundhi</I> are numerical cutoffs on the image roundness
  statistic chosen to eliminate brightness maxima which are due to bad rows or
  columns rather than to astronomical objects.
  </DD>
  </DL>
  <DL>
  <DT><B>mkdetections = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='mkdetections' Line='mkdetections = no'>
  <DD>Mark the positions of the detected objects on the displayed image ?
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  DAOFIND approximates the stellar point spread function with an elliptical
  Gaussian function, whose sigma along the semi-major axis is 0.42466 *
  <I>datapars.fwhmpsf</I> / <I>datapars.scale</I> pixels, semi-minor to semi-major
  axis ratio is <I>ratio</I>, and major axis position angle is <I>theta</I>.
  Using this model, a convolution kernel, truncated at <I>nsigma</I> sigma,
  and normalized to sum to zero, is constructed.
  <P>
  The density enhancement image <I>starmap</I> is computed by convolving the input
  image with the Gaussian kernel. This operation is mathematically equivalent to
  fitting, in the least-squares sense, the image data at each point with a
  truncated, lowered elliptical Gaussian function. After convolution each point
  in <I>starmap</I> contains as estimate of the amplitude of the best fitting
  Gaussian function at that point. Each point in <I>skymap</I>, if the user
  chooses to compute it, contains an estimate of the best fitting sky value
  at that point.
  <P>
  After image convolution DAOFIND steps through <I>starmap</I> searching
  for density enhancements greater than <I>findpars.threshold</I> *
  <I>datapars.sigma</I>, and brighter than all other density enhancements
  within a semi-major axis of 0.42466 <I>findpars.nsigma</I> *
  <I>datapars.fwhmpsf</I>. As the program selects candidates, it computes two
  shape characteristics sharpness and roundness.  The sharpness statistic
  measures the ratio of the difference between the height of the central pixel
  and the mean of the surrounding non-bad pixels, to the height of the best
  fitting Gaussian function at that point. The roundness statistics measures
  the ratio of, the difference in the height of the best fitting Gaussian
  function in x minus the best fitting Gaussian function in y, over the average
  of the best fitting Gaussian functions in x and y. The limits on these
  parameters <I>findpars.sharplo</I>, <I>findpars.sharphi</I>,
  <I>findpars.roundlo</I>, and <I>findpars.roundhi</I>, are set to weed out
  non-astronomical objects and brightness enhancements that are elongated in
  x and y respectively.
  <P>
  Lastly the x and y centroids of the detected objects are computed by
  estimating the x and y positions of the best fitting 1D Gaussian
  functions in x and y respectively, a rough magnitude is estimated
  by computing the ratio of the amplitude of the best fitting Gaussian at
  the object position to <I>findpars.threshold</I> * <I>datapars.sigma</I>,
  and the object is added to the output coordinate file.
  <P>
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. List the object detection parameters.
  <P>
  <PRE>
  	da&gt; lpar findpars
  </PRE>
  <P>
  2. Edit the object detection parameters.
  <P>
  <PRE>
  	da&gt; findpars
  </PRE>
  <P>
  3. Edit the FINDPARS parameters from within the DAOFIND task.
  <P>
  <PRE>
  	da&gt; epar daofind
  <P>
  	    ... edit a few daofind parameters
  <P>
  	    ... move to the findpars parameter and type :e
  <P>
  	    ... edit the findpars parameter and type :wq
  <P>
  	    ... finish editing the daofind parameters and type :wq
  </PRE>
  <P>
  4. Save the current FINDPARS parameter set in a text file fndnite1.par.
  This can also be done from inside a higher level task as in the previous
  example.
  <P>
  <PRE>
  	da&gt; findpars
  <P>
  	    ... edit the parameters
  <P>
  	    ... type ":w fndnite1.par" from within epar
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  daofind
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  epar,lpar,daofind,datapars
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
