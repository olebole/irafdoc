.. _sort:

sort — Sort a text file
=======================

**Package: system**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  sort -- sort a file or the standard input
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  sort input_file
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input_file</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input_file' Line='input_file'>
  <DD>The text file to be sorted.  If the standard input is redirected the standard
  input is sorted.
  </DD>
  </DL>
  <DL>
  <DT><B>column = 0</B></DT>
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
  <DT><B>ignore_whitespace = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ignore_whitespace' Line='ignore_whitespace = no'>
  <DD>Ignore leading whitespace.  Useful only when column = 0 and the sort is
  non-numeric.
  </DD>
  </DL>
  <DL>
  <DT><B>numeric_sort = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='numeric_sort' Line='numeric_sort = no'>
  <DD>If set, make numerical (rather than ASCII text) comparisons.
  </DD>
  </DL>
  <DL>
  <DT><B>reverse_sort = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='reverse_sort' Line='reverse_sort = no'>
  <DD>If set, sort in reverse text/numeric order.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>Sort</I> sorts the contents of the given text file, or the
  standard input, either on a textual (based on the ASCII collating
  sequence), or on a numeric basis.  If a numeric sort is requested,
  and either field in any comparison is non-numeric, a string (ASCII)
  comparison will be made instead.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
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
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  Only one file can be sorted per call, and only one column or all columns can
  be used for the sort.  The current program is inefficient for large numeric
  sorting tasks because the same numeric field may be decoded into its
  corresponding binary value many times.
  </UL>
  <! EndSection:    'BUGS'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS'  >
  
