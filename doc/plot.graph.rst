.. _graph:

graph — Graph one or more image sections or lists
=================================================

**Package: plot**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  graph -- graph one or more lists or image sections
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  graph input
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of operands to be graphed.  May be STDIN, or one or more image sections 
  or lists.
  </DD>
  </DL>
  <DL>
  <DT><B>wx1=0., wx2=0., wy1=0., wy2=0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wx1' Line='wx1=0., wx2=0., wy1=0., wy2=0.'>
  <DD>The range of user coordinates spanned by the plot.  If the range of values
  in x or y = 0, the plot is automatically scaled from the minimum to
  maximum data value along the degenerate dimension.
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
  <P>
  In addition to these three reserved WCS names, the name of any user WCS
  defined for the reference image may be given.  A user world coordinate system
  may be any linear or nonlinear world system.
  </DD>
  </DL>
  <DL>
  <DT><B>vx1=0., vx2=0., vy1=0., vy2=0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='vx1' Line='vx1=0., vx2=0., vy1=0., vy2=0.'>
  <DD>NDC coordinates (0-1) of the device plotting viewport.  If not set by 
  the user, a suitable viewport which allows sufficient room for all labels 
  is used.
  </DD>
  </DL>
  <DL>
  <DT><B>pointmode = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pointmode' Line='pointmode = no'>
  <DD>If <B>pointmode</B> = yes, plot points or markers at data values, rather than 
  connected lines.
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
  <DD>The size of a marker in NDC coordinates (0 to 1 spans the screen).
  If zero and the input operand is a list, marker sizes are taken individually
  from the third column of each list element.  If positive, all markers are
  of size <B>szmarker</B>.  If negative and the input operand is a list,
  the size of a marker is the third column of each list element times the
  absolute value of <B>szmarker</B>.
  </DD>
  </DL>
  <DL>
  <DT><B>ltypes = "<TT></TT>", colors = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ltypes' Line='ltypes = "", colors = ""'>
  <DD>List of line types and colors to use when graphing multiple data sets.
  The lists are comma or space separate integer numbers.  If no list is
  given the line types and colors will cycle through the range of
  values.  If a list is given then the values are used in order and if
  the list is exhausted before the data the last value is used for all
  remaining data sets.
  <P>
  The line types have values between 1 and 4:
  <P>
  <PRE>
      1 - solid line
      2 - dashed line
      3 - dotted line
      4 - dot-dash line
  </PRE>
  <P>
  The colors have values between 1 and 9.  The colors associated with each
  number depend on the graphics device.  For example "<TT>xgterm</TT>" colors are
  assigned by X resources.
  </DD>
  </DL>
  <DL>
  <DT><B>xlabel = "<TT>wcslabel</TT>", ylabel = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xlabel' Line='xlabel = "wcslabel", ylabel = ""'>
  <DD>Label for the X-axis or Y-axis.  if <B>xlabel</B> = "<TT>wcslabel</TT>" and the first
  operand in the <B>input</B> is an image, the world coordinate system label
  if defined is used.
  </DD>
  </DL>
  <DL>
  <DT><B>title = "<TT>imtitle</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='title' Line='title = "imtitle"'>
  <DD>Plot title.  If <B>title</B>  = "<TT>imtitle</TT>"
  and the first operand in <B>input</B> is an image, the image title is used
  as the plot title.
  </DD>
  </DL>
  <DL>
  <DT><B>xformat = "<TT>wcsformat</TT>", yformat = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xformat' Line='xformat = "wcsformat", yformat = ""'>
  <DD>The numerical format for the coordinate labels.  The values may be "<TT></TT>"
  (an empty string), %f for decimal format, %h and %H for xx:xx:xx format, and
  %m and %M for xx:xx.x format.  The upper case %H and %M convert degrees
  to hours.  For images a recommended x coordinate format may be defined as
  a WCS attribute.  If the xformat value is "<TT>wcsformat</TT>" the WCS attribute
  format will be used.  Any other value will override the image attribute.
  </DD>
  </DL>
  <DL>
  <DT><B>box = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='box' Line='box = yes'>
  <DD>Draw axes at the perimeter of the plotting window.
  </DD>
  </DL>
  <DL>
  <DT><B>fill = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fill' Line='fill = yes'>
  <DD>Fill the output viewport regardless of the device aspect ratio?
  </DD>
  </DL>
  <DL>
  <DT><B>axis = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='axis' Line='axis = 1'>
  <DD>Axis along which the projection is to be computed, if an input operand is
  an image section of dimension 2 or higher.  Axis 1 is X (line average),
  2 is Y (column average), and so on.
  </DD>
  </DL>
  <DL>
  <DT><B>transpose = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='transpose' Line='transpose = no'>
  <DD>Swap the X and Y axes of the plot.  If enabled, the axes are transposed 
  after the optional linear transformation of the X-axis.
  </DD>
  </DL>
  <DL>
  <DT><B>logx = no, logy = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logx' Line='logx = no, logy = no'>
  <DD>Log scale the X or Y axis.  Zero or negative values are indefinite and
  will not be plotted, but are tolerated.
  </DD>
  </DL>
  <DL>
  <DT><B>ticklabels = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ticklabels' Line='ticklabels = yes'>
  <DD>Label the tick marks.
  </DD>
  </DL>
  <DL>
  <DT><B>majrx=5, minrx=5, majry=5, minry=5</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='majrx' Line='majrx=5, minrx=5, majry=5, minry=5'>
  <DD>Number of major tick marks on each axis; number of minor tick marks between
  major tick marks.  Ignored if log scaling is in effect for an axis.
  </DD>
  </DL>
  <DL>
  <DT><B>lintran = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lintran' Line='lintran = no'>
  <DD>Perform a linear transformation of the X-axis upon input.  Used to assign
  logical coordinates to the indices of pixel data arrays (image sections).
  </DD>
  </DL>
  <DL>
  <DT><B>p1=0, p2=0, q1=0, q2=1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='p1' Line='p1=0, p2=0, q1=0, q2=1'>
  <DD>If <B>lintran</B> is enabled, pixel index P1 is mapped to Q1, and P2 to Q2.
  If P1 and P2 are zero, P1 is set to 1 and P2 to the number of pixels in
  the input array.
  </DD>
  </DL>
  <DL>
  <DT><B>round = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='round' Line='round = no'>
  <DD>Extend the axes up to "<TT>nice</TT>" values.
  </DD>
  </DL>
  <DL>
  <DT><B>overplot = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='overplot' Line='overplot = no'>
  <DD>Overplot on an existing plot.  All axis scaling and labeling parameters
  apply.
  </DD>
  </DL>
  <DL>
  <DT><B>append = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='append' Line='append = no'>
  <DD>Append to an existing plot.  The previous axis is used and the axis
  scaling and labeling parameters are ignored.
  </DD>
  </DL>
  <DL>
  <DT><B>device = "<TT>stdgraph</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='device' Line='device = "stdgraph"'>
  <DD>The output device.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <B>Graph</B> graphs one or more lists or image sections; lists and image
  sections may be mixed in the input list at will.  If the curves are not
  all the same length the plot will be scaled to the longest curve and all
  curves will be plotted left justified.  If an image section operand has
  more than one dimension the projection (average) along a designated axis
  will be computed and plotted.  By default, a unique dash pattern is used
  for each curve, up to a maximum of 4.
  <P>
  List input may be taken from the standard input or from a file,
  and consists of a sequence of Y values, X and Y values, or X, Y,
  and marker size values, one pair of coordinates per line in the list.
  If the third column of a list contains positive numbers, they are
  interpreted as NDC marker sizes, optionally scaled by the absolute
  value of <I>szmarker</I>.  If you want the third column of a list to
  be interpreted as WCS coordinates, indicating errors for example, the
  marker sizes should be entered as negative numbers.
  Blank lines, comment lines, and extra columns are ignored.
  The first element in the list determines whether the list is a Y list
  or and X,Y list; it is an error if an X,Y list has fewer than two
  coordinates in any element.  INDEF valued elements appear as gaps
  in the plot.
  <P>
  If <B>append</B> is enabled, previous values for <B>box</B>,
  <B>fill</B>, <B>round</B>, the plotting viewport (<B>vx1</B>, <B>vx2</B>, 
  <B>vy1</B>, <B>vy2</B>), and the plotting window (<B>wx1</B>, <B>wx2</B>, 
  <B>wy1</B>, <B>wy2</B>) are used.  The <B>overplot</B> parameter overplots
  a new plot including any new axis scaling and labeling.
  <P>
  By default, the plot drawn will fill the device viewport, if the viewport
  was either specified by the user or automatically calculated by 
  <I>graph</I>.  Setting
  the value of <B>fill</B>  to "<TT>no</TT>" means the viewport will be adjusted so 
  that equal numbers of data values in x and y will occupy equal lengths 
  when plotted.  That is, when <B>fill = no</B>, a unity aspect ratio is 
  enforced, and plots
  appear square regardless of the device aspect ratio.  On devices with non 
  square full device viewports (e.g., the vt640), a plot drawn by <I>graph</I>
  appears extended in the x direction unless <B>fill</B> = no.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Plot the output of a list processing filter:
  <P>
      cl&gt; ... list_filter | graph
  <P>
  2. Plot a graph entered interactively from the terminal:
  <P>
      cl&gt; graph STDIN
  <P>
  3. Overplot two lists:
  <P>
      cl&gt; graph list1,list2
  <P>
  4. Graph line 128 of image "<TT>pix</TT>":
  <P>
      cl&gt; graph pix[*,128]
  <P>
  5. Graph the average of columns 50 through 100:
  <P>
      cl&gt; graph pix[50:100,*] axis=2
  <P>
  6. Graph a list in point plot mode:
  <P>
      cl&gt; graph list po+
  <P>
  7. Annotate a graph:
  <P>
  <PRE>
      cl&gt; graph pix[*,10],pix[*,20] xlabel=column\<BR>
      &gt;&gt;&gt; ylabel=intensity title="lines 10 and 20 of pix"
  </PRE>
  <P>
  8. Direct the graph to the standard plotter device:
  <P>
      cl&gt; graph list device=stdplot
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  Indefinites are not recognized when computing image projections.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  pcol, pcols, prow, prows
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
