tainsert — Copy a column of scalars to an array entry in another table.
=======================================================================

**Package: nttools**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>tainsert (Jan98)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>tables</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>tainsert (Jan98)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>tainsert</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  tainsert -- Copy a column of scalars from one table
  to an array entry in another.
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  tainsert intable outtable row column
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task reads an entire column from one table
  and inserts those values (presumably more than one)
  at a specified row and column in an output table.
  If the output table exists it will be written to in-place;
  otherwise, it will be created.
  <P>
  By default, the same column name is used in both tables.
  If the column does not exist in the output table, the column will be created.
  If the output table and the row and column already exist,
  the array of values at that location will be overwritten.
  The number of elements copied will be the minimum of
  the number of input rows and the output column array size.
  If the number of input rows is larger than the array size,
  a warning message will be printed,
  and the extra rows will be ignored.
  If the number of input rows is smaller than the array size,
  the remaining array elements will be set to INDEF.
  <P>
  If the specified row number is less than one or is INDEF,
  'tainsert' looks for the header keyword ORIG_ROW in the input table.
  ORIG_ROW is written by 'taextract'.
  If that keyword exists, its value is used as the row number.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_intable">intable [file name]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='intable' Line='intable [file name]'>
  <DD>Name of the input table.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_outtable">outtable [file name]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outtable' Line='outtable [file name]'>
  <DD>Name of the output table.
  If this table doesn't exist it will be created.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_row">row = -1 [integer]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='row' Line='row = -1 [integer]'>
  <DD>This is the row number in the output table.
  The default means that 'tainsert' should use
  the value of the header keyword ORIG_ROW.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_column">column [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='column' Line='column [string]'>
  <DD>Column name in the input table and, by default, also in the output table.
  If this column does not exist in the output table, it will be created,
  and the array size will be set to the number of rows in the input table.
  See the descriptions for 'outcolumn' and 'size', however.
  <P>
  It is an error if this column in the input table contains array entries.
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
  The 'size', 'datatype', 'colunits', and 'colfmt' parameters,
  by contrast, are only used when creating a new column.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(size = INDEF) [int]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(size = INDEF) [int]'>
  <DD>When creating a new column in the output table,
  the default is for the array size of that column to be set to
  the number of rows in the input table.
  This may be overridden by specifying a value for 'size'.
  If 'size' is a positive integer, not INDEF,
  this will be used as the array size when creating the new column.
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
  1. Copy the entire column "<TT>polar</TT>" from table "<TT>scalar.tab</TT>",
  and insert the values into row 5, column "<TT>polar</TT>", of table "<TT>array.tab</TT>".
  If "<TT>array.tab</TT>" does not exist it will be created.
  If column "<TT>polar</TT>" does not exist in "<TT>array.tab</TT>",
  that column will be created.
  <P>
  <PRE>
  at&gt; tainsert scalar.tab array.tab 5 polar
  </PRE>
  <P>
  2. Copy the arrays from row 5, columns "<TT>wavelength</TT>" and "<TT>flux</TT>",
  from "<TT>array.tab</TT>" to a temporary table,
  sort them on the wavelength,
  and insert them back where they came from.
  <P>
  <PRE>
  at&gt; taextract array temp 5 wavelength
  at&gt; taextract array temp 5 flux
  at&gt; tsort temp wavelength
  at&gt; tainsert temp array 0 wavelength
  at&gt; tainsert temp array 0 flux
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
  taextract
  <P>
  Type "<TT>help ttools opt=sysdoc</TT>" for a higher-level description of the 'ttools'
  package.
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>