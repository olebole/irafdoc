setairmass — Compute effective airmass and middle UT for an exposure
====================================================================

**Package: specred**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>setairmass (Nov00)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>astutil</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>setairmass (Nov00)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>setairmass</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  setairmass -- update image headers with the effective airmass 
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  setairmass images
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_images">images</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>The list of images for which to calculate the airmass.  The image headers may
  optionally be updated with the airmass and the mid-UT of the exposure.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_observatory">observatory = "<TT>)_.observatory</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='observatory' Line='observatory = ")_.observatory"'>
  <DD>Observatory for which airmasses are to be computed if the observatory is not
  specified in the image header by the keyword OBSERVAT. The default is a
  redirection to look in the parameters for the parent package for a value. The
  observatory may be one of the observatories in the observatory database,
  "<TT>observatory</TT>" to select the observatory defined by the environment variable
  "<TT>observatory</TT>" or the parameter <B>observatory.observatory</B>, or "<TT>obspars</TT>" to
  select the current parameters set in the <B>observatory</B> task. See help for
  <B>observatory</B> for additional information. If the input consists of images
  then the observatory is defined by the OBSERVAT keyword if present.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_intype">intype = "<TT>beginning</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='intype' Line='intype = "beginning"'>
  <DD>The time stamp of the observation as recorded at the telescope for the time
  dependent header keywords.  The choices are the "<TT>beginning</TT>", "<TT>middle</TT>" or "<TT>end</TT>"
  of the observation.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_outtype">outtype = "<TT>effective</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outtype' Line='outtype = "effective"'>
  <DD>The output time stamp desired for the airmass. The choices are the "<TT>effective</TT>"
  airmass, or the airmass at the "<TT>beginning</TT>", "<TT>middle</TT>" or "<TT>end</TT>" of the
  observation.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ra">ra = "<TT>ra</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ra' Line='ra = "ra"'>
  <DD>The name of the keyword that contains the right ascension. The right ascension
  is assumed to be in hours unless ra is one of the standard CRVALn keywords in
  which case it is assumed to be in degrees.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_dec">dec = "<TT>dec</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dec' Line='dec = "dec"'>
  <DD>The name of the keyword that contains the declination in degrees.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_equinox">equinox = "<TT>epoch</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='equinox' Line='equinox = "epoch"'>
  <DD>The name of the keyword that contains the equinox of the right ascension and
  declination coordinates in years.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_st">st = "<TT>st</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='st' Line='st = "st"'>
  <DD>The name of the keyword containing the sidereal time in hours. 
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ut">ut = "<TT>ut</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ut' Line='ut = "ut"'>
  <DD>The name of the keyword containing the ut time.  This keyword can either
  be in date plus time format or in hours.  Note that this allows setting
  both the "<TT>date-obs</TT>" and "<TT>ut</TT>".  If no time is found then
  a time of 0hrs is used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_date">date = "<TT>date-obs</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='date' Line='date = "date-obs"'>
  <DD>The name of the keyword that contains the UT date of the observation. The
  format should be `DD/MM/YY' (old FITS format), YYYY-MM-DD (new FITS format),
  or YYYY-MM-DDTHH:MM:SS (new FITS format with time).  If there is a time
  and no time is found in the ut keyword then it is used for the ut.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_exposure">exposure = "<TT>exptime</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='exposure' Line='exposure = "exptime"'>
  <DD>The name of the keyword that contains the exposure time (in seconds) of the
  image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_airmass">airmass = "<TT>airmass</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='airmass' Line='airmass = "airmass"'>
  <DD>The name of the output keyword that will receive the computed airmass.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_utmiddle">utmiddle = "<TT>utmiddle</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='utmiddle' Line='utmiddle = "utmiddle"'>
  <DD>The name of the output keyword that will receive the universal time for
  the middle of the observation.  The format of the keyword will be the same
  as that specifying the universal time.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_scale">scale = 750.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='scale' Line='scale = 750.0'>
  <DD>The atmospheric scale height.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_show">show = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='show' Line='show = yes'>
  <DD>Print the airmasses and mid-UT's for each image?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_update">update = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='update' Line='update = yes'>
  <DD>Update the image headers with the airmasses and the mid-UT's?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_override">override = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='override' Line='override = yes'>
  <DD>If updating the image headers, override values that were previously recorded ?
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  SETAIRMASS will calculate the effective airmass of an astronomical image, as
  described below under "<TT>ALGORITHMS</TT>".  The task requires the instantaneous
  zenith distance at the beginning, middle and end of the exposure. These are
  calculated using the right ascension, declination, and equinox as well as the
  sidereal time, exposure time, UT date, and observatory from the image header.
  If the observatory is not available in the image header under the keyword
  OBSERVAT, the observatory is defined by the <I>observatory</I> parameter. See
  help for <I>observatory</I> for further information.
  <P>
  The right ascension and declination will be precessed from the given equinox to
  the date of observation. The name of the right ascension, declination, equinox,
  sidereal time, ut time, exposure time, and date keywords can be specified as
  parameters. These keywords should express the right ascension in hours,
  the declination in degrees, the equinox in years, the sidereal time in hours,
  the universal time in hours, the exposure time in seconds, and the date in
  FITS format. If any of the required keywords are missing from the image
  headers, they can be added using the hedit or asthedit tasks.  Note that
  the universal time keyword may be in either a date plus time format or
  in hours and any output middle universal time will be in the same format.
  <P>
  Before using this task, you will need to know the "<TT>time stamp</TT>" of the time
  varying header quantities (e.g. sidereal time).  Do the recorded values
  represent the beginning, the middle or the end of the exposure ? This should
  be set in the <B>intype</B> parameter.
  <P>
  If for some reason the effective airmass is not desired, the value of the
  airmass at the beginning, middle or end of the exposure can be recorded in the
  header keyword specified by the <I>airmass</I> parameter. The <B>show</B>
  parameter can be used to control the output to the terminal. The <B>update</B>
  and <B>override</B> parameters control the header keyword output.
  <P>
  SETAIRMASS will also calculate the universal time of the middle of the exposure
  and place the value in the header keyword specified by the <I>utmiddle</I>
  parameter.  This assumes that the value for the UT is in the date keyword
  or ut keyword, with the same time stamp as the sidereal time. The
  mid-observation UT is useful for interpolating calibration arc dispersion
  solutions using REFSPECTRA, especially when the exposure time is
  long.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_algorithms">ALGORITHMS</A></H2>
  <! BeginSection: 'ALGORITHMS'>
  <UL>
  The mean airmass is calculated uses the formula described in "<TT>Some
  Factors Affecting the Accuracy of Stellar Photometry with CCDs</TT>" by P.
  Stetson, DAO preprint, September 1988.  This simple formula is:
  <P>
  <PRE>
  	    AM (eff) = [AM (beginning) + 4*AM (middle) + AM (end)] / 6
  </PRE>
  <P>
  and is derived by using Simpson's 1/3 rule to approximate the integral
  that represents the mean airmass.
  <P>
  The beginning, middle and end airmasses are calculated using the
  relation between airmass and elevation (or zenith distance) in John
  Ball's book on Algorithms for the HP-45:
  <P>
  <PRE>
  	    AM = sqrt (x**2 + 2*scale + 1) - x, where
  <P>
  	     x = scale * sin(elevation) = scale * cos(ZD)
  </PRE>
  <P>
  The atmospheric scaling parameter is <I>scale</I> (see "<TT>Astrophysical
  Quantities</TT>" by Allen, 1973 p.125,133).
  <P>
  </UL>
  <! EndSection:   'ALGORITHMS'>
  <H2><A NAME="s_keywords">KEYWORDS</A></H2>
  <! BeginSection: 'KEYWORDS'>
  <UL>
  The input keywords are:
  <DL>
  <DT><B><A NAME="l_OBSERVAT">OBSERVAT</A></B></DT>
  <! Sec='KEYWORDS' Level=0 Label='OBSERVAT' Line='OBSERVAT'>
  <DD>Observatory at which the data was taken.  If absent the observatory is
  determined using the <I>observatory</I> parameter.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_"><I>ra</I></A></B></DT>
  <! Sec='KEYWORDS' Level=0 Label='' Line='\fIra\fR'>
  <DD>Right ascension in hours at the beginning, middle, or end of the observation.
  If ra is one of the CRVALn keywords it is assumed to be in degrees.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_"><I>dec</I></A></B></DT>
  <! Sec='KEYWORDS' Level=0 Label='' Line='\fIdec\fR'>
  <DD>Declination in degrees at the beginning, middle, or end of the observation.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_"><I>equinox</I></A></B></DT>
  <! Sec='KEYWORDS' Level=0 Label='' Line='\fIequinox\fR'>
  <DD>The equinox of the coordinates.  The right ascension and declination will
  be precessed from this epoch to the date of the observation before being
  used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_"><I>st</I></A></B></DT>
  <! Sec='KEYWORDS' Level=0 Label='' Line='\fIst\fR'>
  <DD>Sidereal time in hours at the beginning, middle, or end of the observation.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_"><I>ut</I></A></B></DT>
  <! Sec='KEYWORDS' Level=0 Label='' Line='\fIut\fR'>
  <DD>Universal time in hours at the beginning, middle, or end of the observation.
  This may be in either date plus time format or just in hours.  
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_"><I>date</I></A></B></DT>
  <! Sec='KEYWORDS' Level=0 Label='' Line='\fIdate\fR'>
  <DD>The value of the date parameter is the keyword name to be used for the date of
  the observation.  The date must be in either the old or new FITS format.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_"><I>exposure</I></A></B></DT>
  <! Sec='KEYWORDS' Level=0 Label='' Line='\fIexposure\fR'>
  <DD>The value of the exposure parameter is the keyword name to be used for the
  exposure time in seconds.
  </DD>
  </DL>
  <P>
  The output keywords are:
  <DL>
  <DT><B><A NAME="l_"><I>airmass</I></A></B></DT>
  <! Sec='KEYWORDS' Level=0 Label='' Line='\fIairmass\fR'>
  <DD>The value of the airmass parameter is the keyword name to be used for
  the computed airmass at either the beginning, middle, or end of the
  exposure, or for the weighted effective value over the exposure.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_"><I>utmiddle</I></A></B></DT>
  <! Sec='KEYWORDS' Level=0 Label='' Line='\fIutmiddle\fR'>
  <DD>The value of the utmiddle parameter is the keyword name to be used for
  the universal time at the middle of the exposure.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'KEYWORDS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Calculate the effective airmass of the IRAF test picture, dev$pix.
  <P>
  <PRE>
      cl&gt; setairmass dev$pix exposure=itime update-
  </PRE>
  <P>
  Note that the test picture does not have the correct coordinate epoch
  listed in its header, so no precession will be performed. 
  <P>
  2. Calculate the effective airmass of the IRAF test picture dev$ypix in two
  ways.
  <P>
  <PRE>
      cl&gt; setairmass dev$ypix exposure=itime update-
  <P>
      cl&gt; setairmass dev$ypix ra=crval1 dec=crval2 equinox=equinox \<BR>
          exposure=itime update-
  </PRE>
  <P>
  Note the first way gives the same results as example 1. The second way
  uses the J2000 equatorial system rather then the ra and dec at the time
  of observation.
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_revisions">REVISIONS</A></H2>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_SETAIRMASS">SETAIRMASS V2.11.4</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='SETAIRMASS' Line='SETAIRMASS V2.11.4'>
  <DD>The ut keyword now has precedence over any time in the date keyword
  and it can be either date plus time or hours.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_SETAIRMASS">SETAIRMASS V2.11.3</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='SETAIRMASS' Line='SETAIRMASS V2.11.3'>
  <DD>The right ascension, declination, equinox, st, and ut keywords were made 
  parameters rather than being hard wired.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_SETAIRMASS">SETAIRMASS V2.11.2</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='SETAIRMASS' Line='SETAIRMASS V2.11.2'>
  <DD>Y2K update: This task was updated to use the new FITS date format.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  airmass, hedit, refspectra, observatory
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'ALGORITHMS' 'KEYWORDS' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>