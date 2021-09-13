mkms — Create multispec from 1D spectra including associated bands
==================================================================

**Package: nproto**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>mkms (Jan03)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.nproto</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>mkms (Jan03)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>mkms</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  mkms -- make multispec format from 1D arrays with associated bands
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  mkms output spectra raw background sigma
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>Name of output multispec image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_spectra">spectra</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='spectra' Line='spectra'>
  <DD>List of primary 1D spectra to be included in multispec image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_raw">raw</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='raw' Line='raw'>
  <DD>List of 1D raw or secondary spectra.  If none specify "<TT></TT>" otherwise
  the list must match the list of primary spectra.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_background">background</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='background' Line='background'>
  <DD>List of 1D background spectra.  If none specify "<TT></TT>" otherwise
  the list must match the list of primary spectra.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_sigma">sigma</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sigma' Line='sigma'>
  <DD>List of 1D sigma spectra.  If none specify "<TT></TT>" otherwise
  the list must match the list of primary spectra.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  MKMS creates a multispec format from 1D spectra.  Unlike SCOPY it
  can include associated spectra.  There can be any number of primary 1D
  spectra and the associated spectra are optional.  However, when
  associated spectra are specified the list must match the primary spectra
  list and the arrays must have the same number of pixels and dispersion
  as the primary spectrum.  The different spectra may have different
  dispersions.
  <P>
  This is a simple script using SCOPY and IMSTACK.  It has minimal error
  checking.  In particular, if the set of input is not consistent the
  task will abort with an error leaving temporary files behind.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. To create an image with one spectrum and each of the associated types:
  <P>
  <PRE>
      cl&gt; mkms out.ms spec rawspec bkgspec sigspec
  </PRE>
  <P>
  2. To create an image with three primary spectra and error arrays:
  <P>
  <PRE>
      cl&gt; mkms out.ms spec1,spec2,spec3 "" "" err1,err2,err3
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_revisions">REVISIONS</A></H2>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_MKMS">MKMS V2.12.2</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='MKMS' Line='MKMS V2.12.2'>
  <DD>This prototype task added for this release.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  scopy, imstack
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>