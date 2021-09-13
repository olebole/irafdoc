wtextimage — Convert an IRAF image to a text file
=================================================

**Package: dataio**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>wtextimage (Oct93)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>dataio</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>wtextimage (Oct93)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>wtextimage</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  wtextimage -- convert an IRAF image to a text file
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  wtextimage input output
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>An IRAF image file name or template of file names to be converted.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>Name or root_name of output text file.  If more than one IRAF image
  is being converted, the ordinal of the file in the input file list
  is appended to <I>output</I> to generate a unique output file name.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_header">header = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='header' Line='header = yes'>
  <DD>This parameter determines whether or not a descriptive header precedes
  the pixels written to the text file.  When <I>header = no</I>, only
  pixels values are converted; no header information is included in the
  output.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_pixels">pixels = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pixels' Line='pixels = yes'>
  <DD>This parameter determines whether or not to write the pixels to the
  text file.  This can be set to no to only write out the header.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_format">format = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='format' Line='format = ""'>
  <DD>Output format for each pixel.  If not set by the user, the appropriate output 
  pixel format is determined by the image data type.
  Acceptable formats are chosen from "<TT>W.D[defgz]</TT>" where w is the field width and 
  d specifies the precision.  Fortran formats of the form [iefgz]W.D are also
  acceptable.  If a field width of 0 is specified, (e.g., 0.6g),
  output will be free format with each output line containing as many pixels as
  will fit on the line.  This is the most space efficient format but requires
  that the reader program be able to handle free format (list directed) input.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_maxlinelen">maxlinelen = 80</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maxlinelen' Line='maxlinelen = 80'>
  <DD>The maximum number of characters output per line of text; <B>maxlinelen</B>
  must not exceed 322 characters.  (Note that tasks <I>rtextimage</I> and
  <I>wcardimage</I> cannot read lines of text greater than 161 characters.)
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  IRAF images are converted to text files with procedure <B>wtextimage</B>.
  The text file written consists of an optional header optionally followed by
  the pixel values.  The pixels are output in FITS order, that is, the
  leftmost subscript varies most rapidly.  The image header is written in the
  "<TT>keyword = value  / comment</TT>" format of FITS.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Write a text file from an image section of dev$pix.  The default maximum
  linelength of 80 is used; an output format is specified.  The header portion 
  of the output text is as follows:
  <DL>
  <DT><B><A NAME="l_"></A></B></DT>
  <! Sec='EXAMPLES' Level=0 Label='' Line=' '>
  <DD><PRE>
  BITPIX  =                    8  /  8-bit ASCII characters
  NAXIS   =                    2  /  Number of Image Dimensions
  NAXIS1  =                   10  /  Length of axis
  NAXIS2  =                   10  /  Length of axis
  ORIGIN  = 'NOAO-IRAF: WTEXTIMAGE'  /
  IRAF-MAX=               31431.  /  Max image pixel (out of date)
  IRAF-MIN=                  33.  /  Min image pixel (out of date)
  IRAF-B/P=                   16  /  Image bits per pixel
  IRAFTYPE= 'SHORT INTEGER     '  /  Image datatype                       
  OBJECT  = 'NGC 4147 B 1800   '  /                                       
  FILENAME= 'DEV$PIX[1:10,1:10]'  /  IRAF filename                  
  FORMAT  = '11I7              '  /  Text line format
  DATA-TYP= '    object (  0 )'   / object,dark,comp,etc.
  ITIME   =                 1800  / integration time secs
  UT      = '11:23:13'            / universal time
  ZD      = '24: 5: 0'            / zenith distance
  DATE-OBS= '15/02/1985'          / dd/mm/yy observation
  ST      = '13:38:31'            / sidereal time
  RA      = '12: 9:20'            / right ascension
  DEC     = '18:35:35'            / declination
  EPOCH   =                   .0  / epoch of RA and DEC
  CAM-TEMP=              -104.95  / camera temperature, deg C
  DEW-TEMP=              -192.96  / dewar temp, deg C
  HISTORY1= 'bt=   590 bp=     0 cr=     0 dk=     0 '
  HISTORY2= 'ff=    55 fg=     0 sc=   .000  bi=   51  '
  COMMENT = 'ngc 4147 b 1800'
  F1POS   =                    2  / filter bolt I position
  F2POS   =                    0  / filter bolt II position
  END     
  </PRE>
  </DD>
  </DL>
                                                                                  
  2. Write a series of text files from the IRAF images having root name
  "<TT>reduced</TT>".  One text file is written for each image. 
  <P>
      cl&gt; wtext reduced.* txt 
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_time_requirements">TIME REQUIREMENTS</A></H2>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  It takes almost 10 cpu minutes to convert a 512 square image of real pixels.
  A 512 square image of integer pixels takes about 3 cpu minutes.
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  wcardimage, rtextimage, noao.onedspec.wspectext
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>