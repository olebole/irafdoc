.. _chpixtype:

chpixtype — Change the pixel type of a list of images
=====================================================

**Package: imutil**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  chpixtype -- change the pixel type of an image
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  chpixtype input output newpixtype
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The list of input images.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>The list of output images. If the output image list is the same as the input
  image list then the original images are overwritten.
  </DD>
  </DL>
  <DL>
  <DT><B>newpixtype</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='newpixtype' Line='newpixtype'>
  <DD>The pixel type of the output image. The options are: "<TT>ushort</TT>", "<TT>short</TT>",
  "<TT>int</TT>", "<TT>long</TT>", "<TT>real</TT>", "<TT>double</TT>" and "<TT>complex</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>oldpixtype = "<TT>all</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='oldpixtype' Line='oldpixtype = "all"'>
  <DD>The pixel type of the input images to be converted. By default all the
  images in the input list are converted to the pixel type specified by
  newpixtype. The remaining options are "<TT>ushort</TT>", "<TT>short</TT>", "<TT>int</TT>", "<TT>long</TT>",
  "<TT>real</TT>", "<TT>double</TT>" and "<TT>complex</TT>" in which case only those images of the
  specified type are converted.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print messages about actions performed.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  The list of images specified by <I>input</I> and pixel type <I>oldpixtype</I> 
  are converted to the pixel type specified by <I>newpixtype</I> and written
  to the list of output images specified by <I>output</I>.
  <P>
  Conversion from one pixel type to another is direct and may involve both
  loss of precision and dynamic range. Mapping of floating point numbers
  to integer numbers is done by truncation. Mapping of complex numbers
  to floating point or integer numbers will preserve the real part of the
  complex number only.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Convert a list of images to type real, overwriting the existing images.
  <P>
          im&gt; chpixtype nite1*.imh nite1*.imh real
  <P>
  2. Convert only those images in imlist1 which are of type short to type real.
     Imlist1 and imlist2 are text files containing the list of input and
     output images respectively. The image names are listed 1 per line.
  <P>
          im&gt; chpixtype @imlist1 @imlist2 real old=short
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
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imarith
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
