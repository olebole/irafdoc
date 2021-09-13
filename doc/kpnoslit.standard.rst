standard — Identify standard stars to be used in sensitivity calc
=================================================================

**Package: kpnoslit**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>standard (Jan00)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.onedspec</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>standard (Jan00)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>standard</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  standard -- Add standard stars to sensitivity file
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  standard input [records] output
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of input standard star spectra or root names if using the record number
  extension format.  All spectra of the same aperture must be of the same
  standard star.  In beam switch mode or when the same star parameter is set
  all spectra must be of the same standard star regardless of aperture number.
  Normally the spectra will not be extinction corrected but if they are
  then the extinction file should also be given and the same extinction
  file should be used with <B>sensfunc</B>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_records">records (imred.irs and imred.iids only)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='records' Line='records (imred.irs and imred.iids only)'>
  <DD>List of records or ranges of records to be appended to the input spectra
  names when using record number extension format.  The
  syntax of this list is comma separated record numbers or ranges of record
  numbers.  A range consists of two numbers separated by a hyphen.
  A null list may be used if no record number extensions are
  desired.  This is a positional query parameter only if the record
  format is specified.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>The name of a text file which will contain the output from <B>standard</B>.
  Each execution of <B>standard</B> appends to this file information about the
  standard stars, the calibration bandpasses, and observed counts (see the
  DESCRIPTION section for more details).  The output must be explicitly
  deleted by the user if the filename is to be reused.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_samestar">samestar = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='samestar' Line='samestar = yes'>
  <DD>Is the same star in all apertures?  If set to no then each aperture may
  contain a different standard star.  The standard star name is queried
  each time a new aperture is encountered.  Note that this occurs only
  once per aperture and multiple spectra with the same aperture number
  must be of the same star.  If set to yes the standard star name is only
  queried once.  When in beam switch mode this parameter is ignored since
  all apertures must contain the same star.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_beam_switch">beam_switch = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='beam_switch' Line='beam_switch = no'>
  <DD>Beam switch the spectra?  If yes then a beam switch mode is used for the spectra
  in which successive pairs of object and sky observations from the same aperture
  are sky subtracted.  This requires that the object type flag OFLAG be present
  and that the spectra are appropriately ordered.  All object observations must be
  of the same standard star and the <I>samestar</I> parameter is ignored.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_apertures">apertures = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='apertures' Line='apertures = ""'>
  <DD>List of apertures to be selected from the input list of spectra.  If no list
  is specified then all apertures are selected.  The syntax is the same as the
  record number extensions.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_bandwidth">bandwidth = INDEF, bandsep = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='bandwidth' Line='bandwidth = INDEF, bandsep = INDEF'>
  <DD>Bandpass widths and separations in wavelength units.  If INDEF then the
  default bandpasses are those given in the standard star calibration
  file.  If values for these parameters are specified then a default set
  of bandpasses of equal width and separation are defined over the range
  of the input spectrum.  In both cases the default bandpasses can be
  changed interactively if desired.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fnuzero">fnuzero = 3.68e-20</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fnuzero' Line='fnuzero = 3.68e-20'>
  <DD>The absolute flux per unit frequency at an AB magnitude of zero.  This is used
  to convert the calibration  AB magnitudes to absolute flux by the formula
  <P>
  <PRE>
      f_nu = fnuzero * 10. ** (-0.4 * m_AB)
  </PRE>
  <P>
  The flux units are also determined by this parameter.  However, the
  frequency to wavelength interval conversion assumes frequency in hertz.
  The default value is based on a calibration of Vega at 5556 Angstroms of
  3.52e-20 ergs/cm2/s/Hz for an AB magnitude of 0.0336.  This default value
  is that used in earlier versions of this task which did not allow the
  user to change this calibration.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_extinction">extinction = &lt;no default&gt;</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='extinction' Line='extinction = &lt;no default&gt;'>
  <DD>Extinction file used to make second order extinction corrections across
  the bandpasses.  The default value is  redirected to the package
  parameter of the same name.  See <B>lcalib</B> for a list of standard
  extinction files.  Normally the input spectra will not be extinction
  corrected.  But if they are this file will be used to remove the
  extinction and then the same file should be specified in <B>sensfunc</B>.
  Note that one can choose to use a null extinction file in both.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_caldir">caldir = "<TT>)_.caldir</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='caldir' Line='caldir = ")_.caldir"'>
  <DD>Calibration directory containing standard star data.  The
  default value of "<TT>)_.caldir</TT>" means to use the package parameter "<TT>caldir</TT>".
  A list of standard calibration directories may be obtained by listing the
  file "<TT>onedstds$README</TT>"; for example:
  <P>
  <PRE>
      cl&gt; page onedstds$README
  </PRE>
  <P>
  The user may copy or create their own calibration files and specify the
  directory.  The directory "<TT></TT>" refers to the current working directory.  The
  standard calibration directory for blackbody curves is
  "<TT>onedstds$blackbody/</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_observatory">observatory = "<TT>)_.observatory</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='observatory' Line='observatory = ")_.observatory"'>
  <DD>Observatory at which the spectra were obtained if not specified in the
  image header by the keyword OBSERVAT.  The default is a redirection to look
  in the parameters for the parent package for a value.  The observatory may
  be one of the observatories in the observatory database, "<TT>observatory</TT>" to
  select the observatory defined by the environment variable "<TT>observatory</TT>" or
  the parameter <B>observatory.observatory</B>, or "<TT>obspars</TT>" to select the
  current parameters set in the <B>observatory</B> task.  See help for
  <B>observatory</B> for additional information.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interact">interact = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interact' Line='interact = no'>
  <DD>If set to no, then the default wavelength set (either that from the star
  calibration file or the set given by the <I>bandwidth</I> and <I>bandsep</I>
  parameters) is used to select wavelength points along the spectrum where the
  sensitivity is measured. If set to yes, the spectra may be plotted
  and the bandpasses adjusted.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_graphics">graphics = "<TT>stdgraph</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = "stdgraph"'>
  <DD>Graphics output device for use with the interactive mode.  Normally this is
  the user's graphics terminal.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_cursor">cursor = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cursor' Line='cursor = ""'>
  <DD>Graphics cursor input for use with the interactive mode.  When null the
  standard graphics cursor is used otherwise the specified file is used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_star_name">star_name</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='star_name' Line='star_name'>
  <DD>The name of the star observed in the current series of spectra.  Calibration
  data for the star must be in the specified calibration directory "<TT>caldir</TT>".
  This is normally a interactive query parameter and should not be specified on
  the command line unless all spectra are of the same standard star.
  </DD>
  </DL>
  <P>
  The following three queried parameters apply if the selected calibration
  file is for a blackbody.
  <DL>
  <DT><B><A NAME="l_mag">mag</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='mag' Line='mag'>
  <DD>The magnitude of the observed star in the band given by the
  <I>magband</I> parameter.  If the magnitude is not in the same band as
  the blackbody calibration file then the magnitude may be converted to
  the calibration band provided the "<TT>params.dat</TT>" file containing relative
  magnitudes between the two bands is in the calibration directory
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_magband">magband</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='magband' Line='magband'>
  <DD>The standard band name for the input magnitude.  This should generally
  be the same band as the blackbody calibration file.  If it is
  not the magnitude will be converted to the calibration band.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_teff">teff</A></B></DT>
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
  The following two parameters are queried if the image does not contain
  the information.
  <DL>
  <DT><B><A NAME="l_airmass">airmass, exptime</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='airmass' Line='airmass, exptime'>
  <DD>If the airmass and exposure time are not in the header nor can they be
  determined from other keywords in the header then these query parameters
  are used to request the airmass and exposure time.  The values are updated
  in the image.
  </DD>
  </DL>
  <P>
  The following parameter is for the task to make queries.
  <DL>
  <DT><B><A NAME="l_answer">answer</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='answer' Line='answer'>
  <DD>Interactive query parameter.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_cursor_keys">CURSOR KEYS</A></H2>
  <! BeginSection: 'CURSOR KEYS'>
  <UL>
  <PRE>
  ?  Display help page
  a  Add a new band by marking the endpoints
  d  Delete band nearest the cursor in wavelength
  r  Redraw current plot
  q  Quit with current bandpass definitions
  w  Window plot  (follow with <TT>'?'</TT> for help)
  I  Interrupt task immediately
  <P>
  :show	Show current bandpass data
  </PRE>
  </UL>
  <! EndSection:   'CURSOR KEYS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Observations of standard stars are integrated over calibration bandpasses
  and written to an output file along with the associated calibration
  fluxes.  The fluxes are obtained from tabulated standard star calibration
  files or a model flux distribution (currently just a blackbody) based on
  the magnitude and spectral type of the star.  The output data is used by
  the task <B>sensfunc</B> to determine the detector sensitivity function and
  possibly the extinction.  The spectra are required to be dispersion
  corrected.  The input spectra may be in either "<TT>onedspec</TT>" or "<TT>echelle</TT>"
  format and may have many different observation apertures.  The spectra may
  also be beam switched and use the a record number extension format.
  <P>
  The input spectra are specified by a list of names or root names if using
  the record number extension format.  In the latter case each name in the
  list has each of the specified record numbers appended.  A subset of the
  input spectra may be selected by their aperture numbers using the parameter
  <I>apertures</I>.  The spectrum name, aperture number, and title are printed
  to the standard output.  The airmass is required but if absent from the image
  header it may be computed from the observation header parameters and the
  latitude task parameter (normally obtained from the <B>observatory</B> task).
  If the airmass cannot be computed, due to missing keywords, then a
  query is made for the airmass.  The airmass is then updated in the header.
  <P>
  The name of the standard star or blackbody curve is obtained by querying
  the user.  If the parameter <I>samestar</I> is yes or beam switch mode is
  selected then all spectra are assumed to be of the same standard star and
  the query is made once.  If the parameter is no then a query is made for
  each aperture.  This allows each aperture to contain a different standard
  star.  Note however that multiple observations with the same aperture
  number must be of the same standard star.
  <P>
  The standard star name is either the name of an actual standard star or of
  a blackbody calibration.  The latter generally have a star name consisting
  of just the standard bandpass identifier.  If the standard star name is not
  recognized a menu of the available standard stars in the calibration
  directory, the file "<TT>standards.men</TT>", is printed and then the query is
  repeated.  Thus, to get a list you can type ?  or help.
  <P>
  The standard star names must map to a file containing tabulated
  calibration data.  The calibration filename is formed from the star
  name with blanks, "<TT>+</TT>", and "<TT>-</TT>" removed, converted to lower case, and
  the extension "<TT>.dat</TT>" added.  This name is appended to a calibration
  directory, so the directory name must have an appropriate directory
  delimiter such as "<TT>$</TT>" or "/"<TT>.  Generally one of the system calibration
  directories is used but one may copy and modify or create new
  calibration files in a personal directory.  For the current working
  directory the calibration directory is either null or "./</TT>".
  <P>
  The calibration files may include comment parameter information consisting
  of the comment character <TT>'#'</TT>, a parameter name, and the parameter value.
  These elements are separated by whitespace.  Any other comment where the
  first word does not match one of the allowed parameter names is ignored by
  the program.  The parameter names are "<TT>type</TT>" identifying the type of
  calibration file, "<TT>units</TT>" identifying wavelength units, "<TT>band</TT>" identifying
  the band for magnitudes, and "<TT>weff</TT>" identifying the effective wavelength of
  the band.
  <P>
  There are two types of standard star calibration files as described
  below.
  <P>
  <DL>
  <DT><B><A NAME="l_STANDARD">STANDARD STAR CALIBRATION FILES</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='STANDARD' Line='STANDARD STAR CALIBRATION FILES'>
  <DD>This type of file is any file that does not contain the parameter "<TT>type</TT>"
  with a value of "<TT>blackbody</TT>".  The only other parameter used by this type of
  calibration file is the "<TT>units</TT>" parameter for the wavelength units.  If the
  units are not specified then the wavelengths default to Angstroms.  All
  older calibration files will have no parameter information so they are
  interpreted as standard star calibration files with wavelengths in
  Angstroms.
  <P>
  The calibration files consist of lines with wavelengths, calibration
  magnitudes, and bandpass widths.  The magnitudes are m_AB defined as
  <P>
  <PRE>
      m_AB(star) = -2.5 * log10 (f_nu) - 48.60
  </PRE>
  <P>
  where f_nu is in erg/cm^2/s/Hz.  The m_AB calibration magnitudes
  are converted to absolute flux per unit frequency using the
  parameter <I>fnuzero</I> defined by
  <P>
  <PRE>
      f_nu = fnuzero * 10. ** (-0.4 * m_AB)
  </PRE>
  <P>
  Thus, <I>fnuzero</I> is the flux at m_AB of zero.  The flux units are
  determined by this number.  The default value was chosen such that Vega
  at 5556 Angstroms has an AB magnitude of 0.0336 and a flux of 3.52e-20
  ergs/cm2/s/Hz.  This is the same value that was used by all previous
  versions of this task.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B><A NAME="l_BLACKBODY">BLACKBODY CALIBRATION FILES</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='BLACKBODY' Line='BLACKBODY CALIBRATION FILES'>
  <DD>This type of file has the comment parameter "<TT>type</TT>" with a value of
  "<TT>blackbody</TT>".  It must also include the "<TT>band</TT>" and "<TT>weff</TT>"
  comment parameters.  If no "<TT>units</TT>" comment parameter is given then
  the default units are Angstroms.
  <P>
  The rest of the file consists of lines with wavelengths, m_AB of a zero
  magnitude star (in that band magnitude system), and the bandpass widths.
  The m_AB are defined as described previously.  Normally all the m_AB values
  will be the same though it is possible to adjust them to produce a
  departure from a pure blackbody flux distribution.
  <P>
  The actual m_AB calibration magnitudes for the star are obtained by
  the relation
  <P>
  <PRE>
      m_AB(star) = mag + m_AB(m=0) -
          2.5 * log10 (B(weff,teff)/B(w,teff))
  </PRE>
  <P>
  where m is the magnitude of the star in the calibration band, m_AB(m=0) is
  the calibration value in the calibration file representing the magnitude of
  a m=0 star (basically the m_AB of Vega), weff is the effective wavelength
  for the calibration file, and teff is the effective temperature of the
  star.  The function B(w,T) is the blackbody function in f_nu that provides
  the shape of the calibration.  Note how the normalization is such that at
  weff the last term is zero and m_AB(star) = m + m_AB(m=0).
  <P>
  The m_AB(star) computed using the calibration values and the blackbody
  function are then in the same units and form as for the standard
  star files.  The conversion to f_nu and the remaining processing
  proceeds in the same way as for standard star calibration data.
  <P>
  The parameters \Imag and <I>teff</I> are specified by the user for each
  star as described in the section BLACKBODY PARAMETERS.  These parameters
  are queried by the task for each star (unless forced to a value on the
  command line).
  </DD>
  </DL>
  <P>
  The beam switch mode is selected with the <I>beam_switch</I> parameter.
  This mode requires that all apertures are of the same star, the header
  keyword OFLAG be present to identify object and sky spectra, and that
  the sequence of spectra specified are paired such that if an object
  spectrum is encountered first the next spectrum for that aperture
  (spectra from other apertures may appear in between) is a sky spectrum
  or the reverse.  These restrictions are not fundamental but are made so
  that this mode behaves the same as with the previous version of this
  task.  The sky spectrum is subtracted from the object spectrum and the
  result is then used in generating the observed intensities in the calibration
  bandpasses.
  <P>
  If the spectra have been extinction corrected (EX-FLAG = 0) the
  extinction correction is removed.  The specified extinction file is
  used for this operation and so must be the same as that used when the
  extinction correction was made.  The airmass is also required in this step
  and, if needed to compute the airmass, the observatory specified in the
  image or observatory parameter is used.  The
  treatment of extinction in this task is subtle.  The aim of this task
  is to produce observed integrated instrumental intensities without
  extinction correction.  Thus, the extinction correction is removed from
  extinction corrected spectra.  However, a correction is made for an
  extinction gradient across the bandpasses.  This is done by applying an
  extinction correction, integrating across the bandpass, and then
  correcting the integrated intensity for the extinction at the center of
  the bandpass.  An alternative way to look at this is that the integral
  is weighted by the ratio of the extinction correction at each pixel to
  the extinction correction at the center of the bandpass.  This
  correction or weighting is why the extinction file and latitude are
  parameters in this task even though for nonextinction corrected spectra
  they appear not to be needed.
  <P>
  The observed instrumental intensities are integrated within a set of
  bandpasses by summing the pixels using partial pixels at the bandpass
  edges.  Initial bandpasses are defined in one of two ways.  A set of
  evenly spaced bandpasses of constant width covering the range of the
  input spectrum may be specified using the parameters <I>bandwidth</I>
  and <I>bandsep</I> in the same units as the spectrum dispersion.  If
  these parameters have the value INDEF then the bandpasses from the
  calibration file which are entirely within the spectrum are selected.
  Generally these bandpasses are the actual measured bandpasses though
  one is free to make calibration files using estimated points.  The
  calibration bandpasses are preferable because they have been directly
  measured and they have been placed to avoid troubles with spectral
  lines.  However, when the coverage or resolution is such that these
  bandpasses do not allow a good determination of the instrumental
  response the evenly spaced bandpasses may be needed.  The calibration
  fluxes are linearly interpolated (or extrapolated) from the calibration
  data points to the defined bandpasses.
  <P>
  Each spectrum adds a line to the output file containing the spectrum image
  name, the sky spectrum image name if beam switching, the aperture or beam
  number, the number of points in the spectrum, the exposure time, airmass,
  wavelength range, and title.  If the airmass is not found in the image
  header it is computed using the latitude parameter and observation
  information from the header.  If the airmass cannot be computed, due to
  missing keywords, then a query is made for the airmass.
  <P>
  Following the spectrum information, calibration data is added for each
  bandpass.  The bandpass wavelength, absolute flux (per Angstrom),
  bandpass width, and observed instrumental intensity in the bandpass are
  added to the output file.  As discussed above, the observed intensity
  does not include an extinction term but does apply a small correction
  or weighting for the variation of the extinction across the bandpass.
  <P>
  The setting and editing of the bandpasses may be performed
  interactively if the <I>interact</I> flag is set.  In this case the user
  is queried for each spectrum.  The answers to this query may be "<TT>no</TT>" or
  "<TT>yes</TT>" to skip editing or edit the bandpasses for this spectrum, "<TT>NO</TT>" or
  "<TT>YES</TT>" to skip or not skip editing all spectra of the same aperture with
  no further queries for this aperture, and "<TT>NO!</TT>" or "<TT>YES!</TT>" to skip
  editing or edit all spectra with no further queries.
  <P>
  When editing the bandpasses a graph of the spectrum is made with the
  bandpasses plotted at the computed intensity per pixel.  The cursor and
  colon commands available are summarized in the section CURSOR KEYS.
  Basically bandpasses may be added or deleted and the current bandpass
  data may be examined.  Additional keys allow the usual windowing and
  cursor mode operations.  When satisfied with the bandpasses exit with
  <TT>'q'</TT>.  The edited bandpasses for that aperture remain in effect until
  changed again by the user.  Thus if there are many spectra from the
  same aperture one may reply with "<TT>NO</TT>" to queries for the next spectra
  to accept the current bandpasses for all other spectra of the same
  aperture.
  <P>
  BLACKBODY PARAMETERS
  <P>
  When a blackbody calibration is selected (the calibration file selected by
  the <I>star_name</I> parameter has "<TT># type blackbody</TT>") there are two
  quantities needed to scale the blackbody to the observation.  These are the
  magnitude of the star in the same band as the observation and the effective
  temperature.  The magnitude is used for the flux scaling and the effective
  temperature for the shape of the flux distribution.  The values are
  obtained or derived from the user specified parameters <I>mag</I>,
  <I>magband</I>, and <I>teff</I>.  This section describes how the the
  values are derived from other parameters using the data file "<TT>params.dat</TT>"
  in the calibration directory.
  <P>
  The effective temperature in degrees Kelvin may be specified directly or it
  may be derived from a spectral type for the star.  In the latter case the
  file "<TT>params.dat</TT>" is searched for the effective temperature.  The file
  consists of lines with the first value being the spectral type and the
  second the effective temperature.  Other columns are described later.  The
  spectral type can be any string without whitespace that matches what is in
  the file.  However, the program finds the last spectral type that matches
  the first two characters when there is no complete match.  This scheme is
  intended for the case where the spectral types are of the form A0I, A0III,
  or A0V, where A can be any spectral type letter OBAFGKM, the single digit
  subtype is between 0 and 9, and the luminousity class is one of I, III, or
  V.  The two character match selects the last spectral type independent of
  the luminosity class.  The standard file "<TT>onedstds$blackbody/params.dat</TT>"
  uses these spectral type identifiers with the dwarf class acting as the
  default.
  <P>
  The magnitude band is specified along with the input magnitude.  If the
  band is the same as the calibration band given in the calibration file then
  no further transformation is required.  However if the magnitude is
  specified in a different band, a conversion is performed using information
  from the "<TT>params.dat</TT>" file based on the spectral type of the star.
  <P>
  When an effective temperature is specified rather and a spectral type then
  the nearest tabulated temperature for the spectral types that have "<TT>V</TT>" as
  the third character is used.  For the standard spectral type designations
  this means that when an effective temperature is specified the dwarf
  spectral type is used for the magnitude transformation.
  <P>
  As mentioned previously, the "<TT>params.dat</TT>" data file has additional columns
  following the spectral type and effective temperature.  These columns are
  relative magnitudes in various bands.  The standard file has V magnitudes
  of zero so in this case the columns are also the X-V colors (where X is the
  appropriate magnitude).  Given the spectral type the relative magnitudes
  for the calibration band, m_1, and the input magnitude band, m_2, are found
  and the calibration magnitude for the star is given by
  <P>
  <PRE>
      m_calibration = m_input + m_1 - m_2
  </PRE>
  <P>
  If one of the magnitudes is missing,  given as "<TT>INDEF</TT>" because the
  transformation is not available for the spectral type, the last spectral
  type matching the first two characters which does specify the two
  magnitudes will be used.  For example if there is no information for a
  B3III star for a M-J color then the spectral type B3V might be used.
  <P>
  In order for the program to determine the bands for each column in the data
  file there must be a comment before the data with the column names.  It must
  begin with "<TT># Type Teff</TT>" and then be followed by the same band identifiers
  used in the blackbody calibration files and as specified by the
  <I>magband</I> parameter.  Any amount whitespace (space or tab) is used to
  separate the various fields in the comment and in the fields of the table.
  For example the file might have the comment
  <P>
  <PRE>
      # Type    Teff     V      J      H      K      L   Lprime    M
  </PRE>
  <P>
  identifying the third column of the file as the V magnitude and the
  ninth file as the M magnitude.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  To compile observations of three standard stars using a beam
  switched instrument like the IIDS:
  <P>
  <PRE>
      cl&gt; standard.recformat=yes
      cl&gt; standard nite1 1001-1008 std beam_switch+ interact-
      [nite1.1001][0]: HZ 44 - Night 1
      [nite1.1004][0]: HZ 44 - Night 1
      [nite1.1005][0]: HZ 44 - Night 1
      [nite1.1008][0]: HZ 44 - Night 1
      Star name in calibration list: hz 44
      cl&gt; standard nite1 1009-1016 std beam_switch+ interact-
      	...
      cl&gt; standard nite1 1017-1024 std beam_switch+ interact-
      	...
  </PRE>
  <P>
  This will create a file "<TT>std</TT>" which will contain sensitivity measurements
  from the beam-switched observations of the three standard stars given.
  Note that <B>standard</B> is run separately for each standard star.
  <P>
  The spectra will be from the images: nite1.1001, nite.1002 ... nite1.1024,
  and the default calibration file, "<TT>onedstds$irscal.dat</TT>" will be used.
  <P>
  2.  For echelle spectra all apertures, the orders, are of the same star and
  so the samestar parameter is set.  Usually the resolution is much higher than
  the calibration data so in order to get sufficient coverage bandpasses must
  be interpolated from the calibration data.  Therefore the evenly spaced
  bandpasses are used.
  <P>
  <PRE>
      cl&gt; standard.recformat=no
      cl&gt; standard.samestar=yes
      cl&gt; standard ech001.ec std bandwidth=10 bandsep=15
      [ech001.ec][0]: Feige 110
      Star name in calibration list: feige 110
      [ech001.ec][0]: Edit bandpasses? (no|yes|NO|YES|NO!|YES!): yes
      [ech001.ec][1]: Edit bandpasses? (no|yes|NO|YES|NO!|YES!): yes
      [ech001.ec][2]: Edit bandpasses? (no|yes|NO|YES|NO!|YES!): NO!
  </PRE>
  <P>
  3. To use a blackbody infrared calibration where the V magnitude of
  the star is known.
  <P>
  <PRE>
      cl&gt; standard std1.ms std caldir=onedstds$blackbody/
      std1.ms(1): Standard Star
      Star name in calibration list: J
      Magnitude of star: 10.3
      Magnitude type (|V|J|H|K|L|Lprime|M|): V
      Effective temperature or spectral type: B3III
      WARNING: Effective temperature for B3III not found - using B3V
      Blackbody: V = 10.30, J = 10.32, Teff = 19000
      std1[1]: Edit bandpasses? (no|yes|NO|YES|NO!|YES!) (yes): 
  </PRE>
  <P>
  Note the warning message and the confirmation information.
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_revisions">REVISIONS</A></H2>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_STANDARD">STANDARD V2.10.4</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='STANDARD' Line='STANDARD V2.10.4'>
  <DD>The calibration files can be defined to compute blackbody values.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_STANDARD">STANDARD V2.10.3</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='STANDARD' Line='STANDARD V2.10.3'>
  <DD>A query for the airmass and exposure time is now made if the information
  is not in the header and cannot be computed from other header keywords.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_STANDARD">STANDARD V2.10</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='STANDARD' Line='STANDARD V2.10'>
  <DD>Giving an unrecognized standard star name will page a list of standard
  stars available in the calibration directory and then repeat the
  query.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  observatory, lcalib, sensfunc
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'CURSOR KEYS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>