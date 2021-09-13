rgbdisplay — Display an RGB image
=================================

**Package: color**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>rgbdisplay (Oct92)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>color</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>rgbdisplay (Oct92)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>rgbdisplay</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  rgbdisplay -- display an RGB image
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  rgbdisplay rgb
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_rgb">rgb</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rgb' Line='rgb'>
  <DD>Image name of the 8-bit RGB dithered composite image to be displayed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_frame">frame = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='frame' Line='frame = 1'>
  <DD>Image display frame.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <B>Rgbdisplay</B> displays an 8-bit RGB color mapped or dithered image produced
  by the tasks <B>rgbto8</B> or <B>rgbdither</B>.  This task is a simple script
  calling
  the <B>display</B> task with parameters fixed appropriately for the
  images.  The actual display command is:
  <P>
  <PRE>
  	display rgb frame fill- ztrans=none
  </PRE>
  <P>
  where rgb and frame are the parameters of this task.
  <P>
  In addition to loading the image with the <B>rgbdisplay</B> task
  it is also necessary to adjust the image display server.  Either
  SAOimage or IMTOOL may be used.  SAOimage is to be prefered because
  it is possible to make some adjustments in the color mapping while with
  IMTOOL one must modify the composite image by varying the z1 and z2
  values for the three images.
  <P>
  Both display servers must be set so that there is no contrast stretching.
  This is how both programs start initially but it may be difficult to return
  to this state if you adjust the contrast with the right mouse button in
  IMTOOL or the contrast adjustments in the (COLOR) menu of SAOimage.
  <P>
  You must first determine where the special color maps are located.
  For the images produced by <B>rgbto8</B> the color map will be in
  the same directory as the image and have the same name with either
  the extension "<TT>.sao</TT>" or "<TT>.imt</TT>" depending on the target display server.
  Since the display servers are host programs they require host pathnames.
  <P>
  For the images produced by <B>rgbdither</B>
  you can determine the host pathname for the special color map
  from within IRAF using the command
  <P>
  <PRE>
  	cl&gt; path colorlib$saorgb.lut
  	puppis!/ursa/iraf/extern/color/lib/saorgb.lut
  <P>
  			or
  <P>
  	cl&gt; path colorlib$imtoolrgb.lut
  	puppis!/ursa/iraf/extern/color/lib/imtoolrgb.lut
  </PRE>
  <P>
  You can either remember these names (without the node prefix) or
  more simply copy the one you need to your IRAF home directory
  (or any place else you like) with the command
  <P>
  <PRE>
  	cl&gt; copy colorlib$saorgb.lut home$
  <P>
  			or
  <P>
  	cl&gt; copy colorlib$imtoolrgb.lut home$
  </PRE>
  <P>
  With SAOimage load the appropriate color map look up table by entering the
  (COLOR) menu, then the (CMAP) menu, and then pushing the (READ) button.
  When you are prompted for the map enter the pathname for the file
  saorgb.lut.  For IMTOOL you need to call up the setup menu and set the
  pathname for the file imtoolrgb.lut in either of the user look up tables
  and then select the appropriate map.
  <P>
  For IMTOOL that is all you can do.  Beware, don't adjust the contrast (the
  right mouse button) since this destroys the mapping between the composite
  image values and the look up table.
  <P>
  In SAOimage there are a couple of things you can do to make adjustments to
  the display.  If you select (GAMMA) in the (COLOR) menu you can then move
  the mouse with a button down and vary the linearity of the color maps.
  This may be used with either of the 8-bit algorithms.
  <P>
  For the pixel dithered images you can also directly manipulate the color
  map.  Bring up the color editor by clicking on the color bar.  Even if you
  don't adjust the look up table this can be instructive.  You can also
  adjust the individual colors by clicking the left (red), middle (green), or
  right (blue) buttons to either move the shown points or add and move points
  in the middle.  Note that the abrupt discontinuity between the colors can
  cause sudden jumps in the color map if one point is moved past the other
  but you can recover by bring the point slowly back.  If the map gets too
  messed up you can always reload the color map.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  Display a dithered composite image.
  <P>
  <PRE>
  	cl&gt; rgbdisplay tucana!/d1/testdata/rgb/trifid8
  	&lt;Load the color map tucana!/d1/testdata/rgb/trifid8.sao or
  	&lt;tucana!/d1/testdata/rgb/trifid8.imt. Because the display
  	&lt;server is a host program you may need to copy the map
  	&lt;first.
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  rgbto8, rgbdither, color.package
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>