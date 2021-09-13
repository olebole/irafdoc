fitskypars — Edit the sky fitting algorithm parameters
======================================================

**Package: daophot**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>fitskypars (May00)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.digiphot.daophot</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>fitskypars (May00)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>fitskypars</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  fitskypars - edit the sky fitting algorithm parameters
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  fitskypars
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_salgorithm">salgorithm = "<TT>mode</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='salgorithm' Line='salgorithm = "mode"'>
  <DD>The sky fitting algorithm.  The sky fitting options are:
  <DL>
  <DT><B><A NAME="l_constant">constant</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='constant' Line='constant'>
  <DD>Use a user supplied constant sky value.
  This algorithm is useful for measuring large resolved objects on flat
  backgrounds such as galaxies or comets.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_file">file</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='file' Line='file'>
  <DD>Read sky values from a text file. This option is useful for importing
  user determined sky values into DAOPHOT.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_mean">mean</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='mean' Line='mean'>
  <DD>Compute the mean of the sky pixel distribution. This algorithm is useful
  for computing sky values in regions with few background counts.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_median">median</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='median' Line='median'>
  <DD>Compute the median of the sky pixel distribution. This algorithm is a useful
  for computing sky values in regions with rapidly varying sky backgrounds
  and is a good alternative to "<TT>centroid</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_mode">mode</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='mode' Line='mode'>
  <DD>Compute the mode of the sky pixel distribution using the mean and median.
  This is the recommended algorithm for DAOPHOT users measuring stellar objects in
  crowded stellar fields. Mode may not perform well in regions with
  rapidly varying sky backgrounds.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_centroid">centroid</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='centroid' Line='centroid'>
  <DD>Compute the intensity weighted mean of the sky pixel histogram. This algorithm
  is reasonably robust in regions with rapidly varying or crowded sky backgrounds
  and is a good alternative to "<TT>median</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_gauss">gauss</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='gauss' Line='gauss'>
  <DD>Fit a Gaussian function to the sky pixel histogram using non-linear least-
  squares techniques to determine the peak. 
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ofilter">ofilter</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='ofilter' Line='ofilter'>
  <DD>Optimally filter the sky pixel histogram using a triangular weighting
  function to determine the peak.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_crosscor">crosscor</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='crosscor' Line='crosscor'>
  <DD>Compute the peak of the cross-correlation function of the pixel distribution
  and a Gaussian noise function to determine the peak.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_histplot">histplot</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='histplot' Line='histplot'>
  <DD>Mark the peak of the sky pixel histogram with the graphics cursor.
  This algorithm is useful for making careful interactive sky measurements
  for a small number of objects in complicated regions or for checking the
  behavior of other sky algorithms. 
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_radplot">radplot</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='radplot' Line='radplot'>
  <DD>Mark the sky level on a radial profile plot with the graphics cursor.
  This algorithm is useful for making careful interactive sky measurements
  for a small number of objects in complicated regions or for checking the
  behavior of other sky algorithms. 
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_annulus">annulus = 10.0  (scale units)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='annulus' Line='annulus = 10.0  (scale units)'>
  <DD>The inner radius of the annular sky fitting region in units of the DATAPARS
  scale parameter.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_dannulus">dannulus = 10.0  (scale units)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dannulus' Line='dannulus = 10.0  (scale units)'>
  <DD>The width of the annular sky fitting region in units of the DATAPARS scale
  parameter.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_skyvalue">skyvalue = 0.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='skyvalue' Line='skyvalue = 0.0'>
  <DD>The constant for constant sky subtraction.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_smaxiter">smaxiter = 10</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='smaxiter' Line='smaxiter = 10'>
  <DD>The maximum number of iterations performed by the sky fitting algorithm.
  Smaxiter is required by the "<TT>gauss</TT>" and "<TT>ofilter</TT>" sky fitting algorithms.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_sloclip">sloclip = 0.0, shiclip = 0.0 (percent)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sloclip' Line='sloclip = 0.0, shiclip = 0.0 (percent)'>
  <DD>The high and low side clipping parameters in percent of the total number
  of pixels. If either of these parameters &gt; 0.0 then the specified
  percentage of the pixels will be removed from the sky pixel distribution
  before any sky fitting is done.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_snreject">snreject = 50</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='snreject' Line='snreject = 50'>
  <DD>The maximum number of sky pixel rejection cycles.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_sloreject">sloreject = 3.0, shireject = 3.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sloreject' Line='sloreject = 3.0, shireject = 3.0'>
  <DD>The k-sigma clipping factors for the pixel rejection  phase of the
  sky fitting algorithm. Sloreject and shireject are in units of the
  computed sky sigma.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_khist">khist = 3.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='khist' Line='khist = 3.0'>
  <DD>The k-sigma clipping factor for computing the sky pixels histogram. Khist is in
  units of sigma of the local sky pixel distribution.  The histogram will be
  2.0 * khist * sigma wide.  Khist is used by the "<TT>centroid</TT>", "<TT>gauss</TT>",
  "<TT>crosscor</TT>", "<TT>ofilter</TT>", and "<TT>histplot</TT>" sky fitting algorithms.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_binsize">binsize = 0.10</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='binsize' Line='binsize = 0.10'>
  <DD>The width of a single bin of the sky pixel histogram.  Binsize is in units of
  the sigma of the local sky pixel distribution. Binsize is used by the
  "<TT>centroid</TT>", "<TT>gauss</TT>", "<TT>crosscor</TT>", "<TT>ofilter</TT>", and "<TT>histplot</TT>" sky fitting
  algorithms.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_smooth">smooth = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='smooth' Line='smooth = no'>
  <DD>Boxcar smooth the sky pixel histogram before computing a sky value.
  Smooth is used by the "<TT>centroid</TT>", "<TT>gauss</TT>", "<TT>crosscor</TT>", "<TT>ofilter</TT>", and
  "<TT>histplot</TT>" sky fitting algorithms.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_rgrow">rgrow = 0.0  (scale units)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rgrow' Line='rgrow = 0.0  (scale units)'>
  <DD>The region growing radius for pixel rejection in the sky region in units
  of the DATAPARS scale parameter. When a bad sky_pixel is detected, all pixels
  within rgrow / scale pixels of the bad pixel will be rejected. If rgrow is
  0.0 region growing is disabled.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_mksky">mksky = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='mksky' Line='mksky = no'>
  <DD>Mark the sky annuli on the displayed image ?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The sky fitting algorithm parameters control the action of the sky fitting
  algorithms. The default parameter settings should give reasonable results in
  the majority of cases.  Several of the sky fitting parameters scale with
  image scale, <I>scale</I> which is data dependent.
  <I>Scale</I> is defined in the DATAPARS parameter set.
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
  (salgorithm = "<TT>ofilter</TT>"), computing the centroid of the histogram
  (salgorithm = "<TT>centroid</TT>"), or by cross-correlation techniques
  (salgorithm = "<TT>crosscor</TT>").
  <P>
  Two interactive methods of fitting sky are also available. If <I>salgorithm</I>
  is "<TT>radplot</TT>" or "<TT>histplot</TT>", the user must interactively set
  the value of the sky using a radial profile or a histogram plot.
  <P>
  Pixels which deviate from the sky value by more than <I>kreject times the
  computed sky sigma are rejected from the fit. If fIrgrow</I> &gt; 0, pixels
  within a radius of rgrow / scale of the rejected pixel are also rejected from
  the fit. The rejection procedure iterates until no further pixels are rejected,
  all pixels are rejected, or the maximum number of rejection cycles
  <I>snreject</I> iterations is reached.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. List the sky fitting parameters.
  <P>
  <PRE>
  	da&gt; lpar fitskypars
  </PRE>
  <P>
  2. Edit the sky fitting parameters.
  <P>
  <PRE>
  	da&gt; fitskypars
  </PRE>
  <P>
  3. Edit the FITSKYPARS parameters from with the PHOT task.
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
      da&gt; epar fitskypars
  <P>
  	... type ":w skynite1.par"  from within epar
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_time_requirements">TIME REQUIREMENTS</A></H2>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  epar,lpar,datapars,phot
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>