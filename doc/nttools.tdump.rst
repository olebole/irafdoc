tdump — Dump the contents of a table to an ASCII file.
======================================================

**Package: nttools**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>tdump (Nov2000)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>tables</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>tdump (Nov2000)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>tdump</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  tdump -- Convert an STSDAS table to ASCII format.
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  tdump table
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task converts an STSDAS table to ASCII format.
  The output does not include row numbers or column names;
  use the 'tprint' task for more readable output.
  <P>
  The two primary uses for 'tdump' are to allow editing that would be
  difficult or impossible with 'tedit' (such as global substitutions)
  and copying a table over a network to another computer.
  For such purposes the table can be dumped to three separate files
  (i.e., one containing column definitions, one for header parameters,
  and one for table data),
  the data may be edited, column data types changed, etc.,
  and then the 'tcreate' task can be used to reassemble the table 
  from the three ASCII files.
  To prevent loss of information due to truncation,
  floating point data are printed using g format with a wide field.
  A character value with multiple words is printed with enclosing quotes
  to make it clear that it is the value for a single column
  and also for compatibility with 'tcreate'.
  <P>
  All rows and columns of the table are dumped by default,
  but ranges of rows and individual columns may be specified.
  <P>
  The order of printing the data is as follows.
  The first column of the first row is printed,
  then the second column of the first row is printed,
  then the third column of the first row, etc.
  If any column contains arrays,
  each element of the column array in the current row is printed
  before moving on to the next column.
  If the printed output is wider than a page (see 'pwidth'),
  the output will consist of more than one line per row of the table.
  After printing all columns in the first row,
  the second row is printed in the same way.
  Each row begins with a new line in the output text file.
  Note that this can be different from 'tprint',
  which prints all rows for those columns that will fit on a page,
  then prints all rows for the next set of columns.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_table">table [file name]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='table' Line='table [file name]'>
  <DD>The name of the STSDAS table to be dumped.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(cdfile = STDOUT) [file name]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(cdfile = STDOUT) [file name]'>
  <DD>If 'cdfile' is not null (i.e., it is not passed a value of "<TT></TT>")
  then the column definitions will be written
  to an output file having the name passed to 'cdfile'.
  (Note:  A space is not null.)  The column definitions consist of
  the column name, data type ("<TT>R</TT>" for real,
  "<TT>D</TT>" for double, "<TT>I</TT>" for integer, "<TT>B</TT>" for boolean,
  or "<TT>CH*n</TT>" for character strings of length n), print format, and units.
  For columns of arrays,
  the array size is shown in square brackets appended to the data type.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(pfile = STDOUT) [file name]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(pfile = STDOUT) [file name]'>
  <DD>If 'pfile' is not null (i.e., it is not passed a value of "<TT></TT>") 
  then the header parameters will be written
  to an output file with the name passed to 'pfile'.
  This file will not be created
  if there are no header parameters in the input file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(datafile = STDOUT) [file name]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(datafile = STDOUT) [file name]'>
  <DD>If 'datafile' is not null (i.e., it is not passed a value of "<TT></TT>") then 
  the table data will be written
  to an output file with the name passed to 'datafile'.
  This file will not be created if the input table is empty.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(columns = "<TT></TT>") [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(columns = "") [string]'>
  <DD>The names of the columns to be printed.
  A null value causes all columns to be printed.
  A column template consists of a list
  of either column names or column name templates that include wildcards.
  Individual column names or templates are separated by commas or white space.
  This list of column names can be placed in a list file and 'column'
  will then be passed the file name preceded by a "<TT>@</TT>" character.
  If the first non-white character in the column template
  is the negation character (either "<TT>~</TT>" or "<TT>!</TT>")
  the columns NOT named in the template will be printed.
  <P>
  The 'tlcol' task (with the 'nlist' parameter set to 1) may be used 
  to generate a list of column names so there is no question about spelling.
  This list may be edited to rearrange or delete columns.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(rows = "<TT>-</TT>") [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(rows = "-") [string]'>
  <DD>The range of rows to be printed.
  The default of "<TT>-</TT>" means print all rows.
  The first ten rows could be specified as 'rows="<TT>1-10</TT>"'.
  To print the first ten rows and all rows from 900 through
  the last (inclusive), use 'rows="<TT>1-10,900-</TT>"'.
  Setting 'rows="<TT>1,3,7,23</TT>"' will print only those four rows.
  It is not an error to specify rows larger than the largest row number;
  they will simply be ignored.
  Type "<TT>help xtools.ranges</TT>" for more information.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(pwidth = -1) [integer, min=-1, max=INDEF]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(pwidth = -1) [integer, min=-1, max=INDEF]'>
  <DD>Width of the output for printing the table data.
  The default value of -1 means that
  checking the width should be disabled,
  and each table row will be written to one line in the output file.
  <P>
  If any column to be printed is wider than 'pwidth',
  a warning message will be displayed,
  and the data will overflow the page width.
  The width of each character column is
  increased by two to allow space for a pair of enclosing quotes,
  which will be used if the value to be printed includes a blank or tab.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  Dump the table "<TT>junk.tab</TT>" to STDOUT:
  <PRE>
  <P>
       tt&gt; tdump junk.tab cdfile=STDOUT pfile=STDOUT datafile=STDOUT
  <P>
  </PRE>
  2.  Dump "<TT>junk.tab</TT>", but with the order of the columns rearranged:
  <PRE>
  <P>
       tt&gt; tlcol junk.tab nlist=1 &gt; colnames.lis
       tt&gt; edit colnames.lis
          (Rearrange the column names and perhaps delete some of them.)
       tt&gt; tdump junk.tab columns=@colnames.lis
  </PRE>
  <P>
  3.  Dump only the first 100 rows of the file "<TT>big.fits</TT>":
  <P>
  <PRE>
  	tt&gt; tdump big.fits rows="1-100"
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
  tprint, tlcol, tcreate, ranges
  <P>
  Type "<TT>help tables opt=sys</TT>" for a higher-level description of the 'tables' 
  package.
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>