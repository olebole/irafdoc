.. _tabpar:

tabpar — Transfer a table element to an IRAF parameter.
=======================================================

**Package: nttools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  tabpar -- Copy a table element to an IRAF parameter.
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  tabpar table column row
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task reads a table element specified by a table name, column name,
  and row number. The element is written to the task parameter 'value' as
  a character string. If the table element is boolean, then 'value' will
  be either "<TT>yes</TT>" or "<TT>no</TT>". If the element is undefined, the task parameter
  'undef' will be set to "<TT>yes</TT>". String parameters, such as 'value', can be
  converted to numeric types with the built in functions real() and int().
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>table [file name]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='table' Line='table [file name]'>
  <DD>Name of the table from which this task is to read a value.
  </DD>
  </DL>
  <DL>
  <DT><B>column [string]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='column' Line='column [string]'>
  <DD>Column name. (The column name is not case sensitive.)
  </DD>
  </DL>
  <DL>
  <DT><B>row [integer, min=1, max=INDEF]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='row' Line='row [integer, min=1, max=INDEF]'>
  <DD>Row number.
  </DD>
  </DL>
  <DL>
  <DT><B>(format=yes) [boolean]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(format=yes) [boolean]'>
  <DD>Format the value using table print format?
  <P>
  The value from the table is returned to this task as a string parameter
  (see 'value').
  The default is to use the print format for 'column' to format the value,
  because this preserves the behavior of the task
  prior to the addition of the 'format' parameter.
  This behavior may be desirable when using h or m format, for example,
  or perhaps when using x or o format.
  On the other hand,
  it will often be the case that what you want is
  the actual value in the table,
  and using the print format
  could significantly limit the accuracy of the result.
  In this case, use format=no.
  </DD>
  </DL>
  <DL>
  <DT><B>(value) [string]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(value) [string]'>
  <DD>This parameter is used to store the value read in from 'table'.
  </DD>
  </DL>
  <DL>
  <DT><B>(undef) [boolean]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(undef) [boolean]'>
  <DD>Is the value read in from 'table' undefined?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Print the interval between the first 2 wavelengths (i.e., rows 1 and 2
  in the column 'WAVELENGTH') in the table 'spectrum.tab':
  <P>
  <PRE>
  tt&gt; tabpar spectrum.tab WAVELENGTH 1
  tt&gt; x = real(tabpar.value)
  tt&gt; tabpar spectrum.tab WAVELENGTH 2
  tt&gt; y = real(tabpar.value)
  tt&gt; print(y-x)
  </PRE>
  <P>
  2. Print the twelfth component name (i.e., row 12 of the column 'COMPNAME',
  after checking to see if it is undefined.  If the value is undefined, then
  print a message instead:
  <P>
  <PRE>
  tt&gt; tabpar graph.tab COMPNAME 12
  tt&gt; if (tabpar.undef) {
  &gt;&gt;&gt;	print ("Component name undefined")
  &gt;&gt;&gt; } else {
  &gt;&gt;&gt;	print ("Component name = ",tabpar.value)
  &gt;&gt;&gt; }
  </PRE>
  <P>
  3. Here is an example illustrating the difference between
  format=yes and format=no for an integer column with x (hexadecimal) format:
  <P>
  <PRE>
  tt&gt; tabpar g.tab counts 4 format=yes
  tt&gt; =tabpar.value
  31
  tt&gt; tabpar g.tab counts 4 format=no
  tt&gt; =tabpar.value
  49
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>References</H3>
  <! BeginSection: 'REFERENCES'>
  <UL>
  This task was written by Bernie Simon.
  </UL>
  <! EndSection:   'REFERENCES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  keypar, keytab, parkey, partab, tabkey
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
