illumination — Determine illumination calibration
=================================================

**Package: kpnoslit**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>illumination (Jul86)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.twodspec.longslit</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>illumination (Jul86)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>illumination</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  illumination -- Determine illumination calibrations
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  illumination images illuminations
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_images">images</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>Images to use in determining illumination calibrations.  These are
  generally sky spectra.  An image section may be used to select only a
  portion of the image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_illuminations">illuminations</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='illuminations' Line='illuminations'>
  <DD>Iillumination calibration images to be created.  Each illumination image is
  paired with a calibration image.  If the image exists then it will be modified
  otherwise it is created.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interactive">interactive = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = yes'>
  <DD>Graph the average spectrum and select the dispersion bins
  and graph and fit the slit profile for each dispersion bin interactively?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_bins">bins = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='bins' Line='bins = ""'>
  <DD>Range string defining the dispersions bins within which the slit profiles
  are determined.  If the range string is null then the dispersion
  bins are determined by the parameter <I>nbins</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nbins">nbins = 5</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nbins' Line='nbins = 5'>
  <DD>If the dispersion bins are not specified explicitly by the parameter
  <I>bins</I> then the dispersion range is divided into this number of
  nearly equal bins.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_sample">sample = "<TT>*</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sample' Line='sample = "*"'>
  <DD>Sample of points to use in fitting each slit profile.
  The sample is selected with a range string.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_naverage">naverage = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='naverage' Line='naverage = 1'>
  <DD>Number of sample points to average or median before fitting a function.
  If the number is positive the average of each set of naverage sample
  points is formed while if the number is negative then the median of each set
  of points (in absolute value) is formed.  This subsample of points is
  used in fitting the slit profile.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_function">function = "<TT>spline3</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='function' Line='function = "spline3"'>
  <DD>Function to fit to each dispersion bin to form the illumination function.
  The options are "<TT>spline1</TT>", "<TT>spline3</TT>", "<TT>legendre</TT>", and "<TT>chebyshev</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_order">order = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='order' Line='order = 1'>
  <DD>Order of the fitting function or the number of spline pieces.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_low_reject">low_reject = 0., high_reject = 0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='low_reject' Line='low_reject = 0., high_reject = 0.'>
  <DD>Rejection limits below and above the fit in units of the residual sigma.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_niterate">niterate = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='niterate' Line='niterate = 1'>
  <DD>Number of rejection iterations.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_grow">grow = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='grow' Line='grow = 0'>
  <DD>Reject additional points within this distance of points exceeding the
  rejection threshold.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interpolator">interpolator = "<TT>poly3</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interpolator' Line='interpolator = "poly3"'>
  <DD>Interpolation type.  One of "<TT>nearest</TT>", "<TT>linear</TT>", "<TT>poly3</TT>", "<TT>poly5</TT>", or
  "<TT>spline3</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_graphics">graphics = "<TT>stdgraph</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = "stdgraph"'>
  <DD>Graphics output device.  May be one of the standard devices "<TT>stdgraph</TT>",
  "<TT>stdplot</TT>", or "<TT>stdvdm</TT>" or an explicit device.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_cursor">cursor = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cursor' Line='cursor = ""'>
  <DD>Graphics input device.  May be either null for the standard graphics cursor
  or a file containing cursor commands.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_cursor_keys">CURSOR KEYS</A></H2>
  <! BeginSection: 'CURSOR KEYS'>
  <UL>
  The interactive curve fitting package <B>icfit</B> is used to fit a function
  to the average calibration spectrum.  Additional help on using this package
  and the cursor keys is available under the name "<TT>icfit</TT>".
  <P>
  When the dispersion bins are set graphically the following cursor keys are
  defined.
  <P>
  <DL>
  <DT><B><A NAME="l_">?</A></B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line='?'>
  <DD>Clear the screen and print a menu of the cursor options.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_i">i</A></B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='i' Line='i'>
  <DD>Initialize the sample ranges.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_q">q</A></B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='q' Line='q'>
  <DD>Exit interactive dispersion bin selection.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_s">s</A></B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='s' Line='s'>
  <DD>Set a bin with the cursor.  This may be repeated any number of times.
  Two keystrokes are required to mark the two ends of the bin.
  </DD>
  </DL>
  <P>
  The parameters are listed or set with the following commands which may be
  abbreviated.  To list the value of a parameter type the command alone.
  <P>
  <PRE>
  :bins value		Iillumination bins
  :show			Show the values of all the parameters
  </PRE>
  </UL>
  <! EndSection:   'CURSOR KEYS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  An illumination calibration, in the form of an image, is created for each
  longslit calibration image, normally a sky spectrum.  The illumination
  calibration is determined by fitting functions across the slit (the slit
  profiles) at a number of points along the dispersion, normalizing each fitted
  function to unity at the center of the slit, and interpolating the illumination
  between the dispersion points.  The fitted data is formed by dividing the
  dispersion points into a set of bins and averaging the slit profiles within
  each bin.  The interpolation type is a user parameter.
  <P>
  The image header keyword DISPAXIS must be present with a value of 1 for
  dispersion parallel to the lines (varying with the column coordinate) or 2
  for dispersion parallel to the columns (varying with line coordinate).
  This parameter may be added using <B>hedit</B>.  Note that if the image has
  been transposed (<B>imtranspose</B>) the dispersion axis should still refer
  to the original dispersion axis unless the physical world coordinate system
  is first reset (see <B>wcsreset</B>).  This is done in order to allow images
  which have DISPAXIS defined prior to transposing to still work correctly
  without requiring this keyword to be changed.
  <P>
  If the output image does not exist it is first created with unit illumination
  everywhere.  Subsequently the illumination is only modified in those regions
  occupied by the input image.  Thus, an image section in the input image may
  be used to select the data to be used and for which an illumination calibration
  will be determined.  This ability is particularly userful when dealing with
  multiple slits or to exclude regions outside the slit.
  <P>
  The dispersion bins may be selected by a range string (<I>bins</I>) or,
  if no range string is given, by the number of bins into which the dispersion
  range is to be divided (<I>nbins</I>).  When the interactive parameter
  is set (<I>interactive</I>) then the average spectrum is graphed and the
  bins may be set using the cursor or with a colon command.  Once the bins
  have been selected exit with (q)uit to continue to the slit profile fitting.
  <P>
  Fitting of the slit profiles is done using the interactive curve fitting
  package (<B>icfit</B>).  The parameters determining the fit are the
  sample points, the averaging bin size, the fitting function,
  the order of the function, the rejection sigmas, the number of
  rejection iterations, and the rejection width.
  The sample points for the average slit profile are selected by a range string.  
  Points in the slit profile not in the sample are not used in determining
  the fitted function.  The selected sample points may be binned into a
  set of averages or medians which are used in the function fit instead of the
  sample points with the averaging bin size parameter
  <I>naverage</I>.  This parameter selects the number of sample points to be
  averaged if its value is positive or the number of points to be medianed
  if its value is negative (naturally, the absolute value is used for the
  number of points).  A value of one uses all sample points without binning.
  The fitted function may be used to reject points from the fit using the
  parameters <I>low_reject, high_reject, niterate</I> and <I>grow</I>.  If
  one or both of the rejection limits are greater than zero then the sigma
  of the residuals is computed and points with residuals less than
  <I>-low_reject</I> times the sigma and greater than <I>high_reject</I> times
  the sigma are removed and the function fitted again.  In addition points
  within a distance given by the parameter <I>grow</I> of the a rejected point
  are also rejected.  A value of zero for this parameter rejects only the
  points exceeding the rejection threshold.  Finally, the rejection procedure
  may be iterated the number of times given by the parameter <I>niterate</I>.
  <P>
  The fitted functions may be examined and modified interactively when the
  parameter <I>interactive</I> is set.  The user is asked before each dispersion
  bin whether to perform the fit interactively.  The possible response are
  "<TT>no</TT>", "<TT>yes</TT>", "<TT>NO</TT>", and "<TT>YES</TT>".  The lower case responses only affect the
  specified dispersion bin while the upper case responses affect all following
  dispersion bins for the current image.  Thus, if the response is "<TT>NO</TT>" then
  no further prompts or interactive curve fitting need be performed while if
  the response is "<TT>YES</TT>" there are no further prompts but the slit profile
  for each dispersion bin must be graphed and exited with (q)uit.
  Changes to the fitting parameters remain in effect until they are next
  changed.  This allows the fitting parameters to be selected from only the first
  dispersion bin without requiring each dispersion bin to be graphed and
  confirmed.
  <P>
  When a dispersion bin is to be fitted interactively the average slit profile
  and the fitted function or the residuals of the fit are graphed.
  Deleted points are marked with an x and rejected points by a diamond.
  The sample regions are indicated along the bottom of the graph.
  The cursor keys and colon commands are used to change the values
  of the fitting parameters, delete points, and window and expand the
  graph.  When the fitted function is satisfactory exit with
  with a carriage return or <TT>'q'</TT>.  The prompt for the next dispersion bin will
  then be given until the last dispersion bin has been fit.  The illumination
  calibration image is then created.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. To create an illumination image non-interactively:
  <P>
  <PRE>
  	cl&gt; illumination sky illum nbins=8 order=20 interactive=no
  </PRE>
  <P>
  2. To determine independent illuminations for a multislit image determine the
  image sections defining each slit.  Then the illumination functions are
  computed as follows:
  <P>
  <PRE>
  	cl&gt; illumination sky[10:20,*],sky[35:45,*] illum,illum
  </PRE>
  <P>
  3. Generally the slit image sections are prepared in a file which is then
  used to define the lists of input images and illuminations.
  <P>
  <PRE>
  	cl&gt; illumination @slits @illums
  </PRE>
  <P>
  3.  If the DISPAXIS keyword is missing and the dispersion is running
  vertically (varying with the image lines):
  <P>
  <PRE>
  	cl&gt; hedit *.imh dispaxis 2 add+
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  icfit, response
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'CURSOR KEYS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>