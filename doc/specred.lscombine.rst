.. _lscombine:

lscombine — Combine longslit spectra
====================================

**Package: specred**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  lscombine -- Combine longslit images
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  lscombine input output
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of input two-dimensional images to combine.  This task is typically
  used with dispersion calibrated longslit images though it will work with
  any 2D images.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>Output combined image.
  </DD>
  </DL>
  <DL>
  <DT><B>headers = "<TT></TT>" (optional)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='headers' Line='headers = "" (optional)'>
  <DD>Optional output multiextension FITS file where each extension is a dataless
  headers from each input image.
  </DD>
  </DL>
  <DL>
  <DT><B>bpmasks = "<TT></TT>" (optional)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='bpmasks' Line='bpmasks = "" (optional)'>
  <DD>Optional output bad pixel mask with good values of 0 and bad values of 1.
  Output pixels are marked as bad when no input pixels contributed to the
  output pixel.  The file name is also added to the output image header under
  the keyword BPM.
  </DD>
  </DL>
  <DL>
  <DT><B>rejmask = "<TT></TT>" (optional)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rejmask' Line='rejmask = "" (optional)'>
  <DD>Optional output mask file identifying rejected or excluded pixels.  The
  pixel mask is the size of the output image but there is one extra dimension
  with length equal to the number of input images.  Each element of the
  highest dimension is a mask corresponding to an input image with values of
  1 for rejected or excluded pixels and values of 0 for pixels which were
  used.  The order of the masks is the order of the input images and image
  header keywords, indexed by the pixel coordinate of the highest dimension
  identify the input images.  Note that the pixel positions are in the output
  pixel coordinate system.
  </DD>
  </DL>
  <DL>
  <DT><B>nrejmasks = "<TT></TT>" (optional)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nrejmasks' Line='nrejmasks = "" (optional)'>
  <DD>Optional output pixel mask giving the number of input pixels rejected or
  excluded from the input images.
  </DD>
  </DL>
  <DL>
  <DT><B>expmasks = "<TT></TT>" (optional)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='expmasks' Line='expmasks = "" (optional)'>
  <DD>Optional output exposure mask giving the sum of the exposure values of
  the input images with non-zero weights that contributed to that pixel.
  Since masks are integer, the exposure values may be scaled to preserve
  dynamic range and fractional significance.  The scaling values are given in
  the header under the keywords MASKSCAL and MASKZERO.  Exposure values are
  computed from the mask values by scale * value + zero where scale is the
  value of the MASKSCAL keyword and zero is the value of the MASKZERO
  keyword.
  </DD>
  </DL>
  <DL>
  <DT><B>sigma = "<TT></TT>" (optional)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sigma' Line='sigma = "" (optional)'>
  <DD>Optional output sigma image.  The sigma is the standard deviation,
  corrected for a finite population, of the input pixel values (excluding
  rejected pixels) about the output combined pixel values.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B>logfile = "<TT>STDOUT</TT>" (optional)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logfile' Line='logfile = "STDOUT" (optional)'>
  <DD>Optional output log file.  If no file is specified then no log information is
  produced.  The special filename "<TT>STDOUT</TT>" prints log information to the
  terminal.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B>interptype = "<TT>spline3</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interptype' Line='interptype = "spline3"'>
  <DD>Image interpolation type for any resampling prior to combining.
  The allowed types are "<TT>nearest</TT>" (nearest neighbor), "<TT>linear</TT>" (bilinear),
  "<TT>poly3</TT>" (bicubic polynomial), "<TT>poly5</TT>" (biquintic polynomial), and "<TT>spline3</TT>"
  (bicubic polynomial).
  </DD>
  </DL>
  <DL>
  <DT><B>x1 = INDEF, y1 = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='x1' Line='x1 = INDEF, y1 = INDEF'>
  <DD>User coordinates of the first output column and line.  If INDEF then it
  is based on the smallest value over all the images.
  </DD>
  </DL>
  <DL>
  <DT><B>x2 = INDEF, y2 = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='x2' Line='x2 = INDEF, y2 = INDEF'>
  <DD>User coordinates of the last output column and line.  If INDEF then it
  is based on the largest value over all the images.
  </DD>
  </DL>
  <DL>
  <DT><B>dx = INDEF, dy = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dx' Line='dx = INDEF, dy = INDEF'>
  <DD>User coordinate pixel interval of the output.  If INDEF then the it
  is based on smallest interval (i.e. highest dispersion) over all the images.
  </DD>
  </DL>
  <DL>
  <DT><B>nx = INDEF, ny = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nx' Line='nx = INDEF, ny = INDEF'>
  <DD>Number of output pixels.  If INDEF then it is based on the values of the
  other coordinate parameters.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B>combine = "<TT>average</TT>" (average|median|sum)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='combine' Line='combine = "average" (average|median|sum)'>
  <DD>Type of combining operation performed on the final set of pixels (after
  offsetting, masking, thresholding, and rejection).  The choices are
  "<TT>average</TT>", "<TT>median</TT>", or "<TT>sum</TT>".  The median uses the average of the two central
  values when the number of pixels is even.  For the average and sum, the
  pixel values are multiplied by the weights (1 if no weighting is used)
  and summed.  The average is computed by dividing by the sum of the weights.
  If the sum of the weights is zero then the unweighted average is used.
  </DD>
  </DL>
  <DL>
  <DT><B>reject = "<TT>none</TT>" (none|minmax|ccdclip|crreject|sigclip|avsigclip|pclip)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='reject' Line='reject = "none" (none|minmax|ccdclip|crreject|sigclip|avsigclip|pclip)'>
  <DD>Type of rejection operation performed on the pixels remaining after offsetting,
  masking and thresholding.  The algorithms are described in the
  DESCRIPTION section.  The rejection choices are:
  <P>
  <PRE>
        none - No rejection
      minmax - Reject the nlow and nhigh pixels
     ccdclip - Reject pixels using CCD noise parameters
    crreject - Reject only positive pixels using CCD noise parameters
     sigclip - Reject pixels using a sigma clipping algorithm
   avsigclip - Reject pixels using an averaged sigma clipping algorithm
       pclip - Reject pixels using sigma based on percentiles
  </PRE>
  <P>
  </DD>
  </DL>
  <DL>
  <DT><B>outtype = "<TT>real</TT>" (none|short|ushort|integer|long|real|double)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outtype' Line='outtype = "real" (none|short|ushort|integer|long|real|double)'>
  <DD>Output image pixel datatype.  The pixel datatypes are "<TT>double</TT>", "<TT>real</TT>",
  "<TT>long</TT>", "<TT>integer</TT>", unsigned short "<TT>ushort</TT>", and "<TT>short</TT>" with highest
  precedence first.  If "<TT>none</TT>" is specified then the highest precedence
  datatype of the input images is used.  When there is a mixture of
  short and unsigned short images the highest precedence become integer.
  The datatypes may be abbreviated to a single character.
  </DD>
  </DL>
  <DL>
  <DT><B>outlimits = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outlimits' Line='outlimits = ""'>
  <DD>Output region limits in pixels specified as pairs of whitespace separated
  values.  The first two numbers are the limits along the first output image
  dimension, the next two numbers are the limits along the second dimension,
  and so on.  If the higher dimension limits are not specified they default
  to the full range.  Therefore, if no limits are specified then the full
  output is created.  Note that the output size is computed from all the
  input images including offsets if specified and the coordinates are
  relative to that size.
  </DD>
  </DL>
  <DL>
  <DT><B>masktype = "<TT>none</TT>" (none|goodvalue)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='masktype' Line='masktype = "none" (none|goodvalue)'>
  <DD>Type of pixel masking to use.  If "<TT>none</TT>" then no pixel masking is done
  even if an image has an associated  pixel mask.  Otherwise the
  value "<TT>goodvalue</TT>" will use any mask specified for the image under
  the BPM keyword.  The values of the mask will be interpreted as
  zero for good pixels and non-zero for bad pixels.  The mask pixels
  are assumed to be registered with the image pixels.
  </DD>
  </DL>
  <DL>
  <DT><B>blank = 0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='blank' Line='blank = 0.'>
  <DD>Output value to be used when there are no pixels.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B>scale = "<TT>none</TT>" (none|mode|median|mean|exposure|@&lt;file&gt;|!&lt;keyword&gt;)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='scale' Line='scale = "none" (none|mode|median|mean|exposure|@&lt;file&gt;|!&lt;keyword&gt;)'>
  <DD>Multiplicative image scaling to be applied.  The choices are none, multiply
  by the reciprocal of the mode, median, or mean of the specified statistics
  section, multiply by the reciprocal of the exposure time in the image header,
  multiply by the values in a specified file, or multiply by a specified
  image header keyword.  When specified in a file the scales must be one per
  line in the order of the input images.
  </DD>
  </DL>
  <DL>
  <DT><B>zero = "<TT>none</TT>" (none|mode|median|mean|@&lt;file&gt;|!&lt;keyword&gt;)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='zero' Line='zero = "none" (none|mode|median|mean|@&lt;file&gt;|!&lt;keyword&gt;)'>
  <DD>Additive zero level image shifts to be applied.  The choices are none, add
  the negative of the mode, median, or mean of the specified statistics
  section, add the values given in a file, or add the values given by an
  image header keyword.  When specified in a file the zero values must be one
  per line in the order of the input images.  File or keyword zero offset
  values do not allow a correction to the weights.
  </DD>
  </DL>
  <DL>
  <DT><B>weight = "<TT>none</TT>" (none|mode|median|mean|exposure|@&lt;file&gt;|!&lt;keyword&gt;)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='weight' Line='weight = "none" (none|mode|median|mean|exposure|@&lt;file&gt;|!&lt;keyword&gt;)'>
  <DD>Weights to be applied during the final averaging.  The choices are none,
  the mode, median, or mean of the specified statistics section, the exposure
  time, values given in a file, or values given by an image header keyword.
  When specified in a file the weights must be one per line in the order of
  the input images and the only adjustment made by the task is for the number of
  images previously combined.   In this case the weights should be those
  appropriate for the scaled images which would normally be the inverse
  of the variance in the scaled image.
  </DD>
  </DL>
  <DL>
  <DT><B>statsec = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='statsec' Line='statsec = ""'>
  <DD>Section of images to use in computing image statistics for scaling and
  weighting.  If no section is given then the entire region of the input is
  sampled (for efficiency the images are sampled if they are big enough).
  When the images are offset relative to each other one can precede the image
  section with one of the modifiers "<TT>input</TT>", "<TT>output</TT>", "<TT>overlap</TT>".  The first
  interprets the section relative to the input image (which is equivalent to
  not specifying a modifier), the second interprets the section relative to
  the output image, and the last selects the common overlap and any following
  section is ignored.
  </DD>
  </DL>
  <DL>
  <DT><B> expname = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line=' expname = ""'>
  <DD>Image header keyword to be used with the exposure scaling and weighting
  options.  Also if an exposure keyword is specified that keyword will be
  added to the output image using a weighted average of the input exposure
  values.
  </DD>
  </DL>
  <P>
  <CENTER>Algorithm Parameters
  
  </CENTER><BR>
  <DL>
  <DT><B>lthreshold = INDEF, hthreshold = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lthreshold' Line='lthreshold = INDEF, hthreshold = INDEF'>
  <DD>Low and high thresholds to be applied to the input pixels.  This is done
  before any scaling, rejection, and combining.  If INDEF the thresholds
  are not used.
  </DD>
  </DL>
  <DL>
  <DT><B>nlow = 1,  nhigh = 1 (minmax)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nlow' Line='nlow = 1,  nhigh = 1 (minmax)'>
  <DD>The number of low and high pixels to be rejected by the "<TT>minmax</TT>" algorithm.
  These numbers are converted to fractions of the total number of input images
  so that if no rejections have taken place the specified number of pixels
  are rejected while if pixels have been rejected by masking, thresholding,
  or nonoverlap, then the fraction of the remaining pixels, truncated
  to an integer, is used.
  </DD>
  </DL>
  <DL>
  <DT><B>nkeep = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nkeep' Line='nkeep = 1'>
  <DD>The minimum number of pixels to retain or the maximum number to reject
  when using the clipping algorithms (ccdclip, crreject, sigclip,
  avsigclip, or pclip).  When given as a positive value this is the minimum
  number to keep.  When given as a negative value the absolute value is
  the maximum number to reject.  The latter is in addition to pixels
  missing due to non-overlapping offsets, bad pixel masks, or thresholds.
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
  which contains the value.  The noise model for a pixel is:
  <P>
  <PRE>
      variance in DN = (rdnoise/gain)^2 + DN/gain + (snoise*DN)^2
      variance in e- = (rdnoise)^2 + (gain*DN) + (snoise*(gain*DN))^2
  		   = rdnoise^2 + Ne + (snoise * Ne)^2
  </PRE>
  <P>
  where DN is the data number and Ne is the number of electrons.  Sensitivity
  noise typically comes from noise introduced during flat fielding.
  </DD>
  </DL>
  <DL>
  <DT><B>sigscale = 0.1 (ccdclip, crreject, sigclip, avsigclip)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sigscale' Line='sigscale = 0.1 (ccdclip, crreject, sigclip, avsigclip)'>
  <DD>This parameter determines when poisson corrections are made to the
  computation of a sigma for images with different scale factors.  If all
  relative scales are within this value of unity and all relative zero level
  offsets are within this fraction of the mean then no correction is made.
  The idea is that if the images are all similarly though not identically
  scaled, the extra computations involved in making poisson corrections for
  variations in the sigmas can be skipped.  A value of zero will apply the
  corrections except in the case of equal images and a large value can be
  used if the sigmas of pixels in the images are independent of scale and
  zero level.
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
  </DD>
  </DL>
  <DL>
  <DT><B>grow = 0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='grow' Line='grow = 0.'>
  <DD>Radius in pixels for additional pixel to be rejected in an image with a
  rejected pixel from one of the rejection algorithms.  This applies only to
  pixels rejected by one of the rejection algorithms and not the masked or
  threshold rejected pixels.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <B>LSCOMBINE</B> combines two-dimensional longslit images by first
  resampling them to a common world coordinate system, if not already on
  the same system, and then combining the matching pixels.  The final world
  coordinate system is specified by parameters or by looking at the maximum
  ranges and minimum intervals over the input data.
  <P>
  Algorithmically it is a combination of the tasks <B>TRANSFORM</B> (using
  the WCS) and <B>IMCOMBINE</B>.  When executing it will generate temporary
  images ("<TT>lsc*</TT>") and masks ("<TT>mlsc*</TT>") if the images are not already on a
  common world coordinate system.  The user only need be aware of this
  in case of an unexpected abort leaving these files behind.
  <P>
  Rather than repeat the details the user should consult the descriptions
  for <B>TRANSFORM</B> and <B>IMCOMBINE</B> ignoring parameters which are
  not part of this task.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <PRE>
      cl&gt; lscombine obj* lscomb
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Notes</H3>
  <! BeginSection: 'NOTES'>
  <UL>
  <DL>
  <DT><B>LSCOMBINE: V2.12.3</B></DT>
  <! Sec='NOTES' Level=0 Label='LSCOMBINE' Line='LSCOMBINE: V2.12.3'>
  <DD>This is a new task in this relese.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'NOTES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  transform, imcombine. odcombine 
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'NOTES' 'SEE ALSO'  >
  
