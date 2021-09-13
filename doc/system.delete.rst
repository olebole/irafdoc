.. _delete:

delete — Delete a file or files (use IMDELETE to delete imagefiles)
===================================================================

**Package: system**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  delete -- delete a file or files
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  delete files
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>files</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='files' Line='files'>
  <DD>The list of files to be deleted.
  </DD>
  </DL>
  <DL>
  <DT><B>verify = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verify' Line='verify = no'>
  <DD>Check with the user before deleting a file.  If verify is enabled the file
  name is printed and the user is queried before the default action is taken.
  </DD>
  </DL>
  <DL>
  <DT><B>default_action = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='default_action' Line='default_action = yes'>
  <DD>This is the default action to take when operating in "<TT>verify</TT>" mode.
  For example, if the default action is "<TT>yes</TT>", one need only type RETURN in
  response to the verify prompt to delete the file.
  </DD>
  </DL>
  <DL>
  <DT><B>allversions = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='allversions' Line='allversions = yes'>
  <DD>Delete all versions of a file.  This parameter has no effect on systems like
  UNIX which do not support multiple file versions.
  </DD>
  </DL>
  <DL>
  <DT><B>subfiles = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='subfiles' Line='subfiles = yes'>
  <DD>Delete subfiles.  Not currently used.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
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
  <H3>Examples</H3>
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
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  protect, unprotect, imdelete
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
