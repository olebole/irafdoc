.. _txrenumber:

txrenumber: Renumber a list of apphot/daophot text databases
============================================================

**Package: ptools**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  txrenumber -- renumber a list of APPHOT/DAOPHOT text database
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  txrenumber textfiles
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>textfiles</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='textfiles' Line='textfiles' -->
  <dd>The APPHOT/DAOPHOT text database to be renumbered.
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
  <dt><b>id = <tt>"ID"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='id' Line='id = "ID"' -->
  <dd>The name of the keyword whose value is the sequence number of the object in
  the list. After renumbering the original values of the <i>id</i> are replaced
  by numbers 1 through N, where N is the total number of objects in the list.
  The id keyword must denote an integer quantity.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  TXRENUMBER is a simple task which accepts an APPHOT/DAOPHOT text
  database file and renumbers all the objects in the file beginning
  with 1 and ending with the number of objects in the file.
  The renumber operation is performed in place. The original
  values of the  <i>id</i> field are replaced by numbers 1 + idoffset
  through N + idoffset
  where N is the total number of objects in the list.
  A renumber operation is typically performed after another
  list operation such as TXCONCAT or TXSORT.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Renumber the stars in a concatenated file produced by TXCONCAT.
  </p>
  <pre>
     pt&gt; txrenumber m92rall.mag.1
  </pre>
  <p>
  2. Renumber a PHOT photometry file of extra stars so as to ensure the
  stars' id numbers are  greater than 4000.
  </p>
  <pre>
      pt&gt; txrenumber m92r.mag.extra idoffset=4000
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
  ptools.tbrenumber,ptools.prenumber,tables.tcalc
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  -->
  
