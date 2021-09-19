.. _binfil:

binfil: Create a binary file from an IRAF image
===============================================

**Package: proto**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  binfil -- create a 16 bit binary raster file from an IRAF image 
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  binfil input
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input' -->
  <dd>The list of input images to be converted.
  </dd>
  </dl>
  <dl>
  <dt><b>scale_fact = 1.0</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='scale_fact' Line='scale_fact = 1.0' -->
  <dd>A multiplicative scale factor to be applied to each pixel during the
  conversion process.  This parameter provides the means to minimize loss
  of precision when converting from the dynamic range of the IRAF image
  pixels to the dynamic range of the output 16-bit signed integer,
  -32768 to 32767.
  </dd>
  </dl>
  <dl>
  <dt><b>header = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='header' Line='header = no' -->
  <dd>Prepend a short descriptive header to the output binary raster file?
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  BINFIL generates a simple signed 16-bit binary raster file
  from IRAF images. BINFIL can be useful when programs other than IRAF
  applications are to be used to examine the data. The format of the resulting
  file is a simple string of pixels, with the exception that the first
  90 bytes or 45 words may optionally form a minimal header. 
  </p>
  <p>
  The header elements are stored as follows:
  </p>
  <pre>
  	word 1    : nrows
  	word 2    : ncols
  	word 3    : IRAF pixel type flag 
  	word 4-13 : reserved space
  	word 14-45: image title (ASCII 64 bytes)
  </pre>
  <p>
  Pixels from the input images are converted to short integers after scaling
  by the scale_fact parameter. The resultant pixel values are limited to the
  maximum range of a short integer and then written to the binary file.
  </p>
  <p>
  The output binary file assumes the name of the input image with an appended
  <tt>".b"</tt> to indicate binary.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  Convert the IRAF image irafimage to the binary file irafimage.b.
  </p>
  <pre>
  cl&gt; binfil irafimage scale=0.01
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Time requirements</h3>
  <!-- BeginSection: 'TIME REQUIREMENTS' -->
  <!-- EndSection:   'TIME REQUIREMENTS' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  Only the first 64 characters of the image title are placed in the binary file
  header.
  </p>
  <p>
  There is no way to specify the output binary file names.
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  irafil
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  -->
  
