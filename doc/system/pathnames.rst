.. _pathnames:

pathnames: Expand a file template into a list of OS pathnames
=============================================================

**Package: system**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  pathnames [template]
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>template</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='template' Line='template' -->
  <dd>A filename template specifying the set of files for which pathnames
  are desired.  If omitted, the pathname of the current working or default
  directory is printed.  The list of file names can come from the standard input.
  </dd>
  </dl>
  <dl>
  <dt><b>sort = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='sort' Line='sort = yes' -->
  <dd>Sort the output in ASCII collating sequence.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  <i>Pathnames</i> converts a list of IRAF virtual file names into their host
  system equivalents.  When called with no arguments, the function of
  <i>pathnames</i> is to print the current default directory.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Print the pathname of the current default directory (sample output for
  a VMS host system).
  </p>
  <pre>
  	cl&gt; path
  	draco!DRB1:[IRAF.SYS.FIO]
  </pre>
  <p>
  2. Translate the file <span style="font-family: monospace;">"vfiles"</span>, containing a list of virtual filenames, into
  the equivalent list of host system filenames, e.g., for use as input to a
  foreign task.
  </p>
  <p>
  	cl&gt; path @vfiles &gt; hfiles
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  directory, files
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
