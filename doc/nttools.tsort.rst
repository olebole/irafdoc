tsort — Sort a table.
=====================

**Package: nttools**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>tsort (Dec90)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>tables</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>tsort (Dec90)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>tsort</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  tsort -- Sort a table on one or more columns.
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  tsort table columns
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task sorts an STSDAS-format table.  The sort is done in place, so if you want
  to keep a copy of the unsorted table, you should copy it with the 'tcopy'
  task before you
  do the sort.  The column, or columns, on which to sort are specified
  using the parameter
  'columns', which is a list of column names, or column name templates, 
  separated by
  commas.  The most significant column name is the first in the list---the
  column whose values are sorted; subsequent
  columns are used only to break ties.  There are two flags, 'ascend' and 
  'casesens'.  The 'ascend' parameter determines whether the sort is done
  in ascending or descending order, if
  'ascend = yes', the first row in the output table holds the lowest value (if
  the sorted column is numeric) or the first string in alphabetic order (if the
  sorted column is a character string).  If 'casesens = yes', upper 
  case characters
  precede lower case characters.  Otherwise, case is not significant
  in determining the sort order.  When sorting a boolean column, "<TT>no</TT>" precedes
  "<TT>yes</TT>".  Null table elements are always last in the sort, regardless
  of the value of 'ascend'. 
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_table">table [file name template]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='table' Line='table [file name template]'>
  <DD>Name of the table, or tables, to be sorted in-place.
  All tables are sorted on the same column or columns; if more than one table
  is specified all tables must have the column(s) specified by the 'columns'
  parameter.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_columns">columns [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='columns' Line='columns [string]'>
  <DD>Column name or column name template describing columns on which sort will
  be performed.  A column name template consists of a list of
  column names, or column patterns containing wildcard characters.
  Individual column names, or templates, are separated by commas or white space.
  The list of columns can be placed in a file and the name of the 
  file passed to 'columns' (preceded by a
  "<TT>@</TT>" character). 
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(ascend = yes) [boolean]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(ascend = yes) [boolean]'>
  <DD>Sort the table in ascending order?  If you want the table sorted in descending
  order, set 'ascend = no'.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(casesens = yes) [boolean]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(casesens = yes) [boolean]'>
  <DD>Are sorts on character columns to be case sensitive?  If 'casesens = yes',
  upper case letters will precede lower case letters.  If 'casesens = no',
  case is ignored by the sort operation.
  <DL>
  <DT><B><A NAME="l_"></A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line=' '>
  <DD></DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Sort a table of star positions by right ascension and declination:
  <P>
  <PRE>
  tt&gt; tsort starcat.tab ra,dec
  </PRE>
  <P>
  2. Sort a phone list. Make the sort case insensitive:
  <P>
  <PRE>
  tt&gt; tsort phone.tab lname,fname case-
  </PRE>
  <P>
  3. Sort a star catalog so that all binary stars (i.e., a boolean column
  named 'binary') are first:
  <P>
  <PRE>
  tt&gt; tsort starcat.tab binary asc-
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
  This task was written by Bernie Simon.
  </UL>
  <! EndSection:   'REFERENCES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  tcopy
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>