translit — Replace or delete specified characters in a file
===========================================================

**Package: utilities**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>translit (Mar84)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>utilities</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>translit (Mar84)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>translit</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  translit -- replace or delete specified characters in a file
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  translit infile from_string [to_string]
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_infile">infile</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='infile' Line='infile'>
  <DD>The input file name or template, e.g. "<TT>abc</TT>" or "<TT>abc.*</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_from_string">from_string</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='from_string' Line='from_string'>
  <DD>String containing characters to be mapped. 
  If delete is yes then the characters in from_string are deleted from the input
  file(s). The from_string may specify a range of characters, e.g. "<TT>a-z</TT>" or "<TT>A-Z</TT>".
  If the first character of from_string is ^ then the program will operate
  on all but the specified characters, e.g. "<TT>^a-z</TT>" means all but lower case
  alphabetic characters.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_to_string">to_string</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='to_string' Line='to_string'>
  <DD>Requested if delete is no, otherwise set to the null string.
  Characters in from_string are mapped into characters in to_string.
  When to_string is short with respect to from_string, it is padded
  by duplicating the last character.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_delete">delete = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='delete' Line='delete = no'>
  <DD>If delete is yes the characters in from_string are deleted from the input
  file(s) and no to_string is requested.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_collapse">collapse = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='collapse' Line='collapse = no'>
  <DD>If this switch is set all strings of repeatedly mapped output characters
  are squeezed to a single character.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  To change all the alphabetic characters in a file from lower to upper
  case, writing the result on the standard output:
  <P>
      cl&gt; translit filename a-z A-Z
  <P>
  To delete the letters a, b, and c from a file:
  <P>
      cl&gt; translit filename abc de=yes
  <P>
  To replace all but the letters abc in a file with A:
  <P>
      cl&gt; translit filename ^abc A
  </UL>
  <! EndSection:    'EXAMPLES'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'EXAMPLES'  >
  
  </BODY>
  </HTML>