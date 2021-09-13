.. _tee:

tee — Tee the standard output into a file
=========================================

**Package: system**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  tee -- tee the standard output to a file
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  tee file
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>file</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='file' Line='file'>
  <DD>The name of the output file.
  </DD>
  </DL>
  <DL>
  <DT><B>out_type = "<TT>text</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='out_type' Line='out_type = "text"'>
  <DD>The type of output file to be created, either "<TT>text</TT>" or "<TT>binary</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>append = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='append' Line='append = no'>
  <DD>If set, append to an existing file, otherwise create a new file.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>Tee</I> copies its input to both the standard output and the named file.
  Its primary use is in pipes where one wants to capture some intermediate output.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. The results of the <I>set</I> command are captured in the file "<TT>temp</TT>",
  and are also passed on to the "<TT>match</TT>" command.  The result is
  a "<TT>temp</TT>" file of perhaps 100 lines, with the output to the screen
  only around 5 lines.
  <P>
  	cl&gt; set | tee temp | match tty
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  Since the processes in an IRAF pipe execute serially rather than concurrently,
  the teed output will not appear until all tasks to the left have completed.
  </UL>
  <! EndSection:    'BUGS'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS'  >
  
