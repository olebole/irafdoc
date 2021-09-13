.. _rrcopy:

rrcopy — Convert IPPS rasters from an RCOPY tape to IRAF images
===============================================================

**Package: mtlocal**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  rrcopy -- Convert IPPS rasters from RCOPY tapes to IRAF images
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  rrcopy rcopy_file raster_list iraf_file
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>rcopy_file</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rcopy_file' Line='rcopy_file'>
  <DD>The RCOPY data source, i.e., the name of a magtape device or a RCOPY
  format disk file.
  </DD>
  </DL>
  <DL>
  <DT><B>raster_list</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='raster_list' Line='raster_list'>
  <DD>A string listing the IPPS rasters to be read from the rcopy file.
  </DD>
  </DL>
  <DL>
  <DT><B>iraf_file</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='iraf_file' Line='iraf_file'>
  <DD>The IRAF file which will receive the RCOPY data if the make_image parameter
  is set.  If more than one raster is being read, the output filenames
  will be concatenated from this
  parameter and the raster sequence number on the RCOPY tape.  That
  is, reading rasters 1 thru 8 from tape into iraf_file 'pic'
  would generate a sequence of files: pic001, pic002, ..., pic008.
  </DD>
  </DL>
  <DL>
  <DT><B>make_image = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='make_image' Line='make_image = yes'>
  <DD>This switch determines whether RCOPY image data is converted to an IRAF image
  file.  When this switch it set to no, only a listing is produced, no output
  image is written. 
  </DD>
  </DL>
  <DL>
  <DT><B>print_header = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='print_header' Line='print_header = yes'>
  <DD>This switch determines if the header information will be printed for those
  rasters in "<TT>raster_list</TT>".  (It might be appropriate to set print_header=no, or
  redirect the output, if RRCOPY is being run as a background task.)
  </DD>
  </DL>
  <DL>
  <DT><B>data_type = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='data_type' Line='data_type = ""'>
  <DD>The data type of the output IRAF image.  If an incorrect data_type or null 
  string is entered, the default data type used is
  determined by the number of bits per pixel in the IPPS raster.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  IPPS rasters stored on RCOPY tapes are read from the specified source.
  IPPS raster header information is listed.  The image data may optionally
  be converted to an IRAF image file.  It takes RRCOPY about 16 cpu seconds
  to read a 256 x 256 30-bit IPPS raster; 42 cpu seconds for a 320 x 512
  30-bit raster; 34 cpu seconds for a 320 x 512 20-bit raster.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  [1] List all IPPS headers from an RCOPY tape:
  <P>
  	cl&gt; rrcopy mtb 1-999 make_image=no
  <P>
  [2] Read the first 5 rasters from tape into IRAF images ipps001 
  through ipps005 with default data types:
  <P>
  	cl&gt; rrcopy mtb 1-5 ipps
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  The Cyber format readers, including <I>rrcopy</I>, have not been implemented
  on SUN/IRAF and AOS/IRAF.
  <P>
  The current version of IRAF magtape I/O does not read beyond the first 
  volume of a multivolume tape.
  </UL>
  <! EndSection:    'BUGS'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS'  >
  
