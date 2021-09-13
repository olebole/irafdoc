.. _sbands:

sbands — Bandpass spectrophotometry of spectra
==============================================

**Package: onedspec**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  sbands -- bandpass spectrophotometry of spectra
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  sbands input output bands
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>Input list of spectra to be measured.  These may be one dimensional
  spectra in individual or "<TT>multispec</TT>" format or calibrated spatial spectra such
  as long slit or Fabry-Perot images.  The dispersion axis and summing
  parameters are specified by package parameters for the spatial spectra.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>Output file for the results.  This may be a filename or "<TT>STDOUT</TT>" to
  write to the terminal.
  </DD>
  </DL>
  <DL>
  <DT><B>bands</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='bands' Line='bands'>
  <DD>Bandpass file consisting of lines with one, two, or three bandpasses per
  line.  A bandpass is specified by an identification string (quoted if it is
  null or contains whitespace), the central wavelength, the width of the
  bandpass in wavelength, and a filter filename with the special value "<TT>none</TT>"
  if there is no filter (a flat unit response).  This format is described
  further in the description section.
  </DD>
  </DL>
  <DL>
  <DT><B>apertures = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='apertures' Line='apertures = ""'>
  <DD>List of apertures to select from the input spectra.  For one dimensional
  spectra this is the aperture number and for spatial spectra it is
  the column or line.  If the null string is specified all apertures are
  selected.  The aperture list syntax is a range list which includes
  intervals and steps (see <B>ranges</B>).
  </DD>
  </DL>
  <DL>
  <DT><B>normalize = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='normalize' Line='normalize = yes'>
  <DD>Normalize the bandpass fluxes by the bandpass response?  If no then
  the results will depend on the bandpass widths and filter function
  values.  If yes then fluxes will be comparable to an average pixel
  value.  When computing indices and equivalent widths the flux must
  either be normalized or the bandpasses and filter response functions
  must be the same.
  </DD>
  </DL>
  <DL>
  <DT><B>mag = no, magzero = 0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='mag' Line='mag = no, magzero = 0.'>
  <DD>Output the bandpass fluxes as magnitudes with specified magnitude
  zero point?
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Include a verbose header giving a banner, the parameters used,
  the bandpasses, and column headings?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <B>Sbands</B> performs bandpass spectrophotometry with one or more bandpasses
  on one or more spectra.  A list of input spectra is specified.  The spectra
  may be of any type acceptable in the <B>noao.onedspec</B> package including
  multispec format with nonlinear dispersion, long slit spectra, and even
  3D cubes with one dispersion axis.  The <I>apertures</I> parameter allows
  selecting a subset of the spectra by aperture number.
  <P>
  The bandpasses are specified in a text file.  A bandpass consists of four
  fields; an identification name, the wavelength of the bandpass center, a
  bandpass width, and a filename for a filter.  The identification is a
  string which must be quoted if a null name or a name with whitespace is
  desired.  The identification could be given as the central wavelength if
  nothing else is appropriate.  The filter field is a filename for a text
  file containing the filter values.  A filter file consists of a wavelength
  ordered list of wavelength and relative response.  Extrapolation uses the
  end point values and interpolation is linear.  The special name "<TT>none</TT>" is
  used if there is no filter.  This is equivalent to unit response at all
  wavelengths.
  <P>
  In the bandpass file there may be one, two, or three bandpasses on
  a line.  Below are some examples of the three cases:
  <P>
  <PRE>
     alpha 5000 10 myalpha.dat
     beta1 4000 100 none	     beta2 4100 100 none
     line  4500 100 none	     red   4000 200 none blue 5000 200 none
  </PRE>
  <P>
  The flux in each bandpass is measured by summing each pixel in the interval
  multiplied by the interpolated filter response at that pixel.  At the edges
  of the bandpass the fraction of the pixel in the bandpass is used.  If the
  bandpass goes outside the range of the data an INDEF value will be reported.
  If the <I>normalize</I> option is yes then the total flux is divided by
  the sum of the filter response values.  If the <I>mag</I> option is
  yes the flux will be converted to a magnitude (provided it is positive)
  using the formula
  <P>
  <PRE>
      magnitude = magzero - 2.5 * log10 (flux)
  </PRE>
  <P>
  where <I>magzero</I> is a parameter for the zero point magnitude and log10
  is the base 10 logarithm.  Note that there is no attempt to deal with the
  pixel flux units.  This is the responsibility of the user.
  <P>
  If there is only one bandpass (on one line of the band file) then only
  the band flux or magnitude is reported.  If there are two bandpasses
  the fluxes or magnitudes for the two bands are reported as well as a
  band index, the flux ratio or magnitude difference (depending on the <I>mag</I>)
  flag, and an equivalent width using the second band as the continuum.
  If there are three bandpasses then a continuum bandpass flux is computed
  as the interpolation between the bandpass centers to the center of the
  first bandpass.  The special bandpass identification "<TT>cont</TT>" will
  be reported.
  <P>
  The equivalent width is obtained from the two bandpasses by the
  formula
  <P>
  <PRE>
      eq. width = (1 - flux1 / flux2) * width1
  </PRE>
  <P>
  where flux1 and flux2 are the two bandpass fluxes and width1 is the
  width of the first bandpass.  Note that for this to be meaningful
  the bandpasses should be normalized or have the same width/response.
  <P>
  The results of measuring each bandpass in each spectrum are written
  to the specified output file.  This file may be given as "<TT>STDOUT</TT>" to
  write the results to the terminal.  The output file contains lines
  with the spectrum name and aperture, the band identifications and
  fluxes or magnitudes, and the band index and equivalent width (if
  appropriate).  The <I>verbose</I> option allows creating a more
  documented output by including a commented header with the task
  name and parameters, the bandpass definitions, and column labels.
  The examples below show the form of the output.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  The following examples use artificial data and arbitrary bands.
  <P>
  1.  Show example results with one, two, and three bandpass entries in
  the bandpass file.
  <P>
  <PRE>
      cl&gt; type bands
      test 6125 50 none red 6025 100 none blue 6225 100 none
      test 6125 50 none red 6025 100 none
      test 6125 50 none blue 6225 100 none
      test 6125 50 none
      cl&gt; sbands oned STDOUT bands
  <P>
      # SBANDS: NOAO/IRAF IRAFX valdes@puppis Mon 15:31:45 01-Nov-93
      #   bands = bands, norm = yes, mag = no
      #       band     filter wavelength      width
      #       test       none      6125.        50.
      #        red       none      6025.       100.
      #       blue       none      6225.       100.
      #       test       none      6125.        50.
      #        red       none      6025.       100.
      #       test       none      6125.        50.
      #       blue       none      6225.       100.
      #       test       none      6125.        50.
      #
      #       spectrum    band    flux    band    flux   index eqwidth
  	     oned(1)    test   44.33    cont   97.97    0.45   27.37
  	     oned(1)    test   44.33     red   95.89    0.46   26.89
  	     oned(1)    test   44.33    blue  100.04    0.44   27.84
  	     oned(1)    test   44.33
  </PRE>
  <P>
  2.  This example shows measurements on a long slit spectrum with an
  aperture selection and magnitude output.
  <P>
  <PRE>
      cl&gt; type lsbands.dat
      band1 4500 40 none
      band2 4600 40 none
      band3 4700 40 none
      cl&gt; nsum=5
      cl&gt; sbands ls STDOUT lsbands.dat apertures=40-60x5 mag+ magzero=10.1
  <P>
      # SBANDS: NOAO/IRAF IRAFX valdes@puppis Mon 15:37:18 01-Nov-93
      #   bands = lsbands.dat, norm = yes, mag = yes, magzero = 10.10
      #       band     filter wavelength      width
      #      band1       none      4500.        40.
      #      band2       none      4600.        40.
      #      band3       none      4700.        40.
      #
      #       spectrum    band     mag
       ls[38:42,*](40)   band1    3.14
       ls[38:42,*](40)   band2    3.19
       ls[38:42,*](40)   band3    3.15
       ls[43:47,*](45)   band1    3.13
       ls[43:47,*](45)   band2    3.15
       ls[43:47,*](45)   band3    3.14
       ls[48:52,*](50)   band1    2.34
       ls[48:52,*](50)   band2    2.43
       ls[48:52,*](50)   band3    2.43
       ls[53:57,*](55)   band1    3.10
       ls[53:57,*](55)   band2    3.15
       ls[53:57,*](55)   band3    3.12
       ls[58:62,*](60)   band1    3.14
       ls[58:62,*](60)   band2    3.19
       ls[58:62,*](60)   band3    3.15
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>SBANDS V2.10.4</B></DT>
  <! Sec='REVISIONS' Level=0 Label='SBANDS' Line='SBANDS V2.10.4'>
  <DD>The flux column is now printed to 6 digits of precision with possible
  exponential format to permit flux calibrated spectra to print properly.
  </DD>
  </DL>
  <DL>
  <DT><B>SBANDS V2.10.3</B></DT>
  <! Sec='REVISIONS' Level=0 Label='SBANDS' Line='SBANDS V2.10.3'>
  <DD>The task is new in this release
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  splot
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
