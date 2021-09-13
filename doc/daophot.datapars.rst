datapars — Edit the image data dependent parameters
===================================================

**Package: daophot**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>datapars (May00)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.digiphot.daophot</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>datapars (May00)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>datapars</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  datapars -- edit the data dependent parameters
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  datapars
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_scale">scale = 1.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='scale' Line='scale = 1.0'>
  <DD>The scale of the image in user units, e.g. arcseconds per pixel.  All DAOPHOT
  distance dependent parameters are assumed to be in units of scale. If
  <I>scale</I> = 1.0 these parameters are assumed to be in units of pixels. Most
  DAOPHOT users should leave <I>scale</I> set to 1.0 unless they intend to compare
  their aperture photometry results directly with data in the literature.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fwhmpsf">fwhmpsf = 2.5 (scale units)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fwhmpsf' Line='fwhmpsf = 2.5 (scale units)'>
  <DD>The full-width half-maximum of the point spread function in scale units.
  The DAOFIND task and the PHOT task  "<TT>gauss</TT>" and "<TT>ofilter</TT>" centering algorithms
  depend on the value of fwhmpsf. DAOPHOT users can either determine a value
  for fwhmpsf using an external task such as IMEXAMINE, or make use of the
  interactive capabilities of the DAOPHOT tasks to set and store it.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_emission">emission = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='emission' Line='emission = yes'>
  <DD>The features to be measured are above sky. By default the DAOPHOT package
  considers all features to be emission features. DAOPHOT users should
  leave this parameter set to "<TT>yes</TT>". 
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_sigma">sigma = 0.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sigma' Line='sigma = 0.0'>
  <DD>The standard deviation of the sky pixels.  The DAOFIND task and the PHOT task
  "<TT>constant</TT>" sky fitting algorithm error estimate depend on the value of sigma. 
  DAOPHOT users should set sigma to a value representative of the noise in
  the sky background.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_datamin">datamin = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='datamin' Line='datamin = INDEF'>
  <DD>The minimum good pixel value. Datamin defaults to -MAX_REAL the minimum
  floating point number supported by the host computer. Datamin is used
  to detect and remove bad data from the sky aperture, detect and flag
  bad data in the aperture photometry aperture, and detect and remove  bad
  data from the PSF fitting aperture.  DAOPHOT users should either leave
  datamin set to INDEF or set it to a number between 5-7 sigma below the
  sky background value.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_datamax">datamax = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='datamax' Line='datamax = INDEF'>
  <DD>The maximum good pixel value. Datamax defaults to MAX_REAL the maximum
  floating point number supported by the host computer.  Datamax is used
  to detect and remove bad data from the sky aperture, detect and flag
  bad data in the aperture photometry aperture, and detect and remove  bad
  data from the PSF fitting aperture.  DAOPHOT users should either leave
  datamax set to INDEF or set it to the linearity or saturation
  limit of the detector.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_noise">noise = "<TT>poisson</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='noise' Line='noise = "poisson"'>
  <DD>The noise model used to estimate the uncertainties in the computed
  magnitudes. DAOPHOT users must leave noise set to "<TT>poisson</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ccdread">ccdread = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ccdread' Line='ccdread = ""'>
  <DD>The image header keyword defining the readout noise parameter whose units
  are assumed to be electrons.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_gain">gain = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='gain' Line='gain = ""'>
  <DD>The image header keyword defining the gain parameter whose units are assumed to
  be electrons per adu.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_readnoise">readnoise = 0.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='readnoise' Line='readnoise = 0.0'>
  <DD>The readout noise of the detector in electrons. DAOPHOT users should set
  readnoise or ccdread to its correct value before running any of the DAOPHOT
  package tasks in order to ensure that the PSF fitting weights, magnitude
  error estimates, and chi values are correct.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_epadu">epadu = 1.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='epadu' Line='epadu = 1.0'>
  <DD>The gain of the detector in electrons per adu. DAOPHOT users should set this
  epadu or gain to its correct value before running any of the DAOPHOT package
  tasks in order to ensure that the PSF fitting weights, magnitude error 
  estimates, and chi values are correct.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_exposure">exposure = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='exposure' Line='exposure = ""'>
  <DD>The image header exposure time keyword. The time units are arbitrary but
  must be consistent for any list of images whose magnitudes are to be compared.
  The computed magnitudes are normalized to  one timeunit by the PHOT task.
  As the magnitude scale of the DAOPHOT package is set by the PHOT task,
  setting exposure can save DAOPHOT users a lot of unnecessary zero point
  corrections in future analysis and calibration steps.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_airmass">airmass = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='airmass' Line='airmass = ""'>
  <DD>The image header airmass keyword.  The airmass parameter is not used
  directly by DAOPHOT but the airmass value is stored in the output file
  and its presence there will simplify future calibration steps.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_filter">filter = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='filter' Line='filter = ""'>
  <DD>The image header filter id keyword.  The filter parameter is not used
  directly by DAOPHOT but the filter id is stored in the output file
  and its presence there will simplify future calibration steps.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_obstime">obstime = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='obstime' Line='obstime = ""'>
  <DD>The image header time of observation keyword. The obstime parameter is not used
  directly by DAOPHOT but the obstime value is stored in the output file
  and its presence there will simplify future calibration steps.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_itime">itime = 1.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='itime' Line='itime = 1.0'>
  <DD>The exposure time for the image in arbitrary units. The DAOPHOT magnitudes are
  normalized to 1 timeunit by the PHOT task using the value of exposure in the
  image header if exposure is defined or the value of itime.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xairmass">xairmass = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xairmass' Line='xairmass = INDEF'>
  <DD>The airmass value.  The airmass is read from the image header if airmass
  is defined  or from xairmass. The airmass value is stored in the DAOPHOT
  output files.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ifilter">ifilter = "<TT>INDEF</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ifilter' Line='ifilter = "INDEF"'>
  <DD>The filter id string. The filter id is read from the image header if filter
  is defined otherwise from ifilter. The filter id is stored in the DAOPHOT
  output files.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_otime">otime = "<TT>INDEF</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='otime' Line='otime = "INDEF"'>
  <DD>The value of the time of observation. The time of observation is read from
  the image header if obstime is defined otherwise from otime. The time of
  observation is stored in the DAOPHOT output files.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  <I>Datapars</I> sets the image data dependent parameters. These parameters are
  functions, of the instrument optics, the noise characteristics and range of
  linearity of the detector, and the observing conditions. Many of the
  centering, sky fitting, and photometry algorithm parameters in the CENTERPARS,
  FITSKYPARS, PHOTPARS, and DAOPARS  parameter sets scale with the data dependent
  parameters.
  <P>
  The parameter <I>scale</I> sets the scale of the apertures used by the
  centering, sky fitting, aperture photometry, and psf fitting  algorithms.
  Scale converts radial distance measurements in pixels to radial distance
  measurements in scale units. The DAOPHOT parameters cbox, maxshift, rclean
  and rclip in the CENTERPARS parameter set; annulus, dannulus, and rgrow in
  FITSKYPARS parameter set; apertures in the PHOTPARS parameter set; and psfrad,
  fitrad, sannulus, wsannulus, and matchrad in the DAOPARS parameter set are
  expressed in units of the scale. The scale parameter is useful in  cases where
  the observations are to be compared to published aperture photometry
  measurements in the literature.
  <P>
  The parameter <I>fwhmpsf</I> defines the full-width at half-maximum of the
  stellar point spread function. The DAOFIND task, the PHOT task centering
  algorithms "<TT>gauss</TT>" and "<TT>ofilt</TT>", and the PSF modeling task PSF all require
  an accurate estimate for this parameter.
  <P>
  By setting the <I>scale</I> and <I>fwhmpsf</I> appropriately the aperture
  sizes and radial distances may be  expressed in terms of the half-width
  at half-maximum of the stellar point spread function.  The way to do this
  is to define the scale parameter in units of the number of half-width at
  half-maximum per pixel, set the fwhmpsf parameter to 2.0, and then
  set the remaining scale dependent centering, sky fitting, aperture photometry,
  and psf fitting algorithm parameters in CENTERPARS, FITSKYPARS, PHOTPARS,
  and DAOPARS to appropriate values in units of the half-width at half-maximum
  of the point-spread function. Once an optimum set of algorithm parameters is
  chosen, the user need only alter the DATAPARS scale parameter before
  executing a DAOPHOT task on a new image.
  <P>
  If <I>emission</I> is "<TT>yes</TT>", the features to be measured are assumed to
  be above sky. By default the DAOPHOT package considers all features to be
  emission features. DAOPHOT users should leave this parameter set to "<TT>yes</TT>".
  Although the DAOFIND and PHOT tasks can detect and measure absorption features
  the PSF fitting tasks currently cannot.
  <P>
  The parameter <I>sigma</I> estimates the standard deviation of the sky
  background pixels. The star finding algorithm in DAOFIND uses sigma
  and the <I>findpars.threshold</I> parameter to define the stellar
  detection threshold in adu. The PHOT task centering algorithms use sigma,
  1) with the <I>centerpars.kclean</I> parameter to define deviant pixels
  if <I>centerpars.clean</I> is enabled; 2) to estimate the signal to
  noise ratio in the centering box; 3) and with the <I>centerpars.cthreshold</I>
  parameter to define a lower intensity limit for the pixels to be used
  for centering.  If sigma is undefined or &lt;= 0.0 1) no cleaning is performed
  regardless of the value of centerpars.clean; 2) the background noise in the
  centering box is assumed to be 0.0; and 3) default cutoff intensity is used
  for centering.
  <P>
  The <I>datamin</I> and <I>datamax</I> parameters define the good data range.
  If datamin or datamax are defined bad data is removed from the sky pixel
  distribution before the sky is fit, data containing bad pixels in the
  photometry apertures is flagged and the corresponding aperture photometry
  magnitudes are set to INDEF, and bad data removed from the PSF fitting
  aperture. DAOPHOT users should set datamin and datamax to appropriate values
  before running the DAOPHOT tasks.
  <P>
  DAOPHOT users must leave <I>noise</I> set to "<TT>poisson</TT>".  This model includes
  Poisson noise from the object and both Poisson and readout noise in the sky
  background.
  <P>
  The parameters <I>gain</I> and <I>epadu</I> define the image gain.
  The gain parameter specifies which keyword in the image header contains
  the gain value. If gain is undefined or not present in the image header
  the value of epadu is used.  Epadu must be in units of electrons per adu.
  DAOPHOT users should set either gain or epadu to a correct value before
  running any of the DAOPHOT package tasks to ensure that the aperture
  photometry magnitude error estimates, and the PSF fitting weights, chis, and
  magnitude error estimates are computed correctly.
  <P>
  The two parameters <I>ccdread</I> and <I>readnoise</I> define the image
  readout noise.  The ccdread parameter specifies which keyword in the
  image header contains the readout noise value. If ccdread is undefined or
  not present in the image header the value of readnoise is used.
  Readnoise is assumed to be in units of electrons.
  DAOPHOT users should set either ccdread or readnoise before running any
  DAOPHOT tasks to insure that the PSF fitting weights, chis, and magnitude
  error estimates are computed correctly.
  <P>
  The magnitudes computed by PHOT are normalized to an exposure time of 1 
  timeunit using the value of the exposure time in the image header parameter 
  <I>exposure</I> or <I>itime</I>. If exposure is undefined or not present
  in the image header a warning message is issued and the value of itime
  is used. The itime units are arbitrary but must be consistent for images
  analyzed together. As the magnitude scale in DAOPHOT is determined by the
  PHOT task setting either exposure or itime can save DAOPHOT users a lot
  of unnecessary zero point corrections in future analysis and calibration
  steps.
  <P>
  The parameters <I>airmass</I> and <I>xairmass</I> define the airmass
  of the observation. The airmass parameter specifies which keyword in the
  image header contains the airmass value. If airmass is undefined or
  not present in the image header the value of xairmass is used.
  The airmass values are not used in any DAOPHOT computations, however their
  presence in the DAOPHOT output files will simplify future reduction steps.
  <P>
  The parameters <I>filter</I> and <I>ifilter</I> define the filter
  of the observation. The filter parameter specifies which keyword in the
  image header contains the filter id. If filter is undefined or not present
  in the image header the value of ifilter is used. The filter id values are
  not used in any DAOPHOT computations, however their presence in the DAOPHOT
  output files can will simplify future reduction steps.
  <P>
  The parameters <I>obstime</I> and <I>otime</I> define the time
  of the observation (e.g. UT). The obstime parameter specifies which keyword
  in the image header contains the time stamp of the observation. If obstime is
  undefined or not present in the image header the value of otime is used.
  The time of observations values are not used in any DAOPHOT
  computations, however their presence in the DAOPHOT output files can
  greatly simplify future reduction steps.
  <P>
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. List the data dependent parameters.
  <P>
  <PRE>
  	da&gt; lpar datapars
  </PRE>
  <P>
  2. Edit the data dependent parameters.
  <P>
  <PRE>
  	da&gt; datapars
  </PRE>
  <P>
  3. Edit the data dependent parameters from within the PSF task.
  <P>
  <PRE>
      da&gt; epar psf
  <P>
  	... edit a few parameters
  <P>
  	... move to the datapars parameter and type :e
  <P>
  	... edit the datapars parameters and type :wq
  <P>
  	... finish editing the psf parameter and type :wq
  </PRE>
  <P>
  4. Save the current DATAPARS parameter set in a text file datnite1.par.
  This can also be done from inside a higher level task as in the previous
  example.
  <P>
  <PRE>
      da&gt; epar datapars
  <P>
  	... edit a few parameters
  <P>
  	... type ":w datnite1.par"  from within epar
  </PRE>
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
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  epar,lpar,daofind,phot,pstselect,psf,group,peak,nstar,allstar,substar,addstar
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>