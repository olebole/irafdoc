rgbto8 — Create an 8-bit RGB image with special color map
=========================================================

**Package: color**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>rgbto8 (Oct92)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>color</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>rgbto8 (Oct92)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>rgbto8</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  rgbto8 -- make an RGB 8-bit image and associated color map
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  rgbto8 red green blue rgb
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
  <DD>Output image name for the RGB 8-bit image.  A color map with the same
  image name but the extension "<TT>.sao</TT>" or "<TT>.imt</TT>" will also be created.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_maptype">maptype = "<TT>saoimage</TT>" (saoimage|imtool|ximtool)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maptype' Line='maptype = "saoimage" (saoimage|imtool|ximtool)'>
  <DD>This parameter selects the type of color map file to be produced.  The
  choices are "<TT>saoimage</TT>" to produce a map for SAOimage, "<TT>imtool</TT>" to produce a
  map for IMTOOL, and "<TT>ximtool</TT>" to produce a map for XIMTOOL.  The filenames
  are derived from the output image name with the extension "<TT>.sao</TT>", "<TT>.imt</TT>",
  or "<TT>.xim</TT>".
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
  <DT><B><A NAME="l_logmap">logmap = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logmap' Line='logmap = no'>
  <DD>Use logarithmic intensity mapping?  The logarithm of the input pixel
  values, in the range given by the z1 and z2 parameters, is taken before
  dividing the range into the 85 display levels.  Logarithmic mapping allows
  a greater dynamic range.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <B>Rgbto8</B> takes three input IRAF images and produces an 8-bit color map
  which samples the full range of RGB color values and an associated image
  with values indexing the color map.  The compression algorithm is called
  the Median Cut Algorithm and the image is dithered with this color map
  using the Floyd-Steinberg algorithm.  The resulting image is a short image
  with 199 values.  The color map is output in a format suitable for
  use with SAOimage, IMTOOL or XIMTOOL.  This method is recommended over the
  pixel dithering method.
  <P>
  The RGB values are input as three IRAF images.  The images must each be
  scaled to an 8 bit range.  This is done by specifying a range of input
  values to be mapped to the 8 bit range.  In addition the range can be
  mapped logarithmically to allow a greater dynamic range.
  <P>
  The output image is displayed with <B>rgbdisplay</B> and SAOimage, IMTOOL,
  or XIMTOOL.  Note that this requires V1.07 of SAOimage.  The color map
  produced by the <B>rgbto8</B> for a particular image must also be loaded
  into the display server manually.  With IMTOOL use the setup panel and set
  the file name in the user1 or user2 field and then select the appropriate
  map.  With SAOimage you select the "<TT>color</TT>" main menu function, and then the
  "<TT>cmap</TT>" submenu function, and then the "<TT>read</TT>" button.  Note that usually a
  full pathname is required since the server is usually started from the
  login directory.  For XIMTOOL the "<TT>XImtool*cmapDir1</TT>" resource must be
  set to the directory containing the color map and XIMTOOL must be
  restarted to cause the directory to be searched for color map files.
  <P>
  The display server must be setup in it's default contrast mapping (with
  IMTOOL you can use the RESET option, with XIMTOOL the "<TT>normalize</TT>" option is
  used, and with SAOimage you must restart) and the contrast mapping must not
  be changed.  There are no adjustments that can be made in IMTOOL or XIMTOOL
  but with SAOimage you can adjust the colors using the "<TT>gamma</TT>" selections
  and the mouse.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  Three 2048x2048 images of the Trifid nebula are obtained in
  the B, V, and R bandpasses.  These images are properly registered.
  Examination of the histograms leads to selecting the display ranges 1-500
  in each band.  A half size image is created by subsampling using image
  sections.
  <P>
  <PRE>
      cl&gt; rgbto8 trifidr[*:2,*:2] trifidv[*:2,*:2] trifidb[*:2,*:2] \<BR>
      &gt;&gt;&gt; trifid8 maptype=saoimage rz1=1 rz2=500 gz1=1 gz2=500 \<BR>
      &gt;&gt;&gt; bz1=1 bz2=500
  </PRE>
  <P>
  The file trifid8.sao will be created containing the color map for use
  with the image trifid8.
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_time_requirements">TIME REQUIREMENTS</A></H2>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  Example 1 takes 5 minutes on a SparcStation 2.
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  rgbdisplay, rgbdither, rgbsun, color.package
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>