.. _imtranspose:

imtranspose: Transpose a list of 2-D images
===========================================

**Package: imgeom**

.. raw:: html

  <h3>Usage	</h3>
  <!-- BeginSection: 'USAGE	' -->
  <pre>
  imtranspose input output
  </pre>
  <!-- EndSection:   'USAGE	' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input' -->
  <dd>List of images to be transposed.
  </dd>
  </dl>
  <dl>
  <dt><b>output</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='output' Line='output' -->
  <dd>List of output transposed images. If the output image name is the same as
  the input image name then the output image will replace the input image.
  The number of output images must be the same as the number of input images.
  </dd>
  </dl>
  <dl>
  <dt><b>len_blk = 512</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='len_blk' Line='len_blk = 512' -->
  <dd>The one dimensional length of the transpose blocks.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  Imtranspose transposes the list of images in input by interchanging
  their rows and columns and writing the results to images specified in
  output. The number of input and output images must be the same.
  </p>
  <p>
  The transpose is done in square blocks whose dimensions are equal <i>len_blk</i>.
  </p>
  <p>
  The imtranspose tasks can be used to perform counter-clockwise or
  clockwise ninety degree rotations by flipping the y or x axis respectively
  in the input image section specification.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. To transpose an image:
  </p>
  <p>
  	cl&gt; imtranspose image1 image2
  </p>
  <p>
  2. To transpose an image in place:
  </p>
  <p>
  	cl&gt; imtranspose image1 image1
  </p>
  <p>
  3. To rotate an image 90 degrees counter-clockwise and clockwise:
  </p>
  <p>
  	cl&gt; imtranspose image1[*,-*] image2
  </p>
  <p>
  	cl&gt; imtranspose image1[-*,*] image2
  </p>
  <p>
  3. To transpose a set of 3 images listed 1 per line in the file imlist to
  the new images trans001, trans002, and trans003:
  </p>
  <p>
  	cl&gt; imtranspose @imlist trans001,trans002,trans003
  </p>
  <p>
  4. To transpose a set of images in place:
  </p>
  <p>
  	cl&gt; imtranspose frame* frame*
  </p>
  <p>
  5. To rotate an image 90 degrees counter-clockwise in place:
  </p>
  <p>
  	cl&gt; imtranspose image[*,-*] image
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  It is currently not legal to transpose images with a wcs type of MULTISPEC.
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  -->
  
