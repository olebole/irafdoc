.. _rtextimage:

rtextimage — Convert text files to IRAF images
==============================================

**Package: dataio**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  rtextimage -- convert a text file to an IRAF image
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  rtextimage input output
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>A list of text files containing image pixels and optional header.  Most likely
  the output from <I>rcardimage</I>, see examples below.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>The output IRAF image name.  If more than one text file is being
  read, the ordinal of the text file in <B>input</B> 
  is appended to <I>output</I> to generate a unique image name.
  </DD>
  </DL>
  <DL>
  <DT><B>otype = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='otype' Line='otype = ""'>
  <DD>The data type of the output IRAF image pixels.  If left unset and the IRAFTYPE
  keyword is found in the FITS header, output pixels will be of type IRAFTYPE.
  If IRAFTYPE appears more than once in the FITS header, the last value of 
  IRAFTYPE is used.  If left unset and the IRAFTYPE keyword is not provided in
  the FITS header, the output data type is determined from the pixels themselves.
  </DD>
  </DL>
  <DL>
  <DT><B>header = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='header' Line='header = yes'>
  <DD>If <B>header</B> = yes, <I>rtextimage</I> will attempt to read a FITS
  header at the beginning of each text file.  
  </DD>
  </DL>
  <DL>
  <DT><B>pixels = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pixels' Line='pixels = yes'>
  <DD>Read the pixel values from the input text file.  If no then the
  output image is initialized to zero pixel values.
  </DD>
  </DL>
  <DL>
  <DT><B>nskip = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nskip' Line='nskip = 0'>
  <DD>The number of lines to skip before reading pixels.  This is used to
  skip over a non-standard header and is important only when <B>header</B> = no.  
  </DD>
  </DL>
  <DL>
  <DT><B>dim = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dim' Line='dim = ""'>
  <DD>A string listing the dimension of each axis.  The number of dimensions listed
  equals the number of image dimensions.  This information must be entered unless
  it can be read from a FITS header.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Text files are converted to IRAF images files with procedure
  <B>rtextimage</B>.  The text file consists of an optional header optionally
  followed by the pixel values.  If no pixel values are read the image is
  initialized to all zero pixel values.  If pixel values a given they are
  read in FITS order, that is, the leftmost subscript varies most rapidly.
  The number of image dimensions and the length of each dimension must either
  be read from a FITS header or supplied by the user.  Internally,
  <B>rtextimage</B> determines the format (integer or floating point) of the
  pixels in the text file by reading the first one and assuming all others
  are the same.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Read a file written by <I>wtextimage</I> from the magtape file "<TT>mta[1]</TT>" into
  the IRAF image "<TT>picture</TT>".
  <P>
      cl&gt;  rcard mta[1] | rtext out=picture
  <P>
  2. Read a series of text files with no headers preceding the pixels.  The 
  text files were previously read from tape with task <B>rcardimage</B>. 
  The two dimensional images are 512 by 320 pixels, and will be named 
  crab001, crab002, crab003, etc.
  <P>
      cl&gt; rtext text.* crab header- dim=512,320
  <P>
  <P>
  3. Read a file with a non-standard header.  The header is 5 cardimages long.
  <P>
      cl&gt; rcard mta[5] | rtext out=spect.1 head- nskip=5 dim=1024
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  Task <I>rtextimage</I> requires about 145 cpu seconds to write a 512 square
  image (integer or real) from a text file.  
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  The text file being read cannot have lines longer than SZ_LINE characters
  (see hlib$iraf.h).
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  rcardimage, wtextimage
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
