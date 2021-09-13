gkidir — Directory listing of metacode file
===========================================

**Package: plot**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>gkidir (Jan86)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>plot</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>gkidir (Jan86)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>gkidir</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  gkidir -- print directory of plots within the named metacode file
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  gkidir input
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The metacode file or files to be examined.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Task <B>gkidir</B> examines GKI metacode files, and prints a directory of
  the plots contained in each input file.  Each plot is listed with its
  size and an identifying title string.  The title string is the MFTITLE
  string if given, or else the longest GTEXT string found (hopefully the
  plot title), or else the string "<TT>(no title)</TT>".  The output format is as
  follows:
  <PRE>
  <P>
  	file1: 
  	    [1] (1234 words)	title_string
  	    [2] (78364 words)	title_string
  <P>
  	file2:
  	    [1] (874 words)	title_string
  		.
  		.
  		.
  <P>
  </PRE>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. List the plots in the GKI metacode file "<TT>file</TT>":
  <P>
      cl&gt; gkidir file
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  gkiextract
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>