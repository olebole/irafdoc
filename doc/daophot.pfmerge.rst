pfmerge — Merge a list of photometry databases
==============================================

**Package: daophot**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>pfmerge (May00)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.digiphot.daophot</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>pfmerge (May00)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>pfmerge</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  pfmerge -- merge a list of photometry files
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  pfmerge inphotfiles outphotfile
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_inphotfiles">inphotfiles</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='inphotfiles' Line='inphotfiles'>
  <DD>The list of photometry files to be merged. Inphotfiles may be the output of the
  DAOPHOT tasks PHOT, PSTSELECT, PSF, PEAK, GROUP, GRPSELECT, NSTAR, or ALLSTAR.
  Inphotfiles may be either a list of APPHOT/DAOPHOT text databases or a list of
  STSDAS binary tables.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_outphotfile">outphotfile</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outphotfile' Line='outphotfile'>
  <DD>The output photometry file. Outphotfile consists of the header of the first
  input photometry file, followed by a list of records, one per input file
  record, each consisting of five fields: ID, XCENTER, YCENTER, MAG, and MSKY.
  Outphotfile is a an APPHOT/DAOPHOT text database if the first photometry file
  is a text database, an STSDAS binary table if the first photometry file is an
  ST table.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose'>
  <DD>Print messages about the progress of the task ?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  PFMERGE creates a new photometry file suitable for input to PSF, PEAK, GROUP,
  or ALLSTAR by extracting the header of the first input photometry file and the
  values of the five fields: ID, XCENTER, YCENTER, MAG, and MSKY from each
  photometry record in each input file, and writing them to <I>outphotfile</I>.
  <I>Inphotfiles</I> may be either APPHOT/DAOPHOT text databases or STSDAS binary
  tables, but <I>outphotfile</I> inherits the type of the first input photometry
  file.
  <P>
  The principal application of PFMERGE is to combine the results of one of the
  DAOPHOT fitting tasks, e.g. ALLSTAR, with the results of the aperture photometry
  task PHOT, to create a new photometry file suitable for input to the fitting
  task. e.g. ALLSTAR, since it if often the case that the user wishes to combine
  preliminary results for a few additional stars with the best fit results to
  date on the original star list. 
  <P>
  PFMERGE is intended to combine photometry files from different DAOPHOT tasks.
  The task PCONCAT can be used to combine photometry files produced by the same
  task.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Combine the results of the first allstar run with phot task results
  on a small list of stars detected after the first list of stars was
  subtracted from the original image.
  <P>
  <PRE>
  	cl&gt; pfmerge m92.als.1,m92.mag.5 m92.als.2
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_time_requirements">TIME REQUIREMENTS</A></H2>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  pconcat
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>