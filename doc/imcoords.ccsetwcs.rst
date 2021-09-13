.. _ccsetwcs:

ccsetwcs — Create an image celestial wcs from the ccmap plate solution
======================================================================

**Package: imcoords**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  ccsetwcs -- create an image wcs from a plate solution 
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  ccsetwcs image database solutions
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>images</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>The input images for which the wcs is to be created.
  </DD>
  </DL>
  <DL>
  <DT><B>database</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='database' Line='database'>
  <DD>The text database file written by the ccmap task containing the
  plate solutions. If database is undefined ccsetwcs computes
  the image wcs using the xref, yref, xmag, ymag, xrotation, yrotation,
  lngref, latref, lngrefunits, latrefunits, and projection parameters.
  </DD>
  </DL>
  <DL>
  <DT><B>solutions</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='solutions' Line='solutions'>
  <DD>The list of plate solutions. The number of plate solutions must be one
  or equal to the number of input images.  Solutions is either a user name
  supplied to the ccmap task, or the
  name of the ccmap task input image for which the plate solution is valid,
  or the name of the coordinate file that the ccmap task used to compute the
  plate solution. The quantities stored in transform always supersede the
  values of the xref, yref, xmag, ymag, xrotation, yrotation, lngref, latref,
  lnrefunits, latrefunits, and projection parameters.
  </DD>
  </DL>
  <DL>
  <DT><B>xref = INDEF, yref = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xref' Line='xref = INDEF, yref = INDEF'>
  <DD>The x and y pixel coordinates of the sky projection reference point.
  If database is undefined then xref and yref default to the center of the
  image in pixel coordinates, otherwise these parameters are ignored.
  </DD>
  </DL>
  <DL>
  <DT><B>xmag = INDEF, ymag = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xmag' Line='xmag = INDEF, ymag = INDEF'>
  <DD>The x and y scale factors in arcseconds per pixel. If database is undefined
  xmag and ymag default to 1.0 and 1.0 arcsec / pixel, otherwise these parameters
  are ignored.
  </DD>
  </DL>
  <DL>
  <DT><B>xrotation = INDEF, yrotation = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xrotation' Line='xrotation = INDEF, yrotation = INDEF'>
  <DD>The x and y rotation angles in degrees measured counter-clockwise with
  respect to the x and y axes. Xrotation and yrotation are interpreted as the
  rotation of the coordinates with respect to the x and y axes and default 0.0
  and 0.0 degrees. For example xrotation and yrotation values of 30.0 and 30.0
  will rotate a point 30 degrees counter-clockwise with respect to the x and y
  axes. To flip the x axis coordinates in this case either set the angles to
  210.0 and 30.0 degrees or leave the angles set to 30.0 and 30.0 and set the
  xmag parameter to a negative value. To set east to the up, down, left, and
  right directions, set xrotation to 90, 270, 180, and 0 respectively. To set
  north to the up, down, left, and right directions, set yrotation to  0, 180,
  90, and 270 degrees respectively. Any global rotation must be added to both the
  xrotation and yrotation values.
  </DD>
  </DL>
  <DL>
  <DT><B>lngref = INDEF, latref = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lngref' Line='lngref = INDEF, latref = INDEF'>
  <DD>The celestial coordinates of the sky projection reference point, e.g.
  the ra and dec of the reference point for equatorial systems. If database is
  undefined lngref and latref default to 0.0 and 0.0, otherwise these parameters
  are ignored.
  </DD>
  </DL>
  <DL>
  <DT><B>lngunits = "<TT></TT>", latunits = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lngunits' Line='lngunits = "", latunits = ""'>
  <DD>The units of the lngref and latref parameters.
  The options are "<TT>hours</TT>", "<TT>degrees</TT>", "<TT>radians</TT>" for the ra / longitude
  coordinates, and "<TT>degrees</TT>" and "<TT>radians</TT>" for the dec / latitude coordinates.
  If database is undefined then lngunits and latunits default to the preferred
  units for the celestial coordinate system defined by the <I>coosystem</I>
  parameter, otherwise these parameters are ignored.
  </DD>
  </DL>
  <DL>
  <DT><B>transpose = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='transpose' Line='transpose = no'>
  <DD>Transpose the newly created image wcs ?
  </DD>
  </DL>
  <DL>
  <DT><B>projection = "<TT>tan</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='projection' Line='projection = "tan"'>
  <DD>The sky projection geometry. The most commonly used projections in
  astronomy are "<TT>tan</TT>", "<TT>arc</TT>", "<TT>sin</TT>", and "<TT>lin</TT>". Other supported projections
  are "<TT>ait</TT>", "<TT>car</TT>", "<TT>csc</TT>", "<TT>gls</TT>", "<TT>mer</TT>", "<TT>mol</TT>", "<TT>par</TT>", "<TT>pco</TT>", "<TT>qsc</TT>", "<TT>stg</TT>",
  "<TT>tsc</TT>", and "<TT>zea</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>coosystem = "<TT>j2000</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='coosystem' Line='coosystem = "j2000"'>
  <DD>The celestial coordinate system. The systems of most interest to users
  are "<TT>icrs</TT>", "<TT>j2000</TT>" and "<TT>b1950</TT>" which stand for the ICRS J2000.0, FK5 J2000.0,
  and FK4 B1950.0 celestial coordinate systems respectively. The full set of
  options are listed below. The celestial coordinate system sets the preferred
  units for the lngref and latref parameters and the correct values of the image
  wcs header keywords CTYPE, RADECSYS, EQUINOX, and MJD-WCS if the image header
  wcs is updated.  If database is undefined the coosystem parameter is used,
  otherwise this parameter is ignored.
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
  described. The epoch field for icrs, fk5, galactic, and supergalactic
  coordinate systems is required only if the input coordinates are in the
  equatorial fk4, noefk4, fk5, or icrs systems and proper motions are defined.
  </DD>
  </DL>
  <DL>
  <DT><B>update = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='update' Line='update = yes'>
  <DD>Update the world coordinate system in the input image headers ?
  The numerical quantities represented by the keywords CRPIX,
  CRVAL, and CD are computed from the linear portion of the plate solution.
  The values of the keywords CTYPE, RADECSYS, EQUINOX, and MJD-WCS
  are set by the <I>projection</I> and <I>coosystem</I> parameters if database
  is undefined, otherwise projection and coosystem are read from the plate
  solution. As there is currently no standard mechanism for storing the higher
  order plate solution terms if any in the image header wcs, these terms are
  ignored. Any existing image wcs represented by the above keywords is
  overwritten during the update.
  </DD>
  </DL>
  <DL>
  <DT><B>pixsystem = "<TT>logical</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pixsystem' Line='pixsystem = "logical"'>
  <DD>The pixel coordinate system. The options are:
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
  parent image. This option is useful for users working on images that are
  pieces of a larger mosaic.
  </DD>
  </DL>
  <P>
  The pixsystem parameter is only used if no database solution is specified.
  Otherwise pixsystem is read from the database file.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print detailed messages about the progress of the task on the standard output ?
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  CCSETWCS creates an image world coordinate system from the plate solution
  computed by the CCMAP task or supplied by the user, and writes it to the
  headers of the input images <I>images</I> if the <I>update</I> parameter is yes.
  <P>
  The plate solution can either be read from record <I>solutions</I> in the
  database file <I>database</I> written by CCMAP, or specified by the user
  via the <I>xref</I>, <I>yref</I>, <I>xmag</I>, <I>ymag</I>, <I>xrotation</I>,
  <I>yrotation</I>, <I>lngref</I>, <I>latref</I>, <I>lngunits</I>, <I>latunits</I>,
  <I>transpose</I>, <I>projection</I>, <I>coosystem</I> and <I>pixsystem</I>
  parameters.
  <P>
  The plate solution computed by CCMAP has the following form where x and y
  are the image pixel coordinates and xi and eta are the corresponding standard
  coordinates in arcseconds per pixel. The standard coordinates are computed
  by applying the appropriate sky projection to the celestial coordinates.
  <P>
  <P>
  <PRE>
  	 xi = f (x, y)
  	eta = g (x, y)
  </PRE>
  <P>
  The functions f and g are either power series, Legendre, or Chebyshev
  polynomials whose order and region of validity were set by the user when
  CCMAP was run. The computed plate solution is somewhat arbitrary and does
  not correspond to any physically meaningful model. However the linear
  component of the plate solution can be given the simple geometrical
  interpretation shown below.
  <P>
  <PRE>
  	  xi = a + b * x + c * y
  	 eta = d + e * x + f * y
  	   b = xmag * cos (xrotation)
  	   c = ymag * sin (yrotation)
  	   e = -xmag * sin (xrotation)
  	   f = ymag * cos (yrotation)
  	   a = xi0 - b * xref - c * yref = xshift
  	   d = eta0 - e * xref - f * yref = yshift
  	   xi0 = 0.0
  	   eta0 = 0.0
  </PRE>
  <P>
  xref, yref, xi0, and eta0 are the origins of the pixel and standard
  coordinate systems respectively. xmag and ymag are the x and y scale factors
  in " / pixel and xrotation and yrotation are the rotation angles measured
  counter-clockwise of the x and y axes.
  <P>
  If the CCMAP database is undefined then CCSETWCS computes a linear plate
  solution using the parameters <I>xref</I>, <I>yref</I>, <I>xmag</I>,
  <I>ymag</I>, <I>xrotation</I>, <I>yrotation</I>, <I>lngref</I>, <I>latref</I>,
  <I>lngunits</I>, <I>latunits</I>, <I>transpose</I>,  and
  <I>projection</I> as shown below. Note that in this case
  xrotation and yrotation are interpreted as the rotation of the coordinates
  themselves not the coordinate axes. 
  <P>
  <PRE>
  	  xi = a + b * x + c * y
  	 eta = d + e * x + f * y
  	   b = xmag * cos (xrotation)
  	   c = -ymag * sin (yrotation)
  	   e = xmag * sin (xrotation)
  	   f = ymag * cos (yrotation)
  	   a = xi0 - b * xref - c * yref = xshift
  	   d = eta0 - e * xref - f * yref = yshift
  	   xi0 = 0.0
  	   eta0 = 0.0
  </PRE>
  <P>
  The <I>transpose</I> parameter can be used to transpose the newly created
  image wcs.
  <P>
  If the <I>update</I> switch is "<TT>yes</TT>" and an input image is specified,
  a new image wcs is derived from the linear component of the computed plate
  solution and written to the image header. The numerical components of
  the new image wcs are written to the standards FITS keywords, CRPIX, CRVAL,
  and CD, with the actual values depending on the pixel coordinate system
  <I>pixsystem</I> read from the database or set by the user. The FITS keywords
  which define the image celestial coordinate system CTYPE, RADECSYS, EQUINOX,
  and MJD-WCS are set by the <I>coosystem</I> and <I>projection</I> parameters.
  <P>
  The first four characters of the values of the ra / longitude and dec / latitude
  axis CTYPE keywords specify the celestial coordinate system. They are set to
  RA-- / DEC- for equatorial coordinate systems, ELON / ELAT for the ecliptic
  coordinate system, GLON / GLAT for the galactic coordinate system, and
  SLON / SLAT for the supergalactic coordinate system.
  <P>
  The second four characters of the values of the ra / longitude and dec /
  latitude axis CTYPE keywords specify the sky projection geometry.
  The second four characters of the values of the ra / longitude and dec /
  latitude axis CTYPE keywords specify the sky projection geometry. IRAF
  currently supports the TAN, SIN, ARC, AIT, CAR, CSC, GLS, MER, MOL, PAR, PCO,
  QSC, STG, TSC, and ZEA standard projections, in which case the second 4
  characters of CTYPE are set to  -TAN, -ARC, -SIN, etc.
  <P>
  If the input celestial coordinate system is equatorial, the value of the
  RADECSYS keyword specifies the fundamental equatorial system, EQUINOX
  specifies the epoch of the mean place, and MJD-WCS specifies the epoch
  for which the mean place is correct. The permitted values of
  RADECSYS are FK4, FK4-NO-E, FK5, ICRS, and GAPPT. EQUINOX is entered in years
  and interpreted as a Besselian epoch for the FK4 system, a Julian epoch
  for the FK5 and ICRS system. The epoch of the wcs MJD-WCS is entered as
  a modified Julian date. Only those keywords necessary to defined the
  new wcs are written. Any existing keywords which are not required to
  define the wcs or are redundant are removed, with the exception of
  DATE-OBS and EPOCH, which are left unchanged for obvious (DATE-OBS) and
  historical (use of EPOCH keyword at NOAO) reasons.
  <P>
  If <I>verbose</I> is "<TT>yes</TT>", various pieces of useful information are
  printed to the terminal as the task proceeds.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>References</H3>
  <! BeginSection: 'REFERENCES'>
  <UL>
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
  1. Compute the plate solution for an image with the ccmap task and then
  use the ccsetwcs task to create the image wcs. Check the results with the
  imheader and skyctran tasks.
  <P>
  <PRE>
  cl&gt; type coords
  13:29:47.297  47:13:37.52  327.50  410.38
  13:29:37.406  47:09:09.18  465.50   62.10
  13:29:38.700  47:13:36.23  442.01  409.65
  13:29:55.424  47:10:05.15  224.35  131.20
  13:30:01.816  47:12:58.79  134.37  356.33
  <P>
  <P>
  cl&gt; ccmap coords coords.db image=pix xcol=3 ycol=4 lngcol=1 latcol=2 \<BR>
  inter-
  Coords File: coords  Image: pix
      Database: coords.db  Record: pix
  Refsystem: j2000  Coordinates: equatorial FK5
      Equinox: J2000.000 Epoch: J2000.00000000 MJD: 51544.50000
  Insystem: j2000  Coordinates: equatorial FK5
      Equinox: J2000.000 Epoch: J2000.00000000 MJD: 51544.50000
  Coordinate mapping status
      Ra/Dec or Long/Lat fit rms: 0.229  0.241   (arcsec  arcsec)
  Coordinate mapping parameters
      Sky projection geometry: tan
      Reference point: 13:29:48.129  47:11:53.37  (hours  degrees)
      Reference point: 318.735  273.900  (pixels  pixels)
      X and Y scale: 0.764  0.767  (arcsec/pixel  arcsec/pixel)
      X and Y axis rotation: 179.110  358.958  (degrees  degrees)
  Wcs mapping status
      Ra/Dec or Long/Lat wcs rms: 0.229  0.241   (arcsec  arcsec)
  <P>
  cl&gt; type coords.db
  # Mon 15:10:37 13-May-96
  begin   coords
          xrefmean        318.7460000000001
          yrefmean        273.9320000000001
          lngmean         13.49670238888889
          latmean         47.19815944444444
          coosystem       j2000
          projection      tan
          lngref          13.49670238888889
          latref          47.19815944444444
          lngunits        hours
          latunits        degrees
          xpixref         318.7352667484295
          ypixref         273.9002619912411
          geometry        general
          function        polynomial
          xishift         247.3577084680361
          etashift        -206.1795977453246
          xmag            0.7641733802338992
          ymag            0.7666917500560622
          xrotation       179.1101291109185
          yrotation       358.9582148846163
          wcsxirms        0.2288984454992771
          wcsetarms       0.2411034140453112
          xirms           0.2288984454992771
          etarms          0.2411034140453112
          surface1        11
                          3.      3.
                          2.      2.
                          2.      2.
                          0.      0.
                          134.3700000000001       134.3700000000001
                          465.5000000000002       465.5000000000002
                          62.1    62.1
                          410.3800000000001       410.3800000000001
                          247.3577084680361       -206.1795977453246
                          -0.7640812161068504     -0.011868034832272
                          -0.01393966623835092    0.7665650170136847
          surface2        0
  <P>
  <P>
  <P>
  cl&gt; imheader pix l+
  DATE-OBS= '05/04/87'            /  DATE DD/MM/YY
  RA      = '13:29:24.00'         /  RIGHT ASCENSION
  DEC     = '47:15:34.00'         /  DECLINATION
  EPOCH   =              1987.26  /  EPOCH OF RA AND DEC
  <P>
  <P>
  cl&gt; ccsetwcs pix coords.db pix 
  Image: pix  Database: coords.db  Record: pix
  Coordinate mapping parameters
      Sky projection geometry: tan
      Reference point: 13:29:48.129  47:11:53.37  (hours   degrees)
      Ra/Dec logical image axes: 1  2
      Reference point: 318.735  273.900  (pixels  pixels)
      X and Y scale: 0.764  0.767  (arcsec/pixel  arcsec/pixel)
      X and Y coordinate rotation: 179.110  358.958  (degrees  degrees)
  Updating image header wcs
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
  CRVAL1  =     202.450535833334
  CRVAL2  =     47.1981594444445
  CRPIX1  =     318.735266748429
  CRPIX2  =     273.900261991241
  CD1_1   =  -2.1224478225190E-4
  CD1_2   =  -3.8721295106530E-6
  CD2_1   =  -3.2966763422978E-6
  CD2_2   =  2.12934726948246E-4
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
  </PRE>
  <P>
  The skyctran task is used to test that the input image wcs is indeed correct.
  Columns 1 and 2 contain the original ra and dec values and columns 3 and 4
  contain the transformed values. The second imheader listing shows what the
  image wcs looks like.
  <P>
  <P>
  2. Repeat the previous example but enter the plate solution parameters by
  hand.
  <P>
  <PRE>
  cl&gt; ccsetwcs pix "" xref=318.735 yref=273.900 lngref=13:29:48.129 \<BR>
  latref=47:11:53.37 xmag=.764 ymag=.767 xrot=180.890 yrot=1.042
  Image: pix
  Coordinate mapping parameters
      Sky projection geometry: tan
      Reference point: 13:29:48.129  47:11:53.37  (hours   degrees)
      Ra/Dec logical image axes: 1  2
      Reference point: 318.735  273.900  (pixels  pixels)
      X and Y scale: 0.764  0.767  (arcsec/pixel  arcsec/pixel)
      X and Y coordinate rotation: 180.890  1.042  (degrees  degrees)
  Updating image header wcs
  <P>
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
  13:29:47.297  47:13:37.52 13:29:47.285 47:13:37.93
  13:29:37.406  47:09:09.18 13:29:37.428 47:09:09.17
  13:29:38.700  47:13:36.23 13:29:38.698 47:13:35.99
  13:29:55.424  47:10:05.15 13:29:55.395 47:10:05.04
  13:30:01.816  47:12:58.79 13:30:01.839 47:12:58.72
  </PRE>
  <P>
  Note that there are minor differences between the results of examples 1
  and 2 due to precision differences in the input. Note also the difference
  in the way the xrotation and yrotation angles are defined between examples
  1 and 2. In example 2 the rotations are defined as coordinate rotations,
  whereas in example one they are described as axis rotations.
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
  ccmap, cctran, skyctran, imctran
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'REFERENCES' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
