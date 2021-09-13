coefs — Extract mtn reduced coefficients from henear scans
==========================================================

**Package: iids**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>coefs (May85)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.imred.iids/noao.imred.irs</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>coefs (May85)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>coefs</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  coefs -- Extract dispersion coefs from mtn HeNeAr headers
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  coefs input records database
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The input image root name for the spectral images containing the
  dispersion coefficients.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_records">records</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='records' Line='records'>
  <DD>The range of records for which the root name applies.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_database">database</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='database' Line='database'>
  <DD>The database file name which will contain the coefficients.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The spectra specified by the combination of the root name
  and the records are scanned for the presence of dispersion
  coefficients. If present, the coefficients and necessary
  information are written to the file indicated by the database
  parameter. This file an then be used by the linearization
  program DISPCOR to correct any spectra for which the
  database is appropriate.
  <P>
  Each invocation of COEFS appends to the database file, or
  creates a new file if necessary.
  <P>
  The following assumptions are made concerning the coefficients,
  which are always correct for IIDS and IRS mountain reduced
  data at Kitt Peak.
  <DL>
  <DT><B><A NAME="l_">(1)</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='(1)'>
  <DD>The coefficients represent Legendre polynomials.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(2)</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='(2)'>
  <DD>The coefficients apply to pixels 1 through 1024 in the original data.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  The following example reads the coefficients from the headers
  for nite1 arc spectra taken near the beginning and end of the
  night and creates a database file called nite1.db:
  <P>
  	cl&gt; coefs nite1 3-4,201-202 nite1.db
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_time_requirements">TIME REQUIREMENTS</A></H2>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  Approximately 1 second per spectrum is required. This is primarily
  overhead due to file access.
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  dispcor, identify
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>