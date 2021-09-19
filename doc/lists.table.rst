.. _table:

table: Format a list of words into a table
==========================================

**Package: lists**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  table -- format single column input into a table
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  table input_files
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input_files</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input_files' Line='input_files' -->
  <dd>List of files to be formatted, may be STDIN.
  </dd>
  </dl>
  <dl>
  <dt><b>first_col = 7</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='first_col' Line='first_col = 7' -->
  <dd>Offset to first column of table
  </dd>
  </dl>
  <dl>
  <dt><b>last_col = 0</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='last_col' Line='last_col = 0' -->
  <dd>Offset to last column of table.  The value <b>last_col</b> = 0 indicates 
  right margin.
  </dd>
  </dl>
  <dl>
  <dt><b>ncols = 0</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='ncols' Line='ncols = 0' -->
  <dd>Number of columns.  The value <b>ncols</b> = 0 indicates maximum that will fit.
  </dd>
  </dl>
  <dl>
  <dt><b>maxstrlen = 0</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='maxstrlen' Line='maxstrlen = 0' -->
  <dd>Maximum string length for table entry.  The value <b>maxstrlen</b> = 0
  indicates no limit.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  Task <b>table</b> reads a list of strings from the standard input or a 
  list of files and assembles a nicely formatted table.  If reading 
  from multiple input files, make a separate table for each.  There is no 
  fixed limit to the size of the table which can be formatted.  The table 
  is not sorted; this should be done as a separate operation if desired.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Format a file containing names into a two column table.  The table is 
  sorted alphabetically first.
  </p>
  <p>
  	cl&gt; sort names | table ncols=2
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  words, tokens
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
