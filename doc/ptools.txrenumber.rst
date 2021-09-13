.. _txrenumber:

txrenumber — Renumber a list of apphot/daophot text databases
=============================================================

**Package: ptools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  txrenumber -- renumber a list of APPHOT/DAOPHOT text database
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  txrenumber textfiles
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>textfiles</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='textfiles' Line='textfiles'>
  <DD>The APPHOT/DAOPHOT text database to be renumbered.
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
  <DD>The name of the keyword whose value is the sequence number of the object in
  the list. After renumbering the original values of the <I>id</I> are replaced
  by numbers 1 through N, where N is the total number of objects in the list.
  The id keyword must denote an integer quantity.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  TXRENUMBER is a simple task which accepts an APPHOT/DAOPHOT text
  database file and renumbers all the objects in the file beginning
  with 1 and ending with the number of objects in the file.
  The renumber operation is performed in place. The original
  values of the  <I>id</I> field are replaced by numbers 1 + idoffset
  through N + idoffset
  where N is the total number of objects in the list.
  A renumber operation is typically performed after another
  list operation such as TXCONCAT or TXSORT.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Renumber the stars in a concatenated file produced by TXCONCAT.
  <P>
  <PRE>
     pt&gt; txrenumber m92rall.mag.1
  </PRE>
  <P>
  2. Renumber a PHOT photometry file of extra stars so as to ensure the
  stars' id numbers are  greater than 4000.
  <P>
  <PRE>
      pt&gt; txrenumber m92r.mag.extra idoffset=4000
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
  ptools.tbrenumber,ptools.prenumber,tables.tcalc
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
