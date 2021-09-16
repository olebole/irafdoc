.. _mkskyflat:

mkskyflat — Make sky corrected flat field images
================================================

**Package: quadred**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  mkskyflat -- Make sky corrected flat field images
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  mkskyflat input output
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of blank sky images to be used to create sky corrected flat field
  calibration images.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>List of output sky corrected flat field calibration images (called
  sky flats).  If none is specified or if the name is the same as the
  input image then the output image replaces the input image.
  </DD>
  </DL>
  <DL>
  <DT><B>ccdtype = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ccdtype' Line='ccdtype = ""'>
  <DD>CCD image type to select from the input images.
  </DD>
  </DL>
  <DL>
  <DT><B>xboxmin = 5, xboxmax = 0.25, yboxmin = 5, yboxmax = 0.25</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xboxmin' Line='xboxmin = 5, xboxmax = 0.25, yboxmin = 5, yboxmax = 0.25'>
  <DD>Minimum and maximum smoothing box size along the x and y axes.  The
  minimum box size is used at the edges and grows to the maximum size in
  the middle of the image.  This allows the smoothed image to better
  represent gradients at the edge of the image.  If a size is less then 1
  then it is interpreted as a fraction of the image size.  If a size is
  greater than or equal to 1 then it is the box size in pixels.  A size
  greater than the size of image selects a box equal to the size of the
  image.
  </DD>
  </DL>
  <DL>
  <DT><B>clip = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='clip' Line='clip = yes'>
  <DD>Clean the input images of objects?  If yes then a clipping algorithm is
  used to detect and exclude objects from the smoothing.
  </DD>
  </DL>
  <DL>
  <DT><B>lowsigma = 2.5, highsigma = 2.5</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lowsigma' Line='lowsigma = 2.5, highsigma = 2.5'>
  <DD>Sigma clipping thresholds above and below the smoothed iillumination.
  </DD>
  </DL>
  <DL>
  <DT><B>ccdproc (pset)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ccdproc' Line='ccdproc (pset)'>
  <DD>CCD processing parameter set.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  A sky corrected flat field calibration image, called a sky flat, is a
  flat field that when applied to observations of the sky have no large
  scale gradients.  Flat field images are generally obtained by exposures
  to lamps either illuminating the telescope field or a surface in the dome
  at which the telescope is pointed.  Because the detector is not illuminated
  in the same way as an observation of the sky there may be large
  scale iillumination patterns introduced into the observations with such
  a flat field.  To correct this type of flat field a blank sky observation
  (which has been divided by the original flat field) is heavily smoothed
  to remove the noise leaving only the residual large scale iillumination
  pattern.  This iillumination pattern is divided into the original flat
  field to remove this residual.
  <P>
  The advantage of creating a sky flat field is that when processing
  the observations no additional operations are required.  However,
  if the observations have already been processed with the original
  flat field then the residual iillumination pattern of blank sky
  calibration images may be created as an iillumination correction
  to be applied by <B>ccdproc</B>.  Such a correction is created by the
  task <B>mkskycor</B>.  If a good blank sky image is not
  available then it may be desirable to remove the iillumination pattern
  of the flat field image using <B>mkillumflat</B> or <B>mkillumcor</B>
  provided the sky observations are truly uniformly illuminated.
  For more on flat fields and iillumination corrections see <B>flatfields</B>.
  <P>
  The input, blank sky images are first processed, based on the
  <B>ccdproc</B> parameters, if needed.  These parameters also determine
  the flat field image to be used in making the sky flat.  The residual
  iillumination pattern is determined by heavily smoothing the image using
  a moving "<TT>boxcar</TT>" average.  The effects of objects in the input image
  may be minimized by using a sigma clipping algorithm to detect and
  exclude the objects from the average.  The output image is ratio of the
  flat field image, for the same subset as the input image, to the
  residual iillumination pattern determined from the processed blank sky
  input image.  The iillumination pattern is normalized by its mean to
  preserve the mean level of the flat field image.
  <P>
  The smoothing algorithm is a moving average over a two dimensional
  box.  The algorithm is unconvential in that the box size is not fixed.
  The box size is increased from the specified minimum at the edges to
  the maximum in the middle of the image.  This permits a better estimate
  of the background at the edges, while retaining the very large scale
  smoothing in the center of the image.  Note that the sophisticated
  tools of the <B>images</B> package may be used for smoothing but this
  requires more of the user and, for the more sophisticated smoothing
  algorithms such as surface fitting, more processing time.
  <P>
  Blank sky images may not be completely blank so a sigma clipping
  algorithm may be used to detect and exclude objects from the
  iillumination pattern.  This is done by computing the rms of the image
  lines relative to the smoothed background and excluding points
  exceeding the specified threshold factors times the rms.  This is done
  before each image line is added to the moving average, except for the
  first few lines where an iterative process is used.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Two examples in which a new image is created and in which the
  input sky images are converted to sky flats are:
  <P>
  <PRE>
      cl&gt; mkskyflat sky004 Skyflat
      cl&gt; mkskyflat sky* ""
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  ccdproc, flatfields, mkfringecor, mkillumcor, mkillumflat, mkskycor
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
