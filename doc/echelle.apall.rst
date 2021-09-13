.. _apall:

apall — Extract 1D spectra (all parameters in one task)
=======================================================

**Package: echelle**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  apall -- Extract one dimensional sums across the apertures
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  apall input
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of input images.
  </DD>
  </DL>
  <DL>
  <DT><B>output = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output = ""'>
  <DD>List of output root names for extracted spectra.  If the null
  string is given or the end of the output list is reached before the end
  of the input list then the input image name is used as the output root name.
  This will not conflict with the input image since an aperture number
  extension is added for onedspec format, the extension "<TT>.ms</TT>" for multispec
  format, or the extension "<TT>.ec</TT>" for echelle format.
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
  <DT><B>format = "<TT>multispec</TT>" (onedspec|multispec|echelle|strip)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='format' Line='format = "multispec" (onedspec|multispec|echelle|strip)'>
  <DD>Format for output extracted spectra.  "<TT>Onedspec</TT>" format extracts each
  aperture to a separate image while "<TT>multispec</TT>" and "<TT>echelle</TT>" extract
  multiple apertures for the same image to a single output image.
  The "<TT>multispec</TT>" and "<TT>echelle</TT>" format selections differ only in the
  extension added.  The "<TT>strip</TT>" format produces a separate 2D image in
  which each column or line along the dispersion axis is shifted to
  exactly align the aperture based on the trace information.
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
  Input images without/with a database entry are skipped silently.
  </DD>
  </DL>
  <DL>
  <DT><B>profiles = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='profiles' Line='profiles = ""'>
  <DD>List of profile images for variance weighting or cleanning.   If variance
  weighting or cleanning a profile of each aperture is computed from the
  input image unless a profile image is specified, in which case the
  profile is computed from the profile image.  The profile image must
  have the same dimensions and dispersion and it is assumed that the
  spectra have the same position and profile shape as in the object
  spectra.  Use of a profile image is generally not required even for
  faint input spectra but the option is available for those who wish
  to use it.
  </DD>
  </DL>
  <P>
  <CENTER>PROCESSING PARAMETERS
  
  </CENTER><BR>
  <DL>
  <DT><B>interactive = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = yes'>
  <DD>Run this task interactively?  If the task is not run interactively then
  all user queries are suppressed and interactive aperture editing, trace
  fitting, and extraction review are disabled.
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
  <DL>
  <DT><B>extract = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='extract' Line='extract = yes'>
  <DD>Extract the one dimensional aperture sums?
  </DD>
  </DL>
  <DL>
  <DT><B>extras = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='extras' Line='extras = yes'>
  <DD>Extract the raw spectrum (if variance weighting is used), the sky spectrum
  (if background subtraction is used), and sigma spectrum (if variance
  weighting is used)?  This information is extracted to the third dimension
  of the output image.
  </DD>
  </DL>
  <DL>
  <DT><B>review = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='review' Line='review = yes'>
  <DD>Review the extracted spectra?  The <I>interactive</I> parameter must also be
  yes.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B>line = INDEF, nsum = 10</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='line' Line='line = INDEF, nsum = 10'>
  <DD>The dispersion line (line or column perpendicular to the dispersion
  axis) and number of adjacent lines (half before and half after unless
  at the end of the image) used in finding, recentering, resizing,
  and editing operations.  A line of INDEF selects the middle of the
  image along the dispersion axis.  A positive nsum selects a sum of
  lines and a negative selects a median of lines.
  </DD>
  </DL>
  <P>
  <CENTER>DEFAULT APERTURE PARAMETERS
  
  </CENTER><BR>
  <DL>
  <DT><B>lower = -5., upper = 5.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lower' Line='lower = -5., upper = 5.'>
  <DD>Default lower and upper aperture limits relative to the aperture center.
  These limits are used for apertures found with <B>apfind</B> and when
  defining the first aperture in <B>apedit</B>.
  </DD>
  </DL>
  <DL>
  <DT><B>apidtable = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='apidtable' Line='apidtable = ""'>
  <DD>Aperture identification table.  This may be either a text file or an
  image.  A text file consisting of lines with an aperture number, beam
  number, and aperture title or identification.  An image will contain the
  keywords SLFIBnnn with string value consisting of aperture number, beam
  number, optional right ascension and declination, and aperture title.  This
  information is used to assign aperture information automatically in
  <B>apfind</B> and <B>apedit</B>.
  </DD>
  </DL>
  <P>
  <CENTER>DEFAULT BACKGROUND PARAMETERS
  
  </CENTER><BR>
  <DL>
  <DT><B>b_function = "<TT>chebyshev</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='b_function' Line='b_function = "chebyshev"'>
  <DD>Default background fitting function.  The fitting function types are
  "<TT>chebyshev</TT>" polynomial, "<TT>legendre</TT>" polynomial, "<TT>spline1</TT>" linear spline, and
  "<TT>spline3</TT>" cubic spline.
  </DD>
  </DL>
  <DL>
  <DT><B>b_order = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='b_order' Line='b_order = 1'>
  <DD>Default background function order.  The order refers to the number of
  terms in the polynomial functions or the number of spline pieces in the spline
  functions.
  </DD>
  </DL>
  <DL>
  <DT><B>b_sample = "<TT>-10:-6,6:10</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='b_sample' Line='b_sample = "-10:-6,6:10"'>
  <DD>Default background sample.  The sample is given by a set of colon separated
  ranges each separated by either whitespace or commas.  The string "<TT>*</TT>" refers
  to all points.  Note that the background coordinates are relative to the
  aperture center and not image pixel coordinates so the endpoints need not
  be integer.
  </DD>
  </DL>
  <DL>
  <DT><B>b_naverage = -3</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='b_naverage' Line='b_naverage = -3'>
  <DD>Default number of points to average or median.  Positive numbers
  average that number of sequential points to form a fitting point.
  Negative numbers median that number, in absolute value, of sequential
  points.  A value of 1 does no averaging and each data point is used in the
  fit.
  </DD>
  </DL>
  <DL>
  <DT><B>b_niterate = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='b_niterate' Line='b_niterate = 0'>
  <DD>Default number of rejection iterations.  If greater than zero the fit is
  used to detect deviant fitting points and reject them before repeating the
  fit.  The number of iterations of this process is given by this parameter.
  </DD>
  </DL>
  <DL>
  <DT><B>b_low_reject = 3., b_high_reject = 3.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='b_low_reject' Line='b_low_reject = 3., b_high_reject = 3.'>
  <DD>Default background lower and upper rejection sigmas.  If greater than zero
  points deviating from the fit below and above the fit by more than this
  number of times the sigma of the residuals are rejected before refitting.
  </DD>
  </DL>
  <DL>
  <DT><B>b_grow = 0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='b_grow' Line='b_grow = 0.'>
  <DD>Default reject growing radius.  Points within a distance given by this
  parameter of any rejected point are also rejected.
  </DD>
  </DL>
  <P>
  <CENTER>APERTURE CENTERING PARAMETERS
  
  </CENTER><BR>
  <DL>
  <DT><B>width = 5.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='width' Line='width = 5.'>
  <DD>Width of spectrum profiles.  This parameter is used for the profile
  centering algorithm in this and other tasks.
  </DD>
  </DL>
  <DL>
  <DT><B>radius = 10.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='radius' Line='radius = 10.'>
  <DD>The profile centering error radius for the centering algorithm.
  </DD>
  </DL>
  <DL>
  <DT><B>threshold = 0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='threshold' Line='threshold = 0.'>
  <DD>Centering threshold for the centering algorithm.  The range of pixel intensities
  near the initial centering position must exceed this threshold.
  </DD>
  </DL>
  <P>
  <CENTER>AUTOMATIC FINDING AND ORDERING PARAMETERS
  
  </CENTER><BR>
  <DL>
  <DT><B>nfind</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nfind' Line='nfind'>
  <DD>Maximum number of apertures to be defined.  This is a query parameter
  so the user is queried for a value except when given explicitly on
  the command line.
  </DD>
  </DL>
  <DL>
  <DT><B>minsep = 5.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='minsep' Line='minsep = 5.'>
  <DD>Minimum separation between spectra.  Weaker spectra or noise within this
  distance of a stronger spectrum are rejected.
  </DD>
  </DL>
  <DL>
  <DT><B>maxsep = 1000.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maxsep' Line='maxsep = 1000.'>
  <DD>Maximum separation between adjacent spectra.  This parameter
  is used to identify missing spectra in uniformly spaced spectra produced
  by fiber spectrographs.  If two adjacent spectra exceed this separation
  then it is assumed that a spectrum is missing and the aperture identification
  assignments will be adjusted accordingly.
  </DD>
  </DL>
  <DL>
  <DT><B>order = "<TT>increasing</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='order' Line='order = "increasing"'>
  <DD>When assigning aperture identifications order the spectra "<TT>increasing</TT>"
  or "<TT>decreasing</TT>" with increasing pixel position (left-to-right or
  right-to-left in a cross-section plot of the image).
  </DD>
  </DL>
  <P>
  <CENTER>RECENTERING PARAMETERS
  
  </CENTER><BR>
  <DL>
  <DT><B>aprecenter = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='aprecenter' Line='aprecenter = ""'>
  <DD>List of apertures to be used in shift calculation.
  </DD>
  </DL>
  <DL>
  <DT><B>npeaks = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='npeaks' Line='npeaks = INDEF'>
  <DD>Select the specified number of apertures with the highest peak values
  to be recentered.  If the number is INDEF all apertures will be selected.
  If the value is less than 1 then the value is interpreted as a fraction
  of total number of apertures.
  </DD>
  </DL>
  <DL>
  <DT><B>shift = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='shift' Line='shift = yes'>
  <DD>Use the average shift from recentering the apertures selected by the
  <I>aprecenter</I> parameter to apply to the apertures selected by the
  <I>apertures</I> parameter.  The recentering is then a constant shift for
  all apertures.
  </DD>
  </DL>
  <P>
  <CENTER>RESIZING PARAMETERS
  
  </CENTER><BR>
  <DL>
  <DT><B>llimit = INDEF, ulimit = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='llimit' Line='llimit = INDEF, ulimit = INDEF'>
  <DD>Lower and upper aperture size limits.  If the parameter <I>ylevel</I> is
  INDEF then these limits are assigned to all apertures.  Otherwise
  these parameters are used as limits to the resizing operation.
  A value of INDEF places the aperture limits at the image edge (for the
  dispersion line used).
  </DD>
  </DL>
  <DL>
  <DT><B>ylevel = 0.1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ylevel' Line='ylevel = 0.1'>
  <DD>Data level at which to set aperture limits.  If it is INDEF then the
  aperture limits are set at the values given by the parameters
  <I>llimit</I> and <I>ulimit</I>.  If it is not INDEF then it is a
  fraction of the peak or an actual data level depending on the parameter
  <I>peak</I>.  It may be relative to a local background or to zero
  depending on the parameter <I>bkg</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>peak = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='peak' Line='peak = yes'>
  <DD>Is the data level specified by <I>ylevel</I> a fraction of the peak?
  </DD>
  </DL>
  <DL>
  <DT><B>bkg = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='bkg' Line='bkg = yes'>
  <DD>Subtract a simple background when interpreting the <B>ylevel</B> parameter.
  The background is a slope connecting the first inflection points
  away from the aperture center.
  </DD>
  </DL>
  <DL>
  <DT><B>r_grow = 0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='r_grow' Line='r_grow = 0.'>
  <DD>Change the lower and upper aperture limits by this fractional amount.
  The factor is multiplied by each limit and the result added to limit.
  </DD>
  </DL>
  <DL>
  <DT><B>avglimits = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='avglimits' Line='avglimits = no'>
  <DD>Apply the average lower and upper aperture limits to all apertures.
  </DD>
  </DL>
  <P>
  <CENTER>TRACING PARAMETERS
  
  </CENTER><BR>
  <DL>
  <DT><B>t_nsum = 10</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='t_nsum' Line='t_nsum = 10'>
  <DD>Number of dispersion lines to be summed at each step along the dispersion.
  </DD>
  </DL>
  <DL>
  <DT><B>t_step = 10</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='t_step' Line='t_step = 10'>
  <DD>Step along the dispersion axis between determination of the spectrum
  positions.
  </DD>
  </DL>
  <DL>
  <DT><B>t_nlost = 3</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='t_nlost' Line='t_nlost = 3'>
  <DD>Number of consecutive steps in which the profile is lost before quitting
  the tracing in one direction.  To force tracing to continue through
  regions of very low signal this parameter can be made large.  Note,
  however, that noise may drag the trace away before it recovers.
  </DD>
  </DL>
  <DL>
  <DT><B>t_function = "<TT>legendre</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='t_function' Line='t_function = "legendre"'>
  <DD>Default trace fitting function.  The fitting function types are
  "<TT>chebyshev</TT>" polynomial, "<TT>legendre</TT>" polynomial, "<TT>spline1</TT>" linear spline, and
  "<TT>spline3</TT>" cubic spline.
  </DD>
  </DL>
  <DL>
  <DT><B>t_order = 2</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='t_order' Line='t_order = 2'>
  <DD>Default trace function order.  The order refers to the number of
  terms in the polynomial functions or the number of spline pieces in the spline
  functions.
  </DD>
  </DL>
  <DL>
  <DT><B>t_sample = "<TT>*</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='t_sample' Line='t_sample = "*"'>
  <DD>Default fitting sample.  The sample is given by a set of colon separated
  ranges each separated by either whitespace or commas.  The string "<TT>*</TT>" refers
  to all points.
  </DD>
  </DL>
  <DL>
  <DT><B>t_naverage = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='t_naverage' Line='t_naverage = 1'>
  <DD>Default number of points to average or median.  Positive numbers
  average that number of sequential points to form a fitting point.
  Negative numbers median that number, in absolute value, of sequential
  points.  A value of 1 does no averaging and each data point is used in the
  </DD>
  </DL>
  <DL>
  <DT><B>t_niterate = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='t_niterate' Line='t_niterate = 0'>
  <DD>Default number of rejection iterations.  If greater than zero the fit is
  used to detect deviant traced positions and reject them before repeating the
  fit.  The number of iterations of this process is given by this parameter.
  </DD>
  </DL>
  <DL>
  <DT><B>t_low_reject = 3., t_high_reject = 3.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='t_low_reject' Line='t_low_reject = 3., t_high_reject = 3.'>
  <DD>Default lower and upper rejection sigma.  If greater than zero traced
  points deviating from the fit below and above the fit by more than this
  number of times the sigma of the residuals are rejected before refitting.
  </DD>
  </DL>
  <DL>
  <DT><B>t_grow = 0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='t_grow' Line='t_grow = 0.'>
  <DD>Default reject growing radius.  Traced points within a distance given by this
  parameter of any rejected point are also rejected.
  </DD>
  </DL>
  <P>
  <CENTER>EXTRACTION PARAMETERS
  
  </CENTER><BR>
  <DL>
  <DT><B>background = "<TT>none</TT>" (none|average|median|minimum|fit)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='background' Line='background = "none" (none|average|median|minimum|fit)'>
  <DD>Type of background subtraction.  The choices are "<TT>none</TT>" for no background
  subtraction, "<TT>average</TT>" to average the background within the background
  regions, "<TT>median</TT>" to use the median in the background regions, "<TT>minimum</TT>" to
  use the minimum in the background regions, or "<TT>fit</TT>" to fit across the
  dispersion using the background within the background regions.  Note that
  the "<TT>average</TT>" option does not do any medianing or bad pixel checking,
  something which is recommended.  The fitting option is slower than the
  other options and requires additional fitting parameter.
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
  <DT><B>weights = "<TT>none</TT>" (none|variance)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='weights' Line='weights = "none" (none|variance)'>
  <DD>Type of extraction weighting.  Note that if the <I>clean</I> parameter is
  set then the weights used are "<TT>variance</TT>" regardless of the weights
  specified by this parameter.  The choices are:
  <DL>
  <DT><B>"<TT>none</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"none"'>
  <DD>The pixels are summed without weights except for partial pixels at the
  ends.
  </DD>
  </DL>
  <DL>
  <DT><B>"<TT>variance</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"variance"'>
  <DD>The extraction is weighted by the variance based on the data values
  and a poisson/ccd model using the <I>gain</I> and <I>readnoise</I>
  parameters.
  </DD>
  </DL>
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
  <DT><B>saturation = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='saturation' Line='saturation = INDEF'>
  <DD>Saturation or nonlinearity level in data units.  During variance weighted
  extractions wavelength points having any pixels above this value are
  excluded from the profile determination and the sigma spectrum extraction
  output, if selected by the <I>extras</I> parameter, flags wavelengths with
  saturated pixels with a negative sigma.
  </DD>
  </DL>
  <DL>
  <DT><B>readnoise = 0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='readnoise' Line='readnoise = 0.'>
  <DD>Read out noise in photons.  This parameter defines the minimum noise
  sigma.  It is defined in terms of photons (or electrons) and scales
  to the data values through the gain parameter.  A image header keyword
  (case insensitive) may be specified to get the value from the image.
  </DD>
  </DL>
  <DL>
  <DT><B>gain = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='gain' Line='gain = 1'>
  <DD>Detector gain or conversion factor between photons/electrons and
  data values.  It is specified as the number of photons per data value.
  A image header keyword (case insensitive) may be specified to get the value
  from the image.
  </DD>
  </DL>
  <DL>
  <DT><B>lsigma = 4., usigma = 4.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lsigma' Line='lsigma = 4., usigma = 4.'>
  <DD>Lower and upper rejection thresholds, given as a number of times the
  estimated sigma of a pixel, for cleaning.
  </DD>
  </DL>
  <DL>
  <DT><B>nsubaps = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nsubaps' Line='nsubaps = 1'>
  <DD>During extraction it is possible to equally divide the apertures into
  this number of subapertures.  For multispec format all subapertures will
  be in the same file with aperture numbers of 1000*(subap-1)+ap where
  subap is the subaperture (1 to nsubaps) and ap is the main aperture
  number.  For echelle format there will be a separate echelle format
  image containing the same subaperture from each order.  The name
  will have the subaperture number appended.  For onedspec format
  each subaperture will be in a separate file with extensions and
  aperture numbers as in the multispec format.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Additional parameters</H3>
  <! BeginSection: 'ADDITIONAL PARAMETERS'>
  <UL>
  Dispersion axis and I/O parameters are taken from the package parameters.
  </UL>
  <! EndSection:   'ADDITIONAL PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task provides functions for defining, modifying, tracing, and
  extracting apertures from two dimensional spectra.  The functions
  desired are selected using switch parameters.  When the task is
  run interactively queries are made at each step allowing additional
  control of the operations performed on each input image.
  <P>
  The functions, in the order in which they are generally performed, are
  summarized below.
  <DL>
  <DT><B>o</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='o' Line='o'>
  <DD>Automatically find a specified number of spectra and assign default
  apertures.  Apertures may also be inherited from another image or
  defined using an interactive graphical interface called the <I>aperture
  editor</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>o</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='o' Line='o'>
  <DD>Recenter selected reference apertures on the image spectrum profiles.
  </DD>
  </DL>
  <DL>
  <DT><B>o</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='o' Line='o'>
  <DD>Resize the selected reference apertures based on spectrum profile width.
  </DD>
  </DL>
  <DL>
  <DT><B>o</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='o' Line='o'>
  <DD>Interactively define or adjust aperture definitions using a graphical
  interface called the <I>aperture editor</I>.  All function may also
  be performed from this editor and, so, provides an alternative
  method of processing and extracting spectra.
  </DD>
  </DL>
  <DL>
  <DT><B>o</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='o' Line='o'>
  <DD>Trace the positions of the selected spectra profiles from a starting image line
  or column to other image lines or columns and fit a smooth function.
  The trace function is used to shift the center of the apertures
  at each dispersion point in the image.
  </DD>
  </DL>
  <DL>
  <DT><B>o</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='o' Line='o'>
  <DD>Extract the flux in the selected apertures into one dimensional spectra in
  various formats.  This includes possible background subtraction, variance
  weighting, and bad pixel rejection.
  </DD>
  </DL>
  <P>
  Each of these functions has different options and parameters.  In
  addition to selecting any of these functions in this task, they may
  also be selected using the aperture editor and as individual
  commands (which themselves allow selection of other functions).  When
  broken down into individual tasks the parameters are also sorted by
  their function though there are then some mutual parameter
  interdependencies.  This functional decomposition is what was available
  prior to the addition of the <B>apall</B> task.  It is recommended that
  this task be used because it collects all the parameters in one
  place eliminating confusion over where a particular parameter
  is defined.  However, documenting the various functions
  is better organized in terms of the separate descriptions given for
  each of the functions; namely under the help topics
  <B>apdefault, apfind, aprecenter, apresize, apedit,
  aptrace</B>, and <B>apsum</B>.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  This example may be executed if desired.  First we create an artificial
  spectrum with four spectra and a background.  After it is created you
  can display or plot it.  Next we define the dispersion axis and set the
  verbose flag to better illustrate what is happening.  The task APALL
  is run with the default parameters except for background fitting and
  subtracting added.  The text beginning with # are comments of things to
  try and do.
  <P>
  <PRE>
    ap&gt; artdata
    ar&gt; unlearn artdata
    ar&gt; mk1dspec apdemo1d nl=50
    ar&gt; mk2dspec apdemo2d model=STDIN
    apdemo1d 1. gauss 3 0 20 .01
    apdemo1d .8 gauss 3 0 40 .01
    apdemo1d .6 gauss 3 0 60 .01
    apdemo1d .4 gauss 3 0 80 .01
    [EOF=Control D or Control Z]
    ar&gt; mknoise apdemo2d background=100. rdnoise=3. poisson+
    ar&gt; bye
    # Display or plot the spectrum
    ap&gt; dispaxis=2; verbose=yes
    ap&gt; unlearn apall
    ap&gt; apall apdemo2d back=fit
    Searching aperture database ...
    Find apertures for apdemo2d?  (yes): 
    Finding apertures ...
    Number of apertures to be found automatically (1): 4
    Jul 31 16:55: FIND - 4 apertures found for apdemo2d.
    Resize apertures for apdemo2d?  (yes): 
    Resizing apertures ...
    Jul 31 16:55: RESIZE - 4 apertures resized for apdemo2d.
    Edit apertures for apdemo2d?  (yes):
    # Get a list of commands with <TT>'?'</TT>
    # See all the parameters settings with :par
    # Try deleting and marking a spectrum with <TT>'d'</TT> and <TT>'m'</TT>
    # Look at the background fitting parameters with <TT>'b'</TT> (exit with <TT>'q'</TT>)
    # Exit with <TT>'q'</TT>
    Trace apertures for apdemo2d?  (yes): 
    Fit traced positions for apdemo2d interactively?  (yes):
    Tracing apertures ...
    Fit curve to aperture 1 of apdemo2d interactively  (yes):
    # You can use ICFIT commands to adjust the fit.
    Fit curve to aperture 2 of apdemo2d interactively  (yes): n 
    Fit curve to aperture 3 of apdemo2d interactively  (no): 
    Fit curve to aperture 4 of apdemo2d interactively  (no): y 
    Jul 31 16:56: TRACE - 4 apertures traced in apdemo2d.
    Write apertures for apdemo2d to apdemosdb  (yes): 
    Jul 31 16:56: DATABASE - 4 apertures for apdemo2d written to database.
    Extract aperture spectra for apdemo2d?  (yes): 
    Review extracted spectra from apdemo2d?  (yes):
    Extracting apertures ...
    Review extracted spectrum for aperture 1 from apdemo2d?  (yes):
    # Type <TT>'q'</TT> to quit
    Jul 31 16:56: EXTRACT - Aperture 1 from apdemo2d --&gt; apdemo2d.ms
    Review extracted spectrum for aperture 2 from apdemo2d?  (yes): N
    Jul 31 16:56: EXTRACT - Aperture 2 from apdemo2d --&gt; apdemo2d.ms
    Jul 31 16:56: EXTRACT - Aperture 3 from apdemo2d --&gt; apdemo2d.ms
    Jul 31 16:57: EXTRACT - Aperture 4 from apdemo2d --&gt; apdemo2d.ms
  </PRE>
  <P>
  2. To extract a series of similar spectra noninteractively using a
  reference for the aperture definitions, then recentering and resizing
  but not retracing:
  <P>
  <PRE>
    ap&gt; apall fib*.imh ref=flat inter- trace-
  </PRE>
  <P>
  Note that the interactive flag automatically turns off the edit, fittrace,
  and review options and the reference image eliminates the find
  (find only occurs if there are no initial apertures).
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>APALL V2.11</B></DT>
  <! Sec='REVISIONS' Level=0 Label='APALL' Line='APALL V2.11'>
  <DD>The "<TT>apertures</TT>" parameter can be used to select apertures for resizing,
  recentering, tracing, and extraction.  This parameter name was previously
  used for selecting apertures in the recentering algorithm.  The new
  parameter name for this is now "<TT>aprecenter</TT>".
  <P>
  The aperture ID table information may now be contained in the
  image header under the keywords SLFIBnnn.
  <P>
  The "<TT>nsubaps</TT>" parameter now allows onedspec and echelle output formats.
  The echelle format is appropriate for treating each subaperture as
  a full echelle extraction.
  </DD>
  </DL>
  <DL>
  <DT><B>APALL V2.10.3</B></DT>
  <! Sec='REVISIONS' Level=0 Label='APALL' Line='APALL V2.10.3'>
  <DD>The dispersion axis parameter was moved to purely a package parameter.
  <P>
  As a final step when computing a weighted/cleaned spectrum the total
  fluxes from the weighted spectrum and the simple unweighted spectrum
  (excluding any deviant and saturated pixels) are computed and a
  "<TT>bias</TT>" factor of the ratio of the two fluxes is multiplied into
  the weighted spectrum and the sigma estimate.  This makes the total
  fluxes the same.  In this version the bias factor is recorded in the logfile
  if one is kept.  Also a check is made for unusual bias factors.
  If the two fluxes disagree by more than a factor of two a warning
  is given on the standard output and the logfile with the individual
  total fluxes as well as the bias factor.  If the bias factor is
  negative a warning is also given and no bias factor is applied.
  In the previous version a negative (inverted) spectrum would result.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  apdefault, apfind, aprecenter, apresize, apedit, aptrace, apsum
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'ADDITIONAL PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
