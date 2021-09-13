.. _polyphot:

polyphot — Measure magnitudes inside a list of polygonal regions
================================================================

**Package: apphot**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  polyphot -- compute magnitudes inside polygonal apertures
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  polyphot image
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
  <DT><B>coords = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='coords' Line='coords = ""'>
  <DD>The list of text files containing the center coordinates of the polygons
  to be measured. Polygon centers are listed one per line with the x and y
  coordinates in columns one and two. A "<TT>;</TT>" character in column terminates
  the polygon center list for the current polygon and tells POLYPHOT to skip
  to the next polygon listed in <I>polygons</I>.  If coords is undefined the
  polygons are not shifted. The number of polygon center files must be
  zero, one, or equal to the number of images. If coords is "<TT>default</TT>",
  "<TT>dir$default</TT>", or a directory specification then a coords file name
  of the form dir$root.extension.version is constructed and searched for,
  where dir is the directory, root is the root image name, extension is "<TT>coo</TT>"
  and version is the next available version number for the file.
  </DD>
  </DL>
  <DL>
  <DT><B>polygons = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='polygons' Line='polygons = ""'>
  <DD>The list of text files containing the vertices of the polygons to be
  measured.  The polygon vertices are listed 1 vertext per line with the x and y
  coordinates of each vertex in columns 1 and 2. The vertices list is terminated
  a <TT>';'</TT> in column 1. The number of polygon files must be zero, one, or
  equal to the number of images.  If polygons is "<TT>default</TT>", "<TT>dir$default</TT>", or
  a directory specification then a coords file name of the form
  dir$root.extension.version is constructed and searched for, where dir is the
  directory, root is the root image name, extension is "<TT>ver</TT>"
  and version is the next available version number for the file.
  </DD>
  </DL>
  <DL>
  <DT><B>output = "<TT>default</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output = "default"'>
  <DD>The name of the results file or results directory. If output is
  "<TT>default</TT>", "<TT>dir$default</TT>", or a directory specification then an output file name
  of the form dir$root.extension.version is constructed, where dir is the
  directory, root is the root image name, extension is "<TT>ply</TT>" and version is
  the next available version number for the file. The number of output files
  must be zero, one, or equal to the number of image files.  In both interactive
  and batch mode full output is written to output. In interactive mode
  an output summary is also written to the standard output.
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
  <DT><B>polypars = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='polypars' Line='polypars = ""'>
  <DD>The name of the text file containing the polygon photometry parameters,
  If <I>polypars</I> is undefined then the default parameter set in 
   uparm directory is used.
  </DD>
  </DL>
  <DL>
  <DT><B>interactive = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = yes'>
  <DD>Run the task interactively ?
  </DD>
  </DL>
  <DL>
  <DT><B>icommands = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='icommands' Line='icommands = ""'>
  <DD>The image cursor or image cursor command file.
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
  coordinate system. The input coordinate system options are "<TT>logical</TT>", tv"<TT>,
  </TT>"physical"<TT>, and </TT>"world"<TT>. The output coordinate system options are </TT>"logical"<TT>,
  </TT>"tv"<TT>, and </TT>"physical"<TT>. The image cursor coordinate system is assumed to
  be the </TT>"tv"<TT> system.
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
  wcsin and wcsout are </TT>"logical"<TT> and </TT>"logical"<TT> respectively.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>cache = </TT>")_.cache"<TT></B></DT>
  <! Sec='PARAMETERS' Level=-1 Label='cache' Line='cache = ")_.cache"'>
  <DD>Cache the image pixels in memory. Cache may be set to the value of the apphot
  package parameter (the default), </TT>"yes"<TT>, or </TT>"no"<TT>. By default cacheing is 
  disabled.
  </DD>
  </DL>
  <DL>
  <DT><B>verify = </TT>")_.verify"<TT></B></DT>
  <! Sec='PARAMETERS' Level=-1 Label='verify' Line='verify = ")_.verify"'>
  <DD>Verify the critical parameters in non-interactive mode ? Verify may be set to
  the apphot package parameter value (the default), </TT>"yes"<TT>, or </TT>"no.
  </DD>
  </DL>
  <DL>
  <DT><B>update = "<TT>)_.update</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=-1 Label='update' Line='update = ")_.update"'>
  <DD>Update the critical parameters in non-interactive mode if verify is yes ?
  Update may be set to the apphot package parameter value (the default), "<TT>yes</TT>",
  or "<TT>no.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = </TT>")_.verbose"<TT></B></DT>
  <! Sec='PARAMETERS' Level=-1 Label='verbose' Line='verbose = ")_.verbose"'>
  <DD>Print messages in non-interactive mode? Verbose may be set to the apphot
  package parameter value (the default), </TT>"yes"<TT>, or </TT>"no.
  </DD>
  </DL>
  <DL>
  <DT><B>graphics = "<TT>)_.graphics</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=-1 Label='graphics' Line='graphics = ")_.graphics"'>
  <DD>The default graphics device. Graphics may be set to the apphot package
  parameter value (the default), "<TT>yes</TT>",
  or "<TT>no.
  </DD>
  </DL>
  <DL>
  <DT><B>display = </TT>")_.display"<TT></B></DT>
  <! Sec='PARAMETERS' Level=-1 Label='display' Line='display = ")_.display"'>
  <DD>The default display device. By default graphics overlay is disabled. Display
  may be set to the apphot package parameter value (the default), </TT>"yes"<TT>, or </TT>"no. 
  Setting display to one of "<TT>imdr</TT>", "<TT>imdg</TT>", "<TT>imdb</TT>", or "<TT>imdy</TT>" enables graphics
  overlay with the IMD graphics kernel.  Setting display to "<TT>stdgraph</TT>" enables
  POLYPHOT to work interactively from a contour plot.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  POLYPHOT computes the magnitude of objects in the IRAF image <I>image</I>
  inside a list of polygonal apertures whose vertices are listed in the text file
  <I>polygons</I> or are marked on the display interactively with the
  image cursor. The polygon centers  may be read from the polygon center
  file <I>coords</I> or set interactively with the image cursor.
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
  If <I>cache</I> is yes and the host machine physical memory and working set size
  are large enough, the input image pixels are cached in memory. If cacheing
  is enabled and POLYPHOT is run interactively the first measurement will appear
  to take a long time as the entire image must be read in before the measurement
  is actually made. All subsequent measurements will be very fast because POLYPHOT
  is accessing memory not disk. The point of cacheing is to speed up random
  image access by making the internal image i/o buffers the same size as the
  image itself. However if the input object lists are sorted in row order and
  sparse cacheing may actually worsen not improve the execution time. Also at
  present there is no point in enabling cacheing for images that are less than
  or equal to 524288 bytes, i.e. the size of the test image dev$ypix, as the
  default image i/o buffer is exactly that size. However if the size of dev$ypix
  is doubled by converting it to a real image with the chpixtype task then the
  effect of cacheing in interactive is can be quite noticeable if measurements
  of objects in the top and bottom halfs of the image are alternated.
  <P>
  In interactive mode the user may either define the list of objects to be
  measured interactively with the image cursor or create a polygon and polygon
  center list prior to running POLYPHOT. In either case the user may adjust
  the centering, sky fitting, and photometry algorithm parameters until a
  satisfactory fit is achieved and optionally store the final results
  in <I>output</I>. In batch mode the polygon and polygon centers are read
  from the text files <I>polygons</I> and <I>coords</I> or the image cursor
  parameter <I>icommands</I> can be redirected to a text file containing
  a list of cursor commands. In batch mode the current set of algorithm
  parameters is used.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>The polygon and polygon centers files</H3>
  <! BeginSection: 'THE POLYGON and POLYGON CENTERS FILES'>
  <UL>
  <P>
  A sample polygons file and accompanying coordinates file is listed below.
  <P>
  <PRE>
          # Sample Polygons File (2 polygons)
  <P>
          200.5  200.5
          300.5  200.5
          300.5  300.5
          200.5  300.5
          ;
          100.4  100.4
          120.4  100.4
          120.4  120.4
          100.4  120.4
          ;
  </PRE>
  <P>
  <PRE>
          # Sample Coordinates File (2 groups, 1 for each polygon)
  <P>
          123.4  185.5
          110.4  130.4
          150.9  200.5
          ;
          85.6   35.7
          400.5  300.5
          69.5   130.5
          ;
  </PRE>
  <P>
  <P>
  </UL>
  <! EndSection:   'THE POLYGON and POLYGON CENTERS FILES'>
  <H3>Cursor commands</H3>
  <! BeginSection: 'CURSOR COMMANDS'>
  <UL>
  <P>
  The following polyphot commands are currently available.
  <P>
  <PRE>
  	Interactive Keystroke Commands
  <P>
  ?	Print help
  :	Colon commands
  v	Verify the critical parameters
  w	Store the current parameters
  d	Plot radial profile of current object
  i	Define current polygon, graphically set parameters using current object
  g	Define current polygon 
  c	Fit center for current object
  t	Fit sky around cursor
  a       Average sky values fit around several cursor positions
  s	Fit sky around current object
  h	Do photometry for current polygon
  j	Do photometry for current polygon, output results
  p	Do photometry for current object using current sky
  o	Do photometry for current object using current sky, output results
  f	Do photometry for current object
  spbar	Do photometry for current object, output results
  m	Move to next object in coordinate list
  n	Do photometry for next object in coordinate list, output results
  l	Do photometry for remaining objects in list, output results
  r	Rewind the polygon list
  e	Print error messages
  q	Exit task
  <P>
  <P>
  	Colon Commands
  <P>
  :show	[data/center/sky/phot]	List the parameters
  :m [n]	Move to next [nth] object in coordinate list
  :n [n]	Do photometry for next [nth] object in coordinate list, output results
  <P>
  <P>
  	Colon Parameter Editing Commands
  <P>
  # Image and file name parameters
  <P>
  :image		[string]	Image name
  :polygon	[string]	Polygon file
  :coords		[string]	Coordinate file
  :output		[string]	Results file
  <P>
  # Data dependent parameters
  <P>
  :scale		[value]		Image scale (units per pixel)
  :fwhmpsf	[value]		Full-width half-maximum of PSF (scale units)
  :emission	[y/n]		Emission feature (y), absorption (n)
  :sigma		[value]		Standard deviation of sky (counts)
  :datamin	[value]		Minimum good pixel value (counts)
  :datamax	[value]		Maximum good pixel value (counts)
  <P>
  # Noise parameters
  <P>
  :noise		[string]	Noise model (constant|poisson)
  :gain		[string]	Gain image header keyword
  :ccdread	[string]	Readout noise image header keyword
  :epadu		[value]		Gain (electrons per count)
  :epadu		[value]		Readout noise (electrons)
  <P>
  # Observing parameters
  <P>
  :exposure	[string]	Exposure time image header keyword
  :airmass	[string]	Airmass image header keyword
  :filter		[string]	Filter image header keyword
  :obstime	[string]	Time of observation image header keyword
  :itime		[value]		Integration time (time units)
  :xairmass	[value]		Airmass value (number)
  :ifilter	[string]	Filter id string
  :otime		[string]	Time of observation (time units)
  <P>
  # Centering algorithm parameters
  <P>
  :calgorithm	[string]	Centering algorithm
  :cbox		[value]		Width of centering box (scale units)
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
  :khist		[value]		Sky histogram extent (+/- sigma)
  :binsize	[value]		Resolution of sky histogram (sigma)
  :sloclip	[value]		Low-side clipping factor in percent
  :shiclip	[value]		High-side clipping factor in percent
  :smooth		[y/n]		Lucy smooth the sky histogram
  :smaxiter	[value]		Maximum number of iterations
  :snreject	[value]		Maximum number of rejection cycles
  :sloreject	[value]		Low-side pixel rejection limits (sky sigma)
  :shireject	[value]		High-side pixel rejection limits (sky sigma)
  :rgrow		[value]		Region growing radius (scale units)
  <P>
  # Photometry parameters
  <P>
  :zmag		[value]		Zero point of magnitude scale
  <P>
  # Plotting and marking parameters
  <P>
  :mkcenter	[y/n]		Mark computed centers on the display
  :mksky		[y/n]		Mark the sky annuli on the display
  :mkpolygon	[y/n]		Mark the polygon on the display
  <P>
  <P>
  <P>
  The following commands are available from inside the interactive setup menu.
  <P>
  <P>
                      Interactive Photometry Setup Menu
  <P>
  	v	Mark and verify the critical parameters (f,c,s,a,d)
  <P>
  	f	Mark and verify the psf full-width half-maximum
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
  </PRE>
  <P>
  </UL>
  <! EndSection:   'CURSOR COMMANDS'>
  <H3>Algorithms</H3>
  <! BeginSection: 'ALGORITHMS'>
  <UL>
  <P>
  A brief description of the data dependent parameters, the centering
  algorithms and the sky fitting algorithms can be found in the online
  manual pages for the DATAPARS, CENTERPARS, and FITSKYPARS tasks.
  User measuring extended "<TT>fuzzy</TT>" features may wish to set the CENTERPARS 
  <I>calgorithm</I> parameter to "<TT>none</TT>", the FITSKYPARS parameters
  <I>salgorithm</I> and <I>skyvalue</I> to "<TT>constant</TT>" and &lt;uservalue&gt; before
  running POLYPHOT.
  <P>
  POLYPHOT computes the intersection of each image line with the line segments
  composing the polygon in order to determine the extent of the polygon. A one
  dimensional summation including a fractional approximation for the end pixels
  is performed over those regions of the image line which intersect the polygon.
  All the 1D summations are summed to give the total integral. The vertices of
  the polygon must be specified in order either clockwise or counterclockwise.
  <P>
  </UL>
  <! EndSection:   'ALGORITHMS'>
  <H3>Output</H3>
  <! BeginSection: 'OUTPUT'>
  <UL>
  <P>
  In interactive mode the following quantities are printed on the standard
  output as each object is measured. Error is a simple string which indicates
  whether the task encountered an error in the centering algorithm, the sky
  fitting algorithm or the photometry algorithm. Mag are the magnitudes in
  the polygonal aperture and xcenter, ycenter and msky are the x and y centers
  and the sky value respectively.
  <P>
  <PRE>
      image  xcenter  ycenter  msky  mag  merr error
  </PRE>
  <P>
  In both interactive and batch mode full output is written to the text file
  <I>output</I>. At the beginning of each file is a header listing the current
  values of the parameters when the first stellar record was written.  These
  parameters can be subsequently altered. For each star measured the following
  record is written
  <P>
  <PRE>
  	image  xinit  yinit  id  coords  lid
  	   xcenter  ycenter  xshift  yshift  xerr  yerr  cier error
  	   msky  stdev  sskew  nsky  nsrej  sier  serror
  	   itime  xairmass  ifilter  otime
  	   sum  area  flux mag  merr  pier  perr
  	   polygons  pid  oldxmean  oldymean  xmean  ymean  maxrad  nver
  	   xvertex  yvertex
  </PRE>
  <P>
  Image and coords are the name of the image and coordinate file respectively.
  Id and lid are the sequence numbers of objects in the output and coordinate
  files respectively. Cier and cerror are the centering error code and
  accompanying error message respectively.  Xinit, yinit, xcenter, ycenter,
  xshift, yshift, and xerr, yerr are self explanatory and output in pixel units.
  The sense of the xshift and yshift definitions is the following.
  <P>
  <PRE>
  	xshift = xcenter - xinit
  	yshift = ycenter - yinit
  </PRE>
  <P>
  Sier and serror are the sky fitting error code and accompanying error
  message respectively.  Msky, stdev and sskew are the best estimate of the
  sky value (per pixel), standard deviation and skew respectively. Nsky and
  nsrej are the number of sky pixels used and the number of sky pixels rejected
  from the fit respectively.
  <P>
  Itime is the exposure time, xairmass is self-evident, ifilter is an id string
  identifying the filter used during the observation, and otime is a string
  specifying the time of the observation in whatever units the user has chosen.
  <P>
  Sum, area, and flux are the total number of counts including sky in the
  polygonal aperture, the area of the aperture in square pixels, and the total
  number of counts in the aperture excluding sky. Mag and merr are the magnitude
  and error in the magnitude in the aperture after subtracting the sky value
  (see below).
  <P>
  <PRE>
          flux = sum - area * msky
           mag = zmag - 2.5 * log10 (flux) + 2.5 * log10 (itime)
          merr = 1.0857 * error / flux
         error = sqrt (flux / epadu + area * stdev**2 +
                 area**2 * stdev**2 / nsky)
  </PRE>
  <P>
  Pier and perror are photometry error code and accompanying error message.
  <P>
  Polygons and pid are the name of the polygons file and the polygon id
  respectively. Oldxmean, oldymean, xmean and ymean are the original and
  current average coordinates of the current polygon. Oldxmean and oldymean
  are the values in the polygons file or the values which correspond to the
  polygon drawn on the display. Xinit and yinit define the position to
  which the polygonal aperture was shifted. Xmean and ymean are generally
  identical to xcenter and ycenter and describe the position of the
  centered polygonal aperture. Maxrad is the maximum
  distance of a polygon vertex from the average of the vertices. Nver, xvertex
  and yvertex are the number of vertices and the coordinates of the vertices
  of the polygonal aperture.
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
  <P>
  <PRE>
  	0       # No error
  	801	# The polygon is undefined
  	802     # The polygon is partially off the image
  	803     # The polygon is off the image
  	804     # The sky value is undefined
  	805     # There is bad data in the aperture
  </PRE>
  <P>
  </UL>
  <! EndSection:   'ERRORS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Compute the magnitudes inside  2 polygonal aperture for a few  regions in
  dev$ypix using the display and the image cursor.  Turn off centering and set
  the sky background to 0.0.
  <P>
  <PRE>
  	ap&gt; display dev$ypix 1 fi+
  <P>
  	... display the image
  <P>
  	ap&gt; polyphot dev$ypix calgorithm=none salgorithm=constant \<BR>
              skyvalue=0.0 display=imdg mkpolygon+
  <P>
  	... type ? to print a help page
  <P>
  	... move image cursor to a region of interest
  <P>
  	... type g to enter the polygon definition menu
  	... use the image cursor and spbar key to mark the vertices of
              the polygonal aperture 
  	... mark each vertex only once, POLYPHOT will close the polygon
  	    for you
          ... type q to quit the polygon definition menu
  <P>
  	... type the v key to verify the parameters
  <P>
  	... type the w key to save the parameters in the parameter files
  <P>
  	... move the image cursor to the objects of interest and tap
  	    the space bar, the polygon will be marked on the image 
              display
  <P>
  	... type g to enter the polygon definition menu
  	... use the image cursor and spbar key to mark the vertices of
              the polygonal aperture 
  	... mark each vertex only once, POLYPHOT will close the polygon
  	    for you
          ... type q to quit the polygon definition menu
  <P>
  	... move the image cursor to the objects of interest and tap
  	    the space bar, the polygon will be marked on the image
              display 
  <P>
  	... a one line summary of the fitted parameters will appear on the
  	    standard output for each star measured
  <P>
  	... the output will appear in ypix.ply.1
  </PRE>
  <P>
  <P>
  2.  Repeat the previous example but use a contour plot and the graphics
  cursor in place of the image display and image cursor. This option is
  really only useful for users (very few these days) with access to a graphics
  terminal but not an image display server.
  <P>
  <PRE>
  	ap&gt; show stdimcur
  <P>
          ... determine the default value of stdimcur
  <P>
  	ap&gt; set stdimcur = stdgraph
  <P>
  	... define the image cursor to be the graphics cursor
  <P>
          ap&gt; contour dev$ypix
  <P>
          ... create a contour plot of dev$ypix
  <P>
  	ap&gt; contour dev$ypix &gt;G ypix.plot1
  <P>
  	... store the contour plot of dev$ypix in the file ypix.plot1
  <P>
  	ap&gt; polyphot dev$ypix calgorithm=none salgorithm=constant \<BR>
              skyvalue=0.0 display=stdgraph mkpolygon+
  <P>
  	... type ? to print a help page
  <P>
  	... type the v key to verify the parameters
  <P>
  	... type the w key to save the parameters in the parameter files
  <P>
  	... move image cursor to a region of interest
  	... type g to enter the polygon definition menu
  	... use the image cursor and spbar key to mark the vertices of
              the polygonal aperture 
  	... mark each vertex only once, POLYPHOT will close the polygon
  	    for you
          ... type q to quit the polygon definition menu
  <P>
  	... move the image cursor to the objects of interest and tap
  	    the space bar, the polygon will be marked on the contour
              plot
  <P>
  	... move image cursor to a region of interest
  	... type g to enter the polygon definition menu
  	... use the image cursor and spbar key to mark the vertices of
              the polygonal aperture 
  	... mark each vertex only once, POLYPHOT will close the polygon
  	    for you
          ... type q to quit the polygon definition menu
  <P>
  	... move the image cursor to the objects of interest and tap
  	    the space bar, the polygon will be marked on the image 
              display
  <P>
  	... a one line summary of the fitted parameters will appear on the
  	    standard output for each star measured and the polygons will
  	    be drawn on the display
  <P>
  	... full output will appear in the text file ypix.ply.2 
  <P>
  	ap&gt; reset stdimcur = &lt;default&gt;
  <P>
  	... reset stdimcur to its default value
  <P>
  <P>
  </PRE>
  <P>
  3. Setup and run POLYPHOT interactively on a list of objects created with
  POLYMARK.
  <P>
  <PRE>
  	ap&gt; display dev$ypix 1
  <P>
          ... display the image
  <P>
  	ap&gt; polymark dev$ypix display=imdg
  <P>
  	... type g to enter the polygon definition menu
          ... mark each vertex with the spbar
  	... mark each vertex only once, POLYPHOT will close the
  	    polygon for you
          ... type q to quit the polygon definition menu 
  <P>
  	... move the cursor to the regions of interest and tap
  	    the space bar, the polygon will be marked on the image
              display
  <P>
  	... the polygon and polygon centers will be written to the text
              files ypix.ver.1 and ypix.coo.1 respectively
  <P>
  	... type q to quit and q again to confirm the quit
  <P>
  	ap&gt; display dev$ypix 2
  <P>
          ... redisplay the image
  <P>
  	ap&gt; polyphot dev$ypix calgorithm=none salgorithm=constant skyvalue=0.0 \<BR>
              coords=default polygon=default display=imdg mkpolygon+
  <P>
  	... type n to measure the first polygon in the list
  <P>
  	... if everything looks okay type l to measure the rest of the stars 
  <P>
  	... a one line summary of results will appear on the standard output
  	    for each star measured and the aperture will be drawn on the
              image display
  <P>
          ... type q to quit and q again to confirm the quit
  <P>
  	... the output will appear in ypix.ply.3
  </PRE>
  <P>
  <P>
  4. Repeat example 3 but work on a section of the input image while
  preserving the coordinate system of the original image.
  <P>
  <PRE>
  	ap&gt; display dev$ypix[150:450,150:450] 1
  <P>
          ... display the image
  <P>
  	p&gt; polymark dev$ypix[150:450,150:450] wcsout=tv display=imdg
  <P>
  	... type g to enter the polygon definition menu
          ... mark each vertex with the spbar
  	... mark each vertex only once, POLYPHOT will close the
  	    polygon for you
          ... type q to quit the polygon definition menu 
  <P>
  	... move the cursor to the regions of interest and tap
  	    the space bar, the polygon will be marked on the image
              display
  <P>
  	... the polygon and polygon centers will be written to the text
              files ypix.ver.1 and ypix.coo.1 respectively
  <P>
  	... type q to quit and q again to confirm the quit
  <P>
  	ap&gt; display dev$ypix[150:450,150:450] 2
  <P>
          ... redisplay the image
  <P>
  	ap&gt; polyphot dev$ypix[150:450,150:450] calgorithm=none \<BR>
  	    salgorithm=constant skyvalue=0.0 coords=default polygon=default \<BR>
  	    display=imdg mkpolygon+ wcsin=tv wcsout=tv
  <P>
  	... type n to measure the first polygon in the list
  <P>
  	... if everything looks okay type l to measure the rest of the stars 
  <P>
  	... a one line summary of results will appear on the standard output
  	    for each star measured and the aperture will be drawn on the
              image display
  <P>
          ... type q to quit and q again to confirm the quit
  <P>
  	... the output will appear in ypix.ply.4
  <P>
          ap&gt; pdump ypix.ply.4 xc,yc yes | tvmark 2 STDIN col=204
  <P>
          ... mark the centers of the polygons on the display
  </PRE>
  <P>
  <P>
  5. Run POLYPHOT in batch mode using a polygon and coordinate file and the
  default parameters. Verify the critical parameters.
  <P>
  <PRE>
  	ap&gt; polyphot dev$ypix coords=default polygon=default inter- verify+
  <P>
  	... output will appear in ypix.ply.5
  </PRE>
  <P>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Timings</H3>
  <! BeginSection: 'TIMINGS'>
  <UL>
  </UL>
  <! EndSection:   'TIMINGS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  There are no restrictions on the shape of the polygon but the vertices
  must be listed or marked in order.
  <P>
  When marking the polygon on the display it is not necessary to close
  the polygon. When the user types q to quit the marking the program
  will automatically close the polygon.
  <P>
  It is currently the responsibility of the user to make sure that the
  image displayed on the display is the same as that specified by the image
  parameter.
  <P>
  Commands which draw to the image display are disabled by default.
  To enable graphics overlay on the image display, set the display
  parameter to "<TT>imdr</TT>", "<TT>imdg</TT>", "<TT>imdb</TT>", or "<TT>imdy</TT>" to get red, green,
  blue or yellow overlays and set the centerpars mkcenter switch to
  "<TT>yes</TT>", the fitskypars mksky switch to"<TT>yes</TT>", or the polypars mkpolygon
  switch to "<TT>yes</TT>". It may be necessary to run gflush and to redisplay the image
  to get the overlays position correctly.
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  datapars,centerpars,fitskypars,polypars,qphot,phot,wphot
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'THE POLYGON and POLYGON CENTERS FILES' 'CURSOR COMMANDS' 'ALGORITHMS' 'OUTPUT' 'ERRORS' 'EXAMPLES' 'TIMINGS' 'BUGS' 'SEE ALSO'  >
  
