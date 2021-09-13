.. _movefiles:

movefiles — Move files to a directory
=====================================

**Package: system**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  movefiles -- move files to a directory
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  movefiles files directory
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>files</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='files' Line='files'>
  <DD>A template specifying the file or files to be moved.
  </DD>
  </DL>
  <DL>
  <DT><B>directory</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='directory' Line='directory'>
  <DD>The directory to which the files are to be moved.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>If set to "<TT>yes</TT>", tell user as each file is moved.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This routine moves the specified files to the named directory.
  If a subdirectory and a logical directory both exist with the same
  name as the destination directory, the subdirectory is used.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Move all files whose names start with `im' and end with `ab' to
  the directory `dir'.  Since "<TT>verbose</TT>" defaults to "<TT>no</TT>", do the work silently.
  <P>
  	cl&gt; movefiles im*ab dir
  <P>
  2. Move all files in the current directory into the directory one level up.
  <P>
  	cl&gt; move * ..
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  copy, rename
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
