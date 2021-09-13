mkobjects — Make/add artificial stars and galaxies to 2D images
===============================================================

**Package: artdata**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>mkobjects (Jan92)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.artdata</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>mkobjects (Jan92)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>mkobjects</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  mkobjects - Make/add artificial stars and galaxies to 2D images
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  mkobjects input
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>Images to create or modify.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output = ""'>
  <DD>Output images when modifying input images.  If no output images are
  given then existing images in the input list are modified directly.
  If an output image list is given then it must match in number the
  input list.
  </DD>
  </DL>
  <P>
  WHEN CREATING NEW IMAGES
  <DL>
  <DT><B><A NAME="l_title">title = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='title' Line='title = ""'>
  <DD>Image title to be given to the images.  Maximum of 79 characters.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ncols">ncols = 512, nlines = 512</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ncols' Line='ncols = 512, nlines = 512'>
  <DD>Number of columns and lines.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_header">header = "<TT>artdata$stdheader.dat</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='header' Line='header = "artdata$stdheader.dat"'>
  <DD>Image or header keyword data file.  If an image is given then the image header
  is copied.  If a file is given then the FITS format cards are copied.
  This only applies to new images.   The data file consists of lines
  in FITS format with leading whitespace ignored.  A FITS card must begin
  with an uppercase/numeric keyword.  Lines not beginning with a FITS
  keyword such as comments or lower case are ignored.  The user keyword
  output of <B>imheader</B> is an acceptable data file.  See <B>mkheader</B>
  for further information.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_background">background = 1000.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='background' Line='background = 1000.'>
  <DD>Default background and poisson noise background.  This is in data numbers
  with the conversion to photons determined by the <I>gain</I> parameter.
  </DD>
  </DL>
  <P>
  OBJECT PARAMETERS
  <DL>
  <DT><B><A NAME="l_objects">objects = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='objects' Line='objects = ""'>
  <DD>List of object files.  The number of object files must match the number of
  input images.  The object files contain lines of object coordinates,
  magnitudes, and shape parameters (see the DESCRIPTION section).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xoffset">xoffset = 0.,  yoffset = 0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xoffset' Line='xoffset = 0.,  yoffset = 0.'>
  <DD>X and Y coordinate offset to be added to the object list coordinates.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_star">star = "<TT>moffat</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='star' Line='star = "moffat"'>
  <DD>Type of star and point spread function.  The choices are:
  <DL>
  <DT><B><A NAME="l_gaussian">gaussian</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='gaussian' Line='gaussian'>
  <DD>An elliptical Gaussian profile with major axis half-intensity radius
  given by the parameter <I>radius</I>, axial ratio given by the parameter
  <I>ar</I>, and position angle given by the parameter <I>pa</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_moffat">moffat</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='moffat' Line='moffat'>
  <DD>An elliptical Moffat profile with major axis half-intensity radius
  given by the parameter <I>radius</I>, model parameter <I>beta</I>,
  axial ratio given by the parameter <I>ar</I>, and position angle given
  by the parameter <I>pa</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">&lt;image&gt;</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='&lt;image&gt;'>
  <DD>If not one of the profiles above, an image of the specified name is
  sought.  If found the center of the template image is assumed to be the
  center of the star/psf and the image template is scaled so that the
  radius of the template along the first axis is given by the <I>radius</I>
  parameter.  The axial ratio and position angle define an
  elliptical sampling of the template.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">&lt;profile file&gt;</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='&lt;profile file&gt;'>
  <DD>If not one of the above, a text file is sought giving either an intensity
  per unit area profile or a cumulative flux profile from the center to the
  edge.  The two are differentiated by whether the first profile point is 0
  for a cumulative profile or nonzero for an intensity profile.  An intensity
  profile is recommended.  If found the profile defines an elliptical star/psf
  with the major axis radius to the last profile point given by the parameter
  <I>radius</I>, axial ratio given by the parameter <I>ar</I>, and position
  angle given by the parameter <I>pa</I>.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_radius">radius = 1.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='radius' Line='radius = 1.'>
  <DD>Seeing radius/scale in pixels along the major axis.  For the "<TT>gaussian</TT>"
  and "<TT>moffat</TT>" profiles this is the half-intensity radius of the major
  axis, for image templates this is the template radius along the x dimension,
  specifically one half the number of columns, and for arbitrary user profiles
  this is the radius to the last profile point.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_beta">beta = 2.5</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='beta' Line='beta = 2.5'>
  <DD>Moffat model parameter.  See the DESCRIPTION for a definition of the
  Moffat profile.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ar">ar = 1.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ar' Line='ar = 1.'>
  <DD>Minor to major axial ratio for the star/psf.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_pa">pa = 0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pa' Line='pa = 0.'>
  <DD>Position angle in degrees measured counterclockwise from the X axis
  for the star/psf.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_distance">distance = 1.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='distance' Line='distance = 1.'>
  <DD>Relative distance to be applied to the object list coordinates,
  magnitudes, and scale sizes.  This factor is divided into the
  object coordinates, after adding the offset factors, to allow expanding
  or contracting about any origin.  The magnitudes scale as the
  square of the distance and the sizes of the galaxies scale
  linearly.  This parameter allows changing image sizes and fluxes
  at a given seeing and sampling with one value.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_exptime">exptime = 1.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='exptime' Line='exptime = 1.'>
  <DD>Relative exposure time.  The object magnitudes and background
  level are scaled by this parameter.  This is comparable to changing the
  magnitude zero point except that it includes changing the background.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_magzero">magzero = 7.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='magzero' Line='magzero = 7.'>
  <DD>Magnitude zero point defining the conversion from magnitudes in the
  object list to instrumental/image fluxes.
  </DD>
  </DL>
  <P>
  NOISE PARAMETERS
  <DL>
  <DT><B><A NAME="l_gain">gain = 1.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='gain' Line='gain = 1.'>
  <DD>Gain in electrons per data number.  The gain is used for scaling the
  read noise parameter, the background, and in computing poisson noise.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_rdnoise">rdnoise = 0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rdnoise' Line='rdnoise = 0.'>
  <DD>Gaussian read noise in electrons.  For new images this applies to the
  entire image while for existing images this is added only to the objects.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_poisson">poisson = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='poisson' Line='poisson = no'>
  <DD>Add poisson photon noise?  For new images this applies to the entire image
  while for existing images this is only applied to the objects.  Note
  that in the latter case the background parameter is added before
  computing the new value and then subtracted again.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_seed">seed = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='seed' Line='seed = 1'>
  <DD>Random number seed.  If a value of "<TT>INDEF</TT>" is given then the clock
  time (integer seconds since 1980) is used as the seed yielding
  different random numbers for each execution.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B><A NAME="l_comments">comments = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='comments' Line='comments = yes'>
  <DD>Include comments recording task parameters in the image header?
  </DD>
  </DL>
  <P>
  PACKAGE PARAMETERS
  <P>
  These parameters define certain computational shortcuts which greatly
  affect the computational speed.  They should be adjusted with care.
  <DL>
  <DT><B><A NAME="l_nxc">nxc = 5, nyc = 5</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nxc' Line='nxc = 5, nyc = 5'>
  <DD>Number of star and psf centers per pixel in X and Y.  Rather than evaluate
  stars and the psf convolution functions precisely at each subpixel
  coordinate, a set of templates with a grid of subpixel centers is
  computed and then the nearest template to the desired position is chosen.
  The larger the number the more memory and startup time required.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nxsub">nxsub = 10, nysub = 10</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nxsub' Line='nxsub = 10, nysub = 10'>
  <DD>Number of pixel subsamples in X and Y used in computing the star and
  psf.  This is the subsampling in the central
  pixel and the number of subsamples decreases linearly from the center.
  The larger the numbers the longer it takes to compute the star and psf
  convolution templates.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nxgsub">nxgsub = 5, nygsub = 5</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nxgsub' Line='nxgsub = 5, nygsub = 5'>
  <DD>Number of pixel subsamples in X and Y used in computing galaxy images.
  This is the subsampling in the central pixel and the number of
  subsamples decreases linearly from the center.  Because galaxy images
  are extended and each subsample is convolved by the psf convolution it
  need not be as finely sampled as the stars.  This is a critical
  parameter in the execution time if galaxies are being modeled.
  The larger the numbers the longer the execution time.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_dynrange">dynrange = 100000., psfrange = 10.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dynrange' Line='dynrange = 100000., psfrange = 10.'>
  <DD>The intensity profiles of the analytic functions extend to infinity so
  a dynamic range, the ratio of the peak intensity to the cutoff
  intensity, is imposed to cutoff the profiles.  The <I>dynrange</I>
  parameter applies to the stellar templates and to the galaxy profiles.
  The larger this parameter the further the profile extends.
  When modeling galaxies this has a fairly
  strong affect on the time (larger numbers means larger images and more
  execution time).  Only for very high signal-to-noise
  objects will the cutoff be noticeable.  A correction is made to
  the object magnitudes to reflect light lost by this cutoff.
  <P>
  The psf convolution, used on galaxies, is generally not
  evaluated over as large a dynamic range, given by the parameter
  <I>psfrange</I>, especially since it has a very strong affect on the
  execution time.  The convolution is normalized to unit weight over the
  specified dynamic range.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ranbuf">ranbuf = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ranbuf' Line='ranbuf = 0'>
  <DD>Random number buffer size.  When generating readout and poisson noise,
  evaluation of new random values has an affect on the execution time.
  If truly (or computationally truly) random numbers are not needed
  then this number of random values is stored and a simple
  uniform random number is used to select from the stored values.
  To force evaluation of new random values for every pixel set the
  value of this parameter to zero.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task creates or modifies images by adding models of astronomical
  objects, stars and galaxies, as specified in object lists.  New images are
  created with the specified dimensions, background, title, and real datatype.
  Existing images may be modified in place or new images output.  The
  task includes the effects of image scale, pixel sampling, atmospheric
  seeing, and noise.  The object models may be analytic one dimensional
  profiles, user defined one dimensional profiles, and user defined image
  templates.  The profiles and templates are given elliptical shapes by
  specifying a scale radius for the major axis, a minor axis to major
  axis axial ratio, and a position angle.
  <P>
  For new images a set of header keywords may be added by specifying an
  image or data file with the <I>header</I> parameter (see also <B>mkheader</B>).
  If a data file is specified lines beginning with FITS keywords are
  entered in the image header.  Leading whitespace is ignored and any
  lines beginning with words having lowercase and nonvalid FITS keyword
  characters are ignored.  In addition to this optional header,
  keywords, parameters for the gain, read noise, and exposure time are
  defined.  Finally, comments may be added to the image header recording the task
  parameters and any information from the objects file which are not
  object definitions; in particular, the <B>starlist</B> and
  <B>gallist</B> parameters are recorded.
  <P>
  A completely accurate simulation of the effects of pixel sampling,
  atmospheric seeing, object appearance, luminosity functions, and noise
  can require a large amount of computer time even on
  supercomputers.  This task is intended to allow generation of large
  numbers of objects and images over large image sizes representative of
  current deep optical astronomical images.  All this is to be done
  on typical workstations.  Thus, there are many approximations and
  subtle algorithms used to make this possible to as high a degree of
  accuracy as practical.  The discussion will try to describe these in
  sufficient detail for the user to judge the accuracy of the artificial
  data generated and understand the trade offs with many of the
  parameters.
  <P>
  New images are created with the specified dimensions, title, and real
  datatype.  The images have a constant background value given by the
  <I>background</I> parameter (in data numbers) before adding objects and
  noise.  Noise consists of gaussian and poisson components.  For existing
  images, noise is only added to the objects and the background parameter is
  used in the calculation of the poisson noise: specifically, a poisson
  random value with mean given by the sum of the object and the background is
  generated and then the background is subtracted.  For more on how the noise
  is computed and approximations used see <B>mknoise</B>.
  <P>
  Objects are specified by a position, magnitude, model, scale, axial
  ratio, and position angle.  Since the point spread function (PSF)
  is assumed constant over the image the star model, size, axial ratio,
  and position angle are specified by the task parameters <I>star</I>,
  <I>radius</I>, <I>ar</I>, and <I>pa</I>.  For galaxies, where the
  intrinsic shapes vary from object to object, these parameters are
  specified as part of the object lists.  For both types of objects the
  positions and magnitudes are specified in the object lists.
  <P>
  There is a great deal of flexibility in defining the object models.
  The models are defined either in terms of a one dimensional radial
  intensity or cumulative flux profile
  or an image template.  The flux profiles may be
  analytic functions or a user defined profile given as an equally spaced
  set of values in a text file.  The first point is zero at the center
  for a cumulative profile
  and increases monotonically to the edge.  Note that intensity profiles
  are to be preferred to avoid artifacts in the conversion from cumulative
  flux.  In particular, cumulative flux profiles may give a spike at the
  center.  In either case, the profile should be specified fairly finely,
  many points, to avoid interpolation effects.
  <P>
  The functional form of the analytic profiles the user profiles, and
  image template are given below.
  <P>
  <PRE>
        gaussian:  I = exp (-ln (2) * (R/radius)**2)
          moffat:  I = (1 + (2**(1/beta)-1) * (R/radius)**2) ** -beta
       sersic&lt;n&gt;:  I = exp (-b * (R/radius)**1/n)
         expdisk:  I = exp (-1.6783 * R/radius)
          devauc:  I = exp (-7.67 * (R/radius)**1/4)
    flux profile:  I = intensity (nprofile * R/radius)
    flux profile:  F = flux (nprofile * R/radius)
  image template:  I = image (nc/2+nc/2*dX/radius, nl/2+nc/2*dY/radius)
  </PRE>
  <P>
  where R, dX, and dY are defined below, <I>radius</I> is the scale parameter
  and <I>beta</I> is the Moffat parameter specified by the user,
  nprofile is the number of profile points in the user profile, and nc and nl
  are the image template column and line dimensions.  The Gaussian, "<TT>gaussian</TT>",
  and Moffat, "<TT>moffat</TT>", profiles are used for stars and the point spread
  function, while the Sersic (sersic),  exponential disk (expdisk), and
  De Vaucouleurs (devauc) profiles are common models for spiral and elliptical
  galaxies.  The image templates are intended to model images with
  some complex structure.  The usual case is to have a very well sampled
  and high signal-to-noise image be reduced in scale (a more distant
  example), convolved with seeing (loss of detail), and noise (degraded
  signal-to-noise).  This also allows for more complex point spread
  functions.
  <P>
  The radial profiles are mapped into two dimensional objects by an elliptical
  transformation.  The image templates are also mapped by an elliptical
  transformation to rotate and stretch them.  If the output image
  coordinates are given by (x, y), and the specified object center
  coordinates are given by (xc, yc) then the transformation is defined
  as shown below.
  <P>
  <PRE>
  	dx = x - xc
  	dy = y - yc
  	dX = dx * cos(pa) + dy * sin(pa)
  	dY = (-dx * sin(pa) + dy * cos(pa)) / ar
  	R = sqrt (dX ** 2 + dY ** 2)
  </PRE>
  <P>
  where dx and dy are the object coordinates relative to the object
  center,  dX and dY are the object coordinates in the transformed
  circular coordinates, and R is the circularly symmetric radius.
  The transformation parameters are the axial ratio <I>ar</I>
  defined as the ratio of the minor axis to the major axis,
  and the position angle <I>pa</I> defined counterclockwise from
  the x axis.
  <P>
  The <I>radius</I> parameter defines the size, in pixels, of the model
  object (before seeing for the galaxies) in the output image.  It
  consistently refers to the major axis of the object but its meaning
  does depend on the model.  For the gaussian and moffat profiles it is
  defined as the half-intensity radius.  For the sersic, expdisk, and devauc
  profiles it is defined as the half-flux radius.  For the user specified
  profiles it is the radius of the last profile point.  And for the image
  templates it is the radius of the image along the first or x axis given
  by one-half of the image dimension; i.e. nc/2.
  <P>
  The profiles of the analytic functions extend to infinity so a dynamic
  range, the ratio of the peak intensity to the cutoff intensity, is imposed
  to cutoff the profiles.  The <I>dynrange</I> package parameter applies to
  the stellar and galaxy analytic profiles.  The larger this parameter the
  further the profile extends, particularly for the large index Sersic and De
  Vaucouleurs models.  When modeling large galaxies this has a fairly strong
  affect on the execution time because the overall extent of the images
  becomes rapidly greater.  Only for very high signal-to-noise objects will
  the cutoff be noticeable.  A correction is made to account for lost light
  (light beyond the modeled dynamic range) so that an aperture magnitude
  will give the correct value for an object of the specified total magnitude.
  This can become quite significant for larger index Sersic profiles and
  for the default dynamic range.
  <P>
  The object models are integrated over the size of the image pixels.  This
  is done by subsampling, dividing up a pixel into smaller pieces called
  subpixels.  For the image templates a bilinear surface interpolation
  function is used and integrated analytically over the extent of the
  subpixels.  The user cumulative one dimensional profiles are first
  converted to intensity profiles.  The various intensity profiles are then
  binned into pixel fluxes per subpixel on a grid much finer than the
  subpixel spacing.  Then for any particular radius and object center the
  appropriate subpixel flux can be determined quickly and accurately.
  <P>
  The number of subpixels per image pixel is determined by the package
  parameters <I>nxsub</I>, <I>nysub</I>, <I>nxgsub</I>, and <I>nygsub</I>.  The
  first two apply to the stars and the PSF and the latter two apply to the
  galaxies.  Typically the subsampling will be the same in each dimension.
  The galaxies are generally  subsampled less since they will have less
  rapidly changing profiles and are convolved by the PSF.  Also, the stars
  are computed only a few times and then scaled and moved, as described
  below, while each galaxy needs to be computed separately.  Therefore, one
  can afford greater precision in the stars than in the galaxies.
  <P>
  Given an image of several hundred pixels subsampled by a factor of 100
  (10 x 10) this will be a very large number of computations.  A
  shortcut to reduce this number of operations is allow the number
  of subpixels to change as a function of distance from the
  profile center.  Since the profile center is where the intensity
  changes most rapidly with position, the greatest subsampling is needed for
  the pixel nearest the center.  Further from the object center the intensity
  changes more slowly and the number of subpixels may be reduced.
  Thus, the number of subpixels in each dimension in each pixel is
  decreased linearly with distance from the profile center.  For example,
  a pixel which is 3.2 pixels from the profile center will have
  <I>nxsub</I> - 3 subpixels in the x dimension.  There is, of course, a
  minimum of one subpixel per pixel or, in other words, no subsampling
  for the outer parts of the objects.  By adjusting the subsampling
  parameters one can set the degree of accuracy desired at the trade off of
  greatly different execution times.
  <P>
  The star shapes are assumed constant over the images and only their
  position and magnitude change.  Thus, rather than compute each desired
  star from the model profile or image template, a normalized star
  template is computed once, using the spatial transformation and
  subsampling operations described above, and simply scaled each time to
  achieve the desired magnitude and added at the requested position.
  However, the apparent star shape does vary depending on where its
  center lies within an image pixel.  To handle this a set of
  normalized star templates is precomputed over a grid of centers
  relative to the center of a pixel.  Then the template with center
  nearest to that requested, relative to a pixel center, is used.  The
  number of such templates is set by the package parameters <I>nxc</I> and
  <I>nyc</I> where the two axis typically have the same values.  The
  larger the number of centers the more memory and startup time required
  but the better the representation of this sampling effect.  The choice
  also depends on the scale of the stars since the larger the star
  profile compared to a pixel the smaller the subcentering effect is.
  This technique allows generating images with many stars, such as a
  globular cluster or a low galactic latitude field, quite
  efficiently.
  <P>
  Unlike the stars, the galaxies will each have different profiles,
  ellipticities, and position angles and so templates cannot be used (except
  for special test cases as mentioned later).  Another difference is that the
  galaxy models need to be convolved by the PSF; i.e. the shapes are defined
  prior to seeing.  The PSF convolution must also be subsampled and the
  convolution operation requires as many operations as the number of pixels
  in the PSF for each galaxy subpixel.  Thus, computing seeing convolved,
  well subsampled, large galaxy images is the most demanding task of all,
  requiring all the shortcuts described above (larger and variable
  subsampling and the subpixel flux approximation) as well as further ones.
  <P>
  The PSF used for convolving galaxies is truncated at a lower dynamic
  range than the stars according to the package parameter
  <I>psfrange</I>.  This reduces the number of elements in the convolution
  dramatically at the expense of losing only a small amount of the flux
  in the wings.  Like the stars, the PSF is precomputed on a grid of
  pixel subcenters and the appropriate PSF template is used for each
  galaxy subpixel convolution.  Unlike the stars, the truncated PSF is
  normalized to unit flux in order to conserve the total flux in the
  galaxies.  For the extended galaxies this approximation has only a very
  small effect.  As with the other approximations one may increase the
  dynamic range of the PSF at the expense of an increase in execution
  time.
  <P>
  There is an exception to using the truncated PSF.  If the size of the
  galaxy because very small, 0.01 pixel, then a stellar image is substituted.
  <P>
  <P>
  OBJECT FILES
  <P>
  The object files contain lines defining stars and galaxies.  Stars
  are defined by three numbers and galaxies by seven or eight as
  represented symbolically below.
  <P>
  <PRE>
             stars:  xc yc magnitude
          galaxies:  xc yc magnitude model radius ar pa &lt;save&gt;
  </PRE>
  <P>
  <DL>
  <DT><B><A NAME="l_xc">xc, yc:</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='xc' Line='xc, yc:'>
  <DD>Object center coordinates.  These coordinates are transformed to image
  coordinates as follows.
  <P>
  <PRE>
  	xc in image = xoffset + xc / distance
  	yc in image = yoffset + yc / distance
  </PRE>
  <P>
  where <I>xoffset</I> and <I>yoffset</I> are the task offset parameters.
  Objects whose image centers fall outside the image dimensions are ignored.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_magnitude">magnitude:</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='magnitude' Line='magnitude:'>
  <DD>Object magnitude.  This is converted to instrumental fluxes as follows.
  <P>
  <PRE>
  	flux = exptime/distance**2 * 10**(-0.4*(magnitude-magzero))
  </PRE>
  <P>
  where <I>exptime</I>, <I>distance</I>, and <I>magzero</I> are task parameters.
  For the analytic star and galaxy models a correction
  is made for lost light due to the finite extent of the image in the
  sense that the flux added to the image will never quite be that
  requested.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_model">model:</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='model' Line='model:'>
  <DD>The types of galaxy models are as follows:
  <DL>
  <DT><B><A NAME="l_sersic">sersic&lt;n&gt;</A></B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='sersic' Line='sersic&lt;n&gt;'>
  <DD>A Sersic model of index n.  The index may real but the value will be rounded
  to the nearest multiple of 0.5 or, equivalently, two times the index value will
  be rounded to an integer.  The index must be between 0.5 and 10.  The Sersic
  model defined as
  <P>
  <PRE>
  	I = exp (-b * (R/radius)**1/n)
  </PRE>
  <P>
  where radius is the major axis scale length corresponding to half of the
  total flux.  The value of b is computed using the formula of Ciotti and
  Bertin (AA v352, p447, 1999);
  <P>
  <PRE>
  	b = 2n - 1/3 + 4/(405n) + 46 / (25515n^2)
  </PRE>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_expdisk">expdisk</A></B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='expdisk' Line='expdisk'>
  <DD>An exponential disk model defined as
  <P>
  <PRE>
  	I = exp (-b * R/radius)
  </PRE>
  <P>
  where radius is the major axis scale length corresponding to half of the total
  flux and b is computed as with the Sersic model for n=1.  In fact, the
  algorithm is identical with that for the Sersic model using n=1.  Note that
  because of this there will be slight differences with the earlier versions.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_devauc">devauc</A></B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='devauc' Line='devauc'>
  <DD>A De Vaucouleurs profile defined as
  <P>
  <PRE>
  	I = exp (-b * (R/radius)**1/4)
  </PRE>
  <P>
  where radius is the major axis scale length corresponding to half of the total
  flux and b is computed as with the Sersic model for n=4.  In fact, the
  algorithm is identical with that for the Sersic model using n=4.  Note that
  because of this there will be slight differences with the earlier versions.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">&lt;image&gt;</A></B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='' Line='&lt;image&gt;'>
  <DD>If not one of the profiles above an image of the specified name is
  sought.  If found the center of the template image is assumed to be the
  center of the object and the image template is scaled so that the
  radius of the template is given by the major axis scale radius parameter.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">&lt;profile file&gt;</A></B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='' Line='&lt;profile file&gt;'>
  <DD>If not one of the above a text file giving a cumulative flux profile from
  the center to the edge is sought.  If found the profile defines
  a model galaxy of extent to the last profile point given by
  the major axis scale radius parameter.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_radius">radius:</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='radius' Line='radius:'>
  <DD>Major axis scale radius parameter in pixels as defined above for the different
  galaxy models.  The actual image radius is modified as follows.
  <P>
  	radius in image = radius / distance
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ar">ar:</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='ar' Line='ar:'>
  <DD>Minor to major axis axial ratio.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_pa">pa:</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='pa' Line='pa:'>
  <DD>Major axis position angle in degrees measured counterclockwise from the X axis.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_save">save:</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='save' Line='save:'>
  <DD>If a large number of identically shaped galaxies (size, axial ratio,
  and position angle) located at the same subpixel (the same x and y
  fractional part) but with varying magnitudes is desired then by
  putting the word "<TT>yes</TT>" as the eighth field the model will be saved
  the first time and reused subsequent times.  This speeds up the execution.
  There may certain algorithm testing situations where this might be useful. 
  </DD>
  </DL>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Create a galaxy cluster with a power law distribution of field galaxies
  and stars as background/foreground.
  <P>
  <PRE>
      ar&gt; gallist galaxies.dat 100 spatial=hubble lum=schecter egal=.8
      ar&gt; gallist galaxies.dat 500
      ar&gt; starlist galaxies.dat 100
      ar&gt; mkobjects galaxies obj=galaxies.dat gain=3 rdnoise=10 poisson+
  </PRE>
  <P>
  Making the image takes about 5 minutes (2.5 min cpu) on a SPARCstation 1.
  <P>
  2. Create a uniform artificial starfield of 5000 stars for a 512 square image.
  <P>
  <PRE>
      ar&gt; starlist starfield.dat 5000
      ar&gt; mkobjects starfield obj=starfield.dat gain=2 rdnoise=10 poisson+
  </PRE>
  <P>
  This example takes about a minute on a SPARCstation 1.
  <P>
  3. Create a globular cluster field of 5000 stars for a 512 square image.
  <P>
  <PRE>
      ar&gt; starlist gc.dat 5000 spat=hubble lum=bands
      ar&gt; mkobjects gc obj=gc.dat gain=2 rdnoise=10 poisson+
  </PRE>
  <P>
  This example takes about a minute on a SPARCstation 1.
  <P>
  4. Add stars to an existing image for test purposes.
  <P>
  <PRE>
      ar&gt; mkobjects starfield obj=STDIN gain=2 pois+ magzero=30
      100 100 20
      100 200 21
      200 100 22
      200 200 23
      [EOF]
  </PRE>
  <P>
  5. Look at the center of the globular cluster with no noise and very
  good seeing.
  <P>
  <PRE>
  	cl&gt; mkobjects gc1 obj=gc.dat nc=400 nl=400 distance=.5 \<BR>
  	&gt;&gt;&gt; xo=-313 yo=-313 radius=.1
  </PRE>
  <P>
  The offset parameters are used to recenter the cluster from
  (256,256) in the data file to (200,200) in the expanded field.
  This example takes 30 sec (5 sec CPU) on a SPARCstation 1.  To expand
  and contract about a fixed point define the object list to have an
  origin at zero.
  <P>
  <PRE>
      ar&gt; starlist gc.dat 5000 spat=hubble lum=bands xmin=-256 xmax=256 \<BR>
      &gt;&gt;&gt; ymin=-256 ymax=256
      ar&gt; mkobjects gc obj=gc.dat xo=257 yo=257 gain=2 rdnoise=10 poisson+
      ar&gt; mkobjects gc1 obj=gc.dat xo=257 yo=257 gain=2 \<BR>
      &gt;&gt;&gt; distance=.5 rdnoise=10 poisson+
  </PRE>
  <P>
  6. Make an image of dev$pix at various distances and orientation.  First we
  must subtract the background.
  <P>
  <PRE>
  	cl&gt; imarith dev$pix - 38 pix
  	cl&gt; mkobjects pix1 obj=STDIN nc=200 nl=200 back=1000 \<BR>
  	&gt;&gt;&gt; magzero=30 rd=10 poi+
  	50 50 15.0 pix 40 1 0
  	150 50 15.6 pix 30 .8 45
  	50 150 16.5 pix 20 .6 90
  	150 150 17.1 pix 15 .4 135
  	[EOF]
  </PRE>
  <P>
  It would be somewhat more efficient to first block average the
  template since the oversampling in this case is very large.
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_revisions">REVISIONS</A></H2>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_MKOBJECTS">MKOBJECTS V2.11+</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='MKOBJECTS' Line='MKOBJECTS V2.11+'>
  <DD>The random number seed can be set from the clock time by using the value
  "<TT>INDEF</TT>" to yield different random numbers for each execution.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_MKOBJECTS">MKOBJECTS V2.11</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='MKOBJECTS' Line='MKOBJECTS V2.11'>
  <DD>The default value of "<TT>ranbuf</TT>" was changed to zero.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  gallist, starlist, mknoise, mkheader
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>