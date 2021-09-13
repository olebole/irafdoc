prenumber — Renumber stars in an apphot database
================================================

**Package: apphot**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>prenumber (May93)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.digiphot.ptools</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>prenumber (May93)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>prenumber</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  prenumber -- renumber an APPHOT/DAOPHOT database
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  renumber infile
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_infile">infile</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='infile' Line='infile'>
  <DD>The APPHOT/DAOPHOT database to be renumbered.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_id">id = "<TT>ID</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='id' Line='id = "ID"'>
  <DD>The name of the keyword whose value is the sequence number of the object
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_idoffset">idoffset = 0</A></B></DT>
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
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
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
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
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
  ptools.txrenumber,ptools.tbrenumber,tables.tcalc
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>