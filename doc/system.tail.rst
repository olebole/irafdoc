.. _tail:

tail — Print the last few lines of a file
=========================================

**Package: system**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  tail -- print the last few lines of the specified files
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  tail files
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>files</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='files' Line='files'>
  <DD>A template specifying the files to be listed.
  </DD>
  </DL>
  <DL>
  <DT><B>nlines = 12</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nlines' Line='nlines = 12'>
  <DD>The number of lines to be printed.  If negative, the number
  of lines to be skipped, counting from the beginning of the file.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  For each file in the input file list, <I>tail</I> copies the last <I>nlines</I>
  of the file to the standard output.  If there is more than one file in the
  input file list, as one line header is printed before each file.
  If "<TT>nlines</TT>" is negative, then abs(nlines) lines are skipped, and the rest
  of the file is printed, i.e., the tail of the file is still printed, but
  the offset is measured from the beginning of the file rather than the end.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Prints the last 12 lines of each help file in the current directory.
  <P>
  	cl&gt; tail *.hlp
  <P>
  2. Print the last line of each help file.
  <P>
  	cl&gt; tail *.hlp nl=1
  <P>
  3. Prints the third through fifth lines of "<TT>file</TT>".  The same thing
  might be done (at least conceptually) by "<TT>head file,nlines=5</TT>"
  piped into "<TT>tail ,nlines=3</TT>".  However, <I>tail</I> does not work on STDIN.
  <P>
  <PRE>
  	cl&gt; tail file nl=-2 | head nl=3
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  <I>Tail</I> does not presently work on standard input, and therefore cannot
  be used in pipes.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  head
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
