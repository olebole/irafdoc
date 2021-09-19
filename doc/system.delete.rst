.. _delete:

delete: Delete a file or files (use IMDELETE to delete imagefiles)
==================================================================

**Package: system**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  delete -- delete a file or files
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  delete files
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>files</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='files' Line='files' -->
  <dd>The list of files to be deleted.
  </dd>
  </dl>
  <dl>
  <dt><b>verify = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verify' Line='verify = no' -->
  <dd>Check with the user before deleting a file.  If verify is enabled the file
  name is printed and the user is queried before the default action is taken.
  </dd>
  </dl>
  <dl>
  <dt><b>default_action = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='default_action' Line='default_action = yes' -->
  <dd>This is the default action to take when operating in <tt>"verify"</tt> mode.
  For example, if the default action is <tt>"yes"</tt>, one need only type RETURN in
  response to the verify prompt to delete the file.
  </dd>
  </dl>
  <dl>
  <dt><b>allversions = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='allversions' Line='allversions = yes' -->
  <dd>Delete all versions of a file.  This parameter has no effect on systems like
  UNIX which do not support multiple file versions.
  </dd>
  </dl>
  <dl>
  <dt><b>subfiles = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='subfiles' Line='subfiles = yes' -->
  <dd>Delete subfiles.  Not currently used.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  <i>Delete</i> destroys a file or files and returns the space they occupied to
  the host system, to be reused for other files.  Once a file has been deleted,
  it is gone forever (unless a copy exists somewhere).  Enabling <i>verify</i>
  gives one the opportunity to say yes or no before each file is deleted; this
  is particularly useful when <i>files</i> is a template.  Note that
  <i>protect</i> can be used to protect files from deletion, accidental or
  otherwise.  Imagefiles are automatically protected by the system to remind
  the user to use <i>imdelete</i> to delete images (this is necessary because
  an image is stored in more than one physical file).
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Delete all files with extension <tt>".x"</tt>, verifying each file deletion before
  it is performed.
  </p>
  <p>
  	cl&gt; delete *.x ver+
  </p>
  <p>
  2. List all files in the current directory, deleting only those files for
  which the user responds to the verify prompt with <tt>"yes"</tt> or <tt>"y"</tt>.  Note that
  <tt>"delete *"</tt> is a very dangerous operation.
  </p>
  <p>
  	cl&gt; delete * ver+ def=no
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  protect, unprotect, imdelete
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
