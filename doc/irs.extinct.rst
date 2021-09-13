extinct — Use BSWITCH for extinction correction
===============================================

**Package: irs**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>extinct (Apr85)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.onedspec</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>extinct (Apr85)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>extinct</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  extinct -- Correct spectra for atmospheric extinction
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  extinct root records output
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_root">root</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='root' Line='root'>
  <DD>The root name for the input spectra to be corrected.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_records">records</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='records' Line='records'>
  <DD>The range of spectra to be included in the extinction operation.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>The root name for the output corrected spectra
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_start_rec">start_rec</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='start_rec' Line='start_rec'>
  <DD>The starting record number for the output corrected spectra.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nr_aps">nr_aps = 2</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nr_aps' Line='nr_aps = 2'>
  <DD>The number of instrument apertures for this data set.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The input spectra are corrected for atmospheric extinction. 
  EXTINCT redirects the spectra through the task BSWITCH so all
  procedures are identical to those described for that task.
  <P>
  Because BSWITCH attempts to perform a beam-switch operation
  unless the subset parameter is equal to the number of
  instrument apertures (in which case beam-switching degenerates
  to a copy operation), the hidden parameter nr_aps should be set
  appropriately to the instrument. For IIDS and IRS data, this
  is 2.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  	cl&gt; extinct  nite1 1001-1032 nite1ex
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  The input string of spectra must be ordered so that only
  one spectrum from each aperture is present among substrings
  of length nr_aps.
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  bswitch
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>