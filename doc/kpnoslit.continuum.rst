continuum — Fit and normalize the continuum of multispec spectra
================================================================

**Package: kpnoslit**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>continuum (Mar92)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.onedspec</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>continuum (Mar92)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>continuum</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  continuum -- Continuum normalize spectra
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage_">USAGE	</A></H2>
  <! BeginSection: 'USAGE	'>
  <UL>
  continuum input output
  </UL>
  <! EndSection:   'USAGE	'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>Input spectra to be continuum normalized.  These may be any combination
  of echelle, multiaperture, one dimensional, long slit, and spectral
  cube images.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>Output continuum normalized spectra.  The number of output spectra must
  match the number of input spectra.  <B>Output</B> may be omitted if
  <B>listonly</B> is yes.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_lines">lines = "<TT>*</TT>", bands = "<TT>1</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lines' Line='lines = "*", bands = "1"'>
  <DD>A range specifications for the image lines and bands to be fit.  Unspecified
  lines and bands will be copied from the original.  If the value is "<TT>*</TT>", all of
  the currently unprocessed lines or bands will be fit.  A range consists of
  a first line number and a last line number separated by a hyphen.  A
  single line number may also be a range and multiple ranges may be
  separated by commas.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_type">type = "<TT>ratio</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='type' Line='type = "ratio"'>
  <DD>Type of output spectra.  The choices are "<TT>fit</TT>" for the fitted function,
  "<TT>ratio</TT>" for the ratio of the input spectra to the fit, "<TT>difference</TT>" for
  the difference between the input spectra and the fit, and "<TT>data</TT>" for
  the data minus any rejected points replaced by the fit.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_replace">replace = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='replace' Line='replace = no'>
  <DD>Replace rejected points by the fit in the difference, ratio, and
  data output types?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_wavescale">wavescale = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wavescale' Line='wavescale = yes'>
  <DD>Wavelength scale the X axis of the plot?  This option requires that the
  spectra be wavelength calibrated.  If <B>wavescale</B> is no, the plots
  will be in "<TT>channel</TT>" (pixel) space.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_logscale">logscale = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logscale' Line='logscale = no'>
  <DD>Take the log (base 10) of both axes?  This can be used when <B>listonly</B>
  is yes to measure the exponent of the slope of the continuum.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_override">override = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='override' Line='override = no'>
  <DD>Override previously normalized spectra?  If <B>override</B> is yes and
  <B>interactive</B> is yes, the user will be prompted before each order is
  refit.  If <B>override</B> is no, previously fit spectra are silently
  skipped.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_listonly">listonly = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='listonly' Line='listonly = no'>
  <DD>Don't modify any images?  If <B>listonly</B> is yes, the <B>output</B>
  image list may be skipped.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_logfiles">logfiles = "<TT>logfile</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logfiles' Line='logfiles = "logfile"'>
  <DD>List of log files to which to write the power series coefficients.  If
  <B>logfiles</B> = NULL ("<TT></TT>"), the coefficients will not be calculated.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interactive">interactive = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = yes'>
  <DD>Perform the fit interactively using the icfit commands?  This will allow
  the parameters for each spectrum to be adjusted independently.  A separate
  set of the fit parameters (below) will be used for each spectrum and any
  interactive changes to the parameters for a specific spectrum will be
  remembered when that spectrum is fit in the next image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_sample">sample = "<TT>*</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sample' Line='sample = "*"'>
  <DD>The ranges of X values to be used in the continuum fits.  The units will vary
  depending on the setting of the <B>wavescale</B> and <B>logscale</B>
  parameters.  The default units are in wavelength if the spectra have
  been dispersion corrected.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_naverage">naverage = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='naverage' Line='naverage = 1'>
  <DD>Number of sample points to combined to create a fitting point.
  A positive value specifies an average and a negative value specifies
  a median.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_function">function = spline3</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='function' Line='function = spline3'>
  <DD>Function to be fit to the spectra.  The functions are
  "<TT>legendre</TT>" (legendre polynomial), "<TT>chebyshev</TT>" (chebyshev polynomial),
  "<TT>spline1</TT>" (linear spline), and "<TT>spline3</TT>" (cubic spline).  The functions
  may be abbreviated.  The power series coefficients can only be
  calculated if <B>function</B> is "<TT>legendre</TT>" or "<TT>chebyshev</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_order">order = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='order' Line='order = 1'>
  <DD>The order of the polynomials or the number of spline pieces.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_low_reject">low_reject = 2., high_reject = 0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='low_reject' Line='low_reject = 2., high_reject = 0.'>
  <DD>Rejection limits below and above the fit in units of the residual sigma.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_niterate">niterate = 10</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='niterate' Line='niterate = 10'>
  <DD>Number of rejection iterations.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_grow">grow = 1.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='grow' Line='grow = 1.'>
  <DD>When a pixel is rejected, pixels within this distance of the rejected pixel
  are also rejected.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_markrej">markrej = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='markrej' Line='markrej = yes'>
  <DD>Mark rejected points?  If there are many rejected points it might be
  desired to not mark rejected points.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_graphics">graphics = "<TT>stdgraph</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = "stdgraph"'>
  <DD>Graphics output device for interactive graphics.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_cursor">cursor = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cursor' Line='cursor = ""'>
  <DD>Graphics cursor input.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  A one dimensional function is fit to the continuum of spectra in a list of
  echelle, multispec, or onedspec format images and then divided into the
  spectrum to produce continuum normalized spectra.  The first two formats
  will normalize the spectra or orders (i.e. the lines) in each image.  In
  this description the term "<TT>spectrum</TT>" will refer to a line (in whatever
  band) of an image while "<TT>image</TT>" will refer to all spectra in an image.  The
  parameters of the fit may vary from spectrum to spectrum within images and
  between images.  The fitted function may be a legendre polynomial,
  chebyshev polynomial, linear spline, or cubic spline of a given order or
  number of spline pieces.  The output image is of pixel type real.
  <P>
  The line/band numbers (for two/three dimensional images) are written to a
  list of previously processed lines in the header keywords <I>SFIT</I> and
  <I>SFITB</I> of the output image.  A subsequent invocation of SFIT will only
  process those requested spectra that are not in this list.  This ensures
  that even if the output image is the same as the input image that no
  spectra will be processed twice and permits an easy exit from the task in
  the midst of processing many spectra without losing any work or requiring
  detailed notes.
  <P>
  The points to be fit in each spectrum are determined by
  selecting a sample of X values specified by the parameter <I>sample</I>
  and taking either the average or median of the number of points
  specified by the parameter <I>naverage</I>.  The type of averaging is
  selected by the sign of the parameter with positive values indicating
  averaging, and the number of points is selected by the absolute value
  of the parameter.  The sample units will vary depending on the settings
  of the <B>wavescale</B> and the <B>logscale</B> parameters.  Note that a
  sample that is specified in wavelength units may be entirely outside
  the domain of the data (in pixels) if some of the spectra are not
  dispersion corrected.  The syntax of the sample specification is a comma
  separated, colon delimited list similar to the image section notation.
  For example, the <B>sample</B>, "<TT>6550:6555,6570:6575</TT>" might be used to
  fit the continuum near H-alpha.
  <P>
  If <I>low_reject</I> and/or <I>high_reject</I> are greater than zero the
  sigma of the residuals between the fitted points and the fitted
  function is computed and those points whose residuals are less than
  <I>-low_reject</I> * sigma and greater than <I>high_reject</I> * sigma
  are excluded from the fit.  Points within a distance of <I>grow</I>
  pixels of a rejected pixel are also excluded from the fit.  The
  function is then refit without the rejected points.  This rejection
  procedure may be iterated a number of times given by the parameter
  <I>niterate</I>.  This is how the continuum is determined.
  <P>
  If <I>replace</I> is set then any rejected points from the fitting
  are  replaced by the fit in the data before outputing the difference,
  ratio, or data.  For example with replacing the difference will
  be zero at the rejected points and the data output will be cleaned
  of deviant points.
  <P>
  A range specification is used to select the <I>lines</I> and <I>bands</I> to be
  fit.  These parameters may either be specified with the same syntax as the
  <B>sample</B> parameter, or with the "<TT>hyphen</TT>" syntax used elsewhere in
  IRAF.  Note that a NULL range for <B>lines/bands</B> expands to <B>no</B>
  lines, not to all lines.  An asterisk (*) should be used to represent a
  range of all of the image lines/bands.  The fitting parameters (<I>sample,
  naverage, function, order, low_reject, high_reject, niterate, grow</I>)
  may be adjusted interactively if the parameter <I>interactive</I> is
  yes.  The fitting is performed with the <B>icfit</B> package.  The
  cursor mode commands for this package are described in a separate help
  entry under "<TT>icfit</TT>".  Separate copies of the fitting parameters are
  maintained for each line so that interactive changes to the parameter
  defaults will be remembered from image to image.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_prompts">PROMPTS</A></H2>
  <! BeginSection: 'PROMPTS'>
  <UL>
  If several images or lines/bands are specified, the user is asked whether
  to perform an interactive fit for each spectrum.  The response
  may be <B>yes, no, skip, YES, NO</B> or <B>SKIP</B>.  The meaning of each
  response is:
  <P>
  <PRE>
  	yes   - Fit the next spectrum interactively.
  	no    - Fit the next spectrum non-interactively.
  	skip  - Skip the next spectrum in this image.
  <P>
  	YES   - Interactively fit all of the spectra of
  		all of the images with no further prompts.
  	NO   	Non-interactively fit all chosen spectra of all images.
  	SKIP  - This will produce a second prompt, "Skip what?",
  		with the choices:
  <P>
  		spectrum - skip this spectrum in all images
  		image    - skip the rest of the current image
  		all      - <B>exit</B> the program
  		           This will <B>unlearn</B> the fit parameters
  			   for all spectra!
  		cancel  - return to the main prompt
  </PRE>
  </UL>
  <! EndSection:   'PROMPTS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  To normalize all orders of the echelle spectrum for hd221170
  <P>
  	cl&gt; continuum hd221170.ec nhd221170.ec type=ratio
  <P>
  Each order of the spectrum is graphed and the interactive options for
  setting and fitting the continuum are available.  The important
  parameters are low_rejection (for an absorption spectrum), the function
  type, and the order of the function; these fit parameters are
  originally set to the defaults in the <B>continuum</B> parameter file.  A
  <TT>'?'</TT> will display a menu of cursor key options.  Exiting with <TT>'q'</TT> will
  update the output normalized order for the current image and proceed to
  the next order or image.
  <P>
  The parameters of the fit for each order are initialized to the current
  values the first time that the order is fit.  In subsequent images, the
  parameters for a order are set to the values from the previous image.
  The first time an order is fit, the sample region is reset to the
  entire order.  Deleted points are ALWAYS forgotten from order to order
  and image to image.
  <P>
  2.  To do several images at the same time
  <P>
  	cl&gt; continuum spec*.imh c//spec*.imh
  <P>
  Note how the image template concatenation operator is used to construct
  the output list of spectra.  Alternatively:
  <P>
  	cl&gt; continuum @inlist @outlist
  <P>
  where the two list files could have been created with the sections
  command or by editing.
  <P>
  3.  To measure the power law slope of the continuum (fluxed data)
  <P>
  	cl&gt; continuum uv.* type=ratio logscale+ listonly+ fun=leg order=2
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_revisions">REVISIONS</A></H2>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_CONTINUUM">CONTINUUM V2.10.4</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='CONTINUUM' Line='CONTINUUM V2.10.4'>
  <DD>The task was expanded to include fitting specified bands in 3D multispec
  spectra.
  <P>
  The task was expanded to include long slit and spectral cube data.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_CONTINUUM">CONTINUUM V2.10</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='CONTINUUM' Line='CONTINUUM V2.10'>
  <DD>This task was changed from a script based on <B>images.fit1d</B> to a
  task based on <B>sfit</B>.  This provides for individual independent
  continuum fitting in multiple spectra images and for additional
  flexibility and record keeping.  The parameters have been largely
  changed.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  The errors are not listed for the power series coefficients.
  <P>
  Spectra that are updated when <B>logscale</B> is yes are written with a
  linear wavelength scale, but with a log normalized data value.
  <P>
  Selection by aperture number is not supported.
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  sfit, fit1d, icfit, ranges
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'PROMPTS' 'EXAMPLES' 'REVISIONS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>