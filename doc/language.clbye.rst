.. _clbye:

clbye — A cl followed by a bye (used to save file descriptors)
==============================================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  <PRE>
  cl    -- call the CL as a task
  clbye -- like cl(), but closes current script file too
  </PRE>
  </UL>
  <! EndSection:   'NAME'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>gcur = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='gcur' Line='gcur = ""'>
  <DD>Global graphics cursor.
  </DD>
  </DL>
  <DL>
  <DT><B>imcur = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='imcur' Line='imcur = ""'>
  <DD>Global image cursor.
  </DD>
  </DL>
  <DL>
  <DT><B>abbreviate = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='abbreviate' Line='abbreviate = yes'>
  <DD>Permits minimum match abbreviations of task and parameter names (disabled
  within scripts).
  </DD>
  </DL>
  <DL>
  <DT><B>echo = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='echo' Line='echo = no'>
  <DD>Echo all commands received by the CL on the terminal.
  </DD>
  </DL>
  <DL>
  <DT><B>ehinit = "<TT>standout eol noverify</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ehinit' Line='ehinit = "standout eol noverify"'>
  <DD>Ehistory options string.  (See "<TT>ehistory</TT>")
  </DD>
  </DL>
  <DL>
  <DT><B>epinit = "<TT>standout noshowall</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='epinit' Line='epinit = "standout noshowall"'>
  <DD>Eparam options string.  (See "<TT>eparam</TT>")
  </DD>
  </DL>
  <DL>
  <DT><B>keeplog = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='keeplog' Line='keeplog = no'>
  <DD>Keep a log of all CL commands.
  </DD>
  </DL>
  <DL>
  <DT><B>logfile = "<TT>uparm$logfile</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logfile' Line='logfile = "uparm$logfile"'>
  <DD>The name of the logfile, if command logging is enabled.
  </DD>
  </DL>
  <DL>
  <DT><B>logmode = "<TT>commands nobackground noerrors notrace</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logmode' Line='logmode = "commands nobackground noerrors notrace"'>
  <DD>Logging mode control parameter.  (See "<TT>logging</TT>")
  </DD>
  </DL>
  <DL>
  <DT><B>lexmodes = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lexmodes' Line='lexmodes = yes'>
  <DD>Enable automatic mode switching between "<TT>command mode</TT>" (used when commands are
  being entered interactively at the terminal), and "<TT>compute mode</TT>" (used to
  evaluate arithmetic expressions and argument lists).  If <I>lexmodes</I> is
  disabled command mode is disabled.  Command mode is always disabled within
  scripts and within parenthesis, i.e., expressions or formal argument lists.
  </DD>
  </DL>
  <DL>
  <DT><B>menus = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='menus' Line='menus = yes'>
  <DD>If <I>menus</I> are enabled, a table will be printed whenever a package is
  entered or exited listing the tasks (or subpackages) in the new package.
  </DD>
  </DL>
  <DL>
  <DT><B>mode = "<TT>ql</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='mode' Line='mode = "ql"'>
  <DD>The parameter mode of the CL, and of any tasks run by the CL which do not
  specify their own mode (i.e., which specify `auto' mode).  A "<TT>q</TT>" causes a
  query to be generated whenever a parameter is used which was not set explicitly
  on the command line.  An "<TT>m</TT>" (menu mode) causes <I>eparam</I> to be called to
  edit/check a task's parameters when the task is run interactively.  An "<TT>l</TT>"
  causes the parameter file for a task to be updated on disk whenever the task
  is run interactively.  Note that changing the mode at the CL level will have
  no affect on the operation of an individual task unless "<TT>auto</TT>" mode is set
  at the package, task, and parameter level, causing the mode to defer to the
  global CL mode.
  </DD>
  </DL>
  <DL>
  <DT><B>notify = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='notify' Line='notify = yes'>
  <DD>If <I>notify</I> is enabled background jobs will print a message on the user
  terminal (or in the logfile for a queued job) notifying the user when the
  job completes.
  </DD>
  </DL>
  <DL>
  <DT><B>szprcache = (a small number)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='szprcache' Line='szprcache = (a small number)'>
  <DD>Controls the size of the process cache.  The value may range from 1 to 10.
  A larger number reduces process spawns but the idle processes may consume
  critical system/job resources.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <I>cl</I> and <I>clbye</I> commands are used to call the CL as a task.
  The function of the <I>cl</I> task is to read and execute commands from
  its standard input until <I>bye</I> or end of file is reached.  The <I>cl</I>
  task may be called with arguments or executed in the background like any
  other task.  The <I>cl</I> task may be called from within a procedure or
  script to read commands from the command stream which called that procedure
  or task; this is usually the terminal but may be a another script.
  <P>
  When the <I>cl</I> or <I>clbye</I> command is invoked, the command language
  interpreter stores information about which tasks and packages are currently
  defined.  When the command is finished any tasks or packages which
  have become defined since invocation are lost, unless the user specifically
  overrides this by using the <I>keep</I> command.
  <P>
  The <I>clbye</I> command performs exactly like a <I>cl</I> followed by a
  <I>bye</I>, except that when called from a script the script file is closed
  immediately, freeing its file descriptor for use elsewhere.  If <I>cl</I>
  is used instead of <I>clbye</I> in a script, the file is not closed until
  after the <I>cl</I> returns.  If a <I>clbye</I> is used in a script, any
  commands following the <I>clbye</I> will not be executed.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Execute CL commands from a file.
  <P>
  	cl&gt; cl &lt; cmdfile
  <P>
  2. Execute CL commands from a pipe.
  <P>
  	cl&gt; print ("<TT>!type </TT>", fname) | cl
  <P>
  3. Execute <I>cl</I>, taking command input from the terminal.  Since command
  input is already from the terminal, the only effect is to mark the state
  of CL memory, to allow <I>task</I>, <I>set</I>, and other definitions to be
  made temporarily and later freed by terminating the <I>cl</I> with a <I>bye</I>.
  <P>
  <PRE>
  	cl&gt; cl
  	cl&gt; set pak = "home$tasks/"
  	cl&gt; task $mytask = pak$x_mytask.e
  		(execute the task)
  	cl&gt; bye
  </PRE>
  <P>
  In the example above, the declarations of the logical directory "<TT>pak</TT>" and the
  task "<TT>mytask</TT>" are discarded when the <I>bye</I> is entered, terminating the
  <I>cl</I>.
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  Beware that any changes made to the global CL parameters during the execution
  of a <I>cl</I> remain in effect after the task terminates.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  bye, keep, logout
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
