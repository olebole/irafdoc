.. _ridsout:

ridsout — Convert a text file in IDSOUT format to IRAF images
=============================================================

**Package: mtlocal**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  ridsout -- convert IDSOUT format text file to IRAF images
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  ridsout idsout_file iraf_file
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>idsout_file</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='idsout_file' Line='idsout_file'>
  <DD>The text file or files containing the IDSOUT format data.  This will most likely
  be the redirected output from task <B>rcardimage</B>.
  </DD>
  </DL>
  <DL>
  <DT><B>iraf_file</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='iraf_file' Line='iraf_file'>
  <DD>The IRAF file which will receive the data if the <I>make_image</I> parameter
  is set.  If multiple records are being converted, the output
  filename is concatenated from this parameter and the IDS record number.
  That is, images with these names would be created if <I>iraf_file</I> = "<TT>ids</TT>":
  ids.1001, ids.1002, ids.1003, ..., ids.2001, ids.2002, ..., ids.3001 ....
  </DD>
  </DL>
  <DL>
  <DT><B>record_numbers = "<TT>1001-9999</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='record_numbers' Line='record_numbers = "1001-9999"'>
  <DD>A string listing the IDS records to be read.
  </DD>
  </DL>
  <DL>
  <DT><B>make_image = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='make_image' Line='make_image = yes'>
  <DD>This switch determines whether the IDS records are converted to IRAF images.
  When <I>make_image</I> = no, only a listing of the headers is produced, 
  no output image is written.
  </DD>
  </DL>
  <DL>
  <DT><B>print_pixels = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='print_pixels' Line='print_pixels = no'>
  <DD>When this parameter is set to yes, the values of the ids pixels are printed.
  </DD>
  </DL>
  <DL>
  <DT><B>long_header = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='long_header' Line='long_header = yes'>
  <DD>This parameter determines whether a long or short header is printed.  When
  <I>long_header</I> = no, a short header is printed.  The
  short header contains only the record number and ID string; the long header
  contains all information available 
  including the RA, Dec, HA, ST, UT, reduction flags, airmass, integration time,
  starting wavelength and wavelength per channel information.
  </DD>
  </DL>
  <DL>
  <DT><B>data_type = "<TT>r</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='data_type' Line='data_type = "r"'>
  <DD>The data type of the output IRAF image.  If an incorrect data_type or null
  string is entered, the default data type <I>real</I> is used.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  IDSOUT format IDS records are read from a text file and optionally
  converted to a sequence of one dimensional IRAF images.  The text file will
  most likely have been created by reading an IDSOUT tape with <B>rcardimage</B>.
  The IDS records to be read from the file can be specified.
  The IDS header information is printed in either a short or long 
  form.  The pixels values can be listed as well.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  [1] Convert all records in the IDSOUT file to IRAF images, with the root image 
  name being "<TT>aug83</TT>".  The IDSOUT file is the first file on the tape, which is 
  mounted on mtb.
  	
  	cl&gt; rcardimage mtb[1] | ridsout aug83
  <P>
  [2] List the headers from the same IDSOUT file read in example 1, but don't make
  output images.  A <B>long_header</B> will be listed; sample output is shown.
  <P>
  	cl&gt; rcardimage mtb[1] | ridsout make_image=no
  <P>
  <PRE>
  <P>
  RECORD = 2317, label = "CALLISTO  2297/2298  CLEAR/2.5ND",
  oflag = OBJECT, beam_number = 0,   alpha_ID = NEW,   companion = 2318,
  airmass = 1.524,        W0 = 3430.735,    WPC = 1.032,     ITM =  960,
  NP1 = 0, NP2 = 1024,    UT = 3:36:20.0,    ST = 15:36:43.0,
  HA = 1:39:48.5,         RA = 13:56:55.5,  DEC = -10:42:37.1,
  df = -1, sm = -1, qf = -1, dc = 0, qd = 0, ex = 0, bs = 1, ca = 0, co = -1
  </PRE>
  <P>
  [3] Print the pixel values for records 5086 and 5087.  No output image will
  be written, and only the short header listed.  Again, the IDSOUT file is the
  first file on the tape, which is mounted on mtb.
  <P>
  <PRE>
  	cl&gt; rcard mtb[1] | ridsout make- long- print+ rec = 5086,5087
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  The current version of IRAF magtape I/O does not read beyond the first
  volume of a multivolume tape.
  <BR>
  Task <B>ridsout</B> allows for converting more than one IDSOUT file per 
  execution.  In cases where a given record number occurs in more than one
  IDSOUT file being read and <I>make_image = yes</I>, this creates a problem, as
  the images being written will have the same name for the duplicate record 
  numbers ("<TT>iraf_name.record_number</TT>").  The action taken in this situation depends
  on the value of "<TT>noclobber</TT>"; the user should be aware of the potential
  problem.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  ridsfile, ridsmtn
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
