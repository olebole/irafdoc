.. _wcslab:

wcslab — Overlay a displayed image with a world coordinate grid
===============================================================

**Package: tv**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  wcslab -- overlay a labeled world coordinate grid on an image
  <P>
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  wcslab image
  <P>
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <P>
  <DL>
  <DT><B>image </B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image '>
  <DD>The name of the image to be labeled. If image is "<TT></TT>", the parameters
  in wcspars will be used to draw a labeled coordinate grid.
  </DD>
  </DL>
  <DL>
  <DT><B>frame</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='frame' Line='frame'>
  <DD>The display frame buffer displaying the image to be labeled.
  </DD>
  </DL>
  <DL>
  <DT><B>usewcs = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='usewcs' Line='usewcs = no'>
  <DD>Use the world coordinate system specified by the parameters in the wcspars
  parameter set in place of the image world coordinate system  or if
  image is "<TT></TT>" ?
  </DD>
  </DL>
  <DL>
  <DT><B>wcspars = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wcspars' Line='wcspars = ""'>
  <DD>The name of the parameter set defining the world coordinate system
  to be used if image is "<TT></TT>" or if usewcs = "<TT>yes</TT>".  The wcspars parameters
  are described in more detail below.
  </DD>
  </DL>
  <DL>
  <DT><B>wlpars = "<TT></TT>" </B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wlpars' Line='wlpars = "" '>
  <DD>The name of the parameter set which controls the
  detailed appearance of the plot. The wlpars parameters are described
  in more detail below.
  </DD>
  </DL>
  <DL>
  <DT><B>fill = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fill' Line='fill = yes'>
  <DD>If fill is no, wcslab tries to
  create a square viewport with a maximum size dictated by the viewport
  parameters.  If fill is yes, then wcslab
  uses the viewport exactly as specified.
  </DD>
  </DL>
  <DL>
  <DT><B>vl = INDEF, vr = INDEF, vb = INDEF, vt = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='vl' Line='vl = INDEF, vr = INDEF, vb = INDEF, vt = INDEF'>
  <DD>The left, right, bottom, and top edges of the viewport in NDC (0-1)
  coordinates. If any of vl, vr, vb, or vt are  INDEF,
  wcslab computes a default value. To overlay the plot
  with a displayed image, vl, vr, vb, and vt must use the same viewport used
  by the display task to load the image into the frame buffer.
  </DD>
  </DL>
  <DL>
  <DT><B>overplot = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='overplot' Line='overplot = no'>
  <DD>Overplot to an existing plot?  If yes, wcslab will not erase the
  current plot.  This differs from append in that a new viewport
  may be defined.  Append has priority if both
  append and overwrite are yes.
  </DD>
  </DL>
  <DL>
  <DT><B>append = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='append' Line='append = no'>
  <DD>Append to an existing plot?  If no, wcslab resets the
  graphics to a new viewport/wcs for each new plot.  Otherwise, it uses
  the scaling from a previous plot. If append=yes but no plot was drawn, it
  will behave as if append=no.   This differs from overplot in that
  the same viewport is used.  Append has priority if both
  append and overwrite are yes.
  </DD>
  </DL>
  <DL>
  <DT><B>device = "<TT>imd</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='device' Line='device = "imd"'>
  <DD>The graphics device. To create an overlay plot, device must be set
  to one of the imdkern devices listed in dev$graphcap. To create a 
  plot of the coordinate grid in the
  graphics window, device should be set to "<TT>stdgraph</TT>".
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Wcspars parameters</H3>
  <! BeginSection: 'WCSPARS PARAMETERS'>
  <UL>
  <P>
  <DL>
  <DT><B>ctype1 = "<TT>linear</TT>", ctype2 = "<TT>linear</TT>"</B></DT>
  <! Sec='WCSPARS PARAMETERS' Level=0 Label='ctype1' Line='ctype1 = "linear", ctype2 = "linear"'>
  <DD>The coordinate system type of the first and second axes.
  Valid coordinate system types are:
  "<TT>linear</TT>", and "<TT>xxx--tan</TT>", "<TT>xxx-sin</TT>", and "<TT>xxx-arc</TT>", where "<TT>xxx</TT>" can be either
  "<TT>ra-</TT>" or "<TT>dec</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>crpix1 = 0.0, crpix2 = 0.0</B></DT>
  <! Sec='WCSPARS PARAMETERS' Level=0 Label='crpix1' Line='crpix1 = 0.0, crpix2 = 0.0'>
  <DD>The X and Y coordinates of the reference point in pixel space that
  correspond to the reference point in world space.
  </DD>
  </DL>
  <DL>
  <DT><B>crval1 = 0.0, crval2 = 0.0</B></DT>
  <! Sec='WCSPARS PARAMETERS' Level=0 Label='crval1' Line='crval1 = 0.0, crval2 = 0.0'>
  <DD>The X and Y coordinate of the reference point in world space that
  corresponds to the reference point in pixel space.
  </DD>
  </DL>
  <DL>
  <DT><B>cd1_1 = 1.0, cd1_2 = 0.0</B></DT>
  <! Sec='WCSPARS PARAMETERS' Level=0 Label='cd1_1' Line='cd1_1 = 1.0, cd1_2 = 0.0'>
  <DD>The FITS CD matrix elements [1,1] and [1,2] which describe the x-axis
  coordinate transformation.  These elements usually have the values
  &lt;xscale * cos (angle)&gt; and, &lt;-yscale * sin (angle)&gt;, or, for ra/dec systems
  &lt;-xscale * cos (angle)&gt; and &lt;yscale * sin (angle)&gt;.
  </DD>
  </DL>
  <DL>
  <DT><B>cd2_1 = 0.0, cd2_2 = 1.0</B></DT>
  <! Sec='WCSPARS PARAMETERS' Level=0 Label='cd2_1' Line='cd2_1 = 0.0, cd2_2 = 1.0'>
  <DD>The FITS CD matrix elements [2,1] and [2,2] which describe the y-axis
  coordinate transformation. These elements usually have the values
  &lt;xscale * sin (angle)&gt; and &lt;yscale * cos (angle)&gt;.
  </DD>
  </DL>
  <DL>
  <DT><B>log_x1 = 0.0, log_x2 = 1.0, log_y1 = 0.0, log_y2 = 1.0</B></DT>
  <! Sec='WCSPARS PARAMETERS' Level=0 Label='log_x1' Line='log_x1 = 0.0, log_x2 = 1.0, log_y1 = 0.0, log_y2 = 1.0'>
  <DD>The extent in pixel space over which the transformation is valid.
  </DD>
  </DL>
  <P>
  <P>
  </UL>
  <! EndSection:   'WCSPARS PARAMETERS'>
  <H3>Wlpars parameters</H3>
  <! BeginSection: 'WLPARS PARAMETERS'>
  <UL>
  <P>
  <DL>
  <DT><B>major_grid = yes</B></DT>
  <! Sec='WLPARS PARAMETERS' Level=0 Label='major_grid' Line='major_grid = yes'>
  <DD>Draw a grid instead of tick marks at the position of the major
  axes intervals?  If yes, lines of constant axis 1 and axis 2 values
  are drawn.  If no, tick marks are drawn instead.  Major grid
  lines / tick marks are labeled with the appropriate axis values.
  </DD>
  </DL>
  <DL>
  <DT><B>minor_grid = no</B></DT>
  <! Sec='WLPARS PARAMETERS' Level=0 Label='minor_grid' Line='minor_grid = no'>
  <DD>Draw a grid instead of tick marks at the position of the
  minor axes intervals?  If yes, lines of constant axis 1 and axis 2 values
  are drawn between the major grid lines / tick
  marks.  If no, tick marks are drawn instead. Minor grid lines / tick
  marks are not labeled.
  </DD>
  </DL>
  <DL>
  <DT><B>dolabel = yes</B></DT>
  <! Sec='WLPARS PARAMETERS' Level=0 Label='dolabel' Line='dolabel = yes'>
  <DD>Label the major grid lines or tick marks?
  </DD>
  </DL>
  <DL>
  <DT><B>remember = no</B></DT>
  <! Sec='WLPARS PARAMETERS' Level=0 Label='remember' Line='remember = no'>
  <DD>Modify the wlpars parameter file when done?  If yes, parameters that have
  been calculated by the task are written back to the parameter file.
  If no, the default, the parameter file is left untouched by the task.
  This option is useful for fine-tuning the appearance of the graph.
  </DD>
  </DL>
  <DL>
  <DT><B>axis1_beg = "<TT></TT>"</B></DT>
  <! Sec='WLPARS PARAMETERS' Level=0 Label='axis1_beg' Line='axis1_beg = ""'>
  <DD>The lowest value of axis 1 in world coordinates units
  at which a major grid line / tick mark will be drawn.
  If axis1_beg = "<TT></TT>", wcslab  will compute this quantity.
  Axis1_beg will be ignored if axis1_end and axis1_int are undefined.
  </DD>
  </DL>
  <DL>
  <DT><B>axis1_end = "<TT></TT>"</B></DT>
  <! Sec='WLPARS PARAMETERS' Level=0 Label='axis1_end' Line='axis1_end = ""'>
  <DD>The highest value of axis 1 in world coordinate
  units at which a major grid line / tick mark will be drawn.
  If axis1_end = "<TT></TT>", wcslab will compute this quantity.
  Axis1_end will be ignored if axis1_beg and axis1_int are undefined.
  </DD>
  </DL>
  <DL>
  <DT><B>axis1_int = "<TT></TT>"</B></DT>
  <! Sec='WLPARS PARAMETERS' Level=0 Label='axis1_int' Line='axis1_int = ""'>
  <DD>The interval in world coordinate units at which
  major grid lines / tick marks will be drawn along axis 1.
  If axis1_int = "<TT></TT>", wcslab will compute this quantity.
  Axis1_int will be ignored if axis1_beg and axis1_end are undefined.
  </DD>
  </DL>
  <DL>
  <DT><B>axis2_beg = "<TT></TT>"</B></DT>
  <! Sec='WLPARS PARAMETERS' Level=0 Label='axis2_beg' Line='axis2_beg = ""'>
  <DD>The lowest value of axis 2 in world coordinates units
  at which a major grid line / tick mark will be drawn.
  If axis2_beg = "<TT></TT>", wcslab  will compute this quantity.
  Axis2_beg will be ignored if axis2_end and axis2_int are undefined.
  </DD>
  </DL>
  <DL>
  <DT><B>axis2_end = "<TT></TT>"</B></DT>
  <! Sec='WLPARS PARAMETERS' Level=0 Label='axis2_end' Line='axis2_end = ""'>
  <DD>The highest value of axis 2 in world coordinate
  units at which a major grid line / tick mark will be drawn.
  If axis2_end = "<TT></TT>", wcslab will compute this quantity.
  Axis2_end will be ignored if axis2_beg and axis2_int are undefined.
  </DD>
  </DL>
  <DL>
  <DT><B>axis2_int = "<TT></TT>"</B></DT>
  <! Sec='WLPARS PARAMETERS' Level=0 Label='axis2_int' Line='axis2_int = ""'>
  <DD>The interval in world coordinate units at which
  major grid lines / tick marks will be drawn along axis 2.
  If axis2_int = "<TT></TT>", wcslab will compute this quantity.
  Axis2_int will be ignored if axis1_beg and axis1_end are undefined.
  </DD>
  </DL>
  <DL>
  <DT><B>major_line = "<TT>solid</TT>"</B></DT>
  <! Sec='WLPARS PARAMETERS' Level=0 Label='major_line' Line='major_line = "solid"'>
  <DD>The type of major grid lines to be plotted.
  The permitted values are "<TT>solid</TT>", "<TT>dotted</TT>", "<TT>dashed</TT>", and "<TT>dotdash</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>major_tick = .03</B></DT>
  <! Sec='WLPARS PARAMETERS' Level=0 Label='major_tick' Line='major_tick = .03'>
  <DD>Size of major tick marks relative to the size of the viewport.
  By default the major tick marks are .03 times the size of the
  viewport.
  </DD>
  </DL>
  <DL>
  <DT><B>axis1_minor = 5</B></DT>
  <! Sec='WLPARS PARAMETERS' Level=0 Label='axis1_minor' Line='axis1_minor = 5'>
  <DD>The number of minor grid lines / tick marks that will appear between major 
  grid lines / tick marks for axis 1.
  </DD>
  </DL>
  <DL>
  <DT><B>axis2_minor = 5</B></DT>
  <! Sec='WLPARS PARAMETERS' Level=0 Label='axis2_minor' Line='axis2_minor = 5'>
  <DD>The number of minor grid lines / tick marks that will appear between major
  grid lines / tick marks for axis 2.
  </DD>
  </DL>
  <DL>
  <DT><B>minor_line = "<TT>dotted</TT>"</B></DT>
  <! Sec='WLPARS PARAMETERS' Level=0 Label='minor_line' Line='minor_line = "dotted"'>
  <DD>The type of minor grid lines to be plotted.
  The permitted values are "<TT>solid</TT>", "<TT>dotted</TT>", "<TT>dashed</TT>", and "<TT>dotdash</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>minor_tick = .01</B></DT>
  <! Sec='WLPARS PARAMETERS' Level=0 Label='minor_tick' Line='minor_tick = .01'>
  <DD>Size of minor tick marks relative to the size of the viewport.
  BY default the minor tick marks are .01 times the size of the
  viewport.
  </DD>
  </DL>
  <DL>
  <DT><B>tick_in = yes</B></DT>
  <! Sec='WLPARS PARAMETERS' Level=0 Label='tick_in' Line='tick_in = yes'>
  <DD>Do tick marks point into instead of away from the graph ?
  </DD>
  </DL>
  <DL>
  <DT><B>axis1_side = "<TT>default</TT>"</B></DT>
  <! Sec='WLPARS PARAMETERS' Level=0 Label='axis1_side' Line='axis1_side = "default"'>
  <DD>The list of viewport edges, separated by commas, on which to place the axis
  1 labels.  If axis1_side is "<TT>default</TT>", wcslab will choose a side.
  Axis1_side may contain any combination of "<TT>left</TT>", "<TT>right</TT>",
  "<TT>bottom</TT>", "<TT>top</TT>", or "<TT>default</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>axis2_side = "<TT>default</TT>"</B></DT>
  <! Sec='WLPARS PARAMETERS' Level=0 Label='axis2_side' Line='axis2_side = "default"'>
  <DD>The list of viewport edges, separated by commas, on which to place the axis
  2 labels.  If axis2_side is "<TT>default</TT>", wcslab will choose a side.
  Axis2_side may contain any combination of "<TT>left</TT>", "<TT>right</TT>",
  "<TT>bottom</TT>", "<TT>top</TT>", or "<TT>default</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>axis2_dir = "<TT></TT>"</B></DT>
  <! Sec='WLPARS PARAMETERS' Level=0 Label='axis2_dir' Line='axis2_dir = ""'>
  <DD>The axis 1 value at which the axis 2 labels will be written for polar graphs. 
  If axis2_dir is "<TT></TT>", wcslab will compute this number.
  </DD>
  </DL>
  <DL>
  <DT><B>justify = "<TT>default</TT>"</B></DT>
  <! Sec='WLPARS PARAMETERS' Level=0 Label='justify' Line='justify = "default"'>
  <DD>The direction with respect to axis 2 along which the axis 2
  labels will be drawn from the point they are labeling on polar graphs.
  If justify = "<TT></TT>", then wcslab will calculate this quantity.  The permitted
  values are "<TT>default</TT>", "<TT>left</TT>", "<TT>right</TT>", "<TT>top</TT>", and "<TT>bottom</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>labout = yes</B></DT>
  <! Sec='WLPARS PARAMETERS' Level=0 Label='labout' Line='labout = yes'>
  <DD>Draw the labels outside the axes ?  If yes, the labels will be drawn
  outside the image viewport.  Otherwise, the axes labels will be drawn inside
  the image border.  The latter option is useful if the image fills the
  display frame buffer.
  </DD>
  </DL>
  <DL>
  <DT><B>full_label = no</B></DT>
  <! Sec='WLPARS PARAMETERS' Level=0 Label='full_label' Line='full_label = no'>
  <DD>Always draw all the labels in full format (h:m:s or d:m:s) if the world
  coordinate system of the image is in RA and DEC ?  If full_label = no, then
  only certain axes will be labeled in full format. The remainder will
  be labeled in minutes or seconds as appropriate.
  </DD>
  </DL>
  <DL>
  <DT><B>rotate = yes</B></DT>
  <! Sec='WLPARS PARAMETERS' Level=0 Label='rotate' Line='rotate = yes'>
  <DD>Permit the labels to rotate ?
  If rotate = yes, then labels will be written
  at an angle to match that of the major grid lines that are being
  labeled.  If rotate = no, then labels are always written
  "<TT>normally</TT>", that is horizontally. If labout = no, then rotate is
  set to "<TT>no</TT>" by default.
  </DD>
  </DL>
  <DL>
  <DT><B>label_size = 1.0</B></DT>
  <! Sec='WLPARS PARAMETERS' Level=0 Label='label_size' Line='label_size = 1.0'>
  <DD>The size of the characters used to draw the major grid line labels.
  </DD>
  </DL>
  <DL>
  <DT><B>title = "<TT>imtitle</TT>"</B></DT>
  <! Sec='WLPARS PARAMETERS' Level=0 Label='title' Line='title = "imtitle"'>
  <DD>The graph title. If title = "<TT>imtitle</TT>", then a default title containing
  the image name and title is created.
  </DD>
  </DL>
  <DL>
  <DT><B>axis1_title = "<TT></TT>"</B></DT>
  <! Sec='WLPARS PARAMETERS' Level=0 Label='axis1_title' Line='axis1_title = ""'>
  <DD>The title for axis 1. By default no axis title is drawn.
  </DD>
  </DL>
  <DL>
  <DT><B>axis2_title = "<TT></TT>"</B></DT>
  <! Sec='WLPARS PARAMETERS' Level=0 Label='axis2_title' Line='axis2_title = ""'>
  <DD>The title for axis 2. By default no axis title is drawn.
  </DD>
  </DL>
  <DL>
  <DT><B>title_side = "<TT>top</TT>"</B></DT>
  <! Sec='WLPARS PARAMETERS' Level=0 Label='title_side' Line='title_side = "top"'>
  <DD>The side of the plot on which to place the title.
  The options are "<TT>left</TT>", "<TT>right</TT>", "<TT>bottom</TT>", and "<TT>top</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>axis1_title_side = "<TT>default</TT>"</B></DT>
  <! Sec='WLPARS PARAMETERS' Level=0 Label='axis1_title_side' Line='axis1_title_side = "default"'>
  <DD>The side of the plot on which to place the axis 1 title.
  If axis1_title_side = "<TT>default</TT>", wcslab will choose a side for the title.
  The permitted values are "<TT>default</TT>", "<TT>right</TT>", "<TT>left</TT>", "<TT>top</TT>", and
  "<TT>bottom</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>axis2_title_side = "<TT>default</TT>"</B></DT>
  <! Sec='WLPARS PARAMETERS' Level=0 Label='axis2_title_side' Line='axis2_title_side = "default"'>
  <DD>The side of the plot on which to place the axis 2 title.
  If axis2_title_side = "<TT>default</TT>", wcslab will choose a side for the title.
  The permitted values are "<TT>default</TT>", "<TT>right</TT>", "<TT>left</TT>", "<TT>top</TT>", and
  "<TT>bottom</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>title_size = 1.0</B></DT>
  <! Sec='WLPARS PARAMETERS' Level=0 Label='title_size' Line='title_size = 1.0'>
  <DD>The size of characters used to draw the title.
  </DD>
  </DL>
  <DL>
  <DT><B>axis_title_size = 1.0</B></DT>
  <! Sec='WLPARS PARAMETERS' Level=0 Label='axis_title_size' Line='axis_title_size = 1.0'>
  <DD>The size of the characters used to draw the axis titles.
  </DD>
  </DL>
  <DL>
  <DT><B>graph_type = "<TT>default</TT>"</B></DT>
  <! Sec='WLPARS PARAMETERS' Level=0 Label='graph_type' Line='graph_type = "default"'>
  <DD>The type of graph to be drawn.  If graph_type = "<TT>default</TT>", wcslab will
  choose an appropriate graph type.  The permitted values are "<TT>normal</TT>", "<TT>polar</TT>",
  and "<TT>near_polar</TT>".
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'WLPARS PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  WCSLAB draws a labeled world coordinate grid on the graphics device
  <I>device</I> using world coordinate system (WCS)
  information stored in the header of the IRAF image <I>image</I> if
  <I>usewcs</I> is "<TT>no</TT>", or
  in <I>wcspars</I> if <I>usewcs</I> is "<TT>yes</TT>" or <I>image</I> is "<TT></TT>".
  WCSLAB currently supports the following coordinate system types 1)
  the tangent plane, sin, and arc sky projections in right ascension
  and declination and 2) any linear coordinate system.
  <P>
  By default WCSLAB draws on the image display device, displacing
  the currently loaded image pixels with graphics pixels. Therefore in order
  to register the coordinate grid plot with the image, the image must
  loaded into the image display with the DISPLAY task, prior to
  running WCSLAB.
  <P>
  If the viewport parameters <I>vl</I>, <I>vr</I>, <I>vb</I>, and
  <I>vt</I> are left undefined, WCSLAB will try to match the viewport
  of the coordinate grid plot with the viewport of the currently
  displayed image in the selected frame <I>frame</I>. 
  This scheme works well in the case where <I>image</I> is smaller
  than the display frame buffer, and in the case where <I>image</I> is
  actually a subsection of the image currently loaded into the display frame
  buffer.  In the case where <I>image</I>
  fills or overflows the image display frame buffer, WCSLAB 
  draws the appropriate coordinate grid but is not able to draw the
  titles and labels which would normally appear outside the plot.
  In this case the user must, either adjust the DISPLAY parameters
  <I>xmag</I>, and <I>ymag</I> so that the image will fit in the frame
  buffer,  or change the DISPLAY viewport parameters <I>xsize</I> and
  <I>ysize</I> so as to display only a fraction of the image.
  <P>
  WCSLAB can create a new plot each time it is run, <I>append</I> = no
  and <I>overplot</I> = no,  add a new graph to an existing plot
  if <I>overplot</I> = yes and <I>append</I>=no,
  or append to an existing plot if <I>append</I> = yes. 
  For new or overplots WCSLAB computes the viewport and window, otherwise it
  uses the viewport and window of a previously existing plot. If <I>device</I>
  is "<TT>stdgraph</TT>", then WCSLAB will clear the screen between each new plot.
  This is not possible if <I>device</I> is one of the "<TT>imd</TT>" devices
  since the image display graphics kernel writes directly into the display
  frame buffer. In this case the user must redisplay the image and rerun
  WCSLAB for each new plot.
  <P>
  The parameters controlling the detailed appearance of the plot
  are contained in the parameter set specified by <I>wlpars</I>.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>The user-defined wcs</H3>
  <! BeginSection: 'THE USER-DEFINED WCS'>
  <UL>
  <P>
  The parameters in WCSPARS are used to define the world
  coordinate system  only if,  1) the parameter <I>usewcs</I> is "<TT>yes</TT>"
  or, 2) the input image is undefined.
  This user-defined WCS specifies the transformation from the logical coordinate
  system, e.g.  pixel units, to a world system, e.g. ra and dec.
  <P>
  Currently IRAF supports two types of world coordinate systems:
  1) linear, which provides a linear mapping from pixel units to
  the world coordinate system 2) and the sky projections which provide
  a mapping from pixel units to ra and dec.  The parameters
  <I>ctype1</I> and <I>ctype2</I> define which coordinate system will be in
  effect.  If a linear system is
  desired, both <I>ctype1</I> and <I>ctype2</I> must be "<TT>linear</TT>".
  If the tangent plane sky projection is desired,
  and the first axis is ra and the
  second axis is dec, then <I>cypte1</I> and <I>ctype2</I>
  must be "<TT>ra---tan</TT>" and "<TT>dec--tan</TT>" respectively.
  To obtain the sin or arc projections "<TT>tan</TT>" is replaced with "<TT>sin</TT>" or
  "<TT>arc</TT>" respectively.
  <P>
  The scale factor and rotation between the logical and world coordinate
  system is described by the CD matrix.  Using matrix
  multiplication, the logical coordinates are multiplied by the CD
  matrix to produce the world coordinates.  The CD matrix is represented in
  the parameters as follows:
  <P>
  <PRE>
  <P>
                  |---------------|
                  | cd1_1  cd1_2  |
                  |               |
                  | cd2_1  cd2_2  |
                  |---------------|
  <P>
  </PRE>
  <P>
  To construct a typical CD matrix, the following definitions of the
  individual matrix elements may be used:
  <P>
  <PRE>
  <P>
          cd1_1 =  xscale * cos (ROT)
          cd1_2 = -yscale * sin (ROT)
          cd2_1 =  xscale * sin (ROT)
          cd2_2 =  yscale * cos (ROT)
  <P>
  </PRE>
  <P>
  where xscale and yscale are the scale factors from the logical to world
  systems, e.g. degrees per pixel, and ROT is the angle of rotation between
  the two systems, where positive rotations are counter-clockwise.
  <P>
  The ra/dec transformation is a special case.  Since by convention ra
  increases "<TT>to the left</TT>", opposite of standard convention, the first axis
  transformation needs to be multiplied by -1.  This results in the
  following formulas: 
  <P>
  <PRE>
  <P>
          cd1_1 = -xscale * cos (ROT)
          cd1_2 =  yscale * sin (ROT)
          cd2_1 =  xscale * sin (ROT)
          cd2_2 =  yscale * cos (ROT)
  <P>
  </PRE>
  <P>
  Finally, the origins of the logical and world systems must be defined.
  The parameters <I>crpix1</I> and <I>crpix2</I> define the coordinate in
  the logical space that corresponds to the coordinate in world space
  defined by the parameters <I>crval1</I> and <I>crval2</I>. The coordinates
  (crpix1, crpix2) in logical space, when transformed to world space,
  become (crval1, crval2).
  <P>
  The last set of parameters, log_x1, log_x2, log_y1, log_y2, define the
  region in the logical space, e.g. in pixels,  over which the transformation
  is valid.
  <P>
  </UL>
  <! EndSection:   'THE USER-DEFINED WCS'>
  <H3>Axis specification</H3>
  <! BeginSection: 'AXIS SPECIFICATION'>
  <UL>
  <P>
  For all <I>linear</I> transformations axis 1 and axis 2 specify which axis in
  the image is being referred to.
  For example in a 2-dimensional image, the FITS image header keywords
  CTYPE1, CRPIX1, CRVAL1, CDELT1,
  CD1_1, and CD1_2 define the world coordinate transformation for axis 1.
  Similarly the FITS image header keywords
  CTYPE2, CRPIX2, CRVAL2, CDELT2,
  CD2_1, CD2_2, define the world coordinate transformation for axis 2.
  <P>
  THIS RULE DOES NOT APPLY TO THE TANGENT PLANE, SIN, and ARC SKY
  PROJECTION WCS'S.
  For this type of WCS axis 1 and axis 2 
  always refer to right ascension and declination respectively,
  and WCSLAB assumes that all axis 1 parameters refer to right
  ascension and all axis 2 parameters refer to declination, regardless of
  which axis in the image WCS actually specifies right ascension and declination.
  <P>
  </UL>
  <! EndSection:   'AXIS SPECIFICATION'>
  <H3>Grid drawing </H3>
  <! BeginSection: 'GRID DRAWING '>
  <UL>
  <P>
  There are two types of grid lines / tick marks, "<TT>major</TT>" and
  "<TT>minor</TT>".  The major grid lines / tick marks are the lines / ticks
  that will be labeled.  The minor grid lines / tick marks are plotted
  between the major marks.  Whether lines or tick marks are drawn is
  determined by the boolean parameters <I>major_grid</I> and <I>minor_grid</I>.
  If yes, lines are drawn; if no, tick marks are drawn.  How the lines
  appear is controlled by the parameters <I>major_line</I> and <I>minor_line</I>.
  <P>
  The spacing of minor marks is controlled by the parameters <I>axis1_minor</I>
  and <I>axis2_minor</I>. These parameters specify the number of minor marks
  that will appear between the major marks along the axis 1
  and axis 2 axes.
  <P>
  Spacing of major marks is more complicated.  WCSLAB tries to
  present major marks only along "<TT>significant values</TT>" in the
  coordinate system.  For example, if the graph spans several hours of
  right ascension,  the interval between major marks will in general be an
  hour and the major marks will appear at whole hours within the graph.
  If what WCSLAB chooses is unacceptable, the interval and range can
  be modified by the parameters <I>axis1_int</I>, <I>axis1_beg</I>,
  <I>axis1_end</I> for the axis 1, and <I>axis2_int</I>, <I>axis2_beg</I>,
  and <I>axis2_end</I> for axis 2. All three parameters must be specified for
  each axis in order for the new values to take affect
  <P>
  </UL>
  <! EndSection:   'GRID DRAWING '>
  <H3>Graph appearance</H3>
  <! BeginSection: 'GRAPH APPEARANCE'>
  <UL>
  <P>
  WCSLAB supports three types of graph: normal, polar, and near_polar.
  <P>
  A normal graph is the usual Cartesian graph where lines of constant
  axis 1 or 2 values cross at least two different sides of the graph.
  WCSLAB will by default plot a normal type graph for any image 1)
  which has no defined WCS 2) which has a linear WCS 3) where the sky
  projection WCS approximates a Cartesian system.
  <P>
  A polar graph is one in which the north or south pole of the
  coordinate system actually appears on the graph.
  Lines of constant declination are no longer approximately
  straight lines, but are circles which may not intersect any
  of the edges of the graph. In this type of graph, axis 1 values
  are labeled all the way around the graph. 
  Axis 2 values are labeled within the graph
  next to each circle.  An attempt is made to label as many circles as
  possible.  However, if the WCSLAB's defaults are not agreeable,
  the parameters, <I>axis2_dir</I> and <I>justify</I>, can be modified
  to control how this labeling is done.
  <I>Axis2_dir</I> specifies along which axis 1 value the
  axis 2 labels should be written.  <I>Justify</I> specifies on which side of
  this value the label should appear.
  <P>
  The near_polar graph is a cross between the normal graph and the polar
  graph.  In this case the pole is not on the graph, but is close enough
  to significantly affect the appearance of the plot.  The near_polar graph
  is handled like a polar graph.
  <P>
  The parameter <I>graph_type</I> can be used to force WCSLAB
  to plot a graph of the type specified, although in this case it
  may be necessary to modify the values of other WLPARS parameters to
  obtain pleasing results. For example trying to plot a polar graph as
  Cartesian may producing a strange appearing graph.
  <P>
  </UL>
  <! EndSection:   'GRAPH APPEARANCE'>
  <H3>Graph labeling</H3>
  <! BeginSection: 'GRAPH LABELING'>
  <UL>
  <P>
  Due to the variety of graph types that can be plotted (see above), and
  the arbitrary rotation that any WCS can have, the task of labeling
  the major grid lines in a coherent and pleasing manner is not trivial.
  <P>
  The basic model used is the Cartesian or normal graph.  Labels
  normally appear on the left and bottom edges of the graph with a side
  devoted solely to one of the WCS coordinate axis.  For example, right
  ascension might be labeled only along the bottom edge of the graph
  and declination only along the left edge, or vice versa. 
  <P>
  If the defaults chosen by WCSLAB are unacceptable, the
  parameters <I>axis1_side</I> and <I>axis2_side</I>, can be used to specify which
  side (or sides) the labels for axis 1 and axis 2 will appear.
  Either a single side or a list of sides can be specified for either
  axis.  If a list is specified, labels will appear on each side listed,
  even if the same side appears in both of the parameters.  In this way,
  labels can be made to appear on the same side of the graph.
  <P>
  </UL>
  <! EndSection:   'GRAPH LABELING'>
  <H3>Label appearance</H3>
  <! BeginSection: 'LABEL APPEARANCE'>
  <UL>
  <P>
  Due to coordinate rotations, lines of constant axis 1 or axis 2 value
  may not intersect the edges
  of the graph perpendicularly.  To help clarify which line belongs to
  which label, the labels will be drawn at an angle equal to that of the
  line which is being labeled.  If this is not desired, 
  the parameter <I>rotate</I> may be set to no, and labels will always appear
  "<TT>normal</TT>", i.e.  the text will not be rotated in any way.
  <P>
  By default, all labels will be shortened to the smallest unit
  needed to indicate the value of the labeled line.  For example, if the
  graph spans about 30 seconds of declination, the interval between the
  labels will be approximately 5 or 10 seconds. The first label will contain the
  full specification, i.e. -22:32:20.  But the rest of the labels will
  only be the seconds, i.e. 30, 40, 50.  However, at the change in
  minutes, the full format would be used again, -22:33:00, but then
  again afterwards only seconds will be displayed, i.e. 10, 20, etc.
  If this shortening of labels is undesirable, it
  can be turned off by setting the parameter <I>full_label</I> to yes.  This
  forces every label to use the full specification.
  <P>
  Finally, the parameter <I>label_size</I> can be used to adjust the size of the
  characters used in the axis labels.
  <P>
  </UL>
  <! EndSection:   'LABEL APPEARANCE'>
  <H3>Titles</H3>
  <! BeginSection: 'TITLES'>
  <UL>
  <P>
  A graph title may specified using the parameter <I>title</I>. If <I>title</I>
  = "<TT>imtitle</TT>" a default title constructed from the image name and title
  is used. The location and size of the graph title are controlled by
  the parameters <I>title_side</I> and <I>title_size</I>.
  Similarly the content, placement and size of the axis titles are
  controlled by the parameters <I>axis1_title</I>, <I>axis2_title</I>,
  <I>axis1_title_side</I>, <I>axis2_title_side</I>,  and
  <I>axis_title_size</I>.
  <P>
  </UL>
  <! EndSection:   'TITLES'>
  <H3>Output formats</H3>
  <! BeginSection: 'OUTPUT FORMATS'>
  <UL>
  <P>
  If <I>remember</I> = yes, the coordinates are output to the parameter set
  WLPARS in a form suitable for the type of system the coordinates
  represent.  For example right
  ascensions are output in HH:MM:SS (hours:minutes:seconds) and
  declinations are output in DD:MM:SS (degrees:minutes:seconds).
  If the input parameters are changed, for example axis1_int, their values
  must be input in the same format.
  If the WCS is linear, then the parameters will not be formatted in any special
  way; i.e. no assumptions are made about units, etc.
  <P>
  </UL>
  <! EndSection:   'OUTPUT FORMATS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Display the 512 pixel square IRAF test image dev$pix in an 800 square
  display window and overlay it with a labeled coordinate grid.  Since
  dev$pix  does not have a defined WCS a pixel coordinate grid will appear.
  <P>
  <PRE>
  	cl&gt; display  dev$pix 1
  <P>
  	    ... display the image in frame 1
  <P>
  	cl&gt; wcslab dev$pix 1
  <P>
  	    ... the coordinate grid in green will be plotted on the display
  </PRE>
  <P>
  2. Redisplay the previous image and by overlay the labeled
  coordinate grid on the inner 100 by 400 pixels in x and y.
  <P>
  <PRE>
  	cl&gt; display dev$pix 1
  <P>
  	    ... erase the graphics by redisplaying the image
  <P>
  	cl&gt; wcslab dev$pix[100:400,100:400] 1
  </PRE>
  <P>
  3. Display an 800 square image which has a defined linear WCS in an 800 square
  display window and overlay it with the coordinate grid. Reduce
  the display viewport in order to leave space around the edge of the
  displayed image for the labels and titles.
  <P>
  <PRE>
  	cl&gt; display image 1 xsize=0.8 ysize=0.8 fill+
  	cl&gt; wcslab image 1 vl=.1 vr=.9 vb=.1 vt=.9
  </PRE>
  <P>
  4. Repeat the previous example using a different combination of display
  and wcslab parameters to achieve the same goal.
  <P>
  <PRE>
  	cl&gt; display image 1 xmag=0.8 ymag=0.8
  	cl&gt; wcslab image 1
  </PRE>
  <P>
  5. Display a section of the previous image and overlay it with a
  coordinate grid. Note that the same section should be specified in
  both cases.
  <P>
  <PRE>
  	cl&gt; display image[101:700,101:700] 1
  	cl&gt; wcslab image[101:700,101:700] 1
  </PRE>
  <P>
  6. Display a 512 square image with a defined tangent plane sky projection
  in an 800 square frame buffer and overlay the labeled coordinate grid. The 
  standard FITS keywords shown below define the WCS. This WCS is
  approximately correct for the IRAF test image dev$pix.
  <P>
  <PRE>
  	# IRAF image header keywords which define the WCS
  <P>
  	CRPIX1  =               257.75
  	CRPIX2  =               258.93
  	CRVAL1  =      201.94541667302		# RA is stored in degrees !
  	CRVAL2  =             47.45444
  	CTYPE1  = 'RA---TAN'
  	CTYPE2  = 'DEC--TAN'
  	CDELT1  =        -2.1277777E-4
  	CDELT2  =         2.1277777E-4
  <P>
  <P>
  	cl&gt; display dev$pix 1
  <P>
  	cl&gt; wcslab dev$pix 1
  </PRE>
  <P>
  7. Display a  512 square image with a defined tangent plane sky projection
  approximately centered on the north celestial pole in an 800 square frame
  buffer. The FITS keywords shown below define the WCS.
  <P>
  <P>
  <PRE>
  	# IRAF image header keywords which define the WCS
  <P>
  	CRPIX1  =               257.75
  	CRPIX2  =               258.93
  	CRVAL1  =      201.94541667302	    # RA is stored in degrees !
  	CRVAL2  =             90.00000
  	CTYPE1  = 'RA---TAN'
  	CTYPE2  = 'DEC--TAN'
  	CDELT1  =        -2.1277777E-4
  	CDELT2  =         2.1277777E-4
  <P>
  	cl&gt; display northpole 1
  <P>
  	cl&gt; wcslab northpole 1
  </PRE>
  <P>
  8.  Display and label a 512 square image which has no WCS information
  using the values of the parameters in wcspars. The center pixel (256.0, 256.0)
  is located at (9h 22m 30.5s, -15o 05m 42s), the pixels are .10 
  arcseconds in size, and are rotated 30.0 degrees counter-clockwise.
  <P>
  <PRE>
  <P>
  	cl&gt; lpar wcspars
  <P>
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
  <P>
  	cl&gt; display image 1
  <P>
  	cl&gt; wcslab image usewcs+
  <P>
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Authors</H3>
  <! BeginSection: 'AUTHORS'>
  <UL>
  The WCSLAB task was written by members of the STScI SDAS programming group
  and integrated into the IRAF DISPLAY package by members of the IRAF
  programming group for version 2.10 IRAF.
  </UL>
  <! EndSection:   'AUTHORS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  display, gcur, imdkern
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'WCSPARS PARAMETERS' 'WLPARS PARAMETERS' 'DESCRIPTION' 'THE USER-DEFINED WCS' 'AXIS SPECIFICATION' 'GRID DRAWING ' 'GRAPH APPEARANCE' 'GRAPH LABELING' 'LABEL APPEARANCE' 'TITLES' 'OUTPUT FORMATS' 'EXAMPLES' 'AUTHORS' 'SEE ALSO'  >
  
