.. _phot:

phot — Compute sky values and initial magnitudes for a list of stars
====================================================================

**Package: daophot**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  phot -- do aperture photometry on a list of stars
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  phot image coords output
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>image</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD>The list of images containing the objects to be measured.
  </DD>
  </DL>
  <DL>
  <DT><B>coords</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='coords' Line='coords'>
  <DD>The list of text files containing initial coordinates for the objects to
  be centered. Objects are listed in coords one object per line with the
  initial coordinate values in columns one and two. The number of coordinate
  files must be zero, one, or equal to the number of images.  If coords is
  "<TT>default</TT>", "<TT>dir$default</TT>", or a directory specification then a coords file name
  of the form dir$root.extension.version is constructed and searched for,
  where dir is the directory, root is the root image name, extension is "<TT>coo</TT>"
  and version is the highest available version number for the file.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>The name of the results file or results directory. If output is
  "<TT>default</TT>", "<TT>dir$default</TT>", or a directory specification then an output file name
  of the form dir$root.extension.version is constructed, where dir is the
  directory, root is the root image name, extension is "<TT>mag</TT>" and version is
  the next available version number for the file. The number of output files
  must be zero, one, or equal to the number of image files.  In both interactive
  and batch mode full output is written to output. In interactive mode
  an output summary is also written to the standard output.
  </DD>
  </DL>
  <DL>
  <DT><B>skyfile = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='skyfile' Line='skyfile = ""'>
  <DD>The list of text files containing the sky values, of the measured objects,
  one object per line with x, y, the sky value, sky sigma, sky skew, number of sky
  pixels and number of rejected sky pixels in columns one to seven respectively.
  The number of sky files must be zero, one, or equal to the number of input
  images. A skyfile value is only requested if <I>fitskypars.salgorithm</I> =
  "<TT>file</TT>" and if PHOT is run non-interactively.
  </DD>
  </DL>
  <DL>
  <DT><B>plotfile = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='plotfile' Line='plotfile = ""'>
  <DD>The name of the file containing radial profile plots of the stars written
  to the output file. If plotfile is defined then a radial profile plot
  is written to plotfile every time a record is written to <I>output</I>.
  The user should be aware that this can be a time consuming operation.
  </DD>
  </DL>
  <DL>
  <DT><B>datapars = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='datapars' Line='datapars = ""'>
  <DD>The name of the file containing the data dependent parameters. The critical
  parameters <I>fwhmpsf</I> and <I>sigma</I> are located here. If <I>datapars</I>
  is undefined then the default parameter set in uparm directory is used.
  </DD>
  </DL>
  <DL>
  <DT><B>centerpars = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='centerpars' Line='centerpars = ""'>
  <DD>The name of the file containing the centering parameters. The critical
  parameters <I>calgorithm</I> and <I>cbox</I> are located here.
  If <I>centerpars</I> is undefined then the default parameter set in
  uparm directory is used.
  </DD>
  </DL>
  <DL>
  <DT><B>fitskypars = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fitskypars' Line='fitskypars = ""'>
  <DD>The name of the text file containing the sky fitting parameters. The critical
  parameters <I>salgorithm</I>, <I>annulus</I>, and <I>dannulus</I> are located here.
  If <I>fitskypars</I> is undefined then the default parameter set in uparm
  directory is used.
  </DD>
  </DL>
  <DL>
  <DT><B>photpars = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='photpars' Line='photpars = ""'>
  <DD>The name of the file containing the photometry parameters. The critical
  parameter <I>apertures</I> is located here.  If <I>photpars</I> is undefined
  then the default parameter set in uparm directory is used.
  </DD>
  </DL>
  <DL>
  <DT><B>interactive = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = no'>
  <DD>Run the task interactively ?
  </DD>
  </DL>
  <DL>
  <DT><B>radplots = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='radplots' Line='radplots = no'>
  <DD>If <I>radplots</I> is "<TT>yes</TT>" and PHOT is run in interactive mode, a radial
  profile of each star is plotted on the screen after the star is measured.
  </DD>
  </DL>
  <DL>
  <DT><B>icommands = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='icommands' Line='icommands = ""'>
  <DD>The image display cursor or image cursor command file.
  </DD>
  </DL>
  <DL>
  <DT><B>gcommands = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='gcommands' Line='gcommands = ""'>
  <DD>The graphics cursor or graphics cursor command file.
  </DD>
  </DL>
  <DL>
  <DT><B>wcsin = "<TT>)_.wcsin</TT>", wcsout = "<TT>)_.wcsout</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wcsin' Line='wcsin = ")_.wcsin", wcsout = ")_.wcsout"'>
  <DD>The coordinate system of the input coordinates read from <I>coords</I> and
  of the output coordinates written to <I>output</I> respectively. The image
  header coordinate system is used to transform from the input coordinate
  system to the "<TT>logical</TT>" pixel coordinate system used internally,
  and from the internal "<TT>logical</TT>" pixel coordinate system to the output
  coordinate system. The input coordinate system options are "<TT>logical</TT>", "<TT>tv</TT>",
  "<TT>physical</TT>", and "<TT>world</TT>". The output coordinate system options are "<TT>logical</TT>",
  "<TT>tv</TT>", and "<TT>physical</TT>". The image cursor coordinate system is assumed to
  be the "<TT>tv</TT>" system.
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
  The wcsin and wcsout parameters default to the values of the package
  parameters of the same name. The default values of the package parameters
  wcsin and wcsout are "<TT>logical</TT>" and "<TT>logical</TT>" respectively.
  </DD>
  </DL>
  <DL>
  <DT><B>cache = "<TT>)_.cache</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cache' Line='cache = ")_.cache"'>
  <DD>Cache the image pixels in memory. Cache may be set to the value of the apphot
  package parameter (the default), "<TT>yes</TT>", or "<TT>no</TT>". By default caching is
  disabled.
  </DD>
  </DL>
  <DL>
  <DT><B>verify = "<TT>)_.verify</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verify' Line='verify = ")_.verify"'>
  <DD>Verify the critical PHOT parameters in non-interactive mode ? Verify can be set
  to the DAOPHOT package parameter value (the default), "<TT>yes</TT>", or "<TT>no</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>update = "<TT>)_.update</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='update' Line='update = ")_.update"'>
  <DD>Update the algorithm parameter values if <I>verify</I> is "<TT>yes</TT>" and
  <I>interactive</I> is "<TT>no</TT>" ?  Update can be set to the DAOPHOT package parameter
  value (the default), "<TT>yes</TT>", or "<TT>no</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = "<TT>)_.verbose</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = ")_.verbose"'>
  <DD>Print results on the screen in non-interactive mode ?  Verbose can be set to
  the DAOPHOT package parameter value (the default), "<TT>yes</TT>", or "<TT>no</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>graphics = "<TT>)_.stdgraph</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = ")_.stdgraph"'>
  <DD>The default graphics device. Graphics may be set to the DAOPHOT package
  parameter value (the default), "<TT>yes</TT>", or "<TT>no</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>display = "<TT>)_.display</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='display' Line='display = ")_.display"'>
  <DD>The default display device.  Display may be set to the DAOPHOT package
  parameter value (the default), "<TT>yes</TT>", or "<TT>no</TT>". By default graphics overlay is
  disabled.  Setting display to one of "<TT>imdr</TT>", "<TT>imdg</TT>", "<TT>imdb</TT>", or "<TT>imdy</TT>" enables
  graphics overlay with the IMD graphics kernel.  Setting display to "<TT>stdgraph</TT>"
  enables PHOT to work interactively from a contour plot.
  <P>
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  PHOT computes accurate centers, sky values, and magnitudes for a list of
  objects in the IRAF image <I>image</I> whose coordinates are read from
  the text file <I>coords</I> or the image display cursor, and writes the
  computed x and y coordinates, sky values, and magnitudes to the text
  file <I>output</I>.
  <P>
  The coordinates read from <I>coords</I> are assumed to be in coordinate
  system defined by <I>wcsin</I>. The options are "<TT>logical</TT>", "<TT>tv</TT>", "<TT>physical</TT>",
  and "<TT>world</TT>" and the transformation from the input coordinate system to
  the internal "<TT>logical</TT>" system is defined by the image coordinate system.
  The simplest default is the "<TT>logical</TT>" pixel system. Users working on with
  image sections but importing pixel coordinate lists generated from the parent
  image must use the "<TT>tv</TT>" or "<TT>physical</TT>" input coordinate systems.
  Users importing coordinate lists in world coordinates, e.g. ra and dec,
  must use the "<TT>world</TT>" coordinate system and may need to convert their
  equatorial coordinate units from hours and degrees to degrees and degrees first.
  <P>
  The coordinates written to <I>output</I> are in the coordinate
  system defined by <I>wcsout</I>. The options are "<TT>logical</TT>", "<TT>tv</TT>",
  and "<TT>physical</TT>". The simplest default is the "<TT>logical</TT>" system. Users
  wishing to correlate the output coordinates of objects measured in
  image sections or mosaic pieces with coordinates in the parent
  image must use the "<TT>tv</TT>" or "<TT>physical</TT>" coordinate systems.
  <P>
  In interactive mode the user may either define the list of objects to be
  measured interactively with the image cursor or create an object list prior
  to running PHOT. In either case the user may adjust the centering, sky fitting,
   and photometry algorithm parameters until a satisfactory fit is achieved
  and optionally store the final results in <I>output</I>. In batch mode the
  initial positions are read from the text file <I>coords</I> or the image
  cursor parameter <I>icommands</I> can be redirected to a text file containing
  a list of cursor commands. In batch mode the current set of algorithm
  parameters is used.
  <P>
  If <I>cache</I> is yes and the host machine physical memory and working set size
  are large enough, the input image pixels are cached in memory. If caching
  is enabled and PHOT is run interactively the first measurement will appear
  to take a long time as the entire image must be read in before the measurement
  is actually made. All subsequent measurements will be very fast because PHOT
  is accessing memory not disk. The point of caching is to speed up random
  image access by making the internal image i/o buffers the same size as the
  image itself. However if the input object lists are sorted in row order and
  sparse caching may actually worsen not improve the execution time. Also at
  present there is no point in enabling caching for images that are less than
  or equal to 524288 bytes, i.e. the size of the test image dev$ypix, as the
  default image i/o buffer is exactly that size. However if the size of dev$ypix
  is doubled by converting it to a real image with the chpixtype task then the
  effect of caching in interactive is can be quite noticeable if measurements
  of objects in the top and bottom halves of the image are alternated.
  <P>
  <P>
  PHOT computes accurate centers for each object using the centering
  parameters defined in <I>centerpars</I>, computes an accurate sky value
  for each object using the sky fitting parameters defined in <I>fitskypars</I>,
   and computes magnitudes using the photometry parameters defined in
  <I>photpars</I>. The image data characteristics of the data are specified
  in <I>datapars</I>.
  <P>
  Unlike the APPHOT versions of PHOT the DAOPHOT version of PHOT does NOT
  recenter the stars, as the default input coordinate list is created
  by the DAOFIND task which itself computes accurate centers for the stars.
  DAOPHOT users should set the CENTERPARS task parameter <I>calgorithm</I>
  to "<TT>centroid</TT>" if they need to measure stars interactively with the
  image display and image display cursor. The PHOT tasks centers provide
  initial guesses for the PSF modeling and fitting routines in the PSF,
  PEAK, NSTAR, and ALLSTAR tasks.
  <P>
  The DAOPHOT version of PHOT sets the sky fitting algorithm to  "<TT>mode</TT>".
  This algorithm which uses the mean and median to estimate the value
  that the sky would have if the star of interest wasn't there, is in most
  cases the one which will give the best results in crowded fields.  Users
  interested in reducing small stellar groups should realizes that they can,
  fix the sky by setting the FITSKYPARS parameter <I>salgorithm</I> to "<TT>constant</TT>"
  and setting <I>skyvalue</I> to the desired sky value, or set the sky
  interactively using the "<TT>radplot</TT>" or "<TT>histplot</TT>" options.  Users with rapidly
  varying sky backgrounds may wish to explore the "<TT>median</TT>" or "<TT>centroid</TT>" sky
  fitting algorithm which can be more stable than the "<TT>mode</TT>" algorithm
  against complex sky pixel histograms.  Users with very few counts in their
  data or with quantized data where the standard deviation is small with
  respect to the quantization level may wish to explore the "<TT>mean</TT>",
  and "<TT>centroid</TT>"  sky fitting algorithms.
  <P>
  The PHOT task sets the instrumental magnitude scale for all the subsequent
  DAOPHOT tasks. Users should be sure they have set the PHOTPARS <I>apertures</I>
  parameter to a reasonable value, and that they have accounted for the
  exposure time by setting either the DATAPARS <I>exposure</I> or <I>itime</I>
  parameters.
  <P>
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Cursor commands</H3>
  <! BeginSection: 'CURSOR COMMANDS'>
  <UL>
  <P>
  The following list of cursor commands are currently available.
  <P>
  <PRE>
  	Interactive Keystroke Commands
  <P>
  ?	Print help
  :	Colon commands
  v	Verify critical parameters
  w	Save current parameters
  d	Plot radial profile of current star
  i	Set parameters interactively using current star
  c	Fit center for current star
  t	Fit sky around cursor
  s	Fit sky around current centered star
  p	Do photometry for current star, using current sky
  o	Do photometry for current star, using current sky, output results
  f	Do photometry for current star
  spbar	Do photometry for current star, output results
  m	Move to next star in coordinate list
  n	Do photometry for next star in coordinate list, output results
  l	Do photometry for remaining stars in coordinate list, output results
  e	Print error messages
  r	Rewind coordinate list
  q	Exit task
  <P>
  <P>
  Photometry parameters are listed or set with the following commands.
  <P>
  	Colon commands
  <P>
  :show	[data/center/sky/phot]	List the parameters
  :m [n]	Move to next [nth] star in coordinate list
  :n [n]	Measure next [nth] star in coordinate list, output results
  <P>
  	Colon Parameter Editing Commands
  <P>
  # Image and file name parameters
  <P>
  :image		[string]	Image name
  :coords		[string]	Coordinate file name
  :output		[string]	Output file name
  <P>
  # Data dependent parameters
  <P>
  :scale		[value]		Image scale (units per pixel)
  :fwhmpsf	[value]		Full width half maximum of PSF (scale units)
  :emission	[y/n]		Emission feature (y), absorption (n)
  :sigma	        [value]		Standard deviation of sky (counts)
  :datamin	[value]		Minimum good data value (counts)
  :datamax	[value]		Maximum good data value (counts)
  <P>
  # Noise parameters
  <P>
  :noise		[string]	Noise model (constant|poisson)
  :gain		[string]	Gain image header keyword
  :ccdread	[string]	Readout noise image header keyword
  :epadu		[value]		Gain (electrons  per adu)
  :readnoise	[value]		Readout noise (electrons)
  <P>
  # Observations parameters
  <P>
  :exposure	[string]	Exposure time image header keyword
  :airmass	[string]	Airmass image header keyword
  :filter		[string]	Filter image header keyword
  :obstime	[string]	Time of observation image header keyword
  :itime 		[value]		Integration time (time units)
  :xairmass	[value]		Airmass value (number)
  :ifilter	[string]	Filter id string
  :otime		[string]	Time of observation (time units)
  <P>
  # Centering algorithm parameters
  <P>
  :calgorithm	[string]	Centering algorithm
  :cbox		[value]		Width of the centering box (scale units)
  :cthreshold	[value]		Centering intensity threshold (sigma)
  :cmaxiter	[value]		Maximum number of iterations
  :maxshift	[value]		Maximum center shift (scale units)
  :minsnratio	[value]		Minimum S/N ratio for centering
  :clean		[y/n]		Clean subraster before centering
  :rclean		[value]		Cleaning radius (scale units)
  :rclip		[value]		Clipping radius (scale units)
  :kclean		[value]		Clean K-sigma rejection limit (sigma)
  <P>
  # Sky fitting algorithm parameters
  <P>
  :salgorithm	[string]	Sky fitting algorithm
  :skyvalue	[value]		User supplied sky value (counts)
  :annulus	[value]		Inner radius of sky annulus (scale units)
  :dannulus	[value]		Width of sky annulus (scale units)
  :khist		[value]		Sky histogram extent (+/- sky sigma)
  :binsize	[value]		Resolution of sky histogram (sky sigma)
  :smooth		[y/n]		Lucy smooth the sky histogram
  :sloclip	[value]	        Low-side clipping factor in percent
  :shiclip	[value]	        High-side clipping factor in percent
  :smaxiter	[value]		Maximum number of iterations
  :snreject	[value]		Maximum number of rejection cycles
  :sloreject	[value]		Low-side pixel rejection limits (sky sigma)
  :shireject	[value]		High-side pixel rejection limits (sky sigma)
  :rgrow		[value]		Region growing radius (scale units)
  <P>
  # Photometry parameters
  <P>
  :apertures	[string]	List of aperture radii (scale units)
  :zmag		[value]		Zero point of magnitude scale
  <P>
  # Plotting and marking parameters
  <P>
  :mkcenter	[y/n]		Mark computed centers on display
  :mksky		[y/n]		Mark the sky annuli on the display
  :mkapert	[y/n]		Mark apertures on the display
  :radplot	[y/n]		Plot radial profile of object
  <P>
  <P>
  The following commands are available from inside the interactive setup menu.
   
                      Interactive Phot Setup Menu
  <P>
  	v	Mark and verify the critical parameters (f,s,c,a,d,r)
  <P>
  	f	Mark and verify the full-width half-maximum of psf
  	s	Mark and verify the standard deviation of the background
  	l	Mark and verify the minimum good data value
  	u	Mark and verify the maximum good data value
  <P>
  	c	Mark and verify the centering box width
  	n	Mark and verify the cleaning radius
  	p	Mark and verify the clipping radius
  <P>
  	a	Mark and verify the inner radius of the sky annulus
  	d	Mark and verify the width of the sky annulus
  	g	Mark and verify the region growing radius
  <P>
  	r	Mark and verify the aperture radii
  </PRE>
  <P>
  </UL>
  <! EndSection:   'CURSOR COMMANDS'>
  <H3>Algorithms</H3>
  <! BeginSection: 'ALGORITHMS'>
  <UL>
  <P>
  A brief description of the data dependent parameters, centering algorithms,
  sky fitting algorithms and photometry parameters can be found in the
  online help pages for the DATAPARS, CENTERPARS, FITSKYPARS, and PHOTPARS
  tasks.
  <P>
  </UL>
  <! EndSection:   'ALGORITHMS'>
  <H3>Output</H3>
  <! BeginSection: 'OUTPUT'>
  <UL>
  <P>
  In interactive mode the following quantities are printed on the standard
  output as each object is measured. Err is a simple string indicating whether
  or not an error was detected in the centering algorithm, the sky fitting
  algorithm or the photometry algorithm. Mag are the magnitudes in apertures 1
  through N respectively and xcenter, ycenter and msky are the x and y centers
  and the sky value respectively.
  <P>
  <PRE>
      image  xcenter  ycenter  msky  mag[1 ... N]  error
  </PRE>
  <P>
  In both interactive and batch mode full output is written to the text file
  <I>output</I>. At the beginning of each file is a header listing the
  current values of the parameters when the first stellar record was written.
  These parameters can be subsequently altered. For each star measured the
  following record is written
  <P>
  <PRE>
  	image  xinit  yinit  id  coords  lid
  	   xcenter  ycenter  xshift  yshift  xerr  yerr  cier error
  	   msky  stdev  sskew  nsky  nsrej  sier  serror
  	   itime  xairmass  ifilter  otime
  	   rapert  sum  area  mag  merr  pier  perr
  </PRE>
  <P>
  Image and coords are the name of the image and coordinate file respectively.
  Id and lid are the sequence numbers of stars in the output and coordinate
  files respectively. Cier and cerror are the centering algorithm error code
  and accompanying error message respectively.  Xinit, yinit, xcenter, ycenter,
  xshift, yshift, and xerr, yerr are self explanatory and output in pixel units.
  The sense of the xshift and yshift definitions is the following.
  <P>
  <P>
  <PRE>
  	xshift = xcenter - xinit
  	yshift = ycenter - yinit
  </PRE>
  <P>
  Sier and serror are the sky fitting error code and accompanying error
  message respectively. Msky, stdev and sskew are the best estimate of the sky
  value (per pixel), standard deviation and skew respectively. Nsky and nsrej
  are the number of sky pixels and the number of sky pixels rejected respectively.
  <P>
  Itime is the exposure time, xairmass is self-evident, ifilter is an
  id string identifying the filter used in the observations, and otime is
  a string containing the time of the observation in whatever units the
  user has set up.
  <P>
  Rapert, sum, area, and flux  are the radius of the aperture in scale units,
  the total number of counts including sky in the aperture, the area of the
  aperture in square pixels, and the total number of counts excluding sky
  in the aperture. Mag and merr are the magnitude and error in the magnitude
  in the aperture (see below).
  <P>
  <PRE>
          flux = sum - area * msky
           mag = zmag - 2.5 * log10 (flux) + 2.5 * log10 (itime)
          merr = 1.0857 * err / flux
           err = sqrt (flux / epadu + area * stdev**2 +
                 area**2 * stdev**2 / nsky)
  </PRE>
  <P>
  Pier and perror are photometry error code and accompanying error message.
  <P>
  In interactive mode a radial profile of each measured object is plotted
  in the graphics window if <I>radplots</I> is "<TT>yes</TT>".
  <P>
  In interactive and batchmode a radial profile plot is written to
  <I>plotfile</I>  if it is defined each time the result of an object
  measurement is written to <I>output</I> .
  <P>
  <P>
  </UL>
  <! EndSection:   'OUTPUT'>
  <H3>Errors</H3>
  <! BeginSection: 'ERRORS'>
  <UL>
  <P>
  If the object centering was error free then the field cier will be zero.
  Non-zero values of cier flag the following error conditions.
  <P>
  <PRE>
  	0        # No error
  	101      # The centering box is off image
  	102      # The centering box is partially off the image
  	103      # The S/N ratio is low in the centering box
  	104      # There are two few points for a good fit
  	105      # The x or y center fit is singular
  	106      # The x or y center fit did not converge
  	107      # The x or y center shift is greater than maxshift
  	108      # There is bad data in the centering box
  </PRE>
  <P>
  If all goes well during the sky fitting process then the error code sier
  will be 0. Non-zero values of sier flag the following error conditions.
  <P>
  <PRE>
  	0         # No error
  	201       # There are no sky pixels in the sky annulus
  	202       # Sky annulus is partially off the image
  	203       # The histogram of sky pixels has no width
  	204       # The histogram of sky pixels is flat or concave
  	205       # There are too few points for a good sky fit
  	206       # The sky fit is singular
  	207       # The sky fit did not converge
  	208       # The graphics stream is undefined
  	209       # The file of sky values does not exist
  	210       # The sky file is at EOF
  	211       # Cannot read the sky value correctly
  	212       # The best fit parameter are non-physical
  </PRE>
  <P>
  If no error occurs during the measurement of the magnitudes then pier is
  0. Non-zero values of pier flag the following error conditions.
   
  <PRE>
  	 0        # No error
  	 301      # The aperture is off the image
  	 302      # The aperture is partially off the image
  	 303      # The sky value is undefined
  	 305      # There is bad data in the aperture
  </PRE>
  <P>
  </UL>
  <! EndSection:   'ERRORS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Run PHOT on the image dev$ypix using the coordinate list ypix.coo.1
  created by DAOFIND and the default setup.
  <P>
  <PRE>
          da&gt; daofind dev$ypix default fwhmpsf=2.6 sigma=5.0 threshold=20. \<BR>
  	    verify-
  <P>
          ... make the coordinate list ypix.coo.1
  <P>
  	da&gt; phot dev$ypix default default
  <P>
  	... answer the verify prompts
  <P>
  	... the results will appear in ypix.mag.1
  </PRE>
  <P>
  <P>
  2. Compute the magnitudes for a few  stars in dev$ypix using the display
  and the image cursor. Setup the task parameters using the interactive
  setup menu defined by the i key command and a radial profile plot.
  <P>
  <PRE>
          da&gt; display dev$ypix 1 fi+
  <P>
          ... display the image
  <P>
          da&gt; phot dev$ypix "" default calgorithm=centroid interactive+
  <P>
          ... type ? to print an optional help page
  <P>
          ... move the image cursor to a star
          ... type i to enter the interactive setup menu
          ... enter maximum radius in pixels of the radial profile or hit
              CR to accept the default
          ... type v to enter the default menu
          ... set the fwhmpsf, centering radius, inner and outer sky annuli,
              photometry apertures, and sigma using the graphics cursor and
  	    the stellar radial profile plot
          ... typing &lt;CR&gt; leaves everything at the default value
          ... type q to quit the setup menu
  <P>
          ... type the v key to verify the parameters
  <P>
          ... type the w key to save the parameters in the parameter files
  <P>
          ... move the image cursor to the stars of interest and tap
              the space bar
  <P>
          ... a one line summary of the fitted parameters will appear on the
              standard output for each star measured
  <P>
          ... type q to quit and q again to confirm the quit
  <P>
          ... the output will appear in ypix.mag.2
  </PRE>
  <P>
  <P>
  3. Compute the magnitudes for a few stars in dev$ypix using a contour plot
  and the graphics cursor. This option is only useful for those (now very few)
  users who have access to a graphics terminal but not to an image display
  server. Setup the task parameters using the interactive setup menu defined by
  the i key command as in example 1.
  <P>
  <PRE>
          da&gt; show stdimcur
  <P>
          ... record the default value of stdimcur
  <P>
          da&gt; set stdimcur = stdgraph
  <P>
          ... define the image cursor to be the graphics cursor
  <P>
          da&gt; contour dev$ypix
  <P>
          ... make a contour plot of dev$ypix
  <P>
          da&gt; contour dev$ypix &gt;G ypix.plot1
  <P>
          ... store the contour plot of dev$ypix in the file ypix.plot1
  <P>
          da&gt; phot dev$ypix "" default calgorithm="centroid" interactive+ \<BR>
              display=stdgraph
  <P>
          ... type ? to get an optional help page
  <P>
          ... move graphics cursor to a star
          ... type i to enter the interactive setup menu
          ... enter maximum radius in pixels of the radial profile or CR
              to accept the default value
          ... type v to enter the default menu
          ... set the fwhmpsf, centering radius, inner and outer sky annuli,
              apertures, and sigma using the graphics cursor and the
              stellar radial profile plot
          ... typing &lt;CR&gt; leaves everything at the default value
          ... type q to quit the setup menu
  <P>
          ... type the v key to verify the critical parameters
  <P>
          ... type the w key to save the parameters in the parameter files
  <P>
          ... retype :.read ypix.plot1 to reload the contour plot
  <P>
          ... move the graphics cursor to the stars of interest and tap
              the space bar
  <P>
          ... a one line summary of the fitted parameters will appear on the
              standard output for each star measured
  <P>
          ... type q to quit and q again to verify
  <P>
          ... full output will appear in the text file ypix.mag.3
  <P>
          da&gt; set stdimcur = &lt;default&gt;
  <P>
          ... reset stdimcur to its previous value
  </PRE>
  <P>
  <P>
  4. Setup and run PHOT interactively on a list of objects temporarily
  overriding the fwhmpsf, sigma, cbox, annulus, dannulus, and apertures
  parameters determined in examples 1 or 2.
  <P>
  <PRE>
  <P>
  	da&gt; display dev$ypix 1
  <P>
  	    ... display the image
  <P>
          da&gt; phot dev$ypix ypix.coo.1 default calgorithm="centroid" \<BR>
              cbox=7.0 annulus=12.0 dannulus=5.0 apertures="3.0,5.0"  \<BR>
              interactive+
  <P>
          ... type ? for optional help
  <P>
  <P>
          ... move the graphics cursor to the stars and tap space bar
  <P>
                                  or
  <P>
          ... select stars from the input coordinate list with m / :m #
              and measure with spbar
  <P>
          ... measure stars selected from the input coordinate list
              with n / n #
  <P>
          ... a one line summary of results will appear on the standard output
              for each star measured
  <P>
          ... type q to quit and q again to confirm the quit
  <P>
          ... the output will appear in ypix.mag.4 ...
  </PRE>
  <P>
  <P>
  5. Display and measure some stars in an image section and write the output
  coordinates in the coordinate system of the parent image.
  <P>
  <PRE>
          da&gt; display dev$ypix[150:450,150:450] 1
  <P>
          ... display the image section
  <P>
          da&gt; phot dev$ypix[150:450,150:450] "" default wcsout=tv \<BR>
              calgorithm="centroid" interactive+
  <P>
          ... move cursor to stars and type spbar
  <P>
          ... type q to quit and q again to confirm quit
  <P>
          ... output will appear in ypix.mag.5
  <P>
          da&gt; pdump ypix.mag.5 xc,yc yes | tvmark 1 STDIN col=204
  </PRE>
  <P>
  <P>
  6. Run PHOT in batch mode using the coordinate file and the previously
  saved parameters. Verify the critical parameters.
  <P>
  <PRE>
          ap&gt; phot dev$ypix default default 
  <P>
          ... output will appear in ypix.mag.6...
  </PRE>
  <P>
  <P>
  7. Repeat example 6 but assume that the input coordinate are ra and dec
  in degrees and degrees, turn off verification, and submit the task to to
  the background.
  <P>
  <PRE>
          da&gt; display dev$ypix 1
  <P>
          ap&gt; rimcursor wcs=world &gt; radec.coo
  <P>
          ... move to selected stars and type any key
  <P>
          ... type ^Z to quit
  <P>
          da&gt; phot dev$ypix radec.coo default wcsin=world verify- verbose- &amp;
  <P>
          ... output will appear in ypix.mag.7
  <P>
          da&gt; pdump ypix.mag.7 xc,yc yes | tvmark 1 STDIN col=204
  <P>
          ... mark the stars on the display
  </PRE>
  <P>
  <P>
  8. Run PHOT interactively without using the image display cursor.
  <P>
  <PRE>
          da&gt; show stdimcur
  <P>
          ... record the default value of stdimcur
  <P>
          da&gt; set stdimcur = text
  <P>
          ... set the image cursor to the standard input
  <P>
          da&gt; phot dev$ypix default default interactive+ 
  <P>
          ... type ? for optional help
  <P>
          ... type :m 3 to set the initial coordinates to those of the
              third star in the list
  <P>
          ... type i to enter the interactive setup menu
          ... enter the maximum radius in pixels for the radial profile or
              accept the default with a CR
          ... type v to enter the default menu
          ... set the fwhmpsf, centering radius, inner and outer sky annuli,
              apertures, and sigma using the graphics cursor and the
              stellar radial profile plot
          ... typing &lt;CR&gt; after the prompt leaves the parameter at its default
              value
          ... type q to quit the setup menu
  <P>
          ... type r to rewind the coordinate list
  <P>
          ... type l to measure all the stars in the coordinate list
  <P>
          ... a one line summary of the answers will appear on the standard
              output for each star measured
  <P>
          ... type q to quit followed by q to confirm the quit
  <P>
          ... full output will appear in the text file ypix.mag.8
  <P>
          da&gt; set stdimcur = &lt;default&gt;
  <P>
          ... reset the value of stdimcur
  <P>
  </PRE>
  <P>
  8. Use a image cursor command file to drive the PHOT task. The cursor command
  file shown below sets the cbox, annulus, dannulus, and apertures parameters
  computes the centers, sky values, and magnitudes for 3 stars, updates the
  parameter files, and quits the task.
  <P>
  <PRE>
          da&gt; type cmdfile
  	: calgorithm centroid
          : cbox 9.0
          : annulus 12.0
          : dannulus 5.0
          : apertures 5.0
          442 410 101 \040
          349 188 101 \040
          225 131 101 \040
          w
          q
  <P>
          da&gt; phot dev$ypix "" default icommands=cmdfile  verify-
  <P>
          ... full output will appear in ypix.mag.9
  </PRE>
  <P>
  <P>
  <P>
  <P>
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
  <P>
  It is currently the responsibility of the user to make sure that the
  image displayed in the frame is the same as that specified by the image
  parameter.
  <P>
  Commands which draw to the image display are disabled by default.
  To enable graphics overlay on the image display, set the display
  parameter to "<TT>imdr</TT>", "<TT>imdg</TT>", "<TT>imdb</TT>", or "<TT>imdy</TT>" to get red, green,
  blue or yellow overlays and set the centerpars mkcenter switch to
  "<TT>yes</TT>", the fitskypars mksky switch to"<TT>yes</TT>", or the photpars mkapert
  switch to "<TT>yes</TT>". It may be necessary to run gflush and to redisplay the image
  to get the overlays position correctly.
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  datapars, centerpars, fitskypars, photpars
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'CURSOR COMMANDS' 'ALGORITHMS' 'OUTPUT' 'ERRORS' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
