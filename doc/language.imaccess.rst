.. _imaccess:

imaccess: Test if an image exists
=================================

**Package: language**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  imaccess -- test whether an image exists
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  bool = imaccess (image)
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>image</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='image' Line='image' -->
  <dd>The name of the image whose existence is to be tested.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  <i>Imaccess</i> is a boolean intrinsic function returning true (<span style="font-family: monospace;">"yes"</span>) if the
  named image exists.  The function will return false (<span style="font-family: monospace;">"no"</span>) if the image doesn't
  exist, or if no image extension is supplied and the image name is ambiguous.
  <i>Imaccess</i> can only be called as a function in an expression, not as a task.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Print the header of an image if it exists.
  </p>
  <pre>
      if (imaccess ("dev$wpix"))
  	imheader ("dev$wpix",long+)
      else
  	error (11, "Image not found")
  </pre>
  <p>
  2. Tell if a image exists.
  </p>
  <p>
  	cl&gt; = imaccess (<span style="font-family: monospace;">"dev$pix"</span>)
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  An optional second argument should be added to test whether the named file
  can be accessed for reading or writing.
  </p>
  
  <!-- EndSection:    'BUGS' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS'  -->
  
