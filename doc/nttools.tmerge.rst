tmerge — Either merge or append tables.
=======================================

**Package: nttools**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>tmerge (Jun1999)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>tables</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>tmerge (Jun1999)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>tmerge</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  tmerge -- Merge two tables, or append one to the other.
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  tmerge intable outtable option
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task is used to either merge or append tables,
  depending on the option selected by the 'option' parameter.
  The data type of each column is defined by
  the first table in the input list containing that column.
  If subsequent tables use the same column name,
  then data are converted to the type defined by the first table.
  Problems may occur when numerical data are written to
  a boolean column or a narrow character column.
  <P>
  The "<TT>merge</TT>" option is normally used for tables containing few,
  if any, common columns.
  When the user selects "<TT>merge</TT>",
  an output table is created containing as many columns
  as there are unique column names in all the input tables.
  (But see the description of the 'allcols' parameter.)
  The output table will have as many rows as the largest
  number of rows in the input tables.
  The input tables are read in order,
  with all values being placed into the output table.
  If different input tables have the same column names
  then the first values put into the output table
  will be overwritten by the later table values.
  For example, if the two input tables both have the column name "<TT>X_VAL</TT>",
  then for each row number,
  the values written to the output table
  will be taken from the second input table.
  See below regarding text tables.
  <P>
  On the other hand, if the "<TT>append</TT>" option is selected, all rows of
  the first input table are written to the output table, followed by all
  rows of the second table, and so on, until all input tables are written
  to the output table.
  The total number of output rows will be the sum
  of the numbers of rows in the input tables.
  Columns with the same name in different
  input tables will be written into the same output column, but no data
  will be overwritten because they are put into different rows.
  The "<TT>append</TT>" option would normally be used for tables that have all
  the same columns.
  <P>
  An input table may have no rows.
  Such a table may be used as the first input table
  to control the order and definitions of columns in the output table.
  <P>
  Header parameters are appended,
  and parameters with the same keyword name
  in different input tables are overwritten in the output file,
  except for history and comment keywords.
  <P>
  Care must be taken with text tables.
  It is very likely that you would want
  'allcols = yes' if 'option = merge' and
  'allcols = no' if 'option = append'.
  See the description of the 'allcols' parameter for details.
  If the output table is a text file,
  the line length may not be longer than 4095 characters,
  which is a limitation for any text table.
  <P>
  Column units are not checked.
  If columns with the same name have different units
  in two different input tables,
  the merged (or appended) data are likely to have mixed units.
  In addition, the column definition is taken from the first input table,
  but some and perhaps all of the data would come from the second input table,
  so the units in the output column definition would not be correct
  for those data.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_intable">intable [file name template]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='intable' Line='intable [file name template]'>
  <DD>Names of the tables to be merged or appended.  This parameter will take
  either a file name template describing several input tables, and may include
  wildcard characters, or it will take the name of a list file preceded by the
  "<TT>@</TT>" character; in the latter case the list file contains a list of file names
  with each file name on a separate line.  Wildcard characters should not be
  used for file name extensions because files other than tables will be
  processed, causing the program to crash.  For example, if the directory
  contains files "<TT>table.tab</TT>" and "<TT>table.lis</TT>", the command "<TT>tmerge tab*</TT>" would
  open both files.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_outtable">outtable [file name]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outtable' Line='outtable [file name]'>
  <DD>The name of the output table.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_option">option = "<TT>merge</TT>" [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='option' Line='option = "merge" [string]'>
  <DD>allowed values:  merge | append
  <P>
  Either merge the columns in each row of each input table--overwriting
  previous values--or append files to each other.
  See also 'allcols' below.
  (These options are discussed in greater detail in the DESCRIPTION section.)
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(allcols = yes) [boolean]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(allcols = yes) [boolean]'>
  <DD>Define output table columns using columns from
  all input tables?
  <P>
  If 'allcols = no', the output table will contain
  only those columns defined in the first input table.
  If 'allcols = yes', the output table will contain
  all columns from all input tables.
  If 'option = merge', then it is likely that 'allcols' should be set to yes.
  <P>
  For input tables that are simple text tables
  (i.e. that do not contain explicit column definitions),
  the 'allcols' parameter serves an additional function.
  When 'allcols = yes' the name of each column
  in a simple text table is changed
  to be "<TT>c</TT>" followed by the column number in the output table.
  This is intended to make the column names unique
  in order to allow merging text tables
  without having the columns overwrite previously written columns.
  Since the column names in simple text tables are just c1, c2, etc.,
  columns would overwrite previously written columns in the output
  if the names were not modified.
  If all input tables are simple text tables,
  and the output is also a text table,
  the new names will be discarded,
  so the net effect of this scheme is just to preserve all input data.
  If the output is a binary table, however,
  the modified column names will be retained.
  If the modified column names turn out not to be unique,
  a warning message will be printed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(tbltype = "<TT>default</TT>") [string, allowed values:  default | row | </A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(tbltype = "default") [string, allowed values:  default | row | '>
  <DD>column | text]
  <P>
  This parameter specifies the table type.
  Setting 'tbltype' to "<TT>row</TT>" or "<TT>column</TT>" results in an stsdas binary table,
  the contents of which may be either row ordered or column ordered;
  row order is recommended.
  You can also specify that the output be a text table.
  The default ('tbltype = "<TT>default</TT>"') means that the type of the output table
  will be taken from the first input table.
  <P>
  If the extension of the output file name is "<TT>.fits</TT>" or "<TT>.??f</TT>",
  the table to be created will be a BINTABLE extension in a FITS file,
  regardless of how 'tbltype' is set.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(allrows = 100) [integer, min=1, max=INDEF]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(allrows = 100) [integer, min=1, max=INDEF]'>
  <DD>The number of rows to allocate.
  This parameter is only used for column-ordered tables
  (specified by the 'tbltype' parameter).
  The 'allrows' parameter is the minimum number of rows an output
  table will contain.
  If the number of rows required by the input tables
  is greater than 'allrows' then the number of rows in the output table will
  be greater than 'allrows'.
  If 'option = merge', then the total number of rows will be
  the larger of 'allrows' or the number of rows in the largest table.
  If 'option = append', the total rows in the output table will be the larger
  of 'allrows' or the total number of rows in all input tables.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(extracol = 0) [integer, min=0, max=INDEF]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(extracol = 0) [integer, min=0, max=INDEF]'>
  <DD>Extra space to be reserved for columns in the output table.
  <P>
  This parameter is relevant only for a row-ordered table
  (specified by the 'tbltype' parameter).
  The default value of zero is normally appropriate,
  but if you expect to define additional columns in the output table
  at a later time
  then you can allocate the necessary space
  by specifying a value for 'extracol'.
  One unit of space is taken by each single-precision real value,
  integer value, or boolean value.
  A double-precision column requires two units of allocated space,
  and a character-string column takes one unit of space for each four
  characters, or fraction thereof.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <PRE>
  1. Suppose you have the following two tables.
  <P>
  tbl1.tab:
  	one	two	three
  	---	---	-----
  	1	-17	alpha
  	2	-19	beta
  	3	-23	gamma
  <P>
  tbl2.tab:
  	one	three	four
  	---	-----	----
  	27	beta	3.14
  	28	delta	2.72
  <P>
  then the statement
  <P>
  	cl&gt; tmerge tbl1,tbl2 mrg merge
  <P>
  would create the following output table:
  <P>
  mrg.tab:
  	one	two	three	four
  	---	---	-----	----
  	27	-17	beta	3.14
  	28	-19	delta	2.72
  	3	-23	gamma	INDEF
  <P>
  while the statement
  <P>
  	cl&gt; tmerge tbl1,tbl2 app append
  <P>
  would create the following table:
  <P>
  app.tab:
  	one	two	three	four
  	---	---	-----	----
  	1	-17	alpha	INDEF
  	2	-19	beta	INDEF
  	3	-23	gamma	INDEF
  	27	INDEF	beta	3.14
  	28	INDEF	delta	2.72
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
  This task was written by Phil Hodge.
  </UL>
  <! EndSection:   'REFERENCES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  tselect, tproject, and proto.joinlines for text files
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>