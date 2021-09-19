.. _graph:

graph: Graph one or more image sections or lists
================================================

**Package: plot**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  graph -- graph one or more lists or image sections
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  graph input
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input' -->
  <dd>List of operands to be graphed.  May be STDIN, or one or more image sections 
  or lists.
  </dd>
  </dl>
  <dl>
  <dt><b>wx1=0., wx2=0., wy1=0., wy2=0.</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='wx1' Line='wx1=0., wx2=0., wy1=0., wy2=0.' -->
  <dd>The range of user coordinates spanned by the plot.  If the range of values
  in x or y = 0, the plot is automatically scaled from the minimum to
  maximum data value along the degenerate dimension.
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
  In addition to these three reserved WCS names, the name of any user WCS
  defined for the reference image may be given.  A user world coordinate system
  may be any linear or nonlinear world system.
  </dd>
  </dl>
  <dl>
  <dt><b>vx1=0., vx2=0., vy1=0., vy2=0.</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='vx1' Line='vx1=0., vx2=0., vy1=0., vy2=0.' -->
  <dd>NDC coordinates (0-1) of the device plotting viewport.  If not set by 
  the user, a suitable viewport which allows sufficient room for all labels 
  is used.
  </dd>
  </dl>
  <dl>
  <dt><b>pointmode = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='pointmode' Line='pointmode = no' -->
  <dd>If <b>pointmode</b> = yes, plot points or markers at data values, rather than 
  connected lines.
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
  <dd>The size of a marker in NDC coordinates (0 to 1 spans the screen).
  If zero and the input operand is a list, marker sizes are taken individually
  from the third column of each list element.  If positive, all markers are
  of size <b>szmarker</b>.  If negative and the input operand is a list,
  the size of a marker is the third column of each list element times the
  absolute value of <b>szmarker</b>.
  </dd>
  </dl>
  <dl>
  <dt><b>ltypes = <tt>""</tt>, colors = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='ltypes' Line='ltypes = "", colors = ""' -->
  <dd>List of line types and colors to use when graphing multiple data sets.
  The lists are comma or space separate integer numbers.  If no list is
  given the line types and colors will cycle through the range of
  values.  If a list is given then the values are used in order and if
  the list is exhausted before the data the last value is used for all
  remaining data sets.
  The line types have values between 1 and 4:
  <pre>
      1 - solid line
      2 - dashed line
      3 - dotted line
      4 - dot-dash line
  </pre>
  The colors have values between 1 and 9.  The colors associated with each
  number depend on the graphics device.  For example <tt>"xgterm"</tt> colors are
  assigned by X resources.
  </dd>
  </dl>
  <dl>
  <dt><b>xlabel = <tt>"wcslabel"</tt>, ylabel = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='xlabel' Line='xlabel = "wcslabel", ylabel = ""' -->
  <dd>Label for the X-axis or Y-axis.  if <b>xlabel</b> = <tt>"wcslabel"</tt> and the first
  operand in the <b>input</b> is an image, the world coordinate system label
  if defined is used.
  </dd>
  </dl>
  <dl>
  <dt><b>title = <tt>"imtitle"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='title' Line='title = "imtitle"' -->
  <dd>Plot title.  If <b>title</b>  = <tt>"imtitle"</tt>
  and the first operand in <b>input</b> is an image, the image title is used
  as the plot title.
  </dd>
  </dl>
  <dl>
  <dt><b>xformat = <tt>"wcsformat"</tt>, yformat = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='xformat' Line='xformat = "wcsformat", yformat = ""' -->
  <dd>The numerical format for the coordinate labels.  The values may be <tt>""</tt>
  (an empty string), %f for decimal format, %h and %H for xx:xx:xx format, and
  %m and %M for xx:xx.x format.  The upper case %H and %M convert degrees
  to hours.  For images a recommended x coordinate format may be defined as
  a WCS attribute.  If the xformat value is <tt>"wcsformat"</tt> the WCS attribute
  format will be used.  Any other value will override the image attribute.
  </dd>
  </dl>
  <dl>
  <dt><b>box = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='box' Line='box = yes' -->
  <dd>Draw axes at the perimeter of the plotting window.
  </dd>
  </dl>
  <dl>
  <dt><b>fill = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='fill' Line='fill = yes' -->
  <dd>Fill the output viewport regardless of the device aspect ratio?
  </dd>
  </dl>
  <dl>
  <dt><b>axis = 1</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='axis' Line='axis = 1' -->
  <dd>Axis along which the projection is to be computed, if an input operand is
  an image section of dimension 2 or higher.  Axis 1 is X (line average),
  2 is Y (column average), and so on.
  </dd>
  </dl>
  <dl>
  <dt><b>transpose = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='transpose' Line='transpose = no' -->
  <dd>Swap the X and Y axes of the plot.  If enabled, the axes are transposed 
  after the optional linear transformation of the X-axis.
  </dd>
  </dl>
  <dl>
  <dt><b>logx = no, logy = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='logx' Line='logx = no, logy = no' -->
  <dd>Log scale the X or Y axis.  Zero or negative values are indefinite and
  will not be plotted, but are tolerated.
  </dd>
  </dl>
  <dl>
  <dt><b>ticklabels = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='ticklabels' Line='ticklabels = yes' -->
  <dd>Label the tick marks.
  </dd>
  </dl>
  <dl>
  <dt><b>majrx=5, minrx=5, majry=5, minry=5</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='majrx' Line='majrx=5, minrx=5, majry=5, minry=5' -->
  <dd>Number of major tick marks on each axis; number of minor tick marks between
  major tick marks.  Ignored if log scaling is in effect for an axis.
  </dd>
  </dl>
  <dl>
  <dt><b>lintran = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='lintran' Line='lintran = no' -->
  <dd>Perform a linear transformation of the X-axis upon input.  Used to assign
  logical coordinates to the indices of pixel data arrays (image sections).
  </dd>
  </dl>
  <dl>
  <dt><b>p1=0, p2=0, q1=0, q2=1</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='p1' Line='p1=0, p2=0, q1=0, q2=1' -->
  <dd>If <b>lintran</b> is enabled, pixel index P1 is mapped to Q1, and P2 to Q2.
  If P1 and P2 are zero, P1 is set to 1 and P2 to the number of pixels in
  the input array.
  </dd>
  </dl>
  <dl>
  <dt><b>round = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='round' Line='round = no' -->
  <dd>Extend the axes up to <tt>"nice"</tt> values.
  </dd>
  </dl>
  <dl>
  <dt><b>overplot = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='overplot' Line='overplot = no' -->
  <dd>Overplot on an existing plot.  All axis scaling and labeling parameters
  apply.
  </dd>
  </dl>
  <dl>
  <dt><b>append = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='append' Line='append = no' -->
  <dd>Append to an existing plot.  The previous axis is used and the axis
  scaling and labeling parameters are ignored.
  </dd>
  </dl>
  <dl>
  <dt><b>device = <tt>"stdgraph"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='device' Line='device = "stdgraph"' -->
  <dd>The output device.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  <b>Graph</b> graphs one or more lists or image sections; lists and image
  sections may be mixed in the input list at will.  If the curves are not
  all the same length the plot will be scaled to the longest curve and all
  curves will be plotted left justified.  If an image section operand has
  more than one dimension the projection (average) along a designated axis
  will be computed and plotted.  By default, a unique dash pattern is used
  for each curve, up to a maximum of 4.
  </p>
  <p>
  List input may be taken from the standard input or from a file,
  and consists of a sequence of Y values, X and Y values, or X, Y,
  and marker size values, one pair of coordinates per line in the list.
  If the third column of a list contains positive numbers, they are
  interpreted as NDC marker sizes, optionally scaled by the absolute
  value of <i>szmarker</i>.  If you want the third column of a list to
  be interpreted as WCS coordinates, indicating errors for example, the
  marker sizes should be entered as negative numbers.
  Blank lines, comment lines, and extra columns are ignored.
  The first element in the list determines whether the list is a Y list
  or and X,Y list; it is an error if an X,Y list has fewer than two
  coordinates in any element.  INDEF valued elements appear as gaps
  in the plot.
  </p>
  <p>
  If <b>append</b> is enabled, previous values for <b>box</b>,
  <b>fill</b>, <b>round</b>, the plotting viewport (<b>vx1</b>, <b>vx2</b>, 
  <b>vy1</b>, <b>vy2</b>), and the plotting window (<b>wx1</b>, <b>wx2</b>, 
  <b>wy1</b>, <b>wy2</b>) are used.  The <b>overplot</b> parameter overplots
  a new plot including any new axis scaling and labeling.
  </p>
  <p>
  By default, the plot drawn will fill the device viewport, if the viewport
  was either specified by the user or automatically calculated by 
  <i>graph</i>.  Setting
  the value of <b>fill</b>  to <tt>"no"</tt> means the viewport will be adjusted so 
  that equal numbers of data values in x and y will occupy equal lengths 
  when plotted.  That is, when <b>fill = no</b>, a unity aspect ratio is 
  enforced, and plots
  appear square regardless of the device aspect ratio.  On devices with non 
  square full device viewports (e.g., the vt640), a plot drawn by <i>graph</i>
  appears extended in the x direction unless <b>fill</b> = no.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Plot the output of a list processing filter:
  </p>
  <p>
      cl&gt; ... list_filter | graph
  </p>
  <p>
  2. Plot a graph entered interactively from the terminal:
  </p>
  <p>
      cl&gt; graph STDIN
  </p>
  <p>
  3. Overplot two lists:
  </p>
  <p>
      cl&gt; graph list1,list2
  </p>
  <p>
  4. Graph line 128 of image <tt>"pix"</tt>:
  </p>
  <p>
      cl&gt; graph pix[*,128]
  </p>
  <p>
  5. Graph the average of columns 50 through 100:
  </p>
  <p>
      cl&gt; graph pix[50:100,*] axis=2
  </p>
  <p>
  6. Graph a list in point plot mode:
  </p>
  <p>
      cl&gt; graph list po+
  </p>
  <p>
  7. Annotate a graph:
  </p>
  <pre>
      cl&gt; graph pix[*,10],pix[*,20] xlabel=column\<br>
      &gt;&gt;&gt; ylabel=intensity title="lines 10 and 20 of pix"
  </pre>
  <p>
  8. Direct the graph to the standard plotter device:
  </p>
  <p>
      cl&gt; graph list device=stdplot
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  Indefinites are not recognized when computing image projections.
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  pcol, pcols, prow, prows
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  -->
  
