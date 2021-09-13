mktags — Tag all procedure declarations in a set of files
=========================================================

**Package: softools**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>mktags (Sep85)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>softools</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>mktags (Sep85)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>mktags</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  mktags -- tag all procedure declarations in a set of files
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  mktags
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_files">files = "<TT>*.x</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='files' Line='files = "*.x"'>
  <DD>The files to be tagged, e.g., "<TT>*.x</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_listing">listing = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='listing' Line='listing = no'>
  <DD>If this switch is enabled a sorted list of all procedures declared in the
  set of files will be printed on the standard output, giving the procedure
  name, line and file number, and procedure declaration on each output line.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_tags">tags = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='tags' Line='tags = yes'>
  <DD>If this switch is enabled a "<TT>tags</TT>" file will be written in the current
  directory for use with the VI editor.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The named files are scanned for procedure declarations.  Each such declaration
  found is buffered internally.  When all files have been scanned the internal
  tag database is sorted and the output files are generated.  Two types of
  output are provided:
  <DL>
  <DT><B><A NAME="l_"></A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line=' '>
  <DD><DL>
  <DT><B><A NAME="l_">[1]</A></B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='' Line='[1]'>
  <DD>A summary of all procedures defined in the given set of files may be printed
  on the standard output.  This output may be used as a printed index to manually
  find procedures in the given file set.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">[2]</A></B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='' Line='[2]'>
  <DD>A "<TT>tags</TT>" format database file (a text file) may be written.  This file is
  read by the VI editor when a command of the form "<TT>:ta tag</TT>" is entered.
  This command is used to edit procedures regardless of the file in which they
  reside.  For example, to edit procedure "<TT>maxmin</TT>", enter command "<TT>:ta maxmin</TT>"
  when in VI.
  </DD>
  </DL>
  </DD>
  </DL>
  <P>
  <P>
  By default the operation of <I>mktags</I> is to silently update the tags
  database.  If a printed listing is desired the <I>listing</I> switch must
  be enabled.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  A fixed amount of storage is allocated internally and overflow will occur if
  there are too many tags (procedures) or if there is too much text (the string
  buffer will overflow).
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>