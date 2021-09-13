.. _apscatter:

apscatter — Fit and remove scattered light
==========================================

**Package: argus**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  apscatter -- Fit and subtract scattered light
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  apscatter input output
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of input images in which to determine and subtract scattered light.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>List of output scattered light subtracted images.  If no output images
  are specified or the end of the output list is reached before the end 
  of the input list then the output image will overwrite the input image.
  </DD>
  </DL>
  <DL>
  <DT><B>apertures = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='apertures' Line='apertures = ""'>
  <DD>Apertures to recenter, resize, trace, and extract.  All apertures are
  used to define the scattered light region.  This only applies
  to apertures read from the input or reference database.  Any new
  apertures defined with the automatic finding algorithm or interactively
  are always selected.  The syntax is a list comma separated ranges
  where a range can be a single aperture number, a hyphen separated
  range of aperture numbers, or a range with a step specified by "<TT>x&lt;step&gt;</TT>";
  for example, "<TT>1,3-5,9-12x2</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>scatter = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='scatter' Line='scatter = ""'>
  <DD>List of scattered light images.  This is the scattered light subtracted
  from the input image.  If no list is given or the end of the list is
  reached before the end of the input list then no scattered light image
  is created.
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
  all user queries are suppressed and interactive aperture editing, trace
  fitting, and interactive scattered light fitting are disabled.
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
  <DT><B>subtract = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='subtract' Line='subtract = yes'>
  <DD>Subtract the scattered light from the input images?
  </DD>
  </DL>
  <DL>
  <DT><B>smooth = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='smooth' Line='smooth = yes'>
  <DD>Smooth the cross-dispersion fits along the dispersion?
  </DD>
  </DL>
  <DL>
  <DT><B>fitscatter = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fitscatter' Line='fitscatter = yes'>
  <DD>Fit the scattered light across the dispersion interactively?
  The <I>interactive</I> parameter must also be yes.
  </DD>
  </DL>
  <DL>
  <DT><B>fitsmooth = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fitsmooth' Line='fitsmooth = yes'>
  <DD>Smooth the cross-dispersion fits along the dispersion?
  The <I>interactive</I> parameter must also be yes.
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
  the same number of lines are summed at each tracing point.  This is
  also the initial line for interactive fitting of the scattered light.
  A line of INDEF selects the middle of the image along the dispersion
  axis.  A positive nsum takes a sum and a negative value selects a
  median except that tracing always uses a sum.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B>buffer = 1.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='buffer' Line='buffer = 1.'>
  <DD>Buffer distance from the aperture edges to be excluded in selecting the
  scattered light pixels to be used.
  </DD>
  </DL>
  <DL>
  <DT><B>apscat1 = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='apscat1' Line='apscat1 = ""'>
  <DD>Fitting parameters across the dispersion.  This references an additional
  set of parameters for the ICFIT package.  The default is the "<TT>apscat1</TT>"
  parameter set.  See below for additional information.
  </DD>
  </DL>
  <DL>
  <DT><B>apscat2 = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='apscat2' Line='apscat2 = ""'>
  <DD>Fitting parameters along the dispersion.  This references an additional
  set of parameters for the ICFIT package.  The default is the "<TT>apscat2</TT>"
  parameter set.  See below for additional information.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Icfit parameters for fitting the scattered light</H3>
  <! BeginSection: 'ICFIT PARAMETERS FOR FITTING THE SCATTERED LIGHT'>
  <UL>
  There are two additional parameter sets which define the parameters used
  for fitting the scattered light across the dispersion and along the
  dispersion.  The default parameter sets are <B>apscat1</B> and <B>apscat2</B>.
  The parameters may be examined and edited by either typing their names
  or by typing "<TT>:e</TT>" when editing the main parameter set with <B>eparam</B>
  and with the cursor pointing at the appropriate parameter set name.
  These parameters are used by the ICFIT package and a further
  description may be found there.
  <P>
  <DL>
  <DT><B>function = "<TT>spline3</TT>" (apscat1 and apscat2)</B></DT>
  <! Sec='ICFIT PARAMETERS FOR FITTING THE SCATTERED LIGHT' Level=0 Label='function' Line='function = "spline3" (apscat1 and apscat2)'>
  <DD>Fitting function for the scattered light across and along the dispersion.
  The choices are "<TT>legendre</TT>" polynomial, "<TT>chebyshev</TT>" polynomial,
  linear spline ("<TT>spline1</TT>"), and cubic spline ("<TT>spline3</TT>").
  </DD>
  </DL>
  <DL>
  <DT><B>order = 1 (apscat1 and apscat2)</B></DT>
  <! Sec='ICFIT PARAMETERS FOR FITTING THE SCATTERED LIGHT' Level=0 Label='order' Line='order = 1 (apscat1 and apscat2)'>
  <DD>Number of polynomial terms or number of spline pieces for the fitting function.
  </DD>
  </DL>
  <DL>
  <DT><B>sample = "<TT>*</TT>" (apscat1 and apscat2)</B></DT>
  <! Sec='ICFIT PARAMETERS FOR FITTING THE SCATTERED LIGHT' Level=0 Label='sample' Line='sample = "*" (apscat1 and apscat2)'>
  <DD>Sample regions for fitting points.  Intervals are separated by "<TT>,</TT>" and an
  interval may be one point or a range separated by "<TT>:</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>naverage = 1 (apscat1 and apscat2)</B></DT>
  <! Sec='ICFIT PARAMETERS FOR FITTING THE SCATTERED LIGHT' Level=0 Label='naverage' Line='naverage = 1 (apscat1 and apscat2)'>
  <DD>Number of points within a sample interval to be subaveraged or submedianed to
  form fitting points.  Positive values are for averages and negative points
  for medians.
  </DD>
  </DL>
  <DL>
  <DT><B>niterate = 5 (apscat1), niterate = 0 (apscat2)</B></DT>
  <! Sec='ICFIT PARAMETERS FOR FITTING THE SCATTERED LIGHT' Level=0 Label='niterate' Line='niterate = 5 (apscat1), niterate = 0 (apscat2)'>
  <DD>Number of sigma clipping rejection iterations.
  </DD>
  </DL>
  <DL>
  <DT><B>low_reject = 5. (apscat1) , low_reject = 3. (apscat2)</B></DT>
  <! Sec='ICFIT PARAMETERS FOR FITTING THE SCATTERED LIGHT' Level=0 Label='low_reject' Line='low_reject = 5. (apscat1) , low_reject = 3. (apscat2)'>
  <DD>Lower sigma clipping rejection threshold in units of sigma determined
  from the RMS sigma of the data to the fit.
  </DD>
  </DL>
  <DL>
  <DT><B>high_reject = 2. (apscat1) , high_reject = 3. (apscat2)</B></DT>
  <! Sec='ICFIT PARAMETERS FOR FITTING THE SCATTERED LIGHT' Level=0 Label='high_reject' Line='high_reject = 2. (apscat1) , high_reject = 3. (apscat2)'>
  <DD>High sigma clipping rejection threshold in units of sigma determined
  from the RMS sigma of the data to the fit.
  </DD>
  </DL>
  <DL>
  <DT><B>grow = 0. (apscat1 and apscat2)</B></DT>
  <! Sec='ICFIT PARAMETERS FOR FITTING THE SCATTERED LIGHT' Level=0 Label='grow' Line='grow = 0. (apscat1 and apscat2)'>
  <DD>Growing radius for rejected points (in pixels).  That is, any rejected point
  also rejects other points within this distance of the rejected point.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'ICFIT PARAMETERS FOR FITTING THE SCATTERED LIGHT'>
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
  The scattered light outside the apertures defining the two dimensional
  spectra is extracted, smoothed, and subtracted from each input image.  The
  approach is to first select the pixels outside the defined apertures
  and outside a buffer distance from the edge of any aperture at each
  point along the dispersion independently.  A one dimensional function
  is fit using the <B>icfit</B> package.  This fitting uses an iterative
  algorithm to further reject high values and thus fit the minima between
  the spectra.  (This even works reasonably well if no apertures are
  defined).  Because each fit is done independently the scattered light
  thus determined will not be smooth along the dispersion.  If desired
  each line along the dispersion in the scattered light surface may then
  be smoothed by again fitting a one dimensional function using the
  <B>icfit</B> package.  The final scattered light surface is then
  subtracted from the input image to form the output image.  The
  scattered light surface may be output if desired.
  <P>
  The reason for using two one dimensional fits as opposed to a surface fit
  is that the actual shape of the scattered light is often not easily modeled
  by a simple two dimensional function.  Also the one dimensional function
  fitting offers more flexibility in defining functions and options as
  provided by the <B>icfit</B> package.
  <P>
  The organization of the task is like the other tasks in the package
  which has options for defining apertures using a reference image,
  defining apertures through an automatic finding algorithm (see
  <B>apfind</B>), automatically recentering or resizing the apertures (see
  <B>aprecenter</B> and <B>apresize</B>), interactively editing the
  apertures (see <B>apedit</B>), and tracing the positions of the spectra
  as a function of dispersion position (see <B>aptrace</B>).  Though
  unlikely, the actual scattered light subtraction operation may be
  suppressed when the parameter <I>subtract</I> is no.  If the scattered
  light determination and fitting is done interactively (the
  <I>interactive</I> parameter set to yes) then the user is queried
  whether or not to do the fitting and subtraction for each image.  The
  responses are "<TT>yes</TT>", "<TT>no</TT>", "<TT>YES</TT>", or "<TT>NO</TT>", where the upper case
  queries suppress this query for the following images.  When the task is
  interactive there are further queries for each step of the operation
  which may also be answered both individually or collectively for all
  other input images using the four responses.
  <P>
  When the scattered light operation is done interactively the user may
  set the fitting parameters for the scattered light functions both
  across and along the dispersion interactively.  Initially the central
  line or column is used but after exiting (with <TT>'q'</TT>) a prompt is given
  for selecting additional lines or columns and for changing the buffer
  distance.  Note that the point of the interactive stage is to set the
  fitting parameters.  When the entire image is finally fit the last set
  of fitting parameters are used for all lines or columns.
  <P>
  The default fitting parameters are organized as separate parameter sets
  called <B>apscat1</B> for the first fits across the dispersion and
  <B>apscat2</B> for the second smoothing fits along the dispersion.
  Changes to these parameters made interactively during execution of
  this task are updated in the parameter sets.  The general idea for
  these parameters is that when fitting the pixels from between the
  apertures the iteration and rejection thresholds are set to eliminate
  high values while for smoothing along the dispersion a simple smooth
  function is all that is required.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  To subtract the scattered light from a set of images to form a
  new set of images:
  <P>
  	cl&gt; apscatter raw* %raw%new%*
  <P>
  This example uses a substitution in the names from raw to new.
  By default this would be done interactively
  <P>
  2.  To subtract the scattered light in place and save the scattered light
  images:
  <P>
  	cl&gt; apscatter im* "<TT></TT>" scatter="s//im*"<TT> ref=im1 interact-
  <P>
  The prefix s is added to the original names for the scattered light.
  This operation is done noninteractively using a reference spectrum
  to define the apertures.
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>APSCATTER V2.11</B></DT>
  <! Sec='REVISIONS' Level=0 Label='APSCATTER' Line='APSCATTER V2.11'>
  <DD>The </TT>"apertures"<TT> parameter can be used to select apertures for resizing,
  recentering, tracing, and extraction.  This parameter name was previously
  used for selecting apertures in the recentering algorithm.  The new
  parameter name for this is now </TT>"aprecenter"<TT>.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  apfind, aprecenter, apresize,  apedit, aptrace, apsum, apmask, icfit
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'ICFIT PARAMETERS FOR FITTING THE SCATTERED LIGHT' 'ADDITIONAL PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
