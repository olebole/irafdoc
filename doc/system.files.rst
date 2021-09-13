files — Expand a file template into a list of files
===================================================

**Package: system**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>files (Jun86)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>system</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>files (Jun86)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>files</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  files -- expand a file name template into a list of files
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  files template
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_template">template</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='template' Line='template'>
  <DD>A file name template specifying the set of files to be listed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_sort">sort = "<TT>yes</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sort' Line='sort = "yes"'>
  <DD>Sort the file list.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>Files</I> lists all files matching the given template.  The existence of
  the listed files is checked only if pattern matching is used, hence <I>files</I>
  may also be used to parse a comma delimited list of strings which are not
  necessarily filenames.  <I>Files</I> performs the same function as "<TT>dir l+</TT>"
  but is simpler and more convenient to use when generating file lists.
  <P>
  The <I>files</I> task and all other tasks which operate upon groups of files
  use the <B>file template</B> facility to specify the set of files to be
  operated upon.  This should not be confused with the <B>image template</B>
  facility, used by tasks which operate upon sets of images and which is
  documented in the manual page for the <I>sections</I> task.
  <P>
  Pattern matching in a file template is provided by the usual pattern matching
  meta-characters "<TT>*?[]</TT>", documented in the CL User's Guide.  Pattern matching 
  is used to select files from one or more directories.  In addition, the
  filename template notation provides two operators for generating new filenames
  from the matched filenames.  These are the <B>concatenation</B> operator "//"<TT>,
  and the <B>string substitution</B> operator "<TT>%chars%newchars%</TT>".
  The concatenation operator concatenates either a prefix to a filename,
  or a suffix to the root of a filename.  The string substitution operator
  uses the "<TT>chars</TT>" to match filenames, and then replaces the "<TT>chars</TT>" by the
  "<TT>newchars</TT>" to generate the final output filename.  Either string may be null
  length to insert into or delete characters from a filename.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Generate a single column list of files in the current directory,
  sorted in ASCII collating sequence.
  <P>
  	cl&gt; files
  <P>
  2. Generate an unsorted single column list of files in logical directory
  "<TT>lib$</TT>".  Each entry in the output list is of the form "<TT>lib$...</TT>".
  <P>
  	cl&gt; files lib$ sort-
  <P>
  3. Generate a file list to be used to make a set of new files.  The new file
  names will be the old file names with "<TT>_1</TT>" concatenated to the root, e.g.,
  "<TT>root.x</TT>" would map to "<TT>root_1.x</TT>" and so on.
  <P>
  	cl&gt; files root.*//_1
  <P>
  4. Generate a file list similar to that in [3], adding a directory prefix
  to each filename.
  <P>
  	cl&gt; files dir$//root.*
  <P>
  5. Use string substitution to change the filename extension of a set of files
  to "<TT>.y</TT>".
  <P>
  	cl&gt; files root.%*%y%
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  directory, pathnames, images.sections
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>