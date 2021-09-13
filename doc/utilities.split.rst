split — Split a large file into smaller segments
================================================

**Package: utilities**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>split (Sep86)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>utilities</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>split (Sep86)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>split</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  split -- split a large file into smaller segments
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  split input output
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The name of the input file (only a single file can be processed).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>The root name of the output files.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nlines">nlines = 1000</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nlines' Line='nlines = 1000'>
  <DD>The maximum number of lines per output segment file, if the input file
  is a text file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nbytes">nbytes = 16384</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nbytes' Line='nbytes = 16384'>
  <DD>The maximum number of bytes per output segment file, if the input file
  is a binary file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_maxfiles">maxfiles = 999</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maxfiles' Line='maxfiles = 999'>
  <DD>Maximum number of output files.  Used to determine the amount of zero
  padding needed for the filename extensions.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print the name and size of each output file as it is generated.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <I>split</I> task is used to break large files up into smaller segments,
  e.g., when it is necessary to deal with an unmanageably large file.
  Lacking any knowledge of the file structure, the segments are broken on
  arbitrarily located but equally spaced boundaries.  The segments may
  subsequently be reassembled into larger segments of the original file with
  <I>concatenate</I> or <I>copy</I> (with output redirection), or <I>split</I> may
  be applied again to break a large segment up into smaller segments without
  losing any information.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Split a large text file into segments, each of which is the default size.
  <P>
  	cl&gt; split textfile seg
  <P>
  2. Split a large <I>tar</I> format archive file (10240 byte records) up into
  a series of smaller files, each of which contains 10 records from the input
  tar file.
  <P>
  	cl&gt; split big.arc seg nb=(10240*10)
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_time_requirements">TIME REQUIREMENTS</A></H2>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  very fast
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  concatenate, copy
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>