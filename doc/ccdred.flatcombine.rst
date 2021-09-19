.. _flatcombine:

flatcombine: Combine and process flat field images
==================================================

**Package: ccdred**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  flatcombine -- Combine and process flat field images
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  flatcombine input
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input' -->
  <dd>List of flat field images to combine.  The <i>ccdtype</i> parameter
  may be used to select the flat field images from a list containing all
  types of data.
  </dd>
  </dl>
  <dl>
  <dt><b>output = <tt>"Flat"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='output' Line='output = "Flat"' -->
  <dd>Output flat field root image name.  The subset ID is appended.
  </dd>
  </dl>
  <dl>
  <dt><b>combine = <tt>"average"</tt> (average|median)</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='combine' Line='combine = "average" (average|median)' -->
  <dd>Type of combining operation performed on the final set of pixels (after
  rejection).  The choices are
  <tt>"average"</tt> or <tt>"median"</tt>.  The median uses the average of the two central
  values when the number of pixels is even.
  </dd>
  </dl>
  <dl>
  <dt><b>reject = <tt>"avsigclip"</tt> (none|minmax|ccdclip|crreject|sigclip|avsigclip|pclip)</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='reject' Line='reject = "avsigclip" (none|minmax|ccdclip|crreject|sigclip|avsigclip|pclip)' -->
  <dd>Type of rejection operation.  See <b>combine</b> for details.
  </dd>
  </dl>
  <dl>
  <dt><b>ccdtype = <tt>"flat"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='ccdtype' Line='ccdtype = "flat"' -->
  <dd>CCD image type to combine.  If no image type is given then all input images
  are combined.
  </dd>
  </dl>
  <dl>
  <dt><b>process = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='process' Line='process = yes' -->
  <dd>Process the input images before combining?
  </dd>
  </dl>
  <dl>
  <dt><b>subsets = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='subsets' Line='subsets = yes' -->
  <dd>Combine images by subset parameter?  If yes then the input images are
  grouped by subset parameter and each group combined into a separate output
  image.  The subset identifier is appended to the output and sigma image
  names.  See <b>subsets</b> for more on the subset parameter.  This is generally
  used with flat field images.
  </dd>
  </dl>
  <dl>
  <dt><b>delete = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='delete' Line='delete = no' -->
  <dd>Delete input images after combining?  Only those images combined are deleted.
  </dd>
  </dl>
  <dl>
  <dt><b>clobber = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='clobber' Line='clobber = no' -->
  <dd>Clobber existing output images?
  </dd>
  </dl>
  <dl>
  <dt><b>scale = <tt>"mode"</tt> (none|mode|median|mean|exposure)</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='scale' Line='scale = "mode" (none|mode|median|mean|exposure)' -->
  <dd>Multiplicative image scaling to be applied.  The choices are none, scale
  by the mode, median, or mean of the specified statistics section, or scale
  by the exposure time given in the image header.
  </dd>
  </dl>
  <dl>
  <dt><b>statsec = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='statsec' Line='statsec = ""' -->
  <dd>Section of images to use in computing image statistics for scaling.
  If no section is given then the entire region of the image is
  sampled (for efficiency the images are sampled if they are big enough).
  </dd>
  </dl>
  <p style="text-align:center">Algorithm Parameters
  
  </p>
  <dl>
  <dt><b>nlow = 1,  nhigh = 1 (minmax)</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='nlow' Line='nlow = 1,  nhigh = 1 (minmax)' -->
  <dd>The number of low and high pixels to be rejected by the <tt>"minmax"</tt> algorithm.
  </dd>
  </dl>
  <dl>
  <dt><b>nkeep = 1</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='nkeep' Line='nkeep = 1' -->
  <dd>The minimum number of pixels to retain or the maximum number to reject
  when using the clipping algorithms (ccdclip, crreject, sigclip,
  avsigclip, or pclip).  When given as a positive value this is the minimum
  number to keep.  When given as a negative value the absolute value is
  the maximum number to reject.  This is actually converted to a number
  to keep by adding it to the number of images.
  </dd>
  </dl>
  <dl>
  <dt><b>mclip = yes (ccdclip, crreject, sigclip, avsigcliip)</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='mclip' Line='mclip = yes (ccdclip, crreject, sigclip, avsigcliip)' -->
  <dd>Use the median as the estimate for the true intensity rather than the
  average with high and low values excluded in the <tt>"ccdclip"</tt>, <tt>"crreject"</tt>,
  <tt>"sigclip"</tt>, and <tt>"avsigclip"</tt> algorithms?  The median is a better estimator
  in the presence of data which one wants to reject than the average.
  However, computing the median is slower than the average.
  </dd>
  </dl>
  <dl>
  <dt><b>lsigma = 3., hsigma = 3. (ccdclip, crreject, sigclip, avsigclip, pclip)</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='lsigma' Line='lsigma = 3., hsigma = 3. (ccdclip, crreject, sigclip, avsigclip, pclip)' -->
  <dd>Low and high sigma clipping factors for the <tt>"ccdclip"</tt>, <tt>"crreject"</tt>, <tt>"sigclip"</tt>,
  <tt>"avsigclip"</tt>, and <tt>"pclip"</tt> algorithms.  They multiply a <tt>"sigma"</tt> factor
  produced by the algorithm to select a point below and above the average or
  median value for rejecting pixels.  The lower sigma is ignored for the
  <tt>"crreject"</tt> algorithm.
  </dd>
  </dl>
  <dl>
  <dt><b>rdnoise = <tt>"0."</tt>, gain = <tt>"1."</tt>, snoise = <tt>"0."</tt> (ccdclip, crreject)</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='rdnoise' Line='rdnoise = "0.", gain = "1.", snoise = "0." (ccdclip, crreject)' -->
  <dd>CCD readout noise in electrons, gain in electrons/DN, and sensitivity noise
  as a fraction.  These parameters are used with the <tt>"ccdclip"</tt> and <tt>"crreject"</tt>
  algorithms.  The values may be either numeric or an image header keyword
  which contains the value.
  </dd>
  </dl>
  <dl>
  <dt><b>pclip = -0.5 (pclip)</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='pclip' Line='pclip = -0.5 (pclip)' -->
  <dd>Percentile clipping algorithm parameter.  If greater than
  one in absolute value then it specifies a number of pixels above or
  below the median to use for computing the clipping sigma.  If less
  than one in absolute value then it specifies the fraction of the pixels
  above or below the median to use.  A positive value selects a point
  above the median and a negative value selects a point below the median.
  The default of -0.5 selects approximately the quartile point.
  See <b>combine</b> for further details.
  </dd>
  </dl>
  <dl>
  <dt><b>blank = 1.</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='blank' Line='blank = 1.' -->
  <dd>Output value to be used when there are no pixels.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The flat field images in the input image list are combined.  If there
  is more than one subset (such as a filter or grating) then the input
  flat field images are grouped by subset and an combined separately.
  The input images may be processed first if desired.  However if all
  zero level bias effects are linear then this is not necessary and some
  processing time may be saved.  The original images may be deleted
  automatically if desired.  The output pixel datatype will be real.
  </p>
  <p>
  This task is a script which applies <b>ccdproc</b> and <b>combine</b>.  The
  parameters and combining algorithms are described in detail in the help for
  <b>combine</b>.  This script has default parameters specifically set for
  flat field images and simplifies the combining parameters.  There are other
  combining options not included in this task.  For these additional
  features, such as thresholding, offseting, masking, and projecting, use
  <b>combine</b>.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. The image data contains four flat field images for three filters.
  To automatically select them and combine them as a background job
  using the default combining algorithm:
  </p>
  <p>
      cl&gt; flatcombine ccd*.imh&amp;
  </p>
  <p>
  The final images are <tt>"FlatV"</tt>, <tt>"FlatB"</tt>, and <tt>"FlatR"</tt>.
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  ccdproc, combine, subsets
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
