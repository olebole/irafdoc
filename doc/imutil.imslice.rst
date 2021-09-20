.. _imslice:

imslice: Slice images into images of lower dimension
====================================================

**Package: imutil**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  imslice -- slice an image into images of lower dimension
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  imslice input output slicedim
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input' -->
  <dd>The list of input images to be sliced. The input images must have a
  dimensionality greater than one.
  </dd>
  </dl>
  <dl>
  <dt><b>output</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='output' Line='output' -->
  <dd>The root name of the output images. For each n-dimensional input
  image m (n-1)-dimensional images will be created, where m is the
  length of the axis to be sliced. The sequence number m will
  be appended to the output image name.
  </dd>
  </dl>
  <dl>
  <dt><b>slice_dimension</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='slice_dimension' Line='slice_dimension' -->
  <dd>The dimension to be sliced.
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes' -->
  <dd>Print messages about actions taken.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The n-dimensional images <i>input</i> are sliced into m (n-1)-dimensional
  images <i>output</i>, where m is the length of the axis of the input
  image to be sliced. A sequence number from 1 to m is appended to output
  to create the output image name.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Slice the 3-D image <span style="font-family: monospace;">"datacube"</span> into a list of 2D images. A list of
  images called plane001, plane002, plane003 ... will be created.
  </p>
  <pre>
  	im&gt; imslice datacube plane 3
  </pre>
  <p>
  2. Slice the list of 2-D images <span style="font-family: monospace;">"nite1,nite2,nite3"</span> into a list of 1-D images.
  A new list of images nite1001, nite1002, ..., nite2001, nite2002, ...,
  nite3001, nite3002 will be created.
  </p>
  <pre>
  	im&gt; imslice nite1,nite2,nite3 nite1,nite2,nite3 2
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Time requirements</h3>
  <!-- BeginSection: 'TIME REQUIREMENTS' -->
  <!-- EndSection:   'TIME REQUIREMENTS' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  If the image to be sliced is an image section, the images slices will
  refer to the section not the original image.
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  imstack, imcopy
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  -->
  
