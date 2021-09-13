.. _rfits:

rfits — Convert FITS image data into a list of IRAF images
==========================================================

**Package: dataio**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  rfits -- convert image data in FITS files to individual IRAF images 
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  rfits fits_file file_list iraf_file
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>fits_file</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fits_file' Line='fits_file'>
  <DD>The FITS data source.  Fits_file is either a list of disk files or a tape
  device specification of the form mt[*][n], where mt is the mag tape
  device (e.g. mta), * is an optional density (e.g. 1600), and [n] is an
  optional tape file number. If n is specified then only image data in the
  nth tape file is read.
  </DD>
  </DL>
  <DL>
  <DT><B>file_list</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='file_list' Line='file_list'>
  <DD>The list of FITS extensions to be read from each disk file or from a single
  tape file, or the list of tape files AND FITS extensions to be read from
  an entire tape.  FITS extensions are numbered from 0 to n, tape files are
  numbered from 1 to n. If file_list is "<TT></TT>", only the 0th extension is read
  from each disk file or from a single tape file, but all the files and
  extensions are read from an entire tape. Legal file lists are composed
  of a series of file numbers and / or file ranges separated by commas
  or whitespace.  For example the string
  <P>
  	"<TT>1-3,4-8</TT>"
  <P>
  will convert ALL the FITS extensions in files 1 through 8 on tape,
  but only FITS extensions 1 through 8 from a disk file or a single tape file.
  For the case of disk input, the same FITS extensions must be read from
  each input file.  For the case of tape input the FITS extensions to be
  read from each file must be specified separately. For example the following
  string
  <P>
  	"<TT>1-10[2-4],15-21[1-10]</TT>"
  <P>
  tells rfits to convert extensions 2 through 4 in tape files 1 through 10
  and extensions 1 through 10 in tape files 15 through 21. Rfits will only
  convert extensions which contain image data. Other types of fits data
  such as tables will not be converted.
  </DD>
  </DL>
  <DL>
  <DT><B>iraf_file</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='iraf_file' Line='iraf_file'>
  <DD>The IRAF file which will receive the FITS image data if the make_image parameter
  switch is set.  Iraf_file may be a template of output image names or
  a single root output image name. In the former case one output image name
  must be specified for every input file. In the latter case iraf_file is
  a root output image name to which the input file sequence number or tape
  file number is appended if the number of input files &gt; 1. For example
  reading files 1 and 3 from a FITS tape with a value of iraf_file of "<TT>data</TT>"
  will produce the files data0001 and data0003, whereas reading the same
  two files with a value of iraf_file of "<TT>data1,data2</TT>" will produce the files
  data1 and data2. Extension numbers will be appended to the root output
  names if appropriate.
  </DD>
  </DL>
  <DL>
  <DT><B>make_image = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='make_image' Line='make_image = yes'>
  <DD>If make_images is "<TT>yes</TT>" convert the FITS image data to IRAF image data,
  otherwise simply print the header information using the long_header or
  short_header switches.
  </DD>
  </DL>
  <DL>
  <DT><B>long_header = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='long_header' Line='long_header = no'>
  <DD>If long_header is "<TT>yes</TT>" the full FITS header is printed on the standard output.
  </DD>
  </DL>
  <DL>
  <DT><B>short_header = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='short_header' Line='short_header = yes'>
  <DD>If short_header is "<TT>yes</TT>" and long_header is "<TT>no</TT>", only the output filename,
  the title string, and the image dimensions are printed on the standard output.
  </DD>
  </DL>
  <DL>
  <DT><B>datatype</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='datatype' Line='datatype'>
  <DD>The output image data type. Datatype may be s (short integer), i (integer),
  u (unsigned integer), l (long integer), r (real), or d (double).  Data
  truncation may occur if an inappropriate data type is specified. If an
  unsupported data type or a null string is supplied then a default data
  type is selected based on the value of the fits bitpix, bscale, and bzero
  parameters.  If the bscale and bzero parameters in the FITS header are
  undefined or equal to 1.0 and 0.0 respectively, rfits selects datatype
  s or l depending on bitpix. If bscale and bzero are set to 1.0 and 32768.0,
  rfits selects datatype, otherwise rfits selects datatype r.
  </DD>
  </DL>
  <DL>
  <DT><B>blank = 0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='blank' Line='blank = 0.'>
  <DD>The IRAF image value assigned to a FITS blank pixel.
  </DD>
  </DL>
  <DL>
  <DT><B>scale = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='scale' Line='scale = yes'>
  <DD>If scale is "<TT>no</TT>" then the data values are read directly from the FITS image
  without conversion.  Otherwise rfits scales the data before output using
  the values of bscale and bzero.
  </DD>
  </DL>
  <DL>
  <DT><B>oldirafname = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='oldirafname' Line='oldirafname = no'>
  <DD>If the oldirafname switch is set rfits will attempt to restore the image to
  disk with the filename defined by the IRAFNAME parameter in the FITS header.
  </DD>
  </DL>
  <DL>
  <DT><B>offset = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='offset' Line='offset = 0'>
  <DD>An integer parameter specifying the offset to the current tape file
  number. For example if offset = 100, iraf_file = "<TT>fits</TT>" and file_list = "<TT>1-3</TT>"
  then the output file names will be "<TT>fits0101</TT>", "<TT>fits0102</TT>" and "<TT>fits0103</TT>"
  respectively rather than "<TT>fits0001</TT>", "<TT>fits0002</TT>" and "<TT>fits0003</TT>".
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  FITS data is read from the specified source; either disk or
  magnetic tape.  The FITS header may optionally be printed on the standard
  output as either a full listing or a short description.
  The FITS long blocks option is supported. 
  <P>
  At present non-standard FITS files (SIMPLE = F) and files containing
  group data are skipped and a warning message is issued.
  Image stored in the FITS standard extension IMAGE can be read.
  Other standard extensions such as TABLE and BINTABLE are currently ignored.
  <P>
  A warning message will be issued if the default user area allocated in
  memory is too small
  to hold all the FITS parameter cards being read in by RFITS.
  Since the default user area is 64000
  characters and a single card image is 81 characters long, the normal
  user area will hold ~800 complete card images. RFITS will not permit
  partial cards to be written. The user can override the default user area
  length by setting the environment variable min_lenuserarea (see example
  below).
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Convert all the image data  on a mag tape to individual IRAF
  images. Allow rfits to select the output datatype  and set blanks
  to zero.
  <P>
  <PRE>
  	cl&gt; rfits mtb1600 "" images
  <P>
  	      or alternatively
  <P>
  	cl&gt; rfits mtb1600 * images
  </PRE>
  <P>
  2. Convert FITS files on disk to IRAF images. In the first example case the
  files specified by fits* are written to images images0001, images0002, etc.
  In the second example the fits disk files listed one per line in the text
  file fitslist are written to the output images listed one per line in
  the file imlist. Note that by using 0 or "<TT></TT>" for the file_list parameter
  the user has told rfits to read only the primary fits data unit.
  <P>
  <PRE>
  	cl&gt; rfits fits* "" images
  <P>
  	      or alternatively
  <P>
  	cl&gt; rfits fits* 0 images
  <P>
  <P>
  	cl&gt; rfits @fitslist "" @imlist
  <P>
  	      or alternatively
  <P>
  	cl&gt; rfits @fitslist 0 @imlist
  </PRE>
  <P>
  3. List the contents of a FITS tape on the standard output without creating
  any image files.
  <P>
  <PRE>
  	cl&gt; rfits mtb1600 "" images ma-
  </PRE>
  <P>
  4. Convert FITS files on tape directly to IRAF images without scaling.
  <P>
  <PRE>
  	cl&gt; rfits mtb1600 "" images scal-
  </PRE>
  <P>
  5. Convert the first three FITS files on tape to IRAF image converting FITS
  blank values to  -1 in the process. Note that the user will not get what
  he or she expects if the output data type is ushort.
  <P>
  <PRE>
  	cl&gt; rfits mta 1-3 images blank=-1
  </PRE>
  <P>
  6. Read in a disk FITS file with a header roughly twice the usual IRAF length
  of 64000 characters.
  <P>
  <PRE>
  	cl&gt; set min_lenuserarea = 128000
  	cl&gt; rfits fitsimage "" image
  </PRE>
  <P>
  7. Read a FITS tape which has 5 normal fits records (2880 bytes) to a tape
  record.  Notice that no hidden rfits parameters are required to do this.
  <P>
  <PRE>
  	cl&gt; rfits mta * images
  </PRE>
  <P>
  8. Convert only the zeroth FITS extension in each of the first 100 files on a
  magnetic tape and try to restore the original IRAF image name in the process.
  <P>
  <PRE>
  	cl&gt; rfits mta 1-100[0] images old+
  </PRE>
  <P>
  9. Convert the second, third, and fourth FITS extensions in the first 100
  files of a FITS tape and try to restore the original IRAF name in the process.
  <P>
  <PRE>
  	cl&gt; rfits mta "1-100[2-4]" images old+
  </PRE>
  <P>
  10. Convert the second, third, and fourth FITS extensions in each of a list of
  disk files and restore the original IRAF name in the process.
  <P>
  <PRE>
  	cl&gt; rfits @fitslist "2-4" images old+
  </PRE>
  <P>
  11. Convert the second, third, and fourth FITS extensions in the fifth
  mag tape file and try to restore the original IRAF name in the process.
  <P>
  <PRE>
  	cl&gt; rfits mta[5] "2-4" images old+
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  Blank pixels are counted and set to a user determined value, but they are not
  records in the output image header.
  <P>
  Rfits can read image data only. Other FITS data types such as ASCII and
  binary tables are skipped.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  wfits, reblock, t2d, fits kernel
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
