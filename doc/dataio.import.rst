.. _import:

import — Convert some other format to an IRAF image
===================================================

**Package: dataio**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  import -- create an IRAF image from an arbitrary binary file
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  import binfiles images
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>binfiles</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='binfiles' Line='binfiles'>
  <DD>The list of input binary files to be read.
  </DD>
  </DL>
  <DL>
  <DT><B>images</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>The list of output IRAF images to be written. This parameter only needs to
  be specified when generating an output image (see the <I>output</I> parameter
  description).
  </DD>
  </DL>
  <DL>
  <DT><B>format = "<TT>sense</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='format' Line='format = "sense"'>
  <DD>The type of format to be processed. In default mode, i.e. <I>sense</I>,
  the format database is searched for a format identifier that evaluates 
  truly for the current binary file, the input file parameters are then
  derived from the database entry.  A specific format name in the database may
  alternatively be given in which case the input params are derived from that
  entry in the database.  If <I>format</I>=<I>none</I> the task parameters
  are used to describe the input file.
  </DD>
  </DL>
  <P>
  <CENTER>INPUT PARAMETERS
  
  </CENTER><BR>
  <DL>
  <DT><B>dims = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dims' Line='dims = ""'>
  <DD>The input file dimension string.  This is a space or comma delimited string
  containing the length of the file in each dimension, e.g. "<TT>512,512,3</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>pixtype = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pixtype' Line='pixtype = ""'>
  <DD>Input pixel type. This is a comma delimited string giving the type and size
  of each pixel, and an optional tag name to be used in the <I>outbands</I>
  expressions.  The syntax for the pixtype entry is
  <DL>
  <DT><B> &lt;type&gt;&lt;nbytes&gt;[:tag],&lt;type&gt;&lt;nbytes&gt;[:tag],[....]</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line=' &lt;type&gt;&lt;nbytes&gt;[:tag],&lt;type&gt;&lt;nbytes&gt;[:tag],[....]'>
  <DD><P>
  where
  <PRE>
      type = b            # byte (no conversions)
             u            # unsigned integer
             i            # signed integer
             r            # ieee floating point
             n            # native floating point
             x            # ignore (skip)
  <P>
      nbytes = 1, 2, 4, or 8
  <P>
      tag is something like <TT>'r'</TT>,<TT>'g'</TT>,<TT>'b'</TT> (color triplets), <TT>'r'</TT>,
  	<TT>'i'</TT> (complex data), etc.  If no tags are given one will 
  	automatically be assigned of the form 'b1', 'b2', etc.
  <P>
  </PRE>
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>interleave = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interleave' Line='interleave = 0'>
  <DD>Pixel interleave type. If the <I>pixtype</I> parameter is a composite then
  the input pixel are pixel-interleaved (i.e. each pixel in a band is stored
  together, as with RGB triplets) and this parameter is ignored. If 
  the <I>pixtype</I> is an atomic value and <I>interleave</I> is a positive 
  number the image is line interleaved (e.g. a line of <TT>'R'</TT>, followed by a 
  line of <TT>'G'</TT>, and so on).  If the <I>pixtype</I> is atomic and <I>interleave</I> 
  is zero, the no data interleaving is assumed and each band in the file 
  is stored sequentially.
  </DD>
  </DL>
  <DL>
  <DT><B>bswap = "<TT>no</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='bswap' Line='bswap = "no"'>
  <DD>Type of byte-swapping to perform.  By default no byte swapping is done, 
  if <I>bswap</I> is "<TT>yes</TT>" then all input values are byte swapped, if <I>bswap</I>
  is "<TT>i2</TT>" then only short integers are byte swapped, if <I>bswap</I> is "<TT>i4</TT>" then
  only long integers are swapped.  A combination of "<TT>i2,i4</TT>" can be used to
  swap only integer values, floating point numbers will not be swapped.
  </DD>
  </DL>
  <DL>
  <DT><B>hskip = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='hskip' Line='hskip = 0'>
  <DD>Number of bytes preceding pixel data to skip.
  </DD>
  </DL>
  <DL>
  <DT><B>tskip = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='tskip' Line='tskip = 0'>
  <DD>Number of bytes to skip at end of file.
  </DD>
  </DL>
  <DL>
  <DT><B>bskip = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='bskip' Line='bskip = 0'>
  <DD>Number of bytes between image bands to skip.
  </DD>
  </DL>
  <DL>
  <DT><B>lskip = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lskip' Line='lskip = 0'>
  <DD>Number of bytes to skip at font of each line.
  </DD>
  </DL>
  <DL>
  <DT><B>lpad = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lpad' Line='lpad = 0'>
  <DD>Number of bytes to skip at end of each line.
  </DD>
  </DL>
  <P>
  <CENTER>OUTPUT PARAMETERS
  
  </CENTER><BR>
  <DL>
  <DT><B>output = "<TT>image</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output = "image"'>
  <DD>Type of output to generate.  Possible values include "<TT>none</TT>" process the files
  but not generate an output image (e.g. to check the parameter values for
  correctness), "<TT>image</TT>" to generate an output image, "<TT>list</TT>" to generate a 
  pixel listing of the file as would be produced by the <I>LISTPIX</I> task
  on the image if were converted (no image is created with this option), 
  or "<TT>info</TT>" to print information about the file.  The <I>images</I> parameter
  is only used for <I>output</I>=image.
  </DD>
  </DL>
  <DL>
  <DT><B>outtype = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outtype' Line='outtype = ""'>
  <DD>The data type of the output image.  May be one of <TT>'s'</TT> for a short image, <TT>'i'</TT>
  for an integer image, <TT>'l'</TT> for a long image, <TT>'r'</TT> for a real image, and <TT>'d'</TT>
  for a double precision image.  If no <I>outtype</I> is specified then the
  datatype of the <I>outbands</I> expression is used.  This parameter is only 
  used when <I>output</I> is set to "<TT>image</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>outbands = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outbands' Line='outbands = ""'>
  <DD>Output image band expressions.  If no expressions are given then all of the
  input pixels will be converted.  The number of output bands may be more or
  less than the number of input bands.  See the <I>OUTBANDS EXPRESSIONS</I> 
  section for a more complete description of this parameter.
  </DD>
  </DL>
  <DL>
  <DT><B>imheader = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='imheader' Line='imheader = ""'>
  <DD>Image or header keyword data file.  If an image is given then the image header
  is copied.  If a file is given then the FITS format cards are copied.
  This only applies to new images.   The data file consists of lines
  in FITS format with leading whitespace ignored.  A FITS card must begin
  with an uppercase/numeric keyword.  Lines not beginning with a FITS
  keyword such as comments or lower case are ignored.  The user keyword
  output of <B>imheader</B> is an acceptable data file.  See <B>mkheader</B>
  for further information.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B>database = "<TT>imcnv$lib/images.dat</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='database' Line='database = "imcnv$lib/images.dat"'>
  <DD>The format database. This may also be a list of files to be searched (e.g.
  so that user-defined databases may be included), which will be treated as 
  a single database.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print verbose output during the conversion?
  </DD>
  </DL>
  <DL>
  <DT><B>buffer_size = 64</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='buffer_size' Line='buffer_size = 64'>
  <DD>Number of image lines <I>per band</I> to buffer in memory before writing to
  disk.  Image buffering can increase task performance by as much as a factor
  of 30 for some formats but requires more memory.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  	The <I>import</I> task is used to convert arbitrary raster binary
  files to IRAF format images.  The input format may be specified either
  through the task parameters (<I>format</I> set to 'none'), or as an entry 
  in a database of known formats (<I>format</I> set to the name of the entry).
  If the format of the image is not known a priori, the database can be
  searched and each record will be evaluated for an expression which
  identifies the format (<I>format</I> set to "<TT>sense</TT>").  The task will 
  output either an IRAF image, a list of pixel values
  in a manner similar to the <I>LISTPIX</I> task, or information about the
  file format if it is supported in the database. 
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Input file specification</H3>
  <! BeginSection: 'Input File Specification'>
  <UL>
  	The input raster is assumed to be at most three dimensional, with
  pixels of various sizes that can be interleaved in a variety of ways.
  No compression schemes are yet supported, except in the case of builtin
  formats where special code has been written to handle to format.
  Byte-swapping and floating point conversion of pixels (from IEEE to
  native) is also supported.
  <P>
  	The <I>pixtype</I> and <I>interleave</I> parameters define the pixel
  storage in the binary file.  <I>Pixtype</I> is a comma delimited string,
  the elements of which define the type and size of each pixel.  An optional
  'tag' name may be given to each pixel for use in the <I>outbands</I>
  expressions.  If no tag is given one will automatically be assigned.
  For composite pixtypes (i.e. when more than one element is listed), the
  data are assumed to be pixel interleaved (e.g. stored as { {RGB}, {RGB} ...}
  triplets).  For atomic (i.e. single) pixtypes, a positive value of
  <I>interleave</I> indicates that the data are stored in a line-interleaved
  manner (e.g. a line of R, a line of G, ...).  If <I>interleave</I> is
  zero and <I>pixtype</I> is atomic, then no interleaving is done and the 
  image bands are thought to be stored sequentially.  Minimal error
  checking is done to make sure the 
  combination of these parameters is correct.
  <P>
  	The file may contain arbitrary padding around the pixels as
  defined by the <I>tskip</I>, <I>bskip</I>, <I>lskip</I>, and <I>lpad</I>
  parameters, header information may be skipped by setting the <I>hskip</I>
  parameter.  Additionally, pixels may be ignored on input while still
  specifying the full format.
  </UL>
  <! EndSection:   'Input File Specification'>
  <H3>Output parameters</H3>
  <! BeginSection: 'Output Parameters'>
  <UL>
  	Once a format has been found, the task may output an IRAF image
  by setting <I>output</I> to "<TT>image</TT>", a list of the pixels in the file
  can be written to STDOUT by setting <I>output</I> to "<TT>list</TT>", or information
  about the input file can be printed by setting <I>output</I> to "<TT>info</TT>".
  If <I>output</I> is set to "<TT>none</TT>" then no output will be generated, this 
  can be used to check for read errors on the input file to verify task
  parameters.  The datatype of the output image can be set by specifying 
  the <I>outtype</I> parameter.  
  <P>
  	The <I>outbands</I> parameter is a list of expressions which are
  evaluated to compute the pixels in each band of the output image.  Operands
  in these expressions consist of numeric constants and the pixtype tags
  (either user-supplied tags or the automatic tags), general arithmetic
  expressions are supported, which can include any of the special functions
  listed below.  The simplest expression is the name of a tag itself.  
  Regardless of the storage of pixels in the input file, each image band is 
  separated on output unless an expression is given which combines them.
  See below for more details on <I>outbands</I>.
  <P>
  	Header information may be added to an output image by naming
  either a keyword file or an existing image header listing in the
  <I>imheader</I> parameter.  A header keyword data file consists of lines 
  of FITS format cards.  Leading whitespace is ignored.  Lines not recognized 
  as FITS cards are ignored.  A valid FITS card is defined as beginning with 
  a keyword of up to 8 uppercase, digit, hyphen, or underscore characters.  If
  less than 8 characters the remaining characters are blanks.  The
  ninth character may be an equal sign but must be immediately followed
  by a blank.  Such value cards should be in FITS format though no
  attempt is made to enforce this.  Any other ninth character is also
  acceptable and the line will be treated as a comment.  Note that this
  way of recognizing FITS parameters excludes the case of comments
  in which the first 8 characters are blank.  The reason for allowing
  leading whitespace and eliminating the blank keyword case is so that
  the long output of <B>imheader</B> may be used directly as input.
  <P>
  </UL>
  <! EndSection:   'Output Parameters'>
  <H3>Outbands expressions</H3>
  <! BeginSection: 'OUTBANDS EXPRESSIONS'>
  <UL>
  <P>
          The outbands parameter is a comma delimited list of expressions, the 
  simplest of which is the name of a tag itself (or the default names of the 
  tags if none are provided in the <I>pixtype</I> param).  
  The input pixels, regardless of how they are stored in the binary file,
  are always stored as separate bands in the output IRAF image.
  The outbands expressions will be evaluated to compute the pixels in each
  band of the output image.  This means that e.g. RGB triplets in an input
  file will be separated into different bands in the output image, unless a
  single expression is given that combines them.  The components named 
  in <I>pixtype</I> may be eliminated or re-ordered in <I>outbands</I> to 
  exclude certain input bands, or to change the channel order. For example 
  the commands:
  <P>
  <PRE>
  cl&gt; import file img pixtype="u1:a,u1:r,u1:g,u1:b" outbands="g,r,a"
  cl&gt; import file img pixtype="u1,u1,u1,u1" outbands="b3,b2,b1"
  </PRE>
  <P>
  both convert an input 32-bit image with ARGB components.  In the first case
  the output image is an IRAF image where the B component has been eliminated
  and the channel order reversed.  The second case is the same as the first but
  uses the automatic tag names.  A combination of user-supplied tags and
  defaults could also be used.
  <P>
  	General interpreted arithmetic expressions are supported and can 
  contain any of the standard expression evaluator functions (see 
  the <I>imexpr</I> help page for more details).  Special functions in 
  expressions also include:
  <PRE>
  <P>
       flipx (arg)      	- flip image in X
       flipy (arg)      	- flip image in Y
     gr[ea]y (r,g,b)    	- RGB to grayscale using the NTSC Y formula
         red (arg)	- get the red component of a colormap image
       green (arg)	- get the green component of a colormap image
        blue (arg)	- get the blue component of a colormap image
       gamma (arg, gamma) - apply a gamma correction to the image
  <P>
  </PRE>
  The two flip functions can change the image orientation by reversing the order
  of pixels within a line (a flipx() call), or it can flip an image from top-
  to-bottom (a flipy() call).  The flipping will apply to all bands of the out-
  put image even if it was only used in one expression.  To reverse the channel 
  order simply change the order of the tags in the outbands parameter.  RGB
  images may be converted to a single grayscale image using the NTSC formula:
  <PRE>
  <P>
  	gray = (0.289 * r) + (0.587 * G) + (0.114 * B)
  <P>
  </PRE>
  Note that a similar grayscale conversion can be done by explicitly defining
  a similar equation in <I>outbands</I> and supplying different coefficients.
  <P>
  	The <I>red()</I>, <I>green()</I>, or <I>blue()</I> functions can be used
  to get a single color component from a colormap image rather than the 
  grayscale equivalent of the colormap.  For example, to separate an 8-bit
  GIF color image into it's RGB components one could specify an outbands
  parameter such as
  <PRE>
  <P>
  cl&gt; import foo.gif bar format=gif outbands="red(b1),green(b1),blue(b1)"
  <P>
  </PRE>
  <P>
          Functions may also be nested in complex expressions such as:
  <P>
  <PRE>
   flipy (gray(r,g,b))           - convert to grayscale, flip in Y
   flipx (flipy (gray (r,g,b)))  - convert to grayscale, flip in X &amp; Y
    gray (r,g,255)               - use constant 255 as the B band
    gray (r,g+100,-b)            - add constant to G, negate B
  </PRE>
  <P>
  </UL>
  <! EndSection:   'OUTBANDS EXPRESSIONS'>
  <H3>Format database</H3>
  <! BeginSection: 'FORMAT DATABASE'>
  <UL>
  <P>
          The format database is a text file named as a task parameter.  
  Each record of a database entry is of the form:
  <P>
  <PRE>
          &lt;format_name&gt;:
          &lt;alias&gt;:
                  keyword = &lt;expr&gt;
                  keyword = &lt;expr&gt;
                     ...and so on
  </PRE>
  <P>
  A database record begins with the format name at the beginning of a line.
  Whitespace at the beginning of a line is considered the continuation of a
  previous line.  Comments may be inserted in the database using the normal <TT>'#'</TT>
  character, the remainder of the line is considered a comment.  Blank lines
  and comments are ignored, a record ends at the next line with a format name
  at the beginning of the line.  The task <I>database</I> parameter 
  defines the text files to be
  scanned as the database.  If the parameter is a list of files then each file
  in the list will be concatenated to a single database file used by the task.
  <P>
          The format_name field is a string identifying each entry in the
  database, any number of aliases may also be given to identify the same 
  format possibly known by another name. Supported keywords include:
  <P>
  <PRE>
      image_id     - A boolean expression identifying the image type
      id_string    - Verbose name of file format
      bswap        - is file byte-swapped? (See Below)
      dims         - a whitespace/comma delimited string of dimensions
      pixtype      - pixel type, size [and tag], may be a composite
      interleave   - describes how pixels are stored
      hskip        - # of bytes of header info to skip
      tskip        - # of bytes of trailing info to skip at end of file
      bskip        - # of bytes of info to skip between image bands
      lskip        - # of bytes of info to skip at front of each line
      lpad         - # of bytes of info to skip at end of each line
      error        - A condition that would cause a file read error, 
  		   returns a string with the error message, otherwise 
  		   returns the string "okay"
  </PRE>
  <P>
  The 'image_id' string is an expression to be evaluated which, if true,
  uniquely identifies the file format (such as a comparison to a "<TT>magic number</TT>").
  The 'id_string' is a verbose name of the format.  
  The 'error' keywords use the "<TT>? :</TT>" conditional syntax to
  define a boolean expression which, when true, returns an error message and is 
  used to indicate a condition in a format which isn't supported.  The remaining
  keywords have the same meaning as the task parameters.  Keywords not present 
  in the database record will take the default parameter value.
  <P>
          Expressions consist of any valid string that may be evaluated with the
  standard system expression evaluator evvexpr(). (See the documentation for this
  procedure or the <I>IMEXPR</I> task help page for details of builtin functions 
  and operators.)  Operators within expressions may be boolean, arithmetic,
  or the string operators '?=' (substring equality) and '//' (concatenation).
  Operands may be the special functions named below, previously defined
  keywords, constants (numeric or strings), and the special operands 
  <P>
  <DL>
  <DT><B>$FSIZE </B></DT>
  <! Sec='FORMAT DATABASE' Level=0 Label='' Line='$FSIZE '>
  <DD>The size of the binary file in bytes.   In expressions this operand has an
  integer datatype.  For formats with variable header sizes this can be used
  to determine the size of the header, since the size of the data can be 
  derived from the image dimensions and subtracted from the total size of the
  file.
  </DD>
  </DL>
  <DL>
  <DT><B>$FNAME</B></DT>
  <! Sec='FORMAT DATABASE' Level=0 Label='' Line='$FNAME'>
  <DD>The name of the binary file.  In expressions this operand has a character
  datatype.  As a last resort for images without any identifying features the
  file name may possibly be used to determine the format from a file name
  extension.
  </DD>
  </DL>
  <P>
  <P>
  </UL>
  <! EndSection:   'FORMAT DATABASE'>
  <H3>Special functions:</H3>
  <! BeginSection: 'Special Functions:'>
  <UL>
  <P>
          In addition to the intrinsic functions already provided there are a
  number of input and utility functions for the database.  These are:
  <PRE>
  <P>
                       <I>INPUT FUNCTIONS</I>
  <P>
     ctocc ([offset])      - convert byte to printable char constant
      ctod ([offset])      - convert string to double precision real
      ctoi ([offset])      - convert string to integer
      ctol ([offset])      - convert string to long
      ctor ([offset])      - convert string to single precision real
    ctowrd ([offset])      - get 1st white-space delimited word from str
  <P>
    getstr ([offset,] len) - get a string at offset
      getb ([offset])      - get a byte at offset
      getu ([offset])      - get an unsigned short int at offset
  geti[24] ([offset])      - get a signed int at offset
  getr[48] ([offset])      - get an IEEE fp number at offset
  getn[48] ([offset])      - get a native fp number at offset
  <P>
    locate ([offset,] pat) - find an offset to a pattern
      line (n)             - offset of line N
  <P>
                       <I>UTILITY FUNCTIONS</I>
  <P>
       skip (nbytes)       - move offset by N-bytes
      bswap (arg)          - byte swap the argument
     substr (str, c1, c2)  - extract a substring from argument
     stridx (test, str)    - get 1st occurrence of 'test' w/in 'str'
  <P>
  parameter (param)        - return the current task parameter
    default (param)        - return the default task parameter
   lsb_host ()		 - returns true if host is little-endian
   msb_host ()		 - returns true if host is big-endian
  </PRE>
  <P>
  <DL>
  <DT><B>ctocc ([offset])			[string]</B></DT>
  <! Sec='Special Functions:' Level=0 Label='ctocc' Line='ctocc ([offset])			[string]'>
  <DD>Convert byte at the given offset to printable char constant.
  If no offset argument is given the current offset is used.
  </DD>
  </DL>
  <DL>
  <DT><B>ctod ([offset])			[double]</B></DT>
  <! Sec='Special Functions:' Level=0 Label='ctod' Line='ctod ([offset])			[double]'>
  <DD>Convert string to double precision real.
  The function reads a string from
  the file and converts it up to the first unrecognized character.
  If no offset argument is given the current offset is used.
  </DD>
  </DL>
  <DL>
  <DT><B>ctoi ([offset])			[int]</B></DT>
  <! Sec='Special Functions:' Level=0 Label='ctoi' Line='ctoi ([offset])			[int]'>
  <DD>Convert string to integer.
  The function reads a string from
  the file and converts it up to the first unrecognized character.
  If no offset argument is given the current offset is used.
  </DD>
  </DL>
  <DL>
  <DT><B>ctol ([offset])			[long]</B></DT>
  <! Sec='Special Functions:' Level=0 Label='ctol' Line='ctol ([offset])			[long]'>
  <DD>Convert string to long.
  The function reads a string from
  the file and converts it up to the first unrecognized character.
  If no offset argument is given the current offset is used.
  </DD>
  </DL>
  <DL>
  <DT><B>ctor ([offset])			[real]</B></DT>
  <! Sec='Special Functions:' Level=0 Label='ctor' Line='ctor ([offset])			[real]'>
  <DD>Convert string to single precision real.  
  The function reads a string from
  the file and converts it up to the first unrecognized character.
  If no offset argument is given the current offset is used.
  </DD>
  </DL>
  <DL>
  <DT><B>ctowrd ([offset])			[string]</B></DT>
  <! Sec='Special Functions:' Level=0 Label='ctowrd' Line='ctowrd ([offset])			[string]'>
  <DD>Get 1st white-space delimited word from str, leading whitespace is skipped.
  If no offset argument is given the current offset is used.
  </DD>
  </DL>
  <DL>
  <DT><B>getstr ([offset,] len)		[string]</B></DT>
  <! Sec='Special Functions:' Level=0 Label='getstr' Line='getstr ([offset,] len)		[string]'>
  <DD>Get a string at offset.
  If no offset argument is given the current offset is used, the length of
  the string must be specified.
  </DD>
  </DL>
  <DL>
  <DT><B>getb ([offset])			[int]</B></DT>
  <! Sec='Special Functions:' Level=0 Label='getb' Line='getb ([offset])			[int]'>
  <DD>Get a byte at offset.
  If no offset argument is given the current offset is used.
  </DD>
  </DL>
  <DL>
  <DT><B>getu ([offset])			[int]</B></DT>
  <! Sec='Special Functions:' Level=0 Label='getu' Line='getu ([offset])			[int]'>
  <DD>Get an unsigned short integer at offset.
  If no offset argument is given the current offset is used.
  </DD>
  </DL>
  <DL>
  <DT><B>geti[24] ([offset])			[int]</B></DT>
  <! Sec='Special Functions:' Level=0 Label='geti' Line='geti[24] ([offset])			[int]'>
  <DD>Get a signed int at offset.
  If no offset argument is given the current offset is used.
  Long integers values can be read by specifying the function as geti4(),
  the names geti() and geti2() return short integers.
  </DD>
  </DL>
  <DL>
  <DT><B>getr[48] ([offset])			[real/double]</B></DT>
  <! Sec='Special Functions:' Level=0 Label='getr' Line='getr[48] ([offset])			[real/double]'>
  <DD>Get an IEEE floating point number at an optional offset.
  If no offset argument is given the current offset is used.
  Double precision values can be read by specifying the function as getr8(),
  the names getr() and getr4() return single precision real.
  </DD>
  </DL>
  <DL>
  <DT><B>getn[48] ([offset])			[real/double]</B></DT>
  <! Sec='Special Functions:' Level=0 Label='getn' Line='getn[48] ([offset])			[real/double]'>
  <DD>Get a native floating point number at an optional offset.
  If no offset argument is given the current offset is used.
  Double precision values can be read by specifying the function as getn8(),
  the names getn() and getn4() return single precision real.
  </DD>
  </DL>
  <DL>
  <DT><B>locate ([offset,] pat)		[int]</B></DT>
  <! Sec='Special Functions:' Level=0 Label='locate' Line='locate ([offset,] pat)		[int]'>
  <DD>Compute an offset.
  If no offset argument is given the current offset is used.
  </DD>
  </DL>
  <DL>
  <DT><B>line (N)				[int]</B></DT>
  <! Sec='Special Functions:' Level=0 Label='line' Line='line (N)				[int]'>
  <DD>Offset of line N in bytes.  The database is rewound and the offset of the
  requested line number is returned, line are delimited by the '\n' character.
  </DD>
  </DL>
  <DL>
  <DT><B>skip (nbytes)			[int]</B></DT>
  <! Sec='Special Functions:' Level=0 Label='skip' Line='skip (nbytes)			[int]'>
  <DD>Move current offset by N-bytes. The number of bytes skipped is returned as
  the function value.
  </DD>
  </DL>
  <DL>
  <DT><B>bswap (arg)				[type of arg]</B></DT>
  <! Sec='Special Functions:' Level=0 Label='bswap' Line='bswap (arg)				[type of arg]'>
  <DD>Byte swap the argument.
  </DD>
  </DL>
  <DL>
  <DT><B>substr (str, first, last)		[string]</B></DT>
  <! Sec='Special Functions:' Level=0 Label='substr' Line='substr (str, first, last)		[string]'>
  <DD>Extracts a substring from string <I>str</I>.  The  first  character  in
  the string is at index 1.
  </DD>
  </DL>
  <DL>
  <DT><B>stridx (test, str)			[int]</B></DT>
  <! Sec='Special Functions:' Level=0 Label='stridx' Line='stridx (test, str)			[int]'>
  <DD>Finds the position of the first occurrence of any character found
  in <I>test</I> in the string <I>str</I>, returning 0 if the match fails.
  </DD>
  </DL>
  <DL>
  <DT><B>parameter (param)			[param type]</B></DT>
  <! Sec='Special Functions:' Level=0 Label='parameter' Line='parameter (param)			[param type]'>
  <DD>Return the current task parameter. The parameter is specified as a string
  containing the name of a task parameter, the type of the returned value is
  the parameter type 
  </DD>
  </DL>
  <DL>
  <DT><B>default (param)			[param type]</B></DT>
  <! Sec='Special Functions:' Level=0 Label='default' Line='default (param)			[param type]'>
  <DD>Return the default task parameter.  The parameter is specified as a string
  containing the name of a task parameter, the type of the returned value is
  the parameter type 
  </DD>
  </DL>
  <DL>
  <DT><B>lsb_host ()				[bool]</B></DT>
  <! Sec='Special Functions:' Level=0 Label='lsb_host' Line='lsb_host ()				[bool]'>
  <DD>Returns true if host is little-endian.
  This function can be used as the <I>bswap</I> keyword expression for formats
  with a specified byte order.
  </DD>
  </DL>
  <DL>
  <DT><B>msb_host ()				[bool]</B></DT>
  <! Sec='Special Functions:' Level=0 Label='msb_host' Line='msb_host ()				[bool]'>
  <DD>Returns true if host is big-endian.
  This function can be used as the <I>bswap</I> keyword expression for formats
  with a specified byte order.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'Special Functions:'>
  <H3>Byte swapping</H3>
  <! BeginSection: 'BYTE SWAPPING'>
  <UL>
  <P>
  	The 'bswap' database entry is similar to the task parameter,  it may
  be used to set byte swapping for the whole file, or for only certain data
  types.  The value is a string parameter that may be "<TT>yes</TT>" to byteswap the
  whole file, "<TT>no</TT>" to not swap anything, or a comma delimited string of types
  described below to enable swapping for only those values.
  <PRE>
  <P>
          bswap = { no | yes | i2 i4 }
  <P>
                  no              # no swapping (default)
                  yes             # byte swap whole file
                  i2              # byte swap short ints only
                  i4              # byte swap long ints only
  </PRE>
  <P>
  	The <I>bswap</I> task parameter applies only to the pixel data,
  but the bswap keyword in a database record sets byte-swapping 
  for the header information:  arguments to the input and conversion functions
  will be byteswapped prior to being evaluated by the function.  The bswap()
  special function can be used to negate byteswapping for a particular 
  argument if it is or is not set by the keyword (the default is no byte 
  swapping).
  <P>
  </UL>
  <! EndSection:   'BYTE SWAPPING'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <PRE>
  <P>
  Get a list of known input formats:
  <P>
      cl&gt; import "" "" output=info
  <P>
  Get a list of known input formats, including those defined by the user:
  <P>
      cl&gt; import "" "" output=info database="dev$images.dat,mydb.dat"
  <P>
  Get a list of the file formats of each image in the directory:
  <P>
      cl&gt; import file* "" format="sense" output=info verbose-
      file1.ras               Sun rasterfile
      file1.eps               unknown format
      file1.pgm               8-bit PGM file
          :                           :
  <P>
  Get a list of the file formats of each image in the directory and
  print out some information about each file:
  <P>
      cl&gt; import file* "" format="sense" output=info verbose+
      file1.ras:         Sun Rasterfile
                         Resolution:       320 x 200
                         Pixel type:       8-bit unsigned integer
                         Pixel storage:    non-interleaved
                         Header length:    137 bytes
                         Byte swapped:     no
       ...                    :
  <P>
  Read a raw 8-bit file of pixels into an unsigned short IRAF image:
  <P>
      cl&gt; import file img format="none" dims="512,512" pixtype="b1" \<BR>
      &gt;&gt;&gt;     outtype="u" outbands="b1"
  <P>
  Read a JPL VICAR image or 8-bit Sun rasterfile:
  <P>
      cl&gt; import file img format="vicar"
      cl&gt; import file img format="sunras"
  <P>
  Concatenate three separate red, blue, and green images and convert
     to a single grayscale image:
  <P>
      cl&gt; concat pic.[rgb] &gt; rgb
      cl&gt; import rgb img format=none dims="640,480,3" \<BR>
      &gt;&gt;&gt;    pixtype="u1" interleave=0 outbands="gray(b1,b2,b3)"
  <P>
  Read an 8-bit colormap GIF image and separate the RGB colors into 
     separate bands in the output image:
  <P>
      cl&gt; import file.gif img outbands="red(b1),green(b1),blue(b1)"
  <P>
  Read three 8-bit rasterfiles with 200 byte-headers as if they were
      a single image, and combine the images to a single output band:
  <P>
      cl&gt; concat pix.* &gt; rfiles
      cl&gt; import rfiles img dims="512,512,3" pixtype="b1" \<BR>
      &gt;&gt;&gt; hskip=200 bskip=200 interleave=0 outbands="gray(b1,b2,b3)"
  <P>
  Read a FITS image with one header record in which the data bytes
     are incorrectly swapped, but the header info is in the right order:
  <P>
      cl&gt; rfits nite1.fits "" nite1
         File: nite1  1866-A                Size = 640x480
      cl&gt; imheader nite1 l+ &gt; imheader.dat    # Save the header info
      cl&gt; imdel nite1.imh
      cl&gt; import nite1.fits nite1 format="none" dims="640,480" \<BR>
      &gt;&gt;&gt; bswap+ hskip=2880 pixtype="i2" outtype="s" imheader="imheader.dat"
  <P>
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  Bitmap images are not yet supported.  Their most logical use would be as
  pixel masks but there hasn't been much call for these formats so they may
  be implemented at a later time.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>IMPORT V2.11</B></DT>
  <! Sec='REVISIONS' Level=0 Label='IMPORT' Line='IMPORT V2.11'>
  <DD>This is a new task in this version.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  export. imexpr, hedit, default image database imcnv$lib/images.dat
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'Input File Specification' 'Output Parameters' 'OUTBANDS EXPRESSIONS' 'FORMAT DATABASE' 'Special Functions:' 'BYTE SWAPPING' 'EXAMPLES' 'BUGS' 'REVISIONS' 'SEE ALSO'  >
  
