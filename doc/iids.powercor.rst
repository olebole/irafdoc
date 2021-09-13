powercor — Apply power law correction to mountain reduced spectra
=================================================================

**Package: iids**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>powercor (Oct86)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.imred.iids/noao.imred.irs</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>powercor (Oct86)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>powercor</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  powercor -- Apply power law correction to mountain reduced spectra
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  powercor input records
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The root file name of the input spectra.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_records">records</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='records' Line='records'>
  <DD>The range of spectra.
  The names of the spectra will be formed by appending the range
  elements to the input root name.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>This is the root file name for the corrected spectra.
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
  <DT><B><A NAME="l_power">power = )iids.power</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='power' Line='power = )iids.power'>
  <DD>The power law coefficient.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  A power law correction to the IIDS count rates is applied to the input
  spectra.  The mountain reduction software applies a coincidence correction
  to the observed IIDS count rates but does not correct for a nonlinear effect
  in the image tube chain.  This second correction takes the form of a
  power law
  <P>
  	C(out) = C(in) ** power
  <P>
  where C(in) is the input, coincidence corrected, count rate and C(out)
  is the corrected count rate.  The power is a parameter of the task
  which defaults to the <B>iids</B> package parameter set to the appropriate
  value for the IIDS.  The exposure time, in seconds, is a required
  image header parameter (keyword = EXPOSURE) used to convert the
  total counts to count rates.
  <P>
  Note that if the original raw spectra are being reduced then the either
  <B>coincor</B> or <B>powercor</B> may be used to apply both the coincidence
  correction and the power law correction at the same time.  In other words,
  the tasks apply the coincidence correction if the coincidence flag (CO-FLAG) is
  -1 (uncorrected) and the power law correction alone if the flag is zero
  (coincidence corrected only).  The flag is 1 when both the coincidence and
  nonlinear correction have been applied.
  <P>
  This task is a script calling <B>coincor</B> with <I>ccmode</I> = "<TT>iids</TT>".
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  The following example corrects a series of IIDS spectra:
  <P>
  	cl&gt; powercor nite1 1-250 output=nite1cc start_rec=1
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  coincor
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>