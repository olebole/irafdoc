.. _apnoise:

apnoise — Compute and examine noise characteristics of spectra
==============================================================

**Package: apextract**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  apnoise -- Compute and examine noise characteristics of spectra
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  apnoise input dmin dmax nbins
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of input spectra to examine.
  </DD>
  </DL>
  <DL>
  <DT><B>apertures = "<TT></TT>"</B></DT>
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
  <DT><B>references = "<TT></TT>"</B></DT>
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
  <DT><B>dmin, dmax, nbins</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dmin' Line='dmin, dmax, nbins'>
  <DD>The noise sigma is computed in a set of bins over the specified
  range of image data numbers.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B>interactive = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = yes'>
  <DD>Run this task interactively?  If the task is not run interactively then
  all user queries are suppressed and interactive aperture editing and trace
  fitting are disabled.
  </DD>
  </DL>
  <DL>
  <DT><B>find = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='find' Line='find = yes'>
  <DD>Find the spectra and define apertures automatically?  In order for
  spectra to be found automatically there must be no apertures for the
  input image or reference image defined in the database.
  </DD>
  </DL>
  <DL>
  <DT><B>recenter = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='recenter' Line='recenter = yes'>
  <DD>Recenter the apertures?
  </DD>
  </DL>
  <DL>
  <DT><B>resize = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='resize' Line='resize = yes'>
  <DD>Resize the apertures?
  </DD>
  </DL>
  <DL>
  <DT><B>edit = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='edit' Line='edit = yes'>
  <DD>Edit the apertures?  The <I>interactive</I> parameter must also be yes.
  </DD>
  </DL>
  <DL>
  <DT><B>trace = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='trace' Line='trace = yes'>
  <DD>Trace the apertures?
  </DD>
  </DL>
  <DL>
  <DT><B>fittrace = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fittrace' Line='fittrace = yes'>
  <DD>Interactively fit the traced positions by a function?  The <I>interactive</I>
  parameter must also be yes.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B>line = INDEF, nsum = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='line' Line='line = INDEF, nsum = 1'>
  <DD>The dispersion line (line or column perpendicular to the dispersion
  axis) and number of adjacent lines (half before and half after unless
  at the end of the image) used in finding, recentering, resizing,
  and editing operations.  For tracing this is the starting line and
  the same number of lines are summed at each tracing point.  A line of
  INDEF selects the middle of the image along the dispersion axis.
  A positive nsum sums the lines and a negative value takes the median.
  However, for tracing only sums are allowed and the absolute value
  is used.
  </DD>
  </DL>
  <DL>
  <DT><B>threshold = 10.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='threshold' Line='threshold = 10.'>
  <DD>Division threshold.  If a pixel in the two dimensional normalization spectrum
  is less than this value then a flat field value of 1 is output.
  </DD>
  </DL>
  <P>
  The following parameters control the profile and spectrum fitting.
  <DL>
  <DT><B>background = "<TT>none</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='background' Line='background = "none"'>
  <DD>Type of background subtraction.  The choices are "<TT>none</TT>" for no
  background subtraction, "<TT>average</TT>" to average the background within the
  background regions, or "<TT>fit</TT>" to fit across the dispersion using the
  background within the background regions.  Note that the "<TT>average</TT>"
  option does not do any medianing or bad pixel checking; it is faster
  than fitting however.  Background subtraction also requires that the
  background fitting parameters are properly defined.  For the "<TT>average</TT>"
  option only the background sample regions parameter is used.
  </DD>
  </DL>
  <DL>
  <DT><B>pfit = "<TT>fit1d</TT>" (fit1d|fit2d)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pfit' Line='pfit = "fit1d" (fit1d|fit2d)'>
  <DD>Profile fitting algorithm to use with variance weighting or cleaning.
  When determining a profile the two dimensional spectrum is divided by
  an estimate of the one dimensional spectrum to form a normalized two
  dimensional spectrum profile.  This profile is then smoothed by fitting
  one dimensional functions, "<TT>fit1d</TT>", along the lines or columns most closely
  corresponding to the dispersion axis or a special two dimensional
  function, "<TT>fit2d</TT>", described by Marsh (see <B>approfile</B>).
  </DD>
  </DL>
  <DL>
  <DT><B>clean = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='clean' Line='clean = no'>
  <DD>Detect and replace deviant pixels?
  </DD>
  </DL>
  <DL>
  <DT><B>skybox = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='skybox' Line='skybox = 1'>
  <DD>Box car smoothing length for sky background when using background
  subtraction.  Since the background noise is often the limiting factor
  for good extraction one may box car smooth the sky to improve the
  statistics in smooth background regions at the expense of distorting
  the subtraction near spectral features.  This is most appropriate when
  the sky regions are limited due to a small slit length.
  </DD>
  </DL>
  <DL>
  <DT><B>saturation = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='saturation' Line='saturation = INDEF'>
  <DD>Saturation or nonlinearity level.  During variance weighted extractions
  wavelength points having any pixels above this value are excluded from the
  profile determination.
  </DD>
  </DL>
  <DL>
  <DT><B>readnoise = "<TT>0.</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='readnoise' Line='readnoise = "0."'>
  <DD>Read out noise in photons.  This parameter defines the minimum noise
  sigma.  It is defined in terms of photons (or electrons) and scales
  to the data values through the gain parameter.  A image header keyword
  (case insensitive) may be specified to get the value from the image.
  </DD>
  </DL>
  <DL>
  <DT><B>gain = "<TT>1.</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='gain' Line='gain = "1."'>
  <DD>Detector gain or conversion factor between photons/electrons and
  data values.  It is specified as the number of photons per data value.
  A image header keyword (case insensitive) may be specified to get the value
  from the image.
  </DD>
  </DL>
  <DL>
  <DT><B>lsigma = 3., usigma = 3.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lsigma' Line='lsigma = 3., usigma = 3.'>
  <DD>Lower and upper rejection thresholds, given as a number of times the
  estimated sigma of a pixel, for cleaning.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Additional parameters</H3>
  <! BeginSection: 'ADDITIONAL PARAMETERS'>
  <UL>
  I/O parameters and the default dispersion axis are taken from the
  package parameters, the default aperture parameters from
  <B>apdefault</B>, automatic aperture finding parameters from
  <B>apfind</B>, recentering parameters from <B>aprecenter</B>, resizing
  parameters from <B>apresize</B>, parameters used for centering and
  editing the apertures from <B>apedit</B>, and tracing parameters from
  <B>aptrace</B>.
  </UL>
  <! EndSection:   'ADDITIONAL PARAMETERS'>
  <H3>Cursor commands</H3>
  <! BeginSection: 'CURSOR COMMANDS'>
  <UL>
  The following cursor keys and colon commands are available during the
  display of the noise sigmas and noise model.  See <B>apedit</B> for
  the commands for that mode.
  <P>
  <PRE>
  ?  Print command help
  q  Quit
  r  Redraw	
  w  Window the graph (see :/help)
  I  Interupt immediately
  <P>
  :gain &lt;value&gt;		Check or set the gain model parameter
  :readnoise &lt;value&gt;	Check or set the read noise model parameter
  <P>
  Also see the CURSOR MODE commands (:.help) and the windowing commands
  (:/help).
  </PRE>
  </UL>
  <! EndSection:   'CURSOR COMMANDS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <B>Apnoise</B> computes the noise sigma as a function of data value
  using the same profile model used for weighted extraction and
  cosmic ray cleanning.  In particular, the residuals used in computing the
  noise sigma are the same as those during cleanning.  By looking
  at the noise sigma as a function of data value as compared to that
  predicted by the noise model based on the read out noise and gain
  parameters one can then better refine these values for proper
  rejection of cosmic rays without rejection of valid data.
  So this task can be used to check or deduce these values and also
  to adjust them to include additional sources of error such as
  flat field noise and, especially, an additional source of noise due
  to the accuracy of the profile modeling.
  <P>
  The first part of this task follows the standard model of allowing
  one to define apertures by finding, recentering, editing, and
  tracing.  If one has previously defined apertures then these
  steps can be skipped.  Once the apertures are defined the apertures
  are internally extracted using the profile modeling (see <B>approfile</B>)
  with the optional background subtraction, cleanning, and choices of
  profile fitting algorithm, "<TT>fit1d</TT>" or "<TT>fit2d</TT>".  But rather than
  outputing the extracted spectrum as in <B>apsum</B> or <B>apall</B>
  or various functions of the data and profile model as in <B>apfit</B>,
  <B>apnormalize</B>, or <B>apflatten</B>, the task computes the
  residuals for all points in all apertures (essentially the same
  as the difference output of <B>apfit</B>) and determines the
  sigma (population corrected RMS) as a function of model data value
  in the specified bins.  The bins are defined by a minimum and
  maximum data value (found using <B>minmax</B>, <B>implot</B>, or
  <B>imexamine</B>) and the number of bins.
  <P>
  The noise sigma values, with their estimated uncertainties, are then
  plotted as a function of data numer.  A curve representing the specified
  read out noise and gain is also plotted.  The user then has the
  option of varying these two parameters with colon commands.  The
  aim of this is to find a noise model which either represents the
  measure noise sigmas or at least exceeds them so that only valid
  outliers such as cosmic rays will be rejected during cleanning.
  The interactive graphical mode only has this function.  The other
  keys and colon commands are the standard ones for redrawing, windowing,
  and quitting.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  To check that the read noise and gain parameters are reasonable for
  cleaning <B>apnoise</B> is run.  In this case it is assumed that the
  apertures have already been defined and traced.
  <P>
  <PRE>
  	cl&gt; minmax lsobj
  	    lsobj  -2.058870315551758  490.3247375488282
  	cl&gt; apnoise lsobj 0 500 50 rece- resi- edit- trace-
  	    A graph of the noise sigma for data between 0 and 500
  	    data numbers is given with a line showing the
  	    expected value for the current read noise and gain.
  	    The read noise and gain may be varied if desired.
  	    Exit with <TT>'q'</TT>
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>APNOISE V2.11</B></DT>
  <! Sec='REVISIONS' Level=0 Label='APNOISE' Line='APNOISE V2.11'>
  <DD>The "<TT>apertures</TT>" parameter can be used to select apertures for resizing,
  recentering, tracing, and extraction.  This parameter name was previously
  used for selecting apertures in the recentering algorithm.  The new
  parameter name for this is now "<TT>aprecenter</TT>".
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  apbackground, approfile, apvariance, apfit, icfit, minmax,
  apdefault, apfind, aprecenter, apresize, apedit, aptrace, apsum
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'ADDITIONAL PARAMETERS' 'CURSOR COMMANDS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
