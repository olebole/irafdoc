.. _apsum:

apsum — Extract 1D spectra
==========================

**Package: specred**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  apsum -- Extract one dimensional sums across the apertures
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  apsum input
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of input images containing apertures to be extracted.
  </DD>
  </DL>
  <DL>
  <DT><B>output = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output = ""'>
  <DD>List of output rootnames for the extracted spectra.  If the null
  string is given or the end of the output list is reached before the end
  of the input list then the input image name is used as the output rootname.
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
  <DT><B>recenter = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='recenter' Line='recenter = no'>
  <DD>Recenter the apertures?
  </DD>
  </DL>
  <DL>
  <DT><B>resize = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='resize' Line='resize = no'>
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
  <DT><B>extras = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='extras' Line='extras = no'>
  <DD>Extract the raw spectrum (if variance weighting is used), the sky spectrum
  (if background subtraction is used), and variance spectrum (if variance
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
  and editing operations.  For tracing this is the starting line and
  the same number of lines are summed at each tracing point.  A line of
  INDEF selects the middle of the image along the dispersion axis.
  A positive nsum takes a sum while a negative value selects a median
  except that tracing always uses a sum.
  </DD>
  </DL>
  <P>
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
  I/O parameters and the default dispersion axis are taken from the
  package parameters, the default aperture parameters from
  <B>apdefault</B>, automatic aperture finding parameters from
  <B>apfind</B>, recentering parameters from <B>aprecenter</B>, resizing
  parameters from <B>apresize</B>, parameters used for centering and
  editing the apertures from <B>apedit</B>, and tracing parameters from
  <B>aptrace</B>.
  <P>
  When this operation is performed from the task <B>apall</B> all
  parameters except the package parameters are included in that task.
  </UL>
  <! EndSection:   'ADDITIONAL PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  For each image in the input image list, the two dimensional spectra are
  extracted to one dimensional spectra by summing the pixels across the
  dispersion axis at each wavelength along the dispersion axis within a
  set of defined apertures.  The extraction apertures consist of an
  aperture number, a beam number, a title, a center, limits relative to
  the center, a curve describing shifts of the aperture center across the
  dispersion axis as a function of the wavelength, and parameters for
  background fitting and subtraction.  See <B>apextract</B> for a more
  detailed discussion of the aperture structures.
  <P>
  The extracted spectra are recorded in one, two, or three dimensional
  images depending on the <I>format</I> and <I>extras</I> parameters.  The
  output image rootnames are specified by the <I>output</I> list. If the
  list is empty or shorter than the input list the missing names are
  taken to be the same as the input image names.  Because the rootnames
  have extensions added it is common to default to the input names in
  order to preserve a naming relation between the input two dimensional
  spectra and the extracted spectra.
  <P>
  When the parameter <I>extras</I>=no only the extracted spectra are
  output.  If the format parameter <I>format</I>="<TT>onedspec</TT>" the output
  aperture extractions are one dimensional images with names formed from
  the output rootname and a numeric extension given by the aperture
  number; i.e. root.0001 for aperture 1.  Note that there will be as many
  output images as there are apertures for each input image, all with the
  same output rootname but with different aperture extensions.  The
  aperture beam number associated with each aperture is recorded in the
  output image under the keyword BEAM-NUM.  The output image name format
  and the BEAM-NUM entry in the image are chosen to be compatible with
  the <B>onedspec</B> package.
  <P>
  If the format parameter is "<TT>echelle</TT>" or "<TT>multispec</TT>" the output aperture
  extractions are put into a two dimensional image with a name formed from
  the output rootname and the extension "<TT>.ech</TT>" or "<TT>.ms</TT>".  Each line in
  the output image corresponds to one aperture.  Thus in this format
  there is one output image for each input image.  These are the preferred
  output formats for reasons of compactness and ease of handling.  These
  formats are compatible with the <B>onedspec</B>, <B>echelle</B>, and
  <B>msred</B> packages.  The relation between the line and the aperture
  numbers is given by the header parameter APNUMn where n is the line and
  the value is the aperture number and other numeric information.
  <P>
  If the <I>extras</I> parameter is set to yes then the above formats
  become three dimensional.  Each plane in the third dimension contains
  associated information for the spectra in the first plane.  If variance
  weighted extractions are done the unweighted spectra are recorded.  If
  background subtraction is done the background spectra are recorded.  If
  variance weighted extractions are done the sigma spectrum (the
  estimated sigma of each spectrum pixel based on the individual
  variances of the pixels summed) is recorded.  The order of the
  additional information is as given above.  For example, an unweighted
  extraction with background subtraction will have one additional plane
  containing the sky spectra while a variance weighted extraction with
  background subtractions will have the variance weighted spectra, the
  unweighted spectra, the background spectra, and the sigma spectra in
  consecutive planes.
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
  this task, one dimensional spectrum extraction.
  <P>
  Each function selection will produce a query for each input spectrum if
  the <I>interactive</I> parameter is set.  The queries are answered by
  "<TT>yes</TT>", "<TT>no</TT>", "<TT>YES</TT>", or "<TT>NO</TT>", where the upper case responses suppress
  the query for following images.  There are other queries associated
  with tracing and extracted spectrum review which first ask whether the
  operation is to be done interactively and, if yes, lead to queries for
  each aperture.  The cursor keys available during spectrum review are
  minimal, only the CURSOR MODE keys for expanding and adjusting the
  graph are available and the quit key <TT>'q'</TT>.  If the <I>interactive</I>
  parameter is not set then aperture editing, interactive trace fitting,
  and spectrum review are ignored.
  <P>
  Background sky subtraction is done during the extraction based on
  background regions and parameters defined by the default parameters or
  changed during the interactive setting of the apertures.  The background
  subtraction options are to do no background subtraction, subtract the
  average, median, or minimum of the pixels in the background regions, or to
  fit a function and subtract the function from under the extracted object
  pixels.  The background regions are specified in pixels from
  the aperture center and follow changes in center of the spectrum along the
  dispersion.  The syntax is colon separated ranges with multiple ranges
  separated by a comma or space.  The background fitting uses the <B>icfit</B>
  routines which include medians, iterative rejection of deviant points, and
  a choice of function types and orders.  Note that it is important to use a
  method which rejects cosmic rays such as using either medians over all the
  background regions (<I>background</I> = "<TT>median</TT>") or median samples during
  fitting (<I>b_naverage</I> &lt; -1).  The background subtraction algorithm and
  options are described in greater detail in <B>apsum</B> and
  <B>apbackground</B>.
  <P>
  Since the background noise is often the limiting factor for good
  extraction one may box car smooth the sky to improve the statistics in
  smooth background regions at the expense of distorting the subtraction
  near spectra features.  This is most appropriate when the sky region is
  limited due to small slit length.  The smoothing length is specified by
  the parameter <I>skybox</I>.
  <P>
  For a more extended discussion about the background determination see
  <B>apbackground</B>.
  <P>
  The aperture extractions consists of summing all the background
  subtracted pixel values at a given wavelength within the aperture
  limits.  The aperture limits form a fixed width aperture but the center
  varies smoothly to follow changes in the position of the spectrum
  across the dispersion axis.  At the ends of the aperture partial pixels
  are used.
  <P>
  The pixels in the sum may be weighted as specified by the <I>weights</I>
  parameter.  If the weights parameter is "<TT>none</TT>" and the <I>clean</I>
  parameter is no then the simple sum of the pixels (with fractional
  endpoints) is extracted.  If the weights parameter is "<TT>variance</TT>" or if
  the <B>clean</B> parameter is yes the pixels are weighted by their
  estimated variance derived from a noise model based on the <I>gain</I>
  and <I>readnoise</I> parameters and a smooth profile function.  Normally
  the profile function is determined from the data being extracted.
  However, one may substitute a "<TT>profile</TT>" image as specified by the
  <I>profiles</I> parameter for computing the profile.  This requires that
  the profile image have spectra of identical position and profile as
  the image being extracted.  For example, this would likely be the case
  with fiber spectra and an off-telescope spectrograph and a strong flat
  field or object spectrum could be used for weak spectra.  Note that
  experience has shown that even for very weak spectra there is little
  improvement with using a separate profile image but the user is free
  to experiment.
  <P>
  When the <I>clean</I> parameter is set pixels deviating by more than a
  specified number of sigma from the profile function are excluded from the
  variance weighted sum.  Note that the <I>clean</I> parameter always selects
  variance weights.  For a more complete discussion of the extraction sums,
  variance weighting, cleaning, the noise model, and profile function
  determination see <B>apvariance</B> and <B>approfiles</B>.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  To simply extract the spectra from a multislit observation:
  <P>
  	cl&gt; apsum multislit1
  <P>
  The positions of the slits are defined using either automatic finding
  or with the aperture editor.  The positions of the slits are traced if
  necessary and then the apertures are extracted to the image
  "<TT>multslit1.ms</TT>".  The steps of defining the slit positions and tracing
  can be done as part of this command or previously using the other tasks
  in the <B>apextract</B> package.
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>APSUM V2.11</B></DT>
  <! Sec='REVISIONS' Level=0 Label='APSUM' Line='APSUM V2.11'>
  <DD>The "<TT>apertures</TT>" parameter can be used to select apertures for resizing,
  recentering, tracing, and extraction.  This parameter name was previously
  used for selecting apertures in the recentering algorithm.  The new
  parameter name for this is now "<TT>aprecenter</TT>".
  <P>
  The "<TT>nsubaps</TT>" parameter now allows onedspec and echelle output formats.
  The echelle format is appropriate for treating each subaperture as
  a full echelle extraction.
  <P>
  The dispersion axis parameter was moved to purely a package parameter.
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
  apbackground, apvariance, approfile,
  apdefault, apfind, aprecenter, apresize, apedit, aptrace, apall
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'ADDITIONAL PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
