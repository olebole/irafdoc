tinfo — Display table size information.
=======================================

**Package: nttools**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>tinfo (Jun1999)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>tables</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>tinfo (Jun1999)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>tinfo</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  tinfo -- Display information about a table.
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  tinfo table
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task is used to display information about a table.
  This information includes
  such things as the number of rows and columns.
  The output is written to STDOUT by default.
  The first line of output for each table in the input list is the table
  name preceded by a # sign.
  The values for the last table in the list are also put into parameters
  for the 'tinfo' task so that other tasks in a script may use the values.
  <P>
  The parameters 'nrows', 'ncols', 'npar', 'rowlen', 'rowused', 'allrows',
  'maxpar', 'maxcols', 'tbltype', 'subtype' and 'tblversion'
  are output parameters.
  Since they are set rather than read by 'tinfo',
  any value assigned by the user will be overwritten.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_table">table [file name template]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='table' Line='table [file name template]'>
  <DD>A list of tables for which size information is to be produced.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(ttout = yes) [boolean]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(ttout = yes) [boolean]'>
  <DD>Display information on the terminal screen as it is being placed into
  parameters?  Setting 'ttout = no' will cause information to be placed
  only into task parameters.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(nrows) [integer]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(nrows) [integer]'>
  <DD>The number of rows written to the table.
  This and all subsequent parameters are output task parameters;
  that is, they are written by the 'tinfo' task.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(ncols) [integer]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(ncols) [integer]'>
  <DD>The number of columns in the table.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(npar) [integer]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(npar) [integer]'>
  <DD>The number of header parameters in the table.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(rowlen) [real]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(rowlen) [real]'>
  <DD>For a row-ordered table,
  'rowlen' is the amount of space allocated for each row in the table file.
  The unit of 'rowlen' is the size of a single-precision real number.
  <P>
  This is only relevant for row-ordered STSDAS format tables.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(rowused) [real]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(rowused) [real]'>
  <DD>'rowused' is the amount of the row length ('rowlen')
  that has actually been used
  by the columns that have been defined,
  in units of the size of a real number.
  For example, if a table contains three columns
  with data types integer, real and double precision,
  then 'rowused' would be four.
  If the table contains only one column of data type short,
  then 'rowused' would be 0.5.
  <P>
  This is only relevant for row-ordered STSDAS format tables.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(allrows) [integer]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(allrows) [integer]'>
  <DD>The number of allocated rows.
  This is relevant only for column-ordered STSDAS format tables.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(maxpar) [integer]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(maxpar) [integer]'>
  <DD>The space allocated for header parameters.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(maxcols) [integer]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(maxcols) [integer]'>
  <DD>The space allocated for column descriptors.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(tbltype) [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(tbltype) [string]'>
  <DD>The table type, currently either "<TT>stsdas</TT>", "<TT>fits</TT>" or "<TT>text</TT>".
  "<TT>stsdas</TT>" is a machine dependent binary format,
  the default .tab format.
  "<TT>fits</TT>" means that the table is a TABLE or BINTABLE extension
  in a FITS file.
  "<TT>text</TT>" is an ASCII file in tabular format.
  See also 'subtype'.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(subtype) [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(subtype) [string]'>
  <DD>For FITS tables the subtype can be either
  "<TT>ascii</TT>" (a TABLE extension) or "<TT>binary</TT>" (a BINTABLE extension).
  For text tables the subtype can be either
  "<TT>simple</TT>" or "<TT>explicit column definitions</TT>".
  The latter subtype means there are column definition lines in the file,
  in the format:  "<TT>#c column_name datatype print_format units</TT>".
  A simple text table has column names c1, c2, etc., and no units.
  For STSDAS format tables
  the subtype will be either "<TT>row ordered</TT>" or "<TT>column ordered</TT>",
  which indicates the way the elements are stored in the table file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(tblversion) [integer]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(tblversion) [integer]'>
  <DD>The version code is an integer that identifies the version of
  the tables package that created or last modified the table.
  For STSDAS tables, the version code is stored in the table file;
  for other formats this parameter is just
  the current tables version code number.
  This number is zero for 'stsdas' and 'tables' versions 1.2.3 and earlier,
  the number is one for versions 1.3 through 1.3.3,
  the number is two beginning 1995 March 6,
  and the number is three beginning 1998 April 14.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Get size information about the file 'm87pol.tab',
  but do not print the information to STDOUT,
  just put the values into parameters.
  <P>
  <PRE>
  	tt&gt; tinfo m87pol ttout=no
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
  tlcol
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>