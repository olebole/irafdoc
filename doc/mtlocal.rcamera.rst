.. _rcamera:

rcamera: Convert a CAMERA image into an IRAF image
==================================================

**Package: mtlocal**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  rcamera -- Convert Kitt Peak CAMERA image files to IRAF image files
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  rcamera camera_file file_list iraf_file
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>camera_file</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='camera_file' Line='camera_file' -->
  <dd>The CAMERA data source.  If the data source is a list of disk files or an
  explicit tape file
  specification of the form mt*[n] where n is a file number. If the file
  number is specified then only that file
  is converted.  If the general tape device name is given, i.e. mta, mtb800, etc,
  then the files specified by the file_list parameter will be read from the tape.
  </dd>
  </dl>
  <dl>
  <dt><b>file_list</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='file_list' Line='file_list' -->
  <dd>The files to be read from a tape are specified by the file_list string.  The
  string can consist of any sequence of file numbers separated by
  at least one of comma, or dash.
  A dash specifies a range of files.  For example the string
  	<tt>"1,2,3-5,8-6"</tt>
  will convert the files 1 through 8.
  </dd>
  </dl>
  <dl>
  <dt><b>iraf_file</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='iraf_file' Line='iraf_file' -->
  <dd>The IRAF file which will receive the CAMERA data if the make_image parameter
  switch is set.  For multiple disk or tape files the filename
  will be used as a prefix and the tape file number or disk sequence number
  will be appended.   Otherwise,
  the file will be named as specified.  Thus,
  reading files 1 and 3 from a CAMERA tape with a iraf_file set to data will
  produce the files data001 and data003.
  </dd>
  </dl>
  <dl>
  <dt><b>image_list = <tt>"1"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='image_list' Line='image_list = "1"' -->
  <dd>The list of CAMERA images to extract from a single tape file. For all recent
  tapes image_list = <tt>"1"</tt>. Old tapes were however contained multiple images
  per file.
  </dd>
  </dl>
  <dl>
  <dt><b>make_image = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='make_image' Line='make_image = yes' -->
  <dd>This switch determines whether CAMERA image data is converted to an IRAF image
  file.  This switch is set to no to obtain just header information with the
  long_header or short_header switches.
  </dd>
  </dl>
  <dl>
  <dt><b>long_header = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='long_header' Line='long_header = no' -->
  <dd>If this switch is set the full CAMERA header is printed on the standard output.
  </dd>
  </dl>
  <dl>
  <dt><b>short_header = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='short_header' Line='short_header = yes' -->
  <dd>If this switch is set only the output filename,
  the title string, and the image dimensions are printed.
  </dd>
  </dl>
  <dl>
  <dt><b>standard_format = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='standard_format' Line='standard_format = yes' -->
  <dd>The CAMERA standard format has the least significant byte first.  Some CAMERA
  data, however, does not follow this byte order convention.  Thus, to read
  the non-standard CAMERA data this parameter is set to no.
  </dd>
  </dl>
  <dl>
  <dt><b>datatype = <tt>"s"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='datatype' Line='datatype = "s"' -->
  <dd>The IRAF image file may be of a different data type than the CAMERA image data.
  The data type may be specified as s for short, l for long, r for real, and
  d for double.  The user must beware of truncation problems if an
  inappropriate data type is specified.  If an incorrect data_type or a
  null string is given for this parameter then a default data type is used
  which is the appropriate minimum size for the input pixel values.
  </dd>
  </dl>
  <dl>
  <dt><b>offset = 0</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='offset' Line='offset = 0' -->
  <dd>Offset is an integer parameter specifying the offset to the tape file number
  appended to iraf_file. For example if the user specifies offset = 100,
  iraf_file = <tt>"cam"</tt> and file_list = <tt>"1-3"</tt>, the output file names produced
  will be <tt>"cam101"</tt>, <tt>"cam102"</tt> and <tt>"cam103"</tt> respectively, instead of <tt>"cam001"</tt>,
  <tt>"cam002"</tt> and <tt>"cam003"</tt>.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  Kitt Peak CAMERA format image data is read from the specified source;
  either a disk or magnetic tape.
  The CAMERA header may optionally be printed on the standard
  output as either a full listing or a short description.  Image data may
  optionally be converted to an IRAF image of specified data type.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  Convert a camera image tape to a set of IRAF images.
  </p>
  <pre>
  	cl&gt; rcamera mtb1600 1-999 images
  </pre>
  <p>
  Convert a list of camera disk files to IRAF images.
  </p>
  <pre>
  	cl&gt; rcamera cam* 1 images
  </pre>
  <p>
  List the contents of a camera tape on the standard output without
  creating an image file.
  </p>
  <pre>
  	cl&gt; rcamera mtb1600 1-999 images ma-
  </pre>
  <p>
  Read images 1-3 and 6-8 from an old CAMERA tape with many images per file.
  </p>
  <pre>
  	cl&gt; rcam mtb1600[1] image image_list=1-3,6-8
  </pre>
  
  <!-- EndSection:    'EXAMPLES' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES'  -->
  
