.. _rrcopy:

rrcopy: Convert IPPS rasters from an RCOPY tape to IRAF images
==============================================================

**Package: mtlocal**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  rrcopy -- Convert IPPS rasters from RCOPY tapes to IRAF images
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  rrcopy rcopy_file raster_list iraf_file
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>rcopy_file</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='rcopy_file' Line='rcopy_file' -->
  <dd>The RCOPY data source, i.e., the name of a magtape device or a RCOPY
  format disk file.
  </dd>
  </dl>
  <dl>
  <dt><b>raster_list</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='raster_list' Line='raster_list' -->
  <dd>A string listing the IPPS rasters to be read from the rcopy file.
  </dd>
  </dl>
  <dl>
  <dt><b>iraf_file</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='iraf_file' Line='iraf_file' -->
  <dd>The IRAF file which will receive the RCOPY data if the make_image parameter
  is set.  If more than one raster is being read, the output filenames
  will be concatenated from this
  parameter and the raster sequence number on the RCOPY tape.  That
  is, reading rasters 1 thru 8 from tape into iraf_file 'pic'
  would generate a sequence of files: pic001, pic002, ..., pic008.
  </dd>
  </dl>
  <dl>
  <dt><b>make_image = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='make_image' Line='make_image = yes' -->
  <dd>This switch determines whether RCOPY image data is converted to an IRAF image
  file.  When this switch it set to no, only a listing is produced, no output
  image is written. 
  </dd>
  </dl>
  <dl>
  <dt><b>print_header = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='print_header' Line='print_header = yes' -->
  <dd>This switch determines if the header information will be printed for those
  rasters in <tt>"raster_list"</tt>.  (It might be appropriate to set print_header=no, or
  redirect the output, if RRCOPY is being run as a background task.)
  </dd>
  </dl>
  <dl>
  <dt><b>data_type = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='data_type' Line='data_type = ""' -->
  <dd>The data type of the output IRAF image.  If an incorrect data_type or null 
  string is entered, the default data type used is
  determined by the number of bits per pixel in the IPPS raster.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  IPPS rasters stored on RCOPY tapes are read from the specified source.
  IPPS raster header information is listed.  The image data may optionally
  be converted to an IRAF image file.  It takes RRCOPY about 16 cpu seconds
  to read a 256 x 256 30-bit IPPS raster; 42 cpu seconds for a 320 x 512
  30-bit raster; 34 cpu seconds for a 320 x 512 20-bit raster.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  [1] List all IPPS headers from an RCOPY tape:
  </p>
  <p>
  	cl&gt; rrcopy mtb 1-999 make_image=no
  </p>
  <p>
  [2] Read the first 5 rasters from tape into IRAF images ipps001 
  through ipps005 with default data types:
  </p>
  <p>
  	cl&gt; rrcopy mtb 1-5 ipps
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  The Cyber format readers, including <i>rrcopy</i>, have not been implemented
  on SUN/IRAF and AOS/IRAF.
  </p>
  <p>
  The current version of IRAF magtape I/O does not read beyond the first 
  volume of a multivolume tape.
  </p>
  
  <!-- EndSection:    'BUGS' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS'  -->
  
