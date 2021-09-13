.. _tdiffer:

tdiffer — Form a table which is the difference of two tables.
=============================================================

**Package: nttools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  tdiffer -- Create a new table which is the difference of two tables.
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  tdiffer intable1 intable2 outtable colnam1 colnam2
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task creates an output table containing all the rows of the first table
  which do not match the rows in the second table.
  The first, second, and output tables are given by the task
  parameters 'intable1', 'intable2', and 'outtable' respectively.
  The match is done on the columns specified by the task parameters 'colnam1'
  and 'colnam2'.
  Other columns are ignored.
  If the two tables are disjoint, the output table will be a copy of
  the first table, except the rows will be sorted.
  If the first table is a subset of the second, the output table will be empty.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>intable1 [file name]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='intable1' Line='intable1 [file name]'>
  <DD>The name of the first input table.
  </DD>
  </DL>
  <DL>
  <DT><B>intable2 [file name]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='intable2' Line='intable2 [file name]'>
  <DD>The name of the second input table.
  </DD>
  </DL>
  <DL>
  <DT><B>outtable [file name]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outtable' Line='outtable [file name]'>
  <DD>The name of the output table.  The output table has the same header parameters
  and column names as the first table. 
  </DD>
  </DL>
  <DL>
  <DT><B>colnam1 [string]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='colnam1' Line='colnam1 [string]'>
  <DD>The column names in the first table used in the match.  If more than one
  column is used, columns from the first and second
  table are associated with each other based on their position in the list
  and not on their names, i.e., the first column name in 'colnam1' is matched
  to the first column name passed to 'colnam2', regardless of whether the
  names match.
  </DD>
  </DL>
  <DL>
  <DT><B>colnam2 [string]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='colnam2' Line='colnam2 [string]'>
  <DD>The column names in the second table used in the match.  The same number of
  column names must be passed to both the 'colnam1' and 'colnam2' parameters.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. There are two tables, "<TT>targets.tab</TT>", containing a list of targets
  for observation, and "<TT>images.tab</TT>", containing a list of targets which
  have already been observed.  Create a table named "<TT>new.tab</TT>" containing
  those targets which have not previously been observed:
  <P>
  <PRE>
  tt&gt; tdiffer targets.tab images.tab new.tab targetid targetid
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
  tselect
  <P>
  Type "<TT>help tables opt=sys</TT>" for a higher-level description of the 'tables' 
  package.
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
