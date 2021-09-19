.. _tproject:

tproject: Create new table from selected columns in a table.
============================================================

**Package: nttools**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  tproject -- Create a new table from selected columns of an old table.
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  tproject intable outtable columns
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  This task will create a new table containing a subset of the columns in an
  old table. The column names are given as a column name template. There is an
  optional parameter, 'uniq', that filters out duplicate rows from the
  new table.
  </p>
  <p>
  If you do not need to eliminate duplicate rows, you can also use tcopy 
  with a column selector on the input table name.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>intable [file name template]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='intable' Line='intable [file name template]' -->
  <dd>The table(s) from which the columns are to be copied. If input is
  redirected, this parameter will ignored and input will be read from
  STDIN instead.
  </dd>
  </dl>
  <dl>
  <dt><b>outtable [file name template]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='outtable' Line='outtable [file name template]' -->
  <dd>The new table(s) containing the copied columns.
  The number of output tables must equal the number of input tables.
  </dd>
  </dl>
  <dl>
  <dt><b>columns [string]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='columns' Line='columns [string]' -->
  <dd>This is the column template describing those columns that should be
  selected from the old table and put in the new table.
  A column template consists of a list
  of either column names or column name templates that include wildcard
  characters.  Column names (or templates) are separated by commas or white space.
  This parameter will accept the name of a list file (preceded by the <tt>"@"</tt>
  character) containing all of the column names to be selected.
  If the first non-white character in the column template
  is the negation character (either <tt>"~"</tt> or <tt>"!"</tt>),
  the new table will contain those columns
  whose names DO NOT match rest of the column template.
  </dd>
  </dl>
  <dl>
  <dt><b>(uniq = no) [boolean]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='' Line='(uniq = no) [boolean]' -->
  <dd>Eliminate duplicate rows from the output table?
  If 'unique' is set to <tt>"yes"</tt>, only one of each set of duplicate rows is
  included in the output table.  All columns in the output table must be
  identical for the row to be removed.  String comparisons are case
  sensitive. Care should be used in setting this option for
  large tables, as it significantly increases the running time.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Extract the star names, magnitudes, and colors from a catalog:
  </p>
  <pre>
  tt&gt; tproject starcat.tab starmag.tab "name,mag,color"
  </pre>
  <p>
  2. Exclude the measurement error from a set of spectra.  Change the file name
  extensions from <tt>".tab"</tt> to <tt>".tbl"</tt>:
  </p>
  <pre>
  tt&gt; tproject  *.tab  *.%tab%tbl%  "!error"
  </pre>
  <p>
  3. Create a new table of engineering parameters using a column template stored
  in the file 'columns.dat'.  Eliminate duplicate rows:
  </p>
  <pre>
  tt&gt; tproject datalog.tab sublog.tab @columns.dat uniq+
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
  tselect, tjoin, tproduct,tcopy
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  -->
  
