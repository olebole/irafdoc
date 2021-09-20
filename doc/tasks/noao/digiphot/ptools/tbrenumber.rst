.. _tbrenumber:

tbrenumber: Renumber a list of  apphot/daophot tables databases
===============================================================

**Package: ptools**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  tbrenumber tables
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>tables</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='tables' Line='tables' -->
  <dd>The list of APPHOT/DAOPHOT STSDAS table databases to be renumbered.
  </dd>
  </dl>
  <dl>
  <dt><b>idoffset = 0</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='idoffset' Line='idoffset = 0' -->
  <dd>An integer offset  to be added to the id numbers of the stars in
  the output renumbered photometry file. If idoffset is &gt; 0, the output
  id numbers will run from 1 + idoffset to N + idoffset instead of from 1 to N.
  </dd>
  </dl>
  <dl>
  <dt><b>id = <span style="font-family: monospace;">"ID"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='id' Line='id = "ID"' -->
  <dd>The name of the keyword whose value is the sequence number of the object
  in the database.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  TBRENUMBER is a simple script task which accepts an APPHOT/DAOPHOT STSDAS
  table database and renumbers the objects from 1 + idoffset to N + idoffset,
  where N is the number
  of objects in the database. TBRENUMBER calls the TABLES package TCALC task
  to actually do the work.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Renumber a concatenated NSTAR photometry file that has been written with
  TBCONCAT.
  </p>
  <pre>
     pt&gt; tbrenumber m92r.nst
  </pre>
  <p>
  2. Renumber a PHOT photometry file of extra stars so as to ensure the
  stars' id numbers are  greater than 4000.
  </p>
  <pre>
      pt&gt; tbrenumber m92r.mag.extra idoffset=4000
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
  ptools.txrenumber,ptools.prenumber,tables.tcalc
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  -->
  
