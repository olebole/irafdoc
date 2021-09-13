tproduct — Form the Cartesian product of two tables.
====================================================

**Package: nttools**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>tproduct (Dec90)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>tables</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>tproduct (Dec90)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>tproduct</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  tproduct -- Form the Cartesian product of two tables.
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  tproduct intable1 intable2 outtable
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
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
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_intable1">intable1 [file name]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='intable1' Line='intable1 [file name]'>
  <DD>First input table.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_intable2">intable2 [file name]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='intable2' Line='intable2 [file name]'>
  <DD>Second input table.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_outtable">outtable [file name]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outtable' Line='outtable [file name]'>
  <DD>Output table containing the possible Cartesian products.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
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
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_references">REFERENCES</A></H2>
  <! BeginSection: 'REFERENCES'>
  <UL>
  This task was written by Bernie Simon.
  </UL>
  <! EndSection:   'REFERENCES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  tselect, tproject, tjoin
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>