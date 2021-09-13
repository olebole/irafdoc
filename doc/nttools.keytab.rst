keytab — Copy an image or table header keyword to a table element.
==================================================================

**Package: nttools**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>keytab (Dec94)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>tables</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>keytab (Dec94)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>keytab</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  keytab -- Copy a header keyword to a table element.
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  keytab input keyword table column row
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task reads a header keyword from either an image or a table file
  and writes it to a table element (row and column position). If the
  data type of the header keyword differs from that of the table
  element, then the value is converted to the appropriate data type. If
  the keyword is not found in the header, the element will be set to the
  null value appropriate for the column type.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input [file name]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input [file name]'>
  <DD>Name of the file containing header keyword.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_keyword">keyword [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='keyword' Line='keyword [string]'>
  <DD>Name of the header keyword to be read. (Keyword names are not case sensitive.)
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_table">table [file name]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='table' Line='table [file name]'>
  <DD>Name of the table to which the value will be written.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_column">column [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='column' Line='column [string]'>
  <DD>Name of table column. (Column names are not case sensitive.)
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_row">row [integer, min=1, max=INDEF]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='row' Line='row [integer, min=1, max=INDEF]'>
  <DD>Table row number.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(silent = no) [bool]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(silent = no) [bool]'>
  <DD>If this parameter is set to no (the default) a warning message will be
  printed if the keyword is not found in the header. If it is set
  to yes, the warning message is suppressed.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Copy the component name (i.e., the 'COMPNAME' header keyword) 
  from the table 'thruput.tab' to the
  first row of the table 'graph.tab'.
  <P>
  <PRE>
  tt&gt; keytab thruput.tab COMPNAME graph.tab COMPNAME 1
  </PRE>
  <P>
  2. Copy the zero point of the second group (i.e., the 'CRVAL1' keyword)
  in the image file 'image.hhh' to the first
  wavelength in the table 'spectrum.tab'.
  <P>
  <PRE>
  tt&gt; keytab image.hhh[2] CRVAL1 spectrum.tab WAVELENGTH 1
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_references">REFERENCES</A></H2>
  <! BeginSection: 'REFERENCES'>
  <UL>
  This task was written by Bernie Simon.
  </UL>
  <! EndSection:   'REFERENCES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  keypar, parkey, partab, tabkey, tabpar
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'REFERENCES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>