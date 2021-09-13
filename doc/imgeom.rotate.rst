.. _rotate:

rotate — Rotate and shift a list of 2-D images
==============================================

**Package: imgeom**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  rotate -- rotate and shift a list of images
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  rotate input output rotation
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of images to be rotated.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>List of output images.
  </DD>
  </DL>
  <DL>
  <DT><B>rotation</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rotation' Line='rotation'>
  <DD>Angle of rotation of the image in degrees. Positive angles will rotate
  the image counter-clockwise from the x axis.
  </DD>
  </DL>
  <DL>
  <DT><B>xin = INDEF, yin = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xin' Line='xin = INDEF, yin = INDEF'>
  <DD>The origin of the rotation in pixels. Xin and yin default to the center of
  the input image.
  </DD>
  </DL>
  <DL>
  <DT><B>xout = INDEF, yout = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xout' Line='xout = INDEF, yout = INDEF'>
  <DD>The origin of the output image. Xout and yout default to the center of the
  output image.
  </DD>
  </DL>
  <DL>
  <DT><B>ncols = INDEF, nlines = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ncols' Line='ncols = INDEF, nlines = INDEF'>
  <DD>The number of columns and rows in the output image. The default is to
  keep the dimensions the same as the input image. If ncols and nrows is
  less then or equal to zero the program will compute the number of columns
  and rows needed to include the whole image, excluding the effects of
  any origin shifts.
  </DD>
  </DL>
  <DL>
  <DT><B>interpolant = "<TT>linear</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interpolant' Line='interpolant = "linear"'>
  <DD>The interpolant. The options are the following:
  <DL>
  <DT><B>nearest</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='nearest' Line='nearest'>
  <DD>Nearest neighbor.
  </DD>
  </DL>
  <DL>
  <DT><B>linear</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='linear' Line='linear'>
  <DD>Bilinear interpolation in x and y.
  </DD>
  </DL>
  <DL>
  <DT><B>poly3</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='poly3' Line='poly3'>
  <DD>Third order polynomial in x and y.
  </DD>
  </DL>
  <DL>
  <DT><B>poly5</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='poly5' Line='poly5'>
  <DD>Fifth order polynomial in x and y.
  </DD>
  </DL>
  <DL>
  <DT><B>spline3</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='spline3' Line='spline3'>
  <DD>Bicubic spline.
  </DD>
  </DL>
  <DL>
  <DT><B>sinc</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='sinc' Line='sinc'>
  <DD>2D sinc interpolation. Users can specify the sinc interpolant width by
  appending a width value to the interpolant string, e.g. sinc51 specifies
  a 51 by 51 pixel wide sinc interpolant. The sinc width will be rounded up to
  the nearest odd number.  The default sinc width is 31 by 31.
  </DD>
  </DL>
  <DL>
  <DT><B>lsinc</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='lsinc' Line='lsinc'>
  <DD>Look-up table sinc interpolation. Users can specify the look-up table sinc
  interpolant width by appending a width value to the interpolant string, e.g.
  lsinc51 specifies a 51 by 51 pixel wide look-up table sinc interpolant. The user
  supplied sinc width will be rounded up to the nearest odd number. The default
  sinc width is 31 by 31 pixels. Users can specify the resolution of the lookup
  table sinc by appending the look-up table size in square brackets to the
  interpolant string, e.g. lsinc51[20] specifies a 20 by 20 element sinc
  look-up table interpolant with a pixel resolution of 0.05 pixels in x and y.
  The default look-up table size and resolution are 20 by 20 and 0.05 pixels
  in x and y respectively.
  </DD>
  </DL>
  <DL>
  <DT><B>drizzle</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='drizzle' Line='drizzle'>
  <DD>2D drizzle resampling. Users can specify the drizzle pixel fraction in x and y
  by appending a value between 0.0 and 1.0 in square brackets to the
  interpolant string, e.g. drizzle[0.5]. The default value is 1.0.
  The value 0.0 is increased internally to 0.001. Drizzle resampling
  with a pixel fraction of 1.0 in x and y is equivalent to fractional pixel
  rotated block summing (fluxconserve = yes) or averaging (flux_conserve = no)  if
  xmag and ymag are &gt; 1.0.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>boundary = "<TT>nearest</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='boundary' Line='boundary = "nearest"'>
  <DD>The choices are:
  <DL>
  <DT><B>nearest</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='nearest' Line='nearest'>
  <DD>Use the value of the nearest boundary pixel.
  </DD>
  </DL>
  <DL>
  <DT><B>constant</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='constant' Line='constant'>
  <DD>Use a constant value.
  </DD>
  </DL>
  <DL>
  <DT><B>reflect</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='reflect' Line='reflect'>
  <DD>Generate a value by reflecting around the boundary.
  </DD>
  </DL>
  <DL>
  <DT><B>wrap</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='wrap' Line='wrap'>
  <DD>Generate a value by wrapping around to the opposite side of the image.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>constant = 0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='constant' Line='constant = 0.'>
  <DD>The value of the constant for constant boundary extension.
  </DD>
  </DL>
  <DL>
  <DT><B>nxblock = 512, nyblock = 512</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nxblock' Line='nxblock = 512, nyblock = 512'>
  <DD>If the dimensions of the output image are less than nxblock and nyblock
  then the entire image is rotated at once. Otherwise nxblock by nyblock
  segments of the image are rotated.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  ROTATE rotates the list of images in input by rotation degrees and writes
  the output to the images specified by output. The origins of the input and
  output images may be specified by setting xin, yin, xout and yout. The
  transformation is described below.
  <P>
  <PRE>
      xt = (x - xin) * cos (rotation) - (y - yin) * sin (rotation) + xout
      yt = (x - xin) * sin (rotation) + (y - yin) * cos (rotation) + yout
  <P>
  </PRE>
  <P>
  The output image gray levels are determined by interpolating in the input
  image at the positions of the transformed output pixels. ROTATE uses the
  routines in the 2-D interpolation package.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  <PRE>
  1. Rotate an image 45 degrees around its center.
  <P>
     cl&gt; rotate m51 m51r45 45.0
  <P>
  2. Rotate an image by 45 degrees around (100., 100.) and
     shift the origin to (150., 150.0) using bicubic interpolation.
  <P>
     cl&gt; rotate m92 m92r45 45.0 xin=100. yin=100. xout=150. yout=150.\<BR>
     &gt;&gt;&gt; interp=poly3
  <P>
  3. Rotate an image 90 degrees counter-clockwise and clockwise around its
     center. Note the use of imtranspose and image section notation.
  <P>
     cl&gt; imtranspose m92[*,-*] m92d90
  <P>
     cl&gt; imtranspose m92[-*,*] m92d270
  <P>
  4. Rotate an image 180 degrees counter-clockwise. Note the use of imcopy
     and image section notation.
  <P>
     cl&gt; imcopy m92[-*,-*] m92d180
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Timings</H3>
  <! BeginSection: 'TIMINGS'>
  <UL>
  It requires approximately 70 and 290 cpu seconds to rotate a 512 by 512
  real image using bilinear and biquintic interpolation respectively
  (Vax 11/750 fpa).
  </UL>
  <! EndSection:   'TIMINGS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  The interpolation operation is done in real arithmetic. However the output
  type of the pixels is set equal to the input type. This can lead to truncation
  problems for integer images.
  <P>
  Simple 90, 180, 270 etc degree rotations are best performed using the
  imtranspose task and/or image section notation.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imtranspose, imshift, magnify, lintran, geotran, geomap
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIMINGS' 'BUGS' 'SEE ALSO'  >
  
