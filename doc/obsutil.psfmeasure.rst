.. _psfmeasure:

psfmeasure — Measure PSF sizes from stellar images
==================================================

**Package: obsutil**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  psfmeasure -- Measure PSF widths in stellar images
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  psfmeasure images
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>images</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>List of images.
  </DD>
  </DL>
  <DL>
  <DT><B>coords = "<TT>mark1</TT>" (center|mark1|markall)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='coords' Line='coords = "mark1" (center|mark1|markall)'>
  <DD>Method by which the coordinates of objects to be measured are specified.
  If "<TT>center</TT>" then a single object at the center of each image is measured.
  If "<TT>mark1</TT>" then the <I>imagecur</I> parameter, typically the interactive
  image display cursor, defines the coordinates of one or more objects in the
  first image ending with a <TT>'q'</TT> key value and then the same coordinates are
  automatically used in subsequent images.  If "<TT>markall</TT>" then the
  <I>imagecur</I> parameter defines the coordinates for objects in each image
  ending with a <TT>'q'</TT> key value.
  </DD>
  </DL>
  <DL>
  <DT><B>wcs = "<TT>logical</TT>" (logical|physical|world)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wcs' Line='wcs = "logical" (logical|physical|world)'>
  <DD>Coordinate system for input coordinates.  When using image cursor input
  this will always be "<TT>logical</TT>".  When using cursor input from a file this
  could be "<TT>physical</TT>" or "<TT>world</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>display = yes, frame = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='display' Line='display = yes, frame = 1'>
  <DD>Display the image or images as needed?  If yes the image display is checked
  to see if the image is already in one of the display frames.  If it is not
  the <B>display</B> task is called to display the image in the frame
  specified by the <B>frame</B> parameter.  All other display parameters are
  taken from the current settings of the task.  This option requires that the
  image display be active.  A value of no is typically used when an input
  cursor file is used instead of the image display cursor.  An image display
  need not be active in that case.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B>level = 0.5</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='level' Line='level = 0.5'>
  <DD>The parameter used to quantify an object image size is the radius from the
  image center enclosing the fraction of the total flux given by this
  parameter.  If the value is greater than 1 it is treated as a percentage.
  </DD>
  </DL>
  <DL>
  <DT><B>size = "<TT>FWHM</TT>" (Radius|FWHM|GFWHM|MFWHM)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='size' Line='size = "FWHM" (Radius|FWHM|GFWHM|MFWHM)'>
  <DD>There are four ways the PSF size may be shown in graphs and given in
  the output.  These are:
  <P>
  <PRE>
      Radius - the radius enclosing the specified fraction of the flux
      FWHM   - a direct FWHM from the measured radial profile
      GFWHM  - the FWHM of the best fit Gaussian profile
      MFWHM  - the FWHM of the best fit Moffat profile
  </PRE>
  <P>
  The labels in the graphs and output will be the value of this parameter
  to distinguish the different types of size measurements.
  </DD>
  </DL>
  <DL>
  <DT><B>beta = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='beta' Line='beta = INDEF'>
  <DD>For the Moffat profile fit (size = MFWHM) the exponent parameter may
  be fixed at a specified value or left free to be determined from the
  fit.  The exponent parameter is determined by the fit if <I>beta</I>
  task parameter is INDEF.
  </DD>
  </DL>
  <DL>
  <DT><B>scale = 1.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='scale' Line='scale = 1.'>
  <DD>Pixel scale in user units per pixel.  Usually the value is 1 to measure
  sizes in pixels or the image pixel scale in arc seconds per pixel.
  </DD>
  </DL>
  <DL>
  <DT><B>radius = 5., iterations = 3</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='radius' Line='radius = 5., iterations = 3'>
  <DD>Measurement radius in pixels and number of iterations on the radius.  The
  enclosed flux profile is measured out to this radius.  This radius may be
  adjusted if the <I>iteration</I> parameter is greater than 1.  In that case
  after each iteration a new radius is computed from the previous direct FWHM
  estimate.  The new radius is three times direct FWHM (six times the
  half-maximum radius).  The purpose of this is so that if the initial PSF
  size of the image need not be known.  However, the radius should then be
  larger than true image size since the iterations best converge to smaller
  values.
  </DD>
  </DL>
  <DL>
  <DT><B>sbuffer = 5, swidth = 5.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sbuffer' Line='sbuffer = 5, swidth = 5.'>
  <DD>Sky buffer and sky width in pixels.  The buffer is added to the specified
  measurement <I>radius</I> to define the inner radius for a circular sky
  aperture.  The sky width is the width of the circular sky aperture.
  </DD>
  </DL>
  <DL>
  <DT><B>saturation=INDEF, ignore_sat=no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='saturation' Line='saturation=INDEF, ignore_sat=no'>
  <DD>Data values (prior to sky subtraction) to be considered saturated within
  measurement radius.  A value of INDEF treats all pixels as unsaturated.  If
  a measurement has saturated pixels there are two actions.  If
  <I>ignore_sat</I>=no then a warning is given but the measurement is saved
  for use.  The object will also be indicated as saturated in the output
  log.  If <I>ignore_sat</I>=yes then a warning is given and the object is
  discarded as if it was not measured.
  </DD>
  </DL>
  <DL>
  <DT><B>xcenter = INDEF, ycenter = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xcenter' Line='xcenter = INDEF, ycenter = INDEF'>
  <DD>The optical field center of the image given in image pixel coordinates.
  These values need not lie in the image.  If INDEF the center of the image
  is used.  These values are used to make plots of size verse distance from
  the field center for studies of radial variations.
  </DD>
  </DL>
  <DL>
  <DT><B>logfile = "<TT>logfile</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logfile' Line='logfile = "logfile"'>
  <DD>File in which to record the final results.  If no log file is desired a
  null string may be specified.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B>imagecur = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='imagecur' Line='imagecur = ""'>
  <DD>Image cursor input for the "<TT>mark1</TT>" and "<TT>markall</TT>" options.  If null then the
  image dispaly cursor is used interactively.  If a file name is specified
  then the coordinates come from this file.  The format of the file are lines
  of x, y, id, and key.  Values of x an y alone may be used to select objects
  and the single character <TT>'q'</TT> (or the end of the file) may be used to end
  the list.
  </DD>
  </DL>
  <DL>
  <DT><B>graphcur = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphcur' Line='graphcur = ""'>
  <DD>Graphics cursor input.  If null then the standard graphics cursor
  is used otherwise a standard cursor format file may be specified.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Cursor commands</H3>
  <! BeginSection: 'CURSOR COMMANDS'>
  <UL>
  When selecting objects with the image cursor the following commands are
  available.
  <P>
  <PRE>
  ?  Page cursor command summary
  g  Measure object and graph the results.
  m  Measure object.
  q  Quit object marking and go to next image.
     At the end of all images go to analysis of all measurements.
  <P>
  :show  Show current results.
  </PRE>
  <P>
  When in the interactive graphics the following cursor commands are available.
  All plots may not be available depending on the number of stars.
  <P>
  <PRE>
  ?  Page cursor command summary
  a  Spatial plot
  d  Delete star nearest to cursor
  e  Enclosed flux for all stars
  i  Information about star nearest the cursor
  m  Size and ellipticity vs relative magnitude
  n  Normalize enclosed flux at x cursor position
  o  Offset enclosed flux by adjusting background
  p  Radial profiles for all stars
  q  Quit
  r  Redraw
  s  Toggle magnitude symbols in spatial plot
  t  Size and ellipticity vs radius from field center
  u  Undelete all deleted points
  x  Delete nearest point or star (selected by query)
  z  Zoom to a single measurement
  &lt;space&gt; Step through different stars in some plots
  <P>
  :beta &lt;val&gt;     Set the beta parameter for the Moffat profile fit
  :level &lt;val&gt;	Level at which the size parameter is evaluated
  :overplot &lt;y|n&gt; Overplot the profiles from the narrowest profile?
  :radius &lt;val&gt;   Change profile radius
  :show &lt;file&gt;	Page all information for the current set of objects
  :size &lt;type&gt;	Size type (Radius|FWHM)
  :scale &lt;val&gt;	Pixel scale for size values
  :xcenter &lt;val&gt;	X field center for radius from field center plots
  :ycenter &lt;val&gt;	Y field center for radius from field center plots
  </PRE>
  </UL>
  <! EndSection:   'CURSOR COMMANDS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task measures the point-spread function (PSF) width of stars or other
  unresolved objects in digital images.  The width is measured from the
  enclosed flux verses radius profile.  The details of this are described in
  the ALGORITHMS section.  Measurements of multiple stars in multiple images
  may be made.  When there are multiple stars, variations in the PSF with
  position may be examined.  The task has three stages; selecting objects and
  measuring the PSF width and other parameters, an interactive graphical
  analysis, and a final output of the results to the terminal and to a
  logfile.
  <P>
  If a saturation value is specified then all pixels within the specified
  measurement radius are checked for saturation.  If any saturated pixels are
  found a warning is given and <I>ignore_sat</I> parameter may be used ot
  ignore the measurement.  If not ignored the object will still be indicated
  as saturated in the output log.  In a focus sequence only the saturated
  objects are discarded and not the whole sequence.
  <P>
  The input images are specified by an image template list.  The list may
  consist of explicit image names, wildcard templates, and @ files.
  Identifying the object or objects to be measured may be accomplished in
  several ways.  If a single object near the center of the image is to be
  measured then the <I>coords</I> parameter takes the value "<TT>center</TT>".  When
  the "<TT>center</TT>" option is used the <I>display</I> and <I>imagecur</I> parameters
  are ignored.
  <P>
  If there are multiple objects or the desired object is not at the center of
  the frame the object coordinates are entered with the <I>imagecur</I>
  parameter.  This type of coordinate input is selected by specifying either
  "<TT>mark1</TT>" or "<TT>markall</TT>" for the <I>coords</I> parameter.  If the value is
  "<TT>mark1</TT>" then the coordinates are entered for the first image and the same
  values are automatically used for subsequent images.  If "<TT>markall</TT>" is
  specified then the objects in each image are marked.
  <P>
  Normally the <I>imagecur</I> parameter would select the interactive image
  display cursor though a standard cursor file could be used to make this
  part noninteractive.  When the image display cursor is used either the
  image must be displayed previously by the user, or the task may be allowed
  to load the image display using the <B>display</B> task by setting the
  parameter <I>display</I> to yes and <I>frame</I> to a display frame.  If yes
  the image display must be active.  The task will look at the image names as
  stored in the image display and only load the display if needed.
  <P>
  If one wants to enter a coordinate list rather than use the interactive
  image cursor the list can consist of just the column and line coordinates
  since the key will default to <TT>'m'</TT>.  To finish the list either the end
  of file may be encountered or a single <TT>'q'</TT> may be given since the
  coordinates are irrelevant.  For the "<TT>markall</TT>" option with multiple
  images there would need to be a <TT>'q'</TT> at the end of each object except
  possibly the last.
  <P>
  When objects are marked interactively with the image cursor there
  are a four keys which may be used as shown in the CURSOR COMMAND section.
  The important distinction is between <TT>'m'</TT> to mark and measure an
  object and <TT>'g'</TT> to mark, measure, and graph the results.  The former
  accumulates the results until the end while the latter can give an
  immediate result to be examined.  Unless only one object is marked
  the <TT>'g'</TT> key also accumulates the results for later graphical analysis.
  It is important to note that the measurements are done as each
  object is marked so there can be a significant delay before the
  next object may be marked.
  <P>
  The quantities measured and the algorithms used are described in the
  ALGORITHMS section.  Once all the objects have been measured an
  interactive (unless only one object is measured) graphical presentation
  of the measurements is entered.
  <P>
  When the task exits it prints the results to the terminal (STDOUT) and also
  to the <I>logfile</I> if one is specified.  The results may also be
  previewed during the execution of the task with the "<TT>:show</TT>" command.  The
  results begin with a banner and the overall estimate of the PSF size.
  Following this the individual measurements are given.  The columns give the
  image name, the column and line position, the relative magnitude, the PSF
  size as either the enclosed flux radius or the various FWHM, the
  ellipticity, and the position angle.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Algorithms</H3>
  <! BeginSection: 'ALGORITHMS'>
  <UL>
  The PSF of an object is characterized using a radially symmetric
  enclosed flux profile.  First the center of the object is determined from
  an initial rough coordinate.  The center is computed from marginal profiles
  which are sums of lines or columns centered at the initial coordinate and
  with a width given by the sum of the <I>radius</I>, <I>sbuffer</I>, and
  <I>swidth</I> parameters.  The mean of the marginal profile is determined
  and then the centroid of the profile above this is computed.  The centroids
  from the two marginal profiles define a new object center.  These steps of
  forming the marginal profiles centered at the estimated object position and
  then computing the centroids are repeated until the centroids converge or
  three iterations have been completed.
  <P>
  Next a background is determined from the mode of the pixel values in the
  sky annulus defined by the object center and <I>radius</I>, <I>sbuffer</I>,
  and <I>swidth</I> parameters.  The pixel values in the annulus are sorted
  and the mode is estimated as the point of minimum slope in this sorted
  array using a width of 5% of the number of points.  If there are multiple
  regions with the same minimum slope the lowest pixel value is used.
  <P>
  The background subtracted enclosed flux profile is determined next.
  To obtain subpixel precision and to give accurate estimates for small
  widths relative to the pixel sampling, several things are done.
  First interpolation between pixels is done using a cubic spline surface.
  The radii measured are in subpixel steps.  To accommodate small and
  large PSF widths (and <I>radius</I> parameters) the steps are nonuniform
  with very fine steps at small radii (steps of 0.05 pixels in the
  central pixel) and coarser steps at larger radii (beyond 9 pixels
  the steps are one pixel) out to the specified <I>radius</I>.  Similarly each
  pixel is subsampled finely near the center and more coarsely at larger
  distances from the object center.  Each subpixel value, as obtained by
  interpolation, is background subtracted and added into the enclosed flux
  profile.  Even with subpixel sampling there is still a point where a
  subpixel straddles a particular radius.  At those points the fraction of
  the subpixel dimension in radius falling within the radius being measured
  is used as the fraction of the pixel value accumulated.
  <P>
  Because of errors in the background determination due to noise and
  contaminating objects it is sometimes the case that the enclosed flux
  is not completely monotonic with radius.  The enclosed flux
  normalization, and the magnitude used in plots and reported in
  results, is the maximum of the enclosed flux profile even if it
  occurs at a radius less than the maximum radius.  It is possible
  to change the normalization and subtract or add a background correction
  interactively.
  <P>
  Because a very narrow PSF will produce significant errors in the cubic
  spline interpolation due to the steepness and rapid variation in the pixel
  values near the peak, the Gaussian profile with FWHM that encloses the same
  80% of the flux is computed as:
  <P>
      FWHM(80%) = 2 * r(80%) * sqrt (ln(2) / (ln (1/.2)))
  <P>
  If this is less than five pixels the Gaussian model is subtracted from the
  data.  The Gaussian normalization is chosed to perfectly subtract the
  central pixel.  The resulting subtraction will not be perfect but the
  residual data will have much lower amplitudes and variations.  A spline
  interpolation is fit to this residual data and the enclosed flux profile is
  recomputed in exactly the same manner as previously except the subpixel
  intensity is evaluated as the sum of the analytic Gaussian and the
  interpolation to the residual data.
  <P>
  The Gaussian normalization is chosed to perfectly subtract the central
  pixel.  The resulting subtraction will not be perfect but the residual data
  will have much lower amplitudes and variations.  A spline interpolation is
  fit to this residual data and the enclosed flux profile is recomputed in
  exactly the same manner as previously except the subpixel intensity is
  evaluated as the sum of the analytic Gaussian and the interpolation to the
  residual data.  This technique yields accurate FWHM for simulated Gaussian
  PSFs down to at least a FWHM of 1 pixel.
  <P>
  In addition to the enclosed flux profile, an estimate of the radially
  symmetric intensity profile is computed from the enclosed flux profile.
  This is based on the equation
  <P>
  <PRE>
      F(R) = integral from 0 to R { P(r) r dr }
  </PRE>
  <P>
  where F(R) is the enclosed flux at radius R and P(r) is the intensity per
  unit area profile.  Thus the derivative of F(R) divided by R gives an
  estimate of P(R).
  <P>
  Cubic spline interpolation functions are fit to the normalized enclosed
  flux profile and the intensity profile.  These are used to find the radius
  enclosing any specified fraction of the flux and to find the direct FWHM of
  the intensity profile.  These are output when <I>size</I> is "<TT>Radius</TT>" or
  "<TT>FWHM</TT>" respectively.
  <P>
  In addition to enclosed flux radius and direct FWHM size measurements
  there are also two size measurements based on fitting analytic profiles.
  A Gaussian profile and a Moffat profile are fit to the final enclosed flux
  profile to the points with enclosed flux less than 80%.  The limit is
  included to minimize the effects of poor background values and to make the
  profile fit be representative of the core of the PSF profile.  These profiles
  are fit whether or not the selected <I>size</I> requires it.  This is done
  for simplicity and to allow quickly changing the size estimate with the
  "<TT>:size</TT>" command.
  <P>
  The intensity profile functions (with unit peak) are:
  <P>
  <PRE>
      I(r) = exp (-0.5 * (r/sigma)**2)			Gaussian
      I(r) = (1 + (r/alpha)**2)) ** (-beta)		Moffat
  </PRE>
  <P>
  with parameters sigma, alpha, and beta.  The normalized enclosed flux
  profiles, which is what is actually fit, are then:
  <P>
  <PRE>
      F(r) = 1 - exp (-0.5 * (r/sigma)**2)		Gaussian
      F(r) = 1 - (1 + (r/alpha)**2)) ** (1-beta)		Moffat
  </PRE>
  <P>
  The fits determine the parameters sigma or alpha and beta (if a
  beta value is not specified by the users).  The reported FWHM values
  are given by:
  <P>
  <PRE>
      GFWHM = 2 * sigma * sqrt (2 * ln (2))		Gaussian
      MFWHM = 2 * alpha * sqrt (2 ** (1/beta) - 1)	Moffat
  </PRE>
  <P>
  were the units are adjusted by the pixel scale factor.
  <P>
  In addition to the four size measurements there are several additional
  quantities which are determined.  
  Other quantities which are computed are the relative magnitude,
  ellipticity, and position angle.  The magnitude of an individual
  measurement is obtained from the maximum flux attained in the enclosed
  flux profile computation.  Though the normalization and background may be
  adjusted interactively later, the magnitude is not changed from the
  initial determination.  The relative magnitude of an object is then
  computed as
  <P>
  <PRE>
      rel. mag. = -2.5 * log (object flux / maximum star flux)
  </PRE>
  <P>
  The maximum star magnitude over all stars is used as the zero point for the
  relative magnitudes (hence it is possible for an individual object relative
  magnitude to be less than zero).
  <P>
  The ellipticity and positional angle of an object are derived from the
  second central intensity weighted moments.  The moments are:
  <P>
  <PRE>
  	Mxx = sum { (I - B) * x * x } / sum { I - B }
  	Myy = sum { (I - B) * y * y } / sum { I - B }
  	Mxy = sum { (I - B) * x * y } / sum { I - B }
  </PRE>
  <P>
  where x and y are the distances from the object center, I is
  the pixel intensity and B is the background intensity.  The sum is
  over the same subpixels used in the enclosed flux evaluation with
  intensities above an isophote which is slightly above the background.
  The ellipticity and position angles are derived from the moments
  by the equations:
  <P>
  <PRE>
  	M1 = (Mxx - Myy) / (Mxx + Myy)
  	M2 = 2 * Mxy / (Mxx + Myy)
  	ellip = (M1**2 + M2**2) ** 1/2
  	pa = atan (M2 / M1) / 2
  </PRE>
  <P>
  where ** is the exponentiation operator and atan is the arc tangent
  operator.  The ellipticity is essentially (a - b) / (a + b) where a
  is a major axis scale length and b is a minor axis scale length.  A
  value of zero corresponds to a circular image.  The position angle is
  given in degrees counterclockwise from the x or column axis.
  <P>
  The overall size when there are multiple stars is estimated by averaging
  the individual sizes weighted by the flux of the star as described above.
  Thus, when there are multiple stars, the brighter stars are given greater
  weight in the average size.  This average size is what is given in the
  banner for the graphs and in the printed output.
  <P>
  One of the quantities computed for the graphical analysis is the
  FWHM of a Gaussian or Moffat profile that encloses the same flux
  as the measured object as a function of the level.  The equation are:
  <P>
  <PRE>
     FWHM = 2 * r(level) * sqrt (ln(2.) / ln (1/(1-level)))  Gaussian
  <P>
     FWHM = 2 * r(level) * sqrt (2**(1/beta)-1) /
  	  sqrt ((1-level)**(1/(1-beta))-1)		   Moffat
  </PRE>
  <P>
  where r(level) is the radius that encloses "<TT>level</TT>" fraction of the total
  flux.  ln is the natural logarithm and sqrt is the square root.  The beta
  value is either the user specified value or the value determined by fitting
  the enclosed flux profile.
  <P>
  This function of level will be a constant if the object profile matches
  the Gaussian or Moffat profile.  Deviations from a constant show
  the departures from the profile model.  The Moffat profile used in making
  the graphs except for the case where the <I>size</I> is GFWHM.
  </UL>
  <! EndSection:   'ALGORITHMS'>
  <H3>Interactive graphics mode</H3>
  <! BeginSection: 'INTERACTIVE GRAPHICS MODE'>
  <UL>
  The graphics part of <B>psfmeasure</B> consists of a number of different
  plots selected by cursor keys.  The available plots depend on the number of
  stars.  The various plots and the keys which select them are summarized
  below.
  <P>
  <PRE>
  a  Spatial plot
  e  Enclosed flux for all stars
  m  Size and ellipticity vs relative magnitude
  p  Radial profiles for all stars
  t  Size and ellipticity vs radius from field center
  z  Zoom to a single measurement
  </PRE>
  <P>
  If there is only one object the only available plot is
  the <TT>'z'</TT> or zoom plot.  This has three graphs; a graph of the normalized
  enclosed flux verses scaled radius, a graph of the intensity profile verses
  scaled radius, and equivalent Moffat/Gaussian full width at half maximum verses
  enclosed flux fraction.  The latter two graphs are derived from the
  normalized enclosed flux profile as described in the ALGORITHMS section.
  In the graphs the measured points are shown with symbols, a smooth curve is
  drawn through the symbols and dashed lines indicate the measurement level
  and enclosed flux radius at that level.
  <P>
  Overplotted on these graphs are the Moffat profile fit or the
  Gaussian profile fit when <I>size</I> is GFWHM.
  <P>
  The zoom plot is always available from any other plot.  The cursor position
  when the <TT>'z'</TT> key is typed selects a particular object measurement.
  This plot is also the one presented with the <TT>'g'</TT> key when marking objects for
  single exposure images.  In that case the graphs are drawn followed by
  a return to image cursor mode.
  <P>
  There are two types of symbol plots showing the measured PSF size (either
  enclosed flux radius or FWHM) and ellipticity.  These plot the measurements
  verses relative magnitude (<TT>'m'</TT> key) and radius from the field center (<TT>'t'</TT>
  key).  These plots are only available when there are multiple stars
  measured.  The magnitude plot is the initial plot in this case.  The field
  center for the field radius graph may be changed interactively using the
  "<TT>:xcenter</TT>" and "<TT>:ycenter</TT>" commands.
  <P>
  Grids of enclosed flux vs. radius, intensity profile vs. radius, and
  FWHM vs. enclosed flux fraction are shown with the <TT>'e'</TT>, <TT>'p'</TT>, and
  <TT>'g'</TT> keys respectively when there is more than one star.  The grid shows
  a profile for each star.  The profiles in the grid have no axis labels or
  ticks.  Within each box are the coordinates of the object
  and the PSF size.  Below the grid is shown a graph of a single objects
  including axis labels and ticks.
  <P>
  In the grid there is one profile which is highlighted (by a second box or
  by a color border).  This is the profile shown in the lower graph.  To
  change the star in the lower graph on can type the space bar to advance to
  the next star or use the cursor and the <TT>'e'</TT>, <TT>'p'</TT>, or <TT>'g'</TT> key again.  Other
  keys will select another plot using the star nearest the cursor to select a
  measurement.
  <P>
  Any of the graphs with enclosed flux or intensity profiles vs radius may
  have the profiles of the object with the smallest size overplotted.  The
  overplot has a dashed line, a different color on color graphics devices,
  and no symbols marking the measurement points.  The overplots may be
  enabled or disabled with the "<TT>:overplot</TT>" command.  Initially it is
  disabled.
  <P>
  The final plot, the <TT>'a'</TT> key, gives a spatial representation.  This requires
  more than one star.  This plot has a central graph of column and line
  coordinates with symbols indicating the position of an object.  The objects
  are marked with a circle (when plotted at unit aspect ratio) whose size is
  proportional to the measured PSF size.  In addition an optional asterisk
  symbol with size proportional to the relative brightness of the object may
  be plotted.  This symbol is toggled with the <TT>'s'</TT> key.  On color displays
  the circles may have two colors, one if object size is above the average
  best size and the other if the size is below the best size.  The purpose of
  this is to look for a spatial pattern in the PSF sizes.
  <P>
  Adjacent to the central graph are graphs with column or line as one
  coordinate and radius or ellipticity as the other.  The symbols
  are the same as described previously.  These plots can show spatial
  gradients in the PSF size and shape across the image.
  <P>
  In addition to the keys which select plots there are other keys which
  do various things.  These are summarized below.
  <P>
  <PRE>
  ?  Page cursor command summary
  d  Delete star nearest to cursor
  i  Information about point nearest the cursor
  n  Normalize enclosed flux at x cursor position
  o  Offset enclosed flux by adjusting background
  q  Quit
  r  Redraw
  s  Toggle magnitude symbols in spatial plots
  u  Undelete all deleted points
  x  Delete nearest point or star (selected by query)
  &lt;space&gt; Step through different stars in current plot type
  </PRE>
  <P>
  The help, redraw, and quit keys are provide the standard functions.
  The <TT>'s'</TT> and space keys were described previously.  The <TT>'i'</TT> key
  locates the nearest object to the cursor in whatever plot is shown and
  prints one line of information about the object on the graphics device
  status area.
  <P>
  The <TT>'d'</TT> key deletes the star nearest the cursor in whatever plot is
  currently displayed.  To delete all objects from an image, all
  values for one star (the same as <TT>'d'</TT>), or a
  single measurement, the <TT>'x'</TT> key is used.  Typing this key produces a query
  for which type of deletion and the user responds with <TT>'i'</TT>, <TT>'s'</TT>, or
  <TT>'p'</TT>.  Deleted measurements do not appear in any subsequent
  graphics, are excluded from all computations, and are not output in the
  results.  The <TT>'u'</TT> key allows one to recover deleted measurements.  This
  undeletes all previously deleted data.
  <P>
  Due to various sources of error the sky value may be wrong causing
  the enclosed flux profile to not converge properly but instead
  decreases beyond some point (overestimated sky) or linearly
  increases with radius (underestimated sky).  This affects the size
  measurement by raising or lowering the normalization and altering
  the shape of the enclosed flux profile.  The <TT>'n'</TT> and <TT>'o'</TT> keys allow
  fudging the enclosed flux profiles.  These keys apply only in
  the zoom plot or <TT>'e'</TT> key plot of the enclosed flux profile.
  <P>
  The <TT>'n'</TT> key normalizes the enclosed flux profile at the point
  set by the x position of the cursor.  The <TT>'o'</TT> key increases or
  decreases the background estimate to bring curve up or down to
  the point specified by the cursor.  The effect of this is to
  add or subtract a quadratic function since the number of pixels
  at a particular radius varies as the square of the radius.
  To restore the original profile, type <TT>'n'</TT> or <TT>'o'</TT> at a radius
  less than zero.
  <P>
  The colon commands, shown below, allow checking or changing parameters
  initially set by the task parameters, toggling the overplotting of the
  smallest PSF profiles, and showing the current results.  The overplotting
  option and the contents of the results displayed by :show were described
  previously.
  <P>
  <PRE>
  :beta &lt;val&gt;     Beta value for Moffat profile fits
  :level &lt;val&gt;	Level at which the size parameter is evaluated
  :overplot &lt;y|n&gt; Overplot the profiles from the narrowest profile?
  :radius &lt;val&gt;   Change profile radius
  :show &lt;file&gt;	Page all information for the current set of objects
  :size &lt;type&gt;	Size type (Radius|FWHM)
  :scale &lt;val&gt;	Pixel scale for size values
  :xcenter &lt;val&gt;	X field center for radius from field center plots
  :ycenter &lt;val&gt;	Y field center for radius from field center plots
  </PRE>
  <P>
  The important values which one might want to change interactively are
  the measurement level and the profile radius.  The measurement level
  directly affects the results reported.  When it is changed the sizes
  of all object PSFs are recomputed and the displayed plots and title
  information are updated.  The profile radius is the
  maximum radius shown in plots and used to set the enclosed flux normalization.
  It does not affect the object centering or sky region definition and
  evaluation which are done when the image data is accessed.  Because
  the objects are not remeasured from the image data the radius may
  not be made larger than the radius defined by the task parameter though
  it may be decreased and then increased again.
  </UL>
  <! EndSection:   'INTERACTIVE GRAPHICS MODE'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  An image of a star field is studied with default values.
  <P>
  <PRE>
  cl&gt; psfmeasure field1
  &lt;The image is displayed and the image cursor activated&gt;
  &lt;A number of brighter stars are marked&gt;
  &lt;Marking is finished with <TT>'q'</TT>&gt;
  &lt;Graph of FWHM and ellipticity vs relative magnitude are shown&gt;
  &lt;A couple of bad measurements due to blending are deleted&gt;
  &lt;Exit with <TT>'q'</TT>&gt;
  NOAO/IRAF IRAFV2.10.3 valdes@puppis Tue 18:22:36 06-Jul-93
    Average full width at half maximum of 4.5722
  <P>
         Image  Column    Line     Mag    FWHM   Ellip      PA SAT
        field1   68.96   37.87    0.75   5.636    0.03      15
  	      488.41  116.78    1.61   5.376    0.03     -68
  	       72.17  156.35    1.47   4.728    0.06     -14
  	       33.72  211.86    2.74   4.840    0.05     -52
  	      212.80  260.73    2.99   3.888    0.11      83
  	      250.51  277.37    1.92   3.914    0.02     -14
  	      411.81  292.83    1.93   5.032    0.04      34
  	      131.85  301.12    2.67   4.028    0.06       4
  	      168.37  413.70    2.20   4.408    0.05      75
  	      256.02  255.99    0.00   3.940    0.00     -70
  <P>
  The estimated average FWHM is 4.5722.  The variation in size is real
  in this artificial image having a radial variation in PSF.
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  <PRE>
  imexamine, implot, pprofile, pradprof, radlist, radplt, radprof,
  specfocus, starfocus, splot
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'CURSOR COMMANDS' 'DESCRIPTION' 'ALGORITHMS' 'INTERACTIVE GRAPHICS MODE' 'EXAMPLES' 'SEE ALSO'  >
  
