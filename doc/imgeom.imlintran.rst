imlintran — Linearly transform a list of 2-D images
===================================================

**Package: imgeom**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>imlintran (Dec98)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>images.imgeom</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>imlintran (Dec98)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>imlintran</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  imlintran -- shift, scale, rotate a list of images
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  imlintran input output xrotation yrotation xmag ymag
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of images to be transformed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>List of output images.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xrotation">xrotation, yrotation</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xrotation' Line='xrotation, yrotation'>
  <DD>Angle of rotation of points on the image axes in degrees.
  Positive angles rotate in a counter-clockwise sense around the x axis.
  For a normal coordinate axes rotation xrotation and yrotation should
  be the same. A simple y axis flip can be introduced by make yrotation
  equal to xrotation plus 180 degrees. An axis skew can be introduced by
  making the angle between xrotation and yrotation other than a
  multiple of 90 degrees.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xmag">xmag, ymag</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xmag' Line='xmag, ymag'>
  <DD>The number of input pixels per output pixel in x and y. The magnifications
  must always be positive numbers. Numbers less than 1 magnify the image;
  numbers greater than one reduce the image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xin">xin = INDEF, yin = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xin' Line='xin = INDEF, yin = INDEF'>
  <DD>The origin of the input picture in pixels. Xin and yin default to the center of
  the input image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xout">xout = INDEF, yout = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xout' Line='xout = INDEF, yout = INDEF'>
  <DD>The origin of the output image. Xout and yout default to the center of the
  output image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ncols">ncols = INDEF, nlines = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ncols' Line='ncols = INDEF, nlines = INDEF'>
  <DD>The number of columns and rows in the output image. The default is to
  keep the dimensions the same as the input image. If ncols and nrows are
  less than or equal to zero then the task computes the number of rows and
  columns required to include the whole input image, excluding the effects
  of any origin shift.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interpolant">interpolant = "<TT>linear</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interpolant' Line='interpolant = "linear"'>
  <DD>The choices are the following.
  <DL>
  <DT><B><A NAME="l_nearest">nearest</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='nearest' Line='nearest'>
  <DD>Nearest neighbor.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_linear">linear</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='linear' Line='linear'>
  <DD>Bilinear interpolation in x and y.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_poly3">poly3</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='poly3' Line='poly3'>
  <DD>Third order interior polynomial in x and y.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_poly5">poly5</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='poly5' Line='poly5'>
  <DD>Fifth order interior polynomial in x and y.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_spline3">spline3</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='spline3' Line='spline3'>
  <DD>Bicubic spline.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_sinc">sinc</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='sinc' Line='sinc'>
  <DD>2D sinc interpolation. Users can specify the sinc interpolant width by
  appending a width value to the interpolant string, e.g. sinc51 specifies
  a 51 by 51 pixel wide sinc interpolant. The sinc width will be rounded up to
  the nearest odd number.  The default sinc width is 31 by 31.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_lsinc">lsinc</A></B></DT>
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
  <DT><B><A NAME="l_drizzle">drizzle</A></B></DT>
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
  <DT><B><A NAME="l_boundary">boundary = "<TT>nearest</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='boundary' Line='boundary = "nearest"'>
  <DD>The choices are:
  <DL>
  <DT><B><A NAME="l_nearest">nearest</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='nearest' Line='nearest'>
  <DD>Use the value of the nearest boundary pixel.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_constant">constant</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='constant' Line='constant'>
  <DD>Use a constant value.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_reflect">reflect</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='reflect' Line='reflect'>
  <DD>Generate value by reflecting about the boundary.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_wrap">wrap</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='wrap' Line='wrap'>
  <DD>Generate a value by wrapping around to the opposite side of the image.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_constant">constant = 0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='constant' Line='constant = 0.'>
  <DD>The value of the constant for boundary extension.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fluxconserve">fluxconserve = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fluxconserve' Line='fluxconserve = yes'>
  <DD>Preserve the total image flux?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nxblock">nxblock = 512, nyblock = 512</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nxblock' Line='nxblock = 512, nyblock = 512'>
  <DD>If the size of the output image is less than nxblock by nyblock then
  the entire image is transformed at once. Otherwise the output image
  is computed in blocks of nxblock by nxblock pixels.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  IMLINTRAN linearly transforms a the list of images in input using rotation
  angles and magnification factors supplied by the user and writes the output
  images into output. The coordinate transformation from input to output
  image is described below.
  <P>
  <PRE>
      1. subtract the origin
  <P>
      xt = x(input) - xin
      yt = y(input) - yin
  <P>
      2. scale the image
  <P>
      xt = xt / xmag
      yt = xt / xmag
  <P>
      3. rotate the image
  <P>
      xt = xt * cos (xrotation) - yt * sin (yrotation)
      yt = xt * sin (yrotation) + yt * cos (yrotation)
  <P>
      4. new orgin
  <P>
      x(output) = xt + xout
      y(output) = yt + yout
  <P>
  </PRE>
  <P>
  The output image gray levels are determined by interpolating in the input
  image at the positions of the transformed output pixels using the inverse
  of the above transformation.
  IMLINTRAN uses the routines in the 2-D interpolation package.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_timings">TIMINGS</A></H2>
  <! BeginSection: 'TIMINGS'>
  <UL>
  It requires approximately 70 and 290 cpu seconds respectively to linearly
  transform a 512 by 512 real image using bilinear and biquintic
  interpolation respectively (Vax 11/750 fpa).
  <P>
  </UL>
  <! EndSection:   'TIMINGS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  <PRE>
  1. Rotate an image 45 degrees around its center and magnify
     the image by a factor of 2. in each direction.
  <P>
     cl&gt; imlintran n4151 n4151rm 45.0 45.0 0.50 0.50
  <P>
  2. Rotate the axes of an image by 45 degrees around 100. and 100.,
     shift the orgin to 150. and 150. and flip the y axis.
  <P>
     cl&gt; imlintran n1068 n1068r 45.0 225.0 1.0 1.0 xin=100. yin=100. \<BR>
     &gt;&gt;&gt; xout=150. yout=150.
  <P>
  3. Rotate an image by 45 degrees and reduce the scale in x and y
     by a factor of 1.5
  <P>
     cl&gt; imlintran n7026 n7026rm 45.0 45.0 1.5 1.5
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imshift, magnify, rotate, lintran, register, geotran, geomap
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'TIMINGS' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>