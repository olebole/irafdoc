.. _prenumber:

prenumber: Renumber stars in an apphot database
===============================================

**Package: apphot**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  prenumber -- renumber an APPHOT/DAOPHOT database
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  renumber infile
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>infile</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='infile' Line='infile' -->
  <dd>The APPHOT/DAOPHOT database to be renumbered.
  </dd>
  </dl>
  <dl>
  <dt><b>id = <tt>"ID"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='id' Line='id = "ID"' -->
  <dd>The name of the keyword whose value is the sequence number of the object
  </dd>
  </dl>
  <dl>
  <dt><b>idoffset = 0</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='idoffset' Line='idoffset = 0' -->
  <dd>An integer offset  to be added to the id numbers of the stars in
  the output renumbered photometry file. If idoffset is &gt; 0, the output
  id numbers will run from 1 + idoffset to N + idoffset instead of from 1 to N.
  in the database.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  PRENUMBER is a simple task which accepts an APPHOT/DAOPHOT
  database file and renumbers the objects in the file from 1 + idoffset
  to N + idoffset,
  where N is the number of objects in the database. A renumber operation is
  often performed
  after an append operation to insure that the database objects have unique id
  numbers or after a sort to put the id numbers in order.
  </p>
  <p>
  PRENUMBER is a script which executes TXRENUMBER if the APPHOT/DAOPHOT
  database is a text database or TCALC if the file is an STSDAS table
  database.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Renumber a sorted NSTAR database that has been sorted on magnitude.
  </p>
  <pre>
     pt&gt; prenumber m92r.nst.1
  </pre>
  <p>
  2. Renumber a PHOT photometry file of extra stars so as to ensure the
  stars' id numbers are  greater than 4000.
  </p>
  <pre>
      pt&gt; prenumber m92r.mag.extra idoffset=4000
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Time requirements</h3>
  <!-- BeginSection: 'TIME REQUIREMENTS' -->
  <!-- EndSection:   'TIME REQUIREMENTS' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  ptools.txrenumber,ptools.tbrenumber,tables.tcalc
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  -->
  
