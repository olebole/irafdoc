.. _daofind:

daofind — Find stars in an image using the dao algorithm
========================================================

**Package: apphot**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  daofind -- automatically detect objects in an image
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  daofind image 
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>image</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD>The list of images in which objects are to be detected.
  </DD>
  </DL>
  <DL>
  <DT><B>output  = "<TT>default</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output  = "default"'>
  <DD>The name of the results file or the results directory. If output is
  "<TT>default</TT>", "<TT>dir$default</TT>" or a directory specification then a results file
  name of the form dir$root.extension.version is constructed, where
  dir is the directory, root is the root image name, extension is "<TT>coo</TT>"
  and version is the next available version number for the file. If the
  output string is undefined then no output file is created. One output
  file is created for every input image.
  </DD>
  </DL>
  <DL>
  <DT><B>starmap = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='starmap' Line='starmap = ""'>
  <DD>The name of the image prefix and/or directory where the density enhancement
  image will be stored. If starmap is undefined or a directory,
  DAOFIND will create a temporary image which is deleted on exit from
  the program. Otherwise starmap is prefixed to the image name
  and the density enhancement image will be saved for use in a subsequent
  run of DAOFIND.
  </DD>
  </DL>
  <DL>
  <DT><B>skymap = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='skymap' Line='skymap = ""'>
  <DD>The name of the image prefix and/or directory where the mean density
  image will be stored.  If skymap is undefined or a directory, no mean density
  image is created. Otherwise skymap is prefixed to the image name
  and the mean density image will be saved on disk. Skymap is not used by
  the DAOFIND algorithms, but may be used by the user as a check on DAOFIND,
  since the sum of starmap and skymap is a type of best fit to the original 
  image.
  </DD>
  </DL>
  <DL>
  <DT><B>datapars = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='datapars' Line='datapars = ""'>
  <DD>The name of the file containing the data dependent parameters. The critical
  parameters <I>fwhmpsf</I> and <I>sigma</I> are located here.  If <I>datapars</I>
  is undefined then the default parameter set in the user's uparm directory is
  used.
  </DD>
  </DL>
  <DL>
  <DT><B>findpars = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='findpars' Line='findpars = ""'>
  <DD>The name of the file containing the object detection parameters. The 
  parameter <I>threshold</I> is located here. If findpars is undefined then
  the default parameter set in the user's uparm directory is used.
  </DD>
  </DL>
  <DL>
  <DT><B>boundary = "<TT>nearest</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='boundary' Line='boundary = "nearest"'>
  <DD>The type of boundary extension. The choices are:
  <DL>
  <DT><B>nearest</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='nearest' Line='nearest'>
  <DD>Use the value of the nearest boundary pixel.
  </DD>
  </DL>
  <DL>
  <DT><B>constant</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='constant' Line='constant'>
  <DD>Use a constant value.
  </DD>
  </DL>
  <DL>
  <DT><B>reflect</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='reflect' Line='reflect'>
  <DD>Generate a value by reflecting around the boundary.
  </DD>
  </DL>
  <DL>
  <DT><B>wrap</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='wrap' Line='wrap'>
  <DD>Generate a value by wrapping around to the other side of the image.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>constant = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='constant' Line='constant = 0'>
  <DD>The constant for constant boundary extension.
  </DD>
  </DL>
  <DL>
  <DT><B>interactive = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = no'>
  <DD>Interactive or batch mode?
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
  <DT><B>wcsout = "<TT>)_.wcsout</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wcsout' Line='wcsout = ")_.wcsout"'>
  <DD>The coordinate system of the output coordinates written to <I>output</I>. The
  image header coordinate system is used to transform from the internal "<TT>logical</TT>"
  pixel coordinate system to the output coordinate system. The output coordinate
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
  The wcsout parameter defaults to the value of the package parameter of the same
   name. The default values of the package parameters wcsin and wcsout are
  "<TT>logical</TT>" and "<TT>logical</TT>" respectively.
  </DD>
  </DL>
  <DL>
  <DT><B>cache = "<TT>)_.cache</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cache' Line='cache = ")_.cache"'>
  <DD>Cache the image pixels in memory. Cache may be set to the value of the apphot
  package parameter (the default), "<TT>yes</TT>", or "<TT>no</TT>". By default cacheing is 
  disabled.
  </DD>
  </DL>
  <DL>
  <DT><B>verify = "<TT>)_.verify</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verify' Line='verify = ")_.verify"'>
  <DD>Automatically confirm the critical parameters when running in non-interactive
  mode? Verify may be set to the apphot package parameter value (the default),
  "<TT>yes</TT>", or "<TT>no</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>update = "<TT>)_.update</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='update' Line='update = ")_.update"'>
  <DD>Automatically update the algorithm parameters in non-interactive mode if
  verify is "<TT>yes</TT>".  Update may be set to the apphot package parameter value
  (the default), "<TT>yes</TT>", or "<TT>no</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = "<TT>)_.verbose</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = ")_.verbose"'>
  <DD>Print out information about the progress of the task in non-interactive mode.
  Verbose may be set to the apphot package parameter value (the default), "<TT>yes</TT>",
  or "<TT>no</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>graphics = "<TT>)_.graphics</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = ")_.graphics"'>
  <DD>The standard graphics device. Graphics may be set to the apphot package
  parameter value (the default), "<TT>yes</TT>", or "<TT>no</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>display = "<TT>)_.display</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='display' Line='display = ")_.display"'>
  <DD>The standard image display device.  Display may be set to the apphot package
  parameter value (the default), "<TT>yes</TT>", or "<TT>no</TT>". By default graphics overlay is
  disabled.  Setting display to one of "<TT>imdr</TT>", "<TT>imdg</TT>", "<TT>imdb</TT>", or "<TT>imdy</TT>" enables
  graphics overlay with the IMD graphics kernel.  Setting display to "<TT>stdgraph</TT>"
  enables DAOFIND to work interactively from a contour plot.
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
  DAOFIND searches the IRAF images <I>image</I> for local density maxima,
  which have a full-width half-maximum of <I>datapars.fwhmpsf</I> and a peak
  amplitude greater than <I>findpars.threshold</I> * <I>datapars.sigma</I> above
  the local background, and writes a list of detected objects in the file
  <I>output</I>.  The detected objects are also listed on the standard output
  if the program is running in interactive mode, or in non-interactive mode
  with the <I>verbose</I> switch is turned on.
  <P>
  The coordinates written to <I>output</I> are in the coordinate
  system defined by <I>wcsout</I>. The options are "<TT>logical</TT>", "<TT>tv</TT>",
  and "<TT>physical</TT>". The simplest default is the "<TT>logical</TT>" system. Users
  wishing to correlate the output coordinates of objects measured in
  image sections or mosaic pieces with coordinates in the parent
  image must use the "<TT>tv</TT>" or "<TT>physical</TT>" coordinate systems.
  <P>
  If <I>cache</I> is yes and the host machine physical memory and working set size
  are large enough, the input and output image pixels are cached in memory. If
  cacheing is enabled and DAOFIND is run interactively the first measurement
  will appear to take a long time as the entire image must be read in before the
  measurement is actually made. All subsequent measurements will be very fast
  because DAOFIND is accessing memory not disk. The point of cacheing is to speed
  up random image access by making the internal image i/o buffers the same size
  as the image itself. However if the input object lists are sorted in row order
  and sparse cacheing may actually worsen not improve the execution time. Also at
  present there is no point in enabling cacheing for images that are less than
  or equal to 524288 bytes, i.e. the size of the test image dev$ypix, as the
  default image i/o buffer is exactly that size. However if the size of dev$ypix
  is doubled by converting it to a real image with the chpixtype task then the
  effect of cacheing in interactive is can be quite noticeable if measurements
  of objects in the top and bottom halfs of the image are alternated.
  <P>
  DAOFIND can be run either interactively or in batch mode by setting the
  parameter <I>interactive</I>. In interactive mode the user can examine,
  adjust, and save algorithm parameters, and fit or refit the  entire coordinate
  list with the chosen parameter set.  The <I>verify</I> parameter can be used
  to automatically enable confirmation of the critical parameters
  <I>datapars.fwhmpsf</I> and <I>datapars.sigma</I> when running in
  non-interactive mode.
  <P>
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Cursor commands</H3>
  <! BeginSection: 'CURSOR COMMANDS'>
  <UL>
  <P>
  <PRE>
  <P>
  	     Interactive Keystroke Commands
  <P>
  ?	Print help
  :	Colon commands 
  v	Verify the critical parameters
  w	Save the current parameters
  d	Plot radial profile of star near cursor
  i	Interactively set parameters using star near cursor
  f	Find stars in the image
  spbar	Find stars in the image, output results
  q	Exit task
  <P>
  <P>
  		Colon Commands
  <P>
  :show		[data/find]	List the parameters
  <P>
  		Colon Parameter Editing Commands
  <P>
  # Image and file name parameters
  <P>
  :image		[string]	Image name
  :output		[string]	Output file name
  <P>
  # Data dependent parameters
  <P>
  :scale		[value]		Image scale (units per pixel)
  :fwhmpsf	[value]		Full width half maximum of psf (scale units)
  :emission	[y/n]		Emission feature (y), absorption (n)
  :sigma		[value]		Standard deviation of sky (counts)
  :datamin	[value]		Minimum good data value (counts)
  :datamax	[value]		Maximum good data value (counts)
  <P>
  # Noise description parameters
  <P>
  :noise 		[string]	Noise model (constant|poisson)
  :gain		[string]	Gain image header keyword
  :ccdread	[string]	Readout noise image header keyword
  :epadu		[value]		Gain (electrons per adu)
  :readnoise	[value]		Readout noise (electrons)
  <P>
  # Observation parameters
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
  # Object detection parameters
  <P>
  :nsigma		[value]		Size of Gaussian kernel (sigma) 
  :threshold	[value]		Detection intensity threshold (counts)
  :ratio		[value]		Sigmay / sigmax of Gaussian kernel
  :theta		[value]		Position angle of Gaussian kernel
  :sharplo	[value]		Lower bound on sharpness
  :sharphi	[value]		Upper bound on sharpness
  :roundlo	[value]		Lower bound on roundness
  :roundhi	[value]		Upper bound on roundness
  <P>
  # Plotting and marking commands
  <P>
  :mkdetections	[y/n]		Mark detections on the image display
  <P>
  <P>
  The following commands are available inside the interactive setup menu.
  <P>
   
                      Interactive Daofind Setup Menu
  <P>
  	v	Mark and verify critical daofind parameters (f,s)
  <P>
  	f	Mark and verify the full-width half-maximum of the psf
  	s	Mark and verify the standard deviation of the background
  	l	Mark and verify the minimum good data value
  	u	Mark and verify the maximum good data value
  </PRE>
  <P>
  </UL>
  <! EndSection:   'CURSOR COMMANDS'>
  <H3>Algorithms</H3>
  <! BeginSection: 'ALGORITHMS'>
  <UL>
  <P>
  DAOFIND approximates the stellar point spread function with an elliptical
  Gaussian function, whose sigma along the semi-major axis is 0.42466 *
  <I>datapars.fwhmpsf</I> / <I>datapars.scale</I> pixels, semi-minor to semi-major
  axis ratio is <I>ratio</I>, and major axis position angle is <I>theta</I>.
  Using this model, a convolution kernel, truncated at <I>nsigma</I> sigma,
  and normalized so as to sum to zero, is constructed.
  <P>
  The density enhancement image <I>starmap</I> is computed by convolving the input
  image with the Gaussian kernel. This operation is mathematically equivalent to
  fitting, in the least-squares sense, the image data at each point with a
  truncated, lowered elliptical Gaussian function. After convolution each point
  in <I>starmap</I> contains as estimate of the amplitude of the best fitting
  Gaussian function at that point. Each point in <I>skymap</I>, if the user
  chooses to compute it, contains an estimate of the best fitting sky value
  at that point.
  <P>
  After image convolution , DAOFIND steps through <I>starmap</I> searching
  for density enhancements greater than <I>findpars.threshold</I> *
  <I>datapars.sigma</I>, and brighter than all other density enhancements within
  a semi-major axis of 0.42466 <I>findpars.nsigma</I> * <I>datapars.fwhmpsf</I>.
  As the program selects candidates, it computes three shape characteristics,
  sharpness and 2 estimates of roundness.  The sharpness statistic measures the
  ratio of, the difference between the height of the central pixel and the mean
  of the surrounding non-bad pixels, to the height of the best fitting Gaussian
  function at that point. The first roundness characteristic computes the ratio
  of a measure of the bilateral symmetry of the object to a measure of the
  four-fold symmetry of the object. The second roundness statistic measures the
  ratio of, the difference in the height of the best fitting Gaussian function
  in x minus the best fitting Gaussian function in y, over the average of the
  best fitting Gaussian functions in x and y. The limits on these parameters
  <I>findpars.sharplo</I>, <I>findpars.sharphi</I> <I>findpars.roundlo</I>, and
  <I>findpars.roundhi</I>, are set to weed out non-astronomical objects and
  brightness enhancements that are elongated in x and y respectively.
  <P>
  Lastly the x and y centroids of the detected objects are computed by estimating
  the x and y positions of the best fitting 1D Gaussian functions in x and y
  respectively, a rough magnitude is estimated by computing the ratio of the
  amplitude of the best fitting Gaussian at the object position to
  <I>findpars.threshold</I> * <I>datapars.sigma</I>, and the object is added to
  the output coordinate file.
  <P>
  </UL>
  <! EndSection:   'ALGORITHMS'>
  <H3>Output</H3>
  <! BeginSection: 'OUTPUT'>
  <UL>
  <P>
  In interactive mode or in non-interactive with the verbose switch turned on
  the following quantities are written to the terminal as each object is
  detected.
  <P>
  <PRE>
  	xcenter  ycenter  mag  sharpness  sround  ground id
  <P>
  		    where
  <P>
  	mag = -2.5 * log10 (peak density / detection threshold)
  </PRE>
  <P>
  The object centers are in pixels and the magnitude estimate measures the
  ratio of the maximum density enhancement to the detection threshold. 
  Sharpness is typically around .5 to .8 for a star with a fwhmpsf similar to
  the pattern star. Both sround and ground are close to zero for a truly 
  round star. Id is the sequence number of the star in the list.
  <P>
  In both interactive and batch mode the full output is written to the text
  file <I>output</I>. At the beginning of each file is a header, listing
  the current values of the parameters when the first stellar record was
  written. The parameters can subsequently be altered. 
  <P>
  </UL>
  <! EndSection:   'OUTPUT'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Run daofind interactively on dev$ypix using the image display
  and image display cursor. Set the fwhmpsf and sigma parameters
  with the graphics cursor,  radial profile plot, and the interactive
  setup key i.
  <P>
  <PRE>
  	ap&gt; display dev$ypix 1 fi+
  <P>
  	... display the image
  <P>
  	ap&gt; daofind dev$ypix interactive+
  <P>
  	... type ? to see help screen
  <P>
  	... move display cursor to a star
  	... type i to enter the interactive setup menu
  	... enter maximum radius in pixels of the radial profile or
              accept default with a CR
  	... set the fwhmpsf and sigma using the graphics cursor and the
  	    radial profile plot
  	... typing &lt;CR&gt; leaves the parameters at their default values
          ... type q to quit setup menu
  <P>
  	... type the v key to verify the critical parameters
  <P>
  	... type the w key to save the parameters in the parameter files
  <P>
  	... type the space bar to detect stars in the image
  <P>
  	... a 1 line summary of the answers will appear on the standard
  	    output for each star measured
  <P>
  	... type q to quit and q again to confirm the quit
  <P>
  	... full output will appear in the text file ypix.coo.1
  <P>
  </PRE>
  <P>
  2. Run daofind interactively on a single image using a contour plot in place
  of the image and the graphics cursor in place of the image cursor.
  This option is only useful for those (now very few) users who have access to
  a graphics terminal but not to an image display server. Set the fwhmpsf and
  sigma parameters with the graphics cursor and radial profile plot and the
  interactive setup key i.
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
  	ap&gt; daofind dev$ypix display=stdgraph interactive+
  <P>
          ... type ? to see the help screen
  <P>
  	... move graphics cursor to a setup star
  	... type i to enter the interactive setup menu
  	... enter maximum radius in pixels of the radial profile or
              accept the default with a CR
  	... set the fwhmpsf and sigma using the graphics cursor and the
  	    radial profile plot
  	... typing &lt;CR&gt; leaves the parameters at their default values
          ... type q to quit the setup menu
  <P>
  	... type the v key to confirm the critical parameters
  <P>
  	... type the w key to save the parameters in the parameter files
  <P>
          ... retype :.read ypix.plot1 to reload the contour plot
  <P>
  	... type the space bar to detect stars in the image
  <P>
  	... a 1 line summary of the answers will appear on the standard
  	    output for each star measured
  <P>
  	... full output will appear in the text file ypix.coo.2
  <P>
  	ap&gt; set stdimcur = &lt;default&gt;
  <P>
          ... reset the image cursor to its default value
  <P>
  </PRE>
  <P>
  <P>
  3. Run DAOFIND interactively without using the image display cursor.
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
  	ap&gt; display dev$ypix 1
  <P>
  	... display the image
  <P>
  	ap&gt; daofind dev$ypix interactive+
  <P>
          ... type ? for help
  <P>
  	... type "442 409 101 i" in response to the image cursor query where
  	    x and y are the coordinates of the star to be used as setup,
  	    101 is the default world coordinate system, and i enters the
  	    interactive setup menu.
  	... enter maximum radius in pixels of the radial profile or
              type CR to accept the default
  	... set the fwhmpsf and sigma using the graphics cursor and the
  	    radial profile plot
  	... typing &lt;CR&gt; leaves the parameters at their default values
          ... type q to quit the setup menu
  <P>
  	... type the v key to verify the parameters
  <P>
  	... type the w key to save the parameters in the parameter files
  <P>
  	... type the space bar to detect stars in the image
  <P>
  	... a 1 line summary of the answers will appear on the standard
  	    output for each star measured
  <P>
  	... type q to quit and q again to confirm
  <P>
  	... full output will appear in the text file ypix.coo.3
  <P>
  	ap&gt; set stdimcur = &lt;default&gt;
  <P>
          ... reset the image cursor to its default value
  </PRE>
  <P>
  <P>
  4. Run daofind on a list of 3 images contained in the file imlist in batch mode.
  The program will ask the user to verify that the fwhmpsf and the threshold are
  correct before beginning execution.
  <P>
  <PRE>
  	ap&gt; type imlist
  	dev$ypix
  	dev$wpix
  	dev$pix
  <P>
  	ap&gt; daofind @imlist
  <P>
          ... the output will appear in ypix.coo.4, wpix.coo.1, pix.coo.1
  </PRE>
  <P>
  <P>
  5. Display and find stars in an image section. Write the output coordinates
  in the coordinate system of the parent image. Mark the detected stars on
  the displayed image.
  <P>
  <PRE>
          ap&gt; display dev$ypix[150:450,150:450]
  <P>
          ... display the image section
  <P>
          ap&gt; daofind dev$ypix[150:450,150:450] wcsout=tv
  <P>
          ... output will appear in ypix.coo.5
  <P>
          ap&gt; tvmark 1 ypix.coo.5 col=204
  </PRE>
  <P>
  <P>
  6. Repeat example 4 but submit the job to the background  and turn off the
  verify switch.
  <P>
  <PRE>
  	ap&gt; daofind @imlist verify- &amp;
  <P>
  	... the output will appear in ypix.coo.6, wpix.coo.2, pix.coo.2
  </PRE>
  <P>
  <P>
  7. Use an image cursor command file to drive the daofind task. The cursor
  command file shown below sets the fwhmpsf, sigma, and threshold parameters,
  located stars in the image, updates the parameter files, and quits the task.
  <P>
  <PRE>
          ap&gt; type cmdfile
          : fwhmpsf 2.5
          : sigma 5.0
          : threshold 10.0
          \040
          w
          q
  <P>
          ap&gt; daofind dev$ypix icommands=cmdfile verify-
  <P>
          ... full output will appear in ypix.coo.7
  </PRE>
  <P>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  <P>
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
  blue or yellow overlays and set the findpars mkdetections switch to
  "<TT>yes</TT>". It may be necessary to run gflush and to redisplay the image
  to get the overlays position correctly.
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  datapars, findpars
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'CURSOR COMMANDS' 'ALGORITHMS' 'OUTPUT' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
