head — Print the first few lines of a text file
===============================================

**Package: system**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>head (Nov84)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>system</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>head (Nov84)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>head</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  head -- print the first few lines of the specified files
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  head files
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_files">files</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='files' Line='files'>
  <DD>The list of files to be dealt with, quite possibly given as
  a template, such a "<TT>image*</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nlines">nlines = 12</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nlines' Line='nlines = 12'>
  <DD>The number of lines to be printed.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>Head</I> prints, on the standard output, the first <I>nlines</I> of each
  file that matches the given file list.  If the file list has more than one
  name in it, a short header precedes each listing.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Print the first 12 lines of each help file in the current directory.
  <P>
  	cl&gt; head *.hlp
  <P>
  2. Print the first line of each help file.
  <P>
  	cl&gt; head *.hlp nl=1
  <P>
  3. Print the most recently defined <I>set</I> environment definitions.
  <P>
  	cl&gt; set | head
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  tail, page
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>