imexamine — Examine images using image display, graphics, and text
==================================================================

**Package: tv**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>imexamine (Mar96)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>images.tv</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>imexamine (Mar96)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>imexamine</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  imexamine -- examine images using image display, plots, and text
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  imexamine [input [frame]]
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>Optional list of images to be examined.  If specified, images are examined
  in turn, displaying them automatically.  If no images are specified the
  images currently loaded into the image display are examined.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output = ""'>
  <DD>Rootname for output images created with the <TT>'t'</TT> key.  If no name is specified
  then the name of the input image is used.  A three digit number is appended
  to the rootname, such as "<TT>.001</TT>", starting with 1 until no image is found with
  that name.  Thus, successive output images with the same rootname will be
  numbered sequentially.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ncoutput">ncoutput = 101, nloutput = 101</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ncoutput' Line='ncoutput = 101, nloutput = 101'>
  <DD>Size of the output image created with the <TT>'t'</TT> key which is centered on the
  position of the cursor.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_frame">frame = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='frame' Line='frame = 1'>
  <DD>During program execution, a query parameter specifying the frame to be loaded.
  May also be specified on the command line when <I>imexamine</I> is used as a
  task to display a new image, to specify the frame to be loaded.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_image">image</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD>Query parameter for selecting images to be loaded.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_logfile">logfile = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logfile' Line='logfile = ""'>
  <DD>Logfile filename in which to record output of the commands producing text.
  If no filename is given then no logfile will be kept.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_keeplog">keeplog = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='keeplog' Line='keeplog = no'>
  <DD>Log output results initially?  Logging can be toggled interactively during
  program execution.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_defkey">defkey = "<TT>a</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='defkey' Line='defkey = "a"'>
  <DD>Default key for cursor x-y input list.  This key is applied to input
  cursor lists which do not have a cursor key specified.  It is used
  to repetitively apply a cursor command to a list of positions typically
  obtained from another task.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_autoredraw">autoredraw = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='autoredraw' Line='autoredraw = yes'>
  <DD>Automatically redraw graphs after a parameter change?  If no then graphs
  are only drawn when a graph or redraw command is given.
  If yes then colon commands which modify a parameter of the last graph
  will automatically redraw the graph.  A common example of this would
  be changing the graph limits.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_allframes">allframes = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='allframes' Line='allframes = yes'>
  <DD>Use all frames for displaying images?  If set, images from the input list
  are loaded cycling through the available frames.  If not set the last frame
  loaded is reused.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nframes">nframes = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nframes' Line='nframes = 0'>
  <DD>Number of display frames.  When automatically loading images from the input
  list only this number of frames will be used.  This should, of course,
  not exceed the number of frames provided by the display device.
  If the number of frames is set to 0 then the task will query the display
  device to determine how many frames are currently allocated.  New frames may
  be allocated during program execution by displaying images with the <TT>'d'</TT> key.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ncstat">ncstat = 5, nlstat = 5</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ncstat' Line='ncstat = 5, nlstat = 5'>
  <DD>The statistics command computes values from a box centered on the
  specified cursor position with the number of columns and lines
  given by these parameters.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_graphcur">graphcur = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphcur' Line='graphcur = ""'>
  <DD>Graphics cursor input.  If null the standard graphics cursor is used whenever
  graphics cursor input is requested.  A cursor file in the appropriate
  format may be substituted by specifying the name of the file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_imagecur">imagecur = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='imagecur' Line='imagecur = ""'>
  <DD>Image display cursor input.  If null the standard image display cursor is
  used whenever image cursor input is requested.  A cursor file in the
  appropriate format may be substituted by specifying the name of the file.
  Also the image cursor may be changed to query the graphics device or
  the terminal by setting the environment parameter "<TT>stdimcur</TT>"
  to "<TT>stdgraph</TT>" or "<TT>text</TT>" respectively.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_wcs">wcs = "<TT>logical</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wcs' Line='wcs = "logical"'>
  <DD>The world coordinate system (<I>wcs</I>) to be used for axis labeling when
  input is from images.
  The following standard world systems are predefined.
  <DL>
  <DT><B><A NAME="l_logical">logical</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='logical' Line='logical'>
  <DD>Logical coordinates are image pixel coordinates relative to the image currently
  being displayed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_physical">physical</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='physical' Line='physical'>
  <DD>The physical coordinate system is invariant with respect to linear
  transformations of the physical image matrix.  For example, if the reference
  image was created by extracting a section of another image, the physical
  coordinates of an object in the reference image will be the pixel coordinates
  of the same object in the original image.  The physical coordinate system
  thus provides a consistent coordinate system (a given object always has the
  same coordinates) for all images, regardless of whether any user world
  coordinate systems have been defined.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_world">world</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='world' Line='world'>
  <DD>The "<TT>world</TT>" coordinate system is the <I>current default WCS</I>.
  The default world system is the system named by the environment variable
  <I>defwcs</I> if defined in the user environment and present in the reference
  image WCS description, else it is the first user WCS defined for the image
  (if any), else physical coordinates are returned.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xformat">xformat = "<TT></TT>", yformat = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='xformat' Line='xformat = "", yformat = ""'>
  <DD>The numerical format for the world coordinate labels in the line and column
  plots and the format for printing world coordinates.  The values may be "<TT></TT>"
  (an empty string), %f for decimal format, %h and %H for xx:xx:xx format, and
  %m and %M for xx:xx.x format.  The upper case %H and %M convert degrees
  to hours.  Images sometimes include recommended coordinate formats as
  WCS attributes.  These are used if the format specified by these parameters
  is "<TT></TT>".  Any other value will override the image attribute.
  </DD>
  </DL>
  <P>
  In addition to these three reserved WCS names, the name of any user WCS
  defined for the reference image may be given.  A user world coordinate system
  may be any linear or nonlinear world system.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_graphics">graphics = "<TT>stdgraph</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = "stdgraph"'>
  <DD>Graphics output device.  Normally this is the standard graphics device
  specified by the environment variable "<TT>stdgraph</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_display">display = "<TT>display(image='$1',frame=$2)</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='display' Line='display = "display(image='$1',frame=$2)"'>
  <DD>Command template used to display an image.  The image to be displayed is
  substituted for argument $1 and the frame for argument $2.  Any display task
  may be used for image display by modifying this template.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_use_display">use_display = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='use_display' Line='use_display = yes'>
  <DD>Use the image display?  Set to no to disable all interaction with the
  display device, e.g., when working at a terminal that does not provide image
  display capabilities.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_additional_parameters">ADDITIONAL PARAMETERS</A></H2>
  <! BeginSection: 'ADDITIONAL PARAMETERS'>
  <UL>
  The various graphs and the aperture sum command have parameters defined in
  additional parameter sets.  The parameter sets are hidden tasks with
  the first character being the cursor command graph key that uses the
  parameters followed by "<TT>imexam</TT>".  The parameter sets are:
  <P>
  <PRE>
      cimexam    Parameters for column plots
      eimexam    Parameters for contour plots
      himexam    Parameters for histogram plots
      jimexam    Parameters for line 1D gaussian fit plots
      kimexam    Parameters for column 1D gaussian fit plots
      limexam    Parameters for line plots
      rimexam    Parameters for radial profile plots and aperture sums
      simexam    Parameters for surface plots
      vimexam    Parameters for vector plots (centered and endpoint)
  </PRE>
  <P>
  The same  parameters dealing with graph formats occur in many of the parameter
  sets while some are specific only to one parameter set.  In the
  summary below those common to more than one parameter set are shown
  only once.  The characters in parenthesis are the graph key prefixes
  for the parameter sets in which the parameter occurs.
  <P>
  <DL>
  <DT><B><A NAME="l_angh">angh = -33., angv = 25.		(s)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='angh' Line='angh = -33., angv = 25.		(s)'>
  <DD>Horizontal and vertical viewing angles (degrees) for surface plots.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_autoscale">autoscale = yes			(h)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='autoscale' Line='autoscale = yes			(h)'>
  <DD>In the case of integer data, automatically adjust <I>nbins</I> and
  <I>z2</I> to avoid aliasing effects.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_axes">axes = yes				(s)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='axes' Line='axes = yes				(s)'>
  <DD>Draw axes along edge of surface plots?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_background">background = yes			(jkr.)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='background' Line='background = yes			(jkr.)'>
  <DD>Fit and subtract a background for aperture sums, 1D gaussian fits, and
  radial profile plots?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_banner">banner = yes 			 (cehjklrsv.)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='banner' Line='banner = yes 			 (cehjklrsv.)'>
  <DD>Add a standard banner to a graph?  The standard banner includes the
  IRAF user and host identification and time, the image name and title,
  and graph specific parameters.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_beta">beta = INDEF			(ar.)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='beta' Line='beta = INDEF			(ar.)'>
  <DD>Beta value to use for Moffat profile fits.  If the value is INDEF
  the value will be determine as part of the fit otherwise the parameter
  will be fixed at the specified value.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_boundary">boundary = "<TT>constant</TT>"		(v)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='boundary' Line='boundary = "constant"		(v)'>
  <DD>Boundary extension for vector plots in which the averaging width might
  go outside of the image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_box">box = yes 				(cehjklrv.)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='box' Line='box = yes 				(cehjklrv.)'>
  <DD>Draw graph box and axes?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_buffer">buffer = 5.				(r.)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='buffer' Line='buffer = 5.				(r.)'>
  <DD>Buffer distance from object aperture of background annulus for aperture sums
  and radial profile plots.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ceiling">ceiling = INDEF			(es)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='ceiling' Line='ceiling = INDEF			(es)'>
  <DD>Ceiling data value for contour and surface plots.  A value of INDEF does
  not apply a ceiling.  (In contour plots a value of 0. also does not
  apply a ceiling.)
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_center">center = yes			(jkr.)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='center' Line='center = yes			(jkr.)'>
  <DD>Apply a centering algorithm for doing aperture sums, 1D gaussian fits,
  and radial profile plots?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_constant">constant = 0.			(v)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='constant' Line='constant = 0.			(v)'>
  <DD>Boundary extension constant for vector plots in which the averaging width
  might go outside of the image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_dashpat">dashpat = 528			(e)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='dashpat' Line='dashpat = 528			(e)'>
  <DD>Dash pattern for negative contours.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fill">fill = no				(e)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='fill' Line='fill = no				(e)'>
  <DD>Fill the output viewport regardless of the device aspect ratio?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fitplot">fitplot = yes			(r.)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='fitplot' Line='fitplot = yes			(r.)'>
  <DD>Overplot the profile fit on the radial profile data?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fittype">fittype = "<TT>moffat</TT>"			(ar.)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='fittype' Line='fittype = "moffat"			(ar.)'>
  <DD>Profile type to fit the radial profile data?  The choices are "<TT>gaussian</TT>"
  and "<TT>moffat</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_floor">floor = INDEF			(es)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='floor' Line='floor = INDEF			(es)'>
  <DD>Floor data value for contour and surface plots.  A value of INDEF does
  not apply a floor.  (In contour plots a value of 0. also does not
  apply a floor.)
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interval">interval = 0			(e)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='interval' Line='interval = 0			(e)'>
  <DD>Contour interval.  If 0, a contour interval is chosen which places 20 to 30
  contours spanning the intensity range of the image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_iterations">iterations = 3			(ar)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='iterations' Line='iterations = 3			(ar)'>
  <DD>Number of iterations to adjust the fitting radius.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_label">label= no				(e)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='label' Line='label= no				(e)'>
  <DD>Label the major contours in the contour plot?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_logx">logx = no, logy = no		(chjklrv.)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='logx' Line='logx = no, logy = no		(chjklrv.)'>
  <DD>Plot the x or y axis logarithmically?  The default for histogram plots is
  to plot the y axis logarithmically.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_magzero">magzero = 25.			(r.)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='magzero' Line='magzero = 25.			(r.)'>
  <DD>Magnitude zero point for aperture sums.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_majrx">majrx=5, minrx=5, majry=5, minry=5	(cehjklrv.)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='majrx' Line='majrx=5, minrx=5, majry=5, minry=5	(cehjklrv.)'>
  <DD>Maximum number of major tick marks on each axis and number of minor tick marks
  between major tick marks.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_marker">marker = "<TT>box</TT>"			(chjklrv.)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='marker' Line='marker = "box"			(chjklrv.)'>
  <DD>Marker to be drawn if <B>pointmode</B> = yes.  Markers are "<TT>point</TT>", "<TT>box</TT>", 
  "<TT>cross</TT>", "<TT>plus</TT>", "<TT>circle</TT>", "<TT>hebar</TT>", "<TT>vebar</TT>", "<TT>hline</TT>", "<TT>vline</TT>" or "<TT>diamond</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_naverage">naverage = 1			(cjklv)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='naverage' Line='naverage = 1			(cjklv)'>
  <DD>Number of lines, columns, or width perpendicular to a vector to be averaged.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nbins">nbins = 512				(h)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='nbins' Line='nbins = 512				(h)'>
  <DD>The number of bins in, or resolution of, histogram plots.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ncolumns">ncolumns = 21, nlines = 21		(ehs)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='ncolumns' Line='ncolumns = 21, nlines = 21		(ehs)'>
  <DD>Number of columns and lines used in contour, histogram, and surface plots.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ncontours">ncontours = 5			(e)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='ncontours' Line='ncontours = 5			(e)'>
  <DD>Number of contours to be drawn.  If 0, the contour interval may be specified,
  otherwise 20-30 nicely spaced contours are drawn.  A maximum of 40 contours
  can be drawn.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nhi">nhi = -1				(e)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='nhi' Line='nhi = -1				(e)'>
  <DD>If -1, highs and lows are not marked.  If 0, highs and lows are marked
  on the plot.  If 1, the intensity of each pixel is marked on the plot.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_pointmode">pointmode = no			(chlv)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='pointmode' Line='pointmode = no			(chlv)'>
  <DD>Plot points or marks instead of lines?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_pointmode">pointmode = yes			(jkr.)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='pointmode' Line='pointmode = yes			(jkr.)'>
  <DD>Plot points or marks instead of lines?  For radial profile plots point
  mode should always be yes.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_radius">radius = 5.				(r.)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='radius' Line='radius = 5.				(r.)'>
  <DD>Radius of aperture for aperture sums and centering.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_round">round = no				(cehjklrv.)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='round' Line='round = no				(cehjklrv.)'>
  <DD>Extend the axes up to "<TT>nice</TT>" values?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_rplot">rplot = 8.				(jkr.)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='rplot' Line='rplot = 8.				(jkr.)'>
  <DD>Radius to which the radial profile or 1D profile fits are plotted.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_sigma">sigma = 2.				(jk)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='sigma' Line='sigma = 2.				(jk)'>
  <DD>Initial guess for 1D gaussian fits.  The value is in pixels even if the fitting
  is done in world coordinates.  This must be close to the true value
  for convergence.  Also the four times the initial sigma is used to define
  the distance to the background region for the initial background estimate.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_szmarker">szmarker = 1			(chjklrv.)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='szmarker' Line='szmarker = 1			(chjklrv.)'>
  <DD>Size of mark (except for points).  A positive size less than 1 specifies
  a fraction of the device size.  Values of 1, 2, 3, and 4 signify
  default sizes of increasing size.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ticklabels">ticklabels = yes			(cehjklrv.)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='ticklabels' Line='ticklabels = yes			(cehjklrv.)'>
  <DD>Label the tick marks?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_title">title = "<TT></TT>"				(cehjklrsv.)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='title' Line='title = ""				(cehjklrsv.)'>
  <DD>User title.  This is independent of the standard banner title.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_top_closed">top_closed = no			(h)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='top_closed' Line='top_closed = no			(h)'>
  <DD>Include z2 in the top histogram bin?  Each bin of the histogram is a
  subinterval that is half open at the top.  <I>Top_closed</I> decides whether
  those pixels with values equal to z2 are to be counted in the histogram.  If
  <B>top_closed</B> is yes, the top bin will be larger than the other bins.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_width">width = 5.				(jkr.)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='width' Line='width = 5.				(jkr.)'>
  <DD>Width of background region for background subtraction in aperture sums,
  1D profile fits, and radial profile plots.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_wcs">wcs = "<TT>physical</TT>"</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='wcs' Line='wcs = "physical"'>
  <DD>World coordinate system for axis labeling and coordinate readback.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_x1">x1 = INDEF, x2 = INDEF, y1 = INDEF, y2 = INDEF	(chjklrv.)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='x1' Line='x1 = INDEF, x2 = INDEF, y1 = INDEF, y2 = INDEF	(chjklrv.)'>
  <DD>Range of graph along each axis.  If INDEF the range is determined from
  the data range plus a buffer.  The default y1 for histogram plots is 0.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xformat">xformat, yformat</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='xformat' Line='xformat, yformat'>
  <DD>Set world image coordinate formats.  Any format changes take effect on the next
  usage; i.e. there is no automatic redrawing.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xlabel">xlabel, ylabel			(cehjklrv.)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='xlabel' Line='xlabel, ylabel			(cehjklrv.)'>
  <DD>Axis labels.  Each graph type has an appropriate default.  If the label
  value is "<TT>wcslabel</TT>" then the coordinate label from the image WCS
  will be used if defined.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xorder">xorder = 0				(jk)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='xorder' Line='xorder = 0				(jk)'>
  <DD>Order for 1D gaussian background.  If 0 then a median is computed.  If
  1 then a constant background is fit simultaneously with the other gaussian
  parameters.  If 2 then a linear background is fit simultaneously with the
  other gaussian parameters.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xorder">xorder = 0, yorder = 0		(r.)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='xorder' Line='xorder = 0, yorder = 0		(r.)'>
  <DD>If either parameter is zero then the median value of the
  background annulus is used for background subtraction in aperture sums and
  radial profile plots.  Values greater than zero define polynomial
  surface orders for background subtraction.  The orders are actually the
  number of polynomial terms.  An order of 1 is a constant an order of 2
  is a plane.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_zero">zero = 0.				(e)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='zero' Line='zero = 0.				(e)'>
  <DD>Greyscale value of the zero contour, i.e., the value of a zero point shift
  to be applied to the image data before plotting.  Does not affect the values
  of the floor and ceiling parameters.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_z1">z1 = INDEF, z2 = INDEF		(h)</A></B></DT>
  <! Sec='ADDITIONAL PARAMETERS' Level=0 Label='z1' Line='z1 = INDEF, z2 = INDEF		(h)'>
  <DD>Range of pixel values to be used in histogram.  INDEF values default to
  the range in the region being histogramed.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'ADDITIONAL PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Images are examined using an image display, various types of plots, and
  text output.  Commands are given using the image display cursor and/or
  graphics cursor.  This task brings together many of the features of the
  IRAF image display and graphics facilities with some simple image
  analysis capabilities.
  <P>
  IMAGE DISPLAY
  <P>
  If <I>use_display</I> is yes the image display is used to examine images.
  When no input list is specified images may be loaded with the <TT>'d'</TT> key,
  frames selected with <TT>'n'</TT>, <TT>'p'</TT>, and "<TT>:select</TT>", and the scaled contents
  of the display frame buffer examined if the image itself is not available.
  <P>
  When an input list is specified the <TT>'n'</TT>, <TT>'p'</TT>, and "<TT>:select</TT>" allow
  moving about the list and new images may be added to the end of the
  list with <TT>'d'</TT>.  Images are automatically loaded as they are selected if
  not currently loaded.  Two parameters control how the frames are
  loaded.  The <I>nframes</I> parameter determines which frames are
  available.  Within the available frames images may be loaded by cycling
  through them if <I>allframes</I> is yes or in the last loaded frame
  (initially frame 1) if it is no.
  <P>
  When reading the image cursor the frame and the name of the image in
  the frame are determined.  Therefore images may also be selected
  by changing the frame externally or if the image cursor input is
  changed from the standard image display to text or file input.
  <P>
  The <TT>'d'</TT> command displays an image using the template CL command given
  by parameter <I>display</I>.  Usually this is the standard
  IRAF <B>tv.display</B> command though in some circumstances other commands
  like <B>plot.contour</B> may be used.  This command may be used to
  display an image even if <I>use_display</I> is no.
  <P>
  This task is generally intended for interactive use with an image
  display.  However it is possible to disable use of the image display
  and change the image cursor input to a graphics cursor, a file,
  or typed in by the user.  In this case an input image list is most
  appropriate but if one is missing, a query will be issued each time
  a command requiring an image is given.
  <P>
  CURSOR INPUT
  <P>
  Commands are given using cursor input.  Generally the image cursor is
  used to select points in the images to be examined and the key typed
  selects a particular operation.  In addition to the image cursor the
  graphics cursor is sometimes useful.  First, it gives access to the
  graphics cursor mode commands (see <B>cursors</B>) such as annotating,
  saving or printing a graph, expanding and roaming, and printing cursor
  positions.  Second, it can give a better perspective on the data for
  cursor positions than the image cursor.  And lastly, it may be needed
  when an image display is not available.  The commands <TT>'g'</TT> and <TT>'i'</TT>
  select between the graphics and image cursors.  Initially the image
  cursor is read.
  <P>
  Interpretation of the graph coordinate in terms of an image coordinate
  depends on the type of graph as described below.
  <P>
  <DL>
  <DT><B><A NAME="l_contour">contour plot</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='contour' Line='contour plot'>
  <DD>This gives image coordinates directly and both the x and y cursor values
  are used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_column">column plot</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='column' Line='column plot'>
  <DD>The x cursor position gives the line coordinate and the column coordinate
  used for the plot (that specified before averaging) gives the column
  coordinate.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_line">line plot</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='line' Line='line plot'>
  <DD>The x cursor position gives the column coordinate and the line coordinate
  used for the plot (that specified before averaging) gives the line
  coordinate.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_vector">vector plot</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='vector' Line='vector plot'>
  <DD>The x cursor position defines a column and line coordinate along the vector
  plotted.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_surface">surface plot</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='surface' Line='surface plot'>
  <DD>No cursor information is available in this plot and the cursor position
  used to make the surface plot (the center of the surface) is used again.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_histogram">histogram plot</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='histogram' Line='histogram plot'>
  <DD>No cursor information is available in this plot and the cursor position
  used to make the histogram (the center of the box) is used again.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_radial">radial profile plot</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='radial' Line='radial profile plot'>
  <DD>No cursor information is available in this plot and the cursor position
  used to define the center is used again.
  </DD>
  </DL>
  <P>
  There are some special features associated with cursor input in IRAF
  which might be useful in some circumstances.  The image display cursor
  can be reset to be a text cursor, graphics cursor, or image cursor by
  setting the environment variable "<TT>stdimcur</TT>" to "<TT>text</TT>", "<TT>stdgraph</TT>",
  or "<TT>stdimage</TT>" respectively.  Text cursor input consists of the x and
  y coordinates, a frame number, and the key or colon command.  Another
  form of text input is to set the value of the cursor input parameter
  to a file containing cursor commands.  There are two special features
  dealing with text cursor input.  If only x and y are entered the default
  key parameter <I>defkey</I> determines the command.  This is particularly
  useful if one has a list of pixel positions prepared by some other
  program.  The second feature is that for commands not requiring coordinates
  they may be left out and the command key or colon command entered.
  <P>
  TEXT OUTPUT
  <P>
  The following commands produce text output which may also be appended to
  a logfile.
  <P>
  <DL>
  <DT><B><A NAME="l_a">a, <TT>','</TT></A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='a' Line='a, ',''>
  <DD>Circular aperture photometry is performed at the position of the cursor.
  If the centering option is selected the cursor position is used as the
  initial point for computing the central moments of the marginal
  distributions in x and y.  The marginal distributions are obtained from a
  square aperture with edge dimensions of twice the aperture radius
  parameter.  Only the pixels above the mean are used in computing the
  central moments.  If the central moments are in a different pixel than that
  used for extracting the marginal distributions the computation is repeated
  using the new center.
  <P>
  The radius of the photometry and fitting aperture is specified by the
  <I>radius</I> parameter and the <I>iteration</I> parameter.  Iteration of the
  fitting radius and printing of the final radius is only done for the <TT>'a'</TT>
  key.  If the number of iterations is one then the radius is not adjusted.
  If it is greater than one then the direct FWHM (described) below is used to
  adjust the radius.  At each iteration the new radius is set to three times
  the direct FWHM (which is six times the radius at half-maximum).  The
  radius is printed as part of the output.
  <P>
  If the background subtraction option is selected a concentric circular
  annulus is defined.  The inner edge is separated from the object
  aperture by a specified buffer distance and the outer edge is defined
  by a width for the annulus.  The type of background used is determined
  by the parameters <I>xorder</I> and <I>yorder</I>.  If either parameter
  is zero then a median of the background annulus is determined.
  If 1 or greater a polynomial surface of the specified number of terms
  is fit.  Typically the orders are 1 for a constant or 2 for a plane.
  The median or fitted surface values within the object aperture are then
  subtracted.
  <P>
  The flux within the circular aperture is computed by simply summing the
  pixel values with centers within the specified radius of the center
  position.  No partial pixel adjustments are made.  If the flux is
  positive a magnitude is computed as
  <P>
  	magnitude = magzero - 2.5 * log10 (flux)
  <P>
  where the magnitude zero point is a user defined parameter.
  <P>
  In addition to the flux, the second intensity moments are used to compute
  an ellipticity and position angle.  The equations defining the moments and
  related parameters are:
  <P>
  <PRE>
  	Mxx = sum (x * x * I) / sum (I)
  	Myy = sum (y * y * I) / sum (I)
  	Mxy = sum (x * y * I) / sum (I)
  	e = sqrt ((Mxx - Myy) ** 2 + (2 * Mxy) ** 2) / (Mxx + Myy)
  	pa = 0.5 * atan (2 * Mxy / (Mxx - Myy))
  </PRE>
  <P>
  A nonlinear least squares profile of fixed center and zero background is
  fit to the radius and flux values of the background subtracted pixels to
  determine a peak intensity and FWHM.  The profile type is set by the
  <I>fittype</I> parameter.  The choices are "<TT>gaussian</TT>" and "<TT>moffat</TT>".  If the
  profile type is "<TT>moffat</TT>" there is an additional parameter "<TT>beta</TT>".  This
  value may be specified to fix it or given as INDEF to also be determined.
  The profile equations are:
  <P>
  <PRE>
  	I = Ic exp (-0.5 * (r / sigma)**2)	(fittype = "gaussian")
  	I = Ic (1 + (r / alpha)**2)**(-beta)	(fittype = "moffat")
  </PRE>
  <P>
  where Ic is the peak value, r is the radius, and the parameters are
  sigma, alpha, and beta.  The sigma and alpha values are converted to
  FWHM in the reported results.
  <P>
  Weights which are the inverse square of the pixel radius are used.  This
  has the effect of giving equal weight to all parts of the profile instead
  of being overwhelmed by the larger number of pixels are larger radii.  An
  additional weighting factor is used for pixels outside the half-maximum
  radius (as determined using the algorithm described below).  The weights
  are
  <P>
  <PRE>
  	wt = exp (-(r/rhalf - 1)**2)  for r/rhalf &gt; 1
  </PRE>
  <P>
  where rhalf is the radius at half-maximum.  This has the effect
  of reducing the contribution of the profile wings.
  <P>
  The above fit is done to the individual pixel values with a radius measured
  to the center of the pixel.  For the <TT>'a'</TT> key two additional measurements
  are made on a azimuthally averaged radial profile with a finer sampling of
  the radial bins.  This uses the same algorithms for centering, background
  estimation, and FWHM measurement as in the task <B>psfmeasure</B>.  The
  centering is essentially the same as described above but the background
  estimation is a mode of the sky annulus pixels.  Note that the centering
  and background subtraction are done for these measurements regardless of
  the the <I>center</I> and <I>background</I> parameters which apply only to
  the photometry and profile fitting to the individual pixel values.
  <P>
  To form the radially smoothed profile an image interpolator function is fit
  to the region containing the object.  The enclosed flux profile (total flux
  within a particular radius) is computed.  The sampling is done at a much
  finer resolution than individual pixels.  The subsampling scheme is that
  described in <B>psfmeasure</B> and is such that the center of the profile is
  more finely sampled than the edges of the profile.
  <P>
  Because the image interpolator function may not be very good for narrow
  profiles a second iteration is done if the radius enclosing half the flux
  is less than two pixels.  In this second iteration an analytic, radially
  symmetric Gaussian profile is subtracted from the image raster and the
  interpolation function is fit to the residuals.  Subpixel values are then
  computed by evaluating the analytic function plus the interpolated residual
  value.
  <P>
  There are two FWHM measurements computed using the enclosed flux
  radial profile.  One is to fit a Gaussian or Moffat profile to the
  enclosed flux profile.  The type is selected by the same <I>fittype</I>
  parameter used to select the profile to fit to the individual pixel
  values.  As with the direct fit the Moffat beta value may be fixed or
  included in the fit.  The FWHM of the fit is then printed on the
  status line, terminal output, and log file.
  <P>
  The other FWHM measurement directly measure the FWHM independent of a
  profile model.  The derivative of the enclosed flux profile is computed.
  This derivative is the azimuthally averaged radial profile with the radial
  bin sampling mentioned above.  The peak of this profile is found and the
  FWHM is twice the radius of the profile at half the peak value.  This
  "<TT>direct FWHM</TT>" is part of the output and is also used for the iterative
  adjustment of the fitting radius as noted above.
  <P>
  <DL>
  <DT><B><A NAME="l_a">a</A></B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='a' Line='a'>
  <DD>The output consists of the image line and column, the coordinates, the
  final radius used for the photometry and fitting, magnitude, flux, mean
  background, peak value of the profile fit, e, pa (in degrees between -90
  and +90 with 0 along the x axis), the Moffat beta value if a Moffat profile
  is fit, and three measures of the FWHM.  The coordinates are those
  specified by the <I>wcs</I> and formatted by the format parameters.  For the
  logical wcs the coordinates will be the same as the column and line
  values.  If a value is numerically undefined then INDEF is printed.  The
  FWHM values are, in order, the profile fit to the enclosed flux, the
  profile fit to the individual pixels, and the direct measurement from the
  derivative of the enclosed flux profile.  Note that except for the direct
  method, the other estimates are not really measurements of the FWHM but are
  quantities which give the correct FWHM for the specified profile type.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_"><TT>','</TT></A></B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='' Line='',''>
  <DD>The output consists of the image line and column, magnitude, flux, number
  of pixels within the aperture, mean background, r (moment FWHM), e, pa (in
  degrees between -90 and +90 with 0 along the x axis), and the peak value
  and FWHM of the profile fit.  The label GFWHM indicates a Gaussian fit
  while the label MFWHM indicates a Moffat profile fit.  If a quantity is
  numerically undefined then INDEF is printed.
  </DD>
  </DL>
  <P>
  This aperture photometry and FWHM tool is intended only for general image
  analysis and quick look measurements.  The background fitting, photometry,
  and FWHM techniques used are not intended for serious astronomical
  photometry; other packages, e.g., <I>noao.digiphot.apphot</I>, should be
  used if precise results are desired.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_b">b</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='b' Line='b'>
  <DD>The integer pixel coordinates defining a region of the image are printed.
  Two cursor positions are used to select the range of columns and lines.
  The output format consists of the starting and ending column
  coordinates and the starting and ending line coordinates.  This format is
  used as input by some tasks and can be used to generate image sections if
  desired.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_j">j, k</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='j' Line='j, k'>
  <DD>The fitted gaussian center, peak, sigma, full width at half maximum, and
  background at the center is computed and printed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_m">m</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='m' Line='m'>
  <DD>Statistics of a rectangular region centered on the cursor position are
  computed and printed.  The size of the statistics box is set by the
  parameters <I>ncstat</I> and <I>nlstat</I>.  The output format consists
  of the image section, the number of pixels, the mean, the median, the
  standard deviation, the minimum, and the maximum.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_x">x, y</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='x' Line='x, y'>
  <DD>The cursor x and y coordinates and the pixel value nearest this position
  are printed.  The <TT>'y'</TT> key may be used define a relative origin.  If
  an origin is defined (is not 0,0) then additional quantities are printed.
  These quantities are origin coordinates, the delta x and delta y distances,
  the radial distance, and the position angle (in degrees counterclockwise from
  the x axis).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_z">z</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='z' Line='z'>
  <DD>A 10x10 grid of pixel values is printed.  The integer coordinates are
  also printed around the grid.
  </DD>
  </DL>
  <P>
  GRAPHICS OUTPUT
  <P>
  The following commands produce graphics output to the specified graphics
  device (normally the graphics terminal).
  <P>
  <DL>
  <DT><B><A NAME="l_c">c</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='c' Line='c'>
  <DD>A plot of a column or average of columns is made with the line number as
  the ordinate and the pixel value as the abscissa.  The averaging number
  and various graph options are specified by the parameters from the
  <B>cimexam</B> parameter set.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_e">e</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='e' Line='e'>
  <DD>A contour plot of a region centered on the cursor is made.  The
  size of the region and various contouring and labeling options are
  specified by the parameters from the <B>eimexam</B> parameter set.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_h">h</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='h' Line='h'>
  <DD>A histogram of a region centered on the cursor is made.  The size
  of the region and various binning parameters are specified by
  the parameters from the <B>himexam</B> parameter set.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_l">l</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='l' Line='l'>
  <DD>A plot of a line or average of lines is made with the column number as
  the ordinate and the pixel value as the abscissa.  The averaging number
  and various graph options are specified by the parameters from the
  <B>limexam</B> parameter set.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_r">r, <TT>'.'</TT></A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='r' Line='r, '.''>
  <DD>A radial profile plot is made.  As with <TT>'a'</TT>/<TT>','</TT> there are options for centering
  and background subtraction.  There are also graphics option to set the
  radius to be plotted (<I>rplot</I>) and to overplot the profile fit
  (<I>fitplot</I>).  The measurement algorithms are those described for the
  <TT>'a'</TT>/<TT>','</TT> key and the output is the same except that there is no header line and
  the object center is given in the graph title rather than on the graphics
  status line.  The aperture sum and graph options are specified by the
  parameters from the <B>rimexam</B> parameter set.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_s">s</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='s' Line='s'>
  <DD>A surface plot of a region centered on the cursor is made.  The size
  of the region and various surface and labeling options are
  specified by the parameters from the <B>simexam</B> parameter set.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_u">u, v</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='u' Line='u, v'>
  <DD>A plot of a vector defined by two cursor positions is made.  The <TT>'u'</TT>
  plot uses the first cursor position to define the center of the vector
  and the second position to define the endpoint.  The vector is extended
  an equal distance in the opposite direction and the graph x coordinates
  are the radial distance from the center position.  The <TT>'v'</TT> plot
  uses the two cursor positions as endpoints and the coordinates are
  the radial distance from the first cursor position.  The vector may
  be averaged over a specified number of parallel vectors.  The
  averaging number and various graph options are specified by the parameters
  from the <B>vimexam</B> parameter set.
  </DD>
  </DL>
  <P>
  <P>
  MISCELLANEOUS COMMANDS
  <P>
  The following commands control useful features of the task.
  <P>
  <DL>
  <DT><B><A NAME="l_d">d</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='d' Line='d'>
  <DD>The display command given by the parameter <I>display</I> is given
  with appropriate image name.  By default this loads the image
  display using the <B>tv.display</B> task.  When using an input image
  list this operation also appends new images to the list for subsequent
  <TT>'n'</TT> and <TT>'p'</TT> commands.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_f">f</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='f' Line='f'>
  <DD>Redraw the last graph.  If the <I>autoredraw</I> parameter is no then
  this is used to redraw a graph after making parameter changes with
  colon commands.  If the parameter is yes then any colon command which
  affects the current plot will execute a redraw automatically.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_g">g, i</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='g' Line='g, i'>
  <DD>Cursor input may be selected to be from the graphics cursor (g) or
  image display cursor (i).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_n">n, p</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='n' Line='n, p'>
  <DD>Go to the next or previous image in the image list or display frames.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_o">o</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='o' Line='o'>
  <DD>Overplot the next graph.  This generally only makes sense with the
  line, column, and histogram plots.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_q">q</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='q' Line='q'>
  <DD>Quit the task.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_t">t</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='t' Line='t'>
  <DD>Output an image centered on the cursor position with name and size set
  by the <I>output</I>, <I>ncoutput</I> and <I>nloutput</I> parameters.
  Note that the cursor input might be from a contour, surface, or other
  plot as well as from the image display.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_w">w</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='w' Line='w'>
  <DD>Toggle output to the logfile.  If no logfile is specified this has no
  effect except to print a message.  If the logfile is specified a message
  is printed indicating that the logfile has been opened or closed.
  Every time the logfile is opened the current image name and title is
  entered as well as when the image is changed.  The logfile name may
  be set or changed by a colon command.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">:select</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line=':select'>
  <DD>Select an image.  If an input image list is used the specified index
  number selects an image from the list.  If an input image list is not
  used and the image display is used then the specified display frame
  is selected.  If the new image is different from the previous image
  an identification line is inserted in the logfile if it is open.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">:eparam, :unlearn</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line=':eparam, :unlearn'>
  <DD>These colon commands manipulate the various parameter sets as
  described below.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">:c&lt;#&gt;, :l&lt;#&gt;</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line=':c&lt;#&gt;, :l&lt;#&gt;'>
  <DD>Special colon commands to plot specific columns or lines, symbolically
  shown as &lt;#&gt;, rather than use a cursor position.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">:&lt;column&gt; &lt;line&gt; &lt;key&gt;</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line=':&lt;column&gt; &lt;line&gt; &lt;key&gt;'>
  <DD>Special colon command syntax to explicitly give image coordinates for
  a cursor command key.
  </DD>
  </DL>
  <P>
  COLON COMMANDS
  <P>
  Sometimes one wants to explicitly enter the coordinates for a command.
  This may be done with a colon command having the following syntax:
  <P>
  	:&lt;column&gt; &lt;line&gt; &lt;key&gt;
  <P>
  where column and line are the coordinates and key is the command.
  If the line is not given then &lt;column&gt; = &lt;line&gt;.  For the frequently
  used line and column plots there is also the simple syntax:
  <P>
  <PRE>
  	:c&lt;column&gt; 	or	:l&lt;line&gt;
  </PRE>
  <P>
  with no space, e.g., "<TT>:l64</TT>".
  <P>
  Every parameter except the input image list and the display command
  may be queried or set by a
  colon command.  In addition the parameter sets for the various graphs
  and aperture sum algorithm may be edited using the <B>eparam</B> editor
  and reinitialized to default values using the <B>unlearn</B> command.
  There are a large number of parameters as well as many graph types /
  parameter sets.  To achieve some consistency and order as well as
  simplify the colon commands several things have been done.
  <P>
  Many parameters occur in more than one graph type.  This includes things
  like graph labeling, tickmarks, and so forth.  When issuing a colon
  command for one of these parameters the current graph type is assumed
  to be the one affected.  If the graph type is wrong or no graph has
  been made then a warning is given.
  <P>
  If the parameter only occurs in one parameter set then the colon command
  may be used with any current graph.  However, if the parameter affects the
  current graph and the automatic redraw option is set then the graph will
  be redrawn.
  <P>
  The eparam and unlearn commands also apply by default to the parameters
  for the current graph.  However, they may take the keystroke character
  for the graph as an argument to override this.  If the current graph
  parameters are changed and the automatic redraw option is set then
  the graph will be redrawn.
  <P>
  The important colon commands <TT>'x'</TT> and <TT>'y'</TT> affect the x1, y1, x2, y2
  parameters in most of the graphs.  They are frequently used to override
  the automatic graph scaling.  If no arguments are given the window
  limits are set to INDEF resulting in plotting the full range of the
  data plus a buffer.  If two values are given then only that range of
  the data will be plotted.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_commands">COMMANDS</A></H2>
  <! BeginSection: 'COMMANDS'>
  <UL>
  <P>
  <CENTER>Cursor Keys
  
  </CENTER><BR>
  <P>
  <PRE>
  ?	Print help
  a	Aperture sum, moment parameters, and profile fit
  b	Box coordinates for two cursor positions - c1 c2 l1 l2
  c	Column plot
  d	Load the image display
  e	Contour plot
  f	Redraw the last graph
  g	Graphics cursor
  h	Histogram plot
  i	Image cursor
  j	Fit 1D gaussian to image lines
  k	Fit 1D gaussian to image columns
  l	Line plot
  m	Statistics
  	    image[section] npixels mean median stddev min max
  n	Next frame or image
  o	Overplot
  p	Previous frame or image
  q	Quit
  r	Radial profile plot with fit and aperture sum values
  s	Surface plot
  t	Output image centered on cursor (parameters output, ncoutput, nloutput)
  u	Centered vector plot from two cursor positions
  v	Vector plot between two cursor positions
  w	Toggle write to logfile
  x	Print coordinates
  	    col line pixval [xorign yorigin dx dy r theta]
  y	Set origin for relative positions
  z	Print grid of pixel values - 10 x 10 grid
  ,	Quick Gaussian/Moffat photometry
  </PRE>
  <P>
  <CENTER>Colon Commands
  
  </CENTER><BR>
  <P>
  Explicit image coordinates may be entered using the colon command syntax:
  <P>
  	:&lt;column&gt; &lt;line&gt; &lt;key&gt;
  <P>
  where column and line are the image coordinates and the key is one
  of the cursor keys.  A special syntax for line or column plots is also
  available as :c# or :l# where # is a column or line and no space is
  allowed.
  <P>
  Other colon commands set or show parameters governing the plots and other
  features of the task.  Each graph type has it's own set of parameters.
  When a parameter applies to more than one graph the current graph is assumed.
  If the current graph is not applicable then a warning is given.  The
  "<TT>eparam</TT>" and "<TT>unlearn</TT>" commands may be used to change many parameters and
  without an argument the current graph parameters are modified while with
  the graph key as an argument the appropriate parameter set is modified.
  In the list below the graph key(s) to which a parameter applies are shown.
  <P>
  <PRE>
  allframes               Cycle through all display frames to display images
  angh        s           Horizontal angle for surface plot
  angv        s           Vertical angle for surface plot
  autoredraw  cehlrsuv    Automatically redraw graph after colon command?
  autoscale   h           Adjust number of histogram bins to avoid aliasing
  axes        s           Draw axes in surface plot?
  background  jkr         Subtract background for radial plot and photometry?
  banner      cehjklrsuv  Include standard banner on plots?
  beta        ar		Moffat beta parameter (INDEF to fit or value to fix)
  boundary    uv          Boundary extension type for vector plots
  box         cehjklruv   Draw box around graph?
  buffer      r           Buffer distance for background subtraction
  ceiling     es          Data ceiling for contour and surface plots
  center      jkr         Find center for radial plot and photometry?
  constant    uv          Constant value for boundary extension in vector plots
  dashpat     e           Dash pattern for contour plot
  eparam      cehjklrsuv  Edit parameters
  fill        e           Fill viewport vs enforce unity aspect ratio?
  fitplot     r           Overplot profile fit on data?
  fittype     ar          Profile fitting type (gaussian|moffat)
  floor       es          Data floor for contour and surface plots
  interval    e           Contour interval (0 for default)
  iterations  ar          Iterations on fitting radius
  label       e           Draw axis labels for contour plot?
  logfile                 Log file name
  logx        chjklruv    Plot x axis logarithmically?
  logy        chjklruv    Plot y axis logarithmically?
  magzero     r           Magnitude zero for photometry
  majrx       cehjklruv   Number of major tick marks on x axis
  majry       cehjklruv   Number of major tick marks on y axis
  marker      chjklruv    Marker type for graph
  minrx       cehjklruv   Number of minor tick marks on x axis
  minry       cehjklruv   Number of minor tick marks on y axis
  naverage    cjkluv      Number of columns, lines, vectors to average
  nbins       h           Number of histogram bins
  ncolumns    ehs         Number of columns in contour, histogram, or surface plot
  ncontours   e           Number of contours (0 for default)
  ncoutput                Number of columns in output image
  ncstat                  Number of columns in statistics box
  nhi         e           hi/low marking option for contours
  nlines      ehs         Number of lines in contour, histogram, or surface plot
  nloutput                Number of lines in output image
  nlstat                  Number of lines in statistics box
  output			Output image root name
  pointmode   chjkluv     Plot points instead of lines?
  radius      r           Radius of object aperture for radial plot and photometry
  round       cehjklruv   Round axes to nice values?
  rplot       jkr         Radius to plot in 1D and radial profile plots
  select                  Select image or display frame
  sigma       jk          Initial sigma for 1D gaussian fits
  szmarker    chjklruv    Size of marks for point mode
  ticklabels  cehjklruv   Label ticks?
  title       cehjklrsuv  Optional title for graph
  top_closed  h           Close last bin of histogram
  unlearn     cehjklrsuv  Unlearn parameters to default values
  wcs                     World coordinate system for axis labels and readback
  width       jkr         Width of background region
  x [min max] chjklruv    Range of x to be plotted (no values for autoscaling)
  xformat			Coordinate format for column world coordinates
  xlabel      cehjklrsuv  Optional label for x axis
  xorder      jkr         X order of surface for background subtraction
  y [min max] chjklruv    Range of y to be plotted (no values for autoscaling)
  yformat			Coordinate format for line world coordinates
  ylabel      cehjklrsuv  Optional label for y axis
  yorder      r           Y order of surface for background subtraction
  z1          h           Lower intensity value limit of histogram
  z2          h           Upper intensity value limit of histogram
  zero        e           Zero level for contour plot
  </PRE>
  </UL>
  <! EndSection:   'COMMANDS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  The following  example illustrates many of the features in a descriptive
  way using the standard image dev$pix.
  <P>
  <PRE>
    cl&gt; imexam dev$pix nframes=2
    [The image is loaded in the display if not already loaded]
    &lt;Image cursor&gt; l          # Make a line plot
    &lt;Image cursor&gt; e          # Make a contour plot
    &lt;image cursor&gt; d          # Load a new image
    image name: saga
    display frame (1:) (1): 2
    &lt;Image cursor&gt; e          # Make a contour plot
    &lt;Image cursor&gt; g          # Switch to graphics cursor
    &lt;Graph cursor&gt; u          # Mark the center of a vector
    &lt;Graph cursor&gt; u          # Mark endpoint make a vector plot
    &lt;Graph cursor&gt; i          # Go back to display
    &lt;Image cursor&gt; r          # Select star and make radial plot
    &lt;Image cursor&gt; :rplot 10  # Set radius of plot
    &lt;Image cursor&gt; :epar      # Set radius plot parameters
    &lt;Image cursor&gt; c          # Make column plot
    &lt;Image cursor&gt; :100 l     # Line 100 of image 1
    &lt;Image cursor&gt; :20 30 e   # Contour plot at (20,30)
    &lt;Image cursor&gt; p          # Go to previous image
    &lt;Image cursor&gt; n          # Go to next image
    &lt;Image cursor&gt; :sel 1     # Select image 1
    &lt;Image cursor&gt; :log log   # Set log file
    &lt;Image cursor&gt; w          # Begin logging
    Log file log is open
    &lt;Image cursor&gt; a          # Do aperture sum on star 1
    &lt;Image cursor&gt; a          # Do aperture sum on star 2
    &lt;Image cursor&gt; a          # Do aperture sum on star 3
    &lt;Image cursor&gt; a          # Do aperture sum on star 4
    &lt;Image cursor&gt; w          # Close log file
    Log file log is closed
    &lt;Image cursor&gt; y          # Mark position of galaxy center
    &lt;Image cursor&gt; x          # Print position relative to center
    &lt;Image cursor&gt; x          # Print position relative to center
    &lt;Image cursor&gt; s          # Make surface plot
    &lt;Image cursor&gt; q          # Quit
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  If an operation is interrupted, e.g., an image display or surface plot,
  <I>imexamine</I> is terminated rather than the operation in progress.
  <P>
  When used on a workstation <I>imexamine</I> attempts to always position the
  cursor to the window (text, image, or graphics) from which input is being
  taken.  Moving the mouse manually while the program is also trying to move
  it can cause the mouse to be positioned to the wrong window, requiring that
  it be manually moved to the window from which input is currently being taken.
  <P>
  When entering a colon command in image cursor mode, if one types too fast
  the characters typed before the mouse is moved to the input window
  will be lost.  To avoid this, pause a moment after typing the colon, before
  entering the command, and verify that the mouse has been moved to the correct
  window.  In the future colon command input will be entered without moving
  the mouse out of the image window, which will avoid the problem.
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_revisions">REVISIONS</A></H2>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_IMEXAMINE">IMEXAMINE V2.11.4</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='IMEXAMINE' Line='IMEXAMINE V2.11.4'>
  <DD>(<TT>'t'</TT>): A new cursor key to create an output image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_IMEXAMINE">IMEXAMINE V2.11</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='IMEXAMINE' Line='IMEXAMINE V2.11'>
  <DD>(<TT>'a'</TT> and <TT>'r'</TT>): The fit to the radial profile points now includes both a
  Gaussian and a Moffat profile.  The Moffat profile exponent parameter,
  beta, may be fixed or left free to be fit.
  <P>
  (<TT>'a'</TT> and <TT>'r'</TT>): New estimates of the FWHM were added to the <TT>'a'</TT> and <TT>'r'</TT>
  keys.  These include the Moffat profile fit noted above, a direct
  measurement of the FWHM from the radially binned profile, and a Gaussian or
  Moffat fit to the radial enclosed flux profile.  The output from these keys
  was modified to include the new information.
  <P>
  (<TT>'a'</TT> and <TT>'r'</TT>): The direct FWHM may be used to iteratively adjust the
  fitting radius to lessen the dependence on the initial fitting
  radius value.
  <P>
  (<TT>','</TT> and <TT>'.'</TT>): New keys to do the Gaussian or Moffat fitting without
  iteration or the enclosed flux and direct measurements.  The output
  format is the same as the previous version.
  <P>
  (<TT>'k'</TT>): Added a kimexam parameter set.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  cursors, eparam, unlearn, plot.*, tvmark, digiphot.*, apphot.*,
  implot, splot, imedit, radplt, imcntr, imhistogram, imstatistics, display
  psfmeasure.
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'ADDITIONAL PARAMETERS' 'DESCRIPTION' 'COMMANDS' 'EXAMPLES' 'BUGS' 'REVISIONS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>