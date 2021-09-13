.. _polymark:

polymark — Create polygon lists for polyphot
============================================

**Package: apphot**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  polymark -- create or review polygon and coordinate lists for input to the
  polyphot task
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  polymark image
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>images</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>The list of input images used to define the polygons.
  </DD>
  </DL>
  <DL>
  <DT><B>coords = "<TT>default</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='coords' Line='coords = "default"'>
  <DD>The input / output center positions file. The center positions for each
  polygonal aperture are read from or written to coords. There may more than one
  center position per polygon. Center positions are written to coords 1 center
  position per line. When the current polygon changes POLYMARK inserts a line
  containing a single <TT>';'</TT> after the last center position. If coords is
  "<TT>default</TT>", "<TT>dir$default</TT>" or a directory specification then a center position
  file name of the form dir$root.extension.version is constructed, where dir is
  the directory, root is the root image name, extension is "<TT>coo</TT>" and version is
  the next available version of the file. 
  </DD>
  </DL>
  <DL>
  <DT><B>polygons = "<TT>default</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='polygons' Line='polygons = "default"'>
  <DD>The name of the polygons file. The vertices of each polygon  are read from or
  written to the polygons file. The polygons file contains a list of the
  polygon vertices. Each vertex list is terminated by a line containing a  <TT>';'</TT>
  after the last vertex. If polygons is "<TT>default</TT>", "<TT>dir$default</TT>" or a directory
  specification then an output name of the form dir$root.extension.version is
  constructed, where dir is the directory, root is the root image name, extension
  is "<TT>ver</TT>" and the version is next available version of the file. The number of
  polygon files must be equal to the number of image files.
  </DD>
  </DL>
  <DL>
  <DT><B>icommands = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='icommands' Line='icommands = ""'>
  <DD>The image cursor or image cursor command file.
  </DD>
  </DL>
  <DL>
  <DT><B>gcommands = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='gcommands' Line='gcommands = ""'>
  <DD>The graphics cursor or graphics cursor command file.
  </DD>
  </DL>
  <DL>
  <DT><B>wcsin = "<TT>)_.wcsin</TT>", wcsout = "<TT>)_.wcsout</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wcsin' Line='wcsin = ")_.wcsin", wcsout = ")_.wcsout"'>
  <DD>The coordinate system of the input coordinates read from or written
  to <I>coords</I> and <I>polygons</I>. The image header coordinate system is
  used to transform from the input coordinate system to the "<TT>logical</TT>" pixel
  coordinate system used internally, and from the internal "<TT>logical</TT>" pixel
  coordinate system to the output coordinate system. The input coordinate
  system options are "<TT>logical</TT>", tv"<TT>, </TT>"physical"<TT>, and </TT>"world"<TT>. The output
  coordinate system options are </TT>"logical"<TT>, </TT>"tv"<TT>, and </TT>"physical"<TT>. The image
  cursor coordinate system is assumed to be the </TT>"tv"<TT> system.
  <DL>
  <DT><B>logical</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='logical' Line='logical'>
  <DD>Logical coordinates are pixel coordinates relative to the current image.
  The  logical coordinate system is the coordinate system used by the image
  input/output routines to access the image data on disk. In the logical
  coordinate system the coordinates of the first pixel of a  2D image, e.g.
  dev$ypix  and a 2D image section, e.g. dev$ypix[200:300,200:300] are
  always (1,1).
  </DD>
  </DL>
  <DL>
  <DT><B>tv</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='tv' Line='tv'>
  <DD>Tv coordinates are the pixel coordinates used by the display servers. Tv
  coordinates  include  the effects of any input image section, but do not
  include the effects of previous linear transformations. If the input
  image name does not include an image section, then tv coordinates are
  identical to logical coordinates.  If the input image name does include a
  section, and the input image has not been linearly transformed or copied from
  a parent image, tv coordinates are identical to physical coordinates.
  In the tv coordinate system the coordinates of the first pixel of a
  2D image, e.g. dev$ypix and a 2D image section, e.g. dev$ypix[200:300,200:300]
  are (1,1) and (200,200) respectively.
  </DD>
  </DL>
  <DL>
  <DT><B>physical</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='physical' Line='physical'>
  <DD>Physical coordinates are pixel coordinates invariant  with respect to linear
  transformations of the physical image data.  For example, if the current image
  was created by extracting a section of another image,  the  physical
  coordinates of an object in the current image will be equal to the physical
  coordinates of the same object in the parent image,  although the logical
  coordinates will be different.  In the physical coordinate system the
  coordinates of the first pixel of a 2D image, e.g. dev$ypix and a 2D
  image section, e.g. dev$ypix[200:300,200:300] are (1,1) and (200,200)
  respectively.
  </DD>
  </DL>
  <DL>
  <DT><B>world</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='world' Line='world'>
  <DD>World coordinates are image coordinates in any units which are invariant
  with respect to linear transformations of the physical image data. For
  example, the ra and dec of an object will always be the same no matter
  how the image is linearly transformed. The units of input world coordinates
  must be the same as those expected by the image header wcs, e. g.
  degrees and degrees for celestial coordinate systems.
  </DD>
  </DL>
  The wcsin and wcsout parameters default to the values of the package
  parameters of the same name. The default values of the package parameters
  wcsin and wcsout are </TT>"logical"<TT> and </TT>"logical"<TT> respectively.
  </DD>
  </DL>
  <DL>
  <DT><B>cache = </TT>")_.cache"<TT></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cache' Line='cache = ")_.cache"'>
  <DD>Cache the image pixels in memory. Cache may be set to the value of the apphot
  package parameter (the default), </TT>"yes"<TT>, or </TT>"no"<TT>. By default cacheing is 
  disabled.
  </DD>
  </DL>
  <DL>
  <DT><B>graphics = </TT>")_.graphics"<TT></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = ")_.graphics"'>
  <DD>The standard graphics device.
  </DD>
  </DL>
  <DL>
  <DT><B>display = </TT>")_.display"<TT></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='display' Line='display = ")_.display"'>
  <DD>The default display device.  Display may be set to the apphot package
  parameter value (the default), </TT>"yes"<TT>, or </TT>"no.  By default graphics overlay is
  disabled.  Setting display to one of "<TT>imdr</TT>", "<TT>imdg</TT>", "<TT>imdb</TT>", or "<TT>imdy</TT>" enables
  graphics overlay with the IMD graphics kernel.  Setting display to
  "<TT>stdgraph</TT>" enables POLYMARK to work interactively from a contour plot.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  POLYMARK creates and / or displays center position and polygons files
  suitable for input to POLYPHOT. For each image in the input list POLYMARK
  creates a polygons file <I>polygons</I> and center positions file <I>coords</I>, 
  if these do not already exist. The format of the polygons and center
  position files is described in the OUTPUT section. 
  <P>
  Polygonal apertures are defined and drawn on the image display using
  the image display cursor and then shifted to the desired center
  using the image display cursor. At any point in the marking process
  the user may rewind the polygon and coordinate file and draw the previously
  defined polygons on the display.
  <P>
  The coordinates read from <I>polygons</I> or  <I>coords</I> are assumed to be
  in coordinate system defined by <I>wcsin</I>. The options are "<TT>logical</TT>", "<TT>tv</TT>",
  "<TT>physical</TT>", and "<TT>world</TT>" and the transformation from the input coordinate
  system to the internal "<TT>logical</TT>" system is defined by the image coordinate
  system.  The simplest default is the "<TT>logical</TT>" pixel system. Users working on
  with image sections but importing pixel coordinate lists generated from the
  parent image must use the "<TT>tv</TT>" or "<TT>physical</TT>" input coordinate systems.
  Users importing coordinate lists in world coordinates, e.g. ra and dec,
  must use the "<TT>world</TT>" coordinate system and may need to convert their
  equatorial coordinate units from hours and degrees to degrees and degrees first.
  <P>
  The coordinates written to <I>polygons</I> or <I>coords</I> are in the coordinate
  system defined by <I>wcsout</I>. The options are "<TT>logical</TT>", "<TT>tv</TT>", and
  "<TT>physical</TT>". The simplest default is the "<TT>logical</TT>" system. Users
  wishing to correlate the output coordinates of objects measured in
  image sections or mosaic pieces with coordinates in the parent
  image must use the "<TT>tv</TT>" or "<TT>physical</TT>" coordinate systems.
  <P>
  If <I>cache</I> is yes and the host machine physical memory and working set size
  are large enough, the input image pixels are cached in memory. If cacheing
  is enabled and POLYMARK is run interactively the first measurement will appear
  to take a long time as the entire image must be read in before the measurement
  is actually made. All subsequent measurements will be very fast because POLYMARK
  is accessing memory not disk. The point of cacheing is to speed up random
  image access by making the internal image i/o buffers the same size as the
  image itself. However if the input object lists are sorted in row order and
  sparse cacheing may actually worsen not improve the execution time. Also at
  present there is no point in enabling cacheing for images that are less than
  or equal to 524288 bytes, i.e. the size of the test image dev$ypix, as the
  default image i/o buffer is exactly that size. However if the size of dev$ypix
  is doubled by converting it to a real image with the chpixtype task then the
  effect of cacheing in interactive is can be quite noticeable if measurements
  of objects in the top and bottom halfs of the image are alternated.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Cursor commands</H3>
  <! BeginSection: 'CURSOR COMMANDS'>
  <UL>
  <P>
  The following interactive keystroke and colon commands are available.
  <P>
  <PRE>
  	Interactive Keystroke Commands
  <P>
  ?	Print help
  :	Colon commands 
  d	Plot radial profile of star near cursor
  g	Define the current polygonal aperture
  f	Draw the current polygon on the display
  spbar	Draw the current polygon on the display, output the polygon
  r	Rewind the polygon list
  m	Draw the next polygon in the polygon list on the display
  l	Draw all the remaining polygons in the list on the display
  q	Exit
  <P>
  	Colon commands
  <P>
  :m [n]	Draw the next [nth] polygon in the polygon list on the display
  </PRE>
  <P>
  </UL>
  <! EndSection:   'CURSOR COMMANDS'>
  <H3>Output</H3>
  <! BeginSection: 'OUTPUT'>
  <UL>
  <P>
  A sample polygons file and accompanying coordinates file is listed below.
  <P>
  <PRE>
  	# Sample Polygons File (2 polygons)
  <P>
  	200.5  200.5
  	300.5  200.5
  	300.5  300.5
  	200.5  300.5
  	;
  	100.4  100.4
  	120.4  100.4
  	120.4  120.4
  	100.4  120.4
  	;
  </PRE>
  <P>
  <PRE>
  	# Sample Coordinates File (2 groups, 1 for each polygon)
  <P>
  	123.4  185.5
  	110.4  130.4
  	150.9  200.5
  	;
  	85.6   35.7
  	400.5  300.5
  	69.5   130.5
  	;
  </PRE>
  <P>
  </UL>
  <! EndSection:   'OUTPUT'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Create a coordinate list and polygon file using the image display and
  image display cursor. Use polymark to both create and display the 
  polygon and polygon center lists.
  <P>
  <PRE>
  	ap&gt; display dev$ypix 1 fi+ 
  <P>
  	... display the image
  <P>
  	ap&gt; polymark dev$ypix display=imdg
  <P>
  	... type ? for an optional help page 
  <P>
  	... type g to enter the "define a polygon" menu
  	... move the cursor to the first vertex, tap the space bar
  	    to mark the vertex, and repeat for each vertex
  	... type q to quit the "define a polygon" menu
  	... mark each vertex only once, POLYPHOT will close the
  	    polygon for you
  <P>
  	... move the cursor to the desired polygon center and
  	    tap the space bar to record the polygon
  	... repeat for all desired polygon centers
  <P>
  	... type g to define the next polygon
  	... move the cursor to the first vertex, tap the space bar
  	    to mark the vertex and repeat for each vertex
  	... type q to quit the polygon menu
  	... mark each vertex only once, POLYPHOT will close the
  	    polygon for you
  <P>
  	... move the cursor to the desired polygon center and
  	    tap the space bar
  	... repeat for all desired polygon centers
  <P>
  	... type q to quit and q to confirm the quit
  <P>
  	... output will appear in ypix.coo.1 and ypix.ver.1
  <P>
  <P>
  	ap&gt; display dev$ypix 2 fi+ 
  <P>
  	... display the image
  <P>
  	ap&gt; polymark dev$ypix coords=ypix.coo.1 polygons=ypix.ver.1 \<BR>
  	    display=imdg
  <P>
  	... type m to mark the first polygon / polygon center on the display
  <P>
  	... type m to mark the next polygon / polygon center on the display
  <P>
  	... type l to mark the remaining polygons
  <P>
  	... type q to quit and q to confirm the quit
  <P>
  <P>
  	ap&gt; display dev$ypix 2 fi+ 
  <P>
  	... redisplay the image
  <P>
  	ap&gt; polymark dev$ypix coords="" polygons=ypix.ver.1 \<BR>
  	    display=imdg
  <P>
  	... type l to mark the polygon list, note that since there is
  	    no coords file the polygons are not shifted
  <P>
  	... type q to quit and q to confirm the quit
  </PRE>
  <P>
  <P>
  2. Repeat the previous example using an image section.
  <P>
  <PRE>
  	ap&gt; display dev$ypix[150:450,150:450] 1 fi+ 
  <P>
  	... display the image
  <P>
  <P>
  	ap&gt; polymark dev$ypix[150:450,150:450]] display=imdg wcsout=tv
  <P>
  	... type ? for an optional help page 
  <P>
  	... type g to enter the "define a polygon" menu
  	... move the cursor to the first vertex, tap the space bar
  	    to mark the vertex, and repeat for each vertex
  	... type q to quit the "define a polygon" menu
  	... mark each vertex only once, POLYPHOT will close the
  	    polygon for you
  <P>
  	... move the cursor to the desired polygon center and
  	    tap the space bar to record the polygon
  	... repeat for all desired polygon centers
  <P>
  	... type g to define the next polygon
  	... move the cursor to the first vertex, tap the space bar
  	    to mark the vertex and repeat for each vertex
  	... type q to quit the polygon menu
  	... mark each vertex only once, POLYPHOT will close the
  	    polygon for you
  <P>
  	... move the cursor to the desired polygon center and
  	    tap the space bar
  	... repeat for all desired polygon centers
  <P>
  	... type q to quit and q to confirm the quit
  <P>
  	... output will appear in ypix.coo.2 and ypix.ver.2
  <P>
  <P>
  	ap&gt; display dev$ypix[150:450,150:450] 2 fi+ 
  <P>
  	... display the image
  <P>
  <P>
  	ap&gt; polymark dev$ypix[150:450,150:450] coords=ypix.coo.2 \<BR>
              polygons=ypix.ver.2 display=imdg wcsin=tv
  <P>
  	... type m to mark the first polygon / polygon center on the display
  <P>
  	... type m to mark the next polygon / polygon center on the display
  <P>
  	... type l to mark the remaining polygons
  <P>
  </PRE>
  <P>
  <P>
  3. Repeat example 1 using a contour plot instead of the image display.
  <P>
  <PRE>
  	ap&gt; show stdimcur
  <P>
  	... record the default value of stdimcur
  <P>
  	ap&gt; set stdimcur = stdgraph
  <P>
  	... define the image cursor to be the graphics cursor
  <P>
  	ap&gt; contour dev$ypix
  <P>
  	... draw a contour plot on the screen
  <P>
  	ap&gt; contour dev$ypix &gt;G ypix.plot1
  <P>
  	... store the contour plot of dev$ypix in the file ypix.plot1
  <P>
  	ap&gt; polymark dev$ypix display=stdgraph
  <P>
  	... type g to enter the define a polygon menu
  	... move the cursor to the first vertex, tap the space bar
  	    to mark the vertex, and repeat for each vertex
  	... type q to quit the define a polygon menu
  	... mark each vertex only once, POLYPHOT will close the
  	    polygon for you
  <P>
  	... move the cursor to the desired polygon center and
  	    tap the space bar to record the polygon
  	... repeat for all desired polygon centers
  <P>
  	... type g to define the next polygon
  	... move the cursor to the first vertex, tap the space bar
  	    to mark the vertex and repeat for each vertex
  	... type q to quit the define a polygon menu
  	... mark each vertex only once, POLYPHOT will close the
  	    polygon for you
  <P>
  	... move the cursor to the desired polygon center and
  	    tap the space bar
  	... repeat for all desired polygon centers
  <P>
  	... type r to rewind the coordinate and polygon lists
  <P>
  	... type :.read ypix.plot1 to reread the contour plot
  <P>
  	... type l to display all the polygons ...
  <P>
  	... type q to quit and q again to confirm the  quit
  <P>
  	... output will appear in ypix.ver.3 and ypix.coo.3
  <P>
  	ap&gt; contour dev$ypix
  <P>
  	... redraw the contour plot
  <P>
  	ap&gt; polymark dev$ypix coords="ypix.coo.3" polygons=ypix.ver.3 \<BR>
  	    display=stdgraph
  <P>
  	ap&gt; set stdimcur = &lt;default&gt;
  <P>
  	... reset the value of the stdimcur parameter
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  <P>
  It is the responsibility of the user to make sure that the image displayed
  in the image display is the same as the image specified by the image parameter.
  <P>
  Commands which draw to the image display are disabled by default.  To enable
  graphics overlay on the image display, set the display parameter to "<TT>imdr</TT>",
  "<TT>imdg</TT>", "<TT>imdb</TT>", or "<TT>imdy</TT>" to get red, green, blue or yellow overlays. It
  may be necessary to run gflush and to redisplay the image to get the overlays
  position correctly.
  <P>
  There are no restrictions on the shape of the polygon but the vertices
  must be listed in order either clockwise or counterclockwise in the
  polygons file.
  <P>
  It is not necessary to close the polygon when drawing on the display.
  POLYMARK will complete the polygon for you.
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  polyphot
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'CURSOR COMMANDS' 'OUTPUT' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
