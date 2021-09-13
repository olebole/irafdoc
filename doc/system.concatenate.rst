concatenate — Concatenate a list of files
=========================================

**Package: system**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>concatenate (Nov84)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>system</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>concatenate (Nov84)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>concatenate</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  concatenate -- connect files together into one big file
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  concatenate files [output_file]
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_files">files</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='files' Line='files'>
  <DD>The list of input files.  The standard input, STDIN, may be specified to
  interactively enter a few lines of text rather than read from a disk file.
  All input files should be of the same type (binary or text).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output_file">output_file</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output_file' Line='output_file'>
  <DD>The name of the output file.  If no file is explicitly specified the
  standard output (STDOUT) is used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_out_type">out_type = in_type</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='out_type' Line='out_type = in_type'>
  <DD>The output file type is forced if this parameter is defined as "<TT>binary</TT>"
  or "<TT>text</TT>".  If "<TT>out_type</TT>" does not begin with a "<TT>b</TT>" (or "<TT>B</TT>"), or a
  "<TT>t</TT>" ("<TT>T</TT>"), then the output type is either "<TT>text</TT>", if the output file is
  the standard output, or is determined from the type of the first input file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_append">append = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='append' Line='append = no'>
  <DD>If set to "<TT>yes</TT>", "<TT>files</TT>" are appended to "<TT>output_file</TT>".
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Each file in the input file list is appended to the output file.
  If "<TT>output_file</TT>" is not the standard output, and if output redirection ("<TT>&gt;</TT>")
  was not specified on the command line, the resulting stream of data is placed
  in a file.  The input can be STDIN, which makes for an easy way to enter a
  few lines of text into a file (but <I>type</I> is usually more convenient).
  If entering data via the standard input, type the end of file character,
  e.g., &lt;ctrl/z&gt;, to terminate the input sequence.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Write out file1, followed by file2, to the terminal screen.  Note that
  there must be no space after the comma.
  <P>
  <PRE>
  	cl&gt; concatenate file1,file2
  </PRE>
  <P>
  2. Write out files file1 and file2 into the new file "<TT>outfile</TT>".
  <P>
  <PRE>
  	cl&gt; concatenate file1,file2 outfile
  </PRE>
  <P>
  3. Copy what you type (up to the end-of-file character) into the file junk.
  <P>
  <PRE>
  	cl&gt; concatenate STDIN junk
  </PRE>
  <P>
  4. Write out the contents of each of the files whose names are given in "<TT>list</TT>",
  one per line, and append this data to "<TT>junk</TT>".
  <P>
  <PRE>
  	cl&gt; concatenate @list junk append+
  </PRE>
  <P>
  5. Concatenation is also possible using <I>type</I>, e.g., the following
  command will append the contents of "<TT>file</TT>" to the file "<TT>outfile</TT>", which will
  be created if it does not already exist.
  <P>
  	cl&gt; type file &gt;&gt; outfile
  <P>
  The redirect-append operator "<TT>&gt;&gt;</TT>" may be used to append the output of any
  task to a file.
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_notes">NOTES</A></H2>
  <! BeginSection: 'NOTES'>
  <UL>
  All input files should be of the same type, either all "<TT>text</TT>" or all
  "<TT>binary</TT>".
  </UL>
  <! EndSection:   'NOTES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  copy, type
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'NOTES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>