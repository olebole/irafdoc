.. _apnormalize:

apnormalize — Normalize 2D apertures by 1D functions
====================================================

**Package: kpnocoude**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  apnormalize -- Normalize 2D apertures by 1D functions
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  apnormalize input output
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of input images to be normalized.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>List of output image names for the normalized input images.  If no output
  name is given then the input name is used as a root with the extension
  "<TT>.norm</TT>" added.
  </DD>
  </DL>
  <DL>
  <DT><B>apertures = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='apertures' Line='apertures = ""'>
  <DD>Apertures to recenter, resize, trace, and normalize.  This only applies
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
  <DL>
  <DT><B>normalize = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='normalize' Line='normalize = yes'>
  <DD>Normalize the aperture spectra by a one dimensional function?
  </DD>
  </DL>
  <DL>
  <DT><B>fitspec = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fitspec' Line='fitspec = yes'>
  <DD>Fit normalization spectrum interactively?  The <I>interactive</I>
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
  A negative nsum selects a median rather than a sum except that
  tracing always uses a sum.
  </DD>
  </DL>
  <DL>
  <DT><B>cennorm = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cennorm' Line='cennorm = no'>
  <DD>Normalize to the aperture center rather than the mean?
  </DD>
  </DL>
  <DL>
  <DT><B>threshold = 10.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='threshold' Line='threshold = 10.'>
  <DD>All pixels in the normalization spectrum less than this value are replaced
  by this value.
  </DD>
  </DL>
  <P>
  The following parameters control the normalization spectrum extraction.
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
  <DT><B>weights = "<TT>none</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='weights' Line='weights = "none"'>
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
  <DD>The extraction is weighted by estimated variances of the pixels using
  a poisson noise model.
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
  <DT><B>lsigma = 3., usigma = 3.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lsigma' Line='lsigma = 3., usigma = 3.'>
  <DD>Lower and upper rejection thresholds, given as a number of times the
  estimated sigma of a pixel, for cleaning.
  </DD>
  </DL>
  <P>
  The following parameters are used to fit the normalization spectrum using
  the ICFIT routine.
  <DL>
  <DT><B>function = "<TT>legendre</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='function' Line='function = "legendre"'>
  <DD>Fitting function for the normalization spectra.  The choices are "<TT>legendre</TT>"
  polynomial, "<TT>chebyshev</TT>" polynomial, linear spline ("<TT>spline1</TT>"), and
  cubic spline ("<TT>spline3</TT>").
  </DD>
  </DL>
  <DL>
  <DT><B>order = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='order' Line='order = 1'>
  <DD>Number of polynomial terms or number of spline pieces for the fitting function.
  </DD>
  </DL>
  <DL>
  <DT><B>sample = "<TT>*</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sample' Line='sample = "*"'>
  <DD>Sample regions for fitting points.  Intervals are separated by "<TT>,</TT>" and an
  interval may be one point or a range separated by "<TT>:</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>naverage = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='naverage' Line='naverage = 1'>
  <DD>Number of points within a sample interval to be subaveraged or submedianed to
  form fitting points.  Positive values are for averages and negative points
  for medians.
  </DD>
  </DL>
  <DL>
  <DT><B>niterate = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='niterate' Line='niterate = 0'>
  <DD>Number of sigma clipping rejection iterations.
  </DD>
  </DL>
  <DL>
  <DT><B>low_reject = 3. , high_reject = 3.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='low_reject' Line='low_reject = 3. , high_reject = 3.'>
  <DD>Lower and upper sigma clipping rejection threshold in units of sigma determined
  from the RMS sigma of the data to the fit.
  </DD>
  </DL>
  <DL>
  <DT><B>grow = 0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='grow' Line='grow = 0.'>
  <DD>Growing radius for rejected points (in pixels).  That is, any rejected point
  also rejects other points within this distance of the rejected point.
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
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  For each image in the input image list the two dimensional spectra
  defined by a set of apertures are normalized by a one dimensional
  normalization function derived by extracting and smoothing the spectrum
  by fitting a function with the <B>icfit</B> procedure.  The value of the
  fitting function at each point along the dispersion, divided by the
  aperture width to form a mean or scaled to the same mean as the center
  pixel of the aperture depending on the <I>cennorm</I> parameter, is
  divided into the two dimensional input aperture.  All points outside
  the apertures are set to unity.
  <P>
  The purpose of this task is to remove a general shape from the aperture
  spectra.  If low order (order = 1 for instance) functions are used then
  only the amplitudes of the spectra are affected, shifting each aperture
  to approximately unit intensity per pixel.  If high order functions are
  used only the small spatial scale variations are preserved.  This
  is useful for making flat field images with the spectral signature of the
  continuum source removed or for producing two dimensional normalized
  spectra similar to the task <B>onedspec.continuum</B>.  For flat fields
  this algorithm retains the profile shape which may be useful for
  removing the profile response in short slit data.  However, often
  one does not want the profile of the flat fielded observation to be
  modified in which case the task <B>apflatten</B> should be used.
  <P>
  The normalization spectrum is first extracted in the same way as is
  the one dimensional extraction in <B>apsum</B> or <B>apall</B>.  In
  particular the same parameters for selecting weighting and cleaning
  are available.  After extraction the spectrum is fit using the
  <B>icfit</B> routine.  This may be done interactively or noninteractively
  depending on the <I>interactive</I> parameter.  The default fitting
  parameters are part of this task.  The goal of the fitting depends
  on the application.  One may be trying to simply continuum normalize,
  in which case one wants to iteratively reject and grow the rejected
  points to exclude the lines and fit the continuum with a
  moderate order function (see <B>continuum</B> for more discussion).  
  If one wants to simply normalize all spectra to a common flux, say to
  remove a blaze function in echelle data, then an order of 1 will
  normalize by a constant.  For flat field and profile correction of
  small slits one wants to fit the large scale shape of the
  spectrum but not fit the small bumps and wiggles due to sensitivity
  variations and fringing.
  <P>
  The smoothed extracted spectrum represents the total flux within the
  aperture.  There are two choices for scaling to a normalization per
  pixel.  One is to divide by the aperture width, thus computing an average
  flux normalization.  In this case the peak of the spectrum will be
  greater than unity.  This is done when <I>cennorm</I> = no.  When this
  parameter has the value yes then the mean of the normalization spectrum
  is scaled to the mean of the aperture center, computed by linearly
  interpolating the two pixels about the traced center.  This will give
  values near one for the pixels at the center of the aperture in the
  final output image.
  <P>
  Before division of each pixel by the appropriate dispersion point in
  the normalization spectrum, all pixels below the value specified by the
  <I>threshold</I> parameter in the normalization spectrum are replaced by
  the threshold value.  This suppresses division by very small numbers.
  Finally, the pixels within the aperture are divided by the normalization
  function and the pixels outside the apertures are set to 1.
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
  this task, the one dimensional normalization of the aperture
  profiles.
  <P>
  Each function selection will produce a query for each input spectrum if
  the <I>interactive</I> parameter is set.  The queries are answered by
  "<TT>yes</TT>", "<TT>no</TT>", "<TT>YES</TT>", or "<TT>NO</TT>", where the upper case responses suppress
  the query for following images.  There are other queries associated
  with tracing which first ask whether the operation is to be done
  interactively and, if yes, lead to queries for each aperture.  If the
  <I>interactive</I> parameter is not set then aperture editing,
  interactive trace fitting, and interactive spectrum shape fitting are ignored.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  To make a flat field image which leaves the total counts of the object
  images approximately unchanged from a quartz echelle or slitlet image:
  <P>
  <PRE>
  	cl&gt; apnormalize qtz001,qtz002 flat001,flat002
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
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>APNORMALIZE V2.11</B></DT>
  <! Sec='REVISIONS' Level=0 Label='APNORMALIZE' Line='APNORMALIZE V2.11'>
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
  apbackground, approfile, apvariance, apfit, icfit,
  apdefault, apfind, aprecenter, apresize, apedit, aptrace, apsum
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'ADDITIONAL PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
