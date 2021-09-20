.. _imcopy:

imcopy: Copy an image
=====================

**Package: imutil**

.. raw:: html

  <h3>Usage	</h3>
  <!-- BeginSection: 'USAGE	' -->
  <p>
  imcopy input output
  </p>
  <!-- EndSection:   'USAGE	' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input' -->
  <dd>Images to be copied.
  </dd>
  </dl>
  <dl>
  <dt><b>output</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='output' Line='output' -->
  <dd>Output images or directory.
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes' -->
  <dd>Print each operation as it takes place?
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  Each of the input images, which may be given as a general image template
  including sections, is copied to the corresponding output image list,
  which may also be given as an image template, or the output directory.
  If the output is a list of images then the number of input images must be
  equal to the number of output images and the input and output images are paired
  in order.  If the output image name exists and contains a section then the
  input image (provided it is the same size as the section) will be copied
  into that section of the input image.  If the output image name does not
  have a section specification and if it is the same as the input image name
  then the input image is copied to a temporary file which replaces the input
  image when the copy is successfully concluded.  Note that these are the only
  cases where clobber checking is bypassed; that is, if an output image name
  is not equal to the input image name or a subsection of an existing image
  and the file already exists then a clobber error will occur if
  clobber checking is in effect.
  </p>
  <p>
  The verbose options prints for each copy lines of the form:
  </p>
  <pre>
  
  input image -&gt; output image
  </pre>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. For a simple copy of an image:
  </p>
  <p>
  	cl&gt; imcopy image imagecopy
  </p>
  <p>
  2. To copy a portion of an image:
  </p>
  <p>
  	cl&gt; imcopy image[10:20,*] subimage
  </p>
  <p>
  3. To copy several images:
  </p>
  <p>
  	cl&gt; imcopy image1,image2,frame10 a,b,c
  </p>
  <p>
  4. To trim an image:
  </p>
  <p>
  	cl&gt; imcopy image[10:20,*] image
  </p>
  <p>
  In the above example the specified section of the input image replaces the
  original input image.  To trim several images using an image template:
  </p>
  <p>
  	cl&gt; imcopy frame*[1:512,1:512] frame*
  </p>
  <p>
  In this example all images beginning with <span style="font-family: monospace;">"frame"</span> are trimmed to 512 x 512.
  </p>
  <p>
  5. To copy a set of images to a new directory:
  </p>
  <pre>
  	cl&gt; imcopy image* directory
  			or
  	cl&gt; imcopy image* directory$
  			or
  	cl&gt; imcopy image* osdirectory
  </pre>
  <p>
  where <span style="font-family: monospace;">"osdirectory"</span> is an operating system directory name (i.e. /user/me
  in UNIX).
  </p>
  <p>
  6. To copy a section of an image in an already existing image of
     sufficient size to contain the input section.
  </p>
  <pre>
  	cl&gt; imcopy image[1:512,1:512] outimage[257:768,257:768]
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  The distinction between copying to a section of an existing image
  and overwriting a input image is rather inobvious.
  </p>
  
  <!-- EndSection:    'BUGS' -->
  
  <!-- Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS'  -->
  
