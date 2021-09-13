qphot — Measure quick magnitudes for a list of stars
====================================================

**Package: apphot**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>qphot (May00)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.digiphot.apphot</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>qphot (May00)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>qphot</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  qphot -- quick aperture photometer
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  qphot image cbox annulus dannulus apertures
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_image">image</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD>The list of images containing the objects to be measured.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_cbox">cbox</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cbox' Line='cbox'>
  <DD>The width of the centering box in pixels.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_annulus">annulus</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='annulus' Line='annulus'>
  <DD>The inner radius of the sky annulus in pixels.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_dannulus">dannulus</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dannulus' Line='dannulus'>
  <DD>The width of the sky annulus in pixels.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_apertures">apertures</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='apertures' Line='apertures'>
  <DD>The list of aperture radii in pixels. Apertures is a string parameter 
  specifying either a single aperture radius e.g. "<TT>3.0</TT>", a list of aperture
  radii separated by commas e.g. "<TT>3.0,5.0,10.0</TT>", or a range of aperture radii
  e.g. "<TT>1.0:20.0:1.0</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_coords">coords = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='coords' Line='coords = ""'>
  <DD>The list of text files containing initial coordinates for the objects to
  be measured. Objects are listed in coords one object per line with the
  initial coordinate values in columns one and two. The number of coordinate
  files must be zero, one, or equal to the number of images. If coords is
  "<TT>default</TT>", "<TT>dir$default</TT>", or a directory specification then a coords file name
  of the form dir$root.extension.version is constructed and searched for,
  where dir is the directory, root is the root image name, extension is "<TT>coo</TT>"
  and version is the next available version number for the file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output = "<TT>default</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output = "default"'>
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
  <DT><B><A NAME="l_plotfile">plotfile = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='plotfile' Line='plotfile = ""'>
  <DD>The name of the file containing radial profile plots of the stars written
  to the output file. If plotfile is defined then a radial profile plot
  is written to plotfile every time a record is written to <I>output</I>.
  The user should be aware that this can be a time consuming operation.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_zmag">zmag = 25.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='zmag' Line='zmag = 25.0'>
  <DD>The zero point of the magnitude scale.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_exposure">exposure = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='exposure' Line='exposure = ""'>
  <DD>The image header keyword containing the exposure time.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_airmass">airmass = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='airmass' Line='airmass = ""'>
  <DD>The image header keyword containing the airmass of the observation.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_filter">filter = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='filter' Line='filter = ""'>
  <DD>The image header keyword containing the filter id of the observation.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_obstime">obstime = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='obstime' Line='obstime = ""'>
  <DD>The image header keyword containing the time of the observation.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_epadu">epadu = 1.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='epadu' Line='epadu = 1.0'>
  <DD>The gain in photons per adu. Epadu is used to compute the magnitude errors.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interactive">interactive = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = yes'>
  <DD>Interactive or batch mode.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_radplots">radplots = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='radplots' Line='radplots = no'>
  <DD>If radplots is "<TT>yes</TT>" and QPHOT is run in interactive mode then a radial profile
  of each star is plotted on the screen after it is measured.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_icommands">icommands = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='icommands' Line='icommands = ""'>
  <DD>The image display cursor or image cursor command file.
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
  coordinate system. The input coordinate system options are "<TT>logical</TT>", tv"<TT>,
  </TT>"physical"<TT>, and </TT>"world"<TT>. The output coordinate system options are </TT>"logical"<TT>,
  </TT>"tv"<TT>, and </TT>"physical"<TT>. The image cursor coordinate system is assumed to
  be the </TT>"tv"<TT> system.
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
  wcsin and wcsout are </TT>"logical"<TT> and </TT>"logical"<TT> respectively.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_cache">cache = </TT>")_.cache"<TT></A></B></DT>
  <! Sec='PARAMETERS' Level=-1 Label='cache' Line='cache = ")_.cache"'>
  <DD>Cache the image pixels in memory. Cache may be set to the value of the apphot
  package parameter (the default), </TT>"yes"<TT>, or </TT>"no"<TT>. By default cacheing is 
  disabled.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = </TT>")_.verbose"<TT></A></B></DT>
  <! Sec='PARAMETERS' Level=-1 Label='verbose' Line='verbose = ")_.verbose"'>
  <DD>Print messages in non-interactive mode ? Verbose may be set to the apphot
  package parameter value (the default), </TT>"yes"<TT>, or </TT>"no.
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
  <DD>The default display device. Display may be set to the apphot package parameter
  value (the default), </TT>"yes"<TT>, or </TT>"no. By default graphics overlay is disabled.
  Setting display to one of "<TT>imdr</TT>", "<TT>imdg</TT>", "<TT>imdb</TT>", or "<TT>imdy</TT>" enables graphics
  overlay with the IMD graphics kernel.  Setting display to "<TT>stdgraph</TT>" enables
  QPHOT to work interactively from a contour plot.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  QPHOT computes accurate centers, sky values, and magnitudes for a list of
  objects in the IRAF image <I>image</I> whose initial coordinates are
  read from the image cursor or the coordinate file <I>coords</I>,
  and writes the computed x and y coordinates, sky values, and
  magnitudes to the text file <I>output</I>.
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
  In interactive mode the user measure objects interactively with the image
  cursor, or select them interactively from the coordinate list <I>coords</I>.
  In batch mode the coordinates can be read directly from <I>coords</I>, or from 
  the cursor command file specified by the parameter <I>icommands</I>.
  <P>
  If <I>cache</I> is yes and the host machine physical memory and working set size
  are large enough, the input image pixels are cached in memory. If cacheing
  is enabled and QPHOT is run interactively the first measurement will appear
  to take a long time as the entire image must be read in before the measurement
  is actually made. All subsequent measurements will be very fast because QPHOT
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
  QPHOT computes accurate centers for each object using the centroid
  centering algorithm, pixels inside <I>cbox</I> and the default values of the
  <I>centerpars</I> parameters.  Accurate sky values for each object are
  computed using the <I>centroid</I> sky fitting algorithm with histogram
  smoothing turned on, pixels inside the sky annulus defined by <I>annulus</I>
  and <I>dannulus</I>, and the default values of the remaining sky fitting
  parameters as defined in the <I>fitskypars</I> parameter set. Magnitudes
  are computed using pixels inside the apertures defined by <I>apertures</I>.
  The user must set the gain <I>epadu</I> to ensure that the magnitude error
  estimates are correctly computed and <I>exposure</I> to normalize the computed
  magnitudes to an exposure time of 1 time unit. The zero point of the magnitude
  scale can be adjusted by setting <I>zmag</I>. <I>Airmass</I>, <I>filter</I>,
  and <I>obstime</I> are book-keeping parameters. Setting  them to appropriate
  values will simplify future analysis and calibration steps.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_cursor_commands">CURSOR COMMANDS</A></H2>
  <! BeginSection: 'CURSOR COMMANDS'>
  <UL>
  <P>
  The following list of cursor commands are currently available.
  <P>
  <PRE>
  	Interactive Photometry Commands
  <P>
  ?	Print help
  :	Colon commands
  w	Save the current parameters
  d	Plot radial profile of current star
  i	Interactively set parameters using current star
  c	Fit center of current star
  t	Fit sky around the cursor
  a       Average sky values fit around several cursor positions
  s	Fit sky for current centered star
  p	Do photometry for current star, using current sky
  o	Do photometry for current star, using current sky, output results
  f	Do photometry for current star
  spbar	Do photometry for current star, output results
  e	Print error messages
  m	Move to next star in coordinate list
  n	Do photometry for next star in coordinate list, output results
  l	Do photometry for remaining stars in coordinate list, output results
  r	Rewind the coordinate list
  q	Exit task
  <P>
  <P>
  	Colon Commands
  <P>
  :show	List the parameters
  :m [n]	Move to next [nth] star in coordinate list
  :n [n]	Do photometry for next [nth] star in coordinate list, output results
  <P>
  	Colon Parameter Editing Commands
  <P>
  :image		[string]	Image name
  :output		[string]	Output file name
  :coords		[string]	Coords file name
  <P>
  :cbox		[value]		Width of the centering box (pixels)
  :annulus	[value]		Inner radius of sky annulus (pixels)
  :dannulus	[value]		Width of sky annulus (pixels)
  :apertures	[string]	List of aperture radii (pixels)
  :zmag		[value]		Zero point of magnitude scale (magnitudes)
  :epadu		[value]		Gain (electrons  per adu)
  <P>
  :exposure	[string]	Exposure time image header keyword
  :airmass	[string]	Airmass image header keyword
  :filter		[string]	Filter image header keyword
  :obstime	[string]	Time of observation image header keyword
  <P>
  :radplot	[y/n]		Plot radial profile of object
  <P>
  <P>
  The following commands are available from inside the interactive setup menu
  using the i key.
  <P>
  <P>
                      Interactive Qphot Setup Menu
  <P>
  	v	Mark and verify the critical parameters (c,a,d,r)
  <P>
  	c	Mark and verify the centering box width
  	a	Mark and verify the inner radius of the sky annulus
  	d	Mark and verify the width of the sky annulus
  	r	Mark and verify the aperture radii
  </PRE>
  <P>
  </UL>
  <! EndSection:   'CURSOR COMMANDS'>
  <H2><A NAME="s_output">OUTPUT</A></H2>
  <! BeginSection: 'OUTPUT'>
  <UL>
  In interactive mode the following quantities are printed on the standard
  output as each object is measured. Error is a simple string which indicates
  whether the task encountered an error condition from
  the centering algorithm, the sky fitting algorithm or the photometry
  algorithm respectively. Mag are the magnitudes in
  apertures 1 through N respectively and xcenter, ycenter and msky are the
  x and y centers and the sky value respectively.
  <P>
  <PRE>
      image  xcenter  ycenter  msky  mag[1 ... N]  error
  </PRE>
  <P>
  In both interactive and batch mode full output is written to the text file
  <I>output</I>. At the beginning of each file is a header listing the
  current values of the parameters when the first stellar record was written.
  These parameters can be subsequently altered. For each star measured the
  following record is written.
  <P>
  <PRE>
  	image  xinit  yinit  id  coords  lid
  	   xcenter  ycenter  xshift  yshift  xerr  yerr  cier cerror
  	   msky  stdev  sskew  nsky  nsrej  sier  serror
  	   itime  xairmass  ifilter  otime
  	   rapert  sum  area  flux mag  merr  pier  perror
  </PRE>
  <P>
  Image and coords are the name of the image and coordinate file respectively.
  Id and lid are the sequence numbers of stars in the output and coordinate
  files respectively. Cier and cerror are the error code and accompanying
  error message for the center computation.  Xinit, yinit, xcenter, ycenter,
  xshift, yshift, and xerr, yerr are self explanatory and output in pixel units.
  The sense of the xshift and yshift definitions is the following.
  <P>
  <PRE>
  	xshift = xcenter - xinit
  	yshift = ycenter - yinit
  </PRE>
  <P>
  Sier and serror are the sky fitting error code and accompanying error message
  respectively.  Msky, stdev and sskew are the best estimate of the sky value
  (per pixel), standard deviation and skew respectively. Nsky and nsrej are
  the number of sky pixels used and the number of sky pixels rejected
  respectively.
  <P>
  Itime is the exposure time, xairmass is self-evident, ifilter is an
  id string used to identify the filter used during the observation, and
  otime is a string containing the time stamp in whatever units the
  user has written into the image header or the otime parameter.
  <P>
  Rapert, sum, area, and flux  are the radius of the aperture in pixels, the
  total number of counts including sky in the aperture, the area of the aperture
  in square pixels, and the total number of counts in the aperture excluding
  sky. Mag and merr are the magnitude and error in the magnitude in the aperture.
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
  <H2><A NAME="s_errors">ERRORS</A></H2>
  <! BeginSection: 'ERRORS'>
  <UL>
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
  107      # The x or y center shift is greater than 1 pixel
  108      # There is bad data in the centering box
  <P>
  </PRE>
  <P>
  If all goes well during the sky fitting process then the error code sier
  will be 0. Non-zero values of sier flag the following error conditions.
  <P>
  <PRE>
  0         # No error
  201       # There are no sky pixels in the sky annulus
  202       # Sky annulus is partially off the image
  203	  # The histogram of sky pixels has no width
  204	  # The histogram of sky pixels is flat or concave
  205       # There are too few points for a good sky fit
  206       # The sky fit is singular
  207       # The sky fit did not converge
  208       # The graphics stream is undefined
  209       # The file of sky values does not exist
  210       # The sky file is at EOF
  211       # Cannot read the sky value correctly
  212       # The best fit parameter are non-physical
  <P>
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
  305	 # There is bad data in the aperture
  </PRE>
  <P>
  </UL>
  <! EndSection:   'ERRORS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Perform aperture photometry interactively for a few stars in dev$ypix using
  the display and the image cursor.
  <P>
  <PRE>
  	ap&gt; display dev$ypix 1 fi+
  <P>
  	... display the image
  <P>
  	ap&gt; qphot dev$ypix 5. 10. 5. 2.,4.,6.0 
  <P>
  	... move image cursor to objects of interest and tap space bar
  <P>
  	... a 1 line summary will be printed on the standard output
  	    for each object measured
  <P>
  	... type q to quit and q again to confirm the quit
  <P>
  	... full output will appear in ypix.mag.1
  </PRE>
  <P>
  <P>
  2. Perform aperture photometry interactively for a few stars in dev$ypix
  using the contour plot and the graphics cursor. This option is only useful
  for those (now very few) users who have access to a graphics terminal but
  not to an image display server. Setup the task parameters using the
  interactive setup menu defined by the i key command as in example 1.
  <P>
  <P>
  <PRE>
          ap&gt; show stdimcur
  <P>
          ... record the default value of stdimcur
  <P>
  	ap&gt; set stdimcur = stdgraph
  <P>
          ... define the image cursor to be the graphics cursor
  <P>
          ap&gt; contour dev$ypix
  <P>
          ... make a contour plot of dev$ypix
  <P>
  	ap&gt; contour dev$pix &gt;G ypix.plot1
  <P>
  	... store the contour plot of dev$ypix in the file ypix.plot1
  <P>
  	ap&gt; qphot dev$ypix 5. 10. 5. 2.,4.,6.0 
  <P>
          ... type ? to see the help screen
  <P>
  	... move image cursor to objects of interest and tap space bar
  <P>
  	... a 1 line summary will be printed on the standard output
  	    for each object measured
  <P>
  	... type q to quit and q again to confirm the quit
  <P>
  	... full output will be written to ypix.mag.2
  <P>
          ap&gt; set stdimcur = &lt;default&gt;
  <P>
          ... reset stdimcur to its previous value
  </PRE>
  <P>
  <P>
  <P>
  3. Setup and run QPHOT interactively on a list of objects temporarily
  overriding the fwhmpsf, sigma, cbox, annulus, dannulus, and apertures
   parameters determined in examples 1 or 2.
  <P>
  <PRE>
          ap&gt; daofind dev$ypix fwhmpsf=2.6 sigma=25.0 verify-
  <P>
          ... make a coordinate list
  <P>
          ... the output will appear in the text file ypix.coo.1
  <P>
          ap&gt; qphot dev$ypix 7.0 12.0 5.0 "3.0,5.0" coords=ypix.coo.1
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
          ... the output will appear in ypix.mag.3 ...
  </PRE>
  <P>
  <P>
  4. Display and measure some stars in an image section and write the output
  coordinates in the coordinate system of the parent image.
  <P>
  <PRE>
          ap&gt; display dev$ypix[150:450,150:450] 1
  <P>
          ... display the image section
  <P>
          ap&gt; qphot dev$ypix[150:450,150:450] 7.0 12.0 5.0 "3.0,5.0" wcsout=tv
  <P>
          ... move cursor to stars and type spbar
  <P>
          ... type q to quit and q again to confirm quit
  <P>
          ... output will appear in ypix.mag.4
  <P>
          ap&gt; pdump ypix.mag.4 xc,yc yes | tvmark 1 STDIN col=204
  </PRE>
  <P>
  <P>
  5. Run QPHOT in batch mode using the coordinate file and the previously
  saved parameters.
  <P>
  <PRE>
          ap&gt; qphot dev$ypix 7. 12.0 5.0 "3.0,5.0" coords=ypix.coo.1 inter-
  <P>
          ... output will appear in ypix.mag.5 ...
  </PRE>
  <P>
  <P>
  6. Repeat example 5 but assume that the input coordinate are ra and dec
  in degrees and degrees and submit the task to the background.
  <P>
  <PRE>
          ap&gt; display dev$ypix
  <P>
          ap&gt; rimcursor wcs=world &gt; radec.coo
  <P>
          ... move to selected stars and type any key
  <P>
          ... type ^Z to quit
  <P>
          ap&gt; qphot dev$ypix 7.0 12.0 5.0 "3.0,5.0" coords=radec.coo \<BR>
              wcsin=world inter- &amp;
  <P>
          ... output will appear in ypix.ctr.6
  <P>
          ap&gt; pdump ypix.mag.6 xc,yc yes | tvmark 1 STDIN col=204
  <P>
          ... mark the stars on the display
  </PRE>
  <P>
  <P>
  7. Run QPHOT interactively without using the image display.
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
          ap&gt; qphot dev$ypix 7.0 12.0 5.0 "3.0,5.0" coords=ypix.coo.1
  <P>
          ... type ? for optional help
  <P>
          ... type :m 3 to set the initial coordinates to those of the
              third star in the list
  <P>
          ... type "442 409 101 i" to enter the interactive setup menu
          ... enter the maximum radius in pixels for the radial profile or
              accept the default with a CR
          ... type v to enter the default menu
          ... reset cbox, annulus, dannulus, and apertures using the graphics
              cursor and the stellar radial profile plot
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
          ... full output will appear in the text file ypix.mag.7
  <P>
          ap&gt; set stdimcur = &lt;default&gt;
  <P>
          ... reset the value of stdimcur
  </PRE>
  <P>
  8. Use a image cursor command file to drive the qphot task. The cursor command
  file shown below computes the centers, sky values, and magnitudes  for 3 stars
  and quits the task.
  <P>
  <PRE>
          ap&gt; type cmdfile
          442 410 101 \040
          349 188 101 \040
          225 131 101 \040
          q
  <P>
          ap&gt; qphot dev$ypix 7.0 12.0 5.0 "3.0,5.0" icommands=cmdfile
  <P>
          ... full output will appear in ypix.mag.8
  </PRE>
  <P>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  <P>
  It is the responsibility of the user to make sure that the image displayed
  in the image display is the same as that specified by the image parameter.
  <P>
  Commands which draw to the image display are disabled by default.
  To enable graphics overlay on the image display, set the display
  parameter to "<TT>imdr</TT>", "<TT>imdg</TT>", "<TT>imdb</TT>", or "<TT>imdy</TT>" to get red, green,
  blue or yellow overlays. It may be necessary to run gflush and to
  redisplay the image to get the overlays position correctly.
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  phot,wphot,polyphot
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'CURSOR COMMANDS' 'OUTPUT' 'ERRORS' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>