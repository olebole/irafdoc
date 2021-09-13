.. _apresize:

apresize — Resize apertures
===========================

**Package: kpnoslit**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  apresize -- Resize apertures automatically
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  apresize input
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of input images in which apertures are to be resized.
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
  <DT><B>interactive = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = no'>
  <DD>Run this task interactively?  If the task is not run interactively then
  all user queries are suppressed and interactive aperture editing is
  disabled.
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
  <P>
  <DL>
  <DT><B>line = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='line' Line='line = INDEF'>
  <DD>The dispersion line (line or column perpendicular to the dispersion axis) to
  be used in resizing the spectra.  A value of INDEF selects the middle of the
  image.
  </DD>
  </DL>
  <DL>
  <DT><B>nsum = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nsum' Line='nsum = 1'>
  <DD>Number of dispersion lines to be summed or medianed.  The lines are taken
  around the specified dispersion line.  A positive value takes a
  sum and a negative value selects a median.
  </DD>
  </DL>
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
  The background is a slope connecting the first minima
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
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Additional parameters</H3>
  <! BeginSection: 'ADDITIONAL PARAMETERS'>
  <UL>
  I/O parameters and the default dispersion axis are taken from the
  package parameters, the default aperture parameters are taken from the
  task <B>apdefault</B>, automatic aperture finding parameters are taken
  from <B>apfind</B>, and parameters used for centering and editing the
  apertures are taken from <B>apedit</B>.
  <P>
  When this operation is performed from the task <B>apall</B> all parameters
  except the package parameters are included in that task.
  </UL>
  <! EndSection:   'ADDITIONAL PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  For each image in the input image list, the aperture limits are
  redefined to be either specified values or by finding the points at
  which the spectrum profile, linearly interpolated, first crosses a
  specified value moving away from the aperture center at the specified
  dispersion line.  In the latter case the limits may then be increased
  or decreased by a specified percentage, a maximum lower and upper limit,
  may be imposed, and the independent limits may be averaged and the
  single values applied to all the apertures.
  <P>
  The simplest resizing choice is to reset all the aperture limits to
  the values specified by <I>llimit</I> and <I>ulimit</I>.  This option
  is selected if the parameter <I>ylevel</I> is INDEF.
  <P>
  There are several options for specifying a data level at which an
  aperture is sized.  The most common method (the default) is to specify
  a fraction of the peak value since this is data independent and physically
  reasonable.  This is done by setting the fraction with the parameter
  <I>ylevel</I> and the parameter <I>peak</I> to yes.  If the peak parameter
  is no then the level is a data value.
  <P>
  The levels may be relative to zero, as might be used with fibers or
  high dispersion / high signal-to-noise data, or relative to a local
  linear background, as would be appropriate for slit data having a
  significant background.  A background is found and used if the
  parameter <I>bkg</I> is set.  The background determination is very
  simple.  Starting at the peak two background points are found, one in
  each direction, which are inflection points; i.e. the first pixels
  which are less than their two neighbors.  A linear slope is fit and
  subtracted for the purposes of measuring the peak and setting the
  aperture limits.  Note that if the slope is significant the actual
  limits may not correspond to the intercepts of a line at constant data
  value.
  <P>
  Once aperture limits, a distance relative to the center, are determined
  they are increased or decreased by a percentage, expressed as a fraction,
  given by the parameter <I>r_grow</I>.  To illustrate the operation,
  if xlow is the initial lower limit then the final lower limit will be:
  <P>
  	xlow final = xlow * (1 + r_grow)
  <P>
  A value of zero leaves the aperture limits unchanged.
  <P>
  After the aperture limits are found, based on the above steps, a fixed lower
  limit, given by the parameter <I>llimit</I>, is applied to the lower
  aperture points and, similarly, a fixed upper limit is applied to the
  upper aperture points.  This feature protects against absurdly wide apertures.
  <P>
  Finally, if the parameter <I>avglimits</I> is set the individual aperture
  limits are averaged to form an average aperture.  This average aperture
  is then assigned to all apertures.  This option allows keeping common
  aperture sizes but allowing variation due to seeing changes.
  <P>
  The resizing algorithm is available in the interactive aperture editor.
  Here one may select individual apertures or all apertures using the
  <TT>'a'</TT> switch.  The resizing algorithm described above is selected using
  the <TT>'z'</TT> key.  An simple alternative is the <TT>'y'</TT> key which resizes
  apertures to the y level marked by the cursor.
  <P>
  If the task is interactive the user is queried whether to perform
  various steps on each image.  The queries may be answered with one of
  the four values "<TT>yes</TT>", "<TT>no</TT>", "<TT>YES</TT>" and "<TT>NO</TT>", where an upper case
  response suppresses all further queries to this question.
  <P>
  The aperture resizing algorithm may be selected from nearly every task
  in the package with the <I>resize</I> parameter.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  To resize all apertures to the range -4 to 4:
  <P>
  	cl&gt; apresize image llimit=-4 ulimit=4 ylevel=INDEF
  <P>
  2.  To resize all aperture to a point which is 5% of the peak relative
  to a local background:
  <P>
  	cl&gt; apresize image ylevel=.05 peak+ bkg+
  <P>
  3.  To resize all apertures to the point where the data exceeds 100
  data units:
  <P>
  	cl&gt; apresize image ylevel=100 peak- bkg-
  <P>
  4.  To resize all apertures to default values of the task except
  averaging all the results at the end:
  <P>
  	cl&gt; apresize image avg+
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>APRESIZE V2.11</B></DT>
  <! Sec='REVISIONS' Level=0 Label='APRESIZE' Line='APRESIZE V2.11'>
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
  center1d, ranges, apfind, aprecenter, apedit, apall
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'ADDITIONAL PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
