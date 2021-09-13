.. _pexamine:

pexamine — Interactively examine and edit a daophot database
============================================================

**Package: daophot**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  pexamine -- interactively examine or edit a photometry catalog
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  pexamine input output image
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The name of the input photometry catalog. Input may be either an APPHOT/DAOPHOT
  text database file or an STSDAS binary table database.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>The name of the edited output catalog. Output is either an APPHOT/DAOPHOT text
  database or an STSDAS binary table database depending on the file type of
  <I>input</I>. If output = "<TT></TT>" no output catalog is written.
  </DD>
  </DL>
  <DL>
  <DT><B>image</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD>The name of the input image corresponding to the input photometry catalog. If
  <I>image</I> is "<TT></TT>" no image will be attached to PEXAMINE and some interactive
  catalog examining commands will not be available.  All the catalog editing
  commands however are still available.
  </DD>
  </DL>
  <DL>
  <DT><B>deletions = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='deletions' Line='deletions = ""'>
  <DD>The name of an optional output deletions photometry catalog. Deletions is either
  an APPHOT/DAOPHOT text database or an STSDAS binary table database depending on
  the file type of <I>input</I>. If deletions is "<TT></TT>" no deletions file is written.
  </DD>
  </DL>
  <DL>
  <DT><B>photcolumns = "<TT>daophot</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='photcolumns' Line='photcolumns = "daophot"'>
  <DD>The list of standard photometry columns that are loaded when pexamine is run.
  The options are listed below.
  <DL>
  <DT><B>"<TT>daophot</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"daophot"'>
  <DD>The standard columns for the DAOPHOT package. The current list is GROUP, ID,
  XCENTER, YCENTER, MSKY, MAG, MERR, CHI, SHARP and NITER. If any of these columns
  are multi-valued, (as in the case of magnitudes measured through more than one
  aperture), the first value is selected. The standard list may easily be
  extended at user request.
  </DD>
  </DL>
  <DL>
  <DT><B>"<TT>apphot</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"apphot"'>
  <DD>The standard columns for the APPHOT package. The current list is ID, XCENTER,
  YCENTER, MSKY, MAG, and MERR. If any of these columns are multi-valued, (as in
  the case of magnitudes measured through more than one aperture), the first
  value is selected. The standard list may easily be extended at user request.
  </DD>
  </DL>
  <DL>
  <DT><B>user list</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='user' Line='user list'>
  <DD>A user supplied list of standard columns. Column names are listed in full in
  either upper or lower case letters, separated by commas. If more than one value
  of a multi-valued column is requested the individual values must be listed
  separately as in the following example ID, XCENTER, YCENTER, MAG[1], MERR[1],
  MAG[2], MERR[2].
  </DD>
  </DL>
  Photcolumns can be changed interactively from within PEXAMINE at the cost
  of rereading the database. 
  </DD>
  </DL>
  <DL>
  <DT><B>xcolumn = "<TT>mag</TT>" (magnitude), ycolumn = "<TT>merr</TT>" (magnitude error)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xcolumn' Line='xcolumn = "mag" (magnitude), ycolumn = "merr" (magnitude error)'>
  <DD>The names of the two columns which define the default X-Y plot. Xcolumn and
  ycolumn must be listed in <I>photcolumns</I> or <I>usercolumns</I> but may be
  changed interactively by the user. If either xcolumn or ycolumn is a
  multi-valued quantity and more than one value is listed in <I>photcolumns</I>
  or <I>usercolumns</I> then the desired value number must be specified explicitly
  in, e.g. MAG[2] or MERR[2].
  </DD>
  </DL>
  <DL>
  <DT><B>hcolumn = "<TT>mag</TT>" (magnitude)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='hcolumn' Line='hcolumn = "mag" (magnitude)'>
  <DD>The name of the column which defines the default histogram plot.  Hcolumn
  must be listed in <I>photcolumns</I> or <I>usercolumns</I> but may be changed
  interactively by the user. If hcolumn is a multi-valued quantity and more than
  one value is listed in <I>photcolumns</I> or <I>usercolumns</I> then the desired
  value must be specified explicitly in hcolumn, e.g. MAG[2].
  </DD>
  </DL>
  <DL>
  <DT><B>xposcolumn = "<TT>xcenter</TT>", yposcolumn = "<TT>ycenter</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xposcolumn' Line='xposcolumn = "xcenter", yposcolumn = "ycenter"'>
  <DD>The names of the two columns which define the X and Y coordinates in <I>image</I>
  of the objects in the catalog. This information is required if the image
  display and image cursor are to be used to visually identify objects in the
  image with objects in the catalog or if plots of image data are requested.
  Xposcolumn and yposcolumn must be listed in <I>photcolumns</I> or
  <I>usercolumns</I> but may be changed interactively by the user.
  </DD>
  </DL>
  <DL>
  <DT><B>usercolumns = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='usercolumns' Line='usercolumns = ""'>
  <DD>The list of columns loaded into memory in addition to the standard photometry
  columns <I>photcolumns</I>. The column names are listed in full in upper or
  lower case letters and separated by commas. Usercolumns can be changed
  interactively from within PEXAMINE at the cost of rereading the database. 
  </DD>
  </DL>
  <DL>
  <DT><B>first_star = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='first_star' Line='first_star = 1'>
  <DD>The index of the first object to be read out of the catalog.
  </DD>
  </DL>
  <DL>
  <DT><B>max_nstars = 5000</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='max_nstars' Line='max_nstars = 5000'>
  <DD>The maximum number of objects that are loaded into memory at task startup time,
  beginning at object <I>first_star</I>. If there are more than max_nstars in the
  catalog only the first max_nstars objects are read in.
  </DD>
  </DL>
  <DL>
  <DT><B>match_radius = 2.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='match_radius' Line='match_radius = 2.0'>
  <DD>The tolerance in pixels to be used for matching objects in the catalog with
  objects marked on the display with the image cursor.
  </DD>
  </DL>
  <DL>
  <DT><B>use_display = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='use_display' Line='use_display = yes'>
  <DD>Use the image display? Users without access to an image display should set
  use_display to "<TT>no</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>icommands = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='icommands' Line='icommands = ""'>
  <DD>The image display cursor. If null the standard image cursor is used whenever
  image cursor input is requested. A cursor file in the appropriate format may be
  substituted by specifying the name of the file. Also the image cursor may be
  changed to query the graphics device or the terminal by setting the environment
  variable "<TT>stdimcur</TT>" to "<TT>stdgraph</TT>" or "<TT>text</TT>" respectively.
  <DL>
  <DT><B>gcommands = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='gcommands' Line='gcommands = ""'>
  <DD>The graphics cursor. If null the standard graphics cursor is used whenever
  graphics cursor input is requested. A cursor file in the appropriate format may
  be substituted by specifying the name of the file.
  </DD>
  </DL>
  <DL>
  <DT><B>graphics = "<TT>stdgraph</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='graphics' Line='graphics = "stdgraph"'>
  <DD>The default graphics device.
  </DD>
  </DL>
  <P>
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Plotting parameters</H3>
  <! BeginSection: 'PLOTTING PARAMETERS'>
  <UL>
  <P>
  PEXAMINE supports five types of plots 1) an X-Y column plot 2) a histogram
  column plot 3) a radial profile plot 4) a surface plot and 5) a contour plot.
  Each supported plot type has its own parameter set which controls the
  appearance of the plot.  The names of the five parameter sets are listed below.
  <P>
  <PRE>
      cntrplot	Parameters for the contour plot
      histplot	Parameters for the column histogram plot
      radplot	Parameters for radial profile plot
      surfplot	Parameters for surface plot
      xyplot	Parameters for the X-Y column plot	
  </PRE>
  <P>
  The same  parameters dealing with graph formats occur in many of the parameter
  sets while some are specific only to one parameter set. In the summary below
  those common to more than one parameter set are shown only once. The characters
  in parenthesis are the graph key prefixes for the parameter sets in which the
  parameter occurs.
  <P>
  <DL>
  <DT><B>angh = -33., angv = 25.		(s)</B></DT>
  <! Sec='PLOTTING PARAMETERS' Level=0 Label='angh' Line='angh = -33., angv = 25.		(s)'>
  <DD>Horizontal and vertical viewing angles in degrees for surface plots.
  </DD>
  </DL>
  <DL>
  <DT><B>axes = yes				(s)</B></DT>
  <! Sec='PLOTTING PARAMETERS' Level=0 Label='axes' Line='axes = yes				(s)'>
  <DD>Draw axes along the edge of surface plots ?
  </DD>
  </DL>
  <DL>
  <DT><B>banner = yes 			 (chrsx)</B></DT>
  <! Sec='PLOTTING PARAMETERS' Level=0 Label='banner' Line='banner = yes 			 (chrsx)'>
  <DD>Add a standard banner to a graph ?  The standard banner includes the IRAF user
  and host identification and the date and time.
  </DD>
  </DL>
  <DL>
  <DT><B>box = yes 				(chrx)</B></DT>
  <! Sec='PLOTTING PARAMETERS' Level=0 Label='box' Line='box = yes 				(chrx)'>
  <DD>Draw graph box and axes ?
  </DD>
  </DL>
  <DL>
  <DT><B>ceiling = INDEF			(cs)</B></DT>
  <! Sec='PLOTTING PARAMETERS' Level=0 Label='ceiling' Line='ceiling = INDEF			(cs)'>
  <DD>Ceiling data value for contour and surface plots. A value of INDEF does not
  apply a ceiling.  In contour plots a value of 0. also does not apply a ceiling.
  </DD>
  </DL>
  <DL>
  <DT><B>dashpat = 528			(c)</B></DT>
  <! Sec='PLOTTING PARAMETERS' Level=0 Label='dashpat' Line='dashpat = 528			(c)'>
  <DD>Dash pattern for negative contours.
  </DD>
  </DL>
  <DL>
  <DT><B>fill = no (yes)			(c) (hrx)</B></DT>
  <! Sec='PLOTTING PARAMETERS' Level=0 Label='fill' Line='fill = no (yes)			(c) (hrx)'>
  <DD>Fill the output viewport regardless of the device aspect ratio ?
  </DD>
  </DL>
  <DL>
  <DT><B>floor = INDEF			(cs)</B></DT>
  <! Sec='PLOTTING PARAMETERS' Level=0 Label='floor' Line='floor = INDEF			(cs)'>
  <DD>Floor data value for contour and surface plots. A value of INDEF does not apply
  a floor. In contour plots a value of 0. also does not apply a floor.
  </DD>
  </DL>
  <DL>
  <DT><B>grid = no				(rx)</B></DT>
  <! Sec='PLOTTING PARAMETERS' Level=0 Label='grid' Line='grid = no				(rx)'>
  <DD>Draw grid lines at major tick marks ?
  </DD>
  </DL>
  <DL>
  <DT><B>interval = 0.0			(c)</B></DT>
  <! Sec='PLOTTING PARAMETERS' Level=0 Label='interval' Line='interval = 0.0			(c)'>
  <DD>Contour interval.  If 0.0, a contour interval is chosen which places 20 to 30
  contours spanning the intensity range of the image.
  </DD>
  </DL>
  <DL>
  <DT><B>label= no				(c)</B></DT>
  <! Sec='PLOTTING PARAMETERS' Level=0 Label='label' Line='label= no				(c)'>
  <DD>Label the major contours in the contour plot ?
  </DD>
  </DL>
  <DL>
  <DT><B>logx = no, logy = no		(rx) (hrx)</B></DT>
  <! Sec='PLOTTING PARAMETERS' Level=0 Label='logx' Line='logx = no, logy = no		(rx) (hrx)'>
  <DD>Plot the x or y axis logarithmically ? The default for histogram plots is to
  plot the y axis logarithmically.
  </DD>
  </DL>
  <DL>
  <DT><B>majrx=5, minrx=5, majry=5, minry=5	(chrx)</B></DT>
  <! Sec='PLOTTING PARAMETERS' Level=0 Label='majrx' Line='majrx=5, minrx=5, majry=5, minry=5	(chrx)'>
  <DD>Maximum number of major tick marks on each axis and number of minor tick marks
  between major tick marks.
  </DD>
  </DL>
  <DL>
  <DT><B>marker = "<TT>box</TT>"			(rx)</B></DT>
  <! Sec='PLOTTING PARAMETERS' Level=0 Label='marker' Line='marker = "box"			(rx)'>
  <DD>Marker to be drawn.  Markers are "<TT>point</TT>", "<TT>box</TT>", "<TT>cross</TT>", "<TT>plus</TT>", "<TT>circle</TT>",
  "<TT>hline</TT>", "<TT>vline</TT>" or "<TT>diamond</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>nbins = 512				(h)</B></DT>
  <! Sec='PLOTTING PARAMETERS' Level=0 Label='nbins' Line='nbins = 512				(h)'>
  <DD>The number of bins in, or resolution of, histogram plots.
  </DD>
  </DL>
  <DL>
  <DT><B>ncolumns = 21, nlines = 21		(cs)</B></DT>
  <! Sec='PLOTTING PARAMETERS' Level=0 Label='ncolumns' Line='ncolumns = 21, nlines = 21		(cs)'>
  <DD>Number of columns and lines used in contour and surface plots.
  </DD>
  </DL>
  <DL>
  <DT><B>ncontours = 5			(c)</B></DT>
  <! Sec='PLOTTING PARAMETERS' Level=0 Label='ncontours' Line='ncontours = 5			(c)'>
  <DD>Number of contours to be drawn. If 0, the contour interval may be specified,
  otherwise 20 to 30 nicely spaced contours are drawn. A maximum of 40 contours
  can be drawn.
  </DD>
  </DL>
  <DL>
  <DT><B>nhi = -1				(c)</B></DT>
  <! Sec='PLOTTING PARAMETERS' Level=0 Label='nhi' Line='nhi = -1				(c)'>
  <DD>If -1, highs and lows are not marked. If 0, highs and lows are marked on the
  plot. If 1, the intensity of each pixel is marked on the plot.
  </DD>
  </DL>
  <DL>
  <DT><B>rinner = 0, router = 8</B></DT>
  <! Sec='PLOTTING PARAMETERS' Level=0 Label='rinner' Line='rinner = 0, router = 8'>
  <DD>The inner and outer radius of the region whose radial profile is to be plotted.
  </DD>
  </DL>
  <DL>
  <DT><B>round = no				(chrx)</B></DT>
  <! Sec='PLOTTING PARAMETERS' Level=0 Label='round' Line='round = no				(chrx)'>
  <DD>Extend the axes up to "<TT>nice</TT>" values ?
  </DD>
  </DL>
  <DL>
  <DT><B>szmarker = 1			(rx)</B></DT>
  <! Sec='PLOTTING PARAMETERS' Level=0 Label='szmarker' Line='szmarker = 1			(rx)'>
  <DD>Size of mark except for points. A positive size less than 1 specifies a fraction
  of the device size. Values of 1, 2, 3, and 4 signify default sizes of increasing
  size.
  </DD>
  </DL>
  <DL>
  <DT><B>ticklabels = yes			(chrx)</B></DT>
  <! Sec='PLOTTING PARAMETERS' Level=0 Label='ticklabels' Line='ticklabels = yes			(chrx)'>
  <DD>Label the tick marks ?
  </DD>
  </DL>
  <DL>
  <DT><B>top_closed = no			(h)</B></DT>
  <! Sec='PLOTTING PARAMETERS' Level=0 Label='top_closed' Line='top_closed = no			(h)'>
  <DD>Include z2 in the top histogram bin ? Each bin of the histogram is a subinterval
  that is half open at the top. Top_closed decides whether those pixels with
  values equal to z2 are to be counted in the histogram. If top_closed is yes,
  the top bin will be larger than the other bins.
  </DD>
  </DL>
  <DL>
  <DT><B>x1 = INDEF, x2 = INDEF, y1 = INDEF, y2 = INDEF	(hrx)</B></DT>
  <! Sec='PLOTTING PARAMETERS' Level=0 Label='x1' Line='x1 = INDEF, x2 = INDEF, y1 = INDEF, y2 = INDEF	(hrx)'>
  <DD>Range of graph along each axis.  If INDEF the range is determined from the data
  range. The default y1 for histogram plots is 0.
  </DD>
  </DL>
  <DL>
  <DT><B>zero = 0.				(c)</B></DT>
  <! Sec='PLOTTING PARAMETERS' Level=0 Label='zero' Line='zero = 0.				(c)'>
  <DD>Grayscale value of the zero contour, i.e., the value of a zero point shift
  to be applied to the image data before plotting. Does not affect the values
  of the floor and ceiling parameters.
  </DD>
  </DL>
  <DL>
  <DT><B>z1 = INDEF, z2 = INDEF		(h)</B></DT>
  <! Sec='PLOTTING PARAMETERS' Level=0 Label='z1' Line='z1 = INDEF, z2 = INDEF		(h)'>
  <DD>Range of pixel values to be used in histogram. INDEF values default to the
  range in the region being histogramed.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PLOTTING PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  PEXAMINE is a general purpose tool for interactively examining and editing
  photometry catalogs produced by the APPHOT or DAOPHOT packages. It is intended
  to aid the user in assessing the accuracy of the photometry, in diagnosing
  problems with particular catalog objects, in searching the photometry data for
  relationships between the computed quantities, and in editing the catalog
  based on those observed relationships. PEXAMINE is intended to complement the
  more batch oriented editing facilities of the PSELECT task.
  <P>
  PEXAMINE takes the input catalog <I>input</I> and the corresponding image
  <I>image</I> (if defined) and produces an output catalog of selected objects
  <I>output</I> (if defined) and an output catalog of deleted objects
  <I>deletions</I> (if defined). The input catalog may be either an APPHOT/DAOPHOT
  text database or an ST binary table database. The file type of the output
  catalogs <I>output</I> and <I>deletions</I> is the same as that of <I>input</I>.
  <P>
  READING IN THE DATA
  <P>
  PEXAMINE reads the column data specified by <I>photcolumns</I> and
  <I>usercolumns</I> for up to <I>max_nstars</I> into memory. If there are more
  than <I>max_nstars</I> in the input catalog only the data for the first
  <I>max_nstars</I> is read. The <I>photcolumns</I> parameter defines the list of
  standard photometry columns to be loaded. If "<TT>daophot</TT>" or "<TT>apphot</TT>" is selected
  then the standard columns are GROUP, ID, XCENTER, YCENTER, MSKY, MAG, MERR,
  CHI, SHARP and NITER and ID, XCENTER, YCENTER, MSKY, MAG and MERR respectively.
  Otherwise the user must set <I>photcolumns</I> to his or her own preferred list
  of standard photometry columns. Non-standard columns may also be specified
  using the parameter <I>usercolumns</I>. Valid column lists contain the full
  names of the specified columns in upper or lower case letters, separated by
  commas. Either <I>photcolumns</I> or <I>usercolumns</I> may be redefined
  interactively by the user after the task has started up, but only at the
  expense of rereading the data from <I>input</I>.
  <P>
  PEXAMINE will fail to load a specified column if that column is not in the
  photometry database, is of a datatype other than integer or real, or adding
  that column would exceed the maximum number of columns limit currently set at
  twenty. The user can interactively examine the list of requested and loaded
  standard photometry columns, as well as list all the columns in the input after
  the task has started up.
  <P>
  GRAPHICS AND IMAGE COMMAND MODE
  <P>
  PEXAMINE accepts commands either from the graphics cursor <I>gcommands</I>
  (graphics command mode) or the image display cursor <I>icommands</I> if available
  (image command mode). PEXAMINE starts up in graphics command mode, but all the
  interactive commands are accessible from both modes and the user can switch
  modes at any time assuming that the <I>use_display</I> parameter to "<TT>yes</TT>".
  <P>
  PEXAMINE interprets the cursor position in graphics mode differently from how
  it interprets it in image command mode. In graphics command mode the cursor
  coordinates are the position of the cursor in the current plot, whereas in
  image command mode they are the x and y coordinates of the cursor in the
  displayed image. For example, if the user issues a command to PEXAMINE to
  locate the object in the catalog nearest the point in the current X-Y plot
  marked by the graphics cursor, PEXAMINE does so by searching the data for the
  object whose values of <I>xcolumn</I> and <I>ycolumn</I> most closely match those
  of the current cursor position. If the user issues a command  to PEXAMINE to
  locate the object in the catalog corresponding to the object marked on the
  image display with the image cursor, PEXAMINE does so by searching the data for
  the object whose values of <I>xposcolumn</I> and <I>yposcolumn</I> most closely
  match and fall within <I>match_radius</I> of the current cursor position.
  <P>
  Input to PEXAMINE is through single keystroke commands or colon commands.
  Keystroke commands are simple commands that may optionally use the cursor
  position but otherwise require no arguments. The PEXAMINE keystroke commands
  fall into three categories, basic commands, data examining commands and data
  editing commands, all described in detail in the following sections. Colon
  commands take an optional argument and function differently depending on the
  presence or absence of that argument. When the argument is absent colon
  commands are used to display the current value of a parameter or list of
  parameters. When the argument is present they change their current value to
  that argument. The basic colon commands are described in detail below. 
  <P>
  BASIC KEYSTROKE COMMANDS
  <P>
  These keystroke commands are used to display the help page, switch from
  graphics to image command mode and quit the task.
  <P>
  <DL>
  <DT><B>?</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='?'>
  <DD>Page through the help for the PEXAMINE task
  </DD>
  </DL>
  <DL>
  <DT><B>:</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line=':'>
  <DD>Execute a PEXAMINE colon command.
  </DD>
  </DL>
  <DL>
  <DT><B>g</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='g' Line='g'>
  <DD>Change to graphics command mode. Throughout PEXAMINE graphics command mode is
  the default. All PEXAMINE commands are available in graphics command mode.
  </DD>
  </DL>
  <DL>
  <DT><B>i</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='i' Line='i'>
  <DD>Change to image command mode. All the PEXAMINE commands are available in image
  command mode. However if <I>use_display</I> is no and the image cursor has not
  been aliased to the standard input or a text file image command mode is
  disabled.
  </DD>
  </DL>
  <DL>
  <DT><B>q</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='q' Line='q'>
  <DD>Quit PEXAMINE without writing an output catalog. PEXAMINE queries the user for
  confirmation of this option.
  </DD>
  </DL>
  <DL>
  <DT><B>e</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='e' Line='e'>
  <DD>Quit PEXAMINE and write the output catalog.
  </DD>
  </DL>
  <P>
  DATA EXAMINING COMMANDS
  <P>
  The data examining commands fall into two categories, those that examine the
  catalog data including <TT>'l'</TT> (catalog listing), <TT>'o'</TT> (object listing), <TT>'x'</TT> (Y
  column versus X column plot) and <TT>'h'</TT> (histogram column plot) commands, and
  those which examine the image data around specific catalog objects including
  <TT>'r'</TT> (radial profile plotting), <TT>'s'</TT> (surface plotting), <TT>'c'</TT> (contour plotting)
  and <TT>'m'</TT> (pixel dumping). The latter group require that <I>image</I> be defined.
  A brief summary of each data examining command is given below.
  <DL>
  <DT><B>l</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='l' Line='l'>
  <DD>Print out the name, datatype, and units for all the columns in the input
  catalog. The list command can be used to check the contents of the input
  catalog and/or determine why a particular column was not loaded.
  </DD>
  </DL>
  <DL>
  <DT><B>o</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='o' Line='o'>
  <DD>Print out the names and values of the stored columns of the object nearest the
  cursor. In graphics mode the current plot type must be X-Y. In image command
  mode the object nearest the cursor must also be no more than <I>match-radius</I>
  pixels away from the image cursor to be found. If an object is found and the
  current plot type is X-Y the graphics cursor is moved to the position of the
  selected object in the X-Y plot.
  </DD>
  </DL>
  <DL>
  <DT><B>x</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='x' Line='x'>
  <DD>Plot the data in <I>ycolumn</I> versus the data in <I>xcolumn</I> excluding any
  already deleted points and identifying objects marked for deletion with a
  cross. X-Y plotting is undefined if <I>xcolumn</I> or <I>ycolumn</I> is undefined.
  </DD>
  </DL>
  <DL>
  <DT><B>h</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='h' Line='h'>
  <DD>Plot the histogram of the data in <I>hcolumn</I> excluding any already deleted
  points and those marked for deletion. Histogram plotting is disabled if
  <I>hcolumn</I> is undefined.
  </DD>
  </DL>
  <DL>
  <DT><B>r</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='r' Line='r'>
  <DD>Plot the radial profile of the object nearest the cursor including only pixels
  within a distance of <I>rinner</I> and <I>router</I> of the object center. Radial
  profile plotting is disabled if <I>image</I> or <I>xposcolumn</I> or
  <I>yposcolumn</I> is undefined.
  </DD>
  </DL>
  <DL>
  <DT><B>s</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='s' Line='s'>
  <DD>Plot the surface plot of the object nearest the cursor including only pixels
  within an image section <I>ncols</I> by <I>nlines</I> around the object center.
  Surface plotting is disabled if <I>image</I> or <I>xposcolumn</I> or
  <I>yposcolumn</I> is undefined.
  </DD>
  </DL>
  <DL>
  <DT><B>c</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='c' Line='c'>
  <DD>Plot the contour plot of the object nearest the cursor including only pixels
  within an image section <I>ncols</I> by <I>nlines</I> around the object center.
  Contour plotting is disabled if <I>image</I> or <I>xposcolumn</I> or
  <I>yposcolumn</I> is undefined.
  </DD>
  </DL>
  <DL>
  <DT><B>m</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='m' Line='m'>
  <DD>Dump the pixel values of a grid of 10 by 10 pixels around the object nearest
  the cursor. Pixel value dumping is disabled if <I>image</I> or <I>xposcolumn</I>
  or <I>yposcolumn</I> is undefined.
  </DD>
  </DL>
  <DL>
  <DT><B>p</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='p' Line='p'>
  <DD>Replot the current graph.
  </DD>
  </DL>
  <P>
  DATA EDITING COMMANDS
  <P>
  Data points can be deleted from the catalog in either graphics command mode or
  image command mode. In graphics command mode the graphics cursor and either the
  X-Y or histogram plot is used to delete points. In image command mode the image
  cursor and the displayed image are used to delete points. A data point has three
  possible states good, marked for deletion and deleted. Any one of the keystroke
  commands <TT>'d'</TT> (delete point), <TT>'('</TT> (delete points with x less than x cursor),
  <TT>')'</TT> (delete points with x greater than x cursor, <TT>'^'</TT> (delete points with y &gt; y
  cursor), <TT>'v'</TT> (delete points with y &lt; y cursor) or <TT>'b'</TT> (delete points in a box)
  can be used to mark points for deletion. The <TT>'f'</TT> key is used to actually delete
  the points and replot the data. In between marking the points for deletion and
  actually deleting the marked points the <TT>'t'</TT> (toggle) key can be used to undelete
  the last set marked. The full list of the data editing keystroke commands is
  given below.
  <P>
  <DL>
  <DT><B>z</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='z' Line='z'>
  <DD>Undelete not just unmark all the data points replot.
  </DD>
  </DL>
  <DL>
  <DT><B>f</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='f' Line='f'>
  <DD>Delete points marked for deletion and replot. Points marked for deletion but
  not actually deleted will be written to the output catalog and not written to
  the deletions catalog.
  </DD>
  </DL>
  <DL>
  <DT><B>d</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='d' Line='d'>
  <DD>Mark the point nearest the cursor for deletion.
  </DD>
  </DL>
  <DL>
  <DT><B>u</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='u' Line='u'>
  <DD>Undelete the marked point nearest the cursor.
  </DD>
  </DL>
  <DL>
  <DT><B>(</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='('>
  <DD>Mark all points with x values less than the x value of the cursor for deletion.
  In graphics command mode points can only be marked for deletion if the current
  plot type is "<TT>xyplot</TT>" or "<TT>histplot</TT>". In image command mode <I>xposcolumn</I> and
  <I>yposcolumn</I> must be defined before points can be marked for deletion.
  </DD>
  </DL>
  <DL>
  <DT><B>)</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line=')'>
  <DD>Mark all points with x values greater than the x value of the cursor for
  deletion.  In graphics command mode points can only be marked for deletion if
  the current plot type is "<TT>xyplot</TT>" or "<TT>histplot</TT>". In image command mode
  <I>xposcolumn</I> and <I>yposcolumn</I> must be defined before points can be
  marked for deletion.
  </DD>
  </DL>
  <DL>
  <DT><B>v</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='v' Line='v'>
  <DD>Mark all points with y values less than the y value of the cursor for deletion.
  In graphics command mode points can only be marked for deletion if the current
  plot type is "<TT>xyplot</TT>". In image command mode <I>xposcolumn</I> and
  <I>yposcolumn</I> must be defined before points can be marked for deletion.
  </DD>
  </DL>
  <DL>
  <DT><B>^</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='^'>
  <DD>Mark all points with y values greater than the y value of the cursor for
  deletion.  In graphics command mode points can only be marked for deletion if
  the current plot type is "<TT>xyplot</TT>". In image command mode <I>xposcolumn</I> and
  <I>yposcolumn</I> must be defined before points can be marked for deletion.
  </DD>
  </DL>
  <DL>
  <DT><B>b</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='b' Line='b'>
  <DD>Mark all points within a box whose lower left and upper right hand corners are
  marked by the cursor for deletion. In graphics mode points can only be marked
  for deletion if the current plot type is "<TT>xyplot</TT>". In image command mode
  <I>xposcolumn</I> and <I>yposcolumn</I> must be defined before points can be
  marked for deletion.
  </DD>
  </DL>
  <DL>
  <DT><B>t</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='t' Line='t'>
  <DD>Toggle between marking points for deletion or undeletion. The default is to
  mark points for deletion.
  </DD>
  </DL>
  <P>
  BASIC COLON COMMANDS
  <P>
  All the PEXAMINE parameters can be changed interactively with colon commands,
  including those which determine which data is read in, which data is plotted
  and the parameters of each plot. A brief description of the basic commands is
  given here. The full list is given in the following section.
  <P>
  <DL>
  <DT><B>:photcolumns [col1,col2,...]</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line=':photcolumns [col1,col2,...]'>
  <DD>Show or set the list of requested standard photometry columns and the list
  of loaded photometry columns. If the user supplies a new list of columns the
  data will be reread from disk.
  </DD>
  </DL>
  <DL>
  <DT><B>:usercolumns [col1,col2,...]</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line=':usercolumns [col1,col2,...]'>
  <DD>Show or set the list of requested user columns and the list of loaded user
  columns. If the user supplies a new list of columns the data will be reread
  from disk.
  </DD>
  </DL>
  <DL>
  <DT><B>:xcolumn [colname]</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line=':xcolumn [colname]'>
  <DD>Show or set the name of the column to be plotted along the x axis of the X-Y
  plot.
  </DD>
  </DL>
  <DL>
  <DT><B>:ycolumn [colname]</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line=':ycolumn [colname]'>
  <DD>Show or set the name of the column to be plotted along the y axis of the X-Y
  plot.
  </DD>
  </DL>
  <DL>
  <DT><B>:hcolumn [colname]</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line=':hcolumn [colname]'>
  <DD>Show or set the name of the column to be whose histogram is to be plotted.
  </DD>
  </DL>
  <DL>
  <DT><B>:eparam [cntrplot/histplot/radplot/surfplot/xyplot]</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line=':eparam [cntrplot/histplot/radplot/surfplot/xyplot]'>
  <DD>Review or edit the list of parameters for the various plot types.
  </DD>
  </DL>
  <DL>
  <DT><B>:unlearn [cntrplot/histplot/radplot/surfplot/xyplot]</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line=':unlearn [cntrplot/histplot/radplot/surfplot/xyplot]'>
  <DD>Return the list of parameters for the various plot types to their default
  values.
  </DD>
  </DL>
  <DL>
  <DT><B>:x y key cmd</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line=':x y key cmd'>
  <DD>Execute any defined keystroke "<TT>key</TT>" supplying the appropriate x and y value in
  place of the cursor position. In graphics command mode the x and y position are
  assumed to be the position in the current graph. In image command mode the x
  and y position are assumed to be the x and y coordinate in the image display.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Commands</H3>
  <! BeginSection: 'COMMANDS'>
  <UL>
  <P>
  <PRE>
  	PEXAMINE Interactive Cursor Keystroke Commands
  <P>
                     Basic Commands
  <P>
  ?	Print help for the PEXAMINE task
  :	PEXAMINE colon commands
  g	Activate the graphics cursor
  i	Activate the image cursor
  e	Exit PEXAMINE and save the edited catalog
  q	Quit PEXAMINE and discard the edited catalog
  <P>
  		   Data Examining Commands
  <P>
  l	List the name, datatype and units for all columns in the catalog 	
  o	Print out the names and values of the stored columns for the
  	    object nearest the cursor
  x	Replot the current y column versus the current x column
  h	Replot the current histogram
  r	Plot the radial profile of the object nearest the cursor
  s	Plot the surface of the object nearest the cursor
  c	Plot the contour plot of the object nearest the cursor
  m	Print the data values of the object nearest the cursor
  p	Replot the current graph
  <P>
                     Data Editing Commands
  <P>
  z	Reinitialize the data by removing all deletions and replot
  d	Mark the point nearest the cursor for deletion
  u	Undelete the marked point nearest the cursor
  t	Toggle between marking points for deletion or undeletion
  (	Mark points with X &lt; X (cursor) for deletion or undeletion
  )	Mark points with X &gt; X (cursor) for deletion or undeletion
  v	Mark points with Y &lt; Y (cursor) for deletion or undeletion
  ^	Mark points with Y &gt; Y (cursor) for deletion or undeletion
  b	Mark points inside a box for deletion or undeletion
  f	Actually delete the marked points and replot
  <P>
  <P>
  	      PEXAMINE Interactive Colon Commands
  <P>
  :xcolumn	  [name]	     Show/set the X-Y plot X axis quantity
  :ycolumn	  [name]	     Show/set the X-Y plot Y axis quantity
  :hcolumn	  [name]	     Show/set the histogram plot quantity  
  :photcolumns	  [col1,col2,...]    Show/set the list of photometry columns
  :usercolumns	  [col1,col2,...]    Show/set the list of user columns
  :delete		  [yes/no]	     Delete or undelete points
  :eparam		  [x/h/r/s/c]	     Edit/unlearn the specified plot pset
      or
  :unlearn
  <P>
  <P>
  	     PEXAMINE Interactive X-Y Plotting Commands
  <P>
  :x1	    [value]	  Left  world x-coord if not autoscaling
  :x2 	    [value]	  Right world x-coord if not autoscaling
  :y1         [value]	  Lower world y-coord if not autoscaling
  :y2         [value]	  Upper world y-coord if not autoscaling
  :szmarker   [value]	  Marker size
  :marker [point|box|plus|cross|circle|diamond|hline|vline]    Marker type
  :logx       [yes/no]	  Log scale the x axis?
  :logy       [yes/no]      Log scale the y axis?
  :box        [yes/no]      Draw box around periphery of window?
  :ticklabels [yes/no]	  Label tick marks?
  :grid       [yes/no]	  Draw grid lines at major tick marks? 
  :majrx      [value]	  Number of major divisions along x axis
  :minrx      [value]	  Number of minor divisions along x axis
  :majry      [value]	  Number of major divisions along y axis
  :minry      [value]	  Number of minor divisions along y axis
  :round      [yes/no]      Round axes to nice values?
  :fill       [yes/no]      Fill viewport vs enforce unity aspect ratio?
  <P>
  <P>
  	PEXAMINE Interactive Histogram Plotting Commands
  <P>
  :nbins	    [value]	  Number of bins in the histogram
  :z1	    [value]	  Minimum histogram intensity
  :z2	    [value]	  Maximum histogram intensity
  :top_closed [y/n]	  Include z in the top bin?
  :x1	    [value]	  Left  world x-coord if not autoscaling
  :x2	    [value]	  Right world x-coord if not autoscaling
  :y1         [value]	  Lower world y-coord if not autoscaling
  :y2         [value]	  Upper world y-coord if not autoscaling
  :logy       [yes/no]      Log scale the y axis?
  :box        [yes/no]      Draw box around periphery of window?
  :ticklabels [yes/no]	  Label tick marks?
  :majrx      [value]	  Number of major divisions along x axis
  :minrx      [value]	  Number of minor divisions along x axis
  :majry      [value]	  Number of major divisions along y axis
  :minry      [value]	  Number of minor divisions along y axis
  :round      [yes/no]      Round axes to nice values?
  :fill       [yes/no]      Fill viewport vs enforce unity aspect ratio?
  <P>
  	PEXAMINE Interactive Radial Profile Plotting Commands
  <P>
  :rinner	    [value]	  Inner radius of the region to be plotted
  :router	    [value]	  Outer radius of the region to be plotted
  :x1	    [value]	  Left  world x-coord if not autoscaling
  :x2 	    [value]	  Right world x-coord if not autoscaling
  :y1         [value]	  Lower world y-coord if not autoscaling
  :y2         [value]	  Upper world y-coord if not autoscaling
  :szmarker   [value]	  Marker size
  :marker [point|box|plus|cross|circle|diamond|hline|vline]    Marker type
  :logx       [yes/no]	  Log scale the x axis?
  :logy       [yes/no]      Log scale the y axis?
  :box        [yes/no]      Draw box around periphery of window?
  :ticklabels [yes/no]	  Label tick marks?
  :grid       [yes/no]	  Draw grid lines at major tick marks? 
  :majrx      [value]	  Number of major divisions along x axis
  :minrx      [value]	  Number of minor divisions along x axis
  :majry      [value]	  Number of major divisions along y axis
  :minry      [value]	  Number of minor divisions along y axis
  :round      [yes/no]      Round axes to nice values?
  :fill       [yes/no]      Fill viewport vs enforce unity aspect ratio?
  <P>
  <P>
  	PEXAMINE Interactive Surface Plotting Commands
  <P>
  :ncolumns   [value]	  Number of columns to be plotted
  :nlines	    [value]	  Number of lines to be plotted
  :axes	    [yes/no]	  Draw axes?
  :angh	    [value]	  Horizontal viewing angle
  :angv	    [value]	  Vertical viewing angle
  :floor	    [value]	  Minimum value to be plotted
  :ceiling    [value]	  Maximum value to be plotted
  <P>
  <P>
  	PEXAMINE Interactive Contour Plotting Commands
  <P>
  :ncolumns   [value]	  Number of columns to be plotted
  :nlines	    [value]	  Number of lines to be plotted
  :floor	    [value]	  Minimum value to be plotted
  :ceiling    [value]	  Maximum value to be plotted
  :zero	    [value]       Grayscale value of zero contour
  :ncontours  [value]	  Number of contours to be drawn
  :interval   [value]       Contour interval
  :nhi	    [value]       Hi/low marking option
  :dashpat    [value]       Bit pattern for generating dashed lines
  :label      [yes/no]      Label major contours with their values?
  :box        [yes/no]      Draw box around periphery of window?
  :ticklabels [yes/no]	  Label tick marks?
  :majrx      [value]	  Number of major divisions along x axis
  :minrx      [value]	  Number of minor divisions along x axis
  :majry      [value]	  Number of major divisions along y axis
  :minry      [value]	  Number of minor divisions along y axis
  :round      [yes/no]      Round axes to nice values?
  :fill       [yes/no]      Fill viewport vs enforce unity aspect ratio?
  </PRE>
  <P>
  </UL>
  <! EndSection:   'COMMANDS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Examine and edit an APPHOT aperture photometry catalog and a DAOPHOT
  allstar catalog without either attaching the associated image or using the
  image display.
  <P>
  <PRE>
      pt&gt; pexamine ypix.mag.1 ypix.mag.ed use_display-
  <P>
  	... a plot of magnitude error versus magnitude appears on
  	    the screen and the graphics cursor comes up ready to accept
  	    commands
  <P>
  	... the user sees a generally smooth trend of increasing
  	    magnitude error with increasing magnitude except for a
  	    single deviant point at the bright end of the plot
  <P>
  	... the user decides to remove the deviant point using the
  	    <TT>'d'</TT> keystroke command to mark the point and the <TT>'f'</TT>
  	    keystroke command to actually delete and replot the graph
  <P>
  	... after examining the plot further the user decides to delete
  	    all objects for which the magnitude error is &gt; 0.1 magnitudes
  	    using the <TT>'^'</TT> keystroke command, followed by the <TT>'f'</TT>
  	    keystroke command to actually replot and delete the data.
  <P>
  	... after deciding that this new plot is satisfactory the user
  	    issues the <TT>'e'</TT> keystroke command to exit pexamine and save
  	    the good data in m92.mag.ed
  <P>
      pt&gt; pexamine ypix.als.1 ypix.als.ed use_display-
  <P>
  	... a plot of magnitude error versus magnitude appears on the
  	    screen and the graphics cursor comes up ready to accept
  	    commands
  <P>
  	... after looking at the plot the user decides that what they
  	    really want to see is a plot of the goodness of fit parameter
  	    chi versus magnitude
  <P>
  	... the user issues the colon command :ycol chi followed by <TT>'p'</TT>
  	    keystroke command to replot the data
  <P>
  	... the user sees a generally smooth trend of increasing
  	    chi with increasing magnitude 
  <P>
  	... after examining the plot further the user decides to delete
  	    all objects for which the chi value  &gt; 2.0  and the
  	    magnitude is &gt; 25 using the <TT>'^'</TT> key and <TT>')'</TT> keystroke
  	    commands followed by <TT>'f'</TT> to save the deletions and replot
  	    the data
  <P>
  	... after deciding that this new plot is satisfactory the user
  	    issues the <TT>'e'</TT> keystroke command to exit pexamine and save
  	    the good data in m92.als.ed
  </PRE>
  <P>
  2. Examine and edit a DAOPHOT allstar catalog using the subtracted image, the
  original image and the image display.
  <P>
  <PRE>
  	pt&gt; display ypix.sub.1 1
  <P>
  	    ... display the subtracted image
  <P>
  	pt&gt; pexamine ypix.als.1 ypix.als.ed dev$ypix xcol=mag ycol=chi
  <P>
  	... a plot of the goodness of fit versus magnitude appears
  	    on the terminal and the graphics cursor comes up ready to
  	    accept commands
  <P>
  	... the user notices some very anomalous chi values and decides
  	    to see if these correspond to objects which have poor
  	    subtraction on the displayed image
  <P>
  	... the user switches to image command mode by tapping the <TT>'i'</TT>
  	    key, moves to the first poorly subtracted object and taps
  	    the <TT>'o'</TT> key
  <P>
  	... a list of the values of the loaded columns including chi
  	    appears in the text window , the program switches to graphics
  	    mode and places the graphics cursor on the corresponding
  	    point in the X-Y plot
  <P>
  	... the point in question indeed has a very high chi value
  	    and the user decides to try and investigate the reason for the
  	    anomalous value
  <P>
  	... the user taps the <TT>'r'</TT> key to get a radial profile of the
  	    object in the original image
  <P>
  	... after carefully examining the profile it appears that the
  	    object's profile is too broad and that it is not a star
  <P>
  	... the user switches back to the X-Y plot with the <TT>'x'</TT> key,
  	    marks the point with the <TT>'d'</TT> key and saves the deletions
  	    and replots with the <TT>'f'</TT> key.
  <P>
  	... the user goes back to image command mode with the <TT>'i'</TT> key
  	    and begins investigating the next object
  <P>
  	... finally after examining the image and making all the changes
  	    the user decides to quit and save the changes with the <TT>'e'</TT> key
  <P>
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  <P>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  <P>
  INDEF valued points cannot be accessed by PEXAMINE. INDEF valued points should
  be removed from the input catalog with PSELECT prior to entering PEXAMINE.
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  ptools.pselect, ptools.txselect,ptools.tselect
  <P>
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'PLOTTING PARAMETERS' 'DESCRIPTION' 'COMMANDS' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
