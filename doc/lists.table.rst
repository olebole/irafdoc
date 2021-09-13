table — Format a list of words into a table
===========================================

**Package: lists**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>table (Jan86)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>lists</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>table (Jan86)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>table</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  table -- format single column input into a table
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  table input_files
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input_files">input_files</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input_files' Line='input_files'>
  <DD>List of files to be formatted, may be STDIN.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_first_col">first_col = 7</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='first_col' Line='first_col = 7'>
  <DD>Offset to first column of table
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_last_col">last_col = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='last_col' Line='last_col = 0'>
  <DD>Offset to last column of table.  The value <B>last_col</B> = 0 indicates 
  right margin.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ncols">ncols = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ncols' Line='ncols = 0'>
  <DD>Number of columns.  The value <B>ncols</B> = 0 indicates maximum that will fit.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_maxstrlen">maxstrlen = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maxstrlen' Line='maxstrlen = 0'>
  <DD>Maximum string length for table entry.  The value <B>maxstrlen</B> = 0
  indicates no limit.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Task <B>table</B> reads a list of strings from the standard input or a 
  list of files and assembles a nicely formatted table.  If reading 
  from multiple input files, make a separate table for each.  There is no 
  fixed limit to the size of the table which can be formatted.  The table 
  is not sorted; this should be done as a separate operation if desired.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Format a file containing names into a two column table.  The table is 
  sorted alphabetically first.
  <P>
  	cl&gt; sort names | table ncols=2
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  words, tokens
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>