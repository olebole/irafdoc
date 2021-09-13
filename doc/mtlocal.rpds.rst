.. _rpds:

rpds — Convert a PDS image into an IRAF image
=============================================

**Package: mtlocal**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  rpds -- Convert Kitt Peak PDS image files to IRAF image files
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  rpds pds_file file_list iraf_file
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>pds_file</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pds_file' Line='pds_file'>
  <DD>The PDS data source. The data source may be a template specifying
  a list of disk files, e.g. pds* or a mag tape file specification of
  the form mtl*[n], e.g. "<TT>mta1600</TT>" or "<TT>mtb800[1]</TT>". The mt specifies magtape,
  l specifies the drive, a,b,c etc, * specifies the density and [n]
  the tape file number. If no tape file number is specified rpds reads
  the tape files specified by file_list.
  </DD>
  </DL>
  <DL>
  <DT><B>file_list</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='file_list' Line='file_list'>
  <DD>A string parameter containing the list of tape files to be processed.
  File_list is only requested if no tape file number is specified in pds_file.
  For example the string
  <P>
  	"<TT>1,2,3-5,8-6</TT>"
  <P>
  will convert files 1 through 8.
  </DD>
  </DL>
  <DL>
  <DT><B>iraf_file</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='iraf_file' Line='iraf_file'>
  <DD>The IRAF file which will receive the PDS data if the make_image
  switch is set. If multiple files are input from tape or disk, the tape file
  number or disk sequence number will be appended to the output file name.
  </DD>
  </DL>
  <DL>
  <DT><B>make_image = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='make_image' Line='make_image = yes'>
  <DD>If make_image is not set, the PDS image headers are listed on the standard
  output and no image file is created.
  </DD>
  </DL>
  <DL>
  <DT><B>long_header = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='long_header' Line='long_header = no'>
  <DD>If this switch is set the full PDS header is printed on the standard output.
  </DD>
  </DL>
  <DL>
  <DT><B>short_header = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='short_header' Line='short_header = yes'>
  <DD>If this switch is set only the output filename,
  the title string, and the image dimensions for each image are printed
  on the standard output.
  </DD>
  </DL>
  <DL>
  <DT><B>datatype = "<TT>s</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='datatype' Line='datatype = "s"'>
  <DD>The IRAF image data type, s (short integer), i (integer), l (long integer),
   r (real) or d (double).
  </DD>
  </DL>
  <DL>
  <DT><B>tenbit = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='tenbit' Line='tenbit = no'>
  <DD>Old ten bit format?
  </DD>
  </DL>
  <DL>
  <DT><B>ninetrack = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ninetrack' Line='ninetrack = yes'>
  <DD>Ninetrack or old seven track tapes?
  </DD>
  </DL>
  <DL>
  <DT><B>offset = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='offset' Line='offset = 0'>
  <DD>Offset is an integer parameter which is added to the tape file number
  or disk sequence number and
  appended to the parameter iraf_file. For example if offset = 100,
  iraf_file = "<TT>pds</TT>" and file_list = "<TT>1-3</TT>" the output file names will be
  "<TT>pds101</TT>", "<TT>pds102</TT>" and "<TT>pds103</TT>" respectively, instead of "<TT>pds001</TT>", "<TT>pds002</TT>"
  and "<TT>pds003</TT>".
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  Kitt Peak PDS data is read into IRAF from either a
  list of disk files or magnetic tape.
  The PDS header may optionally be printed on the standard output as either a
  full listing or a short description.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  Convert a ninetrack PDS image tape to a set of IRAF images.
  <P>
  <PRE>
  	cl&gt; pdsread mtb1600 1-999 images
  </PRE>
  <P>
  List the contents of a nintrack PDS tape on the standard output.
  <P>
  <PRE>
  	cl&gt; pdsread mtb1600 1-999 images ma-
  </PRE>
  <P>
  Convert a list of pds file on disk to IRAF images.
  <P>
  <PRE>
  	cl&gt; pdsread pds* 1 images
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  <P>
  </UL>
  <! EndSection:    'BUGS'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS'  >
  
