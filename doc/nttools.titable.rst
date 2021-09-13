titable — Insert 2-D tables into rows of a 3-D table.
=====================================================

**Package: nttools**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>titable (Mar97)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>tables</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>titable (Mar97)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>titable</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  titable -- Inserts 2-D tables into rows of a 3-D table.
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  titable intable outtable
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task performs the inverse operation of task txtable: it inserts one or 
  more 2-D tables into rows of a 3-D table  The input may be a filename 
  template, including wildcard characters, or the name of a file (preceded by 
  an @ sign) containing table names.  The output is a single 3-D table name.
  If the output table exists, insertion will be done in place. If the output 
  table does not exist, it will be created. The input and output tables must 
  not be the same.
  <P>
  This task supports row/column selectors in the input table names. These
  may be used to select subsets of both rows and columns from the input table.
  If no selectors are used, all columns and rows will be processed, 
  Type 'help selectors' to see a description of the selector syntax. 
  <P>
  When creating a new output table, the information describing its columns
  can be taken from two sources. If parameter 'template' has the name of an
  existing 3-D table, the column descriptions, including maximum array sizes,
  will be taken from that table. If 'template' has an invalid or null ("<TT></TT>")
  value, the column-defining information will be take from the first table 
  in the input list, where its number of rows will define the maximum array
  size allowed in the table being created. Column selectors are allowed in
  the template table.
  <P>
  NOTE: Both the output and template table names must always be supplied 
  complete, including their extension. Otherwise the task may get confused 
  on the existence of an already existing table.
  <P>
  Insertion is performed by first verifying if column names in both input
  and output tables match. If a match is found, values taken from that column
  and all selected rows from the input table will be stored as a 1-dimensional 
  array in a single cell in the corresponding column in the output 3-D table. 
  The row in this table where the insertion takes place is selected by the 
  "<TT>row</TT>" task parameter. It points to the row where the first table in the input 
  list will be inserted, subsequent tables in the list will be inserted into 
  subsequent rows. This mechanism is superseded if the "<TT>row</TT>" parameter is set 
  to INDEF or a negative value, and the keyword "<TT>ORIG_ROW</TT>" is found in the 
  header of the input table. This keyword is created by task txtable and its 
  value supersedes the row counter in the task.
  <P>
  If the maximum array size in a target column in the output 3-D table is
  larger than the number of selected input rows, the array will be filled 
  up starting from its first element, and the empty elements at the end will 
  be set to INDEF (or "<TT></TT>" if it is a character string column). If the maximum 
  array size is smaller than the number of selected rows, insertion begins by
  the first selected row up to the maximum allowable size, the remaining rows
  being ignored.
  <P>
  This task correctly handles scalars stored in the input table header
  by task txtable. Since the selector mechanism does not work with these
  scalars, the task will always insert them into the output table, provided
  there is a match in column names.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_intable">intable [file name list/template]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='intable' Line='intable [file name list/template]'>
  <DD>A list of one or more tables to be inserted. Row/column selectors are supported.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_outtable">outtable [table name]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outtable' Line='outtable [table name]'>
  <DD>Name of 3-D output table, including extension. No support exists for 
  "<TT>STDOUT</TT>" (ASCII output).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(template = "<TT></TT>") [table name]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(template = "") [table name]'>
  <DD>Name of 3-D table to be used as template when creating a new output table.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(row = INDEF) [int]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(row = INDEF) [int]'>
  <DD>Row where insertion begins. If set to INDEF or a negative value, the row
  number will be looked for in the input table header.
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
  Insert columns named FLUX and WAVELENGTH from input tables into a 3-D table:
  <P>
  <PRE>
  cl&gt; titable "itable*.tab[c:FLUX,WAVELENGTH]" otable.tab
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  The output and template table names must be supplied in full, including 
  the extension (e.g. "<TT>.tab</TT>"). If the output table name is not typed in full, 
  the task will create a new table in place of the existing one, with only the 
  rows actually inserted. This behavior relates to the way the underlying 
  "<TT>access</TT>" routine in IRAF's fio library works.
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
  txtable, selectors
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>