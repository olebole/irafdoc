.. _pcol:

pcol: Plot a column of an image
===============================

**Package: plot**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  pcol -- plot an image column
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  pcol image col
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>image</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='image' Line='image' -->
  <dd>Input image containing column to be plotted.
  </dd>
  </dl>
  <dl>
  <dt><b>col      </b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='col' Line='col      ' -->
  <dd>The column to be plotted.
  </dd>
  </dl>
  <dl>
  <dt><b>wcs = <tt>"logical"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='wcs' Line='wcs = "logical"' -->
  <dd>The world coordinate system (<i>wcs</i>) to be used for axis labeling when
  input is f rom images.
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
  </dd>
  </dl>
  <dl>
  <dt><b>wx1=0., wx2=0., wy1=0., wy2=0.</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='wx1' Line='wx1=0., wx2=0., wy1=0., wy2=0.' -->
  <dd>The range of window (user) coordinates to be included in the plot.  If
  the range of values in x or y = 0, the plot is automatically scaled
  from the minimum to maximum data values along the degenerate axis.
  </dd>
  </dl>
  <dl>
  <dt><b>vx1=0., vx2=0., vy1=0., vy2=0.</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='vx1' Line='vx1=0., vx2=0., vy1=0., vy2=0.' -->
  <dd>NDC coordinates (0-1) of the device plotting viewport.  If not set by
  user, a suitable viewport which allows sufficient room for all labels
  is used.
  </dd>
  </dl>
  <dl>
  <dt><b>pointmode = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='pointmode' Line='pointmode = no' -->
  <dd>Plot individual points instead of a line?
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
  <dt><b>xlabel = <tt>"wcslabel"</tt>, ylabel = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='xlabel' Line='xlabel = "wcslabel", ylabel = ""' -->
  <dd>Label for the X-axis or Y-axis.  if <b>xlabel</b> = <tt>"wcslabel"</tt>
  the world coordinate system label in the image, if defined, is used.
  </dd>
  </dl>
  <dl>
  <dt><b>xformat = <tt>"wcsformat"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='xformat' Line='xformat = "wcsformat"' -->
  <dd>The numerical format for the coordinate labels.  The values may be <tt>""</tt>
  (an empty string), %f for decimal format, %h and %H for xx:xx:xx format, and
  %m and %M for xx:xx.x format.  The upper case %H and %M convert degrees
  to hours.  Some images have a recommended x coordinate format defined as
  a WCS attribute.  If the xformat value is <tt>"wcsformat"</tt> the WCS attribute
  format will be used.  Any other value will override the image attribute.
  </dd>
  </dl>
  <dl>
  <dt><b>title = <tt>"imtitle"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='title' Line='title = "imtitle"' -->
  <dd>Title for plot.  If not changed from the default, the title string from the
  image header, appended with the columns being plotted, is used.
  </dd>
  </dl>
  <dl>
  <dt><b>majrx=5, minrx=5, majry=5, minry=5</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='majrx' Line='majrx=5, minrx=5, majry=5, minry=5' -->
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
  <dd>Fill plotting viewport regardless of device aspect ratio?
  </dd>
  </dl>
  <dl>
  <dt><b>append = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='append' Line='append = no' -->
  <dd>Append to an existing plot?
  </dd>
  </dl>
  <dl>
  <dt><b>device=<tt>"stdgraph"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='device' Line='device="stdgraph"' -->
  <dd>Output device.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  Plot a specified column of an image.  The user can control the
  plot size and placement, the scaling and labeling of axes.  The column can be
  plotted as a continuous line or individual points with a specified marker.
  </p>
  <p>
  If <b>append</b> is enabled, previous values for <b>box</b>,
  <b>fill</b>, <b>round</b>, the plotting viewport (<b>vx1</b>, <b>vx2</b>, 
  <b>vy1</b>, <b>vy2</b>), and the plotting window (<b>wx1</b>, <b>wx2</b>, 
  <b>wy1</b>, <b>wy2</b>) are used.
  </p>
  <p>
  If the plotting viewport was not set by the user, <b>pcol</b> 
  automatically sets a viewport centered on the device.  The default value
  of <b>fill</b> = yes means the plot spans equal amounts of NDC space in
  x and y.  Setting
  the value of <b>fill</b>  to <tt>"no"</tt> means the viewport will be adjusted so 
  that the square plot will span equal physical lengths in x and y
  when plotted.  That is, when <b>fill = no</b>, a unity aspect ratio is 
  enforced, and plots
  appear square regardless of the device aspect ratio.  On devices with non 
  square full device viewports (e.g., the vt640), a plot drawn by <i>pcol</i>
  appears extended in the x direction unless <b>fill</b> = no.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Plot column 128 of image crab.5009 with default parameters:
  </p>
  <p>
      cl&gt; pcol crab.5009 128
  </p>
  <p>
  2. Overplot column 128 of crab.red using boxes to mark the added points:
  </p>
  <p>
      cl&gt; pcol crab.red 128 append+ pointmode+
  </p>
  <p>
  3. Annotate the axes of a column plot:
  </p>
  <p>
      cl&gt; pcol crab.5009 64 xlabel=<tt>"Row Number"</tt> ylabel=Intensity
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Time requirements</h3>
  <!-- BeginSection: 'TIME REQUIREMENTS' -->
  <p>
  <b>pcol</b> requires about 1.6 cp seconds to plot a column of a 512 square
  image.
  </p>
  <!-- EndSection:   'TIME REQUIREMENTS' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  prow, prows, pcols
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  -->
  
