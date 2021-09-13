rvcorrect — Compute radial velocity corrections
===============================================

**Package: astutil**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>rvcorrect (Nov90)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>astutil</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>rvcorrect (Nov90)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>rvcorrect</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  rvcorrect -- Compute radial velocity corrections
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  rvcorrect
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_files">files = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='files' Line='files = ""'>
  <DD>List of files containing date, time, coordinates of observation, and possibly
  an observed radial velocity.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_images">images = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images = ""'>
  <DD>List of images containing date, time, coordinates of observation, and possibly
  an observed radial velocity.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_header">header = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='header' Line='header = yes'>
  <DD>Print header for output?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_input">input = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input = no'>
  <DD>Print input data in output?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_imupdate">imupdate = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='imupdate' Line='imupdate = no'>
  <DD>Update the image header with the computed values of heliocentric correction
  (in the <I>VHELIO</I> keyword), Heliocentric Julian Date (in the <I>HJD</I>
  keyword), Local Standard of Rest velocity (in the <I>VLSR</I> keyword), and
  information describing the solar motion with respect to the desired standard
  of rest (in the <I>VSUN</I> keyword).
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B><A NAME="l_epoch">epoch = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='epoch' Line='epoch = INDEF'>
  <DD>Epoch of observation coordinates in Julian years. If zero or INDEF then the
  epoch is assumed to be the same as the date of observation.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_observatory">observatory = "<TT>)_.observatory</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='observatory' Line='observatory = ")_.observatory"'>
  <DD>Observatory for  which corrections are to be computed.  The default is a
  redirection to look in the parameters for the parent package for a value.
  This may be one of the observatories in the observatory database,
  "<TT>observatory</TT>" to select the observatory defined by the environment variable
  "<TT>observatory</TT>" or the parameter <B>observatory.observatory</B>, or "<TT>obspars</TT>"
  to select the current parameters set in the <B>observatory</B> task.  See
  help for <B>observatory</B> for additional information.  If the input
  consists of images then the observatory is defined by the OBSERVAT keyword
  if present.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_vsun">vsun = 20.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='vsun' Line='vsun = 20.'>
  <DD>Velocity in km/s of the sun relative to the desired standard of rest.  The
  default is for the Local Standard of Rest (LSR).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ra_vsun">ra_vsun = 18:00:00</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ra_vsun' Line='ra_vsun = 18:00:00'>
  <DD>Right ascension in hours of the solar motion relative to the desired standard
  of rest.  The default is for the Local Standard of Rest (LSR).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_dec_vsun">dec_vsun = 30:00:00</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dec_vsun' Line='dec_vsun = 30:00:00'>
  <DD>Declination in degrees of the solar motion relative to the desired standard
  of rest.  The default is for the Local Standard of Rest (LSR).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_epoch_vsun">epoch_vsun = 1900.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='epoch_vsun' Line='epoch_vsun = 1900.'>
  <DD>Epoch in years for the solar motion components.
  </DD>
  </DL>
  <P>
  If no input files or images are specified then the following parameters
  are used for input.
  <DL>
  <DT><B><A NAME="l_year">year, month, day, ut</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='year' Line='year, month, day, ut'>
  <DD>Date and time of observation.  If the year is less than 100 then the century is
  assumed to be 1900.  The month is specified as an integer between 1 and 12.
  The date of observation is the Greenwich date; i.e. the new day begins at
  0 hours universal time.  Universal time of observation in hours.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ra">ra , dec </A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ra' Line='ra , dec '>
  <DD>Right ascension (hours) and declination (degrees) of observation.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_vobs">vobs = 0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='vobs' Line='vobs = 0.'>
  <DD>Observed velocity (km/s) to be corrected.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_keywpars">keywpars = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='keywpars' Line='keywpars = ""'>
  <DD>The image header keyword translation table as described in
  the <I>keywpars</I> named pset.
  </DD>
  </DL>
  <P>
  If no input files or images are specified the following parameters are
  set by the task.
  <DL>
  <DT><B><A NAME="l_hjd">hjd</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='hjd' Line='hjd'>
  <DD>Heliocentric Julian date.  The date of observation is corrected for
  light travel difference to the sun.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_vhelio">vhelio</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='vhelio' Line='vhelio'>
  <DD>Heliocentric radial velocity in km/s.  The observed velocity is corrected
  for the rotation of the Earth, the motion of the Earth about the Earth-Moon
  barycenter, and the orbit of the barycenter about the Sun.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_vlsr">vlsr</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='vlsr' Line='vlsr'>
  <DD>Local standard of rest radial velocity in km/s.
  The heliocentric radial velocity is corrected for the motion of the Sun
  relative to the specified standard of rest.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The observed radial velocity is corrected for the motion of the
  observer in the direction of the observation.  The components of the
  observer's motion corrected are those due to the Earth's rotation
  (diurnal velocity), the motion of the Earth's center about the
  Earth-Moon barycenter (lunar velocity), the motion of the Earth-Moon
  barycenter about the center of the Sun (annual velocity), and the
  motion of the Sun (solar velocity) relative to some specified standard
  of rest.
  <P>
  The input parameters consist of the date and time of the observation, the
  direction of observation, the location of the observation, the direction
  and magnitude of the solar motion relative to some standard of rest, and
  the observed radial velocity.  In all cases years between 0 and 99 are
  treated as 20th century years.  The observatory for the observations
  defaults to that specified by the environment variable "<TT>observatory</TT>" if
  defined or that set for the task <B>observatory</B>.  If the input consists
  of images the observatory is defined by the OBSERVAT image header parameter
  if present.  See <B>ovservatory</B> for additional information.  The solar
  motion defaults to that relative to the galactic local standard of rest
  (LSR).  Note that one can make the local standard of rest velocity be
  equivalent to the heliocentric velocity by setting the velocity of the
  solar motion to zero.
  <P>
  The observed velocity, date, time, and direction of observation may be
  specified in three ways; from files, images, or the task parameters.  If a
  list of files is given then the files are read for the observation
  parameters.  The format of the files is lines containing the year, month
  (as an integer), day, universal time, right ascension, declination,
  (optional) coordinate epoch, and (optional) observed radial velocity.  If
  no file list is specified but a list of images is given then the
  observation parameters are determined from the image header parameters
  specified through the keywpars parameters.  If the observation date
  includes the time then it is used in preference to universal time keyword.
  Finally, if no list of files or images is given then the task parameters
  are used.  If no observed radial velocity is given in the file list or
  found in the image header then a value of zero is assumed.  In this case
  the corrected velocities are interpreted as the corrections to be added to
  a measured velocity to correct to the desired standard of rest.
  <P>
  The results of the radial velocity calculations are output in three
  ways.  The velocities are always printed on the standard output with an
  optional header.  If the observation parameters are set with the task
  parameters (no file or image list) then the results are also stored in
  the parameter file.  This mechanism allows the task to be used easily
  in a script and to obtain greater precision.  If the observation
  parameters are taken from the image headers and the <I>imupdate</I>
  parameter is set, then the heliocentric
  Julian day is recorded as HJD, the heliocentric velocity as VHELIO,
  the LSR velocity as VLSR, and the velocity, ra and dec, and epoch
  of the solar motion used in VLSR is recorded as VSUN.
  <P>
  The printed output may include the input data if desired.  This produces two
  lines per observation, one for the input data and one for the output
  velocities.  The calculated data consists of the heliocentric Julian
  date, the observed velocity, the observed heliocentric velocity, and
  the observed local standard of rest velocity.  Following this are
  component corrections for the diurnal, lunar, annual, and solar
  velocities.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_diurnal_velocity">DIURNAL VELOCITY</A></H2>
  <! BeginSection: 'DIURNAL VELOCITY'>
  <UL>
  The geodetic latitude to geocentric latitude correction is given by
  <P>
  <PRE>
  	dlat = -(11. * 60. + 32.743000) * sin (2*lat) +
  		1.163300 * sin (4*lat) - 0.002600 * sin (6*lat)
  </PRE>
  <P>
  where lat is the geodetic latitude and dlat is the additive correction.
  The distance, r, of the observer from the Earth's center in meters is given by
  <P>
  <PRE>
  	r = 6378160.0 * (0.998327073 + 0.00167643800 * cos(2*lat) -
  	    0.00000351 * cos(4*lat) + 0.000000008 * cos(6*lat)) +
  	    altitude
  </PRE>
  <P>
  where lat is the corrected latitude and altitude is the altitude above
  sea level.  The rotational velocity (perpendicular to the radius vector)
  in km/s is given by
  <P>
  	v = TWOPI * (r / 1000.)  / (23.934469591229 * 3600.)
  <P>
  where 23.934469591229 is the sidereal day in hours for 1986 and TWOPI is the
  ratio of the circumference to the radius of a circle.  The projection of
  this velocity along the line of sight is
  <P>
  	vdiurnal = v * cos (lat) * cos (dec) * sin (ra-lmst)
  <P>
  where lmst is the local mean sidereal time.
  </UL>
  <! EndSection:   'DIURNAL VELOCITY'>
  <H2><A NAME="s_barycentric_velocity">BARYCENTRIC VELOCITY</A></H2>
  <! BeginSection: 'BARYCENTRIC VELOCITY'>
  <UL>
  The orbital elements of the lunar orbit are computed from the following
  interpolation formulas
  <P>
  <PRE>
  	t = (JD - 2415020) / 36525.
  <P>
  	oblq = 23.452294-t*(0.0130125+t*(0.00000164-t*0.000000503))
  	omega = 259.183275-t*(1934.142008+t*(0.002078+t*0.000002))
  	mlong = 270.434164+t*(481267.88315+t*(-0.001133+t*0.0000019))-
  	    omega
  	lperi = 334.329556+t*(4069.034029-t*(0.010325+t*0.000012))-
  	    omega
  	em = 0.054900489
  	inclin = 5.1453964
  </PRE>
  <P>
  where t is the time from the Julian day 2415020 (~J1900) in Julian centuries,
  oblq is the mean obliquity of the ecliptic, omega is the longitude of the mean
  ascending node, mlong is the mean lunar longitude, lperi is the mean lunar
  longitude of perigee, em is the eccentricity of the lunar orbit, and inclin
  is the inclination of the orbit to the ecliptic.  The true lunar longitude,
  tlong, is computed from the mean longitude using the correction for the mean
  anomaly to the true anomaly (radians)
  <P>
  <PRE>
  	manom = mlong - lperi
  	tanom = manom + (2 * em - 0.25 * em**3) * sin (manom) +
  	    1.25 * em**2 * sin (2 * manom) + 13/12 * em**3 *
  	    sin (3 * manom)
  	tlong = tanom + lperi
  </PRE>
  <P>
  The velocity of the Moon around the Earth's center in the plane of the orbit
  in km/s is
  <P>
  <PRE>
  	vmoon = (TWOPI * 384403.12040) / (27.321661 * 86400) /
  	    sqrt (1. - em**2)
  </PRE>
  <P>
  where 384403.12040 is the mean lunar distance (km) and 27.321661 is the mean
  lunar month (days).  The component along the line to the observation is
  <P>
  	v = vmoon * cos (bm) * (sin (tlong-lm) - em*sin (lperi-lm))
  <P>
  where lm and bm are the longitude and latitude of the observation
  along the lunar orbital plane relative to the ascending node using a standard
  coordinate transformation.  The barycentric velocity is that reduced by
  the ratio of the Earth's mass to the Moon's mass.
  <P>
  	vlunar = v / 81.53
  </UL>
  <! EndSection:   'BARYCENTRIC VELOCITY'>
  <H2><A NAME="s_annual_velocity">ANNUAL VELOCITY</A></H2>
  <! BeginSection: 'ANNUAL VELOCITY'>
  <UL>
  The orbital elements of the Earth's orbit are computed from the following
  interpolation formulas
  <P>
  <PRE>
  	t = (ast_julday (epoch) - 2415020) / 36525.
  <P>
  	manom = 358.47583+t*(35999.04975-t*(0.000150+t*0.000003))
  	oblq = 23.452294-t*(0.0130125+t*(0.00000164-t*0.000000503))
  	lperi = 101.22083+t*(1.7191733+t*(0.000453+t*0.000003))
  	eccen = 0.01675104-t*(0.00004180+t*0.000000126)
  </PRE>
  <P>
  where t is the time from the Julian day 2415020 (~J1900) in Julian centuries,
  manom is the mean anomaly (degrees), oblq is the mean obliquity of the ecliptic
  (degrees), lperi is the mean longitude of perihelion (degrees), and
  eccen is the eccentricity of the orbit.  The true anomaly (radians) is 
  obtained from the mean anomaly (radians) by
  <P>
  <PRE>
  	tanom = manom + (2 * eccen - 0.25 * eccen**3) * sin (manom) +
  	    1.25 * eccen**2 * sin (2 * manom) +
  	    13./12. * eccen**3 * sin (3 * manom)
  </PRE>
  <P>
  The orbital velocity of the Earth-Moon barycenter perpendicular to
  the radius vector is given by
  <P>
  <PRE>
  	v = ((TWOPI * 149598500.) / (365.2564 * 86400.)) /
  	    sqrt (1. - eccen**2)
  </PRE>
  <P>
  where the semi-major axis is 149598500 km and the year is 365.2564 days.
  To compute the projection of this velocity along the line of observation
  the direction of observation (precessed to the epoch of observation)
  is converted into ecliptic latitude and
  longitude, l and b, measured from the point of the ascending node using
  a standard spherical coordinate transformation.  The component is then
  <P>
  	vannual = v * cos(b) * (sin(slong-l) - eccen*sin(lperi-l))
  <P>
  where the longitude of the Sun as seen from the Earth, slong, is given by
  <P>
  	slong = lperi + tanom + 180
  </UL>
  <! EndSection:   'ANNUAL VELOCITY'>
  <H2><A NAME="s_solar_motion">SOLAR MOTION</A></H2>
  <! BeginSection: 'SOLAR MOTION'>
  <UL>
  The solar motion is computed by precessing the coordinates of the solar
  motion to the observation epoch and taking the appropriate component
  along the line of sight.
  </UL>
  <! EndSection:   'SOLAR MOTION'>
  <H2><A NAME="s_accuracy">ACCURACY</A></H2>
  <! BeginSection: 'ACCURACY'>
  <UL>
  The calculations are done using IRAF double precision.
  No correction is made for the perturbation of the other planets.  The
  precession does not include nutation.  The interpolation formulas are
  only approximations.  The accuracy of the heliocentric
  velocity are better than a 0.005 of a kilometer per second.
  Relative velocities over short intervals are even better.
  </UL>
  <! EndSection:   'ACCURACY'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. For use directly without data files or images there are two common modes.
  Because of the large number of parameters the parameter values are often
  set using the task <B>eparam</B>.  Then simply execute the command
  <P>
  	cl&gt; rvcorrect
  <P>
  2. To set some of the parameters on the command line
  <P>
  	cl&gt; rvcorrect ra=12:22:1.116 dec=15:55:16.244 ut=5:30
  <P>
  3. To use a text file generate a file containing the year, month, day, ut,
  ra, and dec with one observation per line.
  <P>
  <PRE>
  cl&gt; type rv.obs
  1987 10 21 11:00:24  3:36:15   0:22:04
  1987 10 21 11:08:00  8:19:35  -0:51:35
  1987 10 21 11:15:47  8:35:12   6:40:29
  1987 10 21 12:12:10  9:13:20  61:28:49
  1987 10 21 12:16:03  9:27:48   9:07:08
  1987 10 21 12:20:43  9:50:45  -6:06:58
  1979  3 25 11:22:59 16:07:28 -23:37:49 0 -67.5
  cl&gt; rvcorrect f=rv.obs &gt; rv.dat
  cl&gt; type rv.dat
  ##   HJD          VOBS   VHELIO     VLSR   VDIURNAL   VLUNAR  VANNUAL   VSOLAR
  2447089.96358     0.00    11.07    -2.74     -0.189    0.008   11.246  -13.808
  2447089.96296     0.00    28.05    13.56      0.253    0.010   27.790  -14.498
  2447089.96813     0.00    29.04    16.64      0.262    0.011   28.770  -12.401
  2447090.00834     0.00    22.06    25.26      0.114    0.010   21.940    3.200
  2447090.00884     0.00    27.70    18.55      0.250    0.009   27.438   -9.152
  2447090.01129     0.00    23.99    13.50      0.275    0.007   23.704  -10.484
  2443957.97716   -67.50   -41.37   -31.48      0.002    0.012   26.117    9.884
  </PRE>
  <P>
  4. To use observation parameters from a set of images the command is
  <P>
  	cl&gt; rvcorrect images=hz44.001,aboo.001 &gt; rv.dat
  <P>
  5. A CL loop can be used to compute a table in which one parameter varies.
  <P>
  <PRE>
  	cl&gt; for (x=0.; x&lt;=12.; x=x+1)
  	&gt;&gt;&gt; rvcorrect (ut=x, header=no)
  </PRE>
  <P>
  6. To get the total velocity correction in a script the following may be done.
  <P>
  <PRE>
  	rvcorrect (vobs=12.3, ra=12:33, dec=30:22, ut=5:30, &gt; "dev$null")
  	vlsr = rvcorrect.vlsr
  </PRE>
  <P>
  Note that this does not work when the task is run as a background job!
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_revisions">REVISIONS</A></H2>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_RVCORRECT">RVCORRECT V2.11.4</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='RVCORRECT' Line='RVCORRECT V2.11.4'>
  <DD>The ut keyword can be in either date plus time or hours.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_RVCORRECT">RVCORRECT V2.11</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='RVCORRECT' Line='RVCORRECT V2.11'>
  <DD>Y2K update: The date keyword can be in the full format with full
  year and time.  The time takes precedence over a time keyword.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H2><A NAME="s_acknowledgments">ACKNOWLEDGMENTS</A></H2>
  <! BeginSection: 'ACKNOWLEDGMENTS'>
  <UL>
  Some of the formulas used were obtained by inspection of the code
  for the subroutine DOP in the program DOPSET written by R. N. Manchester
  and M. A. Gordon of NRAO dated January 1970.
  </UL>
  <! EndSection:   'ACKNOWLEDGMENTS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  observatory, asttimes
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'DIURNAL VELOCITY' 'BARYCENTRIC VELOCITY' 'ANNUAL VELOCITY' 'SOLAR MOTION' 'ACCURACY' 'EXAMPLES' 'REVISIONS' 'ACKNOWLEDGMENTS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>