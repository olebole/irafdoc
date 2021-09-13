.. _table:

table — Format a list of words into a table
===========================================

**Package: lists**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  table -- format single column input into a table
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  table input_files
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input_files</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input_files' Line='input_files'>
  <DD>List of files to be formatted, may be STDIN.
  </DD>
  </DL>
  <DL>
  <DT><B>first_col = 7</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='first_col' Line='first_col = 7'>
  <DD>Offset to first column of table
  </DD>
  </DL>
  <DL>
  <DT><B>last_col = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='last_col' Line='last_col = 0'>
  <DD>Offset to last column of table.  The value <B>last_col</B> = 0 indicates 
  right margin.
  </DD>
  </DL>
  <DL>
  <DT><B>ncols = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ncols' Line='ncols = 0'>
  <DD>Number of columns.  The value <B>ncols</B> = 0 indicates maximum that will fit.
  </DD>
  </DL>
  <DL>
  <DT><B>maxstrlen = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maxstrlen' Line='maxstrlen = 0'>
  <DD>Maximum string length for table entry.  The value <B>maxstrlen</B> = 0
  indicates no limit.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Task <B>table</B> reads a list of strings from the standard input or a 
  list of files and assembles a nicely formatted table.  If reading 
  from multiple input files, make a separate table for each.  There is no 
  fixed limit to the size of the table which can be formatted.  The table 
  is not sorted; this should be done as a separate operation if desired.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Format a file containing names into a two column table.  The table is 
  sorted alphabetically first.
  <P>
  	cl&gt; sort names | table ncols=2
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  words, tokens
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
