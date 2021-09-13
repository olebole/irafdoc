.. _head:

head — Print the first few lines of a text file
===============================================

**Package: system**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  head -- print the first few lines of the specified files
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  head files
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>files</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='files' Line='files'>
  <DD>The list of files to be dealt with, quite possibly given as
  a template, such a "<TT>image*</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>nlines = 12</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nlines' Line='nlines = 12'>
  <DD>The number of lines to be printed.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>Head</I> prints, on the standard output, the first <I>nlines</I> of each
  file that matches the given file list.  If the file list has more than one
  name in it, a short header precedes each listing.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Print the first 12 lines of each help file in the current directory.
  <P>
  	cl&gt; head *.hlp
  <P>
  2. Print the first line of each help file.
  <P>
  	cl&gt; head *.hlp nl=1
  <P>
  3. Print the most recently defined <I>set</I> environment definitions.
  <P>
  	cl&gt; set | head
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  tail, page
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
