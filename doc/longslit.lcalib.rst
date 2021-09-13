.. _lcalib:

lcalib — List calibration file data
===================================

**Package: longslit**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  lcalib -- List information about the spectral calibration data
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  lcalib option star_name
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>option</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='option' Line='option'>
  <DD>Chooses calibration data to be listed.  Option
  may be: "<TT>bands</TT>" to list the bandpasses at each wavelength, "<TT>ext</TT>" to
  list the extinction at each wavelength, "<TT>mags</TT>", "<TT>fnu</TT>", or "<TT>flam</TT>"
  to list the magnitude, or flux of
  the star (selected by the star_name parameter) at each wavelength, or
  "<TT>stars</TT>" to list the star names available in the calibration directory.
  </DD>
  </DL>
  <DL>
  <DT><B>star_name</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='star_name' Line='star_name'>
  <DD>Selects which star's magnitude list is chosen if the option parameter
  is "<TT>mags</TT>", "<TT>fnu</TT>", "<TT>flam</TT>", or "<TT>bands</TT>".  Also if <TT>'?'</TT> a list of available
  stars in the specified calibration directory is given.
  </DD>
  </DL>
  <P>
  The following three queried parameters apply if the selected calibration
  file is for a blackbody.  See <B>standard</B> for further details.
  <DL>
  <DT><B>mag</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='mag' Line='mag'>
  <DD>The magnitude of the observed star in the band given by the
  <I>magband</I> parameter.  If the magnitude is not in the same band as
  the blackbody calibration file then the magnitude may be converted to
  the calibration band provided the "<TT>params.dat</TT>" file containing relative
  magnitudes between the two bands is in the calibration directory
  </DD>
  </DL>
  <DL>
  <DT><B>magband</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='magband' Line='magband'>
  <DD>The standard band name for the input magnitude.  This should generally
  be the same band as the blackbody calibration file.  If it is
  not the magnitude will be converted to the calibration band.
  </DD>
  </DL>
  <DL>
  <DT><B>teff</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='teff' Line='teff'>
  <DD>The effective temperature (deg K) or the spectral type of the star being
  calibrated.  If a spectral type is specified a "<TT>params.dat</TT>" file must exist
  in the calibration directory.  The spectral types are specified in the same
  form as in the "<TT>params.dat</TT>" file.  For the standard blackbody calibration
  directory the spectral types are specified as A0I, A0III, or A0V, where A
  can be any letter OBAFGKM, the single digit subclass is between 0 and 9,
  and the luminousity class is one of I, III, or V.  If no luminousity class
  is given it defaults to dwarf.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B>extinction</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='extinction' Line='extinction'>
  <DD>Extinction file.  The current standard extinction files:
  <PRE>
  	onedstds$kpnoextinct.dat - KPNO standard extinction
  	onedstds$ctioextinct.dat - CTIO standard extinction
  </PRE>
  </DD>
  </DL>
  <DL>
  <DT><B>caldir</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='caldir' Line='caldir'>
  <DD>Calibration directory containing standard star data.  The directory name
  must end with /.  The current calibration directories available in the
  onedstds$ may be listed with the command:
  <P>
  <PRE>
  	cl&gt; page onedstds$README
  </PRE>
  </DD>
  </DL>
  <DL>
  <DT><B>fnuzero = 3.68e-20</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fnuzero' Line='fnuzero = 3.68e-20'>
  <DD>The absolute flux per unit frequency at a magnitude of zero.  This is used
  to convert the calibration  magnitudes to absolute flux by the formula
  <P>
  	Flux = fnuzero * 10. ** (-0.4 * magnitude)
  <P>
  The flux units are also determined by this parameter.  However, the
  frequency to wavelength interval conversion assumes frequency in hertz.
  The default value is based on a calibration of Vega at 5556 Angstroms of
  3.52e-20 ergs/cm2/s/hz for a magnitude of 0.048.  This default value
  is that used in earlier versions of this task which did not allow the
  user to change this calibration.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  LCALIB provides a means of checking the flux calibration data.  The calibration
  data consists of extinction, bandpasses, and stellar magnitudes.
  <P>
  The extinction is given in an extinction file consisting of lines with
  wavelength and extinction.  The wavelengths must be order in increasing
  wavelength and the wavelengths must be in Angstroms.  There are two
  standard extinction files currently available, "<TT>onedstds$kpnoextinct.dat</TT>",
  and "<TT>onedstds$ctioextinct.dat</TT>".
  <P>
  The standard star data are in files in a calibration
  directory specified with the parameter <I>caldir</I>.  A standard star
  file is selected by taking the star name given, by the parameter
  <I>star_name</I>, removing blanks, +'s and -'s, appending "<TT>.dat</TT>", and converting
  to lower case.  This file name is appended to the specified calibration
  directory.  A calibration file consists of lines containing a wavelength,
  a stellar magnitude, and a bandpass full width.  The wavelengths are in
  Angstroms.  Comment lines beginning with # may be included in the file.
  The star names printed by this task are just the first line of each file
  in the calibration directory with the first character (#) removed.
  The calibration files may be typed, copied, and printed.  <B>Lcalib</B>
  may also be used to list data from the calibration files.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  <PRE>
  	# List the extinction table
  	cl&gt; lcalib ext
  	# Plot the extinction table
  	cl&gt; lcalib ext | graph
  	# Plot the energy distribution
  	cl&gt; lcalib mags "bd+28 4211" | graph
  	# List the names of all the stars
  	cl&gt; lcalib stars caldir=onedstds$irscal/
  	# As above but for IIDS file
  	cl&gt; lcalib stars calib_file=onedstds$iidscal/
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>LCALIB V2.10</B></DT>
  <! Sec='REVISIONS' Level=0 Label='LCALIB' Line='LCALIB V2.10'>
  <DD>This task has a more compact listing for the "<TT>stars</TT>" option and allows
  paging a list of stars when the star name query is not recognized.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  standard, sensfunc, onedstds$README
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
