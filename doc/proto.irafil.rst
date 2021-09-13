irafil — Create an IRAF image from a binary data file
=====================================================

**Package: proto**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>irafil (mar86)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>proto</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>irafil (mar86)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>irafil</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  irafil -- converts a binary file containing pixel values to an IRAF image
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  irafil input nrows ncols
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>the input file names to be converted
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nrows">nrows</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nrows' Line='nrows'>
  <DD>the number of rows of data in the image
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ncols">ncols</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ncols' Line='ncols'>
  <DD>the number of columns of data in the image
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_bits">bits = 16</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='bits' Line='bits = 16'>
  <DD>the number of data bits per pixel. This must be either 8 or 16
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_signed">signed = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='signed' Line='signed = yes'>
  <DD>the pixels are assumed to be signed integers if the bits parameter is 16,
  and unsigned if the bits parameter is 8. If signed is set to no, then
  the 16 bit pixels will be treated as unsigned integers and the resultant
  image will be of type long integers.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_tb_flip">tb_flip = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='tb_flip' Line='tb_flip = no'>
  <DD>This parameter allows the image to be "<TT>top-to-bottom</TT>" flipped during
  conversion.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_skip">skip = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='skip' Line='skip = 0'>
  <DD>the number of bytes to skip prior to reading pixel data. This allows
  skipping of header data which is otherwise not translatable and would
  be confused with the pixel data.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The specified files are read as integers and converted to IRAF images.
  The specified number of header bytes will be skipped, and the specified
  data format, 8 or 16 bit pixels, at the rate of ncols by nrows will be
  read. Signed data or 8 bit data will be placed into images having data
  type short. Unsigned 16 bit pixels will be converted into images of
  type long.
  <P>
  The resultant images will be assigned the same name as the input file,
  but with "<TT>.i</TT>" appended to indicate IRAF format.
  <P>
  The tb_flip parameter should be set to yes when converting the "<TT>snap</TT>"
  format files from the Compaq image display station, or other devices
  which refer to the first row as inverted from the usual IRAF notation.
  <P>
  This utility is capable of converting a large number of strange
  image formats to IRAF images. By skipping any initial header, and specifying
  a value for ncols equal to either the row length of the image, or the
  number of pixels used in the foreign internal format, almost any
  16-bit format can be read. For example, FORTH pictures can be read
  by skipping the initial 2048 bytes and reading the pixels assuming
  a row length of 1024, even if the actual row length is shorter. There
  will be garbage pixels at the end of each row which can be trimmed
  with IMCOPY using picture sections. An absurd example is to read an
  IRAF pixel file by skipping 1024 bytes and reading with a row length of
  1024 [at least for the 800 pixel image I tried].
  <P>
  Since no byte swapping is performed, a foreign tape format must be byte swapped
  if necessary prior to using IRAFIL. This may be done with REBLOCK in the
  dataio package.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Say you've deleted your header file to an IRAF image. The pixel file
  is pix3034x. Assuming the pixels are short integers, the image is
  10 rows by 800 columns:
  <P>
  <PRE>
  lo&gt; irafil pix3034x 10 1024 skip=1024
  lo&gt; imcopy pix3034x.i[1:800,*] phoenix
  </PRE>
  <P>
  The first line creates the IRAF image pix3034x.i which is readable
  by IRAF tasks, but has 1024 pixels per row. The real image only
  has 800 pixels per row, but we had to read it this way because of the
  way pixels are stored in IRAF images. So we IMCOPY the good part of
  the picture to the new IRAF image we call phoenix.
  <P>
  2. To read the "<TT>snap</TT>" format pictures from the Compaq station:
  <P>
  <PRE>
  lo&gt; irafil m82.snp 512 512 tb_flip+ bits=8
  </PRE>
  <P>
  This will create the IRAF image m82.snp.i which can then be run
  through CRTPICT to make a Dicomed hardcopy.
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_time_requirements">TIME REQUIREMENTS</A></H2>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  There is no way to explicitly specify the output image name.
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  binfil,imcopy,reblock
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>