.. _translit:

translit — Replace or delete specified characters in a file
===========================================================

**Package: utilities**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  translit -- replace or delete specified characters in a file
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  translit infile from_string [to_string]
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>infile</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='infile' Line='infile'>
  <DD>The input file name or template, e.g. "<TT>abc</TT>" or "<TT>abc.*</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>from_string</B></DT>
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
  <DT><B>to_string</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='to_string' Line='to_string'>
  <DD>Requested if delete is no, otherwise set to the null string.
  Characters in from_string are mapped into characters in to_string.
  When to_string is short with respect to from_string, it is padded
  by duplicating the last character.
  </DD>
  </DL>
  <DL>
  <DT><B>delete = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='delete' Line='delete = no'>
  <DD>If delete is yes the characters in from_string are deleted from the input
  file(s) and no to_string is requested.
  </DD>
  </DL>
  <DL>
  <DT><B>collapse = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='collapse' Line='collapse = no'>
  <DD>If this switch is set all strings of repeatedly mapped output characters
  are squeezed to a single character.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Examples</H3>
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
  
