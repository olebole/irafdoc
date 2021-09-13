.. _imexpr:

imexpr — Evaluate a general image expression
============================================

**Package: imutil**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  imexpr -- General image expression evaluator
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  imexpr expr output [a b c ...]
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>expr</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='expr' Line='expr'>
  <DD>The expression to be evaluated.  This may be the actual expression, or the
  string "<TT>@file</TT>" in which case the expression is taken from the named file.
  The input operands (i.e., numeric constants, images, or image header
  parameters) are referred to in the expression symbolically using the letters
  "<TT>a</TT>" through "<TT>z</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>The output image.  A section may be given to write into a section of an
  existing image.
  </DD>
  </DL>
  <DL>
  <DT><B>a - z</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='a' Line='a - z'>
  <DD>The input operands referenced by the expression.  The value of an operand
  may be an image name or section, a numeric constant, or a reference to an
  image header parameter of the form <I>operand.param</I>, where <I>operand</I>
  is one of the other input operands "<TT>a</TT>" through "<TT>z</TT>", corresponding to an input
  image (for example, "<TT>a.itime</TT>" is the parameter "<TT>itime</TT>" from the image
  assigned to operand "<TT>a</TT>").  An example of an input image operand is
  "<TT>a=dev$pix</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>dims = "<TT>auto</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dims' Line='dims = "auto"'>
  <DD>The dimensions of the output image.  If the special value <I>auto</I> is
  given the output image dimensions are computed based on the input operands
  and the expression being evaluated.  Otherwise the value is a list of axis
  lengths, e.g., "<TT>512,512</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>intype = "<TT>int</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='intype' Line='intype = "int"'>
  <DD>The minimum datatype for an input image operand.  If the special value
  <I>auto</I> is given the operand type will be the same as the pixel type of
  the image.  Otherwise one of the values "<TT>short</TT>", "<TT>int</TT>", "<TT>long</TT>", "<TT>real</TT>",
  or "<TT>double</TT>" should be given.  The program will promote the type of the
  input operand to the type specified if the actual type is less precise
  than the value of <I>intype</I>, otherwise the type of the input operand
  is not changed.  For example, if <I>intype</I> is "<TT>int</TT>" (the default),
  short integer input operands will be promoted to integer but int, long,
  real or double operands will be unaffected.  Setting <I>intype</I> to real
  will force the expression to be evaluated in floating point.
  </DD>
  </DL>
  <DL>
  <DT><B>outtype = "<TT>auto</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outtype' Line='outtype = "auto"'>
  <DD>The pixel type of the output image.  If set to the special value <I>auto</I>
  the output image will be the same type as the expression being evaluated.
  If set to <I>ref</I> the output image will have the same type as the
  "<TT>reference</TT>" input image (see below), regardless of the expression type.
  If an explicit type is specified such as "<TT>short</TT>", "<TT>ushort</TT>", "<TT>int</TT>", "<TT>real</TT>",
  an image of the indicated type will be created.
  </DD>
  </DL>
  <DL>
  <DT><B>refim = "<TT>auto</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='refim' Line='refim = "auto"'>
  <DD>The reference image to be used to pass the WCS and other image header
  attributes to the output image.  If set to <I>auto</I> the program will
  compute the best reference image, which is the first input image
  with the highest number of dimensions.  To force a particular input image
  to be the reference image the value should be set to the name of an input
  operand ("<TT>a</TT>", "<TT>b</TT>", etc.).  The named operand must refer to an image.
  </DD>
  </DL>
  <DL>
  <DT><B>bwidth = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='bwidth' Line='bwidth = 0'>
  <DD>The boundary width in pixels for boundary extension.  Boundary extension
  is enabled by setting this value to a positive nonzero value.  Boundary
  extension is needed when an input image section references out of bounds.
  </DD>
  </DL>
  <DL>
  <DT><B>btype = "<TT>nearest</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='btype' Line='btype = "nearest"'>
  <DD>The type of boundary extension, chosen from the list "<TT>constant</TT>", "<TT>nearest</TT>",
  "<TT>reflect</TT>", "<TT>wrap</TT>", or "<TT>project</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>bpixval = 0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='bpixval' Line='bpixval = 0.'>
  <DD>The boundary pixel value if <I>btype</I>="<TT>constant</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>rangecheck = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rangecheck' Line='rangecheck = yes'>
  <DD>If range checking is enabled then the program will check for illegal
  operations such as divide by zero or the square root or logarithm of a
  negative value, substituting a constant value (zero) if such an operation
  is detected.  This may be necessary to avoid aborting the entire operation
  because of a few bad pixels in an image.  A conditional expression may be
  used to detect such pixels and perform any special processing.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Enable or disable informative messages.  If enabled, the program will echo
  the expression to be evaluated after all expansions have been performed,
  and percent-done messages will be printed as the expression is evaluated.
  </DD>
  </DL>
  <DL>
  <DT><B>exprdb = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='exprdb' Line='exprdb = ""'>
  <DD>The file name of an optional expression database.  An expression database
  may be used to define symbolic constants or a library of custom function
  macros.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>imexpr</I> evaluates an image expression and writes the result to the
  output image.  Images may be any dimension or size and any datatype except
  complex (complex images may be read but only the real part will be used).
  <P>
  If the input images are not all the same size the computation will be
  performed over the largest area which is common to all images.  If the
  images are not all the same dimension the lesser dimension operands will be
  iteratively combined with the higher dimension ones.  For example, when
  both a one and two dimensional image are used in the same expression,
  the vector (one dimensional image) will be applied to all lines of the
  two dimensional image.
  <P>
  Evaluation of the image expression is carried out one line at a time.  This
  is efficient and permits operations on arbitrarily large images without
  using excessive memory, but does not allow 2D or higher operations to be
  performed within the expression (e.g., transpose).  The entire expression is
  evaluated once for each line of the output image.
  <P>
  <P>
  <B>Operands</B>
  <P>
  Input operands are represented symbolically in the input expression using
  the symbols "<TT>a</TT>" through "<TT>z</TT>", corresponding to <I>imexpr</I> task parameters.
  Use of symbolic operands allows the same expression to be used with different
  data sets, simplifies the expression syntax, and allows a single input image
  to be used several places in the same expression.
  <P>
  Three classes of input operands are recognized: images, image parameters, and
  numeric constants.
  <P>
  <PRE>
  	dev$pix[*,55]		image operand
  	a.itime			image parameter
  	1.2345			numeric constant
  </PRE>
  <P>
  Since the input operands are CL parameters they may be set on the command
  line, or entered in response to parameter prompts when the task executes and
  evaluates the input expression.  For example,
  <P>
  <PRE>
  	cl&gt; imexpr "a - a/b" pix
  	operand a: dev$pix[*,55]
  	operand b: a.itime
  </PRE>
  <P>
  would evaluate the expression shown, storing the result in the output image
  "<TT>pix</TT>".
  <P>
  Operands may also be specified directly in the expression, with the
  exception of image operands.  For example,
  <P>
  	cl&gt; imexpr "<TT>a - a / a.itime</TT>"
  <P>
  is equivalent to the earlier example.
  <P>
  If the input operand is not a simple identifier (a simple name like "<TT>itime</TT>"
  containing only alphanumeric characters, underscore, "<TT>.</TT>", or "<TT>$</TT>") then it
  is necessary to quote the operand name and precede it with an "<TT>@</TT>", e.g.,
  <P>
  	cl&gt; imexpr 'a - a / @"<TT>a.i-time</TT>"'
  <P>
  Finally, there is a special builtin type of operand used to represent the
  image pixel coordinates in an image expression.  These operands have the
  special reserved names "<TT>I</TT>", "<TT>J</TT>", "<TT>K</TT>", etc., up to the dimensions of the
  output image.  The names must be upper case to avoid confusion to with the
  input operands "<TT>i</TT>", "<TT>j</TT>", "<TT>k</TT>" and so on.
  <P>
  <PRE>
  	I			X coordinate of pixel (column)
  	J			Y coordinate of pixel (line)
  	K			Z coordinate of pixel (band)
  </PRE>
  <P>
  An example of the use of the pixel coordinate operands is the generation of
  multidimensional analytic functions.
  <P>
  <P>
  <B>Operators</B>
  <P>
  The expression syntax implemented by <I>imexpr</I> provides the following
  set of operators:
  <P>
  <PRE>
  	( expr )		grouping
  	+ - * /			arithmetic
  	**			exponentiation
  	//			concatenate
  	expr ? expr1 : expr2	conditional expression
  	@ "name"		get operand
  <P>
  	&amp;&amp;			logical and
  	||			logical or
  	! 			logical not
  	&lt;			less than
  	&lt;=			less than or equal
  	&gt;			greater than
  	&gt;=			greater than or equal
  	==			equals
  	!=			not equals
  	?=			substring equals
  <P>
  	&amp;			bitwise and
  	|			bitwise or
  	^			bitwise exclusive or
  	~			bitwise not (complement)
  </PRE>
  <P>
  The conditional expression has the value <I>expr1</I> if <I>expr</I> is true,
  and <I>expr2</I> otherwise.  Since the expression is evaluated at every pixel
  this permits pixel-dependent operations such as checking for special pixel
  values, or selection of elements from either of two vectors.  For example,
  the command
  <P>
  	(a &lt; 0) ? 555 : b / a
  <P>
  has the constant value 555 if "<TT>a</TT>" is less than zero, and "<TT>b / a</TT>" otherwise.
  Conditional expressions are general expressions and may be nested or used
  anywhere an expression is permitted.
  <P>
  The concatenation operator applies to all types of data, not just strings.
  Concatenating two vectors results in a vector the combined length of the
  two input vectors.
  <P>
  The substring equals operator "<TT>?=</TT>", used for string comparisons,  is like 
  "<TT>==</TT>" but checks for the presence of a substring, rather than exact equality
  of the two strings.
  <P>
  <P>
  <B>Functions</B>
  <P>
  Where it makes sense all intrinsic functions support all datatypes, with
  some restrictions on <I>bool</I> and <I>char</I>.  Arguments may be scalars or
  vectors and scalar and vector arguments may be mixed in the same function
  call.  Arguments are automatically type converted upon input as necessary.
  Some functions support a variable number of arguments and the details of
  the the operation to be performed may depend upon how many arguments are
  given.
  <P>
  Functions which operate upon vectors are applied to the <I>lines</I> of an
  image.  When applied to an image of dimension two or greater, these
  functions are evaluated separately for every line of the multidimensional
  image.
  <P>
  Standard Intrinsic Functions
  <P>
  <PRE>
  	abs (a)				absolute value
  	max (a, b, ...)			maximum value
  	min (a, b, ...)			minimum value
  	mod (a, b)			modulus
         sqrt (a)				square root
  </PRE>
  <P>
  Mathematical or trigonometric functions
  <P>
  <PRE>
         acos (a)				arc cosine
         asin (a)				arc sine
         atan (a [,b])			arc tangent
        atan2 (a [,b])			arc tangent
  	cos (a)				cosine
         cosh (a)				hyperbolic cosine
  	exp (a)				exponential
  	log (a)				natural logarithm
        log10 (a)				logarithm base 10
  	sin (a)				sine
         sinh (a)				hyperbolic sine
  	tan (a) 			tangent
         tanh (a) 			hyperbolic tangent
  </PRE>
  <P>
  The trigonometric functions operate in units of radians.  The <I>deg</I> and
  <I>rad</I> intrinsic functions (see below) can be used to convert to and from
  degrees if desired.
  <P>
  Type conversion functions
  <P>
  <PRE>
         bool (a)				coerce to boolean
        short (a)				coerce to short
  	int (a)				truncate to integer
         nint (a)				nearest integer
         long (a)				coerce to long (same as int)
         real (a)				coerce to real
       double (a)				coerce to double
  	str (a)				coerce to string
  </PRE>
  <P>
  The numeric type conversion functions will convert a string to a number if
  called with a character argument.  The <I>str</I> function will convert any
  number to a string.
  <P>
  Projection functions
  <P>
  <PRE>
  	len (a)				length of a vector
  	hiv (a)				high value of a vector
  	lov (a)				low value of a vector
         mean (a [, ksigma])		mean of a vector
       median (a)				median of a vector
       stddev (a [, ksigma])		standard deviation
  	sum (a)				sum of a vector
  </PRE>
  <P>
  The projection functions take a vector as input and return a scalar value as
  output.  The functions <I>mean</I> and <I>stddev</I>, used to compute the mean
  and standard deviation of a vector, allow an optional second argument which
  if given causes a K-sigma rejection to be performed.
  <P>
  Miscellaneous functions
  <P>
  <PRE>
  	deg (a)				radians to degrees
  	rad (a)				degrees to radians
       median (a, b, c [, d [, e]])	vector median of 3-5 vectors
         repl (a, n)			replicate
         sort (a)				sort a vector
        shift (a, npix)			shift a vector
  </PRE>
  <P>
  The <I>median</I> function shown here computes the vector median of several
  input vectors, unlike the projection median which computes the median value
  of a vector sample.  <I>sort</I> sorts a vector, returning the sorted vector
  as output (this can be useful for studying the statistics of a sample).
  <I>shift</I> applies an integral pixel shift to a vector, wrapping around at
  the endpoints.  A positive shift shifts data features to the right (higher
  indices).
  <P>
  The <I>repl</I> (replicate) function replicates a data element, returning a
  vector of length (n * len(a)) as output.  For example, this can be used to
  create a dummy data array or image by replicating a constant value.
  <P>
  <P>
  <B>The Expression Database</B>
  <P>
  The <I>imexpr</I> expression database provides a macro facility which can be
  used to create custom libraries of functions for specific applications. A
  simple example follows.
  <P>
  <PRE>
  	# Sample IMEXPR expression database file.
  <P>
  	# Constants.
  	SQRTOF2=	1.4142135623730950488
  	BASE_E=		2.7182818284590452353
  	PI=		3.1415926535897932385
  	GAMMA=		.57721566490153286061	# Euler's constant
  <P>
  	# Functions.
  	div10(a)	((a) / 10)
  	divz(a,b)	((abs(b) &lt; .000001) ? 0 : a / b)
  <P>
  	div(a,b)	(div10(b) / a)
  	sinx		(cos(I / 30.0))
  	sinxy(a,b)	(cos (I / a) + cos (J / b))
  </PRE>
  <P>
  The complete syntax of a macro entry is as follows:
  <P>
  	&lt;symbol&gt;[<TT>'('</TT> arg-list <TT>')'</TT>][<TT>':'</TT>|<TT>'='</TT>]     replacement-text
  <P>
  The replacement text may appear on the same line as the macro name or may
  start on the next line, and may extend over multiple input lines if
  necessary.  If so, continuation lines must be indented.  The first line
  with no whitespace at the beginning of the line terminates the macro.
  Macro functions may be nested.  Macro functions are indistinguishable from
  intrinsic functions in expressions.
  <P>
  <P>
  <B>IMEXPR and Pixel Masks</B>
  <P>
  Although <I>imexpr</I> has no special support for pixel masks, it was
  designed to work with masks and it is important to realize how these can be
  used.  IRAF image i/o includes support for a special type of image, the
  pixel mask or "<TT>.pl</TT>" type image.  Pixel masks are used for things such as
  region identification in images - any arbitrary region of an image can be
  assigned a constant value in a mask to mark the region.  Masks can then be
  used during image analysis to identify the subset of image pixels to be
  used.  An image mask stored as a "<TT>.pl</TT>" file is stored in compressed form and
  is typically only a few kilobytes in size.
  <P>
  There are many ways to create masks, but in some cases <I>imexpr</I> itself
  can be used for this purpose.  For example, to create a boolean mask with
  <I>imexpr</I> merely evaluate a boolean expression and specify a "<TT>.pl</TT>" file
  as the output image.  For example,
  <P>
      cl&gt; imexpr "<TT>a &gt; 800</TT>" mask.pl
  <P>
  will create a boolean mask "<TT>mask.pl</TT>" which identifies all the pixels in an
  image with a value greater than 800.
  <P>
  An example of the use of masks is the problem of combining portions of two
  images to form a new image.
  <P>
      cl&gt; imexpr "<TT>c ? a : b</TT>"  c=mask.pl
  <P>
  This example will select pixels from either image A or B to form the output
  image, using the mask assigned to operand C to control the selection.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Copy an image, changing the datatype to real (there are better ways to
  do this of course).
  <P>
      cl&gt; imexpr a pix2 a=pix outtype=real
  <P>
  2. Create a new, empty image with all the pixels set to 0.
  <P>
      cl&gt; imexpr "<TT>repl(0,512)</TT>" pix dim=512,512
  <P>
  3. Create a 1D image containing the sinc function.
  <P>
      cl&gt; imexpr "<TT>I == 10 ? 1.0 : sin(I-10.0)/(I-10)</TT>" sinc dim=20
  <P>
  4. Create a new image containing a simple test pattern consisting of a 5
  element vector repeated 100 times across each image line.
  <P>
      cl&gt; imexpr "<TT>repl((9 // 3 // 3 // 11 // 11), 100)</TT>" patt dim=500,500
  <P>
  5. Subtract the median value from each line of an image.
  <P>
      cl&gt; imexpr "<TT>a - median(a)</TT>" medimage
  <P>
  6. Compute the HIV (low value) projection of an image.  The result is a
  transposed 1D image.
  <P>
      cl&gt; imexpr "<TT>hiv(a)</TT>" hvector
  <P>
  7. Swap the left and right halves of an image.
  <P>
  <PRE>
      cl&gt; imexpr "a // b" pix swapimage
      operand a: dev$pix[256:512,*]
      operand b: dev$pix[1:255,*]
  </PRE>
  <P>
  8. Create a circular mask of a given radius about a user-defined center.
  <P>
  <PRE>
      cl&gt; type expr
      (sqrt((I-b)**2 + (J-c)**2) &lt;= d)
      cl&gt; imexpr @expr mask.pl b=256 c=256 d=100 dims=512,512
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  The input and output images cannot be the same.
  No support for type complex yet, or operations like the fourier transform.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imarith, imfunction, imcombine
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
