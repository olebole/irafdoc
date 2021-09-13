bswitch — Beam-switch strings of spectra to make obj-sky pairs
==============================================================

**Package: iids**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>bswitch (Sep87)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.imred.iids/noao.imred.irs</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>bswitch (Sep87)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>bswitch</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  bswitch - generate sky-subtracted accumulated spectra
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  bswitch input records
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The root name for the input spectra to be beam-switched.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_records">records</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='records' Line='records'>
  <DD>The range of spectra to be included in the beam-switch operation.
  Each range item will be appended to the root name to form an image
  name. For example, if "<TT>input</TT>" is "<TT>nite1</TT>" and records is "<TT>1011-1018</TT>",
  then spectra nite1.1011, nite.1012 ... nite1.1018 will be included.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>New spectra are created by the beam-switch operation. This parameter
  specifies the root name to be used for the created spectra.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_start_rec">start_rec = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='start_rec' Line='start_rec = 1'>
  <DD>Each new spectrum created has "<TT>output</TT>" as its root name and a trailing
  number appended. The number begins with start_rec and is incremented
  for each new spectrum. For example, if "<TT>output</TT>" is given as "<TT>nite1b</TT>"
  and start_rec is given as 1001, then new spectra will be created as
  nite1b.1001, nite1b.1002 ...
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_stats">stats = "<TT>stats</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='stats' Line='stats = "stats"'>
  <DD>A file by this name will have statistical data appended to it, or created
  if necessary. If a null file name is given ("<TT></TT>"), no statistical output
  is given. For each aperture, a listing of countrates for each
  observation is given relative to the observation with the highest rate.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ids_mode">ids_mode = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ids_mode' Line='ids_mode = yes'>
  <DD>If the data are taken under the usual IIDS "<TT>beam-switch</TT>" mode, this
  parameter should be set to yes so that accumulations will be performed
  in pairs. But if the data are taken where there is no sky observation
  or different numbers of sky observations, ids_mode should be set to no.
  If weighting is in effect, ids_mode=yes implies weighting of the
  object-sky sum; if ids_mode=no, then weighting is applied to the
  object and sky independently because then there is no guarantee that
  an object and sky observation are related.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_extinct">extinct = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='extinct' Line='extinct = yes'>
  <DD>If set to yes, a correction for atmospheric extinction is applied.
  The image header must have either a valid entry for AIRMASS or
  for hour angle (or right ascension and sidereal time) and declination.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_weighting">weighting = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='weighting' Line='weighting = no'>
  <DD>If set to yes, the entire spectrum or a specified region will be used
  to obtain a countrate indicative of the statistical weight to be
  applied to the spectrum during the accumulations.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_subset">subset = 32767</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='subset' Line='subset = 32767'>
  <DD>A subset value larger than the number of independent spectra to be
  added indicates that the operation is to produce a single spectrum
  for each aperture regardless of how many input spectra are entered.
  If subset is a smaller number, say 4, then the accumulations
  are written out after every 4 spectra and then re-initialized to zero
  for the next 4.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_wave1">wave1 = 0.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wave1' Line='wave1 = 0.0'>
  <DD>If weighting=yes, this parameter indicates the starting point in the
  spectrum for the countrate to be assessed. For emission-line objects,
  this is particularly useful because the regime of information is then
  confined to a narrow spectral region rather than the entire spectrum.
  Defaults to the beginning of the spectrum.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_wave2">wave2 = 0.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wave2' Line='wave2 = 0.0'>
  <DD>This provides the ending wavelength for the countrate determination.
  Defaults to the endpoint of the spectrum.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_observatory">observatory = "<TT>observatory</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='observatory' Line='observatory = "observatory"'>
  <DD>Observatory at which the spectra were obtained if
  not specified in the image header by the keyword OBSERVAT.  The
  observatory may be one of the observatories in the observatory
  database, "<TT>observatory</TT>" to select the observatory defined by the
  environment variable "<TT>observatory</TT>" or the task <B>observatory</B>, or
  "<TT>obspars</TT>" to select the current parameters set in the <B>observatory</B>
  task.  See help for <B>observatory</B> for additional information.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_extinction">extinction = "<TT>)_.extinction</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='extinction' Line='extinction = ")_.extinction"'>
  <DD>The the name of the file containing extinction values.
  Required if extinct=yes.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Data from multiaperture spectrographs are summed according to
  aperture number and sky subtracted if sky observations are available.
  Data for up to 50 apertures may be simultaneously accumulated.
  The accumulated spectra are written to new images. 
  <P>
  The exposure times for each observation may be different. All
  internal computations are performed in terms of count rates,
  and converted back to counts (for statistical analysis) prior to writing
  the new image. Therefore, the time on the sky and object may
  be different as well. When these extensions to the normal
  mode are required, the flag ids_mode must be set to no.
  Then object and sky accumulations are performed totally
  independently and a difference is derived at the conclusion
  of the operation.
  <P>
  If ids_mode is set to yes, then the usual IIDS/IRS "<TT>beam-switch</TT>"
  observing mode is assumed. This implies that an equal number of
  sky and object spectra are obtained through each aperture
  after 2N spectra have been accumulated, where N is the number
  of instrument apertures (2 for the IIDS/IRS). It is also assumed
  that the object and sky exposure times are equal for each aperture.
  Note that the "<TT>nebular</TT>" mode (where all instrument apertures
  point at an extended object simultaneously, and then all apertures
  point at sky simultaneously) is an acceptable form for
  beam-switched data in ids_mode.
  <P>
  The accumulations are optionally weighted by the countrate
  over a region of the spectrum to improve the statistics during
  variable conditions. The user may specify the region of spectrum
  by wavelength. In ids_mode, the statistics are obtained from
  object-sky differences; otherwise, the statistics are performed
  on object+sky and sky spectra separately.
  <P>
  The spectra may be extinction corrected if this has not already
  been performed.
  In order to perform either the extinction correction or the
  weighting process, the spectra must have been placed on a linear
  wavelength scale (or linear in the base 10 logarithm).
  <P>
  Strings of spectra are  accumulated to produce a single
  summed spectrum for each observing aperture. But in some cases
  it is desirable to produce summed spectra from subsets of the
  entire string to evaluate the presence of variations either due
  to observing conditions or due to the physical nature of the
  object. A subset parameter may be set to the frequency at which
  spectra are to be summed.
  <P>
  In order that the processing occur with minimal user interaction,
  elements from the extended image header are used to direct the
  flow of operation and to obtain key observing parameters.
  The required parameters are: object/sky flag (OFLAG=1/0), exposure
  time in seconds (ITM), beam (that is, aperture) number (BEAM-NUM), airmass (AIRMASS)
  or alternatively hour angle (HA) and declination (DEC), or
  right ascension (RA), sidereal time (ST), declination (DEC), and the
  observatory (OBSERVAT),
  starting wavelength (W0), and wavelength increment per channel (WPC),
  where the names in parenthesis are the expected keywords in the
  header.  If the observatory is not specified in the image the
  observatory parameter is used.  See <B>observatory</B> for further
  details on the observatory database.
  <P>
  The following header flags are used as well: DC_FLAG
  for dispersion corrected data (must=0), BS_FLAG for beam-switching
  (must not be 1 which indicates the operation was already done),
  EX_FLAG for extinction correction (if = 0 extinction is assumed already
  done).  
  <P>
  The headers may be listed with the IMHEADER task, setting
  the parameter "<TT>long</TT>" = yes. The values for the parameters follow 
  the rules used for IIDS and IRS data.
  <P>
  After the beam-switch operation, the newly created spectra will
  have header elements taken from the last object spectrum.
  A few parameters will be updated to reflect the operation
  (e.g. integration time, processing flags).
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  The following example will accumulate a series of 16 spectra obtained
  in the normal beam-switched mode and create two new extinction corrected
  spectra having names nite1bs.1 and nite1bs.2:
  <P>
  	cl&gt; bswitch nite1 1011-1026 nite1bs 1
  <P>
  The following example performs the same functions but accumulates the data
  to produce 8 new spectra representing the individual object-sky pairs:
  <P>
  	cl&gt; bswitch nite1 1011-1026 nite1bs 1 subset=4
  <P>
  The following example produces an extinction corrected spectrum for every
  input spectrum. Note that ids_mode is set to off to generate separate object and
  sky sums, and subset is set to 2 so that every pair of spectra (one object and
  one sky) are written out as two new spectra:
  <P>
  	cl&gt; bswitch nite1 1011-1026 nite1bs 1 subset=2 ids_mode-
  <P>
  The next example produces a pair of spectra for each of 3 independent
  objects observed, provided that each was observed for the same number
  of observations (16 in this case).
  <P>
  <PRE>
  	cl&gt; bswitch nite1 1011-1026,1051-1066,1081-1096 nite1bs 1 \<BR>
  	&gt;&gt;&gt; subset=16
  </PRE>
  <P>
  The next example shows how to use the weighting parameters where
  the indicative flux is derived from the region around the emission-line
  of 5007A.
  <P>
  <PRE>
  	cl&gt; bswitch nite1 1011-1026 nite1bs 1 weighting- \<BR>
  	&gt;&gt;&gt; wave1=4990, wave2=5020
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_time_requirements">TIME REQUIREMENTS</A></H2>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  The principle time expenditure goes toward extinction correcting the
  data. For IIDS type spectra (length=1024 pixels), approximately 30 cpu
  seconds are required to beam-switch a series of 16 spectra.
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  The number of apertures is restricted to 50 and must be labeled
  between 0 and 49 in the image header (the IIDS uses 0 and 1).
  <P>
  Until an image header editor is available, BSWITCH 
  can be applied only to data with properly prepared headers
  such as IIDS/IRS data read by RIDSMTN, RIDSFILE and some data via RFITS.
  <P>
  When used to perform the function of extinction correction only (the
  third example above), the statistics file fails to note the output
  image name for the sky spectrum.
  <P>
  The data must be on a linear wavelength scale.
  The starting wavelength, W0, and a wavelength
  per channel, WPC, are required header information, and the DC_FLAG
  must be set to 0.
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  observatory, sensfunc, imheader, lcalib, ridsmtn, ridsfile, rfits
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>