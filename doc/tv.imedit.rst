.. _imedit:

imedit — Examine and edit pixels in images
==========================================

**Package: tv**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  imedit -- examine and edit pixels in images
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  imedit input output
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of images to be edited.  Images must be two dimensional.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>List of output images.  The list must match the input list or be empty.
  In the latter case the output image is the same as the input image; i.e.
  the edited image replaces the input image.
  </DD>
  </DL>
  <DL>
  <DT><B>cursor = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cursor' Line='cursor = ""'>
  <DD>The editing commands are entered via a cursor list.  When the task is
  run interactively this will normally be the standard image cursor
  (stdimcur) specified by a null string.  Commands may be read from
  a file.  The file format may be cursor values including the command
  keys, a simple list of positions with the default command given
  by the <I>default</I> parameter, and a regions file, as used in
  the task <B>fixpix</B> and the <B>ccdred</B> package, selected by
  the <I>fixpix</I> parameter.
  </DD>
  </DL>
  <DL>
  <DT><B>logfile = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logfile' Line='logfile = ""'>
  <DD>File in which to record the editing commands which modify the images.
  The display and statistics commands which don't modify the images are
  not recorded.  This file may be used for keeping a record of the
  modifications.  It may also be used as cursor input for other images
  to replicate the same editing operations.
  </DD>
  </DL>
  <DL>
  <DT><B>display = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='display' Line='display = yes'>
  <DD>Display the image during editing?  If yes then the display command,
  given by the parameter <I>command</I>, is used to display the image.
  Normally the display is used when editing interactively and turned
  off when using file input.
  </DD>
  </DL>
  <DL>
  <DT><B>autodisplay = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='autodisplay' Line='autodisplay = yes'>
  <DD>Automatically redisplay the image after each change?  If the display
  of the image is rapid enough then each change can be displayed as
  it is made by setting this parameter to yes.  However, it is faster
  to accumulate changes and then explicitly redisplay the image.
  When the parameter is no then the image is only redisplayed by
  explicit command.
  </DD>
  </DL>
  <DL>
  <DT><B>autosurface = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='autosurface' Line='autosurface = no'>
  <DD>Automatically display surface plots after each change?  In addition
  to the image display command, the task can display a before and after
  surface plot of the modified region.  This can be done by explicit
  command or automatically after each change.
  </DD>
  </DL>
  <DL>
  <DT><B>aperture = "<TT>circular</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='aperture' Line='aperture = "circular"'>
  <DD>Aperture for aperture editing.  Some commands specify the region to
  be edited by a center and radius.  The shape of the aperture is selected
  by this parameter.  The choices are "<TT>circular</TT>" and "<TT>square</TT>".  Note that
  this does not apply to commands in which a rectangle is specified by
  selecting the corners.
  </DD>
  </DL>
  <DL>
  <DT><B>radius = 2.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='radius' Line='radius = 2.'>
  <DD>Radius of the aperture for commands selecting an aperture.  For circular
  apertures this is the radius while for square apertures it is half of the
  side of the square.  Note that partial pixels are not used so that a
  circular aperture is not perfectly circular; i.e. if  the center of a
  pixel is within this distance of the center pixel it is modified and
  otherwise it is not.  A radius of zero may be used to select a single
  pixel (with either aperture type).
  </DD>
  </DL>
  <DL>
  <DT><B>search = 2.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='search' Line='search = 2.'>
  <DD>Search radius for adjusting the position of the region to be edited.
  This applies to both aperture regions and rectangular regions.  The
  center pixel of the region is searched within this radius for the
  maximum or minimum pixel value.  If the value is zero then no searching
  is done and the specified region is used directly.  If the value is
  positive then the specified region is adjusted to be centered on a
  relative maximum.  A relative minimum may be found if the value is
  negative with the absolute value used as the search radius.
  </DD>
  </DL>
  <DL>
  <DT><B>buffer = 1.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='buffer' Line='buffer = 1.'>
  <DD>Background buffer width.  A buffer annulus separates the region to be
  edited from a background annulus used for determining the background.
  It has the same shape as the region to be edited; i.e. circular, square,
  rectangular, or line.
  </DD>
  </DL>
  <DL>
  <DT><B>width = 2.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='width' Line='width = 2.'>
  <DD>Width of background annulus.  The pixels used for background determinations
  is taken from an annulus of the same shape as the region to be edited and
  with the specified width in pixels.
  </DD>
  </DL>
  <DL>
  <DT><B>xorder = 2, yorder = 2</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xorder' Line='xorder = 2, yorder = 2'>
  <DD>Orders (number of terms) of surface polynomial fit to background pixels
  for statistics and background subtraction.  The orders should generally
  be low with orders of 2 for a plane background.  If either order is
  zero then a median background is used.
  </DD>
  </DL>
  <DL>
  <DT><B>value = 0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='value' Line='value = 0.'>
  <DD>Value for constant substitution.  One editing command is replacement of
  a region by this value.
  </DD>
  </DL>
  <DL>
  <DT><B>minvalue = INDEF, maxvalue = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='minvalue' Line='minvalue = INDEF, maxvalue = INDEF'>
  <DD>Range of values which may be modified.  Value of INDEF map to the minimum
  and maximum possible values.
  </DD>
  </DL>
  <DL>
  <DT><B>sigma = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sigma' Line='sigma = INDEF'>
  <DD>Sigma of noise to be added to substitution values.  If less than or
  equal to zero then no noise is added.  If INDEF then pixel values from
  the background region are randomly selected after subtracting the
  fitted background surface or median.  Finally if a positive value is given than
  a gaussian noise distribution is added.
  </DD>
  </DL>
  <DL>
  <DT><B>angh = -33., angv = 25.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='angh' Line='angh = -33., angv = 25.'>
  <DD>Horizontal and vertical viewing angles (in degrees) for surface plots.
  </DD>
  </DL>
  <DL>
  <DT><B>command = "<TT>display $image 1 erase=$erase fill=yes order=0 &gt;&amp; dev$null</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='command' Line='command = "display $image 1 erase=$erase fill=yes order=0 &gt;&amp; dev$null"'>
  <DD>Command for displaying images.  This task displays images by executing a
  standard IRAF command.  Two arguments may be substituted by the appropriate
  values; the image name specified by "<TT>$image</TT>" and the boolean erase
  flag specified by "<TT>$erase</TT>".  Except for unusual cases the <B>tv.display</B>
  command is used with the fill option.  The fill option is required to
  provide a zoom feature.  See the examples for another possible command.
  </DD>
  </DL>
  <DL>
  <DT><B>graphics = "<TT>stdgraph</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = "stdgraph"'>
  <DD>Graphics device used for surface plots.  Normally this is the standard
  graphics device "<TT>stdgraph</TT>" though other possibilities are "<TT>stdplot</TT>"
  and "<TT>stdvdm</TT>".  Note the standard graphics output may also be
  redirected to a file with "<TT>&gt;G file</TT>" where "<TT>file</TT>" is any file name.
  </DD>
  </DL>
  <DL>
  <DT><B>default = "<TT>b</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='default' Line='default = "b"'>
  <DD>Default command option for simple position list input.  If the input
  is a list of column and line positions (x,y) then the command executed
  at each position is given by this parameter.  This should be one of
  the aperture type editing commands, the statistics command, or the
  surface plotting command.  Two keystroke commands would obviously 
  be incorrect.  <I>This parameter is ignored in "fixpix" mode</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>fixpix = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fixpix' Line='fixpix = no'>
  <DD>Fixpix style input?  This type of input consists of rectangular regions
  specified by lines giving the starting and ending column and starting
  and ending line.  This is the same input used by <B>fixpix</B> and in
  the <B>ccdred</B> package.  The feature to refer to "<TT>untrimmed</TT>" images
  in the latter package is not available in this task.  When selected
  the editing consists of interpolation across the narrowest dimension
  of the region and the default key is ignored.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Regions of images are examined and edited.  This may be done interactively
  using an image display and cursor or non-interactively using a list of
  positions and commands.  There are a variety of display and editing
  options.  A list of input images and a matching list of output images
  are specified.  The output images are only created if the input image
  is modified (except by an explicit "<TT>write</TT>" command).  If no output
  list is specified (an empty list given by "<TT></TT>") then the modified images
  are written back to the input images.  The images are edited in
  a temporary buffer image beginning with "<TT>imedit</TT>".
   
  Commands are given via a cursor list.  When the task is run
  interactively this will normally be the standard image cursor
  (stdimcur).  Commands may be read from a file.  The file format may be
  cursor values including the command keys, a simple list of positions
  with the default command given by the <I>default</I> parameter, and a
  regions file, as used in the task <B>fixpix</B> and the <B>ccdred</B>
  package, selected by the <I>fixpix</I> parameter.
   
  The commands which modify the image may be written to a log file specified
  by parameter <I>logfile</I>.  This file can be used as a record of the
  pixels modified.  The format of this file is also suitable for input
  as a cursor list.  This allows the same commands to be applied to other
  images.  <I>Be careful not to have the cursor input and logfile have the
  same name!</I>
   
  When the <I>display</I> parameter is set the command given by the parameter
  <I>command</I> is executed.  Normally this command loads the image display
  though it could also create a contour map or other graph whose x and y
  coordinates are the same as the image coordinates.  The image is displayed
  when editing interactively and the standard image cursor (which can
  be redefined to be the standard graphics cursor) is used to select
  regions to be edited.  When not editing interactively the display
  flag should be turned off.
   
  It is nice to see changes to the image displayed immediately.  This is
  possible using the <I>autodisplay</I> option.  Note that this requires
  the display parameter to also be set.  If the autodisplay flag is set
  the display command is repeated after each change to the image.  The
  drawback to this is that the full image (or image section) is reloaded
  and so can be slow.  If not set it is still possible to explicitly give
  a redisplay command, <TT>'r'</TT>, after a number of changes have been made.
   
  Another display option is to make surface graphs to the specified
  graphics device (normally the standard graphics terminal).  This may
  be done by the commands <TT>'g'</TT> and <TT>'s'</TT> and automatically after each
  change if the <I>autosurface</I> parameter is set.  The two types of
  surface plots are a single surface of the image at the marked position
  and before and after plots for a change.
   
  Regions of the image to be examined or edited are selected by one
  or two cursor commands.  The single cursor commands define the center
  of an aperture.  The shape of the aperture, circular or square, is
  specified by the <I>aperture</I> parameter and the radius (or half
  the edge of a square) is specified by the <I>radius</I> parameter.
  The radius may be zero to select a single pixel.  The keys <TT>'+'</TT> and
  <TT>'-'</TT> may be used to quickly increment or decrement the current radius.
  The two keystroke commands either define the corners of a rectangular
  region or the endpoints of a line.
   
  Because it is sometimes difficult to mark cursor position precisely
  the defined region may be shifted so that the center is either
  a local maximum or minimum.  This is usually desired for editing
  cosmicrays, bad pixels, and stars.  The center pixel of the aperture
  is moved within a specified search radius given by parameter
  <I>search</I>.  If the search radius is zero then the region defined
  by the cursor is not adjusted.  The sign of the search radius
  selects whether a maximum (positive value) or a minimum (negative value)
  is sought.  The special key <TT>'t'</TT> toggles between the two modes
  in order to quickly edit both low sensitivity bad pixels and
  cosmicrays and stars.
   
  Once a region has been defined a background region may be required
  to estimate the background for replacement.  The background
  region is an annulus of the same shape separated by a buffer width,
  given by the parameter <I>buffer</I>, and having a width given by
  the parameter <I>width</I>.
   
  The replacement options are described below as is a summary of all the
  commands.  Two commands requiring a little more description are the
  space and <TT>'p'</TT> commands.  These print the statistics at the cursor
  position for the current aperture and background parameters.  The
  printout gives the x and y position of the aperture center (after the
  search if any), the pixel value (z) at that pixel, the mean background
  subtracted flux in the aperture, the number of pixels in the aperture,
  the mean background "<TT>sky</TT>", the sigma of the background residuals from
  the background fit, and the number of pixels in the background region.
  The <TT>'p'</TT> key additionally prints the pixel values in the aperture.
  Beware of apertures with radii greater than 5 since they will wrap
  around in an 80 column terminal.
   
  When done editing or examining an image exit with <TT>'q'</TT> or <TT>'Q'</TT>.  The
  former saves the modified image in the output image (which might be
  the same as the input image) while the latter does not save the
  modified image.  Note that if the image has not been modified then
  no output occurs.  After exiting the next image in the input
  list is edited.  One may also change input images using the
  "<TT>:input</TT>" command.  Note that this command sets the output to be the
  same as the input and a subsequent "<TT>:output</TT>" command should be
  used to define a different output image name.  A final useful
  colon command is "<TT>:write</TT>" which forces the current editor buffer
  to be written.  This can be used to save partial changes.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Replacement algorithms</H3>
  <! BeginSection: 'REPLACEMENT ALGORITHMS'>
  <UL>
  The parameters "<TT>minvalue</TT>" and "<TT>maxvalue</TT>" are may be used to limit the
  range of values modified.  The default is to modify all pixels which
  are selected as described below.
  <P>
  <DL>
  <DT><B>a, b</B></DT>
  <! Sec='REPLACEMENT ALGORITHMS' Level=0 Label='a' Line='a, b'>
  <DD>Replace rectangular or aperture regions by background values.  A background
  surface is fit the pixels in the background annulus if the x and y orders
  are greater than zero otherwise a median is computed.  The x and y orders
  of the surface function are given by the <I>xorder</I> and <I>yorder</I>
  parameters.  The median is used or the surface is evaluated for the pixels
  in the replacement region.  If a positive sigma is specified then gaussian
  noise is added.  If a sigma of INDEF is specified then the residuals of the
  background pixels are sorted, the upper and lower 10% are excluded, and the
  remainder are randomly selected as additive noise.
  </DD>
  </DL>
  <DL>
  <DT><B>c, f, l</B></DT>
  <! Sec='REPLACEMENT ALGORITHMS' Level=0 Label='c' Line='c, f, l'>
  <DD>Replace rectangular or line regions by interpolation from the nearest
  background column or line.  The <TT>'f'</TT> line option interpolates across the
  narrowest dimension; i.e. for lines nearer to the line axis interpolation
  is by lines while for those  nearer to the column axis interpolation is
  by columns.  The buffer region applies but only the nearest background
  pixel at each line or column on either side of the replacement region
  is used for interpolation.  Gaussian noise may be added but background
  sampling is not available.  This method is similar to the method used
  in <B>fixpix</B> or <B>ccdred</B> with no buffer.  For "<TT>fixpix</TT>" type
  input the type of interpolation is automatically selected for the
  narrower dimension with column interpolation for square regions.
  </DD>
  </DL>
  <DL>
  <DT><B>d, e, v</B></DT>
  <! Sec='REPLACEMENT ALGORITHMS' Level=0 Label='d' Line='d, e, v'>
  <DD>Replace rectangular, aperture, or vector regions by the specified
  constant value.  This may be used to flag pixels or make masks.
  The vector option makes a line between two points with a width
  set by the radius value.
  </DD>
  </DL>
  <DL>
  <DT><B>j, k</B></DT>
  <! Sec='REPLACEMENT ALGORITHMS' Level=0 Label='j' Line='j, k'>
  <DD>Replace rectangular or aperture regions in the editor buffer by the data
  from the input image.  This may be used to undo any change.  Note that
  the <TT>'i'</TT> command can be used to completely reinitialize the editor
  buffer from the input image.
  </DD>
  </DL>
  <DL>
  <DT><B>m, n</B></DT>
  <! Sec='REPLACEMENT ALGORITHMS' Level=0 Label='m' Line='m, n'>
  <DD>Replace an aperture region by another aperture region.  There is no
  centering applied in this option.  The aperture region to copy is
  background subtracted using the background annulus for median or surface
  fitting.  This data may then be added to the destination aperture or
  replace the data in the destination aperture.  In the latter case the
  destination background surface is also computed and added.
  </DD>
  </DL>
  <DL>
  <DT><B>u</B></DT>
  <! Sec='REPLACEMENT ALGORITHMS' Level=0 Label='u' Line='u'>
  <DD>Undo the last change.  When a change is made the before and after data
  are saved.  An undo exchanges the two sets of data.  Note that it is
  possible to undo an undo to restore a change.  If any other command is
  used which causes data to be read (including the statistics and surface
  plotting) then the undo is lost.
  </DD>
  </DL>
  <DL>
  <DT><B>=, &lt;, &gt;</B></DT>
  <! Sec='REPLACEMENT ALGORITHMS' Level=0 Label='' Line='=, &lt;, &gt;'>
  <DD>The all pixels with a value equal to that of the pixel at the cursor
  position are replaced by the specified constant value.  This is intended
  for editing detection masks where detected objects have specific mask
  values.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REPLACEMENT ALGORITHMS'>
  <H3>Commands</H3>
  <! BeginSection: 'COMMANDS'>
  <UL>
  <CENTER>		IMEDIT CURSOR KEYSTROKE COMMANDS
  
  </CENTER><BR>
   
  <PRE>
  	?	Print help
  	:	Colon commands (see below)
  	&lt;space&gt;	Statistics
  	g	Surface graph
  	i	Initialize (start over without saving changes)
  	q	Quit and save changes
  	p	Print box of pixel values and statistics
  	r	Redraw image display
  	s	Surface plot at cursor
  	t	Toggle between minimum and maximum search
  	+	Increase radius by one
  	-	Decrease radius by one
  	I	Interrupt task immediately
  	Q	Quit without saving changes
  </PRE>
  <P>
  The following editing options are available.  Rectangular, line, and
  vector regions are specified with two positions and aperture regions
  are specified by one position.  The current aperture type (circular or
  square) is used in the latter case.  The move option takes two positions,
  the position to move from and the position to move to.
  <P>
  <PRE>
  	a 	Background replacement (rectangle)
  	b 	Background replacement (aperture)
  	c 	Column interpolation (rectangle)
  	d 	Constant value substitution (rectangle)
  	e 	Constant value substitution (aperture)
  	f	Interpolation across line (line)
  	j	Replace with input data (rectangle)
  	k	Replace with input data (aperture)
  	l 	Line interpolation (rectangle)
  	m	Copy by replacement (aperture)
  	n	Copy by addition (aperture)
  	u	Undo last change (see also <TT>'i'</TT>, <TT>'j'</TT>, and <TT>'k'</TT>)
  	v	Constant value substitution (vector)
  	=	Constant value substitution of pixels equal
  		    to pixel at the cursor position
  	&lt;	Constant value substitution of pixels less than or equal
  		    to pixel at the cursor position
  	&gt;	Constant value substitution of pixels greater than or equal
  		    to pixel at the cursor position
  </PRE>
   
  When the image display provides a fill option then the effect of zoom
  and roam is provided by loading image sections.  This is a temporary
  mechanism which will eventually be replaced by a more sophisticated
  image display interface.
   
  <PRE>
  	E	Expand image display
  	P	Pan image display
  	R	Redraw image display
  	Z	Zoom image display
  	0	Redraw image display with no zoom
  	1-9	Shift display
  </PRE>
   
   
  <CENTER>IMEDIT COLON COMMANDS
  
  </CENTER><BR>
   
  The colon either print the current value of a parameter when there is
  no value or set the parameter to the specified value.
   
  <PRE>
  angh [value]		Horizontal viewing angle (degrees)
  angv [value]		Vertical viewing angle (degrees)
  aperture [type]		Aperture type (circular|square)
  autodisplay [yes|no]	Automatic image display?
  autosurface [yes|no]	Automatic surface plots?
  buffer [value]		Background buffer width
  command [string]	Display command
  display [yes|no]	Display image?
  eparam			Edit parameters
  graphics [device]	Graphics device
  input [image]		New input image to edit (output name = input)
  output [image]		New output image name
  radius [value]		Aperture radius
  search [value]		Search radius
  sigma [value]		Noise sigma (INDEF for histogram replacement)
  value [value]		Constant substitution value
  minvalue [value]	Minimum value for modification (INDEF=minimum)
  maxvalue [value]	Maximum value for modification (INDEF=maximum)
  width [value]		Background annulus width
  write [name]		Write changes to name (default current output) 
  xorder [value]		X order for background fitting
  yorder [value]		Y order for background fitting
  </PRE>
  </UL>
  <! EndSection:   'COMMANDS'>
  <H3>Keywords</H3>
  <! BeginSection: 'KEYWORDS'>
  <UL>
  None
  </UL>
  <! EndSection:   'KEYWORDS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  Interactively edit an image.
   
  	cl&gt; imedit raw002 ed002
   
  2.  Edit pixels non-interactively from an x-y list.  Replace the original images
      by the edited images.
   
  <PRE>
  	cl&gt; head bad
  	20 32
  	40 91
  	&lt;etc&gt;
  	cl&gt; imedit raw* "" cursor=bad display-
  </PRE>
   
  3.  It is possible to use a contour plot for image display.  This is really
      not very satisfactory but can be used in desperation.
   
  <PRE>
  	cl&gt; reset stdimcur=stdgraph
  	cl&gt; display.command="contour $image &gt;&amp; dev$null"
  	cl&gt; imedit raw002 ed002
  </PRE>
   
  4.  Use a "<TT>fixpix</TT>" file (without trim option).
   
  <PRE>
  	cl&gt; head fixpix
  	20 22 30 80
  	99 99 1 500
  	&lt;etc&gt;
  	cl&gt; imedit raw* %raw%ed%* cursor=fixpix fixpix+ display-
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>IMEDIT V2.13</B></DT>
  <! Sec='REVISIONS' Level=0 Label='IMEDIT' Line='IMEDIT V2.13'>
  <DD>The <TT>'v'</TT> option was added to allow vector replacement.
  The <TT>'='</TT>, <TT>'<'</TT>, <TT>'>'</TT> options were added to replace values matching the pixel
  at the cursor.
  </DD>
  </DL>
  <DL>
  <DT><B>IMEDIT V2.11.2</B></DT>
  <! Sec='REVISIONS' Level=0 Label='IMEDIT' Line='IMEDIT V2.11.2'>
  <DD>The temporary editor image was changed to use a unique temporary image
  name beginning with "<TT>imedit</TT>" rather than the fixed name of "<TT>epixbuf</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>IMEDIT V2.11</B></DT>
  <! Sec='REVISIONS' Level=0 Label='IMEDIT' Line='IMEDIT V2.11'>
  <DD>If xorder or yorder are zero then a median background is computed
  for the <TT>'a'</TT> and <TT>'b'</TT> keys.
  </DD>
  </DL>
  <DL>
  <DT><B>IMEDIT V2.10.4</B></DT>
  <! Sec='REVISIONS' Level=0 Label='IMEDIT' Line='IMEDIT V2.10.4'>
  <DD>The <TT>'u'</TT>, <TT>'j'</TT>, <TT>'k'</TT>, and <TT>'n'</TT> keys were added to those recorded in the
  log file.
  </DD>
  </DL>
  <DL>
  <DT><B>IMEDIT V2.8</B></DT>
  <! Sec='REVISIONS' Level=0 Label='IMEDIT' Line='IMEDIT V2.8'>
  <DD>This task is a first version of what will be an evolving task.
  Additional features and options will be added as they are suggested.
  It is also a prototype using a very limited display interface; execution
  of a separate display command.  Much better interaction with a variety
  of image displays will be provided after a planned "<TT>image display
  interface</TT>" is implemented.  Therefore any deficiencies in this area
  should be excused.
   
  The zoom and roam features provided here are quite useful.  However,
  they depend on a feature of the tv.display program which fills the
  current image display window by pixel replication or interpolation.
  If this is left out of the display command these features will not
  work.  The trick is that this task displays sections of the editor
  buffer whose size and position is based on an internal zoom and
  center and the display program expands the section to fill the
  display.
   
  The surface plotting is done using an imported package.  The limitations
  of this package (actually limitations in the complexity of interfacing
  the application to this sophisticated package) mean that the
  surface plots are always scaled to the range of the data and that
  it is not possible to label the graph or use the graphics cursor to
  point at features for the task.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  ccdred.instruments proto.fixpix
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'REPLACEMENT ALGORITHMS' 'COMMANDS' 'KEYWORDS' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
