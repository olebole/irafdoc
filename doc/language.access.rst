.. _access:

access: Test if a file exists
=============================

**Package: language**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  access -- test whether a file exists
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  bool = access (filename)
  bool = imaccess (imagename)
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>filename</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='filename' Line='filename' -->
  <dd>The name of the file whose existence is to be tested.
  </dd>
  </dl>
  <dl>
  <dt><b>imagename</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='imagename' Line='imagename' -->
  <dd>The name of the image whose existence is to be tested.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  <i>Access</i> is a boolean intrinsic function returning true (<tt>"yes"</tt>) if the
  named file exists.  <i>Access</i> can only be called as a function in an
  expression, not as a task.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Type a file if it exists.
  </p>
  <pre>
      if (access ("lib$motd"))
  	type ("lib$motd")
      else
  	error (11, "File not found")
  </pre>
  <p>
  2. Tell if a file and an image exists.
  </p>
  <pre>
  	cl&gt; = access ("lib$motd")
  	cl&gt; = imaccess ("dev$pix")
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  An optional second argument should be added to test whether the named file
  can be accessed for reading or writing.
  </p>
  
  <!-- EndSection:    'BUGS' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS'  -->
  
