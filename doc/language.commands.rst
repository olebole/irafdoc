.. _commands:

commands — A discussion of the syntax of IRAF commands
======================================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  commands -- the CL command syntax
  </UL>
  <! EndSection:   'NAME'>
  <H3>Syntax</H3>
  <! BeginSection: 'SYNTAX'>
  <UL>
  In <I>command</I> mode (normal interactive commands):
  <P>
  	taskname arg1 ... argN par=val ... par=val redir
  <P>
  In <I>compute</I> mode (algebraic mode, for expressions and procedures)
  <P>
  	taskname (arg1, ... argN, par=val, ... par=val, redir)
  </UL>
  <! EndSection:   'SYNTAX'>
  <H3>Elements</H3>
  <! BeginSection: 'ELEMENTS'>
  <UL>
  <DL>
  <DT><B>taskname</B></DT>
  <! Sec='ELEMENTS' Level=0 Label='taskname' Line='taskname'>
  <DD>The name of the task to be executed.
  </DD>
  </DL>
  <DL>
  <DT><B>argN</B></DT>
  <! Sec='ELEMENTS' Level=0 Label='argN' Line='argN'>
  <DD>The positional arguments to the task.  An argument may be any expression;
  in command mode, a parameter name must be enclosed in parenthesis to avoid
  interpretation as a string constant (e.g., filename).
  </DD>
  </DL>
  <DL>
  <DT><B>param=value</B></DT>
  <! Sec='ELEMENTS' Level=0 Label='param' Line='param=value'>
  <DD>Keyword equals value assignment.  The value of the parameter named on the
  left is set equal to the value of the expression on the right.
  Keyword equals value assignments must follow any positional arguments.
  To save typing, boolean (yes/no) parameters may be set with a trailing
  + or -, e.g., "<TT>verbose+</TT>" is the same as "<TT>verbose=yes</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>redir</B></DT>
  <! Sec='ELEMENTS' Level=0 Label='redir' Line='redir'>
  <DD>A file redirection argument, e.g.:
  <P>
  <PRE>
  <PRE>
  &gt; file		spool output in a file
  &lt; file		read input from a file (rather than the terminal)
  &gt;&gt; file		append the output to a file
  &gt;&amp; file		spool both error and regular output in a file
  &gt;&gt;&amp; file	append both error and regular output to a file
  &gt;[GIP]		redirect graphics output to a file, e.g, &gt;G file
  &gt;&gt;[GIP]		append graphics output to a file, e.g, &gt;&gt;G file
  </PRE>
  </PRE>
  </DD>
  </DL>
  </UL>
  <! EndSection:   'ELEMENTS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  A CL command is an invocation of a predefined CL task.
  A task may be one of the numerous builtin functions
  (e.g. time, lparam, ehistory),
  a task defined in a package supplied to the user automatically,
  (e.g., the <I>directory</I> task in the <I>system</I> package),
  or a task the user has defined himself, using the <I>task</I> directive.
  <P>
  The entire argument list of a command, including file redirection arguments
  may be enclosed in parentheses.  This forces all arguments to be evaluated
  in compute mode.  In command mode arguments are delimited by spaces and
  most characters may be included in strings without need to quote the strings.
  In compute mode arguments are delimited by commas, all strings must be
  quoted, and all CL arithmetic and other operators are recognized.
  Command mode is the default everywhere, except within parenthesis, on the
  right hand side of a "<TT>= expr</TT>" (inspect statement), or within procedures.
  The sequence #{ &lt;statements&gt; #} may be used to force interpretation of a
  series of statements in compute mode.
  <P>
  <P>
  1. <B>Arguments</B>
  <P>
      The task name may be followed by any number of positional arguments
  and/or keyword=value type arguments, switches, or i/o redirection arguments.
  The positional arguments must come first.  Arguments are most commonly simple
  numeric or string constants, but general expressions are allowed.
  Some examples of arguments follow.
  <P>
  <PRE>
  <PRE>
  	"quoted string"
  	(cos(.5)**2 + sin(.5)**2)
  	"work" // 02
  	k + 2			# valid only in compute mode
  	i+3			# valid in both modes
  	(i+3)			# same answer in both modes
  </PRE>
  </PRE>
  <P>
  Within an argument the treatment of unquoted strings depends upon
  the current mode.  In command mode the string is assumed to be
  a string constant, while in compute mode it is taken to be the
  name of a parameter.  For example, in command mode the expression
  <P>
  	i+3
  <P>
  is equivalent to the string "<TT>i+3</TT>", while in compute mode this would
  evaluate to the sum of the <I>value</I> of the parameter "<TT>i</TT>" plus 3.
  To force evaluation of a string like i+3 as a arithmetic expression,
  enclose it in parenthesis.
  <P>
  Positional arguments are assigned to the parameters of the task to
  be executed.  The position of each task parameter is determined by the
  order of the arguments in the <I>procedure</I> declaration of a
  procedure script task, or by the order of declaration of the parameters
  in a parameter file for other tasks.
  <P>
  Hidden parameters cannot be assigned values positionally (one must use
  keywork assignment).  It is an error to have more positional arguments
  than there are corresponding parameters in the task, but omitting
  positional arguments is legal.  In compute mode, arguments
  may be skipped using commas to mark the skipped arguments, e.g. a,,b.
  <P>
  Following the positional arguments the user may specify keyword
  arguments.  All parameters of a task, including hidden parameters
  may be assigned to using keyword arguments.  The form of a keyword
  argument is
  <P>
  	param=expr
  <P>
  where <I>param</I> is the name of the task's parameter, and <I>expr</I> is
  any legal CL expression.  If the parameter is boolean an alternative syntax
  called the "<TT>switch</TT>" syntax is available:
  <P>
  <PRE>
  <PRE>
  	param+		# same as param=yes
  	param-		# same as param=no
  </PRE>
  </PRE>
  <P>
  A given parameter may only be assigned to once in a command line.
  <P>
  <P>
  2. <B>I/O Redirection</B>
  <P>
      Following the argument list the user may specify one or more file
  redirection parameters.  This permits the altering of standard i/o streams
  for this command only.  Note that the file name specified is interpreted
  according to the current mode, i.e.
  <P>
  	&gt; file
  <P>
  sends output to a file with the name "<TT>file</TT>" in command mode, but uses
  the <I>value</I> of the parameter "<TT>file</TT>" as the filename in compute mode.
  <P>
  The output from one command may also be directed to the input of another
  using pipes.  The syntax is
  <P>
  <PRE>
  <PRE>
  	command1 | command2
      or
  	command1 |&amp; command2
  </PRE>
  </PRE>
  <P>
  Here command1 and command2 are full commands, including the taskname
  and all arguments.
  In the first example the standard output of command1 becomes
  the standard input of command2, while in the second the both the
  standard and error output are sent to command2.
  <P>
  Once two commands have been joined by a pipe they function effectively
  as a single command, and the combined command may be joined by
  pipe to further commands.  The resulting "<TT>command block</TT>" is executed
  as a unit, and may be submitted as a background job by following the
  command block with an "<TT>&amp;</TT>".
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Simple positional arguments only (command mode).
  <P>
  	cl&gt; copy file1 file2
  <P>
  2. Simple positional arguments only (compute mode).
  <P>
  	cl&gt; copy ("<TT>file1</TT>", "<TT>file2</TT>")
  <P>
  3. One positional argument, i.e., the string "<TT>file1,file</TT>", and one keyword=value
  type argument.  Note that string need not be quoted even though it contains
  the comma, provided there are no spaces in the string.
  <P>
  	cl&gt; lprint file1,file2 device=versatec
  <P>
  4. Syntax for i/o redirection in compute mode, as in a script.
  <P>
  	type ("<TT>*.x</TT>", &gt; "<TT>spool</TT>")
  <P>
  5. The same command in command mode.
  <P>
  	cl&gt; type *.x &gt; spool
  <P>
  6. Use of an arithmetic expression in command mode; the scalar value of the
  expression given as the third positional argument is added to the value
  of every pixel in image "<TT>pix1</TT>", writing a new image "<TT>pix2</TT>" as output.
  <P>
  	cl&gt; imarith pix1 + (log(4.2)+10) pix2
  <P>
  Many additional examples may be found in the EXAMPLES section of the
  manual pages throughout the system.
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  procedure, parameters
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'SYNTAX' 'ELEMENTS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
