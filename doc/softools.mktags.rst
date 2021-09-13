.. _mktags:

mktags — Tag all procedure declarations in a set of files
=========================================================

**Package: softools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  mktags -- tag all procedure declarations in a set of files
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  mktags
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>files = "<TT>*.x</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='files' Line='files = "*.x"'>
  <DD>The files to be tagged, e.g., "<TT>*.x</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>listing = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='listing' Line='listing = no'>
  <DD>If this switch is enabled a sorted list of all procedures declared in the
  set of files will be printed on the standard output, giving the procedure
  name, line and file number, and procedure declaration on each output line.
  </DD>
  </DL>
  <DL>
  <DT><B>tags = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='tags' Line='tags = yes'>
  <DD>If this switch is enabled a "<TT>tags</TT>" file will be written in the current
  directory for use with the VI editor.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The named files are scanned for procedure declarations.  Each such declaration
  found is buffered internally.  When all files have been scanned the internal
  tag database is sorted and the output files are generated.  Two types of
  output are provided:
  <DL>
  <DT><B></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line=' '>
  <DD><DL>
  <DT><B>[1]</B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='' Line='[1]'>
  <DD>A summary of all procedures defined in the given set of files may be printed
  on the standard output.  This output may be used as a printed index to manually
  find procedures in the given file set.
  </DD>
  </DL>
  <DL>
  <DT><B>[2]</B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='' Line='[2]'>
  <DD>A "<TT>tags</TT>" format database file (a text file) may be written.  This file is
  read by the VI editor when a command of the form "<TT>:ta tag</TT>" is entered.
  This command is used to edit procedures regardless of the file in which they
  reside.  For example, to edit procedure "<TT>maxmin</TT>", enter command "<TT>:ta maxmin</TT>"
  when in VI.
  </DD>
  </DL>
  </DD>
  </DL>
  <P>
  <P>
  By default the operation of <I>mktags</I> is to silently update the tags
  database.  If a printed listing is desired the <I>listing</I> switch must
  be enabled.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  A fixed amount of storage is allocated internally and overflow will occur if
  there are too many tags (procedures) or if there is too much text (the string
  buffer will overflow).
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'BUGS' 'SEE ALSO'  >
  
