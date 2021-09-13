ccfind — Find catalog sources in an image
=========================================

**Package: imcoords**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>ccfind (Jun99)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>images.imcoords</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>ccfind (Jun99)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>ccfind</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  ccfind -- locate objects in an image given a celestial coordinate list and
  the image wcs
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  ccfind input output image
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The list of input celestial coordinate files. Coordinates may be entered
  by hand by setting input to "<TT>STDIN</TT>". A STDIN coordinate list is terminated
  by typing &lt;EOF&gt; (usually &lt;ctrl/d&gt; or &lt;ctrl/z&gt;).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>The list of output matched coordinate files. The computed pixel values
  are appended to the input coordinate file line and written to output. The number
  of output files must equal the number of input files. Results may be
  printed on the terminal by setting output to "<TT>STDOUT</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_image">image</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD>The list of input images associated with the input coordinate files. The number
  of input images must equal the number of input coordinate files.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_lngcolumn">lngcolumn = 1, latcolumn = 2</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lngcolumn' Line='lngcolumn = 1, latcolumn = 2'>
  <DD>The input coordinate file columns containing the celestial ra / longitude and
  dec / latitude coordinates respectively.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_lngunits">lngunits = "<TT></TT>", latunits = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lngunits' Line='lngunits = "", latunits = ""'>
  <DD>The units of the input ra / longitude and dec / latitude coordinates. The
  options are "<TT>hours</TT>", "<TT>degreees</TT>", and "<TT>radians</TT>" for ra / longitude and
  "<TT>degrees</TT>" and "<TT>radians</TT>" for dec / latitude. If lngunits and latunits are
  undefined they default to the preferred units for the coordinates
  system specified by <I>insystem</I>, e.g. "<TT>hours</TT>" and "<TT>degrees</TT>" for
  equatorial systems and "<TT>degrees</TT>" and "<TT>degrees</TT>" for ecliptic, galactic, and
  supergalactic systems.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_insystem">insystem = "<TT>j2000</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='insystem' Line='insystem = "j2000"'>
  <DD>The input celestial coordinate system. The <I>insystem</I> parameter
  sets the preferred units for the input celestial coordinates, and
  tells CCFIND how to transform the input celestial coordinates 
  the input image celestial coordinate system. The systems of most
  interest to users are "<TT>icrs</TT>", "<TT>j2000</TT>", and "<TT>b1950</TT>".  The full set
  of options are the following:
  <P>
  <DL>
  <DT><B><A NAME="l_equinox">equinox [epoch]</A></B></DT>
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
  <DT><B><A NAME="l_icrs">icrs [equinox] [epoch]</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='icrs' Line='icrs [equinox] [epoch]'>
  <DD>The International Celestial Reference System (ICRS) where equinox is
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
  <DT><B><A NAME="l_fk5">fk5 [equinox] [epoch]</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='fk5' Line='fk5 [equinox] [epoch]'>
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
  <DT><B><A NAME="l_fk4">fk4 [equinox] [epoch]</A></B></DT>
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
  <DT><B><A NAME="l_noefk4">noefk4 [equinox] [epoch]</A></B></DT>
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
  <DT><B><A NAME="l_apparent">apparent epoch</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='apparent' Line='apparent epoch'>
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
  <DT><B><A NAME="l_ecliptic">ecliptic epoch</A></B></DT>
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
  <DT><B><A NAME="l_galactic">galactic [epoch]</A></B></DT>
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
  <DT><B><A NAME="l_supergalactic">supergalactic [epoch]</A></B></DT>
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
  Since CCFIND does not currently support proper motions these fields are
  not required.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_usewcs">usewcs = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='usewcs' Line='usewcs = no'>
  <DD>Use image header information to compute the input image celestial coordinate
  system ? If usewcs is "<TT>yes</TT>", the image coordinate system is read from the
  image header.  If usewcs is "<TT>no</TT>", the input image celestial coordinates
  system is defined by <I>xref</I>, <I>yref</I>, <I>xmag</I>, <I>ymag</I>,
  <I>xrotation</I>, <I>yrotation</I>, <I>lngref</I>, <I>latref</I>, 
  <I>lngrefunits</I>, <I>latrefunits</I>, <I>refsystem</I>, and <I>projection</I>
  parameters respectively.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xref">xref = INDEF, yref = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xref' Line='xref = INDEF, yref = INDEF'>
  <DD>The x and y pixel coordinates of the reference point.
  xref and yref default to the center of the image in pixel coordinates.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xmag">xmag = INDEF, ymag = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xmag' Line='xmag = INDEF, ymag = INDEF'>
  <DD>The x and y scale factors in arcseconds per pixel.  xmag and ymag default
  to 1.0 and 1.0 arcseconds per pixel.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xrotation">xrotation = INDEF, yrotation = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xrotation' Line='xrotation = INDEF, yrotation = INDEF'>
  <DD>The x and y rotation angles in degrees. xrotation and yrotation are
  interpreted as the rotation of the ra / longitude and dec / latitude
  coordinates with respect to the x and y axes, and default 0.0 and 0.0 degrees
  respectively. To set east to the up, down, left, and right directions,
  set xrotation to 90, 270, 180, and 0 respectively. To set north to the
  up, down, left, and right directions, set yrotation to  0, 180, 90, and 270
  degrees respectively. Any global rotation must be added to both the
  xrotation and yrotation values.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_lngref">lngref = "<TT>INDEF</TT>", latref = "<TT>INDEF</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lngref' Line='lngref = "INDEF", latref = "INDEF"'>
  <DD>The ra / longitude and dec / latitude of the reference point. Lngref and latref
  may be numbers, e.g 13:20:42.3 and -33:41:26, or keywords for the
  appropriate parameters in the image header, e.g. RA and DEC for NOAO
  image data. If lngref and latref are undefined they default to 0.0 and 0.0
  respectively.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_lngrefunits">lngrefunits = "<TT></TT>", latrefunits = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lngrefunits' Line='lngrefunits = "", latrefunits = ""'>
  <DD>The units of the reference point celestial  coordinates. The options
  are "<TT>hours</TT>", "<TT>degrees</TT>", and "<TT>radians</TT>" for the ra / longitude coordinates,
  and "<TT>degrees</TT>" and "<TT>radians</TT>" for the dec /latitude coordinates.
  If lngrefunits and latrefunits are undefined they default to the preferred
  units of the reference system.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_refsystem">refsystem = "<TT>INDEF</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='refsystem' Line='refsystem = "INDEF"'>
  <DD>The celestial coordinate system of the reference point. Refsystem may
  be any one of the options listed under the <I>insystem</I> parameter, e.g.
  "<TT>b1950</TT>", or an image header keyword containing the epoch of the observation
  in years, e.g. EPOCH for NOAO data.  If refsystem is undefined
  the celestial coordinate system of the reference point defaults to the
  celestial coordinate system of the input coordinates <I>insystem</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_projection">projection = "<TT>tan</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='projection' Line='projection = "tan"'>
  <DD>The sky projection geometry. The most commonly used projections in
  astronomy are "<TT>tan</TT>", "<TT>arc</TT>", "<TT>sin</TT>", and "<TT>lin</TT>". Other supported projections
  are "<TT>ait</TT>", "<TT>car</TT>", "<TT>csc</TT>", "<TT>gls</TT>", "<TT>mer</TT>", "<TT>mol</TT>", "<TT>par</TT>", "<TT>pco</TT>", "<TT>qsc</TT>", "<TT>stg</TT>",
  "<TT>tsc</TT>", and "<TT>zea</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_center">center = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='center' Line='center = yes'>
  <DD>Center the object pixel coordinates using an x and y marginal centroiding
  algorithm ?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_sbox">sbox = 21</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sbox' Line='sbox = 21'>
  <DD>The search box width in pixels. Sbox defines the region of the input image
  searched and used to compute the initial x and y marginal centroids. Users
  worried about contamination can set sbox = cbox, so that the first
  centering iteration will be the same as the others.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_cbox">cbox = 9</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cbox' Line='cbox = 9'>
  <DD>The centering box width in pixels. Cbox defines the region of the input
  image used to compute the final x and y marginal centroids.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_datamin">datamin = INDEF, datamax = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='datamin' Line='datamin = INDEF, datamax = INDEF'>
  <DD>The minimum and maximum good data values. Values outside this range
  are exclude from the x and y marginal centroid computation.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_background">background = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='background' Line='background = INDEF'>
  <DD>The background value used by the centroiding algorithm. If background is
  INDEF, a value equal to the mean value of the good data pixels for
  each object is used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_maxiter">maxiter = 5</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maxiter' Line='maxiter = 5'>
  <DD>The maximum number of centroiding iterations to perform. The centroiding
  algorithm will halt when this limit is reached or when the desired tolerance
  is reached.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_tolerance">tolerance = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='tolerance' Line='tolerance = 0'>
  <DD>The convergence tolerance of the centroiding algorithm. Tolerance is
  defined as the maximum permitted integer shift of the centering box in
  pixels from one iteration to the next.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose'>
  <DD>Print messages about actions taken by the task?
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  CCFIND locates the objects in the input celestial coordinate lists <I>input</I>
  in the input images <I>image</I> using the image world coordinate system,
  and writes the located objects to the output matched coordinates files
  <I>output</I>. CCFIND computes the pixel coordinates of each object by,
  1) transforming the input celestial coordinates to image celestial coordinate
  system, 2) using the image celestial coordinate system to compute the
  initial pixel coordinates, and 3) computing the final pixel coordinates
  using a centroiding algorithm. The image celestial coordinate system may
  be read from the image header or supplied by the user. The CCFIND output
  files are suitable for input to the plate solution computation task CCMAP.
  <P>
  The input ra / longitude and dec / latitude coordinates are read from
  columns <I>lngcolumn</I> and <I>latcolumn</I> in the input coordinate
  file respectively.
  <P>
  The input celestial coordinate system is set by the <I>insystem</I> parameter,
  and must be one of the following: equatorial, ecliptic, galactic, or
  supergalactic.  The equatorial coordinate systems must be one of: 1) FK4,
  the mean place pre-IAU 1976 system, 2) FK4-NO-E, the same as FK4 but without
  the E-terms, 3) FK5, the mean place post-IAU 1976 system, 4) ICRS the
  International Celestial Reference System, 5) GAPPT, the geocentric apparent
  place in the post-IAU 1976 system.
  <P>
  The <I>lngunits</I> and <I>latunits</I> parameters set the units of the input
  celestial coordinates. If undefined, lngunits and latunits assume sensible
  defaults for the input celestial coordinate system set by the <I>insystem</I>
  parameter, e.g. "<TT>hours</TT>" and "<TT>degrees</TT>" for equatorial coordinates and "<TT>degrees</TT>"
  and "<TT>degrees</TT>" for galactic coordinates.
  <P>
  If the <I>usewcs</I> parameter is "<TT>yes</TT>", the image celestial coordinate
  system is read from the image header keywords CRPIX, CRVAL, CD or CDELT/CROTA,
  RADECSYS, EQUINOX or EPOCH, and MJD-OBS or DATE-OBS, where the mathematical
  part of this transformation is shown below.
  <P>
  <PRE>
          xi = a + b * x + c * y
         eta = d + e * x + f * y
           b = CD1_1
           c = CD1_2
           e = CD2_1
           f = CD2_2
           a = - b * CRPIX1 - c * CRPIX2
           d = - e * CRPIX1 - f * CRPIX2 
         lng = CRVAL1 + PROJ (xi, eta)
         lat = CRVAL2 + PROJ (xi, eta)
  </PRE>
  <P>
  If usewcs is "<TT>no</TT>", then the image celestial coordinate system is computed
  using the values of the <I>xref</I>, <I>yref</I>, <I>xmag</I>, <I>ymag</I>,
  <I>xrotation</I>, <I>yrotation</I>, <I>lngref</I>, <I>latref</I>,
  <I>lngrefunits</I>, <I>latrefunits</I>, <I>refsystem</I>, and <I>projection</I>
  supplied by the user, where the mathematical part of this transformation is
  shown below.
  <P>
  <PRE>
          xi = a + b * x + c * y
         eta = d + e * x + f * y
           b = xmag * cos (xrotation)
           c = -ymag * sin (yrotation)
           e = xmag * sin (xrotation)
           f = ymag * cos (yrotation)
           a = - b * xref - c * yref 
           d = - e * xref - f * yref
         lng = lngref + PROJ (xi, eta)
         lat = latref + PROJ (xi, eta)
  </PRE>
  <P>
  In both the above examples, x and y are the pixel coordinates, xi and eta
  are the usual projected (standard) coordinates, lng and lat are the celestial
  coordinates, and PROJ stands for the projection function,  usually
  the tangent plane projection function.
  <P>
  Once the image celestial coordinate system is determined, CCFIND transforms
  the input celestial coordinates to the image celestial coordinate system
  using the value of the <I>insystem</I> parameter, and either the values of
  the image header keywords RADECSYS, EQUINOX / EPOCH, and MJD-OBS / DATE-OBS
  (if <I>usewcs</I> = "<TT>yes</TT>"), or the value of the <I>refsystem</I> parameter (if
  <I>usewcs</I> = "<TT>no</TT>"), and then transforms the image celestial coordinates
  to pixel coordinates using the inverse of the transformation functions
  shown above.
  <P>
  If <I>center</I> is yes, CCFIND locates the objects in the input
  image using an  xn and y marginal centroiding algorithm. Pixels
  inside a box <I>sbox</I> pixels wide centered in the initial coordinates,
  are used to locate the objects in the image. Accurate final centering
  is done using pixels inside a region <I>cbox</I> pixels wide centered on
  these initial coordinates. Sbox should be set to a value large enough
  to locate the object, but small enough to exclude other bright sources.
  Cbox should be set to a value small enough to exclude sky values and other
  bright sources, but large enough to include the wings of point sources.
  Bad data can be excluded from the centroiding algorithm by setting
  the <I>datamin</I> and <I>datamax</I> parameters. If <I>background</I> is
  undefined then the centroiding algorithm sets the background value to
  the mean of the good data values inside the centering box.
  The centroiding algorithm iterates until the maximum number of
  iterations <I>maxiter</I> limit is reached, or until the tolerance
  criteria <I>tolerance</I> is achieved.
  <P>
  Only objects whose coordinates are successfully located in the 
  input image are written to the output coordinate file. The computed
  output pixel coordinates are appended to the input image line using
  the format parameters <I>xformat</I> and <I>yformat</I> parameters,
  whose default values are "<TT>%10.3f</TT>" and "<TT>%10.3f</TT>" respectively
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
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
     
     
  Conventions for w (field width) specification:
     
      W =  n      right justify in field of N characters, blank fill
          -n      left justify in field of N characters, blank fill
          0n      zero fill at left (only if right justified)
  absent, 0       use as much space as needed (D field sets precision)
  <P>
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
  cctran.hlp-(67%)-line 268-file 1 of 1
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
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Locate the object in the list wpix.coords in the image wpix using
  the existing image header wcs. The input celestial coordinates file
  contains j2000 GSC catalog coordinates of 5 objects in the field.
  The image wcs is in b1950.
  <P>
  <PRE>
  cl&gt; imcopy dev$wpix wpix
      ... copy the test image into the current directory
  <P>
  cl&gt; hedit wpix equinox 1950.0 add+
      ... change the epoch keyword value to the correct number
  <P>
  cl&gt; type wpix.coords
  13:29:47.297  47:13:37.52
  13:29:37.406  47:09:09.18
  13:29:38.700  47:13:36.23
  13:29:55.424  47:10:05.15
  13:30:01.816  47:12:58.79
  <P>
  cl&gt; ccfind wpix.coords wpix.match wpix usewcs+
  <P>
  Input File: wpix.coords  Output File: wpix.match
      Image: wpix  Wcs: 
  Insystem: j2000  Coordinates: equatorial FK5
      Equinox: J2000.000 Epoch: J2000.00000000 MJD: 51544.50000
  Refsystem: wpix.imh logical  Projection: TAN  Ra/Dec axes: 1/2
      Coordinates: equatorial FK4 Equinox: B1950.000
      Epoch: B1987.25767884 MJD: 46890.00000
  Located 5 objects in image wpix
  <P>
  cl&gt; type wpix.match
  # Input File: wpix.coords  Output File: wpix.match
  #     Image: wpix  Wcs: 
  # Insystem: j2000  Coordinates: equatorial FK5
  #     Equinox: J2000.000 Epoch: J2000.00000000 MJD: 51544.50000
  # Refsystem: wpix.imh logical  Projection: TAN  Ra/Dec axes: 1/2
  #     Coordinates: equatorial FK4 Equinox: B1950.000
  #     Epoch: B1987.25767884 MJD: 46890.00000
  <P>
  13:29:47.297  47:13:37.52     327.504    410.379
  13:29:37.406  47:09:09.18     465.503     62.101
  13:29:38.700  47:13:36.23     442.013    409.654
  13:29:55.424  47:10:05.15     224.351    131.200
  13:30:01.816  47:12:58.79     134.373    356.327
  <P>
  cl&gt; ccmap wpix.match ccmap.db xcol=3 ycol=4 lngcol=1 latcol=2 ...
  </PRE>
  <P>
  2. Repeat the previous example but input the image coordinate system by hand.
  The scale is known to be ~0.77 arcseconds per pixel, north is up, east is left,
  and the center of the image is near ra = 13:27:47, dec = 47:27:14 in 1950
  coordinates.
  <P>
  <PRE>
  cl&gt; ccfind wpix.coords wpix.match wpix xmag=-0.77 ymag=.77 lngref=13:27:47 \<BR>
  latref=47:27:14 refsystem=b1950.
  <P>
  Input File: wpix.coords  Output File: wpix.match.1
      Image: wpix  Wcs: 
  Insystem: j2000  Coordinates: equatorial FK5
      Equinox: J2000.000 Epoch: J2000.00000000 MJD: 51544.50000
  Refsystem: b1950  Coordinates: equatorial FK4
      Equinox: B1950.000 Epoch: B1950.00000000 MJD: 33281.92346
  Located 5 objects in image wpix
  <P>
  <P>
  cl&gt; type wpix.match 
  <P>
  # Input File: wpix.coords  Output File: wpix.match
  #     Image: wpix  Wcs: 
  # Insystem: j2000  Coordinates: equatorial FK5
  #     Equinox: J2000.000 Epoch: J2000.00000000 MJD: 51544.50000
  # Refsystem: b1950  Coordinates: equatorial FK4
  #     Equinox: B1950.000 Epoch: B1950.00000000 MJD: 33281.92346
  <P>
  13:29:47.297  47:13:37.52     327.504    410.379
  13:29:37.406  47:09:09.18     465.503     62.101
  13:29:38.700  47:13:36.23     442.013    409.654
  13:29:55.424  47:10:05.15     224.351    131.200
  13:30:01.816  47:12:58.79     134.373    356.327
  </PRE>
  <P>
  3. Repeat the previous example but read the ra, dec, and epoch from the
  image header keywords RA, DEC, and EPOCH. It turns out the telescope
  RA and DEC recorded in the image header are not very accurate and that
  EPOCH is 0.0 instead of 1987.26 so we will fix up the header before
  trying out the example.
  <P>
  <PRE>
  cl&gt; hedit wpix EPOCH 1987.26
  cl&gt; hedit wpix RA '13:29:21'
  cl&gt; hedit wpix DEC '47:15:42'
  <P>
  cl&gt; ccfind wpix.coords wpix.match wpix xmag=-0.77 ymag=.77 lngref=RA \<BR>
  latref=DEC refsystem=EPOCH
  <P>
  Input File: wpix.coords  Output File: wpix.match
      Image: wpix  Wcs: 
  Insystem: j2000  Coordinates: equatorial FK5
      Equinox: J2000.000 Epoch: J2000.00000000 MJD: 51544.50000
  Refsystem: 1987.26  Coordinates: equatorial FK5
      Equinox: J1987.260 Epoch: J1987.26000000 MJD: 46891.21500
  Located 5 objects in image wpix
  <P>
  # Input File: wpix.coords  Output File: wpix.match
  #     Image: wpix  Wcs: 
  # Insystem: j2000  Coordinates: equatorial FK5
  #     Equinox: J2000.000 Epoch: J2000.00000000 MJD: 51544.50000
  # Refsystem: 1987.26  Coordinates: equatorial FK5
  #     Equinox: J1987.260 Epoch: J1987.26000000 MJD: 46891.21500
  <P>
  13:29:47.297  47:13:37.52     327.504    410.379
  13:29:37.406  47:09:09.18     465.503     62.101
  13:29:38.700  47:13:36.23     442.013    409.654
  13:29:55.424  47:10:05.15     224.351    131.200
  13:30:01.816  47:12:58.79     134.373    356.327
  </PRE>
  <P>
  4. Use ccfind to predict the pixel coordinate in the last example by
  turning off the object centering, and mark the predicted coordinates
  on the image display with red dots.
  <P>
  <PRE>
  cl&gt; ccfind wpix.coords wpix.match wpix xmag=-0.77 ymag=.77 lngref=RA \<BR>
  latref=DEC refsystem=EPOCH center-
  <P>
  Input File: wpix.coords  Output File: wpix.match
      Image: wpix  Wcs: 
  Insystem: j2000  Coordinates: equatorial FK5
      Equinox: J2000.000 Epoch: J2000.00000000 MJD: 51544.50000
  Refsystem: 1987.26  Coordinates: equatorial FK5
      Equinox: J1987.260 Epoch: J1987.26000000 MJD: 46891.21500
  Located 5 objects in image wpix
  <P>
  cl&gt; type wpix.match
  <P>
  # Input File: wpix.coords  Output File: wpix.match
  #     Image: wpix  Wcs: 
  # Insystem: j2000  Coordinates: equatorial FK5
  #     Equinox: J2000.000 Epoch: J2000.00000000 MJD: 51544.50000
  # Refsystem: 1987.26  Coordinates: equatorial FK5
  #     Equinox: J1987.260 Epoch: J1987.26000000 MJD: 46891.21500
  <P>
  13:29:47.297  47:13:37.52     333.954    401.502
  13:29:37.406  47:09:09.18     465.338     53.175
  13:29:38.700  47:13:36.23     447.687    399.967
  13:29:55.424  47:10:05.15     226.600    125.612
  13:30:01.816  47:12:58.79     141.892    351.084
  <P>
  cl&gt; display wpix 1
  <P>
  cl&gt; fields wpix.match 3,4 | tvmark 1 STDIN col=204
  <P>
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
  starfind, ccxymatch, ccmap, ccsetwcs, cctran
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'FORMATS' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>