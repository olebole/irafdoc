thedit — Edit or print table header keywords.
=============================================

**Package: nttools**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>thedit (Feb2002)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>ttools</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>thedit (Feb2002)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>thedit</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  thedit -- Edit or view keyword values in tables.
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  thedit table keywords value
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This table header editor can be used to add, delete, edit,
  or just print the values of table header keywords.
  <P>
  Although this task was based on 'hedit',
  there are significant differences.
  The 'add', 'verify', and 'update' parameters of 'hedit'
  are not included in 'thedit'.
  If a specified keyword does not already exist,
  then it will be added
  (equivalent to add=yes in 'hedit').
  If a keyword does not exist,
  and the value expression is "<TT>.</TT>",
  a warning will be printed
  ('hedit' is silent in this case).
  <P>
  Such parameters as the number of rows or columns in the table
  are stored differently in FITS, STSDAS, and text tables.
  The following special "<TT>keywords</TT>" can be used
  to reference such information regardless of table type.
  These may be used in the 'keywords' parameter when value="<TT>.</TT>",
  or they can be used in the 'value' parameter as part of an expression.
  <P>
  <PRE>
      i_table   string    table name (may include extension ID)
      i_file    string    name of the file containing the table
      i_ctime   string    file modification (or creation) time
      i_nrows   int       number of rows in the table
      i_ncols   int       number of columns in the table
      i_npar    int       number of keywords in the table header
      i_type    string    table type
  </PRE>
  <P>
  'thedit' supports two of the special operands
  that are available in 'hedit':  "<TT>$</TT>" and "<TT>$I</TT>".
  When 'value' is an expression,
  "<TT>$</TT>" gives the value of the current keyword.
  "<TT>$I</TT>" is equivalent to "<TT>i_table</TT>",
  the name of the current table.
  "<TT>$I</TT>" can be used as a keyword or as part of an expression.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_table">table [file name template]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='table' Line='table [file name template]'>
  <DD>A list of tables for which keywords are to be edited or printed.
  If 'value' is "<TT>.</TT>", each table will be opened read-only;
  otherwise, each table will be opened read-write.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_keywords">keywords [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='keywords' Line='keywords [string]'>
  <DD>One or more keywords, separated by commas and/or blanks,
  which are to be added, modified, or printed.
  If the value expression (see 'value') is not "<TT>.</TT>",
  any keyword in 'keywords' that is not already present
  will be added to the header.
  <P>
  Wildcards are supported; however,
  the "<TT>@filename</TT>" syntax is not supported.
  Do not use wildcard or other special characters
  if a keyword is to be added to the header.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_value">value = "<TT>.</TT>" [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='value' Line='value = "." [string]'>
  <DD>This is the value to be assigned to each keyword in 'keywords'.
  The special value "<TT>.</TT>" means that
  the keywords should be printed rather than edited,
  and in this case the table will be opened read-only.
  If 'value' is not equal to "<TT>.</TT>",
  the same value will be assigned to all the keywords
  matching the template 'keywords'.
  <P>
  In order to set a keyword value to "<TT>.</TT>" or "<TT>,</TT>",
  specify the value as "<TT>\.</TT>" or "<TT>\,</TT>" respectively.
  (Note that if given on the command line,
  the quotes are required in this case.)  Requiring "<TT>,</TT>" to be escaped
  was added as protection against accidentally typing "<TT>,</TT>" instead of "<TT>.</TT>".
  <P>
  As with 'hedit',
  a general expression may be given for 'value'
  by enclosing the expression in parentheses.
  The expression may include constants and/or keyword names;
  it will be evaluated and then assigned to each keyword in 'keywords'.
  <P>
  Note that if delete = yes, then 'value' will be ignored.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(delete = no) [bool]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(delete = no) [bool]'>
  <DD>If delete = yes, the specified keywords will be deleted.
  All the keywords listed in 'keywords' will be deleted,
  for each table in 'table'.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(show = yes) [bool]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(show = yes) [bool]'>
  <DD>Print a record of each edit operation?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  Display all the header keywords (except blank) in "<TT>example.tab</TT>".
  <P>
  <PRE>
      tt&gt; thedit example.tab * .
  </PRE>
  <P>
  2.  Display only the special keywords for "<TT>timetag.fits[events]</TT>".
  <P>
  <PRE>
      tt&gt; thedit timetag.fits[events] i_* .
  <P>
      timetag.fits[events],i_table = timetag.fits[events]
      timetag.fits[events],i_file = timetag.fits
      timetag.fits[events],i_ctime = "Wed 12:07:58 31-May-2000"
      timetag.fits[events],i_nrows = 337824
      timetag.fits[events],i_ncols = 6
      timetag.fits[events],i_npar = 58
      timetag.fits[events],i_type = "fits, binary"
  </PRE>
  <P>
  3.  Print all HISTORY keywords in "<TT>example.txt</TT>".
  <P>
  <PRE>
      tt&gt; thedit example.txt history .
  </PRE>
  <P>
  4.  Add a new HISTORY keyword to "<TT>example.tab</TT>".
  <P>
  <PRE>
      tt&gt; thedit example.tab history \<BR>
      "('file name is ' // i_file) // '; number of rows = ' // str (i_nrows)"
  </PRE>
  <P>
  5.  Increment the value of COUNT.
  <P>
  <PRE>
      tt&gt; thedit example.tab count "($ + 1)"
  </PRE>
  <P>
  6.  Delete all HISTORY and COMMENT keywords in "<TT>example.fits[1]</TT>".
  <P>
  <PRE>
      tt&gt; thedit example.fits history,comment delete+
  </PRE>
  <P>
  7.  Evaluate a simple expression
  and assign the result to keyword WAVELEN.
  Keywords TCRVL1, TCDLT1, and NELEM
  are assumed to be already present in the header.
  <P>
  <PRE>
      tt&gt; thedit example.fits wavelen "(tcrvl1 + tcdlt1 * nelem/2.)"
  </PRE>
  <P>
  8.  A keyword can be renamed by using a two-step process,
  first creating a new keyword with the old value, and then
  deleting the old keyword.
  Note that while this procedure does copy the value,
  the comment will be lost.
  (The "<TT>k</TT>" instruction in 'tupar' can also be used to rename a keyword.)
  <P>
  <PRE>
      tt&gt; thedit example.tab newkey "(oldkey)"
      tt&gt; thedit example.tab oldkey delete+
  </PRE>
  <P>
  9.  The primary header or an image extension of a FITS file
  can also be opened as a table in order to access the keywords.
  <P>
  <PRE>
      tt&gt; thedit o47s01kdm_raw.fits[0] rootname .
      tt&gt; thedit o47s01kdm_flt.fits[1] bunit "COUNTS/S"
  </PRE>
  <P>
  10.  This could have been a big mistake.
  <P>
  <PRE>
      tt&gt; thedit abc.fits[1] * ,
  <P>
      ERROR: In order to set a keyword value to <TT>','</TT> you must use value='\,'
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  Expressions are evaluated using EVEXPR,
  which does not support double precision.
  <P>
  Header lines with keyword = '        ' cannot be displayed.
  <P>
  The 'value' parameter is of type string,
  and 'thedit' interprets the value
  to determine what data type to use
  when writing the value to the table.
  This can fail when a value appears to be a number
  but really should be treated as a string.
  For example, a date and time could be written as "<TT>19940531:11515000</TT>".
  'thedit' would interpret this as hours and minutes (HH:MMss)
  and convert the value to 1994053. + 11515000./60.
  A workaround for this case is to use 'tupar' instead of 'thedit';
  use the "<TT>pt</TT>" instruction, meaning put a keyword of type text.
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_references">REFERENCES</A></H2>
  <! BeginSection: 'REFERENCES'>
  <UL>
  This task was written by Phil Hodge,
  based on the 'hedit' task.
  </UL>
  <! EndSection:   'REFERENCES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  hedit, tupar
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>