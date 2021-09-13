partab — Transfer an IRAF parameter to a table element.
=======================================================

**Package: nttools**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>partab (Nov91)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>tables</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>partab (Nov91)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>partab</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  partab -- Copy an IRAF parameter to a table element.
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  partab value table column row
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task changes the value of a table element to the value of the input
  parameter 'value'.  If 'value' is set to "<TT>INDEF</TT>", the table element will be
  set to undefined.  If the data type of the table element is different from
  that of the input parameter 'value', this task will perform 
  type conversion.  The strings
  "<TT>yes</TT>", "<TT>y</TT>", "<TT>no</TT>", "<TT>n</TT>", "<TT>true</TT>", "<TT>t</TT>", "<TT>false</TT>", and "<TT>f</TT>", in either upper or
  lower case are interpreted as boolean values.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_value">value [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='value' Line='value [string]'>
  <DD>The IRAF parameter that will be copied into the table element.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_table">table [file name]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='table' Line='table [file name]'>
  <DD>Name of the table.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_column">column [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='column' Line='column [string]'>
  <DD>Column name. (Column names are not case sensitive).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_row">row [integer, min=1, max=INDEF]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='row' Line='row [integer, min=1, max=INDEF]'>
  <DD>Row number.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Set the twelfth component (i.e., row 12 of column 'COMPNAME') 
  in the file 'graph.tab' to "<TT>FILTER1</TT>":
  <P>
  <PRE>
  tt&gt; partab FILTER1 graph.tab COMPNAME 12
  </PRE>
  <P>
  2. Set the first wavelength (i.e., row 1 of column 'WAVELENGTH') in 
  the file 'spectrum.tab' to the value contained in parameter
  <TT>'x'</TT>:
  <P>
  <PRE>
  tt&gt; partab (x) spectrum.tab WAVELENGTH 1
  </PRE>
  <P>
  3. Set the hundreth wavelength (i.e., row 100 of column 'WAVELENGTH')
  in 'spectrum.tab' to undefined:
  <P>
  <PRE>
  tt&gt; partab INDEF spectrum.tab WAVELENGTH 100
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
  keypar, keytab, parkey, tabkey, tabpar
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>