wcsmap — Compute geometric transforms using the image wcs
=========================================================

**Package: immatch**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>wcsmap (Feb96)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>images.immatch</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>wcsmap (Feb96)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>wcsmap</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  wcsmap -- compute the spatial transformation function required to register
  a list of images using WCS information
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  wcsmap input reference database
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The list of input images containing the input wcs.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_reference">reference</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='reference' Line='reference'>
  <DD>The list of reference images containing the reference wcs. The number of
  reference images must be one or equal to the number of input images.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_database">database</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='database' Line='database'>
  <DD>The name of the output text database file containing the computed
  transformations.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_transforms">transforms = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='transforms' Line='transforms = ""'>
  <DD>An optional list of transform names. If transforms is undefined the
  transforms are assigned record names identical to the names of the input images.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_results">results = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='results' Line='results = ""'>
  <DD>Optional output files containing a summary of the results including a
  description of the transform geometry and a listing of the input coordinates,
  the fitted coordinates, and the fit residuals. The number of results files
  must be one or equal to the number of input files. If results is "<TT>STDOUT</TT>" the
  results summary is printed on the standard output.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xmin">xmin = INDEF, xmax = INDEF, ymin = INDEF, ymax = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xmin' Line='xmin = INDEF, xmax = INDEF, ymin = INDEF, ymax = INDEF'>
  <DD>The minimum and maximum logical x and logical y coordinates used to generate
  the grid of reference image control points and define the region of
  validity of the spatial transformation. Xmin, xmax, ymin, and
  ymax are assigned defaults of 1, the number of columns in the reference 
  image, 1, and the number of lines in the reference image, respectively.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nx">nx = 10, ny = 10</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nx' Line='nx = 10, ny = 10'>
  <DD>The number of points in x and y used to generate the coordinate grid.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_wcs">wcs = "<TT>world</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wcs' Line='wcs = "world"'>
  <DD>The world coordinate system of the coordinates.  The options are:
  <DL>
  <DT><B><A NAME="l_physical">physical</A></B></DT>
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
  <DT><B><A NAME="l_world">world</A></B></DT>
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
  <DT><B><A NAME="l_transpose">transpose = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='transpose' Line='transpose = no'>
  <DD>Force a transpose of the reference image world coordinates before evaluating
  the world to logical coordinate transformation for the input image ? This
  option is useful if there is not enough information in the reference and
  input image headers to tell whether or not the images are transposed with
  respect to each other.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xformat">xformat = "<TT>%10.3f</TT>", yformat = "<TT>%10.3f</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xformat' Line='xformat = "%10.3f", yformat = "%10.3f"'>
  <DD>The format of the output logical x and y reference and input pixel
  coordinates in columns 1 and 2 and 3 and 4 respectively. By default the
  coordinates are output right justified in a field of ten spaces with
  3 digits following the decimal point. 
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_wxformat">wxformat = "<TT></TT>", wyformat = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wxformat' Line='wxformat = "", wyformat = ""'>
  <DD>The format of the output world x and y reference and input image coordinates
  in columns 5 and 6 respectively. The internal default formats will give
  reasonable output formats and precision for both sky projection coordinates
  and other types, e.g. spectral, coordinates.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fitgeometry">fitgeometry = "<TT>general</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fitgeometry' Line='fitgeometry = "general"'>
  <DD>The fitting geometry to be used. The options are the following.
  <DL>
  <DT><B><A NAME="l_shift">shift</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='shift' Line='shift'>
  <DD>X and y shifts only are fit.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xyscale">xyscale</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='xyscale' Line='xyscale'>
  <DD>X and y shifts and x and y magnification factors are fit. Axis flips are
  allowed for.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_rotate">rotate</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='rotate' Line='rotate'>
  <DD>X and y shifts and a rotation angle are fit. Axis flips are allowed for.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_rscale">rscale</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='rscale' Line='rscale'>
  <DD>X and y shifts, a magnification factor assumed to be the same in x and y, and a
  rotation angle are fit. Axis flips are allowed for.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_rxyscale">rxyscale</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='rxyscale' Line='rxyscale'>
  <DD>X and y shifts, x and y magnifications factors, and a rotation angle are fit.
  Axis flips are allowed for.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_general">general</A></B></DT>
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
  <DT><B><A NAME="l_function">function = "<TT>polynomial</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='function' Line='function = "polynomial"'>
  <DD>The type of analytic coordinate surfaces to be fit. The options are the
  following.
  <DL>
  <DT><B><A NAME="l_legendre">legendre</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='legendre' Line='legendre'>
  <DD>Legendre polynomials in x and y.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_chebyshev">chebyshev</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='chebyshev' Line='chebyshev'>
  <DD>Chebyshev polynomials in x and y.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_polynomial">polynomial</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='polynomial' Line='polynomial'>
  <DD>Power series polynomials in x and y.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xxorder">xxorder = 2, xyorder = 2,  yxorder = 2, yyorder = 2</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xxorder' Line='xxorder = 2, xyorder = 2,  yxorder = 2, yyorder = 2'>
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
  <DT><B><A NAME="l_xxterms">xxterms = "<TT>half</TT>", yxterms = "<TT>half</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xxterms' Line='xxterms = "half", yxterms = "half"'>
  <DD>The options are:
  <DL>
  <DT><B><A NAME="l_none">none</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='none' Line='none'>
  <DD>The individual polynomial terms contain powers of x or powers of y but not
  powers of both.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_half">half</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='half' Line='half'>
  <DD>The individual polynomial terms contain powers of x and powers of y, whose
  maximum combined power is MAX (xxorder - 1, xyorder - 1) for the x fit and
  MAX (yxorder - 1, yyorder - 1) for the y fit. 
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_full">full</A></B></DT>
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
  <DT><B><A NAME="l_reject">reject = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='reject' Line='reject = INDEF'>
  <DD>The rejection limit in units of sigma. The default is no rejection.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_calctype">calctype = "<TT>real</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='calctype' Line='calctype = "real"'>
  <DD>The precision of coordinate transformation calculations. The options are "<TT>real</TT>"
  and "<TT>double</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print messages about the progress of the task?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interactive">interactive = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = yes'>
  <DD>Run the task interactively ?
  In interactive mode the user may interact with the fitting process, e.g.
  change the order of the fit, delete points, replot the data etc.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_graphics">graphics = "<TT>stdgraph</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = "stdgraph"'>
  <DD>The graphics device.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_gcommands">gcommands = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='gcommands' Line='gcommands = ""'>
  <DD>The graphics cursor.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  WCSMAP computes the spatial transformation function required to map the
  coordinate system of the reference image <I>reference</I> to the coordinate
  system of the input image <I>input</I>, and stores the computed function in
  the output text database file <I>database</I>.
  The input and reference images must be one- or two-dimensional and
  must have the same dimensionality. The input image and output
  text database file can be input to the REGISTER or GEOTRAN tasks to
  perform the actual image registration.  WCSMAP assumes that the world
  coordinate systems in the input and reference
  image headers are accurate and that the two systems are compatible, e.g. both
  images have the same epoch sky projection world coordinate systems or both are
  spectra whose coordinates are in the same units.
  <P>
  WCSMAP computes the required spatial transformation by matching the logical
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
  world coordinates are written to a temporary output coordinates file which
  is deleted on task termination.
  The x and y coordinates are written using
  the <I>xformat</I> and <I>yformat</I> and the <I>wxformat</I> and <I>wxformat</I>
  parameters respectively. If these formats are undefined and, in the
  case of the world coordinates a format attribute cannot be
  read from either the reference or the input images, the coordinates are
  output in %g format with <I>min_sigdigits</I> digits of precision.
  If the reference and input images are 1D then all the output logical and
  world y coordinates are set to 1.
  <P>
  WCSMAP computes a spatial transformation of the following form.
  <P>
  <PRE>
      xin = f (xref, yref)
      yin = g (xref, yref)
  </PRE>
  <P>
  The functions f and g are either a power series polynomial or a Legendre or
  Chebyshev polynomial surface of order <I>xxorder</I> and <I>xyorder</I> in
  x and <I>yxorder</I> and <I>yyorder</I> in y.  Cross terms are optional.
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
  If the <B>fitgeometry</B> parameter is anything
  other than "<TT>general</TT>", the  order parameters assume the value 2 and the
  cross terms switches assume the value "<TT>none</TT>", regardless of the values set
  by the user. The computation can be done in either real or
  double precision by setting the <I>calctype</I> parameter.
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
  validity of the fit as well as the limits of the grid
  in the reference coordinate system and must be set by
  the user. These parameters are used to reject out of range data before the
  actual fitting is done.
  <P>
  Each computed transformation is written to the output file <I>database</I>
  in a record whose name is either specified by the user via the <I>transforms</I>
  parameter or defaults the name of the input image.
  The database file is opened in append mode and new records are written
  to the end of the existing file. If more that one record of the same
  name is written to the database file, the last record written is the
  valid record, i.e. the one that will be used by the REGISTER or
  GEOTRAN tasks.
  <P>
  WCSMAP will terminate with an error if the reference and input images
  are not both either 1D or 2D.
  If the world coordinate system information cannot be read from either
  the reference or input image header, the requested transformations
  from the world &lt;-&gt; logical coordinate systems cannot be compiled for either
  or both images, or the world coordinate systems of the reference and input
  images are fundamentally incompatible in some way, the output logical
  reference and input image coordinates are both set to a grid of points
  spanning the logical pixel space of the input, not the reference image.
  This grid of points defines an identity transformation which will leave
  the input image unchanged if applied by the REGISTER or GEOTRAN tasks.
  <P>
  If <I>verbose</I> is "<TT>yes</TT>" then messages about the progress of the task
  as well as warning messages indicating potential problems are written to
  the standard output. If <I>results</I> is set to a file name then the input
  coordinates, the fitted coordinates, and the residuals of the fit are
  written to that file.
  <P>
  WCSMAP may be run interactively by setting the <I>interactive</I>
  parameter to "<TT>yes</TT>".
  In interactive mode the user has the option of viewing the fit, changing the
  fit parameters, deleting and undeleting points, and replotting
  the data until a satisfactory
  fit has been achieved.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_cursor_commands">CURSOR COMMANDS</A></H2>
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
  :xxterms :yxterms [n/h/f]       X, Y fit cross terms type
  :reject [value]                 Rejection threshold
  </PRE>
  <P>
  <P>
  </UL>
  <! EndSection:   'CURSOR COMMANDS'>
  <H2><A NAME="s_formats">FORMATS</A></H2>
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
  <H2><A NAME="s_references">REFERENCES</A></H2>
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
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Compute the spatial transformation required to match a radio image to an
  X-ray image of the same field using a 100 point coordinate  grid
  and a simple linear transformation.  Both images have accurate sky
  projection world coordinate systems. Print the output world coordinates
  in the coords file in hh:mm:ss.ss and dd:mm:ss.s format. Run geotran
  on the results to do the actual registration.
  <P>
  <PRE>
  	cl&gt; wcsmap radio xray geodb wxformat=%12.2H wyformat=%12.1h \<BR>
  	    interactive-
  <P>
  	cl&gt; geotran radio radio.tran geodb radio
  </PRE>
  <P>
  2. Repeat the previous command but begin with a higher order fit
  and run the task in interactive mode in order to examine the fit
  residuals.
  <P>
  <PRE>
  	cl&gt; wcsmap radio xray geodb wxformat=%12.2H wyformat=%12.1h \<BR>
  	    xxo=4 xyo=4 xxt=half yxo=4 yyo=4 yxt=half
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
              ... type q to quit and save the fit
  <P>
  	cl&gt; geotran radio radio.tran geodb radio
  </PRE>
  <P>
  3. Repeat example 1 but assign a user name to the transform.
  <P>
  <PRE>
  	cl&gt; wcsmap radio xray geodb transforms="m82" wxformat=%12.2H \<BR>
  	    wyformat=%12.1h interactive-
  <P>
  	cl&gt; geotran radio radio.tran geodb m82
  </PRE>
  <P>
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
  wcstran,xregister,wcsxymatch,geomap,register,geotran
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'CURSOR COMMANDS' 'FORMATS' 'REFERENCES' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>