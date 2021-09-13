tee — Tee the standard output into a file
=========================================

**Package: system**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>tee (Nov84)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>system</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>tee (Nov84)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>tee</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  tee -- tee the standard output to a file
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  tee file
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_file">file</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='file' Line='file'>
  <DD>The name of the output file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_out_type">out_type = "<TT>text</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='out_type' Line='out_type = "text"'>
  <DD>The type of output file to be created, either "<TT>text</TT>" or "<TT>binary</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_append">append = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='append' Line='append = no'>
  <DD>If set, append to an existing file, otherwise create a new file.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>Tee</I> copies its input to both the standard output and the named file.
  Its primary use is in pipes where one wants to capture some intermediate output.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. The results of the <I>set</I> command are captured in the file "<TT>temp</TT>",
  and are also passed on to the "<TT>match</TT>" command.  The result is
  a "<TT>temp</TT>" file of perhaps 100 lines, with the output to the screen
  only around 5 lines.
  <P>
  	cl&gt; set | tee temp | match tty
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  Since the processes in an IRAF pipe execute serially rather than concurrently,
  the teed output will not appear until all tasks to the left have completed.
  </UL>
  <! EndSection:    'BUGS'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS'  >
  
  </BODY>
  </HTML>