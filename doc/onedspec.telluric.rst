telluric — Remove telluric features from 1D spectra
===================================================

**Package: onedspec**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>telluric (Mar97)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.onedspec</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>telluric (Mar97)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>telluric</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  telluric -- remove telluric features from 1D spectra
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_summary">SUMMARY</A></H2>
  <! BeginSection: 'SUMMARY'>
  <UL>
  Telluric calibration spectra are shifted and scaled to best divide out
  telluric features from data spectra.  This may be done non-interactively to
  minimize the RMS in some region or regions of the data spectra and
  interactively with a graphically search.
  </UL>
  <! EndSection:   'SUMMARY'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  telluric input output cal
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of input data images containing one dimensional spectra to be
  corrected.  All spectra in each image are corrected. The spectra need not
  be wavelength calibrated.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>List of output corrected images.  The list must either match the input list
  or be an empty list.  If an empty list is specified the input spectra will
  be replaced by the corrected spectra.  The input spectra will also be
  replaced if the input and output image names are the same.  Any other image
  name must be for a new image otherwise a warning message will be given and
  the task will proceed to the next input image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_cal">cal  </A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cal' Line='cal  '>
  <DD>List of telluric calibration images.  If a single image is specified it
  will apply to all the input images.  Otherwise the list of calibration
  images must match the list of input images.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ignoreaps">ignoreaps = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ignoreaps' Line='ignoreaps = no'>
  <DD>Ignore aperture numbers between the input spectra and the calibration
  spectra?  If "<TT>no</TT>" then the calibration image must contain a spectrum
  with the same aperture number as each spectrum in the input image.
  Otherwise the first spectrum in the calibration image will be used
  for all spectra in the input image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xcorr">xcorr = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xcorr' Line='xcorr = yes'>
  <DD>Cross-correlate each input spectrum with the calibration spectrum to
  determine an shift for the calibration spectrum?  Only regions specified by
  the sample regions parameter will be used in the cross-correlation.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_tweakrms">tweakrms = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='tweakrms' Line='tweakrms = yes'>
  <DD>Search for the minimum RMS in the corrected spectrum by adjusting the
  shifts and scales between the input spectrum and the calibration spectrum?
  The RMS is minimized in the specified sample regions.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interactive">interactive = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = yes'>
  <DD>Enter an interactive graphical mode to search for the best shift
  and scale between the input spectra and calibration spectra?  This
  is done after the optional automatic cross-correlation and RMS minimization
  step.  A query is made for each input spectrum so that the interactive
  step may be skipped during the execution of the task.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_sample">sample = "<TT>*</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sample' Line='sample = "*"'>
  <DD>Sample regions to use for cross-correlation, automatic RMS minimization,
  and RMS values.  The sample regions are specified by a list of comma
  separated ranges.  The ranges are colon separate coordinate values.
  For dispersion calibrated spectra the coordinate values are in the
  dispersion units otherwise they are in pixel coordinates.  The string "<TT>*</TT>"
  selects the entire spectrum.  The sample regions may be changed
  interactively either with the cursor or with a colon command.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_threshold">threshold = 0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='threshold' Line='threshold = 0.'>
  <DD>Since the calibration consists of division by the scaled calibration data
  it is possible for totally saturated lines to have zero or negative values.
  The task will quit if detects negative or zero calibration values.  The
  <I>threshold</I> allows applying a minimum threshold to the calibration
  values so the task may continue.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_lag">lag = 10</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lag' Line='lag = 10'>
  <DD>The cross-correlation lag to use when <I>xcorr</I> = yes.  The lag
  is given in pixels.   This is the distance to either side of the
  initial shift over which the cross-correlation profile is computed.
  If a value of zero is given then the cross-correlation step is not done.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_shift">shift = 0., dshift = 1.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='shift' Line='shift = 0., dshift = 1.'>
  <DD>The initial shift and shift step in pixels.  This initializes the shift
  search parameters for the first spectrum.  If <I>dshift</I> is zero then
  there will be no search for a new shift and the <TT>'x'</TT> interactive function is
  disabled.  These parameters may be changed interactively.  After the
  first spectrum subsequent spectra begin with the values from the last
  spectrum.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_scale">scale = 1., dscale = 0.2</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='scale' Line='scale = 1., dscale = 0.2'>
  <DD>The initial scale and scale step.  This initializes the scale
  search parameters for the first spectrum.  If <I>dscale</I> is zero then
  there will be no search for a new scale and the <TT>'y'</TT> interactive function is
  disabled.  These parameters may be changed interactively.  After the
  first spectrum subsequent spectra begin with the values from the last
  spectrum.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_offset">offset = 1.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='offset' Line='offset = 1.'>
  <DD>The interactive search displays three candidate corrected spectra which
  have been normalized to a mean of one.  The offset is added and subtracted
  to separate the three candidates.  The value may be changed interactively.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_smooth">smooth = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='smooth' Line='smooth = 1'>
  <DD>The displayed candidate corrected spectra are smoothed by a moving
  boxcar average with a box size specified by this parameter.  The smoothing
  only applies to the displayed spectra and does not affect the measured
  RMS or the output corrected spectra.  The value may be changed interactively.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_cursor">cursor = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cursor' Line='cursor = ""'>
  <DD>Input cursor for the interactive graphics.  A null value selects the
  graphics cursor otherwise a file of cursor values may be specified.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_airmass">airmass</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='airmass' Line='airmass'>
  <DD>Query parameter for the airmass.  If the airmass is not in the image
  header under the keyword AIRMASS the user is queried for the airmass.
  This parameter should not be specified on the command line.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_answer">answer</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='answer' Line='answer'>
  <DD>Query parameter for responding to the interactive question.  This parameter
  should not be specified on the command line.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interp">interp = poly5</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interp' Line='interp = poly5'>
  <DD>The <B>package</B> parameter specifying the interpolation function for shifting
  the calibration spectra to match the input spectra.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Input one dimensional spectra are corrected to remove telluric features by
  dividing by shifted and scaled calibration spectra.  The calibration
  spectra are generally of hot, nearly featureless stars; hence this procedure
  is sometimes referred to as a B-star correction.  The shifting
  allows for possible small shifts or errors in the dispersion zeropoints.
  The intensity scaling allows for differences in the airmass and variations
  in the abundance of the telluric species.  The intensity scaling
  uses Beer's law which is the approximation that the change in absorption
  with abundance is an exponential relation.  
  <P>
  The following describes the correction.  Let J(x_i) be the calibration
  spectrum at a set of pixels x_i.  An interpolation function is fit to this
  spectrum to give J(x).  The shifted and scaled calibration function
  is then
  <P>
  <PRE>
      (1)  J'(x) = max (threshold, J(x+dx)) ** (A / A_cal * scale)
  </PRE>
  <P>
  where dx is the pixel shift parameter, A is the airmass of the input
  spectrum, A_cal is the airmass of the calibration spectrum, and
  scale is the scale parameter.  The operator "<TT>**</TT>" is exponentiation.
  The max operation limits the calibration spectrum to be greater
  than or equal to the specified threshold value.  If the calibration
  value is ever less than or equal to zero then the task will quit
  with a warning error.
  <P>
  The output corrected spectrum is then computed as
  <P>
  <PRE>
      (2)  I'(x_i) = I(x_i) / (J'(x_i) / &lt;J'&gt;)
  </PRE>
  <P>
  where I' is the corrected spectrum, I is the input spectrum, and &lt;J'&gt; is
  the mean of the shifted and scaled calibration spectrum to keep the output
  intensities comparable to the input spectrum.  The value of &lt;J'&gt; is
  printed in the output as the "<TT>normalization</TT>".  If the spectra are
  dispersion calibrated, possibly with different dispersion parameters, then
  the x values in (2) from the input spectrum are converted to matching
  pixels in the calibration spectrum using the dispersion functions of the
  two spectra.
  <P>
  The purpose of this task is to determine the best values of the
  shift and scale parameters dx and scale.  There
  are automatic and interactive methods provided.  The automatic
  methods are cross-correlation of the calibration and input spectra
  to find a shift and an iterative search for the in both
  shift and scale that minimizes the RMS of I' in some region.
  The automatic methods are performed first, if selected, followed
  by the interactive, graphical step.  The following describes
  the steps in the order in which they occur.
  <P>
  The initial values of the shift and scale are set by the parameters
  <I>shift</I> and <I>scale</I> for the first spectrum.  After that the values
  determined for the previous spectrum, those actually applied to correcting
  that spectrum, are used as the initial values for the next spectrum.  The
  search steps and sample regions are also initialized by task parameters but
  may be modified during the interactive step and the modified values apply
  to subsequent spectra.
  <P>
  If the <I>xcorr</I> parameter is yes and the <I>lag</I> parameter is
  not zero the calibration spectrum is cross-correlated against the input
  spectrum.  Each spectrum is prepared as follows.  A large scale continuum
  is fit by a quadratic chebyshev using 5 iterations of sigma clipping with a
  clipping factor of 3 sigma below the fit and 1 sigma above the fit and
  rejecting the deviant points along with one pixel on either side.  This
  attempts to eliminate the effects of absorption lines.  The continuum fit
  is subtracted from the spectrum and the spectrum is extended and tapered by
  a cosine function of length given by the <I>lag</I> parameter.
  <P>
  The prepared spectra are then cross-correlated by shifting the calibration
  spectrum plus and minus the specified <I>lag</I> amount about the current
  shift value.  Only the regions in the input spectrum specified by the
  sample regions parameter are used in the correlation.  This produces a
  correlation profile whose peak defines the relative shift between the two
  spectra.  The current shift value is updated.  This method assumes the
  common telluric features dominate within the specified sample regions.  The
  lag size should be roughly the profile widths of the telluric features.
  <P>
  If the <I>tweakrms</I> parameter is yes and <I>dshift</I> is greater than
  zero trial corrections at the current shift value and plus and minus one
  shift step with the scale value fixed at its current value are made and the
  RMS in the sample regions computed.  If the RMS is smallest at the current
  shift value the shift step is divided in half otherwise the current shift
  value is set to the shift with the lowest RMS.  The process is then
  repeated with the new shift and shift step values.  This continues until
  either the shift step is less than 0.01 pixels or the shift is more than
  two pixels from the initial shift.  In the latter case the final shift is
  reset to the original shift.
  <P>
  The scale factor is then varied if <I>dscale</I> is greater than zero by the
  scale step at a fixed shift in the same way as above to search for a
  smaller RMS in the sample regions.  This search terminates when the scale
  step is less than 0.01 or if the scale value has departed by 100% of the
  initial value.  In the latter case the scale value is left unchanged.
  <P>
  The search over the shifts and scales is repeated a second time after which
  the tweak algorithm terminates.
  <P>
  After the optional cross-correlation and tweak steps the interactive search
  mode may be entered.  This occurs if <I>interactive</I> = yes.  A query is
  asking whether to search interactively.  The answers may be "<TT>no</TT>", "<TT>yes</TT>",
  "<TT>NO</TT>", or "<TT>YES</TT>".  The lower case answers apply to the current spectrum and
  the upper case answers apply to all subsequent spectra.  This means that if
  an answer of "<TT>NO</TT>" or "<TT>YES</TT>" is given then there will be no further queries
  for the remaining input spectra.
  <P>
  If the interactive step is selected a graph of three candidate corrections
  for the input spectrum is displayed.  There also may be a graph of the
  calibration or input spectrum shown for reference.  Initially the
  calibration spectrum is displayed.  The additional graph may be toggled off
  and on and between the input and calibration spectra with the <TT>'c'</TT> and <TT>'d'</TT>
  keys.  The three candidate corrected spectra will be with the current shift
  and scale in the middle and plus or minus one step in either the shift or
  scale.  Initially the spectra will be at different scale values.
  Information about the current shift and scale and the step used is given in
  the graph title.
  <P>
  One may toggle between shift steps and scale steps with the <TT>'x'</TT> (for shift)
  or <TT>'y'</TT> (for scale) keys.  The RMS in the title is the RMS within the
  currently defined sample regions.  If one of the step values is zero then a
  display of different values of that parameter will not be selected.  The
  step size will need to be set with a colon command to search in that
  parameter.
  <P>
  If <TT>'x'</TT> is typed when the three spectra are at different shifts then the
  nearest spectrum to the y cursor at the x cursor position will be
  selected.  If the central spectrum is selected the step size is divided in
  half otherwise the current shift is changed and the  selected spectrum
  becomes the middle spectrum.  Three new spectra are then shown.  The same
  applies if <TT>'y'</TT> is typed when the three spectra are at different scales.
  This allows an interactive search similar to the iterative tweakrms method
  described previously except the user can use whatever criteria is desired
  to search for the best scale and shift.
  <P>
  There are additional keystrokes and colon commands to set or change sample
  regions, reset the current shift, scale, and step sizes, expand the step
  size in the current mode, adjust the offsets between the spectra, and
  get help.  The <TT>'w'</TT> key and GTOOLS colon commands are available to window
  the graphs.  Any changes in the x limits apply to both graphs while y limit
  adjustments apply to the graph pointed to by the cursor.
  <P>
  Two other commands require a short explanation.  The <TT>'a'</TT> key may
  be used to run the tweakrms algorithm starting from the current
  shift, scale, and steps and the current sample regions.  This allows
  one to graphically set or reset the sample regions before doing
  the RMS minimization.  The "<TT>:smooth</TT>" command and associated
  <I>smooth</I> task parameter allow the corrected spectra to be
  displayed with a boxcar smoothing to better see faint features in
  noise.  It is important to realize that the smoothing is only
  done on the displayed spectra.  The telluric correction and computed RMS
  are done in the unsmoothed data.
  <P>
  After the interactive step is quit with <TT>'q'</TT> or if the interactive
  step is not done then the final output spectrum is computed and
  written to the output image.  A brief log output is printed for
  each spectrum.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_cursor_keys_and_colon_commands">CURSOR KEYS AND COLON COMMANDS</A></H2>
  <! BeginSection: 'CURSOR KEYS AND COLON COMMANDS'>
  <UL>
  <PRE>
  ? - print help
  a - automatic RMS minimization within sample regions
  c - toggle calibration spectrum display
  d - toggle data spectrum display
  e - expand (double) the step for the current selection
  q - quit
  r - redraw the graphs
  s - add or reset sample regions
  w - window commands (see :/help for additional information)
  x - graph and select from corrected shifted candidates
  y - graph and select from corrected scaled candidates
  <P>
  :help           - print help
  :shift  [value] - print or reset the current shift
  :scale  [value] - print or reset the current scale
  :dshift [value] - print or reset the current shift step
  :dscale [value] - print or reset the current scale step
  :offset [value] - print or reset the current offset between spectra
  :sample [value] - print or reset the sample regions
  :smooth [value] - print or reset the smoothing box size
  </PRE>
  </UL>
  <! EndSection:   'CURSOR KEYS AND COLON COMMANDS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  To interactively search for a best correction with the default
  cross-correlation and tweak steps:
  <P>
  <PRE>
      cl&gt; telluric spec001.ms telspec001.ms spec005.ms
  </PRE>
  <P>
  2.  To search only for a scale factor:
  <P>
  <PRE>
      cl&gt; telluric spec001.ms telspec001.ms spec005.ms xcorr- dshift=0.
  </PRE>
  <P>
  3.  To processes a set of spectra non-interactively with the same calibration
  spectrum and to replace the input spectra with the corrected spectra and
  log the processing:
  <P>
  <PRE>
      cl&gt; telluric spec* "" calspec inter- &gt; log
  </PRE>
  <P>
  4.  To apply the simplest scaling by the ratio of the airmasses alone:
  <P>
  <PRE>
      cl&gt; telluric spec* tel//spec* calspec inter- xcorr- tweak- inter- \<BR>
      &gt;&gt;&gt; scale=1. shift=0.
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_revisions">REVISIONS</A></H2>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_TELLURIC">TELLURIC V2.12.3</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='TELLURIC' Line='TELLURIC V2.12.3'>
  <DD>The normalization is printed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_TELLURIC">TELLURIC V2.11.2</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='TELLURIC' Line='TELLURIC V2.11.2'>
  <DD>Threshold parameter added.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_TELLURIC">TELLURIC V2.11</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='TELLURIC' Line='TELLURIC V2.11'>
  <DD>This task is new in this version.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  skytweak
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'SUMMARY' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'CURSOR KEYS AND COLON COMMANDS' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>