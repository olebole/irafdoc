mkskycor — Make sky illumination correction images
==================================================

**Package: ccdred**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>mkskycor (Feb88)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.imred.ccdred</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>mkskycor (Feb88)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>mkskycor</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  mkskycor -- Make sky iillumination correction images
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  mkskycor input output
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of input images for making sky iillumination correction images.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>List of output flat field iillumination correction images.  If none is
  specified or if the name is the same as the input image then the output
  image replaces the input image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ccdtype">ccdtype = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ccdtype' Line='ccdtype = ""'>
  <DD>CCD image type to select from the input images.  If none is specified
  then all types are used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xboxmin">xboxmin = 5, xboxmax = 0.25, yboxmin = 5, yboxmax = 0.25</A></B></DT>
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
  <DT><B><A NAME="l_clip">clip = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='clip' Line='clip = yes'>
  <DD>Clean the input images of objects?  If yes then a clipping algorithm is
  used to detect and exclude objects from the smoothing.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_lowsigma">lowsigma = 2.5, highsigma = 2.5</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lowsigma' Line='lowsigma = 2.5, highsigma = 2.5'>
  <DD>Sigma clipping thresholds above and below the smoothed iillumination.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ccdproc">ccdproc (parameter set)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ccdproc' Line='ccdproc (parameter set)'>
  <DD>CCD processing parameters.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The large scale iillumination pattern of the input images, generally
  blank sky calibration images, is determined by heavily smoothing
  the image using a moving "<TT>boxcar</TT>" average.  The effects of objects in
  the image may be minimized by using a sigma clipping algorithm to
  detect and exclude the objects from the average.  This
  iillumination image is applied by <B>ccdproc</B> to CCD images to remove
  the iillumination pattern.
  <P>
  The input images are automatically processed up through flat field
  calibration before computing the iillumination.  The iillumination
  correction is that needed to make the processed images flat
  over large scales.  The input images are generally blank sky calibration
  images which have the same iillumination and instrumental effects
  as the object observations.  Object images may be used but removal
  of the objects may not be very good; particularly large, bright objects.
  For further discussion of flat fields and iillumination corrections
  see <B>flatfields</B>.
  <P>
  You will notice that when you process images with an iillumination
  correction you are dividing each image by a flat field calibration and
  an iillumination correction.  If the iillumination corrections are not
  done as a later step but at the same time as the rest of the processing
  one will get the same calibration by multiplying the flat field by the
  iillumination correction and using this product alone as the flat
  field.  This approach has the advantage of one less calibration image
  and two less computations (scaling and dividing the iillumination
  correction).  Such an image, called a <I>sky flat</I>, may be created by
  <B>mkskyflat</B> as an alternative to this task.
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
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. The two examples below make an iillumination image from a blank sky image,
  "<TT>sky017</TT>".  In the first example a separate iillumination image is created
  and in the second the iillumination image replaces the sky image.
  <P>
  <PRE>
      cl&gt; mkskycor sky017 Illum
      cl&gt; mkskycor sky017 sky017
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  ccdproc, flatfields, mkillumcor, mkillumflat, mkskyflat
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>