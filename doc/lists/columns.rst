.. _columns:

columns: Convert multicolumn file to separate files
===================================================

**Package: lists**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  columns filename numcols 
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>filename</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='filename' Line='filename' -->
  <dd>Name of the input table file.
  </dd>
  </dl>
  <dl>
  <dt><b>numcols</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='numcols' Line='numcols' -->
  <dd>The number of columns in the input file.
  </dd>
  </dl>
  <dl>
  <dt><b>outroot = <span style="font-family: monospace;">"col."</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='outroot' Line='outroot = "col."' -->
  <dd>Root name of the output column files.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  Task <i>columns</i> is used to reformat a multicolumn list file into separate
  files, such that one output file is created for each column in the input
  file.  It is used to break multicolumn tables into simple CL lists.
  Comment lines beginning with  the character <span style="font-family: monospace;">"#"</span> are ignored.  All data
  is transferred as text.  One file <b>outroot</b>n is produced for each
  column in the input table.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  Make 3 files named datacol.1, datacol.2 and datacol.3 from the 3 column
  table dtable:
  </p>
  <pre>
  
      cl&gt; columns dtable 3 outroot=datacol.
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  fields
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
