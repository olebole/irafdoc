taextract — Copy an array entry to a column of scalars in another table.
========================================================================

**Package: nttools**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>taextract (Jan98)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>tables</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>taextract (Jan98)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>taextract</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  taextract -- Copy an array entry from one table
  to a column of scalars in another.
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  taextract intable outtable row column
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task extracts one entry (presumably an array of values)
  at a specified row and column
  and writes it as a column of scalar values to another table.
  If the output table exists it will be written to in-place;
  otherwise, it will be created.
  <P>
  By default, the same column name is used in both tables.
  If the output table and column already exist,
  the data in that column will be overwritten;
  otherwise, the column will be created.
  If the array size for the specified column in the input table is N,
  then the values will be written to rows 1 through N of the output table.
  If the output column already exists,
  and the output table contains more than N rows,
  then rows N+1 through the last will be set to INDEF for this column.
  <P>
  The input row number is written to the header of the output table
  using keyword ORIG_ROW.
  This allows 'tainsert' to put the data back where 'taextract' got them from.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_intable">intable [file name]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='intable' Line='intable [file name]'>
  <DD>Name of the input table containing a column with array entries.
  It is not an error for the array length to be one.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_outtable">outtable [file name]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outtable' Line='outtable [file name]'>
  <DD>Name of the output table.
  If this table doesn't exist it will be created.
  If the table does exist the column will either be created or overwritten.
  The input and output tables may not be the same,
  and they may not be in the same file if FITS format is used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_row">row [integer, min=1, max=INDEF]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='row' Line='row [integer, min=1, max=INDEF]'>
  <DD>This is the row number in the input table.
  In the output table there will be as many rows
  as there are elements in the input table entry for 'column'.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_column">column [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='column' Line='column [string]'>
  <DD>Column name.
  This is used to find the column in the input table,
  and by default the same name is used to create
  (or find, if it already exists)
  the column in the output table.
  See the description for 'outcolumn'.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_outcolumn">outcolumn = "<TT></TT>" [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outcolumn' Line='outcolumn = "" [string]'>
  <DD>If 'outcolumn' is specified,
  that name will be used for the output table;
  otherwise, 'column' will be used for both input and output tables.
  This provides an easier way to change the name of the output column
  than by running 'tchcol' after running 'taextract'.
  Note that if 'outcolumn' is specified,
  it is used not only for finding the column in the output table
  but also for creating the column if it wasn't found.
  The 'datatype', 'colunits', and 'colfmt' parameters, by contrast,
  are only used when creating a new column.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(datatype = "<TT></TT>") [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(datatype = "") [string]'>
  <DD>When creating a new column in the output table,
  the default is to use the same data type as the column in the input table.
  However, if 'datatype' is specified (i.e. not null or blank),
  this will be used as the data type when creating the new column.
  For numeric and boolean columns, only the first character is used:
  "<TT>r</TT>" and "<TT>d</TT>" for single and double precision floating point,
  "<TT>s</TT>" and "<TT>i</TT>" for short integer and integer,
  "<TT>b</TT>" for boolean.
  For a character string of maximum length 12 (for example), use "<TT>ch*12</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(colunits = "<TT></TT>") [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(colunits = "") [string]'>
  <DD>When creating a new column in the output table,
  the units will be set to 'colunits' if it has been specified;
  otherwise, the units will be copied from the column in the input table.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(colfmt = "<TT></TT>") [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(colfmt = "") [string]'>
  <DD>When creating a new column in the output table,
  the print format will be set to 'colfmt' if it has been specified;
  otherwise, the print format will be copied from the column in the input table.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Extract the array from row 5, column "<TT>polar</TT>", from table "<TT>array.tab</TT>",
  putting the values in column "<TT>polar</TT>" of table "<TT>scalar.tab</TT>".
  <P>
  <PRE>
  at&gt; taextract array.tab scalar.tab 5 polar
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
  tainsert
  <P>
  Type "<TT>help ttools opt=sysdoc</TT>" for a higher-level description of the 'ttools'
  package.
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>