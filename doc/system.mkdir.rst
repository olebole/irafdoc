mkdir — Create a new directory
==============================

**Package: system**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>mkdir (May85)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>system</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>mkdir (May85)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>mkdir</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  mkdir -- make a new directory
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  mkdir newdir
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_newdir">newdir</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='newdir' Line='newdir'>
  <DD>New directory or subdirectory to be made.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>Mkdir</I> creates a new directory with the given name.
  <I>Newdir</I> may be an IRAF virtual directory name (not a logical name)
  or a host directory name.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Make a subdirectory named "<TT>sub1</TT>".
  <P>
  	cl&gt; mkdir sub1
  <P>
  2. Make a subdirectory "<TT>sub2</TT>" below "<TT>sub1</TT>".  The subdirectory "<TT>sub1</TT>" must
  already exist.
  <P>
  	cl&gt; mkdir sub1/sub2
  <P>
  3. Make a directory "<TT>blue</TT>" at the same level in the directory hierarchy as
  the current directory ("<TT>..</TT>" is a synonym for the previous directory).
  <P>
  	cl&gt; mkdir ../blue
  </UL>
  <! EndSection:    'EXAMPLES'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES'  >
  
  </BODY>
  </HTML>