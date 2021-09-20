.. _partab:

partab: Transfer an IRAF parameter to a table element.
======================================================

**Package: nttools**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  partab value table column row
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  This task changes the value of a table element to the value of the input
  parameter 'value'.  If 'value' is set to <span style="font-family: monospace;">"INDEF"</span>, the table element will be
  set to undefined.  If the data type of the table element is different from
  that of the input parameter 'value', this task will perform 
  type conversion.  The strings
  <span style="font-family: monospace;">"yes"</span>, <span style="font-family: monospace;">"y"</span>, <span style="font-family: monospace;">"no"</span>, <span style="font-family: monospace;">"n"</span>, <span style="font-family: monospace;">"true"</span>, <span style="font-family: monospace;">"t"</span>, <span style="font-family: monospace;">"false"</span>, and <span style="font-family: monospace;">"f"</span>, in either upper or
  lower case are interpreted as boolean values.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>value [string]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='value' Line='value [string]' -->
  <dd>The IRAF parameter that will be copied into the table element.
  </dd>
  </dl>
  <dl>
  <dt><b>table [file name]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='table' Line='table [file name]' -->
  <dd>Name of the table.
  </dd>
  </dl>
  <dl>
  <dt><b>column [string]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='column' Line='column [string]' -->
  <dd>Column name. (Column names are not case sensitive).
  </dd>
  </dl>
  <dl>
  <dt><b>row [integer, min=1, max=INDEF]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='row' Line='row [integer, min=1, max=INDEF]' -->
  <dd>Row number.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Set the twelfth component (i.e., row 12 of column 'COMPNAME') 
  in the file 'graph.tab' to <span style="font-family: monospace;">"FILTER1"</span>:
  </p>
  <pre>
  tt&gt; partab FILTER1 graph.tab COMPNAME 12
  </pre>
  <p>
  2. Set the first wavelength (i.e., row 1 of column 'WAVELENGTH') in 
  the file 'spectrum.tab' to the value contained in parameter
  <span style="font-family: monospace;">'x'</span>:
  </p>
  <pre>
  tt&gt; partab (x) spectrum.tab WAVELENGTH 1
  </pre>
  <p>
  3. Set the hundreth wavelength (i.e., row 100 of column 'WAVELENGTH')
  in 'spectrum.tab' to undefined:
  </p>
  <pre>
  tt&gt; partab INDEF spectrum.tab WAVELENGTH 100
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
  keypar, keytab, parkey, tabkey, tabpar
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  -->
  
