.. _allstar:

allstar — Group and fit psf to multiple stars simultaneously
============================================================

**Package: daophot**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  allstar -- group and fit psf to multiple stars simultaneously
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  allstar image photfile psfimage allstarfile rejfile subimage
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>image</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD>The list of images containing the stars to be fit.
  </DD>
  </DL>
  <DL>
  <DT><B>photfile</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='photfile' Line='photfile'>
  <DD>The input photometry files containing the initial estimates of the positions,
  sky values, and magnitudes of the stars to be fit. There must be one input
  photometry file for every input image.  If photfile is "<TT>default</TT>", "<TT>dir$default</TT>",
  or a directory specification, then ALLSTAR looks for a file with the name
  image.mag.? where ? is the highest existing version number. Photfile is usually
  the output of the DAOPHOT PHOT task but may also be the output of the PSF, PEAK
  and NSTAR tasks, or the ALLSTAR task itself.
  </DD>
  </DL>
  <DL>
  <DT><B>psfimage</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='psfimage' Line='psfimage'>
  <DD>The list of images containing the PSF models computed by the DAOPHOT PSF task.
  The number of PSF images must be equal to the number of input images. If
  psfimage is "<TT>default</TT>", "<TT>dir$default</TT>", or a directory specification, then PEAK
  will look for an image with the name image.psf.?, where ? is the highest
  existing version number.
  </DD>
  </DL>
  <DL>
  <DT><B>allstarfile</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='allstarfile' Line='allstarfile'>
  <DD>The list of output photometry files. There must be one output photometry
  file for every input image.  If allstarfile is "<TT>default</TT>", "<TT>dir$default</TT>", or a
  directory specification, then ALLSTAR will write an output file with the name
  image.als.? where ? is the next available version number. Allstarfile is a text
  database if the DAOPHOT package parameter text is "<TT>yes</TT>", an STSDAS table
  database if it is "<TT>no</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>rejfile</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rejfile' Line='rejfile'>
  <DD>The list of output rejected photometry files containing the positions and sky
  values of stars that could not be fit. If rejfile is undefined, results for all
  the stars in photfile are written to <I>allstarfile</I>, otherwise only the stars
  which were successfully fit are written to <I>allstarfile</I> and the remainder
  are written to rejfile. If rejfile is "<TT>default</TT>", "<TT>dir$default</TT>", or a directory
  specification ALLSTAR writes an output file with the name image.als.? where ? is
  the next available version number. Otherwise rejfile must specify one output
  photometry file for every input image. Rejfile is a text database if the
  DAOPHOT package parameter <I>text</I> is "<TT>yes</TT>", an STSDAS binary table database
  if it is "<TT>no</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>subimage</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='subimage' Line='subimage'>
  <DD>The list of output images with the fitted stars subtracted. There must be one
  subtracted image for every input image. If subimage is "<TT>default</TT>", "<TT>dir$default</TT>",
  or a directory specification, then ALLSTAR will create an image with the name
  image.sub.? where ? is the next available version number. Otherwise
  <I>subimage</I> must specify one output image for every image in <I>image</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>datapars = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='datapars' Line='datapars = ""'>
  <DD>The name of the file containing the data dependent parameters. The parameters
  <I>scale</I>, <I>datamin</I>, and <I>datamax</I> are located here. If datapars
  is undefined then the default parameter set in uparm directory is used.
  </DD>
  </DL>
  <DL>
  <DT><B>daopars = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='daopars' Line='daopars = ""'>
  <DD>The name of the file containing the daophot fitting parameters. The parameters
  <I>psfrad</I> and <I>fitrad</I> are located here. If <I>daopars</I> is undefined
  then the default parameter set in uparm directory is used.
  </DD>
  </DL>
  <DL>
  <DT><B>wcsin = "<TT>)_.wcsin</TT>", wcsout = "<TT>)_.wcsout</TT>", wcspsf = "<TT>)_.wcspsf</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wcsin' Line='wcsin = ")_.wcsin", wcsout = ")_.wcsout", wcspsf = ")_.wcspsf"'>
  <DD>The coordinate system of the input coordinates read from <I>photfile</I>, of the
  psf model <I>psfimage</I>, and of the output coordinates written to
  <I>allstarfile</I> and <I>rejfile</I> respectively. The image header coordinate
  system is used to transform from the input coordinate system to the "<TT>logical</TT>"
  pixel coordinate system used internally, from the internal logical system to
  the PSF model system, and from the internal "<TT>logical</TT>" pixel coordinate system
  to the output coordinate system. The input coordinate system options are
  "<TT>logical</TT>", "<TT>tv</TT>", "<TT>physical</TT>", and "<TT>world</TT>". The PSF model and output coordinate
  system options are "<TT>logical</TT>", "<TT>tv</TT>", and "<TT>physical</TT>". The image cursor coordinate
  system is assumed to be the "<TT>tv</TT>" system.
  <DL>
  <DT><B>logical</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='logical' Line='logical'>
  <DD>Logical coordinates are pixel coordinates relative to the current image.
  The  logical coordinate system is the coordinate system used by the image
  input/output routines to access the image data on disk. In the logical
  coordinate system the coordinates of the first pixel of a  2D image, e.g.
  dev$ypix  and a 2D image section, e.g. dev$ypix[200:300,200:300] are
  always (1,1).
  </DD>
  </DL>
  <DL>
  <DT><B>tv</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='tv' Line='tv'>
  <DD>Tv coordinates are the pixel coordinates used by the display servers. Tv
  coordinates  include  the effects of any input image section, but do not
  include the effects of previous linear transformations. If the input
  image name does not include an image section, then tv coordinates are
  identical to logical coordinates.  If the input image name does include a
  section, and the input image has not been linearly transformed or copied from
  a parent image, tv coordinates are identical to physical coordinates.
  In the tv coordinate system the coordinates of the first pixel of a
  2D image, e.g. dev$ypix and a 2D image section, e.g. dev$ypix[200:300,200:300]
  are (1,1) and (200,200) respectively.
  </DD>
  </DL>
  <DL>
  <DT><B>physical</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='physical' Line='physical'>
  <DD>Physical coordinates are pixel coordinates invariant  with respect to linear
  transformations of the physical image data.  For example, if the current image
  was created by extracting a section of another image,  the  physical
  coordinates of an object in the current image will be equal to the physical
  coordinates of the same object in the parent image,  although the logical
  coordinates will be different.  In the physical coordinate system the
  coordinates of the first pixel of a 2D image, e.g. dev$ypix and a 2D
  image section, e.g. dev$ypix[200:300,200:300] are (1,1) and (200,200)
  respectively.
  </DD>
  </DL>
  <DL>
  <DT><B>world</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='world' Line='world'>
  <DD>World coordinates are image coordinates in any units which are invariant
  with respect to linear transformations of the physical image data. For
  example, the ra and dec of an object will always be the same no matter
  how the image is linearly transformed. The units of input world coordinates
  must be the same as those expected by the image header wcs, e. g.
  degrees and degrees for celestial coordinate systems.
  </DD>
  </DL>
  The wcsin, wcspsf, and wcsout parameters default to the values of the package
  parameters of the same name. The default values of the package parameters
  wcsin, wcspsf,  and wcsout are "<TT>logical</TT>", "<TT>physical</TT>" and "<TT>logical</TT>" respectively.
  </DD>
  </DL>
  <DL>
  <DT><B>cache = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cache' Line='cache = yes'>
  <DD>Cache all the data in memory ? If <I>cache</I> is "<TT>yes</TT>", then ALLSTAR attempts
  to preallocate sufficient space to store the input image plus the two
  image-sized working arrays it requires, plus space for the starlist, in memory.
  This can significantly reduce the total execution time. Users should however
  beware of creating a situation where excessive paging occurs.  If <I>cache</I> =
  "<TT>no</TT>", ALLSTAR operates on subrasters containing the group currently being
  reduced, and writes the intermediate results to temporary scratch images. This
  option will work on any-sized image (unless a single group becomes the size of
  the entire image!) but can become slow of there are a large number of disk
  accesses. Users may wish to experiment to see which mode of operation suits
  their system best.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = "<TT>)_.verbose</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = ")_.verbose"'>
  <DD>Print messages about the progress of the task ? Verbose can be set to the
  DAOPHOT package parameter value (the default), "<TT>yes</TT>", or "<TT>no</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>verify = "<TT>)_.verify</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verify' Line='verify = ")_.verify"'>
  <DD>Verify the critical ALLSTAR task parameters. Verify can be set to the daophot
  package parameter value (the default), "<TT>yes</TT>", or "<TT>no</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>update = "<TT>)_.update</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='update' Line='update = ")_.update"'>
  <DD>Update the critical ALLSTAR task parameters if <I>verify</I> = "<TT>yes</TT>".  Update
  can be set to the daophot package parameter value (the default), "<TT>yes</TT>", or
  "<TT>no</TT>".
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  ALLSTAR computes x and y centers, sky values, and magnitudes for the stars in
  <I>photfile</I> by fitting the PSF <I>psfimage</I> to groups of stars in the IRAF
  image  <I>image</I>. Initial estimates of the centers, sky values, and
  magnitudes, are read from the photometry list <I>photfile</I>. ALLSTAR groups
  the stars dynamically, performing a regrouping operation after every iteration.
  The new computed centers, sky values, and magnitudes are written to
  <I>allstarfile</I> along with the number of iterations it took to fit the
  star, the goodness of fit statistic chi, and the image sharpness statistic
  sharp. If <I>rejfile</I> is not null ("<TT></TT>"), only stars that are successfully fit
  are written to <I>allstarfile</I>, and the remainder are written to
  <I>rejfile</I>. Otherwise all the stars are written to <I>allstarfile</I>.
  <I>Allstarfile</I> and <I>rejfile</I> are text databases if the DAOPHOT package
  parameter <I>text</I> is "<TT>yes</TT>", STSDAS table databases if it is "<TT>no</TT>". An image
  with all the fitted stars subtracted out is written to <I>subimage</I>. In
  effect ALLSTAR performs the combined operations of GROUP, GRPSELECT, NSTAR,
  and SUBSTAR.
  <P>
  The coordinates read from <I>photfile</I> are assumed to be in coordinate
  system defined by <I>wcsin</I>. The options are "<TT>logical</TT>", "<TT>tv</TT>", "<TT>physical</TT>",
  and "<TT>world</TT>" and the transformation from the input coordinate system to the
  internal "<TT>logical</TT>" system is defined by the image coordinate system. The
  simplest default is the "<TT>logical</TT>" pixel system. Users working on with image
  sections but importing pixel coordinate lists generated from the parent image
  must use the "<TT>tv</TT>" or "<TT>physical</TT>" input coordinate systems.
  <P>
  The coordinate system of the PSF model is the coordinate system defined by the
  <I>wcspsf</I> parameter. Normally the PSF model was derived from the input image
  and this parameter default to "<TT>logical</TT>". However if the PSF model was derived
  from a larger image which is a "<TT>parent</TT>" of the input image, then wcspsf should
  be set to "<TT>tv</TT>" or "<TT>physical</TT>" depending on the circumstances.
  <P>
  The coordinates written to <I>allstarfile</I> and <I>rejfile</I> are in the
  coordinate system defined by <I>wcsout</I>. The options are "<TT>logical</TT>", "<TT>tv</TT>", and
  "<TT>physical</TT>". The simplest default is the "<TT>logical</TT>" system.  Users wishing to
  correlate the output coordinates of objects measured in image sections or
  mosaic pieces with coordinates in the parent image must use the "<TT>tv</TT>" or
  "<TT>physical</TT>" coordinate systems.
  <P>
  By default ALLSTAR computes new centers for all the stars in <I>photfile</I>.
  However if the DAOPARS parameter <I>recenter</I> is "<TT>no</TT>", ALLSTAR assumes that
  the x and y centers in <I>photfile</I> are the true centers and does not refit
  them. This option can be quite useful in cases where accurate center values
  have been derived from an image that has been through some non-linear image
  restoration algorithm, but the photometry must be derived from the original
  unrestored image.
  <P>
  By default (<I>groupsky</I> = "<TT>yes</TT>") ALLSTAR computes the sky value for each
  group by averaging the individual sky values in <I>photfile</I> for all the
  stars in the group. If <I>groupsky</I> = "<TT>no</TT>", the sky value for each pixel
  which contributes to the group fit is set equal to the mean of the sky values
  for those stars for which the pixel falls within one fitting radius.  If the
  DAOPARS parameter <I>fitksy</I> is "<TT>yes</TT>", then ALLSTAR recomputes the individual
  sky values before averaging over the group, by, every third iteration,
  subtracting off the current best fit for the star and using the pixel values in
  the annulus defined by the DAOPARS parameters <I>sannulus</I> and <I>wsannulus</I>
  to recompute the sky. The actual sky recomputation is done by averaging forty
  percent of the sky pixels centered on the median of the distribution.
  Recomputing the sky can significantly reduce the scatter in the magnitudes in
  regions where the sky background is varying rapidly.
  <P>
  Only pixels within the good data range defined by the DATAPARS task parameters
  <I>datamin</I> and <I>datamax</I> are included in the fit.  Most users set
  <I>datamin</I> and <I>datamax</I> so as to exclude pixels outside the linearity
  regime of the detector. By default all the data is fit.  Users are advised to
  determine accurate values for these parameters for their detector and set the
  values in DATAPARS before beginning any DAOPHOT reductions.
  <P>
  Only pixels within the fitting radius parameter <I>fitrad</I> / <I>scale</I> are
  included in the fit for each star. <I>Fitrad</I> is located in the DAOPARS task
  and <I>scale</I> is located in the DATAPARS task. Since the non-linear
  least-squares fits normally compute three unknowns, the x and y position of
  the star's centroid and its brightness, the value of <I>fitrad</I>  must be
  sufficiently large to include at least three pixels in the fit for each star.
  To accelerate the convergence of the non-linear least-squares fitting algorithm
  pixels within <I>fitrad</I> are assigned weights which are  inversely
  proportional to the radial distance of the pixel from the x and y centroid of
  the star, falling from a maximum at the centroid to zero at the fitting radius.
  <I>Fitrad</I> must be sufficiently large to include at least three pixels with
  non-zero radial weights in the fit for each star. ALLSTAR arbitrarily imposes a
  minimum number of good pixels limit of four. Values of <I>fitrad</I> close to
  the full-width at half-maxima of the PSF are recommended.
  <P>
  ALLSTAR computes a weighted fit to the PSF. The weight of each pixel is
  computed by combining, the radial weighting function described above, with
  weights derived from the random errors ALLSTAR predicts based on the detector
  noise characteristics specified by the DATAPARS parameters <I>readnoise</I> and
  <I>epadu</I>, and the flat-fielding and profile interpolation errors specified
  by the DAOPARS task <I>flaterr</I> and <I>proferr</I> parameters. Both to obtain
  optimal fits, and because ALLSTAR employs a conservative formula for reducing
  the weights of deviant pixels (parametrized by the <I>clipexp</I> and
  <I>cliprange</I> parameters in the DAOPARS task) which do not approach the model
  as the fit proceeds, which depends on <I>readnoise</I>,  <I>epadu</I>,
  <I>flaterr</I>, and <I>proferr</I>, users are strongly advised to determine those
  parameters accurately and to enter their values in DATAPARS and DAOPARS before
  beginning any DAOPHOT reductions.
  <P>
  By default for each group of stars to be fit during each iteration, ALLSTAR
  extracts a subraster from <I>image</I> which extends approximately <I>fitrad</I>
  / <I>scale</I> + 1 pixels wide past the limiting values of x and y coordinates
  of the stars in the group. <I>Fitrad</I> is the fitting radius specified in the
  DAOPARS task. <I>Scale</I> is the image scale specified by the DATAPARS task.
  <I>Fitrad</I> may be less than or equal to but can never exceed the value of the
  image header parameter "<TT>PSFRAD</TT>" in <I>psfimage</I>.
  <P>
  If the <I>cache</I> parameter is set to "<TT>yes</TT>" then ALLSTAR attempts to store all
  the vectors and arrays in memory.  This can significantly reduce the system
  overhead but may cause excessive paging on machines with a small amount of
  memory. For large images it may be necessary to set <I>cache</I> to "<TT>no</TT>", and
  use the disk for scratch storage. Users should experiment to see what suits
  them best.
  <P>
  As well as the computed x and y centers, sky values, and magnitudes, ALLSTAR
  outputs the number of times the PSF fit had to be iterated before convergence
  was achieved. The minimum number of iterations is four. The maximum number of
  iteration permitted is specified by the <I>maxiter</I> parameter in the DAOPARS
  task. Obviously the results for stars which have reached the maximum iteration
  count should be viewed with suspicion. However since the convergence criteria
  are quite strict, (the computed magnitude must change  by less than .0005
  magnitudes or 0.10 sigma whichever is larger and the x and y centroids must
  change by less than 0.002 pixels from one iteration to the next), even these
  stars may be reasonably well measured.
  <P>
  ALLSTAR computes a goodness of fit statistic chi which is essentially the ratio
  of the observed pixel-to-pixel scatter in the fitting residuals to the expected
  scatter. Since the expected scatter is dependent on the DATAPARS task parameters
  <I>readnoise</I> and <I>epadu</I>, and the DAOPARS parameters <I>flaterr</I> and
  <I>proferr</I>, it is important for these values to be set correctly. A plot of
  chi versus magnitude should scatter around unity with little or no trend in chi
  with magnitude, except at the bright end where saturation effects may be
  present.
  <P>
  Finally ALLSTAR computes the statistic sharp which estimates the intrinsic
  angular size of the measured object outside the atmosphere.  Sharp is roughly
  defined as the difference between the square of the width of the object and the
  square of the width of PSF. Sharp has values close to zero for single stars,
  large positive values for blended doubles and partially resolved galaxies and
  large negative values for cosmic rays and blemishes.
  <P>
  ALLSTAR implements a sophisticated star rejection algorithm. First of all any
  group of stars which is more than a certain size is not reduced. This maximum
  group size is specified by the <I>maxgroup</I> parameter in the DAOPARS task.
  Large groups may run into numerical precision problems during the fits, so
  users should increase this parameter with caution.  ALLSTAR however, in
  contrast to NSTAR, attempts to subdivide large groups. If the group is too
  dense to reduce in size, ALLSTAR throws out the faintest star in the group
  and tries to rereduce it.  If two stars in a group have centroids separated
  by a critical distance currently set arbitrarily to 0.37 * the FWHM of the
  stellar core and their photocentric position and combined magnitude is assigned
  to the brighter of the two and the fainter is eliminated. Any star which
  converges to magnitude  12.5 magnitudes greater than the magnitude of the PSF
  is considered to be non-existent and eliminated from the group.
  <P>
  After iteration 5, if the faintest star in the group has a brightness less
  than one sigma above zero it is eliminated.  After iteration 10 if the faintest
  star in the group has a brightness less than 1.5 sigma above zero it is
  eliminated. After iteration 15, or whenever the solutions has converged
  whichever comes first, if the faintest star in the group has a brightness less
  than 2.0 sigma above zero it is eliminated. After iterations 5, 10 and 15 if
  two stars are separated by more than 0.37 * FWHM and less than 1.0 * FWHM and
  if the fainter of the two is more uncertain than 1.0, 1.5 or 2.0 sigma
  respectively the fainter one is eliminated.
  <P>
  ALLSTAR replaces the functionality of the GROUP, GRPSELECT, NSTAR and SUBSTAR
  task. However the user has little control over the grouping process and does
  not know at the end which stars were fit together. The grouping process is
  dynamic, as the groups are recomputed after each iteration, and stars can be
  fit and leave the group at any point after the fourth iteration. Therefore the
  quality of the fits may vary over the image as a function of crowding in an
  unknown way. However ALLSTAR is in most cases the routine of choice.  NSTAR
  is the task of choice when a user wants to maintain control over the
  composition of the stellar groups.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Output</H3>
  <! BeginSection: 'OUTPUT'>
  <UL>
  <P>
  If <I>verbose</I> = yes, a single line is output to the terminal for each star
  fit or rejected. Full output is written to <I>allstarfile</I> and <I>rejfile</I>.
  At the beginning of these two files a header listing the current values of the
  parameters is written. For each star fit/rejected the following quantities are
  written to the output file.
  <P>
  <PRE>
  	id  xcenter  ycenter  mag  merr  msky  niter  sharpness  chi
  	    pier  perr
  </PRE>
  <P>
  Id is the id number of the star. Xcenter and ycenter are the fitted coordinates
  in pixels. Mag and merr are the fitted magnitude and magnitude error
  respectively. Msky is the individual sky value for the star. Niter is the
  number of iterations it took to fit the star and sharpness and chi are the
  sharpness and goodness of fit statistic respectively.  Pier and perror are the
  photometry error code and accompanying error message respectively.
  <P>
  </UL>
  <! EndSection:   'OUTPUT'>
  <H3>Errors</H3>
  <! BeginSection: 'ERRORS'>
  <UL>
  <P>
  If no errors occur during the fitting process then pier is 0. Non-zero
  values of pier flag the following error conditions.
  <P>
  <PRE>
  	0		# No error
  	1		# The star is in a group too large to fit
  	2		# The sky is undefined
  	3		# There are too few good pixels to fit the star
  	4		# The fit is singular
  	5		# The star is too faint
  	6		# The star has merged with a brighter star
  	7		# The star is off the image
  </PRE>
  <P>
  </UL>
  <! EndSection:   'ERRORS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Fit the PSF to a list stars in the test image dev$ypix. Good stars for
  making the PSF model can be found at (442,410), (348,189), and (379,67).
  <P>
  <PRE>
     da&gt; datapars.epadu = 14.0
     da&gt; datapars.readnoise = 75.0
  <P>
         ... set the gain and readout noise for the detector
  <P>
     da&gt; daofind dev$ypix default fwhmpsf=2.5 sigma=5.0 threshold=20.0
  <P>
          ... answer verify prompts
  <P>
          ... find stars in the image
  <P>
          ... answer will appear in ypix.coo.1
  <P>
      da&gt; phot dev$ypix default default annulus=10. dannulus=5.       \<BR>
          apertures = 3.0
  <P>
          ... answer verify prompts
  <P>
          ... do aperture photometry on the detected stars
  <P>
          ... answer will appear in ypix.mag.1
  <P>
      da&gt; display dev$ypix 1
  <P>
      da&gt; psf dev$ypix default "" default default default psfrad=11.0 \<BR>
          fitrad=3.0 mkstars=yes display=imdr
  <P>
          ... verify the critical parameters
  <P>
          ... move the image cursor to a candidate star and hit the a key,
              a plot of the stellar data appears
  <P>
          ... type ? for a listing of the graphics cursor menu
  <P>
          ... type a to accept the star, d to reject it
  <P>
  <P>
          ... move to the next candidate stars and repeat the previous
              steps
  <P>
          ... type l to list all the psf stars
  <P>
          ... type f to fit the psf
  <P>
          ... move cursor to first psf star and type s to see residuals,
              repeat for all the psf stars
  <P>
          ... type w to save the PSF model
  <P>
          ... type q to quit, and q again to confirm
  <P>
          ... the output will appear in ypix.psf.1.imh, ypix.pst.1 and
              ypix.psg.1
  <P>
      da&gt; allstar dev$ypix default default default default default
  <P>
          ... verify the prompts
  <P>
          ... the results will appear in ypix.als.1 and ypix.arj.1
  <P>
      da&gt; pdump ypix.als.1 sharpness,chi yes | graph
  <P>
          ... plot chi versus sharpness, the stars should cluster around
              sharpness = 0.0 and chi = 1.0, note that the frame does
              not have a lot of stars
  <P>
      da&gt; display ypix.sub.1 2
  <P>
          ... note that the psf stars subtract reasonably well but other
              objects which are not stars don't
  </PRE>
  <P>
  <P>
  2. Repeat example 1 but refit the sky using an annulus with an inner sky
  radius of 3.0 and an outer radius of 15.0.
  <P>
  <PRE>
      da&gt; allstar dev$ypix default default default default default fitsky+ \<BR>
          sannulus=3.0 wsannulus=12.0
  <P>
          ... verify the prompts
  <P>
          ... the results will appear in ypix.als.2 and ypix.arj.2
  <P>
      da&gt; pdump ypix.als.2 sharpness,chi yes | graph
  <P>
          ... plot chi versus sharpness, the stars should cluster around
              sharpness = 0.0 and chi = 1.0, note that the frame does
              not have a lot of stars
  <P>
      da&gt; display ypix.sub.2 2
  <P>
          ... note that the psf stars subtract reasonably well but other
              objects which are not stars don't
  </PRE>
  <P>
  <P>
  <P>
  3. Run allstar on a section of the input image using the group file and PSF
  model derived in example 1 for the parent image and writing the results
  in the coordinate system of the parent image.
  <P>
  <PRE>
      da&gt; allstar dev$ypix[150:450,150:450] default default default default \<BR>
          default wcsin=tv wcspsf=tv wcsout=tv
  <P>
          ... answer the verify prompts
  <P>
          ... fit the stars
  <P>
          ... the results will appear in ypix.als.3 and ypix.arj.3
  <P>
      da&gt; display dev$ypix[150:450,150:450] 1
  <P>
          ... display the image
  <P>
      da&gt; pdump ypix.als.3 xc,yc yes | tvmark 1 STDIN col=204
  <P>
          ... mark the stars on the original image
  <P>
      da&gt; display ypix.sub.3 2
  <P>
         ... display the subtracted image section
  <P>
  </PRE>
  <P>
  <P>
  4. Run allstar exactly as in example 1 but submit the task to the background.
  Turn off verify and verbose.
  <P>
  <PRE>
      da&gt; allstar dev$ypix default default default default default verbose- \<BR>
          verify- &amp;
  <P>
          ... the results will appear in ypix.als.4 and ypix.arj.4
  </PRE>
  <P>
  <P>
  4. Run ALLSTAR exactly as in example 3 but turn caching off.
  <P>
  <PRE>
      da&gt; allstar m92 m92.grp.1 m92.psf.1 default "" default verb+ veri- \<BR>
          cache- &gt; allstar.out &amp; 
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  datapars,daopars,peak,nstar
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'OUTPUT' 'ERRORS' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
