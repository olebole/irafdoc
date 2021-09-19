.. _mkdir:

mkdir: Create a new directory
=============================

**Package: system**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  mkdir -- make a new directory
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  mkdir newdir
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>newdir</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='newdir' Line='newdir' -->
  <dd>New directory or subdirectory to be made.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  <i>Mkdir</i> creates a new directory with the given name.
  <i>Newdir</i> may be an IRAF virtual directory name (not a logical name)
  or a host directory name.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Make a subdirectory named <tt>"sub1"</tt>.
  </p>
  <p>
  	cl&gt; mkdir sub1
  </p>
  <p>
  2. Make a subdirectory <tt>"sub2"</tt> below <tt>"sub1"</tt>.  The subdirectory <tt>"sub1"</tt> must
  already exist.
  </p>
  <p>
  	cl&gt; mkdir sub1/sub2
  </p>
  <p>
  3. Make a directory <tt>"blue"</tt> at the same level in the directory hierarchy as
  the current directory (<tt>".."</tt> is a synonym for the previous directory).
  </p>
  <p>
  	cl&gt; mkdir ../blue
  </p>
  
  <!-- EndSection:    'EXAMPLES' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES'  -->
  
