.. _fitskypars:

fitskypars — Edit the sky fitting parameters
============================================

**Package: apphot**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  fitskypars - edit the sky fitting algorithm parameters
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  fitskypars
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>salgorithm = "<TT>centroid</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='salgorithm' Line='salgorithm = "centroid"'>
  <DD>The sky fitting algorithm to be employed. The sky fitting options are:
  <DL>
  <DT><B>constant</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='constant' Line='constant'>
  <DD>Use a user supplied constant value <I>skyvalue</I> for the sky.
  This algorithm is useful for measuring large resolved objects on flat
  backgrounds such as galaxies or comments.
  </DD>
  </DL>
  <DL>
  <DT><B>file</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='file' Line='file'>
  <DD>Read sky values from a text file. This option is useful for importing
  user determined sky values into APPHOT.
  </DD>
  </DL>
  <DL>
  <DT><B>mean</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='mean' Line='mean'>
  <DD>Compute the mean of the sky pixel distribution. This algorithm is useful
  for computing sky values in regions with few background counts.
  </DD>
  </DL>
  <DL>
  <DT><B>median</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='median' Line='median'>
  <DD>Compute the median of the sky pixel distribution. This algorithm is a useful
  for computing sky values in regions with rapidly varying sky backgrounds
  and is a good alternative to "<TT>centroid</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>mode</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='mode' Line='mode'>
  <DD>Compute the mode of the sky pixel distribution using the computed mean and
  median.  This is the recommended algorithm for APPHOT users trying to
  measuring stellar objects in crowded stellar fields. Mode may not perform
  well in regions with rapidly varying sky backgrounds.
  </DD>
  </DL>
  <DL>
  <DT><B>centroid</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='centroid' Line='centroid'>
  <DD>Compute the intensity-weighted mean or centroid of the sky pixel histogram.
  This is the algorithm recommended for most APPHOT users. It is reasonably
  robust in rapidly varying and crowded regions.
  </DD>
  </DL>
  <DL>
  <DT><B>gauss</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='gauss' Line='gauss'>
  <DD>Fit a single Gaussian function to the sky pixel histogram using non-linear
  least-squares techniques.
  </DD>
  </DL>
  <DL>
  <DT><B>ofilter</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='ofilter' Line='ofilter'>
  <DD>Compute the sky using the optimal filtering algorithm and a triangular
  weighting function and the histogram of the sky pixels.
  </DD>
  </DL>
  <DL>
  <DT><B>crosscor</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='crosscor' Line='crosscor'>
  <DD>Compute the sky value using the cross-correlation function of the sky pixel
  histogram and a Gaussian noise function with a sigma equal to the
  computed sigma of the sky pixel distribution.
  </DD>
  </DL>
  <DL>
  <DT><B>histplot</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='histplot' Line='histplot'>
  <DD>Mark the peak of the histogram of the sky pixels on a plot of the histogram.
  This algorithm is useful for making careful interactive sky measurements
  for a small number of objects in complicated regions or for checking the
  behavior of other sky algorithms.
  </DD>
  </DL>
  <DL>
  <DT><B>radplot</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='radplot' Line='radplot'>
  <DD>Mark the sky value on a radial distribution plot of the sky pixels.
  This algorithm is useful for making careful interactive sky measurements
  for a small number of objects in complicated regions or for checking the
  behavior of other sky algorithms.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>annulus = 10.0  (scale units)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='annulus' Line='annulus = 10.0  (scale units)'>
  <DD>The inner radius of the annular sky fitting region in units of the DATAPARS
  scale parameter.
  </DD>
  </DL>
  <DL>
  <DT><B>dannulus = 10.0  (scale units)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dannulus' Line='dannulus = 10.0  (scale units)'>
  <DD>The width of the annular sky fitting region in units of the DATAPARS
  scale parameter.
  </DD>
  </DL>
  <DL>
  <DT><B>skyvalue</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='skyvalue' Line='skyvalue'>
  <DD>The constant for constant sky subtraction.
  </DD>
  </DL>
  <DL>
  <DT><B>smaxiter = 10</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='smaxiter' Line='smaxiter = 10'>
  <DD>The maximum number of iterations performed by the sky fitting algorithm.
  <I>Smaxiter</I> is required by the "<TT>gauss</TT>" and "<TT>ofilter</TT>" sky fitting algorithms.
  </DD>
  </DL>
  <DL>
  <DT><B>sloclip = 0.0 (percent)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sloclip' Line='sloclip = 0.0 (percent)'>
  <DD>The low-side clipping factor in percentage points of the total number of
  sky pixels.
  </DD>
  </DL>
  <DL>
  <DT><B>shiclip = 0.0 (percent)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='shiclip' Line='shiclip = 0.0 (percent)'>
  <DD>The high-side clipping factor in percentage points of the total number of
  sky pixels.
  </DD>
  </DL>
  <DL>
  <DT><B>snreject = 50</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='snreject' Line='snreject = 50'>
  <DD>The maximum number of pixel rejection cycles.
  </DD>
  </DL>
  <DL>
  <DT><B>sloject = 3.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sloject' Line='sloject = 3.0'>
  <DD>The ksigma low-side clipping factor for the pixel rejection  phase of the
  sky fitting algorithm. <I>sloreject</I> is in units of the computed sky
  sigma.
  </DD>
  </DL>
  <DL>
  <DT><B>shiject = 3.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='shiject' Line='shiject = 3.0'>
  <DD>The ksigma high-side clipping factor for the pixel rejection  phase of the
  sky fitting algorithm. <I>shireject</I> is in units of the computed sky
  sigma.
  </DD>
  </DL>
  <DL>
  <DT><B>khist = 3.0 </B></DT>
  <! Sec='PARAMETERS' Level=0 Label='khist' Line='khist = 3.0 '>
  <DD>The ksigma clipping factor for computing the histogram of the sky pixels.
  <I>Khist</I> is in units of the computed sky sigma.
  The computed histogram will be 2.0 * khist * sigma wide.
  </DD>
  </DL>
  <DL>
  <DT><B>binsize = 0.10</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='binsize' Line='binsize = 0.10'>
  <DD>The width of a single bin of the histogram of sky values.
  <I>Binsize</I> is in units of the computed sky sigma.
  </DD>
  </DL>
  <DL>
  <DT><B>smooth = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='smooth' Line='smooth = no'>
  <DD>Boxcar smooth the histogram before computing a sky value ?
  </DD>
  </DL>
  <DL>
  <DT><B>rgrow = 0.0  (scale units)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rgrow' Line='rgrow = 0.0  (scale units)'>
  <DD>The region growing radius for pixel rejection in the sky region, in units
  of the DATAPARS <I>scale</I> parameter. When a bad sky pixel is detected,
  all pixels within rgrow / scale will be rejected. If rgrow is 0.0
  region growing is not performed.
  </DD>
  </DL>
  <DL>
  <DT><B>mksky = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='mksky' Line='mksky = no'>
  <DD>Mark the sky annulus on the displayed image ? 
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The sky fitting algorithm parameters control the action of the sky fitting
  algorithms. The default parameter settings should give reasonable results in
  the majority of cases.  Several of the sky fitting parameters scale with
  image scale, <I>scale</I> which is data dependent. <I>Scale</I> is defined in
  the DATAPARS parameter set.
  <P>
  Sky pixels in an annular region of inner radius <I>annulus / scale</I> pixels
  and a width of <I>dannulus / scale</I> pixels are extracted from the IRAF image.
  If the <I>scale</I> parameter is defined in terms of the number of half-width
  at half-maximum of the point spread function per pixel, then single values of
  annulus and dannulus will work well for images with different seeing and
  detector characteristics.
  <P>
  Pixels outside of the good data range specified by <I>datamin</I> and
  <I>datamax</I> are rejected from the sky pixel distribution. After bad
  data rejection <I>Ploclip</I> and <I>phiclip</I> percent pixels are rejected
  from the low and high sides of the sorted pixel distribution before any
  sky fitting is done.
  <P>
  Sky values are computed using the sky fitting algorithm specified by
  <I>salgorithm</I>. The default value is "<TT>centroid</TT>". If <I>salgorithm</I>
  = "<TT>mean</TT>", "<TT>median</TT>" or "<TT>mode</TT>", the sky value is computed directly from the
  array of sky pixels.  The remaining sky fitting algorithms use the histogram
  of the object sky pixels. The computed histogram is <I>khist</I> * sigma wide
  with a bin width of <I>binsize</I> * sigma  where sigma is the computed
  standard deviation of the sky pixels for each object. If <I>smooth</I> = yes,
  boxcar smoothing is performed on the computed histogram before sky fitting.
  The mode of the histogram is  computed using, a non-linear least squares
  fit to a Gaussian (salgorithm = "<TT>gauss</TT>"), optimal filtering of the histogram
  (salgorithm = "<TT>ofilter</TT>"), computing the intensity weighted mean of the
  histogram (salgorithm = "<TT>centroid</TT>"), or by cross-correlation techniques 
  (salgorithm = "<TT>crosscor</TT>").
  <P>
  Two interactive methods of fitting sky are also available. If <I>salgorithm</I>
  is "<TT>radplot</TT>" or "<TT>histplot</TT>", the user must interactively set the value of the
  sky using a radial profile or a histogram profile plot.
  <P>
  Pixels which deviate from the sky value by more than <I>kreject</I> times the
  computed sky sigma are rejected from the fit. If <I>rgrow</I> &gt; 0, pixels
  within a radius of rgrow / scale of the rejected pixel are also rejected from
  the fit. The rejection procedure iterates until no further pixels are rejected,
  all pixels are rejected, or the maximum number of rejection cycles
  <I>snreject</I> iterations is reached.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. List the sky fitting parameters.
  <P>
  <PRE>
  	ap&gt; lpar fitskypars
  </PRE>
  <P>
  2. Edit the sky fitting parameters.
  <P>
  <PRE>
  	ap&gt; fitskypars
  </PRE>
  <P>
  3. Edit the FITSKYPARS parameters from within the PHOT task.
  <P>
  <PRE>
      da&gt; epar phot
  <P>
  	... edit a few phot parameters
  <P>
  	... move to the fitskypars parameter and type :e
  <P>
  	... edit the fitskypars parameters and type :wq
  <P>
  	... finish editing the phot parameters and type :wq
  </PRE>
  <P>
  4. Save the current FITSKYPARS parameter set in a text file skynite1.par.
  This can also be done from inside a higher level task as in the
  above example.
  <P>
  <PRE>
      da&gt; fitskypars
  <P>
  	... edit some parameters
  <P>
  	... type ":w skynite1.par"  from within epar
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  <P>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  radprof,fitsky,phot,wphot,polyphot
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
