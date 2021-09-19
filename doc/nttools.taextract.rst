.. _taextract:

taextract: Copy an array entry to a column of scalars in another table.
=======================================================================

**Package: nttools**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  taextract -- Copy an array entry from one table
  to a column of scalars in another.
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  taextract intable outtable row column
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  This task extracts one entry (presumably an array of values)
  at a specified row and column
  and writes it as a column of scalar values to another table.
  If the output table exists it will be written to in-place;
  otherwise, it will be created.
  </p>
  <p>
  By default, the same column name is used in both tables.
  If the output table and column already exist,
  the data in that column will be overwritten;
  otherwise, the column will be created.
  If the array size for the specified column in the input table is N,
  then the values will be written to rows 1 through N of the output table.
  If the output column already exists,
  and the output table contains more than N rows,
  then rows N+1 through the last will be set to INDEF for this column.
  </p>
  <p>
  The input row number is written to the header of the output table
  using keyword ORIG_ROW.
  This allows 'tainsert' to put the data back where 'taextract' got them from.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>intable [file name]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='intable' Line='intable [file name]' -->
  <dd>Name of the input table containing a column with array entries.
  It is not an error for the array length to be one.
  </dd>
  </dl>
  <dl>
  <dt><b>outtable [file name]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='outtable' Line='outtable [file name]' -->
  <dd>Name of the output table.
  If this table doesn't exist it will be created.
  If the table does exist the column will either be created or overwritten.
  The input and output tables may not be the same,
  and they may not be in the same file if FITS format is used.
  </dd>
  </dl>
  <dl>
  <dt><b>row [integer, min=1, max=INDEF]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='row' Line='row [integer, min=1, max=INDEF]' -->
  <dd>This is the row number in the input table.
  In the output table there will be as many rows
  as there are elements in the input table entry for 'column'.
  </dd>
  </dl>
  <dl>
  <dt><b>column [string]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='column' Line='column [string]' -->
  <dd>Column name.
  This is used to find the column in the input table,
  and by default the same name is used to create
  (or find, if it already exists)
  the column in the output table.
  See the description for 'outcolumn'.
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
  The 'datatype', 'colunits', and 'colfmt' parameters, by contrast,
  are only used when creating a new column.
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
  1. Extract the array from row 5, column <tt>"polar"</tt>, from table <tt>"array.tab"</tt>,
  putting the values in column <tt>"polar"</tt> of table <tt>"scalar.tab"</tt>.
  </p>
  <pre>
  at&gt; taextract array.tab scalar.tab 5 polar
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
  tainsert
  </p>
  <p>
  Type <tt>"help ttools opt=sysdoc"</tt> for a higher-level description of the 'ttools'
  package.
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  -->
  
