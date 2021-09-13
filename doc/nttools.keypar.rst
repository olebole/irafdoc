.. _keypar:

keypar — Copy an image or table header keyword to an IRAF parameter.
====================================================================

**Package: nttools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  keypar -- Copy a header keyword to an IRAF parameter.
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  keypar input keyword
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task reads a header keyword from an image or table file. The
  keyword is written to the IRAF parameter 'value' as a character
  string. If the header keyword is boolean, the value of 'value' will
  either be "<TT>yes</TT>" or "<TT>no</TT>".  If the header keyword is not found, 'value'
  will be set to a null string.  String parameters, such as 'value', can
  be converted to numeric data types with the built in functions real()
  and int().
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input [file name]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input [file name]'>
  <DD>Name of the file containing the header keyword.
  </DD>
  </DL>
  <DL>
  <DT><B>keyword [string]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='keyword' Line='keyword [string]'>
  <DD>Name of the header keyword to be retrieved. (The keyword 
  name is not case sensitive.)
  </DD>
  </DL>
  <DL>
  <DT><B>(silent = no) [bool]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(silent = no) [bool]'>
  <DD>If this parameter is set to no (the default) a warning message will be
  printed if the keyword is not found in the header. If it is set to
  yes, the warning message is suppressed.
  </DD>
  </DL>
  <DL>
  <DT><B>(value) [string]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(value) [string]'>
  <DD>An output  parameter that will contain the value passed from the header
  keyword.
  </DD>
  </DL>
  <DL>
  <DT><B>(found) [bool]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(found) [bool]'>
  <DD>An output parameter that will be set to yes if the keyword is found in
  the header and no if it is not.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Print the number of groups (i.e., the 'GCOUNT' keyword)
  in the image file 'image.hhh':
  <P>
  <PRE>
  tt&gt; keypar image.hhh gcount
  tt&gt; print(keypar.value)
  </PRE>
  <P>
  2. Print the range of the data in the second group of the same image by 
  reading the values of the 'DATAMIN' and 'DATAMAX' keywords:
  <P>
  <PRE>
  tt&gt; keypar image.hhh[2] datamin
  tt&gt; x = real(keypar.value)
  tt&gt; keypar image.hhh[2] datamax
  tt&gt; y = real(keypar.value)
  tt&gt; print(y-x)
  </PRE>
  <P>
  3. Print the component name (i.e., the 'COMPNAME' header keyword)
  for the table 'thruput.tab':
  <P>
  <PRE>
  tt&gt; keypar thruput.tab compname
  tt&gt; print(keypar.value)
  </PRE>
  <P>
  4. Check for the existence of the exposure time in an image header:
  <P>
  <PRE>
  tt&gt; keypar image.hhh exptime silent+
  tt&gt; if (keypar.found) {
  &gt;&gt;&gt; print keypar.value
  &gt;&gt;&gt; } else {
  &gt;&gt;&gt; print INDEF
  &gt;&gt;&gt; }
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>References</H3>
  <! BeginSection: 'REFERENCES'>
  <UL>
  This task was written by Bernie Simon.
  SEE ALSO
  keytab, parkey, partab, tabkey, tabpar
  </UL>
  <! EndSection:    'REFERENCES'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'REFERENCES'  >
  
