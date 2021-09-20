.. _rmfiles:

rmfiles: Find/delete files in subdirectories
============================================

**Package: softools**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  rmfiles [-dnv] [-f progfile] rootdir action extns
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>-d</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='' Line='-d' -->
  <dd>Print debug messages.
  </dd>
  </dl>
  <dl>
  <dt><b>-n</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='' Line='-n' -->
  <dd>No execute; do not delete files.  This option may be used to generate
  a list of binary files for some purpose other than deletion, or to verify
  the delete operation before destroying the files.
  </dd>
  </dl>
  <dl>
  <dt><b>-v</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='' Line='-v' -->
  <dd>Print names of files as they are deleted.
  </dd>
  </dl>
  <dl>
  <dt><b>-f progfile</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='' Line='-f progfile' -->
  <dd>Take delete commands from the named file.  If this option is specified
  the remaining arguments are normally omitted.
  </dd>
  </dl>
  <dl>
  <dt><b>rootdir</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='rootdir' Line='rootdir' -->
  <dd>The root directory of the directory tree to be pruned.  This must be a
  path from the current directory or from a logical directory.
  </dd>
  </dl>
  <dl>
  <dt><b>action</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='action' Line='action' -->
  <dd>The possible actions are listed below.  This is a required parameter.
  <dl>
  <dt><b></b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='' Line=' ' -->
  <dd><dl>
  <dt><b>-all</b></dt>
  <!-- Sec='PARAMETERS' Level=2 Label='' Line='-all' -->
  <dd>Delete all files.
  </dd>
  </dl>
  <dl>
  <dt><b>-allbut</b></dt>
  <!-- Sec='PARAMETERS' Level=2 Label='' Line='-allbut' -->
  <dd>Delete all files except those with the listed extensions.
  </dd>
  </dl>
  <dl>
  <dt><b>-only</b></dt>
  <!-- Sec='PARAMETERS' Level=2 Label='' Line='-only' -->
  <dd>Delete only those files with the listed extensions.
  </dd>
  </dl>
  </dd>
  </dl>
  </dd>
  </dl>
  <dl>
  <dt><b>extns</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='extns' Line='extns' -->
  <dd>A list of filename extensions delimited by spaces, e.g., <span style="font-family: monospace;">".a .o .e .hlp"</span>.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The <i>rmfiles</i> utility is used to delete (or list) files in one or more
  directory trees.  If only one directory tree is to be pruned the necessary
  instructions can be entered on the command line, otherwise a program file
  must be used.  When developing a program file, a dry run using the <span style="font-family: monospace;">"-n"</span>
  switch is recommended to see what files will be deleted.
  </p>
  <p>
  If a program file is used each line in the file has one of two possible
  formats.  If a directory is to be pruned the syntax is the same as is
  used when a one line program is entered on the command line, i.e.:
  </p>
  <p>
  	rootdir action extns
  </p>
  <p>
  The significance of each field is as described in the ARGUMENTS section
  above.  The program file may also contain lines of the form
  </p>
  <p>
  	-file filename
  </p>
  <p>
  to delete one or more files by name.  This is useful for removing files
  which do not fit into any recognizable class.
  </p>
  <p>
  Comments and blank lines are permitted anywhere in the program file.
  All filenames are IRAF virtual filenames (or host filenames).
  </p>
  <p>
  <i>Rmfiles</i> is a bootstrap utility implemented as a foreign task, hence
  it may be called either from within IRAF or from the host system.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Delete all .o, .e, .a, and .hd files in the directory <span style="font-family: monospace;">"iraf$pkg"</span>.
  Print the names of the files as they are deleted.  Note that one must
  move to the directory containing the directory to be pruned before running
  <i>rmfiles</i>.
  </p>
  <pre>
  	cl&gt; cd iraf
  	cl&gt; rmfiles -v pkg .o .e .a .hd
  </pre>
  <p>
  2. Strip the entire IRAF system, using the program in file <span style="font-family: monospace;">"hlib$stripper"</span>.
  The use of the $ in the filename here could cause problems on some systems
  since <i>rmfiles</i> is a foreign task.
  </p>
  <pre>
  	cl&gt; cd iraf
  	cl&gt; rmfiles -vf hlib$stripper
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  rmbin, rtar, wtar
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
