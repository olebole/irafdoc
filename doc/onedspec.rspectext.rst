.. _rspectext:

rspectext — Convert ascii text spectra to image spectra
=======================================================

**Package: onedspec**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  rspectext -- convert 1D ascii text spectra to IRAF image spectra
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  rspectext input output
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>Input list of ascii text spectra.  These may have a optional FITS header
  at the beginning and then two columns of wavelength and flux.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>Output list of IRAF spectra image names.  The list must match the
  input list.
  </DD>
  </DL>
  <P>
  <P>
  The following parameters are only used if there is no FITS header
  with the data.
  <DL>
  <DT><B>title = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='title' Line='title = ""'>
  <DD>Title to be assigned to the spectra.
  </DD>
  </DL>
  <DL>
  <DT><B>flux = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='flux' Line='flux = no'>
  <DD>Are the flux values flux calibrated?  If so then header keywords are
  inserted to identify this for the IRAF spectral software.
  </DD>
  </DL>
  <DL>
  <DT><B>dtype = "<TT>linear</TT>" (none|linear|log|nonlinear|interp)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dtype' Line='dtype = "linear" (none|linear|log|nonlinear|interp)'>
  <DD>Type of dispersion to assign to the spectra.  The options are:
  <DL>
  <DT><B>none</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='none' Line='none'>
  <DD>No dispersion function and nothing is added to the image header.
  </DD>
  </DL>
  <DL>
  <DT><B>linear</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='linear' Line='linear'>
  <DD>Store the linear dispersion parameters <B>crval1</B> and <B>cdelt1</B>
  in the image header.  The wavelength values are ignored.  This may
  be used if the wavelength values are known to be linear but one wants
  to avoid possible roundoff and resampling errors introduced by the
  "<TT>interp</TT>" option.
  </DD>
  </DL>
  <DL>
  <DT><B>log</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='log' Line='log'>
  <DD>Store the log-linear dispersion parameters <B>crval1</B> and <B>cdelt1</B> in
  the image header.  The wavelength values are ignored.  This may be used if
  the wavelength values are known to be linear in the log of the wavelength
  but one wants to avoid possible roundoff and resampling errors introduced
  by the "<TT>interp</TT>" option.
  </DD>
  </DL>
  <DL>
  <DT><B>nonlinear</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='nonlinear' Line='nonlinear'>
  <DD>Store the wavelength values in the image header as a lookup table.
  The flux values are not resampled.  The wavelength values need not
  be evenly sampled.
  </DD>
  </DL>
  <DL>
  <DT><B>interp</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='interp' Line='interp'>
  <DD>Use the wavelength values to resample to a linear dispersion between
  the first and last wavelength values.  The dispersion per pixel is
  determined by the number of pixels and the endpoint wavelengths.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>crval1 = 1., cdelt1 = 1.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='crval1' Line='crval1 = 1., cdelt1 = 1.'>
  <DD>The wavelength coordinate of the first pixel and the wavelength interval
  per pixel to be used with the linear and log dispersion types.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Ascii text files consisting of an optional FITS header (usually produced
  by <B>wspectext</B>) and a two column list of wavelengths and fluxes
  are converted to IRAF image spectra.  If a header is included then
  the header information is assumed to describe the spectra including
  any dispersion function.  If no header is given then the minimal
  information for describing spectra in IRAF is added.  The dispersion
  function can be set either a linear or log-linear based on two
  keywords (ignoring the wavelength values) or from the wavelength
  values.  The latter may be stored in the header as a lookup table
  allowing for nonlinear dispersions or resample to a linear dispersion.
  This task is a script based on <B>rtextimage</B> for the creating
  the image and entering the flux values, <B>hedit</B> to set some
  of the header keywords, and <B>dispcor</B> to handle the nonlinear
  or resampled dispersion functions.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  Create spectrum from a text file originally produced by <B>wspectext</B>.
  <P>
  <PRE>
      cl&gt; type text001
      BITPIX  =                    8  /  8-bit ASCII characters
      NAXIS   =                    1  /  Number of Image Dimensions
      NAXIS1  =                  100  /  Length of axis
      ORIGIN  = 'NOAO-IRAF: WTEXTIMAGE'  /
      IRAF-MAX=                   0.  /  Max image pixel (out of date)
      IRAF-MIN=                   0.  /  Min image pixel (out of date)
      IRAF-B/P=                   32  /  Image bits per pixel
      IRAFTYPE= 'REAL FLOATING     '  /  Image datatype
      OBJECT  = 'TITLE             '  /
      FILENAME= 'TEST              '  /  IRAF filename
      FORMAT  = '5G14.7            '  /  Text line format
      APNUM1  = '1 1     '
      DC-FLAG =                    0
      WCSDIM  =                    1
      CTYPE1  = 'LINEAR  '
      CRVAL1  =                4000.
      CRPIX1  =                   1.
      CDELT1  =     10.1010101010101
      CD1_1   =     10.1010101010101
      LTM1_1  =                   1.
      WAT0_001= 'system=equispec                                 '
      WAT1_001= 'wtype=linear label=Wavelength units=Angstroms   '
      END
  										    
      4000.00  1000.
      4010.10  1005.54
      4020.20  1011.05
      ...
      cl&gt; rspectext text001 spec001
  </PRE>
  <P>
  2.  Create a spectrum with a nonlinear dispersion using the wavelength
  values as a lookup table.
  <P>
  <PRE>
      cl&gt; type text002
      4000.00  1000.
      4010.10  1005.54
      4020.20  1011.05
      ...
      cl&gt; rspectext text002 spec002 title="HH12" dtype=nonlinear
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>RSPECTEXT V2.11</B></DT>
  <! Sec='REVISIONS' Level=0 Label='RSPECTEXT' Line='RSPECTEXT V2.11'>
  <DD>The task now automatically senses the presence of a header.
  </DD>
  </DL>
  <DL>
  <DT><B>RSPECTEXT V2.10.3</B></DT>
  <! Sec='REVISIONS' Level=0 Label='RSPECTEXT' Line='RSPECTEXT V2.10.3'>
  <DD>This is a new task with this version.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  wspectext, rtextimage, dispcor, mkms, imspec, sinterp
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
