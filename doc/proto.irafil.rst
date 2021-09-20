.. _irafil:

irafil: Create an IRAF image from a binary data file
====================================================

**Package: proto**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  irafil -- converts a binary file containing pixel values to an IRAF image
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  irafil input nrows ncols
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input' -->
  <dd>the input file names to be converted
  </dd>
  </dl>
  <dl>
  <dt><b>nrows</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='nrows' Line='nrows' -->
  <dd>the number of rows of data in the image
  </dd>
  </dl>
  <dl>
  <dt><b>ncols</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='ncols' Line='ncols' -->
  <dd>the number of columns of data in the image
  </dd>
  </dl>
  <dl>
  <dt><b>bits = 16</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='bits' Line='bits = 16' -->
  <dd>the number of data bits per pixel. This must be either 8 or 16
  </dd>
  </dl>
  <dl>
  <dt><b>signed = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='signed' Line='signed = yes' -->
  <dd>the pixels are assumed to be signed integers if the bits parameter is 16,
  and unsigned if the bits parameter is 8. If signed is set to no, then
  the 16 bit pixels will be treated as unsigned integers and the resultant
  image will be of type long integers.
  </dd>
  </dl>
  <dl>
  <dt><b>tb_flip = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='tb_flip' Line='tb_flip = no' -->
  <dd>This parameter allows the image to be <span style="font-family: monospace;">"top-to-bottom"</span> flipped during
  conversion.
  </dd>
  </dl>
  <dl>
  <dt><b>skip = 0</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='skip' Line='skip = 0' -->
  <dd>the number of bytes to skip prior to reading pixel data. This allows
  skipping of header data which is otherwise not translatable and would
  be confused with the pixel data.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The specified files are read as integers and converted to IRAF images.
  The specified number of header bytes will be skipped, and the specified
  data format, 8 or 16 bit pixels, at the rate of ncols by nrows will be
  read. Signed data or 8 bit data will be placed into images having data
  type short. Unsigned 16 bit pixels will be converted into images of
  type long.
  </p>
  <p>
  The resultant images will be assigned the same name as the input file,
  but with <span style="font-family: monospace;">".i"</span> appended to indicate IRAF format.
  </p>
  <p>
  The tb_flip parameter should be set to yes when converting the <span style="font-family: monospace;">"snap"</span>
  format files from the Compaq image display station, or other devices
  which refer to the first row as inverted from the usual IRAF notation.
  </p>
  <p>
  This utility is capable of converting a large number of strange
  image formats to IRAF images. By skipping any initial header, and specifying
  a value for ncols equal to either the row length of the image, or the
  number of pixels used in the foreign internal format, almost any
  16-bit format can be read. For example, FORTH pictures can be read
  by skipping the initial 2048 bytes and reading the pixels assuming
  a row length of 1024, even if the actual row length is shorter. There
  will be garbage pixels at the end of each row which can be trimmed
  with IMCOPY using picture sections. An absurd example is to read an
  IRAF pixel file by skipping 1024 bytes and reading with a row length of
  1024 [at least for the 800 pixel image I tried].
  </p>
  <p>
  Since no byte swapping is performed, a foreign tape format must be byte swapped
  if necessary prior to using IRAFIL. This may be done with REBLOCK in the
  dataio package.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Say you've deleted your header file to an IRAF image. The pixel file
  is pix3034x. Assuming the pixels are short integers, the image is
  10 rows by 800 columns:
  </p>
  <pre>
  lo&gt; irafil pix3034x 10 1024 skip=1024
  lo&gt; imcopy pix3034x.i[1:800,*] phoenix
  </pre>
  <p>
  The first line creates the IRAF image pix3034x.i which is readable
  by IRAF tasks, but has 1024 pixels per row. The real image only
  has 800 pixels per row, but we had to read it this way because of the
  way pixels are stored in IRAF images. So we IMCOPY the good part of
  the picture to the new IRAF image we call phoenix.
  </p>
  <p>
  2. To read the <span style="font-family: monospace;">"snap"</span> format pictures from the Compaq station:
  </p>
  <pre>
  lo&gt; irafil m82.snp 512 512 tb_flip+ bits=8
  </pre>
  <p>
  This will create the IRAF image m82.snp.i which can then be run
  through CRTPICT to make a Dicomed hardcopy.
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Time requirements</h3>
  <!-- BeginSection: 'TIME REQUIREMENTS' -->
  <!-- EndSection:   'TIME REQUIREMENTS' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  There is no way to explicitly specify the output image name.
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  binfil,imcopy,reblock
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  -->
  
