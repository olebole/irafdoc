.. _imrename:

imrename: Rename one or more images
===================================

**Package: imutil**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  imrename -- rename one or more images
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  imrename oldnames newnames
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>oldnames</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='oldnames' Line='oldnames' -->
  <dd>An image template specifying the names of the images to be renamed.
  </dd>
  </dl>
  <dl>
  <dt><b>newnames</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='newnames' Line='newnames' -->
  <dd>Either an image template specifying the new names for the images,
  or the name of the directory to which the images are to be renamed (moved).
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no' -->
  <dd>If verbose output is enabled a message will be printed on the standard output
  recording each rename operation.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The <b>imrename</b> task renames one or more images.  The ordinary <i>rename</i>
  task cannot be used to rename images since an image may consist of more than
  one file.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Rename the image <span style="font-family: monospace;">"pix"</span> to <span style="font-family: monospace;">"wfpc.1"</span>.
  </p>
  <p>
  	cl&gt; imrename pix wfpc.1
  </p>
  <p>
  2. Rename all the <span style="font-family: monospace;">"nite1*"</span> images as <span style="font-family: monospace;">"nite1_c"</span>.
  </p>
  <p>
  	cl&gt; imrename nite1.*.imh nite1%%_c%.*.imh
  </p>
  <p>
  3. Move the images in logical directory <span style="font-family: monospace;">"dd"</span> to the current directory.
  </p>
  <p>
  	cl&gt; imrename dd$*.imh .
  </p>
  <p>
  4. Move the pixel files associated with the images in the current directory
  to a subdirectory <span style="font-family: monospace;">"pix"</span> of the current directory.
  </p>
  <pre>
  	cl&gt; reset imdir = HDR$pix/
  	cl&gt; imrename *.imh .
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  imcopy, imdelete, imheader
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
