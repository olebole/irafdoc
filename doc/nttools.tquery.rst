tquery — Create a new table from selected rows and columns in a table.
======================================================================

**Package: nttools**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>tquery (Jan1999)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>tables</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>tquery (Jan1999)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>tquery</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  tquery -- Create a new table from selected rows and columns of an old table.
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  tquery intable outtable expr columns sort
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task combines the functions of the tasks 'tselect', 'tproject', and
  'tsort' to create a more powerful task that can produce a sorted table of
  user-selected rows and columns.
  It can be used whenever you want to do more than one of these operations
  without creating intermediate tables.  This task creates a new table
  containing a subset of the rows and columns in an old table.  The rows in the
  new table can be sorted on any column or combination of columns.  The select,
  project, and sort operations are controlled by the parameters 'expr',
  'columns', and 'sort',
  respectively.  If the value of any of these parameters is a null or
  blank string, the corresponding operation is not performed.  Otherwise, the rows
  are selected whenever the row meets the conditions defined by 'expr';
  columns are
  selected by the 'columns' parameter, and rows are
  sorted on the columns named in 'sort'.  The hidden parameter 'uniq' is used
  to eliminate duplicate rows from the output table.  The hidden parameter
  'ascend' sorts the table in ascending order, and the parameter 'casesens'
  specifies whether sort conditions are to be case sensitive.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_intable">intable [file name template]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='intable' Line='intable [file name template]'>
  <DD>Table(s) from which rows are copied. If input is redirected, this
  parameter will ignored and input will be read from STDIN instead.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_outtable">outtable [file name template]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outtable' Line='outtable [file name template]'>
  <DD>The new table(s) containing the copied rows.
  The number of output tables must equal the number of input tables.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_expr">expr [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='expr' Line='expr [string]'>
  <DD>The boolean expression which determines which rows are copied to the new
  table.  The expression may be placed in a file and the name of the file
  preceeded by a <TT>'@'</TT> can be given in its place.  If the expression is null
  or blank, all rows are selected.  The syntax and method used to define
  this boolean expression is explained in detail in the help file for the
  'tselect' task (type "<TT>help tselect</TT>" for more information).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_columns">columns [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='columns' Line='columns [string]'>
  <DD>Column template describing the columns that are to be selected
  from the old table. A column template consists of a list
  of column names, which can include wildcard characters.
  The column names, or patterns, are separated by commas or white space.
  The list of columns can be placed in a file and then
  the name of that file passed to 'columns' (preceded by
  the "<TT>@</TT>" character).  If the first non-white character in the template
  is the negation character (either "<TT>~</TT>" or "<TT>!</TT>"),
  the new table will contain those columns
  that do NOT match the column template. If the column template
  is null or blank, all columns will be selected.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_sort">sort [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sort' Line='sort [string]'>
  <DD>Column template describing the columns to be sorted.  The
  first column name is the primary sort key with subsequent columns
  used to break ties.  If this parameter
  is null or blank, no sort will be done.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(uniq = no) [boolean]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(uniq = no) [boolean]'>
  <DD>Make sure all rows are unique in a table?
  <P>
  If 'unique' is set to "<TT>yes</TT>", only one of each set of duplicate rows is included
  in the output table.  All columns in the output table must be identical for
  the row to be removed.  String comparisons are case sensitive.  Care should
  be used in setting this option for large tables, as it significantly increases
  the running time.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(ascend = yes) [boolean]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(ascend = yes) [boolean]'>
  <DD>Should sorts be performed in ascending order?
  <P>
  If 'ascend = yes', the table is sorted in ascending order, with the first
  row containing the smallest value of the sorted column.  Otherwise, the table
  is sorted in descending order, with the largest value first.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(casesens = yes) [boolean]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(casesens = yes) [boolean]'>
  <DD>Are sort operations case sensitive?
  <P>
  If 'casesens = yes', sorts on character columns are case sensitive, with upper
  case letters preceding lower case.  Otherwise, the sort is not case
  sensitive.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Extract all binary stars from a catalog; write their names, magnitudes,
  and colors to a new table, sorted on magnitude:
  <P>
  <PRE>
  tt&gt; tquery starcat.tab binary.tab binary name,mag,color mag
  </PRE>
  <P>
  2. Remove duplicate rows from a set of tables. Otherwise, leave the tables
  unchanged. Using file name editing (i.e., the "<TT>%</TT>" characters to delineate
  old strings and new strings), change the file name extensions from "<TT>.tab</TT>"
  to "<TT>.tbl</TT>".
  <P>
  <PRE>
  tt&gt; tquery *.tab *.%tab%tbl% "" "" "" uniq+
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  Column names must be set off from operators by blanks in the expression so
  that they can be correctly parsed by the expression evaluator.
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
  tsort, tselect, tproject
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>