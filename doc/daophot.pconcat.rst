.. _pconcat:

pconcat: Concatenate a list of daophot databases
================================================

**Package: daophot**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  pconcat -- concatenate a list of APPHOT/DAOPHOT databases
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  pconcat infiles outfile
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>infiles</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='infiles' Line='infiles' -->
  <dd>The list of APPHOT/DAOPHOT databases to be concatenated.
  </dd>
  </dl>
  <dl>
  <dt><b>outfile</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='outfile' Line='outfile' -->
  <dd>The name of the output APPHOT/DAOPHOT database.
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
  PCONCAT is a simple task which accepts a list of APPHOT/DAOPHOT
  database files and concatenates them into one resultant output file.
  PCONCAT checks that all the file are indeed APPHOT/DAOPHOT
  database files and that they were all written by the same task before
  performing the concatenation.
  </p>
  <p>
  PCONCAT is a simple script which call TXCONCAT in the PTOOLS package
  if the input files are text database files or TBCONCAT in the PTOOLS package
  if the input files are STSDAS database files. TBCONCAT is itself a script
  which call the TABLES package task TMERGE to do the actual work.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Concatenate a list of DAOPHOT package task GROUP output database files
  into a single output file.
  </p>
  <pre>
     pt&gt; pconcat m92r.grp.1,m92r.grp.2,m92r.grp.3 m92rall.grp.1
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
  ptools.txconcat,ptools.tbconcat,tables.tmerge,concatenate
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  -->
  
