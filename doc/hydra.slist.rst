slist — List spectrum header parameters
=======================================

**Package: hydra**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>slist1d (Jan92)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.imred.irs/iids</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>slist1d (Jan92)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>slist1d</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  slist1d -- List spectral header information
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  slist1d input records
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The image root name for the spectra to be listed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_records">records</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='records' Line='records'>
  <DD>The record string for the spectra to be listed. The records will be appended
  to the root name to form image names of the type "<TT>root.xxxx</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_long_header">long_header = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='long_header' Line='long_header = no'>
  <DD>If set to yes, then a complete listing of the header elements
  is given. If set to no, then a single line per spectrum is given which lists
  in the following order: the image name, object or sky spectrum, exposure
  time, spectrum length, and image title.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Each spectrum in the list implied by the root name and the record string
  is opened and the header is read. The pixel file is not accessed in order
  to save time. The header listing is directed to STDOUT and may be
  redirected for printing.
  <P>
  A warning message is issued if
  a requested image is not found, but otherwise proceeds.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  The following example lists 8 spectral headers in long form on the printer:
  <P>
  <PRE>
  	cl&gt; slist1d nite1 1001-1008 | lprint
  </PRE>
  <P>
  The next example lists the same spectral headers but in short form
  on the terminal
  <P>
  <PRE>
  	cl&gt; slist1d nite1 1001-1008 long-
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_revisions">REVISIONS</A></H2>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_SLIST1D">SLIST1D V2.10</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='SLIST1D' Line='SLIST1D V2.10'>
  <DD>This task is the same as V2.9 <B>slist</B> and applies only to the older
  IRS/IIDS record extension spectra.  In V2.10 <B>slist</B>
  has been revised for multiaperture spectra.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  SLIST1D does not inform the user if the pixel file can or cannot be read.
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  slist, imheader
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>