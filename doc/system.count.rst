.. _count:

count — Count the number of lines, words, characters in a text file
===================================================================

**Package: system**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  count -- determine number of lines, words and characters in a file
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  count files
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>files</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='files' Line='files'>
  <DD>A template specifying the files to be examined.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  For each file, count determines the number of lines, words, and
  characters in the file.  A word is defined as a sequence of characters
  delimited by one or more blanks or tabs, or by the end of a line.
  If <I>count</I> is run on more than one file, each output line is identified
  by the file name, and a final output line gives the total number
  of lines, words, and characters in all files.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Count the number of lines, words and characters in all files in the
  current directory with the extensions "<TT>.x</TT>" and "<TT>.h</TT>".
  <P>
  	cl&gt; count *.[xh]
  <P>
  2. Count the number of .x files in the current directory.
  <P>
  	cl&gt; dir *.x op=1 | count
  <P>
  3. Count the number of <I>set</I> environment definitions.
  <P>
  	cl&gt; set | count
  <P>
  4. Count the number of references to the READ function in all .x files in
  the current directory.
  <P>
  	cl&gt; match "<TT>read#(</TT>" *.x | count
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  directory
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
