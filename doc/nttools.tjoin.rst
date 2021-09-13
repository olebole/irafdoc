tjoin — Perform a relational join of two tables.
================================================

**Package: nttools**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>tjoin (Apr99)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>tables</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>tjoin (Apr99)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>tjoin</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  tjoin -- Combine two tables based on equal values in common columns
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  tjoin intable1 intable2 outtable column1 column2
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task combines two tables into a new table on the basis of one or
  more common columns.  Two rows from the input tables are combined to
  form a row of the output table whenever the values in the common
  columns are equal. If a row in one of the input tables matches several
  rows in the other input table, all combinations of the rows are placed
  in the output table. Null table elements are never matched.  Tables
  can be joined on row number as well as on column by setting the column
  name to "<TT>row</TT>".
  <P>
  This task has three hidden parameters, 'extrarows', 'tolerance', and
  'casesens'.  By default, if a row in one of the input tables does not
  match any row in the other input table, it is not placed in the output
  table.  However, if the parameter 'extrarows' is set to 'first', rows
  in the first table that are unmatched are added to the output table
  and if 'extrarows' is set to 'both', unmatched rows from both input
  tables are added to the output table.
  <P>
  The task parameter 'tolerance' is a comma separated list of
  values. The number of values should either equal to the number of join
  columns or one. If only one value is supplied and there are more than
  one join column, the value is used for all columns.  If the difference
  between two column values is less than or equal to the corresponding
  value of 'tolerance', the values are considered equal and their
  respective rows are placed in the output table.
  <P>
  If 'casesens = no', the case of a string is ignored when testing for
  equality. 'tolerance' must be set to zero when comparing string or
  boolean columns.
  <P>
  If a value of 'tolerance' is nonzero, the output table will contain the
  corresponding join columns from both tables. If a value of
  'tolerance' is zero, the output table will contain a single join column,
  as both values are identical. If a column name in the first input
  table is the same as a column name in the second input table, this
  task tries to create a unique name by appending "<TT>_1</TT>" to the first name
  and "<TT>_2</TT>" to the second name. If the task cannot create a unique name
  in this way, it stops with an error.
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
  <DD>Output table.  This is the join of the two input tables.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_column1">column1 [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='column1' Line='column1 [string]'>
  <DD>Names of the common columns in the first table. If there is more than
  one column name, the names should be separated by commas. If a column
  name is "<TT>row</TT>", the join is done on row number instead of the value of
  a column. This only works if there is not column named "<TT>row</TT>" in the
  table.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_column2">column2 [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='column2' Line='column2 [string]'>
  <DD>Comma separated list of names of the common columns in the second
  table. The number of names must match the number of names in column1.
  The name may be "<TT>row</TT>", in which case the join is done on row number.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(extrarows = "<TT>neither</TT>") [string, allowed values: neither|first|both]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(extrarows = "neither") [string, allowed values: neither|first|both]'>
  <DD>This parameter controls whether unmatched rows are added to the output 
  table. If it is set to 'neither', unmatched rows are not added. If it
  is set to 'first', unmatched rows from the first table are added. If
  it is set to 'both', unmatched rows from both tables are added. When
  unmatched rows are added to the output table columns in the output
  table derived from the other table have their values left undefined.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(tolerance = "<TT>0.0</TT>") [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(tolerance = "0.0") [string]'>
  <DD>Tolerance used in testing for equality between common columns. The
  values must be greater than or equal to zero. If there is more than
  one common column, this parameter may be a comma separated list of
  values. In this case, the number of tolerance values must equal the
  number of common columns or be one. If there is only one tolerance
  value, the same value is used for all columns.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(casesens = yes) [boolean]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(casesens = yes) [boolean]'>
  <DD>Is case important in testing equality of strings?
  If set to "<TT>yes</TT>", the test for equality is case sensitive.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Combine a table of star positions and a table of star magnitudes to create
  a star catalog. The star name is not case sensitive:
  <P>
  <PRE>
  tt&gt; tjoin starpos.tab starmag.tab starcat.tab name name case-
  </PRE>
  <P>
  2. Create a table of all spectral lines that match a set of reference
  wavelengths within 10 angstroms:
  <P>
  <PRE>
  tt&gt; tjoin spectrum.tab reference.tab lines.tab WAVE WAVE tol=10.
  </PRE>
  <P>
  3. Combine a phone list with an address list where the name is stored
  in two columns, "<TT>last</TT>" and "<TT>first</TT>". 
  <P>
  <PRE>
  tt&gt; tjoin phone.tab address.tab output.tab LAST,FIRST LAST,FIRST
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
  tselect, tproject, tproduct
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>