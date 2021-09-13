autoidentify — Automatically identify lines and fit dispersion
==============================================================

**Package: onedspec**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>autoidentify (Jan96)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.onedspec</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>autoidentify (Jan96)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>autoidentify</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  autoidentify -- Automatically identify lines and fit dispersion
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_summary">SUMMARY</A></H2>
  <! BeginSection: 'SUMMARY'>
  <UL>
  Spectral lines are automatically identified from a list of coordinates
  by pattern matching.  The identified lines are then used to fit a
  dispersion function which is written to a database for later use
  in dispersion calibration.  After a solution is found the identified
  lines and dispersion function may be examined interactively.
  </UL>
  <! EndSection:   'SUMMARY'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  autoidentify images crval cdelt
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_images">images</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>List of images containing one dimensional spectra in which to identify
  spectral lines and fit dispersion functions.  For two and three dimensional
  spectral and spatial data one may use an image section to select a one
  dimensional spectral vector or use the <I>section</I> parameter.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_crval">crval, cdelt</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='crval' Line='crval, cdelt'>
  <DD>These parameters specify an approximate coordinate value and coordinate
  interval per pixel.  They may be specified as numerical values, INDEF, or
  image header keyword names whose values are to be used.  The coordinate
  reference value is for the pixel specified by the parameter
  <I>aidpars.crpix</I>.  The default reference pixel is INDEF which means the
  middle of the spectrum.  By default only the magnitude of the coordinate
  interval is used and the search will include both increasing and decreasing
  coordinate values with increasing pixel values.  If one or both of these
  parameters are specified as INDEF the search for a solution will be slower
  and more likely to fail.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_coordlist">coordlist = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='coordlist' Line='coordlist = ""'>
  <DD>Coordinate list consisting of an list of spectral line coordinates.
  A comment line of the form "<TT># units &lt;units&gt;</TT>", where &lt;units&gt; is one of the
  understood units names, defines the units of the coordinate list.  If no units
  are specified then Angstroms are assumed.
  The line list is used for both the final identifications and for the set of
  lines to use in the automatic search.  A restricted search list may be
  specified with the parameter <I>aidpars.reflist</I>.  The line list may
  contain a comment line of the form "<TT># Spectrum &lt;name&gt;</TT>", where &lt;name&gt; is a
  filename containing a reference spectrum.  The reference spectrum will be
  used in selecting the strong lines for the automatic search.  A reference
  spectrum may also be specified with the parameter <I>aidpars.refspec</I>.
  <P>
  Some standard line lists are available in the directory "<TT>linelists$</TT>".
  See the help topic <I>linelists</I> for the available line lists.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_units">units = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='units' Line='units = ""'>
  <DD>The units to use if no database entry exists.  The units are specified as
  described in
  <P>
  <PRE>
      cl&gt; help onedspec.package section=units
  </PRE>
  <P>
  If no units are specified and a coordinate list is used then the units of
  the coordinate list are selected.  If a database entry exists then the
  units defined there override both this parameter and the coordinate list.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interactive">interactive = yes (no|yes|NO|YES)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = yes (no|yes|NO|YES)'>
  <DD>After automatically identifying the spectral lines and dispersion function
  review and modify the solution interactively?  If "<TT>yes</TT>" a query is given
  for each spectrum providing the choice of interactive review.  The
  query may be turned off during execution.  If "<TT>YES</TT>" the interactive review
  is entered automatically without a query.  The interactive, graphical
  review is the same as the task <B>identify</B> with a few restriction.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_aidpars">aidpars = "<TT></TT>" (parameter set)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='aidpars' Line='aidpars = "" (parameter set)'>
  <DD>Parameter set for the automatic line identification algorithm.  The
  parameters are described in the help topic <B>aidpars</B>.
  </DD>
  </DL>
  <P>
  For two and three dimensional spectral images the following parameters are
  used to select a one dimensional spectrum.
  <DL>
  <DT><B><A NAME="l_section">section = "<TT>middle line</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='section' Line='section = "middle line"'>
  <DD>If an image is not one dimensional or specified as a one dimensional image
  section then the image section given by this parameter is used.  The
  section defines a one dimensional spectrum.  The dispersion direction is
  derived from the vector direction.
  <P>
  The section parameter may be specified directly as an image section or
  in one of the following forms
  <P>
  <PRE>
  line|column|x|y|z first|middle|last|# [first|middle|last|#]]
  first|middle|last|# [first|middle|last|#] line|column|x|y|z
  </PRE>
  <P>
  where each field can be one of the strings separated by | except for #
  which is an integer number.  The field in [] is a second designator which
  is used with three dimensional data.  Abbreviations are allowed though
  beware that <TT>'l'</TT> is not a sufficient abbreviation.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nsum">nsum = "<TT>1</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nsum' Line='nsum = "1"'>
  <DD>Number of lines, columns, or bands across the designated dispersion axis to
  be summed when the image is a two or three dimensional image.
  It does not apply to multispec format spectra.  If the image is three
  dimensional an optional second number can be specified for the higher
  dimensional axis  (the first number applies to the lower axis number and
  the second to the higher axis number).  If a second number is not specified
  the first number is used for both axes.
  </DD>
  </DL>
  <P>
  The following parameters are used in finding spectral lines.
  <DL>
  <DT><B><A NAME="l_ftype">ftype = "<TT>emission</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ftype' Line='ftype = "emission"'>
  <DD>Type of spectral lines to be identified.  The possibly abbreviated choices are
  "<TT>emission</TT>" and "<TT>absorption</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fwidth">fwidth = 4.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fwidth' Line='fwidth = 4.'>
  <DD>Full-width at the base (in pixels) of the spectral lines to be identified.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_cradius">cradius = 5.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cradius' Line='cradius = 5.'>
  <DD>The maximum distance, in pixels, allowed between a line position
  and the initial estimate when defining a new line.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_threshold">threshold = 0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='threshold' Line='threshold = 0.'>
  <DD>In order for a line center to be determined the range of pixel intensities
  around the line must exceed this threshold.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_minsep">minsep = 2.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='minsep' Line='minsep = 2.'>
  <DD>The minimum separation, in pixels, allowed between line positions
  when defining a new line.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_match">match = -3.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='match' Line='match = -3.'>
  <DD>The maximum difference for a match between the line coordinate derived from
  the dispersion function and a coordinate in the coordinate list.  Positive
  values are in user coordinate units and negative values are in units of
  pixels.
  </DD>
  </DL>
  <P>
  The following parameters are used to fit a dispersion function to the user
  coordinates.  The <B>icfit</B> routines are used and further descriptions
  about these parameters may be found under that topic.
  <DL>
  <DT><B><A NAME="l_function">function = "<TT>spline3</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='function' Line='function = "spline3"'>
  <DD>The function to be fit to user coordinates as a function of the pixel
  coordinates.  The choices are "<TT>chebyshev</TT>", "<TT>legendre</TT>", "<TT>spline1</TT>", or "<TT>spline3</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_order">order = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='order' Line='order = 1'>
  <DD>Order of the fitting function.  The order is the number of polynomial
  terms (coefficients) or the number of spline pieces.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_sample">sample = "<TT>*</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sample' Line='sample = "*"'>
  <DD>Sample regions for fitting specified in pixel coordinates.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_niterate">niterate = 10</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='niterate' Line='niterate = 10'>
  <DD>Number of rejection iterations.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_low_reject">low_reject = 3.0, high_reject = 3.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='low_reject' Line='low_reject = 3.0, high_reject = 3.0'>
  <DD>Lower and upper residual rejection in terms of the RMS of the fit.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_grow">grow = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='grow' Line='grow = 0'>
  <DD>Distance from a rejected point in which additional points are automatically
  rejected regardless of their residuals.
  </DD>
  </DL>
  <P>
  The following parameters control the input and output.
  <DL>
  <DT><B><A NAME="l_dbwrite">dbwrite = "<TT>yes</TT>"  (no|yes|NO|YES)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dbwrite' Line='dbwrite = "yes"  (no|yes|NO|YES)'>
  <DD>Automatically write or update the database with the line identifications
  and dispersion function?  If "<TT>no</TT>" or "<TT>NO</TT>" then there is no database
  output.  If "<TT>YES</TT>" the results are automatically written to the database.
  If "<TT>yes</TT>" a query is made allowing the user to reply with "<TT>no</TT>", "<TT>yes</TT>", "<TT>NO</TT>"
  or "<TT>YES</TT>".  The negative responses do not write to the database and the
  affirmative ones do write to the database.  The upper-case responses
  suppress any further queries for any remaining spectra.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_overwrite">overwrite = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='overwrite' Line='overwrite = yes'>
  <DD>Overwrite previous solutions in the database?  If there is a previous
  solution for the spectrum being identified this parameter selects whether
  to skip the spectrum ("<TT>no</TT>") or find a new solution ("<TT>yes</TT>").  In the later
  case saving the solution to the database will overwrite the previous
  solution.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_database">database = "<TT>database</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='database' Line='database = "database"'>
  <DD>Database for reading and writing the line identifications and
  dispersion functions.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print results of the identification on the standard output?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_logfile">logfile = "<TT>logfile</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logfile' Line='logfile = "logfile"'>
  <DD>Filename for recording log information about the identifications.
  The null string, "<TT></TT>", may be specified to skip recording the log information.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_plotfile">plotfile = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='plotfile' Line='plotfile = ""'>
  <DD>Filename for recording log plot information as IRAF metacode.  A
  null string, "<TT></TT>", may be specified to skip recording the plot information.
  (Plot output is currently not implemented.)
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_graphics">graphics = "<TT>stdgraph</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = "stdgraph"'>
  <DD>Graphics device for the interactive review.  The default is the standard
  graphics device which is generally a graphics terminal.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_cursor">cursor = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cursor' Line='cursor = ""'>
  <DD>Cursor input file for the interactive review.  If a cursor file is not
  given then the standard graphics cursor is read.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B><A NAME="l_query">query</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='query' Line='query'>
  <DD>Parameter used by the program to query the user.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <B>Autoidentify</B> automatically identifies spectral lines from a list of
  spectral line coordinates (<I>coordlist</I>) and determines a dispersion
  function.  The identified lines and the dispersion function may be reviewed
  interactively (<I>interactive</I>) and the final results are recorded in a
  <I>database</I>.
  <P>
  Each image in the input list (<I>images</I>) is considered in turn.  If the
  image is not one dimensional or a one dimensional section of an image then
  the parameter <I>section</I> is used to select a one dimensional
  spectrum.  It defines the dispersion direction and central spatial
  coordinate(s).  If the image is not one dimensional or a set of one
  dimensional spectra n multispec format then the <I>nsum</I> parameter
  selects the number of neighboring lines, columns, and bands to sum.
  <P>
  This task is not intended to be used on all spectra in an image since in
  most cases the dispersion functions will be similar though possibly with a
  zero point shift.  Once one spectrum is identified the others may be
  reidentified with <B>reidentify</B>.
  <P>
  The coordinate list of spectral lines often covers a much larger dispersion
  range than the spectra being identified.  This is true of the standard line
  lists available in the "<TT>linelists$</TT>" directory.  While the algorithm for
  identifying the lines will often succeed with a large line list it is not
  guaranteed nor will it find the solution quickly without additional
  information.  Thus it is highly desirable to provide the algorithm with
  approximate information about the spectra.  Generally this information is
  known by the observer or recorded in the image header.
  <P>
  As implied in the previous paragraph, one may use a
  limited coordinate line list that matches the dispersion coverage of the
  spectra reasonably well (say within 100% of the dispersion range).
  This may be done with the <I>coordlist</I> parameter or a second
  coordinate list used only for the automatic search may be specified
  with the parameter <I>aidpars.reflist</I>.  This allows using a smaller
  culled list of lines for finding the matching patterns and a large list
  with weaker lines for the final dispersion function fit.
  <P>
  The alternative to a limited list is to use the parameters <I>crval</I> and
  <I>cdelt</I> to specify the approximate coordinate range and dispersion
  interval per pixel.  These parameters may be given explicitly or by
  specifying image header keywords.  The pixel to which <I>crval</I> refers is
  specified by the parameter <I>aidpars.crpix</I>.  By default this is INDEF
  which means use the center of the spectrum.  The direction in which the
  dispersion coordinates increase relative to the pixel coordinates may be
  specified by the <I>aidpars.cddir</I> parameter.  The default is "<TT>unknown</TT>"
  to search in either direction.
  <P>
  The algorithm used to automatically identify the spectral lines and
  find a dispersion function is described under the help topic
  <B>aidpars</B>.  This topic also describes the various algorithm
  parameters.  The default parameters are adequate for most data.
  <P>
  The characteristics of the spectral lines to be found and identified are
  set by several parameters.  The type of spectral lines, whether "<TT>emission</TT>"
  or "<TT>absorption</TT>", is set by the parameter <I>ftype</I>.  For arc-line
  calibration spectra this parameter is set to "<TT>emission</TT>".  The full-width
  (in pixels) at the base of the spectral lines is set by the parameter
  <I>fwidth</I>.  This is used by the centering algorithm to define the extent
  of the line profile to be centered.  The <I>threshold</I> parameter defines
  a minimum contrast (difference) between a line peak and the neighboring
  continuum.  This allows noise peaks to be ignored.  Finding the center of a
  possible line begins with an initial position estimate.  This may be an
  interactive cursor position or the expected position from the coordinate
  line list.  The centering algorithm then searches for a line of the
  specified type, width, and threshold within a given distance, specified by
  the <I>cradius</I> parameter.  These parameters and the centering algorithm
  are described by the help topic <B>center1d</B>.
  <P>
  To avoid finding the same line multiple times, say when there are two lines
  in the line list which are blended into a single in the observation, the
  <I>minsep</I> parameter rejects any new line position found within that
  distance of a previously defined line.
  <P>
  The automatic identification of lines includes matching a line position in
  the spectrum against the list of coordinates in the coordinate line list.
  The <I>match</I> parameter defines how close the measured line position must
  be to a coordinate in the line list to be considered a possible
  identification.  This parameter may be specified either in user coordinate
  units (those used in the line list) by using a positive value or in pixels
  by using a negative value.  In the former case the line position is
  converted to user coordinates based on a dispersion function and in the
  latter the line list coordinate is converted to pixels using the inverse of
  the dispersion function.
  <P>
  The dispersion function is determined by fitting a set of pixel positions
  and user coordinate identifications by least squares to a specified
  function type.  The fitting requires a function type, <I>function</I>, and
  the order (number of coefficients or spline pieces), <I>order</I>.
  In addition the fitting can be limited to specified regions, <I>sample</I>,
  and provide for the rejection of points with large residuals.  These
  parameters are set in advance and used during the automatic dispersion
  function determination.  Later the fitting may be modified interactively.
  For additional discussion of these parameters see <B>icfit</B>.
  <P>
  The output of this program consists of log information, plot information,
  and the line identifications and dispersion function.  The log information
  may be appended to the file specified by the <I>logfile</I> parameter
  and printed to the standard output (normally the terminal) by
  setting the <I>verbose</I> parameter to yes.  This information consists
  of a banner line, a line of column labels, and results for each spectrum.
  For each spectrum the spectrum name, the number of spectral lines found,
  the dispersion coordinate at the middle of the spectrum, the dispersion
  increment per pixel, and the root-mean-square (RMS) of the residuals for
  the lines used in the dispersion function fit is recorded.  The units of
  the RMS are those of the user (line list) coordinates.  If a solution is
  not found the spectrum name and a message is printed.
  <P>
  The line identifications and dispersion function are written to the
  specified <I>database</I>.  The current format of the database is described
  in the help for <I>identify</I>.  If a database entry is already present for
  a spectrum and the parameter <I>overwrite</I> is "<TT>no</TT>" then the spectrum is
  skipped and a message is printed to the standard output.   After a solution
  is found and after any interactive review (see below) the results may be
  written to the database.  The <I>dbwrite</I> parameter may be specified as
  "<TT>no</TT>" or "<TT>NO</TT>" to disable writing to the database (and no queries will be
  made), as "<TT>yes</TT>" to query whether to or not to write to the database, or as
  "<TT>YES</TT>" to automatically write the results to the database with no queries.
  When a query is given the responses may be "<TT>no</TT>" or "<TT>yes</TT>" for an individual
  spectrum or "<TT>NO</TT>" or "<TT>YES</TT>" for all remaining spectra without further
  queries.
  <P>
  After a solution is found one may review and modify the line
  identifications and dispersion function using the graphical functions of
  the <B>identify</B> task (with the exception that a new spectrum may not be
  selected).  The review mode is selected with the <I>interactive</I>
  parameter.  If the parameter is "<TT>no</TT>" or "<TT>NO</TT>" then no interactive review
  will be provided and there will be no queries either.  If the parameter is
  "<TT>YES</TT>" then the graphical review mode will be entered after each solution is
  found without any query.  If the parameter is "<TT>yes</TT>" then a query will be
  made after a solution is found and after any log information is written to
  the terminal.  One may respond to the query with "<TT>no</TT>" or "<TT>yes</TT>" for an
  individual spectrum or "<TT>NO</TT>" or "<TT>YES</TT>" for all remaining spectra without
  further queries.  For "<TT>yes</TT>" or "<TT>YES</TT>" the <I>identify</I> review  mode is
  entered.  To exit type <TT>'q'</TT>.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  The following example finds a dispersion solution for the middle column
  of a long slit spectrum of a He-Ne-Ar arc spectrum using all the
  interactive options.
  <P>
  <PRE>
      cl&gt; autoid arc0022 6000 6 coord=linelists$henear.dat sec="mid col"
      AUTOIDENITFY: NOAO/IRAF IRAFX valdes@puppis Thu 15:50:31 25-Jan-96
        Spectrum                # Found   Midpoint Dispersion        RMS
        arc0022[50,*]                50      5790.       6.17      0.322
      arc0022[50,*]: Examine identifications interactively?  (yes): 
      arc0022[50,*]: Write results to database?  (yes): yes
  </PRE>
  <P>
  2.  The next example shows a non-interactive mode with no queries for
  the middle fiber of an extracted multispec image.
  <P>
  <PRE>
      cl&gt; autoid.coordlist="linelists$henear.dat"
      cl&gt; autoid a0003 5300 3.2 interactive- verbose- dbwrite=YES
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_revisions">REVISIONS</A></H2>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_AUTOIDENTIFY">AUTOIDENTIFY V2.11</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='AUTOIDENTIFY' Line='AUTOIDENTIFY V2.11'>
  <DD>This task is new in this version.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  identify, reidentify, aidpars, linelists, center1d, icfit, gtools
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'SUMMARY' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>