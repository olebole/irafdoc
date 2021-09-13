.. _tbrenumber:

tbrenumber — Renumber a list of  apphot/daophot tables databases
================================================================

**Package: ptools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  tbrenumber -- renumber a list of APPHOT/DAOPHOT STSDAS table database(s)
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  tbrenumber tables
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>tables</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='tables' Line='tables'>
  <DD>The list of APPHOT/DAOPHOT STSDAS table databases to be renumbered.
  </DD>
  </DL>
  <DL>
  <DT><B>idoffset = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='idoffset' Line='idoffset = 0'>
  <DD>An integer offset  to be added to the id numbers of the stars in
  the output renumbered photometry file. If idoffset is &gt; 0, the output
  id numbers will run from 1 + idoffset to N + idoffset instead of from 1 to N.
  </DD>
  </DL>
  <DL>
  <DT><B>id = "<TT>ID</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='id' Line='id = "ID"'>
  <DD>The name of the keyword whose value is the sequence number of the object
  in the database.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  TBRENUMBER is a simple script task which accepts an APPHOT/DAOPHOT STSDAS
  table database and renumbers the objects from 1 + idoffset to N + idoffset,
  where N is the number
  of objects in the database. TBRENUMBER calls the TABLES package TCALC task
  to actually do the work.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Renumber a concatenated NSTAR photometry file that has been written with
  TBCONCAT.
  <P>
  <PRE>
     pt&gt; tbrenumber m92r.nst
  </PRE>
  <P>
  2. Renumber a PHOT photometry file of extra stars so as to ensure the
  stars' id numbers are  greater than 4000.
  <P>
  <PRE>
      pt&gt; tbrenumber m92r.mag.extra idoffset=4000
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
  ptools.txrenumber,ptools.prenumber,tables.tcalc
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
