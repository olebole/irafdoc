.. _keytab:

keytab: Copy an image or table header keyword to a table element.
=================================================================

**Package: nttools**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  keytab input keyword table column row
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  This task reads a header keyword from either an image or a table file
  and writes it to a table element (row and column position). If the
  data type of the header keyword differs from that of the table
  element, then the value is converted to the appropriate data type. If
  the keyword is not found in the header, the element will be set to the
  null value appropriate for the column type.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input [file name]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input [file name]' -->
  <dd>Name of the file containing header keyword.
  </dd>
  </dl>
  <dl>
  <dt><b>keyword [string]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='keyword' Line='keyword [string]' -->
  <dd>Name of the header keyword to be read. (Keyword names are not case sensitive.)
  </dd>
  </dl>
  <dl>
  <dt><b>table [file name]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='table' Line='table [file name]' -->
  <dd>Name of the table to which the value will be written.
  </dd>
  </dl>
  <dl>
  <dt><b>column [string]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='column' Line='column [string]' -->
  <dd>Name of table column. (Column names are not case sensitive.)
  </dd>
  </dl>
  <dl>
  <dt><b>row [integer, min=1, max=INDEF]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='row' Line='row [integer, min=1, max=INDEF]' -->
  <dd>Table row number.
  </dd>
  </dl>
  <dl>
  <dt><b>(silent = no) [bool]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='' Line='(silent = no) [bool]' -->
  <dd>If this parameter is set to no (the default) a warning message will be
  printed if the keyword is not found in the header. If it is set
  to yes, the warning message is suppressed.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Copy the component name (i.e., the 'COMPNAME' header keyword) 
  from the table 'thruput.tab' to the
  first row of the table 'graph.tab'.
  </p>
  <pre>
  tt&gt; keytab thruput.tab COMPNAME graph.tab COMPNAME 1
  </pre>
  <p>
  2. Copy the zero point of the second group (i.e., the 'CRVAL1' keyword)
  in the image file 'image.hhh' to the first
  wavelength in the table 'spectrum.tab'.
  </p>
  <pre>
  tt&gt; keytab image.hhh[2] CRVAL1 spectrum.tab WAVELENGTH 1
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>References</h3>
  <!-- BeginSection: 'REFERENCES' -->
  <p>
  This task was written by Bernie Simon.
  </p>
  <!-- EndSection:   'REFERENCES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  keypar, parkey, partab, tabkey, tabpar
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'REFERENCES' 'SEE ALSO'  -->
  
