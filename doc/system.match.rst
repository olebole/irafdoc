.. _match:

match — Print all lines in a file that match a pattern
======================================================

**Package: system**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  match -- match a pattern against the lines in a file or files
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  match pattern files
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>pattern</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pattern' Line='pattern'>
  <DD>The pattern to be matched.  A pattern may contain any of the
  pattern matching <I>meta-characters</I> described below.
  </DD>
  </DL>
  <DL>
  <DT><B>files</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='files' Line='files'>
  <DD>A template specifying the file or files to be searched.  Omitted if the
  standard input is redirected.
  </DD>
  </DL>
  <DL>
  <DT><B>meta-characters = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='meta' Line='meta-characters = yes'>
  <DD>Set to "<TT>no</TT>" to disable the pattern matching meta-characters, e.g., when
  you want to explicitly match one of the meta-characters as a regular character.
  </DD>
  </DL>
  <DL>
  <DT><B>stop = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='stop' Line='stop = no'>
  <DD>If <I>stop</I> is enabled, lines with match the pattern are "<TT>stopped</TT>" (not
  passed to the output), otherwise only those lines with match the pattern
  are output.
  </DD>
  </DL>
  <DL>
  <DT><B>print_file_names = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='print_file_names' Line='print_file_names = yes'>
  <DD>If more than one file is being searched, preface each printed line
  with the "<TT>file_name: </TT>".
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The listed files are searched for the given pattern, copying each line that
  matches to the standard output.  If "<TT>stop</TT>" is set the action is reversed,
  i.e., all lines are passed on to the output except those which match the
  pattern.  If no files are named text is read from the standard input.
  The pattern matching meta-characters are described in the table below.
  <P>
  <PRE>
  	^		matches the beginning of a line
  	$		matches the end of a line
  	?		matches any single character
  	*		matches zero or more of whatever is at the left
  	[12345]		matches any single character in the given set
  	[1-5]		matches any single character in a range
  	[^a-z]		matches any character NOT in the range/set
  	#		matches whitespace
  	{chars}		turns off case sensitivity inside the braces
  	\		used to include a meta-character in the pattern
  </PRE>
  <P>
  If more than one file is being searched, each output line is prefixed
  with its file name.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. From all the lines displayed by "<TT>set</TT>", print only those that have
  the string "<TT>tty</TT>" somewhere in them.
  <P>
  	cl&gt; set | match tty
  <P>
  2. Find all tasks that delete something.
  <P>
  	cl&gt; help * | match delete
  <P>
  3. Delete all the "<TT>red</TT>" objects from the list file "<TT>catalog</TT>".
  <P>
  	cl&gt; match red catalog stop+ &gt; newcatalog
  <P>
  4. Type out the file "<TT>spool</TT>", omitting all lines that end in a colon,
  and paginating the output.
  <P>
  	cl&gt; match "<TT>:$</TT>" spool stop+ | page
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  lcase, ucase, translit, sort, unique
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
