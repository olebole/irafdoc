.. _pconcat:

pconcat — Concatenate a list of daophot databases
=================================================

**Package: daophot**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  pconcat -- concatenate a list of APPHOT/DAOPHOT databases
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  pconcat infiles outfile
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>infiles</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='infiles' Line='infiles'>
  <DD>The list of APPHOT/DAOPHOT databases to be concatenated.
  </DD>
  </DL>
  <DL>
  <DT><B>outfile</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outfile' Line='outfile'>
  <DD>The name of the output APPHOT/DAOPHOT database.
  </DD>
  </DL>
  <DL>
  <DT><B>task = "<TT>TASK</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='task' Line='task = "TASK"'>
  <DD>The name of the keywords whose value is the name of the task which wrote
  the database.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  PCONCAT is a simple task which accepts a list of APPHOT/DAOPHOT
  database files and concatenates them into one resultant output file.
  PCONCAT checks that all the file are indeed APPHOT/DAOPHOT
  database files and that they were all written by the same task before
  performing the concatenation.
  <P>
  PCONCAT is a simple script which call TXCONCAT in the PTOOLS package
  if the input files are text database files or TBCONCAT in the PTOOLS package
  if the input files are STSDAS database files. TBCONCAT is itself a script
  which call the TABLES package task TMERGE to do the actual work.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Concatenate a list of DAOPHOT package task GROUP output database files
  into a single output file.
  <P>
  <PRE>
     pt&gt; pconcat m92r.grp.1,m92r.grp.2,m92r.grp.3 m92rall.grp.1
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
  ptools.txconcat,ptools.tbconcat,tables.tmerge,concatenate
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
