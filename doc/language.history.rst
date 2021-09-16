.. _history:

history — Display  commands previously executed
===============================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  history -- display the last few commands
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  history [[-]ncommands]
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>ncommands</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ncommands' Line='ncommands'>
  <DD>The number of commands to be displayed.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <I>history</I> task prints a list of the last few commands executed.
  Only commands which terminated normally are included.
  The number of commands to be printed may be specified on the command line
  if desired.  If the number is preceded by a minus sign the default
  number of lines is not changed, otherwise <I>history</I> will take the
  value given as the new default number of commands to be printed.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Print the last few commands.
  	
  	cl&gt; history
  <P>
  2. Print the entire history list.
  <P>
  	cl&gt; history -999
  <P>
  3. Change the default number of history lines to be printed to 5 (and print
  the last five commands).
  <P>
  	cl&gt; history 5
  <P>
  4. Save the history in the file "<TT>commands</TT>".
  <P>
  	cl&gt; history -999 &gt; commands
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  ehistory
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
