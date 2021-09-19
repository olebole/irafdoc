.. _pvector:

pvector: Plot an arbitrary vector in a 2D image
===============================================

**Package: plot**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  pvector -- plot an arbitrary vector in a 2D image
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  pvector image x1 y1 x2 y2
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>image</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='image' Line='image' -->
  <dd>Input image containing data to be plotted.
  </dd>
  </dl>
  <dl>
  <dt><b>x1, y1</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='x1' Line='x1, y1' -->
  <dd>Starting coordinates of the vector to be plotted.
  </dd>
  </dl>
  <dl>
  <dt><b>x2, y2</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='x2' Line='x2, y2' -->
  <dd>Ending coordinates of the vector to be plotted.
  </dd>
  </dl>
  <dl>
  <dt><b>xc, yc</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='xc' Line='xc, yc' -->
  <dd>The center coordinates of the vector to be plotted if the position
  angle <i>theta</i> is defined.
  </dd>
  </dl>
  <dl>
  <dt><b>width = 1</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='width' Line='width = 1' -->
  <dd>Number of pixels perpendicular to the vector to average.
  </dd>
  </dl>
  <dl>
  <dt><b>theta = INDEF</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='theta' Line='theta = INDEF' -->
  <dd>The postion angle of the vector to be plotted measured counter-clockwise
  from the positive x axis. Theta must be between 0.0 and 360.0 degrees.
  If theta is specified, the <i>xc</i>, and <i>yc</i> parameters
  must be specified instead of the starting and ending coordinates
  as in examples 3 and 4.
  </dd>
  </dl>
  <dl>
  <dt><b>length = INDEF</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='length' Line='length = INDEF' -->
  <dd>The length of the vector to be plotted if <i>theta</i> is defined. The
  default is to plot the vector from one edge of the frame to another.
  </dd>
  </dl>
  <dl>
  <dt><b>boundary = constant</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='boundary' Line='boundary = constant' -->
  <dd>The type of boundary extension. The boundary extension options are:
  <dl>
  <dt><b>nearest</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='nearest' Line='nearest' -->
  <dd>Use the value of the nearest boundary pixel.
  </dd>
  </dl>
  <dl>
  <dt><b>constant</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='constant' Line='constant' -->
  <dd>Use a constant value.
  </dd>
  </dl>
  <dl>
  <dt><b>reflect</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='reflect' Line='reflect' -->
  <dd>Generate a value by reflecting around the boundary.
  </dd>
  </dl>
  <dl>
  <dt><b>wrap</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='wrap' Line='wrap' -->
  <dd>Generate a value by wrapping around to the opposite side of the image.
  </dd>
  </dl>
  </dd>
  </dl>
  <dl>
  <dt><b>constant = 0.</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='constant' Line='constant = 0.' -->
  <dd>The constant for constant valued boundary extension.
  </dd>
  </dl>
  <dl>
  <dt><b>vec_output = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='vec_output' Line='vec_output = ""' -->
  <dd>File or image name if output vector is desired.  If this parameter is
  non-null, then the computed vector will be output to the named file of
  the type specified by the <i>out_type</i> parameter.  If set to STDOUT
  or STDERR, a listing of the pixels (i.e. text format) will be output to 
  either of these streams.  Plotting is disabled if vector output is selected.
  </dd>
  </dl>
  <dl>
  <dt><b>out_type = <tt>"text"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='out_type' Line='out_type = "text"' -->
  <dd>Type of output format (image|text). If an image is created, then a new
  header keyword, <tt>"VSLICE"</tt>, will be appended to the new image describing
  the endpoints of the vector, the width, and the parent image name. The 
  parent image header will be copied to the new image.
  </dd>
  </dl>
  <dl>
  <dt><b>wx1 = 0., wx2 = 0., wy1 = 0., wy2 = 0.</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='wx1' Line='wx1 = 0., wx2 = 0., wy1 = 0., wy2 = 0.' -->
  <dd>The range of world coordinates to be included in the plot.  If the
  range of values in x or y is zero, the plot is automatically scaled from the
  minimum to maximum data values along the degenerate axis.
  </dd>
  </dl>
  <dl>
  <dt><b>vx1 = 0., vx2 = 0., vy1 = 0., vy2 = 0.</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='vx1' Line='vx1 = 0., vx2 = 0., vy1 = 0., vy2 = 0.' -->
  <dd>NDC coordinates (0-1) of the device plotting window.  If not set by user,
  a suitable viewport which allows sufficient room for all labels is used.
  </dd>
  </dl>
  <dl>
  <dt><b>pointmode = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='pointmode' Line='pointmode = no' -->
  <dd>Plot individual points instead of a continuous line?
  </dd>
  </dl>
  <dl>
  <dt><b>marker = <tt>"box"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='marker' Line='marker = "box"' -->
  <dd>Marker or line type to be drawn.  If <b>pointmode</b> = yes the markers are
  <tt>"point"</tt>, <tt>"box"</tt>, <tt>"cross"</tt>, <tt>"plus"</tt>, <tt>"circle"</tt>, <tt>"hebar"</tt>, <tt>"vebar"</tt>, <tt>"hline"</tt>,
  <tt>"vline"</tt> or <tt>"diamond"</tt>.  Any other value defaults to <tt>"box"</tt>.  If drawing lines,
  <b>pointmode</b> = no, the values are <tt>"line"</tt>, <tt>"lhist"</tt>, <tt>"bhist"</tt>.  Any other
  value defaults to <tt>"line"</tt>.  <tt>"bhist"</tt> (box histogram) draws lines to the
  bottom of the graph while <tt>"lhist"</tt> does not.  In both cases the
  horizontal histogram lines run between the half way points (reflected
  at the ends).
  </dd>
  </dl>
  <dl>
  <dt><b>szmarker = 0.005</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='szmarker' Line='szmarker = 0.005' -->
  <dd>The size of the marker drawn when <b>pointmode</b> = yes.
  </dd>
  </dl>
  <dl>
  <dt><b>logx = no, logy = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='logx' Line='logx = no, logy = no' -->
  <dd>Draw the x or y axis in log units, versus linear?
  </dd>
  </dl>
  <dl>
  <dt><b>xlabel = <tt>""</tt>, ylabel = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='xlabel' Line='xlabel = "", ylabel = ""' -->
  <dd>The x-axis and y-axis labels.
  </dd>
  </dl>
  <dl>
  <dt><b>title = <tt>"imtitle"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='title' Line='title = "imtitle"' -->
  <dd>Title for plot.  If not changed from the default, the title string from the
  image header, appended with the vector endpoints, is used.
  </dd>
  </dl>
  <dl>
  <dt><b>majrx = 5, minrx = 5, majry = 5, minry = 5</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='majrx' Line='majrx = 5, minrx = 5, majry = 5, minry = 5' -->
  <dd>The number of major and minor divisions along the x or y axis.
  </dd>
  </dl>
  <dl>
  <dt><b>round = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='round' Line='round = no' -->
  <dd>Round axes up to nice values?
  </dd>
  </dl>
  <dl>
  <dt><b>fill = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='fill' Line='fill = yes' -->
  <dd>Fill the output viewport regardless of the device aspect ratio?
  </dd>
  </dl>
  <dl>
  <dt><b>append = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='append' Line='append = no' -->
  <dd>Append to an existing plot?
  </dd>
  </dl>
  <dl>
  <dt><b>device = <tt>"stdgraph"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='device' Line='device = "stdgraph"' -->
  <dd>Output device.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  Plot an arbitrary vector of data from an image.  The vector can be
  specified by either defining the two endpoints of the vector or 
  by specifying the center position, length and position angle of the vector.
  The user can specify
  the plot size and placement, the scaling and labeling of axes.  Data can be
  plotted as a continuous line or individual points with a specified marker.
  Optionally, the computed vector may be output to a named image or text file
  (as specified by the <i>vec_output</i> and <i>out_type</i> parameters).
  </p>
  <p>
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
  </p>
  <p>
  If <b>append</b> is enabled, previous values for <b>box</b>,
  <b>fill</b>, <b>round</b>, the plotting viewport (<b>vx1</b>, <b>vx2</b>, 
  <b>vy1</b>, <b>vy2</b>), and the plotting window (<b>wx1</b>, <b>wx2</b>, 
  <b>wy1</b>, <b>wy2</b>) are used.
  </p>
  <p>
  If the plotting viewport was not set by the user, <b>pvector</b> 
  automatically sets a viewport centered on the device.  The default value
  of <b>fill</b> = yes means the plot spans equal amounts of NDC space in
  x and y.  Setting
  the value of <b>fill</b>  to <tt>"no"</tt> means the viewport will be adjusted so 
  that the square plot will span equal physical lengths in x and y
  when plotted.  That is, when <b>fill = no</b>, a unity aspect ratio is 
  enforced, and plots
  appear square regardless of the device aspect ratio.  On devices with non 
  square full device viewports (e.g., the vt640), a plot drawn by <i>pvector</i>
  appears extended in the x direction unless <b>fill</b> = no.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Plot from the lower left to upper right of 512 square image crab.5009.
  </p>
  <p>
      cl&gt; pvector crab.5009 1. 1. 512. 512.
  </p>
  <p>
  2. Plot the same vector but with the sampling width = 3.
  </p>
  <p>
      cl&gt; pvector crab.5009 1. 1. 512. 512. width=3
  </p>
  <p>
  3. Plot a vector in same image with center position 256, 256, and a position
  angle of 45 degrees which extends from one edge of the frame to the other.
  </p>
  <p>
      cl&gt; pvector crab.5009 0. 0. 0. 0. 256. 256. theta=45.
  			or
      cl&gt; pvector crab.5009 xc=256. xc=256. theta=45.
  </p>
  <p>
  4. Plot the above vector with a length of 100 pixels.
  </p>
  <p>
      cl&gt; pvector crab.5009 0. 0. 0. 0. 256. 256. theta=45. length=100.
  			or
      cl&gt; pvector crab.5009 xc=256. xc=256. theta=45. length=100.
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Time requirements</h3>
  <!-- BeginSection: 'TIME REQUIREMENTS' -->
  <p>
  It takes approximately 6.7 cpu seconds to compute and plot the twenty
  pixel wide diagonal of a 512 square real image. (VAX/VMS 750 with fpa).
  </p>
  <!-- EndSection:   'TIME REQUIREMENTS' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  prow, pcol, prow, pcols
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  -->
  
