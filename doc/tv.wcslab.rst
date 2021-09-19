.. _wcslab:

wcslab: Overlay a displayed image with a world coordinate grid
==============================================================

**Package: tv**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  wcslab -- overlay a labeled world coordinate grid on an image
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  wcslab image
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>image </b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='image' Line='image ' -->
  <dd>The name of the image to be labeled. If image is <tt>""</tt>, the parameters
  in wcspars will be used to draw a labeled coordinate grid.
  </dd>
  </dl>
  <dl>
  <dt><b>frame</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='frame' Line='frame' -->
  <dd>The display frame buffer displaying the image to be labeled.
  </dd>
  </dl>
  <dl>
  <dt><b>usewcs = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='usewcs' Line='usewcs = no' -->
  <dd>Use the world coordinate system specified by the parameters in the wcspars
  parameter set in place of the image world coordinate system  or if
  image is <tt>""</tt> ?
  </dd>
  </dl>
  <dl>
  <dt><b>wcspars = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='wcspars' Line='wcspars = ""' -->
  <dd>The name of the parameter set defining the world coordinate system
  to be used if image is <tt>""</tt> or if usewcs = <tt>"yes"</tt>.  The wcspars parameters
  are described in more detail below.
  </dd>
  </dl>
  <dl>
  <dt><b>wlpars = <tt>""</tt> </b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='wlpars' Line='wlpars = "" ' -->
  <dd>The name of the parameter set which controls the
  detailed appearance of the plot. The wlpars parameters are described
  in more detail below.
  </dd>
  </dl>
  <dl>
  <dt><b>fill = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='fill' Line='fill = yes' -->
  <dd>If fill is no, wcslab tries to
  create a square viewport with a maximum size dictated by the viewport
  parameters.  If fill is yes, then wcslab
  uses the viewport exactly as specified.
  </dd>
  </dl>
  <dl>
  <dt><b>vl = INDEF, vr = INDEF, vb = INDEF, vt = INDEF</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='vl' Line='vl = INDEF, vr = INDEF, vb = INDEF, vt = INDEF' -->
  <dd>The left, right, bottom, and top edges of the viewport in NDC (0-1)
  coordinates. If any of vl, vr, vb, or vt are  INDEF,
  wcslab computes a default value. To overlay the plot
  with a displayed image, vl, vr, vb, and vt must use the same viewport used
  by the display task to load the image into the frame buffer.
  </dd>
  </dl>
  <dl>
  <dt><b>overplot = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='overplot' Line='overplot = no' -->
  <dd>Overplot to an existing plot?  If yes, wcslab will not erase the
  current plot.  This differs from append in that a new viewport
  may be defined.  Append has priority if both
  append and overwrite are yes.
  </dd>
  </dl>
  <dl>
  <dt><b>append = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='append' Line='append = no' -->
  <dd>Append to an existing plot?  If no, wcslab resets the
  graphics to a new viewport/wcs for each new plot.  Otherwise, it uses
  the scaling from a previous plot. If append=yes but no plot was drawn, it
  will behave as if append=no.   This differs from overplot in that
  the same viewport is used.  Append has priority if both
  append and overwrite are yes.
  </dd>
  </dl>
  <dl>
  <dt><b>device = <tt>"imd"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='device' Line='device = "imd"' -->
  <dd>The graphics device. To create an overlay plot, device must be set
  to one of the imdkern devices listed in dev$graphcap. To create a 
  plot of the coordinate grid in the
  graphics window, device should be set to <tt>"stdgraph"</tt>.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Wcspars parameters</h3>
  <!-- BeginSection: 'WCSPARS PARAMETERS' -->
  <dl>
  <dt><b>ctype1 = <tt>"linear"</tt>, ctype2 = <tt>"linear"</tt></b></dt>
  <!-- Sec='WCSPARS PARAMETERS' Level=0 Label='ctype1' Line='ctype1 = "linear", ctype2 = "linear"' -->
  <dd>The coordinate system type of the first and second axes.
  Valid coordinate system types are:
  <tt>"linear"</tt>, and <tt>"xxx--tan"</tt>, <tt>"xxx-sin"</tt>, and <tt>"xxx-arc"</tt>, where <tt>"xxx"</tt> can be either
  <tt>"ra-"</tt> or <tt>"dec"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>crpix1 = 0.0, crpix2 = 0.0</b></dt>
  <!-- Sec='WCSPARS PARAMETERS' Level=0 Label='crpix1' Line='crpix1 = 0.0, crpix2 = 0.0' -->
  <dd>The X and Y coordinates of the reference point in pixel space that
  correspond to the reference point in world space.
  </dd>
  </dl>
  <dl>
  <dt><b>crval1 = 0.0, crval2 = 0.0</b></dt>
  <!-- Sec='WCSPARS PARAMETERS' Level=0 Label='crval1' Line='crval1 = 0.0, crval2 = 0.0' -->
  <dd>The X and Y coordinate of the reference point in world space that
  corresponds to the reference point in pixel space.
  </dd>
  </dl>
  <dl>
  <dt><b>cd1_1 = 1.0, cd1_2 = 0.0</b></dt>
  <!-- Sec='WCSPARS PARAMETERS' Level=0 Label='cd1_1' Line='cd1_1 = 1.0, cd1_2 = 0.0' -->
  <dd>The FITS CD matrix elements [1,1] and [1,2] which describe the x-axis
  coordinate transformation.  These elements usually have the values
  &lt;xscale * cos (angle)&gt; and, &lt;-yscale * sin (angle)&gt;, or, for ra/dec systems
  &lt;-xscale * cos (angle)&gt; and &lt;yscale * sin (angle)&gt;.
  </dd>
  </dl>
  <dl>
  <dt><b>cd2_1 = 0.0, cd2_2 = 1.0</b></dt>
  <!-- Sec='WCSPARS PARAMETERS' Level=0 Label='cd2_1' Line='cd2_1 = 0.0, cd2_2 = 1.0' -->
  <dd>The FITS CD matrix elements [2,1] and [2,2] which describe the y-axis
  coordinate transformation. These elements usually have the values
  &lt;xscale * sin (angle)&gt; and &lt;yscale * cos (angle)&gt;.
  </dd>
  </dl>
  <dl>
  <dt><b>log_x1 = 0.0, log_x2 = 1.0, log_y1 = 0.0, log_y2 = 1.0</b></dt>
  <!-- Sec='WCSPARS PARAMETERS' Level=0 Label='log_x1' Line='log_x1 = 0.0, log_x2 = 1.0, log_y1 = 0.0, log_y2 = 1.0' -->
  <dd>The extent in pixel space over which the transformation is valid.
  </dd>
  </dl>
  <!-- EndSection:   'WCSPARS PARAMETERS' -->
  <h3>Wlpars parameters</h3>
  <!-- BeginSection: 'WLPARS PARAMETERS' -->
  <dl>
  <dt><b>major_grid = yes</b></dt>
  <!-- Sec='WLPARS PARAMETERS' Level=0 Label='major_grid' Line='major_grid = yes' -->
  <dd>Draw a grid instead of tick marks at the position of the major
  axes intervals?  If yes, lines of constant axis 1 and axis 2 values
  are drawn.  If no, tick marks are drawn instead.  Major grid
  lines / tick marks are labeled with the appropriate axis values.
  </dd>
  </dl>
  <dl>
  <dt><b>minor_grid = no</b></dt>
  <!-- Sec='WLPARS PARAMETERS' Level=0 Label='minor_grid' Line='minor_grid = no' -->
  <dd>Draw a grid instead of tick marks at the position of the
  minor axes intervals?  If yes, lines of constant axis 1 and axis 2 values
  are drawn between the major grid lines / tick
  marks.  If no, tick marks are drawn instead. Minor grid lines / tick
  marks are not labeled.
  </dd>
  </dl>
  <dl>
  <dt><b>dolabel = yes</b></dt>
  <!-- Sec='WLPARS PARAMETERS' Level=0 Label='dolabel' Line='dolabel = yes' -->
  <dd>Label the major grid lines or tick marks?
  </dd>
  </dl>
  <dl>
  <dt><b>remember = no</b></dt>
  <!-- Sec='WLPARS PARAMETERS' Level=0 Label='remember' Line='remember = no' -->
  <dd>Modify the wlpars parameter file when done?  If yes, parameters that have
  been calculated by the task are written back to the parameter file.
  If no, the default, the parameter file is left untouched by the task.
  This option is useful for fine-tuning the appearance of the graph.
  </dd>
  </dl>
  <dl>
  <dt><b>axis1_beg = <tt>""</tt></b></dt>
  <!-- Sec='WLPARS PARAMETERS' Level=0 Label='axis1_beg' Line='axis1_beg = ""' -->
  <dd>The lowest value of axis 1 in world coordinates units
  at which a major grid line / tick mark will be drawn.
  If axis1_beg = <tt>""</tt>, wcslab  will compute this quantity.
  Axis1_beg will be ignored if axis1_end and axis1_int are undefined.
  </dd>
  </dl>
  <dl>
  <dt><b>axis1_end = <tt>""</tt></b></dt>
  <!-- Sec='WLPARS PARAMETERS' Level=0 Label='axis1_end' Line='axis1_end = ""' -->
  <dd>The highest value of axis 1 in world coordinate
  units at which a major grid line / tick mark will be drawn.
  If axis1_end = <tt>""</tt>, wcslab will compute this quantity.
  Axis1_end will be ignored if axis1_beg and axis1_int are undefined.
  </dd>
  </dl>
  <dl>
  <dt><b>axis1_int = <tt>""</tt></b></dt>
  <!-- Sec='WLPARS PARAMETERS' Level=0 Label='axis1_int' Line='axis1_int = ""' -->
  <dd>The interval in world coordinate units at which
  major grid lines / tick marks will be drawn along axis 1.
  If axis1_int = <tt>""</tt>, wcslab will compute this quantity.
  Axis1_int will be ignored if axis1_beg and axis1_end are undefined.
  </dd>
  </dl>
  <dl>
  <dt><b>axis2_beg = <tt>""</tt></b></dt>
  <!-- Sec='WLPARS PARAMETERS' Level=0 Label='axis2_beg' Line='axis2_beg = ""' -->
  <dd>The lowest value of axis 2 in world coordinates units
  at which a major grid line / tick mark will be drawn.
  If axis2_beg = <tt>""</tt>, wcslab  will compute this quantity.
  Axis2_beg will be ignored if axis2_end and axis2_int are undefined.
  </dd>
  </dl>
  <dl>
  <dt><b>axis2_end = <tt>""</tt></b></dt>
  <!-- Sec='WLPARS PARAMETERS' Level=0 Label='axis2_end' Line='axis2_end = ""' -->
  <dd>The highest value of axis 2 in world coordinate
  units at which a major grid line / tick mark will be drawn.
  If axis2_end = <tt>""</tt>, wcslab will compute this quantity.
  Axis2_end will be ignored if axis2_beg and axis2_int are undefined.
  </dd>
  </dl>
  <dl>
  <dt><b>axis2_int = <tt>""</tt></b></dt>
  <!-- Sec='WLPARS PARAMETERS' Level=0 Label='axis2_int' Line='axis2_int = ""' -->
  <dd>The interval in world coordinate units at which
  major grid lines / tick marks will be drawn along axis 2.
  If axis2_int = <tt>""</tt>, wcslab will compute this quantity.
  Axis2_int will be ignored if axis1_beg and axis1_end are undefined.
  </dd>
  </dl>
  <dl>
  <dt><b>major_line = <tt>"solid"</tt></b></dt>
  <!-- Sec='WLPARS PARAMETERS' Level=0 Label='major_line' Line='major_line = "solid"' -->
  <dd>The type of major grid lines to be plotted.
  The permitted values are <tt>"solid"</tt>, <tt>"dotted"</tt>, <tt>"dashed"</tt>, and <tt>"dotdash"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>major_tick = .03</b></dt>
  <!-- Sec='WLPARS PARAMETERS' Level=0 Label='major_tick' Line='major_tick = .03' -->
  <dd>Size of major tick marks relative to the size of the viewport.
  By default the major tick marks are .03 times the size of the
  viewport.
  </dd>
  </dl>
  <dl>
  <dt><b>axis1_minor = 5</b></dt>
  <!-- Sec='WLPARS PARAMETERS' Level=0 Label='axis1_minor' Line='axis1_minor = 5' -->
  <dd>The number of minor grid lines / tick marks that will appear between major 
  grid lines / tick marks for axis 1.
  </dd>
  </dl>
  <dl>
  <dt><b>axis2_minor = 5</b></dt>
  <!-- Sec='WLPARS PARAMETERS' Level=0 Label='axis2_minor' Line='axis2_minor = 5' -->
  <dd>The number of minor grid lines / tick marks that will appear between major
  grid lines / tick marks for axis 2.
  </dd>
  </dl>
  <dl>
  <dt><b>minor_line = <tt>"dotted"</tt></b></dt>
  <!-- Sec='WLPARS PARAMETERS' Level=0 Label='minor_line' Line='minor_line = "dotted"' -->
  <dd>The type of minor grid lines to be plotted.
  The permitted values are <tt>"solid"</tt>, <tt>"dotted"</tt>, <tt>"dashed"</tt>, and <tt>"dotdash"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>minor_tick = .01</b></dt>
  <!-- Sec='WLPARS PARAMETERS' Level=0 Label='minor_tick' Line='minor_tick = .01' -->
  <dd>Size of minor tick marks relative to the size of the viewport.
  BY default the minor tick marks are .01 times the size of the
  viewport.
  </dd>
  </dl>
  <dl>
  <dt><b>tick_in = yes</b></dt>
  <!-- Sec='WLPARS PARAMETERS' Level=0 Label='tick_in' Line='tick_in = yes' -->
  <dd>Do tick marks point into instead of away from the graph ?
  </dd>
  </dl>
  <dl>
  <dt><b>axis1_side = <tt>"default"</tt></b></dt>
  <!-- Sec='WLPARS PARAMETERS' Level=0 Label='axis1_side' Line='axis1_side = "default"' -->
  <dd>The list of viewport edges, separated by commas, on which to place the axis
  1 labels.  If axis1_side is <tt>"default"</tt>, wcslab will choose a side.
  Axis1_side may contain any combination of <tt>"left"</tt>, <tt>"right"</tt>,
  <tt>"bottom"</tt>, <tt>"top"</tt>, or <tt>"default"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>axis2_side = <tt>"default"</tt></b></dt>
  <!-- Sec='WLPARS PARAMETERS' Level=0 Label='axis2_side' Line='axis2_side = "default"' -->
  <dd>The list of viewport edges, separated by commas, on which to place the axis
  2 labels.  If axis2_side is <tt>"default"</tt>, wcslab will choose a side.
  Axis2_side may contain any combination of <tt>"left"</tt>, <tt>"right"</tt>,
  <tt>"bottom"</tt>, <tt>"top"</tt>, or <tt>"default"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>axis2_dir = <tt>""</tt></b></dt>
  <!-- Sec='WLPARS PARAMETERS' Level=0 Label='axis2_dir' Line='axis2_dir = ""' -->
  <dd>The axis 1 value at which the axis 2 labels will be written for polar graphs. 
  If axis2_dir is <tt>""</tt>, wcslab will compute this number.
  </dd>
  </dl>
  <dl>
  <dt><b>justify = <tt>"default"</tt></b></dt>
  <!-- Sec='WLPARS PARAMETERS' Level=0 Label='justify' Line='justify = "default"' -->
  <dd>The direction with respect to axis 2 along which the axis 2
  labels will be drawn from the point they are labeling on polar graphs.
  If justify = <tt>""</tt>, then wcslab will calculate this quantity.  The permitted
  values are <tt>"default"</tt>, <tt>"left"</tt>, <tt>"right"</tt>, <tt>"top"</tt>, and <tt>"bottom"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>labout = yes</b></dt>
  <!-- Sec='WLPARS PARAMETERS' Level=0 Label='labout' Line='labout = yes' -->
  <dd>Draw the labels outside the axes ?  If yes, the labels will be drawn
  outside the image viewport.  Otherwise, the axes labels will be drawn inside
  the image border.  The latter option is useful if the image fills the
  display frame buffer.
  </dd>
  </dl>
  <dl>
  <dt><b>full_label = no</b></dt>
  <!-- Sec='WLPARS PARAMETERS' Level=0 Label='full_label' Line='full_label = no' -->
  <dd>Always draw all the labels in full format (h:m:s or d:m:s) if the world
  coordinate system of the image is in RA and DEC ?  If full_label = no, then
  only certain axes will be labeled in full format. The remainder will
  be labeled in minutes or seconds as appropriate.
  </dd>
  </dl>
  <dl>
  <dt><b>rotate = yes</b></dt>
  <!-- Sec='WLPARS PARAMETERS' Level=0 Label='rotate' Line='rotate = yes' -->
  <dd>Permit the labels to rotate ?
  If rotate = yes, then labels will be written
  at an angle to match that of the major grid lines that are being
  labeled.  If rotate = no, then labels are always written
  <tt>"normally"</tt>, that is horizontally. If labout = no, then rotate is
  set to <tt>"no"</tt> by default.
  </dd>
  </dl>
  <dl>
  <dt><b>label_size = 1.0</b></dt>
  <!-- Sec='WLPARS PARAMETERS' Level=0 Label='label_size' Line='label_size = 1.0' -->
  <dd>The size of the characters used to draw the major grid line labels.
  </dd>
  </dl>
  <dl>
  <dt><b>title = <tt>"imtitle"</tt></b></dt>
  <!-- Sec='WLPARS PARAMETERS' Level=0 Label='title' Line='title = "imtitle"' -->
  <dd>The graph title. If title = <tt>"imtitle"</tt>, then a default title containing
  the image name and title is created.
  </dd>
  </dl>
  <dl>
  <dt><b>axis1_title = <tt>""</tt></b></dt>
  <!-- Sec='WLPARS PARAMETERS' Level=0 Label='axis1_title' Line='axis1_title = ""' -->
  <dd>The title for axis 1. By default no axis title is drawn.
  </dd>
  </dl>
  <dl>
  <dt><b>axis2_title = <tt>""</tt></b></dt>
  <!-- Sec='WLPARS PARAMETERS' Level=0 Label='axis2_title' Line='axis2_title = ""' -->
  <dd>The title for axis 2. By default no axis title is drawn.
  </dd>
  </dl>
  <dl>
  <dt><b>title_side = <tt>"top"</tt></b></dt>
  <!-- Sec='WLPARS PARAMETERS' Level=0 Label='title_side' Line='title_side = "top"' -->
  <dd>The side of the plot on which to place the title.
  The options are <tt>"left"</tt>, <tt>"right"</tt>, <tt>"bottom"</tt>, and <tt>"top"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>axis1_title_side = <tt>"default"</tt></b></dt>
  <!-- Sec='WLPARS PARAMETERS' Level=0 Label='axis1_title_side' Line='axis1_title_side = "default"' -->
  <dd>The side of the plot on which to place the axis 1 title.
  If axis1_title_side = <tt>"default"</tt>, wcslab will choose a side for the title.
  The permitted values are <tt>"default"</tt>, <tt>"right"</tt>, <tt>"left"</tt>, <tt>"top"</tt>, and
  <tt>"bottom"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>axis2_title_side = <tt>"default"</tt></b></dt>
  <!-- Sec='WLPARS PARAMETERS' Level=0 Label='axis2_title_side' Line='axis2_title_side = "default"' -->
  <dd>The side of the plot on which to place the axis 2 title.
  If axis2_title_side = <tt>"default"</tt>, wcslab will choose a side for the title.
  The permitted values are <tt>"default"</tt>, <tt>"right"</tt>, <tt>"left"</tt>, <tt>"top"</tt>, and
  <tt>"bottom"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>title_size = 1.0</b></dt>
  <!-- Sec='WLPARS PARAMETERS' Level=0 Label='title_size' Line='title_size = 1.0' -->
  <dd>The size of characters used to draw the title.
  </dd>
  </dl>
  <dl>
  <dt><b>axis_title_size = 1.0</b></dt>
  <!-- Sec='WLPARS PARAMETERS' Level=0 Label='axis_title_size' Line='axis_title_size = 1.0' -->
  <dd>The size of the characters used to draw the axis titles.
  </dd>
  </dl>
  <dl>
  <dt><b>graph_type = <tt>"default"</tt></b></dt>
  <!-- Sec='WLPARS PARAMETERS' Level=0 Label='graph_type' Line='graph_type = "default"' -->
  <dd>The type of graph to be drawn.  If graph_type = <tt>"default"</tt>, wcslab will
  choose an appropriate graph type.  The permitted values are <tt>"normal"</tt>, <tt>"polar"</tt>,
  and <tt>"near_polar"</tt>.
  </dd>
  </dl>
  <!-- EndSection:   'WLPARS PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  WCSLAB draws a labeled world coordinate grid on the graphics device
  <i>device</i> using world coordinate system (WCS)
  information stored in the header of the IRAF image <i>image</i> if
  <i>usewcs</i> is <tt>"no"</tt>, or
  in <i>wcspars</i> if <i>usewcs</i> is <tt>"yes"</tt> or <i>image</i> is <tt>""</tt>.
  WCSLAB currently supports the following coordinate system types 1)
  the tangent plane, sin, and arc sky projections in right ascension
  and declination and 2) any linear coordinate system.
  </p>
  <p>
  By default WCSLAB draws on the image display device, displacing
  the currently loaded image pixels with graphics pixels. Therefore in order
  to register the coordinate grid plot with the image, the image must
  loaded into the image display with the DISPLAY task, prior to
  running WCSLAB.
  </p>
  <p>
  If the viewport parameters <i>vl</i>, <i>vr</i>, <i>vb</i>, and
  <i>vt</i> are left undefined, WCSLAB will try to match the viewport
  of the coordinate grid plot with the viewport of the currently
  displayed image in the selected frame <i>frame</i>. 
  This scheme works well in the case where <i>image</i> is smaller
  than the display frame buffer, and in the case where <i>image</i> is
  actually a subsection of the image currently loaded into the display frame
  buffer.  In the case where <i>image</i>
  fills or overflows the image display frame buffer, WCSLAB 
  draws the appropriate coordinate grid but is not able to draw the
  titles and labels which would normally appear outside the plot.
  In this case the user must, either adjust the DISPLAY parameters
  <i>xmag</i>, and <i>ymag</i> so that the image will fit in the frame
  buffer,  or change the DISPLAY viewport parameters <i>xsize</i> and
  <i>ysize</i> so as to display only a fraction of the image.
  </p>
  <p>
  WCSLAB can create a new plot each time it is run, <i>append</i> = no
  and <i>overplot</i> = no,  add a new graph to an existing plot
  if <i>overplot</i> = yes and <i>append</i>=no,
  or append to an existing plot if <i>append</i> = yes. 
  For new or overplots WCSLAB computes the viewport and window, otherwise it
  uses the viewport and window of a previously existing plot. If <i>device</i>
  is <tt>"stdgraph"</tt>, then WCSLAB will clear the screen between each new plot.
  This is not possible if <i>device</i> is one of the <tt>"imd"</tt> devices
  since the image display graphics kernel writes directly into the display
  frame buffer. In this case the user must redisplay the image and rerun
  WCSLAB for each new plot.
  </p>
  <p>
  The parameters controlling the detailed appearance of the plot
  are contained in the parameter set specified by <i>wlpars</i>.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>The user-defined wcs</h3>
  <!-- BeginSection: 'THE USER-DEFINED WCS' -->
  <p>
  The parameters in WCSPARS are used to define the world
  coordinate system  only if,  1) the parameter <i>usewcs</i> is <tt>"yes"</tt>
  or, 2) the input image is undefined.
  This user-defined WCS specifies the transformation from the logical coordinate
  system, e.g.  pixel units, to a world system, e.g. ra and dec.
  </p>
  <p>
  Currently IRAF supports two types of world coordinate systems:
  1) linear, which provides a linear mapping from pixel units to
  the world coordinate system 2) and the sky projections which provide
  a mapping from pixel units to ra and dec.  The parameters
  <i>ctype1</i> and <i>ctype2</i> define which coordinate system will be in
  effect.  If a linear system is
  desired, both <i>ctype1</i> and <i>ctype2</i> must be <tt>"linear"</tt>.
  If the tangent plane sky projection is desired,
  and the first axis is ra and the
  second axis is dec, then <i>cypte1</i> and <i>ctype2</i>
  must be <tt>"ra---tan"</tt> and <tt>"dec--tan"</tt> respectively.
  To obtain the sin or arc projections <tt>"tan"</tt> is replaced with <tt>"sin"</tt> or
  <tt>"arc"</tt> respectively.
  </p>
  <p>
  The scale factor and rotation between the logical and world coordinate
  system is described by the CD matrix.  Using matrix
  multiplication, the logical coordinates are multiplied by the CD
  matrix to produce the world coordinates.  The CD matrix is represented in
  the parameters as follows:
  </p>
  <pre>
  
                  |---------------|
                  | cd1_1  cd1_2  |
                  |               |
                  | cd2_1  cd2_2  |
                  |---------------|
  
  </pre>
  <p>
  To construct a typical CD matrix, the following definitions of the
  individual matrix elements may be used:
  </p>
  <pre>
  
          cd1_1 =  xscale * cos (ROT)
          cd1_2 = -yscale * sin (ROT)
          cd2_1 =  xscale * sin (ROT)
          cd2_2 =  yscale * cos (ROT)
  
  </pre>
  <p>
  where xscale and yscale are the scale factors from the logical to world
  systems, e.g. degrees per pixel, and ROT is the angle of rotation between
  the two systems, where positive rotations are counter-clockwise.
  </p>
  <p>
  The ra/dec transformation is a special case.  Since by convention ra
  increases <tt>"to the left"</tt>, opposite of standard convention, the first axis
  transformation needs to be multiplied by -1.  This results in the
  following formulas: 
  </p>
  <pre>
  
          cd1_1 = -xscale * cos (ROT)
          cd1_2 =  yscale * sin (ROT)
          cd2_1 =  xscale * sin (ROT)
          cd2_2 =  yscale * cos (ROT)
  
  </pre>
  <p>
  Finally, the origins of the logical and world systems must be defined.
  The parameters <i>crpix1</i> and <i>crpix2</i> define the coordinate in
  the logical space that corresponds to the coordinate in world space
  defined by the parameters <i>crval1</i> and <i>crval2</i>. The coordinates
  (crpix1, crpix2) in logical space, when transformed to world space,
  become (crval1, crval2).
  </p>
  <p>
  The last set of parameters, log_x1, log_x2, log_y1, log_y2, define the
  region in the logical space, e.g. in pixels,  over which the transformation
  is valid.
  </p>
  <!-- EndSection:   'THE USER-DEFINED WCS' -->
  <h3>Axis specification</h3>
  <!-- BeginSection: 'AXIS SPECIFICATION' -->
  <p>
  For all <i>linear</i> transformations axis 1 and axis 2 specify which axis in
  the image is being referred to.
  For example in a 2-dimensional image, the FITS image header keywords
  CTYPE1, CRPIX1, CRVAL1, CDELT1,
  CD1_1, and CD1_2 define the world coordinate transformation for axis 1.
  Similarly the FITS image header keywords
  CTYPE2, CRPIX2, CRVAL2, CDELT2,
  CD2_1, CD2_2, define the world coordinate transformation for axis 2.
  </p>
  <p>
  THIS RULE DOES NOT APPLY TO THE TANGENT PLANE, SIN, and ARC SKY
  PROJECTION WCS'S.
  For this type of WCS axis 1 and axis 2 
  always refer to right ascension and declination respectively,
  and WCSLAB assumes that all axis 1 parameters refer to right
  ascension and all axis 2 parameters refer to declination, regardless of
  which axis in the image WCS actually specifies right ascension and declination.
  </p>
  <!-- EndSection:   'AXIS SPECIFICATION' -->
  <h3>Grid drawing </h3>
  <!-- BeginSection: 'GRID DRAWING ' -->
  <p>
  There are two types of grid lines / tick marks, <tt>"major"</tt> and
  <tt>"minor"</tt>.  The major grid lines / tick marks are the lines / ticks
  that will be labeled.  The minor grid lines / tick marks are plotted
  between the major marks.  Whether lines or tick marks are drawn is
  determined by the boolean parameters <i>major_grid</i> and <i>minor_grid</i>.
  If yes, lines are drawn; if no, tick marks are drawn.  How the lines
  appear is controlled by the parameters <i>major_line</i> and <i>minor_line</i>.
  </p>
  <p>
  The spacing of minor marks is controlled by the parameters <i>axis1_minor</i>
  and <i>axis2_minor</i>. These parameters specify the number of minor marks
  that will appear between the major marks along the axis 1
  and axis 2 axes.
  </p>
  <p>
  Spacing of major marks is more complicated.  WCSLAB tries to
  present major marks only along <tt>"significant values"</tt> in the
  coordinate system.  For example, if the graph spans several hours of
  right ascension,  the interval between major marks will in general be an
  hour and the major marks will appear at whole hours within the graph.
  If what WCSLAB chooses is unacceptable, the interval and range can
  be modified by the parameters <i>axis1_int</i>, <i>axis1_beg</i>,
  <i>axis1_end</i> for the axis 1, and <i>axis2_int</i>, <i>axis2_beg</i>,
  and <i>axis2_end</i> for axis 2. All three parameters must be specified for
  each axis in order for the new values to take affect
  </p>
  <!-- EndSection:   'GRID DRAWING ' -->
  <h3>Graph appearance</h3>
  <!-- BeginSection: 'GRAPH APPEARANCE' -->
  <p>
  WCSLAB supports three types of graph: normal, polar, and near_polar.
  </p>
  <p>
  A normal graph is the usual Cartesian graph where lines of constant
  axis 1 or 2 values cross at least two different sides of the graph.
  WCSLAB will by default plot a normal type graph for any image 1)
  which has no defined WCS 2) which has a linear WCS 3) where the sky
  projection WCS approximates a Cartesian system.
  </p>
  <p>
  A polar graph is one in which the north or south pole of the
  coordinate system actually appears on the graph.
  Lines of constant declination are no longer approximately
  straight lines, but are circles which may not intersect any
  of the edges of the graph. In this type of graph, axis 1 values
  are labeled all the way around the graph. 
  Axis 2 values are labeled within the graph
  next to each circle.  An attempt is made to label as many circles as
  possible.  However, if the WCSLAB's defaults are not agreeable,
  the parameters, <i>axis2_dir</i> and <i>justify</i>, can be modified
  to control how this labeling is done.
  <i>Axis2_dir</i> specifies along which axis 1 value the
  axis 2 labels should be written.  <i>Justify</i> specifies on which side of
  this value the label should appear.
  </p>
  <p>
  The near_polar graph is a cross between the normal graph and the polar
  graph.  In this case the pole is not on the graph, but is close enough
  to significantly affect the appearance of the plot.  The near_polar graph
  is handled like a polar graph.
  </p>
  <p>
  The parameter <i>graph_type</i> can be used to force WCSLAB
  to plot a graph of the type specified, although in this case it
  may be necessary to modify the values of other WLPARS parameters to
  obtain pleasing results. For example trying to plot a polar graph as
  Cartesian may producing a strange appearing graph.
  </p>
  <!-- EndSection:   'GRAPH APPEARANCE' -->
  <h3>Graph labeling</h3>
  <!-- BeginSection: 'GRAPH LABELING' -->
  <p>
  Due to the variety of graph types that can be plotted (see above), and
  the arbitrary rotation that any WCS can have, the task of labeling
  the major grid lines in a coherent and pleasing manner is not trivial.
  </p>
  <p>
  The basic model used is the Cartesian or normal graph.  Labels
  normally appear on the left and bottom edges of the graph with a side
  devoted solely to one of the WCS coordinate axis.  For example, right
  ascension might be labeled only along the bottom edge of the graph
  and declination only along the left edge, or vice versa. 
  </p>
  <p>
  If the defaults chosen by WCSLAB are unacceptable, the
  parameters <i>axis1_side</i> and <i>axis2_side</i>, can be used to specify which
  side (or sides) the labels for axis 1 and axis 2 will appear.
  Either a single side or a list of sides can be specified for either
  axis.  If a list is specified, labels will appear on each side listed,
  even if the same side appears in both of the parameters.  In this way,
  labels can be made to appear on the same side of the graph.
  </p>
  <!-- EndSection:   'GRAPH LABELING' -->
  <h3>Label appearance</h3>
  <!-- BeginSection: 'LABEL APPEARANCE' -->
  <p>
  Due to coordinate rotations, lines of constant axis 1 or axis 2 value
  may not intersect the edges
  of the graph perpendicularly.  To help clarify which line belongs to
  which label, the labels will be drawn at an angle equal to that of the
  line which is being labeled.  If this is not desired, 
  the parameter <i>rotate</i> may be set to no, and labels will always appear
  <tt>"normal"</tt>, i.e.  the text will not be rotated in any way.
  </p>
  <p>
  By default, all labels will be shortened to the smallest unit
  needed to indicate the value of the labeled line.  For example, if the
  graph spans about 30 seconds of declination, the interval between the
  labels will be approximately 5 or 10 seconds. The first label will contain the
  full specification, i.e. -22:32:20.  But the rest of the labels will
  only be the seconds, i.e. 30, 40, 50.  However, at the change in
  minutes, the full format would be used again, -22:33:00, but then
  again afterwards only seconds will be displayed, i.e. 10, 20, etc.
  If this shortening of labels is undesirable, it
  can be turned off by setting the parameter <i>full_label</i> to yes.  This
  forces every label to use the full specification.
  </p>
  <p>
  Finally, the parameter <i>label_size</i> can be used to adjust the size of the
  characters used in the axis labels.
  </p>
  <!-- EndSection:   'LABEL APPEARANCE' -->
  <h3>Titles</h3>
  <!-- BeginSection: 'TITLES' -->
  <p>
  A graph title may specified using the parameter <i>title</i>. If <i>title</i>
  = <tt>"imtitle"</tt> a default title constructed from the image name and title
  is used. The location and size of the graph title are controlled by
  the parameters <i>title_side</i> and <i>title_size</i>.
  Similarly the content, placement and size of the axis titles are
  controlled by the parameters <i>axis1_title</i>, <i>axis2_title</i>,
  <i>axis1_title_side</i>, <i>axis2_title_side</i>,  and
  <i>axis_title_size</i>.
  </p>
  <!-- EndSection:   'TITLES' -->
  <h3>Output formats</h3>
  <!-- BeginSection: 'OUTPUT FORMATS' -->
  <p>
  If <i>remember</i> = yes, the coordinates are output to the parameter set
  WLPARS in a form suitable for the type of system the coordinates
  represent.  For example right
  ascensions are output in HH:MM:SS (hours:minutes:seconds) and
  declinations are output in DD:MM:SS (degrees:minutes:seconds).
  If the input parameters are changed, for example axis1_int, their values
  must be input in the same format.
  If the WCS is linear, then the parameters will not be formatted in any special
  way; i.e. no assumptions are made about units, etc.
  </p>
  <!-- EndSection:   'OUTPUT FORMATS' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Display the 512 pixel square IRAF test image dev$pix in an 800 square
  display window and overlay it with a labeled coordinate grid.  Since
  dev$pix  does not have a defined WCS a pixel coordinate grid will appear.
  </p>
  <pre>
  	cl&gt; display  dev$pix 1
  
  	    ... display the image in frame 1
  
  	cl&gt; wcslab dev$pix 1
  
  	    ... the coordinate grid in green will be plotted on the display
  </pre>
  <p>
  2. Redisplay the previous image and by overlay the labeled
  coordinate grid on the inner 100 by 400 pixels in x and y.
  </p>
  <pre>
  	cl&gt; display dev$pix 1
  
  	    ... erase the graphics by redisplaying the image
  
  	cl&gt; wcslab dev$pix[100:400,100:400] 1
  </pre>
  <p>
  3. Display an 800 square image which has a defined linear WCS in an 800 square
  display window and overlay it with the coordinate grid. Reduce
  the display viewport in order to leave space around the edge of the
  displayed image for the labels and titles.
  </p>
  <pre>
  	cl&gt; display image 1 xsize=0.8 ysize=0.8 fill+
  	cl&gt; wcslab image 1 vl=.1 vr=.9 vb=.1 vt=.9
  </pre>
  <p>
  4. Repeat the previous example using a different combination of display
  and wcslab parameters to achieve the same goal.
  </p>
  <pre>
  	cl&gt; display image 1 xmag=0.8 ymag=0.8
  	cl&gt; wcslab image 1
  </pre>
  <p>
  5. Display a section of the previous image and overlay it with a
  coordinate grid. Note that the same section should be specified in
  both cases.
  </p>
  <pre>
  	cl&gt; display image[101:700,101:700] 1
  	cl&gt; wcslab image[101:700,101:700] 1
  </pre>
  <p>
  6. Display a 512 square image with a defined tangent plane sky projection
  in an 800 square frame buffer and overlay the labeled coordinate grid. The 
  standard FITS keywords shown below define the WCS. This WCS is
  approximately correct for the IRAF test image dev$pix.
  </p>
  <pre>
  	# IRAF image header keywords which define the WCS
  
  	CRPIX1  =               257.75
  	CRPIX2  =               258.93
  	CRVAL1  =      201.94541667302		# RA is stored in degrees !
  	CRVAL2  =             47.45444
  	CTYPE1  = 'RA---TAN'
  	CTYPE2  = 'DEC--TAN'
  	CDELT1  =        -2.1277777E-4
  	CDELT2  =         2.1277777E-4
  
  
  	cl&gt; display dev$pix 1
  
  	cl&gt; wcslab dev$pix 1
  </pre>
  <p>
  7. Display a  512 square image with a defined tangent plane sky projection
  approximately centered on the north celestial pole in an 800 square frame
  buffer. The FITS keywords shown below define the WCS.
  </p>
  <pre>
  	# IRAF image header keywords which define the WCS
  
  	CRPIX1  =               257.75
  	CRPIX2  =               258.93
  	CRVAL1  =      201.94541667302	    # RA is stored in degrees !
  	CRVAL2  =             90.00000
  	CTYPE1  = 'RA---TAN'
  	CTYPE2  = 'DEC--TAN'
  	CDELT1  =        -2.1277777E-4
  	CDELT2  =         2.1277777E-4
  
  	cl&gt; display northpole 1
  
  	cl&gt; wcslab northpole 1
  </pre>
  <p>
  8.  Display and label a 512 square image which has no WCS information
  using the values of the parameters in wcspars. The center pixel (256.0, 256.0)
  is located at (9h 22m 30.5s, -15o 05m 42s), the pixels are .10 
  arcseconds in size, and are rotated 30.0 degrees counter-clockwise.
  </p>
  <pre>
  
  	cl&gt; lpar wcspars
  
  	    ctype1 = 'ra---tan'
  	    ctype2 = 'dec--tan'
  	    crpix1 = 256.0
  	    crpix2 = 256.0
  	    crval1 = 140.62708
  	    crval2 = -15.09500
  	    cd1_1  = -2.405626e-5
  	    cd1_2  = 1.388889e-5
  	    cd2_1  = 1.388889e-5
  	    cd2_2  = 2.405626e-5
              log_x1 = 1.
              log_x2 = 512.
              log_y1 = 1.
              log_y2 = 512.
  
  	cl&gt; display image 1
  
  	cl&gt; wcslab image usewcs+
  
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Authors</h3>
  <!-- BeginSection: 'AUTHORS' -->
  <p>
  The WCSLAB task was written by members of the STScI SDAS programming group
  and integrated into the IRAF DISPLAY package by members of the IRAF
  programming group for version 2.10 IRAF.
  </p>
  <!-- EndSection:   'AUTHORS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  display, gcur, imdkern
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'WCSPARS PARAMETERS' 'WLPARS PARAMETERS' 'DESCRIPTION' 'THE USER-DEFINED WCS' 'AXIS SPECIFICATION' 'GRID DRAWING ' 'GRAPH APPEARANCE' 'GRAPH LABELING' 'LABEL APPEARANCE' 'TITLES' 'OUTPUT FORMATS' 'EXAMPLES' 'AUTHORS' 'SEE ALSO'  -->
  
