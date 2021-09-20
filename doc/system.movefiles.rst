.. _movefiles:

movefiles: Move files to a directory
====================================

**Package: system**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  movefiles -- move files to a directory
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  movefiles files directory
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>files</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='files' Line='files' -->
  <dd>A template specifying the file or files to be moved.
  </dd>
  </dl>
  <dl>
  <dt><b>directory</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='directory' Line='directory' -->
  <dd>The directory to which the files are to be moved.
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no' -->
  <dd>If set to <span style="font-family: monospace;">"yes"</span>, tell user as each file is moved.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  This routine moves the specified files to the named directory.
  If a subdirectory and a logical directory both exist with the same
  name as the destination directory, the subdirectory is used.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Move all files whose names start with `im' and end with `ab' to
  the directory `dir'.  Since <span style="font-family: monospace;">"verbose"</span> defaults to <span style="font-family: monospace;">"no"</span>, do the work silently.
  </p>
  <p>
  	cl&gt; movefiles im*ab dir
  </p>
  <p>
  2. Move all files in the current directory into the directory one level up.
  </p>
  <p>
  	cl&gt; move * ..
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  copy, rename
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
