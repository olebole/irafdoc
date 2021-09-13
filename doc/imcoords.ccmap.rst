.. _ccmap:

ccmap — Compute image plate solutions using matched coordinate lists
====================================================================

**Package: imcoords**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  ccmap -- compute plate solutions using matched pixel and celestial coordinate
  lists
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  ccmap input database
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The input text files containing the pixel and celestial coordinates of
  points in the input images. The coordinates are listed one per line with x, y,
  ra / longitude, and dec / latitude in the columns specified by the
  <I>xcolumn</I>, <I>ycolumn</I>, <I>lngcolumn</I>, and <I>latcolumn</I> parameters
  respectively.  Whether all files are combined to produce one solution or
  each file produces a separate solution depends on whether there is a
  matching list of output <I>solutions</I> names or <I>results</I> files.
  </DD>
  </DL>
  <DL>
  <DT><B>database</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='database' Line='database'>
  <DD>The text database file where the computed plate solutions are stored.
  </DD>
  </DL>
  <DL>
  <DT><B>solutions = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='solutions' Line='solutions = ""'>
  <DD>An optional list of plate solution names. If there are multiple input
  coordinate files and no name or a single name is specified then the
  input coordinates are combined to produce a single solution.  Otherwise
  the list must match the number of input coordinate files.  If no names are
  supplied then the database records are assigned the names of the input
  images <I>images</I>, or the names of the coordinate files <I>input</I>.
  In the case of multiple coordinate files the first image or input is used.
  </DD>
  </DL>
  <DL>
  <DT><B>images = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images = ""'>
  <DD>The images associated with the input coordinate files. The number of images
  must be zero or equal to the number of input coordinate files. If an input
  image exists and the <I>update</I> parameter is enabled, the image wcs will
  be created from the linear component of the computed plate solution
  and written to the image header.
  </DD>
  </DL>
  <DL>
  <DT><B>results = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='results' Line='results = ""'>
  <DD>Optional output files containing a summary of the results including a
  description of the plate geometry and a listing of the input coordinates,
  the fitted coordinates, and the fit residuals. The number of
  results files must be zero, one or equal to the number of input files. If
  results is "<TT>STDOUT</TT>" the results summary is printed on the standard output.
  If there are multiple input coordinate files and zero or one output is
  specified then the input coordinates are combined to produce a single solution.
  </DD>
  </DL>
  <DL>
  <DT><B>xcolumn = 1, ycolumn = 2, lngcolumn = 3, latcolumn = 4</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xcolumn' Line='xcolumn = 1, ycolumn = 2, lngcolumn = 3, latcolumn = 4'>
  <DD>The input coordinate file columns containing the x, y, ra / longitude and
  dec / latitude values.
  </DD>
  </DL>
  <DL>
  <DT><B>xmin = INDEF, xmax = INDEF, ymin = INDEF, ymax = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xmin' Line='xmin = INDEF, xmax = INDEF, ymin = INDEF, ymax = INDEF'>
  <DD>The range of x and y pixel coordinates over which the computed coordinate
  transformation is valid. These limits should be left at INDEF or set to
  the values of the column and row limits of the input images, e.g xmin = 1.0,
  xmax = 512, ymin= 1.0, ymax = 512 for a 512 x 512 image.  If xmin, xmax, ymin,
  or ymax are undefined, they are set to the minimum and maximum x and y
  pixels values in <I>input</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>lngunits = "<TT></TT>", latunits = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lngunits' Line='lngunits = "", latunits = ""'>
  <DD>The units of the input ra / longitude and dec / latitude coordinates. The
  options are "<TT>hours</TT>", "<TT>degrees</TT>", and "<TT>radians</TT>" for ra / longitude, and
  "<TT>degrees</TT>" and "<TT>radians</TT>" for dec / latitude. If the lngunits and latunits
  are undefined they default to the preferred units for the coordinate system
  specified by <I>insystem</I>, e.g. "<TT>hours</TT>" and "<TT>degrees</TT>" for equatorial
  systems, and "<TT>degrees</TT>" and "<TT>degrees</TT>" for ecliptic, galactic, and
  supergalactic systems.
  </DD>
  </DL>
  <DL>
  <DT><B>insystem = "<TT>j2000</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='insystem' Line='insystem = "j2000"'>
  <DD>The input celestial coordinate system. The <I>insystem</I> parameter
  sets the preferred units for the input celestial coordinates,
  tells CCMAP how to transform the celestial coordinates of the reference
  point from the reference point coordinate system to the input coordinate
  system, and sets the correct values of the image header keywords CTYPE,
  RADECSYS, EQUINOX, and MJD-WCS if the image header wcs is updated. The 
  systems of most interest to users are "<TT>icrs</TT>", "<TT>j2000</TT>", and "<TT>b1950</TT>" which
  stand for the ICRS J2000.0, FK5 J2000.0 and FK4 B1950.0 celestial coordinate
  systems respectively.  The full set of options are the following:
  <P>
  <DL>
  <DT><B>equinox [epoch]</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='equinox' Line='equinox [epoch]'>
  <DD>The equatorial mean place post-IAU 1976 (FK5) system if equinox is a
  Julian epoch, e.g. J2000.0 or 2000.0, or the equatorial mean place
  pre-IAU 1976 system (FK4) if equinox is a Besselian epoch, e.g. B1950.0
  or 1950.0. Julian equinoxes are prefixed by a J or j, Besselian equinoxes
  by a B or b. Equinoxes without the J / j or B / b prefix are treated as
  Besselian epochs if they are &lt; 1984.0, Julian epochs if they are &gt;= 1984.0.
  Epoch is the epoch of the observation and may be a Julian
  epoch, a Besselian epoch, or a Julian date. Julian epochs
  are prefixed by a J or j, Besselian epochs by a B or b.
  Epochs without the J / j or B / b prefix default to the epoch type of
  equinox if the epoch value &lt;= 3000.0, otherwise epoch is interpreted as
  a Julian date.  If undefined epoch defaults to equinox.
  </DD>
  </DL>
  <DL>
  <DT><B>icrs [equinox] [epoch]</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='icrs' Line='icrs [equinox] [epoch]'>
  <DD>The International Celestial Reference System where equinox is
  a Julian or Besselian epoch e.g. J2000.0  or B1980.0.
  Equinoxes without the J / j or B / b prefix are treated as Julian epochs.
  The default value of equinox is J2000.0.
  Epoch is a Besselian epoch, a Julian epoch, or a Julian date.
  Julian epochs are prefixed by a J or j, Besselian epochs by a B or b.
  Epochs without the J / j or B / b prefix default to Julian epochs
  if the epoch value &lt;= 3000.0, otherwise epoch is interpreted as
  a Julian date.  If undefined epoch defaults to equinox.
  </DD>
  </DL>
  <DL>
  <DT><B>fk5 [equinox] [epoch] </B></DT>
  <! Sec='PARAMETERS' Level=1 Label='fk5' Line='fk5 [equinox] [epoch] '>
  <DD>The equatorial mean place post-IAU 1976 (FK5) system where equinox is
  a Julian or Besselian epoch e.g. J2000.0  or B1980.0.
  Equinoxes without the J / j or B / b prefix are treated as Julian epochs.
  The default value of equinox is J2000.0.
  Epoch is a Besselian epoch, a Julian epoch, or a Julian date.
  Julian epochs are prefixed by a J or j, Besselian epochs by a B or b.
  Epochs without the J / j or B / b prefix default to Julian epochs
  if the epoch value &lt;= 3000.0, otherwise epoch is interpreted as
  a Julian date.  If undefined epoch defaults to equinox.
  </DD>
  </DL>
  <DL>
  <DT><B>fk4 [equinox] [epoch]</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='fk4' Line='fk4 [equinox] [epoch]'>
  <DD>The equatorial mean place pre-IAU 1976 (FK4) system where equinox is a
  Besselian or Julian epoch e.g. B1950.0  or J2000.0,
  and epoch is the Besselian epoch, the Julian epoch, or the Julian date of the
  observation.
  Equinoxes without the J / j or B / b prefix are treated
  as Besselian epochs. The default value of equinox is B1950.0. Epoch
  is a Besselian epoch, a Julian epoch, or a Julian date.
  Julian epochs are prefixed by a J or j, Besselian epochs by a B or b.
  Epochs without the J / j or B / b prefix default to Besselian epochs
  if the epoch value &lt;= 3000.0, otherwise epoch is interpreted as
  a Julian date.  If undefined epoch defaults to equinox.
  </DD>
  </DL>
  <DL>
  <DT><B>noefk4 [equinox] [epoch]</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='noefk4' Line='noefk4 [equinox] [epoch]'>
  <DD>The equatorial mean place pre-IAU 1976 (FK4) system but without the E-terms
  where equinox is a Besselian or Julian epoch e.g. B1950.0 or J2000.0,
  and epoch is the Besselian epoch, the Julian epoch, or the Julian date of the
  observation.
  Equinoxes without the J / j or B / b prefix are treated
  as Besselian epochs. The default value of equinox is B1950.0.
  Epoch is a Besselian epoch, a Julian epoch, or a Julian date.
  Julian epochs are prefixed by a J or j, Besselian epochs by a B or b.
  Epochs without the J / j or B / b prefix default to Besselian epochs
  if the epoch value &lt;= 3000.0, otherwise epoch is interpreted as
  a Julian day.  If undefined epoch defaults to equinox.
  </DD>
  </DL>
  <DL>
  <DT><B>apparent epoch </B></DT>
  <! Sec='PARAMETERS' Level=1 Label='apparent' Line='apparent epoch '>
  <DD>The equatorial geocentric apparent place post-IAU 1976 system where
  epoch is the epoch of observation.
  Epoch is a Besselian epoch, a Julian epoch or a Julian date.
  Julian epochs are prefixed by a J or j, Besselian epochs by a B or b.
  Epochs without the J / j or B / b prefix default to Besselian
  epochs if the epoch value &lt; 1984.0, Julian epochs
  if the epoch value &lt;= 3000.0, otherwise epoch is interpreted as
  a Julian date.
  </DD>
  </DL>
  <DL>
  <DT><B>ecliptic epoch</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='ecliptic' Line='ecliptic epoch'>
  <DD>The ecliptic coordinate system where epoch is the epoch of observation.
  Epoch is a Besselian epoch, a Julian epoch, or a Julian date.
  Julian epochs are prefixed by a J or j, Besselian epochs by a B or b.
  Epochs without the J / j or B / b prefix default to Besselian epochs
  if the epoch values &lt; 1984.0, Julian epochs
  if the epoch value &lt;= 3000.0, otherwise epoch is interpreted as
  a Julian day.
  </DD>
  </DL>
  <DL>
  <DT><B>galactic [epoch]</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='galactic' Line='galactic [epoch]'>
  <DD>The IAU 1958 galactic coordinate system.
  Epoch is a Besselian epoch, a Julian epoch or a Julian date.
  Julian epochs are prefixed by a J or j, Besselian epochs by a B or b.
  Epochs without the J / j or B / b prefix default to Besselian
  epochs if the epoch value &lt; 1984.0, Julian epochs
  if the epoch value &lt;= 3000.0, otherwise epoch is interpreted as
  a Julian date. The default value of epoch is B1950.0.
  </DD>
  </DL>
  <DL>
  <DT><B>supergalactic [epoch]</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='supergalactic' Line='supergalactic [epoch]'>
  <DD>The deVaucouleurs supergalactic coordinate system.
  Epoch is a Besselian epoch, a Julian epoch or a Julian date.
  Julian epochs are prefixed by a J or j, Besselian epochs by a B or b.
  Epochs without the J / j or B / b prefix default to Besselian
  epochs if the epoch value &lt; 1984.0, Julian epochs
  if the epoch value &lt;= 3000.0, otherwise epoch is interpreted as
  a Julian date. The default value of epoch is B1950.0.
  </DD>
  </DL>
  <P>
  In all the above cases fields in [] are optional with the defaults as
  described. The epoch field for the icrs, fk5, galactic, and supergalactic
  coordinate systems is only used if the input coordinates are in the
  equatorial fk4, noefk4, fk5, or icrs systems and proper motions are supplied.
  Since CCMAP does not currently support proper motions these fields are
  not required.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B>refpoint = "<TT>coords</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='refpoint' Line='refpoint = "coords"'>
  <DD>The definition of the sky projection reference point in celestial coordinates,
  e.g. the tangent point in the case of the usual tangent plane projection.
  The options are:
  <DL>
  <DT><B>coords</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='coords' Line='coords'>
  <DD>The celestial coordinates of the reference point are set to the mean of the 
  input celestial coordinates, e.g. the mean of ra / longitude and dec /
  latitude coordinates. If the true tangent point is reasonably close to
  the center of the input coordinate distribution and the input is not
  too large, this approximation is reasonably accurate.
  </DD>
  </DL>
  <DL>
  <DT><B>user</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='user' Line='user'>
  <DD>The values of the keywords <I>lngref</I>, <I>latref</I>, <I>refsystem</I>,
  <I>lngrefunits</I>, and <I>latrefunits</I> are used to determine the celestial
  coordinates of the reference point.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>xref = "<TT>INDEF</TT>", yref = "<TT>INDEF</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xref' Line='xref = "INDEF", yref = "INDEF"'>
  <DD>The reference pixel may be specified as a value or image header keyword.
  In the latter case a reference image must be specified.  By specifying
  the reference pixel the solution will be constrained to putting the
  reference coordinate at that point.
  </DD>
  </DL>
  <DL>
  <DT><B>lngref = "<TT>INDEF</TT>", latref = "<TT>INDEF</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lngref' Line='lngref = "INDEF", latref = "INDEF"'>
  <DD>The ra / longitude and dec / latitude of the reference point(s).  Lngref
  and latref may be numbers, e.g 13:20:42.3 and -33:41:26 or keywords for the
  appropriate parameters in the image header, e.g. RA/DEC or CRVAL1/CRVAL2.
  Each parameter may be a list to apply different reference points to
  each input coordinate list.  If lngref and latref are undefined then
  the position of the reference point defaults to the mean of the input
  coordinates.
  </DD>
  </DL>
  <DL>
  <DT><B>refsystem = "<TT>INDEF</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='refsystem' Line='refsystem = "INDEF"'>
  <DD>The celestial coordinate system of the reference point. Refsystem may
  be any one of the options listed under the <I>insystem</I> parameter, e.g.
  "<TT>b1950</TT>", or an image header keyword containing the epoch of the observation
  in years, e.g. EPOCH for NOAO data. In the latter case the coordinate system is
  assumed to be equatorial FK4 at equinox EPOCH. If refsystem is undefined
  the celestial coordinate system of the reference point defaults to the
  celestial coordinate system of the input coordinates <I>insystem</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>lngrefunits = "<TT></TT>", latrefunits = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lngrefunits' Line='lngrefunits = "", latrefunits = ""'>
  <DD>The units of the reference point celestial  coordinates. The options
  are "<TT>hours</TT>", "<TT>degrees</TT>", and "<TT>radians</TT>" for the ra / longitude coordinates,
  and "<TT>degrees</TT>" and "<TT>radians</TT>" for the dec /latitude coordinates. 
  If lngunits and latunits are undefined they default to the  units of the
  input coordinate system.
  </DD>
  </DL>
  <DL>
  <DT><B>projection = "<TT>tan</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='projection' Line='projection = "tan"'>
  <DD>The sky projection geometry. The most commonly used projections in astronomy
  are "<TT>tan</TT>", "<TT>arc</TT>", "<TT>sin</TT>", and "<TT>lin</TT>". Other supported  standard projections
  are "<TT>ait</TT>", "<TT>car</TT>","<TT>csc</TT>", "<TT>gls</TT>", "<TT>mer</TT>", "<TT>mol</TT>", "<TT>par</TT>", "<TT>pco</TT>", "<TT>qsc</TT>", "<TT>stg</TT>",
  "<TT>tsc</TT>", and "<TT>zea</TT>". A new experimental function "<TT>tnx</TT>", a combination of the
  tangent plate projection and polynomials, is also available.
  </DD>
  </DL>
  <DL>
  <DT><B>fitgeometry = "<TT>general</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fitgeometry' Line='fitgeometry = "general"'>
  <DD>The plate solution geometry to be used. The options are the following, where
  xi and eta refer to the usual standard coordinates used in astrometry.
  <DL>
  <DT><B>shift</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='shift' Line='shift'>
  <DD>Xi and eta shifts only are fit.
  </DD>
  </DL>
  <DL>
  <DT><B>xyscale</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='xyscale' Line='xyscale'>
  <DD>Xi and eta shifts and x and y magnification factors in " / pixel are fit.
  Axis flips are allowed for.
  </DD>
  </DL>
  <DL>
  <DT><B>rotate</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='rotate' Line='rotate'>
  <DD>Xi and eta shifts and a rotation angle are fit. Axis flips are allowed for.
  </DD>
  </DL>
  <DL>
  <DT><B>rscale</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='rscale' Line='rscale'>
  <DD>Xi and eta shifts, a magnification factor in " / pixel assumed to be the same
  in x and y, and a rotation angle are fit. Axis flips are allowed for.
  </DD>
  </DL>
  <DL>
  <DT><B>rxyscale</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='rxyscale' Line='rxyscale'>
  <DD>Xi and eta shifts, x and y magnifications factors in " / pixel, and a rotation
  angle are fit.  Axis flips are allowed for.
  </DD>
  </DL>
  <DL>
  <DT><B>general</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='general' Line='general'>
  <DD>A polynomial of arbitrary order in x and y is fit. A linear term and a
  distortion term are computed separately. The linear term includes a xi and eta
  shift, an x and y scale factor in " / pixel, a rotation and a skew.  Axis
  flips are also allowed for in the linear portion of the fit. The distortion
  term consists of a polynomial fit to the residuals of the linear term. By
  default the distortion term is set to zero.
  </DD>
  </DL>
  <P>
  For all the fitting geometries except "<TT>general</TT>" no distortion term is fit,
  i.e. the x and y polynomial orders are assumed to be 2 and the cross term
  switches are assumed to be set to "<TT>none</TT>", regardless of the values of the
  <I>xxorder</I>, <I>xyorder</I>, <I>xxterms</I>, <I>yxorder</I>, <I>yyorder</I>
  and <I>yxterms</I> parameters set by the user.
  </DD>
  </DL>
  <DL>
  <DT><B>function = "<TT>polynomial</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='function' Line='function = "polynomial"'>
  <DD>The type of analytic coordinate surface to be fit. The options are the
  following.
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
  <DT><B>xxorder = 2, xyorder = 2,  yxorder = 2, yyorder = 2</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xxorder' Line='xxorder = 2, xyorder = 2,  yxorder = 2, yyorder = 2'>
  <DD>The order of the polynomials in x and y for the xi and eta fits respectively.
  The default order and cross term settings define the linear term in x
  and y, where the 6 coefficients can be interpreted in terms of an xi and eta
  shift, an x and y scaling in " / pixel, and rotations of the x and y axes.
  The "<TT>shift</TT>", "<TT>xyscale</TT>", "<TT>rotation</TT>", "<TT>rscale</TT>", and "<TT>rxyscale</TT>", fitting geometries
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
  maximum combined power is MAX (xxorder - 1, xyorder - 1) for the xi fit and
  MAX (yxorder - 1, yyorder - 1) for the eta fit. This is the recommended
  option for higher order plate solutions. 
  </DD>
  </DL>
  <DL>
  <DT><B>full</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='full' Line='full'>
  <DD>The individual polynomial terms contain powers of x and powers of y, whose
  maximum combined power is MAX (xxorder - 1 + xyorder - 1) for the xi fit and
  MAX (yxorder - 1 + yyorder - 1) for the eta fit.
  </DD>
  </DL>
  <P>
  The "<TT>shift</TT>", "<TT>xyscale</TT>", "<TT>rotation</TT>",
  "<TT>rscale</TT>", and "<TT>rxyscale</TT>" fitting geometries, assume that the
  cross term switches are set to "<TT>none</TT>" regardless of the values set by the user.
  If either of the cross-terms parameters is set to "<TT>half</TT>" or "<TT>full</TT>" and
  <I>fitgeometry</I> is "<TT>general</TT>" then a distortion surface is fit to the
  residuals from the linear portion of the fit.
  </DD>
  </DL>
  <DL>
  <DT><B>maxiter = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maxiter' Line='maxiter = 0'>
  <DD>The maximum number of rejection iterations. The default is no rejection.
  </DD>
  </DL>
  <DL>
  <DT><B>reject = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='reject' Line='reject = INDEF'>
  <DD>The rejection limit in units of sigma.
  </DD>
  </DL>
  <DL>
  <DT><B>update = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='update' Line='update = no'>
  <DD>Update the world coordinate system in the input image headers ?
  The required numerical quantities represented by the keywords CRPIX,
  CRVAL, and CD are computed from the linear portion of the plate solution,
  The values of the keywords CTYPE, RADECSYS, EQUINOX, and MJD-WCS
  are set by the <I>projection</I> and <I>insystem</I> parameters. As there
  is currently no standard mechanism for storing the higher order plate solution
  terms if any in the image header wcs, these terms are currently ignored
  unless the projection function is the experimental function "<TT>tnx</TT>". The "<TT>tnx</TT>"
  function is not FITS compatible and can only be understood by IRAF. Any existing
  image wcs represented by the above keywords is overwritten during the update.
  </DD>
  </DL>
  <DL>
  <DT><B>pixsystem = "<TT>logical</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pixsystem' Line='pixsystem = "logical"'>
  <DD>The input pixel coordinate system. The options are:
  <DL>
  <DT><B>logical</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='logical' Line='logical'>
  <DD>The logical pixel coordinate system is the coordinate system of the image
  pixels on disk. Since most users measure the pixel coordinates of objects
  in this system, "<TT>logical</TT>" is the system of choice for most applications.
  </DD>
  </DL>
  <DL>
  <DT><B>physical</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='physical' Line='physical'>
  <DD>The physical coordinate system is the pixel coordinate system of the
  parent image if any. This option may be useful for users working on images
  that are pieces of a larger mosaic.
  </DD>
  </DL>
  <P>
  The choice of pixsystem has no affect on the fitting process, but does 
  determine how the image header wcs is updated.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print detailed messages about the progress of the task on the standard output ?
  </DD>
  </DL>
  <DL>
  <DT><B>interactive = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = yes'>
  <DD>Compute the plate solution interactively ?
  In interactive mode the user may interact with the fitting process, e.g.
  change the order of the fit, reject points, display the data and refit, etc.
  </DD>
  </DL>
  <DL>
  <DT><B>graphics = "<TT>stdgraph</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = "stdgraph"'>
  <DD>The graphics device.
  </DD>
  </DL>
  <DL>
  <DT><B>cursor = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cursor' Line='cursor = ""'>
  <DD>The graphics cursor.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  CCMAP computes the plate solution for an image or set of images using lists
  of matched pixel and celestial coordinates. The celestial coordinates
  are usually equatorial coordinates, but may also be ecliptic, galactic,
  or supergalactic coordinates.  The input coordinate files <I>input</I> must
  be text file tables whose columns are delimited by whitespace. The pixel
  and celestial coordinates are listed in input, one per line with  x, y,
  ra / longitude, and dec / latitude in columns <I>xcolumn</I>, <I>ycolumn</I>,
  <I>lngcolumn</I>, and <I>latcolumn</I> respectively.
  <P>
  The <I>xmin</I>, <I>xmax</I>, <I>ymin</I> and <I>ymax</I> parameters define
  the region of validity of the fit in the pixel coordinate system. They should
  normally either be left set to INDEF, or set to the size of input images
  <I>images</I> if any, e.g. xmin= 1.0, xmax= 512.0, ymin = 1.0, ymax = 512.0
  for a 512 square image. If set these parameters are also used to reject out
  of range pixel data before the actual fitting is done.
  <P>
  The <I>lngunits</I> and <I>latunits</I> parameters set the units of the input
  celestial coordinates. If undefined lngunits and latunits assume sensible
  defaults for the input celestial coordinate system set by the <I>insystem</I>
  parameter, e.g. "<TT>hours</TT>" and "<TT>degrees</TT>" for equatorial coordinates and "<TT>degrees</TT>"
  and "<TT>degrees</TT>" for galactic coordinates. The input celestial coordinate system
  must be one of the following: equatorial, ecliptic, galactic, or supergalactic.
  The equatorial coordinate systems must be one of: 1) FK4, the mean place
  pre-IAU 1976 system, 2) FK4-NO-E, the same as FK4 but without the E-terms,
  3) FK5, the mean place post-IAU 1976 system, 4) GAPPT, the geocentric apparent
  place in the post-IAU 1976 system.
  <P>
  The plate solution computed by CCMAP has the following form, where x and y
  are the pixel coordinates of points in the input image and xi and eta are the
  corresponding standard coordinates in units of " / pixel.
  <P>
  <PRE>
       xi = f (x, y)
      eta = g (x, y)
  </PRE>
  <P>
  The standard coordinates xi and eta are computed from the input celestial
  coordinates using the sky projection geometry <I>projection</I> and
  the celestial coordinates of the projection reference point set by
  the user. The default projection is the tangent plane or gnomonic
  projection commonly used in optical astronomy. The projections most commonly
  used in astronomy are "<TT>sin</TT>" (the orthographic projection, used in radio
  aperture synthesis), "<TT>arc</TT>" (the zenithal equidistant projection, widely
  used as an approximation for Schmidt telescopes), and "<TT>lin</TT>" (linear).
  Other supported projections are "<TT>ait</TT>", "<TT>car</TT>", "<TT>csc</TT>", "<TT>gls</TT>", "<TT>mer</TT>", "<TT>mol</TT>",
  "<TT>par</TT>", "<TT>pco</TT>", "<TT>qsc</TT>", "<TT>stg</TT>", "<TT>tsc</TT>", and "<TT>zea</TT>". The experimental projection
  function "<TT>tnx</TT>" combines the "<TT>tan</TT>" projection with a polynomial fit
  to the residuals can be used to represent more complicated distortion
  functions.
  <P>
  There are two modes in which this task works with multiple input
  coordinate lists.  In one case each input list and possible associated
  image is treated independently and produce separate solutions.  To
  select this option requires specifying a matching list of solution
  names or output results files.  Note that this can also be simply done
  by running the task multiple times with a single input list each time.
  <P>
  In the second mode data from multiple input lists are combined to
  produce a single solution.  This is useful when multiple exposures are
  taken to define a higher quality astrometric solution.  This mode is
  selected when there are multiple input lists, and possibly associated
  images, and no solution name or a single solution name is specified.
  <P>
  When combining input data each set of coordinates may have different
  reference points which can be specified either as a list or by
  reference to image header keywords.  The different reference points
  are used to convert each set of coordinates to the same coordinate
  frame.  Typically this occurs when a set of exposures, each with the
  same coordinate reference pixel, has slightly different pointing as
  defined by the coordinate reference value.  These different points
  result from a dither and can be useful to more completely sample the
  image pixel space.  In other words, astrometric reference stars can be
  moved around the images to produce many more fitting points than occur
  with a single exposure. The key point to this process is that the
  shifts are mapped by the reference points of the pointing and the
  standard coordinates are independent of the pointing.
  <P>
  A particular feature primarily intending for combining multiple
  exposures, but applies to single exposures as well, is an adjustment to
  the specified tangent point value based on the image WCS.  When images,
  reference pixels, and reference coordinates are all defined and the
  images contain a celestial WCS the following computation is performed.
  The reference information replaces the WCS tangent point values, though
  typically the initial reference information is specified as the tangent
  point, and the updated WCS is used to evaluate celestial coordinates
  from the input pixel coordinates. The average difference between the WCS
  evaluated coordinates and the input celestial coordinates is computed.
  This difference is applied to the reference point prior to the standard
  coordinate plate solution calculation.  In other words, the reference
  point is tweaked in the initial image WCS to make it agree on average with
  the input reference coordinates.  If one updates the WCS of the images by
  the plate solution and the repeats the plate solution, particularly when
  using multiple exposures, an iterative convergence to a self-consistent
  WCS of both the tangent point and plate solution can be obtained.
  <P>
  Several polynomial cross terms options are available. Options "<TT>none</TT>", 
  "<TT>half</TT>", and "<TT>full</TT>" are illustrated below for a quadratic polynomial in
  x and y.
  <P>
  <PRE>
  xxterms = "none", xyterms = "none"
  xxorder = 3, xyorder = 3, yxorder = 3, yyorder = 3
  <P>
      xi = a11 + a21 * x + a12 * y +
           a31 * x ** 2 + a13 * y ** 2
     eta = a11' + a21' * x + a12' * y +
           a31' * x ** 2 + a13' * y ** 2
  <P>
  xxterms = "half", xyterms = "half"
  xxorder = 3, xyorder = 3, yxorder = 3, yyorder = 3
  <P>
      xi = a11 + a21 * x + a12 * y +
           a31 * x ** 2 + a22 * x * y + a13 * y ** 2
     eta = a11' + a21' * x + a12' * y +
           a31' * x ** 2 + a22' * x * y + a13' * y ** 2
  <P>
  xxterms = "full", xyterms = "full"
  xxorder = 3, xyorder = 3, yxorder = 3, yyorder = 3
  <P>
      xi = a11 + a21 * x + a31 * x ** 2 +
           a12 * y + a22 * x * y +  a32 * x ** 2 * y +
           a13 * y ** 2 + a23 * x *  y ** 2 + a33 * x ** 2 * y ** 2
     eta = a11' + a21' * x + a31' * x ** 2 +
           a12' * y + a22' * x * y +  a32' * x ** 2 * y +
           a13' * y ** 2 + a23' * x *  y ** 2 + a33' * x ** 2 * y ** 2
  </PRE>
  <P>
  If <I>refpoint</I> is "<TT>coords</TT>", then the sky projection reference point is set
  to the mean of the input celestial coordinates. For images where the true
  reference point is close to the center of the input coordinate distribution,
  this definition is adequate for many purposes. If <I>refpoint</I> is "<TT>user</TT>",
  the user may either set the celestial coordinates of the reference
  point explicitly, e.g. <I>lngref</I> = 13:41:02.3 and <I>latref</I> = -33:42:20,
  or point these parameters to the appropriate keywords in the input image
  header, e.g. <I>lngref</I> = RA, <I>latref</I> = DEC for NOAO image data.
  If undefined the celestial coordinate system of the reference point
  <I>refsystem</I> defaults to the celestial coordinate system of the input
  coordinates, otherwise it be any of the supported celestial coordinate
  systems described above. The user may also set <I>refsystem</I> to the
  image header keyword containing the epoch of the celestial reference point
  coordinates in years, e.g. EPOCH for NOAO data. In this case the
  reference point coordinates are assumed to be equatorial FK4 coordinates at the
  epoch specified by EPOCH. The units of the reference point celestial
  coordinates are specified by the <I>lngrefunits</I> and <I>latrefunits</I>
  parameters. Lngrefunits and latrefunits default to the values of the input
  coordinate units if undefined by either the user or the <I>refsystem</I>
  parameter. ONCE DETERMINED THE REFERENCE POINT CANNOT BE RESET DURING
  THE FITTING PROCESS.
  <P>
  The <I>xref</I> and <I>yref</I> parameters may be used to constrain the
  solution to putting the reference coordinate at the reference pixel.
  Effectively what this does is fix the zero-th order coefficient in the
  linear part of the solution.  If a reference pixel is not specified the
  solution will produce a point determined from the zero-th order
  constant coefficient.  This may not be what is expected based on
  the specified reference celestial coordinate.
  <P>
  The fitting functions f and g are specified by the <I>function</I> parameter
  and may be power series polynomials, Legendre polynomials, or Chebyshev
  polynomials of order <I>xxorder</I> and <I>xyorder</I> in x and <I>yxorder</I>
  and <I>yyorder</I> in y. Cross-terms are optional and are turned on and
  off by setting the <I>xxterms</I> and <I>xyterms</I> parameters. If the
  <B>fitgeometry</B> parameter is anything other than "<TT>general</TT>", the order
  parameters assume the value 2 and the cross-terms switches assume the value
  "<TT>none</TT>", regardless of the values set by the user. All computation are done in
  double precision. Automatic pixel rejection may be enabled by setting
  <I>maxiter</I> &gt; 0 and <I>reject</I> to a  positive value, usually something
  in the range 2.5-5.0.
  <P>
  CCMAP may be run interactively by setting <I>interactive</I> to "<TT>yes</TT>" and
  inputting commands by the use of simple keystrokes. In interactive mode the
  user has the option of changing the fitting parameters and displaying the
  data and fit graphically until a satisfactory fit has been achieved. The
  keystroke commands are listed below.
  <P>
  <PRE>
  <P>
  ?       Print options
  f       Fit data and graph fit with the current graph type (g,x,r,y,s)
  g       Graph the data and the current fit
  x,r     Graph the xi residuals versus x and y respectively
  y,s     Graph the eta residuals versus x and y respectively
  d,u     Delete or undelete the data point nearest the cursor
  o       Overplot the next graph
  c       Toggle the line of constant x and y plotting option
  t       Plot a line of constant x and y through nearest data point
  l       Print xishift, etashift, xscale, yscale, xrotate, yrotate
  q       Exit the interactive fitting code
  </PRE>
  <P>
  The parameters listed below can be changed interactively with simple colon
  commands. Typing the parameter name along will list the current value.
  <P>
  <PRE>
  :show                List parameters
  :projection          Sky projection 
  :refpoint            Sky projection reference point
  :fit      [value]    Fit type (shift,xyscale,rotate,rscale,rxyscale,general)
  :function [value]    Fitting function (chebyshev,legendre,polynomial)
  :xxorder  [value]    Xi fitting function order in x
  :xyorder  [value]    Xi fitting function order in y
  :yxorder  [value]    Eta fitting function order in x
  :yyorder  [value]    Eta fitting function order in y
  :xxterms  [n/h/f]    The xi fit cross terms type
  :yxterms  [n/h/f]    The eta fit cross terms type
  :maxiter  [value]    Maximum number of rejection iterations
  :reject   [value]    K-sigma rejection threshold
  </PRE>
  <P>
  The final fit is stored in the text database file <I>database</I> file in a
  format suitable for use by the CCSETWCS and CCTRAN tasks. Each fit is
  stored in a record whose name is the name of the input image <I>image</I>
  if one is supplied, or the name of the input coordinate file <I>input</I>.
  <P>
  If the <I>update</I> switch is "<TT>yes</TT>" and an input image is specified,
  a new image wcs is derived from the linear component of the computed plate
  solution and written to the image header. The numerical components of
  the new image wcs are written to the standards FITS keywords, CRPIX, CRVAL,
  and CD, with the actual values depending on the input pixel coordinate
  system <I>pixsystem</I>. 
  The FITS keywords which define the image celestial coordinate
  system CTYPE, RADECSYS, EQUINOX, and MJD-WCS are set by the <I>insystem</I> and
  <I>projection</I> parameters. 
  <P>
  The first four characters of the values of the ra / longitude and dec / latitude
  axis CTYPE keywords specify the celestial coordinate system. They are set to
  RA-- / DEC- for equatorial coordinate systems, ELON / ELAT for the ecliptic
  coordinate system, GLON / GLAT for the galactic coordinate system, and
  SLON / SLAT for the supergalactic coordinate system.
  <P>
  The second four characters of the values of the ra / longitude and dec /
  latitude axis CTYPE keywords specify the sky projection geometry. IRAF
  currently supports the TAN, SIN, ARC, AIT, CAR, CSC, GLS, MER, MOL, PAR, PCO,
  QSC, STG, TSC, and ZEA standard projections, in which case the second 4
  characters of CTYPE are set to  -TAN, -ARC, -SIN, etc. IRAF and CCMAP also
  support the experiment TAN plus polynomials function driver. 
  <P>
  If the input celestial coordinate system is equatorial, the value of the
  RADECSYS keyword specifies the fundamental equatorial system, EQUINOX
  specifies the epoch of the mean place, and MJD-WCS specifies the epoch 
  for which the mean place is correct. The permitted values of
  RADECSYS are FK4, FK4-NO-E, FK5, ICRS, and GAPPT. EQUINOX is entered in years
  and interpreted as a Besselian epoch for the FK4 system, a Julian epoch
  for the FK5 system. The epoch of the wcs MJD-WCS is entered as 
  a modified Julian date. Only those keywords necessary to defined the
  new wcs are written. Any existing keywords which are not required to
  define the wcs or are redundant are removed, with the exception of
  DATE-OBS and EPOCH, which are left unchanged for obvious (DATE_OBS) and
  historical (use of EPOCH keyword at NOAO) reasons.
  <P>
  If <I>verbose</I> is "<TT>yes</TT>", various pieces of useful information are
  printed to the terminal as the task proceeds. If <I>results</I> is set to a
  file name then the original pixel and celestial coordinates, the fitted
  celestial coordinates, and the residuals of the fit in arcseconds are written
  to that file.
  <P>
  The transformation computed by the "<TT>general</TT>" fitting geometry is arbitrary
  and does not correspond to a physically meaningful model. However the computed
  coefficients for the linear term can be given a simple geometrical 
  interpretation for all the fitting geometries as shown below.
  <P>
  <PRE>
  	fitting geometry = general (linear term)
  	     xi = a + b * x + c * y
  	    eta = d + e * x + f * y
  <P>
  	fitting geometry = shift
  	     xi = a + x
  	    eta = d + y
  <P>
  	fitting geometry = xyscale
  	     xi = a + b * x
  	    eta = d + f * y
  <P>
  	fitting geometry = rotate
  	     xi = a + b * x + c * y
  	    eta = d + e * x + f * y
  	    b * f - c * e = +/-1
  	    b = f, c = -e or b = -f, c = e
  <P>
  	fitting geometry = rscale
  	     xi = a + b * x + c * y
  	    eta = d + e * x + f * y
  	    b * f - c * e = +/- const
  	    b = f, c = -e or b = -f, c = e
  <P>
  	fitting geometry = rxyscale
  	     xi = a + b * x + c * y
  	    eta = d + e * x + f * y
  	    b * f - c * e = +/- const
  </PRE>
  <P>
  The coefficients can be interpreted as follows. X0, y0, xi0, eta0
  are the origins in the reference and input frames respectively. By definition
  xi0 and eta0 are 0.0 and 0.0 respectively. Rotation and skew are the rotation
  of the x and y axes and their deviation from perpendicularity respectively.
  Xmag and ymag are the scaling factors in x and y in " / pixel and are assumed
  to be positive by definition.
  <P>
  <PRE>
  	general (linear term)
  	    xrotation = rotation - skew / 2
  	    yrotation = rotation + skew / 2
  	    b = xmag * cos (xrotation)
  	    c = ymag * sin (yrotation)
  	    e = -xmag * sin (xrotation)
  	    f = ymag * cos (yrotation)
  	    a = xi0 - b * x0 - c * y0 = xshift
  	    d = eta0 - e * x0 - f * y0 = yshift
  <P>
  	shift
  	    xrotation = 0.0,  yrotation = 0.0
  	    xmag = ymag = 1.0
  	    b = 1.0
  	    c = 0.0
  	    e = 0.0
  	    f = 1.0
  	    a = xi0 - x0 = xshift
  	    d = eta0 - y0 = yshift
  <P>
  	xyscale
  	    xrotation 0.0 / 180.0 yrotation = 0.0
  	    b = + /- xmag
  	    c = 0.0
  	    e = 0.0
  	    f = ymag
  	    a = xi0 - b * x0 = xshift
  	    d = eta0 - f * y0 = yshift
  <P>
  	rscale
  	    xrotation = rotation + 0 / 180, yrotation = rotation
  	    mag = xmag = ymag
  	    const = mag * mag
  	    b = mag * cos (xrotation)
  	    c = mag * sin (yrotation)
  	    e = -mag * sin (xrotation)
  	    f = mag * cos (yrotation)
  	    a = xi0 - b * x0 - c * y0 = xshift
  	    d = eta0 - e * x0 - f * y0 = yshift
  <P>
  	rxyscale
  	    xrotation = rotation + 0 / 180, yrotation = rotation
  	    const = xmag * ymag
  	    b = xmag * cos (xrotation)
  	    c = ymag * sin (yrotation)
  	    e = -xmag * sin (xrotation)
  	    f = ymag * cos (yrotation)
  	    a = xi0 - b * x0 - c * y0 = xshift
  	    d = eta0 - e * x0 - f * y0 = yshift
  </PRE>
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>References</H3>
  <! BeginSection: 'REFERENCES'>
  <UL>
  <P>
  <P>
  Additional information on the IRAF world coordinate systems can be found in
  the help pages for the WCSEDIT and WCRESET tasks.
  Detailed documentation for the IRAF world coordinate system interface MWCS
  can be found in the file "<TT>iraf$sys/mwcs/MWCS.hlp</TT>". This file can be
  formatted and printed with the command "<TT>help iraf$sys/mwcs/MWCS.hlp fi+ |
  lprint</TT>".
  <P>
  Details of the FITS header world coordinate system interface can
  be found in the draft paper "<TT>World Coordinate Systems Representations Within the
  FITS Format</TT>" by Hanisch and Wells, available from the iraf anonymous ftp
  archive and the draft paper which supersedes it "<TT>Representations of Celestial
  Coordinates in FITS</TT>" by Greisen and Calabretta available from the NRAO
  anonymous ftp archives.
  <P>
  The spherical astronomy routines employed here are derived from the Starlink
  SLALIB library provided courtesy of Patrick Wallace. These routines
  are very well documented internally with extensive references provided
  where appropriate. Interested users are encouraged to examine the routines
  for this information. Type "<TT>help slalib</TT>" to get a listing of the SLALIB
  routines, "<TT>help slalib opt=sys</TT>" to get a concise summary of the library,
  and "<TT>help &lt;routine&gt;</TT>" to get a description of each routine's calling sequence,
  required input and output, etc. An overview of the library can be found in the
  paper "<TT>SLALIB - A Library of Subprograms</TT>", Starlink User Note 67.7
  by P.T. Wallace, available from the Starlink archives.
  <P>
  <P>
  <P>
  </UL>
  <! EndSection:   'REFERENCES'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Compute the plate scale for the test image dev$pix given the following
  coordinate list. Set the tangent point to the mean of the input celestial
  coordinates. Compute the plate scale interactively.
  <P>
  <PRE>
  cl&gt; type coords
  <P>
  13:29:47.297  47:13:37.52  327.50  410.38
  13:29:37.406  47:09:09.18  465.50   62.10
  13:29:38.700  47:13:36.23  442.01  409.65
  13:29:55.424  47:10:05.15  224.35  131.20
  13:30:01.816  47:12:58.79  134.37  356.33
  <P>
  cl&gt; imcopy dev$pix pix
  <P>
  cl&gt; hedit pix epoch 1987.26 
  <P>
  cl&gt; ccmap coords coords.db image=pix xcol=3 ycol=4 lngcol=1 latcol=2
  <P>
      ... a plot of the mapping function appears
      ... type ? to see the list of commands
      ... type x to see the xi fit residuals versus x
      ... type r to see the xi fit residuals versus y
      ... type y to see the eta fit residuals versus x
      ... type s to see the eta fit residuals versus y
      ... type g to return to the default plot
      ... type l to see the computed x and y scales in " / pixel
      ... type q to quit and save fit
  </PRE>
  <P>
  2. Repeat example 2 but compute the fit non-interactively and list the
  fitted values of the ra and dec and their residuals on the standard
  output.
  <P>
  <PRE>
  cl&gt; ccmap coords coords.db image=pix results=STDOUT xcol=3 ycol=4 \<BR>
  lngcol=1 latcol=2 inter- 
  <P>
  # Coords File: coords  Image: pix
  #     Database: coords.db  Record: pix
  # Refsystem: j2000  Coordinates: equatorial FK5
  #     Equinox: J2000.000 Epoch: J2000.00000000 MJD: 51544.50000
  # Insystem: j2000  Coordinates: equatorial FK5
  #     Equinox: J2000.000 Epoch: J2000.00000000 MJD: 51544.50000
  # Coordinate mapping status
  #     XI fit ok.  ETA fit ok.
  #     Ra/Dec or Long/Lat fit rms: 0.229  0.241   (arcsec  arcsec)
  # Coordinate mapping parameters
  #     Sky projection geometry: tan
  #     Reference point: 13:29:48.129  47:11:53.37  (hours  degrees)
  #     Reference point: 318.735  273.900  (pixels  pixels)
  #     X and Y scale: 0.764  0.767  (arcsec/pixel  arcsec/pixel)
  #     X and Y axis rotation: 179.110  358.958  (degrees  degrees)
  # Wcs mapping status
  #     Ra/Dec or Long/Lat wcs rms: 0.229  0.241   (arcsec  arcsec)
  # 
  #                     Input Coordinate Listing
  # X      Y       Ra          Dec        Ra(fit)      Dec(fit)    Dra    Ddec
  # 
  327.5  410.4  13:29:47.30  47:13:37.5  13:29:47.28  47:13:37.9  0.128 -0.370
  465.5   62.1  13:29:37.41  47:09:09.2  13:29:37.42  47:09:09.2 -0.191 -0.062
  442.0  409.6  13:29:38.70  47:13:36.2  13:29:38.70  47:13:35.9  0.040  0.282
  224.3  131.2  13:29:55.42  47:10:05.2  13:29:55.40  47:10:05.1  0.289  0.059
  134.4  356.3  13:30:01.82  47:12:58.8  13:30:01.84  47:12:58.7 -0.267  0.091
  </PRE>
  <P>
  3. Repeat the previous example but in this case input the position of the
  tangent point in fk4 1950.0 coordinates.
  <P>
  <PRE>
  cl&gt; ccmap coords coords.db image=pix results=STDOUT xcol=3 ycol=4 lngcol=1 \<BR>
  latcol=2 refpoint=user lngref=13:27:46.9 latref=47:27:16 refsystem=b1950.0 \<BR>
  inter- 
  <P>
  # Coords File: coords  Image: pix
  #     Database: coords.db  Record: pix
  # Refsystem: b1950.0  Coordinates: equatorial FK4
  #     Equinox: B1950.000 Epoch: B1950.00000000 MJD: 33281.92346
  # Insystem: j2000  Coordinates: equatorial FK5
  #     Equinox: J2000.000 Epoch: J2000.00000000 MJD: 51544.50000
  # Coordinate mapping status
  #     XI fit ok.  ETA fit ok.
  #     Ra/Dec or Long/Lat fit rms: 0.229  0.241   (arcsec  arcsec)
  # Coordinate mapping parameters
  #     Sky projection geometry: tan
  #     Reference point: 13:29:53.273  47:11:48.36  (hours  degrees)
  #     Reference point: 250.256  266.309  (pixels  pixels)
  #     X and Y scale: 0.764  0.767  (arcsec/pixel  arcsec/pixel)
  #     X and Y axis rotation: 179.126  358.974  (degrees  degrees)
  # Wcs mapping status
  #     Ra/Dec or Long/Lat wcs rms: 0.229  0.241   (arcsec  arcsec)
  #
  #                     Input Coordinate Listing
  #  X      Y       Ra         Dec        Ra(fit)      Dec(fit)    Dra    Ddec
  <P>
  327.5  410.4  13:29:47.30  47:13:37.5  13:29:47.28  47:13:37.9  0.128 -0.370
  465.5   62.1  13:29:37.41  47:09:09.2  13:29:37.42  47:09:09.2 -0.191 -0.062
  442.0  409.6  13:29:38.70  47:13:36.2  13:29:38.70  47:13:35.9  0.040  0.282
  224.3  131.2  13:29:55.42  47:10:05.2  13:29:55.40  47:10:05.1  0.289  0.059
  134.4  356.3  13:30:01.82  47:12:58.8  13:30:01.84  47:12:58.7 -0.267  0.091
  </PRE>
  <P>
  Note the computed image scales are identical in examples 2 and 3 but that
  the assumed position of the tangent point is different (the second estimate
  is more accurate) producing different values for the pixel and celestial
  coordinates of the reference point and small differences in the computed
  rotation angles.
   
  4. Repeat the previous example but in this case extract the position of the
  tangent point in from the image header keywords RA, DEC, and EPOCH. 
  <P>
  <PRE>
  cl&gt; imheader pix l+ 
  <P>
  DATE-OBS= '05/04/87'            /  DATE DD/MM/YY
  RA      = '13:29:24.00'         /  RIGHT ASCENSION
  DEC     = '47:15:34.00'         /  DECLINATION
  EPOCH   =              1987.26  /  EPOCH OF RA AND DEC
  <P>
  cl&gt; ccmap coords coords.db image=pix results=STDOUT xcol=3 ycol=4 \<BR>
  lngcol=1 latcol=2 refpoint=user lngref=RA latref=DEC refsystem=EPOCH \<BR>
  inter-
  <P>
  # Coords File: coords  Image: pix
  #     Database: coords.db  Record: pix
  # Refsystem: fk4 b1987.26  Coordinates: equatorial FK4
  #     Equinox: B1987.260 Epoch: B1987.26000000 MJD: 46890.84779
  # Insystem: j2000  Coordinates: equatorial FK5
  #     Equinox: J2000.000 Epoch: J2000.00000000 MJD: 51544.50000
  # Coordinate mapping status
  #     XI fit ok.  ETA fit ok.
  #     Ra/Dec or Long/Lat fit rms: 0.229  0.241   (arcsec  arcsec)
  # Coordinate mapping parameters
  #     Sky projection geometry: tan
  #     Reference point: 13:29:56.232  47:11:38.19  (hours  degrees)
  #     Reference point: 211.035  252.447  (pixels  pixels)
  #     X and Y scale: 0.764  0.767  (arcsec/pixel  arcsec/pixel)
  #     X and Y axis rotation: 179.135  358.983  (degrees  degrees)
  # Wcs mapping status
  #     Ra/Dec or Long/Lat wcs rms: 0.229  0.241   (arcsec  arcsec)
  # 
  #                     Input Coordinate Listing
  #  X      Y       Ra         Dec        Ra(fit)      Dec(fit)    Dra    Ddec
  <P>
  327.5  410.4  13:29:47.30  47:13:37.5  13:29:47.28  47:13:37.9  0.128 -0.370
  465.5   62.1  13:29:37.41  47:09:09.2  13:29:37.42  47:09:09.2 -0.191 -0.062
  442.0  409.6  13:29:38.70  47:13:36.2  13:29:38.70  47:13:35.9  0.040  0.282
  224.3  131.2  13:29:55.42  47:10:05.2  13:29:55.40  47:10:05.1  0.289  0.059
  134.4  356.3  13:30:01.82  47:12:58.8  13:30:01.84  47:12:58.7 -0.267  0.091
  <P>
  </PRE>
  <P>
  Note that the position of the tangent point is slightly different again but
  that this does not have much affect on the fitted coordinates for this image.
  <P>
  5. Repeat the third example but this time store the computed world coordinate
  system in the image header and check the header update with the imheader and
  skyctran tasks.
  <P>
  <PRE>
  cl&gt; imheader pix l+ 
  DATE-OBS= '05/04/87'            /  DATE DD/MM/YY
  RA      = '13:29:24.00'         /  RIGHT ASCENSION
  DEC     = '47:15:34.00'         /  DECLINATION
  EPOCH   =              1987.26  /  EPOCH OF RA AND DEC
  <P>
  cl&gt; ccmap coords coords.db image=pix results=STDOUT xcol=3 ycol=4  \<BR>
  lngcol=1 latcol=2 refpoint=user lngref=13:27:46.9 latref=47:27:16    \<BR>
  refsystem=b1950.0 inter- update+
  <P>
  # Coords File: coords  Image: pix
  #     Database: coords.db  Record: pix
  # Refsystem: b1950.0  Coordinates: equatorial FK4
  #     Equinox: B1950.000 Epoch: B1950.00000000 MJD: 33281.92346
  # Insystem: j2000  Coordinates: equatorial FK5
  #     Equinox: J2000.000 Epoch: J2000.00000000 MJD: 51544.50000
  # Coordinate mapping status
  # Coordinate mapping status
  #     XI fit ok.  ETA fit ok.
  #     Ra/Dec or Long/Lat fit rms: 0.229  0.241   (arcsec  arcsec)
  # Coordinate mapping parameters
  #     Sky projection geometry: tan
  #     Reference point: 13:29:53.273  47:11:48.36  (hours  degrees)
  #     Reference point: 250.256  266.309  (pixels  pixels)
  #     X and Y scale: 0.764  0.767  (arcsec/pixel  arcsec/pixel)
  #     X and Y axis rotation: 179.126  358.974  (degrees  degrees)
  # Wcs mapping status
  #     Ra/Dec or Long/Lat wcs rms: 0.229  0.241   (arcsec  arcsec)
  # Updating image header wcs
  # 
  # 
  #                     Input Coordinate Listing
  #  X      Y       Ra          Dec        Ra(fit)     Dec(fit)    Dra    Ddec
  <P>
  327.5  410.4  13:29:47.30  47:13:37.5  13:29:47.28  47:13:37.9  0.128 -0.370
  465.5   62.1  13:29:37.41  47:09:09.2  13:29:37.42  47:09:09.2 -0.191 -0.062
  442.0  409.6  13:29:38.70  47:13:36.2  13:29:38.70  47:13:35.9  0.040  0.282
  224.3  131.2  13:29:55.42  47:10:05.2  13:29:55.40  47:10:05.1  0.289  0.059
  134.4  356.3  13:30:01.82  47:12:58.8  13:30:01.84  47:12:58.7 -0.267  0.091
  <P>
  cl&gt; imheader pix l+ 
  DATE-OBS= '05/04/87'            /  DATE DD/MM/YY
  RA      = '13:29:24.00'         /  RIGHT ASCENSION
  DEC     = '47:15:34.00'         /  DECLINATION
  EPOCH   =              1987.26  /  EPOCH OF RA AND DEC
  RADECSYS= 'FK5     '
  EQUINOX =                2000.
  MJD-WCS =              51544.5
  WCSDIM  =                    2
  CTYPE1  = 'RA---TAN'
  CTYPE2  = 'DEC--TAN'
  CRVAL1  =     202.471969550729
  CRVAL2  =     47.1967667056819
  CRPIX1  =     250.255619786203
  CRPIX2  =     266.308757328719
  CD1_1   =  -2.1224568721716E-4
  CD1_2   =  -3.8136850875221E-6
  CD2_1   =  -3.2384199624421E-6
  CD2_2   =  2.12935798198448E-4
  LTM1_1  =                   1.
  LTM2_2  =                   1.
  WAT0_001= 'system=image'
  WAT1_001= 'wtype=tan axtype=ra'
  WAT2_001= 'wtype=tan axtype=dec'
  <P>
  cl&gt; skyctran coords STDOUT "pix log" "pix world" lngcol=3 latcol=4 trans+
  <P>
  # Insystem: pix logical  Projection: TAN  Ra/Dec axes: 1/2
  #     Coordinates: equatorial FK5 Equinox: J2000.000
  #     Epoch: J2000.00000000 MJD: 51544.50000
  # Outsystem: pix world  Projection: TAN  Ra/Dec axes: 1/2
  #     Coordinates: equatorial FK5 Equinox: J2000.000
  #     Epoch: J2000.00000000 MJD: 51544.50000
  <P>
  # Input file: incoords  Output file: STDOUT
  <P>
  13:29:47.297  47:13:37.52 13:29:47.284 47:13:37.89
  13:29:37.406  47:09:09.18 13:29:37.425 47:09:09.24
  13:29:38.700  47:13:36.23 13:29:38.696 47:13:35.95
  13:29:55.424  47:10:05.15 13:29:55.396 47:10:05.09
  13:30:01.816  47:12:58.79 13:30:01.842 47:12:58.70
  <P>
  </PRE>
  <P>
  Note that two versions of the rms values are printed, one for the fit
  and one for the wcs fit. For the default fitting parameters these
  two estimates should be identical. If a non-linear high order plate
  solution is requested however, the image wcs will have lower precision
  than the than the full plate solution, because only the linear component
  of the plate solution is preserved in the wcs.
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  cctran,ccsetwcs,skyctran,imctran,finder.tfinder,finder.tastrom
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'REFERENCES' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
