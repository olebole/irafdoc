.. _stty:

stty — Set/show terminal characteristics
========================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  stty -- set/show terminal characteristics
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  stty [terminal]
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>terminal</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='terminal' Line='terminal'>
  <DD>The logical name of the terminal to be used, i.e., the name of the device
  given in the <I>dev$termcap</I> file.
  </DD>
  </DL>
  <DL>
  <DT><B>baud = 9600</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='baud' Line='baud = 9600'>
  <DD>Set to some nonzero value to inform the VOS of the baud rate; the software
  does not automatically sense the baud rate.  The baud rate must be known to
  accurately generate delays.
  </DD>
  </DL>
  <DL>
  <DT><B>ncols = 80</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ncols' Line='ncols = 80'>
  <DD>The logical width of the screen in characters; may be set to some value less
  than the physical width to produce more readable output on very high resolution
  terminals.
  </DD>
  </DL>
  <DL>
  <DT><B>nlines = 24</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nlines' Line='nlines = 24'>
  <DD>The logical height of the screen in characters.
  </DD>
  </DL>
  <DL>
  <DT><B>show = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='show' Line='show = no'>
  <DD>Show the current terminal driver settings.  The <I>show</I> function is
  automatically enabled if <I>stty</I> is called with no arguments.
  </DD>
  </DL>
  <DL>
  <DT><B>all = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='all' Line='all = no'>
  <DD>Show all terminal driver settings, including those which are not currently
  in use.  Setting <I>all</I> automatically sets <I>show</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>reset = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='reset' Line='reset = no'>
  <DD>Reset the terminal driver settings to their default (login time) values.
  Note that the terminal driver is not a task in the normal sense but is always
  active, and once a parameter is set the new value is retained indefinitely.
  </DD>
  </DL>
  <DL>
  <DT><B>resize = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='resize' Line='resize = no'>
  <DD>Recompute the terminal screen size parameters, <B>ttyncols</B> and
  <B>ttynlines</B>, and update their values in the environment.
  If the terminal supports runtime querying of the screen size it will be
  queried (allowing the screen size to change dynamically at runtime),
  otherwise the values from the termcap entry for the terminal will be used.
  </DD>
  </DL>
  <DL>
  <DT><B>clear = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='clear' Line='clear = no'>
  <DD>Clear the function(s) which follow on the command line, e.g.,
  "<TT>clear ucasein ucaseout</TT>" is equivalent to "<TT>ucasein=no ucaseout=no</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>ucasein = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ucasein' Line='ucasein = no'>
  <DD>Map terminal input to lower case, e.g., when working on an old monocase
  terminal, or on a modern terminal with the shiftlock key on.
  </DD>
  </DL>
  <DL>
  <DT><B>ucaseout = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ucaseout' Line='ucaseout = no'>
  <DD>Map terminal output to upper case.
  </DD>
  </DL>
  <DL>
  <DT><B>login = "<TT>home$ttyin.log</TT>" [off]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='login' Line='login = "home$ttyin.log" [off]'>
  <DD>Log all input from the terminal to the named text file.
  </DD>
  </DL>
  <DL>
  <DT><B>logio = "<TT>home$ttyio.log</TT>" [off]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logio' Line='logio = "home$ttyio.log" [off]'>
  <DD>Log all terminal i/o to the named text file.  May not be used if either
  <I>login</I> or <I>logout</I> mode is in effect, and vice versa.
  </DD>
  </DL>
  <DL>
  <DT><B>logout = "<TT>home$ttyout.log</TT>" [off]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logout' Line='logout = "home$ttyout.log" [off]'>
  <DD>Log all output to the terminal to the named text file.
  </DD>
  </DL>
  <DL>
  <DT><B>playback = "<TT>home$ttyin.log</TT>" [off]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='playback' Line='playback = "home$ttyin.log" [off]'>
  <DD>Divert terminal driver input to the named "<TT>stty login</TT>" style text file,
  i.e., take input from a file instead of from the terminal.  The effect is
  to exactly repeat a previous terminal session executed with <I>login</I>
  mode in effect, e.g., to test or demo software.
  </DD>
  </DL>
  <DL>
  <DT><B>verify = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verify' Line='verify = no'>
  <DD>If <I>verify</I> is enabled during <I>playback</I> mode the terminal driver
  will read a key from the keyboard before executing each command in the
  logfile.  Tap the space bar to execute the command, <I>q</I> to terminate
  playback mode, or <I>g</I> to continue execution with <I>verify</I> mode
  disabled.  Typing any other key causes a help line to be printed.
  </DD>
  </DL>
  <DL>
  <DT><B>delay = 500 (msec)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='delay' Line='delay = 500 (msec)'>
  <DD>If <I>verify</I> is disabled during <I>playback</I> mode the terminal driver
  will pause for <I>delay</I> milliseconds before executing each logfile command.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <I>stty</I> task is used to set or display the terminal device
  characteristics and VOS terminal driver options.
  Without arguments, <I>stty</I> prints the current characteristics of the
  terminal.  The default terminal type can be changed by setting <I>ttyname</I>.
  The terminal characteristics <I>ncols</I>, <I>nlines</I> or <I>baud</I>,
  may be changed by typing new values explicitly on the command line.
  <P>
  The most common use of <I>stty</I> is to inform IRAF of the type of terminal
  being used, e.g.,
  <P>
  	cl&gt; stty vt100
  <P>
  would set the terminal type to "<TT>vt100</TT>".  An error message will be printed
  unless an entry for the named terminal is present in the <B>termcap</B> file;
  if the named terminal is a graphics terminal, there must also be an entry
  in the <B>graphcap</B> file.
  <P>
  To find out about the current terminal settings, type
  <P>
  <PRE>
  <PRE>
  	cl&gt; stty
  or
  	cl&gt; stty all
  </PRE>
  </PRE>
  <P>
  A limited number of terminal driver options may also be set.  In particular,
  the VOS terminal driver (not to be confused with the host operating system
  terminal driver, a lower level facility) implements facilities for case
  conversion upon input or output, and for logging all i/o to the terminal
  and playing back a terminal session logged in a file.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Case conversions</H3>
  <! BeginSection: 'Case Conversions'>
  <UL>
  The <B>ucasein</B> option, if set,
  will cause all upper case terminal input to be mapped to lower
  case (e.g., when working from an old monocase terminal).  In this mode,
  individual upper case characters may be input by preceding them with the
  escape character ^, e.g., "<TT>^MAKEFILE</TT>" equates to "<TT>Makefile</TT>".  The full set
  of ^ escapes is summarized below.  The option <B>ucaseout</B> will cause all
  terminal output to be mapped to upper case.  Preceding either or both of
  these option keywords by <B>clear</B> causes the options to be cleared.
  <P>
  <PRE>
  <PRE>
  	^	shift next character to upper case
  	^+	shift lock (caps lock)
  	^-	clear shift lock
  	^^	the character ^
  </PRE>
  </PRE>
  <P>
  Case shifting is disabled in raw mode, e.g., while in cursor mode, and in
  <B>eparam</B>.  All standard IRAF software, however, will sense that ucase
  mode is set before entering raw mode, and will behave as expected.  Ucase mode
  is also disabled by the STDGRAPH kernel whenever the graphics workstation is
  activated.
  <P>
  Note that ^ is also the history meta-character, hence ^^ must be used when
  in <I>ucasein</I> mode to pass a single ^ to the CL history mechanism.
  In cursor mode, upper case keystrokes are intercepted by cursor mode unless
  escaped with a backslash.  Escaped keystrokes are mapped to lower case by
  cursor mode if <I>ucasein</I> mode is in effect, terminating cursor mode and
  returning a lowercase key to the applications program.
  <P>
  </UL>
  <! EndSection:   'Case Conversions'>
  <H3>Recording terminal i/o</H3>
  <! BeginSection: 'Recording Terminal I/O'>
  <UL>
  The terminal driver options <B>logio</B>, <B>logout</B>, and <B>login</B>
  may be used to log, respectively, all terminal i/o, all output to the terminal,
  or all input from the terminal.  The logfile names are "<TT>home$ttyin.log</TT>",
  "<TT>home$ttyout.log</TT>", or "<TT>home$ttyio.log</TT>", unless a different logfile name is
  specified by the user.  All logfiles are standard textfiles containing only
  printable characters.
  <P>
  Terminal i/o logging is especially useful for debugging <I>termcap</I> and
  <I>graphcap</I> entries for new terminals.  All IRAF terminal i/o is logged,
  including raw mode i/o and graphics output.  Terminal i/o from foreign tasks
  or OS escapes is not logged since these tasks bypass the VOS to talk directly
  to the user terminal.
  <P>
  Each sequence of characters read from or written to the terminal (via a zgettt
  or zputtt call to the driver) appears as one logical line of text in the
  logfile, delimited by the data character \n (newline).
  When reading from a terminal in raw mode, each input character will appear
  on a separate line in the logfile with no newline, since only a single
  data character is read at a time during raw mode input.
  All control characters embedded in the data, including newline terminators,
  are rendered into printable form.  Long lines are broken near the right margin,
  adding an escaped newline and indenting continuation lines 4 spaces.
  <P>
  Terminal i/o logging is intended primarily for debugging purposes, rather
  than for logging user commands; the IRAF command language provides a more
  user friendly facility for command logging (see the <I>language.logging</I>
  manpage for further information on the CL command logging facilities).
  All unprintable ASCII codes are rendered in the logfile in a printable form
  intended to eliminate any ambiguity regarding the exact sequence of characters
  sent to or received from the terminal.  In addition to the standard escape
  sequences \n, \t, \r, etc., the following special escape sequences are used:
  <P>
  <PRE>
  <PRE>
  	\\		\<BR>
  	\^		^
  	^@		NUL (ascii 000)
  	^[A-Z]		ctrl/a - ctrl/z (ascii 001 - 032)
  	^[		ESC (ascii 033)
  	^\		FS  (ascii 034)
  	^]		GS  (ascii 035)
  	^^		RS  (ascii 036)
  	^_		US  (ascii 037)
  	\s		blank (ascii 040)
  	\&lt;newline&gt;	long i/o record continued on next line
  </PRE>
  </PRE>
  <P>
  These special escape sequences, plus any ordinary characters, constitute the
  <I>data</I> recorded in the logfile.  The following additional escape
  sequences are used to record information about the logging session itself in
  the logfile.
  <P>
  <PRE>
  <PRE>
  	\#		rest of line is a comment
  	\T		terminal device name at log time
  	\G		stdgraph device name at log time
  	\O		timestamp written at start of log session
  </PRE>
  </PRE>
  <P>
  Any whitespace (unescaped blanks, tabs, or newlines) appearing
  in the logfile is put there only to make the file more readable, and is not
  considered data.  Blocks of text may be enclosed in a logfile delimited by
  escaped curly brackets, i.e., "<TT>\{ ... \}</TT>".  This is used for the <B>playback</B>
  facility described in the next section.  
  <P>
  </UL>
  <! EndSection:   'Recording Terminal I/O'>
  <H3>Playback of terminal sessions</H3>
  <! BeginSection: 'Playback of Terminal Sessions'>
  <UL>
  The terminal driver has the capability not only of recording terminal i/o
  in a file, but of taking input from a logfile to repeat a sequence of commands
  previously entered by the user with terminal input logging enabled.
  Note that we are not talking about simply playing back recorded output,
  but of actually executing an arbitrary sequence of commands formerly entered
  by the user.  This is different from executing a sequence of commands entered
  into, for example, a CL script, because <I>all</I> input is recorded,
  including not only the commands, but also all responses to parameter queries,
  all rawmode keystroke input, and all graphics cursor input occurring
  interactively during execution of the recorded commands.
  These <B>playback scripts</B> are useful for preparing automated demos or
  tutorials of complex software, and for preparing scripts to be used to
  automatically test software.
  <P>
  The basic sequence used to record and later playback a terminal session is as
  follows:
  <P>
  <PRE>
  <PRE>
  	cl&gt; stty login [= logfilename]
  		&lt;execute an arbitrary sequence of commands&gt;
  	cl&gt; stty clear login			# or stty reset
  	cl&gt; stty playback [= logfilename]
  </PRE>
  </PRE>
  <P>
  Naturally, the playback script must be executed in the same context as when
  the script was generated, i.e., one must ensure that all necessary packages
  have been loaded, that the current directory has been set to the proper
  value if it matters, and so on.  It is not necessary to execute a playback
  script on the same type of video terminal or graphics terminal as was
  used when the script was recorded; since only the terminal input is being
  recorded, playback scripts are device independent and may be played back on
  any terminal.
  <P>
  If desired the commands necessary to establish the starting context may be
  recorded as part of the script.  If the script is going to be repeatedly
  executed it may also be desirable to include commands at the end of the
  recording session to clean up, e.g., deleting any temporary files created
  during the recording session.  If anything has changed which causes a command
  to abort during execution of a playback script, normal terminal input is
  automatically restored, aborting the script.   Note that if the "<TT>stty playback</TT>"
  command gets into the playback script for some reason, e.g., because the
  "<TT>stty reset</TT>" (or "<TT>stty login=no</TT>" etc.) was omitted, then the script will
  repeat indefinitely.  This may or may not be what was desired.
  <P>
  Two <B>stty</B> command line arguments are provided for controlling the
  execution of a playback script.  By default, when a script is played back
  the terminal driver will pause for <B>delay</B> milliseconds after echoing
  the command to be executed, to give the user watching the playback a chance
  to read the command.  Aside from this programmed delay, execution is fully
  automated.  For example,
  <P>
  	cl&gt; stty play=filename delay=2000
  <P>
  would playback the file "<TT>filename</TT>", with a delay of 2 seconds following echo
  of each line of recorded input text.
  <P>
  Alternatively, the user may request that the driver pause and wait for the
  user to type a key before executing each logged command (i.e., before
  returning each input line of text to the application).  This is called the
  <B>verify</B> option.  In verify mode, the following keystrokes may be
  entered to continue execution:
  <P>
  <PRE>
  <PRE>
  	space, return		continue execution
  	<TT>'g'</TT>			go: turn verify mode off and continue
  	<TT>'q'</TT>			quit: terminate playback mode
  </PRE>
  </PRE>
  <P>
  Verify mode is automatically disabled during raw mode input since the input
  consists of single characters and an inordinate number of verification
  keystrokes would be required from the user.  Either of the <B>verify</B> or
  <B>delay</B> options may be overridden by control directives embedded in the
  playback text, as we shall see in the next section.
  <P>
  </UL>
  <! EndSection:   'Playback of Terminal Sessions'>
  <H3>Customizing playback scripts</H3>
  <! BeginSection: 'Customizing Playback Scripts'>
  <UL>
  Although playback scripts may be and often are generated and played back
  without ever looking at or modifying the actual playback script, there are
  cases where it may be desirable to do so.  For example, when generating a
  script to be used as a demo or tutorial, it may be desirable to insert
  explanatory text into the script to be printed out on the terminal when
  the script is played back, to explain to the person running the script what
  is going on.  Likewise, it may be desirable to control the verify and delay
  options at a granularity finer than the entire script.
  <P>
  Explanatory text and/or playback control directives may be inserted into the
  script using the following construct:
  <P>
  	"<TT>\{</TT>" [&lt;control_directives&gt;] [&lt;text&gt;] "<TT>\}</TT>"
  <P>
  where <B>control_directive</B> refers to one of the following:
  <P>
  <PRE>
  <PRE>
  	%V+		turn verify on
  	%V-		turn verify off
  	%NNN		set <B>delay</B> to NNN milliseconds
  </PRE>
  </PRE>
  <P>
  For example,
  <P>
  <PRE>
  <PRE>
  	dir\{%5000
  	[list the current directory]\}\n
  </PRE>
  </PRE>
  <P>
  would cause the following to be output, followed after a 5 second delay by a 
  listing of the current directory (the "<TT>&lt;&gt;</TT>" is not printed, but shows where
  the cursor will be during the 5 second pause):
  <P>
  <PRE>
  <PRE>
  	cl&gt; dir
  	[list the current directory]&lt;&gt;
  </PRE>
  </PRE>
  <P>
  Note that the newline following the "<TT>\{%5000</TT>" in the above example is textual
  data, and will be output to the terminal along with whatever follows, up until
  the closing brace, i.e., "<TT>\}</TT>".  The amount of text to be output may be
  arbitrarily large; there is a builtin limit (currently 4096 characters),
  but it is unlikely that this limit will ever be exceedd, since no more than
  one pageful of text should ever be output in a single call.
  <P>
  Normally, a %V or %NNN control directive refers only to the input record
  with which the enclosing \{...\} control block is associated.  The global
  value of <I>verify</I> or <I>delay</I> is temporarily overridden for the
  current record.  If desired, the global value may instead be permanently
  modified by adding a ! after the %, e.g.,
  <P>
  	\{%!V-%3000...\}
  <P>
  would permanently disable <I>verify</I> (unless a %V+ or %!V+ directive
  follows later in the script) then output the text "<TT>...</TT>" followed by a 3
  second delay.
  <P>
  To know where to insert the control directives into a script, it is
  important to understand that input from the script is <B>record oriented</B>,
  and that a control directive refers to the input record with which it is
  associated.  An input record is a single <I>logical</I> line of text in the
  input file.  Note that a logical line of text may span multiple physical lines,
  if the newlines are escaped or present as textual data within a control
  directive.  The position of the control directive within the input record
  determines where the explanatory text will be positioned relative to the
  input text, when both are echoed to the terminal.  Any programmed delay or
  pause will always occur after echoing the full record on the terminal.
  <P>
  </UL>
  <! EndSection:   'Customizing Playback Scripts'>
  <H3>Raw mode playback</H3>
  <! BeginSection: 'Raw Mode Playback'>
  <UL>
  When a program is executing which reads from the terminal in raw mode,
  each character is read from the terminal as soon as it is typed, and
  input characters are not echoed to the terminal unless the application
  explicitly does the echoing.  Examples of programs which use raw mode input are
  <I>eparam</I> and <I>page</I>, which are keystroke driven, and any program
  which reads the <B>graphics cursor</B>, since a graphics cursor read uses raw
  mode input.
  <P>
  Playback works much the same for raw input mode as for line input mode,
  except that during raw mode input the input records normally consist of
  single characters, rather than entire lines of text.  By default, <B>verify</B>
  is turned off while reading from the terminal in raw mode, to avoid having
  the user verify each individual character.  Also, the terminal driver will not
  echo text read from the playback file in raw mode, since the text would not
  have been echoed if playback were not in effect.
  <P>
  </UL>
  <! EndSection:   'Raw Mode Playback'>
  <H3>Cursor reads in playback mode</H3>
  <! BeginSection: 'Cursor Reads in Playback Mode'>
  <UL>
  A typical Tektronix style cursor read will look something like the following,
  as recorded in an <B>stty login</B> script file following a recording session:
  <P>
  <PRE>
  <PRE>
  	K
  	3
  	)
  	'
  	*
  	\r
  </PRE>
  </PRE>
  <P>
  This six character sequence consists of the key value of the cursor read (K),
  followed by the [x,y] cursor coordinate encoded as four ascii characters
  ("<TT>3)'*</TT>" in this case), followed by the "<TT>GIN mode terminator</TT>" character or
  characters, normally a single CR (\r).  Of course, if the terminal is not a
  Tektronix compatible terminal (e.g., DEC-Regis), the details will differ
  from this example.
  <P>
  The single character per line format of a cursor read reflects the fact that
  each input record is a single character when reading from the terminal in
  raw mode.  For the purposes of playback, however, such a sequence may be
  reformatted on a single line if desired, to improve the readability of a
  script (the extra whitespace in the second example is ignored, since if a
  space were data it would appear as \s).
  <P>
  <PRE>
  <PRE>
  	K3)'*\r
  or
  	K 3 ) ' * \r
  or
  	K
  	3)'*
  	\r
  etc.
  </PRE>
  </PRE>
  <P>
  To set the values of the <I>verify</I> or <I>delay</I> parameters for a cursor
  read one may insert the \{...\} sequence anywhere before the \r delimiter
  is returned to the application, e.g.,
  <P>
  	K3)'*\r\{%V+\}
  <P>
  would do, since the sequence shown forms one logical input record in the
  playback file, and the control directive included will be processed before
  any input data characters from the record are returned to the application.
  If the multi-line form of a cursor read is used, the control directive may
  be tacked onto any of the records K through \r in the example.
  <P>
  Output of explanatory text in an interactive graphics session is a little
  more tricky, since if one is not careful the text will come out while in
  graphics mode, causing it to be rendered as random lines drawn all over the
  screen.  A safe technique for outputting comments during playback of a
  graphics session is to output the text to the <B>status line</B>,
  taking care of course to output only a single line of text at once
  (since multiple lines written to the status line would rapidly flash by,
  leaving only the last line visible on the screen).  We can do this by taking
  advantage of the : command sequence, which can be used to put the terminal
  temporarily into status line output mode.
  <P>
  <PRE>
  <PRE>
  	:####\r
  	\{%5000
  	This is a status line comment\}
  	^U\177
  </PRE>
  </PRE>
  <P>
  For example, insertion of the above sequence between any two cursor reads
  in a recorded interactive graphics session would cause the text
  "<TT>This is a status line comment</TT>" to be written to the status line,
  with normal execution of the script occurring after a 5 second delay
  followed by erasure of the status line and exit from status line mode
  (due to the ctrl/u and rubout inserted as data after the colon cursor read).
  <P>
  While executing an interactive graphics session via playback, cursor values
  are read from the playback script instead of from the terminal, hence the
  user never sees the actual cursor crosshairs on the screen.  To give the
  user some idea of what is going on, the key values of successive cursor mode
  keystrokes are echoed in ascii down the left side of the screen, starting at
  the upper left.  The keystroke value is also echoed at the position of the
  cursor, to indicate where the cursor crosshairs would have been in an actual
  interactive session.
  <P>
  </UL>
  <! EndSection:   'Cursor Reads in Playback Mode'>
  <H3>Sample playback script</H3>
  <! BeginSection: 'Sample Playback Script'>
  <UL>
  We conclude with an example of a complete playback script which can be
  entered into a file and played back to demonstrate some of the features of
  the <I>implot</I> task in the PLOT package (the PLOT package must already
  be loaded).
  <P>
  <PRE>
  <PRE>
  	\O=NOAO/IRAF V2.6 iraf@pavo Fri 20:09:21 01-Jan-88
  	\T=gterm40
  	\G=gterm
  	\n
  	imheader\sdev$pix\slo+\suser-\n\{%3000
  	[Print image header]\}
  	\n
  	implot\sdev$pix\n
  	J3..8\r J3-,)\r J3+)9\r K3)'*\r J3((0\r l3&amp;';\r
  	:####\r
  	\{%5000
  	[use key <TT>`o'</TT> to overplot]\}
  	^U\177
  	o3&amp;';\r
  	K3&amp;';\r K3%*(\r K3#,3\r l3!.?\r
  	:####\r
  	\{%5000
  	[key <TT>`X'</TT> expands the plot in x]\}
  	^U\177
  	X3!.?\r
  	qXXXX\r
  	stty\sreset\n
  </PRE>
  </PRE>
  <P>
  </UL>
  <! EndSection:   'Sample Playback Script'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Show the current terminal type and attributes.
  <P>
  <PRE>
  	cl&gt; stty
  	Terminal=vt640, ncols=80, nlines=24, 9600 baud
  	ucasein=no, ucaseout=no, logio=off
  </PRE>
  <P>
  2. Tell the system that the terminal is a vt100.
  <P>
  	cl&gt; stty vt100
  <P>
  3. Set the baud rate of the current terminal to 9600 baud.
  <P>
  	cl&gt; stty baud=9600
  <P>
  4. Set the width of the screen to 80 columns, e.g., to get short menus on a
  workstation where the physical number of columns may be much greater than 80.
  <P>
  	cl&gt; stty ncols=80
  <P>
  5. Set the terminal type to 4012 and set ucasein and ucaseout modes.
  <P>
  	cl&gt; stty 4012 ucasein ucaseout
  <P>
  6. Clear the ucasein and ucaseout modes.
  <P>
  	cl&gt; stty clear ucasein ucaseout
  <P>
  7. Record a terminal session in the default logfile (home$ttyio.log).
  <P>
  	cl&gt; stty logio
  <P>
  8. Record input from the terminal in the file "<TT>demo</TT>".
  	
  	cl&gt; stty login=demo
  <P>
  9. Terminate logging and playback the terminal session recorded in this file.
  <P>
  <PRE>
  	cl&gt; stty reset
  	cl&gt; stty playback=demo
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  1. Note that, when working with a terminal which supports runtime querying
  of the screen size, the screen size is queried when the <B>stty resize</B>
  command is executed, rather than when the terminal screen actually changes size.
  Hence, the screen size parameters printed by a command such as <B>stty show</B>
  will not necessarily reflect the actual screen size.  <B>stty resize show</B>
  queries the terminal for the screen size, hence should always be correct.
  The screen size is automatically queried whenever the <I>page</I> or <I>help</I>
  tasks are run.
  <P>
  2. The terminal screen size is determined by querying the terminal for the
  screen size, and reading the response back (this technique has the advantage
  that it works remotely over IPC and network connections, and is host system
  independent).  If the terminal does not respond for some reason, e.g.,
  because the terminal type has been set improperly and the terminal does not
  support the query function, then <B>stty</B> will hang.  Typing a carriage
  return causes execution to resume, after which the error should be corrected.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  language.logging, fio$zfiott.x, etc$sttyco.x
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'Case Conversions' 'Recording Terminal I/O' 'Playback of Terminal Sessions' 'Customizing Playback Scripts' 'Raw Mode Playback' 'Cursor Reads in Playback Mode' 'Sample Playback Script' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
