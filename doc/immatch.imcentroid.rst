.. _imcentroid:

imcentroid — Compute and print relative shifts for a list of 2-D images
=======================================================================

**Package: immatch**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  imcentroid -- center sources in images, optionally find shifts
  <P>
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  imcentroid input reference coords
  <P>
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <P>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The list of images within which sources are to be centered.  If a
  <I>reference</I> image is specified, imcentroid will calculate the mean
  X and Y shifts between the centered sources within each image and those
  same sources within the reference image.  The input image list
  should normally include the reference image so that its borders are
  used in the calculation of the  overlap region.
  </DD>
  </DL>
  <DL>
  <DT><B>reference = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='reference' Line='reference = ""'>
  <DD>The reference image to which the input images will be aligned.  If
  a reference image is specified the mean X and Y shifts between each of
  the input images and the reference image will be calculated, otherwise
  only the centers for the individual sources will be reported.
  </DD>
  </DL>
  <DL>
  <DT><B>coords</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='coords' Line='coords'>
  <DD>A text file containing the coordinates of the registration objects to
  be centered in each image, one object per line with the x and y
  coordinates in columns one and two respectively.  These coordinates
  should be measured in the frame of the reference image.
  </DD>
  </DL>
  <DL>
  <DT><B>shifts = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='shifts' Line='shifts = ""'>
  <DD>A text file containing the initial estimate for each image of the
  shift in each axis relative to the reference image.  These
  estimates are used to modify the coordinates of the registration
  objects prior to centering.  The format of the file is one image per
  line with the fractional x and y shifts in columns one and two
  respectively.  The sense of the shifts is such that:
  Xshift =Xref - Xin and shift= Yref - Yin. If shifts is undefined,
  a coarse centering pass will be made to attempt to determine
  the initial shifts.
  </DD>
  </DL>
  <DL>
  <DT><B>boxsize = 7</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='boxsize' Line='boxsize = 7'>
  <DD>The size in pixels of the box to use for the final centering, during
  which all the sources in the coords file are recentered in each image
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
  since it is highly data dependent.  Large value should be suspect until
  the final results are checked to see that the centering did not converge
  on the wrong coordinates, although the usual result for an inappropriate
  bigbox size is that the algorithm fails to converge and the task
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
  will halt when this limit is reached or when the desired tolerance
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
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print the centers for the individual objects ?  If verbose is no
  only the shifts relative to the reference coordinates will be reported.
  If no reference image is supplied, verbose is automatically set to yes.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  IMCENTROID measures the X and Y coordinates of a list of sources in a
  list of images and finds the mean X and Y shifts between the input
  images <I>input</I> and a <I>reference</I> image, where the shifts are
  defined as the shifts that should be added to the input image coordinates to
  convert them into the reference coordinates.  The task is meant to
  address the class of two dimensional image registration problems in
  which the images have the same pixel scale, are shifted relative to
  each other by simple translations in each axis, and contain enough high
  signal-to-noise, pointlike sources in common to form good average
  positions.  The basic operation of the task is to find centers for the
  list of registration objects in the coordinate frame of each image and
  then to subtract the corresponding centers found in the reference
  image.  The shifts of the objects are averaged for each image.
  <P>
  A list of the X and Y coordinates of the registration objects should be
  provided in the coordinates file <I>coords</I>.  The registration objects do not
  all have to be common to each frame, rather only that subset of the
  objects that is contained within the bounds of a given image will be
  centered.  Only the objects that are common to both the given image and
  the reference will be used to calculate the shifts.  The coordinates
  should be measured in the frame of the reference image<I>reference</I>.
  If coarse centering is to be done, which is to say, if no <I>shifts</I> file is
  provided, then the first registration source should be separated from
  other sources by at least the maximum expected relative shift.
  <P>
  An initial estimate of the shifts between each of the input images
  <I>input</I> and the reference image <I>reference</I> is required for the
  centering algorithm (a marginal centroid) to work.  This estimate can be
  explicitly supplied in the text file <I>shifts</I> where Xshift = Xref -Xin
  and Yshift = Yref -Y in, or can be generated from the images by measuring
  the relative shift of the first source listed in the coordinates file
  <I>coords</I> for each input image.  This coarse
  centering pass requires that the first source be detached from other
  sources and from the border of each image by a distance that is at
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
  the fine centering pass and should be chosen so as to exclude sky
  background and other sources while including the wings of the point
  spread function.  The sense of the shifts that are calculated is
  consistent with the file supplied to the <I>shifts</I> parameter and
  with that used with the IMSHIFT task.
  <P>
  IMCENTROID may be used with a set of input images which vary in size.
  This can result in vignetting of the calculated overlap region because
  of the nature of tasks such as IMSHIFT to preserve the size of an input
  image.  To visualize this, imagine a large reference image and a single
  small image to be aligned to it, both containing the same registration
  object which is at the center of each image.  IMCENTROID will cause the
  coordinate system of the small image to be shifted such that the object 
  will be positioned at the same pixel location as in the reference.  If
  the shift is performed, a large fraction of the area of the small image
  may be shifted outside of its own borders, whereas the physical overlap
  of the large and small images includes ALL of the pixels of the small
  image.  In the case of such vignetting, IMCENTROID will print a warning
  message and both the vignetted and unvignetted trim sections.  Note
  that the vignetting will not occur if the small image is used as the
  reference image.
  <P>
  The vignetting message may also be printed if the input images are all
  the same size but the reference image is not included in the list.
  This will occur if the sense of the measured shifts in a coordinate are
  all positive or all negative since in this case the border of the
  reference image would have provided one of the limits to the trim
  section.  The reality of this vignetting depends on your point of view.
  <P>
  Note that many of these difficulties are due to the intrinsically fuzzy
  nature of the process of image registration.  This all leads to a few
  guidelines:
  <P>
  <PRE>
      o	Include the reference image in the input image list
  <P>
      o	Use the smallest image as the reference image
  <P>
      o	Choose the reference image such that the input images
          are scattered to either side in the shifts in each axis
  <P>
      o	Align images that are the same size, OR
  <P>
      o	Pad dissimilar sized images with blanks to the largest size
  </PRE>
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Centering algorithm</H3>
  <! BeginSection: 'CENTERING ALGORITHM'>
  <UL>
  <P>
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
  try increasing the tolerance gingerly.  If the sky background is not
  flat, but varies across the image, it can be removed before processing.
  <P>
  </UL>
  <! EndSection:   'CENTERING ALGORITHM'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Calculate the shifts between three images using the first image
  as a reference image and the list of registration star coordinates in
  the file "<TT>x1.coords</TT>".
  <P>
  <PRE>
      cl&gt; imcentroid x1,x2,x3 x1 x1.coords
  </PRE>
  <P>
  2. Calculate the shifts between a list of images contained in the file
  "<TT>imlist</TT>":
  <P>
  <PRE>
      pr&gt; imcentroid @imlist x1 x1.coords
  </PRE>
  <P>
  3. Perform the centering, but don't calculate the shifts, i.e., don't
  supply a reference image.  Note that the <I>input</I> list of shifts,
  or a coarse centering pass are still needed:
  <P>
  <PRE>
      pr&gt; imcentroid @imlist "" x1.coords
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  The coarse centering portion of the algorithm can be fooled if the
  first source on the list is not well separated from other sources, or
  if the first source has a low signal to noise ratio, or if there is a
  complicated shape to the background.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imalign, imshift, xregister, geomap, geotran
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'CENTERING ALGORITHM' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
