txtable — Extract 2-D tables from rows of 3-D tables.
=====================================================

**Package: nttools**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>txtable (Jan97)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>tables</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>txtable (Jan97)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>txtable</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  txtable -- Extract rows from a 3-D table into separate 2-D tables.
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  txtable intable outtable
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task extracts one or more rows from a 3-D table and writes each row
  as a 2-D table. The input may be a filename template, including 
  wildcard characters, or the name of a file (preceded by an @ sign) containing 
  table names.  The output may be either a directory specification or a list 
  of table names. If the output is a list of tables then there must be the same 
  number of names in the input and output lists, and the names are taken in 
  pairs, one from input and one from output. The input and output tables must 
  not be the same.
  <P>
  This task supports row/column selectors in the input table name. These
  may be used to select subsets of both rows and columns from the input table.
  If no selectors are used, all columns will be extracted, and the number
  of output tables will be the number of rows in the input table.
  Type 'help selectors' to see a description of the selector syntax. 
  <P>
  Since one input table may generate several output tables, the task adopts
  the following naming scheme for these output tables: their names are
  built by appending a suffix to the name given in parameter "<TT>outtable</TT>".
  The suffix has the form "<TT>_rXXXX</TT>", where XXXX stands for the row number 
  in the input table. The suffix is appended before the file name extension.
  The task recognizes as valid table name extensions the values "<TT>.tab</TT>",
  "<TT>.fits</TT>" and "<TT>.fit</TT>". Any other extension is assumed to be part of the root
  file name. If only one row is extracted, or in case of ASCII output, no 
  suffixing takes place.
  <P>
  NOTE: Be careful when using a wildcard for the extension.
  If you have the files "<TT>table.tab</TT>" and "<TT>table.lis</TT>" in the current directory,
  for example, then the command "<TT>txtable tab* test/</TT>" would expand both files 
  to the subdirectory "<TT>test</TT>".
  <P>
  There are two forms of handling scalar columns in the input table. If
  task parameter "<TT>compact</TT>" is set to 'no', the corresponding column in the
  output table will have the scalar value in its first row, and all other
  rows will be filled with INDEF. If parameter "<TT>compact</TT>" is set to 'yes',
  scalar columns will be written into the header as a set of header keywords.
  These keywords can be used later by task 'titable' to re-insert the
  scalars as cell elements of a 3-D table.
  <P>
  The task does not propagate array dimensionality when extracting arrays
  into columns in the output table. If dimensionality information exists
  in the 3-D table, that information is lost, that is, the table cell from
  the input table is written as a structureless, plain table column.
  <P>
  The input row number is written to the header of the output table in
  keyword ORIG_ROW. This allows 'titable' to put the data back where 
  'txtable' got them from.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_intable">intable [file name list/template]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='intable' Line='intable [file name list/template]'>
  <DD>A list of one or more tables to be expanded. Row/column selectors are supported.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_outtable">outtable [file name template]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outtable' Line='outtable [file name template]'>
  <DD>Either a directory name or a list of output table names. The standard
  value "<TT>STDOUT</TT>" generates ASCII output that can be redirected to a file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(compact = yes) [boolean]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(compact = yes) [boolean]'>
  <DD>Write scalars as header keywords ?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(verbose = yes) [boolean]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(verbose = yes) [boolean]'>
  <DD>Display names of input and output tables as files are processed ?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  Extract columns named FLUX and WAVELENGTH from rows 11 to 13 of a 3-D table:
  <P>
  <PRE>
  cl&gt; txtable "table.tab[c:FLUX,WAVELENGTH][r:row=(11:13)]" tableout
  </PRE>
  <P>
  This will generate three tables named "<TT>tableout_r0011</TT>", "<TT>tableout_r0012</TT>"
  and "<TT>tableout_r0013</TT>".
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
  This task was written by I. Busko.
  </UL>
  <! EndSection:   'REFERENCES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  titable, selectors
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>