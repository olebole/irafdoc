.. _mkapropos:

mkapropos: Make the apropos database (from STSDAS).
===================================================

**Package: softools**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  mkapropos pkglist aproposdb
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The 'mkapropos' task descends a tree of help directory ('.hd') files
  and compiles a text database from the information found there, specifically
  from the package menu files ('.men').
  </p>
  <p>
  The apropos database is used to speed global searches when information
  is requested for a particular subject.
  Each line of the apropos database contains the name of the task or package,
  along with a brief description (from the '.men' files) and its package.
  </p>
  <p>
  By default, 'mkapropos' parameters are set to recompile the standard
  IRAF and NOAO apropos database (placed in 'lib$apropos.db'), although any other
  similar database may be recompiled, for example, for other add-on packages such
  as 'stsdas', 'xray' and 'ctio'. 
  </p>
  <p>
  Additionally, you can build apropos databases for your own packages.
  </p>
  <p>
  This is the mkapropos from stsdas.toolbox.tools, copied into Ureka/AstroConda
  IRAF's softools to facilitate building IRAF packages before stsdas is installed.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>pkglist = <span style="font-family: monospace;">"iraf, noao"</span> [string]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='pkglist' Line='pkglist = "iraf, noao" [string]' -->
  <dd>The names of the packages to examine when building the apropos database.
  By default, the
  IRAF, NOAO, and STSDAS packages are used.   Any IRAF external package may be 
  included.
  </dd>
  </dl>
  <dl>
  <dt><b>helpdir = <span style="font-family: monospace;">"lib/root.hd"</span> [string]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='helpdir' Line='helpdir = "lib/root.hd" [string]' -->
  <dd>The filename of the root help directory file ('.hd' file)
  defining the help tree to be updated. This string is appended to each of the
  packages listed in the 'pkglist' parameter above. 
  </dd>
  </dl>
  <dl>
  <dt><b>aproposdb = <span style="font-family: monospace;">"lib$apropos.db"</span> [string]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='aproposdb' Line='aproposdb = "lib$apropos.db" [string]' -->
  <dd>The filename of the apropos database to be written. 
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = no [boolean]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no [boolean]' -->
  <dd>Print a detailed description of the help database as it is compiled?
  A more concise summary listing only the packages and the number
  of help modules in each package is printed by default.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Update the stsdas package apropos database.
  </p>
  <pre>
    cl&gt; mkapropos stsdas lib/root.hd stsdas$lib/apropos.db
  </pre>
  <p>
  2. Update a user apropos database.
  </p>
  <pre>
    cl&gt; mkap pkglist=home helpdir=myroot.hd aproposdb=my.db
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  apropos, mkhelpdb
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'SEE ALSO'  -->
  
