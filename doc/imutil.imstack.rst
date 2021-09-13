.. _imstack:

imstack — Stack images into a single image of higher dimension
==============================================================

**Package: imutil**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  imstack -- stack images into an image of higher dimension
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage	</H3>
  <! BeginSection: 'USAGE	'>
  <UL>
  imstack images output
  </UL>
  <! EndSection:   'USAGE	'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>images</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>List of images to be stacked.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>Name of output image created.
  </DD>
  </DL>
  <DL>
  <DT><B>title = "<TT>*</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='title' Line='title = "*"'>
  <DD>Title of output image.  If "<TT>*</TT>" then the title defaults to that of
  the first input image.
  </DD>
  </DL>
  <DL>
  <DT><B>pixtype = "<TT>*</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pixtype' Line='pixtype = "*"'>
  <DD>Pixel datatype of output image.  If "<TT>*</TT>" then the pixel datatype defaults to
  that of the first input image.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  The input <I>images</I> are stacked to form an <I>output</I> image having one
  higher dimension than the input images, and a length of that dimension equal
  to the number of input images.  The input images must all be of the same
  dimension and size.
  <P>
  The output image inherits the world coordinate system (WCS) of the first
  input image. If the dimension of the input image WCS is greater than or
  equal to the dimension of the output image, the input WCS is copied to the
  output image WCS without modification. Otherwise the input image WCS
  dimension is incremented by 1 and copied to the output image WCS, the input
  WCS coordinate transformations for each input image axis are copied to the
  output image WCS without modification, and the new output image axis is
  assigned a WCS type of 'linear' and the identity transformation.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Stack a set of four two dimensional images:
  <P>
  	cl&gt; imstack image* image.3d
  <P>
  2. To stack a section of images:
  <P>
  	cl&gt; imstack image*[1:10,1:10] newimage
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imslice
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
