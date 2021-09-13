delete — Delete a file or files (use IMDELETE to delete imagefiles)
===================================================================

**Package: system**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>delete (Nov84)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>system</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>delete (Nov84)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>delete</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  delete -- delete a file or files
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  delete files
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_files">files</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='files' Line='files'>
  <DD>The list of files to be deleted.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verify">verify = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verify' Line='verify = no'>
  <DD>Check with the user before deleting a file.  If verify is enabled the file
  name is printed and the user is queried before the default action is taken.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_default_action">default_action = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='default_action' Line='default_action = yes'>
  <DD>This is the default action to take when operating in "<TT>verify</TT>" mode.
  For example, if the default action is "<TT>yes</TT>", one need only type RETURN in
  response to the verify prompt to delete the file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_allversions">allversions = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='allversions' Line='allversions = yes'>
  <DD>Delete all versions of a file.  This parameter has no effect on systems like
  UNIX which do not support multiple file versions.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_subfiles">subfiles = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='subfiles' Line='subfiles = yes'>
  <DD>Delete subfiles.  Not currently used.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>Delete</I> destroys a file or files and returns the space they occupied to
  the host system, to be reused for other files.  Once a file has been deleted,
  it is gone forever (unless a copy exists somewhere).  Enabling <I>verify</I>
  gives one the opportunity to say yes or no before each file is deleted; this
  is particularly useful when <I>files</I> is a template.  Note that
  <I>protect</I> can be used to protect files from deletion, accidental or
  otherwise.  Imagefiles are automatically protected by the system to remind
  the user to use <I>imdelete</I> to delete images (this is necessary because
  an image is stored in more than one physical file).
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Delete all files with extension "<TT>.x</TT>", verifying each file deletion before
  it is performed.
  <P>
  	cl&gt; delete *.x ver+
  <P>
  2. List all files in the current directory, deleting only those files for
  which the user responds to the verify prompt with "<TT>yes</TT>" or "<TT>y</TT>".  Note that
  "<TT>delete *</TT>" is a very dangerous operation.
  <P>
  	cl&gt; delete * ver+ def=no
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  protect, unprotect, imdelete
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>