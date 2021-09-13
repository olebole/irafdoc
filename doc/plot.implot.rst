implot — Plot lines and columns of images using cursors
=======================================================

**Package: plot**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>implot (Feb94)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>plot</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>implot (Feb94)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>implot</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  implot -- plot lines and columns of images
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  implot image [line]
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_image">image</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD>List of images to be plotted.  If more than one image is in the list then
  the <TT>'m'</TT> and <TT>'n'</TT> keys are used proceed to the previous and next image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_line">line</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='line' Line='line'>
  <DD>If given, the number of the image line to be plotted, otherwise the central
  line is plotted.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_wcs">wcs = "<TT>logical</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wcs' Line='wcs = "logical"'>
  <DD>The world coordinate system (<I>wcs</I>) to be used for axis labeling.
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
  <P>
  In addition to these three reserved WCS names, the name of any user WCS
  defined for the reference image may be given.  A user world coordinate system
  may be any linear or nonlinear world system.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_step">step = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='step' Line='step = 0'>
  <DD>Step size for stepping through lines or columns in an image with the
  <TT>'j'</TT> and <TT>'k'</TT> keys.  If zero or INDEF the step defaults to ~10% of the
  image axis length.  This parameter may be changed interactively with
  a colon command.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Implot is an interactive, cursor driven task for examining images by plotting
  the lines and columns or the averages of lines and columns.  An image
  line is plotted when the task is first run, then cursor mode is entered and
  keystrokes may be used to generate additional line and column plots.  <TT>'q'</TT>
  is typed to exit cursor mode and implot and <TT>'n'</TT> is typed to proceed to
  the next image in the input image list.
  <P>
  The following single character keystrokes are recognized by Implot.  Note that
  numerous additional keystrokes are provided by "<TT>cursor mode</TT>" itself, i.e.,
  by the graphics system.  These additional keystrokes provide such standard
  facilities as stepwise cursor motion, plot expansion, movies, disposal to a
  batch plotter or metafile, and plot annotation facilities.  Cursor mode is
  documented elsewhere.
  <P>
  <P>
  <PRE>
  <PRE>
  	?		print help and other info
  	a		plot the average of a range of lines or columns
  	c		plot a column
  	e		expand plot by marking corners of viewport
  	j		move down within image (moving section)
  	k		move up within image (moving section)
  	l		plot a line
  	m		proceed to the previous image in the list
  	n		proceed to the next image in the list
  	o		overplot next vector
  	p		measure profile (mark region and bkg with 2 pos)
  	q		quit
  	s		print statistics on a region
  	w		change world coordinate system
  	/		scroll status line
  	&lt;space&gt;		print coordinates and pixel value
  </PRE>
  </PRE>
  <P>
  <P>
  The single character keystroke commands use the position to the cursor to
  determine what region of the image to plot.  If the plot is examined carefully
  one will note an extra scale on the right hand edge.  This scale gives the
  "<TT>other</TT>" axis of the image in units of pixels.  For example, if the current
  plot is a line plot (rather than a column plot), the X axis of the plot
  will correspond to the X axis of the image, and the right Y axis of the plot
  will correspond to the Y axis of the image.  Both axes will be scaled
  linearly in units of pixels.  The left Y axis is scaled in either linear or
  logarithmic pixel intensity units.  In the case of a column plot the bottom
  axis will correspond to image Y and the right axis to image X.
  <P>
  The <TT>'l'</TT> and <TT>'c'</TT> keystrokes, used to plot lines and columns, take image
  coordinates from the bottom and right axes of the plot.  In the case of a
  lineplot, the cursor would be positioned in Y and the key <TT>'l'</TT> typed to
  plot a new line.  Extrapolation of this convention to the other cases and
  keystrokes is self evident.  The <TT>'a'</TT> keystroke is used to mark an X or Y
  region to be averaged and plotted.  This mode of averaging is independent
  of the ':a' command discussed below.
  <P>
  Successive vectors may be overplotted by typing an <TT>'o'</TT> and then any other
  command.  A range of linetypes are used if the device supports them to
  make the curves easier to distinguish.  The position of each line is marked
  on the right axis with a small tick to document the coordinates of the
  curves.
  <P>
  The <TT>'j'</TT> and <TT>'k'</TT> commands are used to step through an image in either the
  upward (k) or downward (j) directions, relative to the current line or
  column plot.  Each new vector is plotted in place of the previous one
  without clearing the screen, making it easy to compare successive vectors.
  The step between vectors may be defined by a task parameter and
  changed by a colon command.
  <P>
  The <TT>'m'</TT> and <TT>'n'</TT> commands are used to step through the input image list.
  This is the same as using the <TT>'i'</TT> key to switch images and the <TT>'l'</TT> key
  to plot the same line or column as the previous image.
  <P>
  There are three keys which print various quantities of interest.
  The space bar key will read the cursor position, find the nearest pixel,
  and report the image line and column, the coordinate along the current
  axis, and the pixel value.  The line and column are in logical pixels
  (that is the coordinates in the current image section) and the
  coordinates are in the selected world coordinate system and printed
  in the current coordinate format.  If the selected world coordinate
  system is "<TT>logical</TT>" then the coordinate will be the same as the line
  or column.
  <P>
  The <TT>'s'</TT> key requires two cursor positions and then computes statistics of
  the region.  The values are the median, mean, sigma, sum, and number of
  pixels.  The <TT>'p'</TT> key also requires two cursor positions with the x
  positions defining a region and the y positions defining a linear
  background.  Within the defined region the peak departure from the
  background (either above or below the background) is found and the full
  width at half maximum of this peak is measured.  The linear background, the
  peak position and distance from the background and the widths at half the
  peak value are overplotted on the data.  In addition to the profile
  quantities the moments of the background subtracted data are measured.  The
  moments computed are the centroid, the integral (or flux), the width, and
  the normalized asymmetry.  The width reported is the square root of the
  second central moment multiplied by 2.35482.  For a gaussian profile this
  corresponds to the full width at half maximum which can be compared with
  the direct measure of the profile width.  The normalized asymmetry is the
  third central moment divided by the 3/2 power of the second central
  moment.  The various measurements are printed on the status line.  There
  are multiple lines of results which are scrolled using the <TT>'/'</TT> key.
  <P>
  In addition to the single keystroke commands, the following : escape
  commands are provided:
  <P>
  <P>
  <PRE>
  <PRE>
  	:a N		set number of lines or columns to average
  	:c N [M]	plot column N [average of columns N to M]
  	:f format	set the x coordinate numerical format
  	:i imagename	open a new image for input
  	:l N [M]	plot line N [average of lines N to M]
  	:o		overplot
  	:log+		log scale in Y
  	:log-		turn off log scale in Y
  	:step N		set step size for j,k
  	:solid		overplot with solid, not dashed, lines
  	:w wcsname	change world coordinate systems
  	:x x1 x2	fix range in X (call with no args to unfix)
  	:y y1 y2	fix range in Y (call with no args to unfix)
  </PRE>
  </PRE>
  <P>
  <P>
  The <TT>'c'</TT> and <TT>'l'</TT> commands are identical to the keystroke commands except
  that the column or line position is explicitly entered rather than taken
  from the cursor.  An averaging factor entered with <TT>'a'</TT> will apply to all
  subsequent line and column plots, as well as plots generated by <TT>'j'</TT> and <TT>'k'</TT>.
  The input image may be changed at any time using the <TT>'i'</TT> command; only one
  image may be open at a time.  Log scaling on the Y axis may be turned on
  and off with the 'log' commands.  The default step size of 1/10 the height
  of the image may be changed with the 'step' command.  Finally, the 'solid'
  command may be used to draw all overplotted curves using solid, rather than
  dashed, line segments.
  <P>
  The <TT>'x'</TT> and <TT>'y'</TT> commands may be used to fix the plotting scale in either
  X or Y, i.e., to disable autoscaling.  Once the scale is fixed on an axis
  it remains fixed until either the fix scale command is repeated without
  any arguments, or the <TT>'e'</TT> option is used to expand the plot (this causes
  the fixed scale to be lost).  Plotting different lines or columns or even
  changing images does not cause loss of fixed scaling.  If the X scale is
  fixed to a range less than an entire line or column Y autoscaling, if enabled,
  will only pertain to the displayed range in X.
  <P>
  The numerical format for the coordinate labels are set with the <TT>'f'</TT>
  command.  The values may be "<TT></TT>" (an empty string), %f for decimal format, %h
  and %H for xx:xx:xx format, and %m and %M for xx:xx.x format.  The upper
  case %H and %M convert degrees to hours.  Some images have a recommended x
  coordinate format defined as a WCS attribute.  If the format value is "<TT></TT>"
  (the default) the WCS attribute format will be used.  Any other value will
  override the image attribute.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Enter cursor mode, plotting line 240 of the 300x480 image 'crab':
  <P>
  <PRE>
  	cl&gt; implot crab
  	(plot appears)
  </PRE>
  <P>
  Type <TT>'?'</TT> to get the list of recognized keystrokes.  Move the cursor and
  type <TT>'l'</TT> to plot the line at the Y position of the cursor.  Try typing <TT>'c'</TT>
  to plot a column (note that a column plot will take longer than a line
  plot since the entire image must be read).  Go back to a line plot and
  try several <TT>'k'</TT> keystrokes to step up through the image.  Try a cursor
  mode <TT>'E'</TT> to playback a movie of a small region, then type 0 (zero) to
  restore the original plot.
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  It should be possible to use the image display cursor to mark the lines or
  columns to be plotted.  This capability will be added when the image display
  is interfaced to GIO (the IRAF graphics subsystem).
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imexamine, cursor
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>