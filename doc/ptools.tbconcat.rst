tbconcat — Concatenate a list of apphot/daophot tables databases
================================================================

**Package: ptools**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>tbconcat (Dec92)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.digiphot.ptools</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>tbconcat (Dec92)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>tbconcat</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  tbconcat -- concatenate a list of APPHOT/DAOPHOT STSDAS databases
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  tbconcat tables outtable
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_tables">tables</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='tables' Line='tables'>
  <DD>The list of APPHOT/DAOPHOT STSDAS databases to be concatenated.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_outtable">outtable</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outtable' Line='outtable'>
  <DD>The name of the output APPHOT/DAOPHOT STSDAS database.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_task">task = "<TT>TASK</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='task' Line='task = "TASK"'>
  <DD>The name of the keyword whose value is the name of the task which wrote
  the database.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  TBCONCAT is a simple task which accepts a list of APPHOT/DAOPHOT STSDAS
  database files and concatenates them into one resultant database.
  TBCONCAT checks that all the file are indeed APPHOT/DAOPHOT STSDAS
  database files and that they were all written by the same task before
  performing the concatenation.
  <P>
  TBCONCAT is a simple script built around the STSDAS TABLES package
  task TMERGE. Users should consult the manual page for TMERGE for
  more details about the inner working of the task.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Concatenate a list of DAOPHOT package GROUP output tables into a
  single file.
  <P>
  <PRE>
     pt&gt; tbconcat m92r.grp.1,m92r.grp.2,m92r.grp.3 m92rall.grp.1
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
  ptools.txconcat,ptools.pconcat,tables.tmerge,concatenate
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>