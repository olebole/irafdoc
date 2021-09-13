.. _rgcursor:

rgcursor — Read the graphics cursor (makes a list)
==================================================

**Package: lists**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  rgcursor -- read the graphics cursor (makes a list)
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  gcursor
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Task <I>rgcursor</I> iteratively reads the graphics cursor, writing the
  cursor values to the standard output.  The standard output is normally
  redirected into a text file to generate a coordinate list to be used as
  input to one or more other programs.  Any IRAF program which reads the
  graphics cursor may be run taking input from a list prepared in advance
  with <I>rgcursor</I> (as well as interactively, of course).
  <P>
  A plot should be drawn on the graphics terminal before running <I>rgcursor</I>.
  When the program is run a loop is entered, reading the global graphics
  cursor until the end of file character (e.g., &lt;ctrl/z&gt;, &lt;ctrl/d&gt;) is typed.
  Each cursor read causes a line to be printed on the standard output, after
  which the cursor is again read.
  <P>
  While the program is waiting for the cursor to be read, i.e., whenever
  the cursor crosshairs are displayed, the terminal is said to be in
  "<TT>cursor mode</TT>".  While in cursor mode, various commands may be entered,
  e.g., to zoom in a feature to get a more accurate cursor position, without
  terminating the current cursor read.  To read the cursor position, enter
  any key not recognized as a cursor mode command, i.e., any lower case or
  non-alphanumeric character.  The actual character one should type depends
  upon the program for which the list is intended.  If the program will use
  only the X and Y coordinates of the cursor any character may be typed,
  e.g., tap the space bar.  If the program uses the key to determine what
  action to take, then you must type a specific key.
  <P>
  The X and Y coordinates of the cursor position and other information
  comprising the cursor value are printed on the standard output when the
  cursor is read.  The cursor position may optionally be marked whenever the
  cursor is read, by setting the "<TT>:.markcur</TT>" option when in cursor mode.
  This is useful when preparing long lists to keep track of the objects
  or features that have already been marked.
  <P>
  For additional information on <I>cursor mode</I> and the format of a cursor
  value string, type "<TT>help cursor</TT>".  For information on the key and string values
  required by the applications program for which the cursor list is intended,
  consult the documentation for that program.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Interactively generate a starlist (file "<TT>starlist</TT>") to be used as input
  to another program, e.g., for digital photometry.  In this case one would
  probably want to start with a contour plot labeled in image pixel coordinates.
  <P>
  <PRE>
  	cl&gt; contour m74			# make the plot
  	cl&gt; rgcursor &gt; starlist		# make the object list
  <P>
  	At this point, the cursor loop is entered and the terminal
  	is placed into cursor mode.  Any of the following commands
  	might be appropriate:
  <P>
  	<B>command</B>		<B>action</B>
  <P>
  	:.markcur+	enables marking of the cursor position
  			    when the cursor is read
  <P>
  	:radius 7	set object radius in pixels
  	:annulus 10 15	set annulus radii to be used for sky
  	space_bar	mark the position of an object
  	space_bar	mark the position of an object
  				(etc.)
  	
  	Z		zoom in on a feature to get a more
  			    accurate cursor read
  	space_bar	mark the position of the object
  	space_bar	mark the position of another object
  	0		replot the original plot
  	
  	&lt;crtl/z&gt;	(EOF) terminates rgcursor
  </PRE>
  <P>
  Given the above command sequence, the output file "<TT>starlist</TT>" might
  contain the following cursor values.
  <P>
  <PRE>
  	234.435 78.9292 1 : radius 7
  	234.475 78.9243 1 : annulus 10 15
  	67.2822 282.319 1 \40
  	766.252 344.224 1 \40
  	822.918 311.748 1 \40
  	76.8272 822.139 1 \40
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  rimcursor, cursor
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
