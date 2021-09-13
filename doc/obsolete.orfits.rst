orfits — Convert a FITS image into an IRAF image (dataio V2.10.4)
=================================================================

**Package: obsolete**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>orfits (Jan90)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>dataio</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>orfits (Jan90)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>orfits</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  orfits -- convert FITS data files to IRAF image files
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  orfits fits_file file_list iraf_file
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_fits_file">fits_file</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fits_file' Line='fits_file'>
  <DD>The FITS data source.  This is either a template describing a list of disk files
  or a tape file
  specification of the form mt*[n], where mt indicates a mag tape device,
  * represents a density, and [n] is the tape file number.
  If the tape file number n is specified then only that file
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
  <DD>The IRAF file which will receive the FITS data if the make_image parameter
  switch is set.  Iraf_file can be a template of output image names or
  a root output image name. In the former case one output image name
  must be specified for every input file. In the latter case iraf_file is
  a root output image name to which the input file sequence number or tape
  file number is appended if the number of input files &gt; 1. For example
  reading files 1 and 3 from a FITS tape with a value of iraf_file of "<TT>data</TT>"
  will produce the files data0001 and data0003, whereas reading the same
  two files with a value of iraf_file of "<TT>data1,data2</TT>" will produce the files
  data1 and data2.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_make_image">make_image = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='make_image' Line='make_image = yes'>
  <DD>This switch determines whether FITS image data is converted to an IRAF image
  file.  This switch is set to no to obtain just header information with the
  long_header or short_header switches.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_long_header">long_header = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='long_header' Line='long_header = no'>
  <DD>If this switch is set the full FITS header is printed on the standard output.
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
  <DT><B><A NAME="l_datatype">datatype</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='datatype' Line='datatype'>
  <DD>The IRAF image file may be of a different data type than the FITS image data.
  The data type may be specified as s for short, u for unsigned short,
  i for integer, l for long,
  r for real, and d for double.  The user must beware of truncation problems if an
  inappropriate data type is specified.  If an incorrect data_type or a
  null string is given for this parameter then a default data type is used
  which is the appropriate minimum size for the input pixel values.
  If the bscale and bzero parameters in the FITS header are undefined or equal to 
  1.0 and 0.0 respectively, orfits
  selects datatype s or l depending on bitpix. If bscale and bzero are set to
  other than 1.0 and 0.0, orfits selects datatype r.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_blank">blank = 0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='blank' Line='blank = 0.'>
  <DD>The IRAF image value of a blank pixel.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_scale">scale = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='scale' Line='scale = yes'>
  <DD>If scale equals no the integers are read directly off the tape.
  Otherwise ORFITS checks the values of bscale and bzero. If these numbers
  are not 1. and 0. respectively, ORFITS scales the data before output.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_oldirafname">oldirafname = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='oldirafname' Line='oldirafname = no'>
  <DD>If the oldirafname switch is set ORFITS will attempt to restore the image to
  disk with the filename defined by the IRAFNAME parameter in the FITS header.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_offset">offset = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='offset' Line='offset = 0'>
  <DD>Offset is an integer parameter specifying the offset to the current tape file
  number. For example if offset = 100, iraf_file = "<TT>fits</TT>" and file_list = "<TT>1-3</TT>"
  then the output file names will be "<TT>fits0101</TT>", "<TT>fits0102</TT>" and "<TT>fits0103</TT>"
  respectively rather than "<TT>fits0001</TT>", "<TT>fits0002</TT>" and "<TT>fits0003</TT>".
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  FITS data is read from the specified source; either disk or
  magnetic tape.  The FITS header may optionally be printed on the standard
  output as either a full listing or a short description.
  The FITS long blocks option is supported. 
  At present non-standard FITS files (SIMPLE = F) and files containing
  group data are skipped and a warning message is issued.
  A warning message will be issued if the default user area allocated in
  memory is too small
  to hold all the FITS parameter cards being read in by ORFITS.
  Since the default user area is 8000
  characters and a single card image is 81 characters long, the normal
  user area will hold 98 complete card images. ORFITS will not permit
  partial cards to be written. The user can override the default user area
  length by setting the environment variable min_lenuserarea (see example
  below).
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Convert a set of FITS files on tape to a set of IRAF image files, allowing
  orfits to select the output datatype. Blanks are set to zero.
  <P>
  <PRE>
  	cl&gt; orfits mtb1600 1-999 images
  </PRE>
  <P>
  2. Convert a list of FITS files on disk to a set of IRAF images. In the first
  case the files specified by fits* are written to the images images0001,
  images0002, etc. In the second case the fits disk files listed one per
  line in the text file fitslist are written to the output images listed
  one per line in the file imlist.
  <P>
  <PRE>
  	cl&gt; orfits fits* * images
  <P>
  	cl. orfits @fitslist * @imlist
  </PRE>
  <P>
  3. List the contents of a FITS tape on the standard output without creating
  any image files.
  <P>
  <PRE>
  	cl&gt; orfits mtb1600 1-999 images ma-
  </PRE>
  <P>
  4. Convert FITS files directly to IRAF images without scaling.
  <P>
  <PRE>
  	cl&gt; orfits mtb1600 1-999 images scal-
  </PRE>
  <P>
  5. Convert the first three FITS files on tape to IRAF files setting blanks
  to -1.
  <P>
  <PRE>
  	cl&gt; orfits mta 1-3 images blan=-1
  </PRE>
  <P>
  6. Read in a FITS file with a header roughly twice the usual IRAF length
  of 8000 characters.
  <P>
  <PRE>
  	cl&gt; set min_lenuserarea = 16300
  	cl&gt; orfits mta 1 images
  </PRE>
  <P>
  7. Read a FITS tape with 5 normal fits records (2880 bytes) to a tape record.
  Notice that no extra parameters are needed.
  <P>
  <PRE>
  	cl&gt; orfits mta 1-3 fits
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  Blank pixels are counted and set to a user determined value,  but not flagged
  in the image header.
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  owfits, reblock, t2d
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>