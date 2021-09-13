.. _mkpattern:

mkpattern — Make/add patterns to images
=======================================

**Package: artdata**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  mkpattern - Make/add patterns in images
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  mkpattern input
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>Images to create or modify.  Image sections are allowed to apply a pattern
  to a portion of an image.
  </DD>
  </DL>
  <DL>
  <DT><B>output = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output = ""'>
  <DD>Output images when modifying input images.  If no output images are
  given then existing images in the input list are modified directly.
  If an output image list is given then it must match in number the
  input list.
  </DD>
  </DL>
  <DL>
  <DT><B>pattern = "<TT>constant</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pattern' Line='pattern = "constant"'>
  <DD>Pattern to be used.  The patterns are:
  <DL>
  <DT><B>constant</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='constant' Line='constant'>
  <DD>Constant value v1.
  </DD>
  </DL>
  <DL>
  <DT><B>grid</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='grid' Line='grid'>
  <DD>A grid starting with the first pixel and going in steps of the
  pattern size with value v2.  Pixels between the grid have value v1.
  A minimum grid size of 2 is enforced.
  </DD>
  </DL>
  <DL>
  <DT><B>checker</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='checker' Line='checker'>
  <DD>A checkerboard with squares of the pattern size alternating between values v1
  and v2 starting with v1.
  </DD>
  </DL>
  <DL>
  <DT><B>coordinates</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='coordinates' Line='coordinates'>
  <DD>Each pixel is numbered sequentially starting with 1 with the column
  dimension varying fastest.
  </DD>
  </DL>
  <DL>
  <DT><B>slope</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='slope' Line='slope'>
  <DD>A sloped plane starting with value v1 for the first pixel and value v2 for
  the last pixel in one or two dimensions.
  </DD>
  </DL>
  <DL>
  <DT><B>square</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='square' Line='square'>
  <DD>A checkerboard pattern in which the size of the squares begin with
  the pattern size and grow as the square of the coordinate.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>option = "<TT>replace</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='option' Line='option = "replace"'>
  <DD>Editing option when modifying existing images.  Often this is used
  in conjunction with image sections to modify a part of an image.
  The options are:
  <P>
  <PRE>
   replace - Replace the image with the pattern.
       add - Add the pattern to the image.
  multiply - Multiply the pattern with the image values.
  </PRE>
  </DD>
  </DL>
  <DL>
  <DT><B>v1 = 0., v2 = 1.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='v1' Line='v1 = 0., v2 = 1.'>
  <DD>Pattern values used as described for each pattern.
  </DD>
  </DL>
  <DL>
  <DT><B>size = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='size' Line='size = 1'>
  <DD>Pattern size used as described for each pattern.
  </DD>
  </DL>
  <P>
  WHEN CREATING NEW IMAGES
  <DL>
  <DT><B>title = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='title' Line='title = ""'>
  <DD>Image title to be given to the images.  Maximum of 79 characters.
  </DD>
  </DL>
  <DL>
  <DT><B>pixtype = "<TT>real</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pixtype' Line='pixtype = "real"'>
  <DD>Pixel datatype of new images; one of ushort, short, integer, real, double,
  or complex.
  </DD>
  </DL>
  <DL>
  <DT><B>ndim = 2</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ndim' Line='ndim = 2'>
  <DD>Number of dimensions between 0 and 7.
  </DD>
  </DL>
  <DL>
  <DT><B>ncols = 512, nlines = 512</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ncols' Line='ncols = 512, nlines = 512'>
  <DD>Number of columns (first dimension) and lines (second dimension).
  </DD>
  </DL>
  <DL>
  <DT><B>n3 = 1, n4 = 1, n5 = 1, n6 = 1, n7 = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='n3' Line='n3 = 1, n4 = 1, n5 = 1, n6 = 1, n7 = 1'>
  <DD>Number of pixels in 3rd-7th  dimensions
  </DD>
  </DL>
  <DL>
  <DT><B>header = "<TT>artdata$stdheader.dat</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='header' Line='header = "artdata$stdheader.dat"'>
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
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task creates or modifies images with a choice of patterns.  New images
  are created with the specified dimensions, datatype, and pattern.
  Existing images may have the pattern replace, add, or multiply the
  pixel values.  Existing images may be modified in place or new images may be
  created and image sections are allowed.
  <P>
  For new images a set of header keywords may be added by specifying an
  image or data file with the <I>header</I> parameter (see also <B>mkheader</B>).
  If a data file is specified lines beginning with FITS keywords are
  entered in the image header.  Leading whitespace is ignored and any
  lines beginning with words having lowercase and nonvalid FITS keyword
  characters are ignored.
  <P>
  This task is the simplest one for creating empty images to be used for
  mosaicing with <B>imcopy</B> and making patterns for testing display and
  image operators.  The replace option is generally used with image sections
  to place constant values in regions.  The multiply option is useful
  for making masks of the given pattern when the values are 0 and 1.
  <P>
  Though the patterns make sense extending to higher dimensions they
  are only defined in two dimensions.  One dimensional images may be
  thought of as the first line of the two dimensional pattern.  Images
  with dimensions greater than 2 simply repeat the two dimensional
  pattern into the higher dimensions.  The reason for stopping at
  two dimensions is simplicity.
  <P>
  The patterns have the following precise definitions where P(i,j) is the
  pixel value at column i and line j, v1 and v2 are the pattern
  values, size is the pattern size, ncols and nlines are the number of
  columns and lines in the image, int is the integer function, mod is the
  modulus function, and sqrt is the square root function.
  <P>
  <PRE>
                  k = int ((i-1)/size), l = int ((j-1)/size)
                  ksr = int (sqrt (k)), lsr = int (sqrt (l))
                  slope = (v2-v1) / ((ncols+nlines-2)/size)
  <P>
      constant:   P(i,j) = v1
  <P>
          grid:   P(i,j) = v2   when mod(i,size)=1 or mod(j,size)=1
                  P(i,j) = v1   otherwise
  <P>
   coordinates:   P(i,j) = i + j * ncols
  <P>
       checker:   P(i,j) = v1   when mod(k,2)=0 and mod(l,2)=0
                  P(i,j) = v2   when mod(k,2)=1 and mod(l,2)=0
                  P(i,j) = v2   when mod(k,2)=0 and mod(l,2)=1
                  P(i,j) = v1   when mod(k,2)=1 and mod(l,2)=1
  <P>
         slope:   P(i,j) = v1 + slope * (k + l) 
  <P>
        square:   P(i,j) = v1   when mod(ksr,2)=0 and mod(lsr,2)=0
                  P(i,j) = v2   when mod(ksr,2)=1 and mod(lsr,2)=0
                  P(i,j) = v2   when mod(ksr,2)=0 and mod(lsr,2)=1
                  P(i,j) = v1   when mod(ksr,2)=1 and mod(lsr,2)=1
  </PRE>
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Create an empty (constant value of zero) three dimensional image.
  <P>
  <PRE>
  	cl&gt; mkpattern cube ndim=3 nc=100 nl=100 n3=100
  </PRE>
  <P>
  2. Replace a square region of an image with the value -1000.
  <P>
  <PRE>
  	cl&gt; mkpat alpha[201:250,1:50] v1=-1000
  </PRE>
  <P>
  3. Put a grid pattern on an image to create a new image.
  <P>
  <PRE>
  	cl&gt; mkpat dev$pix out=gridpix pat=grid op=mul v1=1 v2=0
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>MKPATTERN V2.11</B></DT>
  <! Sec='REVISIONS' Level=0 Label='MKPATTERN' Line='MKPATTERN V2.11'>
  <DD>Now allows ndim=0 to create dataless header.
  <P>
  Now allows type ushort pixel type.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imcopy, imreplace
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
