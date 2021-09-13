.. _hdbexamine:

hdbexamine — Examine a help database
====================================

**Package: softools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  hdbexamine -- examine a help database
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  hdbexamine
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>helpdb = "<TT>helpdb</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='helpdb' Line='helpdb = "helpdb"'>
  <DD>The filename of the help database to be examined.  The reserved name "<TT>helpdb</TT>"
  causes the actual filename to be taken from the environment variable of
  the same name.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>If this switch is enabled, <I>hdbexamine</I> will print a detailed description
  of the help database listing the modules in each package, the date the entry
  for the package was last modified, and other information.  A more concise
  summary listing only the packages and the number of help modules in each
  package is printed by default.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <I>hdbexamine</I> task is used to examine the contents of a help
  database.  By default the standard IRAF help database is examined.
  Examining the help database with <I>hdbexamine</I> verifies that it can
  be read by <I>help</I>, and may be useful as a diagnostic in the event
  that an invalid help directory file ("<TT>.hd</TT>") somewhere in the help
  directory tree, causes the database to be compiled incorrectly.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Print a concise summary of the contents and structure of the standard
  help database.
  <P>
  <PRE>
  cl&gt; hdbexamine
  Help database dev$help.db created Feb 14 21:34 by tody
  Database contains 794 modules in 43 packages, file size 105460 bytes
  <P>
  _clpackage   Nov  4  1984 tody     clpackage$_clpackage.hd
  clpackage    May 29 17:44 rooke    clpackage$clpackage.hd
  os           Feb 13 11:06 tody     host$os/doc/os.hd
  root         Nov  4  1984 tody     lib$root.hd
  _math        Apr  1 13:38 tody     math$_math.hd
  curfit       Jan  6 16:23 tody     math$curfit/doc/curfit.hd
  gsurfit      Jan  2 14:46 davis    math$gsurfit/doc/gsurfit.hd
  iminterp     Aug  6 16:31 davis    math$iminterp/doc/iminterp.hd
  bias         Dec 17  8:53 valdes   pkg$imred/bias/bias.hd
  coude        Dec 31 14:38 valdes   pkg$imred/coude/coude.hd
  vtel         Jan 22  8:36 lytle    pkg$imred/vtel/vtel.hd
  plot         Jan 28 14:04 hammond  pkg$plot/plot.hd
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  mkhelpdb, help
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
