.. _xregister:

xregister — Register 1-D or 2-D images using x-correlation techniques
=====================================================================

**Package: immatch**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  xregister -- register 1 and 2D images using X-correlation techniques
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  xregister input reference regions shifts
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The list of input images to be registered.
  </DD>
  </DL>
  <DL>
  <DT><B>reference</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='reference' Line='reference'>
  <DD>The list of reference images to which the input images are to be registered.
  The number of reference images must be one or equal to the number of input
  images.
  </DD>
  </DL>
  <DL>
  <DT><B>regions</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='regions' Line='regions'>
  <DD>The list of reference image region(s) used to compute the 
  x and y shifts.
  <I>Regions</I> may be: 1) a list of one or more image sections
  separated by whitespace, 2) the name of a text file containing a list
  of one or more image sections separated by whitespace and/or newlines,
  3) a string of the form "<TT>grid nx ny</TT>" defining a grid of nx by ny
  equally spaced and sized image sections spanning the entire image. Shifts are
  computed for each specified region individually and averaged to produce the
  final x and y shift.
  </DD>
  </DL>
  <DL>
  <DT><B>shifts</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='shifts' Line='shifts'>
  <DD>The name of the text file where the computed x and y shifts 
  are written. If <I>databasefmt</I> is "<TT>yes</TT>",  a single record containing the
  computed x and y shifts for each image region and the final average x and y
  shift is written to a text database file for each input image.
  If <I>databasefmt</I> = "<TT>no</TT>", a single line containing the image name and the
  final average x and y shift is written to a simple text file
  for each input image.
  </DD>
  </DL>
  <DL>
  <DT><B>output = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output = ""'>
  <DD>The list of output shifted images. If <I>output</I> is the NULL string
  then x and y shifts are computed for each input image and written to
  <I>shifts</I> but no output images are written. If <I>output</I> is not NULL
  then the number of output images must equal the number of input images.
  </DD>
  </DL>
  <DL>
  <DT><B>databasefmt = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='databasefmt' Line='databasefmt = yes'>
  <DD>If <I>databasefmt</I> is "<TT>yes</TT>" the results are written to a text database
  file, otherwise they are written to a simple text file.
  </DD>
  </DL>
  <DL>
  <DT><B>records = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='records' Line='records = ""'>
  <DD>The list of records to be written to or read from <I>shifts</I> for each
  input image. If <I>records</I> is NULL then the output or input record names
  are assumed to be the names of the input images. If <I>records</I> is not NULL
  then the record names in <I>records</I> are used to write / read the
  records. This parameter is useful for users
  who, wish to compute the x and y shifts using images that have been processed
  in some manner (e.g. smoothed), but apply the computed x and y shifts to the
  original unprocessed images. If more then one record
  with the same name exists in <I>shifts</I> then the most recently written
  record takes precedence. The records parameter is ignored if
  <I>databasefmt</I> is "<TT>no</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>append = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='append' Line='append = yes'>
  <DD>Append new records to an existing <I>shifts</I> file or start a new shifts
  file for each execution of XREGISTER? The append parameter is ignored
  if <I>databasefmt</I> is "<TT>no</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>coords = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='coords' Line='coords = ""'>
  <DD>An optional list of coordinates files containing the x and y coordinates of
  an object in the reference image on the first line and the x and y coordinates
  of the same object in the input image(s) on succeeding lines. The number
  of coordinate files must be equal to the number of reference images.
  The input coordinates are used to compute initial
  values for the x and y lags between the input image and the reference image,
  and supersede any non-zero values of <I>xlag</I>, <I>ylag</I>, <I>dxlag</I>,
  and <I>dylag</I> supplied by the user.
  </DD>
  </DL>
  <DL>
  <DT><B>xlag = 0, ylag = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xlag' Line='xlag = 0, ylag = 0'>
  <DD>The initial x and y lags of the input image with respect to the reference
  image. Positive values imply that the input image is shifted
  in the direction of increasing x and y values with respect to the
  reference image. <I>Xlag</I> and <I>ylag</I> are overridden if an offset
  has been determined using the x and y coordinates in the <I>coords</I> file.
  </DD>
  </DL>
  <DL>
  <DT><B>dxlag = 0, dylag = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dxlag' Line='dxlag = 0, dylag = 0'>
  <DD>The increment in <I>xlag</I> and <I>ylag</I> to be applied to successive input
  images. If <I>dxlag</I> and <I>dylag</I> are set to INDEF then the 
  computed x and y lags for the previous image are used as the initial
  x and y lags for the current image. This option is useful for images which
  were taken as a time sequence and whose x and y the shifts increase or
  decrease in a systematic manner.
  <I>Dxlag</I> and <I>dylag</I> are overridden if an offset
  has been determined using x and y coordinates in the <I>coords</I> file.
  </DD>
  </DL>
  <DL>
  <DT><B>background = none</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='background' Line='background = none'>
  <DD>The default background function to be subtracted from the input
  and reference image data in each region before the
  cross-correlation function is computed. The options are:
  <DL>
  <DT><B>none</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='none' Line='none'>
  <DD>no background subtraction is done.
  </DD>
  </DL>
  <DL>
  <DT><B>mean</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='mean' Line='mean'>
  <DD>the mean of the reference and input image region is computed and subtracted
  from the image data.
  </DD>
  </DL>
  <DL>
  <DT><B>median</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='median' Line='median'>
  <DD>the median of the reference and input image region is computed and subtracted
  from the data.
  </DD>
  </DL>
  <DL>
  <DT><B>plane</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='plane' Line='plane'>
  <DD>a plane is fit to the reference and input image region and subtracted
  from the data.
  </DD>
  </DL>
  <P>
  By default the cross-correlation function is computed in a manner
  which removes the mean intensity in the reference and input image regions 
  from the data. For many data sets this "<TT>correction</TT>"  is sufficient to
  remove first order background level effects
  from the computed cross-correlation function and  no additional
  background subtraction is required.
  </DD>
  </DL>
  <DL>
  <DT><B>border = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='border' Line='border = INDEF'>
  <DD>The width of the border region around the input and reference image data
  regions used to compute the background function if <I>background</I>
  is not "<TT>none</TT>". By default the entire region is used.
  </DD>
  </DL>
  <DL>
  <DT><B>loreject = INDEF, ls hireject = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='loreject' Line='loreject = INDEF, ls hireject = INDEF'>
  <DD>The k-sigma rejection limits for removing the effects of bad data from the
  background fit.
  </DD>
  </DL>
  <DL>
  <DT><B>apodize = 0.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='apodize' Line='apodize = 0.0'>
  <DD>The fraction of the input and reference image data endpoints in x and y
  to apodize with a
  cosine bell function before the cross-correlation function is computed.
  </DD>
  </DL>
  <DL>
  <DT><B>filter = none</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='filter' Line='filter = none'>
  <DD>The spatial filter to be applied to the reference and input image
  data before the cross-correlation function is computed. The options are:
  <DL>
  <DT><B>none</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='none' Line='none'>
  <DD>no spatial filtering is performed.
  </DD>
  </DL>
  <DL>
  <DT><B>laplace</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='laplace' Line='laplace'>
  <DD>a Laplacian filter is applied to the reference and input image data.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>correlation = discrete</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='correlation' Line='correlation = discrete'>
  <DD>The algorithm used to compute the cross-correlation function. The options
  are:
  <DL>
  <DT><B>discrete</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='discrete' Line='discrete'>
  <DD>The cross-correlation function is calculated by computing the discrete
  convolution of the reference and input image regions over the x and y 
  window of interest.  This technique is most efficient method for small
  cross-correlation function x and y search windows.
  </DD>
  </DL>
  <DL>
  <DT><B>fourier</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='fourier' Line='fourier'>
  <DD>The cross-correlation function is calculated by computing the convolution
  of the reference and input image regions  using Fourier techniques.
  This technique is the most efficient method for computing  the
  cross-correlation function for small x and y search windows.
  </DD>
  </DL>
  <DL>
  <DT><B>difference</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='difference' Line='difference'>
  <DD>The cross-correlation function is calculated by computing the error
  function of the reference and input images as a function of position
  in the x and y search window.
  </DD>
  </DL>
  <DL>
  <DT><B>file</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='file' Line='file'>
  <DD>No cross-correlation function is computed. Instead the previously
  computed x and y shifts are read from record <I>record</I> in  the text
  database file <I>shifts</I> if <I>databasefmt</I> is "<TT>yes</TT>", or the
  next line of a simple text file if <I>databasefmt</I> is "<TT>no</TT>".
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>xwindow = 11, ywindow = 11</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xwindow' Line='xwindow = 11, ywindow = 11'>
  <DD>The x and y width of the cross-correlation function region
  to be computed and/or searched for peaks. The search window corresponds
  to shifts of - xwindow / 2 &lt;= xshift &lt;= xwindow /2  and - ywindow / 2 &lt;=
  yshift &lt;= ywindow / 2.  <I>Xwindow</I> and <I>ywindow</I>
  are automatically rounded up to the next nearest odd number.
  </DD>
  </DL>
  <DL>
  <DT><B>function = centroid</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='function' Line='function = centroid'>
  <DD>The algorithm used to compute the x and y position of the cross-correlation
  function peak.  The options are:
  <DL>
  <DT><B>none</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='none' Line='none'>
  <DD>the position of the cross-correlation function peak is set to
  x and y position of the maximum pixel.
  </DD>
  </DL>
  <DL>
  <DT><B>centroid</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='centroid' Line='centroid'>
  <DD>the position of the cross-correlation function peak is calculated
  by computing the intensity-weighted mean of the marginal profiles of
  the cross-correlation function in x and y.
  </DD>
  </DL>
  <DL>
  <DT><B>sawtooth</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='sawtooth' Line='sawtooth'>
  <DD>the position of the cross-correlation function peak is calculated
  by  convolving 1D slices in x and y through the cross-correlation function
  with a 1D sawtooth function and using the point at which the peak is
  bisected to determine the x and y position of the cross-correlation
  peak. 
  </DD>
  </DL>
  <DL>
  <DT><B>parabolic</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='parabolic' Line='parabolic'>
  <DD>a 1D parabola is fit to 1D slices in x and y through the cross-correlation
  function and the fitted coefficients are used to compute the peak of
  the cross-correlation function.
  </DD>
  </DL>
  <DL>
  <DT><B>mark</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='mark' Line='mark'>
  <DD>mark the peak of the cross-correlation function with the graphics cursor.
  This option will only work if <I>interactive</I> = "<TT>yes</TT>".
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>xcbox = 5, ycbox = 5</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xcbox' Line='xcbox = 5, ycbox = 5'>
  <DD>The width of the box centered on the peak of the cross-correlation function
  used to compute the fractional pixel x and y center.
  </DD>
  </DL>
  <DL>
  <DT><B>interp_type = "<TT>linear</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interp_type' Line='interp_type = "linear"'>
  <DD>The interpolant type use to computed the output shifted image.
  The choices are the following:
  <DL>
  <DT><B>nearest</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='nearest' Line='nearest'>
  <DD>nearest neighbor.
  </DD>
  </DL>
  <DL>
  <DT><B>linear</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='linear' Line='linear'>
  <DD>bilinear interpolation in x and y.
  </DD>
  </DL>
  <DL>
  <DT><B>poly3</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='poly3' Line='poly3'>
  <DD>third order interior polynomial in x and y.
  </DD>
  </DL>
  <DL>
  <DT><B>poly5</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='poly5' Line='poly5'>
  <DD>fifth order interior polynomial in x and y.
  </DD>
  </DL>
  <DL>
  <DT><B>spline3</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='spline3' Line='spline3'>
  <DD>bicubic spline.
  </DD>
  </DL>
  <DL>
  <DT><B>sinc</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='sinc' Line='sinc'>
  <DD>2D sinc interpolation. Users can specify the sinc interpolant width by
  appending a width value to the interpolant string, e.g. sinc51 specifies
  a 51 by 51 pixel wide sinc interpolant. The sinc width input by the
  user will be rounded up to the nearest odd number. The default sinc width
  is 31 by 31.
  </DD>
  </DL>
  <DL>
  <DT><B>drizzle</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='drizzle' Line='drizzle'>
  <DD>2D drizzle resampling. Users can specify the drizzle pixel fractions in x and y
  by appending values between 0.0 and 1.0 in square brackets to the
  interpolant string, e.g. drizzle[0.5]. The default value is 1.0. The
  value 0.0 is increased to 0.001. Drizzle resampling with a pixel fraction
  of 1.0 in x and y is identical to bilinear interpolation.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>boundary_type = "<TT>nearest</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='boundary_type' Line='boundary_type = "nearest"'>
  <DD>The boundary extension algorithm used to compute the output shifted
  image.  The choices are:
  <DL>
  <DT><B>nearest</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='nearest' Line='nearest'>
  <DD>use the value of the nearest boundary pixel.
  </DD>
  </DL>
  <DL>
  <DT><B>constant</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='constant' Line='constant'>
  <DD>use a constant value.
  </DD>
  </DL>
  <DL>
  <DT><B>reflect</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='reflect' Line='reflect'>
  <DD>generate a value by reflecting about the boundary.
  </DD>
  </DL>
  <DL>
  <DT><B>wrap</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='wrap' Line='wrap'>
  <DD>generate a value by wrapping around to the opposite side of the image.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>constant = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='constant' Line='constant = 0'>
  <DD>The default constant for constant boundary extension.
  </DD>
  </DL>
  <DL>
  <DT><B>interactive = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = no'>
  <DD>Compute the cross-correlation function and the shifts for each image
  interactively using graphics cursor and optionally image cursor input.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose'>
  <DD>Print messages about the progress of the task during task execution
  in non-interactive mode.
  </DD>
  </DL>
  <DL>
  <DT><B>graphics = "<TT>stdgraph</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = "stdgraph"'>
  <DD>The default graphics device.
  </DD>
  </DL>
  <DL>
  <DT><B>display = "<TT>stdimage</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='display' Line='display = "stdimage"'>
  <DD>The default image display device.
  </DD>
  </DL>
  <DL>
  <DT><B>gcommands = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='gcommands' Line='gcommands = ""'>
  <DD>The default graphics cursor.
  </DD>
  </DL>
  <DL>
  <DT><B>icommands = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='icommands' Line='icommands = ""'>
  <DD>The default image display cursor.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  XREGISTER computes the x and y shifts required to register a list of input
  images <I>input</I> to a list of reference images <I>reference</I> using
  cross-correlation techniques. The computed x and y shifts are stored
  in the text file <I>shifts</I>, in the records <I>records</I> if
  <I>databasefmt</I> is "<TT>yes</TT>" or a single line of a simple text file
  if <I>databasefmt</I> is "<TT>no</TT>". One entry is made in the shifts file for
  each input image. If a non NULL list of output images
  <I>output</I> is supplied a shifted output image is written for each input
  image. XREGISTER is intended to solve 1D and 2D image registration problems
  where the images have the same size, the same pixel scale, are shifted
  relative to
  each other by simple translations in x and y, and contain one or more
  extended features in common that will produce a peak in the computed
  cross-correlation function.
  <P>
  The reference image regions used to compute the cross-correlation
  function shifts are defined by the parameter
  <I>regions</I>. <I>Regions</I> may be:
  1) a list of one or more image sections, e.g.
  "<TT>[100:200,100:200] [400:500,400:500]</TT>" separated
  by whitespace, 2) the name of a text file containing a list of one or
  more image sections separated by whitespace and / or newline characters,
  or, 3) a string
  of the form "<TT>grid nx ny</TT>" specifying a grid of nx by ny
  image sections spanning the entire reference image.
  All reference image regions should be chosen so as to 
  include at least one well-defined object or feature. Cross-correlation
  functions and x and y shifts are computed independently for each
  reference image region
  and averaged to produce the final x and y shift for each input image.
  <P>
  By default the initial x and y lags between the input and reference
  image are assumed to by 0.0 and 0.0
  respectively and each reference image region is cross-correlated
  with the identical region in the input image, e.g reference image
  region [100:200,100:200] is cross-correlated with input image
  region [100:200,100:200].
  <P>
  Non-zero initial guesses for
  the x and y shifts for each input image can be input to XREGISTER using
  the coordinates file parameter <I>coords</I>.
  <I>Coords</I> is a simple text file containing the x
  and y coordinates of a  single
  object in the reference image in columns one and two
  of line one, and the x and y coordinates of the same object in the first
  input image in columns one and two of line two, etc. If <I>coords</I>
  is defined there must be one coordinate file for every reference image.
  If there are fewer lines of text in <I>coords</I> than there are 
  numbers of reference plus input images, then x and y shifts of 0.0 are
  assumed for the extra input images. For example,
  if the  user specifies a single input and reference image, sets the
  <I>regions</I> parameter to "<TT>[100:200,100:200]</TT>", and defines
  a coordinates file  which contains the numbers 
  50.0 50.0 in columns one and two of line one,  and the numbers 52.0 and 52.0
  in columns one and two of line two, then the initial x and y
  lags for the input image with respect to the reference image will be 2.0
  and 2.0 respectively, and the reference image region [100:200,100:200] will be
  cross-correlated with the input image region [102:202,102:202]. 
  <P>
  If <I>coords</I> is NULL, the parameters <I>xlag</I>, <I>ylag</I>,
  <I>dxlag</I>, and <I>dylag</I> can be used to define initial x and y lags
  for each input image. <I>Xlag</I> and <I>ylag</I> define the x and y lags
  of the first input image with respect to the reference image. In the
  example above they would be set to 2.0 and 2.0 respectively. Initial
  shifts for succeeding images are computed by adding the values of the
  <I>dxlag</I> and <I>dylag</I> parameters  to the values of
  <I>xlag</I> and <I>ylag</I> assumed for the previous image.
  If <I>dxlag</I> and <I>dylag</I> are 0.0 and 0.0
  the same initial x and y lag will be used for all the input
  images. If <I>dxlag</I> and <I>dylag</I> are both finite numbers then these
  numbers will be added to
  the x and y lags assumed for the previous image. If these numbers
  are both INDEF then the computed x and y lags for the previous image
  will be used to compute the initial x and y lags for the current image.
  Both options can be useful for time series images where the x and y
  shifts between successive images display some regular behavior.
  <P>
  Prior to computing the cross-correlation function
  large mean background values and gradients should be removed
  from the input and reference image data as either
  can seriously degrade the peak of the cross-correlation
  function.  To first order XREGISTER computes the cross-correlation function
  in a manner which removes
  the effect of large mean background values from the resulting
  function. For many if not most typical data sets the user can safely leave
  the parameter <I>background</I> at its default value of "<TT>none</TT>" and
  achieve reasonable results. For more demanding data sets the user should
  experiment with the "<TT>mean</TT>", "<TT>median</TT>", and "<TT>plane</TT>" background fitting
  algorithms which compute and subtract, the mean value, median value, and
  a plane from the input and reference image data respectively,
  before computing the
  cross-correlation function. The region used to compute the background fitting
  function can be restricted to a border around the reference and
  input image regions by setting the <I>border</I> parameter. Bad
  data can be rejected from the background fit by setting the <I>loreject</I>
  and <I>hireject</I> parameters.
  <P>
  A cosine bell function can be applied to the edges of the input and
  reference image data before
  computing the cross-correlation function by setting the <I>apodize</I>
  parameter.
  <P>
  If the <I>filter</I> parameter is set to "<TT>laplace</TT>" instead of its default
  value of "<TT>none</TT>" then a Laplacian filter is applied to the input and
  reference image data before the cross-correlation function is computed.
  This spatial filtering operation effectively
  removes both a background and a slope from the input and reference image
  data and
  highlights regions of the image where the intensity is changing rapidly.
  The effectiveness of this filtering operation in sharpening the
  correlation peak depends on the degree to
  which the intensity in adjacent pixels is correlated.
  <P>
  The cross-correlation function for each region is computed by
  discrete convolution, <I>correlation</I> = "<TT>discrete</TT>",
  Fourier convolution, <I>correlation</I> = "<TT>fourier</TT>", or by computing
  the error function, <I>correlation</I> = "<TT>difference</TT>". The x and y lag
  space in pixels around the initial x and y lag over which the cross-correlation 
  function is searched for the correlation peak, is specified by the
  <I>xwindow</I> and
  <I>ywindow</I>  parameters. These parameter define a range of x and y lags from
  -xwindow / 2 to xwindow / 2 and -ywindow / 2 to ywindow / 2 respectively. For
  a given input and reference image region, the
  execution time of XREGISTER will depend strongly on both the correlation
  algorithm chosen and
  the size of the search window. In general users should use discrete
  or difference correlation for small search windows and fourier
  correlation for large search windows.
  <P>
  The x and y lags for each input and reference image
  region are computed by computing
  the position of the peak of the cross-correlation function in the
  search window using
  one of the four centering algorithms: "<TT>none</TT>", "<TT>centroid</TT>", "<TT>sawtooth</TT>",
  and "<TT>parabolic</TT>".
  <P>
  The computed x and y shifts for each region and the final x and y shift
  for each input image (where the computed x and y shifts are just the negative
  of the computed x and y lags) are written to the shifts file <I>shifts</I>.
  If <I>databasefmt</I> is "<TT>yes</TT>" each results is written in a record whose name
  is either identical to the name of the input
  image or supplied by the user via the <I>records</I> parameter .
  If <I>databasefmt</I> is "<TT>no</TT>", then a single containing the input image
  name and the computed x and y shifts is written to the output shifts file.
  <P>
  If a list of output image names have been supplied then the x and y
  shifts will be applied to the input images to compute the output images
  using the interpolant type specified by <I>interp_type</I> and the
  boundary extension algorithm specified by <I>boundary</I> and <I>constant</I>. 
  <P>
  If the <I>correlation</I> parameter is set to "<TT>file</TT>" then the shifts
  computed in a previous run of XREGISTER will be read from the <I>shifts</I>
  file and applied to the input images to compute the output images.
  If no record list is supplied by the user XREGISTER will for each input
  image search for
  a record whose name is the same as the input image name. If more than
  one record of the same name is found then the most recently written
  record will be used.
  <P>
  XREGISTER does not currently trim the input images but it computes and
  prints the region over which they all overlap in the form of an image
  section. Although XREGISTER is designed for use with same sized images,
  it may be used with images of varying size.
  In this case it is possible for the calculated overlap region to be vignetted,
  as XREGISTER currently preserves the size of the input image when it shifts it.
  For example if an image is much smaller than the reference image
  it is possible for the image to be shifted outside of its own borders.
  If the smallest image is used as a reference this will not occur. If
  vignetting is detected the vignetted image section is printed on the 
  screen. Vignetting may also occur for a list of same-sized images
  if the reference image is not included in the input image list, and the
  computed shifts are all positive or negative as may occur in a time
  sequence. Choosing a reference image with  a shift which is in the
  middle of the observed range of shifts in x and y will remove this problem.
  <P>
  In non-interactive mode the parameters are set at task startup
  and the input images are processed sequentially. If the <I>verbose</I>
  flag is set messages about the progress of the task are printed on the
  screen as the task is running.
  <P>
  In interactive mode the user can mark the regions to be used
  to compute the cross-correlation function on the image display,
  define the initial shifts from the reference image to the input image
  on the image display, show/set the data and algorithm parameters,
  compute, recompute,  and plot the cross-correlation function, experiment
  with the various peak fitting algorithms, and overlay row and column
  plots of the input and reference images with and without the initial and / or
  computed shifts factored in.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Cursor commands</H3>
  <! BeginSection: 'CURSOR COMMANDS'>
  <UL>
  <P>
  The following graphics cursor commands are currently available in
  XREGISTER.
  <P>
  <P>
  <PRE>
  		Interactive Keystroke Commands
  <P>
  ?	Print help 
  :	Colon commands
  t	Define the offset between the reference and the input image
  c	Draw a contour plot of the cross-correlation function
  x	Draw a column plot of the cross-correlation function
  y	Draw a line plot of the cross-correlation function
  r	Redraw the current plot
  f	Recompute the cross-correlation function
  o	Enter the image overlay plot submenu 
  w	Update the task parameters
  q	Exit
  <P>
  <P>
  		Colon Commands
  <P>
  :mark		Mark regions on the display
  :show	        Show the current values of the parameters
  <P>
  		Show/Set Parameters
  <P>
  :reference	[string]    Show/set the current reference image name
  :input		[string]    Show/set the current input image name
  :regions	[string]    Show/set the regions list
  :shifts		{string]    Show/set the shifts database file name
  :coords		[string]    Show/set the current coordinates file name
  :output		[string]    Show/set the current output image name
  :records	[string]    Show/set the current database record name
  :xlag		[value]     Show/set the initial lag in x
  :ylag		[value]     Show/set the initial lag in y
  :dxlag		[value]     Show/set the incremental lag in x
  :dylag		[value]     Show/set the incremental lag in y
  :cregion	[value]	    Show/set the current region
  :background	[string]    Show/set the background fitting function
  :border		[value]     Show/set border region for background fitting
  :loreject	[value]     Show/set low side k-sigma rejection
  :hireject	[value]     Show/set high side k-sigma rejection 
  :apodize	[value]	    Show/set percent of end points to apodize
  :filter		[string]    Show/set the default spatial filter 
  :correlation	[string]    Show/set cross-correlation function 
  :xwindow	[value]     Show/set width of correlation window in x
  :ywindow	[value]     Show/set width of correlation window in y
  :function	[string]    Show/set correlation peak centering function 
  :xcbox		[value]	    Show/set the centering box width in x
  :ycbox		[value]	    Show/set the centering box width in y
  </PRE>
  <P>
  <P>
  The following submenu of image cursor commands is also available.
  <P>
  <PRE>
  		Image Overlay Plot Submenu
  <P>
  <P>
  ?	Print help
  c  	Overlay the marked column of the reference image
  	with the same column of the input image
  l  	Overlay the marked line of the reference image
  	with the same line of the input image
  x 	Overlay the marked column of the reference image
  	with the x and y lagged column of the input image
  y 	Overlay the marked line of the reference image
  	with the x and y lagged line of the input image
  v 	Overlay the marked column of the reference image
  	with the x and y shifted column of the input image
  h 	Overlay the marked line of the reference image
  	with the x and y shifted line of the input image
  q	Quit 
  <P>
  <P>
  		Image Overlay Sub-menu Colon Commands
  <P>
  :c  [m] [n] 	Overlay the middle [mth] column of the reference image
  		with the mth [nth] column of the input image
  :l  [m] [n]	Overlay the middle [mth] line of the reference image
  		with the mth [nth]  line of the input image
  :x  [m] 	Overlay the middle [mth] column of the reference image
  		with the x and y lagged column of the input image
  :y  [m] 	Overlay the middle [mth] line of the reference image
  		with the x and y lagged line of the input image
  :v  [m] 	Overlay the middle [mth] column of the reference image
  		with the x and y shifted column of the input image
  :h  [m] 	Overlay the middle [mth] line of the reference image
  		with the x and y shifted line of the input image
  </PRE>
  <P>
  </UL>
  <! EndSection:   'CURSOR COMMANDS'>
  <H3>Algorithms</H3>
  <! BeginSection: 'ALGORITHMS'>
  <UL>
  <P>
  The cross-correlation function is computed in the following manner.
  The symbols I and R refer to the input and reference images respectively.
  <P>
  <PRE>
  correlation = discrete
  <P>
          &lt;I&gt; = SUMj SUMi { I[i+xlag,j+ylag] } / (Nx * Ny)
          &lt;R&gt; = SUMj SUMi { R[i,j] } / (Nx * Ny)
       sumsqI = sqrt (SUMj SUMi { (I[i+xlag,j+ylag] - &lt;I&gt;) ** 2 })
       sumsqR = sqrt (SUMj SUMi { (R[i,j] - &lt;R&gt;) ** 2 })
  <P>
  	  X = SUMj SUMi { (I[i+xlag,j+ylag] - &lt;I&gt;) * (R[i,j] - &lt;R&gt;) }
  	      ----------------------------------------------------
  			 sumsqI * sumsqR
  <P>
  <P>
  correlation = fourier
  <P>
          &lt;I&gt; = SUMj SUMi { I[i,j] } / (Nx * Ny)
          &lt;R&gt; = SUMj SUMi { R[i,j] } / (Nx * Ny)
       sumsqI = sqrt (SUMj SUMi { (I[i,j] - &lt;I&gt;) ** 2 })
       sumsqR = sqrt (SUMj SUMi { (R[i,j] - &lt;R&gt;) ** 2 })
         FFTI = FFT { (I - &lt;I&gt;) / sumsqI } 
         FFTR = FFT { (R - &lt;R&gt;) / sumsqR } 
  <P>
            X = FFTINV { FFTR * conj { FFTI } }
  <P>
  <P>
  correlation = difference
  <P>
          &lt;I&gt; = SUMj SUMi { I[i+xlag,j+ylag] } / (Nx * Ny)
          &lt;R&gt; = SUMj SUMi { R[i,j] } / (Nx * Ny)
  <P>
  	  X = SUMj SUMi { abs ((I[i+xlag,j+ylag] - &lt;I&gt;) - (R[i,j] - &lt;R&gt;)) }
  	  X = 1.0 - X / max { X }
  </PRE>
  <P>
  </UL>
  <! EndSection:   'ALGORITHMS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Register a list of images whose dimensions are all 256 by 256 pixels
  and whose shifts with respect to the reference image are all less than
  5.0 pixels, using the discrete cross-correlation algorithm and a search
  window of 21 pixels in x and y.
  <P>
  <PRE>
  	cl&gt; xregister @inimlist refimage [*,*] shifts.db out=@outimlist \<BR>
  	    xwindow=21 ywindow=21
  </PRE>
  <P>
  2. Register the previous list of images, but compute the cross_correlation
  function using boxcar smoothed versions of the input images.
  <P>
  <PRE>
  	cl&gt; xregister @binimlist brefimage [*,*] shifts.db xwindow=21 \<BR>
  	    ywindow=21
  <P>
  	cl&gt; xregister @inimlist refimage [*,*] shifts.db out=@outimlist \<BR>
  	    records=@binimlist correlation=file
  </PRE>
  <P>
  3. Register the previous list of images but write the results to a simple
  text file instead of a text database file and do the actual shifting with
  the imshift task.
  <P>
  <PRE>
  	cl&gt; xregister @binimlist brefimage [*,*] shifts.db xwindow=21 \<BR>
  	    ywindow=21 databasefmt-
  <P>
  	cl&gt; fields shifts.db 2,3 &gt; shifts
  <P>
  	cl&gt; imshift @inimlist @outimlist shifts_file=shifts
  </PRE>
  <P>
  4. Register list of 512 by 512 pixel square solar sunspot images that were
  observed as a time series. Compute the cross-correlation function using
  Fourier techniques, a search window of 21 pixels in x and y, an initial
  shift of 10 pixels in x and 1 pixel in y, and use the computed shift of
  the previous image as the initial guess for the current image.
  <P>
  <PRE>
  	cl&gt; xregister @inimlist refimage [*,*] shifts.db out=@outimlist \<BR>
  	    xlag=10 ylag=1 dxlag=INDEF dylag=INDEF correlation=fourier \<BR>
  	    xwindow=21 ywindow=21
  </PRE>
  <P>
  5. Register two 2K square images interactively using discrete cross-correlation
  and an initial search window of 15 pixels in x and y.
  <P>
  <PRE>
  	cl&gt; display refimage
  <P>
  	cl&gt; xregister inimage refimage [900:1100,900:1100] shifts.db \<BR>
  	    xwindow=15 ywindow=15 interactive+
  <P>
  	    ... a contour plot of the cross-correlation function appears
  		with the graphics cursor ready to accept commands
  <P>
  	    ... type x and y to get line and column plots of the cross-
  		correlation function at various points and c to return
  		to the default contour plot
  <P>
  	    ... type ? to get a list of the available commands
  <P>
  	    ... type :mark to mark a new region on the image display
  <P>
  	    ... type f to recompute the cross-correlation function using
  		the new data
  <P>
  	    ... increase the search window to 21 pixels in x and y
  		with the :xwindow 21 and :ywindow 21 commands
  <P>
  	    ... type f to recompute the cross-correlation function with the
  		new search window
  <P>
  	    ... type o to enter the image data overlay plot submenu, 
  		move the cursor to a line in the displayed reference image
  		and type l to see of plot of the line in the input and
  		reference image, type h to see a plot of the same line in
  		the reference image and the x and y shifted line in the input
  		image, type q to return to the main menu
  <P>
  	    ... type q to quit the task, and q again to verify the previous
  	    	q command
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  rv.fxcor,proto.imalign,images.imcombine,ctio.immatch,center1d,images.imshift
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'CURSOR COMMANDS' 'ALGORITHMS' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
