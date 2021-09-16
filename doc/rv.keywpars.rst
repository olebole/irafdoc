.. _keywpars:

keywpars — Translate the image header keywords used in RV package
=================================================================

**Package: rv**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  keywpars -- edit the image header keywords used by the package
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  keywpars
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>ra = "<TT>RA</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ra' Line='ra = "RA"'>
  <DD>Right Ascension keyword. (Value in HMS format).
  </DD>
  </DL>
  <DL>
  <DT><B>dec = "<TT>DEC</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dec' Line='dec = "DEC"'>
  <DD>Declination keyword. (Value in HMS format).
  </DD>
  </DL>
  <DL>
  <DT><B>ut = "<TT>UT</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ut' Line='ut = "UT"'>
  <DD>UT of observation keyword.  This field is the UT start of the observation.
  (Value in HMS Format).
  </DD>
  </DL>
  <DL>
  <DT><B>utmiddle = "<TT>UTMIDDLE</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='utmiddle' Line='utmiddle = "UTMIDDLE"'>
  <DD>UT mid-point of observation keyword.  This field is the UT mid-point of 
  the observation.  (Value in HMS Format).
  </DD>
  </DL>
  <DL>
  <DT><B>exptime = "<TT>EXPTIME</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='exptime' Line='exptime = "EXPTIME"'>
  <DD>Exposure time keyword. (Value in Seconds).
  </DD>
  </DL>
  <DL>
  <DT><B>epoch = "<TT>EPOCH</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='epoch' Line='epoch = "EPOCH"'>
  <DD>Epoch of coordinates keyword. (Value in Years).
  </DD>
  </DL>
  <DL>
  <DT><B>date_obs = "<TT>DATE-OBS</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='date_obs' Line='date_obs = "DATE-OBS"'>
  <DD>Date of observation keyword.  Format for this field should be
  dd/mm/yy, (old FITS format), yyyy-mm-dd (new FITS format), or
  yyyy-mm-ddThh:mm:ss.sss (new FITS format with time).
  </DD>
  </DL>
  <P>
  <CENTER>OUTPUT KEYWORDS
  
  </CENTER><BR>
  <DL>
  <DT><B>hjd = "<TT>HJD</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='hjd' Line='hjd = "HJD"'>
  <DD>Heliocentric Julian date keyword. (Value in Days).
  </DD>
  </DL>
  <DL>
  <DT><B>mjd_obs = "<TT>MJD-OBS</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='mjd_obs' Line='mjd_obs = "MJD-OBS"'>
  <DD>Modified Julian Data keyword.  The MJD is defined as the julian date of
  the mid-point of the observation - 2440000.5.  (Value in Days).
  </DD>
  </DL>
  <DL>
  <DT><B>vobs = "<TT>VOBS</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='vobs' Line='vobs = "VOBS"'>
  <DD>Observed radial velocity keyword.  (Value in Km/sec).
  </DD>
  </DL>
  <DL>
  <DT><B>vrel = "<TT>VREL</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='vrel' Line='vrel = "VREL"'>
  <DD>Observed radial velocity keyword. (Value in Km/sec).
  </DD>
  </DL>
  <DL>
  <DT><B>vhelio = "<TT>VHELIO</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='vhelio' Line='vhelio = "VHELIO"'>
  <DD>Corrected heliocentric radial velocity keyword.  (Value in Km/sec).
  </DD>
  </DL>
  <DL>
  <DT><B>vlsr = "<TT>VLSR</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='vlsr' Line='vlsr = "VLSR"'>
  <DD>Local Standard of Rest velocity keyword.  (Value in Km/sec).
  </DD>
  </DL>
  <DL>
  <DT><B>vsun = "<TT>VSUN</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='vsun' Line='vsun = "VSUN"'>
  <DD>Epoch of solar motion.  (Character string with four real valued fields 
  describing the solar velocity (km/sec), the RA of the solar velocity (hours),
  the declination of the solar velocity (degrees), and the epoch of solar
  coordinates (years)).
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The image header keywords used by the <I>fxcor</I> task can be 
  edited if they differ
  from the NOAO standard keywords.  For example, if the image header keyword
  giving the exposure time for the image is written out as "<TT>EXP-TIME</TT>" instead
  of the standard "<TT>OTIME</TT>" at a given site, the keyword accessed for 
  that information
  may be changed based on the value of the <I>exptime</I> parameter.
  <P>
  The <I>vhelio</I> keywords must be added to the image header of the template 
  spectrum and should contain the known radial velocity of the template star.
  The output keywords may be added to the object image header if the
  tasks <I>fxcor.imudate</I> parameter is set.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. List the image header keywords.
  <P>
  <PRE>
  	rv&gt; lpar keywpars
  </PRE>
  <P>
  2. Edit the image header keywords
  <P>
  <PRE>
  	rv&gt; keywpars
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  fxcor
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
