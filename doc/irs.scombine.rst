.. _scombine:

scombine — Combine spectra having different wavelength ranges
=============================================================

**Package: irs**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  scombine -- Combine spectra
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  scombine input output
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of input images containing spectra to be combined.  The spectra
  in the images to be combined are selected with the <I>apertures</I> and
  <I>group</I> parameters.  Only the primary spectrum is combined and
  the associated band spectra are ignored.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>List of output images to be created containing the combined spectra.
  If the grouping option is "<TT>all</TT>"
  or "<TT>apertures</TT>" then only one output image will be created.  In the
  first case the image will contain only one spectrum and in the latter case
  there will be a spectrum for each selected aperture.
  If the grouping option is "<TT>images</TT>" then there will be one
  output spectrum per input spectrum.
  </DD>
  </DL>
  <DL>
  <DT><B>noutput = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='noutput' Line='noutput = ""'>
  <DD>List of output images to be created containing the number of spectra combined.
  The number of images required is the same as the <I>output</I> list.
  Any or all image names may be given as a null string, i.e. "<TT></TT>", in which
  case no output image is created.
  </DD>
  </DL>
  <DL>
  <DT><B>logfile = "<TT>STDOUT</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logfile' Line='logfile = "STDOUT"'>
  <DD>File name for recording log information about the combining operation.
  The file name "<TT>STDOUT</TT>" is used to write the information to the terminal.
  If the null string is specified then no log information is printed or
  recorded.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B>apertures = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='apertures' Line='apertures = ""'>
  <DD>List of apertures to be selected for combining.  If none is specified
  then all apertures are selected.  The syntax is a blank or comma separated
  list of aperture numbers or aperture ranges separated by a hyphen.
  </DD>
  </DL>
  <DL>
  <DT><B>group = "<TT>apertures</TT>" (all|images|apertures)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='group' Line='group = "apertures" (all|images|apertures)'>
  <DD>Option for grouping input spectra for combining (after selection by aperture)
  from one or more input images.  The options are:
  <DL>
  <DT><B>"<TT>all</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"all"'>
  <DD>Combine all spectra from all images in the input list into a single output
  spectrum.
  </DD>
  </DL>
  <DL>
  <DT><B>"<TT>images</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"images"'>
  <DD>Combine all spectra in each input image into a single spectrum in
  separate output images.
  </DD>
  </DL>
  <DL>
  <DT><B>"<TT>apertures</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"apertures"'>
  <DD>Combine all spectra of the same aperture from all input images and put it
  into a single output image with the other selected apertures.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>combine = "<TT>average</TT>" (average|median|sum)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='combine' Line='combine = "average" (average|median|sum)'>
  <DD>Option for combining pixels at the same dispersion coordinate.  after any
  rejection operation.  The options are to compute the  "<TT>average</TT>", "<TT>median</TT>",
  or "<TT>sum</TT>" of the pixels.  The first two are applied after any pixel
  rejection.  The sum option ignores the rejection and scaling parameters and
  no rejection is performed.  In other words, the "<TT>sum</TT>" option is simply the
  direct summation of the pixels.  The median uses the average of the two
  central values when the number of pixels is even.
  </DD>
  </DL>
  <DL>
  <DT><B>reject = "<TT>none</TT>" (none|minmax|ccdclip|crreject|sigclip|avsigclip|pclip)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='reject' Line='reject = "none" (none|minmax|ccdclip|crreject|sigclip|avsigclip|pclip)'>
  <DD>Type of rejection operation performed on the pixels which overlap at each
  dispersion coordinate.  The algorithms are discussed in the
  DESCRIPTION section.  The rejection choices are:
  <P>
  <PRE>
        none - No rejection
      minmax - Reject the nlow and nhigh pixels
     sigclip - Reject pixels using a sigma clipping algorithm
   avsigclip - Reject pixels using an averaged sigma clipping algorithm
     ccdclip - Reject pixels using CCD noise parameters
    crreject - Reject only positive pixels using CCD noise parameters
       pclip - Reject pixels using sigma based on percentiles
  </PRE>
  <P>
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B>first = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='first' Line='first = no'>
  <DD>Use the first input spectrum of each set to be combined to define the
  dispersion coordinates for combining and output?  If yes then all other
  spectra to be combined will be interpolated to the dispersion of this
  reference spectrum and that dispersion defines the dispersion of the
  output spectrum.  If no, then all the spectra are interpolated to a linear
  dispersion as determined by the following parameters.  The interpolation
  type is set by the package parameter <I>interp</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>w1 = INDEF, w2=INDEF, dw = INDEF, nw = INDEF, log = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='w1' Line='w1 = INDEF, w2=INDEF, dw = INDEF, nw = INDEF, log = no'>
  <DD>The output linear or log linear wavelength scale if the dispersion of the
  first spectrum is not used.  INDEF values are filled in from the maximum
  wavelength range and minimum dispersion of the spectra to be combined.  The
  parameters are aways specified in linear wavelength even when the log
  parameter is set to produce constant pixel increments in the log of the
  wavelength.  The dispersion is interpreted in that case as the difference
  in the log of the endpoints divided by the number of pixel increments.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B>scale = "<TT>none</TT>" (none|mode|median|mean|exposure|@&lt;file&gt;|!&lt;keyword&gt;)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='scale' Line='scale = "none" (none|mode|median|mean|exposure|@&lt;file&gt;|!&lt;keyword&gt;)'>
  <DD>Multiplicative image scaling to be applied.  The choices are none,
  multiply by the reciprocal of the mode , median, or mean of the specified
  statistics section, scale by the exposure time in the image header, multiply
  by the values in a specified file, or multiply by a specified image header
  keyword.  When specified in a file the scales must be one per line in the
  order of the input spectra.
  </DD>
  </DL>
  <DL>
  <DT><B>zero = "<TT>none</TT>" (none|mode|median|mean|@&lt;file&gt;|!&lt;keyword&gt;)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='zero' Line='zero = "none" (none|mode|median|mean|@&lt;file&gt;|!&lt;keyword&gt;)'>
  <DD>Additive zero level image shifts to be applied.  The choices are none,
  add the negative of the mode, median, or mean of the specified statistics
  section, add the values given in a file, or add values given by an
  image header keyword.  When specified in a file the zero values must be one
  per line in the order of the input spectra. File or keyword zero offset
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
  the input spectra.
  </DD>
  </DL>
  <DL>
  <DT><B>sample = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sample' Line='sample = ""'>
  <DD>Wavelength sample regions to use in computing spectrum statistics for
  scaling and weighting.  If no sample regions are given then the entire
  input spectrum is used.  The syntax is colon separated wavelengths
  or a file containing colon separated wavelengths preceded by the
  @ character; i.e. @&lt;file&gt;.
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
  These numbers are converted to fractions of the total number of input spectra
  so that if no rejections have taken place the specified number of pixels
  are rejected while if pixels have been rejected by thresholding
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
  <DD>Effective CCD readout noise in electrons, gain in electrons/DN, and
  sensitivity noise as a fraction.  These parameters are used with the
  "<TT>ccdclip</TT>" and "<TT>crreject</TT>" algorithms.  The values may be either numeric or
  an image header keyword which contains the value.  Note that if the spectra
  have been extracted from a 2D CCD image then the noise parameters must be
  adjusted for background and the aperture summing.
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
  See the DESCRIPTION section for further details.
  </DD>
  </DL>
  <DL>
  <DT><B>grow = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='grow' Line='grow = 0'>
  <DD>Number of pixels to either side of a rejected pixel
  to also be rejected.  This applies only to pixels rejected by one of
  the rejection algorithms and not the threshold rejected pixels.
  </DD>
  </DL>
  <DL>
  <DT><B>blank = 0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='blank' Line='blank = 0.'>
  <DD>Value to use when there are no input pixels to combine for an output pixel.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <B>Scombine</B> combines input spectra by interpolating them (if necessary)
  to a common dispersion sampling, rejecting pixels exceeding specified low
  and high thresholds, scaling them in various ways, applying a rejection
  algorithm based on known or empirical noise statistics, and computing the
  sum, weighted average, or median of the remaining pixels.  Note that
  the "<TT>sum</TT>" option is the direct summation of the pixels and does not
  perform any rejection or scaling of the data regardless of the parameter
  settings.
  <P>
  The input spectra are specified using an image list in which each image
  may contain multiple spectra.  The set of spectra may be restricted
  by the <I>aperture</I> parameter to specific apertures.  The set of input
  spectra may then be grouped using the <I>group</I> parameter and each
  group combined separately into a final output spectrum.  The grouping
  options are to select all the input spectra regardless of the input
  image or aperture number, select all spectra of the same aperture,
  or select all the spectra from the same input image.
  <P>
  The output consists of either a single image with one spectrum for each
  combined group or, when grouping by image, an image with the single
  combined spectra from each input image.  The output images and
  combined spectra inherit the header parameters from the first spectrum
  of the combined group.  In addition to the combined spectrum an associated
  integer spectrum containing the number of pixels combined
  and logfile listing the combined spectra, scaling, weights, etc, may
  be produced.
  <P>
  The spectral combining is done using pixels at common dispersion
  coordinates rather than physical or logical pixel coordinates.  If the
  spectra to be combined do not have identical dispersion coordinates then
  the spectra are interpolated to a common dispersion sampling before
  combining.  The interpolation conserves pixel values rather pixel fluxes.
  This means that flux calibrated data is treated correctly and that
  spectra in counts are not corrected in the interpolation for changes
  in pixel widths.  
  The default interpolation function is a 5th order polynomial.  The
  choice of interpolation type is made with the package parameter "<TT>interp</TT>".
  It may be set to "<TT>nearest</TT>", "<TT>linear</TT>", "<TT>spline3</TT>", "<TT>poly5</TT>", or "<TT>sinc</TT>".
  Remember that this applies to all tasks which might need to interpolate
  spectra in the <B>onedspec</B> and associated packages.  For a discussion of
  interpolation types see <B>onedspec</B>.
  <P>
  There are two choices for the common dispersion coordinate sampling. If the
  <I>first</I> parameter is set then the dispersion sampling of the first
  spectrum is used.  This dispersion system may be nonlinear.  If the
  parameter is not set then the user specified linear or log linear
  dispersion system is used.  Any combination of starting wavelength, ending
  wavelength, wavelength per pixel, and number of output pixels may be
  specified.  Unspecified values will default to reasonable values based on
  the minimum or maximum wavelengths of all spectra, the minimum dispersion,
  and the number of pixels needed to satisfy the other parameters.  If the
  parameters overspecify the linear system then the ending wavelength is
  adjusted based on the other parameters.  Note that for a log linear system
  the wavelengths are still specified in nonlog units and the dispersion is
  finally recalculated using the difference of the log wavelength endpoints
  divided by the number pixel intervals (the number of pixels minus one).
  <P>
  There are several stages to combining a selected group of spectra.  The
  first is interpolation to a common dispersion sampling as discussed
  above.  The second stage is to eliminate any pixels outside the specified
  thresholds.  Note that the thresholds apply to the interpolated
  spectra.  Scaling and zero offset factors are computed and applied to the
  spectra if desire.  The computation of these factors as well as weights is
  discussed in the following section.  Next there is a choice of rejection
  algorithms to identify and eliminate deviant pixels.  Some of these are
  based on order statistics and some relative to the distance from an initial
  median or average using a noise model cutoff.  A growing factor may be
  applied to neighbors of rejected pixels to reject additional pixels.  The
  various algorithms are described in detail in a following section.
  Finally, the remaining pixels are combined by summing (which may not be
  appropriate when pixels are rejected), computing a median, or computing a
  weighted or unweighted average.  The combined spectrum is written to an
  output image as well the number of pixels used in the final combining.
  <P>
  SCALES AND WEIGHTS
  <P>
  In order to combine spectra with rejection of pixels based on deviations
  from some average or median they must be scaled to a common level.  There
  are two types of scaling available, a multiplicative intensity scale and an
  additive zero point shift.  The intensity scaling is defined by the
  <I>scale</I> parameter and the zero point shift by the <I>zero</I>
  parameter.  These parameters may take the values "<TT>none</TT>" for no scaling,
  "<TT>mode</TT>", "<TT>median</TT>", or "<TT>mean</TT>" to scale by statistics of the spectrum pixels,
  "<TT>exposure</TT>" (for intensity scaling only) to scale by the exposure time
  keyword in the image header, any other image header keyword specified by
  the keyword name prefixed by the character <TT>'!'</TT>, and the name of a file
  containing the scale factors for the input image prefixed by the
  character <TT>'@'</TT>.
  <P>
  Examples of the possible parameter values are shown below where
  "<TT>myval</TT>" is the name of an image header keyword and "<TT>scales.dat</TT>" is
  a text file containing a list of scale factors.
  <P>
  <PRE>
  	scale = none		No scaling
  	zero = mean		Intensity offset by the mean
  	scale = exposure	Scale by the exposure time
  	zero = !myval		Intensity offset by an image keyword
  	scale = @scales.dat	Scales specified in a file
  </PRE>
  <P>
  The spectrum statistics factors are computed within specified sample
  regions given as a series of colon separated wavelengths.  If no
  regions are specified then all pixels are used.  If the
  wavelength sample list is too long the regions can be defined in a file and
  specified in the <I>sample</I> parameter using the syntax @&lt;file&gt; where file
  is the filename.
  <P>
  The statistics are as indicated by their names.  In particular, the
  mode is a true mode using a bin size which is a fraction of the
  range of the pixels and is not based on a relationship between the
  mode, median, and mean.  Also thresholded pixels are excluded from the
  computations as well as during the rejection and combining operations.
  <P>
  The "<TT>exposure</TT>" option in the intensity scaling uses the value of the image
  header keyword (EXPTIME, EXPOSURE, or ITIME).  Note that the exposure
  keyword is also updated in the final image as the weighted average of the
  input values.  If one wants to use a nonexposure time keyword and keep the
  exposure time updating feature the image header keyword syntax is
  available; i.e. !&lt;keyword&gt;.
  <P>
  Scaling values may be defined as a list of values in a text file.  The file
  name is specified by the standard @file syntax.  The list consists of one
  value per line.  The order of the list is assumed to be the same as the
  order of the input spectra.  It is a fatal error if the list is incomplete
  and a warning if the list appears longer than the number of input spectra.
  Consideration of the grouping parameter must be included in
  generating this list since spectra may come from different images,
  some apertures may be missing, and, when there are multiple output spectra
  or images, the same list will be repeatedly used.
  <P>
  If both an intensity scaling and zero point shift are selected the
  multiplicative scaling is done first.  Use of both makes sense for images
  if the intensity scaling is the exposure time to correct for
  different exposure times and with the zero point shift allowing for
  sky brightness changes.  This is less relevant for spectra but the option
  is available.
  <P>
  The spectrum statistics and scale factors are recorded in the log file
  unless they are all equal, which is equivalent to no scaling.  The
  intensity scale factors are normalized to a unit mean and the zero
  point shifts are adjusted to a zero mean.  When scal factors
  or zero point shifts are specified by the user in an @file or by an
  image header keyword, no normalization is done.
  <P>
  Scaling affects not only the mean values between spectra but also the
  relative pixel uncertainties.  For example scaling an spectrum by a
  factor of 0.5 will reduce the effective noise sigma of the spectrum
  at each pixel by the square root of 0.5.  Changes in the zero
  point also changes the noise sigma if the spectrum noise characteristics
  are Poissonian.  In the various rejection algorithms based on
  identifying a noise sigma and clipping large deviations relative to
  the scaled median or mean, one may need to account for the scaling induced
  changes in the spectrum noise characteristics.
  <P>
  In those algorithms it is possible to eliminate the "<TT>sigma correction</TT>"
  while still using scaling.  The reasons this might be desirable are 1) if
  the scalings are similar the corrections in computing the mean or median
  are important but the sigma corrections may not be important and 2) the
  spectrum statistics may not be Poissonian, either inherently or because the
  spectra have been processed in some way that changes the statistics.  In the
  first case because computing square roots and making corrections to every
  pixel during the iterative rejection operation may be a significant
  computational speed limit the parameter <I>sigscale</I> selects how
  dissimilar the scalings must be to require the sigma corrections.  This
  parameter is a fractional deviation which, since the scale factors are
  normalized to unity, is the actual minimum deviation in the scale factors.
  For the zero point shifts the shifts are normalized by the mean shift
  before adjusting the shifts to a zero mean.  To always use sigma scaling
  corrections the parameter is set to zero and to eliminate the correction in
  all cases it is set to a very large number.
  <P>
  If the final combining operation is "<TT>average</TT>" then the spectra may be
  weighted during the averaging.  The weights are specified in the same way
  as the scale factors.  The weights, scaled to a unit sum, are printed in
  the log output.
  <P>
  The weights are only used for the final weighted average and sigma image
  output.  They are not used to form averages in the various rejection
  algorithms.  For weights in the case of no scaling or only multiplicative
  scaling the weights are used as given or determined so that images
  with lower signal levels will have lower weights.  However, for
  cases in which zero level scaling is used the weights are computed
  from the initial weights (the exposure time, image statistics, or
  input values) using the formula:
  <P>
  <PRE>
  	weight_final = weight_initial / (scale * zero)
  </PRE>
  <P>
  where the zero values are those before adjustment to zero mean over
  all images.  The reasoning is that if the zero level is high the sky
  brightness is high and so the S/N is lower and the weight should be lower.
  <P>
  <P>
  THRESHOLD REJECTION
  <P>
  There is an initial threshold rejection step which may be applied.  The
  thresholds are given by the parameters <I>lthreshold</I> and
  <I>hthreshold</I>.  Values of INDEF mean that no threshold value is
  applied.  Threshold rejection may be used to exclude very bad pixel values
  or as a way of masking images.  The former case is useful to exclude very
  bright cosmic rays.  Some of the rejection algorithms, such as "<TT>avsigclip</TT>",
  can perform poorly if very strong cosmic rays are present.  For masking one
  can use a task like <B>imedit</B> or <B>imreplace</B> to set parts of the
  spectra to be excluded to some very low or high magic value.
  <P>
  <P>
  REJECTION ALGORITHMS
  <P>
  The <I>reject</I> parameter selects a type of rejection operation to
  be applied to pixels not thresholded.  If no rejection
  operation is desired the value "<TT>none</TT>" is specified.  This task is
  closely related to the image combining task <B>imcombine</B> and, in
  particular, has the same rejection algorithms.
  Some the algorithms are more appropriate to images but are available
  in this task also for completeness.
  <P>
  MINMAX
  A specified fraction of the highest and lowest pixels are rejected.
  The fraction is specified as the number of high and low pixels, the
  <I>nhigh</I> and <I>nlow</I> parameters, when data from all the input spectra
  are used.  If pixels are missing where there is no overlap or have been
  rejected by thresholding then a matching fraction of the remaining pixels,
  truncated to an integer, are used.  Thus,
  <P>
  <PRE>
  	nl = n * nlow/nspectra + 0.001 
  	nh = n * nhigh/nspectra + 0.001 
  </PRE>
  <P>
  where n is the number of pixels to be combined, nspectra is the number
  of input spectra, nlow and nhigh
  are task parameters and nl and nh are the final number of low and
  high pixels rejected by the algorithm.  The factor of 0.001 is to
  adjust for rounding of the ratio.
  <P>
  As an example with 10 input spectra and specifying one low and two high
  pixels to be rejected the fractions to be rejected are 0.1 and 0.2
  and the number rejected as a function of n is:
  <P>
  <PRE>
  	 n   0  1  2  3  4  5  6  7  8  9 10
  	 nl  0  0  0  0  0  1  1  1  1  1  2
  	 nh  0  0  0  0  0  0  0  0  0  0  1
  </PRE>
  CCDCLIP
  If the noise characteristics of the spectra can be described by fixed
  gaussian noise, a poissonian noise which scales with the square root of
  the intensity, and a sensitivity noise which scales with the intensity,
  the sigma in data values at a pixel with true value &lt;I&gt;,
  as approximated by the median or average with the lowest and highest value
  excluded, is given as:
  <P>
  <PRE>
  	sigma = ((rn / g) ** 2 + &lt;I&gt; / g + (s * &lt;I&gt;) ** 2) ** 1/2
  </PRE>
  <P>
  where rn is the read out noise in electrons, g is the gain in
  electrons per data value, s is a sensitivity noise given as a fraction,
  and ** is the exponentiation operator.  Often the sensitivity noise,
  due to uncertainties in the pixel sensitivities (for example from the
  flat field), is not known in which case a value of zero can be used.
  <P>
  This model is typically valid for CCD images.  During extraction of 
  spectra from CCD images the noise parameters of the spectrum pixels
  will be changed from those of the CCD pixels.  Currently it is up to
  the user to determine the proper modifications of the CCD read noise
  gain, and sensitivity noise.
  <P>
  The read out noise is specified by the <I>rdnoise</I> parameter.  The value
  may be a numeric value to be applied to all the input spectra or an image
  header keyword containing the value for spectra from each image.
  Similarly, the parameter <I>gain</I> specifies the gain as either a value or
  image header keyword and the parameter <I>snoise</I> specifies the
  sensitivity noise parameter as either a value or image header keyword.
  <P>
  The algorithm operates on each output pixel independently.  It starts by
  taking the median or unweighted average (excluding the minimum and maximum)
  of the unrejected pixels provided there are at least two input pixels.  The
  expected sigma is computed from the CCD noise parameters and pixels more
  that <I>lsigma</I> times this sigma below or <I>hsigma</I> times this sigma
  above the median or average are rejected.  The process is then iterated
  until no further pixels are rejected.  If the average is used as the
  estimator of the true value then after the first round of rejections the
  highest and lowest values are no longer excluded.  Note that it is possible
  to reject all pixels if the average is used and is sufficiently skewed by
  bad pixels such as cosmic rays.
  <P>
  If there are different CCD noise parameters for the input images
  (as might occur using the image header keyword specification) then
  the sigmas are computed for each pixel from each image using the
  same estimated true value.
  <P>
  If the images are scaled and shifted and the <I>sigscale</I> threshold
  is exceedd then a sigma is computed for each pixel based on the
  spectrum scale parameters; i.e. the median or average is scaled to that of the
  original image before computing the sigma and residuals.
  <P>
  After rejection the number of retained pixels is checked against the
  <I>nkeep</I> parameter.  If there are fewer pixels retained than specified
  by this parameter the pixels with the smallest residuals in absolute
  value are added back.  If there is more than one pixel with the same
  absolute residual (for example the two pixels about an average
  or median of two will have the same residuals) they are all added
  back even if this means more than <I>nkeep</I> pixels are retained.
  Note that the <I>nkeep</I> parameter only applies to the pixels used
  by the clipping rejection algorithm and does not apply to threshold
  or bad pixel mask rejection.
  <P>
  This is the best clipping algorithm to use if the CCD noise parameters are
  adequately known.  The parameters affecting this algorithm are <I>reject</I>
  to select this algorithm, <I>mclip</I> to select the median or average for
  the center of the clipping, <I>nkeep</I> to limit the number of pixels
  rejected, the CCD noise parameters <I>rdnoise, gain</I> and <I>snoise</I>,
  <I>lsigma</I> and <I>hsigma</I> to select the clipping thresholds,
  and <I>sigscale</I> to set the threshold for making corrections to the sigma
  calculation for different image scale factors.
  <P>
  CRREJECT
  This algorithm is identical to "<TT>ccdclip</TT>" except that only pixels above
  the average are rejected based on the <I>hsigma</I> parameter.  This
  is appropriate for rejecting cosmic ray events and works even with
  two spectra.
  <P>
  SIGCLIP
  The sigma clipping algorithm computes at each output pixel the median or
  average excluding the high and low values and the sigma about this
  estimate.  There must be at least three input pixels, though for this method
  to work well there should be at least 10 pixels.  Values deviating by more
  than the specified sigma threshold factors are rejected.  These steps are
  repeated, except that after the first time the average includes all values,
  until no further pixels are rejected or there are fewer than three pixels.
  <P>
  After rejection the number of retained pixels is checked against the
  <I>nkeep</I> parameter.  If there are fewer pixels retained than specified
  by this parameter the pixels with the smallest residuals in absolute
  value are added back.  If there is more than one pixel with the same
  absolute residual (for example the two pixels about an average
  or median of two will have the same residuals) they are all added
  back even if this means more than <I>nkeep</I> pixels are retained.
  Note that the <I>nkeep</I> parameter only applies to the pixels used
  by the clipping rejection algorithm and does not apply to threshold
  rejection.
  <P>
  The  parameters affecting this algorithm are <I>reject</I> to select
  this algorithm, <I>mclip</I> to select the median or average for the
  center of the clipping, <I>nkeep</I> to limit the number of pixels
  rejected, <I>lsigma</I> and <I>hsigma</I> to select the
  clipping thresholds, and <I>sigscale</I> to set the threshold for
  making corrections to the sigma calculation for different spectrum scale
  factors.
  <P>
  AVSIGCLIP
  The averaged sigma clipping algorithm assumes that the sigma about the
  median or mean (average excluding the low and high values) is proportional
  to the square root of the median or mean at each point.  This is
  described by the equation:
  <P>
  <PRE>
  	sigma(column,line) = sqrt (gain(line) * signal(column,line))
  </PRE>
  <P>
  where the <I>estimated</I> signal is the mean or median (hopefully excluding
  any bad pixels) and the gain is the <I>estimated</I> proportionality
  constant having units of photons/data number.
  <P>
  This noise model is valid for spectra whose values are proportional to the
  number of photons recorded.  In effect this algorithm estimates a
  photon per data value gain for each spectrum.
  The gain proportionality factor is computed
  independently for each output spectrum by averaging the square of the residuals
  (at points having three or more input values) scaled by the median or
  mean.
  <P>
  Once the proportionality factor is determined, deviant pixels exceeding the
  specified thresholds are rejected at each point by estimating the sigma
  from the median or mean.  If any values are rejected the median or mean
  (this time not excluding the extreme values) is recomputed and further
  values rejected.  This is repeated until there are no further pixels
  rejected or the number of remaining input values falls below three.  Note
  that the proportionality factor is not recomputed after rejections.
  <P>
  If the spectra are scaled differently and the sigma scaling correction
  threshold is exceedd then a correction is made in the sigma
  calculations for these differences, again under the assumption that
  the noise in an spectra scales as the square root of the mean intensity.
  <P>
  After rejection the number of retained pixels is checked against the
  <I>nkeep</I> parameter.  If there are fewer pixels retained than specified
  by this parameter the pixels with the smallest residuals in absolute
  value are added back.  If there is more than one pixel with the same
  absolute residual (for example the two pixels about an average
  or median of two will have the same residuals) they are all added
  back even if this means more than <I>nkeep</I> pixels are retained.
  Note that the <I>nkeep</I> parameter only applies to the pixels used
  by the clipping rejection algorithm and does not apply to threshold
  rejection.
  <P>
  This algorithm works well for even a few input spectra.  It works better if
  the median is used though this is slower than using the average.  Note that
  if the spectra have a known read out noise and gain (the proportionality
  factor above) then the "<TT>ccdclip</TT>" algorithm is superior.  However, currently
  the CCD noise characteristics are not well propagated during extraction so
  this empirical algorithm is the one most likely to be useful.  The two
  algorithms are related in that the average sigma proportionality factor is
  an estimate of the gain.
  <P>
  The  parameters affecting this algorithm are <I>reject</I> to select
  this algorithm, <I>mclip</I> to select the median or average for the
  center of the clipping, <I>nkeep</I> to limit the number of pixels
  rejected, <I>lsigma</I> and <I>hsigma</I> to select the
  clipping thresholds, and <I>sigscale</I> to set the threshold for
  making corrections to the sigma calculation for different image scale
  factors.
  <P>
  PCLIP
  The percentile clipping algorithm is similar to sigma clipping using the
  median as the center of the distribution except that, instead of computing
  the sigma of the pixels from the CCD noise parameters or from the data
  values, the width of the distribution is characterized by the difference
  between the median value and a specified "<TT>percentile</TT>" pixel value.  This
  width is then multipled by the scale factors <I>lsigma</I> and <I>hsigma</I>
  to define the clipping thresholds above and below the median.  The clipping
  is not iterated.
  <P>
  The pixel values at each output point are ordered in magnitude and the
  median is determined.  In the case of an even number of pixels the average
  of the two middle values is used as the median value and the lower or upper
  of the two is the median pixel when counting from the median pixel to
  selecting the percentile pixel.  The parameter <I>pclip</I> selects the
  percentile pixel as the number (if the absolute value is greater
  than unity) or fraction of the pixels from the median in the ordered set.
  The direction of the percentile pixel from the median is set by the sign of
  the <I>pclip</I> parameter with a negative value signifying pixels with
  values less than the median.  Fractional values are internally converted to
  the appropriate number of pixels for the number of input spectra.  A minimum
  of one pixel and a maximum corresponding to the extreme pixels from the
  median are enforced.  The value used is reported in the log output.  Note
  that the same percentile pixel is used even if pixels have been rejected by
  nonoverlap or thresholding; for example, if the 3nd pixel below
  the median is specified then the 3rd pixel will be used whether there are
  10 pixels or 5 pixels remaining after the preliminary steps.
  <P>
  After rejection the number of retained pixels is checked against the
  <I>nkeep</I> parameter.  If there are fewer pixels retained than specified
  by this parameter the pixels with the smallest residuals in absolute
  value are added back.  If there is more than one pixel with the same
  absolute residual (for example the two pixels about an average
  or median of two will have the same residuals) they are all added
  back even if this means more than <I>nkeep</I> pixels are retained.
  Note that the <I>nkeep</I> parameter only applies to the pixels used
  by the clipping rejection algorithm and does not apply to threshold
  or bad pixel mask rejection.
  <P>
  Some examples help clarify the definition of the percentile pixel.  In the
  examples assume 10 pixels.  The median is then the average of the
  5th and 6th pixels.  A <I>pclip</I> value of 2 selects the 2nd pixel
  above the median (6th) pixel which is the 8th pixel.  A <I>pclip</I>
  value of -0.5 selects the point halfway between the median and the
  lowest pixel.  In this case there are 4 pixels below the median,
  half of that is 2 pixels which makes the percentile pixel the 3rd pixel.
  <P>
  The percentile clipping algorithm is most useful for clipping small
  excursions, such as the wings of bright lines when combining
  disregistered observations, that are missed when using
  the pixel values to compute a sigma.  It is not as powerful, however, as
  using the CCD noise parameters (provided they are accurately known) to clip
  about the median.  This algorithm is primarily used with direct images
  but remains available for spectra.
  <P>
  The  parameters affecting this algorithm are <I>reject</I> to select this
  algorithm, <I>pclip</I> to select the percentile pixel, <I>nkeep</I> to limit
  the number of pixels rejected, and <I>lsigma</I> and <I>hsigma</I> to select
  the clipping thresholds.
  <P>
  <P>
  GROW REJECTION
  <P>
  Neighbors of pixels rejected by the rejection algorithms
  may also be rejected.  The number of neighbors to be rejected on either
  side is specified by the <I>grow</I> parameter.
  <P>
  This rejection step is also checked against the <I>nkeep</I> parameter
  and only as many pixels as would not violate this parameter are
  rejected.  Unlike it's application in the rejection algorithms at
  this stage there is no checking on the magnitude of the residuals
  and the pixels retained which would otherwise be rejected are randomly
  selected.
  <P>
  <P>
  COMBINING
  <P>
  After all the steps of offsetting the input images, masking pixels,
  threshold rejection, scaling, and applying a rejection algorithms the
  remaining pixels are combined and output.  The pixels may be combined
  by computing the median or by computing a weighted average.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  Combine orders of echelle images.
  <P>
  <PRE>
  	cl&gt; scombine *.ec *%.ec%% group=images combine=sum
  </PRE>
  <P>
  2.  Combine all spectra using range syntax and scale by the exposure times.
  <P>
  <PRE>
  	cl&gt; names irs 10-42 &gt; irs.dat
  	cl&gt; scombine @irs.dat irscombine group=all scale=exptime
  </PRE>
  <P>
  3.  Combine spectra by apertures using exposure time scaling and weighting.
  <P>
  <PRE>
  	cl&gt; scombine *.ms combine.ms nout=ncombine.ms \\<BR>
  	&gt;&gt;&gt; group=apertures scale=exptime weights=exptime
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>SCOMBINE V2.10.3</B></DT>
  <! Sec='REVISIONS' Level=0 Label='SCOMBINE' Line='SCOMBINE V2.10.3'>
  <DD>The weighting was changed from using the square root of the exposure time
  or spectrum statistics to using the values directly.  This corresponds
  to variance weighting.  Other options for specifying the scaling and
  weighting factors were added; namely from a file or from a different
  image header keyword.  The <I>nkeep</I> parameter was added to allow
  controlling the maximum number of pixels to be rejected by the clipping
  algorithms.  The <I>snoise</I> parameter was added to include a sensitivity
  or scale noise component to the noise model.
  </DD>
  </DL>
  <DL>
  <DT><B>SCOMBINE V2.10</B></DT>
  <! Sec='REVISIONS' Level=0 Label='SCOMBINE' Line='SCOMBINE V2.10'>
  <DD>This task is new.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H3>Notes</H3>
  <! BeginSection: 'NOTES'>
  <UL>
  The pixel uncertainties and CCD noise model are not well propagated.  In
  particular it would be desirable to propagate the pixel uncertainties
  and CCD noise parameters from the initial CCD images.
  </UL>
  <! EndSection:   'NOTES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imcombine, odcombine, lscombine
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'NOTES' 'SEE ALSO'  >
  
