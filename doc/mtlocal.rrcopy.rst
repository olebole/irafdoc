rrcopy — Convert IPPS rasters from an RCOPY tape to IRAF images
===============================================================

**Package: mtlocal**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>rrcopy (Jun87)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.mtlocal</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>rrcopy (Jun87)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>rrcopy</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  rrcopy -- Convert IPPS rasters from RCOPY tapes to IRAF images
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  rrcopy rcopy_file raster_list iraf_file
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_rcopy_file">rcopy_file</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rcopy_file' Line='rcopy_file'>
  <DD>The RCOPY data source, i.e., the name of a magtape device or a RCOPY
  format disk file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_raster_list">raster_list</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='raster_list' Line='raster_list'>
  <DD>A string listing the IPPS rasters to be read from the rcopy file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_iraf_file">iraf_file</A></B></DT>
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
  <DT><B><A NAME="l_make_image">make_image = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='make_image' Line='make_image = yes'>
  <DD>This switch determines whether RCOPY image data is converted to an IRAF image
  file.  When this switch it set to no, only a listing is produced, no output
  image is written. 
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_print_header">print_header = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='print_header' Line='print_header = yes'>
  <DD>This switch determines if the header information will be printed for those
  rasters in "<TT>raster_list</TT>".  (It might be appropriate to set print_header=no, or
  redirect the output, if RRCOPY is being run as a background task.)
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_data_type">data_type = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='data_type' Line='data_type = ""'>
  <DD>The data type of the output IRAF image.  If an incorrect data_type or null 
  string is entered, the default data type used is
  determined by the number of bits per pixel in the IPPS raster.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  IPPS rasters stored on RCOPY tapes are read from the specified source.
  IPPS raster header information is listed.  The image data may optionally
  be converted to an IRAF image file.  It takes RRCOPY about 16 cpu seconds
  to read a 256 x 256 30-bit IPPS raster; 42 cpu seconds for a 320 x 512
  30-bit raster; 34 cpu seconds for a 320 x 512 20-bit raster.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
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
  <H2><A NAME="s_bugs">BUGS</A></H2>
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
  
  </BODY>
  </HTML>