.. _mkfringecor:

mkfringecor — Make fringe correction images from sky images
===========================================================

**Package: quadred**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  mkfringecor -- Make fringe correction images from sky images
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  mkfringecor input output
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of input images for making fringe correction images.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>List of output fringe correction images.  If none is
  specified or if the name is the same as the input image then the output
  image replaces the input image.
  </DD>
  </DL>
  <DL>
  <DT><B>ccdtype = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ccdtype' Line='ccdtype = ""'>
  <DD>CCD image type to select from the input images.  If none is specified
  then all types are used.
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
  <DD>Sigma clipping thresholds above and below the smoothed background.
  </DD>
  </DL>
  <DL>
  <DT><B>ccdproc (parameter set)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ccdproc' Line='ccdproc (parameter set)'>
  <DD>CCD processing parameters.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The input blank sky images are automatically processed up through the
  iillumination correction before computing the fringe correction images.
  The fringe corrections are subset dependent.
  The slowly varying background is determined and subtracted leaving only
  the fringe pattern caused by the sky emission lines.  These fringe images
  are then scaled and subtracted from the observations by <B>ccdproc</B>.
  The background is determined by heavily smoothing the image using a
  moving "<TT>boxcar</TT>" average.  The effects of the objects and fringes in the
  image is minimized by using a sigma clipping algorithm to detect and
  exclude them from the average.  Note, however, that objects left in the
  fringe image will affect the fringe corrected observations.  Any objects
  in the sky image should be removed using <B>skyreplace</B> (not yet
  available).
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
  To minimize the effects of the fringes and any objects in the blank sky
  calibration images a sigma clipping algorithm is used to detect and
  exclude features from the background.  This is done by computing the
  rms of the image lines relative to the smoothed background and
  excluding points exceeding the specified threshold factors times the
  rms.  This is done before each image line is added to the moving
  average, except for the first few lines where an iterative process is
  used.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. The two examples below make an fringe correction image from a blank
  sky image, "<TT>sky017</TT>".  In the first example a separate fringe
  image is created and in the second the fringe image replaces the
  sky image.
  <P>
  <PRE>
      cl&gt; mkskycor sky017 Fringe
      cl&gt; mkskycor sky017 frg017
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  ccdproc
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
