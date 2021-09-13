pcols — Plot the average of a range of image columns
====================================================

**Package: plot**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>pcols (Sep91)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>plot</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>pcols (Sep91)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>pcols</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  pcols -- plot average of image columns
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  prows image col1 col2
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_image">image</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD>Input image containing columns to be plotted.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_col1">col1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='col1' Line='col1'>
  <DD>First column to average.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_col2">col2</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='col2' Line='col2'>
  <DD>Last column to average.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_wcs">wcs = "<TT>logical</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wcs' Line='wcs = "logical"'>
  <DD>The world coordinate system (<I>wcs</I>) to be used for axis labeling when
  input is f rom images.
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
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_wx1">wx1=0., wx2=0., wy1=0., wy2=0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wx1' Line='wx1=0., wx2=0., wy1=0., wy2=0.'>
  <DD>The range of window (user) coordinates to be included in the plot.  If
  the range of values in x or y = 0, the plot is automatically scaled from
  the minimum to maximum data values along the degenerate axis.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_vx1">vx1=0., vx2=0., vy1=0., vy2=0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='vx1' Line='vx1=0., vx2=0., vy1=0., vy2=0.'>
  <DD>NDC coordinates (0-1) of the device plotting viewport.  If not set by the
  user, a suitable viewport which allows sufficient room for all labels
  is used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_pointmode">pointmode = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pointmode' Line='pointmode = no'>
  <DD>Plot individual points instead of a line?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_marker">marker = "<TT>box</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='marker' Line='marker = "box"'>
  <DD>Marker or line type to be drawn.  If <B>pointmode</B> = yes the markers are
  "<TT>point</TT>", "<TT>box</TT>", "<TT>cross</TT>", "<TT>plus</TT>", "<TT>circle</TT>", "<TT>hebar</TT>", "<TT>vebar</TT>", "<TT>hline</TT>",
  "<TT>vline</TT>" or "<TT>diamond</TT>".  Any other value defaults to "<TT>box</TT>".  If drawing lines,
  <B>pointmode</B> = no, the values are "<TT>line</TT>", "<TT>lhist</TT>", "<TT>bhist</TT>".  Any other
  value defaults to "<TT>line</TT>".  "<TT>bhist</TT>" (box histogram) draws lines to the
  bottom of the graph while "<TT>lhist</TT>" does not.  In both cases the
  horizontal histogram lines run between the half way points (reflected
  at the ends).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_szmarker">szmarker = 0.005</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='szmarker' Line='szmarker = 0.005'>
  <DD>The size of the marker drawn when <B>pointmode</B> = yes.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_logx">logx = no, logy = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logx' Line='logx = no, logy = no'>
  <DD>Draw the x or y axis in log units, versus linear?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xlabel">xlabel = "<TT>wcslabel</TT>", ylabel = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xlabel' Line='xlabel = "wcslabel", ylabel = ""'>
  <DD>Label for the X-axis or Y-axis.  if <B>xlabel</B> = "<TT>wcslabel</TT>"
  the world coordinate system label in the image, if defined, is used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xformat">xformat = "<TT>wcsformat</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xformat' Line='xformat = "wcsformat"'>
  <DD>The numerical format for the coordinate labels.  The values may be "<TT></TT>"
  (an empty string), %f for decimal format, %h and %H for xx:xx:xx format, and
  %m and %M for xx:xx.x format.  The upper case %H and %M convert degrees
  to hours.  Some images have a recommended x coordinate format defined as
  a WCS attribute.  If the xformat value is "<TT>wcsformat</TT>" the WCS attribute
  format will be used.  Any other value will override the image attribute.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_title">title = "<TT>imtitle</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='title' Line='title = "imtitle"'>
  <DD>Title for plot.  If not changed from the default, the title string from the
  image header, appended with the columns being plotted, is used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_majrx">majrx=5, minrx=5, majry=5, minry=5</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='majrx' Line='majrx=5, minrx=5, majry=5, minry=5'>
  <DD>The number of major and minor divisions along the x or y axis.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_round">round = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='round' Line='round = no'>
  <DD>Round axes up to nice values?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fill">fill = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fill' Line='fill = yes'>
  <DD>Fill plotting viewport regardless of device aspect ratio?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_append">append = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='append' Line='append = no'>
  <DD>Append to an existing plot?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_device">device="<TT>stdgraph</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='device' Line='device="stdgraph"'>
  <DD>Output device.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Plot the average of specified columns from an image.  The user can control the
  plot size and placement, the scaling and labeling of axes.  Columns can be
  plotted as a continuous line or individual points with a specified marker.
  <P>
  If <B>append</B> is enabled, previous values for <B>box</B>,
  <B>fill</B>, <B>round</B>, the plotting viewport (<B>vx1</B>, <B>vx2</B>, 
  <B>vy1</B>, <B>vy2</B>), and the plotting window (<B>wx1</B>, <B>wx2</B>, 
  <B>wy1</B>, <B>wy2</B>) are used.
  <P>
  If the plotting viewport was not set by the user, <B>pcols</B> 
  automatically sets a viewport centered on the device.  The default value
  of <B>fill</B> = yes means the plot spans equal amounts of NDC space in
  x and y.  Setting
  the value of <B>fill</B>  to "<TT>no</TT>" means the viewport will be adjusted so 
  that the square plot will span equal physical lengths in x and y
  when plotted.  That is, when <B>fill = no</B>, a unity aspect ratio is 
  enforced, and plots
  appear square regardless of the device aspect ratio.  On devices with non 
  square full device viewports (e.g., the vt640), a plot drawn by <I>pcols</I>
  appears extended in the x direction unless <B>fill</B> = no.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Plot columns 64 through 128 of image crab.5009 with default parameters:
  <P>
      cl&gt; pcols crab.5009 64 128
  <P>
  2. Overplot columns 64 through  128 of crab.red using boxes to mark the 
  added points:
  <P>
      cl&gt; pcols crab.red 64 128 append+ pointmode+
  <P>
  3. Annotate the axes of the plot:
  <P>
      cl&gt; pcols crab.5009 64 84 xlabel="<TT>Row Number</TT>" ylabel=Intensity
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_time_requirements">TIME REQUIREMENTS</A></H2>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  <B>pcols</B> takes about 3.25 cp seconds to plot the average of 20 columns
  from a 512 square image.
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  prow, prows, pcol
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>