apmask — Create and IRAF pixel list mask of the apertures
=========================================================

**Package: apextract**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>apmask (Sep96)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.twodspec.apextract</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>apmask (Sep96)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>apmask</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  apmask -- Make pixel mask from apertures definitions
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
  <DD>List of input images with aperture definitions.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>List of output mask names.  As a convention the extension "<TT>.pl</TT>" (pixel
  list) should be used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_apertures">apertures = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='apertures' Line='apertures = ""'>
  <DD>Apertures to recenter, resize, trace, and create a mask.  This only applies
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
  <DL>
  <DT><B><A NAME="l_trace">trace = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='trace' Line='trace = yes'>
  <DD>Trace apertures?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fittrace">fittrace = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fittrace' Line='fittrace = yes'>
  <DD>Fit the traced points interactively?  The <I>interactive</I> parameter
  must also be yes.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_mask">mask = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='mask' Line='mask = yes'>
  <DD>Create mask images?
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B><A NAME="l_line">line = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='line' Line='line = INDEF'>
  <DD>The dispersion line (line or column perpendicular to the dispersion axis) to
  be used in finding, recentering, resizing, editing, and starting to
  trace spectra.  A value of INDEF selects the middle of the image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nsum">nsum = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nsum' Line='nsum = 1'>
  <DD>Number of dispersion lines to be summed or medianed.  The lines are taken
  around the specified dispersion line.  A positive value takes the
  sum and a negative value selects a median.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_buffer">buffer = 0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='buffer' Line='buffer = 0.'>
  <DD>Buffer to add to aperture limits.  One use for this is to increase
  the width of the apertures when a mask is used to fit data between
  the apertures.
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
  Pixel list masks are created from the aperture definitions in the input
  images.  Pixel list masks are a compact way to define arbitrary
  regions of an image.  The masks may be used directly as an image with values
  of 1 (in an aperture) and 0 (outside an aperture).  Alternatively,
  some tasks may use a mask to define regions to be operated upon.
  When this task was written there were no such tasks though eventually
  some tasks will be converted to use this general format.  The intent
  of making an aperture mask is to someday allow using it with the task
  <B>imsurfit</B> to fit a background or scattered light surface.
  (See <B>apscatter</B> for an alternative method).
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. To replace all data outside the apertures by zero:
  <P>
  <PRE>
  	cl&gt; apmask image image.pl nfind=10
  	cl&gt; imarith image * image.pl image1
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_revisions">REVISIONS</A></H2>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_APMASK">APMASK V2.11</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='APMASK' Line='APMASK V2.11'>
  <DD>The "<TT>apertures</TT>" parameter can be used to select apertures for resizing,
  recentering, tracing, and extraction.  This parameter name was previously
  used for selecting apertures in the recentering algorithm.  The new
  parameter name for this is now "<TT>aprecenter</TT>".
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  apdefault, aprecenter, apresize, apedit, aptrace, apall
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'ADDITIONAL PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>