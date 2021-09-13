.. _rmbin:

rmbin — Find/delete binary files in subdirectories
==================================================

**Package: softools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  rmbin -- find/remove binary files in subdirectories
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  rmbin [-dinrv] [-o extns] [-e extns] dir1 dir2 ... dirN
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>-d</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='-d'>
  <DD>Disable recursive descent into subdirectories.
  </DD>
  </DL>
  <DL>
  <DT><B>-e extns</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='-e extns'>
  <DD>Exclude files with the listed extensions (whitespace delimited).
  </DD>
  </DL>
  <DL>
  <DT><B>-i</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='-i'>
  <DD>Verify before deleting files without extensions.  Files with well known
  extensions like "<TT>.[aoe]</TT>" are deleted without a query.  A heuristic (ZFACSS)
  is used to determine the filetype of files with unknown extensions, and
  it can fail, though in practice it works quite well.
  </DD>
  </DL>
  <DL>
  <DT><B>-n</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='-n'>
  <DD>No execute; do not delete files.  This option may be used to generate
  a list of binary files for some purpose other than deletion.  For example,
  on a UNIX host, the following command will compute the disk space used
  by the binary files in a directory tree:
  <P>
  	% du `rmbin -n .`
  <P>
  The -n option, of course, is also useful for verifying the delete operation
  before destroying the files.
  </DD>
  </DL>
  <DL>
  <DT><B>-o extns</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='-o extns'>
  <DD>Delete only files with the listed extensions (whitespace delimited).
  </DD>
  </DL>
  <DL>
  <DT><B>-r</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='-r'>
  <DD>Reenable recursive descent.  Recursive descent is the default, however
  it may be turned off at one point in the command line, and later reenabled
  with this switch.
  </DD>
  </DL>
  <DL>
  <DT><B>-v</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='-v'>
  <DD>Print names of files as they are deleted.
  </DD>
  </DL>
  <P>
  Note that flags may be inserted between directory name arguments to change
  switches for different directories.
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <I>rmbin</I> task is used to descend a directory tree, deleting (or listing)
  all the binary files therein.  The task may also be used to delete or list
  nonbinary files by explicitly listing their extensions.
  <P>
  <I>Rmbin</I> is used the strip the IRAF system down to the sources, prior to
  a full system rebuild.  After changing to the IRAF root directory, one runs
  <I>rmbin</I> to delete all the binaries in lib, sys, pkg, etc. (but <I>not</I>
  in hlib, else a bootstrap will be necessary too).  <I>Mkpkg</I> is then run
  to recompile the system; this currently takes about 20 hours on our UNIX
  11/750 development system, provided nothing else is running on the system.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Delete all binaries in the pkg and sys directories of IRAF.  The example
  is for a UNIX host, but this works for all other IRAF hosts as well.
  <P>
  <PRE>
  	% cd $iraf
  	% rmbin -v pkg sys
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  rtar, wtar, mkpkg
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
