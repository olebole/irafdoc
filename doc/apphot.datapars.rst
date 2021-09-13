.. _datapars:

datapars — Edit the data dependent parameters
=============================================

**Package: apphot**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  datapars -- edit the data dependent parameters
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  datapars
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>scale = 1.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='scale' Line='scale = 1.0'>
  <DD>The scale of the image in user units, e.g arcseconds per pixel.
  All APPHOT distance dependent parameters are assumed to be in units of scale.
  If scale = 1.0 these parameters are assumed to be in units of pixels.
  Most APPHOT users should leave scale set to 1.0 unless they intend to
  compare their aperture photometry results directly with data 
  in the literature.
  </DD>
  </DL>
  <DL>
  <DT><B>fwhmpsf = 2.5 (scale units)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fwhmpsf' Line='fwhmpsf = 2.5 (scale units)'>
  <DD>The full-width at half-maximum of the point spread function in scale units.
  The DAOFIND, FITPSF and WPHOT tasks and the "<TT>gauss</TT>" and "<TT>ofilter</TT>" centering
  algorithms depend on the value of fwhmpsf. APPHOT users can either determine
  a value for fwhmpsf using an external task such as IMEXAMINE, or make use of
  the interactive capabilities of the APPHOT tasks to set and store it.
  </DD>
  </DL>
  <DL>
  <DT><B>emission = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='emission' Line='emission = yes'>
  <DD>The features to be measured are above sky. By default the APPHOT package
  considers all features to be emission features. However all the package tasks
  measure absorption features if emission is set to no.
  </DD>
  </DL>
  <DL>
  <DT><B>sigma = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sigma' Line='sigma = INDEF'>
  <DD>The standard deviation of the sky pixels. The DAOFIND task and the "<TT>constant</TT>"
  sky fitting algorithm error estimate depend on the value of sigma. APPHOT
  users should set sigma to a value which is representative of the noise
  in the sky background.
  </DD>
  </DL>
  <DL>
  <DT><B>datamin = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='datamin' Line='datamin = INDEF'>
  <DD>The minimum good pixel value. Datamin defaults to -MAX_REAL, the minimum
  floating point number supported by the host computer.  APPHOT users should
  set this parameter if they wish to remove bad data from the sky pixel
  distribution before the sky is fit or if they wish to flag stars with
  bad data in the centering and / or photometry apertures.
  </DD>
  </DL>
  <DL>
  <DT><B>datamax = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='datamax' Line='datamax = INDEF'>
  <DD>The maximum good pixel value. Datamax defaults to MAX_REAL the maximum
  floating point number supported by the host computer.
  APPHOT users should set this parameter if they wish to flag
  saturated stars or stars with bad data in the centering and / or
  photometry apertures.
  </DD>
  </DL>
  <DL>
  <DT><B>noise = "<TT>poisson</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='noise' Line='noise = "poisson"'>
  <DD>The noise model used to estimate the uncertainties in the computed APPHOT
  magnitudes. The options are the following:
  <DL>
  <DT><B>poisson</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='poisson' Line='poisson'>
  <DD>Poisson statistics in the object and the sky background are used to estimate
  the error in the object measurement.  There are two components to the sky 
  noise measurement the sky noise in the object aperture and the mean error
  in the estimated sky value.
  </DD>
  </DL>
  <DL>
  <DT><B>constant</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='constant' Line='constant'>
  <DD>The standard deviation of the sky background is used to estimate the
  error in the object measurement.  There are two components to the error
  estimate the sky noise in the object aperture and the mean error in the
  estimated sky value.
  </DD>
  </DL>
  <P>
  Most APPHOT users should use the Poisson model appropriate for CCD detectors.
  APPHOT users should also be aware that one or other of the parameters
  gain or epadu must be set correctly in order to compute the magnitude
  errors correctly.
  </DD>
  </DL>
  <DL>
  <DT><B>ccdread = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ccdread' Line='ccdread = ""'>
  <DD>The image header keyword defining the readout noise parameter whose units are
  assumed to be electrons.
  </DD>
  </DL>
  <DL>
  <DT><B>gain = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='gain' Line='gain = ""'>
  <DD>The image header keyword defining the gain parameter whose units are assumed
  to be electrons per adu.
  </DD>
  </DL>
  <DL>
  <DT><B>readnoise = 0.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='readnoise' Line='readnoise = 0.0'>
  <DD>The readout noise of the image in electrons.  APPHOT users should set this
  parameter or the ccdread parameter to its correct value before running any
  of the APPHOT tasks.
  </DD>
  </DL>
  <DL>
  <DT><B>epadu = 1.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='epadu' Line='epadu = 1.0'>
  <DD>The gain in electrons per adu.  APPHOT users should set epadu or ain to its
  correct value before running any of the APPHOT tasks in order to insure that
  the magnitude error estimates are correct.
  </DD>
  </DL>
  <DL>
  <DT><B>exposure = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='exposure' Line='exposure = ""'>
  <DD>The image header exposure time keyword. The time units are arbitrary but
  must be consistent for any list of images whose magnitudes are to be compared.
  The computed magnitudes are normalized to 1 timeunit.  Setting the exposure
  parameter will greatly simplify  future reduction steps. The value of exposure
  is recorded in the APPHOT output file.
  </DD>
  </DL>
  <DL>
  <DT><B>airmass = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='airmass' Line='airmass = ""'>
  <DD>The image header airmass keyword.  The airmass parameter is not used
  directly by APPHOT but the airmass value is stored in the output file
  and its presence there will simplify future calibration steps.
  </DD>
  </DL>
  <DL>
  <DT><B>filter = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='filter' Line='filter = ""'>
  <DD>The image header filter id keyword.  The filter parameter is not used
  directly by APPHOT but the filter id is stored in the output file
  and its presence there will simplify future calibration steps.
  </DD>
  </DL>
  <DL>
  <DT><B>obstime = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='obstime' Line='obstime = ""'>
  <DD>The image header time of observation keyword. The obstime parameter is not used
  directly by APPHOT but the obstime value is stored in the output file
  and its presence there will simplify future calibration steps.
  </DD>
  </DL>
  <DL>
  <DT><B>itime = 1.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='itime' Line='itime = 1.0'>
  <DD>The exposure time for the image in arbitrary units. The APPHOT magnitudes are
  normalized to 1 timeunit  using the value of exposure in the image header
  if exposure is defined or the value of itime.
  </DD>
  </DL>
  <DL>
  <DT><B>xairmass = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xairmass' Line='xairmass = INDEF'>
  <DD>The airmass value.  The airmass is read from the image header if airmass
  is defined  or from xairmass. The airmass value is stored in the APPHOT
  output files.
  </DD>
  </DL>
  <DL>
  <DT><B>ifilter = "<TT>INDEF</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ifilter' Line='ifilter = "INDEF"'>
  <DD>The filter id string. The filter id is read from the image header if filter
  is defined otherwise from ifilter. The filter id is stored in the APPHOT
  output files.
  </DD>
  </DL>
  <DL>
  <DT><B>otime = "<TT>INDEF</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='otime' Line='otime = "INDEF"'>
  <DD>The value of the time of observation. The time of observation is read from
  the image header if obstime is defined otherwise from otime. The time of
  observation is stored in the APPHOT output files.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>Datapars</I> sets the image data dependent parameters. These parameters are
  functions, of the instrument optics, the noise characteristics and range of
  linearity of the detector, and the observing conditions. Many of the
  centering, sky fitting, and photometry algorithm parameters in the CENTERPARS,
  FITSKYPARS and PHOTPARS  parameter sets scale with the data dependent
  parameters.
  <P>
  The parameter <I>scale</I> sets the scale of the apertures used by the
  centering, sky fitting and photometry algorithms.  Scale converts radial
  distance measurements in pixel units to radial distance measurements in
  scale units. The APPHOT parameters, cbox, maxshift, rclean and rclip
  in the CENTERPARS parameter set; annulus, dannulus, and rgrow in
  the FITSKYPARS parameter set; and apertures in the PHOTPARS
  parameter set are expressed in units of the scale. The scale parameter is
  useful in cases where the observations are to be compared to published
  aperture photometry measurements in the literature.
  <P>
  The parameter <I>fwhmpsf</I> defines the full-width at half-maximum of the
  stellar point spread function.  Most APPHOT tasks and algorithms do not 
  require this parameter. The exceptions are the DAOFIND task, the centering
  algorithms "<TT>gauss</TT>" and "<TT>ofilter</TT>", the FITPSF task, and the WPHOT task.
  <P>
  By setting the <I>scale</I> and <I>fwhmpsf</I> appropriately the aperture
  sizes and radial distances may be  expressed in terms of the half-width
  at half-maximum of the stellar point spread function.  The way to do this
  is to define the scale parameter in units of the number of half-width at
  half-maximum per pixel, set the fwhmpsf parameter to 2.0, and then
  set the remaining scale dependent centering, sky fitting and photometry
  algorithm parameters in CENTERPARS, FITSKYPARS and PHOTPARS to
  appropriate values in units of the half-width at half-maximum of the
  point-spread function. Once an optimum set of algorithm parameters is
  chosen, the user need only alter the DATAPARS scale parameter before
  executing an APPHOT task on a new image.
  <P>
  If  <I>emission</I> is "<TT>yes</TT>", the features to be measured are assumed to be
  above sky. By default the APPHOT package considers all measurements to
  be measurements of emission features. In most cases APPHOT users should
  leave emission set to "<TT>yes</TT>".
  <P>
  The parameter <I>sigma</I> estimates the standard deviation of the sky
  background pixels. The star finding algorithm in DAOFIND uses sigma
  and the <I>findpars.threshold</I> parameter to define the stellar
  detection threshold in adu. The centering algorithms uses sigma,
  1) with the <I>centerpars.kclean</I> parameter to define deviant pixels
  if <I>centerpars.clean</I> is enabled; 2) to estimate the signal to
  noise ratio in the centering box; 3) and with the <I>centerpars.cthreshold</I>
  parameter to define the lower intensity limit for the pixels to be used
  for centering.  If sigma is undefined or &lt;= 0.0 1) no cleaning is performed
  regardless of the value of centerpars.clean; 2) the background
  noise in the centering box is assumed to be 0; and 3) default cutoff
  intensity intensity is used for centering. 
  <P>
  The <I>datamin</I> and <I>datamax</I> parameters define the  good data range.
  If datamin or datamax are defined bad data is removed from the sky pixel
  distribution before the sky is fit, data containing bad pixels in the 
  photometry apertures is flagged, and the corresponding aperture photometry
  magnitudes are set to INDEF. APPHOT users should set datamin and datamax
  to appropriate values before running the APPHOT tasks.
  <P>
  Two noise models are available "<TT>constant</TT>" and "<TT>poisson</TT>". If <I>noise</I> =
  constant, the total noise is assumed to be due to noise in the sky background
  alone. If <I>noise</I> = poisson, the total noise includes Poisson noise from
  the object and the sky noise. 
  <P>
  The parameters <I>gain</I> and <I>epadu</I> define the image gain.
  The gain parameter specifies which keyword in the image header contains
  the gain value. If gain is undefined or not present in the image header
  the value of epadu is used.  Epadu must be in units of electrons per adu.
  APPHOT users should set either gain or epadu before running any 
  APPHOT tasks to insure the magnitude error computations are correct.
  <P>
  The two parameters <I>ccdread</I> and <I>readnoise</I> define the image
  readout noise.  The ccdread parameter specifies which keyword in the
  image header contains the readout noise value. If ccdread is undefined or
  not present in the image header the value of readnoise is used.
  Readnoise is assumed to be in units of electrons.
  APPHOT users should set either ccdread or readnoise before running any 
  APPHOT tasks to insure the magnitude error computations are correct.
  <P>
  The magnitudes are normalized to an exposure time of 1 timeunit using
  the value of the exposure time in the image header parameter <I>exposure</I>
  or <I>itime</I>. If exposure is undefined or not present in the image header
  the value of itime is used. Itime can be in arbitrary units.
  Setting either exposure or itime will simplify future analysis steps.
  <P>
  The parameters <I>airmass</I> and <I>xairmass</I> define the airmass
  of the observation. The airmass parameter specifies which keyword in the
  image header contains the airmass value. If airmass is undefined or
  not present in the image header the value of xairmass is used.
  The airmass values are not used in any APPHOT computations, however their
  presence in the APPHOT output files will simplify future reduction steps. 
  <P>
  The parameters <I>filter</I> and <I>ifilter</I> define the filter
  of the observation. The filter parameter specifies which keyword in the
  image header contains the filter id. If filter is undefined or not present
  in the image header the value of ifilter is used. The filter id values are
  not used in any APPHOT computations, however their presence in the APPHOT
  output files can will simplify future reduction steps. 
  <P>
  The parameters <I>obstime</I> and <I>otime</I> define the time 
  of the observation (e.g. UT). The obstime parameter specifies which keyword
  in the image header contains the time stamp of the observation. If obstime is
  undefined or not present in the image header the value of otime is used.
  The time of observations values are not used in any APPHOT 
  computations, however their presence in the APPHOT output files can
  greatly simplify future reduction steps. 
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. List the data dependent parameters.
  <P>
  <PRE>
  	ap&gt; lpar datapars
  </PRE>
  <P>
  2. Edit the data dependent parameters.
  <P>
  <PRE>
  	ap&gt; datapars
  </PRE>
  <P>
  3. Edit the DATAPARS parameters from within the PHOT task.
  <P>
  <PRE>
      da&gt; epar phot
  <P>
  	... edit a few parameters
  <P>
  	... move to the datapars parameter and type :e
  <P>
  	... edit the datapars parameters and type :wq
  <P>
  	... finish editing the phot parameters and type :wq
  </PRE>
  <P>
  4. Save the current DATAPARS parameter set in a text file datnite1.par.
  This can also be done from inside a higher level task as in the
  previous example.
  <P>
  <PRE>
      da&gt; datapars
  <P>
  	... edit a few parameters
  <P>
  	... type ":w datnite1.par"  from within epar
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  <P>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  epar,lpar,daofind,center,fitsky,phot,wphot,polyphot,radprof,fitpsf
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
