mkmanpage — Make a manual page
==============================

**Package: softools**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>mkmanpage (Feb86)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>softools</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>mkmanpage (Feb86)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>mkmanpage</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  mkmanpage -- create and edit a new manual page
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  mkmanage module
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_module">module</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='module' Line='module'>
  <DD>The name of the program to be documented, i.e., the name that will appear at
  the top of the manual page, and the root name of the "<TT>.hlp</TT>" file to be
  created.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_clformat">clformat = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='clformat' Line='clformat = yes'>
  <DD>Make a CL format manual page template?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_cltemplate">cltemplate = "<TT>doc$mancl.hlp</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cltemplate' Line='cltemplate = "doc$mancl.hlp"'>
  <DD>Filename of the template file for a CL manual page.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xtemplate">xtemplate = "<TT>doc$manx.hlp</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xtemplate' Line='xtemplate = "doc$manx.hlp"'>
  <DD>Filename of the template file for a library procedure manual page.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <I>mkmanpage</I> task is used to create a fill-in-the-blanks type
  template, to be edited to create the manual page for the named help module
  or task.  Depending upon the type of manual page to be created, <I>mkmanpage</I>
  copies the template file to the current directory, creating a new file with
  the name "<TT>module.hlp</TT>", where <I>module</I> is the name entered on the
  command line.  The editor is called up to edit the file and the task exits.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Make a new manual page for task "<TT>page</TT>".
  <P>
  	cl&gt; mkmanpage page
  <P>
  The task creates a file "<TT>page.hlp</TT>" in the current directory, and calls
  up the editor to edit the new file.
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  mkhelpdb, help, lroff
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>