.. _normalize:

normalize — Normalize images
============================

**Package: generic**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  normalize -- Normalize images
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage	</H3>
  <! BeginSection: 'USAGE	'>
  <UL>
  normalize images
  </UL>
  <! EndSection:   'USAGE	'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>images</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>Images to be normalized.
  </DD>
  </DL>
  <DL>
  <DT><B>norm = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='norm' Line='norm = INDEF'>
  <DD>Normalization factor to be used if not INDEF.  If INDEF the normalization
  factor is determined by sampling the images.
  </DD>
  </DL>
  <DL>
  <DT><B>sample_section = "<TT>[]</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sample_section' Line='sample_section = "[]"'>
  <DD>Section of the image to be sampled in determining the image mean.
  </DD>
  </DL>
  <DL>
  <DT><B>lower = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lower' Line='lower = INDEF'>
  <DD>Lower limit of pixel values for calculating the normalization.
  INDEF corresponds to the minimum possible pixel value.
  </DD>
  </DL>
  <DL>
  <DT><B>upper = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='upper' Line='upper = INDEF'>
  <DD>Upper limit of pixel values for calculating the normalization.
  INDEF corresponds to the maximum possible pixel value.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Each of the images is normalized.  The normalization is specified by the
  parameter <I>norm</I>.  If the value of <I>norm</I> is INDEF then a normalization
  is determined by sampling the image.  The normalization is then the mean
  of the pixels in the sample section with values in the range <I>lower</I>
  to <I>upper</I>.  The default sample section selects all pixels in the image.
  The normalized images are of datatype "<TT>real</TT>" and replace the original images.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  To normalize a set of two dimensional images excluding deviant pixels below
  1000 and above 5000 and subsampling every fifth pixel in each dimension:
  <P>
  	cl&gt; normalize frame* sample=[*:5,*:5] low=1000 up=5000
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imstatistics, normflat
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
