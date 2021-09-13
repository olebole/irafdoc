fitcoords — Fit user coordinates to image coordinates
=====================================================

**Package: longslit**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>fitcoords (Apr00)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.twodspec.longslit</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>fitcoords (Apr00)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>fitcoords</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  fitcoords -- Fit user coordinates to the image coordinates
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  fitcoords images fitname
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_images">images</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>List of images containing the feature coordinates to be fit.  If the
  parameter <I>combine</I> is yes then feature coordinates from all the images
  are combined and fit by a single function.  Otherwise the feature coordinates
  from each image are fit separately.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fitname">fitname = "<TT></TT>" </A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fitname' Line='fitname = "" '>
  <DD>If the input images are combined and fit by a single function then the fit
  is stored under this name.  If the images are not combined then the
  fit for each image is stored under the name formed by appending the image
  name to this name.  A null prefix is acceptable when not combining but it
  is an error if combining a list of images.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interactive">interactive = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = yes'>
  <DD>Determine coordinate fits interactively?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_combine">combine = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='combine' Line='combine = no'>
  <DD>Combine the coordinates from all the input images and fit them by a single
  function?  If 'no' then fit the coordinates from each image separately.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_database">database = "<TT>database</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='database' Line='database = "database"'>
  <DD>Database containing the feature coordinate information used in fitting the
  coordinates and in which the coordinate fit is recorded.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_deletions">deletions = "<TT>deletions.db</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='deletions' Line='deletions = "deletions.db"'>
  <DD>Deletion list file.  If not null then points whose coordinates match those in
  this file (if it exists) are initially deleted from the fit.
  If the fitting is done interactively then the coordinates of
  any deleted points (after exiting from the interactive fitting) are recorded
  in this file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_function">function = "<TT>chebyshev</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='function' Line='function = "chebyshev"'>
  <DD>Type of two dimensional function to use in fitting the user coordinates.
  The choices are "<TT>chebyshev</TT>" polynomial and "<TT>legendre</TT>" polynomial.
  The function may be abbreviated.  If the task is interactive then
  the user may change the function later.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xorder">xorder = 6</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xorder' Line='xorder = 6'>
  <DD>Order of the mapping function along the first image axis.
  The order is the number of polynomial terms.  If the task is interactive
  then the user may change the order later.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_yorder">yorder = 6</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='yorder' Line='yorder = 6'>
  <DD>Order of the mapping function along the second image axis.
  The order is the number of polynomial terms.  If the task is interactive
  then the user may change the order later.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_logfiles">logfiles = "<TT>STDOUT,logfile</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logfiles' Line='logfiles = "STDOUT,logfile"'>
  <DD>List of files in which to keep logs containing information about
  the coordinate fit.  If null then no log is kept.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_plotfile">plotfile = "<TT>plotfile</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='plotfile' Line='plotfile = "plotfile"'>
  <DD>Name of file to contain metacode for log plots.  If null then no log plots
  are kept.  When the fitting is interactive the last graph is recorded in
  the plot file and when not interactive a default plot is recorded.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_graphics">graphics = "<TT>stdgraph</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = "stdgraph"'>
  <DD>Graphics output device.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_cursor">cursor = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cursor' Line='cursor = ""'>
  <DD>Graphics cursor input.  If null the standard graphics cursor is used.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_cursor_commands">CURSOR COMMANDS</A></H2>
  <! BeginSection: 'CURSOR COMMANDS'>
  <UL>
  <P>
  <PRE>
  ?  List commands
  c  Print data values for point nearest the cursor
  d  Delete the point or set of points with constant x, y, or z
  	nearest the cursor (p, x, y, z,)
  f  Fit surface
  l  Graph the last set of points (in zoom mode)
  n  Graph the next set of points (in zoom mode)
  p  Graph all features
  q  Quit
  r  Redraw a graph
  u  Undelete the point or set of points with constant x, y, or z
  	nearest the cursor (p, x, y, z,)
  w  Window the graph.  Type <TT>'?'</TT> to the "window:" prompt for more help.
  x  Select data for the x axis (x, y, z, s, r)
  y  Select data for the y axis (x, y, z, s, r)
  z  Zoom on the set of points with constant x, y, or z (x, y, z)
     Unzoom with p
  <P>
  :corners	Show the fitted values for the corners of the image
  :function type	Set the function for the fitted surface
  		(chebyshev, legendre)
  :show		Show the fitting parameters
  :xorder value	Set the x order  for the fitted surface
  :yorder value	Set the y order  for the fitted surface
  </PRE>
  </UL>
  <! EndSection:   'CURSOR COMMANDS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  A two dimensional function of the image coordinates is fitted to the user
  coordinates from the specified images;
  <P>
  <PRE>
  	user coordinate = function (column, line)
  <P>
  			or
  <P>
  		      z = s (x, y)
  </PRE>
  <P>
  The coordinates from all the input images may be combined in a single fit or
  the coordinates from each image may be fit separately.  If the
  coordinates from the input images are combined then the fitted function
  is recorded in the database under the specified name.  If
  the coordinates are fit separately the fitted function is recorded under
  a name formed by appending the image name to the specified root name.
  <P>
  When the task is interactive the user is first queried whether to perform
  the fitting interactively.  The user may answer "<TT>yes</TT>", "<TT>no</TT>", "<TT>YES</TT>", or "<TT>NO</TT>"
  to the query.  The lowercase responses apply only to the current fit
  and the uppercase responses apply to all remaining fits.  When the
  fitting is done interactively the user may change the fitted function and
  orders iteratively, delete individual coordinates or entire features,
  and graph the fit and residuals in a number ways.
  The CURSOR COMMANDS section describes the graphics cursor keystrokes
  which are available.  When selecting data for the graph axes the
  follow definitions apply:
  <P>
  <PRE>
  	x	Input image column positions
  	y	Input image line positions
  	z	Input user coordinates
  	s	Fitted user coordinates
  	r	Residuals (s - z)
  </PRE>
  <P>
  A very useful feature is zooming, deleting, or undeleting a subset of data
  points.  The subsets
  are defined as points with the same x, y, or z value as the point indicated
  by the cursor when typing (z)oom, (d)elete, or (u)ndelete.
  <P>
  When a satisfactory coordinate fit has been determined exit with the (q)uit
  key.  The user is asked if the fit is to be recorded in the database.
  <P>
  If a deletion list file is specified then the coordinates of any
  points deleted interactively are recorded in this file.  This file then can
  be read by subsequent fits to initially delete points with matching
  coordinates.  This is generally used when fitting a series of images
  non-interactively.
  <P>
  Information about the fitted function may be recorded.  Textual information
  is written to the specified log files (which may include the standard
  output STDOUT).  The last interactive plot or a default non-interactive
  plot is written the specified plot file which may be examined and spooled
  at a later time.
  <P>
  <P>
  FITCOORDS DATABASE
  <P>
  The FITCOORDS fits are stored in text files in the subdirectory given by
  the "<TT>database</TT>" parameter.  The name of the file is fc&lt;fitname&gt; where
  &lt;fitname&gt; is the specified fit name.  The database text file contains
  blocks of lines beginning with a time stamp followed by line with the
  "<TT>begin</TT>" keyword.  The value following "<TT>begin</TT>" is the fit name, which is
  often the name of the image used for the fit.  If there is more than one
  block with the same fit name then the last one is used.
  <P>
  The "<TT>task</TT>" keyword will has the value "<TT>fitcoords</TT>" and the "<TT>axis</TT>" keyword
  identifies the axis to which the surface fit applies.  An axis of 1 refers
  to the first or x axis (the first dimension of the image) and 2 refers to
  the second or y axis.
  <P>
  The "<TT>surface</TT>" keyword specifies the number of coefficients for the surface
  fit given in the following lines .  The surface fit is produced by an IRAF
  math package called "<TT>gsurfit</TT>".  The coefficients recorded in the database
  are intented to be internal to that package.  However the following
  describes how to interpret the coefficients.
  <P>
  The first 8 lines specify:
  <P>
  <PRE>
     function - Function type (1=chebyshev, 2=legendre)
       xorder - X "order" (highest power of x)
       yorder - Y "order" (highest power of y)
       xterms - Cross-term type (always 1 for FITCOORDS)
         xmin - Minimum x over which the fit is defined
         xmax - Maximum x over which the fit is defined
         ymin - Minimum y over which the fit is defined
         ymax - Maximum y over which the fit is defined
  </PRE>
  <P>
  The polynomial coefficients follow in array order with the x index
  varying fastest:
  <P>
  <PRE>
  	C00
  	C10
  	C20
  	...
  	C&lt;xorder-1&gt;0
  	C01
  	C11
  	C21
  	...
  	C&lt;xorder-1&gt;1
  	...
  	C&lt;xorder-1&gt;&lt;yorder-1&gt;
  </PRE>
  <P>
  The surface fitting functions have the form
  <P>
  <PRE>
  	fit(x,y) = Cmn * Pmn
  </PRE>
  <P>
  where the Cmn are the coefficients of the polynomials terms Pmn, and the Pmn
  are defined as follows:
  <P>
  <PRE>
  Chebyshev: Pmn = Pm(xnorm) * Pn(ynorm)
  <P>
  	   xnorm = (2 * x - (xmax + xmin)) / (xmax - xmin)
  	   ynorm = (2 * y - (ymax + ymin)) / (ymax - ymin)
  <P>
  	   P0(xnorm) = 1.0
  	   P1(xnorm) = xnorm
  	   Pm+1(xnorm) = 2.0 * xnorm * Pm(xnorm) - Pm-1(xnorm) 
  <P>
  	   P0(ynorm) = 1.0
  	   P1(ynorm) = ynorm
  	   Pn+1(ynorm) = 2.0 * ynorm * Pn(ynorm) - Pn-1(ynorm) 
  <P>
  Legendre:  Pmn = Pm(xnorm) * Pn(ynorm)
  <P>
  	   xnorm = (2 * x - (xmax + xmin)) / (xmax - xmin)
  	   ynorm = (2 * y - (ymax + ymin)) / (ymax - ymin)
  <P>
  	   P0(xnorm) = 1.0
  	   P1(xnorm) = xnorm
  	   Pm+1(xnorm) = ((2m+1)*xnorm*Pm(xnorm)-m*Pm-1(xnorm))/(m+1)   
  <P>
  	   P0(ynorm) = 1.0
  	   P1(ynorm) = ynorm
  	   Pn+1(ynorm) = ((2n+1)*ynorm*Pn(ynorm)-n*Pn-1(ynorm))/(n+1)   
  </PRE>
  <P>
  Notice that the x and y values are first normalized to the interval -1 to 1
  over the range of the surface as given by the xmin, xmax, ymin, and ymax
  elements of the database description.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  A number of strong arc lines are identified along one column of an arc
  calibration image "<TT>arc001</TT>".  The arc lines are then reidentified at every
  20th column.  A two dimensional dispersion solution is determined as follows:
  <P>
  	cl&gt; fitcoords arc001 fit.
  <P>
  The fitting is done interactively and deleted points are recorded.
  The fit is recorded under the name fit.arc001.  A set of similar arc
  calibrations are fit non-interactively, with the same points deleted,
  as follows:
  <P>
  	cl&gt; fitcoords arc* interactive=no
  <P>
  Several stellar spectra are identified at different positions along the slit
  and traced to other lines.  A fit to the geometric distortion is determined
  with the command:
  <P>
  	cl&gt; fitcoords star001,star003,star005 fitname=distortion combine=yes
  <P>
  In this case the coordinates from all the tracings are combined in a single
  fit called distortion.
  <P>
  The plots in the plot file are spooled to the standard plotting device as
  follows:
  <P>
  	cl&gt; gkimosaic plotfile
  <P>
  <B>Gkimosaic</B> is in the <B>plot</B> package.
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  transform
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'CURSOR COMMANDS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>