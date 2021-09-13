.. _tchsize:

tchsize — Change allocated sizes of various sections of a table.
================================================================

**Package: nttools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  tchsize -- Change the size of tables.
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  tchsize intable outtable maxpar maxcols rowlen allrows
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task changes the allocated sizes of various portions of a table
  or a list of tables.
  In some cases it is difficult to effectively use this task,
  so caution is advised.
  <P>
  NOTE:  This task should not be used on FITS tables.
  If any input table is of type FITS,
  a message will be printed, and that file will be skipped.
  <P>
  Four integer parameters specify table sizes.
  Passing a value of -1 to any parameter means that the current value
  should not be changed.  A value (such as zero) that is smaller than
  the minimum allowed value for that parameter results in the truncation
  of unused space; for example, if three header parameters have already
  been written to a table then setting 'maxpar=0' gives you a table with
  space for only three header parameters.
  <P>
  The input may be a general filename
  template, including wildcard characters or the name of a list file (preceded
  by an "<TT>@</TT>" sign) containing table names.  The output may be null, a directory
  specification, or a list of table names.  If the output is a list of tables
  then there must be the same number of names in the input and output lists,
  and the names are taken in pairs, one from input and one from output.
  A null string for the output is equivalent to specifying the same names
  for the input and output tables.
  <P>
  NOTE: Be careful when using a wildcard for the extension.
  If you have the files 'table.tab' and 'table.lis' in the current directory,
  for example, then "<TT>tchsize tab* test/</TT>" would crash when trying to open
  'table.lis' as a table.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>intable [file name template]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='intable' Line='intable [file name template]'>
  <DD>A list of one or more tables whose sizes are to be changed.
  </DD>
  </DL>
  <DL>
  <DT><B>outtable = "<TT></TT>" [file name template]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outtable' Line='outtable = "" [file name template]'>
  <DD>Either a null string, a directory name, or a list of output table names.
  </DD>
  </DL>
  <DL>
  <DT><B>maxpar = -1 [integer]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maxpar' Line='maxpar = -1 [integer]'>
  <DD>The number of records to allocate for header (i.e., user) parameters.
  <P>
  Use 'maxpar=-1' if no change is to be made; set 'maxpar=0' to 
  truncate unused space.
  </DD>
  </DL>
  <DL>
  <DT><B>maxcols = -1 [integer]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maxcols' Line='maxcols = -1 [integer]'>
  <DD>The amount of space to allocate for column descriptors.  There must be
  at least one for each column that is defined or is to be defined.
  For a column-ordered table 'maxcols' actually determines the maximum
  number of columns that may be defined (without having to rewrite the
  table).  For a row-ordered table, however, you must also specify an
  appropriate value for 'rowlen'; you may want to use the 'tinfo' task
  to get the
  current row length before using this task.
  <P>
  Set 'maxcols=-1' if no change is to be made; set 'maxcols=0' 
  to truncate unused space.
  </DD>
  </DL>
  <DL>
  <DT><B>rowlen = -1 [integer]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rowlen' Line='rowlen = -1 [integer]'>
  <DD>The row length; this is only relevant for a row-ordered table.
  The unit of length is the amount of memory used to store 
  a real number; so a double-precision column
  takes two units, and a character*24 column takes six units (assuming
  that a real
  is four bytes).
  The number of columns that may be defined is limited both by the
  space allocated for column descriptors and by the row length.
  <P>
  Set 'rowlen=-1' if no change is to be made; set 'rowlen=0' 
  to truncate unused space.
  </DD>
  </DL>
  <DL>
  <DT><B>allrows = -1 [integer]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='allrows' Line='allrows = -1 [integer]'>
  <DD>The number of rows to allocate; this is only relevant for a column-ordered
  table.
  <P>
  Set 'allrows=-1' if no change is to be made; set 'allrows=0' to truncate
  unused space.
  </DD>
  </DL>
  <DL>
  <DT><B>(verbose = yes) [boolean]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(verbose = yes) [boolean]'>
  <DD>Display the names of the input and output tables for each table that is
  processed?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Truncate (in-place) all unused space in a single table:
  <P>
  <PRE>
  	tt&gt; tchsize table "" 0 0 0 0
  		or
  	tt&gt; tchsize table table 0 0 0 0
  </PRE>
  <P>
  2. Set the allocated space for user (header) parameters to 27 records
  without changing any other size parameter.  The result is to be put
  in a new file called 'table2.tab', leaving the input table unchanged.
  <P>
  	tt&gt; tchsize table table2 27 -1 -1 -1
  <P>
  3. Truncate unused space in three different tables, with the truncated tables
  named 'a.tab', 'b.tab', and 'c.tab':
  <P>
  <PRE>
  	tt&gt; tchsize table1,table2,tab67 a,b,c 0 0 0 0
  		or
  	tt&gt; tchsize tab*.tab a,b,c 0 0 0 0
  </PRE>
  In the latter case the extension is given explicitly in case there
  are other files beginning with 'tab' that are not tables; there must
  be exactly three tables beginning with tab because the output list
  has three names.
  <P>
  4. Increase the space available for allocating new columns:
  <P>
  Suppose the following information about the table has been obtained
  by using the 'tinfo' task:
  <P>
  <PRE>
    tinfo.ncols   = 7
    tinfo.maxcols = 8
    tinfo.rowlen  = 12
    tinfo.rowused = 10
    tinfo.tbltype = "row"
  </PRE>
  <P>
  Suppose we want to add 10 more columns:  five single-precision columns,
  two double-precision, and three character*12.  If the table were
  column-ordered we would only have to increase 'maxcols' to at least 17
  ('ncols'+10).  Since the table is row-ordered we still must have 'maxcols=17',
  but we also have to increase the row length to allow room for the
  additional columns.  The extra row length needed is 5 + 2*2 + 3*3 = 18,
  so we must set the new row length to at least 'tinfo.rowused' + 18 = 28.
  So we have
  <P>
  <PRE>
  	tt&gt; tchsize table "" -1 17 28 -1
  </PRE>
  <P>
  if the space for header parameters does not need to be changed, and
  the allocated number of rows is irrelevant for a row-ordered table.
  <P>
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
  tinfo
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
