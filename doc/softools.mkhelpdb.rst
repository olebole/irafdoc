.. _mkhelpdb:

mkhelpdb — Make (compile) a help database
=========================================

**Package: softools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  mkhelpdb -- update the help database
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  mkhelpdb helpdir helpdb
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>helpdir = "<TT>lib$root.hd</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='helpdir' Line='helpdir = "lib$root.hd"'>
  <DD>The filename of the root help directory file ("<TT>.hd</TT>" file) defining the
  help tree to be updated.  By convention this is <I>root.hd</I> in some
  directory.
  </DD>
  </DL>
  <DL>
  <DT><B>helpdb = "<TT>lib$helpdb.mip</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='helpdb' Line='helpdb = "lib$helpdb.mip"'>
  <DD>The filename of the help database file to be written.  By convention this
  is <I>helpdb.mip</I> in some directory (the "<TT>.mip</TT>" signifies that the file
  format is machine independent).
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>If this switch is enabled, <I>mkhelpdb</I> will print a detailed description
  of the help database as it is being compiled.  A more concise summary listing
  only the packages and the number of help modules in each package is printed
  by default.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <I>mkhelpdb</I> task descends a tree of help directory ("<TT>.hd</TT>") files and
  compiles a binary help database from the information therein.  The help
  database is used to speed global searches when help is requested for a
  module, the "<TT>.hlp</TT>" file for which might be anywhere in the system.
  The help database defines the packages and modules in the help database,
  and stores the filenames of the associated help files.  No actual help text
  is stored in the help database, only sufficient index information to find
  the help files when the <I>help</I> task is run.  The help directory files
  are text files which define the packages and modules in the help database.
  The format of these files is self explanatory hence is documented by example
  only.
  <P>
  By default, <I>mkhelpdb</I> recompiles the standard IRAF help database,
  although any other similar database may be recompiled by changing the values
  of the parameters <I>helpdir</I> and <I>helpdb</I>.  The standard
  IRAF help database is rooted in the file <B>lib$root.hd</B>.
  <P>
  The help database must be updated whenever a new help module (e.g., manual
  page) is added, deleted, or renamed.  It is also necessary for sites receiving
  a source only version of IRAF to run <I>mkhelpdb</I> to rebuild the help
  database once the system is up, since the database is a binary file and
  is not included in a source only distribution.  It is not necessary to rerun
  <I>mkhelpdb</I> when an existing manual page is edited, since only index
  information is stored in the database.
  <P>
  The <I>help</I> utilities make use of the following types of files.  Examples
  of these files will be found throughout the IRAF directories.
  <P>
  <PRE>
  	.hd		help directory file (tree structured)
  	.hlp		manual page
  	.men		package menu (module listing)
  </PRE>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Update the standard IRAF help database.
  <P>
  <PRE>
  	cl&gt; softools
  	so&gt; mkhelpdb helpdir=lib$root.hd helpdb=lib$helpdb.mip
  </PRE>
  <P>
  2. Update the NOAO package help database.
  <P>
  	so&gt; mkhelpdb helpdir=noao$lib/root.hd helpdb=noao$lib/helpdb.mip
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  hdbexamine, help
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
