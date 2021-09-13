.. _display:

display — Load an image or image section into the display
=========================================================

**Package: tv**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  display -- Load and display images in an image display
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  display image frame
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>image</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD>Image to be loaded.
  </DD>
  </DL>
  <DL>
  <DT><B>frame</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='frame' Line='frame'>
  <DD>Display frame to be loaded.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B>bpmask = "<TT>BPM</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='bpmask' Line='bpmask = "BPM"'>
  <DD>Bad pixel mask.  The bad pixel mask is used to exclude bad pixels from the
  automatic intensity mapping algorithm.  It may also be displayed as an
  overlay or to interpolate the input image as selected by the <I>bpdisplay</I>
  parameter.  The bad pixel mask is specified by a pixel list image
  (.pl extension) or an regular image.  Values greater than zero define the
  bad pixels.  The special value "<TT>BPM</TT>" may be specified to select a pixel list
  image defined in the image header under the keyword "<TT>BPM</TT>".  If the
  bad pixel mask cannot be found a warning is given and the bad pixel mask
  is not used in the display.
  </DD>
  </DL>
  <DL>
  <DT><B>bpdisplay = "<TT>none</TT>" (none|overlay|interpolate)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='bpdisplay' Line='bpdisplay = "none" (none|overlay|interpolate)'>
  <DD>Type of display for the bad pixel mask.  The options are "<TT>none</TT>" to not
  display the mask, "<TT>overlay</TT>" to display as an overlay with the colors given
  by the <I>bpcolors</I> parameter, or "<TT>interpolate</TT>" to linearly interpolate
  across the bad pixels in the displayed image.  Note that the bad is still
  used in the automatic intensity scaling regardless of the type of display
  for the bad pixel mask.
  </DD>
  </DL>
  <DL>
  <DT><B>bpcolors = "<TT>red</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='bpcolors' Line='bpcolors = "red"'>
  <DD>The mapping between bad pixel values and display colors or intensity values
  when the bad pixels are displayed as an overlay.  There are two forms,
  explicit color assignments for values or ranges of values, and expressions.
  These is described in the OVERLAY COLOR section.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B>overlay = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='overlay' Line='overlay = ""'>
  <DD>Overlay mask to be displayed.  The overlay mask may be a pixel list image
  (.pl extension) or a regular image.  Overlay pixels are identified by
  values greater than zero.  The overlay values are displayed with a mapping
  given by the <I>ocolors</I> parameter.  If the overlay cannot be found a
  warning is given and the overlay is not displayed.
  </DD>
  </DL>
  <DL>
  <DT><B>ocolors = "<TT>green</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ocolors' Line='ocolors = "green"'>
  <DD>The mapping between bad pixel values and display colors or intensity values
  when the bad pixels are displayed as an overlay.  There are two forms,
  explicit color assignments for values or ranges of values, and expressions.
  These is described in the OVERLAY COLOR section.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B>erase = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='erase' Line='erase = yes'>
  <DD>Erase frame before loading image?
  </DD>
  </DL>
  <DL>
  <DT><B>border_erase = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='border_erase' Line='border_erase = no'>
  <DD>Erase unfilled area of window in display frame if the whole frame is not
  erased?
  </DD>
  </DL>
  <DL>
  <DT><B>select_frame = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='select_frame' Line='select_frame = yes'>
  <DD>Select the display frame to be the same as the frame being loaded?
  </DD>
  </DL>
  <DL>
  <DT><B>repeat = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='repeat' Line='repeat = no'>
  <DD>Repeat the previous spatial and intensity transformations?
  </DD>
  </DL>
  <DL>
  <DT><B>fill = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fill' Line='fill = no'>
  <DD>Interpolate the image to fit the display window?
  </DD>
  </DL>
  <DL>
  <DT><B>zscale = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='zscale' Line='zscale = yes'>
  <DD>Apply an automatic intensity mapping algorithm when loading the image?
  </DD>
  </DL>
  <DL>
  <DT><B>contrast = 0.25</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='contrast' Line='contrast = 0.25'>
  <DD>Contrast factor for the automatic intensity mapping algorithm.
  If a value of zero is given then the minimum and maximum of the
  intensity sample is used.
  </DD>
  </DL>
  <DL>
  <DT><B>zrange = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='zrange' Line='zrange = yes'>
  <DD>If not using the automatic mapping algorithm (<I>zscale = no</I>) map the
  full range of the image intensity to the full range of the display?  If the
  displayed image has current min/max values defined these will be used to
  determine the mapping, otherwise the min/max of the intensity sample will
  be used.  The <I>MINMAX</I> task can be used to update the min/max values in
  the image header.
  </DD>
  </DL>
  <DL>
  <DT><B>zmask = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='zmask' Line='zmask = ""'>
  <DD>Pixel mask selecting the sample pixels for the automatic or range intensity
  mapping algorithm.  The pixel mask may be a pixel list image (.pl
  extension), a regular image, or an image section.  The sample pixels are
  identified by values greater than zero in the masks and by the region specified
  in an image section.  If no mask specification is given then a uniform sample
  of approximately <I>nsample</I> good pixels will be used.  The <I>nsample</I>
  parameter also limits the number of sample pixels used from a mask.  Note that
  pixels identified by the bad pixel mask will be excluded from the sample.
  </DD>
  </DL>
  <DL>
  <DT><B>nsample = 1000 (minimum of 100)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nsample' Line='nsample = 1000 (minimum of 100)'>
  <DD>The number of pixels from the image sampled for computing the automatic
  intensity scaling.  This number will be uniformly sampled from the image
  if the default <I>zmask</I> is used otherwise the first <I>nsample</I>
  pixels from the specified mask will be used.
  </DD>
  </DL>
  <DL>
  <DT><B>xcenter = 0.5, ycenter = 0.5</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xcenter' Line='xcenter = 0.5, ycenter = 0.5'>
  <DD>Horizontal and vertical centers of the display window in normalized
  coordinates measured from the left and bottom respectively.
  </DD>
  </DL>
  <DL>
  <DT><B>xsize = 1, ysize = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xsize' Line='xsize = 1, ysize = 1'>
  <DD>Horizontal and vertical sizes of the display window in normalized coordinates.
  </DD>
  </DL>
  <DL>
  <DT><B>xmag = 1., ymag = 1.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xmag' Line='xmag = 1., ymag = 1.'>
  <DD>Horizontal and vertical image magnifications when not filling the display
  window.  Magnifications greater than 1 map image pixels into more than 1
  display pixel and magnifications less than 1 map more than 1 image pixel
  into a display pixel.
  </DD>
  </DL>
  <DL>
  <DT><B>order = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='order' Line='order = 0'>
  <DD>Order of the interpolator to be used for spatially interpolating the image.
  The current choices are 0 for pixel replication, and 1 for bilinear
  interpolation.
  </DD>
  </DL>
  <DL>
  <DT><B>z1, z2</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='z1' Line='z1, z2'>
  <DD>Minimum and maximum image intensity to be mapped to the minimum and maximum
  display levels.  These values apply when not using the automatic or range
  intensity mapping methods.
  </DD>
  </DL>
  <DL>
  <DT><B>ztrans = "<TT>linear</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ztrans' Line='ztrans = "linear"'>
  <DD>Transformation of the image intensity levels to the display levels.  The
  choices are:
  <DL>
  <DT><B>"<TT>linear</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"linear"'>
  <DD>Map the minimum and maximum image intensities linearly to the minimum and
  maximum display levels.
  </DD>
  </DL>
  <DL>
  <DT><B>"<TT>log</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"log"'>
  <DD>Map the minimum and maximum image intensities linearly to the range 1 to 1000,
  take the logarithm (base 10), and then map the logarithms to the display
  range.
  </DD>
  </DL>
  <DL>
  <DT><B>"<TT>none</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"none"'>
  <DD>Apply no mapping of the image intensities (regardless of the values of
  <I>zcale, zrange, z1, and z2</I>).  For most image displays, values exceeding
  the maximum display value are truncated by masking the highest bits.
  This corresponds to applying a modulus operation to the intensity values
  and produces "<TT>wrap-around</TT>" in the display levels.
  </DD>
  </DL>
  <DL>
  <DT><B>"<TT>user</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"user"'>
  <DD>User supplies a look up table of intensities and their corresponding
  greyscale values.  
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>lutfile = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lutfile' Line='lutfile = ""'>
  <DD>Name of text file containing the look up table when <I>ztrans</I> = user.
  The table should contain two columns per line; column 1 contains the
  intensity, column 2 the desired greyscale output.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The specified image and overlay mask are loaded into the specified frame of
  the standard image display device ("<TT>stdimage</TT>").  For devices with more than
  one frame it is possible to load an image in a frame different than that
  displayed on the monitor.  An option allows the loaded frame to become the
  displayed frame.  The previous contents of the frame may be erased (which
  can be done very quickly on most display devices) before the image is
  loaded.  Without erasing, the image replaces only those pixels in the frame
  defined by the display window and spatial mapping described below.  This
  allows displaying more than one image in a frame.  An alternate erase
  option erases only those pixels in the defined display window which are not
  occupied by the image being loaded.  This is generally slower than erasing
  the entire frame and should be used only if a display window is smaller
  than the entire frame.
  <P>
  The image is mapped both in intensity and in space.  The intensity is
  mapped from the image pixel values to the range of display values in the
  device.  Spatial interpolation maps the image pixel coordinates into a part
  of the display frame called the display window.  Many of the parameters of
  this task are related to these two transformations.
  <P>
  A bad pixel mask may be specified to be displayed as an overlay or to
  interpolate the displayed image.  It is also used to exclude bad pixels
  from the automatic intensity scaling.  The bad pixel mask is specified by
  the parameter <I>bpmask</I> and the display mode by the <I>bpdisplay</I>
  parameter.  The overlay display option uses the <I>bpcolors</I> parameters
  to specify a color mapping as described in the OVERLAY COLOR section.
  Interpolation consists of linear interpolation across columns if the mask
  value is one, across lines if the mask value is two, or across the shortest
  direction for other values.  This interpolation is done on the input data
  before any spatial interpolation and filling is done.  It does not modify
  the input data.  The task <B>fixpix</B> provides the same algorithm to fix
  the data in the image.
  <P>
  An overlay mask may be specified by the <I>overlay</I> parameter.  Any
  value greater than zero in the overlay mask will be displayed in the color or
  intensity specified by the <I>ocolor</I> parameter (see the OVERLAY COLOR
  section).
  <P>
  Note that bad pixel masks in "<TT>pixel list</TT>" format are constrained to
  non-negative values.  When an image is used instead of a pixel list the
  image is internally converted to a pixel list.  Negative values are
  set to zero or good pixels and positive real values are truncated to
  the nearest integer.
  <P>
  A display window is defined in terms of the full frame.  The lower left
  corner of the frame is (0, 0) and the upper right corner is (1, 1) as
  viewed on the monitor.  The display window is specified by a center
  (defaulted to the center of the frame (0.5, 0.5)) and a size (defaulted to
  the full size of the frame, 1 by 1).  The image is loaded only within the
  display window and does not affect data outside the window; though, of
  course, an initial frame erase erases the entire frame.  By using different
  windows one may load several images in various parts of the display frame.
  <P>
  If the option <I>fill</I> is selected the image and overlay mask are
  spatially interpolated to fill the display window in its largest dimension
  (with an aspect ratio of 1:1).  When the display window is not
  automatically filled the image is scaled by the magnification factors
  (which need not be the same) and centered in the display window.  If the
  number of image pixels exceeds the number of display pixels in the window
  only the central portion of the image which fills the window is loaded.  By
  default the display window is the full frame, the image is not interpolated
  (no filling and magnification factors of 1), and is centered in the frame.
  The spatial interpolation algorithm is described in the section MAGNIFY AND
  FILL ALGORITHM.
  <P>
  There are several options for mapping the pixel values to the display values.
  There are two steps; mapping a range of image intensities to
  the full display range and selecting the mapping function or
  transformation.  The mapping transformation is set by the parameter
  <I>ztrans</I>.  The most direct mapping is "<TT>none</TT>" which loads the
  image pixel values directly without any transformation or range
  mapping.  Most displays only use the lowest bits resulting in a
  wrap-around effect for images with a range exceeding the display range.
  This is sometimes desirable because it produces a contoured image which
  is not saturated at the brightest or weakest points.
  This is the fastest method of loading the display.  Another
  transformation, "<TT>linear</TT>", maps the selected image range linearly to the full
  display range.  The logarithmic transformation, "<TT>log</TT>", maps the image range
  linearly between 1 and 1000 and then maps the logarithm (base 10) linearly
  to the full display range.  In the latter transformations pixel values
  greater than selected maximum display intensity are set to the maximum
  display value and pixel values less than the minimum intensity
  are set to the minimum display value.
  <P>
  Methods for setting of the range of image pixel values, <I>z1</I> and
  <I>z2</I>, to be mapped to the full display range are arranged in a
  hierarchy from an automatic mapping which gives generally good result for
  typical astronomical images to those requiring the user to specify the
  mapping in detail.  The automatic mapping is selected with the parameter
  <I>zscale</I>.  The automatic mapping algorithm is described in the section
  ZSCALE ALGORITHM and has three parameters, <I>zmask</I>, <I>nsample</I> and
  <I>contrast</I>.
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
  examined.  If <I>zrange</I> is yes then the minimum and maximum pixel values
  in the image are taken from the image header or estimated from the
  intensity sample and <I>z1</I> and <I>z1</I> are set to those values,
  respectively.  This insures that the full range of the image is displayed
  but is generally slower than the zscale algorithm (because all the image
  pixels must be examined) and, for images with a large dynamic range, will
  generally show only the brightest parts of the image.
  <P>
  Finally, if the zrange algorithm is not selected the user specifies the
  values of <I>z1</I> and <I>z2</I> directly.
  <P>
  Often several images are to be loaded with the same intensity and spatial
  transformations.  The option <I>repeat</I> repeats the transformations from
  the previous image loaded.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Zscale algorithm</H3>
  <! BeginSection: 'ZSCALE ALGORITHM'>
  <UL>
  The zscale algorithm is designed to display the image values near the median
  image value without the time consuming process of computing a full image
  histogram.  This is particularly useful for astronomical images which
  generally have a very peaked histogram corresponding to the background
  sky in direct imaging or the continuum in a two dimensional spectrum.
  <P>
  The sample of pixels, specified by values greater than zero in the sample mask
  <I>zmask</I> or by an image section, is selected up to a maximum of
  <I>nsample</I> pixels.  If a bad pixel mask is specified by the <I>bpmask</I>
  parameter then any pixels with mask values which are greater than zero are not
  counted in the sample.  Only the first pixels up to the limit are selected
  where the order is by line beginning from the first line.  If no mask is
  specified then a grid of pixels with even spacing along lines and columns
  that make up a number less than or equal to the maximum sample size is
  used.
  <P>
  If a <I>contrast</I> of zero is specified (or the <I>zrange</I> flag is
  used and the image does not have a valid minimum/maximum value) then
  the minimum and maximum of the sample is used for the intensity mapping
  range.
  <P>
  If the contrast is not zero the sample pixels are ranked in brightness to
  form the function I(i) where i is the rank of the pixel and I is its
  value.  Generally the midpoint of this function (the median) is very near
  the peak of the image histogram and there is a well defined slope about the
  midpoint which is related to the width of the histogram.  At the ends of
  the I(i) function there are a few very bright and dark pixels due to
  objects and defects in the field.  To determine the slope a linear function
  is fit with iterative rejection;
  <P>
          I(i) = intercept + slope * (i - midpoint)
  <P>
  If more than half of the points are rejected then there is no well defined
  slope and the full range of the sample defines <I>z1</I> and <I>z2</I>.
  Otherwise the endpoints of the linear function are used (provided they are
  within the original range of the sample):
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
  <H3>Magnify and fill algorithm</H3>
  <! BeginSection: 'MAGNIFY AND FILL ALGORITHM'>
  <UL>
  The spatial interpolation algorithm magnifies (or demagnifies) the image
  (and the bad pixel and overlay masks) along each axis by the desired
  amount.  The fill option is a special case of magnification in that the
  magnification factors are set by the requirement that the image just fit
  the display window in its maximum dimension with an aspect ratio (ratio of
  magnifications) of 1.  There are two requirements on the interpolation
  algorithm; all the image pixels must contribute to the interpolated image
  and the interpolation must be time efficient.  The second requirement means
  that simple linear interpolation is used.  If more complex interpolation is
  desired then tasks in the IMAGES package must be used to first interpolate
  the image to the desired size before loading the display frame.
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
  <H3>Overlay colors</H3>
  <! BeginSection: 'OVERLAY COLORS'>
  <UL>
  The masks specified by the <I>bpmask</I> and <I>overlay</I> parameters may be
  displayed as color overlays on the image data.  The non-zero pixels in the
  mask are assigned integer display values.  The values may fall in the same
  range, 1 to 200, as the mapped image pixel data values and will behave the
  same way as the pixel values when the display map is interactively adjusted.
  Values of 0 and 201 to 255 may be used and depend on the display server and
  display resource definitions.  The expected or standard server behavior is
  that 0 is the background color and 201 to 255 are various colors with the
  lower numbers being the more standard primary colors.  The expected colors
  are:
  <P>
  <PRE>
          Value   Color               Value   Color
          201     white (cursor)      210     coral
          202     black (background)  211     maroon
          203     white               212     orange
          204     red                 213     khaki
          205     green               214     orchid
          206     blue                215     turquoise
          207     yellow              216     violet
          208     cyan                217     wheat
          209     magenta
  </PRE>
  <P>
  The values 201 and 202 are tied to the cursor and background resource
  colors.  These are generally white and black respectively.  Values above 217
  are not defined and depend on the current state of the color table for the
  window system.
  <P>
  The mapping between mask values and overlay colors are specified
  by the <I>bpcolors</I> and <I>ocolors</I> parameters.  There are two mapping
  syntax, a list and an expression.
  <P>
  The list syntax consists of
  a comma delimited set of values and assignments with one of the following
  forms.
  <P>
  <PRE>
      color
      maskvalue=color
      maskvalue-maskvalue=color
  </PRE>
  <P>
  where color may be a color name, a color value, or value to be added or
  subtracted to the mask value to yield a color value.  Color names may be
  black, white, red, green, blue, yellow, cyan, magenta, or transparent with
  case ignored and abbreviations allowed.  Transparent does the obvious of
  being invisible.  These values are based on the default resource colors for
  the display servers (as shown above) and any custom definitions may result
  in incorrect colors.
  <P>
  The color values are unsigned integers (no <TT>'+'</TT> or <TT>'-'</TT>) or values to be added
  or subtracted are given as signed integers.  The first form provides the
  default intensity or color for all mask values.  Note that if no default
  color is specified the default will be white.  The other forms map a mask
  value or range of mask values to a color.  In a list the last color defined
  for the default or mask value will be used.
  <P>
  The addition or subtraction from mask values provides a mechanism to have
  the bad pixel or overlay masks encode a variety of overlay colors.  Note
  that to display the mask values directly as colors one would use the color
  value "<TT>+0</TT>".  Subtraction may produce values less than zero which then
  are not visible; i.e. equivalent to "<TT>transparent</TT>".
  <P>
  The following examples illustrate the features of the syntax.
  <P>
  <PRE>
      ocolors=""          Display in default white
      ocolors="red"       Display in red
      ocolors="+0"        Display mask values as color values
      ocolors="+200"      Display mask values offset by 200
  <P>
      ocolors="205,1=red,2=yellow,10-20=cyan,30-40=+100,50-100=transparent"
  </PRE>
  <P>
  The last example has a default color of 205, mask values of 1 are
  red, mask values of 2 are yellow, mask values of 10 to 20 are cyan,
  and mask values of 30 to 40 are displayed as intensities 130 to 140.
  <P>
  Expressions are identified by being enclosed in parentheses.
  This uses the general IRAF expression syntax (see <B>expressions</B>).
  The mask values are referenced by the character $.  The same named
  colors (black, white, red, green, blue, yellow, cyan, magenta,
  and transparent) may be used in place of color values. Expressions
  must evaluate to integer values.  To avoid needing special handling of
  input mask values of zero, all pixels with input mask values of zero
  are not shown regardless of the expression value.
  <P>
  There are currently two function extensions, "<TT>colors</TT>" and "<TT>acenum</TT>".
  In both functions the first and only required argument, arg1, is an integer
  value.  Typically this will <TT>'$'</TT> or a function based on <TT>'$'</TT>.
  <P>
  The "<TT>colors</TT>" function maps input values with a modulus type behavior.  The
  optional second argument, arg2, is a color value for mapping zero.  As noted
  above, if the input mask value is zero it will not be displayed.  However,
  functions applied to non-zero input mask values may return a value of zero
  which may then be displayed with the specified color.  The default is
  transparent.  The next two optional arguments (arg3 and arg4) define a color
  range with defaults of 204 to 217.  If only arg3 is specified then
  arg4 takes the value of arg3, thus having the effect of a constant
  output color.  Positive values of the first argument are mapped to a color
  value by
  <P>
  <PRE>
      if arg1 is 0:       result = arg2
      if arg1 greater 0:  result = arg3 + mod ($-1, arg4-arg3+1)
      otherwise:          result = arg1
  </PRE>
  <P>
  This function is primarily used to make colorful displays of regions
  defined with different mask values.
  <P>
  The "<TT>acenum</TT>" function handles <B>ace</B> package object detection masks
  which include bit flags.  Each object in the mask has an object number
  with value greater than 10.  Values less than 10 are passed along during
  detection and generally identify detector or saturated bad pixels.
  Along with the object number there may be zero or more bit flags
  set.  This function removes the bit flags and returns the mask number.
  The optional second argument, arg2, is a string of letters which selects
  pixels with certain sets of bit flags.  The bit flags are:
  <P>
  <PRE>
      B -- a bad pixel treated as a good for detection
      D -- original detection (i.e. without G or S flag)
      E -- edge pixel used for displaying detection isophotes
      F -- object contains a bad pixel
      G -- grown pixel
      S -- pixel not assigned to an object during splitting
  </PRE>
  <P>
  The default of arg2 is "<TT>BDEG</TT>" which essentially returns all pixels
  in an object.
  <P>
  The acenum function also returns 0 for the pixels with values between
  one and ten and -1 for the pixels not selected by the flags.  The value
  of zero may be made visible using the colors function.  The two functions
  are often used in concert:
  <P>
  <PRE>
      (colors(acenum($)))
      (colors(acenum($),black))
      (colors(acenum($,<TT>'E'</TT>),red,green)
  </PRE>
  <P>
  Note that when filling and anti-aliasing the behavior of the overlay
  colors may be different than intended.
  </UL>
  <! EndSection:   'OVERLAY COLORS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  For the purpose of these examples we assume a display with four frames,
  512 x 512 in size, and a display range of 0 to 255.  Also consider two
  images, image1 is 100 x 200 with a range 200 to 2000 and image2 is
  2000 x 1000 with a range -1000 to 1000.  To load the images with the
  default parameters:
  <P>
  <PRE>
          cl&gt; display image1 1
          cl&gt; display image2 2
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
          cl&gt; display image2 3 fill+ zscale-
  <P>
  The next example makes image1 square and sets the intensity range explicitly.
  <P>
          cl&gt; display image1 4 zscale- zrange- z1=800 z2=1200 xmag=2
  <P>
  The next example loads the two images in the same frame side-by-side.
  <P>
  <PRE>
          cl&gt; display.xsize=0.5
          cl&gt; display image1 fill+ xcen=0.25
          cl&gt; display image2 erase- fill+ xcen=0.75
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>DISPLAY V2.11</B></DT>
  <! Sec='REVISIONS' Level=0 Label='DISPLAY' Line='DISPLAY V2.11'>
  <DD>The bad pixel mask, overlay mask, sample mask, and overlay colors
  parameters and functionality have been added.  The "<TT>nsample_lines</TT>"
  parameter is now an "<TT>nsample</TT>" parameter.
  <P>
  Bugs in the coordinate system sent to the image display for cursor
  readback were fixed.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  The "<TT>repeat</TT>" option is not implemented.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  cvl, magnify, implot, minmax, fixpix
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'ZSCALE ALGORITHM' 'MAGNIFY AND FILL ALGORITHM' 'OVERLAY COLORS' 'EXAMPLES' 'REVISIONS' 'BUGS' 'SEE ALSO'  >
  
