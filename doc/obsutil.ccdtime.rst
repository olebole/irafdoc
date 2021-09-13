ccdtime — CCD photometry exposure time calculator
=================================================

**Package: obsutil**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>ccdtime (Nov01)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.obsutil</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>ccdtime (Nov01)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>ccdtime</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  ccdtime -- compute time, magnitude, and signal-to-noise for CCDs
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  ccdtime
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_time">time = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='time' Line='time = INDEF'>
  <DD>Time in seconds for output of magnitude at the specified signal-to-noise and
  signal-to-noise at the specified magnitude.  This time applies to all
  filters.  If specified as INDEF then no output at fixed exposure time will
  be produced.  If the value is not greater than zero or less than 100000
  an error is reported.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_magnitude">magnitude = 20.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='magnitude' Line='magnitude = 20.'>
  <DD>Magnitude for output of time at the specified signal-to-noise and
  signal-to-noise at the specified time.  This magnitude applies to all
  filters. If specified as INDEF then no output at fixed magnitude will
  be produced.  If the absolute value of the magnitude is greater than 40
  an error will be reported.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_snr">snr = 20.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='snr' Line='snr = 20.'>
  <DD>Signal-to-noise ratio for output of time at the specified magnitude and
  magnitude at the specified time.  This signal-to-noise ratio applies to all
  filters. If specified as INDEF then no output at fixed signal-to-noise
  ratio will be produced.  If the value is not greater than zero or less than
  100000 an error is reported.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B><A NAME="l_database">database = "<TT>ccdtime$kpno.dat</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='database' Line='database = "ccdtime$kpno.dat"'>
  <DD>Database file for telescope, filter, and detector information.  The format
  of this file is described elsewhere.  This file is typically a standard
  file from the logical directory "<TT>ccdtime$</TT>" or a personal copy in a
  user's directory.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_telescope">telescope = "<TT>?</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='telescope' Line='telescope = "?"'>
  <DD>Telescope entry from the database.  If "<TT>?</TT>" a list of telescopes in the
  database is produced.  The name must match the entry name in the database
  but ignoring case.  If the same telescope has multiple focal ratios then
  there must be multiple entries in the database.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_detector">detector = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='detector' Line='detector = ""'>
  <DD>Detector entry from the database.  If "<TT>?</TT>" a list of detectors in the
  database is produced.  The name must match the entry name in the database
  but ignoring case.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_sum">sum = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sum' Line='sum = 1'>
  <DD>CCD on-chip summing or binning factor.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_seeing">seeing = 1.5</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='seeing' Line='seeing = 1.5'>
  <DD>Expected seeing (FWHM) in arc seconds.  The number of pixels used for computing
  the total star counts and the signal-to-noise is given by 1.4 times the square
  of the seeing converted to pixels and rounded up.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_airmass">airmass = 1.2</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='airmass' Line='airmass = 1.2'>
  <DD>Airmass for observation.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_phase">phase = 0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='phase' Line='phase = 0.'>
  <DD>Moon phase in days (0-28) for the estimation of sky brightness.  A
  phase of zero is new moon or dark sky conditions and a phase of 14
  is full moon.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B><A NAME="l_f1">f1 = "<TT>U</TT>", f2 = "<TT>B</TT>", f3 = "<TT>V</TT>", f4 = "<TT>R</TT>", f5 = "<TT>I</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='f1' Line='f1 = "U", f2 = "B", f3 = "V", f4 = "R", f5 = "I"'>
  <DD>Filters for which to compute the CCD information.  If given as "<TT>?</TT>"
  a list of filters in the database is produced.  If the name (ignoring
  case) is not found then it is ignored.  A null name, that is "<TT></TT>", is used
  to eliminate listing of a filter.  If more than five filters is desired
  each of the parameters may be a comma delimited list of desired filters.
  Note that whitespace is preserved so "<TT>U, V</TT>" will expand to "<TT>U</TT>" and "<TT> V</TT>"
  and so will not match "<TT>V</TT>" in the database.  Use "<TT>U,V</TT>" instead.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  A telescope, CCD detector, and list of filters is selected from a database
  to define the expected photon/electron count rates.  These rates along with
  a specified seeing and airmass are used to estimate the signal-to-noise
  ratio (SNR) for a stellar observation in each filter.  The output provides
  three results per filter; the exposure time to achieve a desired SNR for a
  given magnitude, the magnitude to achieve a desired SNR in a given time, and
  the SNR at a specified magnitude and exposure time.  With each of these,
  the number of star photons (or CCD electrons) in an area 1.4 times the
  square of the seeing, the number of sky photons per pixel, and the RMS noise
  contributions from photon noise in the star, the sky, and the detector
  noise from dark current and read out noise are given.  Note that least two
  of the time, magnitude, and signal-to-noise ratio must be specified but if
  one is INDEF then output with that quantity fixed will be skipped or, in
  other words, only the output where the quantity is computed is produced.
  <P>
  The calibration information needed to define the count rates are
  taken from a database file.  This file may be standard ones given in
  the logical directory "<TT>ccdtime$</TT>" or the user may create their own.
  The database contains entries organized by telescope name (which may
  include a focal ratio if there are multiple ones), detector name,
  and filter name.  One of the standard files may be used as a template.
  <P>
  The file is actually in free format with whitespace and comments ignored.
  However, following the template formatting makes it easy to see the logical
  structure.  All lines, except the "<TT>end</TT>" line which separates the different
  catagories of entries, consist of a keyword an equal sign, and a value
  separated by whitespace.  An entry begins with one of the keywords
  "<TT>telescope</TT>", "<TT>detector</TT>", or "<TT>filter</TT>" and ends with the beginning of
  a new entry or the "<TT>end</TT>" separator.
  <P>
  A keyword is one of the words shown in the example below.  These keywords
  can also be indexed by the name of a telescope, filter, and/or detector
  entry.  This allows having different transmissions in different filters
  due to correctors, different scales for different detectors which may
  have fore-optics, etc.
  <P>
  Specifically a keyword in the telescope section may have arguments
  from the filter or detector entries, a keyword in the filter section may
  have arguments from the telescope and detector entries, and a keyword
  in the detector section may have arguments from the telescope and filter
  entries.  The formats are keyword, keyword(arg), and keyword(arg,arg).
  The arg fields must match an entry name exactly (without the quotes)
  and there can be no whitespace between the keyword and (, between (
  and the argument, between the arguments and the comma, and between the
  last argument and the closing ).  The software will first look for
  keywords with both arguments in either order, then for keywords with
  one argument, and then for keywords with no arguments.
  <P>
  Below is an example of each type of entry:
  <P>
  <PRE>
      telescope = "0.9m"
  	    aperture = 0.91
  	    scale = 30.2
  	    transmission = 1.0
  	    transmission(U) = 0.8
  	    transmission(U,T1KA) = 0.7
  <P>
      filter = "U"
  	    mag = 20
  	    star = 18.0
  	    extinction = 0.2
  	    sky0 = 22.0
  	    sky1 = -0.2666
  	    sky2 = -.00760
  <P>
      detector = "T1KA"
  	    rdnoise = 3.5
  	    dark = 0.001
  	    pixsize = 24
  	    U = 0.36
  	    B = 0.61
  	    V = 0.71
  	    R = 0.78
  	    I = 0.60
  </PRE>
  <P>
  In the example, a transmission of 0.7 will be used if the filter is U
  and the detector is T1KA, a value of 0.8 if the filter is U and the
  detector is not T1KA, and a value of 1 for all other cases.
  <P>
  The telescope entry contains the aperture diameter in meters, the
  scale in arcsec/mm, and a transmission factor.  The transmission factor is
  mostly a fudge factor but may be useful if a telescope has various
  configurations with additional mirrors and optics.
  <P>
  The filter entry contains a fiducial magnitude and the total photon count
  rate for a star of that magnitude.  The units are photons per second
  per square meter of aperture.  An effective extinction in magnitudes/airmass is
  given here.  The sky is defined by a quadratic
  function of lunar phase in days:
  <P>
  <PRE>
  	if (phase &lt; 14)
  	    sky = sky0 + sky1 * phase + sky2 * phase**2
  	else
  	    sky = sky0 + sky1 * (14 - phase) + sky2 * (14 - phase)**2
  </PRE>
  <P>
  One may set the higher order terms to zero if the moon contribution
  is to be ignored.  The units are magnitudes per square arc second.
  <P>
  The detector entry contains the read out noise in electrons, the
  dark current rate in electrons per second, the pixel size in
  microns, and the detective quantum efficiency (DQE); the fraction of
  detected photons converted to electrons.  Note that the actual
  values used are the DQE times the rates given by the filter entries.
  Thus, one may set the DQE values to 1 and adjust the filter values
  or set the star count rates to 1 in the filter and set the actual
  count rates in the DQE values.
  <P>
  The computed quantities are formally given as follows.  The
  star count rates for the specified telescope/detector/filter are:
  <P>
  <PRE>
  	r(star) = star * aperture**2 * transmission *
  	    10**(0.4*(1-airmass)*extinction) * dqe
  </PRE>
  <P>
  where the "<TT>star</TT>", "<TT>aperture</TT>", "<TT>transmission</TT>", "<TT>extinction</TT>", are those
  in the database and the "<TT>dqe</TT>" is the appropriate filter value.  The sky
  rate per pixel is:
  <P>
  <PRE>
  	r(sky) = r(star) * 10 ** (0.4 * (mag - sky)) * pixel**2
  	pixel = pixsize * scale * sum
  </PRE>
  <P>
  where mag is the fiducial magnitude, sky is the value computed using
  the quadratic formula for the specified moon phase and the database
  coefficients, the "<TT>pixel</TT>" size is computed using the CCD pixel size and
  the telescope scale from the database, and sum is the
  specified CCD binning factor.
  <P>
  The number of pixels per star is computed from the seeing as:
  <P>
  <PRE>
  	npix = 1.4 * (seeing / pixel) ** 2
  </PRE>
  <P>
  where the number is rounded up to the next integer and a minimum of 9
  pixels is enforced.  This number is a compromise between a large aperture
  for high SNR stars and a smaller aperture for fainter stars.
  <P>
  The number of star photons/electrons per star of magnitude m,
  the number of sky photons per pixel, and the number of dark current
  electrons, all in exposure time t, are given by:
  <P>
  <PRE>
  	nstar = r(star) * 10 ** (0.4 * (mag - m)) * t
  	nsky = r(sky) * t
  	ndark = dark * t
  </PRE>
  <P>
  where dark is taken from the detector database entry.
  <P>
  Finally the noise contributions, total noise, and signal-to-noise are
  given by:
  <P>
  <PRE>
  	noise star = nstar ** 1/2
  	noise sky = (npix * nsky) ** 1/2
  	noise ccd = (npix * (ndark + rdnoise**2)) ** 1/2
  	noise total = (nstar+npix*(nsky+ndark+rdnoise**2)) ** 1/2
  	SNR = nstar / noise total
  </PRE>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  To get a list of the telescopes, filters, and detectors in a database:
  <P>
  <PRE>
      cl&gt; ccdtime telescope=? detector=? f1=?
      Entries for telescope in database ccdtime$kpno.dat:
  	    0.9m
  	    ...
  	    4m
      Entries for detector in database ccdtime$kpno.dat:
  	    T1KA
  	    T2KA
  	    T2KB
  	    TI2
  	    TI3
  	    T5HA
  	    S2KA
      Entries for filter in database ccdtime$kpno.dat:
  	    U
  	    B
  	    V
  	    R
  	    I
  </PRE>
  <P>
  2.  The following is for the default magnitude and SNR and with
  a 1 second exposure time specified.  The output has some
  whitespace removed to fit on this page.
  <P>
  <PRE>
      cl&gt; ccdtime time=1
      Telescope: 0.9m
      Detector: t1ka
      Database: ccdtime$kpno.dat Telescope: 0.9m    Detector: t1ka
        Sum: 1 Arcsec/pixel: 0.72  Pixels/star: 6.0
        Seeing: 1.5  Airmass: 1.20  Phase: 0.0
  <P>
  <P>
       Filter  Time   Mag   SNR   Star Sky/pix Noise contributions
  					      Star    Sky    CCD
  <P>
  	  U  70.2  20.0  10.0  196.6    8.8  14.02   8.90  10.53
  	  B  13.0  20.0  10.0  208.8   13.0  14.45  10.82  10.51
  	  V  13.2  20.0  10.0  250.7   29.8  15.83  16.37  10.51
  	  R  17.3  20.0  10.0  365.8   95.9  19.13  29.38  10.51
  	  I 126.4  20.0  10.0 1259.2 1609.8  35.49 120.37  10.55
  <P>
  	  U   1.0  15.6  10.0  166.6    0.1  12.91   1.06  10.50
  	  B   1.0  17.4  10.0  170.0    1.0  13.04   3.00  10.50
  	  V   1.0  17.6  10.0  174.6    2.3  13.21   4.50  10.50
  	  R   1.0  17.6  10.0  186.0    5.5  13.64   7.06  10.50
  	  I   1.0  16.7  10.0  207.9   12.7  14.42  10.71  10.50
  <P>
  	  U   1.0  20.0   0.3    2.8    0.1   1.67   1.06  10.50
  	  B   1.0  20.0   1.4   16.0    1.0   4.00   3.00  10.50
  	  V   1.0  20.0   1.6   19.0    2.3   4.36   4.50  10.50
  	  R   1.0  20.0   1.6   21.1    5.5   4.59   7.06  10.50
  	  I   1.0  20.0   0.7   10.0   12.7   3.16  10.71  10.50
  <P>
  </PRE>
  <P>
  Note that the default of 1 second in the last section
  gives the count rates per second for star and sky.
  <P>
  3.  Sometimes one may want to vary one parameter easily on the command
  line or query.  This can be done by changing the parameter to query
  mode.  In the following example we want to change the magnitude.
  <P>
  <PRE>
      cl&gt; ccdtime.magnitude.p_mode=query
      cl&gt; ccdtime.telescope="0.9m"
      cl&gt; ccdtime.detector="t1ka"
      cl&gt; ccdtime.f1=""; ccdtime.f5=""
      cl&gt; ccdtime
      Magnitude (20.):
      Database: ccdtime$kpno.dat   Telescope: 0.9m     Detector: t1ka
        Sum: 1 Arcsec/pixel: 0.72  Pixels/star: 6.0
        Seeing: 1.5  Airmass: 1.20  Phase: 0.0
  <P>
       Filter  Time   Mag   SNR  Star Sky/pix  Noise contributions
  					       Star   Sky    CCD
  <P>
  	  B  13.0  20.0  10.0 208.8    13.0  14.45  10.82  10.51
  	  V  13.2  20.0  10.0 250.7    29.8  15.83  16.37  10.51
  	  R  17.3  20.0  10.0 365.8    95.9  19.13  29.38  10.51
  <P>
      cl&gt; ccdtime 21
      ...
      cl&gt; ccdtime 22
      ...
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_revisions">REVISIONS</A></H2>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_CCDTIME">CCDTIME V2.13</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='CCDTIME' Line='CCDTIME V2.13'>
  <DD>The f1 to f5 parameters were modified to allow lists of filters so
  that more than five filters can be output without changing the parameter
  interface.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_CCDTIME">CCDTIME V2.12</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='CCDTIME' Line='CCDTIME V2.12'>
  <DD>Task added to OBSUTIL package.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_CCDTIME">CCDTIME V2.11.4</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='CCDTIME' Line='CCDTIME V2.11.4'>
  <DD>A error will be reported if the requested time or SNR is not greater
  than zero and less than 100000., or if the absolute value
  of the magnitude is greater than 40.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_CCDTIME">CCDTIME V2.11.2</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='CCDTIME' Line='CCDTIME V2.11.2'>
  <DD>The incorrect usage of a 1 mag/airmass extinction was fixed by adding an
  expected "<TT>extinction</TT>" entry in the filter entries.  Note that old files
  will still give the same result by using an extinction of 1 if the keyword
  is not found.
  <P>
  The database keywords can not be indexed by telescope, filter, and/or
  detector.
  <P>
  The number of pixels per aperture now has a minimum of 9 pixels.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  sptime
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>