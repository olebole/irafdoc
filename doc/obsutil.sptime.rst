.. _sptime:

sptime — Spectroscopic exposure time calculator
===============================================

**Package: obsutil**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  sptime -- spectroscopic exposure time calculator
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  sptime
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  The parameters in this task have certain common features.
  <DL>
  <DT><B>(1)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(1)'>
  <DD>All parameters, except <I>spectrograph</I> and <I>search</I>, may be
  specified as spectrograph table parameters of the same name.  Some
  parameters may also be specified in other tables.  The tables in which the
  paramters may be specified are shown in brackets.  Table values are used
  only if a string parameter is "<TT></TT>" or a numeric parameter is INDEF.
  Therefore parameter set values override values in the tables.  To override
  a table specified in the spectrograph file by no file the special value
  "<TT>none</TT>" is used.  This task also uses default values, shown below in
  parenthesis, for parameters that have no value specified either in the
  parameter set or in a table.
  </DD>
  </DL>
  <DL>
  <DT><B>(2)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(2)'>
  <DD>Parameters that specify a table take the value of a file or a numeric
  constant.  A constant is like a table with the same values for all value
  of the independent variable(s).
  </DD>
  </DL>
  <DL>
  <DT><B>(3)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(3)'>
  <DD>Tables which are specified as filenames are sought first in the current
  working directory, then in one of the directories given by the
  <I>search</I> parameter, and finally in the package library directory
  sptimelib$.
  </DD>
  </DL>
  <P>
  <P>
  <DL>
  <DT><B>time = INDEF (INDEF) [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='time' Line='time = INDEF (INDEF) [spectrograph]'>
  <DD>Total exposure time in seconds.  This time may be divided into shorter
  individual exposure times as defined by the <I>maxexp</I> parameter.  If
  the value is INDEF then the exposure time needed to achieve the
  signal-to-noise per pixel specified by the <I>sn</I> parameter is computed.
  </DD>
  </DL>
  <DL>
  <DT><B>sn = 25. (25.) [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sn' Line='sn = 25. (25.) [spectrograph]'>
  <DD>Desired signal-to-noise per pixel at the central wavelength if the
  exposure <I>time</I> parameter is not specified.
  </DD>
  </DL>
  <P>
  <P>
  The following parameters define the source and sky/atmosphere background
  spectra.
  <DL>
  <DT><B>spectrum = "<TT>blackbody</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='spectrum' Line='spectrum = "blackbody"'>
  <DD>Source spectrum.  This may be a table or one of the following  special words:
  <DL>
  <DT><B>blackbody</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='blackbody' Line='blackbody'>
  <DD>Blackbody spectrum with temperature given by the <I>temperature</I>
  parameter.
  </DD>
  </DL>
  <DL>
  <DT><B>flambda_power</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='flambda_power' Line='flambda_power'>
  <DD>Power law in f(lambda) with index given by the <I>index</I> parameter;
  f(lambda) proportional to lambda^(index).
  </DD>
  </DL>
  <DL>
  <DT><B>fnu_power</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='fnu_power' Line='fnu_power'>
  <DD>Power law in f(nu) with index given by the <I>index</I> parameter;
  f(nu) proportional to nu^(index).
  </DD>
  </DL>
  <P>
  The table is a two column text file of wavelength in Angstroms and flux in
  ergs/s/cm^2/A.
  </DD>
  </DL>
  <DL>
  <DT><B>spectitle = "<TT></TT>" [spectrum|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='spectitle' Line='spectitle = "" [spectrum|spectrograph]'>
  <DD>Spectrum title.
  </DD>
  </DL>
  <DL>
  <DT><B>E = 0. (0.) [spectrum|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='E' Line='E = 0. (0.) [spectrum|spectrograph]'>
  <DD>The E(B-V) color excess to apply a reddening to the source spectrum.  The
  reddening maintains the same table or reference flux at the reference
  wavelength.  A value of zero corresponds to no reddening.
  </DD>
  </DL>
  <DL>
  <DT><B>R = 3.1 (3.1) [spectrum|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='R' Line='R = 3.1 (3.1) [spectrum|spectrograph]'>
  <DD>The R(V) = A(V)/E(B-V) for the extinction law.  The extinction law is that
  of Cardelli, Clayton, and Mathis, <B>ApJ 345:245</B>, 1989.  The default
  R(V) is typical of the interstellar medium.
  </DD>
  </DL>
  <DL>
  <DT><B>sky = "<TT></TT>" ("<TT>none</TT>") [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sky' Line='sky = "" ("none") [spectrograph]'>
  <DD>Sky or background table.  The table is a two or three column text file
  consisting of wavelength in Angstroms, optional moon phase between 0 (new
  moon) and 14 (full moon), and flux in ergs/s/cm^2/A/arcsec^2.
  </DD>
  </DL>
  <DL>
  <DT><B>skytitle = "<TT></TT>" [sky|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='skytitle' Line='skytitle = "" [sky|spectrograph]'>
  <DD>Sky title.
  </DD>
  </DL>
  <DL>
  <DT><B>extinction = "<TT></TT>" ("<TT>none</TT>") [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='extinction' Line='extinction = "" ("none") [spectrograph]'>
  <DD>Extinction table.  The table is a two column text file consisting of
  wavelength in Angstroms and extinction in magnitudes per airmass.
  </DD>
  </DL>
  <DL>
  <DT><B>exttitle = "<TT></TT>" [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='exttitle' Line='exttitle = "" [spectrograph]'>
  <DD>Extinction title.
  </DD>
  </DL>
  <P>
  <P>
  The following parameters are used with the source spectrum is specified
  by the special functions.
  <DL>
  <DT><B>refwave = INDEF (INDEF) [spectrum|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='refwave' Line='refwave = INDEF (INDEF) [spectrum|spectrograph]'>
  <DD>Reference wavelength, in units given by the <I>units</I> parameter, defining
  the flux of the source.  This is also used as the wavelength where
  reddening does not change the spectrum flux.  A value of INDEF uses the
  observation central wavelength.
  </DD>
  </DL>
  <DL>
  <DT><B>refflux = 10. (10.) [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='refflux' Line='refflux = 10. (10.) [spectrograph]'>
  <DD>Reference source flux or magnitude at the reference wavelength for the
  model spectral distributions.  The units are specified by the funits parameter.
  </DD>
  </DL>
  <DL>
  <DT><B>funits = "<TT>AB</TT>" ("<TT>AB</TT>") [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='funits' Line='funits = "AB" ("AB") [spectrograph]'>
  <DD>Flux units for the reference flux.  The values are "<TT>AB</TT>" for monochromatic
  magnitude, "<TT>F_lambda</TT>" for ergs/s/cm^2/A, "<TT>F_nu</TT>" for ergs/s/cm^2/Hz,
  and standard bandpasses of U, B, V, R, I, J, H, Ks, K, L, L' and M.
  </DD>
  </DL>
  <DL>
  <DT><B>temperature = 6000. (6000.) [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='temperature' Line='temperature = 6000. (6000.) [spectrograph]'>
  <DD>Blackbody temperature for a blackbody source spectrum in degrees Kelvin.
  </DD>
  </DL>
  <DL>
  <DT><B>index = 0. (0.) [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='index' Line='index = 0. (0.) [spectrograph]'>
  <DD>Power law index for the power law source spectrum.
  </DD>
  </DL>
  <P>
  <P>
  The following parameters are observational parameters describing either
  the observing conditions or spectrograph setup.
  <DL>
  <DT><B>seeing = 1. (1.) [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='seeing' Line='seeing = 1. (1.) [spectrograph]'>
  <DD>The full width at half maximum (FWHM) of a point source in arc seconds.
  </DD>
  </DL>
  <DL>
  <DT><B>airmass = 1. (1.) [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='airmass' Line='airmass = 1. (1.) [spectrograph]'>
  <DD>The airmass of the observation.  This is only used if an extinction table
  is specified.
  </DD>
  </DL>
  <DL>
  <DT><B>phase = 0. (0.) [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='phase' Line='phase = 0. (0.) [spectrograph]'>
  <DD>The moon phase running from 0 for new moon to 14 for full moon.  This is
  used if the sky spectrum is given as a function of the moon phase.
  </DD>
  </DL>
  <DL>
  <DT><B>thermal = 0. (0.) [telescope|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='thermal' Line='thermal = 0. (0.) [telescope|spectrograph]'>
  <DD>Temperature in degress Kelvin for the thermal background of the telescope
  and spectrograph.  If greater than zero a blackbody surface brightness
  background is computed and multiplied by an emissivity specified by
  the <I>emissivity</I> table.
  </DD>
  </DL>
  <DL>
  <DT><B>wave = INDEF (INDEF) [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wave' Line='wave = INDEF (INDEF) [spectrograph]'>
  <DD>Central wavelength of observation in units given by the <I>units</I>
  parameter.  If the value is INDEF it is determined from the efficiency peak
  of the disperser.
  </DD>
  </DL>
  <DL>
  <DT><B>order = INDEF (INDEF) [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='order' Line='order = INDEF (INDEF) [spectrograph]'>
  <DD>Order for grating or grism dispersers.  If the value is INDEF it is
  determined from the order nearest the desired central wavelength.  If both
  the order and central wavelength are undefined the first order is used.
  </DD>
  </DL>
  <DL>
  <DT><B>xorder = INDEF (INDEF) [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xorder' Line='xorder = INDEF (INDEF) [spectrograph]'>
  <DD>Order for grating or grism cross dispersers.  If the value is INDEF it
  is determined from the order nearest the desired central wavelength.  If
  both the order and central wavelength are undefined the first order is
  used.
  </DD>
  </DL>
  <DL>
  <DT><B>width = INDEF (-2.) [aperture|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='width' Line='width = INDEF (-2.) [aperture|spectrograph]'>
  <DD>The aperture width (dispersion direction) for rectangular apertures
  such as slits.  Values may be positive to specify in arc seconds or
  negative to specify in projected pixels on the detector.
  </DD>
  </DL>
  <DL>
  <DT><B>length = INDEF (-100.) [aperture|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='length' Line='length = INDEF (-100.) [aperture|spectrograph]'>
  <DD>The aperture length (cross dispersion direction) for rectangular
  apertures such as slits.  Values may be positive to specify in arc seconds
  or negative to specify in projected pixels on the detector.
  </DD>
  </DL>
  <DL>
  <DT><B>diameter = INDEF (-2.) [fiber|aperture|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='diameter' Line='diameter = INDEF (-2.) [fiber|aperture|spectrograph]'>
  <DD>The aperture diameter for circular apertures.  Values
  may be positive to specify in arc seconds or negative to specify in
  projected pixels on the detector.  If it is found in the fiber table,
  positive values are treated as mm at the focal plane instead of arc seconds.
  </DD>
  </DL>
  <DL>
  <DT><B>xbin = 1 (1) [detector|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xbin' Line='xbin = 1 (1) [detector|spectrograph]'>
  <DD>Detector binning along the dispersion direction.
  </DD>
  </DL>
  <DL>
  <DT><B>ybin = 1 (1) [detector|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ybin' Line='ybin = 1 (1) [detector|spectrograph]'>
  <DD>Detector binning along the spatial direction.
  </DD>
  </DL>
  <P>
  <P>
  The following parameters a miscellaneous parameters for the task.
  <DL>
  <DT><B>search = "<TT>spectimedb$</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='search' Line='search = "spectimedb$"'>
  <DD>List of directories to search for the various table files.  The current
  direction is always searched first and the directory sptimelib$ is searched
  last so it is not necessary to include these directories.  The list may be
  a comma delimited list of directories, an @file, or a template.
  </DD>
  </DL>
  <DL>
  <DT><B>minexp = 0.01 (0.01) [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='minexp' Line='minexp = 0.01 (0.01) [spectrograph]'>
  <DD>Minimumm time in seconds per individual exposure time.  This only applies
  when <I>time</I> is INDEF.  Adjustment of the exposure time for saturation
  will not allow the exposure time to fall below this value.
  </DD>
  </DL>
  <DL>
  <DT><B>maxexp = 3600. (3600.) [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maxexp' Line='maxexp = 3600. (3600.) [spectrograph]'>
  <DD>Maximum time in seconds per individual exposure.  The minimum exposure time
  has precedence over this value.  If the total exposure time exceeds this
  amount by more than 1% then the total exposure time will be divided up into
  the fewest individual exposures with equal exposure time that are less than
  this amount.  Note that by making the minimum and maximum times the same a
  fixed integration time can be defined.
  </DD>
  </DL>
  <DL>
  <DT><B>units = "<TT>Angstroms</TT>" ("<TT>Angstroms</TT>") [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='units' Line='units = "Angstroms" ("Angstroms") [spectrograph]'>
  <DD>Dispersion units for input and output dispersion coordinates.  The
  units syntax is described in the UNITS section.  The most common units
  are "<TT>Angstroms</TT>", "<TT>nm</TT>", "<TT>micron</TT>", and "<TT>wn</TT>".  Note that this does not
  apply to the dispersion units in the tables which are always in Angstroms.
  </DD>
  </DL>
  <DL>
  <DT><B>skysub = "<TT></TT>" (default based on context) [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='skysub' Line='skysub = "" (default based on context) [spectrograph]'>
  <DD>Type of sky and background subtraction.  The values are "<TT>none</TT>" for no
  background subtraction, "<TT>longslit</TT>" for subtraction using pixels in the
  aperture, "<TT>multiap</TT>" for background determined from a number of other
  apertures, and "<TT>shuffle</TT>" for shuffled observations.  The multiap case is
  typical for fiber spectrographs.  For shuffle the duty cycle is 50% and the
  exposure times are the sum of both sky and object.  If no sky or thermal
  background is specified then the default is "<TT>none</TT>".  If a fiber table or
  circular aperture is specified the default is "<TT>multiap</TT>" otherwise the
  default is "<TT>longslit</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>nskyaps = 10  (10) [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nskyaps' Line='nskyaps = 10  (10) [spectrograph]'>
  <DD>Number of sky apertures when using "<TT>multiap</TT>" sky subtraction.
  </DD>
  </DL>
  <DL>
  <DT><B>subpixels = 1 (1) [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='subpixels' Line='subpixels = 1 (1) [spectrograph]'>
  <DD>Number of subpixels within each computed pixel.
  The dispersion pixel width is divided into this number of equal
  width subpixels.  The flux at the dispersions represented by the subpixels
  are computed and then summed to form the full pixel flux.  This option is used
  when there is structure in the tables, such as the sky and filter tables to
  simulate instrumental masking of sky lines, which is finer than a pixel
  dispersion width.
  </DD>
  </DL>
  <DL>
  <DT><B>sensfunc = "<TT></TT>" [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sensfunc' Line='sensfunc = "" [spectrograph]'>
  <DD>Sensitivity function table.  This is a two column text file consisting
  of wavelength in Angstroms and sensitivity defined as
  2.5*(log(countrate)-log(flambda)),
  where countrate is the count rate (without extinction) in counts/s/A
  and flambda is the source flux in ergs/s/cm^2/A.  This table is used
  to compute an efficiency correction given a measurement of the
  sensitivity function from standard stars for the instrument.
  </DD>
  </DL>
  <P>
  <P>
  The following parameters control the output of the task.  The task
  always prints a result page at the central wavelength but additional
  graphical and text output may be produced at a set of equally spaced
  points across the size of the detector.
  <DL>
  <DT><B>output = "<TT>object</TT>" ("<TT></TT>") [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output = "object" ("") [spectrograph]'>
  <DD>List of quantities to output as graphs and/or in a text file.  These are
  given as a function of dispersion (as specified by units parameters)
  sampled across the dispersion coverage of the detector.  The choices are:
  <DL>
  <DT><B>counts</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='counts' Line='counts'>
  <DD>Object and background counts per individual exposure.
  </DD>
  </DL>
  <DL>
  <DT><B>snr</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='snr' Line='snr'>
  <DD>Signal-to-noise ratio per pixel per individual exposure.
  </DD>
  </DL>
  <DL>
  <DT><B>object</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='object' Line='object'>
  <DD>Object counts per individual exposure.  This includes contribution
  from other orders if there is no cross dispersion and the blocking
  filters do not completely exclude other orders.
  </DD>
  </DL>
  <DL>
  <DT><B>rate</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='rate' Line='rate'>
  <DD>Photons/second/A per individual exposure for the object and background.
  </DD>
  </DL>
  <DL>
  <DT><B>atmosphere</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='atmosphere' Line='atmosphere'>
  <DD>Percent transmission of the atmosphere.
  </DD>
  </DL>
  <DL>
  <DT><B>telescope</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='telescope' Line='telescope'>
  <DD>Percent transmission of the telescope.
  </DD>
  </DL>
  <DL>
  <DT><B>adc</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='adc' Line='adc'>
  <DD>Percent transmission of the ADC if one is used.
  </DD>
  </DL>
  <DL>
  <DT><B>aperture</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='aperture' Line='aperture'>
  <DD>Percent transmission of the aperture.
  </DD>
  </DL>
  <DL>
  <DT><B>fiber</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='fiber' Line='fiber'>
  <DD>Percent transmission of the fiber if one is used.
  </DD>
  </DL>
  <DL>
  <DT><B>filter</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='filter' Line='filter'>
  <DD>Percent transmission of the first filter if one is used.
  </DD>
  </DL>
  <DL>
  <DT><B>filter2</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='filter2' Line='filter2'>
  <DD>Percent transmission of the second filter if one is used.
  </DD>
  </DL>
  <DL>
  <DT><B>collimator</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='collimator' Line='collimator'>
  <DD>Percent transmission of the collimator.
  </DD>
  </DL>
  <DL>
  <DT><B>disperser</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='disperser' Line='disperser'>
  <DD>Percent efficiency of the disperser.
  </DD>
  </DL>
  <DL>
  <DT><B>xdisperser</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='xdisperser' Line='xdisperser'>
  <DD>Percent efficiency of the cross disperser if one is used.
  </DD>
  </DL>
  <DL>
  <DT><B>corrector</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='corrector' Line='corrector'>
  <DD>Percent transmission of the corrector if one is used.
  </DD>
  </DL>
  <DL>
  <DT><B>camera</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='camera' Line='camera'>
  <DD>Percent transmission of the camera.
  </DD>
  </DL>
  <DL>
  <DT><B>detector</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='detector' Line='detector'>
  <DD>Percent DQE of the detector.
  </DD>
  </DL>
  <DL>
  <DT><B>spectrograph</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='spectrograph' Line='spectrograph'>
  <DD>Percent transmission of the spectrograph if a transmission
  function is defined.
  </DD>
  </DL>
  <DL>
  <DT><B>emissivity</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='emissivity' Line='emissivity'>
  <DD>Emissivity of the telescope/spectrograph if an emissivity function
  is defined.
  </DD>
  </DL>
  <DL>
  <DT><B>thruput</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='thruput' Line='thruput'>
  <DD>Percent system thruput from telescope to detected photons.
  </DD>
  </DL>
  <DL>
  <DT><B>sensfunc</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='sensfunc' Line='sensfunc'>
  <DD>Sensitivity function values given as 2.5*(log(countrate)-log(flambda)),
  where countrate is the count rate (without extinction) in counts/s/A
  and flambda is the source flux in ergs/s/cm^2/A.
  </DD>
  </DL>
  <DL>
  <DT><B>correction</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='correction' Line='correction'>
  <DD>Multiplicative correction factor needed to convert the computed
  count rate to that given by an input sensitivity function.
  </DD>
  </DL>
  <DL>
  <DT><B>ALL  </B></DT>
  <! Sec='PARAMETERS' Level=1 Label='ALL' Line='ALL  '>
  <DD>All of the above.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>nw = 101 (101) [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nw' Line='nw = 101 (101) [spectrograph]'>
  <DD>Number of dispersion points to use in the output graphs and text
  file.  Note that this is generally less than the number of pixels in
  the detector for execution speed.
  </DD>
  </DL>
  <DL>
  <DT><B>list = "<TT></TT>" [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='list' Line='list = "" [spectrograph]'>
  <DD>Filename for list output of the selected quantities.  The output
  will be appended if the file already exists.
  </DD>
  </DL>
  <DL>
  <DT><B>graphics = "<TT>stdgraph</TT>" ("<TT>stdgraph</TT>") [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = "stdgraph" ("stdgraph") [spectrograph]'>
  <DD>Graphics output device for graphs of the output quantities.
  </DD>
  </DL>
  <DL>
  <DT><B>interactive = "<TT>yes</TT>" ("<TT>yes</TT>") [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = "yes" ("yes") [spectrograph]'>
  <DD>Interactive pause after each graph?  If "<TT>yes</TT>" then cursor input is
  enabled after each graph otherwise all the graphs will be drawn without
  pause.  When viewing the graphs interactively this should be "<TT>yes</TT>" otherwise
  the graphs will flash by rapidly leaving the last graph on the screen.
  When outputing only one graph or when redirecting the graphs to a
  printer or file then setting this parameter to "<TT>no</TT>" is suggested.
  </DD>
  </DL>
  <P>
  The last parameter is a "<TT>parameter set</TT>" ("<TT>pset</TT>") containing all the
  spectrograph parameters.
  <DL>
  <DT><B>specpars = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='specpars' Line='specpars = ""'>
  <DD>Spectrograph parameter set.  If "<TT></TT>" then the default pset <B>specpars</B>
  is used otherwise the named pset is used.
  </DD>
  </DL>
  <P>
  <P>
  <P>
  SPECPARS PARAMETERS
  <DL>
  <DT><B>spectrograph = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='spectrograph' Line='spectrograph = ""'>
  <DD>Spectrograph efficiency table.  This text file may contain parameters and an
  efficiency table.  The table consists of two columns containing
  wavelengths and efficiencies.  The efficiencies are for all elements
  which are not accounted for by other tables.
  </DD>
  </DL>
  <DL>
  <DT><B>title = "<TT></TT>" [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='title' Line='title = "" [spectrograph]'>
  <DD>Title for the spectrograph.
  </DD>
  </DL>
  <DL>
  <DT><B>apmagdisp = INDEF (1.), apmagxdisp = INDEF (1.) [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='apmagdisp' Line='apmagdisp = INDEF (1.), apmagxdisp = INDEF (1.) [spectrograph]'>
  <DD>Magnification between the entrance aperture and the detector along and
  across the dispersion direction.  This describes any magnification (or
  demagnification) in the spectrograph other than that produced by the ratio
  of the collimator and camera focal lengths and anamorphic magnification
  from the disperser.  The may consist of actual magnification optics or
  projection effects such as tilted aperture plates (when the aperture size
  is specified in the untilted plate).
  </DD>
  </DL>
  <DL>
  <DT><B>inoutangle = INDEF (INDEF) [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='inoutangle' Line='inoutangle = INDEF (INDEF) [spectrograph]'>
  <DD>Incident to diffracted grating angle in degrees for grating dispersers.
  For typical spectrographs which are not cross dispersed this is the
  collimator to camera angle.  If the value is INDEF derived from the grating
  parameters.
  </DD>
  </DL>
  <DL>
  <DT><B>xinoutangle = INDEF (INDEF) [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xinoutangle' Line='xinoutangle = INDEF (INDEF) [spectrograph]'>
  <DD>Incident to diffracted grating angle in degrees for grating cross
  dispersers.  If the value is INDEF it is derived from the grating
  parameters.
  </DD>
  </DL>
  <P>
  <P>
  <DL>
  <DT><B>telescope = "<TT></TT>" [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='telescope' Line='telescope = "" [spectrograph]'>
  <DD>Telescope efficiency table as a function of wavelength.  
  </DD>
  </DL>
  <DL>
  <DT><B>teltitle = "<TT></TT>" [telescope|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='teltitle' Line='teltitle = "" [telescope|spectrograph]'>
  <DD>Telescope title.
  </DD>
  </DL>
  <DL>
  <DT><B>area = INDEF (1.) [telescope|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='area' Line='area = INDEF (1.) [telescope|spectrograph]'>
  <DD>Effective collecting area of the telescope in m^2.  The effective area
  includes reductions in the primary area due to obstructions.
  </DD>
  </DL>
  <DL>
  <DT><B>scale = INDEF (10.) [telescope|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='scale' Line='scale = INDEF (10.) [telescope|spectrograph]'>
  <DD>Telescope plate scale, in arcsec/mm, at the entrance aperture of the
  spectrograph.
  </DD>
  </DL>
  <DL>
  <DT><B>emissivity = "<TT></TT>" [telescope|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='emissivity' Line='emissivity = "" [telescope|spectrograph]'>
  <DD>Emissivity table.  The emissivity is for all elements in the telescope
  and spectrograph.  If an emissivity is specified and an the <I>thermal</I>
  temperature parameter is greater than zero then a thermal background
  is added to the calculation.
  </DD>
  </DL>
  <DL>
  <DT><B>emistitle = "<TT></TT>" [emissivity|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='emistitle' Line='emistitle = "" [emissivity|spectrograph]'>
  <DD>Title for the emissivity table used.
  </DD>
  </DL>
  <P>
  <P>
  <DL>
  <DT><B>corrector = "<TT></TT>" [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='corrector' Line='corrector = "" [spectrograph]'>
  <DD>Efficiency table for one or more correctors.
  </DD>
  </DL>
  <DL>
  <DT><B>cortitle = "<TT></TT>" [corrector|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cortitle' Line='cortitle = "" [corrector|spectrograph]'>
  <DD>Title for corrector table used.
  </DD>
  </DL>
  <DL>
  <DT><B>adc = "<TT></TT>" [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='adc' Line='adc = "" [spectrograph]'>
  <DD>Efficiency table for atmospheric dispersion compensator.
  </DD>
  </DL>
  <DL>
  <DT><B>adctitle = "<TT></TT>" [adc|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='adctitle' Line='adctitle = "" [adc|spectrograph]'>
  <DD>Title for ADC table used.
  </DD>
  </DL>
  <P>
  <P>
  <DL>
  <DT><B>disperser = "<TT></TT>" [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='disperser' Line='disperser = "" [spectrograph]'>
  <DD>Disperser table.  If this file contains an efficiency table it applies
  only to first order.  An alternate first order table and tables for
  other orders are given by table parameters "<TT>effN</TT>", where N is the order.
  </DD>
  </DL>
  <DL>
  <DT><B>disptitle = "<TT></TT>" [disperser|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='disptitle' Line='disptitle = "" [disperser|spectrograph]'>
  <DD>Title for disperser.
  </DD>
  </DL>
  <DL>
  <DT><B>disptype = "<TT></TT>" ("<TT>grating</TT>") [disperser|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='disptype' Line='disptype = "" ("grating") [disperser|spectrograph]'>
  <DD>Type of disperser element.  The chocies are "<TT>grating</TT>", "<TT>grism</TT>", or "<TT>generic</TT>".
  The generic setting will simply use the desired central wavelength and
  dispersion without a grating or grism model.  One effect of this is that
  the mapping between detector pixel and wavelength is linear; i.e. a constant
  dispersion per pixel.
  </DD>
  </DL>
  <DL>
  <DT><B>gmm = INDEF (300.) [disperser|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='gmm' Line='gmm = INDEF (300.) [disperser|spectrograph]'>
  <DD>Ruling in lines per mm.  If not specified it will be derived from the
  other disperser parameters.  If there is not enough information to
  derive the ruling then an ultimate default of 300 lines/mm is used.
  </DD>
  </DL>
  <DL>
  <DT><B>blaze = INDEF (6.) [disperser|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='blaze' Line='blaze = INDEF (6.) [disperser|spectrograph]'>
  <DD>Blaze (grating) or prism (grism) angle in degrees.  If not specified it
  will be derived from the other disperser parameters.  If there is not
  enough information to derive the angle then an ultimate default of 6
  degrees is used.
  </DD>
  </DL>
  <DL>
  <DT><B>oref = INDEF (1) [disperser|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='oref' Line='oref = INDEF (1) [disperser|spectrograph]'>
  <DD>When a central (blaze) wavelength is specified this parameter indicates
  which order it is for.
  </DD>
  </DL>
  <DL>
  <DT><B>wavelength = INDEF (INDEF) [disperser|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wavelength' Line='wavelength = INDEF (INDEF) [disperser|spectrograph]'>
  <DD>Central (blaze) wavelength in Angstroms for the reference order.  This
  parameter only applies to gratings.  If it is not specified it will
  be derived from the other disperser parameters.
  </DD>
  </DL>
  <DL>
  <DT><B>dispersion = INDEF (INDEF) [disperser|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dispersion' Line='dispersion = INDEF (INDEF) [disperser|spectrograph]'>
  <DD>Central dispersion in A/mm for the reference order.  This parameter only
  applies to gratings.  If it is not specified it will be derived from the
  other disperser parameters.
  </DD>
  </DL>
  <DL>
  <DT><B>indexref = INDEF (INDEF) [disperser|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='indexref' Line='indexref = INDEF (INDEF) [disperser|spectrograph]'>
  <DD>Grism index of refraction for the reference order.  This parameter only
  applies to grisms.  If it is not specified it will be derived from
  the other disperser parameters.
  </DD>
  </DL>
  <DL>
  <DT><B>eff = INDEF (1.) [disperser|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='eff' Line='eff = INDEF (1.) [disperser|spectrograph]'>
  <DD>Peak efficiency for the theoretical disperser efficiency function.
  When an efficiency table is not specified then a theoretical efficiency
  is computed for the disperser.  This theoretical efficiency is scaled
  to peak efficiency given by this parameter.
  </DD>
  </DL>
  <P>
  <P>
  <DL>
  <DT><B>xdisperser = "<TT></TT>" [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xdisperser' Line='xdisperser = "" [spectrograph]'>
  <DD>Crossdisperser table.  If this file contains an efficiency table it applies
  only to first order.  An alternate first order table and tables for
  other orders are given by table parameters "<TT>xeffN</TT>", where N is the order.
  </DD>
  </DL>
  <DL>
  <DT><B>xdisptitle = "<TT></TT>" [xdisperser|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xdisptitle' Line='xdisptitle = "" [xdisperser|spectrograph]'>
  <DD>Title for crossdisperser.
  </DD>
  </DL>
  <DL>
  <DT><B>disptype = "<TT></TT>" ("<TT>grating</TT>") [xdisperser|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='disptype' Line='disptype = "" ("grating") [xdisperser|spectrograph]'>
  <DD>Type of crossdisperser element.  The chocies are "<TT></TT>", "<TT>grating</TT>", "<TT>grism</TT>",
  or "<TT>generic</TT>".  The empty string eliminates use of a cross disperser.
  The generic setting will simply use the desired central wavelength and
  dispersion without a grating or grism model.  One effect of this is that
  the mapping between detector pixel and wavelength is linear; i.e. a constant
  dispersion per pixel.
  </DD>
  </DL>
  <DL>
  <DT><B>gmm = INDEF (INDEF) [xdisperser|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='gmm' Line='gmm = INDEF (INDEF) [xdisperser|spectrograph]'>
  <DD>Ruling in lines per mm.  If not specified it will be derived from the
  other crossdisperser parameters.
  </DD>
  </DL>
  <DL>
  <DT><B>xblaze = INDEF (6.) [xdisperser|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xblaze' Line='xblaze = INDEF (6.) [xdisperser|spectrograph]'>
  <DD>Blaze (grating) or prism (grism) angle in degrees.  If not specified it
  will be derived from the other crossdisperser parameters.
  </DD>
  </DL>
  <DL>
  <DT><B>xoref = INDEF (1) [xdisperser|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xoref' Line='xoref = INDEF (1) [xdisperser|spectrograph]'>
  <DD>When a central (blaze) wavelength is specified this parameter indicates
  which order it is for.
  </DD>
  </DL>
  <DL>
  <DT><B>xwavelength = INDEF (INDEF) [xdisperser|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xwavelength' Line='xwavelength = INDEF (INDEF) [xdisperser|spectrograph]'>
  <DD>Central (blaze) wavelength in Angstroms for the reference order.  This
  parameter only applies to gratings.  If it is not specified it will
  be derived from the other crossdisperser parameters.
  </DD>
  </DL>
  <DL>
  <DT><B>xdispersion = INDEF (INDEF) [xdisperser|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xdispersion' Line='xdispersion = INDEF (INDEF) [xdisperser|spectrograph]'>
  <DD>Central dispersion in A/mm for the reference order.  This parameter only
  applies to gratings.  If it is not specified it will be derived from the
  other crossdisperser parameters.
  </DD>
  </DL>
  <DL>
  <DT><B>xindexref = INDEF (INDEF) [xdisperser|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xindexref' Line='xindexref = INDEF (INDEF) [xdisperser|spectrograph]'>
  <DD>Grism index of refraction for the reference order.  This parameter only
  applies to grisms.  If it is not specified it will be derived from
  the other crossdisperser parameters.
  </DD>
  </DL>
  <DL>
  <DT><B>xeff = INDEF (1.) [xdisperser|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xeff' Line='xeff = INDEF (1.) [xdisperser|spectrograph]'>
  <DD>Peak efficiency for the theoretical crossdisperser efficiency function.
  When an efficiency table is not specified then a theoretical efficiency
  is computed for the crossdisperser.  This theoretical efficiency is scaled
  to peak efficiency given by this parameter.
  </DD>
  </DL>
  <P>
  <P>
  <DL>
  <DT><B>aperture = "<TT></TT>" (default based on context) [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='aperture' Line='aperture = "" (default based on context) [spectrograph]'>
  <DD>Aperture table.  The text file gives aperture thruput as a function of the
  aperture size in units of seeing FWHM.  For rectangular apertures there are
  two independent variables corresponding to the width and length while for
  circular apertures there is one independent variable corresponding to the
  diameter.  If not specified a default table is supplied.  If a fiber table
  or a diameter is specified then the table "<TT>circle</TT>" is used otherwise the
  table "<TT>slit</TT>" is used.  Because "<TT>sptimelib$</TT>" is the last directory searched
  there are default files with these names in this directory for Gaussian
  seeing profiles passing through a circular or slit aperture.
  </DD>
  </DL>
  <DL>
  <DT><B>aptitle = "<TT></TT>" [aperture|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='aptitle' Line='aptitle = "" [aperture|spectrograph]'>
  <DD>Title for aperture used.
  </DD>
  </DL>
  <DL>
  <DT><B>aptype = "<TT></TT>" (default based on context) [aperture|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='aptype' Line='aptype = "" (default based on context) [aperture|spectrograph]'>
  <DD>The aperture types are "<TT>rectangular</TT>" or "<TT>circular</TT>".  If the
  parameter is not specified then if the aperture table has two columns the
  type is "<TT>circular</TT>" otherwise it is "<TT>rectangular</TT>".
  </DD>
  </DL>
  <P>
  <P>
  <DL>
  <DT><B>fiber = "<TT></TT>" [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fiber' Line='fiber = "" [spectrograph]'>
  <DD>Fiber transmission table.  The transmission is a function of wavelength
  in Angstroms.  If no fiber transmission is specified then no fiber
  component is included.
  </DD>
  </DL>
  <DL>
  <DT><B>fibtitle = "<TT></TT>" [fiber|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fibtitle' Line='fibtitle = "" [fiber|spectrograph]'>
  <DD>Title for fiber transmission used.
  </DD>
  </DL>
  <P>
  <P>
  <DL>
  <DT><B>filter = "<TT></TT>" [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='filter' Line='filter = "" [spectrograph]'>
  <DD>Filter transmission table.  The transmission is a function of wavelength
  in Angstroms.  If no filter transmission is specified then no filter
  component is included.
  </DD>
  </DL>
  <DL>
  <DT><B>ftitle = "<TT></TT>" [filter|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ftitle' Line='ftitle = "" [filter|spectrograph]'>
  <DD>Title for filter transmission used.
  </DD>
  </DL>
  <DL>
  <DT><B>filter2 = "<TT></TT>" [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='filter2' Line='filter2 = "" [spectrograph]'>
  <DD>Filter transmission table.  The transmission is a function of wavelength
  in Angstroms.  If no filter transmission is specified then no filter
  component is included.
  </DD>
  </DL>
  <DL>
  <DT><B>f2title = "<TT></TT>" [filter|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='f2title' Line='f2title = "" [filter|spectrograph]'>
  <DD>Title for filter transmission used.
  </DD>
  </DL>
  <DL>
  <DT><B>block = "<TT></TT>" ("<TT>no</TT>") [filter|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='block' Line='block = "" ("no") [filter|spectrograph]'>
  <DD>If "<TT>yes</TT>" then no check will be made for other orders.
  </DD>
  </DL>
  <P>
  <P>
  <DL>
  <DT><B>collimator = "<TT></TT>" (1.) [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='collimator' Line='collimator = "" (1.) [spectrograph]'>
  <DD>Collimator transmission table.  The transmission is a function of
  wavelength in Angstroms.  If no collimator is specified then a unit
  transmission is used.
  </DD>
  </DL>
  <DL>
  <DT><B>coltitle = "<TT></TT>" [collimator|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='coltitle' Line='coltitle = "" [collimator|spectrograph]'>
  <DD>Title for collimator.
  </DD>
  </DL>
  <DL>
  <DT><B>colfl = INDEF (1.) [collimator|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='colfl' Line='colfl = INDEF (1.) [collimator|spectrograph]'>
  <DD>Collimator focal length in meters.  The ratio of the collimator to camera
  focal lengths determines the magnification between the aperture and the
  detector.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B>camera = "<TT></TT>" (1.) [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='camera' Line='camera = "" (1.) [spectrograph]'>
  <DD>Camera transmission table.  The transmission is a function of wavelength
  in Angstroms.  If no camera is specified then a unit transmission
  is used.
  </DD>
  </DL>
  <DL>
  <DT><B>camtitle = "<TT></TT>" [camera|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='camtitle' Line='camtitle = "" [camera|spectrograph]'>
  <DD>Title for camera.
  </DD>
  </DL>
  <DL>
  <DT><B>camfl = "<TT></TT>" (1.) [camera|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='camfl' Line='camfl = "" (1.) [camera|spectrograph]'>
  <DD>Camera focal length in meters.  The ratio of the collimator to
  camera focal lengths determines the magnification between the aperture
  and the detector.  The camera focal length also determines the dispersion
  scale at the detector.
  </DD>
  </DL>
  <DL>
  <DT><B>resolution = "<TT></TT>" (2 pixels) [camera|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='resolution' Line='resolution = "" (2 pixels) [camera|spectrograph]'>
  <DD>Camera resolution on the detector in mm.
  </DD>
  </DL>
  <DL>
  <DT><B>vignetting = "<TT></TT>" (1.) [camera|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='vignetting' Line='vignetting = "" (1.) [camera|spectrograph]'>
  <DD>Vignetting table.  The independent variable is distance from the center
  of the detector in mm.  The value is the fraction the light transmitted.
  If no vignetting table is specified then no vignetting effect is applied.
  </DD>
  </DL>
  <P>
  <P>
  <DL>
  <DT><B>detector = "<TT></TT>" (1.) [spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='detector' Line='detector = "" (1.) [spectrograph]'>
  <DD>Detector DQE table.  The DQE is a function of wavelength in Angstroms.
  </DD>
  </DL>
  <DL>
  <DT><B>dettitle = "<TT></TT>" [detector|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dettitle' Line='dettitle = "" [detector|spectrograph]'>
  <DD>Title for detector.
  </DD>
  </DL>
  <DL>
  <DT><B>ndisp = INDEF (2048) [detector|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ndisp' Line='ndisp = INDEF (2048) [detector|spectrograph]'>
  <DD>Number of pixels along the dispersion.
  </DD>
  </DL>
  <DL>
  <DT><B>pixsize = INDEF (0.02) [detector|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pixsize' Line='pixsize = INDEF (0.02) [detector|spectrograph]'>
  <DD>Pixel size (assumed square) in mm.
  </DD>
  </DL>
  <DL>
  <DT><B>gain = INDEF (1.) [detector|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='gain' Line='gain = INDEF (1.) [detector|spectrograph]'>
  <DD>The conversion between photons and detector data numbers or counts.
  This is given as photons/ADU where ADU is analog-to-digital unit.
  </DD>
  </DL>
  <DL>
  <DT><B>rdnoise = INDEF (0.) [detector|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rdnoise' Line='rdnoise = INDEF (0.) [detector|spectrograph]'>
  <DD>Readout noise in photons.
  </DD>
  </DL>
  <DL>
  <DT><B>dark = INDEF (0.) [detector|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dark' Line='dark = INDEF (0.) [detector|spectrograph]'>
  <DD>Dark count rate in photons/s.
  </DD>
  </DL>
  <DL>
  <DT><B>saturation = INDEF [detector|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='saturation' Line='saturation = INDEF [detector|spectrograph]'>
  <DD>Number of detected photons in a pixel resulting in saturation.
  The default is no saturation.  The time per exposure will be reduced,
  but no lower than the minimum time per exposure,
  and the number of exposures increased to try and avoid saturation.
  </DD>
  </DL>
  <DL>
  <DT><B>dnmax = INDEF [detector|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dnmax' Line='dnmax = INDEF [detector|spectrograph]'>
  <DD>Maximum data number or ADU allowed.  The default is no maximum.
  The time per exposure will be reduced,
  but no lower than the minimum time per exposure,
  and the number of exposures increased to try and avoid overflow.
  </DD>
  </DL>
  <DL>
  <DT><B>xbin = 1 (1) [detector|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xbin' Line='xbin = 1 (1) [detector|spectrograph]'>
  <DD>Detector binning along the dispersion direction.
  </DD>
  </DL>
  <DL>
  <DT><B>ybin = 1 (1) [detector|spectrograph]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ybin' Line='ybin = 1 (1) [detector|spectrograph]'>
  <DD>Detector binning along the spatial direction.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Discussion</H3>
  <! BeginSection: 'DISCUSSION'>
  <UL>
  <P>
  <P>
  OVERVIEW
  <P>
  The spectroscopic exposure time package, <B>SPECTIME</B>, consists of a
  general calculation engine, <B>SPTIME</B>, and a collection of user or
  database defined IRAF scripts.  The scripts are one type of user interface
  for <B>SPTIME</B>.  Other user interfaces are Web-based forms and IRAF
  graphics/window applications.  The user interfaces customize the general
  engine to specific spectrographs by hiding components and parameters not
  applicable to that spectrograph and guiding the user, through menus or
  other facilities, in the choice of filters, gratings, etc.  However,
  <B>SPTIME</B> is a standard IRAF task that can be executed directly.
  <P>
  <B>SPTIME</B> takes an input source spectrum (either a reference blackbody,
  a power law, or a user spectrum), a background "<TT>sky</TT>" spectrum and a
  instrumental thermal background, reddening to apply to the spectrum,
  observing parameters such as exposure time, central wavelength, seeing,
  airmass, and moon phase, instrument parameters such as aperture sizes and
  detector binning, a description of the spectrograph, and produces
  information about the expected signal and signal-to-noise ratio in the
  extracted one-dimensional spectrum.  The output consists of a description
  of the observation, signal-to-noise statistics, and optional graphs and
  tables of various quantities as a function of wavelength over the
  spectrograph wavelength coverage.
  <P>
  <B>SPTIME</B> models a spectroscopic system as a flow of photons from a
  source to the detector through various optical components.  Background
  photons from the sky, atmosphere, and the thermal emission from the
  telescope and spectrograph are added.  It then computes signal-to-noise
  ratios from the detected photons of the source and background and the
  instrumental noise characteristics.  The spectroscopic system components
  are defined at a moderate level of detail.  It is not so detailed that
  every optical element has to be described and modeled and not so coarse
  that a single throughput function is used (though one is free to put all
  the thruput information into one component).  Not all components modeled by
  the task occur in all spectroscopic systems.  Therefore many of the
  components can be left out of the calculation.
  <P>
  The components currently included in <B>SPTIME</B> are:
  <P>
  <PRE>
      - the atmosphere (extinction and IR transmission)
      - the telescope (all elements considered as a unit)
      - an optional atmospheric dispersion compensator
      - the entrance aperture (slits, fibers, masks, etc.)
      - an optional fiber feed
      - a spectrograph (for components not represented elsewhere)
      - filters
      - a collimator
      - a disperser (grating, grism, prism, etc)
      - a optional cross disperser (grating, grism, prism, etc)
      - a corrector (either in the telescope of spectrograph)
      - a camera
      - a detector
  </PRE>
  <P>
  Each of these components represent a transmission function specifying the
  fraction of incident light transmitted or detected as a function of some
  parameter or parameters.  Except for the aperture, which is a function of
  the incident source profile (typically the seeing profile) relative to the
  aperture size, the transmissions of the components listed above are all
  functions of wavelength.
  <P>
  All the component transmission functions may be specified as either numeric
  values or as tables.  A numeric value is considered to be a special type of
  table which has the same value at all values of the independent parameters.
  By specifying only numeric values the task may be run without any table
  files.  To obtain information at a single wavelength this is all that is
  needed.
  <P>
  To specify a dependence on wavelength or other parameter a text file table
  with two or more columns may be specified.  The tables are interpolated in
  the parameter columns to find the desired value in the last column.  The
  tables are searched for in the current directory and then in a list of user
  specified directories.  Thus, users may place files in their work area to
  override system supplied files and observatories can organize the data
  files in a database directory tree.
  <P>
  In addition to transmission or DQE functions the spectrograph is described
  by various parameters.  All the parameters are described in the PARAMETERS
  section.  For flexibility parameters may be defined either in the
  parameter set or in one or more table files.  In all cases the parameter
  set values have precedence.   But if the values are "<TT></TT>" for string  parameters
  or INDEF for numeric parameters the values are found either in the
  spectrograph table or in a table that is associated with the parameter.
  <P>
  Therefore table files provide for interchangeable components, each with
  their own transmission curves, and for organizing parameters for different
  instruments.  Note that a table file may contain only parameters, only
  a table, or both.
  <P>
  There is also another way to maintain a separate file for different
  instruments.  The <I>specpars</I> parameter is a "<TT>parameter set</TT>" or "<TT>pset</TT>".
  The default value of "<TT></TT>" corresponds to the pset task <B>specpars</B>.
  However, using <B>eparam</B> one can edit this pset and then save the
  parameters to a named parameter file with "<TT>:e &lt;name&gt;.par</TT>".  This
  pset can be edited with <B>eparam</B> and specified in the
  <I>specpars</I> parameter.  One other point about pset parameters is that
  they can also be included as command line arguments just as any other
  parameter in the main task parameters.
  <P>
  Many spectrographs provide a wide variety of wavelength regions and
  dispersions.  For gratings (and to some extent for grisms) this means use
  of different gratings, orders, tilts, and possibly camera angles in the
  spectrograph.  The transmission as a function of wavelength (the grating
  efficiency) changes with these different setups.  If the transmission
  function is given as an interpolation table this would require data files
  for each setup of each disperser.  The structure of <B>SPTIME</B> allows
  for this.
  <P>
  However, it is also possible to specify the grating and spectrograph
  parameters and have the task predict the grating efficiency in any
  particular setup.  In many cases it may be easier to use the calculated
  efficiencies rather than measure them.  Depending on the level of accuracy
  desired this may be adequate or deviations from the analytic blaze function
  can be accounted for in another component.
  <P>
  <P>
  TABLES
  <P>
  <B>SPTIME</B> uses text files to provide parameters and interpolation
  tables.  The files may contain comments, parameters, and tables.
  <P>
  Comment lines begin with <TT>'#'</TT> and may contain any text.  They can occur
  anywhere in the file, though normally they are at the beginning of the file.
  <P>
  Parameters are comment lines of the form
  <P>
  <PRE>
      # [parameter] = [value]
  </PRE>
  <P>
  where whitespace is required between each field, [parameter] is a single
  word parameter name, and [value] is a single word value.  A quoted string
  is a single word so if the value field contains whitespace, such as in
  titles, it must be quoted.  Any text following the value is ignored and may
  be used for units (not read or used by the program) or comments.
  <P>
  The parameters are those described in the PARAMETERS section.  The tables
  in which the parameters may be included are identified in that section
  in the square brackets.  Note that it is generally true that any parameter
  may appear in the spectrograph table.
  <P>
  The table data is a multicolumn list of numeric values.  The list must be
  in increasing order in the independent columns.  Only 1D (two columns) and
  2D (three columns) tables are currently supported.  2D tables must form a
  regular grid.  This means that any particular value from column one must
  occur for all values of column 2 and vice versa.   The table is
  interpolated as needed.  The interpolation is linear or bi-linear.
  Extrapolation outside of the table consists of the taking the nearest
  value; thus, a single line may be used to define a constant value for all
  values of the independent variable(s).
  <P>
  Normally the table values, the dependent variable in the last column, are
  in fractional transmission or DQE.  There is a special parameter,
  "<TT>tablescale</TT>", which may be specified to multiply the dependent variable
  column.  This would mainly be used to provide tables in percent rather
  than fraction.
  <P>
  The independent variable columns depend on the type of table.  Most tables
  are a function of wavelength.  Currently wavelengths must be in Angstroms.
  <P>
  The types of tables and the units of the columns are listed below.
  <P>
  <PRE>
          spectrum - Angstroms ergs/s/cm^2/A
               sky - Angstroms ergs/s/cm^2/A/arcsec^2
        extinction - Angstroms mag/airmass
      spectrograph - Angstroms transmission
         telescope - Angstroms transmission
        emissivity - Angstroms emissivity
               adc - Angstroms transmission
             fiber - Angstroms transmission
        collimator - Angstroms transmission
            filter - Angstroms transmission
         disperser - Angstroms transmission
        xdisperser - Angstroms transmission
         corrector - Angstroms transmission
            camera - Angstroms transmission
          detector - Angstroms transmission
       sensitivity - Angstroms 2.5*(log(countrate)-log(flambda)),
  <P>
               sky - Angstroms moonphase ergs/s/cm^2/A/arcsec^2
          aperture - diameter/FWHM transmission
          aperture - width/FWHM length/FWHM transmission
        vignetting - mm transmission
  </PRE>
  <P>
  The disperser and crossdisperser files have an additional feature to allow
  for efficiency curves at different orders.  The parameter "<TT>effN</TT>" (or "<TT>xeffN
  for crossdispersers), where N is the order, may be specified whose value is
  a separate table (or constant).  If there is no </TT>"eff1/xeff1"<TT> (efficiency in
  first order) then any efficiency table in the disperser table is used.  In
  other words, any table in the disperser file applies only to first order
  and only if there is no </TT>"eff1/xeff1"<TT> parameter defining a separate first
  order efficiency file.
  <P>
  DISPERSION UNITS
  <P>
  The output results, text file, and graphs are presented in dispersion
  units defined by the <I>units</I> parameter.  In addition the <I>wave</I>
  and <I>refwave</I> input parameters are specified in the selected units.
  All other dispersion values must currently be specified in Angstroms.
  <P>
  The dispersion units are specified by strings having a unit type from the
  list below along with the possible preceding modifiers, "<TT>inverse</TT>", to
  select the inverse of the unit and "<TT>log</TT>" to select logarithmic units. For
  example "<TT>log angstroms</TT>" to select the logarithm of wavelength in Angstroms
  and "<TT>inv microns</TT>" to select inverse microns.  The various identifiers may
  be abbreviated as words but the syntax is not sophisticated enough to
  recognize standard scientific abbreviations except for those given
  explicitly below.
  <P>
  <PRE>
  	   angstroms - Wavelength in Angstroms
  	  nanometers - Wavelength in nanometers
  	millimicrons - Wavelength in millimicrons
  	     microns - Wavelength in microns
  	 millimeters - Wavelength in millimeters
  	  centimeter - Wavelength in centimeters
  	      meters - Wavelength in meters
  	       hertz - Frequency in hertz (cycles per second)
  	   kilohertz - Frequency in kilohertz
  	   megahertz - Frequency in megahertz
  	    gigahertz - Frequency in gigahertz
  	         m/s - Velocity in meters per second
  	        km/s - Velocity in kilometers per second
  	          ev - Energy in electron volts
  	         kev - Energy in kilo electron volts
  	         mev - Energy in mega electron volts
  <P>
  	          nm - Wavelength in nanometers
  	          mm - Wavelength in millimeters
  	          cm - Wavelength in centimeters
  	           m - Wavelength in meters
  	          Hz - Frequency in hertz (cycles per second)
  	         KHz - Frequency in kilohertz
  	         MHz - Frequency in megahertz
  	         GHz - Frequency in gigahertz
  		  wn - Wave number (inverse centimeters)
  </PRE>
  <P>
  The velocity units require a trailing value and unit defining the
  velocity zero point.  For example to transform to velocity relative to
  a wavelength of 1 micron the unit string would be:
  <P>
  <PRE>
  	km/s 1 micron
  </PRE>
  <P>
  <P>
  CALCULATIONS
  <P>
  This section describes the calculations, and assumptions behind the
  calculations, performed by <B>SPTIME</B>.  These include the dispersion and
  efficiencies of gratings and grisms, the dispersion resolution, the spatial
  resolution and how it applies to the number of object and sky pixels in the
  apertures, the object and sky detected photons/counts, the signal-to-noise
  ratio , and the exposure time for a given S/N.
  <P>
  <P>
  Gratings
  <P>
  Gratings are assumed to tilted only around the axis parallel to the
  groves and with the incident angle greater than the blaze angle.  The
  grating equation is then
  <P>
  <PRE>
      g * m * w = sin(tilt+phi/2) + sin(beta)
  </PRE>
  <P>
  where g is the number of groves per wavelength unit, m is the order, w is
  the wavelength, tilt is the grating tilt measured from the grating normal,
  phi is the angle between the incident and diffracted rays, and beta is the
  diffracted angle.  Phi is a spectrograph parameter and g is a grating
  parameter.  At the desired central wavelength beta is tilt-phi/2 and at the
  blaze peak it is 2*blaze-tilt-phi/2 where blaze is the blaze angle.
  <P>
  The tilt is computed from the desired central wavelength.  It is
  also used to compute the grating magnification
  <P>
  <PRE>
      magnification = cos(tilt-phi/2) / cos(tilt+phi/2)
  </PRE>
  <P>
  which is used in calculating the projected slit size at the detector.
  This number is less than zero so the aperture is actually demagnified.
  <P>
  The dispersion, treated as constant over the spectrum for the sake of
  simplicity, is given by the derivative of the grating equation at
  the blaze peak,
  <P>
  <PRE>
      dispersion = cos(blaze-phi/2) / (g * m * f)
  </PRE>
  <P>
  where f is the camera focal length.
  <P>
  The grating efficiency or blaze function is computed as described by
  Schroeder and Hilliard (Applied Optics, vol 19, 1980, p. 2833).  The
  requirements on the grating noted previously correspond to their case A.
  As they show, use of incident angles less than the blaze angle, their case
  B, significantly degrades the efficiency due to back reflection which is
  why this case is not included.  The efficiency formulation includes
  variation in the peak efficiency due light diffracted into other orders,
  shadowing of the groves, and a reflectance parameter.  The reflectance
  parameter is basically the blaze peak normalization and does not currently
  include a wavelength dependence.  Thus the peak efficiency is near the
  reflectance value but somewhat lower and is order dependent due to the other
  effects.
  <P>
  <P>
  Grisms
  <P>
  Grisms are assumed to have a prism angle equal to the blaze angle of
  the inscribed grating.  The index of refraction is treated as constant
  over the wavelength range of an order, though different index of refraction
  values can be specified for each order.
  <P>
  The grism formula used is a variation on the grating equation.
  <P>
  <PRE>
      g * m * w = n * sin (theta+prism) - sin (beta+prism)
  </PRE>
  <P>
  where n is the index of refraction, prism is the prism or blaze angle,
  theta is the incident angle relative to the prism face, and beta is the
  refracted angle relative to the prism face.  Theta and beta are defined so
  that at the undeviated wavelength they are zero.  In other words at the
  undeviated wavelength the light path is a straight through transmission.
  <P>
  The efficiency is also computed in an analogous manner to the
  reflection grating except that shadowing is not included (a consequence of
  the blaze face being parallel to the prism face and theta being near
  zero).  Instead of a reflectance value normalizing the blaze function a
  transmission value is used.
  <P>
  <P>
  Scales and Sizes
  <P>
  The scale between arc seconds on the sky and millimeters at the
  aperture(s) of the spectrograph is specified by the <I>scale</I> parameter.
  This parameter is used to convert aperture sizes between arc seconds and
  millimeters.
  <P>
  The aperture sizes are magnified or demagnified by three possible factors.
  The basic magnification is given by the ratio of the collimator focal
  length to the camera focal length.  This magnification applies both along
  and across the dispersion.
  <P>
  The camera focal length also determines the dispersion scale on the detector.
  It converts radians of dispersion to mm at the detector.
  <P>
  For grating dispersers there is a demagnification along the dispersion
  due to the tilt of the grating(s).  The demagnification is computed (as
  given previously) from the grating parameters and the spectrograph
  parameter giving the angle between the incident and diffracted rays at the
  detector center.
  <P>
  The last magnification factor is given by the spectrograph parameters
  "<TT>apmagdisp</TT>" and apxmagdisp"<TT>.  These define magnifications of the aperture
  along and across the dispersion apart from the other two magnifications.
  These parameters are often missing which means no additional
  magnifications.
  <P>
  One use for the last magnification parameters is to correct aperture
  sizes given as millimeters or arc seconds on a plane tilted with respect to
  the focal plane.  Such tilted apertures occur with aperture mechanisms
  (usually slits) that reflect light for acquisition and guiding.  Note that
  one only needs to use these terms if users are expected to define the
  apertures sizes on the tilted plane.  If instead the projection factors are
  handled by the spectrograph system and users specify aperture size as
  millimeters or arc seconds on the sky then these terms are not needed.
  <P>
  The above scale factors map arc seconds on the sky and aperture sizes
  in millimeter to arc seconds and millimeters projected on the detector.  To
  convert to pixels on the detector requires the pixel size.
  One option in <B>SPTIME</B> is to specify aperture
  sizes as projected pixels on the detector (either in the user parameters or
  in the aperture description file).  Using the detector pixel size and the
  scale factors allows conversion of aperture sizes specified in this way
  back to the actual aperture size.
  <P>
  <P>
  Resolution
  <P>
  A camera resolution parameter may be set in the camera description.  If
  a resolution value is not given it is taken to be 2 pixels.  This parameter
  is used to define the dispersion resolution element and the number of
  pixels across the dispersion imaged by the detector for the aperture and
  the object.  The latter usage is discussed in the next section.
  <P>
  The dispersion resolution element, in pixels, is given by
  <P>
  <PRE>
  				 |  2 pixels
      disp resolution = maximum of |  camera resolution
  				 |  1 + min (seeing, apsize)
  </PRE>
  <P>
  where seeing is the FWHM seeing diameter in pixels and apsize is the
  aperture size in pixels.  For circular apertures the aperture size is
  the diameter and for rectangular apertures it is the width.  The first term
  comes from sampling considerations, the second from the camera resolution,
  and the third from the finite resolution of a pixel (the factor of 1) and
  the spread of wavelengths across the aperture or seeing disk.  The
  dispersion resolution is printed for information and the S/N per dispersion
  resolution element is given in addition to the per pixel value.
  <P>
  <P>
  Object and Sky Pixels Across the Dispersion
  <P>
  The number of pixels across the dispersion in the object and the sky
  are required to compute the S/N statistics.  The number of pixels
  in the projected aperture image is taken to be
  <P>
  <PRE>
  		       | diameter + resolution  (circular apertures)
      aperture pixels =  |
  		       | length + resolution    (rectangular apertures)
  </PRE>
  <P>
  where resolution is the camera resolution discussed previously.  The value
  is rounded up to an integer.
  <P>
  Objects are assumed to fill circular (fiber) apertures.  Therefore the
  number of object pixels is the same as the number of pixels in the
  aperture.  In rectangular (slit) apertures the number of object pixels is
  taken to be
  <P>
  <PRE>
  				| 3*seeing + resolution
      object pixels = minimum of  |
  				| number of aperture pixels
  </PRE>
  <P>
  where seeing is the FWHM seeing diameter converted to pixels.  The values
  are rounded up to an integer.
  <P>
  The number of sky pixels depends on the type of sky subtraction.
  For "<TT>longslit</TT>" sky subtraction the number of sky pixels is given
  by the difference of the number of aperture pixels and the number of
  object pixels.  For circular apertures this always comes out to zero so
  it does not make sense to use longslit sky subtraction.  For rectangular
  apertures the number of sky pixels in the aperture depends on the
  aperture size and the seeing.  If the number of sky pixels comes out to
  zero a warning is printed.
  <P>
  For "<TT>multiap</TT>" sky subtraction the number of sky pixels is the
  number of sky apertures times the number of pixels per aperture.
  <P>
  <P>
  Source Counts
  <P>
  The source spectrum flux at each wavelength, either given in a spectrum
  table or as a model distribution, is in units of
  photons per second per Angstrom per square centimeter.  This is multiplied
  by the telescope effective area, the exposure time, and the pixel size in
  Angstroms to give the source photons per dispersion pixel per exposure.
  This is then multiplied by any of the following terms that apply to arrive
  at the number of source photons detected over all spatial pixels.  The
  spatial integration is implicit in the aperture function.
  <P>
  <PRE>
      - the extinction using the specified airmass
      - the telescope transmission
      - the ADC transmission
      - the aperture transmission based on the aperture size relative
        to the seeing
      - the fiber transmission
      - the filter transmission (one or two filters)
      - the collimator transmission
      - the disperser efficiency (one or two dispersers)
      - the corrector transmission
      - the camera transmission
      - the detector DQE
  </PRE>
  <P>
  <P>
  Background Counts
  <P>
  The sky or atmospheric background spectrum, if one is given, defines a
  photon flux per square arc second.  When it is given as a function of the
  moon phase it is interpolated to the specified moon phase.  In addition
  if a thermal temperature and an emissivity are given then a thermal
  background is computed and added to the sky/atmospheric background.
  <P>
  The surface brightness of the background is multiplied by the area of the
  aperture occupied by the object (in arc seconds) and divided by the
  aperture transmission of the source.  This is the quantity reported in the
  output for the sky photon flux.  It is comparable to the source photon
  flux.
  <P>
  Next this flux is multiplied by the telescope effective area, the
  exposure time, and the pixel size in Angstroms.  Finally it is multiplied
  by the same transmission terms as the object except for the extinction.
  Note that this removes the aperture transmission term included earlier
  giving the background photons as the number passing through the aperture per
  object profile.  The final value is the number of background photons from the
  object.  To get the background photons per spatial pixel the value is divided by
  the number of spatial pixels occupied by the source.
  <P>
  If no background subtraction is specified then the background counts are added
  to the source counts to define the final source counts and the background
  counts are set to zero.
  <P>
  <P>
  Signal-to-Noise Ratio
  <P>
  The noise attributed to the source and background is based on Poisson
  statistics; namely the noise is the square root of the number of photons.
  The detector noise is given by a dark count component and a readout noise
  component.  The noise from the dark counts is obtain by multiplying the
  dark count rate by the exposure time and the number of spatial pixels used
  in extracting the source and taking the square root.  The readout noise is
  the detector readout noise parameter multiplied by the square root of the
  number of spatial source pixels.
  <P>
  If background subtraction is selected and the number of available
  background pixels is greater than zero then the uncertainty in the
  background estimation is computed.  The uncertainty in a single pixel is
  the square root of the background photons per pixel, the dark counts per
  pixel, and the readout noise per pixel.  This is divided by the square root
  of the number of background pixels to get the uncertainty in the background
  estimation for subtraction from the source.
  <P>
  The total noise is the combination of the source, background, dark count,
  and readout noise values and the background subtraction uncertainty added
  in quadrature.
  <P>
  The signal-to-noise ratio per pixel per exposure is the source counts
  divided by total noise.  This value is multiplied by the square root of
  number of pixels per resolution element to get the S/N per resolution
  element.  If multiple exposures are used to make up the total exposure time
  then the single exposure S/N is multiplied by the square root of the number
  of exposures.
  <P>
  <P>
  Exposure Time From Signal-to-Noise Ratio
  <P>
  If no exposure time is specified, that is a value of INDEF, then
  the exposure time required to reach a desired signal-to-noise ratio
  per pixel is determined.  The computation is done at the specified central
  wavelength.  The task iterates, starting with the specified maximum time per
  exposure, by computing the S/N and adjusting the exposure time
  (possibly breaking the total exposure up into subexposures) until
  the computed S/N matches the desired S/N to 0.1%.
  <P>
  In addition to breaking the exposure time into individual exposure less
  than the maximum per exposure, the task will break single exposures that
  exceed the specified saturation and maximum data number values at the
  reference wavelength.  If other wavelengths are then saturated or exceed
  the data maximum a warning is printed.
  </UL>
  <! EndSection:    'DISCUSSION'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DISCUSSION'  >
  
