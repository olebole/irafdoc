rgbdither — Create an 8-bit RGB dithered image
==============================================

**Package: color**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>rgbdither (Oct92)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>color</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>rgbdither (Oct92)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>rgbdither</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  rgbdither -- make an RGB composite image using 8-bit pixel dithering
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  rgbdither red green blue rgb
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_red">red, green, blue</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='red' Line='red, green, blue'>
  <DD>Input image names for the red, green, and blue components.  The images
  must all be two dimensional and of the same size.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_rgb">rgb</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rgb' Line='rgb'>
  <DD>Output image name for the RGB dithered composite image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_rz1">rz1, rz2, gz1, gz2, bz1, bz2</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rz1' Line='rz1, rz2, gz1, gz2, bz1, bz2'>
  <DD>Range of values in the input images to be mapped to the minimum and maximum
  intensity in each color.  Image pixel values outside the range are mapped
  to the nearest endpoint.  The values correspond to the input image
  intensities even when using logarithmic mapping.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_blkavg">blkavg = 3</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='blkavg' Line='blkavg = 3'>
  <DD>Block average factor for the input images.  The input images may first be
  block averaged before creating the output dithered composite image.  Note
  that the output image will be have dimensions three times larger than the
  block averaged input images so a block average factor of three will produce
  an image which is nearly the same size as the original input images.  A
  factor of 1 will use the pixel values without any averaging.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_logmap">logmap = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logmap' Line='logmap = no'>
  <DD>Use logarithmic intensity mapping?  The logarithm of the input pixel
  values, in the range given by the z1 and z2 parameters, is taken before
  dividing the range into the 85 display levels.  Logarithmic mapping allows
  a greater dynamic range.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_pattern">pattern = "<TT>rgbgbrbrg</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pattern' Line='pattern = "rgbgbrbrg"'>
  <DD>Dither pattern given as a list of characters specifying a 3x3 array
  with the column element incrementing fastest.  A character of r is
  the red image, a character of g is the green image, and a character of
  b is the blue image.  Note that each image should occur three times.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <B>Rgbdither</B> takes three input IRAF images and produces a special
  composite IRAF image which may be displayed as an RGB color image using a
  special color map.  The input images are first block averaged by the
  <I>blkavg</I> factor, pixel values outside the specified ranges are mapped
  to the nearest endpoint, converted to logarithmic intensities if desired,
  and the range mapped to 85 integer levels.  The red image is mapped to the
  values 0 to 84, the green image to the values 85 to 169, and the blue image
  to the values 170 to 254.  The corresponding pixels from the three images
  are then replicated in the output image to form a specified 3x3 dither
  pattern such as the default of
  <P>
  <PRE>
  		brg
  		gbr
  		rgb
  </PRE>
  <P>
  where r is the red image pixel, g is the green image pixel, and b is the
  blue image pixel.  This produces a composite image which is three times
  larger in each dimension than the block averaged input images.
  <P>
  When the dithered 8-bit composite image is displayed using a color map that
  shows values 0-84 as shades of red, 85-169 as shades of green, and 170-254
  as shades of blue the eye (or camera) will blend the individual pixels into
  a RGB color image.  See <B>rgbdisplay</B> and <B>color</B> for a description of
  how to display the composite image.  A better technique may be to use
  <B>rgbto8</B>.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  Three 2048x2048 images of the Trifid nebula are obtained in the B, V,
  and R bandpasses.  These images are properly registered.  Examination of
  the histograms leads to selecting the display ranges 1-500 in each band.
  The large scale colors of the extended emission is of interest and so a
  block averaging factor 6 will yield a final composite image of size
  1023x1023 to be displayed.
  <P>
  <PRE>
  	cl&gt; rgbdither trifidr trifidv trifidb trifidrgb \<BR>
  	&gt;&gt;&gt; rz1=1 rz2=500 gz1=1 gz2=500 bz1=1 bz2=500 blk=6
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_time_requirements">TIME REQUIREMENTS</A></H2>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  Example 1 takes 2:20 minutes (33 seconds CPU) on a SparcStation 2.
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  rgbdisplay, rgbto8, rgbsun, color.package
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>