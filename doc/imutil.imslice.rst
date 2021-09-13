.. _imslice:

imslice — Slice images into images of lower dimension
=====================================================

**Package: imutil**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  imslice -- slice an image into images of lower dimension
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  imslice input output slicedim
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The list of input images to be sliced. The input images must have a
  dimensionality greater than one.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>The root name of the output images. For each n-dimensional input
  image m (n-1)-dimensional images will be created, where m is the
  length of the axis to be sliced. The sequence number m will
  be appended to the output image name.
  </DD>
  </DL>
  <DL>
  <DT><B>slice_dimension</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='slice_dimension' Line='slice_dimension'>
  <DD>The dimension to be sliced.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print messages about actions taken.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The n-dimensional images <I>input</I> are sliced into m (n-1)-dimensional
  images <I>output</I>, where m is the length of the axis of the input
  image to be sliced. A sequence number from 1 to m is appended to output
  to create the output image name.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Slice the 3-D image "<TT>datacube</TT>" into a list of 2D images. A list of
  images called plane001, plane002, plane003 ... will be created.
  <P>
  <PRE>
  	im&gt; imslice datacube plane 3
  </PRE>
  <P>
  2. Slice the list of 2-D images "<TT>nite1,nite2,nite3</TT>" into a list of 1-D images.
  A new list of images nite1001, nite1002, ..., nite2001, nite2002, ...,
  nite3001, nite3002 will be created.
  <P>
  <PRE>
  	im&gt; imslice nite1,nite2,nite3 nite1,nite2,nite3 2
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  If the image to be sliced is an image section, the images slices will
  refer to the section not the original image.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imstack, imcopy
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
