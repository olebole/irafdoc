.. _pathnames:

pathnames — Expand a file template into a list of OS pathnames
==============================================================

**Package: system**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  pathnames -- print the host pathnames for a set of files
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  pathnames [template]
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>template</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='template' Line='template'>
  <DD>A filename template specifying the set of files for which pathnames
  are desired.  If omitted, the pathname of the current working or default
  directory is printed.  The list of file names can come from the standard input.
  </DD>
  </DL>
  <DL>
  <DT><B>sort = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sort' Line='sort = yes'>
  <DD>Sort the output in ASCII collating sequence.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>Pathnames</I> converts a list of IRAF virtual file names into their host
  system equivalents.  When called with no arguments, the function of
  <I>pathnames</I> is to print the current default directory.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
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
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  directory, files
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
