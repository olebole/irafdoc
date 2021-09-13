sensfunc — Create sensitivity function
======================================

**Package: iids**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>sensfunc (Mar93)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.onedspec</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>sensfunc (Mar93)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>sensfunc</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  sensfunc -- Determine sensitivity and extinction functions
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  sensfunc standards sensitivity
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_standards">standards = "<TT>std</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='standards' Line='standards = "std"'>
  <DD>Input standard star data file created by the task <B>standard</B>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_sensitivity">sensitivity = "<TT>sens</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sensitivity' Line='sensitivity = "sens"'>
  <DD>Output sensitivity function image name or rootname.  Generally each
  aperture results in an independent sensitivity function with the
  aperture number appended to the rootname.  If the parameter <I>ignoreaps</I>
  is set, however, the aperture numbers are ignored and a single sensitivity
  function is determined with the output image having the specified name
  with no extension.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_apertures">apertures = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='apertures' Line='apertures = ""'>
  <DD>List of apertures to be selected from the input file.  All other apertures
  are ignored.  If no list is specified then all apertures are selected.
  See <B>ranges</B> for the syntax.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ignoreaps">ignoreaps = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ignoreaps' Line='ignoreaps = no'>
  <DD>Ignore aperture numbers and create a single sensitivity function?  Normally
  each aperture produces an independent sensitivity function.  If the
  apertures are ignored then all the observations are combined into
  a single sensitivity function.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_logfile">logfile = "<TT>logfile</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logfile' Line='logfile = "logfile"'>
  <DD>Output log filename for statistical information about the stars used
  and the sensitivity function and extinction function.
  If no filename is given then no file is written.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_extinction">extinction = &lt;no default&gt;</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='extinction' Line='extinction = &lt;no default&gt;'>
  <DD>Input extinction file.  Any extinction determination made will be
  relative to this extinction.  If no file is given then no extinction
  correction is applied and any extinction determination from the
  standard star data will be an absolute determination of the
  extinction.  The default value is redirected to the package parameter
  of the same name.  The extinction file is generally one of the standard
  extinctions in the calibration directory "<TT>onedstds$</TT>".
  <P>
  If extinction corrected spectra were used as input to <B>standard</B>
  then it is important that the same extinction file be used here.
  This includes using no extinction file in both tasks.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_newextinction">newextinction = "<TT>extinct.dat</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='newextinction' Line='newextinction = "extinct.dat"'>
  <DD>Output revised extinction file.  If the extinction is revised and an
  output filename is given then a revised extinction file is written.  It
  has the same format as the standard extinction files.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_observatory">observatory = "<TT>)_.observatory</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='observatory' Line='observatory = ")_.observatory"'>
  <DD>Observatory at which the spectra were obtained if not specified in the
  image header by the keyword OBSERVAT.  The default is a redirection to look
  in the parameters for the parent package for a value.  This is only used
  when graphing flux calibrated data of spectra which do not include the
  airmass in the image header.  The observatory may be one of the
  observatories in the observatory database, "<TT>observatory</TT>" to select the
  observatory defined by the environment variable "<TT>observatory</TT>" or the
  parameter <B>observatory.observatory</B>, or "<TT>obspars</TT>" to select the current
  parameters set in the <B>observatory</B> task.  See help for
  <B>observatory</B> for additional information.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_function">function = "<TT>spline3</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='function' Line='function = "spline3"'>
  <DD>Function used to fit the sensitivity data.  The function types are
  "<TT>chebyshev</TT>" polynomial, "<TT>legendre</TT>" polynomial, "<TT>spline3</TT>" cubic spline,
  and "<TT>spline1</TT>" linear spline.  The default value may be changed interactively.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_order">order = 6</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='order' Line='order = 6'>
  <DD>Order of the sensitivity fitting function.  The value corresponds to the
  number of polynomial terms or the number of spline pieces.  The default
  value may be changed interactively.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interactive">interactive = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = yes'>
  <DD>Determine the sensitivity function interactively?  If yes the user
  graphically interacts with the data, modifies data and parameters
  affecting the sensitivity function, and determines a residual extinction.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_graphs">graphs = "<TT>sr</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphs' Line='graphs = "sr"'>
  <DD>Graphs to be displayed per frame.  From one to four graphs may be displayed
  per frame.  The graph types are selected by single characters and are:
  <P>
  <PRE>
  a - residual sensitivity vs airmass
  c - composite residual sensitivity and error bars vs wavelength
  e - input extinction and revised extinction vs wavelength
  i - Flux calibrated spectrum vs wavelength
  r - residual sensitivity vs wavelength
  s - sensitivity vs wavelength
  </PRE>
  <P>
  All other characters including whitespace and commas are ignored.  The order
  and number of graphs determines the positions of the graphs.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_marks">marks = "<TT>plus cross box</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='marks' Line='marks = "plus cross box"'>
  <DD>Symbols used to mark included, deleted, and added data respectively.
  The available mark types are point, box, plus, cross, diamond, hline
  (horizontal line), vline (vertical line), hebar (horizontal error bar),
  vebar (vertical error bar), and circle.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_colors">colors = "<TT>2 1 3 4</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='colors' Line='colors = "2 1 3 4"'>
  <DD>Colors to use for "<TT>lines</TT>", "<TT>marks</TT>", "<TT>deleted</TT>" data, and "<TT>added</TT>" data.
  The colors associated with the numbers is graphics device dependent.
  For example in XGTERM they are defined by resources while on other
  devices that don't support colors only one color will appear.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_cursor">cursor = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cursor' Line='cursor = ""'>
  <DD>Graphics cursor input list.  If not specified as a file then standard
  graphics cursor is read.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_device">device = "<TT>stdgraph</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='device' Line='device = "stdgraph"'>
  <DD>Graphics output device.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_answer">answer</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='answer' Line='answer'>
  <DD>Query parameter for selecting whether to fit apertures interactively.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_cursor_commands">CURSOR COMMANDS</A></H2>
  <! BeginSection: 'CURSOR COMMANDS'>
  <UL>
  <P>
  <PRE>
  ?	Print help
  a	Add a point at the cursor position
  c	Toggle use of composite points
  d	Delete point, star, or wavelength nearest the cursor
  e	Toggle residual extinction correction
  f	Fit data with a sensitivity function and overplot
  g	Fit data with a sensitivity function and redraw the graph(s)
  i	Print information about point nearest the cursor
  m	Move point, star, wavelength nearest the cursor to new sensitivity
  o	Reset to original data
  q	Quit and write sensitivity function for current aperture
  r	Redraw graph(s)
  s	Toggle shift of standard stars to eliminate mean deviations
  u	Undelete point, star, or wavelength nearest the cursor
  w	Change weights of point, star, or wavelength nearest the cursor
  <P>
  :flux [min] [max]  Limits for flux calibrated graphs (INDEF for autoscale)
  :function [type]   Function to be fit to sensitivity data:
  			chebyshev - Chebyshev polynomial
  			legendre  - Legendre polynomial
  			spline1   - Linear spline
  			spline3   - Cubic spline
  :graphs [types]    Graphs to be displayed (up to four):
  		a - Residual sensitivity vs airmass
  		c - Composite residuals and error bars vs wavelength
  		e - Extinction (and revised extinction) vs wavelength
  		i - Flux calibrated image vs wavelength
  		l - Log of flux calibrated image vs wavelength
  		r - Residual sensitivity vs wavelength
  		s - Sensitivity vs wavelength
  :images [images]   Images to flux calibrate and plot (up to four)
  :marks marks       Mark types to use for included, delete, and added points:
  			point, box, plus, cross, diamond, hline,
  			vline, hebar, vebar, circle
  :order [order]     Order of function
  :skys [images]     Sky images for flux calibration (up to four)
  :stats [file]      Statistics about stars and sensitivity fit
  :vstats [file]     Verbose statistics about sensitivity fit
  </PRE>
  </UL>
  <! EndSection:   'CURSOR COMMANDS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Standard star calibration measurements are used to determine the system
  sensitivity as a function of wavelength for each independent aperture.
  If the parameter <I>ignoreaps</I> is set then the aperture numbers are
  ignored and a single sensitivity function is determined from all the
  observations.  Using measurements spanning a range of airmass it is
  also possible to derive an adjustment to the standard extinction curve
  or even an absolute determination.  Extinction determination requires
  that the observations span a good range of airmass during photometric
  conditions.  When conditions are poor and standard star observations
  are obtained during periods of variable transparency, the entire
  sensitivity curve may vary by a constant factor, assuming that the
  cause of the variations has no color effect.  This is often the case
  during periods of thin clouds.  In this case the mean sensitivity of
  each observation may be shifted to match the observation of greatest
  sensitivity.  This allows for the possibility of deriving correct
  absolute fluxes if one observation of a standard was obtained during a
  clear period.
  <P>
  The input data is a file of calibration information produced by the
  task <B>standard</B>.  The data consists of a spectrum identification
  line containing the spectrum image name, the sky image name if beam
  switching, the aperture number, the length of the spectrum, the
  exposure time, airmass, wavelength range, and title.  Following the
  identification line are calibration lines consisting of the central
  bandpass wavelengths, the tabulated fluxes in the bandpasses, the
  bandpass widths, and the observed counts in the bandpasses.  The
  spectrum identification and calibration lines repeat for each standard
  star observation.  The parameter <I>apertures</I> may be used to select
  only specific apertures from the input data.  This parameter is in the
  form of a range list (see help for <B>ranges</B>) and if no list is
  given (specified by the null string "<TT></TT>") then all apertures are selected.
  <P>
  An input extinction file may also be specified.  Any extinction
  determinations are then residuals to this input extinction table.
  The format of this table is described in <B>lcalib</B>.
  <P>
  The calibration factor at each point is computed as
  <P>
  	(1) C = 2.5 log (O / (T B F)) + A E
  <P>
  where O is the observed counts in a bandpass of an observation,
  T is the exposure time of the observation, B is the bandpass width,
  F is the flux per Angstrom at the bandpass for the standard star,
  A is the airmass of the observation, and E is the extinction
  at the bandpass.  Thus, C is the ratio of the observed count rate per
  Angstrom corrected to some extinction curve to the expected flux
  expressed in magnitudes.  The goal of the task is to fit the observations
  to the relation
  <P>
  	(2) C = S(W) + AE(W)
  <P>
  where W is wavelength, S(W) is the sensitivity function, and E(W) is
  a residual extinction function relative to the extinction used in (1).
  In later discussion we will also refer to the residual sensitivity which
  is defined by
  <P>
  	(3) R = C - S(W) - AE(W)
  <P>
  The sensitivity function S(W) is output as an one dimensional image
  much like the spectra.  The sensitivities are in magnitude units to
  better judge the variations and because the interpolation is smoother
  in the logarithmic space (mags = 2.5 log10[sensitivity]).  There is one
  sensitivity function for each aperture unless the parameter
  <I>ignoreaps</I> is set.  In the first case the image names are formed
  from the specified rootname with the aperture number as a four digit
  numerical extension.  In the latter case a single sensitivity function
  is determined from all data, ignoring the aperture numbers, and the
  specified output image is created without an extension.  These images
  are used by <B>calibrate</B> to correct observations to a relative of
  absolute flux scale.  If no sensitivity function image rootname is
  specified then the sensitivity curves are not output.
  <P>
  If a revised extinction function E(W) has been determined for one or
  more of the apertures then the functions are averaged over all
  apertures, added to the original extinction, and written to the
  specified extinction table.  The format of this table is the same as
  the standard extinction tables and are, thus, interchangeable.  If no
  new extinction filename is specified then no extinction table is
  recorded.
  <P>
  If a log filename is given then statistical information about the
  sensitivity function determinations are recorded.  This includes the
  names of the input standard star observations and the tabulated
  sensitivity, extinction, and error information.
  <P>
  Some points to note are that if no input extinction is given then the
  E in (1) are zero and the E determined in (2) is the absolute extinction.
  If the data are not good enough to determine extinction then using one
  of the standard extinction curves the problem reduces to fitting
  <P>
  	(4) C = S(W)
  <P>
  The sensitivity and extinction functions are determined as fitted
  curves.  The curves are defined by a function type and order.  There
  are four function types and the order specifies either the number of
  terms in the polynomial or the number of pieces in the spline.  The
  order is automatically reduced to the largest
  value which produces a nonsingular result.  In this case the function
  will attempt to pass through every calibration point.  Lower orders
  provide for a smoother representation of the function.  The latter
  is generally more appropriate for a detector.  The initial function
  type and order for the sensitivity function is specified by the
  parameters <I>function</I> and <I>order</I>.
  <P>
  If the <I>interactive</I> flag is no then the default function and order
  is fit to equation (4) (i.e. there is no residual extinction determination
  or manipulation of the data).  The sensitivity functions are output
  if an image rootname is given and the log information is output if a
  log filename is given.
  <P>
  When the sensitivity is determined interactively a query is given for
  each aperture.  The responses "<TT>no</TT>" and "<TT>yes</TT>" select fitting the sensitivity
  interactively or not for the specified aperture.  The responses "<TT>NO</TT>" and
  "<TT>YES</TT>" apply to all apertures and no further queries will be given.
  When interactive fitting is selected the data are graphed
  on the specified graphics device and input is through the specified
  cursor list.  The graphics output consists of from one to four graphs.
  The user selects how many and which types of graphs to display.  The
  graph types and their single character code used to select them are:
  <P>
  <PRE>
     a - residual sensitivity vs airmass
     c - composite residual sensitivity and error bars vs wavelength
     e - input extinction and revised extinction vs wavelength
     i - Flux calibrated spectrum vs wavelength
     r - residual sensitivity vs wavelength
     s - sensitivity vs wavelength
  </PRE>
  <P>
  The initial graphs are selected with the parameter <B>graphs</B> and changed
  interactively with the colon command ':graphs <I>types</I>'.  The ability
  to view a variety of graphs allows evaluating the effects of the
  sensitivity curve and extinction in various ways.  The flux calibrated
  spectrum graph uses the current sensitivity function and checks for
  possible wiggles in the sensitivity curve which affect the shape of the
  continuum.  The choice of graphs also allows the
  user to trade off plotting speed and resolution against the amount of
  information available simultaneously.  Thus, with some graphics devices
  or over a slow line one can reduce the number of graphs for greater speed
  while on very fast devices with large screens one can look at more
  data.  The parameter <I>marks</I> and the associated colon command
  ':marks <I>types</I>' also let the user define the symbols used to mark
  included, deleted, and added data points.
  <P>
  The list of interactive commands in given in the section on CURSOR COMMANDS.
  The commands include deleting, undeleting, adding, moving, and identifying
  individual data points, whole stars, or all points at the same wavelength.
  Some other commands include <TT>'c'</TT> to create composite points by averaging
  all points at the same wavelength (this requires exact overlap in the
  bandpasses) which then replace the individual data points in the fit.
  This is different than the composite point graph which displays the
  residual in the mean sensitivity
  and error <I>in the mean</I> but uses the input data in the fitting.
  The <TT>'s'</TT> command shifts the data so that the mean sensitivity of each
  star is the same as the star with the greatest mean sensitivity.
  This compensates for variable grey extinction due to clouds.  Note
  that delete points are excluded from the shift calculation and a
  deleted star will not be used as the star of greatest sensitivity.
  Another useful command is <TT>'o'</TT> to recover the original data.  This cancels
  all changes made due to shifting, extinction corrections, deleting points,
  creating composite points, etc.
  <P>
  The <TT>'e'</TT> command attempts to compute a residual extinction by finding
  correlations between the sensitivity points at different airmass.
  Note that this is not iterative so that repeating this after having
  added an extinction correction simply redetermines the correction.
  At each wavelength or wavelength regions having multiple observations at
  different airmass a slope with airmass is determined.  This slope is
  the residual extinction at that wavelength.  A plot of the residual
  extinctions at each wavelength is made using the ICFIT procedure.
  The user may then examine and fit a curve through the residual extinction
  estimates as a function of wavelength (see <B>icfit</B> for a description
  of the commands).  The user must decide how much wavelength dependence
  is derivable from the data.  In many cases only a constant fit
  to a "<TT>gray extinction</TT>" or possibly a linear fit is realistic.
  The fitting is exited by the key <TT>'q'</TT>.
  <P>
  To help evaluate how important the residual extinction determination
  is a t-statistic significance is computed.  This statistic is defined by
  <P>
  	(5) t = sqrt (r**2 * (N - 2) / (1 - r**2))
  <P>
  where the correlation coefficient
  <P>
  	(6) r = RMS with correction / RMS without correction
  <P>
  is the fractional improvement in the RMS due to the added extinction
  correction and N is the number of wavelength points.  For large
  N this approaches a gaussian sigma but a more precise significance
  requires the t-distribution for N-2 degrees of freedom.  Basically this
  asks, was the improvement in the RMS significantly more than would
  occur with random errors?  A value greater than 3 is good while
  a value less than 1 is not significant.  The user may then accept the
  revised extinction and apply it to the data.
  <P>
  Note that when there are multiple apertures used each aperture has an
  independent system sensitivity but the residual extinction is the same.
  Therefore, the residual extinctions from each aperture are averaged at
  the end.  If one determines a new extinction then one may replace the
  original input extinction by the new extinction and rederive the
  sensitivity.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  The following command generates sensitivity spectra
  <P>
  	cl&gt; sensfunc std sens
  <P>
  This command uses the data from the <B>standard</B> output
  file "<TT>std</TT>" to create sensitivity functions with rootname "<TT>sens</TT>".
  If not interactive the task will produce the output with some
  progress messages being printed.  If it is interactive the graphics
  device will be used to display the data and the fit and user can
  change the function and order of the fit, delete bad points, shift
  data to correct for clouds or bandpass errors, and possibly determine
  a revised extinction function.  The statistics of the
  sensitivity determination are written to the logfile ("<TT>logfile</TT>" by
  default).
  <P>
  2. The following examples illustrate the colon command syntax.  Generally
  if no argument is given the current value is displayed.  For the statistics
  commands an optional output file may be given to record the information.
  <P>
  <PRE>
  :flux 1e-12 INDEF    Set lower limit for flux plots
  :flux INDEF INDEF    Restore autoscaling in flux plots
  :func spline3	     Select cubic spline function
  :g srae		     Graph sensitivity, residuals, airmass,
  		     and extinction
  :g sii		     Graph sensitivity and two images
  :i n1.0004 n1.0008   Set first two images to graph (the defaults
  		     are taken from the standard star list)
  :skys n1.0005	     Subtract this sky image from first image
  		     for flux calibrated spectrum
  :m plus		     Change the mark type for included points and
  		     don't change the deleted or added point mark type
  :stats		     Print statistics to terminal
  :vstats stdstats     Print verbose statistics to file
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_revisions">REVISIONS</A></H2>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_SENSFUNC">SENSFUNC V2.10.3+</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='SENSFUNC' Line='SENSFUNC V2.10.3+'>
  <DD>Deleted points and stars are now ignored from the grey shift calculation.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_SENSFUNC">SENSFUNC V2.10.3</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='SENSFUNC' Line='SENSFUNC V2.10.3'>
  <DD>A color parameter was added for graphics terminals supporting color.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_SENSFUNC">SENSFUNC V2.10</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='SENSFUNC' Line='SENSFUNC V2.10'>
  <DD>The latitude parameter has been replaced by the observatory parameter.
  The <TT>'i'</TT> flux calibrated graph type now shows flux in linear scaling 
  while the new graph type <TT>'l'</TT> shows flux in log scaling.  A new colon
  command allows fixing the flux limits for the flux calibrated graphs.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_SENSFUNC">SENSFUNC V2.8</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='SENSFUNC' Line='SENSFUNC V2.8'>
  <DD>This task has been completely rewritten from that of versions 2.5 and
  earlier.
  <P>
  <PRE>
  1. The input standard data format is different.
  2. Extinction corrections beyond a grey term are now supported.
  3. Weighting by the counts is not supported.
  4. Tabular input is not supported.
  5. The data which can be displayed is greatly improved.
  6. The fitting options have been greatly enhanced.
  7. The fitting function types available have been extended.
  8. One or more flux calibrated images may be displayed using the
     current sensitivity function.
  9. Additional flexibility is provided for treating apertures.
  </PRE>
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  If the flux points do not span the wavelength range, set by the
  standard star observations, then the fitting may fail at some maximum
  order.  When it fails there is no message but the highest order which
  can be successfully fit is used.  To work around this one can either
  add fake points, truncate the wavelength range in the first line of each
  tabulated object in the file produced by <B>standard</B>, or exclude the
  part of the image data which cannot be uncalibrated (using
  <B>scopy</B> or <B>dispcor</B>).
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  standard, lcalib, calibrate, observatory, icfit, ranges, scopy, dispcor
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'CURSOR COMMANDS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>