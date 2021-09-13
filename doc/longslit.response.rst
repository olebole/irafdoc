.. _response:

response — Determine response calibration
=========================================

**Package: longslit**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  response -- Determine response calibrations
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  response calibration normalization response
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>calibration</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='calibration' Line='calibration'>
  <DD>Images to use in determining response calibrations.  These are
  generally quartz continuum spectra.  An image section may be used to select
  only a portion of the image.
  </DD>
  </DL>
  <DL>
  <DT><B>normalization</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='normalization' Line='normalization'>
  <DD>Images to use determining the normalization spectrum.  In almost all cases
  the normalization images are the same as the calibration images or a
  subsection of the calibration images.
  </DD>
  </DL>
  <DL>
  <DT><B>responses</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='responses' Line='responses'>
  <DD>Response calibration images to be created.  Each response image is paired
  with a calibration image.  If the image exists then it will be modified
  otherwise it is created.
  </DD>
  </DL>
  <DL>
  <DT><B>interactive = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = yes'>
  <DD>Graph the average calibration spectrum and fit the normalization spectrum
  interactively?
  </DD>
  </DL>
  <DL>
  <DT><B>threshold = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='threshold' Line='threshold = INDEF'>
  <DD>Set the response to 1 when the normalization spectrum or input image data
  fall below this value.  If INDEF then no threshold is applied.
  </DD>
  </DL>
  <DL>
  <DT><B>sample = "<TT>*</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sample' Line='sample = "*"'>
  <DD>Sample of points to use in fitting the average calibration spectrum.
  The sample is selected with a range string.
  </DD>
  </DL>
  <DL>
  <DT><B>naverage = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='naverage' Line='naverage = 1'>
  <DD>Number of sample points to average or median before fitting the function.
  If the number is positive the average of each set of naverage sample
  points is formed while if the number is negative then the median of each set
  of points (in absolute value) is formed.  This subsample of points is
  used in fitting the normalization spectrum.
  </DD>
  </DL>
  <DL>
  <DT><B>function = "<TT>spline3</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='function' Line='function = "spline3"'>
  <DD>Function to fit to the average image spectrum to form the normalization
  spectrum.  The options are "<TT>spline1</TT>", "<TT>spline3</TT>", "<TT>legendre</TT>", and "<TT>chebyshev</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>order = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='order' Line='order = 1'>
  <DD>Order of the fitting function or the number of spline pieces.
  </DD>
  </DL>
  <DL>
  <DT><B>low_reject = 0., high_reject = 0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='low_reject' Line='low_reject = 0., high_reject = 0.'>
  <DD>Rejection limits below and above the fit in units of the residual sigma.
  </DD>
  </DL>
  <DL>
  <DT><B>niterate = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='niterate' Line='niterate = 1'>
  <DD>Number of rejection iterations.
  </DD>
  </DL>
  <DL>
  <DT><B>grow = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='grow' Line='grow = 0'>
  <DD>Reject additional points within this distance of points exceeding the
  rejection threshold.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Cursor keys</H3>
  <! BeginSection: 'CURSOR KEYS'>
  <UL>
  The interactive curve fitting package <B>icfit</B> is used to fit a function
  to the average calibration spectrum.  Help for this package is found
  under the name "<TT>icfit</TT>".
  </UL>
  <! EndSection:   'CURSOR KEYS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  A response calibration, in the form of an image, is created for each input
  image, normally a quartz spectrum.  The response calibration is formed by
  dividing the calibration image by a normalization spectrum which is the
  same at all points along the spatial axis.  The normalization spectrum is
  obtained by averaging the normalization image across the dispersion to form
  a one dimensional spectrum and smoothing the spectrum by fitting a
  function.  The threshold value does not apply to creating or fitting of
  the normalization spectrum but only the final creation of the response
  values.  When normalizing (that is dividing the data values by the
  fit to the normalization spectrum) only pixels in which both the fitted
  normalization value and the data value are above the threshold are
  computed.  If either the normalization value or the data value is below
  the threshold the output response value is one.
  <P>
  The image header keyword DISPAXIS must be present with a value of 1 for
  dispersion parallel to the lines (varying with the column coordinate) or 2
  for dispersion parallel to the columns (varying with line coordinate).
  This parameter may be added using <B>hedit</B>.  Note that if the image has
  been transposed (<B>imtranspose</B>) the dispersion axis should still refer
  to the original dispersion axis unless the physical world coordinate system
  is first reset (see <B>wcsreset</B>).  This is done in order to allow images
  which have DISPAXIS defined prior to transposing to still work correctly
  without requiring this keyword to be changed.
  <P>
  If the output image does not exist it is first created with unit response
  everywhere.  Subsequently the response is only modified in those regions
  occupied by the input calibration image.  Thus, image sections may be used
  to select regions in which the response is desired.  This ability is
  particularly useful when dealing with multiple slits within an image or to
  exclude regions outside the slit.
  <P>
  Normally the normalization images are the same as the calibration images.
  In other words the calibration image is normalized by the average spectrum
  of the calibration image itself.  Sometimes, however, the normalization
  image may be a smaller image section of the calibration image to avoid
  contaminating the normalization spectrum by effects at the edge of the
  slit.  Again, this may be quite useful in multi-slit images.
  <P>
  The normalization spectrum is smoothed by fitting a function
  using the interactive curve fitting package (<B>icfit</B>).  The
  parameters determining the fitted normalization spectrum are the sample
  points, the averaging bin size, the fitting function, the order of the
  function, the rejection sigmas, the number of rejection iterations, and
  the rejection width.  The sample points for the average spectrum are
  selected by a range string.  Points in the normalization spectrum not in the
  sample are not used in determining the fitted function.  The selected
  sample points may be binned into a set of averages or medians which are
  used in the function fit instead of the sample points with the
  averaging bin size parameter <I>naverage</I>.  This parameter selects
  the number of sample points to be averaged if its value is positive or
  the number of points to be medianed if its value is negative
  (naturally, the absolute value is used for the number of points).  A
  value of one uses all sample points without binning.  The fitted
  function may be used to reject points from the fit using the parameters
  <I>low_reject, high_reject, niterate</I> and <I>grow</I>.  If one or both
  of the rejection limits are greater than zero then the sigma of the
  residuals is computed and points with residuals less than
  <I>-low_reject</I> times the sigma and greater than <I>high_reject</I>
  times the sigma are removed and the function fitted again.  In addition
  points within a distance given by the parameter <I>grow</I> of the a
  rejected point are also rejected.  A value of zero for this parameter
  rejects only the points exceeding the rejection threshold.  Finally,
  the rejection procedure may be iterated the number of times given by
  the parameter <I>niterate</I>.
  <P>
  The fitted function may be examined and modified interactively when the
  parameter <I>interactive</I> is set.  In this case the normalization spectrum
  and the fitted function or the residuals of the fit are graphed.
  Deleted points are marked with an x and rejected points by a diamond.
  The sample regions are indicated along the bottom of the graph.
  The cursor keys and colon commands are used to change the values
  of the fitting parameters, delete points, and window and expand the
  graph.  When the fitted function is satisfactory exit with a carriage
  return or <TT>'q'</TT> and the calibration image will be created.  Changes in
  the fitted parameters are remembered from image to image within the
  task but not outside the task.
  <P>
  When the task finishes creating a response image the fitting parameters
  are updated in the parameter file.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. To create a response image non-interactively:
  <P>
  	cl&gt; response quartz quartz response order=20 interactive=no
  <P>
  2. To determine independent responses for a multislit image determine the
  image sections defining each slit.  Then the responses are computed as
  follows:
  <P>
  <PRE>
  	cl&gt; response quartz[10:20,*],quartz[35:45,*] \<BR>
  	&gt;&gt;&gt; quartz[12:18,*],quartz[12:18,*] resp,resp
  </PRE>
  <P>
  Generally the slit image sections are prepared in a file which is then
  used to define the lists of input images and response.
  <P>
  <PRE>
  	cl&gt; response @slits @slits @responses
  </PRE>
  <P>
  3.  If the DISPAXIS keyword is missing and the dispersion is running
  vertically (varying with the image lines):
  <P>
  <PRE>
  	cl&gt; hedit *.imh dispaxis 2 add+
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  icfit, iillumination
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'CURSOR KEYS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
