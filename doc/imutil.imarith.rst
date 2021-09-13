imarith — Simple image arithmetic
=================================

**Package: imutil**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>imarith (Sep86)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>images.imutil</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>imarith (Sep86)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>imarith</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  imarith -- binary image arithmetic
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage_">USAGE	</A></H2>
  <! BeginSection: 'USAGE	'>
  <UL>
  imarith operand1 op operand2 result
  </UL>
  <! EndSection:   'USAGE	'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_operand1">operand1, operand2</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='operand1' Line='operand1, operand2'>
  <DD>Lists of images and constants to be used as operands.
  Image templates and image sections are allowed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_op">op    </A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='op' Line='op    '>
  <DD>Operator to be applied to the operands.  The allowed operators
  are "<TT>+</TT>", "<TT>-</TT>", "<TT>*</TT>", "/"<TT>, </TT>"min"<TT>, and </TT>"max"<TT>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_result">result</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='result' Line='result'>
  <DD>List of resultant images.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_title">title = </TT>""<TT></A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='title' Line='title = ""'>
  <DD>Title for the resultant images.  If null (</TT>""<TT>) then the title is taken
  from operand1 if operand1 is an image or from operand2 otherwise.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_divzero">divzero = 0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='divzero' Line='divzero = 0.'>
  <DD>Replacement value for division by zero.  When the denominator is zero
  or nearly zero the result is replaced by this value.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_hparams">hparams = </TT>""<TT></A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='hparams' Line='hparams = ""'>
  <DD>List of header parameters to be operated upon.  This is primarily
  used for adding exposure times when adding images.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_pixtype">pixtype = </TT>""<TT>, calctype = </TT>""<TT></A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pixtype' Line='pixtype = "", calctype = ""'>
  <DD>Pixel datatype for the resultant image and the internal calculation datatype.
  The choices are given below.  They may be abbreviated to one character.
  <DL>
  <DT><B><A NAME="l_"></TT>""<TT>    </A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='""    '>
  <DD><I>Calctype</I> defaults to the highest precedence operand datatype.  If the
  highest precedence datatype is an integer type and the operation is
  division then the calculation type will be "<TT>real</TT>".  If the highest
  precedence operand is type "<TT>ushort</TT>", <I>calctype</I> will default to
  "<TT>long</TT>".  <I>Pixtype</I> defaults to <I>calctype</I>. Users who want type
  "<TT>ushort</TT>" images on output will need to set <I>pixtype</I> to "<TT>ushort</TT>"
  explicitly.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">"<TT>1</TT>", "<TT>2</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"1", "2"'>
  <DD>The pixel datatype of the first or second operand.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">"<TT>short</TT>", "<TT>ushort</TT>", "<TT>integer</TT>", "<TT>long</TT>", "<TT>real</TT>", "<TT>double</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"short", "ushort", "integer", "long", "real", "double"'>
  <DD>Allowed IRAF pixel datatypes.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>Print the operator, operands, calculation datatype, and the resultant image
  name, title, and pixel datatype.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_noact">noact = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='noact' Line='noact = no'>
  <DD>Like the verbose option but the operations are not actually performed.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Binary image arithmetic is performed of the form:
  <P>
  	operand1 op operand2 = result
  <P>
  where the operators are addition, subtraction, multiplication,
  division, and minimum and maximum.  The division operator checks for
  nearly zero denominators and replaces the ratio by the value specified
  by the parameter <I>divzero</I>.  The operands are lists of images and
  numerical constants and the result is a list of images.  The number of
  elements in an operand list must either be one or equal the number of
  elements in the resultant list.  If the number of elements is one then
  it is used for each resultant image.  If the number is equal to the
  number of resultant images then the elements in the operand list are
  matched with the elements in the resultant list.  The only limitation
  on the combination of images and constants in the operand lists is that
  both operands for a given resultant image may not be constants.  The
  resultant images may have the same name as one of the operand images in
  which case a temporary image is created and after the operation is
  successfully completed the image to be replaced is overwritten by the
  temporary image.
  <P>
  If both operands are images the lengths of each axis for the common
  dimensions must be the same though the dimensions need not be the
  same.  The resultant image header will be a copy of the operand image
  with the greater dimension.  If the dimensions are the same then image
  header for the resultant image is copied from operand1.  The title of
  the resultant image may be changed using the parameter <I>title</I>.
  The pixel datatype for the resultant image may be set using the
  parameter <I>pixtype</I>.  If no pixel datatype is specified then the
  pixel datatype defaults to the calculation datatype given by the
  parameter <I>calctype</I>.  The calculation datatype defaults to the
  highest precedence datatype of the operand images or constants except
  that a division operation will default to real for integer images.
  The precedence of the datatypes, highest first, is double,
  real, long, integer, and short.  The datatype of a constant operand is
  either short integer or real.  A real constant has a decimal point.
  <P>
  Arithmetic on images of unequal dimensions implies that the operation
  is repeated for each element of the higher dimensions.  For example
  subtracting a two dimensional image from a three dimensional image
  consists of subtracting the two dimensional image from each band of the
  three dimensional image.  This works for any combination of image
  dimensions.  As an extreme example dividing a seven dimensional image
  by a one dimension image consists of dividing each line of each plane
  of each band ... by the one dimensional image.
  <P>
  There are two points to emphasize when using images of unequal
  dimensions.  First, a one dimensional image operates on a line
  of a two or higher dimension image.  To apply a one dimensional image
  to the columns of a higher dimensional image increase the image
  dimensionality with <B>imstack</B>, transpose the resultant image,
  and then replicate the columns with <B>blkrep</B> (see the EXAMPLE
  section).  The second point of confusion is that an image with a
  size given by <B>imheader</B> of [20,1] is a two dimensional image
  while an image with size of [20] is a one dimensional image.  To
  reduce the dimensionality of an image use <B>imcopy</B>.
  <P>
  In addition to operating on the image pixels the image header parameters
  specified by the list <I>hparams</I> are also operated upon.  The operation
  is the same as performed on the pixels and the values are either the
  values associated with named header parameters or the operand constant
  values.  The primary purpose of this feature is to add exposure times
  when adding images.
  <P>
  The verbose option is used to record the image arithmetic.  The output
  consists of the operator, the operand image names, the resultant image
  name and pixel datatype, and the calculation datatype.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. To add two images and the exposure times:
  <P>
  <PRE>
  	cl&gt; imarith ccd1 + ccd2 sum
  	&gt;&gt;&gt; hparams="itime,otime,ttime,exposure"
  </PRE>
  <P>
  2. To subtract a constant from an image and replace input image by the
  subtracted image:
  <P>
  	cl&gt; imarith m31 - 223.2 m31
  <P>
  Note that the final pixel datatype and the calculation datatype will be at
  least of type real because the constant operand is real.
  <P>
  3. To scale two exposures, divide one by the other, and extract the central
  portion:
  <P>
  <PRE>
  	cl&gt; imarith exp1[10:90,10:90] * 1.2 temp1
  	cl&gt; imarith exp2[10:90,10:90] * 0.9 temp2
  	cl&gt; imarith temp1 / temp2 final title='Ratio of exp1 and exp 2'
  	cl&gt; imdelete temp1,temp2
  </PRE>
  <P>
  Note that in this example the images temp1, temp2, and final will be
  of real pixel datatype (or double if either exp1 or exp2 are of pixel
  datatype double) because the numerical constants are real numbers.
  <P>
  4. To divide two images of arbitrary pixel datatype using real arithmetic
  and create a short pixel datatype resultant image:
  <P>
  <PRE>
  	cl&gt; imarith image1 / image2 image3 pixtype=short  \<BR>
  	&gt;&gt;&gt; calctype=real title="Ratio of image1 and image2"
  </PRE>
  <P>
  5. To divide several images by calibration image using the image pixel type of
  the numerator images to determine the pixel type of the calibrated images
  and the calculation arithmetic type:
  <P>
  <PRE>
  	cl&gt; imarith image1,image2,image3 / calibration \<BR>
  	&gt;&gt;&gt; image1a,image2a,image3a pixtype=1 calctype=1
  </PRE>
  <P>
  The same operation can be done in place with image template expansion by:
  <P>
  <PRE>
  	cl&gt; imarith image* / calibration image* pixtype=1 calctype=1
  </PRE>
  <P>
  6. To subtract a two dimensional bias from stacked observations (multiple
  two dimensional observations stacked to form a three dimensional image):
  <P>
  	cl&gt; imarith obs* - bias obs*//b
  <P>
  Note that the output observations obs101b, ..., will be three dimensional.
  <P>
  7. To divide a 50 x 50 image by the average column:
  <P>
  <PRE>
  	cl&gt; blkavg img avcol 50 1
  	cl&gt; blkrep avcol avcol 50 1
  	cl&gt; imarith img / avcol flat
  </PRE>
  <P>
  8. To subtract a one dimensional image from the lines of a two dimensional
  image:
  <P>
  	cl&gt; imarith im2d - im1d diff
  <P>
  9. To subtract a one dimensional image from the columns of a two dimensional
  image:
  <P>
  <PRE>
  	cl&gt; imstack im1d imcol
  	cl&gt; imtranspose imcol imcol
  	cl&gt; blkrep imcol imcol 100 1
  	cl&gt; imarith im2d - imcol diff
  </PRE>
  <P>
  Note the need to make a two dimensional image with each column
  replicated since a one dimensional image will operate on the lines
  of a two dimensional image.
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  blkrep, imdivide, imfunction, imstack, imtranspose
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>