mskexpr — Create masks using an expression and reference images
===============================================================

**Package: proto**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>mskexpr (Dec01)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>proto</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>mskexpr (Dec01)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>mskexpr</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  mskexpr -- General mask expression evaluator
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  mskexpr expr masks refimages
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_expr">expr</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='expr' Line='expr'>
  <DD>The expression to be evaluated.  This may be the actual expression, or the
  string "<TT>@file</TT>" in which case the expression is taken from the named file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_masks">masks</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='masks' Line='masks'>
  <DD>The output masks. The size of the output masks defaults to the size of
  the reference image if any, the size of the reference mask if any, or the
  value of the dims parameter, in that order.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_refimages">refimages</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='refimages' Line='refimages'>
  <DD>The optional list of reference images. If the reference image list is defined
  there must be one reference image for every output mask. The reference image
  operand name is "<TT>i</TT>" and the associated reference image keywords are
  referred to as "<TT>i.&lt;keyword&gt;</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_refmasks">refmasks</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='refmasks' Line='refmasks'>
  <DD>The optional list of reference masks. If the reference mask list is defined
  there must be one reference mask for every output mask. The reference mask
  operand name is "<TT>m</TT>" and the associated reference image keywords are
  referred to as "<TT>m.&lt;keyword&gt;</TT>".
  <P>
  If both a reference image and reference mask are defined the reference mask will
  be matched to reference image as described by the help topic <B>pmmatch</B>.
  The application default is a match in "<TT>logical</TT>" coordinates which is
  effectively a trim or pad operation to match the size of the reference image.
  However, by use of the "<TT>pmmatch</TT>" environment variable one may match in
  "<TT>physcial</TT>" or "<TT>world</TT>" coordinates.  Note that the simple expression
  "<TT>m</TT>" may be used to create an output mask file from the internal matching.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_dims">dims = "<TT>512,512</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dims' Line='dims = "512,512"'>
  <DD>The default output mask dimensions. The value of dims is a comma delimited
  list of dimensions.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_depth">depth = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='depth' Line='depth = 0'>
  <DD>The output mask depth in bits. The maximum depth and current default is
  27.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_exprdb">exprdb = "<TT>none</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='exprdb' Line='exprdb = "none"'>
  <DD>The file name of an optional expression database. An expression database
  may be used to define symbolic constants or a library of custom function
  macros.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print task status messages ?
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  Mskexpr evaluates a mask expression <I>expr</I> and writes the results to an
  output mask <I>masks</I> image. If expr is preceded by an "<TT>@</TT>" sign then
  the expression is read from the named file.  The size of the output mask is
  determined by the reference image <I>refimages</I> if any, the reference masks
  <I>refmasks</I> if any, or the values of the <I>dims</I> parameter, in that
  order of precedence.
  <P>
  The output mask is an integer image. Therefore any mask expression must
  evaluate to an integer value. The depth of the output mask in bits is defined
  by the <I>depth</I> parameter. The default value is 27 bits.
  <P>
  Evaluation of the mask expression is carried out one line at a time. This
  is efficient and permits operations on masks with large reference images
  to be carried out efficiently without using excessive memory. The entire
  expression is evaluated once per line of the output mask.
  <P>
  <B>Reference Images and Masks</B>
  <P>
  In most cases one wants to make output masks to associate with images.
  The reference image list provides a reference image which is used to
  define the size and some of the header for the output mask.  Note that
  a reference mask may be used for this purpose if no reference image
  is specified.
  <P>
  Sometimes one may want to merge previous mask information into the output
  mask.  The reference mask can be used for this purpose using the operand
  "<TT>m</TT>" in the expressions.
  <P>
  When both a reference image and a reference mask are specified another
  useful feature is provided.  This consists of matching the reference
  mask to the reference image even when the two are of different sizes or
  are related not "<TT>pixel-by-pixel</TT>" but through various transformations.
  The matching feature is described in the help topic <B>pmmatch</B>.
  (Note that the default for matching in world coordinates results in
  boolean mask values so if the actual mask values are needed the pmmatch
  setting must be set appropriately.)  The application default is a match
  in "<TT>logical</TT>" coordinates which is effectively a trim or pad operation to
  match the size of the reference image.  However, by use of the "<TT>pmmatch</TT>"
  environment variable one may match in "<TT>physcial</TT>" or "<TT>world</TT>" coordinates.
  <P>
  This task is one way to create a matched mask for tasks that do not
  do the matching.  The simple expression "<TT>m</TT>" when both a reference image
  and reference mask are specified will output a mask from for the reference
  image that is match in logical pixel space.
  <P>
  <B>Operands</B>
  <P>
  Input operands are represented symbolically in the input expression. Use of
  symbolic operands allows the same expression to be used with different data
  sets, simplifies the expression syntax, and allows a single input image
  to be used several places in the same expression.
  <P>
  The following operands are recognized:
  <P>
  <PRE>
  	i		reference image 
  	i.itime		reference image keyword
  	m		reference mask 
  	m.itime		reference mask keyword
  	1.2345		numeric constant
  </PRE>
  <P>
  Finally, there is a special builtin type of operand used to represent the
  mask pixel coordinates in a mask expression.  These operands have the
  special reserved names "<TT>I</TT>", "<TT>J</TT>", "<TT>K</TT>", etc., up to the dimensions of the
  output image.  The names must be upper case to avoid confusion to with the
  input operands "<TT>i</TT>" and "<TT>m</TT>".
  <P>
  <PRE>
          I                x coordinate of pixel (column)
          J                y coordinate of pixel (line)
          K                z coordinate of pixel (band)
  </PRE>
  <P>
  <B>Operators</B>
  <P>
  The expression syntax implemented by mskexpr provides the following
  set of operators:
  <P>
  <PRE>
          ( expr )                grouping
          + - * /                 arithmetic
          **                      exponentiation
          //                      concatenate
          expr ? expr1 : expr2    conditional expression
          @ "name"                get operand
  <P>
          &amp;&amp;                      logical and
          ||                      logical or
          !                       logical not
          &lt;                       less than
          &lt;=                      less than or equal
          &gt;                       greater than
          &gt;=                      greater than or equal
          ==                      equals
          !=                      not equals
          ?=                      substring equals
  <P>
          &amp;                       bitwise and
          |                       bitwise or
          ^                       bitwise exclusive or
          ~                       bitwise not
  </PRE>
  <P>
  The conditional expression has the value <I>expr1</I> if <I>expr</I> is true,
  and <I>expr2</I> otherwise.  Since the expression is evaluated at every pixel
  this permits pixel-dependent operations such as checking for special pixel
  values, or selection of elements from either of two vectors.  For example,
  the command
  <P>
          (i &gt; -10 &amp;&amp; i &lt; 32000) ? 0 : 1
  <P>
  has the constant value 0 if the reference image is greater than -10 and less
  than 32000, and 1 otherwise. Conditional expressions are general expressions
  and may be nested or used anywhere an expression is permitted.
  <P>
  The concatenation operator applies to all types of data, not just strings.
  Concatenating two vectors results in a vector the combined length of the
  two input vectors.
  <P>
  The substring equals operator "<TT>?=</TT>", used for string comparisons,  is like
  "<TT>==</TT>" but checks for the presence of a substring, rather than exact equality
  of the two strings.
  <P>
  <B>Region Functions</B>
  <P>
  Mskexpr supports a group of boolean region functions which can be used to set
  values inside or outside of certain geometric shapes. The routines may be
  called in two ways. The first way assumes that the output masks are two-
  dimensional. The second way assumes that they are multi-dimensional and
  specifies which dimensions the geometric operator applies to.
  <P>
  <PRE>
        point (x1, y1)
       circle (xc, yc, r)
      ellipse (xc, yc, r, ratio, theta)
          box (x1, y1, x2, y2) 
    rectangle (xc, yc, r, ratio, theta)
       vector (x1, y1, x2, y2, width)
          pie (xc, yc, theta1, theta2)
      polygon (x1, y1, ..., xn, yn)
         cols (ranges)
        lines (ranges)
     cannulus (xc, yc, r1, r2)
     eannulus (xc, yc, r1, r2, ratio, theta)
     rannulus (xc, yc, r1, r2, ratio, theta)
     pannulus (width, x1, y1, ..., xn, yn)
  <P>
        point (I, J, x1, y1)
       circle (I, J, xc, yc, r)
      ellipse (I, J, xc, yc, r, ratio, theta)
          box (I, J, x1, y1, x2, y2) 
    rectangle (I, J, xc, yc, r, ratio, theta)
       vector (I, J, x1, y1, x2, y2, width)
          pie (I, J, xc, yc, theta1, theta2)
      polygon (I, J, x1, y1, .., xn, yn)
         cols (I, ranges)
        lines (J, ranges)
     cannulus (I, J, xc, yc, r1, r2)
     eannulus (I, J, xc, yc, r1, r2, ratio, theta)
     rannulus (I, J, xc, yc, r1, r2, ratio, theta)
     pannulus (I, J, width, x1, y1, ..., xn, yn)
  <P>
        xc,yc - center coordinates in pixels
        r1,r2 - semi-major axis lengths in pixels
        ratio - ratio of semi-minor / semi-major axes
     theta[n] - position angle in degrees
        x1,y1 - starting coordinates in pixels
        x2,y2 - ending coordinates in pixels
    x[n],y[n] - vertices of a polygon
       ranges - string defining a range, e.g. "100-200,300,400-500"
  </PRE>
  <P>
  <B>Other Functions</B>
  <P>
  Where it makes sense all intrinsic functions support all datatypes, with
  some restrictions on <I>bool</I> and <I>char</I>.  Arguments may be scalars or
  vectors. Scalar and vector arguments may be mixed in the same function
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
          abs (arg)                       absolute value
          max (arg, 0.0, ...)             maximum value
          min (arg1, arg2, ...)           minimum value
          mod (arg1, arg2)                modulus
         sqrt (arg)                       square root
  </PRE>
  <P>
  Mathematical or trigonometric functions
  <P>
  <PRE>
         acos (arg)                         arc cosine
         asin (arg)                         arc sine
         atan (arg [,arg2])                 arc tangent
        atan2 (arg [,arg2])                 arc tangent
          cos (arg)                         cosine
         cosh (arg)                         hyperbolic cosine
          exp (arg)                         exponential
          log (arg)                         natural logarithm
        log10 (arg)                         logarithm base 10
          sin (arg)                         sine
         sinh (arg)                         hyperbolic sine
          tan (arg)                         tangent
         tanh (arg)                         hyperbolic tangent
  </PRE>
  <P>
  The trigonometric functions operate in units of radians.  The <I>deg</I> and
  <I>rad</I> intrinsic functions (see below) can be used to convert to and from
  degrees if desired.
  <P>
  Type conversion functions
  <P>
  <PRE>
         bool (arg)                         coerce to boolean
        short (arg)                         coerce to short
          int (arg)                         truncate to integer
         nint (arg)                         nearest integer
         long (arg)                         coerce to long (same as int)
         real (arg)                         coerce to real
       double (arg)                         coerce to double
          str (arg)                         coerce to string
  </PRE>
  <P>
  The numeric type conversion functions will convert a string to a number if
  called with a character argument.  The <I>str</I> function will convert any
  number to a string.
  <P>
  Projection functions
  <P>
  <PRE>
          len (arg)                         length of a vector
          hiv (arg)                         high value of a vector
          lov (arg)                         low value of a vector
         mean (arg [,ksigma])               mean of a vector
       median (arg)                         median of a vector
       stddev (arg [, ksigma])              standard deviation
          sum (arg)                         sum of a vector
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
          deg (arg)                         radians to degrees
          rad (arg)                         degrees to radians
       median (arg1, arg2, arg3, ...)       vector median of 3-5 vectors
         repl (arg, n)                      replicate
         sort (arg)                         sort a vector
        shift (arg, npix)                   shift a vector
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
  <B>The Expression Database</B>
  <P>
  The <I>mskexpr</I> expression database provides a macro facility which can be
  used to create custom libraries of functions for specific applications. A
  simple example follows.
  <P>
  <PRE>
          # Sample MSKEXPR expression database file.
  <P>
          # Constants.
          SQRTOF2=        1.4142135623730950488
          PI=             3.1415926535897932385
  <P>
          # Simple bad data functions.
  	bdata1		(i &lt; -100 || i &gt; 25000)
  	bdata2		(i &lt; -100 || i &gt; 32000)
  <P>
  	# New regions functions.
  	cmpie(xc,yc,r,t1,t2) 	circle (xc, yc, r) &amp;&amp; (! pie (xc, yc, t1, t2))
  </PRE>
  <P>
  The complete syntax of a macro entry is as follows:
  <P>
          &lt;symbol&gt;[<TT>'('</TT> arg-list <TT>')'</TT>][<TT>':'</TT>|<TT>'='</TT>]     replacement-text
  <P>
  The replacement text may appear on the same line as the macro name or may
  start on the next line, and may extend over multiple input lines if necessary.
  If so, continuation lines must be indented.  The first line with no whitespace
  at the beginning of the line terminates the macro. Macro functions may be
  nested.  Macro functions are indistinguishable from intrinsic functions in
  expressions.
  <P>
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Create a 0-valued 512 x 512 mask and set all the pixels inside a circular
  annulus to 1.
  <P>
  <PRE>
  cl&gt; type expr.dat
  cannulus (256., 256., 20., 40.) ? 1 : 0 
  cl&gt; mskexpr @expr.dat mask.pl ""
  </PRE>
  <P>
  2. Repeat the previous example but set all the pixels outside the circular
  annulus to 1.
  <P>
  <PRE>
  cl&gt; type expr.dat
  ! cannulus (256., 256., 20., 40.) ? 1 : 0 
  cl&gt; mskexpr @expr.dat mask.pl ""
  </PRE>
  <P>
  3. Create a 0-valued 512 x 512 mask and set all the pixels inside the
  intersection of 2 circles to 1.
  <P>
  <PRE>
  cl&gt; type expr.dat
  circle (220., 220., 50.) &amp;&amp; circle (240., 220., 50.) ? 1 : 0 
  cl&gt; mskexpr @expr.dat mask.pl ""
  </PRE>
  <P>
  4. Create a 0 valued mask and set all the pixels outside the good
  data range 0 &lt;= pixval &lt;= 10000 in the reference image and outside
  a circle to 1. Note that the i character defines the reference image
  operand.
  <P>
  <PRE>
  cl&gt; type expr.dat
  i &lt; 0 || i &gt; 10000 || circle (256., 256., 50.) ? 1 : 0 
  cl&gt; mskexpr @expr.dat mask.pl dev$pix
  </PRE>
  <P>
  5. Create a 0 valued 512 x 512 mask and set all the pixels inside a circle
  excluding a wedge shaped region to 1. The expression cmpie is used defined
  and stored in the expression database "<TT>myexpr.db</TT>" 
  <P>
  <PRE>
  cl&gt; type myexpr.db
  # Sample MSKEXPR expression database file.
  <P>
  # Constants.
  SQRTOF2=        1.4142135623730950488
  PI=             3.1415926535897932385
  <P>
  # Simple bad data functions.
  bdata1          (i &lt; -100 || i &gt; 25000)
  bdata2          (i &lt; -100 || i &gt; 32000)
  <P>
  # New regions functions.
  cmpie(xc,yc,r,t1,t2)    circle (xc, yc, r) &amp;&amp; (! pie (xc, yc, t1, t2))
  <P>
  cl&gt; type expr.dat
  cmpie (256., 256., 50., 0., 30.) ? 1 : 0
  <P>
  cl&gt; mskexpr @expr.dat mask.pl "" exprdb=myexpr.db
  </PRE>
  <P>
  6.  A set of dithered images have been transformed to a common world
  coordinate system, stacked, and a mask created for the sources.  To
  create a boolean mask for one of the images from the deep source mask:
  <P>
  <PRE>
  cl&gt; set pmmatch="world"
  cl&gt; mskexpr "m" mask1.pl exp1 refmask=stackmask
  </PRE>
  <P>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_time_requirements">TIME REQUIREMENTS</A></H2>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  <P>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imexpr, mskregions, pmmatch
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>