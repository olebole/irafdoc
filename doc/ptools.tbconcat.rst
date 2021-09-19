.. _tbconcat:

tbconcat: Concatenate a list of apphot/daophot tables databases
===============================================================

**Package: ptools**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  tbconcat -- concatenate a list of APPHOT/DAOPHOT STSDAS databases
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  tbconcat tables outtable
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>tables</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='tables' Line='tables' -->
  <dd>The list of APPHOT/DAOPHOT STSDAS databases to be concatenated.
  </dd>
  </dl>
  <dl>
  <dt><b>outtable</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='outtable' Line='outtable' -->
  <dd>The name of the output APPHOT/DAOPHOT STSDAS database.
  </dd>
  </dl>
  <dl>
  <dt><b>task = <tt>"TASK"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='task' Line='task = "TASK"' -->
  <dd>The name of the keyword whose value is the name of the task which wrote
  the database.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  TBCONCAT is a simple task which accepts a list of APPHOT/DAOPHOT STSDAS
  database files and concatenates them into one resultant database.
  TBCONCAT checks that all the file are indeed APPHOT/DAOPHOT STSDAS
  database files and that they were all written by the same task before
  performing the concatenation.
  </p>
  <p>
  TBCONCAT is a simple script built around the STSDAS TABLES package
  task TMERGE. Users should consult the manual page for TMERGE for
  more details about the inner working of the task.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Concatenate a list of DAOPHOT package GROUP output tables into a
  single file.
  </p>
  <pre>
     pt&gt; tbconcat m92r.grp.1,m92r.grp.2,m92r.grp.3 m92rall.grp.1
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
  ptools.txconcat,ptools.pconcat,tables.tmerge,concatenate
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  -->
  
