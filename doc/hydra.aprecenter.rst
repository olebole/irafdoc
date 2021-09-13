.. _aprecenter:

aprecenter — Recenter apertures
===============================

**Package: hydra**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  aprecenter -- Recenter apertures automatically
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  aprecenter input
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of input images in which apertures are to be recentered.
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
  <DT><B>recenter = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='recenter' Line='recenter = yes'>
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
  <P>
  <DL>
  <DT><B>line = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='line' Line='line = INDEF'>
  <DD>The dispersion line (line or column perpendicular to the dispersion axis) to
  be used in recentering the spectra.  A value of INDEF selects the middle of the
  image.
  </DD>
  </DL>
  <DL>
  <DT><B>nsum = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nsum' Line='nsum = 1'>
  <DD>Number of dispersion lines to be summed or medianed.  The lines are taken
  around the specified dispersion line.  A positive value takes a sum
  and a negative values selects a median.
  </DD>
  </DL>
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
  <DD>Use the median shift from recentering the selected apertures to apply to
  all apertures.  The recentering is then a constant shift for all apertures.
  The median is the average of the two central values for an even number
  of apertures.
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
  For each image in the input image list, the aperture center positions
  are redefined by centering at the specified dispersion line using the
  <B>center1d</B> algorithm with centering parameters from <B>apedit</B>.
  Normally this is done when inheriting apertures from an aperture
  reference image.  The recentering does not change the "<TT>trace</TT>" of the
  aperture but simple adds a shift across the dispersion axis.
  <P>
  There are a several recentering options.  Each selected aperture may be
  recentered independently.  However, if some or all of the spectra are
  relatively weak this may actually be worse than using the reference
  apertures defined by strong spectra or flat fields in the case of
  fibers or aperture masks.  One may select a subset of apertures to be
  used in calculating shift.  This is done with a the <I>aprecenter</I>
  list of aperture numbers (see
  <B>ranges</B> for the syntax) and/or by selecting a specific number or
  fraction of the apertures with the strongest peak values.  The list
  selection is done first and the strongest remaining apertures are used
  to satisfy the <B>npeaks</B> value.  Though some or all of the apertures
  may be recentered independently the most common case of recentering
  reference apertures is to account for detector shifts.  In this case
  one expects that any shift should be common to all apertures.  The
  <I>shift</I> parameter allows using the new centers for all selected
  apertures to compute a median shift to be added to ALL apertures.  Using
  a median shift for all apertures is the default.
  <P>
  The <I>find</I> parameter allows automatically finding apertures if none
  are defined for the image or by a reference image.  Since the purpose
  of this task is to recenter reference apertures it is usually the case
  that reference images are used and apertures are not defined by this
  task.  One case in which the apertures from the image itself might be
  recentered is if one wants to use a different dispersion line.  The
  <I>resize</I> parameter may be used to adjust the widths in a variety
  of ways based on the spectra profiles specific to each image.  The
  aperture positions and any other parameters may also be edited with the
  aperture editing function if selected by the <I>apedit</I> parameter and
  the task is run interactively.  The recentering algorithm may be run
  from the aperture editor using the <TT>'g'</TT> keystroke.
  <P>
  If the task is interactive the user is queried whether to perform
  various steps on each image.  The queries may be answered with one of
  the four values "<TT>yes</TT>", "<TT>no</TT>", "<TT>YES</TT>" and "<TT>NO</TT>", where an upper case
  response suppresses all further queries to this question.
  <P>
  The aperture recentering algorithm may be selected from nearly every task
  in the package.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  	cl&gt; aprecenter newimage reference=flat
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>APRECENTER V2.11</B></DT>
  <! Sec='REVISIONS' Level=0 Label='APRECENTER' Line='APRECENTER V2.11'>
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
  center1d, ranges, apfind, apresize, apedit, apall
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'ADDITIONAL PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
