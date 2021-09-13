rdumpf — Convert IPPS rasters from a DUMPF tape to IRAF images
==============================================================

**Package: mtlocal**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>rdumpf (Jul87)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.mtlocal</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>rdumpf (Jul87)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>rdumpf</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  rdumpf -- convert IPPS rasters from DUMPF tapes to IRAF images
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  rdumpf dumpf_file file_list iraf_file
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_dumpf_file">dumpf_file</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dumpf_file' Line='dumpf_file'>
  <DD>The dumpf data source, i.e., the name of a magtape device.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_file_list">file_list</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='file_list' Line='file_list'>
  <DD>A string listing the permanent files to be read from the DUMPF tape.  
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_iraf_file">iraf_file</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='iraf_file' Line='iraf_file'>
  <DD>The IRAF file which will receive the image data if the <I>make_image</I>
  parameter
  is set.  If more then one raster is being read, the output
  filename is concatenated from the <I>iraf_file</I> parameter, the tape
  file number and the raster sequence number.  That is, reading rasters 1 - 3
  from files 3 and 4 with iraf_file = <I>pic</I> would generate a sequence of 
  files:
  pic3.001, pic3.002, pic3.003, pic4.001, pic4.002, pic4.003.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_raster_list">raster_list = "<TT>1-999</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='raster_list' Line='raster_list = "1-999"'>
  <DD>A string listing the IPPS rasters to be read from each file specified by
  the <I>file_list</I> parameter.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_make_image">make_image = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='make_image' Line='make_image = yes'>
  <DD>This switch determines whether the IPPS rasters are converted to IRAF images.
  When this switch is set to <I>no</I>, only a listing of the IPPS rasters is 
  produced, no output image is written.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_print_header">print_header = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='print_header' Line='print_header = yes'>
  <DD>This switch determines if the IPPS header information will be listed for those
  rasters being read.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_data_type">data_type = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='data_type' Line='data_type = ""'>
  <DD>The data type of the output IRAF image.  If an incorrect data_type or null
  string is entered, the default data type used is determined by the number
  of bits per pixel in the IPPS raster.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  IPPS rasters stored in DUMPF format are read and optionally converted to
  IRAF images.  The IPPS ID and other header information is printed.
  The rasters to be converted are specified by both a file
  number and then a raster number within that file.  It may be helpful to
  first run task <B>ldumpf</B> to list the contents of the DUMPF tape; only
  IPPS rasters can be converted.  
  <BR>
  Some dumpf volumes are written on more than one tape.
  Task <I>rdumpf</I> cannot recover a file that is split across two tapes on 
  a "<TT>multi-volume-set</TT>" dumpf tape.  It is, however, possible to read the files
  beyond the leading partial file; this is done by incrementing the 
  <B>file_list</B> parameter by 1.  For example, the first complete file 
  on the second tape of a multi-volume-set is indicated by <B>file_list</B> = 2.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  [1] Convert all rasters in the 3rd permanent file on tape:
  <P>
  	cl&gt; rdumpf mta 3 ipps
  <P>
  [2] Convert all rasters in all permanent files:
  <P>
  	cl&gt; rdumpf mta 1-999 ipps
  <P>
  [3] List the first 10 IPPS rasters of the first permanent file:
  <P>
  	cl&gt; rdumpf mta 1 raster_list=1-10 make_image=no
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  The Cyber format readers, including <I>rdumpf</I>, have not been implemented
  on SUN/IRAF and AOS/IRAF.
  <P>
  The current version of IRAF magtape I/O does not read beyond the first
  volume of a multivolume tape.  As described above, <I>rdumpf</I> cannot
  read a file split across two tapes.
  <BR>
  The record structure of a DUMPF tape is used to
  filter out noise records and extraneous bits that fill out a tape byte;
  this tape structure information is lost when the tape is copied to disk,
  and so <B>rdumpf</B> may not be able to convert some DUMPF format disk files.
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  ldumpf
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>