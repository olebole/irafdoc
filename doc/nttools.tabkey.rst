tabkey — Copy a table element to an image or table header keyword.
==================================================================

**Package: nttools**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>tabkey (Nov91)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>tables</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>tabkey (Nov91)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>tabkey</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  tabkey -- Copy a table element to a header keyword.
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  tabkey table column row output keyword
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task copies the value of a table element to a header 
  keyword in either a table
  or an image. If the table element and the header keyword are of different
  data types, this task will convert the type.
  An error will occur if any attempt is made
  to copy an undefined table element to a header keyword. If the value of
  the task parameter 'add' is "<TT>yes</TT>", the task will allow you to add a new
  keyword to the header, otherwise, adding a new keyword will cause an
  error.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_table">table [file name]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='table' Line='table [file name]'>
  <DD>Name of table containing the element to be copied.  The particular element
  is defined by the 'column' and 'row' parameters.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_column">column [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='column' Line='column [string]'>
  <DD>Name of column. (Column names are not case sensitive.)
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_row">row [integer, min=1, max=INDEF]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='row' Line='row [integer, min=1, max=INDEF]'>
  <DD>Row number.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output [file name]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output [file name]'>
  <DD>Name of the file with the header keyword whose value is to be changed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_keyword">keyword [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='keyword' Line='keyword [string]'>
  <DD>Name of header keyword. (Header keyword names are not case sensitive.)
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(add = no) [boolean]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(add = no) [boolean]'>
  <DD>Allow new keywords to be added to the header?
  If 'add = no', then only existing header keywords can be modified--an error
  will occur if a keyword is specified that does not already exist.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Copy the first component name (i.e., row 1 of column 'COMPNAME'
  from the file 'graph.tab' to the header of the
  table 'thruput.tab'.  If the keyword does not already exist, then add
  it:
  <P>
  <PRE>
  tt&gt; tabkey graph.tab COMPNAME 1 thruput.tab COMPNAME add+
  </PRE>
  <P>
  2. Copy the date of the tenth observation (i.e., row 10 of column 'DATE')
  from the file 'schedule.tab' to the
  header keyword 'DATE' in 'image.hhh'. The keyword 'DATE' must already exist:
  <P>
  <PRE>
  tt&gt; tabkey schedule.tab DATE 10 image.hhh date
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
  keypar, keytab, parkey, partab, tabpar
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>