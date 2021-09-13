detab — Replace tabs with tabs and blanks
=========================================

**Package: utilities**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>detab (Mar84)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>utilities</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>detab (Mar84)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>detab</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  detab -- remove tab characters from a file or files
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  detab files
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_files">files</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='files' Line='files'>
  <DD>Template specifying files to be processed e.g. "<TT>file1</TT>" or "<TT>file*</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_tablist">tablist = "<TT>9 +8</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='tablist' Line='tablist = "9 +8"'>
  <DD>String containing a list of tabstops separated by blanks or commas.
  Alternatively a two element string of the form m +n will set
  tabstops every n columns beginning in column m.  A null string will
  default to "<TT>9 +8</TT>".
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_example">EXAMPLE</A></H2>
  <! BeginSection: 'EXAMPLE'>
  <UL>
  Remove the tabs from file "<TT>cubspl.f</TT>", using the default tab stops.
  <P>
  <PRE>
  	cl&gt; detab cubspl.f &gt; temp
  	cl&gt; delete cubspl.f
  	cl&gt; rename temp cubspl.f
  </PRE>
  </UL>
  <! EndSection:    'EXAMPLE'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'EXAMPLE'  >
  
  </BODY>
  </HTML>