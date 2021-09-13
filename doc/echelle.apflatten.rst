apflatten — Remove overall spectral and profile shapes from flat fields
=======================================================================

**Package: echelle**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>apflatten (Sep96)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.twodspec.apextract</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>apflatten (Sep96)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>apflatten</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  apflatten -- Create flat fields for fiber or narrow aperture spectra
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  apflatten input output
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of input flat field observations.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output = ""'>
  <DD>List of output flat field images.  If no output name is given then the
  input name is used as a root with the extension "<TT>.flat</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_apertures">apertures = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='apertures' Line='apertures = ""'>
  <DD>Apertures to recenter, resize, trace, and flatten.  This only applies
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
  <DT><B><A NAME="l_recenter">recenter = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='recenter' Line='recenter = yes'>
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
  <DL>
  <DT><B><A NAME="l_flatten">flatten = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='flatten' Line='flatten = yes'>
  <DD>Remove the profile shape and flat field spectrum leaving only
  sensitivity variations?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fitspec">fitspec = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fitspec' Line='fitspec = yes'>
  <DD>Fit normalization spectrum interactively?  The <I>interactive</I>
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
  A positive nsum sums the lines and a negative value takes the median.
  However, for tracing only sums are allowed and the absolute value
  is used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_threshold">threshold = 10.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='threshold' Line='threshold = 10.'>
  <DD>Division threshold.  If a pixel in the two dimensional normalization spectrum
  is less than this value then a flat field value of 1 is output.
  </DD>
  </DL>
  <P>
  The following parameters control the profile and spectrum fitting.
  <DL>
  <DT><B><A NAME="l_pfit">pfit = "<TT>fit1d</TT>" (fit1d|fit2d)</A></B></DT>
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
  <DT><B><A NAME="l_clean">clean = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='clean' Line='clean = no'>
  <DD>Detect and replace deviant pixels?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_saturation">saturation = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='saturation' Line='saturation = INDEF'>
  <DD>Saturation or nonlinearity level.  During variance weighted extractions
  wavelength points having any pixels above this value are excluded from the
  profile determination.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_readnoise">readnoise = 0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='readnoise' Line='readnoise = 0.'>
  <DD>Read out noise in photons.  This parameter defines the minimum noise
  sigma.  It is defined in terms of photons (or electrons) and scales
  to the data values through the gain parameter.  A image header keyword
  (case insensitive) may be specified to get the value from the image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_gain">gain = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='gain' Line='gain = 1'>
  <DD>Detector gain or conversion factor between photons/electrons and
  data values.  It is specified as the number of photons per data value.
  A image header keyword (case insensitive) may be specified to get the value
  from the image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_lsigma">lsigma = 3., usigma = 3.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lsigma' Line='lsigma = 3., usigma = 3.'>
  <DD>Lower and upper rejection thresholds, given as a number of times the
  estimated sigma of a pixel, for cleaning.
  </DD>
  </DL>
  <P>
  The following parameters are used to fit the normalization spectrum using
  the ICFIT routine.
  <DL>
  <DT><B><A NAME="l_function">function = "<TT>legendre</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='function' Line='function = "legendre"'>
  <DD>Fitting function for the normalization spectra.  The choices are "<TT>legendre</TT>"
  polynomial, "<TT>chebyshev</TT>" polynomial, linear spline ("<TT>spline1</TT>"), and
  cubic spline ("<TT>spline3</TT>").
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_order">order = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='order' Line='order = 1'>
  <DD>Number of polynomial terms or number of spline pieces for the fitting function.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_sample">sample = "<TT>*</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sample' Line='sample = "*"'>
  <DD>Sample regions for fitting points.  Intervals are separated by "<TT>,</TT>" and an
  interval may be one point or a range separated by "<TT>:</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_naverage">naverage = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='naverage' Line='naverage = 1'>
  <DD>Number of points within a sample interval to be subaveraged or submedianed to
  form fitting points.  Positive values are for averages and negative points
  for medians.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_niterate">niterate = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='niterate' Line='niterate = 0'>
  <DD>Number of sigma clipping rejection iterations.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_low_reject">low_reject = 3. , high_reject = 3.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='low_reject' Line='low_reject = 3. , high_reject = 3.'>
  <DD>Lower and upper sigma clipping rejection threshold in units of sigma determined
  from the RMS sigma of the data to the fit.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_grow">grow = 0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='grow' Line='grow = 0.'>
  <DD>Growing radius for rejected points (in pixels).  That is, any rejected point
  also rejects other points within this distance of the rejected point.
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
  parameters from <B>apresize</B>, parameters used for centering and
  editing the apertures from <B>apedit</B>, and tracing parameters from
  <B>aptrace</B>.
  </UL>
  <! EndSection:   'ADDITIONAL PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  It is sometimes the case that it is undesirable to simply divide
  two dimensional format spectra taken through fibers, aperture masks
  with small apertures such as holes and slitlets, or small slits in
  echelle formats by a flat field observation of a lamp.  This is due
  to the sharp dropoff of the flat field and object profiles and
  absence of signal outside of the profile.  Slight shifts or changes
  in profile shape introduce bad edge effects, unsightly "<TT>grass</TT>" is
  produced where there is no signal (which may also confuse extraction
  programs), and the division will also remove the characteristic
  profile of the object which might be needed for tracking the
  statistical significance, variance weighted extraction, and more.
  A straight flat field division also has the problem of changing the
  shape of the spectrum in wavelength, again compromising the
  poisson statistics and artificially boosting low signal regions.
  <P>
  There are three approaches to consider.  First, the
  flat field correction can be done after extraction to one dimension.
  This is valid provided the flat field and object profiles don't shift
  much.  However, for extractions that depend on a smooth profile,
  such as the variance weighting algorithms of this package, the sensitivity
  corrections must remain small; i.e. no large fringes or other
  small scale variations that greatly perturb the true photon profile.
  The second approach is to divide out the overall spectral shape of
  the flat field spectrum, fill regions outside of the signal with
  one and leave the profile shape intact.  This will still cause profile
  division problems described earlier but is mentioned here since it
  implemented in a related task called <B>apnormalize</B>.  The last
  approach is to model both the profile and overall spectrum shape and
  remove it from the flat field leaving only the sensitivity variations.
  This is what the task <B>apflatten</B> does.
  <P>
  The two dimensional flat field spectra within the defined apertures of
  the input images are fit by a model having the profile of the data and
  a smooth spectral shape.  This model is then divided into the flat
  field image within the aperture, replacing points of low signal, set
  with the <I>threshold</I> parameter, within the aperture and all points
  outside the aperture by one to produce an output sensitivity variation
  only flat field image.
  <P>
  A two dimensional normalized profile is computed by dividing the data
  within the aperture by the one dimensional spectrum and smoothing with
  low order function fits parallel to the dispersion axis if the aperture
  is well aligned with the axis or parallel to the traced aperture center
  if the trace is tilted relative to the dispersion axis.  The smooth
  profile is then used to improve the spectrum estimate using variance
  weighting and to eliminate deviant or cosmic ray pixels by sigma
  tests.  The profile algorithm is described in detail in
  <B>approfiles</B> and the variance weighted spectrum is described in
  <B>apvariance</B>.
  <P>
  The process of determining the profile and variance weighted spectrum,
  and hence the two dimensional spectrum model, is identical to that used
  for variance weighted extraction of the one dimensional spectra in the
  tasks <B>apall</B> or <B>apsum</B> and in making a two dimensional
  spectrum model in the task <B>apfit</B>.  Most of the parameters in
  this task are the same in those tasks and so further information about
  them may be found in their descriptions.  In fact, up to this point the
  task is the same as <B>apfit</B> and, if the flat field were normalized
  by this model it would produce the "<TT>ratio</TT>" output of that task.
  <P>
  This task deviates from <B>apfit</B> in that the final variance weighted
  one dimensional spectrum of the flat field is subjected to a smoothing
  operation.  This is done by fitting a function to the spectrum using
  the <B>icfit</B> routine.  This may be done interactively or
  noninteractively depending on the <B>interactive</B> parameter.  The
  default fitting parameters are part of this task.  The goal of the
  fitting is to follow the general spectral shape of the flat field light
  (usually a lamp) but not the small bumps and wiggles which are the one
  dimensional projection of sensitivity variations.  When the fitted
  function is multiplied into the normalize profile and then the two
  dimensional model divided into the data the sensitivity variations not
  part of the fitted spectrum are what is left in the final output flat
  field.
  <P>
  The remainder of this description covers the basic steps defining the
  apertures to be used.  These steps and parameter are much the same as
  in any of the other <B>apextract</B> tasks.
  <P>
  Aperture definitions may be inherited from those of other images by
  specifying a reference image with the <B>references</B> parameter.
  Images in the reference list are matched with those in the input list
  in order.  If the reference image list is shorter than the number of
  input images, the last reference image is used for all remaining input
  images.  Thus, a single reference image may be given for all the input
  images or different reference images may be given for each input
  image.  The special reference name "<TT>last</TT>" may be used to select the
  last set apertures used in any of the <B>apextract</B> tasks.
  <P>
  If an aperture reference image is not specified or no apertures are
  found for the specified reference image, previously defined apertures
  for the input image are sought in the aperture database.  Note that
  reference apertures supersede apertures for the input image.  If no
  apertures are defined they may be created automatically, the <I>find</I>
  option, or interactively in the aperture editor, if the
  <I>interactive</I> and <I>edit</I> options are set.
  <P>
  The functions performed by the task are selected by a set of flag
  parameters.  The functions are an automatic spectrum finding and
  aperture defining algorithm (see <B>apfind</B>) which is ignored if
  apertures are already defined, automatic recentering and resizing
  algorithms (see <B>aprecenter</B> and <B>apresize</B>), an interactive
  aperture editing function (see <B>apedit</B>), a spectrum position tracing
  and trace function fit (see <B>aptrace</B>), and the main function of
  this task, the flat field profile and spectral shape modeling and removal.
  <P>
  Each function selection will produce a query for each input spectrum if
  the <I>interactive</I> parameter is set.  The queries are answered by
  "<TT>yes</TT>", "<TT>no</TT>", "<TT>YES</TT>", or "<TT>NO</TT>", where the upper case responses suppress
  the query for following images.  There are other queries associated
  with tracing which first ask whether the operation is to be done
  interactively and, if yes, lead to queries for each aperture.  If the
  <I>interactive</I> parameter is not set then aperture editing
  interactive trace fitting, and interactive spectrum shape fitting are ignored.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_revisions">REVISIONS</A></H2>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_APFLATTEN">APFLATTEN V2.11</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='APFLATTEN' Line='APFLATTEN V2.11'>
  <DD>The "<TT>apertures</TT>" parameter can be used to select apertures for resizing,
  recentering, tracing, and extraction.  This parameter name was previously
  used for selecting apertures in the recentering algorithm.  The new
  parameter name for this is now "<TT>aprecenter</TT>".
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  To make a two dimensional flat field from a lamp observation:
  <P>
  <PRE>
  	cl&gt; apflatten fiber1 flat read=3 gain=1 back=fit
  	Yes find
  	No resize
  	No edit
  	Yes trace
  	Yes trace interactively
  	NO
  	Yes flatten
  	Yes fit interactively
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  apbackground, approfile, apvariance, apfit, icfit,
  apdefault, apfind, aprecenter, apresize, apedit, aptrace, apsum
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'ADDITIONAL PARAMETERS' 'DESCRIPTION' 'REVISIONS' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>