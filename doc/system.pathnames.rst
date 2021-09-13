pathnames — Expand a file template into a list of OS pathnames
==============================================================

**Package: system**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>pathnames (Nov84)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>system</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>pathnames (Nov84)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>pathnames</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  pathnames -- print the host pathnames for a set of files
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  pathnames [template]
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_template">template</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='template' Line='template'>
  <DD>A filename template specifying the set of files for which pathnames
  are desired.  If omitted, the pathname of the current working or default
  directory is printed.  The list of file names can come from the standard input.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_sort">sort = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sort' Line='sort = yes'>
  <DD>Sort the output in ASCII collating sequence.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>Pathnames</I> converts a list of IRAF virtual file names into their host
  system equivalents.  When called with no arguments, the function of
  <I>pathnames</I> is to print the current default directory.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Print the pathname of the current default directory (sample output for
  a VMS host system).
  <P>
  <PRE>
  	cl&gt; path
  	draco!DRB1:[IRAF.SYS.FIO]
  </PRE>
  <P>
  2. Translate the file "<TT>vfiles</TT>", containing a list of virtual filenames, into
  the equivalent list of host system filenames, e.g., for use as input to a
  foreign task.
  <P>
  	cl&gt; path @vfiles &gt; hfiles
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  directory, files
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>