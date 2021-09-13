entab — Replace blanks with tabs and blanks
===========================================

**Package: utilities**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>entab (Mar84)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>utilities</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>entab (Mar84)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>entab</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  entab -- replaces blanks by tabs and blanks
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  entab files
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_files">files</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='files' Line='files'>
  <DD>Template specifying the files to be processed, e.g. "<TT>file</TT>" or "<TT>file*</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_tablist">tablist = "<TT>9 +8</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='tablist' Line='tablist = "9 +8"'>
  <DD>String containing a list of tabstops separated by blanks or commas.
  A two element string of the form "<TT>m +n</TT>" will set
  tabstops in every n columns beginning in column m.
  A null string defaults to "<TT>9 +8</TT>".
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_example">EXAMPLE</A></H2>
  <! BeginSection: 'EXAMPLE'>
  <UL>
  Convert the file "<TT>prog.c</TT>", written using full tabstop indents, to
  an equivalent file with an initial indent of one full tabstop, 
  with 4 space indents thereafter.
  <P>
  <PRE>
  	cl&gt; detab prog.c tab='9 +4' | entab &gt; temp
  	cl&gt; delete prog.c
  	cl&gt; rename temp prog.c
  </PRE>
  </UL>
  <! EndSection:    'EXAMPLE'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'EXAMPLE'  >
  
  </BODY>
  </HTML>