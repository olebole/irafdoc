mkillumflat — Make illumination corrected flat fields
=====================================================

**Package: quadred**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>mkillumflat (Oct88)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.imred.ccdred</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>mkillumflat (Oct88)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>mkillumflat</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  mkillumflat -- Make illumination corrected flat fields
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  mkillumflat input output
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of input flat field images to be illumination corrected.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>List of output illumination corrected flat field images.
  If none is specified or if the name is the same as the
  input image then the output image replaces the input image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ccdtype">ccdtype = "<TT>flat</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ccdtype' Line='ccdtype = "flat"'>
  <DD>CCD image type to select from the input images.
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
  <DD>Sigma clipping thresholds above and below the smoothed illumination.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_divbyzero">divbyzero = 1.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='divbyzero' Line='divbyzero = 1.'>
  <DD>The illumination flat field is the ratio of the flat field to a
  smoothed flat field.  This may produce division by zero.  A warning is
  given if division by zero takes place and the result (the illumination
  corrected flat field value) is replaced by the value of this
  parameter.
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
  First, the input flat field images are processed as needed.  Then the
  large scale illumination pattern of the images is removed.  The
  illumination pattern is determined by heavily smoothing the image using
  a moving "<TT>boxcar</TT>" average.  The output image is the ratio of the input
  image to the illumination pattern.  The illumination pattern is
  normalized by its mean to preserve the mean level of the input image.
  <P>
  When this task is applied to flat field images only the small scale
  response effects are retained.  This is appropriate if the flat field
  images have illumination effects which differ from the astronomical
  images and blank sky images are not available for creating sky
  corrected flat fields.  When a high quality blank sky image is
  available the related task <B>mkskyflat</B> should be used.  Note that
  the illumination correction, whether from the flat field or a sky
  image, may be applied as a separate step by using the task
  <B>mkillumcor</B> or <B>mkskycor</B> and applying the illumination
  correction as a separate operation in <B>ccdproc</B>.  However, creating
  an illumination corrected flat field image before processing is more
  efficient since one less operation per image processed is needed.  For
  more discussion about flat fields and illumination corrections see
  <B>flatfields</B>.
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
  used to detect and reject these pixels from the illumination.  This is
  done by computing the rms of the image lines relative to the smoothed
  illumination and excluding points exceeding the specified threshold
  factors times the rms.  This is done before each image line is added to
  the moving average, except for the first few lines where an iterative
  process is used.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Two examples in which a new image is created and in which the
  input flat fields are corrected in place are:
  <P>
  <PRE>
      cl&gt; mkllumflat flat004 FlatV
      cl&gt; mkillumflat flat* ""
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  ccdproc, flatfields, mkfringecor, mkillumcor, mkskycor, mkskyflat
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>