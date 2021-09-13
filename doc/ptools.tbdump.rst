.. _tbdump:

tbdump — Print selected columns of a list of tables databases
=============================================================

**Package: ptools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  tbdump -- print fields (columns) from a list of  APPHOT/DAOPHOT STSDAS table
  	  databases
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  tbdump tables columns expr
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>tables</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='tables' Line='tables'>
  <DD>The name of the APPHOT/DAOPHOT table database(s) to be dumped.
  </DD>
  </DL>
  <DL>
  <DT><B>columns</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='columns' Line='columns'>
  <DD>The template specifying the names of the columns to be dumped.
  A null or blank string means
  dump all columns.  A column template consists of a list
  of either column names or column patterns containing the usual pattern matching
  meta-characters.  The names or patterns are separated by commas or white space.
  Column names must be spelled in full but may be upper or lower case.
  The columns list can be placed in a file and the name of the file preceded
  by an <TT>'@'</TT> character given in place of the column template.
  If the first non-white character in the column template
  is the negation character <TT>'~'</TT>, the output will contain those columns
  NOT named in the remainder of the column template.
  </DD>
  </DL>
  <DL>
  <DT><B>expr</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='expr' Line='expr'>
  <DD>The boolean expression to be evaluated once per record.
  Only the fields in those records for which the boolean expression
  evaluates to yes are printed.
  If <I>expr</I> = "<TT>yes</TT>", the specified columns in all the records are
  printed.
  </DD>
  </DL>
  <DL>
  <DT><B>datafile = STDOUT</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='datafile' Line='datafile = STDOUT'>
  <DD>If <I>Datafile</I> is not null ("<TT></TT>") then the table data will be written
  to an output file with this name. By default the table data is written
  on the standard output.
  <I>Datafile</I> will not be created if the table is empty.
  </DD>
  </DL>
  <DL>
  <DT><B>cdfile = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cdfile' Line='cdfile = ""'>
  <DD>If <I>Cdfile</I> is not null ("<TT></TT>") then the column definitions will be written
  to an output file with this name.
  The column definitions consist of the column name, data type (R, D, I, B,
  or C), print format, and units.
  </DD>
  </DL>
  <DL>
  <DT><B>pfile = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pfile' Line='pfile = ""'>
  <DD>If <I>Pfile</I> is not null ("<TT></TT>") then the header parameters will be written
  to an output file with this name.
  <I>Pfile</I> will not be created if there are no header parameters.
  </DD>
  </DL>
  <DL>
  <DT><B>rows = "<TT>-</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rows' Line='rows = "-"'>
  <DD><I>Rows</I> is a string which may be used to specify ranges of rows which are
  to be dumped.  The default of "<TT>-</TT>" means dump all rows.  The first
  ten rows could be specified as <I>rows</I> = "<TT>1-10</TT>" or just <I>rows</I> = "<TT>-10</TT>".
  To dump the first ten rows and all rows from 900 through the last,
  use <I>rows</I> = "<TT>-10,900-</TT>".  <I>Rows</I> = "<TT>1,3,7,23</TT>" will print only
  those four rows.  It is not an error to specify rows larger than the largest
  row number as they will simply be ignored.
  See the help for RANGES in XTOOLS for further information.
  </DD>
  </DL>
  <DL>
  <DT><B>pagwidth = 158</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pagwidth' Line='pagwidth = 158'>
  <DD>The width of the output for printing the table data.  If any of the columns
  to be printed is wider than this an error message will be displayed, and
  the data will not be dumped.  The width of each character column is
  increased by two to include a pair of enclosing quotes.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task converts selected records from an APPHOT/DAOPHOT STSDAS table
  database to ASCII format
  and by default prints the result on the standard output.
  TBDUMP  output does not include row numbers or column names.
  The TABLES package task TPRINT can be used for more readable output.
  <P>
  The PTOOLS version of TBDUMP described here is 
  actually a combination of the STSDAS TABLES package tasks TSELECT and TDUMP.
  <P>
  The three primary uses for TBDUMP are to format STSDAS tables for input to
  applications
  which expect simple text input, allow editing that would be
  difficult or impossible with the TABLES package TEDIT task, such as
  global substitutions,
  and facilitate copying a table over a network to another computer.
  For the latter two applications the table can be dumped to three separate files
  containing column definitions, header parameters, and table data,
  edited, column data types changed, etc.
  The TABLES package TCREATE can be used to create a new table from the three
  ASCII files produced by TBDUMP.
  By default only the column data is dumped.
  <P>
  TBDUMP queries for the columns to be dumped. If <I>columns</I> is null ("<TT></TT>")
  then all the columns are dumped.
  All the rows are dumped by default, but ranges of
  rows may be specified with the <I>rows</I> parameter.
  If the table is wider than will fit on a page,
  the output will consist of more than one line per row of the table,
  but all the columns will be printed before moving on to the next row.
  This is in contrast to TPRINT,
  which prints all rows for those columns that will fit on a page,
  then prints all rows for the next set of columns, etc.
  Character columns with multiple words are printed with enclosing quotes.
  <P>
  The TABLES package TLCOL task (with TLCOL.NLIST=1) may be used to generate
  a list of
  column names so there is no question about spelling or case.  This list may
  be edited to rearrange the names and/or delete some, the list
  file preceded by an <TT>'@'</TT> and used as the value of the <I>columns</I>
  parameter.
  <P>
  The output records are selected on the basis of an input boolean
  expression <I>expr</I> whose variables are the tables column names.
  If after substituting the values associated
  with a particular record into the field name variables the
  expression evaluates
  to yes, that record is included in the output table.
  <P>
  The supported
  operators and functions are briefly described below. A detailed description
  of the boolean expression evaluator and its syntax can be found
  in the manual page for the IMAGES package HEDIT task.
  <P>
  The following logical operators can be used in the boolean expression. 
  <P>
  <PRE>
  	equal		  ==	not equal		!=
  	less than	  &lt;	less than or equal	&lt;=
  	greater than	  &gt;	greater than or equal	&gt;=
  	or		  ||	and			&amp;&amp;
  	negation	  !	pattern match		?=
  	concatenation	  //
  </PRE>
  <P>
  The pattern match character ?=  takes a
  string expression as its first argument and a pattern as its second argument.
  The result is yes if the pattern is contained in the string expression.
  Patterns are strings which may contain pattern matching meta-characters.
  The meta-characters themselves can be matched by preceeding them with the escape
  character.  The meta-characters listed below. 
  <P>
  <PRE>
  	beginning of string	^	end of string		$
  	one character		?	zero or more characters	*
  	white space		#	escape character	\<BR>
  	ignore case		{	end ignore case		}
  	begin character class	[	end character class	]
  	not, in char class	^	range, in char class	-
  </PRE>
  <P>
  The expression may also include arithmetic operators and functions.
  The following arithmetic operators and functions are supported.
  <P>
  <PRE>
  addition		+		subtraction		-
  multiplication		*		division		/
  negation		-		exponentiation		**
  absolute value		abs(x)		cosine			cos(x)
  sine			sin(x)		tangent			tan(x)
  arc cosine		acos(x)		arc sine		asin(x)
  arc tangent		atan(x)		arc tangent		atan2(x,y)
  exponential		exp(x)		square root		sqrt(x)
  natural log		log(x)		common log		log10(x)
  minimum			min(x,y)	maximum			max(x,y)
  convert to integer	int(x)		convert to real		real(x)
  nearest integer		nint(x)		modulo			mod(x)
  </PRE>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <PRE>
  1. Dump the "ID", "MAG" and "MAGERR" columns of the DAOPHOT package NSTAR
  output to the standard output.
  <P>
      pt&gt; tbdump n4147.nst.1 "ID,MAG,MAGERR" yes
  <P>
  2. Dump the "ID", "MAG", and "MAGERR" columns of the above file for records
  which have  "MAG &lt;= 20.0".
  <P>
      pt&gt; tbdump n4147.nst.1 "ID,MAG,MAGERR" "MAG &lt;= 20.0"
  <P>
  3. Dump the "MAG" and "MAGERR" columns of the above file and pipe the
  result to graph.
  <P>
      pt&gt; tbdump n4147.nst.1 "MAG,MAGERR" yes | graph STDIN
  <P>
  4.  Dump all the columns in the first 100 rows of the above file.
  <P>
      pt&gt; tbdump n4147.nst.1 "" yes rows="1-100"
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  tables.tdump,tables.tprint,tables.tlcol,tables.tcreate,ptools.txdump,ptools.pdump
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
