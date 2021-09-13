.. _tproduct:

tproduct — Form the Cartesian product of two tables.
====================================================

**Package: nttools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  tproduct -- Form the Cartesian product of two tables.
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  tproduct intable1 intable2 outtable
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task creates an output table which is the Cartesian product of two input
  tables. This Cartesian product consists of every possible combination of the
  rows of the two input tables. Therefore, the number of rows in the output table
  is the product of the number of rows in the two input tables. The output table
  will contain all the columns from both input tables. If a column name in the
  first input table is the same as a column name in the second input table, this
  task tries to create a unique name by appending "<TT>_1</TT>" to the first name and "<TT>_2</TT>"
  to the second name. If the task cannot create a unique name in this way, it
  stops with an error. 
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>intable1 [file name]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='intable1' Line='intable1 [file name]'>
  <DD>First input table.
  </DD>
  </DL>
  <DL>
  <DT><B>intable2 [file name]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='intable2' Line='intable2 [file name]'>
  <DD>Second input table.
  </DD>
  </DL>
  <DL>
  <DT><B>outtable [file name]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outtable' Line='outtable [file name]'>
  <DD>Output table containing the possible Cartesian products.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Find all persons sharing a phone from a phone list:
  <P>
  <PRE>
  tt&gt; tproduct phone.tab phone.tab phone.tmp
  tt&gt; tselect phone.tmp share.tmp "phone_1 == phone_2 &amp;&amp; name_1 &lt; name_2"
  tt&gt; tproject share.tmp share.tab phone_2 inc-
  tt&gt; delete *.tmp
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>References</H3>
  <! BeginSection: 'REFERENCES'>
  <UL>
  This task was written by Bernie Simon.
  </UL>
  <! EndSection:   'REFERENCES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  tselect, tproject, tjoin
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
