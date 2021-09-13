.. _imalign:

imalign — Align and register 2-D images using a reference pixel list
====================================================================

**Package: immatch**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  imalign -- register a list of images by computing relative object shifts
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  imalign input reference coords output
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The input images to be shifted and trimmed.  The input image list should
  contain the reference image so that its borders are
  used in the computation of the overlap region.
  </DD>
  </DL>
  <DL>
  <DT><B>reference</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='reference' Line='reference'>
  <DD>The reference image to which the input images will be aligned. 
  </DD>
  </DL>
  <DL>
  <DT><B>coords</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='coords' Line='coords'>
  <DD>A text file containing the reference image coordinates of the registration
  objects to be centered in each image, one object per line with the x and y
  coordinates in columns one and two respectively.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>The output images. 
  </DD>
  </DL>
  <DL>
  <DT><B>shifts = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='shifts' Line='shifts = ""'>
  <DD>A text file containing the initial estimate for each image of the
  shift in each axis relative to the reference image.  These
  estimates are used to modify the coordinates of the registration
  objects prior to centering.  The format of the file is one image per
  line with the x and y shifts in columns one and two respectively.
  The sense of the shifts is such that: <I>Xshift=Xref-Xin</I> and
  <B>Yshift=Yref-Yin</B>.  If <I>shifts</I> is null, a coarse centering
  pass will be made to attempt to determine the initial shifts.
  </DD>
  </DL>
  <DL>
  <DT><B>boxsize = 7</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='boxsize' Line='boxsize = 7'>
  <DD>The size in pixels of the box to use for the final centering, during
  which all the sources in <I>coords</I> are recentered in each image
  using the initial estimate of the relative shift for each image.
  Care should be taken to choose an appropriate value for this parameter,
  since it is highly data dependent.
  </DD>
  </DL>
  <DL>
  <DT><B>bigbox = 11</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='bigbox' Line='bigbox = 11'>
  <DD>The size in pixels of the box to use for coarse centering.  The coarse
  pass through the centering algorithm is made with the box centered at
  the nominal position of the first source in the coordinate list.
  Coarse centering is performed only if the shifts file is undefined.
  Care should be taken to choose an appropriate value for this parameter,
  since it is highly data dependent.  Large values should be suspect until
  the final results are checked to see that the centering did not converge
  on the wrong coordinates, although the usual result for an inappropriate
  <I>bigbox</I> size is that the algorithm fails to converge and the task
  aborts.
  </DD>
  </DL>
  <DL>
  <DT><B>negative = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='negative' Line='negative = no'>
  <DD>Are the features negative ?
  </DD>
  </DL>
  <DL>
  <DT><B>background = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='background' Line='background = INDEF'>
  <DD>The absolute reference level for the marginal centroid calculation.
  If background is INDEF, this is set to the mean value (between the
  thresholds) of the individual sources.
  </DD>
  </DL>
  <DL>
  <DT><B>lower = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lower' Line='lower = INDEF'>
  <DD>The lower threshold for the data.  Individual pixels less than this
  value will be given zero weight in the centroids.
  </DD>
  </DL>
  <DL>
  <DT><B>upper = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='upper' Line='upper = INDEF'>
  <DD>The upper threshold for the data.  Individual pixels greater than this
  value will be given zero weight in the centroids.
  </DD>
  </DL>
  <DL>
  <DT><B>niterate = 3</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='niterate' Line='niterate = 3'>
  <DD>The maximum number of centering iterations to perform.  The centering
  will halt when this limit is reached or when the desired Itolerance
  is achieved.
  </DD>
  </DL>
  <DL>
  <DT><B>tolerance = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='tolerance' Line='tolerance = 0'>
  <DD>The tolerance for convergence of the centering algorithm.  This is the
  integral shift of the centering box from one iteration to the next.
  </DD>
  </DL>
  <DL>
  <DT><B>maxshift = INDEFR</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maxshift' Line='maxshift = INDEFR'>
  <DD>The maximum permitted difference between the predicted shift and the
  the computed shift for each object. Objects with shifts greater than
  maxshift are ignored. If maxshift is undefined no shift checking is done.
  </DD>
  </DL>
  <DL>
  <DT><B>shiftimages = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='shiftimages' Line='shiftimages = yes'>
  <DD>If shiftimages is yes, the IMSHIFT task will be used to align the
  images.  If shiftimages is no, the images will not be aligned, but
  the coordinates will still be centered.
  </DD>
  </DL>
  <DL>
  <DT><B>interp_type = "<TT>spline3</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interp_type' Line='interp_type = "spline3"'>
  <DD>The interpolation function used by the IMSHIFT task.
  </DD>
  </DL>
  <DL>
  <DT><B>boundary_type = "<TT>constant</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='boundary_type' Line='boundary_type = "constant"'>
  <DD>The boundary extension type used by the IMSHIFT task.
  </DD>
  </DL>
  <DL>
  <DT><B>constant = 0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='constant' Line='constant = 0.'>
  <DD>The constant used by the IMSHIFT task if <I>boundary_type</I> is "<TT>constant</TT>". 
  </DD>
  </DL>
  <DL>
  <DT><B>trimimages = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='trimimages' Line='trimimages = yes'>
  <DD>If trimimages is yes, the output images will be trimmed to
  include only the region over which they all overlap.  The
  trim section that is actually used may differ slightly from that
  reported by IMCENTROID, due to a correction applied to compensate for
  the boundary extension "<TT>contamination</TT>" near the edges of the images.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print the centers, shifts, and trim section?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  IMALIGN measures the X and Y axis shifts between a list of input images
  <I>input</I> and a reference image <I>reference</I>, registers the
  input images to the reference image using the computed shifts,
  and trims the input images to a common overlap region.
  The task is meant to address the class of two dimensional image
  registration problems in which the images have the same pixel scale,
  are shifted relative to each other by simple x and y translations, and contain
  enough high signal / noise, pointlike sources in common to compute good
  average positions.  The basic operation of the task is to find centers
  for the list of registration objects or features in the coordinate
  frame of each image and then to subtract the corresponding centers
  found in the reference image.  The shifts of the registration objects
  are averaged for each image.
  <P>
  IMALIGN is a simple script front end for IMCENTROID, which computes the
  shifts, IMSHIFT, which shifts the images, and
  IMCOPY, which performs the trimming.
  <P>
  A list of the X and Y coordinates of the registration objects should be
  provided via the <I>coords</I> parameter.  The registration objects do not
  all have to be common to each frame; only that subset of the
  objects that is contained within the bounds of a given image will be
  centered.  Only the objects that are common to both the given image and
  the reference will be used to calculate the shifts.  The coordinates
  must be measured in the frame of the reference image.  If coarse
  centering is to be done, which is to say, if no <I>shifts</I> file is
  provided, then the first registration source should be separated from
  other sources by at least the maximum expected relative shift.
  <P>
  An initial estimate of the shifts between each of the input images and
  the reference image is required for the centering algorithm (a marginal
  centroid) to work.  This estimate can be explicitly supplied in the file
  <I>shifts</I> (<I>Xshift=Xref-Xin</I> and <I>Yshift=Yref-Yin</I>) or can
  be generated from the images by measuring the relative shift of the
  first source listed in the coords file for each image.  This coarse
  centering pass requires that the first source be detached from other
  sources and from the border of each image, by a distance that is at
  least the maximum shift between the reference and input image.  This
  source should be pointlike and have a high signal to noise ratio.  The
  value of the <I>bigbox</I> parameter should be chosen to include the
  location of the source in each of the images to be aligned while
  excluding other sources.  Large values of <I>bigbox</I> should be held
  suspect until the final convergence of the centering algorithm is
  verified, although given a small value for the <I>tolerance</I>, the
  quality of the final centers is independent of the estimate for the
  initial shifts.  Better convergence may also be obtained by increasing
  the <I>niterate</I> parameter, although the default value of three
  should work for most cases.  <I>Niterate</I> should be kept small to
  avoid runaway.
  <P>
  The <I>boxsize</I> parameter controls the size of the centering box for
  the fine centering passes and should be chosen so as to exclude sky
  background and other sources while including the wings of the point
  spread function.  The sense of the shifts that are calculated is
  consistent with the file supplied to the <I>shifts</I> parameter and
  with that used with the IMSHIFT task.
  <P>
  If <I>shiftimages</I> is yes the images will actually be shifted using
  the IMSHIFT task.  Note that if <I>interp_type</I> is "<TT>nearest</TT>" the
  effect on the images is the same as if the shifts were rounded to
  integral values.  In this case, the pixels will be shifted without
  interpolation.  This can be used for data in which it is more important
  to preserve the pixel values than it is to achieve perfect
  registration.
  <P>
  If <I>trimimages</I> is yes, the output images will be trimmed to
  include only the region over which they all overlap.  The trim section
  that is actually used may differ slightly from that reported by
  IMCENTROID.  A one or two pixel correction may be applied to each edge
  to compensate for the boundary extension "<TT>contamination</TT>" due to
  multi-pixel (e.g., <I>interp_type</I> = poly5) interpolation near the
  edges of the images.
  <P>
  IMALIGN may be used with a set of <I>images</I> which vary in size.
  This can result in vignetting of the calculated overlap region because
  of the nature of the IMSHIFT task to preserve the size of an input
  image.  To visualize this, imagine a large reference image and a single
  small image to be aligned to it, both containing the same registration
  object which is at the center of each image.  IMALIGN will cause the
  small image to be shifted such that the object is positioned at the same
  pixel location as in the reference.  In performing the shift, a large
  fraction of the area of the small image may be shifted outside of its
  own borders, whereas the physical overlap of the large and small images
  includes ALL of the pixels of the small image.  In the case of such
  vignetting, IMALIGN will print a warning message and refuse to proceed
  with the trimming although the vignetting will occur whether or not the
  images are trimmed.  Note that the vignetting will not occur if the
  small image is used as the <I>reference</I>.
  <P>
  The vignetting message may also be printed if the <I>images</I> are all
  the same size but the <I>reference</I> is not included in the list.
  This will occur if the sense of the measured shifts in a coordinate are
  all positive or all negative since in this case the border of the
  <I>reference</I> would have provided one of the limits to the trim
  section.  The reality of this vignetting depends on your point of view.
  <P>
  Trimming will also not be performed if the entire overlap region vanishes.
  <P>
  Note that many of these difficulties are due to the intrinsically fuzzy
  nature of the process of image registration.  This all leads to a few
  "<TT>rules of thumb</TT>":
  <P>
  <PRE>
      o	Include the reference image in the input image list
  <P>
      o	Use the smallest image as the reference image
  <P>
      o	Choose the reference image such that the input images are
  	scattered to either side in the shifts in each axis
  <P>
      o	Align images that are the same size, OR
  <P>
      o	Pad dissimilar sized images with blanks to
  	the largest size and disable trimming
  </PRE>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Centering algorithm</H3>
  <! BeginSection: 'CENTERING ALGORITHM'>
  <UL>
  The algorithm is a "<TT>marginal</TT>" centroid in which the fit for each axis
  is performed separately upon a vector created by collapsing the
  centering box perpendicular to that axis.  The centroid is calculated
  with respect to the level specified by <I>background</I>.  If
  <I>background</I> is INDEF, the reference level for each source in each
  image is the local mean for those pixels that lie between the
  <I>lower</I> and <I>upper</I> thresholds.  The thresholds are set to the
  local data minimum or maximum if <I>lower</I> or <I>upper</I>,
  respectively, are INDEF.  If <I>negative</I> is yes, than the marginal
  vector will be inverted before being passed to the centroid algorithm.
  <P>
  The maximum number of centering iterations and the tolerance for
  convergence are controlled by <I>niterate</I> and <I>tolerance</I>.  Note
  that the tolerance is an integer value that represents the maximum
  movement of the centering box between two successive iterations.  The
  default value of 0 requires that the centroid lie within the center
  pixel of the centering box which is <I>boxsize</I> in extent (note that
  <I>boxsize</I> must be an odd number).  This should normally be the case
  for bright, circularly symmetric point sources in images with a flat
  sky background.  If the registration sources are not circular symmetric
  try increasing the tolerance gingerly.  A sky level that varies across
  the image should be removed before processing.  The centering and
  calculation of the shifts may be performed with <I>shiftimages</I> = no
  (or directly with IMCENTROID) and the calculated shifts applied to the
  images directly with IMSHIFT.
  <P>
  </UL>
  <! EndSection:   'CENTERING ALGORITHM'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Align three images to the first using the list of registration star
  coordinates in the file "<TT>x1.coords</TT>".
  <P>
  <PRE>
      cl&gt; imalign x1,x2,x3 x1 x1.coords x1.out,x2.out,x3.out
  </PRE>
  <P>
  2. Align a list of images contained in the file "<TT>imlist</TT>", overwriting the
  original images with the shifted and trimmed images:
  <P>
  <PRE>
      cl&gt; imalign @imlist x1 x1.coords @imlist
  </PRE>
  <P>
  3. Align the images leaving the output images the same size as the input
  images:
  <P>
  <PRE>
      cl&gt; imalign @imlist x1 x1.coords @outlist trimimages-
  </PRE>
  <P>
  4. Perform the centering but not the shifts:
  <P>
  <PRE>
      cl&gt; imalign @imlist x1 x1.coords shiftimages-
  </PRE>
  <P>
  5. Perform the centering, but don't calculate the shifts at all,
  and don't shift the image.
  <P>
  <PRE>
      pr&gt; imalign @imlist "" x1.coords shiftimages-
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  The images being shifted must be in the current directory.
  <P>
  The coarse centering portion of the algorithm can be fooled if the
  first source on the list is not well separated from other sources, or
  if the first source has a low signal to noise ratio, or if there is a
  complicated shape to the background.
  <P>
  The task can produce output images that do not contain the entire
  overlap region.  This can only occur if the images are of varying sizes.
  This behavior is caused by the action of the IMSHIFT task to preserve the
  size of an input image, thus implicitly "<TT>trimming</TT>" the image.  A work
  around is to use IMCOPY to place the images into subsections of blank
  images that are the size (in each dimension) of the largest image(s)
  and use IMALIGN with <I>trimimages</I> set to no.  The borders of the output
  images can be trimmed manually.  This is discussed above in more detail.
  <P>
  If <I>images</I> does not contain the <I>reference</I> and <I>trimimages</I>
  is set to yes then the set of shifted and trimmed images may no longer
  be aligned to the reference.  This occurs because any place holder
  pixels at the bottom and left edges of the images will be trimmed off.
  This is also discussed above.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imcentroid, center, imshift, geomap, geotran
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'CENTERING ALGORITHM' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
