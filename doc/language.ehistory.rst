.. _ehistory:

ehistory — Edit history file to re-execute commands
===================================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  ehistory -- edit and re-execute previous commands
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  ehistory (or just "<TT>e</TT>")
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  None.
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <I>ehistory</I> command calls up a screen editor to edit previously
  executed commands, executing the edited command when return is typed.
  Interrupt (e.g., &lt;ctrl/c&gt; may be used to escape from the editor at any time.
  The type of editor commands recognized is determined by the value of the
  CL environment variable <I>editor</I>, which may currently be set to
  "<TT>edt</TT>", "<TT>emacs</TT>", or "<TT>vi</TT>".
  <P>
  After the <I>ehistory</I> command is entered, the previous command is
  displayed at the bottom of the terminal.  If the previous command was
  a compound statement, or if it extended over more than one line,
  all the lines of the command will be displayed.  To reach a different
  command simply enter the appropriate cursor movement keys for the editor type
  being used.  When the cursor attempts to move above the current command
  the previous command will be displayed.  Similarly when it attempts
  to move below, the next command will appear.  Hitting the return
  key will execute the command currently being edited.
  <P>
  The CL parameter "<TT>ehinit</TT>" may be used to set the following options:
  <DL>
  <DT><B>[no]standout</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='[no]standout'>
  <DD>Controls whether the command to be edited is displayed in reverse or
  normal video.
  </DD>
  </DL>
  <DL>
  <DT><B>eol</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='eol' Line='eol'>
  <DD>The editor is entered with the cursor positioned to be end of the command line.
  </DD>
  </DL>
  <DL>
  <DT><B>bol</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='bol' Line='bol'>
  <DD>The editor is entered with the cursor positioned to be beginning of the command
  line.
  </DD>
  </DL>
  <DL>
  <DT><B>[no]verify</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='[no]verify'>
  <DD>If <I>verify</I> is specified, <I>ehistory</I> will be automatically entered
  when history commands are entered to recall and execute previous commands.
  If <I>noverify</I> is specified, the commands are recalled and immediately
  executed.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Set no standout and verify modes. 
  <P>
  	cl&gt; ehinit = "<TT>nostandout verify</TT>".
  <P>
  2. Recall the last "<TT>xc</TT>" command from the history list and edit it.
  If <I>verify</I> were not enabled the command would simply be repeated.
  <P>
  	cl&gt; ^xc
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  The command editor really only works well for single line commands;
  multiline command blocks are not easily edited at present.
  VI is poorly emulated at present since only control code editor commands
  are possible.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  eparam
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
