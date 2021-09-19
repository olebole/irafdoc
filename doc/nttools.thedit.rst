.. _thedit:

thedit: Edit or print table header keywords.
============================================

**Package: nttools**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  thedit -- Edit or view keyword values in tables.
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  thedit table keywords value
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  This table header editor can be used to add, delete, edit,
  or just print the values of table header keywords.
  </p>
  <p>
  Although this task was based on 'hedit',
  there are significant differences.
  The 'add', 'verify', and 'update' parameters of 'hedit'
  are not included in 'thedit'.
  If a specified keyword does not already exist,
  then it will be added
  (equivalent to add=yes in 'hedit').
  If a keyword does not exist,
  and the value expression is <tt>"."</tt>,
  a warning will be printed
  ('hedit' is silent in this case).
  </p>
  <p>
  Such parameters as the number of rows or columns in the table
  are stored differently in FITS, STSDAS, and text tables.
  The following special <tt>"keywords"</tt> can be used
  to reference such information regardless of table type.
  These may be used in the 'keywords' parameter when value=<tt>"."</tt>,
  or they can be used in the 'value' parameter as part of an expression.
  </p>
  <pre>
      i_table   string    table name (may include extension ID)
      i_file    string    name of the file containing the table
      i_ctime   string    file modification (or creation) time
      i_nrows   int       number of rows in the table
      i_ncols   int       number of columns in the table
      i_npar    int       number of keywords in the table header
      i_type    string    table type
  </pre>
  <p>
  'thedit' supports two of the special operands
  that are available in 'hedit':  <tt>"$"</tt> and <tt>"$I"</tt>.
  When 'value' is an expression,
  <tt>"$"</tt> gives the value of the current keyword.
  <tt>"$I"</tt> is equivalent to <tt>"i_table"</tt>,
  the name of the current table.
  <tt>"$I"</tt> can be used as a keyword or as part of an expression.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>table [file name template]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='table' Line='table [file name template]' -->
  <dd>A list of tables for which keywords are to be edited or printed.
  If 'value' is <tt>"."</tt>, each table will be opened read-only;
  otherwise, each table will be opened read-write.
  </dd>
  </dl>
  <dl>
  <dt><b>keywords [string]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='keywords' Line='keywords [string]' -->
  <dd>One or more keywords, separated by commas and/or blanks,
  which are to be added, modified, or printed.
  If the value expression (see 'value') is not <tt>"."</tt>,
  any keyword in 'keywords' that is not already present
  will be added to the header.
  Wildcards are supported; however,
  the <tt>"@filename"</tt> syntax is not supported.
  Do not use wildcard or other special characters
  if a keyword is to be added to the header.
  </dd>
  </dl>
  <dl>
  <dt><b>value = <tt>"."</tt> [string]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='value' Line='value = "." [string]' -->
  <dd>This is the value to be assigned to each keyword in 'keywords'.
  The special value <tt>"."</tt> means that
  the keywords should be printed rather than edited,
  and in this case the table will be opened read-only.
  If 'value' is not equal to <tt>"."</tt>,
  the same value will be assigned to all the keywords
  matching the template 'keywords'.
  In order to set a keyword value to <tt>"."</tt> or <tt>","</tt>,
  specify the value as <tt>"\."</tt> or <tt>"\,"</tt> respectively.
  (Note that if given on the command line,
  the quotes are required in this case.)  Requiring <tt>","</tt> to be escaped
  was added as protection against accidentally typing <tt>","</tt> instead of <tt>"."</tt>.
  As with 'hedit',
  a general expression may be given for 'value'
  by enclosing the expression in parentheses.
  The expression may include constants and/or keyword names;
  it will be evaluated and then assigned to each keyword in 'keywords'.
  Note that if delete = yes, then 'value' will be ignored.
  </dd>
  </dl>
  <dl>
  <dt><b>(delete = no) [bool]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='' Line='(delete = no) [bool]' -->
  <dd>If delete = yes, the specified keywords will be deleted.
  All the keywords listed in 'keywords' will be deleted,
  for each table in 'table'.
  </dd>
  </dl>
  <dl>
  <dt><b>(show = yes) [bool]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='' Line='(show = yes) [bool]' -->
  <dd>Print a record of each edit operation?
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1.  Display all the header keywords (except blank) in <tt>"example.tab"</tt>.
  </p>
  <pre>
      tt&gt; thedit example.tab * .
  </pre>
  <p>
  2.  Display only the special keywords for <tt>"timetag.fits[events]"</tt>.
  </p>
  <pre>
      tt&gt; thedit timetag.fits[events] i_* .
  
      timetag.fits[events],i_table = timetag.fits[events]
      timetag.fits[events],i_file = timetag.fits
      timetag.fits[events],i_ctime = "Wed 12:07:58 31-May-2000"
      timetag.fits[events],i_nrows = 337824
      timetag.fits[events],i_ncols = 6
      timetag.fits[events],i_npar = 58
      timetag.fits[events],i_type = "fits, binary"
  </pre>
  <p>
  3.  Print all HISTORY keywords in <tt>"example.txt"</tt>.
  </p>
  <pre>
      tt&gt; thedit example.txt history .
  </pre>
  <p>
  4.  Add a new HISTORY keyword to <tt>"example.tab"</tt>.
  </p>
  <pre>
      tt&gt; thedit example.tab history \<br>
      "('file name is ' // i_file) // '; number of rows = ' // str (i_nrows)"
  </pre>
  <p>
  5.  Increment the value of COUNT.
  </p>
  <pre>
      tt&gt; thedit example.tab count "($ + 1)"
  </pre>
  <p>
  6.  Delete all HISTORY and COMMENT keywords in <tt>"example.fits[1]"</tt>.
  </p>
  <pre>
      tt&gt; thedit example.fits history,comment delete+
  </pre>
  <p>
  7.  Evaluate a simple expression
  and assign the result to keyword WAVELEN.
  Keywords TCRVL1, TCDLT1, and NELEM
  are assumed to be already present in the header.
  </p>
  <pre>
      tt&gt; thedit example.fits wavelen "(tcrvl1 + tcdlt1 * nelem/2.)"
  </pre>
  <p>
  8.  A keyword can be renamed by using a two-step process,
  first creating a new keyword with the old value, and then
  deleting the old keyword.
  Note that while this procedure does copy the value,
  the comment will be lost.
  (The <tt>"k"</tt> instruction in 'tupar' can also be used to rename a keyword.)
  </p>
  <pre>
      tt&gt; thedit example.tab newkey "(oldkey)"
      tt&gt; thedit example.tab oldkey delete+
  </pre>
  <p>
  9.  The primary header or an image extension of a FITS file
  can also be opened as a table in order to access the keywords.
  </p>
  <pre>
      tt&gt; thedit o47s01kdm_raw.fits[0] rootname .
      tt&gt; thedit o47s01kdm_flt.fits[1] bunit "COUNTS/S"
  </pre>
  <p>
  10.  This could have been a big mistake.
  </p>
  <pre>
      tt&gt; thedit abc.fits[1] * ,
  
      ERROR: In order to set a keyword value to <tt>','</tt> you must use value='\,'
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  Expressions are evaluated using EVEXPR,
  which does not support double precision.
  </p>
  <p>
  Header lines with keyword = '        ' cannot be displayed.
  </p>
  <p>
  The 'value' parameter is of type string,
  and 'thedit' interprets the value
  to determine what data type to use
  when writing the value to the table.
  This can fail when a value appears to be a number
  but really should be treated as a string.
  For example, a date and time could be written as <tt>"19940531:11515000"</tt>.
  'thedit' would interpret this as hours and minutes (HH:MMss)
  and convert the value to 1994053. + 11515000./60.
  A workaround for this case is to use 'tupar' instead of 'thedit';
  use the <tt>"pt"</tt> instruction, meaning put a keyword of type text.
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>References</h3>
  <!-- BeginSection: 'REFERENCES' -->
  <p>
  This task was written by Phil Hodge,
  based on the 'hedit' task.
  </p>
  <!-- EndSection:   'REFERENCES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  hedit, tupar
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  -->
  
