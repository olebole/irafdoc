bintxt — Convert a binary file to an IRAF text file
===================================================

**Package: dataio**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>bintxt (Jun86)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>dataio</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>bintxt (Jun86)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>bintxt</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  bintxt -- Convert binary files containing only text to text files
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  bintxt binary_file text_file
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_binary_file">binary_file</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='binary_file' Line='binary_file'>
  <DD>Input file name or template,  e.g. "<TT>file1</TT>" or "<TT>file*</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_text_file">text_file</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='text_file' Line='text_file'>
  <DD>The output file name.  If multiple input files the filenumber will
  be concatenated onto the output file name.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print messages of actions performed?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Convert a binary file on disk to a text file on disk.
  <P>
  	cl&gt; bintxt binary_file text_file
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  txtbin
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>