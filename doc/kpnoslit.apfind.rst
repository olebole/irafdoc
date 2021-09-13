apfind — Automatically find spectra and define apertures
========================================================

**Package: kpnoslit**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>apfind (Sep96)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.twodspec.apextract</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>apfind (Sep96)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>apfind</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  apfind -- Find spectra and define apertures automatically
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  apfind input
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of input images in which spectra are to be identified and
  apertures defined automatically.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_apertures">apertures = "<TT></TT>"</A></B></DT>
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
  <DT><B><A NAME="l_interactive">interactive = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = no'>
  <DD>Run this task interactively?  If the task is not run interactively then
  all user queries are suppressed and interactive aperture editing is
  disabled.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_find">find = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='find' Line='find = yes'>
  <DD>Find the spectra and define apertures automatically?  In order for
  spectra to be found automatically there must be no apertures for the
  input image or reference image defined in the database and the
  parameter <I>nfind</I> must be greater than zero.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_recenter">recenter = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='recenter' Line='recenter = no'>
  <DD>Recenter the apertures?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_resize">resize = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='resize' Line='resize = no'>
  <DD>Resize the apertures?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_edit">edit = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='edit' Line='edit = yes'>
  <DD>Edit the apertures?  The <I>interactive</I> parameter must also be yes.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B><A NAME="l_line">line = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='line' Line='line = INDEF'>
  <DD>The dispersion line (line or column perpendicular to the dispersion axis) to
  be used in finding the spectra.  A value of INDEF selects the middle of the
  image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nsum">nsum = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nsum' Line='nsum = 1'>
  <DD>Number of dispersion lines to be summed or medianed.  The lines are taken
  around the specified dispersion line.  A positive value sums lines and
  a negative value medians lines.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nfind">nfind = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nfind' Line='nfind = 1'>
  <DD>Maximum number of apertures to be defined.  This is a query parameter
  so the user is queried for a value except when given explicitly on
  the command line.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_minsep">minsep = 5.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='minsep' Line='minsep = 5.'>
  <DD>Minimum separation between spectra.  Weaker spectra or noise within this
  distance of a stronger spectrum are rejected.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_maxsep">maxsep = 1000.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maxsep' Line='maxsep = 1000.'>
  <DD>Maximum separation between adjacent spectra.  This parameter
  is used to identify missing spectra in uniformly spaced spectra produced
  by fiber spectrographs.  If two adjacent spectra exceed this separation
  then it is assumed that a spectrum is missing and the aperture identification
  assignments will be adjusted accordingly.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_order">order = "<TT>increasing</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='order' Line='order = "increasing"'>
  <DD>When assigning aperture identifications order the spectra "<TT>increasing</TT>"
  or "<TT>decreasing</TT>" with increasing pixel position (left-to-right or
  right-to-left in a cross-section plot of the image).
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_additional_parameters">ADDITIONAL PARAMETERS</A></H2>
  <! BeginSection: 'ADDITIONAL PARAMETERS'>
  <UL>
  I/O parameters and the default dispersion axis are taken from the
  package parameters, the default aperture parameters are taken from the
  task <B>apdefault</B>, and parameters used for centering and editing the
  apertures are taken from <B>apedit</B>.
  <P>
  When this operation is performed from the task <B>apall</B> all parameters
  except the package parameters are included in that task.
  </UL>
  <! EndSection:   'ADDITIONAL PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  For each image in the input image list spectra are identified and
  default apertures defined.  The automatic aperture finding is performed
  only if 1) there are no apertures defined for the reference image, 2)
  there are no apertures defined for the input image, 3) the parameter
  <I>find</I> is yes, and 4) the parameter <I>nfind</I> is greater than
  zero.
  <P>
  The automatic finding algorithm uses the following steps.  First, all local
  maxima are found.  The maxima are sorted by peak value and the weaker
  of the peaks separated by less than the value given by the parameter
  <I>minsep</I> are rejected.  Finally, at most the <I>nfind</I> strongests
  peaks are kept.  <B>Nfind</B> is a query parameter, so if it is not
  specified explicitly on the command line, the desired number of spectra
  to be found is requested.  After the peaks have been found the
  <B>center1d</B> algorithm is used to refine the centers of the
  profiles.  Apertures having the default parameters set with the task
  <B>apdefault</B> are defined at each center.  This algorithm is also
  available with the <TT>'f'</TT> key in the task <B>apedit</B> with the change that
  existing apertures are kept and count toward the maximum number
  specified by <B>nfind</B>.
  <P>
  The automatic assignment of aperture numbers, beam numbers, and titles
  has several options.  The simplest is when no aperture identification
  table, parameter <I>apidtable</I>, is specified and the maximum separation
  parameter, <I>maxsep</I>, is very large.  In this case the aperture and
  beam numbers are sequential starting from one and numbered either from
  left-to-right or right-to-left depending on the <I>order</I> parameter.
  There are no aperture titles in this case.  If two adjacent spectra are
  separated by more than the specified maximum then the aperture numbers
  jump by the integer part of the ratio of the separation to the
  specified maximum separation.  This is used when the image is expected
  to have evenly spaced spectra, such as in multifiber spectrographs, in
  which some may be missing due to broken fibers.  Finally, the
  aperture identification table (either a text file or an image
  having a set of SLFIBnnn keyowrds) may contain lines with aperture number,
  beam number, and (optional) title.  The sequential numbers are then
  indices into this table.  Note that the skipping of missing spectra and
  the ordering applies to entries in this table as well.
  <P>
  The ways in which the automatic method can fail for evenly spaced
  spectra with missing members are when the first spectrum is missing on
  the side from which the ordering begins and when the expected rather
  the actual number of spectra is used.  In the first case one can use
  the interactive <TT>'o'</TT> key of the aperture editing facility to specify the
  identity of any aperture and then all other apertures will be
  appropriately reidentified.  If more spectra are sought than actually
  exist then noise spikes may be mistakenly found.  This problem can be
  eliminated by specifying the actual number of spectra or minimized by
  using the threshold centering parameter.
  <P>
  The <I>recenter</I> parameter allows recentering apertures if defined by
  a reference image.  Since the purpose of this task is to find new
  apertures it is usually the case that there are no reference images and
  recentering is not done.  The default apertures are of fixed width.
  The <I>resize</I> parameter may be used to adjust the widths in a
  variety of ways.  The aperture positions and any other parameters may
  also be edited with the aperture editing function if selected by the
  <I>apedit</I> parameter and the task is run interactively.
  <P>
  If the task is interactive the user is queried whether to perform
  various steps on each image.  The queries may be answered with one of
  the four values "<TT>yes</TT>", "<TT>no</TT>", "<TT>YES</TT>" and "<TT>NO</TT>", where an upper case
  response suppresses all further queries to this question.
  <P>
  The aperture finding algorithm may be selected from nearly every task
  in the package.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  	cl&gt; apfind image nfind=10
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_revisions">REVISIONS</A></H2>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_APFIND">APFIND V2.11</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='APFIND' Line='APFIND V2.11'>
  <DD>The "<TT>apertures</TT>" parameter can be used to select apertures for resizing,
  recentering, tracing, and extraction.  This parameter name was previously
  used for selecting apertures in the recentering algorithm.  The new
  parameter name for this is now "<TT>aprecenter</TT>".
  <P>
  The aperture ID table information may now be contained in the
  image header under the keywords SLFIBnnn.
  </DD>
  </DL>
  SEE ALSO
  center1d, apdefault, aprecenter, apresize, apedit, apall
  </UL>
  <! EndSection:    'REVISIONS'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'ADDITIONAL PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS'  >
  
  </BODY>
  </HTML>