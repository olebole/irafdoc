.. _txtable:

txtable: Extract 2-D tables from rows of 3-D tables.
====================================================

**Package: nttools**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  txtable -- Extract rows from a 3-D table into separate 2-D tables.
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  txtable intable outtable
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  This task extracts one or more rows from a 3-D table and writes each row
  as a 2-D table. The input may be a filename template, including 
  wildcard characters, or the name of a file (preceded by an @ sign) containing 
  table names.  The output may be either a directory specification or a list 
  of table names. If the output is a list of tables then there must be the same 
  number of names in the input and output lists, and the names are taken in 
  pairs, one from input and one from output. The input and output tables must 
  not be the same.
  </p>
  <p>
  This task supports row/column selectors in the input table name. These
  may be used to select subsets of both rows and columns from the input table.
  If no selectors are used, all columns will be extracted, and the number
  of output tables will be the number of rows in the input table.
  Type 'help selectors' to see a description of the selector syntax. 
  </p>
  <p>
  Since one input table may generate several output tables, the task adopts
  the following naming scheme for these output tables: their names are
  built by appending a suffix to the name given in parameter <tt>"outtable"</tt>.
  The suffix has the form <tt>"_rXXXX"</tt>, where XXXX stands for the row number 
  in the input table. The suffix is appended before the file name extension.
  The task recognizes as valid table name extensions the values <tt>".tab"</tt>,
  <tt>".fits"</tt> and <tt>".fit"</tt>. Any other extension is assumed to be part of the root
  file name. If only one row is extracted, or in case of ASCII output, no 
  suffixing takes place.
  </p>
  <p>
  NOTE: Be careful when using a wildcard for the extension.
  If you have the files <tt>"table.tab"</tt> and <tt>"table.lis"</tt> in the current directory,
  for example, then the command <tt>"txtable tab* test/"</tt> would expand both files 
  to the subdirectory <tt>"test"</tt>.
  </p>
  <p>
  There are two forms of handling scalar columns in the input table. If
  task parameter <tt>"compact"</tt> is set to 'no', the corresponding column in the
  output table will have the scalar value in its first row, and all other
  rows will be filled with INDEF. If parameter <tt>"compact"</tt> is set to 'yes',
  scalar columns will be written into the header as a set of header keywords.
  These keywords can be used later by task 'titable' to re-insert the
  scalars as cell elements of a 3-D table.
  </p>
  <p>
  The task does not propagate array dimensionality when extracting arrays
  into columns in the output table. If dimensionality information exists
  in the 3-D table, that information is lost, that is, the table cell from
  the input table is written as a structureless, plain table column.
  </p>
  <p>
  The input row number is written to the header of the output table in
  keyword ORIG_ROW. This allows 'titable' to put the data back where 
  'txtable' got them from.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>intable [file name list/template]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='intable' Line='intable [file name list/template]' -->
  <dd>A list of one or more tables to be expanded. Row/column selectors are supported.
  </dd>
  </dl>
  <dl>
  <dt><b>outtable [file name template]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='outtable' Line='outtable [file name template]' -->
  <dd>Either a directory name or a list of output table names. The standard
  value <tt>"STDOUT"</tt> generates ASCII output that can be redirected to a file.
  </dd>
  </dl>
  <dl>
  <dt><b>(compact = yes) [boolean]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='' Line='(compact = yes) [boolean]' -->
  <dd>Write scalars as header keywords ?
  </dd>
  </dl>
  <dl>
  <dt><b>(verbose = yes) [boolean]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='' Line='(verbose = yes) [boolean]' -->
  <dd>Display names of input and output tables as files are processed ?
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  Extract columns named FLUX and WAVELENGTH from rows 11 to 13 of a 3-D table:
  </p>
  <pre>
  cl&gt; txtable "table.tab[c:FLUX,WAVELENGTH][r:row=(11:13)]" tableout
  </pre>
  <p>
  This will generate three tables named <tt>"tableout_r0011"</tt>, <tt>"tableout_r0012"</tt>
  and <tt>"tableout_r0013"</tt>.
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <!-- EndSection:   'BUGS' -->
  <h3>References</h3>
  <!-- BeginSection: 'REFERENCES' -->
  <p>
  This task was written by I. Busko.
  </p>
  <!-- EndSection:   'REFERENCES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  titable, selectors
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  -->
  
