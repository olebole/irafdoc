.. _rpds:

rpds: Convert a PDS image into an IRAF image
============================================

**Package: mtlocal**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  rpds -- Convert Kitt Peak PDS image files to IRAF image files
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  rpds pds_file file_list iraf_file
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>pds_file</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='pds_file' Line='pds_file' -->
  <dd>The PDS data source. The data source may be a template specifying
  a list of disk files, e.g. pds* or a mag tape file specification of
  the form mtl*[n], e.g. <tt>"mta1600"</tt> or <tt>"mtb800[1]"</tt>. The mt specifies magtape,
  l specifies the drive, a,b,c etc, * specifies the density and [n]
  the tape file number. If no tape file number is specified rpds reads
  the tape files specified by file_list.
  </dd>
  </dl>
  <dl>
  <dt><b>file_list</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='file_list' Line='file_list' -->
  <dd>A string parameter containing the list of tape files to be processed.
  File_list is only requested if no tape file number is specified in pds_file.
  For example the string
  	<tt>"1,2,3-5,8-6"</tt>
  will convert files 1 through 8.
  </dd>
  </dl>
  <dl>
  <dt><b>iraf_file</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='iraf_file' Line='iraf_file' -->
  <dd>The IRAF file which will receive the PDS data if the make_image
  switch is set. If multiple files are input from tape or disk, the tape file
  number or disk sequence number will be appended to the output file name.
  </dd>
  </dl>
  <dl>
  <dt><b>make_image = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='make_image' Line='make_image = yes' -->
  <dd>If make_image is not set, the PDS image headers are listed on the standard
  output and no image file is created.
  </dd>
  </dl>
  <dl>
  <dt><b>long_header = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='long_header' Line='long_header = no' -->
  <dd>If this switch is set the full PDS header is printed on the standard output.
  </dd>
  </dl>
  <dl>
  <dt><b>short_header = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='short_header' Line='short_header = yes' -->
  <dd>If this switch is set only the output filename,
  the title string, and the image dimensions for each image are printed
  on the standard output.
  </dd>
  </dl>
  <dl>
  <dt><b>datatype = <tt>"s"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='datatype' Line='datatype = "s"' -->
  <dd>The IRAF image data type, s (short integer), i (integer), l (long integer),
   r (real) or d (double).
  </dd>
  </dl>
  <dl>
  <dt><b>tenbit = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='tenbit' Line='tenbit = no' -->
  <dd>Old ten bit format?
  </dd>
  </dl>
  <dl>
  <dt><b>ninetrack = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='ninetrack' Line='ninetrack = yes' -->
  <dd>Ninetrack or old seven track tapes?
  </dd>
  </dl>
  <dl>
  <dt><b>offset = 0</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='offset' Line='offset = 0' -->
  <dd>Offset is an integer parameter which is added to the tape file number
  or disk sequence number and
  appended to the parameter iraf_file. For example if offset = 100,
  iraf_file = <tt>"pds"</tt> and file_list = <tt>"1-3"</tt> the output file names will be
  <tt>"pds101"</tt>, <tt>"pds102"</tt> and <tt>"pds103"</tt> respectively, instead of <tt>"pds001"</tt>, <tt>"pds002"</tt>
  and <tt>"pds003"</tt>.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  Kitt Peak PDS data is read into IRAF from either a
  list of disk files or magnetic tape.
  The PDS header may optionally be printed on the standard output as either a
  full listing or a short description.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  Convert a ninetrack PDS image tape to a set of IRAF images.
  </p>
  <pre>
  	cl&gt; pdsread mtb1600 1-999 images
  </pre>
  <p>
  List the contents of a nintrack PDS tape on the standard output.
  </p>
  <pre>
  	cl&gt; pdsread mtb1600 1-999 images ma-
  </pre>
  <p>
  Convert a list of pds file on disk to IRAF images.
  </p>
  <pre>
  	cl&gt; pdsread pds* 1 images
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  
  <!-- EndSection:    'BUGS' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS'  -->
  
