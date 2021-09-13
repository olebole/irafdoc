.. _imjoin:

imjoin — N-dimensional image join along arbitrary axis
======================================================

**Package: vol**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  imjoin -- join input images into output image along specified axis
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  imjoin input output 
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>Input images or @file
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>Output joined image
  </DD>
  </DL>
  <DL>
  <DT><B>joindim = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='joindim' Line='joindim = 1'>
  <DD>Image dimension along which the input images will be joined.
  </DD>
  </DL>
  <DL>
  <DT><B>outtype = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outtype' Line='outtype = ""'>
  <DD>Output image datatype.  If not specified, defaults to highest precedence
  input image datatype.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  IMJOIN concatenates a set of input images into a single output image,
  in a specified dimension only.  For example, it can join a set of one
  dimensional images into a single, long one dimensional image, or a
  set of one dimensional images into a single two dimensional image.
  IMJOIN may be used to piece together datacubes into larger
  datacubes, either in x, y, or z; likewise with higher dimensional images.
  <P>
  For joining a set of 1 or 2 dimensional images in both x and y at the same
  time, see IMMOSAIC.  For stacking images of any dimension into an image
  of the next higher dimension, see IMSTACK.  Although IMJOIN can also
  stack a set of images into a single higher dimensional image, IMSTACK
  is more efficient for that operation.  In most cases, IMJOIN must keep
  all input images open at the same time, while IMSTACK does not (there may
  be limitations on the number of files that can be kept open at one time).
  Use IMJOIN primarily when joining a set of images along any dimension that
  is not the next higher one from that of the input images.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  <PRE>
  1.  Join a list of one dimensional spectra into a single long image.
  <P>
      cl&gt; imjoin @inlist output 1
  <P>
  2.  Join three datacubes along the z direction.
  <P>
      cl&gt; imjoin c1,c2,c3 fullxcube 3
  <P>
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Timings</H3>
  <! BeginSection: 'TIMINGS'>
  <UL>
  <P>
  Join 10 5000 column type short spectra into one 50000 column image:
  6 seconds on a diskless Sun-3.  
  <P>
  Join 2 512*512 images:  28 seconds on diskless Sun-3.  Join 2 50*50*50
  datacubes in x, y, or z:  15 seconds.
  <P>
  </UL>
  <! EndSection:   'TIMINGS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  <P>
  There may be limitations on the number of input images that can be handled
  in one execution on some systems.
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  immosaic, imstack, imslice
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIMINGS' 'BUGS' 'SEE ALSO'  >
  
