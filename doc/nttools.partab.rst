.. _partab:

partab — Transfer an IRAF parameter to a table element.
=======================================================

**Package: nttools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  partab -- Copy an IRAF parameter to a table element.
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  partab value table column row
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Description</H3>
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
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>value [string]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='value' Line='value [string]'>
  <DD>The IRAF parameter that will be copied into the table element.
  </DD>
  </DL>
  <DL>
  <DT><B>table [file name]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='table' Line='table [file name]'>
  <DD>Name of the table.
  </DD>
  </DL>
  <DL>
  <DT><B>column [string]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='column' Line='column [string]'>
  <DD>Column name. (Column names are not case sensitive).
  </DD>
  </DL>
  <DL>
  <DT><B>row [integer, min=1, max=INDEF]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='row' Line='row [integer, min=1, max=INDEF]'>
  <DD>Row number.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Examples</H3>
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
  keypar, keytab, parkey, tabkey, tabpar
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
