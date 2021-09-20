.. _tproduct:

tproduct: Form the Cartesian product of two tables.
===================================================

**Package: nttools**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  tproduct intable1 intable2 outtable
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  This task creates an output table which is the Cartesian product of two input
  tables. This Cartesian product consists of every possible combination of the
  rows of the two input tables. Therefore, the number of rows in the output table
  is the product of the number of rows in the two input tables. The output table
  will contain all the columns from both input tables. If a column name in the
  first input table is the same as a column name in the second input table, this
  task tries to create a unique name by appending <span style="font-family: monospace;">"_1"</span> to the first name and <span style="font-family: monospace;">"_2"</span>
  to the second name. If the task cannot create a unique name in this way, it
  stops with an error. 
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>intable1 [file name]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='intable1' Line='intable1 [file name]' -->
  <dd>First input table.
  </dd>
  </dl>
  <dl>
  <dt><b>intable2 [file name]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='intable2' Line='intable2 [file name]' -->
  <dd>Second input table.
  </dd>
  </dl>
  <dl>
  <dt><b>outtable [file name]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='outtable' Line='outtable [file name]' -->
  <dd>Output table containing the possible Cartesian products.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Find all persons sharing a phone from a phone list:
  </p>
  <pre>
  tt&gt; tproduct phone.tab phone.tab phone.tmp
  tt&gt; tselect phone.tmp share.tmp "phone_1 == phone_2 &amp;&amp; name_1 &lt; name_2"
  tt&gt; tproject share.tmp share.tab phone_2 inc-
  tt&gt; delete *.tmp
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <!-- EndSection:   'BUGS' -->
  <h3>References</h3>
  <!-- BeginSection: 'REFERENCES' -->
  <p>
  This task was written by Bernie Simon.
  </p>
  <!-- EndSection:   'REFERENCES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  tselect, tproject, tjoin
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  -->
  
