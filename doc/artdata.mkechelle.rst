.. _mkechelle:

mkechelle — Make artificial 1D and 2D echelle spectra
=====================================================

**Package: artdata**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  mkechelle -- Make artificial echelle spectra
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  mkechelle images [clobber]
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>images</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>List of echelle spectra to create or modify.
  </DD>
  </DL>
  <DL>
  <DT><B>clobber (query)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='clobber' Line='clobber (query)'>
  <DD>If an existing image is specified the clobber query parameter is used.
  Normally the parameter is not specified on the command line so that
  a query will be made for each image which exists.  Putting a value
  on the command line permanently overrides the query.  This should be
  done if the task is run in the background.
  </DD>
  </DL>
  <DL>
  <DT><B>ncols = 512, nlines = 512, norders = 23</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ncols' Line='ncols = 512, nlines = 512, norders = 23'>
  <DD>For two dimensional spectra these parameters define the number of columns
  and lines in the final image and the maximum number of orders (there may be
  orders falling outside the image).  The dispersion is along the columns
  which is the second or line axis (dispersion axis is 2) so the number of
  columns is the number of pixels across the dispersion and the number of
  lines is the number of pixels along the dispersion per order.
  <P>
  The extracted format turns the number of lines into the number columns
  and the number of orders is the number of lines; i.e the image
  has the specified number of extracted orders, one per image line,
  with the number of pixels along the dispersion specified by the
  <I>nlines</I> parameter.  This is equivalent to what the <B>apextract</B>
  package would  produces for an extracted echelle format with an original
  dispersion axis of 2.  There is no check in this case for orders
  which might fall outside the two dimensional format; i.e. exactly
  the number of orders are created.
  </DD>
  </DL>
  <DL>
  <DT><B>title = "<TT>Artificial Echelle Spectrum</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='title' Line='title = "Artificial Echelle Spectrum"'>
  <DD>Image title to be given to the spectra.  Maximum of 79 characters.
  </DD>
  </DL>
  <DL>
  <DT><B>header = "<TT>artdata$stdheader.dat</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='header' Line='header = "artdata$stdheader.dat"'>
  <DD>Image or header keyword data file.  If an image is given then the image
  header is copied.  If a file is given then the FITS format cards are
  copied.  The data file consists of lines in FITS format with leading
  whitespace ignored.  A FITS card must begin with an uppercase/numeric
  keyword.  Lines not beginning with a FITS keyword such as comments or lower
  case are ignored.  The user keyword output of <B>imheader</B> is an
  acceptable data file.  See <B>mkheader</B> for further information.
  </DD>
  </DL>
  <DL>
  <DT><B>list = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='list' Line='list = no'>
  <DD>List the grating/instrument parameters?
  </DD>
  </DL>
  <DL>
  <DT><B>make = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='make' Line='make = yes'>
  <DD>Make the artificial spectra?  This is set to no if only the grating
  parameter listing is desired.
  </DD>
  </DL>
  <DL>
  <DT><B>comments = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='comments' Line='comments = yes'>
  <DD>Include comments recording task parameters in the image header?
  </DD>
  </DL>
  <P>
  <CENTER>FORMAT PARAMETERS
  
  </CENTER><BR>
  <DL>
  <DT><B>xc = INDEF, yc = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xc' Line='xc = INDEF, yc = INDEF'>
  <DD>The column and line position of the blaze peak in the reference order (see
  <I>order</I> parameter.  If INDEF then the middle of the dimension is used.
  This allows setting the image center relative to the center of the echelle
  pattern.  As with the number of lines and columns the interpretation of
  these numbers relative to the image created depends on whether the format
  is extracted or not.
  </DD>
  </DL>
  <DL>
  <DT><B>pixsize = 0.027</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pixsize' Line='pixsize = 0.027'>
  <DD>Pixel size in millimeters.  This is used to convert the focal length
  and dispersion to pixels.  If INDEF then these parameters are
  assumed to be in pixels.
  </DD>
  </DL>
  <DL>
  <DT><B>profile = "<TT>gaussian</TT>" (extracted|gaussian|slit)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='profile' Line='profile = "gaussian" (extracted|gaussian|slit)'>
  <DD>The order profile across the dispersion.  If the value is "<TT>extracted</TT>"
  then an extracted echelle format spectrum is produced.  Otherwise a
  two dimensional format with a gaussian or slit profile is produced.
  See <B>mk2dspec</B> for a discussion of the profile functions.
  </DD>
  </DL>
  <DL>
  <DT><B>width = 5.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='width' Line='width = 5.'>
  <DD>If two dimensional echelle images are selected this parameter specifies
  the order profile full width at half maximum in pixels.  See <B>mk2dspec</B>
  for a fuller discussion.
  </DD>
  </DL>
  <DL>
  <DT><B>scattered = 0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='scattered' Line='scattered = 0.'>
  <DD>Scattered light peak flux per pixel.  A simple scattered light component
  may be included in the two dimensional format.  The scattered light has the
  blaze function shape of the central order along the dispersion and the
  crossdisperser blaze function shape across the dispersion with the peak
  value given by this parameter.  A value of zero indicates no scattered
  light component.
  </DD>
  </DL>
  <P>
  <CENTER>GRATING PARAMETERS
  
  </CENTER><BR>
  <P>
  Any of the following parameters may be specified as INDEF.  The missing
  values are resolved using the grating equations described in the
  DESCRIPTION section.  If it is not possible to resolve all the grating
  parameters but the order, wavelength, and dispersion are specified
  then a linear dispersion function is used.  Also in this case the
  extracted format will include dispersion information.
  <DL>
  <DT><B>f = 590., cf = 590.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='f' Line='f = 590., cf = 590.'>
  <DD>Echelle and crossdisperser focal lengths in millimeters (if <I>pixsize</I>
  is given) or pixels.  Technically it is defined by the equation x = f * tan
  (theta) where x is distance from the optical axis on the detector and theta
  is the diffraction angle; i.e. it converts angular measures to millimeters
  or pixels on the detector.  If the focal length is specified as INDEF  it
  may be computed from the dispersion, which is required in this case, and
  the other parameters.
  </DD>
  </DL>
  <DL>
  <DT><B>gmm = 31.6, cgmm = 226.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='gmm' Line='gmm = 31.6, cgmm = 226.'>
  <DD>Echelle and crossdisperser grating grooves per millimeter.  If specified as
  INDEF it may be computed from the order, which is required in this case,
  and the other parameters.
  </DD>
  </DL>
  <DL>
  <DT><B>blaze = 63., cblaze = 4.53</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='blaze' Line='blaze = 63., cblaze = 4.53'>
  <DD>Echelle and crossdisperser blaze angles in degrees.  It is always specified or printed as a positive
  angle relative to the grating normal.  If specified as INDEF it is
  computed from the other parameters.
  </DD>
  </DL>
  <DL>
  <DT><B>theta = 69., ctheta = -11.97</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='theta' Line='theta = 69., ctheta = -11.97'>
  <DD>Echelle and crossdisperser angles of incidence in degrees.  The angle of
  incidence must be in the plane perpendicular to face of the grating.  The
  angle of incidence may be specified relative to the grating normal or the
  blaze angle though it is always printed relative to the grating normal.  To
  specify it relative to the blaze angle add 360 degrees; for example to have
  an angle of 15 degrees less than the blaze angle specify 360 - 15 = 345.
  If the angle of incidence is specified as INDEF it is computed from the
  other parameters.
  </DD>
  </DL>
  <DL>
  <DT><B>order = 112</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='order' Line='order = 112'>
  <DD>The central or reference echelle order for which the wavelength and
  dispersion are specified.  If specified as INDEF it will be computed from
  the grooves per mm, which is required in this case, and the other
  parameters.  In combination with the number of orders this defines the
  first and last orders.  The highest order is the central order plus
  the integer part of one half the number of orders.  However, the
  lowest order is constrained to be at least 1.  The
  reference order is also used in the definitions of <I>xc</I> and <I>yc</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>corder = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='corder' Line='corder = 1'>
  <DD>The crossdisperser order for which the crossdisperser blaze wavelength and
  dispersion are specified.  If specified as INDEF it will be computed from
  the grooves per mm, which is required in this case, and the other
  parameters.
  <P>
  If the order is zero then the other grating parameters are ignored and a
  prism-like dispersion is used with the property that the order spacing is
  constant.  Specifically the dispersion varies as the inverse of the
  wavelength with the <I>cwavelength</I> and <I>cdispersion</I> defining the
  function.
  </DD>
  </DL>
  <DL>
  <DT><B>wavelength = 5007.49 cwavelength = 6700.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wavelength' Line='wavelength = 5007.49 cwavelength = 6700.'>
  <DD>Echelle and crossdisperser blaze wavelengths in Angstroms at the reference
  orders.  If specified as INDEF it will be computed from the other parameters.
  </DD>
  </DL>
  <DL>
  <DT><B>dispersion = 2.61 cdispersion = 70.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dispersion' Line='dispersion = 2.61 cdispersion = 70.'>
  <DD>Echelle and crossdisperser blaze dispersions in Angstroms per millimeter
  (if <I>pixsize</I> is specified) or pixels.
  If specified as INDEF it will be computed from the focal length, which is
  required in this case, and the other parameters.
  </DD>
  </DL>
  <P>
  <CENTER>SPECTRA PARAMETERS
  
  </CENTER><BR>
  <DL>
  <DT><B>rv = 0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rv' Line='rv = 0.'>
  <DD>Radial velocity (km/s) or redshift, as selected by the parameter <I>z</I>,
  applied to line positions and continuum.  Velocities are converted to
  redshift using the relativistic relation 1+z = sqrt ((1+rv/c)/(1-rv/c)).
  Note the shift is not a shift in the dispersion parameters but in the
  underlying artificial spectrum.
  </DD>
  </DL>
  <DL>
  <DT><B>z = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='z' Line='z = no'>
  <DD>Is the velocity parameter a radial velocity or a redshift?
  </DD>
  </DL>
  <DL>
  <DT><B>continuum = 1000.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='continuum' Line='continuum = 1000.'>
  <DD>Continuum at the echelle blaze peak in the reference order.
  </DD>
  </DL>
  <DL>
  <DT><B>temperature = 5700.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='temperature' Line='temperature = 5700.'>
  <DD>Blackbody continuum temperature in Kelvin.  A value of 0 is used if
  no blackbody continuum is desired.  The intensity level is set by
  scaling to the continuum level at blaze peak reference point.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B>lines = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lines' Line='lines = ""'>
  <DD>List of spectral line files.  Spectral line files contain lines of rest
  wavelength, peak, and widths (see the DESCRIPTION section).
  The latter two parameters may be missing in which case they default to
  the task <I>peak</I> and <I>sigma</I> parameters.  If no file or a new
  (nonexistent) file is specified then a number of random lines given by the
  parameter <I>nlines</I> is generated.  If a new file name is specified then
  the lines generated are recorded in the file.  If the list of spectral
  line files is shorter than the list of input spectra, the last
  spectral line list file is reused.
  </DD>
  </DL>
  <DL>
  <DT><B>nlines = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nlines' Line='nlines = 0'>
  <DD>If no spectral line file or a new file is specified then the task will
  generate this number of random spectral lines.  The rest wavelengths are
  uniformly random within the limits of the spectrum, the peaks are
  uniformly random between zero and the value of the <I>peak</I> parameter
  and the width is fixed at the value of the <I>sigma</I> parameter.
  If a redshift is applied the rest wavelengths are shifted and repeated
  periodically.
  </DD>
  </DL>
  <DL>
  <DT><B>peak = -0.5</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='peak' Line='peak = -0.5'>
  <DD>The maximum spectral line peak value when generating random lines or
  when the peak is missing from the spectral line file.
  This value is relative to the continuum unless the continuum is zero.
  Negative values are absorption lines and positive values are emission lines.
  </DD>
  </DL>
  <DL>
  <DT><B>sigma = 1.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sigma' Line='sigma = 1.'>
  <DD>The default line width as a gaussian sigma in Angstroms when generating
  random lines or when the width is missing from the spectral line file.
  </DD>
  </DL>
  <DL>
  <DT><B>seed = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='seed' Line='seed = 1'>
  <DD>Random number seed.
  </DD>
  </DL>
  <P>
  PACKAGE PARAMETERS
  <DL>
  <DT><B>nxsub = 10</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nxsub' Line='nxsub = 10'>
  <DD>Number of pixel subsamples used in computing the gaussian spectral line
  profiles.
  </DD>
  </DL>
  <DL>
  <DT><B>dynrange = 100000.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dynrange' Line='dynrange = 100000.'>
  <DD>The gaussian line profiles extend to infinity so a dynamic range, the ratio
  of the peak intensity to the cutoff intensity, is imposed to cutoff the
  profiles.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task creates or adds to artificial extracted (one dimensional
  "<TT>echelle</TT>" format) or two dimensional echelle spectra.  The input spectrum
  (before modification by the spectrograph model) may be a combination of
  doppler shifted blackbody or constant continuum and emission and absorption
  gaussian profile spectral lines.  The lines may have randomly selected
  parameters or be taken from an input file.  Note that the parameters and
  method is similar to the task <B>mk1dspec</B> except that the input line list
  cannot specify a profile type and only Gaussian profiles are currently
  allowed.  The input spectrum is then
  separated out into echelle orders and either recorded as extracted one
  dimensional orders or convolved with a spatial profile and crossdispersed
  into a two dimensional image.  The properties of the echelle grating,
  crossdisperser, and instrumental configuration are modeled described
  later.
  <P>
  If an existing image is specified the <I>clobber</I> parameter is used
  to determine whether to add the generated artificial echelle spectrum
  to the image.  Generally the clobber parameter is not specified on the
  command line to cause a query with the image name to be made for
  each image which already exists.  However, it is possible to put
  the clobber parameter on the command line to eliminate the query.
  This is appropriate for running the task in the background.
  <P>
  There is <I>no</I> checking for consistency with an existing image;
  i.e. that it is an echelle image, whether it is an extracted format
  or a two dimensional spectrum, and what it's wavelength and order
  coverage is.  The only thing that happens is that the <I>ncols</I>,
  <I>nlines</I>, and <I>norders</I> parameters are replaced by the appropriate
  dimensions of the image with the choice between <I>nlines</I> and
  <I>norders</I> made by the <I>profile</I> parameter (as discussed below)
  and not by the format of the image.
  <P>
  The created spectra are two dimensional, real datatype, images.  A title
  may be given and a set of header keywords be added by specifying an image
  or data file with the <I>header</I> parameter (see also <B>mkheader</B>).  If
  a data file is specified lines beginning with FITS keywords are entered in
  the image header.  Leading whitespace is ignored and any lines beginning
  with words having lowercase and nonvalid FITS keyword characters are
  ignored.  In addition to this optional header, various parameters which
  occur during reduction of real echelle spectra, such a wavelength
  coordinates for extracted and dispersion corrected spectra, are added.
  Finally, comments may be added to the image header recording the task
  parameters and any information from the line file which are not line
  definitions.
  <P>
  The creation of an artificial echelle spectra has three stages.  First a
  true spectrum is generated; i.e. the spectrum which arrives at the
  spectrograph.  The spectrum is then separated into orders and the
  dispersion and  blaze functions of the echelle and crossdisperser gratings
  (or crossdisperser prism) are applied.  Finally, if a two dimensional
  format is desired it is convolved by an spatial profile (either a gaussian
  or a broader slit-like profile) and the orders are placed as required by
  the crossdispersion relation.
  <P>
  Generation of the model spectrum has three parts; defining a continuum,
  adding emission and absorption lines, and applying a doppler shift.  The
  continuum has two parameters; an intensity scale set by the <I>continuum</I>
  parameter and a shape set by the <I>temperature</I> parameter.  The
  intensity scale is set by defining the total, final, extracted intensity in
  a pixel at the blaze peak (rest) wavelength in the reference order; i.e. at
  the wavelength set by the <I>wavelength</I> parameter.  Note this means that
  the efficiency of the gratings at that wavelength is included.  The shape
  of the continuum may be either a blackbody if a positive temperature is
  specified or constant.
  <P>
  Spectral lines are modeled by gaussian profiles of specified wavelength,
  peak, and sigma.  The lines are defined in a spectral line file or
  generated randomly.  A spectral line file consists of text lines giving
  rest wavelength, peak, and sigma.  The sigma or the sigma and peak may be
  absent in which case the parameters <I>sigma</I> and <I>peak</I> will be
  used.  If peak values are missing random values between zero and the
  <I>peak</I> value are generated.  Thus, a simple list of wavelengths or a
  list of wavelengths and peaks may be used.
  <P>
  If no spectral line file is specified or a new (nonexistent) file is named
  then the number of random lines given by the parameter <I>nlines</I> is
  generated.  The rest wavelengths are uniformly random within the wavelength
  range of the spectrum and extend periodically outside this range in the
  case of an applied velocity shift, the peaks are uniformly random between
  zero and the <I>peak</I> parameter, and the widths are given by the
  <I>sigma</I> parameter.  If a new file is named then the parameters of the
  generated lines will be output.
  <P>
  The peak values are taken relative to a positive continuum.  In other words
  the generated line profile is multiplied by the continuum (with a minimum
  of zero for fully saturated absorption lines).  If the continuum is less
  than or equal to zero, as in the case of an artificial arc spectrum or pure
  emission line spectrum, then the peak values are interpreted as absolute
  intensities.  Positive peak values produce emission lines and negative
  values produce absorption lines.  Odd results will occur if the continuum
  has both positive and zero or negative values.
  <P>
  The width values are gaussian sigmas given in Angstroms.
  <P>
  The underlying rest spectrum may be shifted.  This is used primarily for
  testing radial velocity measuring algorithms and is not intended as a
  complete model of redshift effects.  The observed wavelength coverage as
  defined by the grating parameters and number of orders is not changed by
  redshifting.  Input line wavelengths are specified at rest and then shifted
  into or out of the final spectrum.  To be realistic the line list should
  include wavelengths over a great enough range to cover all desired
  redshifts.  The peaks and sigma are also appropriately modified by a
  redshift.  As an example, if the redshift is 1 the lines will appear
  broader by a factor of 2 and the peaks will be down by a factor of 2 in
  order to maintain the same flux.
  <P>
  The random line generation is complicated because one wants to have the
  same set of lines (for a given seed) observed at different redshifts.  What
  is done is that the specified number of random lines is generated within
  the observed wavelength interval taken at rest.  This set is then repeated
  periodical over all wavelengths.  A redshift will then shift these rest
  lines in to or out of the observed spectrum.  If the lines are output to a
  line file, they are given at rest.  <B>Note that this periodicity may be
  important in interpreting cross-correlation redshift tests for large shifts
  between template and object spectra.</B>
  <P>
  The definitions of the continuum are also affected by a redshift.  The
  reference point for the continuum level and blackbody shape is the starting
  wavelength taken at rest.  Shifts will then modify the continuum level at
  the reference pixel appropriately.  In particular a large redshift will
  shift the blackbody in such a way that the flux is still given by the
  <I>continuum</I> parameter at the reference wavelength at rest.
  <P>
  Once the input spectrum is defined it is modified by the effects of an
  echelle grating and crossdispersion.  This includes the dispersion relation
  between pixel and wavelength, the blaze response function of the gratings,
  and separation into orders.
  <P>
  The primary reference for the model of the echelle grating (a
  crossdisperser grating also obeys this model) used in this task is "<TT>Echelle
  efficiencies: theory and experiment</TT>" by Schroeder and Hilliard in Applied
  Optics, Vol. 19, No. 16, 1980, p. 2833.  (The nomenclature below is similar
  to that paper except we use theta for alpha, their theta is theta - blaze,
  the reciprocal of the groove spacing which is the grooves per millimeter,
  and the dispersion per linear distance at the detector rather than per
  radian).  This task only treats the case where the incident beam is in the
  plane perpendicular to the grating face (gamma=0).  In this case the basic
  equation is
  <P>
  <PRE>
  (1)	m * lambda = (sin(theta) + sin(beta)) / g
  </PRE>
  <P>
  where m is the order, lambda the wavelength, g the grooves per wavelength
  unit, theta the angle of incidence to the grating normal, and beta the
  angle of diffraction to the normal.  The diffraction angle relative to that
  of the blaze maximum, psi, is given by
  <P>
  <PRE>
  (2)	beta = psi + 2 * blaze - theta
  </PRE>
  <P>
  where blaze is the blaze angle.  The diffraction angle psi is related to
  position on the detector, again measured from the blaze peak, by
  <P>
  <PRE>
  (3)	x = f / pixsize * tan(psi)
  </PRE>
  <P>
  where f is the effective focal length (as defined by this equation) and
  pixsize is the pixel size in millimeters that converts the detector
  positions to pixels.  If a pixel size is not specified then f will be
  taken as being in pixels.
  <P>
  The second basic equation is the diffraction pattern or blaze response
  given by
  <P>
  <PRE>
  (5)	I = I0 * (sin(delta) / delta) ** 2
  (6)	delta = 2 * pi / lambda * (cos(theta) / g) / cos(epsilon) *
  		sin(psi/2) * cos(epsilon-psi/2)
  (7)	epsilon = theta - blaze
  </PRE>
  <P>
  where epsilon is the angle between the blaze angle and the angle of
  incidence (the theta of  Shroeder and Hilliard).  When theta = blaze, (6)
  simplifies to
  <P>
  <PRE>
  (6a)	delta = pi / lambda * (cos (blaze) / g) * sin (psi)
  </PRE>
  <P>
  As discussed by Schroeder and Hilliard, the relative intensity at the blaze
  peak, I0, must be reduced by the fraction of light at the same wavelength
  as the blaze peak which is diffracted into other orders.  Furthermore at
  some diffraction angles the light is reflected off the second face of the
  grating giving a different effective diffraction angle to be used in (6).
  This computation is done by the task giving a variation in relative blaze
  response with order and reproducing the calculations of Schroeder and
  Hilliard.  The absolute normalization, including the crossdisperser blaze
  function if any, is such that the response at the blaze peak of the
  reference order is unity.  This insures that specified continuum level at
  the reference wavelength is produced.
  <P>
  At the blaze maximum psi = x = 0 and the wavelength and dispersion per
  millimeter on the detector are given by (1) and the derivative of (1) with
  respect to x:
  <P>
  <PRE>
  (8)	wavelength = 1E7*(sin(theta)+sin(2*blaze-theta))/(gmm*order)
  (9)	dispersion = 1E7*cos(2*blaze-theta)/(gmm*order*f/pixsize)
  </PRE>
  <P>
  The variable names are the same as the parameters in this task.   In
  particular, gmm is the echelle grooves per millimeter with the factors of
  1E7 (10 to the seventh power) to convert to Angstroms, the factor of f /
  pixsize to convert the dispersion to per pixel, and order is the reference
  order for the wavelength and dispersion.
  <P>
  The <B>mkechelle</B> task provides different ways to define the parameters.
  If there is insufficient information to determine all the grating
  parameters but the wavelength, dispersion, order are specified then
  a simplified grating equation is used which is linear with pixel
  position.  The approximation is that tan(psi) = sin(psi) = psi so
  that
  <P>
  <PRE>
  (9)	lambda = (order * wavelength + dispersion * x) / m
                 = (a + b * x) / m
  (10)	delta  = pi * order * dispersion / lambda * x
                 =  c / lambda * x
  </PRE>
  <P>
  Also in this case the extracted format (described later) includes
  wavelength information in the header so that the spectra appear as fully
  dispersion corrected.
  <P>
  If there are at least five of the seven grating parameters specified
  then equations (8) and (9) are used to determine
  unspecified parameters or to override parameters if the equations are
  overspecified.  For example, suppose the grooves per millimeter is known
  but not the blaze angle or focal length.  Then the wavelength and
  dispersion at the reference order are used to compute these quantities.
  <P>
  The full set of grating parameters derived and used to create the spectra
  are documented in the image header if the <I>comments</I> parameter is
  specified.  Also the <I>list</I> parameter may be set to print the grating
  parameters and the <I>make</I> parameter may be set to no to check the
  grating parameters without making the spectra.
  <P>
  The crossdisperser grating parameters are treated exactly as above except,
  since only one order is used, the relative blaze efficiency is not
  computed.
  <P>
  There is a variant on the crossdispersion to allow a prism-like separation
  of the echelle orders.  If the crossdispersion grating order, <I>corder</I>
  is set to zero then the other grating parameters are ignored and a
  prism-like dispersion is used with the property that the order spacing is
  constant.  Specifically the dispersion varies as the inverse of the
  wavelength with the <I>cwavelength</I> and <I>cdispersion</I> defining the
  function.  There is no crossdisperser blaze function in this case either;
  i.e. the relative intensities between orders is solely due to the echelle
  grating blaze response.
  <P>
  There is an interesting effect which follows from the above equations but
  which is not obvious at first glance.  When the full grating equation is
  used the dispersion varies with wavelength.  This means the size of a pixel
  in wavelength varies and so the flux in a pixel changes.  The effect is
  such that the order intensity maximum shifts to the blue from the blaze peak
  because the pixel width in Angstroms increases to the blue faster, for a
  while, than the blaze response decreases.
  <P>
  Once the spectrum has been separated into orders, modified by the
  grating blaze functions, and sampled into pixels in the dispersion
  direction it may be output as an extracted "<TT>echelle</TT>" format spectrum.
  This occurs when the spatial profile is specified as "<TT>extracted</TT>".
  The keywords added by the <B>apextract</B> package are included in
  the image header.  If the dispersion model is linear
  the keywords are the same as those produced by the dispersion
  correction task <B>ecdispcor</B>.
  <P>
  If the spatial profile is specified as "<TT>gaussian</TT>" or "<TT>slit</TT>" then the
  orders are convolved by the profile function and the crossdispersion
  relation is used to determine where the order falls at each wavelength.
  The spatial profiles are defined by the formulas:
  <P>
  <PRE>
      gaussian:   I(x) = exp (-ln(2) * (2*(x-xc(w))/width)**2)
          slit:   I(x) = exp (-ln(2) * (2*(x-xc(w))/width)**10)
  </PRE>
  <P>
  where x is the spatial coordinate, xc(w) is the order center at
  wavelength w, and width is the full width at half maximum specified by
  the parameter of that name.  The "<TT>gaussian</TT>" profile
  is the usual gaussian specified in terms of a FWHM.  The "<TT>slit</TT>"
  profile is one which is relatively flat and then rapidly drops
  to zero.  The profile is normalized to unit integral so that
  the total flux across the profile is given by the scaled
  1D spectrum flux.  The profile is fully sampled and then binned to
  the pixel size to correctly include sampling effects as a function
  of where in a pixel the order center falls.
  <P>
  Note that in this model the orders are always tilted with respect
  to the columns and constant wavelength is exactly aligned with the
  image lines.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Create an absorption spectrum with blackbody continuum and scattered
  light using the default grating parameters then add noise.
  <P>
  <PRE>
  	cl&gt; mkechelle ex1 nrand=100 scat=100.
  	cl&gt; mknoise ex1 gain=2 rdnoise=5 poisson+
  </PRE>
  <P>
  2. Create an arc spectrum using the line list noao$lib/onedstds/thorium.dat.
  <P>
  <PRE>
  	cl&gt; mkechelle ex2 cont=10 temp=0 \<BR>
  	lines=noao$lib/onedstds/thorium.dat peak=1000 sigma=.05
  </PRE>
  <P>
  Note that the line intensities are random and not realistic.  The peak
  intensities range from 0 to 1000 times the continuum or 10000.
  <P>
  3. Create an extracted version of example1.
  <P>
  <PRE>
  	cl&gt; mkechelle ex1.ec prof=extracted nrand=100 scat=100.
  	cl&gt; mknoise ex1.ec gain=2 rdnoise=5 poisson+
  </PRE>
  <P>
  Note that the noise is different and greater than would be the case with
  extracting the orders of example 1 because the noise is not summed
  over the order profile but is added after the fact.
  <P>
  4. Create an extracted and dispersion corrected version of example1.
  <P>
  <PRE>
  	cl&gt; mkechelle ex1.ec prof=extracted nrand=100 scat=100. \<BR>
  	gmm=INDEF blaze=INDEF theta=INDEF
  	Echelle grating: Using linear dispersion
  	Warning: Insufficient information to resolve grating parameters
  	cl&gt; mknoise ex1.ec gain=2 rdnoise=5 poisson+
  </PRE>
  <P>
  The warning is expected.  By not specifying all the parameters needed to
  fully model an echelle grating the default action is to use a linear
  dispersion in each order and to set the image header dispersion
  information.  When a complete grating model is specified, as in example 3,
  the extracted spectrum is not given dispersion information so that the
  nonlinear behavior of the dispersion can be applied by <B>ecidentify</B> and
  <B>dispcor</B>.  As with example 3, the noise is different since it is added
  after extraction and dispersion correction.
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>MKECHELLE V2.10.3</B></DT>
  <! Sec='REVISIONS' Level=0 Label='MKECHELLE' Line='MKECHELLE V2.10.3'>
  <DD>The task was updated to produce the current coordinate system format.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H3>See also mknoise, mk1dspec, mk2dspec, mkheader, astutil.gratings</H3>
  <! BeginSection: 'SEE ALSO mknoise, mk1dspec, mk2dspec, mkheader, astutil.gratings'>
  <UL>
  </UL>
  <! EndSection:    'SEE ALSO mknoise, mk1dspec, mk2dspec, mkheader, astutil.gratings'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO mknoise, mk1dspec, mk2dspec, mkheader, astutil.gratings'  >
  
