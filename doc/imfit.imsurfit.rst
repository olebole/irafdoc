imsurfit — Fit a surface to a 2-D image
=======================================

**Package: imfit**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>imsurfit (Feb88)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>images.imfit</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>imsurfit (Feb88)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>imsurfit</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  imsurfit -- fit a surface function to an image
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage_">USAGE	</A></H2>
  <! BeginSection: 'USAGE	'>
  <UL>
  imsurfit input, output, xorder, yorder
  </UL>
  <! EndSection:   'USAGE	'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of images to be fit.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>Output image(s) of <I>type_output</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xorder">xorder</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xorder' Line='xorder'>
  <DD>The order in x of the polynomials (1 = constant) or the number of polynomial
  pieces for the bicubic spline.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_yorder">yorder</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='yorder' Line='yorder'>
  <DD>The order in y of the polynomials (1 = constant) or the number of polynomial
  pieces for the bicubic spline.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_cross_terms">cross_terms = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cross_terms' Line='cross_terms = yes'>
  <DD>Cross terms for the polynomials. For example, if <I>xorder</I> = 2 and
  <I>yorder</I> = 2
  then a function of the form z = a + b * x + c * y + d * x * y will be fit.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_function">function = "<TT>leg</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='function' Line='function = "leg"'>
  <DD>Functional for of surface to be fit to the image. The available functions
  (with minimum match abbreviation) are:
  <DL>
  <DT><B><A NAME="l_legendre">legendre</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='legendre' Line='legendre'>
  <DD></DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_chebyshev">chebyshev</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='chebyshev' Line='chebyshev'>
  <DD></DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_spline3">spline3</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='spline3' Line='spline3'>
  <DD></DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_spline1">spline1</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='spline1' Line='spline1'>
  <DD></DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_type_output">type_output = "<TT>fit</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='type_output' Line='type_output = "fit"'>
  <DD>The type of output image.  The allowed types (with minimum match abbreviation)
  are:
  <DL>
  <DT><B><A NAME="l_clean">clean</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='clean' Line='clean'>
  <DD>The input image with deviant pixels in the good regions replaced by the
  fitted value.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fit">fit  </A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='fit' Line='fit  '>
  <DD>An image created from the surface fits to the image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_residual">residual</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='residual' Line='residual'>
  <DD>The difference of the input image and the fitted image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_response">response</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='response' Line='response'>
  <DD>The ratio of the input image to the fitted image.
  All fitted (denominator) pixels below <I>div_min</I> are given a value of 1.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xmedian">xmedian = 1, ymedian = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xmedian' Line='xmedian = 1, ymedian = 1'>
  <DD>The x and y dimensions of the box used for median processing.
  If <I>xmedian</I> &gt; 1 or <I>ymedian</I> is &gt; 1,
  then the median is calculated for each box and used in the surface
  fit instead of the individual pixels.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_median_percent">median_percent = 50.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='median_percent' Line='median_percent = 50.'>
  <DD>If the number of pixels in the median box is less than <I>median_percent</I> *
  <I>xmedian</I> * <I>ymedian</I> the box will be omitted from the fit.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_upper">upper = 0., lower = 0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='upper' Line='upper = 0., lower = 0.'>
  <DD>The number of sigma  limits for pixel rejection. If <I>upper</I> &gt; 0. or
  <I>lower</I> &gt; 0. and median processing is turned off,
  pixel rejection is enabled.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ngrow">ngrow = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ngrow' Line='ngrow = 0'>
  <DD>The radius in pixels for region growing.
  Pixels within a distance of <I>ngrow</I> pixels of
  a rejected pixel are also rejected.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_niter">niter = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='niter' Line='niter = 0'>
  <DD>The maximum number of iterations in the rejection cycle.
  Rejection will be terminated if the number of rejected pixels is zero
  or the number of iterations equals <I>niter</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_regions">regions = "<TT>all</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='regions' Line='regions = "all"'>
  <DD>The available options (with minimum match abbreviation) are:
  <DL>
  <DT><B><A NAME="l_all">all</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='all' Line='all'>
  <DD>All points in the image are fit.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_rows">rows</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='rows' Line='rows'>
  <DD>The fit is performed on the image rows specified by <I>rows</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_columns">columns</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='columns' Line='columns'>
  <DD>The fit is performed on the image columns specified by <I>columns</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_border">border</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='border' Line='border'>
  <DD>The fit is performed on a border around the image whose width is specified
  by <I>border</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_sections">sections</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='sections' Line='sections'>
  <DD>The fit is performed on image sections listed in the file specified
  by <I>sections</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_circle">circle</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='circle' Line='circle'>
  <DD>The fit is performed on a circular region whose parameters are specified by
  <I>circle</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_invcircle">invcircle</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='invcircle' Line='invcircle'>
  <DD>The fit is performed on a region exterior to the circular region whose
  parameters are specified by <I>circle</I>.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_rows">rows = "<TT>*</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rows' Line='rows = "*"'>
  <DD>When <I>region_type</I> = 'rows', the string parameter <I>rows</I> specifies
  the rows to be fit.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_columns">columns = "<TT>*</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='columns' Line='columns = "*"'>
  <DD>When <I>region_type</I> = 'columns', the string parameter <I>columns</I>
  specifies the columns to be fit.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_border">border = "<TT>50</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='border' Line='border = "50"'>
  <DD>When <I>region_type</I> = 'border', the
  string parameter <I>border</I> specifies the width of the border to be fit.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_sections">sections = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sections' Line='sections = ""'>
  <DD>When <I>region_type</I> = 'sections', the
  string parameter <I>sections</I> is the name of the  file containing the list of
  image sections to be fit, where <I>Sections</I> may be the standard
  input (STDIN).
  The sections must be listed one per line in the following form: x1 x2 y1 y2.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_circle">circle = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='circle' Line='circle = ""'>
  <DD>The string parameter <I>circle</I> lists the parameter needed to specify
  the circle in the following format: xcenter ycenter radius. The three
  parameters must be integers.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_div_min">div_min = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='div_min' Line='div_min = INDEF'>
  <DD>When <I>type_output</I> = 'response' all divisions in which the fitted value
  is below <I>div_min</I> are set to the value 1.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  A surface is fit to selected portions of the input image.
  The user may elect to fit the whole image, <I>region_type</I> = 'all',
  selected rows, <I>region_type</I> = 'rows', selected columns,
  <I>region_type</I> = 'columns', a
  border around the image, <I>region_type</I> = 'border' or image sections, 
  <I>region_type</I> = 'sections'. If the sections  option is enabled the user
  must supply the name of the file containing a list of sections,
  <I>sections</I> = 'list', or enter them from the standard input. In either case
  the sections must be listed one per line in the following form: x1 x2 y1 y2.
  <P>
  The parameter <I>surface_type</I> may be a
  "<TT>legendre</TT>" polynomial, "<TT>chebyshev</TT>" polynomial,
  a cubic spline ("<TT>spline3</TT>") or a linear spline ("<TT>spline1</TT>").
  The order of the polynomials is selected in both x and y.
  Cross terms for the polynomial surfaces are optional.
  For the cubic spline the parameters <I>xorder</I> and <I>yorder</I> specify
  the number of polynomial pieces to be fit to the surface in
  each direction.
  <P>
  The output image may be the fitted image, the difference between the
  input and the fitted image, the ratio of the input to the fitted image
  or the input image with deviant pixels in the fitted regions replaced
  with the fitted values, according to whether <I>type_output</I> =
  'fit', 'residual',
  'response' or 'clean'. If <I>type_output</I> = 'response' then pixels in the
  fitted image with values &lt; <I>div_min</I> are replaced by 1.
  If <I>type_output</I> =
  'clean' then at least one of <I>upper</I> or <I>lower</I> must be &gt; 0.
  <P>
  Pixel rejection is enabled if median processing is turned off,
  <I>niter</I> &gt; 0,
  and at least one of the parameters <I>upper</I> and <I>lower</I> is &gt; 0.
  Region growing
  can be turned on by setting <I>ngrow</I> &gt; 0, in which case all pixels within
  a radius ngrow of a deviant pixel will be rejected.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. To create a smoothed version of an image:
  <P>
  <PRE>
  	cl&gt; imsurfit m74 m74smooth 5 10 function=spline3
  </PRE>
  <P>
  2. To create a smoothed version of an image using median processing:
  <P>
  <PRE>
  	cl&gt; imsurfit m74 m74med 5 10 function=spline3 \<BR>
  	&gt;&gt;&gt; xmed=5 ymed=5
  </PRE>
  <P>
  3. To subtract a constant background from an image:
  <P>
  <PRE>
  	cl&gt; imsurfit abell30 abell30bck 1 1 function=leg \<BR>
  	&gt;&gt;&gt; type=resid
  </PRE>
  <P>
  4. To make a ratio image using signals above 1000 units:
  <P>
  <PRE>
  	cl&gt; imsurfit n7006 n7006ratio 20 20 function=spline3 \<BR>
  	&gt;&gt;&gt; type=response div_min=1000
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_timings">TIMINGS</A></H2>
  <! BeginSection: 'TIMINGS'>
  <UL>
  Fitting and subtracting a constant from a 512 by 512 IRAF image requires
  ~35 cpu seconds. Approximately 130 cpu seconds are required to fit a
  second degree polynomial in x and y (including cross-terms) to a
  100 pixel wide border around a 512 by
  512 IRAF image, and to subtract the fitted image from the input image.
  To produce a smooth 512 by 512 IRAF image using a 10 by 10 bicubic spline
  requires ~300 cpu seconds. Timings refer to a VAX 11/750 + fpa.
  <P>
  </UL>
  <! EndSection:   'TIMINGS'>
  <H2><A NAME="s_notes">NOTES</A></H2>
  <! BeginSection: 'NOTES'>
  <UL>
  The surface fitting code uses the IRAF SURFIT math routines,
  which have been optimized for image fitting .
  The routines which fit selected portions
  of the image, perform pixel rejection and region growing, and create and
  maintain a list of rejected pixels utilize the ranges and pixlist packages
  of routines currently maintained in the images directory. These will be
  replaced by more general ranges and image masking routines in the future.
  </UL>
  <! EndSection:    'NOTES'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIMINGS' 'NOTES'  >
  
  </BODY>
  </HTML>