.. _eparam:

eparam — Edit parameters of a task
==================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  eparam -- edit a task's parameters
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  eparam task [task ...]
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>task</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='task' Line='task'>
  <DD>The name of the task whose parameter set is to be edited.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <I>eparam</I> command calls up an interactive screen editor
  to edit the parameters of the named task or tasks.  The syntax of the
  page editor is controlled by the environment variable `editor' which
  may have the values "<TT>edt</TT>", "<TT>emacs</TT>", or "<TT>vi</TT>".  The user may also customize
  the editor by copying the associated "<TT>dev$*.ed</TT>" file to their home
  directory, and editing the file.
  <P>
  The CL parameter "<TT>epinit</TT>" may be used to set the following options:
  <DL>
  <DT><B>[no]standout</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='[no]standout'>
  <DD>Enables or disables use of standout mode (reverse video) in the display.
  </DD>
  </DL>
  <DL>
  <DT><B>[no]showall</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='[no]showall'>
  <DD>Controls whether or not hidden parameters are displayed and edited.
  </DD>
  </DL>
  <P>
  The <I>eparam</I> task may be used to edit either ordinary task parameter
  sets, or named parameter files.
  The presence or absence of a <B>.par</B> filename extension is used to
  determine whether an operand is a taskname or a filename.  For example,
  <P>
  	cl&gt; eparam skypars.par
  <P>
  will edit the parameter <I>file</I> <B>skypars.par</B> in the current directory,
  whereas
  <P>
  	cl&gt; eparam skypars
  <P>
  will edit the parameter set for the pset-task <I>skypars</I>.
  Lastly, since <I>spypars</I> is a pset-task, we could just type
  <P>
  	cl&gt; skypars
  <P>
  to edit or review the contents of the pset.
  <P>
  The parameter file <B>skypars.par</B> in the above example would probably be
  created using the new colon-command extensions to eparam.  The original
  eparam supported only single keystroke editing commands.  The new colon
  commands are used to enter command lines of arbitrary length to be processed
  by eparam.
  <P>
  A colon command is entered by typing the colon character (`<B>:</B>') while
  the cursor is positioned to the starting column of any value field of the
  parameter set being edited.  The colon character is not recognized as a
  special character beyond column one, e.g., when entering the string value
  of a parameter.  When colon command mode is entered, the colon character
  will be echoed at the start of the bottom line on the screen, and the cursor
  will move to the character following the colon, waiting for the command to
  be entered.  The command is read in raw mode, but the usual delete,
  &lt;ctrl/c&gt;, &lt;ctrl/u&gt;, etc. sequences are recognized.
  <P>
  The following eparam colon commands are currently supported.  All commands
  are carefully error checked before being executed to avoid having eparam
  abort with a stack trace.  An illegal operation causes colon command entry
  mode to be exited, leaving an error message on the command entry line.
  All commands which cause editing of the current pset to terminate may include
  the <B>!</B> character to avoid updating the current pset before reading in
  the new one or exiting eparam.  The default is to update the current pset.
  In all cases, <I>pset</I> may be either the name of a task or the name of a
  parameter file.  Parameter files are always indicated by a <B>.par</B>
  extension, even though the actual file may be a <B>.cl</B> file:
  only <B>.par</B> files will be written, although either type of file may be
  read.
  <P>
  <DL>
  <DT><B>:e[!] [pset]</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line=':e[!] [pset]'>
  <DD>Edit a new pset.  If <I>pset</I> is omitted and the cursor was positioned to
  a pset parameter when the colon command was entered then eparam descends into
  the referenced pset; when editing of the sub-pset is complete eparam returns
  to editing the higher level pset at the point at which the '<B>:e</B>'
  command was entered.  If a pset is named the editor context is switched to
  the new pset, updating the current pset first unless the '<B>:e!</B>' command
  was given.
  </DD>
  </DL>
  <DL>
  <DT><B>:q[!]</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line=':q[!]'>
  <DD>Exit eparam for the current pset; equivalent to a &lt;ctrl/z&gt;.  The variant
  '<B>:q!</B>' causes eparam to be exited without updating the current pset.  
  Entering this command when editing a sub-pset causes an exit to the higher
  level pset.  To abort eparam entirely without updating anything, &lt;ctrl/c&gt;
  should be used.
  </DD>
  </DL>
  <DL>
  <DT><B>:r[!] [pset]</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line=':r[!] [pset]'>
  <DD>Read in a new pset.  If the command is '<B>:r</B>', an error message is
  printed.  If the command is '<B>:r!</B>' the pset currently being edited
  is reread, canceling any modifications made since the last update.
  If a pset is specified the contents of the named pset are merged into the
  current pset, i.e., the named pset is loaded into the current pset,
  overwriting the contents of the current pset.
  The command '<B>:r pfile.par</B>' is commonly used to load a pset formerly
  saved in a user file with '<B>:w pfile.par</B>' into the UPARM version of
  the parameter set for a task.
  </DD>
  </DL>
  <DL>
  <DT><B>:w[!] pset</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line=':w[!] pset'>
  <DD>Write or update a pset.  If <I>pset</I> is omitted the pset currently being
  edited is updated on disk.  If <I>pset</I> is given it should normally be the
  name of a parameter file to be written.  If the file exists an error message
  will be printed unless the command '<B>:w! pfile.par</B>' is given to force
  the file to be overwritten.
  </DD>
  </DL>
  <DL>
  <DT><B>:g[o][!]</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line=':g[o][!]'>
  <DD>Run the task.  Eparam exits, updating the pset and running the task whose pset
  was being edited.  This is implemented by pushing a command back into the input
  stream of the task which called eparam, hence if eparam was called in a script
  or with other commands on the same line, execution may be delayed until these
  other commands have been edited.  The feature works as expected when used
  interactively.  Since the run command is pushed back into the command input 
  stream it will appear in the history record and in any log files.
  </DD>
  </DL>
  <P>
  To get out of colon command mode without doing anything, simply type delete
  until the colon prompt is deleted and the cursor returns to the parameter
  it was positioned to when colon command entry mode was entered.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Set standout mode and disable the editing of hidden parameters (leaving
  only the positional parameters).
  <P>
  	cl&gt; epinit = "<TT>standout noshowall</TT>"
  <P>
  2. Edit the parameters for the <I>delete</I> task.
  <P>
  	cl&gt; ep delete
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  lparam, ehistory
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
