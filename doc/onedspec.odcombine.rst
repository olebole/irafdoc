odcombine — Combine spectra having different wavelength ranges (new)
====================================================================

**Package: onedspec**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>odcombine (Apr04)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>onedspec</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>odcombine (Apr04)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>odcombine</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  odcombine -- Combine spectra using various algorithms
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage_">USAGE	</A></H2>
  <! BeginSection: 'USAGE	'>
  <UL>
  odcombine input output
  </UL>
  <! EndSection:   'USAGE	'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of input images containing spectra to be combined.  The spectra
  in the images to be combined are selected with the <I>apertures</I> and
  <I>group</I> parameters.  Only the primary spectrum is combined and
  the associated band spectra are ignored.  This task does not work on
  higher dimensional spectra data.  To apply it first use a task to
  extract it to 1D spectra.  The simplest method is <B>scopy</B>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>List of output images to be created containing the combined spectra.  If
  the grouping option is "<TT>all</TT>" then only one output image is created with the
  specified name.  If the grouping option is "<TT>images</TT>" then there will be one
  output image for each input image and the output list must match the input
  list in number.  If the grouping option is "<TT>apertures</TT>" then only one output
  root name is specified and there will be one output image for each selected
  aperture.  In this case the output images will have a name formed from the
  root name and a four digit aperture number extension.  In all cases the
  output images contain a single 1D spectrum.  Other tasks, such as
  <B>scopy</B>, may be used to pack the spectra into a single file.
  </DD>
  </DL>
  <P>
  <P>
  There are a number of additional optional output files that may be produced.
  The lists are handled in the same was as for the primary output; i.e.
  depending on the grouping a single name, root name, or a matching list
  is specified.
  <DL>
  <DT><B><A NAME="l_headers">headers = "<TT></TT>" (optional)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='headers' Line='headers = "" (optional)'>
  <DD>Optional output multiextension FITS file(s).  The extensions are dataless
  headers from each input image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_bpmasks">bpmasks = "<TT></TT>" (optional)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='bpmasks' Line='bpmasks = "" (optional)'>
  <DD>Optional output bad pixel mask(s) with good values of 0 and bad values of
  1.  Output pixels are marked as bad when no input pixels contributed to the
  output pixel.  The file name is also added to the output image header under
  the keyword BPM.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_rejmask">rejmask = "<TT></TT>" (optional)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rejmask' Line='rejmask = "" (optional)'>
  <DD>Optional output mask file(s) identifying rejected or excluded pixels.  The
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
  <DT><B><A NAME="l_nrejmasks">nrejmasks = "<TT></TT>" (optional)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nrejmasks' Line='nrejmasks = "" (optional)'>
  <DD>Optional output pixel mask(s) giving the number of input pixels rejected or
  excluded from the input images.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_expmasks">expmasks = "<TT></TT>" (optional)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='expmasks' Line='expmasks = "" (optional)'>
  <DD>Optional output exposure mask(s) giving the sum of the exposure values of
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
  <DT><B><A NAME="l_sigma">sigma = "<TT></TT>" (optional)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sigma' Line='sigma = "" (optional)'>
  <DD>Optional output sigma image(s).  The sigma is the standard deviation,
  corrected for a finite population, of the input pixel values (excluding
  rejected pixels) about the output combined pixel values.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_logfile">logfile = "<TT>STDOUT</TT>" (optional)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logfile' Line='logfile = "STDOUT" (optional)'>
  <DD>Optional output log file.  If no file is specified then no log information is
  produced.  The special filename "<TT>STDOUT</TT>" prints log information to the
  terminal.
  </DD>
  </DL>
  <P>
  <P>
  <CENTER>Grouping Parameters
  
  </CENTER><BR>
  <DL>
  <DT><B><A NAME="l_apertures">apertures = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='apertures' Line='apertures = ""'>
  <DD>List of apertures to be selected for combining.  If none is specified
  then all apertures are selected.  The syntax is a blank or comma separated
  list of aperture numbers or hypen separated aperture ranges.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_group">group = "<TT>apertures</TT>" (all|images|apertures)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='group' Line='group = "apertures" (all|images|apertures)'>
  <DD>Option for grouping input spectra for combining (after selection by aperture)
  from one or more input images.  The options are:
  <DL>
  <DT><B><A NAME="l_">"<TT>all</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"all"'>
  <DD>Combine all spectra from all images in the input list into a single output
  spectrum.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">"<TT>images</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"images"'>
  <DD>Combine all spectra in each input image into a single spectrum in
  separate output images.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">"<TT>apertures</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"apertures"'>
  <DD>Combine all spectra of the same aperture from all input images and put it
  into an output image with specified root name and a four digit aperture
  number extension.
  </DD>
  </DL>
  </DD>
  </DL>
  <P>
  <P>
  <CENTER>Dispersion Matching Parameters
  
  </CENTER><BR>
  <DL>
  <DT><B><A NAME="l_first">first = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='first' Line='first = no'>
  <DD>Use the first input spectrum of each set to be combined to define the
  dispersion coordinates for combining and output?  If yes then all other
  spectra to be combined will be interpolated to the dispersion of this
  spectrum and that dispersion defines the dispersion of the
  output spectrum.  If no, then all the spectra are interpolated to a linear
  dispersion as determined by the following parameters.  The interpolation
  type is set by the package parameter <I>interp</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_w1">w1 = INDEF, w2=INDEF, dw = INDEF, nw = INDEF, log = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='w1' Line='w1 = INDEF, w2=INDEF, dw = INDEF, nw = INDEF, log = no'>
  <DD>The output linear or log linear wavelength scale if the dispersion of the
  first spectrum is not used.  INDEF values are filled in from the maximum
  wavelength range and minimum dispersion of the spectra to be combined.  The
  parameters are aways specified in linear wavelength even when the log
  parameter is set to produce constant pixel increments in the log of the
  wavelength.  The dispersion is interpreted in that case as the difference
  in the log of the endpoints divided by the number of pixel.
  </DD>
  </DL>
  <P>
  <P>
  <CENTER>Combining Parameters
  
  </CENTER><BR>
  <DL>
  <DT><B><A NAME="l_combine">combine = "<TT>average</TT>" (average|median|sum)</A></B></DT>
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
  <DT><B><A NAME="l_reject">reject = "<TT>none</TT>" (none|minmax|ccdclip|crreject|sigclip|avsigclip|pclip)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='reject' Line='reject = "none" (none|minmax|ccdclip|crreject|sigclip|avsigclip|pclip)'>
  <DD>Type of rejection operation performed on the pixels remaining after offsetting,
  masking and thresholding.  The algorithms are described in the
  help page for <B>imcombine</B>.  The rejection choices are:
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
  <DT><B><A NAME="l_outtype">outtype = "<TT>real</TT>" (none|short|ushort|integer|long|real|double)</A></B></DT>
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
  <DT><B><A NAME="l_outlimits">outlimits = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outlimits' Line='outlimits = ""'>
  <DD>Output region limits specified as a pair of whitespace separated pixel
  values.
  </DD>
  </DL>
  <P>
  <P>
  <CENTER>Masking Parameters
  
  </CENTER><BR>
  <DL>
  <DT><B><A NAME="l_smaskformat">smaskformat = "<TT>bpmspectrum</TT>" (bpmspectrum|bpmpixel)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='smaskformat' Line='smaskformat = "bpmspectrum" (bpmspectrum|bpmpixel)'>
  <DD>When a mask is applied it must be matched to the input spectrum.  If the
  value of this parameter is "<TT>bpmspectrum</TT>" the mask file is assumed to have a
  spectral file structure with aperture and dispersion information.  The mask
  spectrum is matched to the input spectrum by aperture number and is
  rebinned from its dispersion to match the rebinned dispersion of the input
  spectrum.  If the value is "<TT>bpmpixel</TT>" the mask file is assumed to have
  minimal header information and the pixel information is matched to the
  input image pixels.  This means the mask pixels are extracted from the same
  line as the input spectrum and the mask pixels are resampled in the same
  way as the input spectrum pixels.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_smasktype">smasktype = "<TT>none</TT>" (none|goodvalue|badvalue|goodbits|badbit)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='smasktype' Line='smasktype = "none" (none|goodvalue|badvalue|goodbits|badbit)'>
  <DD>Type of pixel masking to use.  If "<TT>none</TT>" or "<TT></TT>" then no pixel masking is
  done even if an image has an associated  pixel mask.  The other choices are
  to select the value in the pixel mask to be treated as good (goodvalue) or
  bad (badvalue) or the bits (specified as a value) to be treated as good
  (goodbits) or bad (badbits).  The pixel mask filename is specified by the
  image header keyword "<TT>BPM</TT>".  Note that if the input image contains
  multiple spectra then the mask file must also contain at least the
  selected apertures if the mask format is "<TT>bpmspectrum</TT>" or matching
  image dimensions if the mask format is "<TT>bpmpixel</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_maskvalue">maskvalue = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maskvalue' Line='maskvalue = 0'>
  <DD>Mask value used with the <I>masktype</I> parameter.  If the mask type
  selects good or bad bits the value may be specified using IRAF notation
  for decimal, octal, or hexadecimal; i.e 12, 14b, 0cx to select bits 3
  and 4.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_blank">blank = 0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='blank' Line='blank = 0.'>
  <DD>Output value to be used when there are no pixels.
  </DD>
  </DL>
  <P>
  <P>
  <CENTER>Scaling/Weighting Parameters
  
  </CENTER><BR>
  <P>
  The following scaling and weighting parameters have the following behavior
  and constraints, which are particularly relevant to multispec formats where
  multiple spectra are contained in an image with a single image header.
  When using image statistics these are calculated from the rebinned spectra
  being combined as expected.  When using header keywords the values will be
  the same for all spectra from the same input file.
  <P>
  When using a file then the list will be applied repeatedly to each
  group being combined.  If the grouping is by aperture then the values will
  be matched in the order of the input images.  Note that if an image does
  not contain a specified aperture the ordering will be wrong.  If the
  grouping is by image then the file will be matched to the spectra in the
  order of the apertures in the image.  And if the grouping is "<TT>all</TT>" then the
  list is matched in the order of the images and apertures within the
  images with the apertures in an image varying first.
  <P>
  <DL>
  <DT><B><A NAME="l_scale">scale = "<TT>none</TT>" (none|mode|median|mean|exposure|@&lt;file&gt;|!&lt;keyword&gt;)</A></B></DT>
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
  <DT><B><A NAME="l_zero">zero = "<TT>none</TT>" (none|mode|median|mean|@&lt;file&gt;|!&lt;keyword&gt;)</A></B></DT>
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
  <DT><B><A NAME="l_weight">weight = "<TT>none</TT>" (none|mode|median|mean|exposure|@&lt;file&gt;|!&lt;keyword&gt;)</A></B></DT>
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
  <DT><B><A NAME="l_statsec">statsec = "<TT></TT>"</A></B></DT>
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
  <DT><B><A NAME="l_"> expname = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line=' expname = ""'>
  <DD>Image header keyword to be used with the exposure scaling and weighting
  options.  Also if an exposure keyword is specified that keyword will be
  added to the output image using a weighted average of the input exposure
  values.
  </DD>
  </DL>
  <P>
  <P>
  <CENTER>Algorithm Parameters
  
  </CENTER><BR>
  <DL>
  <DT><B><A NAME="l_lthreshold">lthreshold = INDEF, hthreshold = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lthreshold' Line='lthreshold = INDEF, hthreshold = INDEF'>
  <DD>Low and high thresholds to be applied to the input pixels.  This is done
  before any scaling, rejection, and combining.  If INDEF the thresholds
  are not used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nlow">nlow = 1,  nhigh = 1 (minmax)</A></B></DT>
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
  <DT><B><A NAME="l_nkeep">nkeep = 1</A></B></DT>
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
  <DT><B><A NAME="l_mclip">mclip = yes (ccdclip, crreject, sigclip, avsigcliip)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='mclip' Line='mclip = yes (ccdclip, crreject, sigclip, avsigcliip)'>
  <DD>Use the median as the estimate for the true intensity rather than the
  average with high and low values excluded in the "<TT>ccdclip</TT>", "<TT>crreject</TT>",
  "<TT>sigclip</TT>", and "<TT>avsigclip</TT>" algorithms?  The median is a better estimator
  in the presence of data which one wants to reject than the average.
  However, computing the median is slower than the average.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_lsigma">lsigma = 3., hsigma = 3. (ccdclip, crreject, sigclip, avsigclip, pclip)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lsigma' Line='lsigma = 3., hsigma = 3. (ccdclip, crreject, sigclip, avsigclip, pclip)'>
  <DD>Low and high sigma clipping factors for the "<TT>ccdclip</TT>", "<TT>crreject</TT>", "<TT>sigclip</TT>",
  "<TT>avsigclip</TT>", and "<TT>pclip</TT>" algorithms.  They multiply a "<TT>sigma</TT>" factor
  produced by the algorithm to select a point below and above the average or
  median value for rejecting pixels.  The lower sigma is ignored for the
  "<TT>crreject</TT>" algorithm.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_rdnoise">rdnoise = "<TT>0.</TT>", gain = "<TT>1.</TT>", snoise = "<TT>0.</TT>" (ccdclip, crreject)</A></B></DT>
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
  <DT><B><A NAME="l_sigscale">sigscale = 0.1 (ccdclip, crreject, sigclip, avsigclip)</A></B></DT>
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
  <DT><B><A NAME="l_pclip">pclip = -0.5 (pclip)</A></B></DT>
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
  <DT><B><A NAME="l_grow">grow = 0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='grow' Line='grow = 0.'>
  <DD>Radius in pixels for additional pixel to be rejected in an image with a
  rejected pixel from one of the rejection algorithms.  This applies only to
  pixels rejected by one of the rejection algorithms and not the masked or
  threshold rejected pixels.
  </DD>
  </DL>
  <P>
  The following parameters are internal to the task and not user parameters:
  <P>
  <PRE>
      offsets, masktype, maskvalue
  </PRE>
  <P>
  <CENTER>Environment Variables
  
  </CENTER><BR>
  <P>
  <DL>
  <DT><B><A NAME="l_">&lt;package&gt;.interp</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='&lt;package&gt;.interp'>
  <DD>When the spectra have to be interpolated to a common pixel sampling
  the "<TT>interp</TT>" parameter from the package from which ODCOMBINE is used
  will be used.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <B>Odcombine</B> combines input spectra by interpolating them (if necessary)
  to a common dispersion sampling, rejecting pixels exceeding specified low
  and high thresholds or identified as bad in a bad pixel mask, scaling them
  in various ways, applying a rejection algorithm based on known or empirical
  noise statistics, and computing the sum, weighted average, or median of the
  remaining pixels.  Note that the "<TT>sum</TT>" option is the direct summation of
  the pixels and does not perform any rejection or scaling of the data
  regardless of the parameter settings.
  <P>
  The input spectra are specified using an image list in which each image
  may contain multiple spectra.  The set of spectra may be restricted
  by the <I>aperture</I> parameter to specific apertures.  The set of input
  spectra may then be grouped using the <I>group</I> parameter and each
  group combined separately into final output spectra.  The grouping
  options are to select all the input spectra regardless of the input
  image or aperture number, select all spectra of the same aperture,
  or select all the spectra from the same input image.
  <P>
  The output consists of one image for each combined group.  The output
  images and combined spectra inherit the header parameters from the first
  spectrum in the combined group.  There are a number of additional optional
  outputs provided.  The optional logfile lists parameters, the spectra
  combined for each group, scaling, weights, etc., and the output names.
  <P>
  The spectral combining is done using pixels at common dispersion
  coordinates rather than physical or logical pixel coordinates.  If the
  spectra to be combined do not have identical dispersion coordinates then
  the spectra are interpolated to a common dispersion sampling before
  combining.  The interpolation conserves pixel values rather pixel fluxes.
  This means that flux calibrated data is treated correctly and that
  spectra in counts are not corrected in the interpolation for changes in
  pixel widths.  The default interpolation function is a 5th order
  polynomial.  The choice of interpolation type is made with the package
  parameter "<TT>interp</TT>".  It may be set to "<TT>nearest</TT>", "<TT>linear</TT>", "<TT>spline3</TT>",
  "<TT>poly5</TT>", or "<TT>sinc</TT>".  Remember that this applies to all tasks which might
  need to interpolate spectra in the <B>onedspec</B> and associated packages.
  For a discussion of interpolation types see <B>onedspec</B>.
  <P>
  There are two choices for the common dispersion coordinate sampling. If the
  <I>first</I> parameter is set then the dispersion sampling of the first
  spectrum is used.  If this dispersion is nonlinear then the end points and
  number of pixels are preserved and a linear dispersion is applied between
  the endpoints.  If the parameter is not set then the user specified linear
  or log linear dispersion system is used.  Any combination of starting
  wavelength, ending wavelength, wavelength per pixel, and number of output
  pixels may be specified.  Unspecified values will default to reasonable
  values based on the minimum or maximum wavelengths of all spectra, the
  minimum dispersion, and the number of pixels needed to satisfy the other
  parameters.  If the parameters overspecify the linear system then the
  ending wavelength is adjusted based on the other parameters.  Note that for
  a log linear system the wavelengths are still specified in nonlog units and
  the dispersion is finally recalculated using the difference of the log
  wavelength endpoints divided by the number pixel intervals (the number of
  pixels minus one).
  <P>
  This task is layered on top of the <B>imcombine</B> task.  What happens
  is that the spectra for each group to be combined is extracted from
  the input, resampled to a common dispersion, and the resulting spectra
  written to temporary images, one per spectrum.  The temporary images
  are written to the current working directory with names begining with
  "<TT>tmp</TT>".  The same is done with any bad pixel masks.  Then the list of
  images are combined using the IMCOMBINE algorithms.  When the combining
  is completed the temporary images are removed.  If ODCOMBINE aborts
  for some reason these file may be left behind and the user may delete
  them.  Details of what IMCOMBINE does are presented separate under the
  help topic for the IMCOMBINE task.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  Combine orders of echelle images.
  <P>
  <PRE>
  	cl&gt; odcombine *.ec *%.ec%% group=images combine=sum
  </PRE>
  <P>
  2.  Combine all spectra using range syntax and scale by the exposure times.
  <P>
  <PRE>
  	cl&gt; names irs 10-42 &gt; irs.dat
  	cl&gt; odcombine @irs.dat irscombine group=all scale=exptime
  </PRE>
  <P>
  3.  Combine spectra by apertures using exposure time scaling and weighting.
  <P>
  <PRE>
  	cl&gt; odcombine *.ms comb1d \\<BR>
  	&gt;&gt;&gt; group=apertures scale=exptime weights=exptime
  	cl&gt; scopy comb1d.* comb.ms format="multispec"
  	cl&gt; imdel comb1d.*
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_revisions">REVISIONS</A></H2>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_ODCOMBINE">ODCOMBINE V2.12.3</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='ODCOMBINE' Line='ODCOMBINE V2.12.3'>
  <DD>This is a new version that incorporates most of the features of
  IMCOMBINE.
  <P>
  In addition to the many new features, including application of pixel
  masks, the following functional differences from the old SCOMBINE
  are noted.
  <P>
  <DL>
  <DT><B><A NAME="l_"></A></B></DT>
  <! Sec='REVISIONS' Level=1 Label='' Line=''>
  <DD>The output is always a single spectrum per image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_"></A></B></DT>
  <! Sec='REVISIONS' Level=1 Label='' Line=''>
  <DD>The "<TT>first</TT>" option does not allow rebinning to a non-linear dispersion.
  Instead, it rebins to the nearest linear dispersion matching the first
  spectrum.
  </DD>
  </DL>
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imcombine, scombine, scopy, sarith, lscombine
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>