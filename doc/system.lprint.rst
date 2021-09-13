lprint — Print a file on the line printer device
================================================

**Package: system**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>lprint (Nov84)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>system</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>lprint (Nov84)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>lprint</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  lprint -- print a file or files
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  lprint files
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_files">files</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='files' Line='files'>
  <DD>A filename template specifying the files to be printed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_device">device = "<TT>printer</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='device' Line='device = "printer"'>
  <DD>The output device.  If the value of <I>device</I> is the reserved string
  "<TT>printer</TT>", the name of the actual printer device is taken from the value
  of the environment variable "<TT>printer</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_map_cc">map_cc = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='map_cc' Line='map_cc = yes'>
  <DD>If set to "<TT>yes</TT>", any unprintable characters embedded in the text are printed
  in the form "<TT>^X</TT>", where ^A is &lt;ctrl/A&gt; (ASCII 1), and so on.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_paginate">paginate = "<TT>auto</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='paginate' Line='paginate = "auto"'>
  <DD>If <I>paginate</I> is set to "<TT>auto</TT>" and the standard input is not redirected,
  pages are broken and a header is printed at the top of each page.
  If <I>paginate</I> is set to "<TT>auto</TT>" and the standard input <I>is</I> redirected,
  the input text is not paginated, allowing proper operation when <I>lprint</I>
  is used in a pipe, e.g., taking input from <I>help</I>.
  If "<TT>paginate</TT>" is set to "<TT>yes</TT>", pages are broken even if the input text
  is being read from STDIN.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_label">label = "<TT>STDIN</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='label' Line='label = "STDIN"'>
  <DD>If displaying a header with input from the standard input, use the
  "<TT>label</TT>" string where the filename would appear in a normal header.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The named files, or the standard input, are printed on the standard
  line printer device.  Each file is printed starting at the top of a new
  page, with a header giving the page number and the date of last modification
  for the file.  Pagination and headers are normally suppressed when reading
  input from the standard input, but may be enabled if desired.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Print all files with an extension of either "<TT>.x</TT>" or "<TT>.h</TT>", followed by
  all files with the extension "<TT>.com</TT>".  Note that filename sorting occurs only
  within a comma delimited field of the filename template, hence the "<TT>*.[xh]</TT>"
  files are printed in sort order, followed by the "<TT>.com</TT>" files.
  <P>
  	cl&gt; lprint *.[xh],*.com
  <P>
  2. Print the output of the <I>imstat</I> task on the versatec printer,
  paginating the output with the given label on each page.  Note that the
  command may be broken after the "<TT>pipe</TT>" character without need for
  explicit backslash continuation.
  <P>
  <PRE>
  	cl&gt; imstat nite1.* |
  	&gt;&gt;&gt; lprint pag+ label="Image Statistics" device=versatec
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  type
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>