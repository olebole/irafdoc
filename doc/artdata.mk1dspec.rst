mk1dspec — Make/add artificial 1D spectra
=========================================

**Package: artdata**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>mk1dspec (Jul95)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.artdata</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>mk1dspec (Jul95)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>mk1dspec</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  mk1dspec -- Make/add artificial 1D spectra
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  mk1dspec input
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>Spectra to create or modify.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output = ""'>
  <DD>Output spectra when modifying input spectra.  If no output spectra are
  given then existing spectra in the input list are modified directly.
  If an output list is given then it must match in number the input list.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ap">ap = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ap' Line='ap = 1'>
  <DD>Image line to be created or modified in images of dimension greater than 1.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_rv">rv = 0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rv' Line='rv = 0.'>
  <DD>Radial velocity (km/s) or redshift, as selected by the parameter <I>z</I>,
  applied to line positions and continuum.  Velocities are converted to
  redshift using the relativistic relation 1+z = sqrt ((1+rv/c)/(1-rv/c)).
  Note the shift is not a shift in the dispersion parameters but in the
  underlying artificial spectrum.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_z">z = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='z' Line='z = no'>
  <DD>Is the velocity parameter a radial velocity or a redshift?
  </DD>
  </DL>
  <P>
  WHEN CREATING NEW SPECTRA
  <DL>
  <DT><B><A NAME="l_title">title = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='title' Line='title = ""'>
  <DD>Image title to be given to the spectra.  Maximum of 79 characters.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ncols">ncols = 512</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ncols' Line='ncols = 512'>
  <DD>Number of columns.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_naps">naps = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='naps' Line='naps = 1'>
  <DD>Number of lines or apertures.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_header">header = "<TT>artdata$stdheader.dat</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='header' Line='header = "artdata$stdheader.dat"'>
  <DD>Image or header keyword data file.  If an image is given then the image header
  is copied.  If a file is given then the FITS format cards are copied.
  This only applies to new images.   The data file consists of lines
  in FITS format with leading whitespace ignored.  A FITS card must begin
  with an uppercase/numeric keyword.  Lines not beginning with a FITS
  keyword such as comments or lower case are ignored.  The user keyword
  output of <B>imheader</B> is an acceptable data file.  See <B>mkheader</B>
  for further information.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_wstart">wstart = 4000., wend = 8000.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wstart' Line='wstart = 4000., wend = 8000.'>
  <DD>Starting and ending wavelengths in Angstroms.  The dispersion is
  determined by these values and the number of columns.
  </DD>
  </DL>
  <P>
  CONTINUUM PARAMETERS
  <DL>
  <DT><B><A NAME="l_continuum">continuum = 1000., slope = 0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='continuum' Line='continuum = 1000., slope = 0.'>
  <DD>Continuum of the starting wavelength at rest and the slope of the continuum.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_temperature">temperature = 5700.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='temperature' Line='temperature = 5700.'>
  <DD>Blackbody continuum temperature in Kelvin.  A value of 0 is used if
  no blackbody continuum is desired.  The intensity level is set by
  scaling to the continuum level of the starting wavelength at rest.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fnu">fnu = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fnu' Line='fnu = no'>
  <DD>Compute the continuum as flux per unit frequency (F-nu) if yes or flux per
  unit wavelength (F-lambda) if no.
  </DD>
  </DL>
  <P>
  <P>
  LINE PARAMETERS
  <DL>
  <DT><B><A NAME="l_lines">lines = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lines' Line='lines = ""'>
  <DD>List of spectral line files.  Spectral line files contain lines of rest
  wavelength, peak, profile type, and widths (see the DESCRIPTION
  section).  The latter parameters may be missing or INDEF in which case they
  default to the task <I>peak</I>, <I>profile</I>, <I>gfwhm</I>, and <I>lfwhm</I>
  parameters (note that the <I>peak</I> parameter is not a constant but the
  random number scaling).  If no file or a new (nonexistent) file is
  specified then a number of random lines given by the parameter <I>nlines</I>
  is generated.  If a new file name is specified then the lines generated are
  recorded in the file.  If the list of spectral line files is shorter than
  the list of input spectra, the last spectral line list file is reused.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nlines">nlines = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nlines' Line='nlines = 0'>
  <DD>If no spectral line file or a new file is specified then the task will
  generate this number of random spectral lines.  The rest wavelengths are
  uniformly random within the limits of the spectrum, the peaks are uniformly
  random between zero and the value of the <I>peak</I> parameter, the profile
  type is given by <I>profile</I>, and the widths are fixed at the values of
  the <I>gfhwm</I> ad <I>lfwhm</I> parameters.  If a redshift is applied the
  rest wavelengths are shifted and repeated periodically.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_profile">profile = "<TT>gaussian</TT>" (gaussian|lorentzian|voigt)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='profile' Line='profile = "gaussian" (gaussian|lorentzian|voigt)'>
  <DD>The default profile type for random lines or when not specified in the
  spectral line file.  The profile types are:
  <P>
  <PRE>
        gaussian - Gaussian profile
      lorentzian - Lorentzian profile
           voigt - Voigt profile
  </PRE>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_peak">peak = -0.5</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='peak' Line='peak = -0.5'>
  <DD>The maximum spectral line peak value when generating random lines or
  when the peak is missing from the spectral line file.
  This value is relative to the continuum unless the continuum is zero.
  Negative values are absorption lines and positive values are emission lines.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_gfwhm">gfwhm = 20., lfwhm = 20.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='gfwhm' Line='gfwhm = 20., lfwhm = 20.'>
  <DD>The default gaussian and lorentzian full widths at half maximum (FWHM), in
  Angstroms, used when generating random lines or when the widths are missing
  from the spectral line file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_seed">seed = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='seed' Line='seed = 1'>
  <DD>Random number seed.  If a value of "<TT>INDEF</TT>" is given then the clock
  time (integer seconds since 1980) is used as the seed yielding
  different random numbers for each execution.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B><A NAME="l_comments">comments = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='comments' Line='comments = yes'>
  <DD>Include comments recording task parameters in the image header?
  </DD>
  </DL>
  <P>
  PACKAGE PARAMETERS
  <DL>
  <DT><B><A NAME="l_nxsub">nxsub = 10</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nxsub' Line='nxsub = 10'>
  <DD>Number of pixel subsamples used in computing the gaussian spectral line
  profiles.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_dynrange">dynrange = 100000.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dynrange' Line='dynrange = 100000.'>
  <DD>The gaussian line profiles extend to infinity so a dynamic range, the ratio
  of the peak intensity to the cutoff intensity, is imposed to cutoff
  the profiles.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task creates or modifies one dimensional spectra.  with a combination
  of blackbody and linear sloped continuum and emission and absorption
  spectral lines.  The spectral lines may be gaussian, lorentzian, or voigt
  profiles.  A velocity shift may be applied to the underlying artificial
  spectrum which is shifted into the specified observed wavelength region.
  No noise is included but may be added with the task <B>mknoise</B>.  New
  spectra are created with the specified number of pixels, wavelength range,
  and real datatype.  When <I>nlines</I> is greater than 1 then an image with
  the specified number of lines is created though only the line given by the
  <I>ap</I> is will have a spectrum.  Existing spectra may be modified in
  place or new spectra output.  Spectra are modified by adding the continuum
  and lines defined by the parameters.
  <P>
  For new images a set of header keywords may be added by specifying an image
  or data file with the <I>header</I> parameter (see also <B>mkheader</B>).  If
  a data file is specified lines beginning with FITS keywords are entered in
  the image header.  Leading whitespace is ignored and any lines beginning
  with words having lowercase and nonvalid FITS keyword characters are
  ignored.  In addition to this optional header, parameters for the
  wavelength coordinates are defined.  Finally, comments may be added to the
  image header recording the task parameters and any information from the
  line file which are not line definitions.
  <P>
  Initially all spectra are created without a dispersion function; i.e.
  pixel coordinates.  For multiple spectra in an image this task must be
  executed for each image line to set the dispersion function and add data.
  When an image line is selected if it has a defined dispersion function that
  is used otherwise the task wavelength parameters are used.
  <P>
  A continuum is defined by the value at the starting wavelength at rest, a
  slope, and a blackbody function of a given temperature.  The blackbody
  function is scaled to have the specified continuum value at the starting
  wavelength at rest.  The blackbody flux units are per unit wavelength
  (F-lambda).  A zero continuum value or a zero temperature will not produce a
  blackbody continuum.
  <P>
  Spectral lines are modeled by gaussian, lorentzian, or voigt profiles of
  specified wavelength, peak, and widths.  The lines are defined in a
  spectral line file or generated randomly.  A spectral line file consists of
  text lines giving rest wavelength, peak, profile type, gaussian full width
  at half maximum and/or lorentzian full width at half maximum.  Only the
  wavelength is required and subsequent fields may be missing or given as
  INDEF.  The following table shows the possible formats where wavelength,
  peak,  gfwhm, and lfwhm are values of wavelength, peak, gaussian FWHM, and
  lorentzian FWHM.  The profile types are as shown though they may be
  abbreviated to one character.
  <P>
  <PRE>
  	wavelength
  	wavelength peak
  	wavelength peak gaussian
  	wavelength peak gaussian gfwhm
  	wavelength peak gaussian gfwhm
  	wavelength peak lorentzian
  	wavelength peak lorentzian lfwhm
  	wavelength peak lorentzian lfwhm
  	wavelength peak voigt
  	wavelength peak voigt gfwhm
  	wavelength peak voigt gfwhm lfwhm
  	wavelength peak voigt gfwhm lfwhm
  </PRE>
  <P>
  When a field is missing or INDEF the values given by the parameters
  <I>peak</I>, <I>profile</I>, <I>gfwhm</I>, and <I>lfwhm</I> are used.  If a
  peak value is missing, random values between zero and the <I>peak</I> value
  are generated.  Note that to get random line intensities with some
  specified profile type and widths the value INDEF would be used for
  the peak field.
  <P>
  If no spectral line file is specified or a new (nonexistent) file is named
  then the number of random lines given by the parameter <I>nlines</I> is
  generated.  The rest wavelengths are uniformly random within the wavelength
  range of the spectrum and extend periodically outside this range in the
  case of an applied velocity shift, the peaks are uniformly random between
  zero and the <I>peak</I> parameter, and the profile type and widths are
  given by the <I>profile</I>, <I>gfwhm</I>, and <I>lfwhm</I> parameters.  If a
  new file is named then the parameters of the generated lines will be
  output.
  <P>
  The peak values are taken relative to a positive continuum.  In other
  words the generated line profile is multiplied by the continuum (with a
  minimum of zero for fully saturated absorption lines).  If the
  continuum is less than or equal to zero, as in the case of an
  artificial arc spectrum or pure emission line spectrum, then the peak
  values are absolute intensities.  Positive peak values produce emission
  lines and negative values produce absorption lines.  Odd results will
  occur if the continuum has both positive and zero or negative values.
  <P>
  The underlying rest spectrum may be shifted.  This is used primarily for
  testing radial velocity measuring algorithms and is not intended as a
  complete model of redshift effects.  The starting and ending wavelengths
  are not changed by redshifting; these are the instrumental observed
  wavelengths.  Input line wavelengths are specified at rest and then
  shifted into or out of the final spectrum.  To be realistic the line
  list should include wavelengths over a great enough range to cover
  all desired redshifts.  The peaks and widths are also appropriately
  modified by a redshift.  As an example, if the redshift is 1 the
  lines will appear broader by a factor of 2 and the peaks will be down
  by a factor of 2 in order to maintain the same flux.
  <P>
  The random line generation is difficult in that one wants to have the
  same set of lines (for a given seed) observed at different redshifts.
  What is done is that the specified number of random lines is generated
  within the observed wavelength interval taken at rest.  This set is
  then repeated periodical over all wavelengths.  A redshift will then
  shift these rest lines in to or out of the observed spectrum.  If the
  lines are output, they are given at rest.  <B>Note that this
  periodicity may be important in interpreting cross correlation redshift
  tests for large shifts between template and object spectra.</B>
  <P>
  The definitions of the continuum are also affected by a redshift.
  The reference point for the continuum level, slope, and blackbody
  continuum is the starting wavelength taken at rest.  Shifts will then
  modify the continuum level at the first pixel appropriately.  In
  particular a large redshift will shift the blackbody in such a way that
  the flux is still given by the <I>continuum</I> parameter at the starting
  wavelength at rest.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Create a simple blackbody continuum between the default wavelengths.
  <P>
  <PRE>
  	cl&gt; mk1dspec bb title=Blackbody
  </PRE>
  <P>
  2. Create a random absorption spectrum on a blackbody continuum without
  saving the line list.
  <P>
  <PRE>
  	cl&gt; mk1dspec bbab title=Absorption nlines=100
  </PRE>
  <P>
  3. Create a random absorption spectrum with noise and cosmic rays.
  <P>
  <PRE>
  	cl&gt; mk1dspec bbab title=Absorption nlines=100
  	cl&gt; mknoise bbab rdnoise=10 poisson+ ncos=5 energy=1000
  </PRE>
  <P>
  4. Create a random emission spectrum on a blackbody continuum and save
  the line list.
  <P>
  <PRE>
  	cl&gt; mk1dspec bbem title=Emission nl=30 peak=0.6 lines=bbem.dat
  </PRE>
  <P>
  5. Create an artificial random arc line spectrum.
  <P>
  <PRE>
  	cl&gt; mk1dspec arc title="Arc lines" cont=0 peak=500 nl=30
  </PRE>
  <P>
  6. Create a test spectrum with a line list.
  <P>
  <PRE>
  	cl&gt; type linelist
  	4100 -.1 g 20
  	4200 -2. g 20
  	4300 -.3 g 20
  	5100 -.9 g 2
  	5200 -.9 g 4
  	5300 -.9 g 8
  	6700 .9 g 8
  	6800 .9 g 2
  	6900 .9 g 4
  	7700 .3 g 20
  	7800 .2 g 20
  	7900 .1 g 20
  	cl&gt; mk1dspec testspec title=Test cont=500 temp=0 lines=linelist
  </PRE>
  <P>
  7. Add absorption lines to a spectrum.
  <P>
  <PRE>
  	cl&gt; mk1dspec bb out=artspec cont=0 lines=STDIN
  	4300 -60
  	5000 -200
  	[EOF]
  </PRE>
  <P>
  Normally the input spectrum would be a real spectrum.
  <P>
  8. Make two spectra taken from the same set of random lines but differing
  in redshift.
  <P>
  <PRE>
  	cl&gt; mk1dspec restspec nl=30
  	cl&gt; mk1dspec redspec rv=3000 nl=30
  	cl&gt; mk1dspec bluespec rv=-.01 z+ nl=30
  </PRE>
  <P>
  9. Make a multispec image with 5 apertures and a range of redshifts.
  <P>
  <PRE>
  	cl&gt; mk1dspec spec.ms ap=1 nl=30 rv=0 naps=5
  	cl&gt; mk1dspec spec.ms ap=2 nl=30 rv=1000
  	cl&gt; mk1dspec spec.ms ap=3 nl=30 rv=2000
  	cl&gt; mk1dspec spec.ms ap=4 nl=30 rv=3000
  	cl&gt; mk1dspec spec.ms ap=5 nl=30 rv=4000
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_revisions">REVISIONS</A></H2>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_MK1DSPEC">MK1DSPEC V2.11+</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='MK1DSPEC' Line='MK1DSPEC V2.11+'>
  <DD>The random number seed can be set from the clock time by using the value
  "<TT>INDEF</TT>" to yield different random numbers for each execution.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_MK1DSPEC">MK1DSPEC V2.11</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='MK1DSPEC' Line='MK1DSPEC V2.11'>
  <DD>Lorentzian and Voigt profiles were added and the parameters and input
  line list format were changed.  The widths are now FWHM instead of
  gaussian sigmas.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_MK1DSPEC">MK1DSPEC V2.10.3</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='MK1DSPEC' Line='MK1DSPEC V2.10.3'>
  <DD>The format parameter was eliminated and the task updated to produce the
  current coordinate system format.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  mknoise, mk2dspec, mkheader, onedspec.sinterp
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>