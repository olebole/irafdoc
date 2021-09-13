.. _shiftlines:

shiftlines — Shift the lines of a list of N-D images
====================================================

**Package: imgeom**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  shiftlines -- shift lines in a list of images
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage	</H3>
  <! BeginSection: 'USAGE	'>
  <UL>
  <PRE>
  shiftlines input output shift
  </PRE>
  </UL>
  <! EndSection:   'USAGE	'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of images to be shifted.  Image sections are allowed.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>List of output image names.  If the output image name is the same as the input
  image name then the shifted image replaces the input image.
  </DD>
  </DL>
  <DL>
  <DT><B>shift</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='shift' Line='shift'>
  <DD>Shift in pixels.
  </DD>
  </DL>
  <DL>
  <DT><B>interp_type = "<TT>linear</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interp_type' Line='interp_type = "linear"'>
  <DD>The interpolant type use to computed the output shifted image.
  The choices are the following:
  <DL>
  <DT><B>nearest</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='nearest' Line='nearest'>
  <DD>nearest neighbor interpolation.
  </DD>
  </DL>
  <DL>
  <DT><B>linear</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='linear' Line='linear'>
  <DD>linear interpolation in x.
  </DD>
  </DL>
  <DL>
  <DT><B>poly3</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='poly3' Line='poly3'>
  <DD>third order interior polynomial in x.
  </DD>
  </DL>
  <DL>
  <DT><B>poly5</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='poly5' Line='poly5'>
  <DD>fifth order interior polynomial in x.
  </DD>
  </DL>
  <DL>
  <DT><B>spline3</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='spline3' Line='spline3'>
  <DD>cubic spline in x.
  </DD>
  </DL>
  <DL>
  <DT><B>sinc</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='sinc' Line='sinc'>
  <DD>sinc interpolation in x. Users can specify the sinc interpolant width by
  appending a width value to the interpolant string, e.g. sinc51 specifies
  a 51 pixel wide sinc interpolant. The sinc width input by the user will
  be rounded up to the nearest odd number. The default sinc width
  is 31 pixels.
  </DD>
  </DL>
  <DL>
  <DT><B>drizzle</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='drizzle' Line='drizzle'>
  <DD>1D drizzle resampling. Users can specify the drizzle pixel fraction
  by appending a value between 0.0 and 1.0 in square brackets to the
  interpolant string, e.g. drizzle[0.5]. The default value is 1.0. The
  value 0.0 is increased to 0.001. Drizzle resampling with a pixel fraction
  of 1.0 is identical to linear interpolation.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>boundary_type = "<TT>nearest</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='boundary_type' Line='boundary_type = "nearest"'>
  <DD>Boundary condition for shifts outside the input image.
  The minimum match abbreviated choices are:
  <DL>
  <DT><B>"<TT>nearest</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"nearest"'>
  <DD>Use the values of the nearest boundary pixel.
  </DD>
  </DL>
  <DL>
  <DT><B>"<TT>wrap</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"wrap"'>
  <DD>Generate a value by wrapping around to the opposite boundary.
  </DD>
  </DL>
  <DL>
  <DT><B>"<TT>reflect</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"reflect"'>
  <DD>Generate a value by reflecting around the boundary
  </DD>
  </DL>
  <DL>
  <DT><B>"<TT>constant</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"constant"'>
  <DD>Use a user supplied constant pixel value.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>constant = "<TT>0.0</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='constant' Line='constant = "0.0"'>
  <DD>The constant for constant boundary extension.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The list of images in <I>input</I> is shifted by the amount <I>shift</I>
  and copied to the list of output images <I>output</I>.
  The number of output image names must be the same as the number of input
  images.  An output image name may be the same as the corresponding
  input image in which case the shifted image replaces the input image.
  <P>
  The shift is defined by the following relation.
  <P>
      xout = xint + shift
  <P>
  Features in the input image are moved to higher columns when the shift
  is positive and to lower columns when the shift is negative.  For example,
  to shift a feature at column 10 to column 12 the shift is 2.0. The task
  has been optimized for integral pixel shifts.
  <P>
  There are five choices for the one dimensional image interpolation
  which is selected with the parameter <I>interp_type</I>.
  The value of the output pixels corresponding to input pixel positions
  outside the boundaries of the image is determined by the parameter
  <I>boundary_type</I>.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Shift the lines of an image by 0.25 pixels to the right.
  <P>
  	cl&gt; shiftlines imagein imageout 0.25
  <P>
  2. Shift the lines of an image by -.3 pixels using cubic spline interpolation
  and replace the input image by the output image.
  <P>
  	cl&gt; shiftlines image image -.3 interp=spline3
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Timings</H3>
  <! BeginSection: 'TIMINGS'>
  <UL>
  It requires approximately 28 and 59 seconds to shift a 512 square image
  using linear and cubic spline interpolation respectively
  (Vax 11/750 with fpa).
  </UL>
  <! EndSection:   'TIMINGS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imshift, magnify, rotate, imlintran, blkrep, blkav, geotran
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIMINGS' 'BUGS' 'SEE ALSO'  >
  
