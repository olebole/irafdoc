.. _wregister:

wregister — Register 1-D or 2-D images using the image wcs
==========================================================

**Package: immatch**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  wregister -- register a list of images to a reference image using WCS
  information
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  wregister input reference output
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The list of input images containing the input wcs.
  </DD>
  </DL>
  <DL>
  <DT><B>reference</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='reference' Line='reference'>
  <DD>The list of reference images containing the reference wcs. The number of
  reference images must be one or equal to the number of input images.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>The list of output registered images. The number of output images must
  be equal to the number of input images.
  </DD>
  </DL>
  <DL>
  <DT><B>xmin = INDEF, xmax = INDEF, ymin = INDEF, ymax = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xmin' Line='xmin = INDEF, xmax = INDEF, ymin = INDEF, ymax = INDEF'>
  <DD>The minimum and maximum logical x and logical y coordinates used to, generate
  the grid of reference image control points, define the region of validity of
  the spatial transformation, and define the extent of the output image.
  Xmin, xmax, ymin, and
  ymax are assigned defaults of 1, the number of columns in the reference 
  image, 1, and the number of lines in the reference image, respectively.
  </DD>
  </DL>
  <DL>
  <DT><B>nx = 10, ny = 10</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nx' Line='nx = 10, ny = 10'>
  <DD>The number of points in x and y used to generate the coordinate grid.
  </DD>
  </DL>
  <DL>
  <DT><B>wcs = "<TT>world</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wcs' Line='wcs = "world"'>
  <DD>The world coordinate system of the coordinates.  The options are:
  <DL>
  <DT><B>physical</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='physical' Line='physical'>
  <DD>Physical coordinates are pixel coordinates which are invariant with
  respect to linear transformations of the physical image data.  For example,
  if the reference 
  image is a rotated section of a larger input image, the physical
  coordinates of an object in the reference image are equal to the physical
  coordinates of the same object in the input image, although the logical
  pixel coordinates are different.
  </DD>
  </DL>
  <DL>
  <DT><B>world</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='world' Line='world'>
  <DD>World coordinates are image coordinates which are invariant with
  respect to linear transformations of the physical image data and which
  are in world units, normally decimal degrees for sky projection coordinate
  systems and angstroms for spectral coordinate systems. Obviously if the
  wcs is correct the ra and dec or wavelength and position of an object
  should remain the same not matter how the image
  is linearly transformed. The default world coordinate
  system is either 1) the value of the environment variable "<TT>defwcs</TT>" if
  set in the user's IRAF environment (normally it is undefined) and present
  in the image header, 2) the value of the "<TT>system</TT>"
  attribute in the image header keyword WAT0_001 if present in the
  image header or, 3) the "<TT>physical</TT>" coordinate system.
  Care must be taken that the wcs of the input and
  reference images are compatible, e.g. it makes no sense to
  match the coordinates of a 2D sky projection and a 2D spectral wcs.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>transpose = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='transpose' Line='transpose = no'>
  <DD>Force a transpose of the reference image world coordinates before evaluating
  the world to logical coordinate transformation for the input image ? This
  option is useful if there is not enough information in the reference and
  input image headers to tell whether or not the images are transposed with
  respect to each other.
  </DD>
  </DL>
  <DL>
  <DT><B>xformat = "<TT>%10.3f</TT>", yformat = "<TT>%10.3f</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xformat' Line='xformat = "%10.3f", yformat = "%10.3f"'>
  <DD>The format of the output logical x and y reference and input pixel
  coordinates in columns 1 and 2 and 3 and 4 respectively. By default the
  coordinates are output right justified in a field of ten spaces with
  3 digits following the decimal point. 
  </DD>
  </DL>
  <DL>
  <DT><B>wxformat = "<TT></TT>", wyformat = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wxformat' Line='wxformat = "", wyformat = ""'>
  <DD>The format of the output world x and y reference and input image coordinates
  in columns 5 and 6 respectively. The internal default formats will give
  reasonable output formats and precision for both sky projection coordinates
  and other, e.g. spectral, coordinates.
  </DD>
  </DL>
  <DL>
  <DT><B>fitgeometry = "<TT>general</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fitgeometry' Line='fitgeometry = "general"'>
  <DD>The fitting geometry to be used. The options are the following.
  <DL>
  <DT><B>shift</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='shift' Line='shift'>
  <DD>X and y shifts only are fit.
  </DD>
  </DL>
  <DL>
  <DT><B>xyscale</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='xyscale' Line='xyscale'>
  <DD>X and y shifts and x and y magnification factors are fit. Axis flips are
  allowed for.
  </DD>
  </DL>
  <DL>
  <DT><B>rotate</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='rotate' Line='rotate'>
  <DD>X and y shifts and a rotation angle are fit. Axis flips are allowed for.
  </DD>
  </DL>
  <DL>
  <DT><B>rscale</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='rscale' Line='rscale'>
  <DD>X and y shifts, a magnification factor assumed to be the same in x and y, and a
  rotation angle are fit. Axis flips are allowed for.
  </DD>
  </DL>
  <DL>
  <DT><B>rxyscale</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='rxyscale' Line='rxyscale'>
  <DD>X and y shifts, x and y magnifications factors, and a rotation angle are fit.
  Axis flips are allowed for.
  </DD>
  </DL>
  <DL>
  <DT><B>general</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='general' Line='general'>
  <DD>A polynomial of arbitrary order in x and y is fit. A linear term and a
  distortion term are computed separately. The linear term includes an x and y
  shift, an x and y scale factor, a rotation and a skew.  Axis flips are also
  allowed for in the linear portion of the fit. The distortion term consists
  of a polynomial fit to the residuals of the linear term. By default the
  distortion terms is set to zero.
  </DD>
  </DL>
  <P>
  For all the fitting geometries except "<TT>general</TT>" no distortion term is fit,
  i.e. the x and y polynomial orders are assumed to be 2 and the cross term
  switches are set to "<TT>none</TT>", regardless of the values of the <I>xxorder</I>,
  <I>xyorder</I>, <I>xxterms</I>, <I>yxorder</I>, <I>yyorder</I> and <I>yxterms</I>
  parameters set by the user.
  </DD>
  </DL>
  <DL>
  <DT><B>function = "<TT>polynomial</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='function' Line='function = "polynomial"'>
  <DD>The type of analytic coordinate surfaces to be fit. The options are the
  following:
  <DL>
  <DT><B>legendre</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='legendre' Line='legendre'>
  <DD>Legendre polynomials in x and y.
  </DD>
  </DL>
  <DL>
  <DT><B>chebyshev</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='chebyshev' Line='chebyshev'>
  <DD>Chebyshev polynomials in x and y.
  </DD>
  </DL>
  <DL>
  <DT><B>polynomial</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='polynomial' Line='polynomial'>
  <DD>Power series polynomials in x and y.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>xxorder = 2, xyorder = 2, yxorder = 2, yyorder = 2</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xxorder' Line='xxorder = 2, xyorder = 2, yxorder = 2, yyorder = 2'>
  <DD>The order of the polynomials in x and y for the x and y fits respectively.
  The default order and cross term settings define the linear term in x
  and y, where the 6 coefficients can be interpreted in terms of an x and y shift,
  an x and y scale change, and rotations of the x and y axes. The "<TT>shift</TT>",
  "<TT>xyscale</TT>", "<TT>rotation</TT>", "<TT>rscale</TT>", and "<TT>rxyscale</TT>", fitting geometries
  assume that the polynomial order parameters are 2 regardless of the values
  set by the user. If any of the order parameters are higher than 2 and
  <I>fitgeometry</I> is "<TT>general</TT>", then a distortion surface is fit to the
  residuals from the linear portion of the fit.
  </DD>
  </DL>
  <DL>
  <DT><B>xxterms = "<TT>half</TT>", yxterms = "<TT>half</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xxterms' Line='xxterms = "half", yxterms = "half"'>
  <DD>The options are:
  <DL>
  <DT><B>none</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='none' Line='none'>
  <DD>The individual polynomial terms contain powers of x or powers of y but not
  powers of both.
  </DD>
  </DL>
  <DL>
  <DT><B>half</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='half' Line='half'>
  <DD>The individual polynomial terms contain powers of x and powers of y, whose
  maximum combined power is MAX (xxorder - 1, xyorder - 1) for the x fit and
  MAX (yxorder - 1, yyorder - 1) for the y fit.
  </DD>
  </DL>
  <DL>
  <DT><B>full</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='full' Line='full'>
  <DD>The individual polynomial terms contain powers of x and powers of y, whose
  maximum combined power is MAX (xxorder - 1 + xyorder - 1) for the x fit and
  MAX (yxorder - 1 + yyorder - 1) for the y fit.
  </DD>
  </DL>
  <P>
  The "<TT>shift</TT>", "<TT>xyscale</TT>", "<TT>rotation</TT>", "<TT>rscale</TT>", and "<TT>rxyscale</TT>" fitting
  geometries, assume that the cross term switches are set to "<TT>none</TT>"regardless
  of the values set by the user.  If either of the cross terms parameters is
  set to "<TT>half</TT>" or "<TT>full</TT>" and <I>fitgeometry</I> is "<TT>general</TT>" then a distortion
  surface is fit to the residuals from the linear portion of the fit.
  </DD>
  </DL>
  <DL>
  <DT><B>reject = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='reject' Line='reject = INDEF'>
  <DD>The rejection limit in units of sigma. The default is no rejection.
  </DD>
  </DL>
  <DL>
  <DT><B>calctype = "<TT>real</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='calctype' Line='calctype = "real"'>
  <DD>The precision of coordinate transformation calculations. The options are "<TT>real</TT>"
  and "<TT>double</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>geometry = "<TT>geometric</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='geometry' Line='geometry = "geometric"'>
  <DD>The type of geometric transformation.  The options are:
  <DL>
  <DT><B>linear</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='linear' Line='linear'>
  <DD>Perform only the linear part of the geometric transformation.
  </DD>
  </DL>
  <DL>
  <DT><B>geometric</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='geometric' Line='geometric'>
  <DD>Compute both the linear and distortion portions of the geometric correction.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>xsample = 1.0, ysample = 1.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xsample' Line='xsample = 1.0, ysample = 1.0'>
  <DD>The coordinate surface subsampling factor. The coordinate surfaces are
  evaluated at every xsample-th pixel in x and every ysample-th pixel in y.
  Transformed coordinates  at intermediate pixel values are determined by
  bilinear interpolation in the coordinate surfaces. If the coordinate
  surface is of high order setting these numbers to some reasonably high
  value is recommended.
  </DD>
  </DL>
  <DL>
  <DT><B>interpolant = "<TT>linear</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interpolant' Line='interpolant = "linear"'>
  <DD>The interpolant used for rebinning the image.  The choices are the following.
  <DL>
  <DT><B>nearest</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='nearest' Line='nearest'>
  <DD>Nearest neighbor.
  </DD>
  </DL>
  <DL>
  <DT><B>linear</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='linear' Line='linear'>
  <DD>Bilinear interpolation in x and y.
  </DD>
  </DL>
  <DL>
  <DT><B>poly3</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='poly3' Line='poly3'>
  <DD>Third order polynomial in x and y.
  </DD>
  </DL>
  <DL>
  <DT><B>poly5</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='poly5' Line='poly5'>
  <DD>Fifth order polynomial in x and y.
  </DD>
  </DL>
  <DL>
  <DT><B>spline3</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='spline3' Line='spline3'>
  <DD>Bicubic spline.
  </DD>
  </DL>
  <DL>
  <DT><B>sinc</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='sinc' Line='sinc'>
  <DD>2D sinc interpolation. Users can specify the sinc interpolant width by
  appending a width value to the interpolant string, e.g. sinc51 specifies
  a 51 by 51 pixel wide sinc interpolant. The sinc width will be rounded up to
  the nearest odd number.  The default sinc width is 31 by 31.
  </DD>
  </DL>
  <DL>
  <DT><B>lsinc</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='lsinc' Line='lsinc'>
  <DD>Look-up table sinc interpolation. Users can specify the look-up table sinc
  interpolant width by appending a width value to the interpolant string, e.g.
  lsinc51 specifies a 51 by 51 pixel wide look-up table sinc interpolant. The user
  supplied sinc width will be rounded up to the nearest odd number. The default
  sinc width is 31 by 31 pixels. Users can specify the resolution of the lookup
  table sinc by appending the look-up table size in square brackets to the
  interpolant string, e.g. lsinc51[20] specifies a 20 by 20 element sinc
  look-up table interpolant with a pixel resolution of 0.05 pixels in x and y.
  The default look-up table size and resolution are 20 by 20 and 0.05 pixels
  in x and y respectively.
  </DD>
  </DL>
  <DL>
  <DT><B>drizzle</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='drizzle' Line='drizzle'>
  <DD>2D drizzle resampling. Users can specify the drizzle pixel fraction in x and y
  by appending a value between 0.0 and 1.0 in square brackets to the
  interpolant string, e.g. drizzle[0.5]. The default value is 1.0.
  The value 0.0 is increased internally to 0.001. Drizzle resampling
  with a pixel fraction of 1.0 in x and y is equivalent to fractional pixel
  rotated block summing (fluxconserve = yes) or averaging (flux_conserve = no)  if
  xmag and ymag are &gt; 1.0.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>boundary = "<TT>nearest</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='boundary' Line='boundary = "nearest"'>
  <DD>The choices are:
  <DL>
  <DT><B>nearest</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='nearest' Line='nearest'>
  <DD>Use the value of the nearest boundary pixel.
  </DD>
  </DL>
  <DL>
  <DT><B>constant</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='constant' Line='constant'>
  <DD>Use a user supplied constant value.
  </DD>
  </DL>
  <DL>
  <DT><B>reflect</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='reflect' Line='reflect'>
  <DD>Generate a value by reflecting about the boundary of the image.
  </DD>
  </DL>
  <DL>
  <DT><B>wrap</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='wrap' Line='wrap'>
  <DD>Generate a value by wrapping around to the opposite side of the image.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>constant = 0.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='constant' Line='constant = 0.0'>
  <DD>The value of the constant for boundary extension.
  </DD>
  </DL>
  <DL>
  <DT><B>fluxconserve = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fluxconserve' Line='fluxconserve = yes'>
  <DD>Preserve the total image flux? If flux conservation is turned on, the output
  pixel values are multiplied by the Jacobian of the coordinate transformation.
  </DD>
  </DL>
  <DL>
  <DT><B>nxblock = 512, nyblock = 512</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nxblock' Line='nxblock = 512, nyblock = 512'>
  <DD>If the size of the output image is less than nxblock by nyblock then the
  entire image is  computed in one iteration. Otherwise the output image is
  computed in blocks of nxblock by nyblock pixels.
  </DD>
  </DL>
  <DL>
  <DT><B>wcsinherit = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wcsinherit' Line='wcsinherit = yes'>
  <DD>Inherit the wcs of the reference image ?
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print messages about the progress of the task?
  </DD>
  </DL>
  <DL>
  <DT><B>interactive = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = no'>
  <DD>Run the task interactively ?
  In interactive mode the user may interact with the fitting process, e.g.
  change the order of the fit, delete points, replot the data etc.
  </DD>
  </DL>
  <DL>
  <DT><B>graphics = "<TT>stdgraph</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = "stdgraph"'>
  <DD>The graphics device.
  </DD>
  </DL>
  <DL>
  <DT><B>gcommands = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='gcommands' Line='gcommands = ""'>
  <DD>The graphics cursor.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  WREGISTER computes the spatial transformation function required to register
  the input image <I>input</I> to the reference image <I>reference</I>,
  and writes the registered input image to the output image <I>output</I>. 
  The input and reference images must be one- or two-dimensional and
  have the same dimensionality.  WREGISTER assumes that the world
  coordinate systems in the input and reference
  image headers are accurate and that the two systems are compatible, e.g. both
  images have the same epoch sky projection world coordinate systems, or both are
  spectra whose coordinates are in the same units.
  <P>
  WREGISTER computes the required spatial transformation by matching the logical
  x and y pixel coordinates of a grid of points 
  in the input image with the logical x and y pixels coordinates
  of the same grid of points in the reference image,
  using world coordinate information stored in the two image headers.
  The coordinate grid consists of <I>nx * ny</I> points evenly distributed
  over the logical pixel space of interest in the reference image defined by the
  <I>xmin</I>, <I>xmax</I>, <I>ymin</I>, <I>ymax</I> parameters.
  The logical x and y pixel reference image coordinates are transformed to the
  reference image world coordinate system defined by <I>wcs</I>, using the wcs
  information in the reference image header.
  The reference image world coordinates are then transformed to logical x and
  y pixel coordinates in the input image, using world coordinate system
  information stored in the input image header. 
  <P>
  The computed reference and input logical coordinates and the
  world coordinates are written to a temporary coordinates file which is
  deleted on task termination.
  The x and y coordinates are written using
  the <I>xformat</I> and <I>yformat</I> and the <I>wxformat</I> and <I>wxformat</I>
  parameters respectively. If these formats are undefined and, in the
  case of the world coordinates a format attribute cannot be
  read from either the reference or the input images, the coordinates are
  output in %g format with <I>min_sigdigits</I> digits of precision.
  If the reference and input images are 1D then all the output logical and
  world y coordinates are set to 1.
  <P>
  WREGISTER computes a spatial transformation of the following form.
  <P>
  <PRE>
      xin = f (xref, yref)
      yin = g (xref, yref)
  </PRE>
  <P>
  The functions f and g are either a power series polynomial or a Legendre or
  Chebyshev polynomial surface of order
  <I>xxorder</I> and <I>xyorder</I> in x and <I>yxorder</I> and <I>yyorder</I> in y.
  <P>
  Several polynomial cross terms options are available. Options "<TT>none</TT>",
  "<TT>half</TT>", and "<TT>full</TT>" are illustrated below for a quadratic polynomial in
  x and y.
  <P>
  <PRE>
  xxterms = "none", xyterms = "none"
  xxorder = 3, xyorder = 3, yxorder = 3, yyorder = 3
  <P>
     xin = a11 + a21 * xref + a12 * yref +
           a31 * xref ** 2 + a13 * yref ** 2
     yin = a11' + a21' * xref + a12' * yref +
           a31' * xref ** 2 + a13' * yref ** 2
  <P>
  xxterms = "half", xyterms = "half"
  xxorder = 3, xyorder = 3, yxorder = 3, yyorder = 3
  <P>
     xin = a11 + a21 * xref + a12 * yref +
           a31 * xref ** 2 + a22 * xref * yref + a13 * yref ** 2
     yin = a11' + a21' * xref + a12' * yref +
           a31' * xref ** 2 + a22' * xref * yref + a13' * yref ** 2
  <P>
  xxterms = "full", xyterms = "full"
  xxorder = 3, xyorder = 3, yxorder = 3, yyorder = 3
  <P>
     xin = a11 + a21 * xref + a31 * xref ** 2 +
           a12 * yref + a22 * xref * yref +  a32 * xref ** 2 * yref +
           a13 * yref ** 2 + a23 * xref *  yref ** 2 +
           a33 * xref ** 2 * yref ** 2
     yin = a11' + a21' * xref + a31' * xref ** 2 +
           a12' * yref + a22' * xref * yref +  a32' * xref ** 2 * yref +
           a13' * yref ** 2 + a23' * xref *  yref ** 2 +
           a33' * xref ** 2 * yref ** 2
  </PRE>
  <P>
  <P>
  If the <B>fitgeometry</B> parameter is anything other than "<TT>general</TT>", the  order
  parameters assume the value 2 and the cross terms switches assume the value
  "<TT>none</TT>", regardless of the values set by the user. The computation can be done in
  either real or double precision by setting the <I>calctype</I> parameter.
  Automatic pixel rejection may be enabled by setting the <I>reject</I>
  parameter to some number &gt; 0.0.
  <P>
  The transformation computed by the "<TT>general</TT>" fitting geometry is arbitrary
  and does not correspond to a physically meaningful model. However the computed
  coefficients for the linear term can be given a simple geometrical geometric
  interpretation for all the fitting geometries as shown below.
  <P>
  <PRE>
          fitting geometry = general (linear term)
              xin = a + b * xref + c * yref
              yin = d + e * xref + f * yref
  <P>
          fitting geometry = shift
              xin = a + xref
              yin = d + yref
  <P>
          fitting geometry = xyscale
              xin = a + b * xref
              yin = d + f * yref
  <P>
          fitting geometry = rotate
              xin = a + b * xref + c * yref
              yin = d + e * xref + f * yref
              b * f - c * e = +/-1
              b = f, c = -e or b = -f, c = e
  <P>
          fitting geometry = rscale
              xin = a + b * xref + c * yref
              yin = d + e * xref + f * yref
              b * f - c * e = +/- const
              b = f, c = -e or b = -f, c = e
  <P>
          fitting geometry = rxyscale
              xin = a + b * xref + c * yref
              yin = d + e * xref + f * yref
              b * f - c * e = +/- const
  </PRE>
  <P>
  <P>
  The coefficients can be interpreted as follows. Xref0, yref0, xin0, yin0
  are the origins in the reference and input frames respectively. Orientation
  and skew are the orientation of the x and y axes and their deviation from
  perpendicularity respectively. Xmag and ymag are the scaling factors in x and
  y and are assumed to be positive.
  <P>
  <PRE>
          general (linear term)
              xrotation = rotation - skew / 2
              yrotation = rotation + skew / 2
              b = xmag * cos (xrotation)
              c = ymag * sin (yrotation)
              e = -xmag * sin (xrotation)
              f = ymag * cos (yrotation)
              a = xin0 - b * xref0 - c * yref0 = xshift
              d = yin0 - e * xref0 - f * yref0 = yshift
  <P>
          shift
              xrotation = 0.0,  yrotation = 0.0
              xmag = ymag = 1.0
              b = 1.0
              c = 0.0
              e = 0.0
              f = 1.0
              a = xin0 - xref0 = xshift
              d = yin0 - yref0 = yshift
  <P>
          xyscale
              xrotation 0.0 / 180.0 yrotation = 0.0
              b = + /- xmag
              c = 0.0
              e = 0.0
              f = ymag
              a = xin0 - b * xref0 = xshift
              d = yin0 - f * yref0 = yshift
  <P>
          rscale
              xrotation = rotation + 0 / 180, yrotation = rotation
              mag = xmag = ymag
              const = mag * mag
              b = mag * cos (xrotation)
              c = mag * sin (yrotation)
              e = -mag * sin (xrotation)
              f = mag * cos (yrotation)
              a = xin0 - b * xref0 - c * yref0 = xshift
              d = yin0 - e * xref0 - f * yref0 = yshift
  <P>
          rxyscale
              xrotation = rotation + 0 / 180, yrotation = rotation
              const = xmag * ymag
              b = xmag * cos (xrotation)
              c = ymag * sin (yrotation)
              e = -xmag * sin (xrotation)
              f = ymag * cos (yrotation)
              a = xin0 - b * xref0 - c * yref0 = xshift
              d = yin0 - e * xref0 - f * yref0 = yshift
  </PRE>
  <P>
  <P>
  <I>Xmin</I>, <I>xmax</I>, <I>ymin</I> and <I>ymax</I> define the region of
  validity of the transformation as well as the limits of the grid
  in the reference coordinate system.
  <P>
  Each computed transformation is written to a temporary output text database
  file  which is deleted on task termination. If more that one record of the same
  name is written to the database file, the last record written is the
  valid record.
  <P>
  WREGISTER will terminate with an error if the reference and input images
  are not both either 1D or 2D.
  If the world coordinate system information cannot be read from either
  the reference or input image header, the requested transformations
  from the world &lt;-&gt; logical coordinate systems cannot be compiled for either
  or both images, or the world coordinate systems of the reference and input
  images are fundamentally incompatible in some way, the output logical
  reference and input image coordinates are both set to a grid of points
  spanning the logical pixel space of the input, not the reference image.
  This grid of points defines an identity transformation which results in
  an output image equal to the input image.
  <P>
  WREGISTER computes the output image by evaluating the fitted coordinate
  surfaces and interpolating in the input image at position of the transformed
  coordinates. The scale of the output image is the same as the scale of the
  reference image. The extent and size of the output image are determined
  by the <I>xmin</I>, <I>xmax</I>, <I>ymin</I>, and <I>ymax</I> parameters
  as shown below
  <P>
  <PRE>
      xmin &lt;= x &lt;= xmax
      ymin &lt;= x &lt;= ymax
      ncols =  xmax - xmin + 1
      nlines = xmax - xmin + 1
  </PRE>
  <P>
  WREGISTER samples the coordinate surfaces at every <I>xsample</I> and 
  fIysample pixels in x and y.
  The transformed coordinates at intermediate pixel values are
  determined by bilinear interpolation in the coordinate surface. If
  <I>xsample</I> and <I>ysample</I> = 1, the coordinate
  surface is evaluated at every pixel. Use of <I>xsample</I> and <I>ysample</I>
  are strongly recommended for large images and high order coordinate
  surfaces in order to reduce the time required to compute the output image.
  <P>
  The output image gray levels are determined by interpolating in the input
  image at the positions of the transformed output pixels using the
  interpolant specified by the <I>interpolant</I> parameter. If the
  <I>fluxconserve</I> switch is set the output pixel values are multiplied by
  the Jacobian of the transformation, which preserves the flux of the entire
  image. Out-of-bounds pixels are evaluated using the <I>boundary</I> and
  <I>constant</I> parameters.
  <P>
  The output image is computed in <I>nxblock</I> by <I>nyblock</I> pixel sections.
  If possible users should set these number to values larger than the dimensions
  of the output image to minimize the number of disk reads and writes required
  to compute the output image.  If this is not feasible and the image rotation is
  small users should set nxblock to be greater than the number of columns in
  the output image, and nyblock to be as large as machine memory will permit.
  <P>
  If <I>wcsinherit</I> is "<TT>yes</TT>" then the world coordinate system of the
  reference image will be copied to the output image.
  Otherwise if the environment variable <I>nomwcs</I> is "<TT>no</TT>" the
  world coordinate
  system of the input image is modified in the output image to reflect the
  effects of the <I>linear</I> portion of the registration operation.
  Support does not yet exist in the IRAF world coordinate system interface
  for the higher order distortion corrections that WREGISTER is capable
  of performing.
  <P>
  If <I>verbose</I> is "<TT>yes</TT>" then messages about the progress of the task
  as well as warning messages indicating potential problems
  are written to the standard output.
  <P>
  WREGISTER may be run interactively by setting the <I>interactive</I>
  parameter to "<TT>yes</TT>".
  In interactive mode the user has the option of viewing the fitted
  spatial transformation, changing the
  fit parameters, deleting and undeleting points, and replotting
  the data until a satisfactory
  fit has been achieved.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Cursor commands</H3>
  <! BeginSection: 'CURSOR COMMANDS'>
  <UL>
  <P>
  In interactive mode the following cursor commands are currently available.
  <P>
  <PRE>
          Interactive Keystroke Commands
  <P>
  ?       Print options
  f       Fit the data and graph with the current graph type (g, x, r, y, s)
  g       Graph the data and the current fit
  x,r     Graph the x fit residuals versus x and y respectively
  y,s     Graph the y fit residuals versus x and y respectively
  d,u     Delete or undelete the data point nearest the cursor
  o       Overplot the next graph
  c       Toggle the constant x, y plotting option
  t       Plot a line of constant x, y through the nearest data point
  l       Print xshift, yshift, xmag, ymag, xrotate, yrotate
  q       Exit the interactive curve fitting
  </PRE>
  <P>
  The parameters listed below can be changed interactively with simple colon
  commands. Typing the parameter name alone will list the current value.
  <P>
  <PRE>
  	Colon Parameter Editing Commands
  <P>
  :show                           List parameters
  :fitgeometry                    Fitting geometry (shift,xyscale,rotate,
                                  rscale,rxyscale,general)
  :function [value]               Fitting function (chebyshev,legendre,
                                  polynomial)
  :xxorder :xyorder [value]       X fitting function xorder, yorder
  :yxorder :yyorder [value]       Y fitting function xorder, yorder
  :xxterms :yxterms [nh/f]        X, Y fit cross terms fit
  :reject [value]                 Rejection threshold
  </PRE>
  <P>
  <P>
  </UL>
  <! EndSection:   'CURSOR COMMANDS'>
  <H3>Formats</H3>
  <! BeginSection: 'FORMATS'>
  <UL>
  <P>
  A  format  specification has the form "<TT>%w.dCn</TT>", where w is the field
  width, d is the number of decimal places or the number of digits  of
  precision,  C  is  the  format  code,  and  n is radix character for
  format code "<TT>r</TT>" only.  The w and d fields are optional.  The  format
  codes C are as follows:
   
  <PRE>
  b       boolean (YES or NO)
  c       single character (c or '\c' or '\0nnn')
  d       decimal integer
  e       exponential format (D specifies the precision)
  f       fixed format (D specifies the number of decimal places)
  g       general format (D specifies the precision)
  h       hms format (hh:mm:ss.ss, D = no. decimal places)
  m       minutes, seconds (or hours, minutes) (mm:ss.ss)
  o       octal integer
  rN      convert integer in any radix N
  s       string (D field specifies max chars to print)
  t       advance To column given as field W
  u       unsigned decimal integer
  w       output the number of spaces given by field W
  x       hexadecimal integer
  z       complex format (r,r) (D = precision)
   
  <P>
  <P>
  Conventions for w (field width) specification:
   
      W =  n      right justify in field of N characters, blank fill
          -n      left justify in field of N characters, blank fill
          0n      zero fill at left (only if right justified)
  absent, 0       use as much space as needed (D field sets precision)
   
  Escape sequences (e.g. "\n" for newline):
   
  \b      backspace   (not implemented)
       formfeed
  \n      newline (crlf)
  \r      carriage return
  \t      tab
  \"      string delimiter character
  \'      character constant delimiter character
  \\      backslash character
  \nnn    octal value of character
   
  Examples
   
  %s          format a string using as much space as required
  %-10s       left justify a string in a field of 10 characters
  %-10.10s    left justify and truncate a string in a field of 10 characters
  %10s        right justify a string in a field of 10 characters
  %10.10s     right justify and truncate a string in a field of 10 characters
   
  %7.3f       print a real number right justified in floating point format
  %-7.3f      same as above but left justified
  %15.7e      print a real number right justified in exponential format
  %-15.7e     same as above but left justified
  %12.5g      print a real number right justified in general format
  %-12.5g     same as above but left justified
  <P>
  %h          format as nn:nn:nn.n
  %15h        right justify nn:nn:nn.n in field of 15 characters
  %-15h       left justify nn:nn:nn.n in a field of 15 characters
  %12.2h      right justify nn:nn:nn.nn
  %-12.2h     left justify nn:nn:nn.nn
   
  %H          / by 15 and format as nn:nn:nn.n
  %15H        / by 15 and right justify nn:nn:nn.n in field of 15 characters
  %-15H       / by 15 and left justify nn:nn:nn.n in field of 15 characters
  %12.2H      / by 15 and right justify nn:nn:nn.nn
  %-12.2H     / by 15 and left justify nn:nn:nn.nn
  <P>
  \n          insert a newline
  </PRE>
  <P>
  </UL>
  <! EndSection:   'FORMATS'>
  <H3>References</H3>
  <! BeginSection: 'REFERENCES'>
  <UL>
  <P>
  Additional  information  on  IRAF  world  coordinate  systems including
  more detailed descriptions of the "<TT>logical</TT>", "<TT>physical</TT>", and "<TT>world</TT>"
  coordinate systems can be
  found  in  the  help  pages  for  the  WCSEDIT  and  WCRESET  tasks. 
  Detailed   documentation   for  the  IRAF  world  coordinate  system 
  interface MWCS can be found in  the  file  "<TT>iraf$sys/mwcs/MWCS.hlp</TT>".
  This  file  can  be  formatted  and  printed  with the command "<TT>help
  iraf$sys/mwcs/MWCS.hlp fi+ | lprint</TT>".  Information on the spectral
  coordinates systems and their suitability for use with WCSXYMATCH
  can be obtained by typing "<TT>help specwcs | lprint</TT>".
  Details of  the  FITS  header
  world  coordinate  system  interface  can  be  found in the document
  "<TT>World Coordinate Systems Representations Within  the  FITS  Format</TT>"
  by Hanisch and Wells, available from our anonymous ftp archive.
      
  </UL>
  <! EndSection:   'REFERENCES'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Register a radio image to an X-ray image of the same field using
  a 100 point coordinate  grid and a simple linear transformation.  Both
  images have accurate sky projection world coordinate systems. Print the
  output world coordinates in the coords file in hh:mm:ss.ss and dd:mm:ss.s
  format. Display the input and output image and blink them.
  <P>
  <PRE>
  	cl&gt; wregister radio xray radio.tran wxformat=%12.2H \<BR>
  	    wyformat=%12.1h
  <P>
  	cl&gt; display radio 1 fi+
  <P>
  	cl&gt; display radio.tran 2 fi+
  </PRE>
  <P>
  2. Repeat the previous command but begin with a higher order fit
  and run the task in interactive mode in order to examine the fit
  residuals.
  <P>
  <PRE>
  	cl&gt; wregister radio xray radio.tran wxformat=%12.2H \<BR>
  	    wyformat=%12.1h xxo=4 xyo=4 xxt=half yxo=4 yyo=4 \<BR>
              yxt=half  inter+
  <P>
              ... a plot of the fit appears
  <P>
  	    ... type x and r to examine the residuals of the x
                  surface fit versus x and y
  <P>
  	    ... type y and s to examine the residuals of the y
                  surface fit versus x and y
  <P>
  	    ... delete 2 deviant points with the d key and
                  recompute the fit with the f key
  <P>
              ... type q to quit, save the fit, and compute the registered
  		image
  </PRE>
  <P>
  3. Mosaic a set of 9 images covering a ~ 1 degree field into a single image
  centered at  12:32:53.1 +43:13:03. Set the output image scale to 0.5
  arc-seconds / pixel which is close the detector scale of 0.51 arc-seconds
  per pixel. Set the orientation to be north up and east to the left.
  The 9 images all have accurate world coordinate information in their headers.
  <P>
  <PRE>
  	# Create a dummy reference image big enough to cover 1 square degree
  <P>
  	cl&gt; mkpattern refimage ncols=7200 nlines=7200 ...
  <P>
  	# Give the dummy reference image the desired coordinate system
  <P>
  	cl&gt; ccsetwcs refimage "" xref=3600.5 yref=3600.5 xmag=-0.5 \<BR>
  	ymag=0.5 lngref=12:32:53.1 latref=43:13:03 ...
  <P>
  	# Register the images using constant boundary extension and
  	# set uservalue to some reasonable value outside the good data
  	# range. Note that it may be possible to improve performance by
  	#increasing nxblock and nyblock.
  <P>
  	cl&gt; wregister @inlist refimage @outlist boundary=constant \<BR>
  	constant=&lt;uservalue&gt; nxblock=7200 nyblock=1024 ...
  <P>
  	# Combine the images using imcombine
  <P>
  	cl&gt; imcombine @outlist mosaic lthreshold=&lt;uservalue&gt; ...
  <P>
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
  imalign,xregister,tprecess,wcsxymatch,geomap,gregister,geotran,wcscopy
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'CURSOR COMMANDS' 'FORMATS' 'REFERENCES' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
