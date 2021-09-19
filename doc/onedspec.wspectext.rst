.. _wspectext:

wspectext: Convert 1D image spectra to ascii text spectra
=========================================================

**Package: onedspec**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  wspectext -- convert 1D image spectra to an ascii text spectra
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  wspectext input output
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input' -->
  <dd>Input list of 1D image spectra to be converted.  If the image is
  not one dimensional an warning will be given and the image will be skipped.
  </dd>
  </dl>
  <dl>
  <dt><b>output</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='output' Line='output' -->
  <dd>Output list of ascii text spectra filenames.  The list must match the
  input list.
  </dd>
  </dl>
  <dl>
  <dt><b>header = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='header' Line='header = yes' -->
  <dd>This parameter determines whether or not a descriptive header precedes the
  wavelength and flux values written to the text file.  When <i>header =
  no</i>, only a two column list of wavelengths and fluxes is output.
  </dd>
  </dl>
  <dl>
  <dt><b>wformat = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='wformat' Line='wformat = ""' -->
  <dd>The wavelength coordinate output format.  If it is undefined the formatting
  option stored with the WCS in the image header is used.  If the WCS
  formatting option is not defined then a free format is used.  See
  <b>listpixels</b> for a description of the format syntax.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  IRAF one dimensional spectra are converted to ascii text files.  The
  text files consist of an optional FITS type header followed by a two
  column list of wavelengths and flux values.  The format of the wavelengths
  can be set but the flux values are given in free format.  This task
  is a combination of <b>wtextimage</b> and <b>listpixels</b>.  The output
  of this task may be converted back to an image spectrum with the
  task <b>rspectext</b>.
  </p>
  <p>
  Spectra which are not in 1D images such as multispec format or long slit
  may first be converted to 1D images using <b>scopy</b> with format=<tt>"onedspec"</tt>.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1.  Write a text file with a header.
  </p>
  <pre>
      cl&gt; wspectext spec001 text001 header+ wformat="%0.2f"
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
  </pre>
  <p>
  2.  Write a simple text file with two columns of wavelength and flux.
  </p>
  <pre>
      cl&gt; wspectext spec001 text002 header- wformat="%0.2f"
      cl&gt; type text002
      4000.00  1000.
      4010.10  1005.54
      4020.20  1011.05
      ...
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Revisions</h3>
  <!-- BeginSection: 'REVISIONS' -->
  <dl>
  <dt><b>WSPECTEXT V2.10.3</b></dt>
  <!-- Sec='REVISIONS' Level=0 Label='WSPECTEXT' Line='WSPECTEXT V2.10.3' -->
  <dd>This is a new task with this version.
  </dd>
  </dl>
  <!-- EndSection:   'REVISIONS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  rspectext, wtextimage, listpixels, scopy, imspec
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  -->
  
