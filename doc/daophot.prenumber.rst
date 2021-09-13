.. _prenumber:

prenumber — Renumber stars in a daophot database
================================================

**Package: daophot**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  prenumber -- renumber an APPHOT/DAOPHOT database
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  renumber infile
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>infile</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='infile' Line='infile'>
  <DD>The APPHOT/DAOPHOT database to be renumbered.
  </DD>
  </DL>
  <DL>
  <DT><B>id = "<TT>ID</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='id' Line='id = "ID"'>
  <DD>The name of the keyword whose value is the sequence number of the object
  </DD>
  </DL>
  <DL>
  <DT><B>idoffset = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='idoffset' Line='idoffset = 0'>
  <DD>An integer offset  to be added to the id numbers of the stars in
  the output renumbered photometry file. If idoffset is &gt; 0, the output
  id numbers will run from 1 + idoffset to N + idoffset instead of from 1 to N.
  in the database.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  PRENUMBER is a simple task which accepts an APPHOT/DAOPHOT
  database file and renumbers the objects in the file from 1 + idoffset
  to N + idoffset,
  where N is the number of objects in the database. A renumber operation is
  often performed
  after an append operation to insure that the database objects have unique id
  numbers or after a sort to put the id numbers in order.
  <P>
  PRENUMBER is a script which executes TXRENUMBER if the APPHOT/DAOPHOT
  database is a text database or TCALC if the file is an STSDAS table
  database.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Renumber a sorted NSTAR database that has been sorted on magnitude.
  <P>
  <PRE>
     pt&gt; prenumber m92r.nst.1
  </PRE>
  <P>
  2. Renumber a PHOT photometry file of extra stars so as to ensure the
  stars' id numbers are  greater than 4000.
  <P>
  <PRE>
      pt&gt; prenumber m92r.mag.extra idoffset=4000
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
  ptools.txrenumber,ptools.tbrenumber,tables.tcalc
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
