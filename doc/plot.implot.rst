.. _implot:

implot: Plot lines and columns of images using cursors
======================================================

**Package: plot**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  implot -- plot lines and columns of images
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  implot image [line]
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>image</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='image' Line='image' -->
  <dd>List of images to be plotted.  If more than one image is in the list then
  the <tt>'m'</tt> and <tt>'n'</tt> keys are used proceed to the previous and next image.
  </dd>
  </dl>
  <dl>
  <dt><b>line</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='line' Line='line' -->
  <dd>If given, the number of the image line to be plotted, otherwise the central
  line is plotted.
  </dd>
  </dl>
  <dl>
  <dt><b>wcs = <tt>"logical"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='wcs' Line='wcs = "logical"' -->
  <dd>The world coordinate system (<i>wcs</i>) to be used for axis labeling.
  The following standard world systems are predefined.
  <dl>
  <dt><b>logical</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='logical' Line='logical' -->
  <dd>Logical coordinates are image pixel coordinates relative to the image currently
  being displayed.
  </dd>
  </dl>
  <dl>
  <dt><b>physical</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='physical' Line='physical' -->
  <dd>The physical coordinate system is invariant with respect to linear
  transformations of the physical image matrix.  For example, if the reference
  image was created by extracting a section of another image, the physical
  coordinates of an object in the reference image will be the pixel coordinates
  of the same object in the original image.  The physical coordinate system
  thus provides a consistent coordinate system (a given object always has the
  same coordinates) for all images, regardless of whether any user world
  coordinate systems have been defined.
  </dd>
  </dl>
  <dl>
  <dt><b>world</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='world' Line='world' -->
  <dd>The <tt>"world"</tt> coordinate system is the <i>current default WCS</i>.
  The default world system is the system named by the environment variable
  <i>defwcs</i> if defined in the user environment and present in the reference
  image WCS description, else it is the first user WCS defined for the image
  (if any), else physical coordinates are returned.
  </dd>
  </dl>
  In addition to these three reserved WCS names, the name of any user WCS
  defined for the reference image may be given.  A user world coordinate system
  may be any linear or nonlinear world system.
  </dd>
  </dl>
  <dl>
  <dt><b>step = 0</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='step' Line='step = 0' -->
  <dd>Step size for stepping through lines or columns in an image with the
  <tt>'j'</tt> and <tt>'k'</tt> keys.  If zero or INDEF the step defaults to ~10% of the
  image axis length.  This parameter may be changed interactively with
  a colon command.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  Implot is an interactive, cursor driven task for examining images by plotting
  the lines and columns or the averages of lines and columns.  An image
  line is plotted when the task is first run, then cursor mode is entered and
  keystrokes may be used to generate additional line and column plots.  <tt>'q'</tt>
  is typed to exit cursor mode and implot and <tt>'n'</tt> is typed to proceed to
  the next image in the input image list.
  </p>
  <p>
  The following single character keystrokes are recognized by Implot.  Note that
  numerous additional keystrokes are provided by <tt>"cursor mode"</tt> itself, i.e.,
  by the graphics system.  These additional keystrokes provide such standard
  facilities as stepwise cursor motion, plot expansion, movies, disposal to a
  batch plotter or metafile, and plot annotation facilities.  Cursor mode is
  documented elsewhere.
  </p>
  <pre>
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
  </pre>
  <p>
  The single character keystroke commands use the position to the cursor to
  determine what region of the image to plot.  If the plot is examined carefully
  one will note an extra scale on the right hand edge.  This scale gives the
  <tt>"other"</tt> axis of the image in units of pixels.  For example, if the current
  plot is a line plot (rather than a column plot), the X axis of the plot
  will correspond to the X axis of the image, and the right Y axis of the plot
  will correspond to the Y axis of the image.  Both axes will be scaled
  linearly in units of pixels.  The left Y axis is scaled in either linear or
  logarithmic pixel intensity units.  In the case of a column plot the bottom
  axis will correspond to image Y and the right axis to image X.
  </p>
  <p>
  The <tt>'l'</tt> and <tt>'c'</tt> keystrokes, used to plot lines and columns, take image
  coordinates from the bottom and right axes of the plot.  In the case of a
  lineplot, the cursor would be positioned in Y and the key <tt>'l'</tt> typed to
  plot a new line.  Extrapolation of this convention to the other cases and
  keystrokes is self evident.  The <tt>'a'</tt> keystroke is used to mark an X or Y
  region to be averaged and plotted.  This mode of averaging is independent
  of the ':a' command discussed below.
  </p>
  <p>
  Successive vectors may be overplotted by typing an <tt>'o'</tt> and then any other
  command.  A range of linetypes are used if the device supports them to
  make the curves easier to distinguish.  The position of each line is marked
  on the right axis with a small tick to document the coordinates of the
  curves.
  </p>
  <p>
  The <tt>'j'</tt> and <tt>'k'</tt> commands are used to step through an image in either the
  upward (k) or downward (j) directions, relative to the current line or
  column plot.  Each new vector is plotted in place of the previous one
  without clearing the screen, making it easy to compare successive vectors.
  The step between vectors may be defined by a task parameter and
  changed by a colon command.
  </p>
  <p>
  The <tt>'m'</tt> and <tt>'n'</tt> commands are used to step through the input image list.
  This is the same as using the <tt>'i'</tt> key to switch images and the <tt>'l'</tt> key
  to plot the same line or column as the previous image.
  </p>
  <p>
  There are three keys which print various quantities of interest.
  The space bar key will read the cursor position, find the nearest pixel,
  and report the image line and column, the coordinate along the current
  axis, and the pixel value.  The line and column are in logical pixels
  (that is the coordinates in the current image section) and the
  coordinates are in the selected world coordinate system and printed
  in the current coordinate format.  If the selected world coordinate
  system is <tt>"logical"</tt> then the coordinate will be the same as the line
  or column.
  </p>
  <p>
  The <tt>'s'</tt> key requires two cursor positions and then computes statistics of
  the region.  The values are the median, mean, sigma, sum, and number of
  pixels.  The <tt>'p'</tt> key also requires two cursor positions with the x
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
  are multiple lines of results which are scrolled using the <tt>'/'</tt> key.
  </p>
  <p>
  In addition to the single keystroke commands, the following : escape
  commands are provided:
  </p>
  <pre>
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
  </pre>
  <p>
  The <tt>'c'</tt> and <tt>'l'</tt> commands are identical to the keystroke commands except
  that the column or line position is explicitly entered rather than taken
  from the cursor.  An averaging factor entered with <tt>'a'</tt> will apply to all
  subsequent line and column plots, as well as plots generated by <tt>'j'</tt> and <tt>'k'</tt>.
  The input image may be changed at any time using the <tt>'i'</tt> command; only one
  image may be open at a time.  Log scaling on the Y axis may be turned on
  and off with the 'log' commands.  The default step size of 1/10 the height
  of the image may be changed with the 'step' command.  Finally, the 'solid'
  command may be used to draw all overplotted curves using solid, rather than
  dashed, line segments.
  </p>
  <p>
  The <tt>'x'</tt> and <tt>'y'</tt> commands may be used to fix the plotting scale in either
  X or Y, i.e., to disable autoscaling.  Once the scale is fixed on an axis
  it remains fixed until either the fix scale command is repeated without
  any arguments, or the <tt>'e'</tt> option is used to expand the plot (this causes
  the fixed scale to be lost).  Plotting different lines or columns or even
  changing images does not cause loss of fixed scaling.  If the X scale is
  fixed to a range less than an entire line or column Y autoscaling, if enabled,
  will only pertain to the displayed range in X.
  </p>
  <p>
  The numerical format for the coordinate labels are set with the <tt>'f'</tt>
  command.  The values may be <tt>""</tt> (an empty string), %f for decimal format, %h
  and %H for xx:xx:xx format, and %m and %M for xx:xx.x format.  The upper
  case %H and %M convert degrees to hours.  Some images have a recommended x
  coordinate format defined as a WCS attribute.  If the format value is <tt>""</tt>
  (the default) the WCS attribute format will be used.  Any other value will
  override the image attribute.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Enter cursor mode, plotting line 240 of the 300x480 image 'crab':
  </p>
  <pre>
  	cl&gt; implot crab
  	(plot appears)
  </pre>
  <p>
  Type <tt>'?'</tt> to get the list of recognized keystrokes.  Move the cursor and
  type <tt>'l'</tt> to plot the line at the Y position of the cursor.  Try typing <tt>'c'</tt>
  to plot a column (note that a column plot will take longer than a line
  plot since the entire image must be read).  Go back to a line plot and
  try several <tt>'k'</tt> keystrokes to step up through the image.  Try a cursor
  mode <tt>'E'</tt> to playback a movie of a small region, then type 0 (zero) to
  restore the original plot.
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  It should be possible to use the image display cursor to mark the lines or
  columns to be plotted.  This capability will be added when the image display
  is interfaced to GIO (the IRAF graphics subsystem).
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  imexamine, cursor
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  -->
  
