.. _tinfo:

tinfo — Display table size information.
=======================================

**Package: nttools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  tinfo -- Display information about a table.
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  tinfo table
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Description</H3>
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
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>table [file name template]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='table' Line='table [file name template]'>
  <DD>A list of tables for which size information is to be produced.
  </DD>
  </DL>
  <DL>
  <DT><B>(ttout = yes) [boolean]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(ttout = yes) [boolean]'>
  <DD>Display information on the terminal screen as it is being placed into
  parameters?  Setting 'ttout = no' will cause information to be placed
  only into task parameters.
  </DD>
  </DL>
  <DL>
  <DT><B>(nrows) [integer]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(nrows) [integer]'>
  <DD>The number of rows written to the table.
  This and all subsequent parameters are output task parameters;
  that is, they are written by the 'tinfo' task.
  </DD>
  </DL>
  <DL>
  <DT><B>(ncols) [integer]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(ncols) [integer]'>
  <DD>The number of columns in the table.
  </DD>
  </DL>
  <DL>
  <DT><B>(npar) [integer]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(npar) [integer]'>
  <DD>The number of header parameters in the table.
  </DD>
  </DL>
  <DL>
  <DT><B>(rowlen) [real]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(rowlen) [real]'>
  <DD>For a row-ordered table,
  'rowlen' is the amount of space allocated for each row in the table file.
  The unit of 'rowlen' is the size of a single-precision real number.
  <P>
  This is only relevant for row-ordered STSDAS format tables.
  </DD>
  </DL>
  <DL>
  <DT><B>(rowused) [real]</B></DT>
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
  <DT><B>(allrows) [integer]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(allrows) [integer]'>
  <DD>The number of allocated rows.
  This is relevant only for column-ordered STSDAS format tables.
  </DD>
  </DL>
  <DL>
  <DT><B>(maxpar) [integer]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(maxpar) [integer]'>
  <DD>The space allocated for header parameters.
  </DD>
  </DL>
  <DL>
  <DT><B>(maxcols) [integer]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(maxcols) [integer]'>
  <DD>The space allocated for column descriptors.
  </DD>
  </DL>
  <DL>
  <DT><B>(tbltype) [string]</B></DT>
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
  <DT><B>(subtype) [string]</B></DT>
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
  <DT><B>(tblversion) [integer]</B></DT>
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
  <H3>Examples</H3>
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
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>References</H3>
  <! BeginSection: 'REFERENCES'>
  <UL>
  This task was written by Phil Hodge.
  </UL>
  <! EndSection:   'REFERENCES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  tlcol
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
