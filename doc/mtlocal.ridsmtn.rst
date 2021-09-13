ridsmtn — Convert mountain format IDS/IRS data to IRAF images
=============================================================

**Package: mtlocal**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>ridsmtn (Jun86)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.mtlocal</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>ridsmtn (Jun86)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>ridsmtn</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  ridsmtn -- convert mountain format IDS data to IRAF images
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  ridsmtn ids_file iraf_file
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_ids_file">ids_file</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ids_file' Line='ids_file'>
  <DD>The IDS data source.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_iraf_file">iraf_file</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='iraf_file' Line='iraf_file'>
  <DD>The IRAF file which will receive the data if the <I>make_image</I> parameter
  is set.  If multiple records are being read, the output
  filename is concatenated from this parameter and the IDS record number.
  IRAF images with these names would be created from IDS records 1, 2 and 3 if
  <I>iraf_file</I> = "<TT>ids</TT>" (and offset = 0; see below):  ids.0001, ids.0002, 
  ids.0003.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_file_number">file_number = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='file_number' Line='file_number = 1'>
  <DD>If <I>ids_file</I> is a tape device, this parameter tells which tape file
  will be read.  In almost all cases, the IDS data will occupy the first
  and only file on the tape.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_record_numbers">record_numbers = "<TT>1-9999</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='record_numbers' Line='record_numbers = "1-9999"'>
  <DD>A string listing the IDS records to be read.  
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_reduced_data">reduced_data = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='reduced_data' Line='reduced_data = yes'>
  <DD>A boolean parameter which indicates the data is mountain reduced if set
  to yes, and that the data is raw (unreduced) if set to no.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_np1">np1 = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='np1' Line='np1 = 0'>
  <DD>The starting pixel to extract in the image. If set to 0, the
  record header parameter NP1 will be used to determine the
  starting pixel.
  This and the following parameter are in effect only when reduced_data
  is set to no. If reduced_data=yes, then the entire spectrum (1024 points)
  is copied.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_np2">np2 = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='np2' Line='np2 = 0'>
  <DD>The ending pixel to extract. If set to 0, the record
  header parameter NP2 will be used to determine the
  starting pixel.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_make_image">make_image = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='make_image' Line='make_image = yes'>
  <DD>This switch determines whether the IDS records are converted to IRAF images.
  When <I>make_image</I> = no, only a listing of the headers is produced, 
  no output image is written.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_print_pixels">print_pixels = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='print_pixels' Line='print_pixels = no'>
  <DD>When this parameter is set to yes, the values of the ids pixels are printed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_long_header">long_header = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='long_header' Line='long_header = no'>
  <DD>This parameter determines whether a long or short header is printed.  The
  short header contains only the record number and ID string; the long header
  contains all information available 
  including the RA, Dec, HA, ST, UT, reduction flags, airmass, integration time,
  starting wavelength and wavelength per channel information.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_data_type">data_type = "<TT>r</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='data_type' Line='data_type = "r"'>
  <DD>The data type of the output IRAF image.  If an incorrect data_type or null
  string is entered, the default data type <I>real</I> is used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_offset">offset = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='offset' Line='offset = 0'>
  <DD>The integer value of this parameter is added to each IDS record number when
  generating output filenames.  Filenames are of the form 
  <PRE>
  	<I>iraf_file</I>.record_number+<I>offset</I>
  <P>
  </PRE>
  The offset parameter can be used to create a sequence of output IRAF 
  filenames with continuous, sequential suffixes over more than one night's data.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The IDS records from either a raw or reduced IDS mountain tape are read and
  optionally converted to a sequence of one dimensional IRAF images.  The records
  to be read can be specified.  The IDS header information is printed in either 
  a short or long form.  The pixel values can be listed as well.
  <P>
  The entire image may be extracted (default for reduced data) by specifying
  the parameters np1=1 and np2=1024 (IIDS and IRS). Otherwise, the
  header parameters NP1 and NP2 will be used to indicate the useful
  portion of the spectrum. For raw data these values are 6 and 1024 for the
  IIDS and 68 and 888 for the IRS (your IRS values may vary).
  <P>
  On the mountain, the NEW-TAPE command writes a dummy record on tape with a
  record number equal to the starting record number minus 1.  If this dummy
  record number is included in the <I>record_numbers</I> range, a meaningless
  IRAF image will be written.  In most cases, the dummy record number = 0.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  [1] Convert all records on the IDS tape to IRAF images, with the root image name
  being "<TT>aug83</TT>".  The data is mountain reduced, and all records will be
  converted.  The IDS tape is mounted on mtb.
  	
  	cl&gt; ridsmtn mtb aug83
  <P>
  [2] List the headers from the same mountain tape read in example 1 but don't
  make output images.  A <I>long_header</I> will be listed; sample output is shown.
  <P>
  	cl&gt; ridsmtn mtb make_image=no long_header=yes
  <P>
  <PRE>
  <P>
  RECORD = 79, label = "NGC 7662 7.4E 10S AUG 23/24 84 CLOUDS",
  oflag = OBJECT, beam_number = 0,  W0 = 4588.503,  WPC = 2.598, ITM = 120,
  NP1 = 0, NP2 = 1024,  UT = 7:37:04.0,  ST = 22:21:46.0,  HA = -1:03:25.7,
  RA = 23:25:12.6,   DEC = 42:26:37.0,   DRA = 7.4,   DDEC = -10.,
  df =-1, sm =-1, qf =-1, dc = 0, qd = 0, ex =-1, bs = -1, ca = -1, co = 0
  <P>
  <P>
  RECORD = 238, label = "HENEAR AUG 23/24 84 END 8.4" ENT",
  oflag = SKY,  beam_number = 1,  W0 = 4585.501,  WPC = 2.602, ITM = 400,
  NP1 = 8, NP2 = 1019,  UT = 12:31:01.0,  ST = 3:16:33.0,  HA = 0:17:16.3,
  RA = 2:59:16.7,   DEC = 31:57:30.0
  df = 6, sm = -1, qf = -1, dc = -1, qd =-1, ex =-1, bs =-1, ca =-1, co = -1,
  df[1] =  5889.2139, df[2] =  1355.6821, df[3] =  23.1303, df[4] = -2.85366, 
  df[5] =  3.0472932, df[6] =  -4.541831
  </PRE>
  <P>
  [3] Print the pixel values for records 5086 and 5087.  No output image will
  be written, and only the short header listed.  This time, the IDS tape 
  contains raw data, not reduced.
  <P>
  <PRE>
  	cl&gt; ridsmtn mtb red- make_im- rec=5086,5087 print_pix-
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  ridsout, ridsfile
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>