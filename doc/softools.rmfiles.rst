rmfiles — Find/delete files in subdirectories
=============================================

**Package: softools**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>rmfiles (Jul86)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>softools</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>rmfiles (Jul86)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>rmfiles</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  rmfiles -- find/remove files in subdirectories
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  rmfiles [-dnv] [-f progfile] rootdir action extns
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_">-d</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='-d'>
  <DD>Print debug messages.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">-n</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='-n'>
  <DD>No execute; do not delete files.  This option may be used to generate
  a list of binary files for some purpose other than deletion, or to verify
  the delete operation before destroying the files.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">-v</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='-v'>
  <DD>Print names of files as they are deleted.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">-f progfile</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='-f progfile'>
  <DD>Take delete commands from the named file.  If this option is specified
  the remaining arguments are normally omitted.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_rootdir">rootdir</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rootdir' Line='rootdir'>
  <DD>The root directory of the directory tree to be pruned.  This must be a
  path from the current directory or from a logical directory.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_action">action</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='action' Line='action'>
  <DD>The possible actions are listed below.  This is a required parameter.
  <DL>
  <DT><B><A NAME="l_"></A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line=' '>
  <DD><DL>
  <DT><B><A NAME="l_">-all</A></B></DT>
  <! Sec='PARAMETERS' Level=2 Label='' Line='-all'>
  <DD>Delete all files.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">-allbut</A></B></DT>
  <! Sec='PARAMETERS' Level=2 Label='' Line='-allbut'>
  <DD>Delete all files except those with the listed extensions.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">-only</A></B></DT>
  <! Sec='PARAMETERS' Level=2 Label='' Line='-only'>
  <DD>Delete only those files with the listed extensions.
  </DD>
  </DL>
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_extns">extns</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='extns' Line='extns'>
  <DD>A list of filename extensions delimited by spaces, e.g., "<TT>.a .o .e .hlp</TT>".
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <I>rmfiles</I> utility is used to delete (or list) files in one or more
  directory trees.  If only one directory tree is to be pruned the necessary
  instructions can be entered on the command line, otherwise a program file
  must be used.  When developing a program file, a dry run using the "<TT>-n</TT>"
  switch is recommended to see what files will be deleted.
  <P>
  If a program file is used each line in the file has one of two possible
  formats.  If a directory is to be pruned the syntax is the same as is
  used when a one line program is entered on the command line, i.e.:
  <P>
  	rootdir action extns
  <P>
  The significance of each field is as described in the ARGUMENTS section
  above.  The program file may also contain lines of the form
  <P>
  	-file filename
  <P>
  to delete one or more files by name.  This is useful for removing files
  which do not fit into any recognizable class.
  <P>
  Comments and blank lines are permitted anywhere in the program file.
  All filenames are IRAF virtual filenames (or host filenames).
  <P>
  <I>Rmfiles</I> is a bootstrap utility implemented as a foreign task, hence
  it may be called either from within IRAF or from the host system.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Delete all .o, .e, .a, and .hd files in the directory "<TT>iraf$pkg</TT>".
  Print the names of the files as they are deleted.  Note that one must
  move to the directory containing the directory to be pruned before running
  <I>rmfiles</I>.
  <P>
  <PRE>
  	cl&gt; cd iraf
  	cl&gt; rmfiles -v pkg .o .e .a .hd
  </PRE>
  <P>
  2. Strip the entire IRAF system, using the program in file "<TT>hlib$stripper</TT>".
  The use of the $ in the filename here could cause problems on some systems
  since <I>rmfiles</I> is a foreign task.
  <P>
  <PRE>
  	cl&gt; cd iraf
  	cl&gt; rmfiles -vf hlib$stripper
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  rmbin, rtar, wtar
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>