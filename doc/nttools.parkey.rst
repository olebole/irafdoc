parkey — Put an IRAF parameter into an image or table header keyword.
=====================================================================

**Package: nttools**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>parkey (Dec90)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>tables</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>parkey (Dec90)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>parkey</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  parkey -- Write an IRAF parameter to a header keyword.
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  parkey value output keyword
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task changes the value of a header keyword in either a table or an
  image. If the value of the task parameter 'add' is "<TT>yes</TT>", the task will
  allow you to add a new keyword to the header, otherwise, adding a new
  keyword will cause an error. Type conversion is performed if the data type of
  the header keyword differs from the data type of the input parameter 'value'. 
  If a new
  keyword is added to the file, the type is determined 
  from the input value. The
  strings "<TT>yes</TT>", "<TT>y</TT>", "<TT>no</TT>", "<TT>n</TT>", "<TT>true</TT>", "<TT>t</TT>", "<TT>false</TT>", and "<TT>f</TT>", in either
  upper or lower case, are interpreted as boolean values.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_value">value [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='value' Line='value [string]'>
  <DD>Input value to be written to the header keyword. (Strings are case sensitive.)
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output [file name]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output [file name]'>
  <DD>Name of the file whose header keyword is to be changed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_keyword">keyword [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='keyword' Line='keyword [string]'>
  <DD>Name of the header keyword to be changed. (The name is not case sensitive.)
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(add = no) [boolean]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(add = no) [boolean]'>
  <DD>Allow new header keywords to be added?  
  <P>
  If 'add = no', then existing keywords
  can take new values but no new keywords can be added to the file.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Set the header keyword 'OVERSCAN' in the file 'image.hhh' to 5:
  <P>
  <PRE>
  tt&gt; parkey 5 image.hhh overscan
  </PRE>
  <P>
  2. Set the group parameter 'CTYPE1' in the second group of the same
  file to "<TT>ANGSTROM</TT>":
  <P>
  <PRE>
  tt&gt; parkey ANGSTROM image.hhh[2] ctype1
  </PRE>
  <P>
  3. Set the header keyword 'YSTEP' to the value stored 
  in the IRAF parameter <TT>'x'</TT>:
  <P>
  <PRE>
  tt&gt; parkey (x) image.hhh ystep
  </PRE>
  <P>
  4. Add the keyword 'COMPNAME' to the table header and put the value "<TT>FILTER1</TT>"
  in it:
  <P>
  <PRE>
  tt&gt; parkey FILTER1 graph.tab compname add+
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
  keypar, keytab, partab, tabkey, tabpar
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>