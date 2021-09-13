keywpars — Translate the image header keywords used in ASTUTIL package
======================================================================

**Package: astutil**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>keywpars (May93)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.astutil</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>keywpars (May93)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>keywpars</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  keywpars -- edit the image header keywords used by the package
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  keywpars
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_ra">ra = "<TT>RA</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ra' Line='ra = "RA"'>
  <DD>Right Ascension keyword. (Value in HMS format).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_dec">dec = "<TT>DEC</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dec' Line='dec = "DEC"'>
  <DD>Declination keyword. (Value in HMS format).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ut">ut = "<TT>UT</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ut' Line='ut = "UT"'>
  <DD>UT of observation keyword.  This field is the UT start of the observation.
  (Value in HMS Format).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_utmiddle">utmiddle = "<TT>UTMIDDLE</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='utmiddle' Line='utmiddle = "UTMIDDLE"'>
  <DD>UT mid-point of observation keyword.  This field is the UT mid-point of 
  the observation.  (Value in HMS Format).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_exptime">exptime = "<TT>EXPTIME</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='exptime' Line='exptime = "EXPTIME"'>
  <DD>Exposure time keyword. (Value in Seconds).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_epoch">epoch = "<TT>EPOCH</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='epoch' Line='epoch = "EPOCH"'>
  <DD>Epoch of coordinates keyword. (Value in Years).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_date_obs">date_obs = "<TT>DATE-OBS</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='date_obs' Line='date_obs = "DATE-OBS"'>
  <DD>Date of observation keyword.  Format for this field should be
  dd/mm/yy (old FITS format), yyyy-mm-dd (new FITS format), or
  yyyy-mm-ddThh:mm:ss.sss (new FITS format with time).
  </DD>
  </DL>
  <P>
  <CENTER>OUTPUT KEYWORDS
  
  </CENTER><BR>
  <DL>
  <DT><B><A NAME="l_hjd">hjd = "<TT>HJD</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='hjd' Line='hjd = "HJD"'>
  <DD>Heliocentric Julian date keyword. (Value in Days).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_mjd_obs">mjd_obs = "<TT>MJD-OBS</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='mjd_obs' Line='mjd_obs = "MJD-OBS"'>
  <DD>Modified Julian Data keyword.  The MJD is defined as the Julian date of
  the mid-point of the observation - 2440000.5.  (Value in Days).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_vobs">vobs = "<TT>VOBS</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='vobs' Line='vobs = "VOBS"'>
  <DD>Observed radial velocity keyword.  (Value in Km/sec).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_vrel">vrel = "<TT>VREL</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='vrel' Line='vrel = "VREL"'>
  <DD>Observed radial velocity keyword. (Value in Km/sec).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_vhelio">vhelio = "<TT>VHELIO</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='vhelio' Line='vhelio = "VHELIO"'>
  <DD>Corrected heliocentric radial velocity keyword.  (Value in Km/sec).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_vlsr">vlsr = "<TT>VLSR</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='vlsr' Line='vlsr = "VLSR"'>
  <DD>Local Standard of Rest velocity keyword.  (Value in Km/sec).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_vsun">vsun = "<TT>VSUN</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='vsun' Line='vsun = "VSUN"'>
  <DD>Epoch of solar motion.  (Character string with four real valued fields 
  describing the solar velocity (km/sec), the RA of the solar velocity (hours),
  the declination of the solar velocity (degrees), and the epoch of solar
  coordinates (years)).
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
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
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. List the image header keywords.
  <P>
  <PRE>
  	as&gt; lpar keywpars
  </PRE>
  <P>
  2. Edit the image header keywords
  <P>
  <PRE>
  	as&gt; keywpars
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_revisions">REVISIONS</A></H2>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_KEYPARS">KEYPARS V2.10.3</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='KEYPARS' Line='KEYPARS V2.10.3'>
  <DD>First version.  Currently only used by the <I>RVCORRECT</I> task.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  fxcor, rvcorrect
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>