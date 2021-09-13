sort — Sort a text file
=======================

**Package: system**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>sort (Mar87)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>system</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>sort (Mar87)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>sort</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  sort -- sort a file or the standard input
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  sort input_file
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input_file">input_file</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input_file' Line='input_file'>
  <DD>The text file to be sorted.  If the standard input is redirected the standard
  input is sorted.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_column">column = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='column' Line='column = 0'>
  <DD>If 0, sort entire text lines, else sort based on data/text starting
  in the specified column.  Columns are delimited by whitespace.  Thus,
  <PRE>
  	12   abc   34   56
  </PRE>
  has four columns, "<TT>abc</TT>" being in the second.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ignore_whitespace">ignore_whitespace = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ignore_whitespace' Line='ignore_whitespace = no'>
  <DD>Ignore leading whitespace.  Useful only when column = 0 and the sort is
  non-numeric.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_numeric_sort">numeric_sort = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='numeric_sort' Line='numeric_sort = no'>
  <DD>If set, make numerical (rather than ASCII text) comparisons.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_reverse_sort">reverse_sort = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='reverse_sort' Line='reverse_sort = no'>
  <DD>If set, sort in reverse text/numeric order.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>Sort</I> sorts the contents of the given text file, or the
  standard input, either on a textual (based on the ASCII collating
  sequence), or on a numeric basis.  If a numeric sort is requested,
  and either field in any comparison is non-numeric, a string (ASCII)
  comparison will be made instead.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Sort the output of the set command into alphabetic (ASCII collating)
  order.
  <P>
  	cl&gt; set | sort
  <P>
  2. Sort the contents of "<TT>file</TT>", in reverse ASCII order, ignoring the
  contents of columns 1 through 4.
  <P>
  	cl&gt; sort file rev+ col=5
  <P>
  3. Print a long form directory listing with the files sorted by size,
  largest files first.
  <P>
  	cl&gt; dir | sort num+ rev+ col=3
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  Only one file can be sorted per call, and only one column or all columns can
  be used for the sort.  The current program is inefficient for large numeric
  sorting tasks because the same numeric field may be decoded into its
  corresponding binary value many times.
  </UL>
  <! EndSection:    'BUGS'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS'  >
  
  </BODY>
  </HTML>