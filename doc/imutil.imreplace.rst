.. _imreplace:

imreplace — Replace a range of pixel values with a constant
===========================================================

**Package: imutil**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  imreplace -- replace pixels in a window by a constant
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage	</H3>
  <! BeginSection: 'USAGE	'>
  <UL>
  imreplace images value lower upper
  </UL>
  <! EndSection:   'USAGE	'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>images</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>Images in which the pixels are to be replaced.
  </DD>
  </DL>
  <DL>
  <DT><B>value</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='value' Line='value'>
  <DD>Replacement value for pixels in the window.
  </DD>
  </DL>
  <DL>
  <DT><B>imaginary = 0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='imaginary' Line='imaginary = 0.'>
  <DD>Replacement value for pixels in the windoe for the imaginary part of
  complex data.
  </DD>
  </DL>
  <DL>
  <DT><B>lower = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lower' Line='lower = INDEF'>
  <DD>Lower limit of window for replacing pixels.  If INDEF then all pixels
  are above <I>lower</I>.  For complex images this is the magnitude
  of the pixel values.  For integer images the value is rounded up
  to the next higher integer.
  </DD>
  </DL>
  <DL>
  <DT><B>upper = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='upper' Line='upper = INDEF'>
  <DD>Upper limit of window for replacing pixels.  If INDEF then all pixels
  are below <I>upper</I>.  For complex images this is the magnitude
  of the pixel values.  For integer images the value is rounded down
  to the next lower integer.
  </DD>
  </DL>
  <DL>
  <DT><B>radius = 0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='radius' Line='radius = 0.'>
  <DD>Additional replacement radius around pixels which are in the replacement
  window.  If a pixel is within this distance of a pixel within the replacement
  window it is also replaced with the replacement value.  Distances are
  measured between pixel centers which are have integer coordinates.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The pixels in the <I>images</I> between <I>lower</I> and <I>upper</I>,
  and all other pixels with a distance given by <I>radius</I>,
  are replaced by the constant <I>value</I>.  The special value INDEF in
  <I>lower</I> and <I>upper</I> corresponds to the minimum and maximum
  possible pixel values, respectively.
  <P>
  For complex images the replacement value is specified as separate
  real and imaginary and the thresholds are the magnitude.  For
  integer images the thresholds are used as inclusive limits
  so that, for example, the range 5.1-9.9 affets pixels 6-9.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. In a flat field calibration which has been scaled to unit mean replace
  all response values less than or equal to 0.8 by 1.
  <P>
      cl&gt; imreplace calib 1 upper=.8
  <P>
  2. Set all pixels to zero within a section of an image.
  <P>
      cl&gt; imreplace image[1:10,5:100] 0
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>IMREPLACE V2.11.1</B></DT>
  <! Sec='REVISIONS' Level=0 Label='IMREPLACE' Line='IMREPLACE V2.11.1'>
  <DD>A replacement radius to replace additional pixels was added.
  </DD>
  </DL>
  <DL>
  <DT><B>IMREPLACE V2.11</B></DT>
  <! Sec='REVISIONS' Level=0 Label='IMREPLACE' Line='IMREPLACE V2.11'>
  <DD>The lower value is now rounded up for integer images so that a range
  like 5.1-9.9 affects pixels 6-9 instead of 5-9.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imexpr
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
