.. _center:

center — Compute accurate centers for a list of objects
=======================================================

**Package: irred**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  center -- compute accurate centers for a list of objects
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  center image
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>image</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD>The list of images containing the objects to be centered.
  </DD>
  </DL>
  <DL>
  <DT><B>coords = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='coords' Line='coords = ""'>
  <DD>The list of text files containing initial coordinates for the objects to
  be centered. Objects are listed in coords one object per line with the
  initial coordinate values in columns one and two. The number of coordinate
  files must be zero, one, or equal to the number of images.
  If coords is "<TT>default</TT>", "<TT>dir$default</TT>", or a directory specification then an
  coords file name of the form dir$root.extension.version is constructed and
  searched for, where dir is the directory, root is the root image name,
  extension is "<TT>coo</TT>" and version is the next available version number for the
  file.
  </DD>
  </DL>
  <DL>
  <DT><B>output = "<TT>default</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output = "default"'>
  <DD>The name of the results file or results directory. If output is
  "<TT>default</TT>", "<TT>dir$default</TT>", or a directory specification then an output file name
  of the form dir$root.extension.version is constructed, where dir is the
  directory, root is the root image name, extension is "<TT>ctr</TT>" and version is
  the next available version number for the file. The number of output files
  must be zero, one, or equal to the number of image files.  In both interactive
  and batch mode full output is written to output. In interactive mode
  an output summary is also written to the standard output.
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
  <DD>The name of the file containing the data dependent parameters.
  The critical parameters <I>fwhmpsf</I> and <I>sigma</I> are located in
  datapars.  If datapars is undefined then the default parameter set in 
  uparm directory is used.
  </DD>
  </DL>
  <DL>
  <DT><B>centerpars = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='centerpars' Line='centerpars = ""'>
  <DD>The name of the file containing the centering algorithm parameters.
  The critical parameters <I>calgorithm</I> and <I>cbox</I> are located in
  centerpars. If centerpars is undefined then the default parameter
  set in uparm is used.
  </DD>
  </DL>
  <DL>
  <DT><B>interactive = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = yes'>
  <DD>Interactive or non-interactive mode?
  </DD>
  </DL>
  <DL>
  <DT><B>radplots = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='radplots' Line='radplots = no'>
  <DD>If <I>radplots</I> is "<TT>yes</TT>" and CENTER is run in interactive mode, a radial
  profile of each star is plotted on the screen after the center is fit.
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
  <DT><B>wcsin = "<TT>logical</TT>", wcsout = "<TT>logical</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wcsin' Line='wcsin = "logical", wcsout = "logical"'>
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
  <DT><B>tv  </B></DT>
  <! Sec='PARAMETERS' Level=1 Label='tv' Line='tv  '>
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
  <DL>
  <DT><B>cache = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cache' Line='cache = no'>
  <DD>Cache the image pixels in memory. Cache may be set to </TT>"yes"<TT>, or </TT>"no"<TT>.
  By default cacheing is 
  disabled.
  </DD>
  </DL>
  <DL>
  <DT><B>verify = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verify' Line='verify = yes'>
  <DD>Verify the critical parameters in non-interactive mode ? Verify may be set to
  or </TT>"no.
  </DD>
  </DL>
  <DL>
  <DT><B>update = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='update' Line='update = no'>
  <DD>Update the critical parameters in non-interactive mode if <I>verify</I> is
  set to yes? Update may be set to "<TT>yes</TT>" or "<TT>no.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print messages on the terminal in non-interactive mode ? Verbose may be set
  to </TT>"yes"<TT> or </TT>"no.
  </DD>
  </DL>
  <DL>
  <DT><B>graphics = "<TT>)_.graphics</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = ")_.graphics"'>
  <DD>The default graphics device.
  Graphics may be set to the apphot package parameter value (the default), "<TT>yes</TT>",
  or "<TT>no.
  </DD>
  </DL>
  <DL>
  <DT><B>display = </TT>")_.display"<TT></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='display' Line='display = ")_.display"'>
  <DD>The default display device.  Display may be set to the apphot package
  parameter value (the default), </TT>"yes"<TT>, or </TT>"no. By default graphics overlay
  is disabled.  Setting display to one of "<TT>imdr</TT>", "<TT>imdg</TT>", "<TT>imdb</TT>", or "<TT>imdy</TT>"
  enables graphics overlay with the IMD graphics kernel.  Setting display to
  "<TT>stdgraph</TT>" enables CENTER to work interactively from a contour plot.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  CENTER computes accurate centers for a set of objects in the IRAF image
  <I>image</I>, whose initial coordinates are read from the image display cursor, 
  from the text file <I>coords</I>, or from a cursor command file.
  The computed x and y coordinates, the errors,  and the fitting parameters
  are written to the text file <I>output</I>.
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
  is enabled and CENTER is run interactively the first measurement will appear
  to take a long time as the entire image must be read in before the measurement
  is actually made. All subsequent measurements will be very fast because CENTER
  is accessing memory not disk. The point of cacheing is to speed up random
  image access by making the internal image i/o buffers the same size as the
  image itself. However if the input object lists are sorted in row order and
  sparse cacheing may actually worsen not improve the execution time. Also at
  present there is no point in enabling cacheing for images that are less than
  or equal to 524288 bytes, i.e. the size of the test image dev$ypix, as the
  default image i/o buffer is exactly that size. However if the size of dev$ypix
  is doubled by converting it to a real image with the chpixtype task then the
  effect of cacheing in interactive is can be quite noticeable if measurements
  of objects in the top and bottom halves of the image are alternated.
  <P>
  CENTER can be run either interactively or in batch mode by setting the
  parameter <I>interactive</I>. In interactive mode starting x and y positions
  can either be read directly from the image cursor or read from the text
  file <I>coords</I>. In interactive mode the user can examine, adjust, and
  save the algorithm parameters, change ojects interactively, query for
  the next or nth object in the list, or fit the entire coordinate list with
  the chosen parameter set.  In batch mode the positions can be read from the
  text file <I>coords</I> or the image cursor can be redirected to a text file
  containing a list of cursor commands as specified by the parameter
  <I>icommands</I>. 
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Cursor commands</H3>
  <! BeginSection: 'CURSOR COMMANDS'>
  <UL>
  <P>
  The following cursor commands are currently available.
  <P>
  <PRE>
  	Interactive Keystroke Commands
  <P>
  ?	Print help
  :	Colon commands
  v	Verify the critical parameters
  w	Save the current parameters
  d	Plot radial profile of current star
  i	Interactively set parameters using current star
  f	Fit center of current star
  spbar	Fit center of current star, output results
  m	Move to next star in coordinate list
  n	Center next star in coordinate list, output results
  l	Center remaining stars in coordinate list, output results
  e	Print error messages
  r	Rewind the coordinate list
  q	Exit task
  <P>
  <P>
  	Colon Commands
  <P>
  :show	[data/center]	List the parameters
  :m      [n]	        Move to next [nth] star in coordinate list
  :n      [n]	        Center next [nth] star in coordinate list,
  			output results
  <P>
  <P>
  	Colon Parameter Editing Commands
  <P>
  # Image and file name parameters
  <P>
  :image		[string]	Image name
  :coords		[string]	Coordinate file name
  :output 	[string]	Output file name
  <P>
  # Data dependent parameters
  <P>
  :scale		[value]		Image scale (units per pixel)
  :fwhmpsf	[value]		Full-width half-maximum of PSF (scale units)
  :emission	[y/n]		Emission feature (y), absorption (n)
  :sigma		[value]		Standard deviation of sky (counts)
  :datamin	[value]		Minimum good data value (counts)
  :datamax	[value]		Maximum good data value (counts)
  <P>
  # Noise parameters
  <P>
  :noise 		[string]	Noise model (constant|poisson)
  :gain		[string]	Gain image header keyword
  :ccdread	[string]	Readout noise image header keyword
  :epadu		[value]		Gain (electrons per adu)
  :readnoise	[value]		Readout noise (electrons)
  <P>
  # Observations parameters
  <P>
  :exposure	[string]	Exposure time image header keyword
  :airmass	[string]	Airmass image header keyword
  :filter		[string]	Filter image header keyword
  :obstime	[string]	Time of observation image header keyword
  :itime		[value]		Exposure time (time units)
  :xairmass	[value]		Airmass value (number)
  :ifilter	[string]	Filter id string
  :otime		[string]	Time of observation (time units)
  <P>
  # Centering parameters 
  <P>
  :calgorithm	[string]	Centering algorithm
  :cbox		[value]		Width of centering box (scale units)
  :cthreshold	[value]		Centering intensity threshold (sigma)
  :cmaxiter	[value]		Maximum number of iterations
  :maxshift	[value]		Maximum center shift (scale units)
  :minsnratio	[value]		Minimum signal to noise for centering
  :clean		[y/n]		Clean subraster before centering
  :rclean		[value]		Cleaning radius (scale units)
  :rclip		[value]		Clipping radius (scale units)
  :kclean		[value]		Clean K-sigma rejection limit (sigma)
  <P>
  # Plotting and marking parameters
  <P>
  :mkcenter	[y/n]		Mark computed centers on the display
  :radplot	[y/n]		Plot radial profile of object
  <P>
  <P>
  The following keystroke commands are available from the interactive setup
  menu.
  <P>
                      Interactive Center Setup Menu
  <P>
  	v	Mark and verify the critical center parameters (f,s,c)
  <P>
  	f	Mark and verify the full-width half-maximum of the psf
  	s	Mark and verify the standard deviation of the background
  	l	Mark and verify the minimum good data value
  	u	Mark and verify the maximum good data value
  <P>
  	c	Mark and verify the centering box half-width
  	n	Mark and verify the cleaning radius
  	p	Mark and verify the clipping radius
  </PRE>
  <P>
  </UL>
  <! EndSection:   'CURSOR COMMANDS'>
  <H3>Algorithms</H3>
  <! BeginSection: 'ALGORITHMS'>
  <UL>
  <P>
  Descriptions of the data dependent parameters and the centering
  algorithm parameters can be found in the online manual pages for
  <I>datapars</I> and <I>centerpars</I>.
  <P>
  </UL>
  <! EndSection:   'ALGORITHMS'>
  <H3>Output</H3>
  <! BeginSection: 'OUTPUT'>
  <UL>
  <P>
  In interactive mode the following quantities are written to the terminal
  as each object is measured. Error is a simple string which indicates
  whether an error condition has been flagged.  The centers and their errors are
  in pixel units.
  <P>
  <PRE>
  	image  xinit  yinit  xcenter  ycenter  xerr  yerr  error
  </PRE>
  <P>
  In both interactive and batch mode the full output is written to the
  text file <I>output</I>. At the beginning of each file is a header
  listing the current values of the parameters when the first stellar
  record was written. These parameters can be subsequently altered.
  For each star measured the following record is written
  <P>
  <PRE>
  	image  xinit  yinit  id  coords  lid
  	   xcenter  ycenter  xshift  yshift  xerr  yerr  cier error
  </PRE>
  <P>
  Image and coords are the name of the image and coordinate file respectively.
  Id and lid are the sequence numbers of stars in the output and coordinate
  files respectively. Cier and error are the centering error code and accompanying
  error message respectively.  Xinit, yinit, xcenter, ycenter, xshift, yshift,
  and xerr, yerr are self explanatory and output in pixel units. The sense of
  the xshift and yshift definitions is the following.
  <P>
  <PRE>
  	xshift = xcenter - xinit
  	yshift = ycenter - yinit
  </PRE>
  <P>
  In interactive mode a radial profile of each measured object is plotted
  in the graphics window if <I>radplots</I> is "<TT>yes</TT>".
  <P>
  In interactive and batchmode a radial profile plot is written to
  <I>plotfile</I>  if it is defined each time the result of an object
  measurement is written to <I>output</I> .
  <P>
  </UL>
  <! EndSection:   'OUTPUT'>
  <H3>Errors</H3>
  <! BeginSection: 'ERRORS'>
  <UL>
  <P>
  If the object centering was error free then the field cier will be zero.
  Non-zero values in the cier column flag the following error conditions.
  <P>
  <PRE>
  	0        # No error
  	101      # The centering box is off the image
  	102      # The centering box is partially off the image
  	103      # The S/N ratio is low in the centering box
  	104      # There are two few points for a good fit
  	105      # The x or y center fit is singular
  	106      # The x or y center fit did not converge
  	107      # The x or y center shift is greater than maxshift
  	108      # There is bad data in the centering box
  </PRE>
  <P>
  </UL>
  <! EndSection:   'ERRORS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Compute the centers for a few  stars in dev$ypix using the image display
  and the image cursor. Setup the task parameters using the interactive
  setup menu defined by the i keystroke command and a radial profile plot.
  <P>
  <PRE>
  	ap&gt; display dev$ypix 1 fi+
  <P>
  	... display the image
  <P>
  	ap&gt; center dev$ypix
  <P>
  	... type ? to see help screen
  <P>
  	... move image cursor to a star
  	... type i to enter the interactive setup menu
  	... enter the maximum radius in pixels for the radial profile or
  	    accept the default with a CR
  	... type  v to get the default menu
  	... set the fwhmpsf, sigma, and centering box half-width using the
  	    graphics cursor and the stellar radial profile plot
  	... typing &lt;CR&gt; after a prompt leaves the parameter at its default
  	    value
  	... type q to exit setup menu
  <P>
  	... type the v key to verify the critical parameters
  <P>
  	... type the w key to save the parameters in the parameter files
  <P>
  	... move the image cursor to the stars of interest and tap
  	    the space bar
  <P>
  	... type q to quit followed by q to confirm the quit
  <P>
  	... the output will appear in ypix.ctr.1
  <P>
  </PRE>
  <P>
  2. Compute the centers for a few stars in dev$ypix using the contour plot
  and the graphics cursor. This option is only useful for those (now very few)
  users who have access to a graphics terminal but not to an image display
  server. Setup the task parameters using the interactive setup menu defined by
  the i key command as in example 1.
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
  	ap&gt; contour dev$ypix &gt;G ypix.plot1
  <P>
  	... store the contour plot of ypix in the file ypix.plot
  <P>
  	ap&gt; center dev$ypix display=stdgraph
  <P>
  	... type ? to see the help screen
  <P>
  	... move graphics cursor to a star
  	... type i to enter the interactive setup menu
  	... enter the maximum radius in pixels for the radial profile or
  	    accept the default with a CR
  	... type v key to get the default setup menu
  	... enter maximum radius in pixels of the radial profile
  	... set the fwhmpsf, sigma, and centering box half-width
  	    using the graphics cursor and the stellar radial profile plot
  	... typing &lt;CR&gt; after the prompt leaves the parameter at its
  	    default value
  	... type q to quit the setup menu
  <P>
  	... type the v key to verify critical parameters
  <P>
  	... type the w key to save the parameters in the parameter files
  <P>
  	... retype :.read ypix.plot1 to reload the contour plot
  <P>
  	... move the graphics cursor to the stars of interest and tap
  	    the space bar
  <P>
  	... a one line summary of the answers will appear on the standard
  	    output for each star measured
  <P>
  	... type q to quit followed by q to confirm the quit
  <P>
  	... full output will appear in the text file ypix.ctr.2 
  <P>
  	ap&gt; set stdimcur = &lt;default&gt;
  <P>
  	... reset stdimcur to its previous value
  </PRE>
  <P>
  <P>
  3. Setup and run CENTER interactively on a list of objects temporarily
  overriding the fwhmpsf, sigma, and cbox parameters determined in examples
  1 or 2.
  <P>
  <PRE>
  	ap&gt; daofind dev$ypix fwhmpsf=2.6 sigma=25.0 verify-
  <P>
  	... make a coordinate list 
  <P>
  	... the output will appear in the text file ypix.coo.1
  <P>
  	ap&gt; center dev$ypix cbox=7.0 coords=ypix.coo.1 
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
  	... the output will appear in ypix.ctr.3 ...
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
  	ap&gt; center dev$ypix[150:450,150:450] wcsout=tv
  <P>
  	... move cursor to stars and type spbar
  <P>
  	... type q to quit and q again to confirm quit
  <P>
  	... output will appear in ypix.ctr.4
  <P>
  	ap&gt; pdump ypix.ctr.4 xc,yc yes | tvmark 1 STDIN col=204 
  </PRE>
  <P>
  <P>
  5. Run CENTER in batch mode using the coordinate file and the previously
  saved parameters. Verify the critical parameters.
  <P>
  <PRE>
  	ap&gt; center dev$ypix coords=ypix.coo.1 verify+ inter-
  <P>
  	... output will appear in ypix.ctr.5 ...
  </PRE>
  <P>
  <P>
  6. Repeat example 5 but assume that the input coordinate are ra and dec
  in degrees and degrees, turn off verification, and submit the task to to
  the background.
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
  	ap&gt; center dev$ypix coords=radec.coo wcsin=world verify- inter- &amp;
  <P>
  	... output will appear in ypix.ctr.6
  <P>
  	ap&gt; pdump ypix.ctr.6 xc,yc yes | tvmark 1 STDIN col=204
  <P>
  	... mark the stars on the display
  <P>
  <P>
  7. Run CENTER interactively without using the image display.
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
  	ap&gt; center dev$ypix coords=ypix.coo.1
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
  	... set the fwhmpsf, sigma, and centering box half-width
  	    using the graphics cursor and the stellar radial profile plot
  	... typing &lt;CR&gt; after the prompt leaves the parameter at its default
  	    value
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
  	... full output will appear in the text file ypix.ctr.7 
  <P>
  	ap&gt; set stdimcur = &lt;default&gt;
  <P>
  	... reset the value of stdimcur
  </PRE>
  <P>
  8. Use a image cursor command file to drive the CENTER task. The cursor command
  file shown below sets the fwhmpsf, calgorithm, and cbox parameters, computes
  the centers for 3 stars, updates the parameter files, and quits the task.
  <P>
  <PRE>
  	ap&gt; type cmdfile
  	: calgorithm gauss
  	: fwhmpsf 2.5
  	: cbox 9.0
  	442 410 101 \040 
  	349 188 101 \040 
  	225 131 101 \040 
  	w
  	q
  <P>
  	ap&gt; center dev$ypix icommands=cmdfile  verify-
  <P>
  	... full output will appear in ypix.ctr.8
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  <P>
  It is the responsibility of the user to make sure that the image displayed
  in the image display is the same as the image specified by the image parameter.
  <P>
  Commands which draw to the image display are disabled by default.
  To enable graphics overlay on the image display, set the display
  parameter to "<TT>imdr</TT>", "<TT>imdg</TT>", "<TT>imdb</TT>", or "<TT>imdy</TT>" to get red, green,
  blue or yellow overlays and set the centerpars mkcenter switch to
  "<TT>yes</TT>". It may be necessary to run gflush and to redisplay the image
  to get the overlays position correctly. 
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  datapars, centerpars
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'CURSOR COMMANDS' 'ALGORITHMS' 'OUTPUT' 'ERRORS' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
