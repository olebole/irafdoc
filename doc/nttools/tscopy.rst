.. _tscopy:

tscopy: Copy row/column subsets of tables using selectors.
==========================================================

**Package: nttools**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  tscopy intable outtable
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  This task is used to copy tables.  The input may be a filename
  template, including wildcard characters or the name of a file (preceded
  by an @ sign) containing table names.  The output may be either a directory
  specification or a list of table names.  If the output is a list of tables
  then there must be the same number of names in the input and output lists,
  and the names are taken in pairs, one from input and one from output.
  The input and output tables must not be the same.
  </p>
  <p>
  This task supports row/column selectors in the input table name. These
  may be used to select subsets of both rows and columns from the input table.
  Type 'help selectors' to see a description of the selector syntax. 
  </p>
  <p>
  NOTE: Be careful when using a wildcard for the extension.
  If you have the files 'table.tab' and 'table.lis' in the current directory,
  for example, then the command <span style="font-family: monospace;">"tscopy tab* test/"</span> would copy both files to the subdirectory
  'test'.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>intable [file name template]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='intable' Line='intable [file name template]' -->
  <dd>A list of one or more tables to be copied. Row/column selectors are supported.
  </dd>
  </dl>
  <dl>
  <dt><b>outtable [file name template]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='outtable' Line='outtable [file name template]' -->
  <dd>Either a directory name or a list of output table names. The standard
  value <span style="font-family: monospace;">"STDOUT"</span> generates ASCII output that can be redirected to a file.
  </dd>
  </dl>
  <dl>
  <dt><b>(verbose = yes) [boolean]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='' Line='(verbose = yes) [boolean]' -->
  <dd>Display names of input and output tables as files are copied?
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. To simply copy a table:
  </p>
  <pre>
        cl&gt; tscopy table tablecopy
  </pre>
  <p>
  2. To copy a table into an ASCII table:
  </p>
  <pre>
        cl&gt; tscopy table STDOUT &gt; table.txt
  </pre>
  <p>
  3. To copy several tables:
  </p>
  <pre>
        cl&gt; tscopy table1,table2,tab67 a,b,c
        cl&gt; tscopy tab*.tab a,b,c
  </pre>
  <p>
  In the latter case the extension is given explicitly in case there
  are other files beginning with <span style="font-family: monospace;">"tab"</span> that are not tables; there must
  be exactly three tables beginning with <span style="font-family: monospace;">"tab"</span> because the output list
  has three names.
  </p>
  <p>
  4. To copy a set of tables to a new directory:
  </p>
  <pre>
        cl&gt; tscopy table*.tab directory
  			or
        cl&gt; tscopy table*.tab directory$
  			or
        cl&gt; tscopy table*.tab osdirectory
  </pre>
  <p>
  where <span style="font-family: monospace;">"directory"</span> is an IRAF environment variable for a directory name,
  and <span style="font-family: monospace;">"osdirectory"</span> is an operating system directory name
  (e.g., <span style="font-family: monospace;">"/user/me/"</span> in UNIX).
  </p>
  <p>
  5. To copy a subset of rows and columns:
  </p>
  <pre>
        cl&gt; tscopy "table.tab[c:wave,flux][r:wave=(4000:5000)]" tableout
  </pre>
  <p>
  This command will copy only columns named <span style="font-family: monospace;">"wave"</span> and <span style="font-family: monospace;">"flux"</span> from the input
  table to the output. It will also select and copy only the rows in which
  the <span style="font-family: monospace;">"wave"</span> value lies between 4000 and 5000.
  </p>
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
  selectors
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  -->
  
