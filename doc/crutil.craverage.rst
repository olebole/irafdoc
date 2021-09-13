craverage — Detect CRs against average and avoid objects
========================================================

**Package: crutil**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>craverage (Apr98)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.imred.crutil</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>craverage (Apr98)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>craverage</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  craverage -- detect CRs and objects using average filter
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_synopsis">SYNOPSIS</A></H2>
  <! BeginSection: 'SYNOPSIS'>
  <UL>
  <B>Craverage</B> detects cosmic rays and objects using a moving block
  average filter with the central pixel plus some number of additional high
  pixels  excluded and a median of an annulus around the block average box.
  It avoids identification of the cores of objects as cosmic rays by
  excluding pixels within the detected objects as cosmic ray candidates.
  </UL>
  <! EndSection:   'SYNOPSIS'>
  <H2><A NAME="s_usage___">USAGE   </A></H2>
  <! BeginSection: 'USAGE   '>
  <UL>
  <PRE>
  craverage input output
  </PRE>
  </UL>
  <! EndSection:   'USAGE   '>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of input images in which to detect cosmic rays and objects.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>List of output images in which cosmic rays are replaced by the block average
  value excluding the cosmic ray.  If no output image name is given then
  no output image will be created.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_crmask">crmask = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='crmask' Line='crmask = ""'>
  <DD>List of input and output cosmic ray and object masks.  If the mask exists
  then the mask values are used to exclude data pixels from the calculations
  and zero mask values are candidates for cosmic rays or objects.
  Detected cosmic rays and objects are identified in the mask with values
  given by the <I>crval</I> and <I>objval</I> parameters.  If no output cosmic
  ray mask is given then no mask will be created.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_average">average = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='average' Line='average = ""'>
  <DD>List of output block average filtered images.  If no image name is given
  then no image will be created.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_sigma">sigma = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sigma' Line='sigma = ""'>
  <DD>List of output sigma images.  If no image name is given then no image
  will be created.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B><A NAME="l_navg">navg = 5 (minimum of 3)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='navg' Line='navg = 5 (minimum of 3)'>
  <DD>Square block average filter size given as the number of pixels along an
  edge.  The value will be rounded up to an odd value to be symmetrical
  around the center pixel excluded from the average.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nrej">nrej = 0 (minimum of 0)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nrej' Line='nrej = 0 (minimum of 0)'>
  <DD>Number of additional highest pixels to exclude, in addition to the
  central pixel, in the block average.  The value should be small but it
  is needed to deal with cosmic rays that are bigger than a single pixel.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nbkg">nbkg = 5 (minimum of 1)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nbkg' Line='nbkg = 5 (minimum of 1)'>
  <DD>Background annulus width around the box average filter in pixels.  The
  median of the pixels in this annulus is used to estimate the background.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nsig">nsig = 25 (minimum of 10)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nsig' Line='nsig = 25 (minimum of 10)'>
  <DD>Square box size for empirical sigma estimates given as the number of
  pixels along an edge.  The sigma is estimated using percentile points
  of the pixels in the box.  The size of the box should contain
  of order 100 pixels or more.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_var0">var0 = 0., var1 = 0., var2 = 0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='var0' Line='var0 = 0., var1 = 0., var2 = 0.'>
  <DD>Variance coefficients for the variance model.  The variance model is
  <P>
  <PRE>
      variance = var0 + var1 * data + var2 * data^2
  </PRE>
  <P>
  where data is the maximum of zero and the average filtered pixel value and
  the variance is in data numbers.  All the coefficients must be positive or
  zero.  If they are all zero then empirical data sigmas are estimated by a
  percentile method in boxes of size given by <I>nsig</I>.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B><A NAME="l_crval">crval = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='crval' Line='crval = 1'>
  <DD>Mask value for detected cosmic rays.  It is legal for the value to be
  zero to not mark the cosmic rays in the output mask.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_lcrsig">lcrsig = 10., hcrsig = 5.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lcrsig' Line='lcrsig = 10., hcrsig = 5.'>
  <DD>Low and high sigma factors for detecting cosmic rays.  These factors
  multiply the computed or estimated sigma at each pixel and these threshold
  values are compared to the difference between the candidate pixel and the
  block average filter value (average of box around the pixel).  This only
  applies to pixels where the block average filter value is within a
  specified threshold of the background estimate; i.e. the average value is
  not considered as part of an object.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_crgrow">crgrow = 0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='crgrow' Line='crgrow = 0.'>
  <DD>Cosmic ray growing radius.  Pixels detected and marked in the output cosmic
  ray mask by the <I>crval</I> value are increased in size in the mask (but
  not replaced in the output image) by also flagging all zero valued mask
  pixels within this specified radius with the cosmic ray mask value.  This
  is done after the detection phase is complete.  The separation between
  pixels is the distance between pixel centers computed as a real value.
  Note a value of at least one is required to affect other mask pixels.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B><A NAME="l_objval">objval = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='objval' Line='objval = 0'>
  <DD>Mask value for detected objects.  It is legal for the value to be
  zero to not mark the objects in the output mask.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_lobjsig">lobjsig = 10., hobjsig = 5.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lobjsig' Line='lobjsig = 10., hobjsig = 5.'>
  <DD>Low and high sigma factors for detecting objects.  These factors multiply
  the computed or estimated sigma at each pixel and these threshold values
  are compared to the difference between the block average filter value and
  the background annulus median.  If the values are made very large then
  object detection can be eliminated and cosmic rays will be detected
  everywhere.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_objgrow">objgrow = 0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='objgrow' Line='objgrow = 0.'>
  <DD>Object detection growing radius.  Pixels detected and marked in the output
  mask by the <I>objval</I> value are increased in size in the mask by also
  flagging all zero valued mask pixels within this specified radius with the
  cosmic ray mask value.  This is done after the detection phase is complete
  and so object grown pixels are not used in excluding cosmic ray
  candidates.  The separation between pixels is the distance between pixel
  centers computed as a real value.  Note a value of at least one is
  required to affect other mask pixels.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <B>Craverage</B> detects cosmic rays and objects using a moving block
  average filter with the central pixel and a specified number of additional
  highest pixels excluded and a median of an annulus around the block average
  box.  It avoids identification of the cores of objects as cosmic rays by
  excluding pixels within the detected objects as cosmic ray candidates.
  <P>
  The block average filter computes the average of pixels in a box with the
  central or target pixel excluded.  In addition the <I>nrej</I> parameter can
  be used to exclude that number of highest remaining pixels as possible
  contamination from cosmic rays which are larger than one pixel or possibly
  a very nearby additional cosmic ray.  The <I>nrej</I> value should be kept
  small relative to the total number of pixels in the average so that the
  average will still be elevated over the median in real underlying objects.
  The resulting average is used as the prediction for the value of the target
  pixel.  The median of the pixels in a square background annulus around the
  block average box provides the prediction for the background at the target
  pixel.
  <P>
  The target pixel is considered part of an object if the difference between
  the average value and the median background exceeds a specified threshold.
  If the pixel is NOT considered to be part of an object then if the
  difference between the pixel value and the average value exceeds a
  different specified threshold it is identified as a cosmic ray.
  <P>
  The thresholds are defined in terms of sigma factors, which may be
  different for positive and negative deviations and for object and
  cosmic ray identification.  The sigma factors multiply an estimate
  for the statistical sigma of the target pixel.  The estimate is
  either based on a noise model or sigma of pixels in a box near the
  target pixel.
  <P>
  The <I>crmask</I> parameter specifies a pixel mask for the image.  If the
  mask exists then non-zero mask values will be used to exclude pixels from
  the average, background median, and empirical sigma estimates.  Also any
  pixels with non-zero mask values will not be altered either in the output
  image or in the final mask.  If the  mask does not exist then it behaves as
  if all mask values are zero.  If all pixels in the average box or median
  annulus are previously flagged then the estimates will be undefined and
  nothing will be done to the output image or mask.  Because the task can
  use an input mask to mark pixels not to be considered it can be used
  in an iterative fashion.
  <P>
  The noise model is given by the formula
  <P>
  <PRE>
      variance = var0 + var1 * data + var2 * data^2
  </PRE>
  <P>
  where data is the maximum of zero and the average estimate for the target
  pixel.  The coefficients are all given in terms of the data numbers.  This
  model can be related to common detector parameters.  For CCDs var0 is the
  readout noise expressed as a variance in data numbers and var1 is the
  inverse gain (DN/electrons).  The second order coefficient has the
  interpretation of flat field introduced variance.
  <P>
  If all the coefficients are zero then an empirical sigma is estimated as
  follows.  The input image is divided into square blocks of size
  <I>nsig</I>.  The (unmasked) pixel values in a block are sorted and the
  pixel values nearest the 15.9 and 84.1 percentiles are selected.  These are
  the one sigma points in a Gaussian distribution.  The sigma estimate is the
  difference of these two values divided by two.  This algorithm is used to
  avoid contamination of the sigma estimate by the bad pixel values.  The
  block size must be at least 10 pixels in each dimension to provide
  sufficient pixels for a good estimate of the percentile points.  The sigma
  estimate for a pixel is the sigma from the nearest block.  A moving box is
  not used for reasons of efficiency.
  <P>
  If an output image name is specified then the output image is produced as a
  copy of the input image but with the identified cosmic ray pixels replaced
  by the average predicted value.  Other optional output images are
  the average filtered values and the sigma values.
  <P>
  If a mask is specified the detected cosmic rays will be identified with
  values given by the <I>crval</I> parameter and object pixels will be
  identified with values given by the <I>objval</I> parameter.  Note that one
  does not need to use an output image and the cosmic rays can be replaced by
  interpolation in the data using the tasks <I>crfix</I>, <I>fixpix</I>, or
  <I>ccdproc</I>.
  <P>
  One final step may be applied to the output mask.  The mask values
  identified with the <I>crval</I> and <I>objval</I> values may be grown
  by identifying pixel values within a specified radius with the same
  mask value.  Note that this step is done at the end and so any pixels
  in a preexisting input mask with the same values will also be grown.
  Also the grown pixels will not affect the output cosmic ray replaced
  image.  See <I>crgrow</I> for a further discussion.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  This example illustrates using the <B>craverage</B> task to
  create a mask with cosmic rays and objects identified and displayed.
  The image is a CCD image with a readout noise of 5 electrons
  and a gain of 3 electrons per data number.  This implies variance
  model coefficients of
  <P>
  <PRE>
      var0 = (5/3)^2 = 2.78
      var1 = 1/3 = 0.34
  </PRE>
  <P>
  <PRE>
      cl&gt; display obj001 1                  # Display in first frame
      cl&gt; craverage obj001 "" crmask=mask001 var0=2.78 var1=0.34\<BR>
      &gt;&gt;&gt; crval=1 objval=2
      cl&gt; display crobj001 2 overlay=mask001 ocol="1=green,2=red"
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  cosmicrays, crnebula, median, crfix, crgrow, crmedian
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'SYNOPSIS' 'USAGE   ' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>