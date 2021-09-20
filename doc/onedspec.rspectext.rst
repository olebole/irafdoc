.. _rspectext:

rspectext: Convert ascii text spectra to image spectra
======================================================

**Package: onedspec**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  rspectext -- convert 1D ascii text spectra to IRAF image spectra
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  rspectext input output
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input' -->
  <dd>Input list of ascii text spectra.  These may have a optional FITS header
  at the beginning and then two columns of wavelength and flux.
  </dd>
  </dl>
  <dl>
  <dt><b>output</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='output' Line='output' -->
  <dd>Output list of IRAF spectra image names.  The list must match the
  input list.
  </dd>
  </dl>
  <p>
  The following parameters are only used if there is no FITS header
  with the data.
  </p>
  <dl>
  <dt><b>title = <span style="font-family: monospace;">""</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='title' Line='title = ""' -->
  <dd>Title to be assigned to the spectra.
  </dd>
  </dl>
  <dl>
  <dt><b>flux = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='flux' Line='flux = no' -->
  <dd>Are the flux values flux calibrated?  If so then header keywords are
  inserted to identify this for the IRAF spectral software.
  </dd>
  </dl>
  <dl>
  <dt><b>dtype = <span style="font-family: monospace;">"linear"</span> (none|linear|log|nonlinear|interp)</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='dtype' Line='dtype = "linear" (none|linear|log|nonlinear|interp)' -->
  <dd>Type of dispersion to assign to the spectra.  The options are:
  <dl>
  <dt><b>none</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='none' Line='none' -->
  <dd>No dispersion function and nothing is added to the image header.
  </dd>
  </dl>
  <dl>
  <dt><b>linear</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='linear' Line='linear' -->
  <dd>Store the linear dispersion parameters <b>crval1</b> and <b>cdelt1</b>
  in the image header.  The wavelength values are ignored.  This may
  be used if the wavelength values are known to be linear but one wants
  to avoid possible roundoff and resampling errors introduced by the
  <span style="font-family: monospace;">"interp"</span> option.
  </dd>
  </dl>
  <dl>
  <dt><b>log</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='log' Line='log' -->
  <dd>Store the log-linear dispersion parameters <b>crval1</b> and <b>cdelt1</b> in
  the image header.  The wavelength values are ignored.  This may be used if
  the wavelength values are known to be linear in the log of the wavelength
  but one wants to avoid possible roundoff and resampling errors introduced
  by the <span style="font-family: monospace;">"interp"</span> option.
  </dd>
  </dl>
  <dl>
  <dt><b>nonlinear</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='nonlinear' Line='nonlinear' -->
  <dd>Store the wavelength values in the image header as a lookup table.
  The flux values are not resampled.  The wavelength values need not
  be evenly sampled.
  </dd>
  </dl>
  <dl>
  <dt><b>interp</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='interp' Line='interp' -->
  <dd>Use the wavelength values to resample to a linear dispersion between
  the first and last wavelength values.  The dispersion per pixel is
  determined by the number of pixels and the endpoint wavelengths.
  </dd>
  </dl>
  </dd>
  </dl>
  <dl>
  <dt><b>crval1 = 1., cdelt1 = 1.</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='crval1' Line='crval1 = 1., cdelt1 = 1.' -->
  <dd>The wavelength coordinate of the first pixel and the wavelength interval
  per pixel to be used with the linear and log dispersion types.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  Ascii text files consisting of an optional FITS header (usually produced
  by <b>wspectext</b>) and a two column list of wavelengths and fluxes
  are converted to IRAF image spectra.  If a header is included then
  the header information is assumed to describe the spectra including
  any dispersion function.  If no header is given then the minimal
  information for describing spectra in IRAF is added.  The dispersion
  function can be set either a linear or log-linear based on two
  keywords (ignoring the wavelength values) or from the wavelength
  values.  The latter may be stored in the header as a lookup table
  allowing for nonlinear dispersions or resample to a linear dispersion.
  This task is a script based on <b>rtextimage</b> for the creating
  the image and entering the flux values, <b>hedit</b> to set some
  of the header keywords, and <b>dispcor</b> to handle the nonlinear
  or resampled dispersion functions.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1.  Create spectrum from a text file originally produced by <b>wspectext</b>.
  </p>
  <pre>
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
  </pre>
  <p>
  2.  Create a spectrum with a nonlinear dispersion using the wavelength
  values as a lookup table.
  </p>
  <pre>
      cl&gt; type text002
      4000.00  1000.
      4010.10  1005.54
      4020.20  1011.05
      ...
      cl&gt; rspectext text002 spec002 title="HH12" dtype=nonlinear
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Revisions</h3>
  <!-- BeginSection: 'REVISIONS' -->
  <dl>
  <dt><b>RSPECTEXT V2.11</b></dt>
  <!-- Sec='REVISIONS' Level=0 Label='RSPECTEXT' Line='RSPECTEXT V2.11' -->
  <dd>The task now automatically senses the presence of a header.
  </dd>
  </dl>
  <dl>
  <dt><b>RSPECTEXT V2.10.3</b></dt>
  <!-- Sec='REVISIONS' Level=0 Label='RSPECTEXT' Line='RSPECTEXT V2.10.3' -->
  <dd>This is a new task with this version.
  </dd>
  </dl>
  <!-- EndSection:   'REVISIONS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  wspectext, rtextimage, dispcor, mkms, imspec, sinterp
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  -->
  
