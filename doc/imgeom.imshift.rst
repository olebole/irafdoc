imshift — Shift a list of 1-D or 2-D images
===========================================

**Package: imgeom**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>imshift (Dec98)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>images.imgeom</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>imshift (Dec98)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>imshift</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  imshift -- shift a set of images in x and y
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  imshift input output xshift yshift
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
  <DT><B><A NAME="l_xshift">xshift, yshift</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xshift' Line='xshift, yshift'>
  <DD>Fractional pixel shift in x and y such that xout = xin + xshift and
  yout = yin + yshift.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_shifts_file">shifts_file = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='shifts_file' Line='shifts_file = ""'>
  <DD>The name of the text file containing the shifts for each input image. If no
  file name is supplied each input image is shifted by <I>xshift</I> and
  <I>yshift</I>. Shifts are listed in the text file, 1 set of shifts per image,
  with the x and y shift in columns 1 and 2 respectively. The number of
  shifts in the file must equal the number of input images.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interp_type">interp_type = "<TT>linear</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interp_type' Line='interp_type = "linear"'>
  <DD>The interpolant type use to computed the output shifted image.
  The choices are the following:
  <DL>
  <DT><B><A NAME="l_nearest">nearest</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='nearest' Line='nearest'>
  <DD>nearest neighbor.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_linear">linear</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='linear' Line='linear'>
  <DD>bilinear interpolation in x and y.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_poly3">poly3</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='poly3' Line='poly3'>
  <DD>third order interior polynomial in x and y.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_poly5">poly5</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='poly5' Line='poly5'>
  <DD>fifth order interior polynomial in x and y.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_spline3">spline3</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='spline3' Line='spline3'>
  <DD>bicubic spline.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_sinc">sinc</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='sinc' Line='sinc'>
  <DD>2D sinc interpolation. Users can specify the sinc interpolant width by
  appending a width value to the interpolant string, e.g. sinc51 specifies
  a 51 by 51 pixel wide sinc interpolant. The sinc width input by the
  user will be rounded up to the nearest odd number. The default sinc width
  is 31 by 31.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_drizzle">drizzle</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='drizzle' Line='drizzle'>
  <DD>2D drizzle resampling. Users can specify the drizzle pixel fractions in x and y
  by appending values between 0.0 and 1.0 in square brackets to the
  interpolant string, e.g. drizzle[0.5]. The default value is 1.0. The
  value 0.0 is increased to 0.001. Drizzle resampling with a pixel fraction
  of 1.0 in x and y is identical to bilinear interpolation.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_boundary_type">boundary_type = "<TT>nearest</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='boundary_type' Line='boundary_type = "nearest"'>
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
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  IMSHIFT will shift an image in x and y such that:
  <P>
  <PRE>
      xout = xin + xshift
      yout = yin + yshift
  <P>
  </PRE>
  <P>
  The output image gray levels are determined by interpolating in the input
  image at the positions of the shifted output pixels.
  IMSHIFT uses the routines in the 2-D interpolator package.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Shift an image by (+3.2, -4.5) using a biquintic interior polynomial
     interpolant and boundary extension.
  <P>
     cl&gt; imshift vys70 vys70shift 3.2 -4.5 inter=poly5 bound=neare
  <P>
  2. Shift an image by (-6., 1.2) using bilinear interpolation and
     boundary extension.
  <P>
     cl&gt; imshift ugc1040 ugc1040shift -6.0 1.2 bound=neare
  <P>
  3. Shift a set of images using shifts listed in the textfile "<TT>shifts</TT>".
  <P>
     cl&gt; page shifts
  <P>
         3.5  4.86
         -2.  8.9
         10.1 7.8
  <P>
     cl&gt; imshift im1,im2,im3 im1.s,im2.s,im3.s shifts_file=shifts
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_timings">TIMINGS</A></H2>
  <! BeginSection: 'TIMINGS'>
  <UL>
  The time required to shift a 512 by 512 real image by fractional pixel
  amounts in x and y is approximately 10, 20, 70, 120, and 120 cpu seconds for the
  nearest neighbor, bilinear, bicubic, biquintic and bicubic spline
  interpolants respectively (Vax 11/750 fpa).
  <P>
  </UL>
  <! EndSection:   'TIMINGS'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  shiftlines, magnify, rotate, geomap, geotran, imlintran
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIMINGS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>