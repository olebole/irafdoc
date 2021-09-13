radprof — Compute the stellar radial profile of a list of stars
===============================================================

**Package: apphot**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>radprof (May00)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.digiphot.apphot</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>radprof (May00)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>radprof</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  radprof -- compute the radial profile of an object
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  radprof image radius step
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_image">image</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD>The name of the image containing the objects to be measured.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_radius">radius, step</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='radius' Line='radius, step'>
  <DD>The size and resolution of the computed radial profile in scale units which is
  equal to radius * <I>scale</I>  and step * <I>scale</I> in pixels.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_coords">coords = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='coords' Line='coords = ""'>
  <DD>The list of text files containing initial coordinates for the objects to
  be centered. Objects are listed in coords one object per line with the
  initial coordinate values in columns one and two. The number of coordinate
  files must be zero, one, or equal to the number of images.  If coords is
  "<TT>default</TT>", "<TT>dir$default</TT>", or a directory specification then a coords file name
  of the form dir$root.extension.version is constructed and searched for,
  where dir is the directory, root is the root image name, extension is "<TT>prf</TT>"
  and version is the next available version number for the file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output = ""'>
  <DD>The name of the results file or results directory.
  If output is "<TT>default</TT>", "<TT>dir$default</TT>" or a directory specification then an
  output file name of the form dir$root.extension.version is constructed, where
  dir is the directory, root is the root image name, extension is "<TT>prf</TT>" and
  version is the next available version of the file. If output is undefined,
  then no output file is created. If output is defined, the number of output files
  is either 1 or the same as the number of input images.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_plotfile">plotfile = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='plotfile' Line='plotfile = ""'>
  <DD>The name of the file containing radial profile plots of the stars written
  to the output file. If plotfile is defined then a radial profile plot
  is written to plotfile every time a record is written to <I>output</I>.
  The user should be aware that this can be a time consuming operation.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_datapars">datapars = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='datapars' Line='datapars = ""'>
  <DD>The name of the file containing the data dependent parameters. The critical
  parameters <I>fwhmpsf</I> and <I>sigma</I> are located here. If <I>datapars</I>
  is undefined then the default parameter set in uparm directory is used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_centerpars">centerpars = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='centerpars' Line='centerpars = ""'>
  <DD>The name of the file containing the centering parameters. The critical
  parameters <I>calgorithm</I> and <I>cbox</I> are located here.
  If <I>centerpars</I> is undefined then the default parameter set in
  uparm directory is used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fitskypars">fitskypars = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fitskypars' Line='fitskypars = ""'>
  <DD>The name of the text file containing the sky fitting parameters. The critical
  parameters <I>salgorithm</I>, <I>annulus</I>, and <I>dannulus</I> are located here.
  If <I>fitskypars</I> is undefined then the default parameter set in uparm
  directory is used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_photpars">photpars = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='photpars' Line='photpars = ""'>
  <DD>The name of the file containing the photometry parameters. The critical
  parameter <I>apertures</I> is located here.  If <I>photpars</I> is undefined
  then the default parameter set in uparm directory is used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_order">order = 5</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='order' Line='order = 5'>
  <DD>The number of pieces in the spline fit.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nreject">nreject = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nreject' Line='nreject = 1'>
  <DD>The maximum number of rejection cycles.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_kreject">kreject = 3.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='kreject' Line='kreject = 3.0'>
  <DD>The k-sigma rejection limit for the radial profile fit.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interactive">interactive = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = yes'>
  <DD>Run the task interactively ?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_radplots">radplots = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='radplots' Line='radplots = yes'>
  <DD>If <I>radplots</I> is "<TT>yes</TT>" and RADPROF  is run in interactive mode, a radial
  profile of each star is plotted on the screen after the star is measured.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_icommands">icommands = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='icommands' Line='icommands = ""'>
  <DD>The image cursor or image cursor command file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_gcommands">gcommands = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='gcommands' Line='gcommands = ""'>
  <DD>The graphics cursor or graphics cursor command file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_wcsin">wcsin = "<TT>)_.wcsin</TT>", wcsout = "<TT>)_.wcsout</TT>"</A></B></DT>
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
  <DT><B><A NAME="l_logical">logical</A></B></DT>
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
  <DT><B><A NAME="l_tv">tv</A></B></DT>
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
  <DT><B><A NAME="l_physical">physical</A></B></DT>
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
  <DT><B><A NAME="l_world">world</A></B></DT>
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
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_cache">cache = "<TT>)_.cache</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=-1 Label='cache' Line='cache = ")_.cache"'>
  <DD>Cache the image pixels in memory. Cache may be set to the value of the apphot
  package parameter (the default), "<TT>yes</TT>", or "<TT>no</TT>". By default cacheing is 
  disabled.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verify">verify = "<TT>)_.verify</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=-1 Label='verify' Line='verify = ")_.verify"'>
  <DD>Verify the critical parameters in non-interactive mode ? Verify may be set to
  the apphot package parameter value (the default), "<TT>yes</TT>", or "<TT>no</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_update">update = "<TT>)_.update</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=-1 Label='update' Line='update = ")_.update"'>
  <DD>Update the critical parameter in non-interactive mode if verify is yes ?
  Update may be set to the apphot package parameter value (the default), "<TT>yes</TT>",
  or "<TT>no</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = "<TT>)_.verbose</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=-1 Label='verbose' Line='verbose = ")_.verbose"'>
  <DD>Print messages on the screen in non-interactive mode ? Verbose may be set
  to the apphot package parameter value (the default), "<TT>yes</TT>", or "<TT>no</TT>".
  <P>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_graphics">graphics = "<TT>)_.graphics</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=-1 Label='graphics' Line='graphics = ")_.graphics"'>
  <DD>The default graphics device.  Graphics may be set to the apphot package
  parameter value (the default), "<TT>yes</TT>", or "<TT>no.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_display">display = </TT>")_.display"<TT></A></B></DT>
  <! Sec='PARAMETERS' Level=-1 Label='display' Line='display = ")_.display"'>
  <DD>The default display device. Display may be set to the apphot package
  parameter value (the default), </TT>"yes"<TT>, or </TT>"no. By default graphics overlay
  is disabled.  Setting display to one of "<TT>imdr</TT>", "<TT>imdg</TT>", "<TT>imdb</TT>", or "<TT>imdy</TT>"
  enables graphics overlay with the IMD graphics kernel.  Setting display to
  "<TT>stdgraph</TT>" enables RADPROF to work interactively from a contour plot.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  The radial profiles of objects in the image <I>image</I> are computed
  the object center out to the radius <I>radius * scale</I>, in steps of
  <I>step * scale</I> pixels, and plotted. The initial positions are
  read from the image cursor or the text file <I>coords</I>.
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
  is enabled and RADPROF is run interactively the first measurement will appear
  to take a long time as the entire image must be read in before the measurement
  is actually made. All subsequent measurements will be very fast because RADPROF
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
  RADPROF can be run either interactively or in batch mode by setting the
  interactive switch to yes. In interactive mode starting x and y coordinates
  can either be read directly from the image cursor or read from the text
  file specified by <I>coords</I>. In interactive mode the results are
  plotted on the terminal. In batch mode the estimated positions
  are read from the text file <I>coords</I> or the image cursor parameter
  <I>icommands</I> is redirected to a text file containing a list of cursor
  commands.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_cursor_commands">CURSOR COMMANDS</A></H2>
  <! BeginSection: 'CURSOR COMMANDS'>
  <UL>
  <P>
  The RADPROF cursor commands are listed below.
  <P>
  <PRE>
  	Interactive Keystroke Commands
  <P>
  ?	Print help
  :	Colon commands
  v	Verify the critical parameters
  w	Store the current parameters
  d	Plot radial profile of current star
  i	Interactively set parameters using current star
  c	Fit center of current star
  t	Fit sky around the cursor position
  a       Average sky values fit around several cursor positions
  s	Fit sky around the current star 
  p	Fit star using current sky
  o	Fit star using current sky, output results
  f	Fit current star
  spbar	Fit current star, output results
  m	Move to next star in coordinate list
  n	Fit next star in coordinate list, output results
  l	Fit remaining stars in coordinate list, output results	
  r	Rewind the coordinate list
  e	Print error messages
  q	Exit task
  <P>
  <P>
  	Colon Commands
  <P>
  :show	[data/center/sky/fit]	List the parameters
  :m [n]	Move to next [nth] object in coordinate list
  :n [n]	Fit next [nth] object in coordinate list, output results
  <P>
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
  :fwhmpsf	[value]		Full-width half-maximum of psf (scale units)
  :emission	[y/n]		Emission features (y), absorption (n)
  :sigma		[value]		Standard deviation of sky (counts)
  :datamin	[value]		Minimum good pixel value (counts)
  :datamax	[value]		Maximum good pixel value (counts)
  <P>
  # Noise parameters
  <P>
  :noise		[string]	Noise model (constant|poisson)
  :gain		[string]	Gain image header keyword
  :ccdread	[string]	Readout noise image header keyword
  :epadu		[value]		Gain (electrons per adu)
  :readnoise	[value]		Readout noise (electrons)
  <P>
  # Observing parameters
  <P>
  :exposure	[value]		Exposure time image header keyword
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
  :khist		[value]		Sky histogram extent (+/- sigma)
  :binsize	[value]		Resolution of sky histogram (sigma)
  :sloclip	[value]		Low-side clipping factor in percent
  :shiclip	[value]		High-side clipping factor in percent
  :smaxiter	[value]		Maximum number of iterations
  :smooth		[y/n]		Lucy smooth the sky histogram
  :snreject	[value]		Maximum number of rejection cycles
  :sloreject	[value]		Low-side pixel rejection limits (sky sigma)
  :shireject	[value]		High-side pixel rejection limits (sky sigma)
  :rgrow		[value]		Region growing radius (scale units)
  <P>
  # Photometry parameters
  <P>
  :apertures	[string]	List of apertures (scale units)
  :zmag		[value]		Zero point of magnitude scale
  <P>
  # Profile fitting parameters
  <P>
  :radius		[value]		Maximum profile radius (scale units)
  :step		[value]		Step size for computed profile (scale units)
  :order		[value]		Number of spline pieces in fit
  :kreject	[value]		K-sigma rejection for fit (fit sigma)
  :nreject	[value]		Maximum number of rejection cycles
  <P>
  # Marking and plotting parameters
  <P>
  :mkcenter	[y/n]		Mark computed centers on display
  :mksky		[y/n]		Mark the sky annuli on the display
  :mkapert	[y/n]		Mark apertures on the display
  :radplot	[y/n]		Plot the radial profile
  <P>
  <P>
  <P>
  The following commands are available from inside the interactive setup menu.
  <P>
  <P>
                      Interactive Radprof Setup Menu
  <P>
  	v	Mark and verify the critical parameters (f,c,s,a,d,r,w,x)
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
  <P>
  	r	Mark and verify the photometry aperture radii
  	w	Mark and verify the radius of the radial profile
  	x	Mark and verify the step size of radial profile
  </PRE>
  <P>
  </UL>
  <! EndSection:   'CURSOR COMMANDS'>
  <H2><A NAME="s_algorithms">ALGORITHMS</A></H2>
  <! BeginSection: 'ALGORITHMS'>
  <UL>
  <P>
  Prior to computing the radial profile of the star, RADPROF computes the
  center, estimates a sky value, and does aperture photometry on the star
  using the parameters in the DATAPARS, CENTERPARS, FITSKYPARS, and
  PHOTPARS tasks.
  <P>
  Next the radial and intensity coordinates of all the pixels inside
  <I>radius * scale</I> are computed using the calculated center and sky
  values and fit to a least squares cubic spline of order <I>order</I> with
  optional bad data rejection.  The fit is interpolated at intervals of
  <I>step_size * scale</I> to derive the output profile and estimate the
  full width at half maximum of the object. The fit noise model parameters
  are defined in DATAPARS.
  <P>
  </UL>
  <! EndSection:   'ALGORITHMS'>
  <H2><A NAME="s_output">OUTPUT</A></H2>
  <! BeginSection: 'OUTPUT'>
  <UL>
  <P>
  In interactive mode the following quantities are printed on the standard
  output as each object is measured.  Error is a simple string which
  indicates whether an error was encountered in the
  the centering algorithm, the sky fitting algorithm, the photometry
  algorithm or the spline fitting algorithm respectively.
  Mag and merr are the magnitudes and errors in
  aperture N and xcenter, ycenter and msky are the
  x and y centers and the sky value respectively.
  Pfwhm is the fitted full width half maximum of the fitted radial profile.
  <P>
  <PRE>
      image  xcenter  ycenter  msky  pfwhm  mag[N]  merr[N] iers
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
  	   rapert  sum  area  flux mag  merr  pier  perr
  	   pfwhm  inorm  tinorm  rier  rerror
  	   pradius  intensity  tintensity
  </PRE>
  <P>
  Image and coords are the name of the image and coordinate file respectively.
  Id and lid are the sequence numbers of stars in the output and coordinate
  files respectively. Cier and cerror are the error code and accompanying
  error message respectively.  Xinit, yinit, xcenter, ycenter, xshift, yshift,
  and xerr, yerr are self explanatory and output in pixel units. The sense of
  the xshift and yshift definitions is the following.
  <P>
  <PRE>
  	xshift = xcenter - xinit
  	yshift = ycenter - yinit
  </PRE>
  <P>
  Sier and serror are the error code and accompanying error message respectively.
  Msky, stdev and sskew are the best estimate of the sky value (per pixel),
  standard deviation and skew respectively. Nsky and nsrej are the number of
  sky pixels and the number of sky pixels rejected respectively.
  <P>
  Itime is the exposure time, xairmass is self-evident, filter is an id
  string specifying the filter used during the observation and otime is
  a string containing the time of observation in whatever units the user
  has defined.
  <P>
  Rapert, sum, area and flux are the radius of the aperture in pixels, the total
  number of counts including sky in the aperture, the area of the aperture in
  square pixels, and the total number of counts in the aperture excluding sky.
  Mag and merr are the magnitude and error in the magnitude in the aperture
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
  Pfwhm is the full width at half intensity of the fitted profile. Inorm and
  tinorm are the normalization factors for the fitted radial profile and the
  fitted total intensity profile respectively. Rier and rerror are the spline
  fitting error code and accompanying error message. Pradius, intensity
  and tintensity are the computed radii, intensity and total intensity
  values at each radial step.
  <P>
  <P>
  </UL>
  <! EndSection:   'OUTPUT'>
  <H2><A NAME="s_errors">ERRORS</A></H2>
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
  	0        # No error
  	301      # The aperture is off the image
  	302      # The aperture is partially off the image
  	303      # The sky value is undefined
  	305      # There is bad data in the aperture
  </PRE>
  <P>
  If no error occurs during the profile fitting then rier is 0.
  Non-zero values of rier flag the following error conditions.
  <P>
  <PRE>
  	0       # No error
  	901     # The profile region is off the image
  	902     # The profile region is partially off the image
  	903	# There are too few points in the profile
  	904	# The fit is singular
  	905     # The sky value is undefined
  </PRE>
  <P>
  </UL>
  <! EndSection:   'ERRORS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Compute the radial profiles for a few  stars in dev$ypix using the
  display and the image cursor. Setup the task parameters using the
  interactive setup menu defined by the i key command.
  <P>
  <PRE>
  	ap&gt; display dev$ypix 1 fi+
  <P>
  	... display the image
  <P>
  	ap&gt; radprof dev$ypix 7.0 0.5 
  <P>
  	... type ? to print a short help page
  <P>
  	... move the image cursor to a star
  	... type i to enter the interactive setup menu
  	... enter maximum radius in pixels of the radial profile or
  	    CR to accept the default value
  	... set the fwhmpsf, centering radius, inner and outer sky
      	    annuli, apertures, sigma, profile radius and step size
  	    using the graphics cursor and the stellar radial profile
  	    plot
  	... typing &lt;CR&gt; leaves everything at the default value
  	... type q to quit the setup menu
  <P>
  	... type the v key to verify the parameters
  <P>
  	... type the w key to save the parameters in the parameter files
  <P>
  	... move the image cursor to the star of interest and tap
  	    the space bar
  <P>
  	... type :order 3 to change the spline order and see if the
  	     fit improves, if it does type w
  <P>
  	... a radial profile plot will appear on the graphics terminal
  <P>
  	... type q to quit and q to confirm the quit
  <P>
  	... by default radprof does not create an output file
  </PRE>
  <P>
  2. Compute the radial profiles for a few  stars in dev$ypix using a contour
  plot and the graphics cursor. Setup the task parameters using the interactive
  setup menu defined by the i key command. This option is only useful for
  those users (now very few) who do not have access to an image display server
  but do have access to a graphics terminal. 
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
  	... make a contour plot of dev$ypix
  <P>
  	ap&gt; contour dev$ypix  &gt;G ypix.plot1
  <P>
  	... store the contour plot of dev$ypix in ypix.plot1
  <P>
  	ap&gt; radprof dev$ypix 7.0 0.5
  <P>
  	... type ? to print the help page
  <P>
  	... move graphics cursor to a star
  	... type i to enter the interactive setup menu
  	... enter maximum radius in pixels of the radial profile or
  	    hit CR to accept the default value
  	... set the fwhmpsf, centering radius, inner and outer sky annuli,
  	    apertures, sigma, profile radius and step size using the
  	    graphics cursor and the stellar radial profile plot
  	... typing &lt;CR&gt; leaves everything at the default value
  	... type q to quit the setup menu
  <P>
  	... type the v key to verify the parameters
  <P>
  	... type the w key to save the parameters in the parameter files
  <P>
  	... type :.read ypix.plot1 to reload the contour plot
  <P>
  	... move the graphics cursor to the star of interest and tap
  	    the space bar
  <P>
  	... a radial profile plot will appear on the graphics terminal
  <P>
  	... repeat the above sequence for each additional star
  <P>
  	... type q to quit and q to confirm the quit
  <P>
  	... by default radprof does not create an output file
  </PRE>
  <P>
  3. Setup and run RADPROF interactively on a list of objects temporarily
  overriding the fwhmpsf, sigma, cbox, annulus, dannulus, apertures,
  radius, and step  parameters determined in examples 1 or 2.
  <P>
  <PRE>
          ap&gt; daofind dev$ypix fwhmpsf=2.6 sigma=25.0 verify-
  <P>
          ... make a coordinate list
  <P>
          ... the output will appear in the text file ypix.coo.1
  <P>
          ap&gt; radprof dev$ypix 7.0 0.5 fwhmpsf=2.6 sigma=5.0 cbox=7.0 \<BR>
              annulus=10.0 dannulus=5.0 apertures=5.0 coords=ypix.coo.1
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
          ... by default radprof does not create an output file
  </PRE>
  <P>
  4. Display and fit some stars in an image section and write the output
  coordinates in the coordinate system of the parent image.
  <P>
  <PRE>
          ap&gt; display dev$ypix[150:450,150:450] 1
  <P>
          ... display the image section
  <P>
          ap&gt; radprof dev$ypix[150:450,150:450] 7.0 0.5 output=default \<BR>
              wcsout=tv 
  <P>
          ... move cursor to stars and type spbar
  <P>
          ... type q to quit and q again to confirm quit
  <P>
          ... output will appear in ypix.prf.1
  <P>
          ap&gt; pdump ypix.prf.1 xc,yc yes | tvmark 1 STDIN col=204
  </PRE>
  <P>
  <P>
  5. Run RADPROF in batch mode using the coordinate file and the previously
  saved parameters. Save the text and plot output. 
  <P>
  <PRE>
  	ap&gt; radprof dev$ypix 7. 0.5 coords=ypix.coo.1 output="default" \<BR>
  	    plotfile=ypix.rplots inter- verify-
  <P>
  	... output will appear in m92.prf.2 and ypix.rplots
  <P>
  	ap&gt; gkidir ypix.rplots
  <P>
  	... get a listing of the plots in ypix.rplots
  <P>
  	ap&gt; gkiextract ypix.rplots 1-3 | stdplot dev=lw16
  <P>
  	... extract plots 1-3 and plot them on device lw16
  </PRE>
  <P>
  6. Repeat example 5 but assume that the input coordinates are ra and dec
  in degrees and degrees, turn off verification, and submit the task to to
  the background.
  <P>
  <PRE>
          ap&gt; display dev$ypix 1
  <P>
          ap&gt; rimcursor wcs=world &gt; radec.coo
  <P>
          ... move to selected stars and type any key
  <P>
          ... type ^Z to quit
  <P>
          ap&gt; radprof dev$ypix 7.0 0.5 coords=radec.coo output=default \<BR>
              plotfile=ypix.rplots2 wcsin=world verify- inter- &amp;
  <P>
          ... output will appear in ypix.prf.3, plots will appear in
              ypix.rplots2
  <P>
          ap&gt; pdump ypix.prf.3 xc,yc yes | tvmark 1 STDIN col=204
  <P>
          ... mark the stars on the display
  </PRE>
  <P>
  <P>
  7. Run RADPROF interactively without using the image display.
  <P>
  <PRE>
          ap&gt; show stdimcur
  <P>
          ... record the default value of stdimcur
  <P>
          ap&gt; set stdimcur = text
  <P>
          ... set the image cursor to the standard input
  <P>
          ap&gt; radprof dev$ypix 7.0 0.5 coords=ypix.coo.1
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
          ... type n to measure the next star
  <P>
          ... a one line summary of the answers will appear on the standard
              output for each star measured
  <P>
          ... type q to quit followed by q to confirm the quit
  <P>
  	... by default no output file is written
  <P>
          ap&gt; set stdimcur = &lt;default&gt;
  <P>
          ... reset the value of stdimcur
  </PRE>
  <P>
  8. Use a image cursor command file to drive the RADPROF task. The cursor
  command file shown below sets the cbox, annulus, dannulus, and apertures
  parameters computes the centers, sky values, magnitudes, and readial profiles
  for 3 stars, updates the parameter files, and quits the task.
  <P>
  <PRE>
          ap&gt; type cmdfile
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
          ap&gt; radprof dev$ypix 7.0 0.5 icommands=cmdfile  \<BR>
  	    plotfile=ypix.rplots3 verify-
  <P>
          ... by default no output file is written, plots will appear in
  	    ypix.rplots3
  </PRE>
  <P>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
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
  witch to "<TT>yes</TT>". It may be necessary to run gflush and to redisplay the image
  to get the overlays position correctly.
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  datapars, centerpars, fitskypars, photpars
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'CURSOR COMMANDS' 'ALGORITHMS' 'OUTPUT' 'ERRORS' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>