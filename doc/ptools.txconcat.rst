txconcat — Concatenate a list of apphot/daophot text databases
==============================================================

**Package: ptools**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>txconcat (Dec92)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.digiphot.ptools</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>txconcat (Dec92)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>txconcat</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  txconcat -- concatenate a list of APPHOT/DAOPHOT text databases
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  txconcat textfiles outfile
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_textfiles">textfiles</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='textfiles' Line='textfiles'>
  <DD>The list of APPHOT/DAOPHOT text databases to be concatenated.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_outfile">outfile</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outfile' Line='outfile'>
  <DD>The name of the output APPHOT/DAOPHOT text database.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_task">task = "<TT>TASK</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='task' Line='task = "TASK"'>
  <DD>The name of the keywords whose value is the name of the task which wrote
  the database.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  TXCONCAT is a simple task which accepts a list of APPHOT/DAOPHOT text
  database files and concatenates them into one resultant output file.
  TXCONCAT checks that all the file are indeed APPHOT/DAOPHOT text
  database files and that they were all written by the same task before
  performing the concatenation.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Concatenate a list of DAOPHOT PHOT task result files into a single
  output file.
  <P>
  <PRE>
     pt&gt; txconcat m92r.mag.1,m92r.mag.2,m92r.mag.3 m92rall.mag.1
  </PRE>
  <P>
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
  ptools.tbconcat,ptools.pconcat,tables.tmerge,concatenate
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>