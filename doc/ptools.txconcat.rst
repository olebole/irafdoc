.. _txconcat:

txconcat: Concatenate a list of apphot/daophot text databases
=============================================================

**Package: ptools**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  txconcat -- concatenate a list of APPHOT/DAOPHOT text databases
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  txconcat textfiles outfile
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>textfiles</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='textfiles' Line='textfiles' -->
  <dd>The list of APPHOT/DAOPHOT text databases to be concatenated.
  </dd>
  </dl>
  <dl>
  <dt><b>outfile</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='outfile' Line='outfile' -->
  <dd>The name of the output APPHOT/DAOPHOT text database.
  </dd>
  </dl>
  <dl>
  <dt><b>task = <tt>"TASK"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='task' Line='task = "TASK"' -->
  <dd>The name of the keywords whose value is the name of the task which wrote
  the database.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  TXCONCAT is a simple task which accepts a list of APPHOT/DAOPHOT text
  database files and concatenates them into one resultant output file.
  TXCONCAT checks that all the file are indeed APPHOT/DAOPHOT text
  database files and that they were all written by the same task before
  performing the concatenation.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Concatenate a list of DAOPHOT PHOT task result files into a single
  output file.
  </p>
  <pre>
     pt&gt; txconcat m92r.mag.1,m92r.mag.2,m92r.mag.3 m92rall.mag.1
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
  ptools.tbconcat,ptools.pconcat,tables.tmerge,concatenate
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  -->
  
