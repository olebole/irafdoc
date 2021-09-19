.. _imstack:

imstack: Stack images into a single image of higher dimension
=============================================================

**Package: imutil**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  imstack -- stack images into an image of higher dimension
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage	</h3>
  <!-- BeginSection: 'USAGE	' -->
  <p>
  imstack images output
  </p>
  <!-- EndSection:   'USAGE	' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>images</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='images' Line='images' -->
  <dd>List of images to be stacked.
  </dd>
  </dl>
  <dl>
  <dt><b>output</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='output' Line='output' -->
  <dd>Name of output image created.
  </dd>
  </dl>
  <dl>
  <dt><b>title = <tt>"*"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='title' Line='title = "*"' -->
  <dd>Title of output image.  If <tt>"*"</tt> then the title defaults to that of
  the first input image.
  </dd>
  </dl>
  <dl>
  <dt><b>pixtype = <tt>"*"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='pixtype' Line='pixtype = "*"' -->
  <dd>Pixel datatype of output image.  If <tt>"*"</tt> then the pixel datatype defaults to
  that of the first input image.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The input <i>images</i> are stacked to form an <i>output</i> image having one
  higher dimension than the input images, and a length of that dimension equal
  to the number of input images.  The input images must all be of the same
  dimension and size.
  </p>
  <p>
  The output image inherits the world coordinate system (WCS) of the first
  input image. If the dimension of the input image WCS is greater than or
  equal to the dimension of the output image, the input WCS is copied to the
  output image WCS without modification. Otherwise the input image WCS
  dimension is incremented by 1 and copied to the output image WCS, the input
  WCS coordinate transformations for each input image axis are copied to the
  output image WCS without modification, and the new output image axis is
  assigned a WCS type of 'linear' and the identity transformation.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Stack a set of four two dimensional images:
  </p>
  <p>
  	cl&gt; imstack image* image.3d
  </p>
  <p>
  2. To stack a section of images:
  </p>
  <p>
  	cl&gt; imstack image*[1:10,1:10] newimage
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  imslice
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  -->
  
