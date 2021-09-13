.. _prows:

prows — Plot the average of a range of image lines
==================================================

**Package: plot**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  prows -- plot average of image rows
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  prows image row1 row2
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>image</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD>Input image containing rows to be plotted.
  </DD>
  </DL>
  <DL>
  <DT><B>row1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='row1' Line='row1'>
  <DD>First row to average.
  </DD>
  </DL>
  <DL>
  <DT><B>row2</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='row2' Line='row2'>
  <DD>Last row to average.
  </DD>
  </DL>
  <DL>
  <DT><B>wcs = "<TT>logical</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wcs' Line='wcs = "logical"'>
  <DD>The world coordinate system (<I>wcs</I>) to be used for axis labeling when
  input is f rom images.
  The following standard world systems are predefined.
  <DL>
  <DT><B>logical</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='logical' Line='logical'>
  <DD>Logical coordinates are image pixel coordinates relative to the image currently
  being displayed.
  </DD>
  </DL>
  <DL>
  <DT><B>physical</B></DT>
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
  <DT><B>world</B></DT>
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
  <DT><B>wx1=0., wx2=0., wy1=0., wy2=0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wx1' Line='wx1=0., wx2=0., wy1=0., wy2=0.'>
  <DD>The range of window (user) coordinates to be included in the plot.
  If the range of values in x or y = 0, the plot is automatically scaled
  from the minimum to maximum data values along the degenerate axis.
  </DD>
  </DL>
  <DL>
  <DT><B>vx1=0., vx2=0., vy1=0., vy2=0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='vx1' Line='vx1=0., vx2=0., vy1=0., vy2=0.'>
  <DD>NDC coordinates (0-1) of the plotting device viewport.  If not set
  by the user, a suitable viewport which allows sufficient room for all
  labels is used.
  </DD>
  </DL>
  <DL>
  <DT><B>pointmode = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pointmode' Line='pointmode = no'>
  <DD>Plot individual points instead of a continuous line?
  </DD>
  </DL>
  <DL>
  <DT><B>marker = "<TT>box</TT>"</B></DT>
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
  <DT><B>szmarker = 0.005</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='szmarker' Line='szmarker = 0.005'>
  <DD>The size of the marker drawn when <B>pointmode</B> = yes.
  </DD>
  </DL>
  <DL>
  <DT><B>logx = no, logy = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logx' Line='logx = no, logy = no'>
  <DD>Draw the x or y axis in log units, versus linear?
  </DD>
  </DL>
  <DL>
  <DT><B>xlabel = "<TT>wcslabel</TT>", ylabel = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xlabel' Line='xlabel = "wcslabel", ylabel = ""'>
  <DD>Label for the X-axis or Y-axis.  if <B>xlabel</B> = "<TT>wcslabel</TT>"
  the world coordinate system label in the image, if defined, is used.
  </DD>
  </DL>
  <DL>
  <DT><B>xformat = "<TT>wcsformat</TT>"</B></DT>
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
  <DT><B>title = "<TT>imtitle</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='title' Line='title = "imtitle"'>
  <DD>Title for plot.  If not changed from the default, the title string from the
  image header, appended with the rows being plotted, is used.
  </DD>
  </DL>
  <DL>
  <DT><B>majrx=5, minrx=5, majry=5, minry=5</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='majrx' Line='majrx=5, minrx=5, majry=5, minry=5'>
  <DD>The number of major and minor divisions along the x or y axis.
  </DD>
  </DL>
  <DL>
  <DT><B>round = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='round' Line='round = no'>
  <DD>Round axes up to nice values?
  </DD>
  </DL>
  <DL>
  <DT><B>fill = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fill' Line='fill = yes'>
  <DD>Fill the plotting viewport regardless of the device aspect ratio?
  </DD>
  </DL>
  <DL>
  <DT><B>append = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='append' Line='append = no'>
  <DD>Append to an existing plot?
  </DD>
  </DL>
  <DL>
  <DT><B>device="<TT>stdgraph</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='device' Line='device="stdgraph"'>
  <DD>Output device.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Plot the average of specified rows from an image.  The user can control the
  plot size and placement, the scaling and labeling of axes.  Rows can be
  plotted as a continuous line or individual points with a specified marker.
  <P>
  If <B>append</B> is enabled, previous values for <B>box</B>,
  <B>fill</B>, <B>round</B>, the plotting viewport (<B>vx1</B>, <B>vx2</B>, 
  <B>vy1</B>, <B>vy2</B>), and the plotting window (<B>wx1</B>, <B>wx2</B>, 
  <B>wy1</B>, <B>wy2</B>) are used.
  <P>
  If the plotting viewport was not set by the user, <B>prows</B> 
  automatically sets a viewport centered on the device.  The default value
  of <B>fill</B> = yes means the plot spans equal amounts of NDC space in
  x and y.  Setting
  the value of <B>fill</B>  to "<TT>no</TT>" means the viewport will be adjusted so 
  that the square plot will span equal physical lengths in x and y
  when plotted.  That is, when <B>fill = no</B>, a unity aspect ratio is 
  enforced, and plots
  appear square regardless of the device aspect ratio.  On devices with non 
  square full device viewports (e.g., the vt640), a plot drawn by <I>prows</I>
  appears extended in the x direction unless <B>fill</B> = no.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Plot rows 128 through 150 of image crab.5009 with default parameters:
  <P>
      cl&gt; prows crab.5009 128 150
  <P>
  2. Overplot rows 128 through 150 of crab.red using circles to mark the 
  added points:
  <P>
      cl&gt; prows crab.red 128 150 append+ pointmode+ marker=circle
  <P>
  3. Annotate the axes of the plot:
  <P>
      cl&gt; prows crab.5009 64 128 xlabel="<TT>Column Number</TT>" ylabel=Intensity
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  To plot the average of 20 rows from a 512 square image, <I>prows</I> takes
  about 1.5 cp seconds.
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  prow, pcol, pcols
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
