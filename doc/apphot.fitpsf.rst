fitpsf — Model the stellar psf with an analytic function
========================================================

**Package: apphot**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>fitpsf (May00)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.digiphot.apphot</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>fitpsf (May00)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>fitpsf</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  fitpsf -- model the point spread function with an analytic function
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  fitpsf image box
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
  <DT><B><A NAME="l_box">box    </A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='box' Line='box    '>
  <DD>The width of the fitting box in scale units.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_coords">coords = "<TT></TT>"</A></B></DT>
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
  <DT><B><A NAME="l_output">output = "<TT>default</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output = "default"'>
  <DD>The name of the results file or results directory. If output is
  "<TT>default</TT>", "<TT>dir$default</TT>", or a directory specification then an output file name
  of the form dir$root.extension.version is constructed, where dir is the
  directory, root is the root image name, extension is "<TT>psf</TT>" and version is
  the next available version number for the file. The number of output files
  must be zero, one, or equal to the number of image files.  In both interactive
  and batch mode full output is written to output. In interactive mode
  an output summary is also written to the standard output.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_datapars">datapars = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='datapars' Line='datapars = ""'>
  <DD>The name of the file containing the data dependent parameters.
  The critical parameters <I>fwhmpsf</I> and <I>sigma</I> are located in
  datapars.  If datapars is undefined then the default parameter set in
  uparm directory is used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_function">function = "<TT>radgauss</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='function' Line='function = "radgauss"'>
  <DD>The function to be fit. The options are:
  <DL>
  <DT><B><A NAME="l_radgauss">radgauss</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='radgauss' Line='radgauss'>
  <DD>A 2D radial Gaussian function is fit. The parameters of the fitting function
  are: x and y center, sigma of the Gaussian, amplitude of the Gaussian and
  the local sky value.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_elgauss">elgauss</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='elgauss' Line='elgauss'>
  <DD>A 2D elliptical Gaussian function is fit. The parameters of the fitting
  function are: x and y center, x and y sigma of the Gaussian, amplitude of
  the Gaussian and the local sky value.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_moments">moments</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='moments' Line='moments'>
  <DD>The 0th, 1st and 2nd order moments are computed and used to derive
  estimates of the
  x and y center values, radius of gyration, ellipticity and position
  angle of the object.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_maxiter">maxiter = 50</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maxiter' Line='maxiter = 50'>
  <DD>The maximum number of iterations that the non-linear fitting routines will
  perform in an attempt to find a satisfactory fit.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nreject">nreject = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nreject' Line='nreject = 0'>
  <DD>The maximum number of rejection cycles performed after the fit.
  The default is no rejection.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_kreject">kreject = 3.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='kreject' Line='kreject = 3.0'>
  <DD>The k-sigma rejection limit in units of sigma.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_mkbox">mkbox = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='mkbox' Line='mkbox = no'>
  <DD>Draw the fitting box on the image display?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interactive">interactive = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = yes'>
  <DD>Run the task interactively ?
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
  <DT><B><A NAME="l_verify">verify = </TT>")_.verify"<TT></A></B></DT>
  <! Sec='PARAMETERS' Level=-1 Label='verify' Line='verify = ")_.verify"'>
  <DD>Verify the critical parameters in non-interactive mode ? Verify may be set to
  the apphot package parameter value (the default), </TT>"yes"<TT>, or </TT>"no.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_update">update = "<TT>)_.update</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=-1 Label='update' Line='update = ")_.update"'>
  <DD>Update the critical parameters in non-interactive mode if verify is set of
  "<TT>yes</TT>" ? Update may be set to the apphot package parameter value (the default),
  "<TT>yes</TT>", or "<TT>no.
  <P>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = </TT>")_.verbose"<TT></A></B></DT>
  <! Sec='PARAMETERS' Level=-1 Label='verbose' Line='verbose = ")_.verbose"'>
  <DD>Print messages on the terminal in non-interactive mode ? Verbose may be set
  to the apphot package parameter value (the default), </TT>"yes"<TT>, or </TT>"no.
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
  <DD>The default display device.  Display may be set to the apphot package
  parameter value (the default), </TT>"yes"<TT>, or </TT>"no.  By default graphics overlay
  is disabled.  Setting display to one of "<TT>imdr</TT>", "<TT>imdg</TT>", "<TT>imdb</TT>", or "<TT>imdy</TT>"
  enables graphics overlay with the IMD graphics kernel.  Setting display to
  "<TT>stdgraph</TT>" enables FITPSF to work interactively from a contour plot.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  FITPSF models the stellar brightness distribution of objects in the IRAF image
  <I>image</I> using non-linear least squares techniques and writes the
  list of model parameters and associated errors to the file <I>output</I>.
  Initial coordinates for the objects are read from the image cursor or
  the text file <I>coords</I>.  Pixels in a subraster of width <I>box * scale</I>
  are extracted and used in the fit.
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
  is enabled and FITPSF is run interactively the first measurement will appear
  to take a long time as the entire image must be read in before the measurement
  is actually made. All subsequent measurements will be very fast because FITPSF
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
  FITPSF can be run either interactively or in batch mode by setting the
  parameter <I>interactive</I>. In interactive mode starting x and y positions
  can either be read directly from the image cursor or read from the text
  file specified by <I>coords</I>. In batch mode the estimated
  positions can be read from the text file <I>coords</I> or the image cursor
  parameter <I>icommands</I> can be redirected to a text file containing
  a list of cursor commands.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_cursor_commands">CURSOR COMMANDS</A></H2>
  <! BeginSection: 'CURSOR COMMANDS'>
  <UL>
  <P>
  The currently available cursor commands are listed below.
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
  f	Fit current star
  spbar	Fit current star, output results
  m	Move to next star in coordinate list
  n	Fit next star in coordinate list, output results
  l	Fit remaining stars in coordinate list, output results
  e	Print error messages
  r	Rewind the coordinate list
  q	Exit task 
  <P>
  <P>
  <P>
                   Colon Commands
  <P>
  :show	[data/fit]	List the parameters
  :m [n]	Move to next [nth] star in coordinate list
  :n [n]	Fit next [nth] star in coordinate list, output results
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
  :fwhmpsf	[value]		Scale factor (scale units)		
  :emission	[y/n]		Emission feature (y), absorption (n)
  :sigma		[value]		Standard deviation of sky (counts)
  :datamin	[value]		Minimum good data value (counts)
  :datamax	[value]		Maximum good data value (counts)
  <P>
  # Noise description parameters
  <P>
  :noise		[string]	Noise model (constant|poisson)
  :gain		[string]	Gain image header keyword
  :ccdread	[string]	Readout noise image header keyword
  :epadu		[value]		Gain (electrons  per adu)
  :readnoise	[value]		Readnoise (electrons)
  <P>
  # Observation parameters
  <P>
  :exposure	[string]	Exposure time image header keyword
  :airmass	[string]	Airmass image header keyword
  :filter		[string]	Filter image header keyword
  :obstime	[string]        Time of observation image header keyword
  :itime		[value]		Exposure time (time units)
  :xairmass	[value]		Airmass value (number)
  :ifilter	[string]	Filter id string
  :otime		[string]	Time of observation (time units)
  <P>
  # Fitting parameters
  <P>
  :function	[string]	PSF model (radgauss|elgauss|moments)
  :box		[value]		Width of the fitting box (scale units)
  :maxiter	[value]		Maximum number of iterations
  :nreject	[value]		Maximum number of rejection cycles
  :kreject	[value]		Rejection limit (sigma)
  <P>
  # Plotting and marking functions
  <P>
  :mkbox		[y/n]		Mark the fitting box on the display
  <P>
  <P>
  The following command are available from within the interactive setup menu.
  <P>
  <P>
                      Interactive Fitpsf Setup Menu
  <P>
  	v	Mark and verify the critical fitpsf parameters (f,s,b)
  <P>
  	f	Mark and verify the full-width half-maximum of the psf
  	s	Mark and verify the standard deviation of the background
  	l	Mark and verify the minimum good data value
  	u	Mark and verify the maximum good data value
  <P>
  	b	Mark and verify the half-width of the fitting box
  </PRE>
  <P>
  </UL>
  <! EndSection:   'CURSOR COMMANDS'>
  <H2><A NAME="s_algorithms">ALGORITHMS</A></H2>
  <! BeginSection: 'ALGORITHMS'>
  <UL>
  <P>
  The fitting parameters are <I>function</I>, the functional form of the model
  to be fit, <I>maxiter</I>, the maximum number of iterations per fit,
  <I>kreject</I>, the K-sigma rejection limit and <I>nreject</I>, the maximum
  number of rejection cycles. The currently available functions are a 2D
  moments analysis "<TT>moments</TT>", a 2D radial Gaussian "<TT>radgauss</TT>",  and a
  2D elliptical Gaussian "<TT>elgauss</TT>".
  <P>
  The weighting of the fit is determined by the parameter <I>noise</I> in the 
  <I>datapars</I> file. The two options are <I>constant</I>, in which all the
  weights are set to 1 and <I>poisson</I> in which the weights are equal to
  the inverse of the counts divided by the image gain read from the datapars
  <I>gain</I> or <I>epadu</I> parameters plus the square of the readout noise
  determined from the datapars parameters <I>ccdread</I> or <I>readnoise</I>.
  If <I>function</I> is either "<TT>radgauss</TT>" or "<TT>ellgauss</TT>" then the datapars
  parameter <I>fwhmpsf</I> is used to determine the initial guess for the
  Gaussian sigma.  The datapars parameter <I>threshold</I> determines the
  intensity threshold above which the moment analysis is performed.
  <P>
  </UL>
  <! EndSection:   'ALGORITHMS'>
  <H2><A NAME="s_output">OUTPUT</A></H2>
  <! BeginSection: 'OUTPUT'>
  <UL>
  <P>
  In interactive mode the following quantities are printed on the
  terminal as shown below, for the radial Gaussian, elliptical Gaussian and
  moments functions respectively.
  <P>
  <PRE>
      image  xcenter  ycenter  rsigma  amplitude  sky  err
  <P>
      image  xcenter  ycenter  xsigma  ysigma rot  amplitude  sky  err
  <P>
      image  xcenter  ycenter  rgyrat  ellip  pa amplitude  sky  err
  <P>
  </PRE>
  <P>
  In both interactive and batch mode the full output is written to the
  text file <I>output</I>. At the beginning of each file is a header
  listing the values of the parameters when the first stellar
  record was written. These parameters can be subsequently altered.
  For each star measured the following record is written for the radial
  Gaussian, elliptical Gaussian, and moments functions respectively.
  <P>
  <PRE>
          image  xinit  yinit  id  coords  lid
      	    xcenter  ycenter  rsigma  amplitude  sky
  	    excenter eycenter ersigma eamplitude esky  ier  error
  <P>
          image  xinit  yinit  id  coords  lid
      	    xcenter  ycenter  xsigma  ysigma  rot  amplitude  sky
  	    excenter eycenter exsigma eysigma erot eamplitude esky  ier\<BR>
  	    error
  <P>
          image  xinit  yinit  id  coords  lid
  	    xcenter  ycenter  rgyrat  ellip  pa amplitude  sky
  	    excenter eycenter ergyrat eellip epa eamplitude esky  ier\<BR>
  	    error
  </PRE>
  <P>
  Image and coords are the name of the image and coordinate files respectively.
  Id and lid are the sequence numbers of stars in the output and coordinate
  files respectively and xinit and yinit are the initial positions.
  Xcenter and ycenter are the computed x and y
  positions of the object. Rsigma, xsigma and ysigma are the distance from
  the center of the Gaussian at which the Gaussian is equal to exp (-0.5)
  of its central value. Xsigma and ysigma refer to those values along the major
  and minor axes of the ellipse respectively. The amplitude and sky refer to
  the amplitude of
  the Gaussian function and a constant background value respectively.
  If function = "<TT>moments</TT>" amplitude and sky refer to the total intensity
  above threshold and sky is the threshold value. Rot and pa are position angles
  of the major axis measured counter-clockwise with respect to the x axis.
  Rgyrat is the radius
  of gyration of the object and ellip its ellipticity.
  Quantities prefixed by an e represent the errors in the corresponding
  fitted parameters.
  <P>
  </UL>
  <! EndSection:   'OUTPUT'>
  <H2><A NAME="s_errors">ERRORS</A></H2>
  <! BeginSection: 'ERRORS'>
  <UL>
  <P>
  If all went well in the fitting process the error code stored in the ier
  field described above is 0. Non-zero values of ier flag the following error
  conditions.
  <P>
  <PRE>
            0     # No error
  	401     # The fitting box is off the image
  	402     # The fitting box is partially off the image
  	403     # There are too few points to fit the function
  	404     # The fit is singular
  	405     # The fit did not converge
  </PRE>
  <P>
  </UL>
  <! EndSection:   'ERRORS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Compute the radial Gaussian function parameters for a few  stars in dev$ypix
  using the display and the image cursor. Setup the task parameters using
  the interactive setup menu defined by the i key command. Use uniform
  weighting.
  <P>
  <PRE>
  	ap&gt; display dev$ypix 1 fi+
  <P>
  	... display the image
  <P>
  	ap&gt; fitpsf dev$ypix 11 noise=constant
  <P>
  	... type ? to see the help screen
  <P>
  	... move the image cursor to a star
  	... type i to enter the interactive setup menu
  	... enter maximum radius in pixels of the radial profile or type
  	    CR to accept the default value
  	... set the fitting box width, fwhmpsf, and sigma using the graphics
  	    cursor and the stellar radial profile plot
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
  	... type q to quit and another q to confirm the quit
  <P>
  	... the full output will appear in ypix.psf.1
  </PRE>
  <P>
  2. Compute the radial Gaussian function  parameters for a few  stars in 
  dev$ypix using the contour plot and the graphics cursor. Setup the task
  parameters using the interactive setup menu defined by the i key command.
  Use uniform weighting.
  <P>
  <PRE>
  	ap&gt; show stdimcur
  <P>
  	... save the current value of stdimcur
  <P>
  	ap&gt; set stdimcur = stdgraph
  <P>
  	... define the image cursor to be the graphics cursor
  <P>
  	ap&gt; contour dev$ypix &gt;G ypix.plot1
  <P>
  	... store the contour plot of dev$ypix in the file ypix.plot1
  <P>
  	ap&gt; fitpsf dev$ypix 11.0 noise=constant display=stdgraph
  <P>
  	... type ? to get a short help page on the screen
  <P>
  	... move the graphics cursor to a star
  	... type i to enter the interactive setup menu
  	... enter the maximum radius in pixels of the radial profile or
  	    type CR to accept the default value
  	... set the fitting box width, fwhmpsf, and sigma using the graphics
  	    cursor and the stellar radial profile plot
  	... typing &lt;CR&gt; leaves everything at the default value
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
  	... a one line summary of the fitted parameters will appear on the
  	    standard output for each star measured
  <P>
  	... type q to quit and q again to confirm the quit
  <P>
  	... full output will appear in the text file ypix.psf.2 
  </PRE>
  <P>
  <P>
  3. Setup and run FITPSF interactively on a list of objects temporarily
  overriding the fwhmpsf and sigma parameters determined in examples 1 or 2.
  Use uniform weighting.
  <P>
  <PRE>
          ap&gt; daofind dev$ypix fwhmpsf=2.6 sigma=25.0 verify-
  <P>
          ... make a coordinate list
  <P>
          ... the output will appear in the text file ypix.coo.1
  <P>
          ap&gt; fitpsf dev$ypix 11.0 fwhmpsf=2.6 noise=constant coords=ypix.coo.1
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
          ... the output will appear in ypix.psf.3 ...
  </PRE>
  <P>
  <P>
  4. Display and fit some stars in an image section and write the output
  coordinates in the coordinate system of the parent image. Use uniform 
  weighting.
  <P>
  <PRE>
          ap&gt; display dev$ypix[150:450,150:450] 1
  <P>
          ... display the image section
  <P>
          ap&gt; fitpsf dev$ypix[150:450,150:450] 11.0 noise=constant wcsout=tv
  <P>
          ... move cursor to stars and type spbar
  <P>
          ... type q to quit and q again to confirm quit
  <P>
          ... output will appear in ypix.psf.4
  <P>
          ap&gt; pdump ypix.psf.4 xc,yc yes | tvmark 1 STDIN col=204
  </PRE>
  <P>
  <P>
  5. Run FITPSF in batch mode using the coordinate file and the previously
  saved parameters. Use uniform weighting. Verify the critical parameters.
  <P>
  <PRE>
          ap&gt; fitpsf dev$ypix 11.0 coords=ypix.coo.1 noise=constant verify+ \<BR>
              inter-
  <P>
          ... output will appear in ypix.psf.5 ...
  </PRE>
  <P>
  6. Repeat example 5 but assume that the input coordinate are ra and dec
  in degrees and degrees, turn off verification, and submit the task to to
  the background. Use uniform weighting.
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
          ap&gt; fitpsf dev$ypix 11.0 coords=radec.coo noise=constant \<BR>
              wcsin=world verify- inter- &amp;
  <P>
          ... output will appear in ypix.psf.6
  <P>
          ap&gt; pdump ypix.psf.6 xc,yc yes | tvmark 1 STDIN col=204
  <P>
          ... mark the stars on the display
  </PRE>
  <P>
  7. Run FITPSF interactively without using the image display.
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
          ap&gt; fitpsf dev$ypix 11.0 coords=ypix.coo.1 noise=constant
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
          ... set the fwhmpsf, sigma, and fitting box size  using the
              graphics cursor and the stellar radial profile plot
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
          ... full output will appear in the text file ypix.psf.7
  <P>
          ap&gt; set stdimcur = &lt;default&gt;
  <P>
          ... reset the value of stdimcur
  </PRE>
  <P>
  8. Use an image cursor command file to drive the FITPSF task. The cursor command
  file shown below sets the fwhmpsf, sigma, and noise, computes the model
  fit parameter values for 3 stars, updates the parameter files, and quits
  the task.
  <P>
  <PRE>
          ap&gt; type cmdfile
          : fwhmpsf 2.6
          : sigma 5.0
          : noise constant
          442 410 101 \040
          349 188 101 \040
          225 131 101 \040
          w
          q
  <P>
          ap&gt; fitpsf dev$ypix 11.0 icommands=cmdfile verify-
  <P>
          ... full output will appear in ypix.psf.8
  </PRE>
  <P>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  <P>
  In interactive mode the user should not change the type function to be fit
  after the first record is written to the output file. In this case the file
  header and record structure will not match.
  <P>
  It is currently the responsibility of the user to make sure that the
  image displayed in the frame is the same as that specified by the image
  parameter.
  <P>
  Commands which draw to the image display are disabled by default.
  To enable graphics overlay on the image display, set the display
  parameter to "<TT>imdr</TT>", "<TT>imdg</TT>", "<TT>imdb</TT>", or "<TT>imdy</TT>" to get red, green,
  blue or yellow overlays and set the  mkbox switch to"<TT>yes</TT>".
  It may be necessary to run gflush and to redisplay the image
  to get the overlays position correctly.
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  <P>
  datapars, radprof
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'CURSOR COMMANDS' 'ALGORITHMS' 'OUTPUT' 'ERRORS' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>