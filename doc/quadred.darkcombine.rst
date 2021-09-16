.. _darkcombine:

darkcombine — Combine and process dark count images
===================================================

**Package: quadred**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  darkcombine -- Combine and process dark count images
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  darkcombine input
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of dark count images to combine.  The <I>ccdtype</I> parameter
  may be used to select the zero level images from a list containing all
  types of data.
  </DD>
  </DL>
  <DL>
  <DT><B>output = "<TT>Dark</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output = "Dark"'>
  <DD>Output dark count root image name.
  </DD>
  </DL>
  <DL>
  <DT><B>combine = "<TT>average</TT>" (average|median)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='combine' Line='combine = "average" (average|median)'>
  <DD>Type of combining operation performed on the final set of pixels (after
  rejection).  The choices are
  "<TT>average</TT>" or "<TT>median</TT>".  The median uses the average of the two central
  values when the number of pixels is even.
  </DD>
  </DL>
  <DL>
  <DT><B>reject = "<TT>minmax</TT>" (none|minmax|ccdclip|crreject|sigclip|avsigclip|pclip)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='reject' Line='reject = "minmax" (none|minmax|ccdclip|crreject|sigclip|avsigclip|pclip)'>
  <DD>Type of rejection operation.  See <B>combine</B> for details.
  </DD>
  </DL>
  <DL>
  <DT><B>ccdtype = "<TT>dark</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ccdtype' Line='ccdtype = "dark"'>
  <DD>CCD image type to combine.  If no image type is given then all input images
  are combined.
  </DD>
  </DL>
  <DL>
  <DT><B>process = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='process' Line='process = yes'>
  <DD>Process the input images before combining?
  </DD>
  </DL>
  <DL>
  <DT><B>delete = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='delete' Line='delete = no'>
  <DD>Delete input images after combining?  Only those images combined are deleted.
  </DD>
  </DL>
  <DL>
  <DT><B>clobber = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='clobber' Line='clobber = no'>
  <DD>Clobber existing output images?
  </DD>
  </DL>
  <DL>
  <DT><B>scale = "<TT>exposure</TT>" (none|mode|median|mean|exposure)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='scale' Line='scale = "exposure" (none|mode|median|mean|exposure)'>
  <DD>Multiplicative image scaling to be applied.  The choices are none, scale
  by the mode, median, or mean of the specified statistics section, or scale
  by the exposure time given in the image header.
  </DD>
  </DL>
  <DL>
  <DT><B>statsec = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='statsec' Line='statsec = ""'>
  <DD>Section of images to use in computing image statistics for scaling.
  If no section is given then the entire region of the image is
  sampled (for efficiency the images are sampled if they are big enough).
  </DD>
  </DL>
  <P>
  <CENTER>Algorithm Parameters
  
  </CENTER><BR>
  <DL>
  <DT><B>nlow = 0,  nhigh = 1 (minmax)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nlow' Line='nlow = 0,  nhigh = 1 (minmax)'>
  <DD>The number of low and high pixels to be rejected by the "<TT>minmax</TT>" algorithm.
  </DD>
  </DL>
  <DL>
  <DT><B>nkeep = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nkeep' Line='nkeep = 1'>
  <DD>The minimum number of pixels to retain or the maximum number to reject
  when using the clipping algorithms (ccdclip, crreject, sigclip,
  avsigclip, or pclip).  When given as a positive value this is the minimum
  number to keep.  When given as a negative value the absolute value is
  the maximum number to reject.  This is actually converted to a number
  to keep by adding it to the number of images.
  </DD>
  </DL>
  <DL>
  <DT><B>mclip = yes (ccdclip, crreject, sigclip, avsigcliip)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='mclip' Line='mclip = yes (ccdclip, crreject, sigclip, avsigcliip)'>
  <DD>Use the median as the estimate for the true intensity rather than the
  average with high and low values excluded in the "<TT>ccdclip</TT>", "<TT>crreject</TT>",
  "<TT>sigclip</TT>", and "<TT>avsigclip</TT>" algorithms?  The median is a better estimator
  in the presence of data which one wants to reject than the average.
  However, computing the median is slower than the average.
  </DD>
  </DL>
  <DL>
  <DT><B>lsigma = 3., hsigma = 3. (ccdclip, crreject, sigclip, avsigclip, pclip)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lsigma' Line='lsigma = 3., hsigma = 3. (ccdclip, crreject, sigclip, avsigclip, pclip)'>
  <DD>Low and high sigma clipping factors for the "<TT>ccdclip</TT>", "<TT>crreject</TT>", "<TT>sigclip</TT>",
  "<TT>avsigclip</TT>", and "<TT>pclip</TT>" algorithms.  They multiply a "<TT>sigma</TT>" factor
  produced by the algorithm to select a point below and above the average or
  median value for rejecting pixels.  The lower sigma is ignored for the
  "<TT>crreject</TT>" algorithm.
  </DD>
  </DL>
  <DL>
  <DT><B>rdnoise = "<TT>0.</TT>", gain = "<TT>1.</TT>", snoise = "<TT>0.</TT>" (ccdclip, crreject)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rdnoise' Line='rdnoise = "0.", gain = "1.", snoise = "0." (ccdclip, crreject)'>
  <DD>CCD readout noise in electrons, gain in electrons/DN, and sensitivity noise
  as a fraction.  These parameters are used with the "<TT>ccdclip</TT>" and "<TT>crreject</TT>"
  algorithms.  The values may be either numeric or an image header keyword
  which contains the value.
  </DD>
  </DL>
  <DL>
  <DT><B>pclip = -0.5 (pclip)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pclip' Line='pclip = -0.5 (pclip)'>
  <DD>Percentile clipping algorithm parameter.  If greater than
  one in absolute value then it specifies a number of pixels above or
  below the median to use for computing the clipping sigma.  If less
  than one in absolute value then it specifies the fraction of the pixels
  above or below the median to use.  A positive value selects a point
  above the median and a negative value selects a point below the median.
  The default of -0.5 selects approximately the quartile point.
  See <B>combine</B> for further details.
  </DD>
  </DL>
  <DL>
  <DT><B>blank = 0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='blank' Line='blank = 0.'>
  <DD>Output value to be used when there are no pixels.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The dark count images in the input image list are combined.
  The input images may be processed first if desired.
  The original images may be deleted automatically if desired.
  The output pixel datatype will be real.
  <P>
  This task is a script which applies <B>ccdproc</B> and <B>combine</B>.  The
  parameters and combining algorithms are described in detail in the help for
  <B>combine</B>.  This script has default parameters specifically set for
  dark count images and simplifies the combining parameters.  There are other
  combining options not included in this task.  For these additional
  features, such as thresholding, offseting, masking, and projecting, use
  <B>combine</B>.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. The image data contains four dark count images.  To automatically select
  them and combine them as a background job using the default combining algorithm:
  <P>
      cl&gt; darkcombine ccd*.imh&amp;
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  ccdproc, combine
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
