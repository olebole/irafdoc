.. _runmed:

runmed — Running median a list of images at each pixel position
===============================================================

**Package: imfilter**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  runmed -- running median filter a list of images
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  runmed input output window
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of input images.  The list is used in the order provided without
  sorting.  All images must be the same dimensionality and size.  There must
  be at least three images.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>List of output images. The number of output images must be the same as
  the number of input images.  If the input image name is the same as the
  output image name the original image is replaced by the filtered image.
  </DD>
  </DL>
  <DL>
  <DT><B>window</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='window' Line='window'>
  <DD>Number of images for the running window.  This must be at least three, and
  less than or equal to the number of images in the input list.
  </DD>
  </DL>
  <DL>
  <DT><B>masks = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='masks' Line='masks = ""'>
  <DD>List of output masks indicating the number of pixels used in calculating the
  filter value.  If specified the list must match the output list.
  </DD>
  </DL>
  <DL>
  <DT><B>inmaskkey = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='inmaskkey' Line='inmaskkey = ""'>
  <DD>Keyword in the input image containing a maskname for selecting or ignoring
  pixels.  Pixels to be used are selected by zero values in the mask.
  </DD>
  </DL>
  <DL>
  <DT><B>outmaskkey = "<TT>HOLES</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outmaskkey' Line='outmaskkey = "HOLES"'>
  <DD>Keyword in the output image to containing the name of the output mask.
  If no output mask is created or if no keyword is specified then the
  keyword is not added or replaced in the output image.
  </DD>
  </DL>
  <DL>
  <DT><B>outtype = "<TT>filter</TT>" (filter|difference|ratio)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outtype' Line='outtype = "filter" (filter|difference|ratio)'>
  <DD>The type of output values in the images.  The choices are "<TT>filter</TT>" for
  the filter value, "<TT>difference</TT>" for the difference of the input and
  filter value (input-filter), and "<TT>ratio</TT>" for the ratio of the input
  and filter value (input/filter).
  </DD>
  </DL>
  <DL>
  <DT><B>exclude = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='exclude' Line='exclude = no'>
  <DD>Exclude the input image from the filter.
  </DD>
  </DL>
  <DL>
  <DT><B>nclip = 0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nclip' Line='nclip = 0.'>
  <DD>This parameter allows clipping high values from the median calculation.
  The value multiples the difference between the median and the lowest value
  and rejects values that exceed the median by this amount.  The is done
  after scaling, mask rejections, and image exclusion.
  </DD>
  </DL>
  <DL>
  <DT><B>navg = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='navg' Line='navg = 1'>
  <DD>Number of central values to average.  A value of 1 is used to compute
  the median.
  </DD>
  </DL>
  <DL>
  <DT><B>scale = "<TT>none</TT>" (none|mode|!&lt;keyword&gt;|@&lt;file&gt;)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='scale' Line='scale = "none" (none|mode|!&lt;keyword&gt;|@&lt;file&gt;)'>
  <DD>Scale the images with the specified method.  The choices are
  "<TT>none</TT>", "<TT>mode</TT>" to compute a mode for each image and divide by the value,
  "<TT>!&lt;keyword&gt;</TT>" to find the value to multiple the image from the specified
  keyword in the header, and "<TT>@&lt;file&gt;</TT>" to get the values to multiple the
  images from the specified file.  The scales are normalized by the scale
  for the first image to make the scaling relative to the first image.
  The values in a file must be in the same order as the input images.
  </DD>
  </DL>
  <DL>
  <DT><B>normscale = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='normscale' Line='normscale = yes'>
  <DD>Normalize the scales to the first image scale?
  </DD>
  </DL>
  <DL>
  <DT><B>outscale = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outscale' Line='outscale = yes'>
  <DD>Scale output images?  If yes the output images will be on the system
  defined by the input scale factors.  If no the output is scaled back
  to match the input levels.
  </DD>
  </DL>
  <DL>
  <DT><B>blank = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='blank' Line='blank = 0'>
  <DD>Filter value when all data have been excluded from the calculation.
  </DD>
  </DL>
  <DL>
  <DT><B>storetype = "<TT>real</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='storetype' Line='storetype = "real"'>
  <DD>Internal storage type which may be "<TT>real</TT>" or "<TT>short</TT>".  The short
  integer type saves memory at the cost of rounding.  Unless memory
  is a problem real storage is recommended.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print progress information to the standard output.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <B>RUNMED</B> takes a list of input images (<I>input</I>) and produces
  a set of filtered output images (<I>output</I>).  The output images
  are matched with the input images and the header of the output image
  is that of the matching input image.  The output image may be the
  same as the input image if desired.
  <P>
  Each input image may have an associated pixel mask.  The mask is specified
  by the keyword in the image specified by the <I>inmaskkey</I> parameter.
  The masks must be of a matching size.  This task matches mask pixel with
  image pixels based on the logical pixel coordinates.  In other words, it
  does not take into account any subsection that may have been applied to the
  input images which was not also applied to the mask images.  A non-zero
  mask value identifies pixels to be excluded from the computation of the
  filter value or the mode of the image.
  <P>
  The input images may be scaled (<I>scale</I>) as they are read.
  The scale factors may be normalized relative to the first image in the
  list (<I>normscale</I>).  The scale factors may be given explicitly in a
  file or keyword or computed from an estimate of the mode of the image.
  The mode computation excludes pixels identified by non-zero values in
  the associated input mask.  On output the computed filter value based
  on the set of scaled pixel values maybe scaled back to match that of
  the input image (<I>outscale</I>).
  <P>
  The running filter operates independently on the sequence of pixel
  values across the list of input images at each pixel position.  If an
  input mask is specified then non-zero mask values identify pixel values
  to exclude from the calculations.  The <I>exclude</I> parameter may be
  used to exclude the central image of the window.  This is useful to
  avoid unnatural histograms with a spike at for the output image.
  The filter sorts the sequence of unrejected values in a running window
  (<I>window</I>).
  <P>
  The median is the central value when the number of unrejected values is
  odd and the average of the two central values.  This median may be used
  with the <I>nclip</I> parameter to exclude high outliers in the sorted
  values at each point.  The clipping computes the difference between
  the median and the lowest value, multiplies by the clipping factor,
  and rejects values more than this threshold above the median.  This is
  only done when <I>nclip</I> is greater than zero and there are at least
  3 unrejected values prior to this clipping step.
  <P>
  After the clipping the average, as set by <I>navg</I>, of the central values
  is computed.  Note that an average of one is a median.
  <P>
  The number of central values averaged will be even when the number of
  pixels is even and odd when it is odd.  What is done is that high
  and low values are excluded symmetrically until the number of remaining
  pixels is less than or equal to the specified average but with at least
  one or two values remaining.
  <P>
  The number of values available to the average is odd when no data is
  excluded because the window size must be odd.  When the <I>exclude</I>
  parameter is selected the number of values will be even.  And when pixel
  masks are used the number be anywhere from zero to the window size.
  When all pixels are excluded the filter value is the <I>blank</I> value.
  Also when the ratio output is selected and the filter value used as the
  denominator is zero the <I>blank</I> value is also used.
  <P>
  The output of this task are images of the filter values
  (<I>outtype</I>="<TT>filter</TT>"), the difference of the input image and the
  filter value (<I>outtype</I>="<TT>difference</TT>"), or the ratio of the input
  image and the filter value (<I>outtype</I>="<TT>ratio</TT>").  The difference
  output is useful as a background subtraction for a background that varies
  systematically through the list of images.  When the difference
  is selected the input and filter value are matched by their scale factors
  either in the scaled system (<I>outscale</I>=yes) or in the input
  system (<I>outscale</I>=no).
  <P>
  The <I>exclude</I> option is useful for the background subtraction case.
  Use of this option excludes the input image from the to the filter
  computation value for the matching output.  This insures that the output
  pixel value histogram does not have a spike of zero values when <I>navg</I>
  = 1 and the median pixel value is that of the input image.
  <P>
  An output mask list (<I>masks</I>) may be specified to produce masks which
  contain the number of pixels used in computing the filter value.  This
  is most useful to define regions where no pixels were used and the
  blank value was substituted.  The name of the output mask is recorded
  in the output image header under the keyword specified by the
  <I>outmaskkey</I> parameter.  Note that it is valid to specify the
  output mask keyword to be the same as the input mask keyword.  If this
  is not done the input mask keyword, if present, will remain in the
  output header.
  <P>
  Normally the filter window is centered on each input image within the list.
  In other words there are an equal number of images before and after the
  input image taken from the input list.  However, at the beginning and end
  of the input list, the window spans the first or last <I>window</I> images.
  The filter value will then be the same except that the <I>exclude</I>
  option applies to the particular input image and the difference and
  ratio output types will be based on the particular input image.
  <P>
  This task is designed to be as efficient as possible so that images
  are read only once (or twice if the mode is computed) and added to an
  optimized tree algorithm to avoid completely resorting data as each new
  image is read.  In order to do this it buffers pixel data internally as
  well as having some memory overhead from the tree algorithm.  The memory
  is compressed as much as possible.  The amount of memory required will
  scale with the size of the window, the number of pixels in the images,
  and the storage datatype.  The storage datatype (<I>storetype</I>) may be
  short integer, which is two bytes per pixel, and real, which is four bytes
  per pixel.  If memory limitations are an issue one may chose to use short
  storage which requires of order 75% less memory.  The tradeoff is that
  data will be rounded (not truncated).  In many cases this effect
  will be minor.  Note that even if the input data is integer the pixels
  values may be scaled resulting in fractional scaled values.  The output
  images will be real regardless of the input type.
  <P>
  With sufficiently large images and large windows it is possible this task
  will fail to run requiring the user to make adjustments.  The simplest
  method would be to break the images into smaller pieces and run this task
  on each piece.  Note that input image sections can be used to reduce the
  size of the input images being processed and <B>imtile</B>
  can be use to piece the output back together.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imcombine, rskysub, irproc
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
