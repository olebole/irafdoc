.. _setjd:

setjd — Compute and set Julian dates in images
==============================================

**Package: echelle**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  setjd -- set various Julian dates in image headers
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  setjd images
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>images</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>The list of images for which to compute Julian dates.  If the <I>listonly</I>
  parameter is not set the image headers will be modified to add or update
  the calculated Julian date values.
  </DD>
  </DL>
  <DL>
  <DT><B>observatory = "<TT>)_.observatory</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='observatory' Line='observatory = ")_.observatory"'>
  <DD>Observatory of observation, used to define the time zone relative to
  Greenwich, if not specified in the image header by the keyword OBSERVAT.
  The default is a redirection to look in the parameters for the parent
  package for a value.  The observatory may be one of the observatories in
  the observatory database, "<TT>observatory</TT>" to select the observatory defined
  by the environment variable "<TT>observatory</TT>" or the parameter
  <B>observatory.observatory</B>, or "<TT>obspars</TT>" to select the current
  parameters set in the <B>observatory</B> task.  See <B>observatory</B> for
  additional information.
  </DD>
  </DL>
  <DL>
  <DT><B>date = "<TT>date-obs</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='date' Line='date = "date-obs"'>
  <DD>Date of observation keyword.  The value must be in FITS format.
  This is one of DD/MM/YY (old FITS format), YYYY-MM-DD (new FITS format),
  or YYYY-MM-DDTHH:MM:SS (new FITS format with time).  The date should be
  in universal time though the <I>utdate</I> parameter can be used if
  this is not the case.  If a time is included it is used in preference
  to the <I>time</I> value.
  </DD>
  </DL>
  <DL>
  <DT><B>time = "<TT>ut</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='time' Line='time = "ut"'>
  <DD>Time of observation keyword with value given in decimal hours or HH:MM:SS.S
  format.  The date may be a local time or universal time as selected by the
  <I>uttime</I> parameter.  The time is used as is
  unless an exposure time keyword is specified, in which case
  the time will be corrected to the midpoint of the exposure from the
  beginning or end of the exposure.  This time is not used if a time
  is given in the date keyword.
  </DD>
  </DL>
  <DL>
  <DT><B>exposure = "<TT>exptime</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='exposure' Line='exposure = "exptime"'>
  <DD>Exposure time keyword with value in seconds.  If specified the time
  is corrected to the midpoint of the exposure.  The time is assumed
  to be the beginning of the exposure unless
  the exposure time keyword name begins with a minus sign, for example
  "<TT>-exptime</TT>", in which case the time is used as the end of the exposure.
  </DD>
  </DL>
  <DL>
  <DT><B>ra = "<TT>ra</TT>", dec = "<TT>dec</TT>", epoch = "<TT>epoch</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ra' Line='ra = "ra", dec = "dec", epoch = "epoch"'>
  <DD>If the heliocentric Julian date is requested the right ascension (in hours)
  and declination (in degrees) of the observation is determined from these
  keywords.  The values may be in either decimal or sexagesimal notation.
  An epoch keyword is optional and if given is used to precess
  the coordinates from the specified epoch to the observation epoch.
  If an epoch keyword is given but is not found in the header or can't
  be interpreted then it is an error.  The epoch keyword value may begin
  with <TT>'B'</TT> or <TT>'J'</TT>.  If the value is before 1800 or after 2100 a warning
  will be printed though the task will still compute the values.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B>jd = "<TT>jd</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='jd' Line='jd = "jd"'>
  <DD>If specified compute the geocentric Julian day (Greenwich) at the
  midpoint of the exposure and record the value in the specified
  header keyword.
  </DD>
  </DL>
  <DL>
  <DT><B>hjd = "<TT>hjd</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='hjd' Line='hjd = "hjd"'>
  <DD>If specified compute the heliocentric Julian day (Greenwich) at the
  midpoint of the exposure and record the value in the specified
  header keyword.
  </DD>
  </DL>
  <DL>
  <DT><B>ljd = "<TT>ljd</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ljd' Line='ljd = "ljd"'>
  <DD>If specified compute the local Julian day number.  This is an integer
  number which is constant for all observations made during the same night.
  It may be used to group observations by night in such tasks as
  <B>refspectra</B>.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B>utdate = yes, uttime = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='utdate' Line='utdate = yes, uttime = yes'>
  <DD>Define whether the date and time of observation are in local standard
  time or in universal time.
  </DD>
  </DL>
  <DL>
  <DT><B>listonly = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='listonly' Line='listonly = no'>
  <DD>List the computed values only and do not modify the image headers.
  When simply listing the images need not have write permission.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <B>Setjd</B> computes the geocentric, heliocentric, and integer
  local Julian dates from information given in the headers of
  the input list of images.  This information may simply be listed or
  the values may be added or modified in the image headers.  Only
  those values which have a keyword specified are computed, printed,
  and entered in the images.  Thus, one need not compute all values
  and the dependent image header parameters required for computing them
  need not be present.  For example, if the coordinates of the
  observation are not available one should set the <I>hjd</I> parameter
  to an empty string.
  <P>
  Often the date and time of observation are recorded either at the
  beginning or the end of an exposure.  To compute the Julian dates
  at the midpoint of the exposure the exposure keyword is specified.
  A negative sign preceding the keyword name defines correcting from
  the end of the exposure otherwise the correction is from the
  beginning of the exposure.  The exposure time must be in seconds and
  there is no allowance made for exposures which are interrupted.
  See also the task <B>setairmass</B> which may be used to compute a
  universal time midexposure value.
  <P>
  The date and time of observations should be given either in universal
  time.  However, if they are given in local standard time (there is no
  provisions for daylight savings times) the <I>utdate</I> and <I>uttime</I>
  parameters may be used.  Conversion between local and universal times, as
  well as the computation of the local integer date, requires the time zone
  in (positive) hours behind Greenwich or (negative) hours ahead of
  Greenwich.  This information is determined from the observatory at which
  the observations were made.  If the observatory is specified in the image
  header under the keyword OBSERVAT with a value which has an entry in the
  NOAO, local, or user observatory database then the value from the database
  is used.  This is the safest way since the observatory is tied to the
  actual image.  Otherwise, the <I>observatory</I> parameter defines the
  observatory.  The special value "<TT>observatory</TT>" allows defining a default
  observatory with an environment variable or the <B>observatory</B> task.
  Explicitly use the parameter <I>observatory.timezone</I> use the value
  "<TT>obspars</TT>".  For more information see help under <B>observatory</B>.
  <P>
  The heliocentric Julian date is computed by defining a keyword for
  this value and also defining the keywords for the right ascension (in hours)
  and declination (in degrees).  An optional epoch keyword may be
  used if the RA and DEC are not for the observation epoch.
  <P>
  The local integer Julian day number is the Julian date which begins at
  local noon.  Thus, all observations made during a night will have the
  same day number.  This day number may be useful in grouping
  observations by nights.  Note that in some time zones the UT
  date of observation may also be constant over a night.
  <P>
  Among the uses for this task is to define keywords to be used by the task
  <B>refspectra</B>.  In particular, the exposure midpoint geocentric Julian
  date makes a good sort parameter and the local Julian day number makes a
  good group parameter.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  Compute all the Julian date quantities for 4 arc exposures with
  header parameters given below.
  <P>
  <PRE>
      demoarc1:
  	OBSERVAT= 'KPNO              '  /  observatory
  	EXPTIME =                  60.  /  actual integration time
  	DATE-OBS= '26/11/91          '  /  date (dd/mm/yy) of obs.
  	UT      = '12:11:30.00       '  /  universal time
  	RA      = '06:37:02.00       '  /  right ascension
  	DEC     = '06:09:03.00       '  /  declination
  	EPOCH   =               1991.9  /  epoch of ra and dec
  <P>
      demoarc2:
  	OBSERVAT= 'KPNO              '  /  observatory
  	EXPTIME =                  60.  /  actual integration time
  	DATE-OBS= '26/11/91          '  /  date (dd/mm/yy) of obs.
  	UT      = '12:41:30.00       '  /  universal time
  	RA      = '06:37:02.00       '  /  right ascension
  	DEC     = '06:09:03.00       '  /  declination
  	EPOCH   =               1991.9  /  epoch of ra and dec
  <P>
      demoarc3:
  	OBSERVAT= 'CTIO              '  /  observatory
  	EXPTIME =                  60.  /  actual integration time
  	DATE-OBS= '27/11/91          '  /  date (dd/mm/yy) of obs.
  	UT      = '11:11:30.00       '  /  universal time
  	RA      = '06:37:02.00       '  /  right ascension
  	DEC     = '06:09:03.00       '  /  declination
  	EPOCH   =               1991.9  /  epoch of ra and dec
  <P>
      demoarc4:
  	OBSERVAT= 'CTIO              '  /  observatory
  	EXPTIME =                  60.  /  actual integration time
  	DATE-OBS= '27/11/91          '  /  date (dd/mm/yy) of obs.
  	UT      = '12:21:30.00       '  /  universal time
  	RA      = '06:37:02.00       '  /  right ascension
  	DEC     = '06:09:03.00       '  /  declination
  	EPOCH   =               1991.9  /  epoch of ra and dec
  <P>
      cl&gt; setjd demoarc?.imh
      # SETJD: Observatory parameters for Kitt Peak ...
      #              Image            JD           HJD   LOCALJD
  	    demoarc1.imh  2448587.0083  2448587.0127   2448586
  	    demoarc2.imh  2448587.0292  2448587.0336   2448586
      # SETJD: Observatory parameters for Cerro Tololo ...
  	    demoarc3.imh  2448587.9667  2448587.9711   2448587
  	    demoarc4.imh  2448588.0153  2448588.0197   2448587
  </PRE>
  <P>
  Note the use of the observatory parameter to switch observatories and
  the local Julian day number which is constant over a night even though
  the Julian date may change during the observations.
  <P>
  2.  To compute only the geocentric Julian date from the "<TT>DATE</TT>" and
  "<TT>TIME</TT>" keywords in an image,
  <P>
  <PRE>
      cl&gt; setjd obs1 date=date time=time exp="" hjd="" ljd=""
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>SETJD V2.11.2</B></DT>
  <! Sec='REVISIONS' Level=0 Label='SETJD' Line='SETJD V2.11.2'>
  <DD>Y2K update:  Updated to use the new FITS format for the date.  If the
  time is given in the date keyword it is used in preference to the
  time keyword.
  </DD>
  </DL>
  <DL>
  <DT><B>SETJD V2.11</B></DT>
  <! Sec='REVISIONS' Level=0 Label='SETJD' Line='SETJD V2.11'>
  <DD>The checking of the epoch keyword value was improved.  Previously if
  there was a problem with the keyword value (missing or malformed) the
  task would use the epoch of the observation.  Now it is an error
  if an epoch keyword is specified but the epoch value can't be determined.
  Also a leading <TT>'B'</TT> or <TT>'J'</TT> is allowed and a warning will be given if
  the epoch value is unlikely.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  setairmass, hedit, refspectra, observatory
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
