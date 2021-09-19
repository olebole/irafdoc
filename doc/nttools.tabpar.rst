.. _tabpar:

tabpar: Transfer a table element to an IRAF parameter.
======================================================

**Package: nttools**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  tabpar -- Copy a table element to an IRAF parameter.
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  tabpar table column row
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  This task reads a table element specified by a table name, column name,
  and row number. The element is written to the task parameter 'value' as
  a character string. If the table element is boolean, then 'value' will
  be either <tt>"yes"</tt> or <tt>"no"</tt>. If the element is undefined, the task parameter
  'undef' will be set to <tt>"yes"</tt>. String parameters, such as 'value', can be
  converted to numeric types with the built in functions real() and int().
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>table [file name]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='table' Line='table [file name]' -->
  <dd>Name of the table from which this task is to read a value.
  </dd>
  </dl>
  <dl>
  <dt><b>column [string]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='column' Line='column [string]' -->
  <dd>Column name. (The column name is not case sensitive.)
  </dd>
  </dl>
  <dl>
  <dt><b>row [integer, min=1, max=INDEF]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='row' Line='row [integer, min=1, max=INDEF]' -->
  <dd>Row number.
  </dd>
  </dl>
  <dl>
  <dt><b>(format=yes) [boolean]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='' Line='(format=yes) [boolean]' -->
  <dd>Format the value using table print format?
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
  </dd>
  </dl>
  <dl>
  <dt><b>(value) [string]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='' Line='(value) [string]' -->
  <dd>This parameter is used to store the value read in from 'table'.
  </dd>
  </dl>
  <dl>
  <dt><b>(undef) [boolean]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='' Line='(undef) [boolean]' -->
  <dd>Is the value read in from 'table' undefined?
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Print the interval between the first 2 wavelengths (i.e., rows 1 and 2
  in the column 'WAVELENGTH') in the table 'spectrum.tab':
  </p>
  <pre>
  tt&gt; tabpar spectrum.tab WAVELENGTH 1
  tt&gt; x = real(tabpar.value)
  tt&gt; tabpar spectrum.tab WAVELENGTH 2
  tt&gt; y = real(tabpar.value)
  tt&gt; print(y-x)
  </pre>
  <p>
  2. Print the twelfth component name (i.e., row 12 of the column 'COMPNAME',
  after checking to see if it is undefined.  If the value is undefined, then
  print a message instead:
  </p>
  <pre>
  tt&gt; tabpar graph.tab COMPNAME 12
  tt&gt; if (tabpar.undef) {
  &gt;&gt;&gt;	print ("Component name undefined")
  &gt;&gt;&gt; } else {
  &gt;&gt;&gt;	print ("Component name = ",tabpar.value)
  &gt;&gt;&gt; }
  </pre>
  <p>
  3. Here is an example illustrating the difference between
  format=yes and format=no for an integer column with x (hexadecimal) format:
  </p>
  <pre>
  tt&gt; tabpar g.tab counts 4 format=yes
  tt&gt; =tabpar.value
  31
  tt&gt; tabpar g.tab counts 4 format=no
  tt&gt; =tabpar.value
  49
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <!-- EndSection:   'BUGS' -->
  <h3>References</h3>
  <!-- BeginSection: 'REFERENCES' -->
  <p>
  This task was written by Bernie Simon.
  </p>
  <!-- EndSection:   'REFERENCES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  keypar, keytab, parkey, partab, tabkey
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  -->
  
