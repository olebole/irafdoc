centerpars — Edit the centering algorithm parameters
====================================================

**Package: daophot**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>centerpars (May00)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.digiphot.daophot</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>centerpars (May00)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>centerpars</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  centerpars -- edit the centering algorithm parameters
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  centerpars
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_calgorithm">calgorithm = "<TT>none</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='calgorithm' Line='calgorithm = "none"'>
  <DD>The centering algorithm. The "<TT>gauss</TT>" and "<TT>ofilter</TT>" centering algorithms
  depend critically on the value of the fwhmpsf parameter in the DATAPARS task. 
  The centering options are:
  <DL>
  <DT><B><A NAME="l_none">none</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='none' Line='none'>
  <DD>The initial positions are assumed to be the true centers. Users should
  select this option if the initial centers are known to be accurate,
  e.g. they were computed by DAOFIND task.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_centroid">centroid</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='centroid' Line='centroid'>
  <DD>The object centers are determined by computing the intensity weighted means
  of the marginal profiles in x and y.  Centroid is the recommended centering
  algorithm for users running PHOT interactively and selecting objects
  with the image display cursor, or when the input coordinates may be inaccurate.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_gauss">gauss</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='gauss' Line='gauss'>
  <DD>The object centers are computed by fitting a Gaussian of fixed fwhmpsf,
  specified by the DATAPARS fwhmpsf parameter, to the marginal profiles in
  x and y using non-linear least squares techniques.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ofilter">ofilter</A></B></DT>
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
  <DT><B><A NAME="l_cbox">cbox = 5.0  (scale units)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cbox' Line='cbox = 5.0  (scale units)'>
  <DD>The width of the subraster used for object centering in units of the
  scale parameter. Cbox needs to be big enough to include sufficient
  pixels for centering but not so large as to include a lot of noise.
  Reasonable starting values are 2.5-4.0 * FWHM of the PSF.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_cthreshold">cthreshold = 0.0 (sigma units)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cthreshold' Line='cthreshold = 0.0 (sigma units)'>
  <DD>xels cthreshold * sigma above (emission features) or below (absorption
  features) the data minimum or maximum respectively are used by the centering
  algorithms where sigma is equal to the value of the DATAPARS sigma parameter.
  features) the data minimum or maximum are used by the centering algorithms.
  DAOPHOT users should leave this value at 0.0 which invokes the appropriate
  default thresholding technique for each centering algorithm. Setting
  cthreshold to INDEF turns off thresholding altogether for all the centering
  algorithms.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_minsnratio">minsnratio = 1.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='minsnratio' Line='minsnratio = 1.0'>
  <DD>The minimum signal to noise ratio for object centering. If the estimated signal
  to noise ratio is less than minsnratio the computed center will be returned
  with an error flag.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_cmaxiter">cmaxiter = 10</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cmaxiter' Line='cmaxiter = 10'>
  <DD>The maximum number of iterations performed by the centering algorithm.
  All the centering algorithms use this parameter.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_maxshift">maxshift = 1.0  (scale units)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maxshift' Line='maxshift = 1.0  (scale units)'>
  <DD>The maximum permissible shift of the center with respect to the initial
  coordinates in units of the scale parameter. If the shift produced by the
  centering algorithms is larger than maxshift, the computed center is returned
  with an error flag.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_clean">clean = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='clean' Line='clean = no'>
  <DD>Symmetry-clean the centering subraster before centering? DAOPHOT users should
  leave clean set to "<TT>no</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_rclean">rclean = 1.0  (scale units)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rclean' Line='rclean = 1.0  (scale units)'>
  <DD>The cleaning radius for the symmetry-clean algorithm in units of
  the scale parameter.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_rclip">rclip = 2.0  (scale units)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rclip' Line='rclip = 2.0  (scale units)'>
  <DD>The clipping radius for the symmetry-clean algorithm in units of
  the scale parameter.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_kclean">kclean = 3.0  (sigma)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='kclean' Line='kclean = 3.0  (sigma)'>
  <DD>The number of standard sky deviations for the symmetry-clean algorithm.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_mkcenter">mkcenter = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='mkcenter' Line='mkcenter = no'>
  <DD>Mark the fitted centers on the displayed image ?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
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
  sky background. DAOPHOT users should leave clean set to "<TT>no</TT>".
  <P>
  <P>
  <P>
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
  The default centering algorithm is <I>none</I> is which case the initial
  centers are assumed to be accurate and no recentering is done.
  <P>
  The simplest centering algorithm is <I>centroid</I>. Centroid computes the
  intensity weighted mean and mean error of the centering box x and y marginal
  distributions using points in the marginal arrays above (below) the minimum
  (maximum) data pixel plus (minus) a threshold value.  The threshold value is
  either the mean, <I>datapars.sigma * cthreshold</I> above (below) the local
  minimum (maximum) if <I>cthreshold</I> is greater than zero, or zero above
  (below) the local minimum (maximum) if <I>cthreshold</I> is INDEF. The centroid
  algorithm is similar to that by the old KPNO Mountain Photometry Code.
  Note that centroid is the only centering algorithm which does not depend
  on the value of <I>datapars.fwhmpsf</I>.
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
  <P>
  1. List the centering parameters.
  <P>
  <PRE>
  	da&gt; lpar centerpars
  </PRE>
  <P>
  2. Edit the centering parameters.
  <P>
  <PRE>
  	da&gt; centerpars
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
  above example.
  <P>
  <PRE>
      da&gt; epar centerpars
  <P>
  	... type ":w ctrnite1.par"  from within epar
  </PRE>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  epar,lpar,datapars,phot
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>