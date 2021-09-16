.. _task:

task — Define a new task
========================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  <PRE>
  task     -- define a new IRAF task
  redefine -- redefine an IRAF task
  </PRE>
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  <PRE>
  task     t1 [t2 ...] = tfile
  redefine t1 [t2 ...] = tfile
  </PRE>
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>t1, t2, ...</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='t1' Line='t1, t2, ...'>
  <DD>The names of the new logical tasks.  The task name should be prefixed by a $
  if the task has no parameter file.  An optional extension should be appended
  if either the standard input or output of the task is a binary stream, rather
  than text.  For example, "<TT>$mytask.tb</TT>" denotes a task with no parameter file,
  a text standard input, and a binary standard output.
  </DD>
  </DL>
  <DL>
  <DT><B>tfile</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='tfile' Line='tfile'>
  <DD>The name of the file to be executed or interpreted to run the task.
  The type of the task is determined by the file extension.  An "<TT>.e</TT>" extension
  indicates an executable task, while "<TT>.cl</TT>" indicates a CL script task or
  procedure.  The <I>tfile</I> string is prefixed by a $ to define a
  <I>foreign task</I> (see the discussion below).
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <I>task</I> statement defines a new task to the CL, and is required before
  the task can be run from the CL.  The new task is added to the "<TT>current
  package</TT>", i.e., the package that is listed when "<TT>?</TT>" is entered.  Any task
  definitions made since the current package was entered will be discarded
  when the package is exited.
  <P>
  In addition to defining a new task, the <I>task</I> statement defines the
  type and attributes of the new task.  Three types of tasks can be defined:
  script (.cl), executable (.e), and foreign ($...).  A task is assumed to
  have a parameter file ("<TT>taskname.par</TT>", in the same directory as <I>tfile</I>),
  unless the taskname is explicitly prefixed by a $.  A suffix or extension
  may optionally be added to the task name to indicate whether the input and
  output streams are text or binary.  The default is text, meaning that if
  output (or input) is redirected to a file, the file will be opened as a
  text file.
  <P>
  The <I>foreign task</I> facility allows host system tasks, e.g., host utilities
  or user written Fortran or C programs, to be called from the CL as if they
  were regular IRAF tasks.  The command line of a foreign task is parsed
  like that of any other task (and unlike an OS escape), allowing expression
  evaluation, i/o redirection, and background job submission.  The difference
  between a regular IRAF task and a foreign task is that the foreign tasks have
  little or no access to IRAF facilities, are usually machine dependent
  (and programs which use them are machine dependent), and cannot be cached.
  Nonetheless the foreign task facility is very useful for personalizing and
  extending the IRAF environment with a minimum of effort.
  <P>
  The <I>task</I> statement includes facilities for defining how the host system
  argument list for a foreign task will be built when the task is called from
  the CL.  The simplest form of the foreign task statement is the following:
  <P>
  	task [$]taskname = "<TT>$host_command_prefix</TT>"
  <P>
  where <I>host_command_prefix</I> is the first part of the command string to be
  passed to the host system.  Any command line arguments are simply tacked onto
  the end of this string, delimited by blanks.
  <P>
  If this is insufficient then argument substitution may be used to define how
  the argument list is to be built up.  The macro <B>$N</B> denotes argument N
  from the CL command line, with the first argument being number 1.  The macro
  <B>$0</B> is a special case, and is replaced the name of the task being
  executed.  Likewise, <B>$*</B> denotes all arguments.  If the character
  following the $ is enclosed in parenthesis, the corresponding argument string
  will be treated as an IRAF virtual filename, with the equivalent host system
  filename being substituted for use in the host command.  Any other character
  sequences are passed on unchanged.  The argument substitution macros are
  summarized in the table below.
  <P>
  <PRE>
  <PRE>
  	$0		task name
  	$N		argument N
  	$*		all arguments
  	$(...)		host system filename translation of "..."
  </PRE>
  </PRE>
  <P>
  When a task is invoked, an executable is run by starting an attached
  sub-process, while a script is run by starting a new level of the CL
  with its standard input set to the script file.
  <P>
  An executable image may contain any number of executable CL tasks, hence it
  can be pointed to by multiple task names or in multiple <I>task</I> statements.
  A script file can only contain one script task.
  <P>
  <I>Redefine</I> has the same syntax as the <I>task</I> command, but all the
  task names must already be defined in the current package.  It is often
  useful after misspelling the task file name in a task command.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Call up the editor to create a new program (task) mytask.x.  Compile
  the new program.  Declare it using the task statement and then run it.
  <P>
  <PRE>
  	cl&gt; edit mytask.x			# edit
  	cl&gt; xc mytask.x				# compile &amp; link
  	cl&gt; task $mytask = mytask.e		# define task
  	cl&gt; mytask arg1 arg2			# run it
  </PRE>
  <P>
  2. Define a script task with associated parameter file (if the script is
  a <I>procedure</I>, the parameter file is omitted since procedure scripts
  always have defined parameters).
  <P>
  	cl&gt; task myscript = myscript.cl
  <P>
  3. Define the four new tasks implot, graph, showcap, and gkiextract.
  All have parameter files except showcap.  The gkiextract task has a
  binary output stream.  All tasks are executable and are stored in the
  executable file "<TT>plot$x_plot.e</TT>".  Note the use of comma argument
  delimiters in this example; this is a compute mode example as would
  be found in a package script task.
  <P>
  <PRE>
  	task	implot,			# compute mode syntax
  		graph,
  		$showcap,
  		gkiextract.tb	= "plot$x_plot.e"
  </PRE>
  <P>
  4. Make the listed UNIX programs available in the IRAF environment as
  foreign tasks.  None of the tasks has a parameter file.  The "<TT>$foreign</TT>"
  declares the tasks as foreign, and indicates that the IRAF task name
  is the same as the host system task name.
  <P>
  	cl&gt; task $ls $od $rlogin = $foreign
  <P>
  5. Define a couple of foreign tasks for VMS, where the command to be sent
  to VMS is not the same as the IRAF task name.
  <P>
  <PRE>
  	cl&gt; task $run	= $run/nodebug
  	cl&gt; task $debug = $run/debug
  	cl&gt; task $top	= "$show proc/topcpu"
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  The distinction between command and compute mode syntax can be confusing.
  When defining tasks in your login.cl or in a package script task, use
  compute mode, with commas between the arguments and all strings quoted
  (there are plenty of examples in the system).  When typing in <I>task</I>
  statements interactively, use command mode.  If you forget and leave in
  the commas, they will be assumed to be part of the task name, causing the
  following error message when the task is run:
  <P>
  	ERROR: IRAF Main: command syntax error
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  prcache, flprcache, package
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
