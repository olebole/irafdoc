surfit — Fit a surface, z=f(x,y), to a set of x, y, z points
============================================================

**Package: utilities**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>surfit (Jun93)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>utilities</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>surfit (Jun93)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>surfit</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  surfit -- fit a surface, z=f(x,y), to a set of x, y, z points
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  surfit input
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>Input text file containing the data to be fit.  The file consists of lines
  with three or four whitespace separated values giving x, y, z, and
  optionally a weight.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_image">image = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image = ""'>
  <DD>Optional image name in which to create an evenly sampled image of the
  fitted surface.  If no name is specified a image is not created.  If an
  image name is specified then the x range in the input is evenly divided by
  the specified number of image columns, the y range is evenly divided by the
  specified number of lines, and the fitted surface values evaluated at the
  sampled x and y points are written as the pixel values of the image.  A
  linear world coordinate system based on the x and y values is also created
  for the image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_coordinates">coordinates = "<TT></TT>", fit = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='coordinates' Line='coordinates = "", fit = ""'>
  <DD>The first two columns of the text file specified by the coordinates parameter
  are use to supply x and y values which are evaluated by the surface and
  the resulting x, y, and z values are appended to the specified fit file.
  If either parameter is not specified then this surface evaluation is
  not done.  Note that the input data points are evaluated as part of
  the standard output but one may, if desired, specify the input file
  as the coordinate file to create a separate output.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B><A NAME="l_function">function = "<TT>polynomial</TT>" (chebyshev|legendre|polynomial)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='function' Line='function = "polynomial" (chebyshev|legendre|polynomial)'>
  <DD>Surface function type to fit.  The choices are a chebyshev, legendre,
  or simple power series bi-dimensional polynomial.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xorder">xorder = 2, yorder = 2</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xorder' Line='xorder = 2, yorder = 2'>
  <DD>The polynomial orders in x and y.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xterms">xterms = "<TT>full</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xterms' Line='xterms = "full"'>
  <DD>The options are:
  <DL>
  <DT><B><A NAME="l_none">none</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='none' Line='none'>
  <DD>The individual polynomial terms contain powers of x or powers of y but not
  powers of both.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_half">half</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='half' Line='half'>
  <DD>The individual polynomial terms contain powers of x and powers of y, whose
  maximum combined power is max (xorder - 1, yorder - 1).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_full">full</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='full' Line='full'>
  <DD>The individual polynomial terms contain powers of x and powers of y, whose
  maximum combined power is max (xorder - 1 + yorder - 1).
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_weighting">weighting = "<TT>user</TT>" (uniform|user|statistical|instrumental)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='weighting' Line='weighting = "user" (uniform|user|statistical|instrumental)'>
  <DD>The type of weighting for the fit. The options are:
  <DL>
  <DT><B><A NAME="l_uniform">uniform</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='uniform' Line='uniform'>
  <DD>All weights are 1.  Any input weights are ignored.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_user">user</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='user' Line='user'>
  <DD>The weights in the fourth input column are used.  If no weight is given
  a weight of 1 is supplied.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_statistical">statistical</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='statistical' Line='statistical'>
  <DD>The reciprocal of the absolute value of z input data is used as the weight.
  Any input weights are ignored.  Z values less than 1e-20 are set to 1e-20.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_instrumental">instrumental</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='instrumental' Line='instrumental'>
  <DD>The fourth input column is taken as a sigma and the weight is the
  reciprocal of the sigma squared.  If no sigma is given a sigma of
  1 is supplied.  Sigma values less than 1e-10 are set to 1e-10.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xmin">xmin = INDEF, xmax = INDEF, ymin = INDEF, ymax = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xmin' Line='xmin = INDEF, xmax = INDEF, ymin = INDEF, ymax = INDEF'>
  <DD>These parameters define the range of input x and y data to be used and
  also define the range over which the surface function is defined.  If
  INDEF then the appropriate limit from the input data points is used.
  If input data points lie outside these limits they are discarded.  The
  range may be given larger than the range of the input data in order
  to all evaluating coordinates outside input data; i.e. to
  allow extrapolation.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_zmin">zmin = INDEF, zmax = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='zmin' Line='zmin = INDEF, zmax = INDEF'>
  <DD>These parameters apply threshold limits to the input data.  If INDEF
  the appropriate limit from the input data points is used.  Input
  data points with z values outside this range are discarded.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ncols">ncols = 100, nlines = 100</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ncols' Line='ncols = 100, nlines = 100'>
  <DD>The number of columns and lines for the optional surface image.  These
  parameters determine the size of the image and how finely the x and
  y input data range is subdivided.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task fits a surface, a function of two coordinates, to a set of
  possibly irregularly sampled data points specified in a text file.
  The input consists of a file with three or four columns.  The first
  two columns define the two coordinates, called x and y, the third
  column gives the value the function is supposed to fit, called z,
  and the optional fourth column is a weight or sigma.  If a weight or
  sigma is not specified it will have a unit weight or sigma.  The type
  of weighting is selected by a task parameter.
  <P>
  The input data points may be restricted by use of the <I>xmin, xmax,
  ymin, ymax, zmin, zmax</I> parameters.  If these parameters are INDEF
  (the default) the full range of the input is used.  The surface function
  is only defined within the specified x and y range.  In order to
  extrapolate outside the range of the input data these limits must
  be specified explicitly.
  <P>
  The functions which may be fit are legendre, chebyshev, or simple
  power series bi-dimensional polynomials.  The user selects the
  function type, the order in x and y, and whether to include
  cross terms.  The orders are the number of coefficients which
  is the highest polynomial power plus 1.  For example the default
  values of 2 in each coordinate define a linear sloped plane.
  All computations are done in double precision.
  <P>
  Several polynomial cross terms options are available. Options "<TT>none</TT>",
  "<TT>half</TT>", and "<TT>full</TT>" are illustrated below for a quadratic polynomial in
  x and y.
  <P>
  <PRE>
  xterms = "none"
  xorder = 3, yorder = 3
  <P>
     z = a11 + a21 * x + a12 * y + a31 * x ** 2 + a13 * y ** 2
  <P>
  xterms = "half"
  xorder = 3, yorder = 3
  <P>
     z = a11 + a21 * x + a12 * y + a31 * x ** 2 + a22 * x * y + a13 * y ** 2
  <P>
  xterms = "full"
  xorder = 3, yorder = 3
  <P>
     z = a11 + a21 * x + a31 * x ** 2 +
           a12 * y + a22 * x * y +  a32 * x ** 2 * y +
           a13 * y ** 2 + a23 * x *  y ** 2 +
           a33 * x ** 2 * y ** 2
  </PRE>
  <P>
  <P>
  The fit results are written to the standard output; the terminal unless
  redirected.  It consists of the input parameters, the coefficients and
  errors, and the input data plus the fitted values and residuals.  The
  coefficient lines contain four columns.  The first two columns are the x
  and y polynomial powers and then the coefficient and error in the
  coefficient are given.  The coefficients are determined based on a
  normalized coordinate; the range of input x and y values, which is shown in
  the output as xmin, xmax, ymin, and ymax, is mapped to the range -1 to 1.
  The data portion gives the x, y, and z input values followed by the fitted
  value and the residual (z - fit) and finally the weight.
  <P>
  There are two types of additional output which may be selected if desired.
  One is a two dimensional image of the surface evenly sampled over the x and
  y data range set by the xmin, xmax, ymin, ymax parameters.  This type of
  output is selected by specifying an image name and the number of columns
  and lines.  The number of columns and lines defines the size of the image
  and also the sampling of the x and y values.  The first pixel in each
  dimension is the minimum x or y value and the sample interval per pixel is
  given by:
  <P>
  <PRE>
  	dx = (xmax - xmin) / (ncols - 1)
  	dy = (ymax - ymin) / (nlines - 1)
  </PRE>
  <P>
  The fitted surface is evaluated at each pixel and written to the image.
  The linear world coordinate system defining the x and y pixel sampling is
  written to the image header.  This allows tasks such as <B>implot</B> and
  <B>listpixels</B> to show the fitted values in the input x and y units.
  <P>
  The second type of output allows the surface to be evaluated at an
  arbitrary set of x and y coordinates.  The coordinates are input
  as a text file.  The first two columns are taken as the x and y values
  and any other columns are ignored.  The x and y values and the fitted
  values are appended to a specified text file.  This output is
  optional and only occurs if both an input coordinate and output
  fit file are specified.  Note that the input data points are
  always evaluated as part of the standard output but the input
  data file may also be used as a coordinate file if desired.
  Also the output data file may be specified as "<TT>STDOUT</TT>" to merge
  this output with the basic results output.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  The following example shows use of all the output options using some
  random numbers.
  <P>
  <PRE>
      cl&gt; urand 50 3 scale=100. &gt;sf1
      cl&gt; head sf1 nl=5
       70.87   42.5  99.06
       51.49  42.19  64.86
       70.75  83.34  80.39
        57.1  67.79  30.24
       60.91  49.76  53.32
  <P>
      cl&gt; urand 5 2 scale=100. seed=2 &gt;sf2
      cl&gt; head sf2
       20.62  17.86
       66.39  86.26
       48.08  35.07
       70.39   95.8
       53.64  15.51
  <P>
      cl&gt; surfit sf1 image=sf coord=sf2 fit=sf3 ncols=20 nlines=20
      Surface parameters:
        function = polynomial
        xorder = 2
        yorder = 2
        xterms = full
        weighting = user
        xmin =    0.684
        xmax =    89.74
        ymin =    1.051
        ymax =    95.36
        zmin =    1.217
        zmax =    99.14
  <P>
  <P>
      Surface coefficients:
         x  y    coeff    error
         0  0  75.7125  17.2504
         1  0 -0.37273 0.356014
         0  1 -0.77194 0.336627
         1  1 0.009884 0.006295
  <P>
      Fitted points:
  	     x        y        z      fit residual   weight
  	 70.87     42.5    99.06  46.2611  52.7989       1.
  	 51.49    42.19    64.86  45.4249  19.4351       1.
  	 70.75    83.34    80.39  43.2899  37.1001       1.
  	  57.1    67.79    30.24  40.3604 -10.1204       1.
  	 60.91    49.76    53.32  44.5562  8.76384       1.
  	 ...
  <P>
        chisqr = 903.797
  <P>
      cl&gt; head sf3
       20.62    17.86  57.8802
       66.39    86.26  40.9855
       48.08    35.07  47.3864
       53.64    15.51  51.9697
  <P>
      cl&gt; listpix sf[*:10,*:10] wcs=world formats="%5.2f %5.2f"
       0.68  1.05  74.65366
      47.56  1.05  57.66973
       0.68 50.69  36.67273
      47.56 50.69  42.6855
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  apphot.fitsky, apphot.txdump, imsurfit
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>