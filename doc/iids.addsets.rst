addsets — Add subsets of strings of spectra
===========================================

**Package: iids**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>addsets (Feb85)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.imred.iids/noao.imred.irs</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>addsets (Feb85)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>addsets</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  addsets - Add subsets of a string of spectra
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  addsets input records
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The root file name for the input spectra in the string.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_records">records</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='records' Line='records'>
  <DD>The range of spectra indicating the elements of the string.
  The names of the spectra will be formed by appending the range
  elements to the input root name.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>This is the root file name for the names of the spectra which will
  be created by the addset operation.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_start_rec">start_rec = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='start_rec' Line='start_rec = 1'>
  <DD>The starting record number to be appended to the root name of the
  created spectra.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_subset">subset = 2</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='subset' Line='subset = 2'>
  <DD>The length of the substring of spectra which will be added together.
  For IIDS/IRS data which has been processed through BSWITCH, this
  parameter should be 2. This implies that spectra will be taken 
  2 at a time, added, and the sum written as a new spectrum.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_weighting">weighting = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='weighting' Line='weighting = yes'>
  <DD>If set to yes, an average of the substring of spectra is generated
  (if flux calibrated) weighted by the integration times of the
  individual spectra. If set to no, a simple average is generated.
  If not flux calibrated, this parameter has no effect - a simple
  sum is generated.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Every "<TT>subset</TT>" group of spectra will be accumulated and the sum will be
  written as a new spectrum. For example, if the input string contains
  100 spectra, and subset=2, then 50 new spectra will be created. Each
  new spectrum will be the sum of the consecutive pairs in the original string.
  <P>
  If there are insufficient spectra to complete a subset accumulation,
  the sum is written out anyway and a warning printed. For example,
  if the input string contains 23 spectra, and subset=4, there will be
  6 new spectra created, but the last one will be based on only 3 spectra.
  <P>
  Subset may be set to 1 to allow a copy operation although this is not
  a very efficient way to do so.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  The following three examples are those described above.
  <P>
  <PRE>
  	cl&gt; addsets nite1 2001-2100
  	cl&gt; addsets nite1 2001-2023 subset=4
  	cl&gt; addsets nite1 2001-2010 subset=1 output=nite2 \<BR>
  	&gt;&gt;&gt; start_rec=2001
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  bswitch
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>