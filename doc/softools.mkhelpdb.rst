.. _mkhelpdb:

mkhelpdb: Make (compile) a help database
========================================

**Package: softools**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  mkhelpdb -- update the help database
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  mkhelpdb helpdir helpdb
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>helpdir = <tt>"lib$root.hd"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='helpdir' Line='helpdir = "lib$root.hd"' -->
  <dd>The filename of the root help directory file (<tt>".hd"</tt> file) defining the
  help tree to be updated.  By convention this is <i>root.hd</i> in some
  directory.
  </dd>
  </dl>
  <dl>
  <dt><b>helpdb = <tt>"lib$helpdb.mip"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='helpdb' Line='helpdb = "lib$helpdb.mip"' -->
  <dd>The filename of the help database file to be written.  By convention this
  is <i>helpdb.mip</i> in some directory (the <tt>".mip"</tt> signifies that the file
  format is machine independent).
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no' -->
  <dd>If this switch is enabled, <i>mkhelpdb</i> will print a detailed description
  of the help database as it is being compiled.  A more concise summary listing
  only the packages and the number of help modules in each package is printed
  by default.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The <i>mkhelpdb</i> task descends a tree of help directory (<tt>".hd"</tt>) files and
  compiles a binary help database from the information therein.  The help
  database is used to speed global searches when help is requested for a
  module, the <tt>".hlp"</tt> file for which might be anywhere in the system.
  The help database defines the packages and modules in the help database,
  and stores the filenames of the associated help files.  No actual help text
  is stored in the help database, only sufficient index information to find
  the help files when the <i>help</i> task is run.  The help directory files
  are text files which define the packages and modules in the help database.
  The format of these files is self explanatory hence is documented by example
  only.
  </p>
  <p>
  By default, <i>mkhelpdb</i> recompiles the standard IRAF help database,
  although any other similar database may be recompiled by changing the values
  of the parameters <i>helpdir</i> and <i>helpdb</i>.  The standard
  IRAF help database is rooted in the file <b>lib$root.hd</b>.
  </p>
  <p>
  The help database must be updated whenever a new help module (e.g., manual
  page) is added, deleted, or renamed.  It is also necessary for sites receiving
  a source only version of IRAF to run <i>mkhelpdb</i> to rebuild the help
  database once the system is up, since the database is a binary file and
  is not included in a source only distribution.  It is not necessary to rerun
  <i>mkhelpdb</i> when an existing manual page is edited, since only index
  information is stored in the database.
  </p>
  <p>
  The <i>help</i> utilities make use of the following types of files.  Examples
  of these files will be found throughout the IRAF directories.
  </p>
  <pre>
  	.hd		help directory file (tree structured)
  	.hlp		manual page
  	.men		package menu (module listing)
  </pre>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Update the standard IRAF help database.
  </p>
  <pre>
  	cl&gt; softools
  	so&gt; mkhelpdb helpdir=lib$root.hd helpdb=lib$helpdb.mip
  </pre>
  <p>
  2. Update the NOAO package help database.
  </p>
  <p>
  	so&gt; mkhelpdb helpdir=noao$lib/root.hd helpdb=noao$lib/helpdb.mip
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  hdbexamine, help
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
