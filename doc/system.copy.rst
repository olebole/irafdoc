copy — Copy a file or files (use IMCOPY for imagefiles)
=======================================================

**Package: system**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>copy (Nov84)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>system</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>copy (Nov84)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>copy</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  copy -- copy a file, or a set of files to a directory
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  copy input output
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The input file or list of files to be copied.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>The (new) output file when copying one file to another, or the destination
  directory when copying a set of files.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>If set to "<TT>yes</TT>", a line of the type "<TT> from -&gt; to </TT>" is printed on the
  terminal for each file copied to a directory.  This parameter is not
  used when copying one file to another.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Copy makes a copy of a single file, or it copies a set of files to a different
  directory.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Copy all files in the current directory with extension "<TT>.x</TT>" to the
  directory "<TT>home$src</TT>".  As each copy is made, the user is informed.
  <P>
  	cl&gt; copy *.x home$src ver+
  <P>
  2. Make a copy "<TT>fred.BAK</TT>" of the file "<TT>fred</TT>".
  <P>
  	cl&gt; copy fred fred.BAK
  <P>
  3. Copy the "<TT>graphcap</TT>" file from the remote node "<TT>lyra</TT>" to the current node,
  without changing the name of the file.  Note that "<TT>.</TT>" is a synonym for the
  current directory.
  <P>
  	cl&gt; copy lyra!dev$graphcap .
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  concatenate, movefiles
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>