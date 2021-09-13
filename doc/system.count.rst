count — Count the number of lines, words, characters in a text file
===================================================================

**Package: system**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>count (Nov84)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>system</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>count (Nov84)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>count</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  count -- determine number of lines, words and characters in a file
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  count files
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_files">files</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='files' Line='files'>
  <DD>A template specifying the files to be examined.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  For each file, count determines the number of lines, words, and
  characters in the file.  A word is defined as a sequence of characters
  delimited by one or more blanks or tabs, or by the end of a line.
  If <I>count</I> is run on more than one file, each output line is identified
  by the file name, and a final output line gives the total number
  of lines, words, and characters in all files.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Count the number of lines, words and characters in all files in the
  current directory with the extensions "<TT>.x</TT>" and "<TT>.h</TT>".
  <P>
  	cl&gt; count *.[xh]
  <P>
  2. Count the number of .x files in the current directory.
  <P>
  	cl&gt; dir *.x op=1 | count
  <P>
  3. Count the number of <I>set</I> environment definitions.
  <P>
  	cl&gt; set | count
  <P>
  4. Count the number of references to the READ function in all .x files in
  the current directory.
  <P>
  	cl&gt; match "<TT>read#(</TT>" *.x | count
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  directory
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>