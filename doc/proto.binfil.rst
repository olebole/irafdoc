.. _binfil:

binfil — Create a binary file from an IRAF image
================================================

**Package: proto**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  binfil -- create a 16 bit binary raster file from an IRAF image 
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  binfil input
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The list of input images to be converted.
  </DD>
  </DL>
  <DL>
  <DT><B>scale_fact = 1.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='scale_fact' Line='scale_fact = 1.0'>
  <DD>A multiplicative scale factor to be applied to each pixel during the
  conversion process.  This parameter provides the means to minimize loss
  of precision when converting from the dynamic range of the IRAF image
  pixels to the dynamic range of the output 16-bit signed integer,
  -32768 to 32767.
  </DD>
  </DL>
  <DL>
  <DT><B>header = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='header' Line='header = no'>
  <DD>Prepend a short descriptive header to the output binary raster file?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  BINFIL generates a simple signed 16-bit binary raster file
  from IRAF images. BINFIL can be useful when programs other than IRAF
  applications are to be used to examine the data. The format of the resulting
  file is a simple string of pixels, with the exception that the first
  90 bytes or 45 words may optionally form a minimal header. 
  <P>
  The header elements are stored as follows:
  <P>
  <PRE>
  	word 1    : nrows
  	word 2    : ncols
  	word 3    : IRAF pixel type flag 
  	word 4-13 : reserved space
  	word 14-45: image title (ASCII 64 bytes)
  </PRE>
  <P>
  Pixels from the input images are converted to short integers after scaling
  by the scale_fact parameter. The resultant pixel values are limited to the
  maximum range of a short integer and then written to the binary file.
  <P>
  The output binary file assumes the name of the input image with an appended
  "<TT>.b</TT>" to indicate binary.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  Convert the IRAF image irafimage to the binary file irafimage.b.
  <P>
  <PRE>
  cl&gt; binfil irafimage scale=0.01
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  Only the first 64 characters of the image title are placed in the binary file
  header.
  <P>
  There is no way to specify the output binary file names.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  irafil
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
