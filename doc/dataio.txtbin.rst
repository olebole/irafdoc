txtbin — Convert an IRAF text file to a binary file
===================================================

**Package: dataio**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>txtbin (Jun86)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>dataio</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>txtbin (Jun86)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>txtbin</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  txtbin -- convert text files to binary files
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  txtbin text_file binary_file
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_text_file">text_file</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='text_file' Line='text_file'>
  <DD>Input file name or template, e.g. "<TT>abc</TT>" or "<TT>abc.*</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_binary_file">binary_file</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='binary_file' Line='binary_file'>
  <DD>Output file name. If multiple input files the file_number will be
  added to the output file name.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = "<TT>yes</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = "yes"'>
  <DD>Print messages about files processed?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Convert a text file on disk to a binary file on disk.
  <P>
  	cl&gt; txtbin text_file binary_file
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  bintxt
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>