mkillumcor — Make flat field illumination correction images
===========================================================

**Package: ccdred**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>mkillumcor (Oct88)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.imred.ccdred</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>mkillumcor (Oct88)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>mkillumcor</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  mkillumcor -- Make flat field iillumination correction images
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  mkillumcor input output
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of input images for making flat field iillumination correction images.
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
  <DT><B><A NAME="l_ccdtype">ccdtype = "<TT>flat</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ccdtype' Line='ccdtype = "flat"'>
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
  used to detect and exclude deviant points from the smoothing.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_lowsigma">lowsigma = 2.5, highsigma = 2.5</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lowsigma' Line='lowsigma = 2.5, highsigma = 2.5'>
  <DD>Sigma clipping thresholds above and below the smoothed iillumination.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_divbyzero">divbyzero = 1.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='divbyzero' Line='divbyzero = 1.'>
  <DD>The iillumination correction is the inverse of the smoothed flat field.
  This may produce division by zero.  A warning is given if division
  by zero takes place and the result (the iillumination correction value)
  is replaced by the value of this parameter.
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
  First, the input flat field images are automatically processed if
  needed.  Then, the large scale iillumination pattern of the images is
  determined by heavily smoothing them using a moving "<TT>boxcar</TT>" average.
  The iillumination correction, the inverse of the iillumination pattern,
  is applied by <B>ccdproc</B> to CCD images to remove the iillumination
  pattern introduced by the flat field.  The combination of the flat
  field calibration and the iillumination correction based on the flat
  field is equivalent to removing the iillumination from the flat field
  (see <B>mkillumflat</B>).  This two step calibration is generally used
  when the observations have been previously flat field calibrated.  This
  task is closely related to <B>mkskycor</B> which determines the
  iillumination correction from a blank sky image; this is preferable to
  using the iillumination from the flat field as it corrects for the
  residual iillumination error.  For a general discussion of the options
  for flat fields and iillumination corrections see <B>flatfields</B>.
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
  To minimize the effects of bad pixels a sigma clipping algorithm is
  used to detect and reject these pixels from the iillumination.  This is
  done by computing the rms of the image lines relative to the smoothed
  iillumination and excluding points exceeding the specified threshold
  factors times the rms.  This is done before each image line is added to
  the moving average, except for the first few lines where an iterative
  process is used.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. The example below makes an iillumination correction image from the
  flat field image, "<TT>flat017</TT>".
  <P>
      cl&gt; mkillumcor flat017 Illum
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  ccdproc, flatfields, mkillumflat, mkskycor, mkskyflat
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>