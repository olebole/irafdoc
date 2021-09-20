.. _keywpars:

keywpars: Translate the image header keywords used in RV package
================================================================

**Package: rv**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  keywpars -- edit the image header keywords used by the package
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  keywpars
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>ra = <span style="font-family: monospace;">"RA"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='ra' Line='ra = "RA"' -->
  <dd>Right Ascension keyword. (Value in HMS format).
  </dd>
  </dl>
  <dl>
  <dt><b>dec = <span style="font-family: monospace;">"DEC"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='dec' Line='dec = "DEC"' -->
  <dd>Declination keyword. (Value in HMS format).
  </dd>
  </dl>
  <dl>
  <dt><b>ut = <span style="font-family: monospace;">"UT"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='ut' Line='ut = "UT"' -->
  <dd>UT of observation keyword.  This field is the UT start of the observation.
  (Value in HMS Format).
  </dd>
  </dl>
  <dl>
  <dt><b>utmiddle = <span style="font-family: monospace;">"UTMIDDLE"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='utmiddle' Line='utmiddle = "UTMIDDLE"' -->
  <dd>UT mid-point of observation keyword.  This field is the UT mid-point of 
  the observation.  (Value in HMS Format).
  </dd>
  </dl>
  <dl>
  <dt><b>exptime = <span style="font-family: monospace;">"EXPTIME"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='exptime' Line='exptime = "EXPTIME"' -->
  <dd>Exposure time keyword. (Value in Seconds).
  </dd>
  </dl>
  <dl>
  <dt><b>epoch = <span style="font-family: monospace;">"EPOCH"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='epoch' Line='epoch = "EPOCH"' -->
  <dd>Epoch of coordinates keyword. (Value in Years).
  </dd>
  </dl>
  <dl>
  <dt><b>date_obs = <span style="font-family: monospace;">"DATE-OBS"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='date_obs' Line='date_obs = "DATE-OBS"' -->
  <dd>Date of observation keyword.  Format for this field should be
  dd/mm/yy, (old FITS format), yyyy-mm-dd (new FITS format), or
  yyyy-mm-ddThh:mm:ss.sss (new FITS format with time).
  </dd>
  </dl>
  <p style="text-align:center">OUTPUT KEYWORDS
  
  </p>
  <dl>
  <dt><b>hjd = <span style="font-family: monospace;">"HJD"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='hjd' Line='hjd = "HJD"' -->
  <dd>Heliocentric Julian date keyword. (Value in Days).
  </dd>
  </dl>
  <dl>
  <dt><b>mjd_obs = <span style="font-family: monospace;">"MJD-OBS"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='mjd_obs' Line='mjd_obs = "MJD-OBS"' -->
  <dd>Modified Julian Data keyword.  The MJD is defined as the julian date of
  the mid-point of the observation - 2440000.5.  (Value in Days).
  </dd>
  </dl>
  <dl>
  <dt><b>vobs = <span style="font-family: monospace;">"VOBS"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='vobs' Line='vobs = "VOBS"' -->
  <dd>Observed radial velocity keyword.  (Value in Km/sec).
  </dd>
  </dl>
  <dl>
  <dt><b>vrel = <span style="font-family: monospace;">"VREL"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='vrel' Line='vrel = "VREL"' -->
  <dd>Observed radial velocity keyword. (Value in Km/sec).
  </dd>
  </dl>
  <dl>
  <dt><b>vhelio = <span style="font-family: monospace;">"VHELIO"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='vhelio' Line='vhelio = "VHELIO"' -->
  <dd>Corrected heliocentric radial velocity keyword.  (Value in Km/sec).
  </dd>
  </dl>
  <dl>
  <dt><b>vlsr = <span style="font-family: monospace;">"VLSR"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='vlsr' Line='vlsr = "VLSR"' -->
  <dd>Local Standard of Rest velocity keyword.  (Value in Km/sec).
  </dd>
  </dl>
  <dl>
  <dt><b>vsun = <span style="font-family: monospace;">"VSUN"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='vsun' Line='vsun = "VSUN"' -->
  <dd>Epoch of solar motion.  (Character string with four real valued fields 
  describing the solar velocity (km/sec), the RA of the solar velocity (hours),
  the declination of the solar velocity (degrees), and the epoch of solar
  coordinates (years)).
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The image header keywords used by the <i>fxcor</i> task can be 
  edited if they differ
  from the NOAO standard keywords.  For example, if the image header keyword
  giving the exposure time for the image is written out as <span style="font-family: monospace;">"EXP-TIME"</span> instead
  of the standard <span style="font-family: monospace;">"OTIME"</span> at a given site, the keyword accessed for 
  that information
  may be changed based on the value of the <i>exptime</i> parameter.
  </p>
  <p>
  The <i>vhelio</i> keywords must be added to the image header of the template 
  spectrum and should contain the known radial velocity of the template star.
  The output keywords may be added to the object image header if the
  tasks <i>fxcor.imudate</i> parameter is set.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. List the image header keywords.
  </p>
  <pre>
  	rv&gt; lpar keywpars
  </pre>
  <p>
  2. Edit the image header keywords
  </p>
  <pre>
  	rv&gt; keywpars
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  fxcor
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
