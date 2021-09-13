.. _pvector:

pvector — Plot an arbitrary vector in a 2D image
================================================

**Package: plot**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  pvector -- plot an arbitrary vector in a 2D image
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  pvector image x1 y1 x2 y2
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>image</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD>Input image containing data to be plotted.
  </DD>
  </DL>
  <DL>
  <DT><B>x1, y1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='x1' Line='x1, y1'>
  <DD>Starting coordinates of the vector to be plotted.
  </DD>
  </DL>
  <DL>
  <DT><B>x2, y2</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='x2' Line='x2, y2'>
  <DD>Ending coordinates of the vector to be plotted.
  </DD>
  </DL>
  <DL>
  <DT><B>xc, yc</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xc' Line='xc, yc'>
  <DD>The center coordinates of the vector to be plotted if the position
  angle <I>theta</I> is defined.
  </DD>
  </DL>
  <DL>
  <DT><B>width = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='width' Line='width = 1'>
  <DD>Number of pixels perpendicular to the vector to average.
  </DD>
  </DL>
  <DL>
  <DT><B>theta = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='theta' Line='theta = INDEF'>
  <DD>The postion angle of the vector to be plotted measured counter-clockwise
  from the positive x axis. Theta must be between 0.0 and 360.0 degrees.
  If theta is specified, the <I>xc</I>, and <I>yc</I> parameters
  must be specified instead of the starting and ending coordinates
  as in examples 3 and 4.
  </DD>
  </DL>
  <DL>
  <DT><B>length = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='length' Line='length = INDEF'>
  <DD>The length of the vector to be plotted if <I>theta</I> is defined. The
  default is to plot the vector from one edge of the frame to another.
  </DD>
  </DL>
  <DL>
  <DT><B>boundary = constant</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='boundary' Line='boundary = constant'>
  <DD>The type of boundary extension. The boundary extension options are:
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
  <DD>Generate a value by wrapping around to the opposite side of the image.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>constant = 0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='constant' Line='constant = 0.'>
  <DD>The constant for constant valued boundary extension.
  </DD>
  </DL>
  <DL>
  <DT><B>vec_output = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='vec_output' Line='vec_output = ""'>
  <DD>File or image name if output vector is desired.  If this parameter is
  non-null, then the computed vector will be output to the named file of
  the type specified by the <I>out_type</I> parameter.  If set to STDOUT
  or STDERR, a listing of the pixels (i.e. text format) will be output to 
  either of these streams.  Plotting is disabled if vector output is selected.
  </DD>
  </DL>
  <DL>
  <DT><B>out_type = "<TT>text</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='out_type' Line='out_type = "text"'>
  <DD>Type of output format (image|text). If an image is created, then a new
  header keyword, "<TT>VSLICE</TT>", will be appended to the new image describing
  the endpoints of the vector, the width, and the parent image name. The 
  parent image header will be copied to the new image.
  </DD>
  </DL>
  <DL>
  <DT><B>wx1 = 0., wx2 = 0., wy1 = 0., wy2 = 0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wx1' Line='wx1 = 0., wx2 = 0., wy1 = 0., wy2 = 0.'>
  <DD>The range of world coordinates to be included in the plot.  If the
  range of values in x or y is zero, the plot is automatically scaled from the
  minimum to maximum data values along the degenerate axis.
  </DD>
  </DL>
  <DL>
  <DT><B>vx1 = 0., vx2 = 0., vy1 = 0., vy2 = 0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='vx1' Line='vx1 = 0., vx2 = 0., vy1 = 0., vy2 = 0.'>
  <DD>NDC coordinates (0-1) of the device plotting window.  If not set by user,
  a suitable viewport which allows sufficient room for all labels is used.
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
  <DT><B>xlabel = "<TT></TT>", ylabel = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xlabel' Line='xlabel = "", ylabel = ""'>
  <DD>The x-axis and y-axis labels.
  </DD>
  </DL>
  <DL>
  <DT><B>title = "<TT>imtitle</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='title' Line='title = "imtitle"'>
  <DD>Title for plot.  If not changed from the default, the title string from the
  image header, appended with the vector endpoints, is used.
  </DD>
  </DL>
  <DL>
  <DT><B>majrx = 5, minrx = 5, majry = 5, minry = 5</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='majrx' Line='majrx = 5, minrx = 5, majry = 5, minry = 5'>
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
  <DD>Fill the output viewport regardless of the device aspect ratio?
  </DD>
  </DL>
  <DL>
  <DT><B>append = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='append' Line='append = no'>
  <DD>Append to an existing plot?
  </DD>
  </DL>
  <DL>
  <DT><B>device = "<TT>stdgraph</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='device' Line='device = "stdgraph"'>
  <DD>Output device.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Plot an arbitrary vector of data from an image.  The vector can be
  specified by either defining the two endpoints of the vector or 
  by specifying the center position, length and position angle of the vector.
  The user can specify
  the plot size and placement, the scaling and labeling of axes.  Data can be
  plotted as a continuous line or individual points with a specified marker.
  Optionally, the computed vector may be output to a named image or text file
  (as specified by the <I>vec_output</I> and <I>out_type</I> parameters).
  <P>
  The vector is extracted as a straight line between the given
  coordinates, sampled at a spacing along that line equivalent to that
  between adjacent pixels in the x or y direction (e.g. the length of a
  diagonal endpoint vector from a square image is n*sqrt(2)).
  It is possible to specify an averaging width
  which determines how many pixels perpendicular to the vector are averaged.
  This averaging window is centered
  on the vector pixel.  When this window is greater than one pixel, it
  is possible that the extraction process might try to exceed the
  image boundary, in which case the specified type of boundary extension
  is employed. The extraction algorithm uses bilinear interpolation to
  evaluate points at non-integral pixel positions.
  <P>
  If <B>append</B> is enabled, previous values for <B>box</B>,
  <B>fill</B>, <B>round</B>, the plotting viewport (<B>vx1</B>, <B>vx2</B>, 
  <B>vy1</B>, <B>vy2</B>), and the plotting window (<B>wx1</B>, <B>wx2</B>, 
  <B>wy1</B>, <B>wy2</B>) are used.
  <P>
  If the plotting viewport was not set by the user, <B>pvector</B> 
  automatically sets a viewport centered on the device.  The default value
  of <B>fill</B> = yes means the plot spans equal amounts of NDC space in
  x and y.  Setting
  the value of <B>fill</B>  to "<TT>no</TT>" means the viewport will be adjusted so 
  that the square plot will span equal physical lengths in x and y
  when plotted.  That is, when <B>fill = no</B>, a unity aspect ratio is 
  enforced, and plots
  appear square regardless of the device aspect ratio.  On devices with non 
  square full device viewports (e.g., the vt640), a plot drawn by <I>pvector</I>
  appears extended in the x direction unless <B>fill</B> = no.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Plot from the lower left to upper right of 512 square image crab.5009.
  <P>
      cl&gt; pvector crab.5009 1. 1. 512. 512.
  <P>
  2. Plot the same vector but with the sampling width = 3.
  <P>
      cl&gt; pvector crab.5009 1. 1. 512. 512. width=3
  <P>
  3. Plot a vector in same image with center position 256, 256, and a position
  angle of 45 degrees which extends from one edge of the frame to the other.
  <P>
      cl&gt; pvector crab.5009 0. 0. 0. 0. 256. 256. theta=45.
  			or
      cl&gt; pvector crab.5009 xc=256. xc=256. theta=45.
  <P>
  <P>
  4. Plot the above vector with a length of 100 pixels.
  <P>
      cl&gt; pvector crab.5009 0. 0. 0. 0. 256. 256. theta=45. length=100.
  			or
      cl&gt; pvector crab.5009 xc=256. xc=256. theta=45. length=100.
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  It takes approximately 6.7 cpu seconds to compute and plot the twenty
  pixel wide diagonal of a 512 square real image. (VAX/VMS 750 with fpa).
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
  prow, pcol, prow, pcols
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
