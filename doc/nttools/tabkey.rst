.. _tabkey:

tabkey: Copy a table element to an image or table header keyword.
=================================================================

**Package: nttools**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  tabkey table column row output keyword
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  This task copies the value of a table element to a header 
  keyword in either a table
  or an image. If the table element and the header keyword are of different
  data types, this task will convert the type.
  An error will occur if any attempt is made
  to copy an undefined table element to a header keyword. If the value of
  the task parameter 'add' is <span style="font-family: monospace;">"yes"</span>, the task will allow you to add a new
  keyword to the header, otherwise, adding a new keyword will cause an
  error.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>table [file name]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='table' Line='table [file name]' -->
  <dd>Name of table containing the element to be copied.  The particular element
  is defined by the 'column' and 'row' parameters.
  </dd>
  </dl>
  <dl>
  <dt><b>column [string]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='column' Line='column [string]' -->
  <dd>Name of column. (Column names are not case sensitive.)
  </dd>
  </dl>
  <dl>
  <dt><b>row [integer, min=1, max=INDEF]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='row' Line='row [integer, min=1, max=INDEF]' -->
  <dd>Row number.
  </dd>
  </dl>
  <dl>
  <dt><b>output [file name]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='output' Line='output [file name]' -->
  <dd>Name of the file with the header keyword whose value is to be changed.
  </dd>
  </dl>
  <dl>
  <dt><b>keyword [string]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='keyword' Line='keyword [string]' -->
  <dd>Name of header keyword. (Header keyword names are not case sensitive.)
  </dd>
  </dl>
  <dl>
  <dt><b>(add = no) [boolean]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='' Line='(add = no) [boolean]' -->
  <dd>Allow new keywords to be added to the header?
  If 'add = no', then only existing header keywords can be modified--an error
  will occur if a keyword is specified that does not already exist.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Copy the first component name (i.e., row 1 of column 'COMPNAME'
  from the file 'graph.tab' to the header of the
  table 'thruput.tab'.  If the keyword does not already exist, then add
  it:
  </p>
  <pre>
  tt&gt; tabkey graph.tab COMPNAME 1 thruput.tab COMPNAME add+
  </pre>
  <p>
  2. Copy the date of the tenth observation (i.e., row 10 of column 'DATE')
  from the file 'schedule.tab' to the
  header keyword 'DATE' in 'image.hhh'. The keyword 'DATE' must already exist:
  </p>
  <pre>
  tt&gt; tabkey schedule.tab DATE 10 image.hhh date
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
  keypar, keytab, parkey, partab, tabpar
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  -->
  
