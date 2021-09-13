export — Convert IRAF images to some other format
=================================================

**Package: dataio**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>export (Oct94)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>dataio</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>export (Oct94)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>export</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  export -- create a binary image file from one or more IRAF images
  <P>
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  export images binfiles
  <P>
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <P>
  <DL>
  <DT><B><A NAME="l_images">images</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>The list of input IRAF images to be converted.  The list may contain
  either 2-D images  or 3-D images.
  Any number of 2-D images may be combined to a single output file, only
  one 3-D image (or section) at a time may be converted.  See the <I>Builtin 
  Formats</I> section for notes about the number of image expressions required 
  for each builtin format and the handling of 3-D image data.  Images greater
  than three dimensions should be converted using image sections.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_binfiles">binfiles</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='binfiles' Line='binfiles'>
  <DD>The list of output binary files to create.  If any of the builtin formats
  is selected for conversion the filename will have an extension added
  reflecting the format (if it is not already given).
  </DD>
  </DL>
  <P>
  <CENTER>OUTPUT PARAMETERS
  
  </CENTER><BR>
  <DL>
  <DT><B><A NAME="l_format">format = "<TT>raw</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='format' Line='format = "raw"'>
  <DD>The type of binary file to write.  If the value is "<TT>raw</TT>" then the input
  images are converted directly to a raw binary raster using the task 
  parameters.  If the value is "<TT>list</TT>" the pixel values will be written
  to the standard output after evaluation of the <I>outbands</I> parameter in
  the same format as would appear from the <I>LISTPIX</I> task.  Finally,
  the value may include any of the currently supported specific builtin formats:
  <P>
  <PRE>
  	eps		- Encapsulated PostScript
  	gif		- Compuserve's GIF format
  	imh		- IRAF OIF image
  	miff		- ImageMagick MIFF format image
  	pgm		- PBMPlus PGM format image
  	ppm		- PBMPlus PPM format image
  	ras		- Sun rasterfile format
  	rgb		- SGI RGB format image
  	xwd		- X11 Window dump file
  </PRE>
  <P>
  If any of these builtin formats is selected one or more of the following 
  parameters may be ignored. See the <I>Builtin Formats</I> section for notes 
  about the formats supported by this task.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_outbands">outbands = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outbands' Line='outbands = ""'>
  <DD>Output image band expressions to write.  This is a comma-delimited list of 
  expressions or an @-file containing the expressions.  Evaluated expressions 
  do not all need to be the same length since the output image will be padded
  to the maximum size.  See below for more information.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = no                    </A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no                    '>
  <DD>Print verbose output to the screen during conversion?
  </DD>
  </DL>
  <P>
  <CENTER>RAW BINARY OUTPUT PARAMETERS
  
  </CENTER><BR>
  <DL>
  <DT><B><A NAME="l_header">header = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='header' Line='header = yes'>
  <DD>For raw binary file output only, prepend a header describing how the data 
  are stored?  If set to "<TT>no</TT>" then no header will be written.  If set to "<TT>yes</TT>", 
  a standard text header describing how the data were written will be 
  prepended to the output file.  Setting the <I>header</I> parameter to the 
  reserved string "<TT>long</TT>" will write the image headers from the IRAF images
  making up the output file in the standard header.  The parameter may also
  be set to a filename that will be prepended to the output file.  This
  parameter is ignored for builtin format output. See below for a description 
  of the header layout.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_outtype">outtype = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outtype' Line='outtype = ""'>
  <DD>Output pixel type if <I>format</I> is set to "<TT>raw</TT>" or "<TT>list</TT>".  This is a 
  string giving the type and size of each pixel, the syntax for the outtype 
  entry is
  <PRE>
  <P>
  		&lt;type&gt;[&lt;nbytes&gt;]
  where
      type = b            # byte
             u            # unsigned (short) integer
             i            # signed integer
             r            # ieee floating point
             n            # native floating point
  <P>
      nbytes = 1, 2, 4, or 8
  <P>
  </PRE>
  If no value for <I>nbytes</I> is given the smallest size for the given type
  (i.e. 1 byte for <TT>'b'</TT>, 2 bytes for ints, 4 bytes for floating point) will
  be used.  If no value is entered at all the type of the input image is used, 
  for multiple images used to create a single binary file the type of the first 
  image is used.  This parameter is ignored for builtin format output options.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interleave">interleave = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interleave' Line='interleave = 0'>
  <DD>Pixel interleave type.  If the <I>outbands</I> parameter is composite 
  (i.e. a comma-delimited list of expressions) the output file is pixel 
  interleaved and the <I>interleave</I> parameter is ignored.  If the 
  <I>outbands</I> parameter is a single expression the file is line-interleaved 
  when the <I>interleave</I> value is a positive integer.  If the <I>outbands</I> 
  is an empty string or a single expression the binary file is band interleaved 
  if this parameter is zero.  This parameter is ignored for builtin formats 
  where the pixel storage is predefined.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_bswap">bswap = "<TT>no</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='bswap' Line='bswap = "no"'>
  <DD>Type of byte-swapping to perform on output. The default is bswap=no which
  may be abbreviated "<TT>bswap-</TT>" (similarly a value of 'yes' can be abbreviated
  "<TT>bswap+</TT>").  If disabled no byte-swapping is performed, if set all integers
  are swapped on output relative to the current machine's byte ordering.
  Values of 'i2' or 'i4' will swap only two or four byte integers respectively,
  floating point values remain unswapped.  This parameter may be used by some
  builtin formats that don't have a specified byte order.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  	The <I>export</I> task will convert one or more images in an
  input list to a binary raster file, a text listing of pixels values,
  or one of several specific file formats.  For general binary
  rasters, various pixel types, data interleaving, and the byte order can be
  specified.  An optional header may be added to the output file.
  Arbitrary arithmetic expressions, using both standard and custom
  functions, may be applied to the images in the
  input list before conversion allowing the user to scale intensity values,
  change image orientation, compute colormaps, or compute output pixel
  values.
  <P>
  	The <I>format</I> parameter controls the type of output generated:
  if set to <I>raw</I> a binary file described by the <I>outtype</I>, 
  <I>interleave</I>, and <I>bswap</I> parameters is written with pixel values
  determined from the expressions in the 
  <I>outbands</I> parameter.  The value of <I>outtype</I>
  defines the output pixel size and type (long or short ints, native or IEEE
  reals, see parameter description for details).  The
  <I>bswap</I> parameter can be used to set the byte order (relative to the
  current machine) of integer values, this 
  parameter is ignored for floating point pixels or builtin
  formats with a specified byte order. The <I>outbands</I> and <I>interleave</I> 
  parameters define the pixel storage in the binary file.  For multiple 
  <I>outbands</I>
  expressions the data are assumed to be pixel interleaved (e.g. written 
  as { {RGB}, {RGB} ...} triplets).  For single expressions, a positive value 
  of <I>interleave</I> indicates that the data are written in a line-interleaved
  manner (e.g. a line of R, a line of G, ...).  If <I>interleave</I> is
  zero and <I>outbands</I> is a single expression 
  then no interleaving is done and the image bands are written sequentially.  
  If <I>outbands</I> is the null string, all pixels in a single input image 
  will be written to a single output file.
  Error checking is done to make sure the combination of these 
  parameters is correct.  If the <I>header</I> parameter is "<TT>yes</TT>" a text header
  describing how the data were written will be prepended to the file, setting
  the <I>header</I> parameter to the reserved string "<TT>long</TT>"
  will cause the image header for each input image
  to be saved in the standard header.  The <I>header</I> parameter may also 
  be the name of a user-defined file to prepend to the output instead of the
  standard header.
  <P>
  	If the <I>format</I> parameter is set to "<TT>list</TT>" the pixels values 
  will be written to the screen as an ascii list of pixel coordinates 
  followed by the pixel value.   Pixel coordinates are determined using the
  same interleaving scheme as above, values are determined by evaluating
  each <I>outbands</I> expression.
  <P>
  	Lastly, the <I>format</I> parameter may be any of the currently
  supported builtin formats.  See the section on <I>Builtin Formats</I> for
  more information and the restrictions or requirements of each format.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_more_on_outbands_expressions">MORE ON OUTBANDS EXPRESSIONS</A></H2>
  <! BeginSection: 'MORE ON OUTBANDS EXPRESSIONS'>
  <UL>
  	The simplest specification for <I>outbands</I> is a null string, 
  in which case the image is converted directly (i.e. band storage, 
  pixels converted to output type).  Arbitrary interpreted arithmetic 
  expressions using standard and custom functions and operators are also 
  supported.  If the <I>images</I> parameter is a list of 3-D images the 
  operand names are the predefined tags b1, b2, ... bN for the bands in each 
  image, the <I>binfiles</I> parameter must contain an equal number of 
  output files.  To convert multiple 3-D images they must either be sliced 
  to individual 2-D images (or specified as image sections) or stacked into 
  a single image.  If the <I>images</I> parameter is a list of 2-D images 
  (or sections) the operand names are the predefined tags i1, i2, ... iN for 
  the each image in the input list, the b1, b2, etc names are also recognized.
  For more complex or 
  lengthy expressions the <I>outbands</I> parameter may alternatively be an
  @-file containing the expressions.  Within this @-file whitespace and
  newline characters are ignored to allow expressions to be indented in a 
  readable manner.
  <P>
  	The image operands determine which input images in the list are
  converted to which output files.  For 3-D input images one IRAF image is
  converted for each output file in the list, for 2-D images multiple images
  may be converted to a single output file.  In the latter case the list 
  pointers are updated automatically to keep track of the images.  For example,
  to convert six images to two output files, the <I>outbands</I> expression
  should contain three images operands.  The first three images in the list
  will be used in evaluating the expressions for the first output file,
  the last three for the second file.
  <P>
  	The image tags may be reordered in the expression but still refer to 
  e.g. band-1, band-2 and so on.  For example (where rgbim is a 512x512x3 image, 
  and rim, gim, and bim are 512x512 images),
  <P>
  <PRE>
  cl&gt; export rgbim file outtype="u2" header-                       (1)
  cl&gt; export rgbim file outtype="u2" header- outbands="b3,b2,b1"   (2)
  cl&gt; export rim,gim,bim file outty="u2" outbands="i3,i2,i1"       (3)
  cl&gt; export rim,gim,bim file outty="b" outbands="gray(i1,i2,i3)"  (4)
  </PRE>
  <P>
  Example (1) converts the input image pixels to a raw binary file of 
  unsigned short integers with no header written as one image band following 
  another.  In example (2) the order of the bands is reversed and the binary 
  file is stored as pixel interleaved BGR triplets of short ints.  
  Example (3) is the same as (2) except that the input images in the list 
  are reordered instead of bands within a single image. When using the image 
  tags the input list is updated to account for this, so it is allowed to have 
  more input images than output binary files.
  In example (4) the three images are converted to a single grayscale image
  before being written as byte data to the binary file.
  More complex and detailed examples are given below.
  <P>
  Individual <I>outbands</I> expressions are composed of operators and operands
  in general interpreted arithmetic expressions as follows:
  <P>
  <B>Operands</B>
  <PRE>
  <P>
  	iN		      	    # image list item
  	iN.param		    # image parameter
  	@"param"	    	    # parameter of 3-D image
  	bN		      	    # band within 3-D image
  <P>
  	func()		      	    # function
  	constant	      	    # numeric constant
  </PRE>
  <P>
      The 'iN.param' and '@"<TT>param</TT>"' syntax allows an image header parameter 
  to be accessed.  For example 'i2.otime' refers to the 'otime' image 
  header parameter in the second image of a list and '@"<TT>otime</TT>"' refers to the 
  current image if the input list contains 3-D images.  They may
  be used in an outbands expression such as
  <PRE>
  <P>
      (i1*(i1.otime/i2.otime)),i2,(i3*(i3.otime/i2.otime))	(1)
      (b1/@"otime")),(b2/@"otime"),(b3/@"otime")			(2)
  <P>
  </PRE>
  to normalize the output bands by the exposure time value in the second image
  in the first example, or to normalize by the 'otime' keyword of a 3-D image
  in the second example.
  <P>
      In cases where a constant value is used as an outbands expression an 
  alpha channel (an extra 8-bits of constant intensity) will be created 
  consisting of that value.  For example, writing a 32-bit RGB image with an 
  alpha channel of 255 could be written using
  <P>
      cl&gt; export rgbim file outtype="<TT>b1</TT>" outbands="<TT>b1,b2,b3,255</TT>"
  <P>
  <P>
  <B>Operators</B>
  <P>
  The expression syntax implemented by <I>export</I> provides the following
  set of operators:
  <P>
  <PRE>
  <P>
          ( expr )              	    - grouping
          + - * /               	    - arithmetic
          **                    	    - exponentiation
          //                    	    - concatenate
          expr ? expr1 : expr2  	    - conditional expression
      
          &amp;&amp;                    	    - logical and
          ||                    	    - logical or
          !                     	    - logical not
          &lt;                     	    - less than
          &lt;=                    	    - less than or equal
          &gt;                     	    - greater than
          &gt;=                    	    - greater than or equal
          ==                    	    - equals
          !=                    	    - not equals
  	?=                          - substring equals
  </PRE>
  <P>
  The conditional expression has the value <I>expr1</I> if <I>expr</I> is true,
  and <I>expr2</I> otherwise.  Since the expression is evaluated at every pixel
  this permits pixel-dependent operations such as checking for special pixel
  values, or selection of elements from either of two vectors.  For example,
  the command
  <P>
          	(i1 &lt;= 0) ? 0 : 1
  <P>
  has the constant value zero if "<TT>i1</TT>" is less than or equal to zero, 
  and one otherwise, effectively creating a pixel mask of positive pixels.
  Conditional expressions are general expressions and may be nested or used
  anywhere an expression is permitted.
  <P>
  The concatenation operator applies to all types of data, not just
  strings.  Concatenating two vectors results in a vector the 
  combined length of the two input vectors.  An example use of this would
  be to concatenate images side-by-side on output.
  <P>
  <P>
  <B>Special Functions</B>
  <P>
  	In addition to the intrinsic functions already provided (see the help
  page for the <I>imexpr</I> task for a list of standard, mathematical and type
  conversion functions) there are a number of custom functions for this task:
  <P>
  <CENTER><B>Output Functions:</B>
  
  </CENTER><BR>
  <P>
  <PRE>
         band (args)     	    	  - force band interleaved storage
         line (args)         	  - force line interleaved storage
        flipx (args)   	     	  - flip image in X dimension
        flipy (args)   	     	  - flip image in Y dimension
  <P>
        block (val,width,height)	  - block fill area with a constant
  </PRE>
  <P>
      These functions define how the output data are written. For builtin 
  formats whose normal orientation and storage format is known these functions 
  are ignored (except where noted).  These functions may not be used as arguments to other functions (except where noted) or as single operands
  within expressions (e.g. "<TT>255 + flipx(i1)</TT>"), however their arguments may
  be expressions or (perhaps output) functions themselves.
  <P>
  <DL>
  <DT><B><A NAME="l_band">band (args)</A></B></DT>
  <! Sec='MORE ON OUTBANDS EXPRESSIONS' Level=0 Label='band' Line='band (args)'>
  <DD>Force band storage in the output file regardless of the value of the
  <I>interleave</I> parameter.  This may be used to specify multiple
  expressions for each band while still forcing band storage (the default
  for multiple expressions is pixel-interleaved storage).  This function
  may be used with some builtin formats to write multiple images to the output
  file as if they were a column of images in the original. This function
  is ignored by builtin formats that do not support this scheme (i.e RGB
  format) and may be used as an argument to the <I>setcmap()</I>, <I>psdpi()</I>,
  and <I>psscale()</I> functions only.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_line">line (args)</A></B></DT>
  <! Sec='MORE ON OUTBANDS EXPRESSIONS' Level=0 Label='line' Line='line (args)'>
  <DD>Force line storage in the output file regardless of the value of the
  <I>interleave</I> parameter.  This may be used to specify multiple
  expressions for each band while still forcing line storage (the default
  for multiple expressions is pixel-interleaved storage).  This function
  is ignored by builtin formats that do not support this scheme.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_flipx">flipx (args)</A></B></DT>
  <! Sec='MORE ON OUTBANDS EXPRESSIONS' Level=0 Label='flipx' Line='flipx (args)'>
  <DD>Flip the image left-to-right on output.  This function may be used as an
  argument to the <I>band()</I>, <I>setcmap()</I>, <I>psdpi()</I>, or 
  <I>psscale()</I> functions only.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_flipy">flipy (args)</A></B></DT>
  <! Sec='MORE ON OUTBANDS EXPRESSIONS' Level=0 Label='flipy' Line='flipy (args)'>
  <DD>Flip the image top-to-bottom on output.  Certain builtin formats (such as
  GIF, PGM, PPM, RAS and XWD) have their normal orientation already flipped wrt 
  to IRAF and these will automatically be flipped on output.  Using this
  function with those formats cancels the flip action, writing the image in the
  normal IRAF orientation and not the normal format orientation.
  This function may be used as an argument to the <I>band()</I>, <I>setcmap()</I>,
  <I>psdpi()</I>, or <I>psscale()</I> functions only.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_block">block (value, width, height)</A></B></DT>
  <! Sec='MORE ON OUTBANDS EXPRESSIONS' Level=0 Label='block' Line='block (value, width, height)'>
  <DD>Fill an area with a constant value.  This function can be used to fill a
  vertical area between images to provide padding of a constant value.  It
  is similar to the "<TT>repl()</TT>" intrinsic function which replicates a data element
  a given number of times.
  </DD>
  </DL>
  <P>
  <P>
  <CENTER><B>Scaling Functions:</B>
  
  </CENTER><BR>
  <PRE>
  <P>
     zscale (arg [,z1, z2 [, nbins]]) - scale to a fixed number of bins
                 zscalem (arg1, arg2) - automatic scaling with filtering
             gr[ea]y (arg1,arg2,arg3) - RGB to grayscale conversion
            bscale (arg, zero, scale) - linearly transform intensity scale
         gamma (arg, gamma [, scale]) - apply a gamma correction
  </PRE>
  <P>
          These functions may be used to scale the intensity values of the
  image before output in order to map image datatypes to a specified range.
  The 'args' value may be a list of image operands or expressions.  These 
  functions may be used as arguments to the output functions above
  or as operands within more complex expressions.
  <P>
  <DL>
  <DT><B><A NAME="l_zscale">zscale (arg [,z1,z2 [,nbins]])</A></B></DT>
  <! Sec='MORE ON OUTBANDS EXPRESSIONS' Level=0 Label='zscale' Line='zscale (arg [,z1,z2 [,nbins]])'>
  <DD>Scale the pixels in a given range to a specified number of bins.  This
  function will map the input pixels within the range z1 to z2 to one of 
  'nbins' values.  Pixels less than z1 are mapped to the lowest output
  intensity value, pixels greater than z2 are mapped to the highest value.
  If no <I>z1</I> and <I>z2</I> arguments are given appropriate values will
  be computed using the same algorithm and default parameters used by 
  the <I>DISPLAY</I> task (see the help page for more information).
  If no <I>nbins</I> value is given 256 bins are assumed.
  <P>
  If the given value of z1 is greater than z2 the mappings will be inverted,
  i.e. larger pixel values will map to the lower bin numbers, smaller pixel
  values will map to larger bin numbers.  For example, to map the dev$pix
  test image to 200 colors such that there are "<TT>black</TT>" stars on a "<TT>white</TT>"
  background one could use
  <PRE>
  <P>
  	zscale (b1, @"i_maxpixval", @"i_minpixval", 200)
  </PRE>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_zscalem">zscalem (arg1, arg2)</A></B></DT>
  <! Sec='MORE ON OUTBANDS EXPRESSIONS' Level=0 Label='zscalem' Line='zscalem (arg1, arg2)'>
  <DD>This is a variant of the zscale operand with automatic scale calculation;
  i.e.  zscale (arg).  The first argument is the same as for zscale to select
  the pixel values.  The second argument is a boolean (true or false)
  expression selecting whether a value in the first argument is to be used in
  the calculation.  This allows limiting the automatic scale calculation to
  pixels specified in a mask or to a certain range to exclude extreme or bad
  values that would otherwise perturb the result.  Typical usages might be
  <PRE>
  <P>
  	zscalem (i1, i2==0)
  	zscalem (i1, i1&gt;0&amp;&amp;i1&lt;10000)
  </PRE>
  where i1 are the image pixels and i2 would be pixels from the second
  input argument which defines a mask.  Note that you can't just say i2
  for a mask but must use it in an expression resulting in a true or false
  value.  Also note that the result is always in the range 0 to 255.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_grey">grey (arg1,arg2,arg3) or gray (arg1,arg2,arg3)</A></B></DT>
  <! Sec='MORE ON OUTBANDS EXPRESSIONS' Level=0 Label='grey' Line='grey (arg1,arg2,arg3) or gray (arg1,arg2,arg3)'>
  <DD>Convert three image operands or expressions to a single grayscale image
  using the standard NTSC equation:
  <PRE>
  <P>
  	Gray = 0.3 * arg1 + 0.59 * arg2 + 0.11 * arg3
  </PRE>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_bscale">bscale (arg, zero, scale)</A></B></DT>
  <! Sec='MORE ON OUTBANDS EXPRESSIONS' Level=0 Label='bscale' Line='bscale (arg, zero, scale)'>
  <DD>Linearly transform the intensity scale of the image using the equation
  <PRE>
  <P>
  	new[i] = (arg[i] - zero) / scale
  <P>
  </PRE>
  Pixels are scaled in their input datatype prior to converting to the output
  datatype.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_gamma">gamma (arg, gamma [, scale])</A></B></DT>
  <! Sec='MORE ON OUTBANDS EXPRESSIONS' Level=0 Label='gamma' Line='gamma (arg, gamma [, scale])'>
  <DD>Apply a gamma correction to the pixels.  Pixel values are scaled according to
  the equation
  <PRE>
  <P>
  	new = scale * [ (old/scale) ** (1.0/gamma) ]
  <P>
  </PRE>
  If no scale argument is given a value of 255 will be assumed.
  </DD>
  </DL>
  <P>
  <P>
      <I>Additional functions</I> are supported for specific formats:
  <P>
  <PRE>
        Function	           Description		    Formats
        --------	           -----------		    -------
      cmap (r,g,b [,ncols])  create 8-bit colormap    GIF,RAS,XWD,EPS
   setcmap (args, [opts])    define a colormap        GIF,RAS,XWD,EPS
     psdpi (args, dpi)       set dpi for output	    EPS
   psscale (args, scale)     set scale of output	    EPS
  </PRE>
  <P>
  	These functions may take as arguments some of the output functions
  named above.  For example, one can specify the dpi resolution of EPS output
  and band storage of images using something like
  <PRE>
  <P>
  	psdpi(band(args), dpi)
  <P>
  </PRE>
  <P>
  <DL>
  <DT><B><A NAME="l_cmap">cmap (arg1,arg2,arg3 [, ncolors])</A></B></DT>
  <! Sec='MORE ON OUTBANDS EXPRESSIONS' Level=0 Label='cmap' Line='cmap (arg1,arg2,arg3 [, ncolors])'>
  <DD>Compute an 8-bit colormap from three image operands or expressions using a
  Median-Cut Algorithm and Floyd-Steinberg dithering.  The computed colormap
  is written to the header of the output file.  The resultant image 
  is an 8-bit color index into the computed colormap.  The <I>ncolors</I> argument
  specifies the number of desired colors, a default value of 256 will be used
  if not provided.  This function is only
  allowed for builtin formats supporting color lookup tables and may not be
  used within another expression or function.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_setcmap">setcmap (args, cmap [, brightness, contrast]) </A></B></DT>
  <! Sec='MORE ON OUTBANDS EXPRESSIONS' Level=0 Label='setcmap' Line='setcmap (args, cmap [, brightness, contrast]) '>
  <DD>Define the colormap to be used on output.  This function is only supported
  for formats that support colormaps, the <I>args</I> expressions are used to
  compute the color index values.  The <I>cmap</I> argument may either be the
  filename of a normalized colormap table (such as is used by <I>XImtool</I>)
  or one of the builtin values:
  <PRE>
  	aips0		- and RGB false color mapping
  	blue		- various shades of blue
  	color		- standard B/W and RGB colormap
  	grayscale	- standard grayscale
  	greyscale	- (alias for above)
  	green		- various shades of green
  	halley		- standard halley mission colormap
  	heat		- temperatures as colors
  	rainbow		- rainbow colors
  	red		- various shades of red
  	staircase	- RGB staircase
  	standard	- RGB ramps
  	overlay		- grayscale with IMDKERN overlay colors
  </PRE>
  <P>
  Colormap names must be quoted with either single or double quote characters.
  The optional <I>brightness</I> and <I>contrast</I> arguments have default 
  values of 0.5 and 1.0 respectively corresponding to the default 
  brightness/contrast scaling of the <I>XImtool</I> display server.  
  If the cmap argument is an empty string the default Grayscale LUT will 
  be used, IRAF logical paths may be used in the filename specification. 
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_psdpi">psdpi (args, dpi)</A></B></DT>
  <! Sec='MORE ON OUTBANDS EXPRESSIONS' Level=0 Label='psdpi' Line='psdpi (args, dpi)'>
  <DD>Specify the dots-per-inch resolution of the output image.  The default 
  resolution is 300dpi, this may need to be reset for some printers or if
  the raster rendering produces "<TT>bands</TT>" in the output.  This function may
  only be used as an argument to the <I>psscale()</I> function.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_psscale">psscale (args, scale)</A></B></DT>
  <! Sec='MORE ON OUTBANDS EXPRESSIONS' Level=0 Label='psscale' Line='psscale (args, scale)'>
  <DD>Specify the scale of the output image.  The default value is 1.0 which 
  means that image printed on a 300dpi device is roughly the same size 
  as displayed on a typical 72dpi screen.  Scale values less than one reduce
  the image size on the page, values greater than one increase the size.  The
  scale value will automatically be adjusted if it creates an image that will
  not fit on a 8.5 inch by 11 inch page.  A scale value of 0.25 prints one
  image pixel per 300dpi printer pixel.  This function may
  only be used as an argument to the <I>psdpi()</I> function.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'MORE ON OUTBANDS EXPRESSIONS'>
  <H2><A NAME="s_export_header_format">EXPORT HEADER FORMAT</A></H2>
  <! BeginSection: 'EXPORT HEADER FORMAT'>
  <UL>
  	The header prepended to the binary data is ascii text consisting of
  keyword-value pairs, one per line, terminated with a newline after the
  value, beginning with the magic string 
  "<TT>format = EXPORT</TT>".  Using an ascii header allows the file format to be
  easily determined by the user with a file pager or any program reading 
  the file.
  <P>
  Defined keywords are:
  <P>
  <PRE>
  	date		    - date file was written (dd/mm/yy)
  	hdrsize		    - size of header (bytes)
  	ncols		    - no. of image columns
  	nrows		    - no. of image rows
  	nbands		    - no. of image bands
  	datatype	    - pixel type (as &lt;type&gt;&lt;nbytes&gt;)
  	outbands	    - outband expression list
  	interleave	    - interleave value (same as above)
  	bswap		    - are ints swapped relative to MII format?
  	image1 		    - image names used in creating file
  	  :
  	imageN	
  	header1 <TT>'{'</TT> &lt;header&gt; <TT>'}'</TT>  - image headers of above
  	  :
  	headerN	<TT>'{'</TT> &lt;header&gt; <TT>'}'</TT>
  	end		    - terminate header
  </PRE>
  <P>
  If the <I>header</I> parameter is set to "<TT>long</TT>" the image headers for 
  each image used in creating the file is included in the output header, 
  otherwise only the image names are included.
  <P>
  A sample (verbose) header might look like:
  <P>
  <PRE>
      format = EXPORT
      date = '19/06/94'
      hdrsize = 2084
      nrows = 512
      ncols = 512
      nbands = 1
      datatype = 'i2'
      outbands = ''
      interleave = 0
      bswap = no
      image1 = "dev$pix"
      header1 = {
      IRAF-BPX=                   16  /  DATA BITS/PIXEL
      IRAFTYPE= 'SHORT   '            /  PIXEL TYPE
      CCDPICNO=                   53  /  ORIGINAL CCD PICTURE NUM
      ITIME   =                  600  /  INTEGRATION TIME (SECS)
      	:   :		:			:
      }
      end
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXPORT HEADER FORMAT'>
  <H2><A NAME="s_builtin_formats">BUILTIN FORMATS</A></H2>
  <! BeginSection: 'BUILTIN FORMATS'>
  <UL>
  	While the task provides a way of writing general binary raster
  files there is still a need for converting to specific formats.  
  Implementing most formats is trivial since they usually follow the
  data model and the only "<TT>builtin</TT>" knowledge of the format is the minimal
  header required.  More complex formats such as GIF and EPS are implemented 
  as special cases.  Note that all of the builtin formats require 8-bit color
  index or 8-bits per color in RGB or RGBA files, users should be careful
  in how the datatype conversion from IRAF image types is handled. In most
  cases this can be handled with the <I>zscale()</I> or <I>zscalem</I> functions.
  <P>
  	For each of the formats listed below the table shows the number
  of <I>outbands</I> expressions required and the type of output file that
  can be written.  Complete examples for the most common cases are shown in
  the <I>Examples</I> section below.  The columns in the table are defined as
  <PRE>
  <P>
      #expr		- number of required <I>outbands</I> expressions
      Type		- RGB or 8-bit colormap (index) file
      bitpix		- number of bits-per-pixel
      CLT?		- does the file have a colormap?
      Alpha?		- does the file have an alpha channel?
      Interleaving	- type of pixel interleaving
      Notes		- see explanation below each table
  <P>
  </PRE>
  A general description and specific restrictions or requirements are given for 
  each format.  An error is generated of the input parameters do not meet the 
  requirements of the requested format.  Unless otherwise noted the values of 
  the <I>header</I>, <I>bswap</I> and <I>interleave</I> parameters will be ignored.
  The value of <I>outtype</I> will be set internally and is also ignored.
  <P>
  	If the input image is 3-D and no <I>outbands</I> expressions are
  given, then where supported each band will be written to the output file as 
  a complete image or RGB color component.  For example, a 512x512x3 image 
  will be written as a 512x1536 image with each band comprising one third 
  the height of the output image.  If the output format requires 24-bit pixels 
  then each band of the image will be written as a color component.
  <P>
  	The currently supported builtin formats include:
  <P>
  <DL>
  <DT><B><A NAME="l_EPS">EPS     - Encapsulated PostScript</A></B></DT>
  <! Sec='BUILTIN FORMATS' Level=0 Label='EPS' Line='EPS     - Encapsulated PostScript'>
  <DD><PRE>
  <P>
    #expr    Type   bitpix  CLT?  Alpha?  Interleaving  Notes
    -----    -----  ------  ----  ------  ------------  -----
      1      index  8       no    no      none          
  <P>
  </PRE>
  	The output 8-bit Encapsulated PostScript image
  centered on the page at a default scale of 1.0 at 300dpi (i.e. the image will
  appear on a 300dpi printer about the same size as displayed on a 72dpi 
  screen).  The output scale may be adjusted using 
  the <I>psscale()</I> function, e.g. to set the output for one image pixel
  per 300 dpi printer pixel use "<TT>psscale(b1,0.25)</TT>" (one quarter the normal size
  on the page).  The output dpi resolution may be set explicitly with 
  the <I>psdpi()</I> function, this is sometimes necessary if "<TT>bands</TT>" appear 
  in the final output image.  Color EPS files may be written as either RGB
  postscript or with a colormap applied to the data (using either the
  <I>cmap()</I> or <I>setcmap()</I> functions).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_GIF">GIF     - Compuserve's GIF format</A></B></DT>
  <! Sec='BUILTIN FORMATS' Level=0 Label='GIF' Line='GIF     - Compuserve's GIF format'>
  <DD><PRE>
  <P>
    #expr    Type   bitpix  CLT?  Alpha?  Interleaving  Notes
    -----    -----  ------  ----  ------  ------------  -----
      1      index  8       yes   no      none          1
      3      index  8       yes   no      none          2
  <P>
      Notes:
  	1) Colormap generation enabled using <I>setcmap()</I> or else
             default grayscale colormap will be used
  	2) use of <I>cmap()</I> required to generate colormap
  <P>
  </PRE>
  	The output file is a GIF '87 image.  A linear colormap of 256 entries 
  will automatically be generated if only one image or expression is given for
  conversion and no colormap is specified.  
  If three images or expressions are specified a 24-to-8 bit
  conversion can be done using a Median Cut Algorithm and Floyd-Steinberg
  dithering with the required <I>cmap()</I> function.  Since the colormap 
  sizes are limited to 256 entries the maximum pixel value is assumed to 
  be 255, i.e. the output pixel size will be forced to 8-bits or less.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_IMH">IMH     - IRAF image file</A></B></DT>
  <! Sec='BUILTIN FORMATS' Level=0 Label='IMH' Line='IMH     - IRAF image file'>
  <DD>	The output file is an IRAF OIF format image of the specified datatype.
  Writing the image out as another IRAF image may be used to scale or composite
  several images into a new image that can be annotated with the <I>TVMARK</I>
  task before writing out the final format.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_MIFF">MIFF    - ImageMagick MIFF format image</A></B></DT>
  <! Sec='BUILTIN FORMATS' Level=0 Label='MIFF' Line='MIFF    - ImageMagick MIFF format image'>
  <DD><PRE>
  <P>
    #expr    Type   bitpix  CLT?  Alpha?  Interleaving  Notes
    -----    -----  ------  ----  ------  ------------  -----
      1      index  8       no    no      none
      1      index  8       yes   no      none          1,2
      3      rgb    24      no    no      pixel         
  <P>
      Notes:
  	1) Colormap generation enabled using <I>setcmap()</I>
  	2) Colormap generation enabled using <I>cmap()</I>
  <P>
  </PRE>
  	The output file is a Machine Independent File Format image, with or
  without a colormap or as a 24-bit RGB image.  Although MIFF permits 64K
  colors in a colormap the task only supports 256 colors, no compression is
  used in the image.  The maximum pixel value per color is assumed to be 255.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_PGM">PGM     - PBMPlus PGM format image</A></B></DT>
  <! Sec='BUILTIN FORMATS' Level=0 Label='PGM' Line='PGM     - PBMPlus PGM format image'>
  <DD><PRE>
  <P>
    #expr    Type   bitpix  CLT?  Alpha?  Interleaving  Notes
    -----    -----  ------  ----  ------  ------------  -----
      1      index  8       no    no      none
      3      index  8       no    no      none          1
  <P>
      Notes:
  	1) Grayscale may be produce with <I>gray()</I> function
  <P>
  </PRE>
  	The output file is an 8-bit raw (i.e. binary pixels) PGM image.  
  The maximum pixel value is assumed to be 255.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_PPM">PPM     - PBMPlus PPM format image</A></B></DT>
  <! Sec='BUILTIN FORMATS' Level=0 Label='PPM' Line='PPM     - PBMPlus PPM format image'>
  <DD><PRE>
  <P>
    #expr    Type   bitpix  CLT?  Alpha?  Interleaving  Notes
    -----    -----  ------  ----  ------  ------------  -----
      3      rgb    24      no    no      pixel         
  <P>
  </PRE>
  	The output file is an 24-bit raw (i.e. binary pixels) PPM image. 
  The maximum pixel value per color is assumed to be 255.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_RAS">RAS     - Sun rasterfile format</A></B></DT>
  <! Sec='BUILTIN FORMATS' Level=0 Label='RAS' Line='RAS     - Sun rasterfile format'>
  <DD><PRE>
  <P>
    #expr    Type   bitpix  CLT?  Alpha?  Interleaving  Notes
    -----    -----  ------  ----  ------  ------------  -----
      1      index  8       no    no      none
      1      index  8       yes   no      none          1,2
      3      rgb    24      no    no      pixel
      4      rgb    32      no    yes     pixel
  <P>
      Notes:
  	1) Colormap generation enabled using <I>setcmap()</I>
  	2) Colormap generation enabled using <I>cmap()</I>
  <P>
  </PRE>
  	The output file will be a Sun rasterfile.  The header values
  (long integers) may be byte swapped by setting the <I>bswap</I> parameter 
  to "<TT>yes</TT>" or "<TT>i4</TT>".  For 32-bit true-color rasterfiles the
  alpha channel should be specified as the first expression.  The maximum 
  pixel value is assumed to be 255.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_RGB">RGB     - SGI RGB format image</A></B></DT>
  <! Sec='BUILTIN FORMATS' Level=0 Label='RGB' Line='RGB     - SGI RGB format image'>
  <DD><PRE>
  <P>
    #expr    Type   bitpix  CLT?  Alpha?  Interleaving  Notes
    -----    -----  ------  ----  ------  ------------  -----
      1      index  8       no    no      none          
      3      rgb    24      no    no      scanline      
  <P>
  </PRE>
  	The output file will be an SGI RGB (IRIS) format image.  Although
  this format supports colormaps they are not supported by this task.
  The maximum pixel value is assumed to be 255.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_XWD">XWD     - X11 Window dump file</A></B></DT>
  <! Sec='BUILTIN FORMATS' Level=0 Label='XWD' Line='XWD     - X11 Window dump file'>
  <DD><PRE>
  <P>
    #expr    Type   bitpix  CLT?  Alpha?  Interleaving  Notes
    -----    -----  ------  ----  ------  ------------  -----
      1      index  8       yes   no      none          1,2,3
      3      rgb    24      no    no      none          
  <P>
      Notes:
  	1) Linear grayscale colormap automatically generated
  	2) Colormap generation enabled using <I>setcmap()</I>
  	3) Colormap generation enabled using <I>cmap()</I>
  <P>
  </PRE>
  	The output file will be an X11 window dump file.
  A linear colormap of 256 entries will automatically be generated if only 
  one image or expression is given for conversion, the <I>setcmap()</I> function
  may be used to create an alternate colormap.  If three images or expressions 
  are specified a 24-to-8 bit conversion can be done using a Median Cut 
  Algorithm and Floyd-Steinberg dithering if the <I>cmap()</I> function is 
  specified.  Header values (long integers) may be byte swapped by setting the
  task <I>bswap</I> parameter to "<TT>yes</TT>" or "<TT>i4</TT>".  The maximum pixel value is 
  assumed to be 255.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'BUILTIN FORMATS'>
  <H2><A NAME="s_color_output_images">COLOR OUTPUT IMAGES</A></H2>
  <! BeginSection: 'COLOR OUTPUT IMAGES'>
  <UL>
  	In theory the colormaps generated by the <I>cmap()</I> and
  <I>setcmap()</I> functions could be written in the header for raw binary
  output and the pixel written out as color indices, but since we also
  support color index formats which are recognized widely by other packages 
  there is no need to do this.  Therefore we limit the use of colormaps to 
  the builtin formats which already support it.
  <P>
  	The simplest type of "<TT>color</TT>" image is the familiar grayscale image.
  Pixel values represent the display gray level, although for some formats a CLT 
  (color lookup table) is required (e.g. GIF) and these pixel values are 
  actually indices into a grayscale colormap.  Most of the conversion done
  with this task will produce a grayscale image of some sort.  For "<TT>color 
  index</TT>" images the pixel values are indices into a colormap containing the 
  RGB components of the color for a pixel with that value.  Colormaps 
  usually permit at most 256 possible colors implying 8-bit pixels.
  In this task the colormap may be computed either with the <I>cmap()</I> (which 
  does a 24-to-8 bit mapping of the colors) or the <I>setcmap()</I> function 
  (which computes the colormap from a display lookup table of colors).  
  "<TT>True color</TT>" images are those which have 24-bits of color (8-bit for each
  component) for each pixel, some true color images also contain an alpha 
  channel (an extra 8-bits of constant intensity) which may or may not be 
  used by the software displaying the image.
  <P>
  	The <I>cmap()</I> function takes three images and computes a colormap
  using Paul Heckbert's Median Cut Algorithm ("<TT>Color Image Quantization for
  Frame Buffer Display</TT>", SIGGRAPH '82 Proceedings, pg 297) and Floyd-Steinberg 
  dithering technique.  The computed colormap is written to the file header 
  and pixel values are converted to color indices.  By default 256 colors are 
  computed but fewer colors may be requested.  This function is most useful 
  for generating pseudo-color images from three input images taken in different
  filter bands (which is required for some formats like GIF that do not 
  support 24-bit RGB).
  	
  	The <I>setcmap()</I> function, on the other hand, can be used to
  generate a color image from a single input image and a lookup table such as
  the ones used by displays servers like XImtool.  In this case the pixel
  values are indices into a pre-defined colormap which is normalized between
  zero and one (so that it may be scaled to the desired number of colors).
  The <I>brightness</I> argument defines the center of the transfer function, the
  default is 0.5 because it in the middle of the normalized range.  The 
  <I>contrast</I> arguments sets the contrast of the transfer function.  For
  example, the normalized pixel values and default brightness/contrast settings
  will map the pixel values to the corresponding color in the LUT.  Changing
  the brightness to a lower value means that pixel intensities will map to lower
  values in the LUT, doubling the contrast for instance means that the LUT 
  will increment two colors for every unit pixel change.  This is what happens
  when changing a displayed image in IRAF with the mouse by moving the cursor
  left-right (changing the brightness) or up-down (changing the contrast).
  <P>
  	An example use of this function would be if one wanted to convert an 
  IRAF image to a color rasterfile with the same colormap and intensity 
  scaling as was displayed in XImtool.  After adjusting the display the 
  brightness/contrast values could be read from the control panel and the 
  rasterfile generated using
  <PRE>
  <P>
          setcmap (b1, "aips0", 0.36, 1.2)
  <P>
  </PRE>
  where the "<TT>aips0</TT>" is one of the builtin colormaps and the brightness and
  contrast arguments are those from the ximtool display.  Similarly, the
  expression
  <PRE>
  <P>
          setcmap (zscale(i1),"idl15.lut")
  <P>
  </PRE>
  will save the image with the same intensity scaling and color as would be see
  by displaying it to ximtool using the default DISPLAY task settings,
  normalized XImtool brightness/contrast values and the "<TT>idl15.lut</TT>" LUT in the
  current directory.
  <P>
  <P>
  </UL>
  <! EndSection:   'COLOR OUTPUT IMAGES'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  	The examples below are divided into several categories showing
  typical usage when creating various raw and builtin output files.  Note
  that the output file will have a filename extension added indicating the 
  format when converting to a builtin format.
  <P>
  <I>Creating Raw Binary Files</I>
  <PRE>
  <P>
  List the pixels being one the standard output, apply a linear scale
  function first:
  <P>
      cl&gt; export dev$pix "" list outbands="bscale(b1,1.0,3.2)"
  <P>
  Convert the dev$pix test image to an 8-bit binary file with a gamma 
  correction, write the standard header:
  <P>
      cl&gt; export dev$pix bfil raw header+ outty="u1" outbands="gamma(b1,1.8)"
  <P>
  Write the three bands of an IRAF image to a pixel interleaved binary 
  file of short integers, prepend a user-defined header:
  <P>
      cl&gt; export rgbim bfil raw header="hdr.txt" outty="i2" outban="b1,b2,b3"
  <P>
  Convert three images representing RGB to a 4-color line-interleaved
  file, the IRAF images don't require scaling, create alpha channel:
  <P>
      cl&gt; export rim,gim,bim bfil raw outty="u1" outban="line(i1,i2,i3,0)"
  <P>
  Write the three bands of an IRAF image to a line-interleaved binary 
  file of short integers:
  <P>
      cl&gt; export rgbim binfil raw outtype="i2" outbands="line(b1,b2,b3)"
      cl&gt; export rgbim binfil raw outtype="i2" outbands="" interleave=3
  <P>
  Write the three bands of an IRAF image to a grayscale binary file using 
  a custom conversion formula.  Pixel values are truncated to 8-bits:
  <P>
      cl&gt; export rgbim grey raw outty="u1" outban="(.2*b1)+(.5*b2)+(.3*b3)"
  <P>
  </PRE>
  <P>
  <I>Creating Specific Formats</I>
  <PRE>
  <P>
  Convert dev$pix to an 8-bit Sun rasterfile with no colormap, scale the 
  image to 8-bits using the default <I>zscale()</I> intensity mapping:
  <P>
      cl&gt; export dev$pix dpix ras outbands="zscale(i1)"
  <P>
  Apply various functions to the data before doing the same conversion:
  <P>
      cl&gt; export dev$pix dpix ras outbands="zscale(log(i1))"
      cl&gt; export dev$pix dpix ras outbands="zscale(sqrt(i1))"
  <P>
  Convert dev$pix to an 8-bit Sun rasterfile with no colormap, image pixel
  values are truncated to 8-bits:
  <P>
      cl&gt; export dev$pix dpix ras
  <P>
  Convert three images representing RGB to a 24-bit Sun rasterfile, assume
  the IRAF images don't require intensity scaling:
  <P>
      cl&gt; export rim,gim,bim rgb ras outbands="i1,i2,i3"
  <P>
  Create a Silicon Graphics RGB format image from a 3-D image:
  <P>
    cl&gt; export rgbim bdata rgb outbands="b1,b2,b3"
  <P>
  Convert dev$pix to an 8-bit GIF grayscale image, scale the image to map 
  only pixel values between 0 and 320:
  <P>
    cl&gt; export dev$pix dpix gif outbands="zscale(i1,0.0,320.0)"
  <P>
  Combine three images representing RGB into an 8-bit X11 window dump
  grayscale image:
  <P>
    cl&gt; export rim,gim,bim gray xwd outbands="gray(i1,i2,i3)"
  <P>
  Convert dev$pix to an Encapsulated PostScript file at half the normal scale 
  and apply a linear transformation to scale the pixel values:
  <P>
      cl&gt; export dev$pix dpix eps \<BR>
      &gt;&gt;&gt;    outbands="psscale(bscale(i1,0.,0.32), 0.5)"
  <P>
  Convert three images representing RGB to an 8-bit GIF color image with
  a computed colormap:
  <P>
    cl&gt; export rim,gim,bim rgb gif outbands="cmap(i1,i2,i3)"
  <P>
  Convert dev$pix to a color rasterfile using the builtin "heat" colormap
  and default intensity mapping:
  <P>
    cl&gt; export dev$pix dpix ras outban='setcmap(zscale(i1),"heat")'
  <P>
  Convert dev$pix to a color rasterfile using the XImtool "idl15.lut" 
  LUT file in the current directory and default intensity mapping:
  <P>
    cl&gt; copy /usr/local/lib/imtoolcmap/idl15.lut .
    cl&gt; export dev$pix dpix ras outbands="setcmap(zscale(i1),'idl15.lut')"
  <P>
  <P>
  <I>Advanced Usage</I>
  <P>
  Given a set of DISPLAY task z1/z2 values of 10 and 320 respectively, and
  brightness/contrast values from XImtool of 0.6 and 1.2 respectively, 
  convert an image to an EPS file with the same appearance:
  <P>
    im&gt; type expr
    setcmap ( zscale (i1, 10.0, 320.0), "greyscale", 0.6, 1.2 )
    im&gt; export dev$pix dpix eps outbands="@expr"
  <P>
  Concatenate two images side-by-side to a PGM file, normalize each image 
  by it's exposure time and apply a default intensity mapping:
  <P>
    cl&gt; export im1,im2 two pgm \<BR>
    &gt;&gt;&gt;     outbands='(zscale(i1/i1.otime)) // (zscale(i2/i2.otime))'
  <P>
  Convert dev$pix to a color GIF using the XImtool "idl15" LUT with a spec-
  ified brightness/contrast scale.  Map only pixel values between 5 and 300 
  to 201 output intensity values.  This should produce and image identical 
  to what one would get by displaying dev$pix to imtool, setting the same 
  brightness/contrast scale, and selecting the idl15 LUT:
  <P>
    cl&gt; copy /usr/local/lib/imtoolcmap/idl15.lut .
    cl&gt; type expr.dat
  	setcmap (
  	    zscale(i1, 5.0, 320.0, 201),
  	    "idl15.lut", 
  	    0.41, 
  	    1.35)
    cl&gt; export dev$pix dpix gif outbands="@expr.dat"
  <P>
  Combine three images representing RGB to an 8-bit Sun rasterfile with a
  computed colormap.  Scale the intensity value of each image differently.
  <P>
    cl&gt; type expr.dat
          cmap (
              zscale (i1),
              zscale (i2, 0.0, 1200.0),
  	    zscale (i3, -1.0, 320.0) )
    cl&gt; export im1,im2,im3 rgb ras outbands="@expr.dat"
  <P>
  Do the same example but apply a gamma correction to the images:
  <P>
    cl&gt; type expr.dat
          cmap (
              gamma (zscale(i1),        2.2),
              gamma (zscale(i2,0,1200), 2.2),
  	    gamma (zscale(i3,-1,320), 2.2) )
  <P>
  Write four images to a grayscale GIF file such that they are tiled in a 
  2x2 grid:
  <P>
    cl&gt; export im1,im2,im3,im4 quad gif \<BR>
    &gt;&gt;&gt;        outbands="band( (i1//i2), (i3//i4) )"
  <P>
  Do the same example but create a border of 2 gray pixels around each
  of the images and apply the AIPS0 LUT with brightness/contrast values
  to create a color image:
  <P>
    cl&gt; copy /usr/local/lib/imtoolcmap/aips0.lut .
    cl&gt; type expr.dat
          setcmap (
              band( 
                  128, 128,
                  (repl (128,2) // i1// repl (128,2) // i2 // repl (128,2)), 
                  128, 128,
                  (repl (128,2) // i3// repl (128,2) // i4 // repl (128,2)),
                  128, 128 ),
              "aips0.lut",
              0.54,
              1.03)
    cl&gt; export im1,im2,im3,im4 cquad gif outbands="@expr.dat"
  <P>
  </PRE>
  <P>
  Automatically scale an image ignoring data in a bad pixel mask (bpm), map the
  result to the greyscale part of the "<TT>overlay</TT>" color map, and apply a
  overlay pattern given by another mask (pattern).
  <P>
    cl&gt; export dev$pix,bpm,pattern foo gif \<BR>
    &gt;&gt;&gt; outbands = "<TT>setcmap(i3==0?(zscalem(i1,i2==0)*200/255.):i3+203,'overlay')</TT>"
  <P>
  <P>
  The pattern has values of 1 and 203 is added to get it into the color map
  values of the overlay colors.  The factor of 200/255 is to scale the result
  of zscalem from the range 0-255 to the range 0-200.
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_notes">NOTES</A></H2>
  <! BeginSection: 'NOTES'>
  <UL>
  	This task is new with V2.11.
  <P>
  	(long int headers in RAS and XWD may cause problems on 64-bit 
  machines like the Alpha where host software expects 64-bit values.  Need to
  see if IRAF on the alpha produces 32 or 64-bit longs, either way exchanging
  images may be a problem)
  <P>
  </UL>
  <! EndSection:   'NOTES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  	Output of bitmap images is currently not supported.
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  import, tvmark, imexpr
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'MORE ON OUTBANDS EXPRESSIONS' 'EXPORT HEADER FORMAT' 'BUILTIN FORMATS' 'COLOR OUTPUT IMAGES' 'EXAMPLES' 'NOTES' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>