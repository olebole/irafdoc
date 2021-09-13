page — Page through a file
==========================

**Package: system**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>page (Nov86)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>system</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>page (Nov86)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>page</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  page -- display a file or files one page at a time
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  page files
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_files">files</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='files' Line='files'>
  <DD>The list of files.  If omitted, text is read from the standard input.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_map_cc">map_cc = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='map_cc' Line='map_cc = yes'>
  <DD>Map non-printing control characters into printable form, e.g., BEL
  (ctrl/G, ASCII 7) is printed as "<TT>^G</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_clear_screen">clear_screen = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='clear_screen' Line='clear_screen = no'>
  <DD>If set, the screen is cleared before each page is written.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_first_page">first_page = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='first_page' Line='first_page = 1'>
  <DD>The first page to be printed.  Pages are defined by form feed characters
  embedded in the text.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_prompt">prompt = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='prompt' Line='prompt = ""'>
  <DD>Optional prompt string for the end-of-page prompt.  If no prompt string is
  given the name of the file being paged is used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_device">device = "<TT>terminal</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='device' Line='device = "terminal"'>
  <DD>The output device.  The special device <I>text</I> may be specified to
  represent standout mode with upper case rather than reverse video characters.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>Page</I> displays a file on the terminal, one page of text at a time,
  pausing between successive pages of output until a key is typed on the
  terminal.  Pages are normally broken when the screen fills, but may also
  be delimited by form feed characters embedded in the input text.
  A prompt is printed after each page of text naming the current file,
  showing the percentage of the file which has been displayed, and the numeric
  order of the file within the file list if a file template was given.
  <P>
  When the end of page prompt is displayed any of the following command
  keystrokes may be entered.  Command keystrokes are input in raw mode,
  i.e., no carriage return is required to pass the command to the program.
  <P>
  <PRE>
  <PRE>
  	.		go to the beginning of the current file    [BOF]
  	:		colon escape (see below)
  	?		display a one-line command summary
  	G		go to the end of the current file          [EOF]
  	N,&lt;ctrl/n&gt;	go to the next file
  	P,&lt;ctrl/p&gt;	go back to the previous file
  	b		back up one page
  	d		scroll down half a page of text
  	e		edit the current file
  	f,space		advance to the next page
  	j,return	scroll down one line
  	k		back up one line
  	n		search for the next occurrence of a pattern
  	q		quit
  	u		back up half a screen
  <P>
  	&lt;ctrl/c&gt;	quit (interrupt)
  	&lt;ctrl/z&gt;	quit (EOF)
  	&lt;ctrl/d&gt;	quit (EOF)
  </PRE>
  </PRE>
  <P>
  If an unrecognized keystroke is entered the terminal will beep.  The following
  colon commands are recognized in addition to the single keystroke commands
  described above.
  <P>
  <PRE>
  <PRE>
  	:!&lt;clcmd&gt;	send a command to the CL (:!! for host command)
  	:/&lt;pattern&gt;	advance to line matching the given pattern
  	:file &lt;fname&gt;	display file "fname" (may be abbreviated)
  	:help		print summary of colon commands
  	:line [+/-]N	goto line N (relative move if +/- given)
  	:spool &lt;fname&gt;	spool output to the named file
  </PRE>
  </PRE>
  <P>
  The <I>:clcmd</I> facility is used to send commands to the CL from within
  the context of the pager.  For example, "<TT>:!cl</TT>" will temporarily suspend the
  pager, allowing CL commands to be entered until the command "<TT>bye</TT>" is entered,
  causing execution of the pager to resume.  Note that since the <I>page</I>
  task resides in the system process <I>x_system.e</I>, it will be necessary
  for the CL to connect a second system process if the command issued calls
  another task in the system package, since the first system process will
  still be running, i.e., executing the <I>page</I> task.  This is harmless,
  but the second process may be removed from the process cache with
  <I>flprcache</I> if desired, after exiting the original <I>page</I> task.
  <P>
  The sequence ":/"<TT> followed by a pattern will cause the current input stream
  to be searched for the next occurrence of the pattern given.  A pattern once
  entered is retained indefinitely and may be used in subsequent searches by
  typing the single keystroke <TT>`n'</TT>, without need to reenter the pattern.
  Searching stops at the end of the current file, requiring a <TT>`.'</TT> to wrap back
  around to the beginning of the file, or a <TT>`N'</TT> to advance to the next file.
  <P>
  The <I>:file</I> command is used to change the current position within the
  file list specified by <I>files</I>, and may not be used to page a file not
  specified in the initial template.  Note that the filename may be abbreviated,
  and that searching stops with the first file lexically greater than or equal
  to the given string (hence "<TT>:file x</TT>" might return file "<TT>y</TT>").
  <P>
  The <I>:line N</I> command may be used to randomly position to the indicated line
  within the current file.  If the line number argument N is preceded by a plus
  or minus the argument is taken to be an offset from the current position.
  <P>
  The <I>:spool</I> command is used to spool output to a file.  Each time a
  file line is printed on the screen, it is appended to the named file as well.
  One can interactively position to the desired line of the file and then turn
  on spooling to extract a portion of the file or stream being displayed.
  A subsequent <I>:spool</I> command with no filename will turn spooling off.
  Issuing a <I>:spool</I> to begin spooling on a new file when already spooling
  to some other file will cause the old spool file to be closed.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Page through all of the files in the directory "<TT>lib</TT>" which have
  the extension "<TT>.h</TT>".
  <P>
  	cl&gt; page lib$*.h
  <P>
  2. Use <I>help</I> to format the text in the file "<TT>doc$spp.hlp</TT>", displaying
  the formatted document beginning on page 5 (the entire document has to be
  formatted first so it takes a minute or so to get any output).
  <P>
  	cl&gt; help doc$spp.hlp fi+ | page first=5
  <P>
  3. Run <I>rfits</I> to print a long format listing of the headers of a series
  of FITS images from a magnetic tape, directing the output through <I>page</I>
  so that it does not flash by when you aren't looking.
  <P>
  	cl&gt; rfits mta make- long+ | page
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  Since <I>page</I> does not currently buffer any input text, backwards motions
  and absolute line positioning are not permitted when paging the standard input.
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  type, match, head, tail
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>