.. _tbconcat:

tbconcat — Concatenate a list of apphot/daophot tables databases
================================================================

**Package: ptools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  tbconcat -- concatenate a list of APPHOT/DAOPHOT STSDAS databases
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  tbconcat tables outtable
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>tables</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='tables' Line='tables'>
  <DD>The list of APPHOT/DAOPHOT STSDAS databases to be concatenated.
  </DD>
  </DL>
  <DL>
  <DT><B>outtable</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outtable' Line='outtable'>
  <DD>The name of the output APPHOT/DAOPHOT STSDAS database.
  </DD>
  </DL>
  <DL>
  <DT><B>task = "<TT>TASK</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='task' Line='task = "TASK"'>
  <DD>The name of the keyword whose value is the name of the task which wrote
  the database.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
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
  <H3>Examples</H3>
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
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  ptools.txconcat,ptools.pconcat,tables.tmerge,concatenate
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
