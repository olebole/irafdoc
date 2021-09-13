.. _apfit:

apfit — Fit 2D spectra and output the fit, difference, or ratio
===============================================================

**Package: apextract**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  apfit -- Fit 2D spectra using APEXTRACT profile algorithms
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  apfit input output fittype
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of input images to be fit.
  </DD>
  </DL>
  <DL>
  <DT><B>output = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output = ""'>
  <DD>List of output images to be created with the  fitting results.  If the null
  string is given or the end of the output list is reached before the end
  of the input list then the input image name is used and an extension
  of "<TT>.fit</TT>", "<TT>.diff</TT>", or "<TT>.ratio</TT>" is added based on the type of fit.
  </DD>
  </DL>
  <DL>
  <DT><B>apertures = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='apertures' Line='apertures = ""'>
  <DD>Apertures to recenter, resize, trace, and fit.  This only applies
  to apertures read from the input or reference database.  Any new
  apertures defined with the automatic finding algorithm or interactively
  are always selected.  The syntax is a list comma separated ranges
  where a range can be a single aperture number, a hyphen separated
  range of aperture numbers, or a range with a step specified by "<TT>x&lt;step&gt;</TT>";
  for example, "<TT>1,3-5,9-12x2</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>fittype = "<TT>difference</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fittype' Line='fittype = "difference"'>
  <DD>Type of fitted output.  The choices are:
  <DL>
  <DT><B>"<TT>fit</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"fit"'>
  <DD>The fitted spectra are output.
  </DD>
  </DL>
  <DL>
  <DT><B>"<TT>difference</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"difference"'>
  <DD>The difference (or residuals) of the data and the fit (data - fit).
  </DD>
  </DL>
  <DL>
  <DT><B>"<TT>ratio</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"ratio"'>
  <DD>The ratio of the data to the fit.  If a fitted pixel goes below a specified
  threshold the ratio is set to 1.
  </DD>
  </DL>
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
  <DT><B>fit = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fit' Line='fit = yes'>
  <DD>Fit the spectra and produce a fitted output image?
  </DD>
  </DL>
  <P>
  The following two parameters are used in the finding, recentering, resizing,
  editing, and tracing operations.
  <DL>
  <DT><B>line = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='line' Line='line = INDEF'>
  <DD>The starting dispersion line (line or column perpendicular to the dispersion
  axis) for the tracing.  A value of INDEF starts at the middle of the image.
  </DD>
  </DL>
  <DL>
  <DT><B>nsum = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nsum' Line='nsum = 1'>
  <DD>Number of dispersion lines to be summed or medianed at each step along
  the dispersion.  For tracing only summing is done and the sign is
  ignored.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B>threshold = 10.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='threshold' Line='threshold = 10.'>
  <DD>Division threshold for ratio fit type.  If a pixel in the fitted spectrum
  is less than this value then a ratio of 1 is output.
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
  The two dimensional spectra within the defined apertures of the input
  images are fit by a model and new output images are created with either
  the model spectra, the difference between the input and model spectra,
  or the ratio of input and model spectra.  The type of output is
  selected by the parameter <I>fittype</I> which may have one of the
  values "<TT>fit</TT>", "<TT>difference</TT>", or "<TT>ratio</TT>".
  <P>
  Aperture definitions may be inherited from those of other images by
  specifying a reference image with the <B>references</B> parameter.
  Images in the reference list are matched with those in the
  input list in order.  If the reference image list is shorter than the
  number of input images, the last reference image is used for all
  remaining input images.  Thus, a single reference image may be given
  for all the input images or different reference images may be given for
  each input image.  The special reference name "<TT>last</TT>" may be used to
  select the last set apertures used in any of the <B>apextract</B> tasks.
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
  this task, two dimensional model fitting.
  <P>
  Each function selection will produce a query for each input spectrum if
  the <I>interactive</I> parameter is set.  The queries are answered by
  "<TT>yes</TT>", "<TT>no</TT>", "<TT>YES</TT>", or "<TT>NO</TT>", where the upper case responses suppress
  the query for following images.  There are other queries associated
  with tracing which first ask whether the operation is to be done
  interactively and, if yes, lead to queries for each aperture.  If the
  <I>interactive</I> parameter is not set then aperture editing and
  interactive trace fitting are ignored.
  <P>
  The two dimensional spectrum model consists of a smooth two dimensional
  normalized profile multiplied by the variance weighted one dimensional
  spectrum.  The profile is computed by dividing the data within the aperture
  by the one dimensional spectrum, smoothing with either low order function
  fits parallel to the dispersion axis or a special two dimensional function
  as selected by the <I>pfit</I> parameter.  The smooth profile is then used
  to improve the spectrum estimate using variance weighting and to eliminate
  deviant or cosmic ray pixels by sigma tests.  The profile algorithm is
  described in detail in <B>approfiles</B> and the variance weighted spectrum
  is described in <B>apvariance</B>.
  <P>
  The process of determining the profile and variance weighted spectrum,
  and hence the two dimensional spectrum model, is identical to that used
  for variance weighted extraction of the one dimensional spectra in the
  tasks <B>apall</B> or <B>apsum</B>.  Most of the parameters of in this
  task are the same as those in the extraction tasks and so further
  information about them may be found in the descriptions of those tasks.
  <P>
  Because of the connection with variance weighted extraction and cleaning
  of one dimensional spectra, this task is useful as a diagnostic tool for
  understanding and evaluating the variance weighting algorithm.
  For example the "<TT>difference</TT>" image provides the residuals in a
  two dimensional visual form.
  <P>
  The "<TT>fit</TT>" output image does not include any background determination;
  i.e the fit is background subtracted.  Pixels outside the modeled
  spectra are set to zero.
  <P>
  The "<TT>difference</TT>" output image is simply the difference between the
  background subtracted "<TT>fit</TT>" and the data.  Thus the difference within
  the apertures should approximate the background and outside the
  apertures the difference will be identical with the input image.
  <P>
  The "<TT>ratio</TT>" output image does include any background in the model
  before taking the ratio of the data and model.  If a model pixel
  is less than the given <I>threshold</I> parameter the output ratio
  is set to one.  This is used to avoid division by zero and set a
  limit to noise in ratio image.  Outside of the apertures the ratio
  output pixels are set to one.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  To compute the residuals of a model fit where the image already has
  aperture defined:
  <P>
  	cl&gt; apfit ls1 inter- rec- res- trace- read=3 gain=1 back=fit
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>APFIND V2.11</B></DT>
  <! Sec='REVISIONS' Level=0 Label='APFIND' Line='APFIND V2.11'>
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
  apbackground, approfile, apvariance,
  apdefault, apfind, aprecenter, apresize, apedit, aptrace, apsum, apall
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'ADDITIONAL PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
