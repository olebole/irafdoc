cvl — Load image display (newer version of 'display')
=====================================================

**Package: iis**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>cvl (Jul87)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>images.tv.iis</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>cvl (Jul87)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>cvl</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  cvl -- load images in image display
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  cvl image frame
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_image">image</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD>Image to be loaded.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_frame">frame</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='frame' Line='frame'>
  <DD>Display frame to be loaded.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_erase">erase = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='erase' Line='erase = yes'>
  <DD>Erase frame before loading image?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_border_erase">border_erase = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='border_erase' Line='border_erase = no'>
  <DD>Erase unfilled area of window in display frame if the whole frame is not
  erased?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_select_frame">select_frame = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='select_frame' Line='select_frame = yes'>
  <DD>Display the frame to be loaded?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fill">fill = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fill' Line='fill = no'>
  <DD>Interpolate or block average the image to fit the display window?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_zscale">zscale = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='zscale' Line='zscale = yes'>
  <DD>Apply an automatic intensity mapping algorithm when loading the image?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_contrast">contrast = 0.25</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='contrast' Line='contrast = 0.25'>
  <DD>Contrast factor for the automatic intensity mapping algorithm.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_zrange">zrange = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='zrange' Line='zrange = yes'>
  <DD>If not using the automatic mapping algorithm (<I>zscale = no</I>) map the
  full range of the image intensity to the full range of the display?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nsample_lines">nsample_lines = 5</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nsample_lines' Line='nsample_lines = 5'>
  <DD>Number of sample lines to use in the automatic intensity mapping algorithm.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xcenter">xcenter = 0.5, ycenter = 0.5</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xcenter' Line='xcenter = 0.5, ycenter = 0.5'>
  <DD>Horizontal and vertical centers of the display window in normalized
  coordinates measured from the left and bottom respectively.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xsize">xsize = 1, ysize = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xsize' Line='xsize = 1, ysize = 1'>
  <DD>Horizontal and vertical sizes of the display window in normalized coordinates.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xmag">xmag = 1., ymag = 1.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xmag' Line='xmag = 1., ymag = 1.'>
  <DD>Horizontal and vertical image magnifications when not filling the display
  window.  Magnifications greater than 1 map image pixels into more than 1
  display pixel and magnifications less than 1 map more than 1 image pixel
  into a display pixel.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_z1">z1, z2</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='z1' Line='z1, z2'>
  <DD>Minimum and maximum image intensity to be mapped to the minimum and maximum
  display levels.  These values apply when not using the automatic or range
  intensity mapping methods.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ztrans">ztrans = "<TT>linear</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ztrans' Line='ztrans = "linear"'>
  <DD>Transformation of the image intensity levels to the display levels.  The
  choices are:
  <DL>
  <DT><B><A NAME="l_">"<TT>linear</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"linear"'>
  <DD>Map the minimum and maximum image intensities linearly to the minimum and
  maximum display levels.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">"<TT>log</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"log"'>
  <DD>Map the minimum and maximum image intensities linearly to the range 1 to 1000,
  take the logarithm (base 10), and then map the logarithms to the display
  range.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">"<TT>none</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"none"'>
  <DD>Apply no mapping of the image intensities (regardless of the values of
  <I>zscale, zrange, z1, and z2</I>).  For most image displays, values exceeding
  the maximum display value are truncated by masking the highest bits.
  This corresponds to applying a modulus operation to the intensity values
  and produces "<TT>wrap-around</TT>" in the display levels.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">"<TT>user</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"user"'>
  <DD>User supplies a look up table of intensities and their corresponding
  greyscale values.  
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_lutfile">lutfile = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lutfile' Line='lutfile = ""'>
  <DD>Name of text file containing the look up table when <I>ztrans</I> = user.
  The table should contain two columns per line; column 1 contains the
  intensity, column 2 the desired greyscale output.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The specified image is loaded into the specified frame of the standard
  image display device ("<TT>stdimage</TT>").  For devices with more than one
  frame it is possible to load an image in a frame different than that
  displayed on the monitor.  An option allows the loaded frame to become
  the displayed frame.  The previous contents of the frame may be erased
  (which can be done very quickly on most display devices) before the
  image is loaded.  Without erasing, the image replaces only those pixels
  in the frame defined by the display window and spatial mapping
  described below.  This allows displaying more than one image in a
  frame.  An alternate erase option erases only those pixels in the
  defined display window which are not occupied by the image being
  loaded.  This is generally slower than erasing the entire frame and
  should be used only if a display window is smaller than the entire
  frame.
  <P>
  The image is mapped both in intensity and in space.  The intensity is
  mapped from the image pixel values to the range of display values in
  the device.  Spatial interpolation maps the image pixel coordinates
  into a part of the display frame called the display window.  Many of
  the parameters of this task are related to these two transformations.
  <P>
  A display window is defined in terms of the full frame.  The lower left
  corner of the frame is (0, 0) and the upper right corner is (1, 1) as viewed on
  the monitor.  The display window is specified by a center (defaulted to the
  center of the frame (0.5, 0.5)) and a size (defaulted to the full size of
  the frame, 1 by 1).  The image is loaded only within the display window and
  does not affect data outside the window; though, of course, an initial
  frame erase erases the entire frame.  By using different windows one may
  load several images in various parts of the display frame.
  <P>
  If the option <I>fill</I> is selected the image is spatially interpolated
  to fill the display window in its largest dimension (with an aspect
  ratio of 1:1).  When the display window is not automatically filled
  the image is scaled by the magnification factors (which need not be
  the same) and centered in the display window.  If the number of image
  pixels exceeds the number of display pixels in the window only the central
  portion of the image which fills the window is loaded.  By default
  the display window is the full frame, the image is not interpolated
  (no filling and magnification factors of 1), and is centered in the frame.
  The spatial interpolation algorithm is described in the section
  MAGNIFY AND FILL ALGORITHM.
  <P>
  There are several options for mapping the pixel values to the display
  values.  There are two steps; mapping a range of image intensities to
  the full display range and selecting the mapping function or
  transformation.  The mapping transformation is set by the parameter
  <I>ztrans</I>.  The most direct mapping is "<TT>none</TT>" which loads the image
  pixel values directly without any transformation or range mapping.
  Most displays only use the lowest bits resulting in a wrap-around
  effect for images with a range exceeding the display range.  This is
  sometimes desirable because it produces a contoured image which is not
  saturated at the brightest or weakest points.  This transformation is
  also the fastest.  Another transformation, "<TT>linear</TT>", maps the selected
  image range linearly to the full display range.  The logarithmic
  transformation, "<TT>log</TT>", maps the image range linearly between 1 and 1000
  and then maps the logarithm (base 10) linearly to the full display
  range.  In the latter transformations pixel values greater than
  selected maximum display intensity are set to the maximum display value
  and pixel values less than the minimum intensity are set to the minimum
  display value.
  <P>
  Methods for setting of the range of image pixel values, <I>z1</I> and
  <I>z2</I>, to be mapped to the full display range are arranged in a
  hierarchy from an automatic mapping which gives generally good result
  for typical astronomical images to those requiring the user to specify
  the mapping in detail.  The automatic mapping is selected with the
  parameter <I>zscale</I>.  The automatic mapping algorithm is described
  in the section ZSCALE ALGORITHM and has two parameters,
  <I>nsample_lines</I> and <I>contrast</I>.
  <P>
  When <I>ztrans</I> = user, a look up table of intensity values and their
  corresponding greyscale levels is read from the file specified by the
  <I>lutfile</I> parameter.  From this information, a piecewise linear
  look up table containing 4096 discrete values is composed.  The text
  format table contains two columns per line; column 1 contains the
  intensity, column 2 the desired greyscale output.  The greyscale values
  specified by the user must match those available on the output device.
  Task <I>showcap</I> can be used to determine the range of acceptable
  greyscale levels.  When <I>ztrans</I> = user, parameters <I>zscale</I>,
  <I>zrange</I> and <I>zmap</I> are ignored.
  <P>
  If the zscale algorithm is not selected the <I>zrange</I> parameter is
  examined.  If <I>zrange</I> is yes then <I>z1</I> and <I>z2</I> are set to
  the minimum and maximum image pixels values, respectively.  This insures
  that the full range of the image is displayed but is generally slower
  than the zscale algorithm (because all the image pixels must be examined)
  and, for images with a large dynamic range, will generally show only the
  brightest parts of the image.
  <P>
  Finally, if the zrange algorithm is not selected the user specifies the
  values of <I>z1</I> and <I>z2</I> directly.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_zscale_algorithm">ZSCALE ALGORITHM</A></H2>
  <! BeginSection: 'ZSCALE ALGORITHM'>
  <UL>
  The zscale algorithm is designed to display the image values near the median
  image value without the time consuming process of computing a full image
  histogram.  This is particularly useful for astronomical images which
  generally have a very peaked histogram corresponding to the background
  sky in direct imaging or the continuum in a two dimensional spectrum.
  <P>
  A subset of the image is examined.  Approximately 600 pixels are
  sampled evenly over the image.  The number of lines is a user parameter,
  <I>nsample_lines</I>.  The pixels are ranked in brightness to
  form the function I(i) where i is the rank of the pixel and I is its value.
  Generally the midpoint of this function (the median) is very near the peak
  of the image histogram and there is a well defined slope about the midpoint
  which is related to the width of the histogram.  At the ends of the
  I(i) function there are a few very bright and dark pixels due to objects
  and defects in the field.  To determine the slope a linear function is fit
  with iterative rejection;
  <P>
  	I(i) = intercept + slope * (i - midpoint)
  <P>
  If more than half of the points are rejected
  then there is no well defined slope and the full range of the sample
  defines <I>z1</I> and <I>z2</I>.  Otherwise the endpoints of the linear
  function are used (provided they are within the original range of the
  sample):
  <P>
  <PRE>
  	z1 = I(midpoint) + (slope / contrast) * (1 - midpoint)
  	z2 = I(midpoint) + (slope / contrast) * (npoints - midpoint)
  </PRE>
  <P>
  As can be seen, the parameter <I>contrast</I> may be used to adjust the contrast
  produced by this algorithm.
  </UL>
  <! EndSection:   'ZSCALE ALGORITHM'>
  <H2><A NAME="s_magnify_and_fill_algorithm">MAGNIFY AND FILL ALGORITHM</A></H2>
  <! BeginSection: 'MAGNIFY AND FILL ALGORITHM'>
  <UL>
  The spatial interpolation algorithm magnifies (or demagnifies) the
  image along each axis by the desired amount.  The fill option is a
  special case of magnification in that the magnification factors are set
  by the requirement that the image just fit the display window in its
  maximum dimension with an aspect ratio (ratio of magnifications) of 1.
  There are two requirements on the interpolation algorithm; all the
  image pixels must contribute to the interpolated image and the
  interpolation must be time efficient.  The second requirement means that
  simple linear interpolation is used.  If more complex interpolation is
  desired then tasks in the IMAGES package must be used to first
  interpolate the image to the desired size before loading the display
  frame.
  <P>
  If the magnification factors are greater than 0.5 (sampling step size
  less than 2) then the image is simply interpolated.  However, if the
  magnification factors are less than 0.5 (sampling step size greater
  than 2) the image is first block averaged by the smallest amount such
  that magnification in the reduced image is again greater than 0.5.
  Then the reduced image is interpolated to achieve the desired
  magnifications.  The reason for block averaging rather than simply
  interpolating with a step size greater than 2 is the requirement that
  all of the image pixels contribute to the displayed image.  If this is
  not desired then the user can explicitly subsample using image
  sections.  The effective difference is that with subsampling the
  pixel-to-pixel noise is unchanged and small features may be lost due to
  the subsampling.  With block averaging pixel-to-pixel noise is reduced
  and small scale features still contribute to the displayed image.
  </UL>
  <! EndSection:   'MAGNIFY AND FILL ALGORITHM'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  For the purpose of these examples we assume a display with four frames,
  512 x 512 in size, and a display range of 0 to 255.  Also consider two
  images, image1 is 100 x 200 with a range 200 to 2000 and image2 is
  2000 x 1000 with a range -1000 to 1000.  To load the images with the
  default parameters:
  <P>
  <PRE>
  	cl&gt; cvl image1 1
  	cl&gt; cvl image2 2
  </PRE>
  <P>
  The image frames are first erased and image1 is loaded in the center of
  display frame 1 without spatial interpolation and with the automatic intensity
  mapping.  Only the central 512x512 area of image2 is loaded in display frame 2
  <P>
  To load the display without any intensity transformation:
  <P>
  	cl&gt; cvl image1 1 ztrans=none
  <P>
  The next example interpolates image2 to fill the full 512 horizontal range
  of the frame and maps the full image range into the display range.  Note
  that the spatial interpolation first block averages by a factor of 2 and then
  magnifies by 0.512.
  <P>
  	cl&gt; cvl image2 3 fill+ zscale-
  <P>
  The next example makes image1 square and sets the intensity range explicitly.
  <P>
  	cl&gt; cvl image1 4 zscale- zrange- z1=800 z2=1200 xmag=2
  <P>
  The next example loads the two images in the same frame side-by-side.
  <P>
  <PRE>
  	cl&gt; cvl.xsize=0.5
  	cl&gt; cvl image1 fill+ xcen=0.25
  	cl&gt; cvl image2 erase- fill+ xcen=0.75
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  display, magnify
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'ZSCALE ALGORITHM' 'MAGNIFY AND FILL ALGORITHM' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>