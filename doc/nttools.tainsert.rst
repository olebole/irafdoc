.. _tainsert:

tainsert: Copy a column of scalars to an array entry in another table.
======================================================================

**Package: nttools**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  tainsert -- Copy a column of scalars from one table
  to an array entry in another.
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  tainsert intable outtable row column
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  This task reads an entire column from one table
  and inserts those values (presumably more than one)
  at a specified row and column in an output table.
  If the output table exists it will be written to in-place;
  otherwise, it will be created.
  </p>
  <p>
  By default, the same column name is used in both tables.
  If the column does not exist in the output table, the column will be created.
  If the output table and the row and column already exist,
  the array of values at that location will be overwritten.
  The number of elements copied will be the minimum of
  the number of input rows and the output column array size.
  If the number of input rows is larger than the array size,
  a warning message will be printed,
  and the extra rows will be ignored.
  If the number of input rows is smaller than the array size,
  the remaining array elements will be set to INDEF.
  </p>
  <p>
  If the specified row number is less than one or is INDEF,
  'tainsert' looks for the header keyword ORIG_ROW in the input table.
  ORIG_ROW is written by 'taextract'.
  If that keyword exists, its value is used as the row number.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>intable [file name]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='intable' Line='intable [file name]' -->
  <dd>Name of the input table.
  </dd>
  </dl>
  <dl>
  <dt><b>outtable [file name]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='outtable' Line='outtable [file name]' -->
  <dd>Name of the output table.
  If this table doesn't exist it will be created.
  </dd>
  </dl>
  <dl>
  <dt><b>row = -1 [integer]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='row' Line='row = -1 [integer]' -->
  <dd>This is the row number in the output table.
  The default means that 'tainsert' should use
  the value of the header keyword ORIG_ROW.
  </dd>
  </dl>
  <dl>
  <dt><b>column [string]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='column' Line='column [string]' -->
  <dd>Column name in the input table and, by default, also in the output table.
  If this column does not exist in the output table, it will be created,
  and the array size will be set to the number of rows in the input table.
  See the descriptions for 'outcolumn' and 'size', however.
  It is an error if this column in the input table contains array entries.
  </dd>
  </dl>
  <dl>
  <dt><b>outcolumn = <tt>""</tt> [string]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='outcolumn' Line='outcolumn = "" [string]' -->
  <dd>If 'outcolumn' is specified,
  that name will be used for the output table;
  otherwise, 'column' will be used for both input and output tables.
  This provides an easier way to change the name of the output column
  than by running 'tchcol' after running 'taextract'.
  Note that if 'outcolumn' is specified,
  it is used not only for finding the column in the output table
  but also for creating the column if it wasn't found.
  The 'size', 'datatype', 'colunits', and 'colfmt' parameters,
  by contrast, are only used when creating a new column.
  </dd>
  </dl>
  <dl>
  <dt><b>(size = INDEF) [int]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='' Line='(size = INDEF) [int]' -->
  <dd>When creating a new column in the output table,
  the default is for the array size of that column to be set to
  the number of rows in the input table.
  This may be overridden by specifying a value for 'size'.
  If 'size' is a positive integer, not INDEF,
  this will be used as the array size when creating the new column.
  </dd>
  </dl>
  <dl>
  <dt><b>(datatype = <tt>""</tt>) [string]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='' Line='(datatype = "") [string]' -->
  <dd>When creating a new column in the output table,
  the default is to use the same data type as the column in the input table.
  However, if 'datatype' is specified (i.e. not null or blank),
  this will be used as the data type when creating the new column.
  For numeric and boolean columns, only the first character is used:
  <tt>"r"</tt> and <tt>"d"</tt> for single and double precision floating point,
  <tt>"s"</tt> and <tt>"i"</tt> for short integer and integer,
  <tt>"b"</tt> for boolean.
  For a character string of maximum length 12 (for example), use <tt>"ch*12"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>(colunits = <tt>""</tt>) [string]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='' Line='(colunits = "") [string]' -->
  <dd>When creating a new column in the output table,
  the units will be set to 'colunits' if it has been specified;
  otherwise, the units will be copied from the column in the input table.
  </dd>
  </dl>
  <dl>
  <dt><b>(colfmt = <tt>""</tt>) [string]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='' Line='(colfmt = "") [string]' -->
  <dd>When creating a new column in the output table,
  the print format will be set to 'colfmt' if it has been specified;
  otherwise, the print format will be copied from the column in the input table.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Copy the entire column <tt>"polar"</tt> from table <tt>"scalar.tab"</tt>,
  and insert the values into row 5, column <tt>"polar"</tt>, of table <tt>"array.tab"</tt>.
  If <tt>"array.tab"</tt> does not exist it will be created.
  If column <tt>"polar"</tt> does not exist in <tt>"array.tab"</tt>,
  that column will be created.
  </p>
  <pre>
  at&gt; tainsert scalar.tab array.tab 5 polar
  </pre>
  <p>
  2. Copy the arrays from row 5, columns <tt>"wavelength"</tt> and <tt>"flux"</tt>,
  from <tt>"array.tab"</tt> to a temporary table,
  sort them on the wavelength,
  and insert them back where they came from.
  </p>
  <pre>
  at&gt; taextract array temp 5 wavelength
  at&gt; taextract array temp 5 flux
  at&gt; tsort temp wavelength
  at&gt; tainsert temp array 0 wavelength
  at&gt; tainsert temp array 0 flux
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <!-- EndSection:   'BUGS' -->
  <h3>References</h3>
  <!-- BeginSection: 'REFERENCES' -->
  <p>
  This task was written by Phil Hodge.
  </p>
  <!-- EndSection:   'REFERENCES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  taextract
  </p>
  <p>
  Type <tt>"help ttools opt=sysdoc"</tt> for a higher-level description of the 'ttools'
  package.
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  -->
  
