.. _tcopy:

tcopy: Copy tables.
===================

**Package: nttools**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  tcopy -- Copy tables.
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  tcopy intable outtable
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  This task is used to copy tables.  The input may be a general filename
  template, including wildcard characters or the name of a file (preceded
  by an @ sign) containing table names.  The output may be either a directory
  specification or a list of table names.  If the output is a list of tables
  then there must be the same number of names in the input and output lists,
  and the names are taken in pairs, one from input and one from output.
  The input and output tables must not be the same.
  This task will convert the format of the table
  if the output filename extension indicates it.
  For example, if the output filename extension is <tt>".fits"</tt>,
  the output table will be a fits file.
  If the output is redirected or piped,
  it will be written to a text table.
  </p>
  <p>
  NOTE: Be careful when using a wildcard for the extension.
  If you have the files <tt>"table.tab"</tt> and <tt>"table.lis"</tt> in the current directory,
  for example, then the command <tt>"tcopy tab* test/"</tt> would copy both files
  to the subdirectory <tt>"test"</tt>.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>intable [file name template]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='intable' Line='intable [file name template]' -->
  <dd>A list of one or more tables to be copied.
  </dd>
  </dl>
  <dl>
  <dt><b>outtable [file name template]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='outtable' Line='outtable [file name template]' -->
  <dd>Either a directory name or a list of output table names.
  If 'outtable' is not a directory,
  the number of input tables and output tables must be the same.
  An exception to this rule is that if 'outtable' is a FITS file
  (i.e. an existing FITS file, or the name ends in <tt>".fits"</tt>)
  then multiple input tables can be copied to one output file.
  </dd>
  </dl>
  <dl>
  <dt><b>(verbose = yes) [boolean]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='' Line='(verbose = yes) [boolean]' -->
  <dd>Display names of input and output tables as they are copied?
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1.  To simply copy a table:
  </p>
  <pre>
      tt&gt; tcopy table.tab tablecopy.tab
  </pre>
  <p>
  2.  To copy one or more tables, possibly changing table type:
  </p>
  <pre>
      tt&gt; tcopy table1.tab,table2.tab a.fits,b.tab
      tt&gt; tcopy a.fits,b.tab a.tab,b.fits
      tt&gt; tcopy a.fits &gt; a.txt
  </pre>
  <p>
  The number of input and output tables must be the same.
  In the third case,
  <tt>"a.txt"</tt> will be a text file because
  the output table name was <tt>"STDOUT"</tt>
  (the name was implicitly set, in this case,
  because the output was redirected.)
  </p>
  <p>
  3.  To copy a set of tables to a new directory:
  </p>
  <pre>
      tt&gt; tcopy table*.tab directory
      		or
      tt&gt; tcopy table*.tab directory$
      		or
      tt&gt; tcopy table*.tab osdirectory
  </pre>
  <p>
  where <tt>"directory"</tt> is an IRAF environment variable for a directory name,
  and <tt>"osdirectory"</tt> is an operating system directory name
  (e.g., <tt>"/user/me/"</tt> in UNIX).
  </p>
  <p>
  4.  To copy only specified extensions of a FITS file:
  </p>
  <pre>
      tt&gt; tcopy xyz.fits[3],xyz.fits[5] b.fits
  </pre>
  <p>
  If <tt>"b.fits"</tt> did not already exist,
  it would be created and would then contain two table extensions.
  If it did already exist,
  the two extensions would be appended.
  Note that the number of input and output files are not the same;
  this is OK because the output is a FITS file
  and can therefore contain multiple table extensions.
  </p>
  <p>
  5.  The input and/or output may be redirected:
  </p>
  <pre>
      tt&gt; dir l+ | tproject columns=c7,c3 | tcopy dir.tab &gt; verbose.lis
  </pre>
  <p>
  <tt>"verbose.lis"</tt> contains just the one line <tt>"# STDIN -&gt; dir.tab"</tt>,
  and <tt>"dir.tab"</tt> has the output of 'tproject', the file names and sizes.
  </p>
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
  tdelete
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  -->
  
