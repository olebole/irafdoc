aptrace — Trace positions of spectra
====================================

**Package: echelle**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>aptrace (Sep96)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.twodspec.apextract</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>aptrace (Sep96)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>aptrace</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  aptrace -- Trace spectra for aperture extraction
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  <PRE>
  aptrace images
  </PRE>
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of input images to be traced.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_apertures">apertures = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='apertures' Line='apertures = ""'>
  <DD>Apertures to recenter, resize, trace, and extract.  This only applies
  to apertures read from the input or reference database.  Any new
  apertures defined with the automatic finding algorithm or interactively
  are always selected.  The syntax is a list comma separated ranges
  where a range can be a single aperture number, a hyphen separated
  range of aperture numbers, or a range with a step specified by "<TT>x&lt;step&gt;</TT>";
  for example, "<TT>1,3-5,9-12x2</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_references">references = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='references' Line='references = ""'>
  <DD>List of reference images to be used to define apertures for the input
  images.  When a reference image is given it supersedes apertures
  previously defined for the input image. The list may be null, "<TT></TT>", or
  any number of images less than or equal to the list of input images.
  There are three special words which may be used in place of an image
  name.  The word "<TT>last</TT>" refers to the last set of apertures written to
  the database.  The word "<TT>OLD</TT>" requires that an entry exist
  and the word "<TT>NEW</TT>" requires that the entry not exist for each input image.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B><A NAME="l_interactive">interactive = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = yes'>
  <DD>Run this task interactively?  If the task is not run interactively then
  all user queries are suppressed and interactive aperture editing and trace
  fitting are disabled.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_find">find = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='find' Line='find = yes'>
  <DD>Find the spectra and define apertures automatically?  In order for
  spectra to be found automatically there must be no apertures for the
  input image or reference image defined in the database.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_recenter">recenter = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='recenter' Line='recenter = no'>
  <DD>Recenter the apertures?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_resize">resize = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='resize' Line='resize = yes'>
  <DD>Resize the apertures?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_edit">edit = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='edit' Line='edit = yes'>
  <DD>Edit the apertures?  The <I>interactive</I> parameter must also be yes.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_trace">trace = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='trace' Line='trace = yes'>
  <DD>Trace the apertures?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fittrace">fittrace = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fittrace' Line='fittrace = yes'>
  <DD>Interactively fit the traced positions by a function?  The <I>interactive</I>
  parameter must also be yes.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B><A NAME="l_line">line = INDEF, nsum = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='line' Line='line = INDEF, nsum = 1'>
  <DD>The dispersion line (line or column perpendicular to the dispersion
  axis) and number of adjacent lines (half before and half after unless
  at the end of the image) used in finding, recentering, resizing,
  and editing operations.  For tracing this is the starting line and
  the same number of lines are summed at each tracing point.  A line of
  INDEF selects the middle of the image along the dispersion axis.
  A positive nsum selects the number of lines to sum while a negative
  value selects a median.  Tracing always uses a sum.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_step">step = 10</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='step' Line='step = 10'>
  <DD>Step along the dispersion axis between determination of the spectrum
  positions.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nlost">nlost = 3</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nlost' Line='nlost = 3'>
  <DD>Number of consecutive steps in which the profile is lost before quitting
  the tracing in one direction.  To force tracing to continue through
  regions of very low signal this parameter can be made large.  Note,
  however, that noise may drag the trace away before it recovers.
  </DD>
  </DL>
  <P>
  The following parameters are the defaults used to fit the traced positions
  by a function of the dispersion line.  These parameters are those used by
  the ICFIT package.
  <DL>
  <DT><B><A NAME="l_function">function = "<TT>legendre</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='function' Line='function = "legendre"'>
  <DD>Default trace fitting function.  The fitting function types are
  "<TT>chebyshev</TT>" polynomial, "<TT>legendre</TT>" polynomial, "<TT>spline1</TT>" linear spline, and
  "<TT>spline3</TT>" cubic spline.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_order">order = 2</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='order' Line='order = 2'>
  <DD>Default trace function order.  The order refers to the number of
  terms in the polynomial functions or the number of spline pieces in the spline
  functions.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_sample">sample = "<TT>*</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sample' Line='sample = "*"'>
  <DD>Default fitting sample.  The sample is given by a set of colon separated
  ranges each separated by either whitespace or commas.  The string "<TT>*</TT>" refers
  to all points.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_naverage">naverage = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='naverage' Line='naverage = 1'>
  <DD>Default number of points to average or median.  Positive numbers
  average that number of sequential points to form a fitting point.
  Negative numbers median that number, in absolute value, of sequential
  points.  A value of 1 does no averaging and each data point is used in the
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_niterate">niterate = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='niterate' Line='niterate = 0'>
  <DD>Default number of rejection iterations.  If greater than zero the fit is
  used to detect deviant traced positions and reject them before repeating the
  fit.  The number of iterations of this process is given by this parameter.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_low_reject">low_reject = 3., high_reject = 3.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='low_reject' Line='low_reject = 3., high_reject = 3.'>
  <DD>Default lower and upper rejection sigma.  If greater than zero traced
  points deviating from the fit below and above the fit by more than this
  number of times the sigma of the residuals are rejected before refitting.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_grow">grow = 0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='grow' Line='grow = 0.'>
  <DD>Default reject growing radius.  Traced points within a distance given by this
  parameter of any rejected point are also rejected.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_additional_parameters">ADDITIONAL PARAMETERS</A></H2>
  <! BeginSection: 'ADDITIONAL PARAMETERS'>
  <UL>
  I/O parameters and the default dispersion axis are taken from the
  package parameters, the default aperture parameters from
  <B>apdefault</B>, automatic aperture finding parameters from
  <B>apfind</B>, recentering parameters from <B>aprecenter</B>, resizing
  parameters from <B>apresize</B>, and parameters used for centering and
  editing the apertures from <B>apedit</B>.
  <P>
  When this operation is performed from the task <B>apall</B> all parameters
  except the package parameters are included in that task.
  </UL>
  <! EndSection:   'ADDITIONAL PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  For each image in the input image list the position of the spectrum
  within each aperture are determined at a number of points along the
  dispersion axis and a smooth function is fit to these positions.  The
  fitted curve defines a shift to be added to the aperture center at each
  wavelength.  Other options allow defining apertures using a reference
  image, defining apertures through an automatic finding algorithm (see
  <B>apfind</B>), automatically recentering apertures (see
  <B>aprecenter</B>), automatically resizing apertures (see
  <B>apresize</B>), and interactively editing the apertures prior to
  tracing (see <B>apedit</B>).  Tracing is selected with the parameter
  <I>trace</I>.  If the tracing is done interactively (the
  <I>interactive</I> parameter set to yes) then the user is queried
  whether or not to trace each image.  The responses are "<TT>yes</TT>", "<TT>no</TT>",
  "<TT>YES</TT>", or "<TT>NO</TT>", where the upper case queries suppress this query
  for the following images.
  <P>
  The tracing begins with the specified dispersion line.  A dispersion
  line is a line or column of the image perpendicular to the dispersion
  axis.  The dispersion axis is defined in the image header or by the
  package parameter <I>dispaxis</I>.  If the starting dispersion line is
  INDEF then the middle dispersion line of the image is used.  The
  positions of the spectra are determined using the <B>center1d</B>
  algorithm and the centering parameters from the <B>apedit</B> task.
  (See help under <B>center1d</B> for a description of the one dimensional
  position measuring algorithm.) The positions are redetermined at other
  points along the dispersion axis by stepping from the starting line in
  steps specified by the user.  A number of dispersion lines around each
  dispersion line to be measured may be summed to improve the position
  determinations, particularly for weak profiles.  This number usually is
  set equal to the tracing step.
  <P>
  It is important to understand how to set the step size and the
  relationship between the step size and the centering error radius.
  Larger steps reduce the computational time, which is an important
  consideration.  However, if the step is too large then the tracing may
  fail to follow the systematic changes in the positions of the
  spectrum.  The centering error radius, <I>radius</I>, is used to limit
  the maximum position change between two successive steps.  If the
  positions of a spectrum changes by more than the specified amount or
  the data contrast falls below the <I>threshold</I> parameter then
  the position is marked as lost.
  <P>
  The centering radius should be large enough to follow changes in the
  spectrum positions from point to point but small enough to detect an error
  in the tracing by a sudden abrupt change in position, such as caused by
  crowding with other spectra or by the disappearance of the spectrum.  The
  <I>nlost</I> parameter determines how many consecutive steps the position
  may fail to be found before tracing in that direction is stopped.  If this
  parameter is small the trace will stop quickly upon loss of the profile
  while if it is very large it will continue to try and recover the profile.
  <P>
  The parameter <I>threshold</I> checks for the vanishing of a spectrum by
  requiring a minimum range in the data used for centering.  If the
  tracing fails when the spectra are strong and well defined the problem
  is usually that the step size is too large and/or the centering error
  radius is too small.
  <P>
  The traced positions of a spectrum include some measurement variation
  from point to point.  Since the actual position of the spectrum in the
  image should be a smooth curve, a function of the dispersion line is fit
  to the measured points.  The fitted function is stored as part of the
  aperture description.  It is an offset to be added to the aperture's
  center as a function of the dispersion line.  Even if the fitting is not
  done interactively plots of the trace and the fit are recorded in the
  plot file or device specified by the parameter <I>plotfile</I>.
  <P>
  Fitting the traced spectrum positions with a smooth function may be
  performed interactively when parameters <I>fittrace</I> and
  <I>interactive</I> are yes.  This allows changing the default fitting
  parameters.  The function fitting is done with the interactive curve
  fitting tools described under the help topic <B>icfit</B>.  There are
  two levels of queries when fitting the spectrum positions
  interactively; prompts for each image and prompts for each aperture in
  an image.  These prompts may be answered individually with the lower
  case responses "<TT>yes</TT>" or "<TT>no</TT>" or answered for all further prompts with
  the responses "<TT>YES</TT>" or "<TT>NO</TT>".  Responding with "<TT>yes</TT>" or "<TT>YES</TT>" to the
  image prompt allows interactive fitting of the traced positions for the
  spectra.  Prompts are then given for each aperture in the image.  When
  an spectrum is not fit interactively the last set of fitting parameters
  are used (initially the default function and order given by the task
  parameters).  Note that answering "<TT>YES</TT>" or "<TT>NO</TT>" to a aperture prompt
  applies to all further aperture in the current image only.  Responding
  with "<TT>no</TT>" or "<TT>NO</TT>" to the image prompt fits the spectrum positions for
  all apertures in all images with the last set of fitting parameters.
  <P>
  The tracing may also be done from the interactive aperture editor with
  the <TT>'t'</TT> key.  The aperture tracing algorithm may be selected from many
  of the tasks in the package with the <I>trace</I> parameter.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_aptrace_database_coefficients">APTRACE DATABASE COEFFICIENTS</A></H2>
  <! BeginSection: 'APTRACE DATABASE COEFFICIENTS'>
  <UL>
  The path of an aperture is described by a function that gives an additive
  offset relative to the aperture center as stored under the database keyword
  center.  The function is saved in the database as a series of
  coefficients.  The section containing the coefficients starts with the
  keyword "<TT>curve</TT>" and the number of coefficients.
  <P>
  The first four coefficients define the type of function, the order
  or number of spline pieces, and the range of the independent variable
  (the line or column coordinate along the dispersion).  The first
  coefficient is the function type code with values:
  <P>
  <PRE>
  	Code	Type
  	   1	Chebyshev polynomial
  	   2	Legendre polynomial
  	   3	Cubic spline
  	   4	Linear spline
  </PRE>
  <P>
  The second coefficient is the order (actually the number of terms) of
  the polynomial or the number of pieces in the spline.
  <P>
  The next two coefficients are the range of the independent variable over
  which the function is defined.  These values are used to normalize the
  input variable to the range -1 to 1 in the polynomial functions.  If the
  independent variable is x and the normalized variable is n, then
  <P>
  <PRE>
  	n = (2 * x - (xmax + xmin)) / (xmax - xmin)
  </PRE>
  <P>
  where xmin and xmax are the two coefficients.
  <P>
  The spline functions divide the range into the specified number of
  pieces.  A spline coordinate s and the nearest integer below s,
  denoted as j, are defined by
  <P>
  <PRE>
  	s = (x - xmin) / (xmax - xmin) * npieces
  	j = integer part of s
  </PRE>
  <P>
  where npieces are the number of pieces.
  <P>
  The remaining coefficients are those for the appropriate function.
  The number of coefficients is either the same as the function order
  for the polynomials, npieces+1 for the linear spline, or npieces + 3
  for the cubic spline.
  <P>
  1. Chebyshev Polynomial
  <P>
  The polynomial can be expressed as the sum
  <P>
  <PRE>
  	y = sum from i=1 to order {c_i * z_i}
  </PRE>
  <P>
  where the c_i are the coefficients and the z_i are defined
  interactively as:
  <P>
  <PRE>
  	z_1 = 1
  	z_2 = n
  	z_i = 2 * n * z_{i-1} - z_{i-2}
  </PRE>
  <P>
  2. Legendre Polynomial
  <P>
  The polynomial can be expressed as the sum
  <P>
  <PRE>
  	y = sum from i=1 to order {c_i * z_i}
  </PRE>
  <P>
  where the c_i are the coefficients and the z_i are defined
  interactively as:
  <P>
  <PRE>
  	z_1 = 1
  	z_2 = n
  	z_i = ((2*i-3) * n * z_{i-1} - (i-2) * z_{i-2}) / (i - 1)
  </PRE>
  <P>
  3. Linear Spline
  <P>
  The linear spline is evaluated as
  <P>
  <PRE>
  	y = c_j * a + c_{j+1} * b
  </PRE>
  <P>
  where j is as defined earlier and a and b are fractional difference
  between s and the nearest integers above and below
  <P>
  <PRE>
  	a = (j + 1) - s
  	b = s - j
  </PRE>
  <P>
  4.  Cubic Spline
  <P>
  The cubic spline is evaluated as
  <P>
  <PRE>
  	y = sum from i=0 to 3 {c_{i+j} * z_i}
  </PRE>
  <P>
  where j is as defined earlier.  The term z_i are computed from
  a and b, as defined earlier, as follows
  <P>
  <PRE>
  	z_0 = a**3
  	z_1 = 1 + 3 * a * (1 + a * b)
  	z_2 = 1 + 3 * b * (1 + a * b)
  	z_3 = b**3
  </PRE>
  </UL>
  <! EndSection:   'APTRACE DATABASE COEFFICIENTS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_revisions">REVISIONS</A></H2>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_APTRACE">APTRACE V2.11</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='APTRACE' Line='APTRACE V2.11'>
  <DD>The "<TT>apertures</TT>" parameter can be used to select apertures for resizing,
  recentering, tracing, and extraction.  This parameter name was previously
  used for selecting apertures in the recentering algorithm.  The new
  parameter name for this is now "<TT>aprecenter</TT>".
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  apdefault, apfind, aprecenter, apresize, apedit, apall,
  center1d, icfit, gtools
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'ADDITIONAL PARAMETERS' 'DESCRIPTION' 'APTRACE DATABASE COEFFICIENTS' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>