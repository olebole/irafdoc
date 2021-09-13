joinlines — Join text files line by line
========================================

**Package: proto**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>joinlines (Feb90)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>proto</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>joinlines (Feb90)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>joinlines</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  joinlines -- join input text files line by line.
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  joinlines list1 [list2]
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_list1">list1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='list1' Line='list1'>
  <DD>List of input text files to be joined.  It is an error if a file does
  not exist.  The special file "<TT>STDIN</TT>" may be used to read from the
  terminal, redirected input, or a pipe.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_list2">list2</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='list2' Line='list2'>
  <DD>Optional second list of input text files to be combined with the
  first list.  This only applies when two lists are specified on
  the command line otherwise this parameter is ignored.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output = "<TT>STDOUT</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output = "STDOUT"'>
  <DD>Output filename.  The result of joining the input lines is appended
  to the specified file.  The special file "<TT>STDOUT</TT>" selects the standard
  output stream, which is usually the terminal but which may be redirected.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_delim">delim = "<TT> </TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='delim' Line='delim = " "'>
  <DD>The delimiter placed between joined input lines.  The default is a space
  (note that this will not be visible when viewed with <B>eparam</B>).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_missing">missing = "<TT>Missing</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='missing' Line='missing = "Missing"'>
  <DD>This string is substituted for missing lines when going beyond the end
  of shorter input files.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_maxchars">maxchars = 161</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maxchars' Line='maxchars = 161'>
  <DD>Maximum number of characters in output lines.  Longer output lines will
  be truncated and a warning may be given.  Note that this number always
  includes the final newline character.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_shortest">shortest = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='shortest' Line='shortest = yes'>
  <DD>Stop at the end of the shortest file?  If the input files are of unequal
  number of lines then this option provides for stopping at the end
  of the shortest file or the end of the longest file.  In the latter case
  the string specified by the parameter <I>missing</I> is used for input
  from the shorter files.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Warnings are printed to the standard error stream giving the number
  of lines exceeding the maximum number of output characters, the number
  of lines exceeding the IRAF line length limit, and the number of files
  completed in case the files are of unequal length.  If verbose is no
  then no warnings are printed.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The task <B>joinlines</B> reads lines from each of the input text files and
  joins them into one line separated by the specified delimiter.  This is useful
  for making multicolumn files from individual files.  The output may
  be directed to the standard output, the default, or appended to a
  file.
  <P>
  The list of input files may be given in either <I>list1</I> or with
  <I>list2</I>.  The second list is only used if two arguments are given
  on the command line.  This feature is provided for compatibility with
  an earlier version of this task which only joined two files given separately.
  <P>
  There is no limit to the possible number of characters per output line but
  the parameter <I>maxchars</I> may be used to truncate long lines.  This
  can be important because many IRAF tasks read files a line at a time
  with a fixed sized line buffer.  Also other tasks and host programs
  (for example UNIX/vi) have line limits as well.  If an input line
  exceeds these limits incorrect results may occur.  The IRAF limit is 
  SZ_LINE characters (see hlib$iraf.h) and so the default for the maximum 
  number of output characters is set at the current value.  One may 
  chose to go beyond this limit.
  <P>
  If the input files do not all have the same number of lines then there
  are two courses of action.  If the <I>shortest</I> parameter is set
  then the join operation is terminated with the last line from the
  shortest file.  If it is not set then the string from the parameter
  <I>missing</I> is substituted for input from the shorter files until
  the end of the longest file is reached.  Note that the delimiter will
  still be placed between input lines even when such lines are missing.
  <P>
  There are three types of warnings which may be produced if the verbose
  flag is set.  These are warnings for the number of lines exceeding the
  specified maximum number of characters resulting in truncated output,
  the number of lines exceeding the IRAF line buffer limit, and a warning
  when some input files are shorter than others.  The
  warnings are printed on the standard error stream so that redirection
  of the standard output will still leave the warnings on the user's
  terminal.  To redirect the warnings one must include the standard error
  stream in the redirection syntax.  See the examples for how to do
  this.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Join the two files "<TT>names</TT>" and "<TT>titles</TT>", redirecting the output into a third
  file "<TT>personnel_file</TT>".
  <P>
  <PRE>
  	cl&gt; joinlines names titles &gt; personnel_file
  </PRE>
  <P>
  2. Join a set of magnitudes given in separate files and place the
  output in "<TT>allmags</TT>".  Separate the columns by tabs.
  <P>
  <PRE>
  	cl&gt; joinlines mags* out=allmags delim="	"
  </PRE>
  <P>
  3. Join a set of files into long lines and redirect the error output
  to a log file.  Set missing lines to INDEF value.
  <P>
  <PRE>
  	cl&gt; joinlines tables* out=jointbls miss=INDEF short- ver+ &gt;&amp; log
  </PRE>
  <P>
  4. Join the second column from the output of a program to the previous
  results.  This illustrates the use of pipes.
  <P>
  <PRE>
  	cl&gt; myprog | fields STDIN 2 | joinlines last STDIN &gt; new
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  fields
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>