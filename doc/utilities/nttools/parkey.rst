.. _parkey:

parkey: Put an IRAF parameter into an image or table header keyword.
====================================================================

**Package: nttools**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  parkey value output keyword
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  This task changes the value of a header keyword in either a table or an
  image. If the value of the task parameter 'add' is <span style="font-family: monospace;">"yes"</span>, the task will
  allow you to add a new keyword to the header, otherwise, adding a new
  keyword will cause an error. Type conversion is performed if the data type of
  the header keyword differs from the data type of the input parameter 'value'. 
  If a new
  keyword is added to the file, the type is determined 
  from the input value. The
  strings <span style="font-family: monospace;">"yes"</span>, <span style="font-family: monospace;">"y"</span>, <span style="font-family: monospace;">"no"</span>, <span style="font-family: monospace;">"n"</span>, <span style="font-family: monospace;">"true"</span>, <span style="font-family: monospace;">"t"</span>, <span style="font-family: monospace;">"false"</span>, and <span style="font-family: monospace;">"f"</span>, in either
  upper or lower case, are interpreted as boolean values.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>value [string]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='value' Line='value [string]' -->
  <dd>Input value to be written to the header keyword. (Strings are case sensitive.)
  </dd>
  </dl>
  <dl>
  <dt><b>output [file name]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='output' Line='output [file name]' -->
  <dd>Name of the file whose header keyword is to be changed.
  </dd>
  </dl>
  <dl>
  <dt><b>keyword [string]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='keyword' Line='keyword [string]' -->
  <dd>Name of the header keyword to be changed. (The name is not case sensitive.)
  </dd>
  </dl>
  <dl>
  <dt><b>(add = no) [boolean]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='' Line='(add = no) [boolean]' -->
  <dd>Allow new header keywords to be added?  
  If 'add = no', then existing keywords
  can take new values but no new keywords can be added to the file.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Set the header keyword 'OVERSCAN' in the file 'image.hhh' to 5:
  </p>
  <pre>
  tt&gt; parkey 5 image.hhh overscan
  </pre>
  <p>
  2. Set the group parameter 'CTYPE1' in the second group of the same
  file to <span style="font-family: monospace;">"ANGSTROM"</span>:
  </p>
  <pre>
  tt&gt; parkey ANGSTROM image.hhh[2] ctype1
  </pre>
  <p>
  3. Set the header keyword 'YSTEP' to the value stored 
  in the IRAF parameter <span style="font-family: monospace;">'x'</span>:
  </p>
  <pre>
  tt&gt; parkey (x) image.hhh ystep
  </pre>
  <p>
  4. Add the keyword 'COMPNAME' to the table header and put the value <span style="font-family: monospace;">"FILTER1"</span>
  in it:
  </p>
  <pre>
  tt&gt; parkey FILTER1 graph.tab compname add+
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
  keypar, keytab, partab, tabkey, tabpar
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  -->
  
