rcamera — Convert a CAMERA image into an IRAF image
===================================================

**Package: mtlocal**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>rcamera (Jan87)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.mtlocal</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>rcamera (Jan87)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>rcamera</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  rcamera -- Convert Kitt Peak CAMERA image files to IRAF image files
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  rcamera camera_file file_list iraf_file
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_camera_file">camera_file</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='camera_file' Line='camera_file'>
  <DD>The CAMERA data source.  If the data source is a list of disk files or an
  explicit tape file
  specification of the form mt*[n] where n is a file number. If the file
  number is specified then only that file
  is converted.  If the general tape device name is given, i.e. mta, mtb800, etc,
  then the files specified by the file_list parameter will be read from the tape.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_file_list">file_list</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='file_list' Line='file_list'>
  <DD>The files to be read from a tape are specified by the file_list string.  The
  string can consist of any sequence of file numbers separated by
  at least one of comma, or dash.
  A dash specifies a range of files.  For example the string
  <P>
  	"<TT>1,2,3-5,8-6</TT>"
  <P>
  will convert the files 1 through 8.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_iraf_file">iraf_file</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='iraf_file' Line='iraf_file'>
  <DD>The IRAF file which will receive the CAMERA data if the make_image parameter
  switch is set.  For multiple disk or tape files the filename
  will be used as a prefix and the tape file number or disk sequence number
  will be appended.   Otherwise,
  the file will be named as specified.  Thus,
  reading files 1 and 3 from a CAMERA tape with a iraf_file set to data will
  produce the files data001 and data003.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_image_list">image_list = "<TT>1</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image_list' Line='image_list = "1"'>
  <DD>The list of CAMERA images to extract from a single tape file. For all recent
  tapes image_list = "<TT>1</TT>". Old tapes were however contained multiple images
  per file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_make_image">make_image = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='make_image' Line='make_image = yes'>
  <DD>This switch determines whether CAMERA image data is converted to an IRAF image
  file.  This switch is set to no to obtain just header information with the
  long_header or short_header switches.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_long_header">long_header = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='long_header' Line='long_header = no'>
  <DD>If this switch is set the full CAMERA header is printed on the standard output.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_short_header">short_header = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='short_header' Line='short_header = yes'>
  <DD>If this switch is set only the output filename,
  the title string, and the image dimensions are printed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_standard_format">standard_format = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='standard_format' Line='standard_format = yes'>
  <DD>The CAMERA standard format has the least significant byte first.  Some CAMERA
  data, however, does not follow this byte order convention.  Thus, to read
  the non-standard CAMERA data this parameter is set to no.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_datatype">datatype = "<TT>s</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='datatype' Line='datatype = "s"'>
  <DD>The IRAF image file may be of a different data type than the CAMERA image data.
  The data type may be specified as s for short, l for long, r for real, and
  d for double.  The user must beware of truncation problems if an
  inappropriate data type is specified.  If an incorrect data_type or a
  null string is given for this parameter then a default data type is used
  which is the appropriate minimum size for the input pixel values.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_offset">offset = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='offset' Line='offset = 0'>
  <DD>Offset is an integer parameter specifying the offset to the tape file number
  appended to iraf_file. For example if the user specifies offset = 100,
  iraf_file = "<TT>cam</TT>" and file_list = "<TT>1-3</TT>", the output file names produced
  will be "<TT>cam101</TT>", "<TT>cam102</TT>" and "<TT>cam103</TT>" respectively, instead of "<TT>cam001</TT>",
  "<TT>cam002</TT>" and "<TT>cam003</TT>".
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  Kitt Peak CAMERA format image data is read from the specified source;
  either a disk or magnetic tape.
  The CAMERA header may optionally be printed on the standard
  output as either a full listing or a short description.  Image data may
  optionally be converted to an IRAF image of specified data type.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  Convert a camera image tape to a set of IRAF images.
  <P>
  <PRE>
  	cl&gt; rcamera mtb1600 1-999 images
  </PRE>
  <P>
  Convert a list of camera disk files to IRAF images.
  <P>
  <PRE>
  	cl&gt; rcamera cam* 1 images
  </PRE>
  <P>
  List the contents of a camera tape on the standard output without
  creating an image file.
  <P>
  <PRE>
  	cl&gt; rcamera mtb1600 1-999 images ma-
  </PRE>
  <P>
  Read images 1-3 and 6-8 from an old CAMERA tape with many images per file.
  <P>
  <PRE>
  	cl&gt; rcam mtb1600[1] image image_list=1-3,6-8
  </PRE>
  </UL>
  <! EndSection:    'EXAMPLES'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES'  >
  
  </BODY>
  </HTML>