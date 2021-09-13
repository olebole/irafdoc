.. _calibrate:

calibrate — Apply extinction and flux calibrations to spectra
=============================================================

**Package: ctioslit**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  calibrate -- Apply extinction corrections and flux calibrations
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  calibrate input output [records]
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of input spectra to be calibrated.  When using record format
  extensions the root names are specified, otherwise full image names
  are used.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>List of calibrated spectra.  If no output list is specified or if the
  output name is the same as the input name then the calibrated spectra
  replace the input spectra.  When using record format extensions the output
  names consist of root names to which the appropriate record number
  extension is added.  The record number extension will be the same as the
  input record number extension.  The output spectra are coerced to have
  real datatype pixels regardless of the  pixel type.
  </DD>
  </DL>
  <DL>
  <DT><B>records (imred.irs and imred.iids only)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='records' Line='records (imred.irs and imred.iids only)'>
  <DD>The set of record number extensions to be applied to each input and output
  root name when using record number extension format.  The syntax consists
  of comma separated numbers or ranges of numbers.  A range consists of
  two numbers separated by a hyphen.  This parameter is not queried
  when record number formats are not used.
  </DD>
  </DL>
  <DL>
  <DT><B>extinct = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='extinct' Line='extinct = yes'>
  <DD>Apply extinction correction if a spectrum has not been previously
  corrected?  When applying an extinction correction, an extinction file
  is required.
  </DD>
  </DL>
  <DL>
  <DT><B>flux = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='flux' Line='flux = yes'>
  <DD>Apply a flux calibration if a spectrum has not been previously calibrated?
  When applying a flux calibration, sensitivity spectra are required.
  </DD>
  </DL>
  <DL>
  <DT><B>extinction = &lt;no default&gt;</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='extinction' Line='extinction = &lt;no default&gt;'>
  <DD>Extinction file for the observation.  Standard extinction files
  are available in the "<TT>onedstds$</TT>" directory.
  </DD>
  </DL>
  <DL>
  <DT><B>observatory = "<TT>)_.observatory</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='observatory' Line='observatory = ")_.observatory"'>
  <DD>Observatory at which the spectra were obtained if not specified in the
  image header by the keyword OBSERVAT.  The default is a redirection to the
  package parameter of the same name.  The observatory may be one of the
  observatories in the observatory database, "<TT>observatory</TT>" to select the
  observatory defined by the environment variable "<TT>observatory</TT>" or the
  parameter <B>observatory.observatory</B>, or "<TT>obspars</TT>" to select the current
  parameters in the <B>observatory</B> task.  See <B>observatory</B> for
  additional information.
  </DD>
  </DL>
  <DL>
  <DT><B>ignoreaps = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ignoreaps' Line='ignoreaps = no'>
  <DD>Ignore aperture numbers and apply a single flux calibration to all
  apertures?  Normally multiaperture instruments have separate sensitivity
  functions for each aperture while long slit or Fabry-Perot data use a
  single sensitivity function where the apertures are to be ignored.  The
  sensitivity spectra are obtained by adding the aperture number as an
  extension to the sensitivity spectrum root name.  When apertures are
  ignored the specified sensitivity spectrum name is used without adding an
  extension and applied to all input apertures.
  </DD>
  </DL>
  <DL>
  <DT><B>sensitivity = "<TT>sens</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sensitivity' Line='sensitivity = "sens"'>
  <DD>The root name for the sensitivity spectra produced by <B>sensfunc</B>.
  Normally with multiaperture instruments, <B>sensfunc</B> will produce a
  spectrum appropriate to each aperture with an aperture number extension.
  If the apertures are ignored (<I>ignoreaps</I> = yes) then the sensitivity
  spectrum specified is used for all apertures and no aperture number is
  appended automatically.
  </DD>
  </DL>
  <DL>
  <DT><B>fnu = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fnu' Line='fnu = no'>
  <DD>The default calibration is into units of flux per unit wavelength (F-lambda).
  If <I>fnu</I> = yes then the calibrated spectrum will be in units of
  flux per unit frequency (F-nu).
  </DD>
  </DL>
  <DL>
  <DT><B>airmass, exptime</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='airmass' Line='airmass, exptime'>
  <DD>If the airmass and exposure time are not in the header nor can they be
  determined from other keywords in the header then these query parameters
  are used to request the airmass and exposure time.  The values are updated
  in the input and output images.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The input spectra are corrected for extinction and calibrated to a flux
  scale using sensitivity spectra produced by the task <B>sensfunc</B>.
  One or both calibrations may be performed by selecting the appropriate
  parameter flags.  It is an error if no calibration is specified.  Normally
  the spectra should be extinction corrected if also flux calibrating.
  The image header keywords DC-FLAG (or the dispersion type field in the
  "<TT>multispec</TT>" world coordinate system), EX-FLAG, and CA-FLAG are checked for
  dispersion solution (required), previous extinction correction, and
  previous flux calibration.  If previously calibrated the spectrum is
  skipped and a new output image is not created.
  <P>
  The input spectra are specified by a list of root names (when using record
  extension format) or full image names.  The output calibrated spectra may
  replace the input spectra if no output spectra list is specified or if the
  output name is the same as the input name.  When using record number
  extensions the output spectra will have the same extensions applied to the
  root names as those used for the input spectra.
  <P>
  When applying an extinction correction the AIRMASS keyword is sought.
  If the keyword is not present then the airmass at the time defined
  by the other header keywords is computed using the
  latitude of the observatory and observation parameters in the image
  header.  The observatory is first determined from the image under the
  keyword OBSERVAT.  If absent the observatory specified by the task
  parameter "<TT>observatory</TT>" is used.  See <B>observatory</B> for further
  details of the observatory database.  If the air mass cannot be
  determined an error results.  Currently a single airmass is used
  and no correction for changing extinction during the observation is
  made and adjustment to the middle of the exposure.  The task
  <B>setairmass</B> provides a correction for the exposure time to compute
  an effective air mass.  Running this task before calibration is
  recommended.
  <P>
  If the airmass is not in the header and cannot be computed then
  the user is queried for a value.  The value entered is then
  recorded in both the input and output image headers.  Also if
  the exposure time is not found then it is also queried and
  recorded in the image headers.
  <P>
  The extinction correction is given by the factor
  <P>
  		10. ** (0.4 * airmass * extinction)
  <P>
  where the extinction is the value interpolated from the specified
  extinction file for the wavelength of each pixel.  After extinction
  correction the EX-FLAG is set to 0.
  <P>
  When applying a flux calibration the spectra are divided by the
  aperture sensitivity which is represented by a spectrum produced by
  the task <B>sensfunc</B>.  The sensitivity spectrum is in units of:
  <P>
  	2.5 * Log10 [counts/sec/Ang / ergs/cm2/sec/Ang].
  <P>
  A new spectrum is created in "<TT>F-lambda</TT>" units - ergs/cm2/sec/Angstrom
  or "<TT>F-nu</TT>" units - ergs/cm2/sec/Hz.  The sensitivity must span the range of
  wavelengths in the spectrum and interpolation is used if the wavelength
  coordinates are not identical.  If some pixels in the spectrum being
  calibrated fall outside the wavelength range of the sensitivity function
  spectrum a warning message giving the number of pixels outside the
  range.  In this case the sensitivity value for the nearest wavelength
  in the sensitivity function is used.
  <P>
  Multiaperture instruments typically have
  a separate aperture sensitivity function for each aperture.  The appropriate
  sensitivity function for each input spectrum is selected based on the
  spectrum's aperture by appending this number to the root sensitivity function
  spectrum name.  If the <I>ignoreaps</I> flag is set, however, the aperture
  number relation is ignored and the single sensitivity spectrum (without
  extension) is applied.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  To flux calibrates a series of spectra replacing the input spectra by
  the calibrated spectra:
  <P>
  	cl&gt; calibrate nite1 "<TT></TT>"
  <P>
  2.  To only extinction correct echelle spectra:
  <P>
  	cl&gt; calibrate ccd*.ec.imh new//ccd*.ec.imh flux-
  <P>
  3. To flux calibrate a long slit spectrum:
  <P>
  <PRE>
  	cl&gt; dispaxis = 2
  	cl&gt; calibrate obj.imh fcobj.imh
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>CALIBRATE V2.10.3</B></DT>
  <! Sec='REVISIONS' Level=0 Label='CALIBRATE' Line='CALIBRATE V2.10.3'>
  <DD>This task was revised to operate on 2D and 3D spatial spectra; i.e. long
  slit and Fabry-Perot data cubes.  This task now includes the functionality
  previously found in <B>longslit.extinction</B> and <B>longslit.fluxcalib</B>.
  <P>
  A query for the airmass and exposure time is now made if the information
  is not in the header and cannot be computed from other header keywords.
  </DD>
  </DL>
  <DL>
  <DT><B>CALIBRATE V2.10</B></DT>
  <! Sec='REVISIONS' Level=0 Label='CALIBRATE' Line='CALIBRATE V2.10'>
  <DD>This task was revised to operate on nonlinear dispersion corrected spectra
  and 3D images (the <B>apextract</B> "<TT>extras</TT>").  The aperture selection
  parameter was eliminated (since the header structure does not allow mixing
  calibrated and uncalibrated spectra) and the latitude parameter was
  replaced by the observatory parameter.  The observatory mechanism insures
  that if the observatory latitude is needed for computing an airmass and the
  observatory is specified in the image header the correct calibration will
  be applied.  The record format syntax is available in the <B>irs/iids</B>
  packages.  The output spectra are coerced to have real pixel datatype.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  setairmass, standard, sensfunc, observatory, continuum
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
