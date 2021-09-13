geomap — Compute geometric transforms using matched coordinate lists
====================================================================

**Package: immatch**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>geomap (Jan01)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>images.immatch</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>geomap (Jan01)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>geomap</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  geomap -- compute one or more spatial transformation functions
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  geomap input database xmin xmax ymin ymax
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The list of text files containing the pixel coordinates of control points in
  the reference and input images. The control points are listed
  one per line with xref, yref, xin, and yin in columns 1 through 4 respectively.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_database">database</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='database' Line='database'>
  <DD>The name of the text file database where the computed transformations will
  be stored.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xmin">xmin, xmax, ymin, ymax</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xmin' Line='xmin, xmax, ymin, ymax'>
  <DD>The range of reference coordinates over which the computed coordinate
  transformation is valid. If the user is working in pixel units  these limits
  should normally be set to the values of the column and row limits of the
  reference image, e.g xmin = 1.0, xmax = 512, ymin= 1.0, ymax = 512 for
  a 512 x 512 image. The minimum and maximum xref and yref values in <I>input</I>
  are used if xmin, xmax, ymin, or ymax are undefined.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_transforms">transforms = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='transforms' Line='transforms = ""'>
  <DD>An optional list of transform record names. If transforms is undefined 
  the database record(s) are assigned the names of the
  individual text files specified by <I>input</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_results">results = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='results' Line='results = ""'>
  <DD>Optional output files containing a summary of the results including a
  description of the transform geometry and a listing of the input coordinates,
  the fitted coordinates, and the fit residuals. The number of results files
  must be one or equal to the number of input files. If results is "<TT>STDOUT</TT>" the
   results summary is printed on the standard output.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fitgeometry">fitgeometry = "<TT>general</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fitgeometry' Line='fitgeometry = "general"'>
  <DD>The fitting geometry to be used. The options are the following.
  <DL>
  <DT><B><A NAME="l_shift">shift</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='shift' Line='shift'>
  <DD>X and y shifts only are fit.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xyscale">xyscale</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='xyscale' Line='xyscale'>
  <DD>X and y shifts and x and y magnification factors are fit. Axis flips are
  allowed for.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_rotate">rotate</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='rotate' Line='rotate'>
  <DD>X and y shifts and a rotation angle are fit. Axis flips are allowed for.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_rscale">rscale</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='rscale' Line='rscale'>
  <DD>X and y shifts, a magnification factor assumed to be the same in x and y, and a
  rotation angle are fit. Axis flips are allowed for.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_rxyscale">rxyscale</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='rxyscale' Line='rxyscale'>
  <DD>X and y shifts, x and y magnifications factors, and a rotation angle are fit.
  Axis flips are allowed for.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_general">general</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='general' Line='general'>
  <DD>A polynomial of arbitrary order in x and y is fit. A linear term and a
  distortion term are computed separately. The linear term includes an x and y
  shift, an x and y scale factor, a rotation and a skew.  Axis flips are also
  allowed for in the linear portion of the fit. The distortion term consists
  of a polynomial fit to the residuals of the linear term. By default the
  distortion term is set to zero.
  </DD>
  </DL>
  <P>
  For all the fitting geometries except "<TT>general</TT>" no distortion term is fit,
  i.e. the x and y polynomial orders are assumed to be 2 and the cross term
  switches are assumed to be "<TT>none</TT>", regardless of the values of the
  <I>xxorder</I>, <I>xyorder</I>, <I>xxterms</I>, <I>yxorder</I>, <I>yyorder</I> and
  <I>yxterms</I> parameters set by the user.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_function">function = "<TT>polynomial</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='function' Line='function = "polynomial"'>
  <DD>The type of analytic surface to be fit. The options are the following.
  <DL>
  <DT><B><A NAME="l_legendre">legendre</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='legendre' Line='legendre'>
  <DD>Legendre polynomials in x and y.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_chebyshev">chebyshev</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='chebyshev' Line='chebyshev'>
  <DD>Chebyshev polynomials in x and y.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_polynomial">polynomial</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='polynomial' Line='polynomial'>
  <DD>Power series in x and y.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xxorder">xxorder = 2, xyorder = 2,  yxorder = 2, yyorder = 2</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xxorder' Line='xxorder = 2, xyorder = 2,  yxorder = 2, yyorder = 2'>
  <DD>The order of the polynomials in x and y for the x and y fits respectively.
  The default order and cross term settings define the linear term in x
  and y, where the 6 coefficients can be interpreted in terms of an x and y shift,
  an x and y scale change, and rotations of the x and y axes. The "<TT>shift</TT>",
  "<TT>xyscale</TT>", "<TT>rotation</TT>", "<TT>rscale</TT>", and "<TT>rxyscale</TT>", fitting geometries
  assume that the polynomial order parameters are 2 regardless of the values
  set by the user. If any of the order parameters are higher than 2 and
  <I>fitgeometry</I> is "<TT>general</TT>", then a distortion surface is fit to the
  residuals from the linear portion of the fit.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xxterms">xxterms = "<TT>half</TT>", yxterms = "<TT>half</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xxterms' Line='xxterms = "half", yxterms = "half"'>
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
  maximum combined power is max (xxorder - 1, xyorder - 1) for the x fit and
  max (yxorder - 1, yyorder - 1) for the y fit. 
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_full">full</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='full' Line='full'>
  <DD>The individual polynomial terms contain powers of x and powers of y, whose
  maximum combined power is max (xxorder - 1, xyorder - 1) for the x fit and
  max (yxorder - 1, yyorder - 1) for the y fit.
  </DD>
  </DL>
  <P>
  The "<TT>shift</TT>", "<TT>xyscale</TT>", "<TT>rotation</TT>", "<TT>rscale</TT>", and "<TT>rxyscale</TT>" fitting
  geometries, assume that the cross term switches are set to "<TT>none</TT>"
  regardless of the values set by the user.  If either of the cross terms
  parameters are set to "<TT>half</TT>" or "<TT>full</TT>" and <I>fitgeometry</I> is "<TT>general</TT>"
  then a distortion surface is fit to the residuals from the linear
  portion of the fit.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_maxiter">maxiter = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maxiter' Line='maxiter = 0'>
  <DD>The maximum number of rejection iterations. The default is no rejection.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_reject">reject = 3.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='reject' Line='reject = 3.0'>
  <DD>The rejection limit in units of sigma.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_calctype">calctype = "<TT>real</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='calctype' Line='calctype = "real"'>
  <DD>The precision of the coordinate transformation calculations. The options are
  real and double.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print messages about actions taken by the task ?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interactive">interactive = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = yes'>
  <DD>In interactive mode the user may interact with the fitting process, e.g.
  change the order of the fit, reject points, display the data, etc.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_graphics">graphics = "<TT>stdgraph</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = "stdgraph"'>
  <DD>The graphics device.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_cursor">cursor = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cursor' Line='cursor = ""'>
  <DD>The graphics cursor.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  GEOMAP computes the transformation required to map the reference coordinate
  system to the input coordinate system.  The coordinates of points in common
  to the two systems are listed in the input text file(s) <I>input</I>
  one per line in the following format: "<TT>xref yref xin yin</TT>".
  <P>
  The computed transforms are stored in the text database file <I>database</I>
  in records with names specified by the parameter <I>transforms</I>. If the
  transforms parameter is undefined the records are assigned the name of
  the input coordinate files.
  <P>
  The computed transformation has the form shown below, where the reference
  coordinates must be defined in the coordinate system of the reference image
  system if the user intends to resample an image with gregister or geotran, or
  transform coordinates from the reference coordinate system to the input
  image coordinate system. 
  <P>
  <PRE>
      xin = f (xref, yref)
      yin = g (xref, yref)
  </PRE>
  <P>
  If on the other hand the user wishes to transform coordinates from the
  input image coordinate system to the reference coordinate system then he or she
  must reverse the roles of the reference and input coordinates as defined above,
  and compute the inverse transformation.
  <P>
  <P>
  The functions f and g are either a power series polynomial or a Legendre or
  Chebyshev polynomial surface of order <I>xxorder</I> and <I>xyorder</I> in x
  and <I>yxorder</I> and <I>yyorder</I> in y.
  <P>
  Several polynomial cross terms options are available. Options "<TT>none</TT>",
  "<TT>half</TT>", and "<TT>full</TT>" are illustrated below for a quadratic polynomial in
  x and y.
  <P>
  <PRE>
  xxterms = "none", xyterms = "none"
  xxorder = 3, xyorder = 3, yxorder = 3, yyorder = 3
  <P>
     xin = a11 + a21 * xref + a12 * yref +
           a31 * xref ** 2 + a13 * yref ** 2
     yin = a11' + a21' * xref + a12' * yref +
           a31' * xref ** 2 + a13' * yref ** 2
  <P>
  xxterms = "half", xyterms = "half"
  xxorder = 3, xyorder = 3, yxorder = 3, yyorder = 3
  <P>
     xin = a11 + a21 * xref + a12 * yref +
           a31 * xref ** 2 + a22 * xref * yref + a13 * yref ** 2
     yin = a11' + a21' * xref + a12' * yref +
           a31' * xref ** 2 + a22' * xref * yref + a13' * yref ** 2
  <P>
  xxterms = "full", xyterms = "full"
  xxorder = 3, xyorder = 3, yxorder = 3, yyorder = 3
  <P>
     xin = a11 + a21 * xref + a31 * xref ** 2 +
           a12 * yref + a22 * xref * yref +  a32 * xref ** 2 * yref +
           a13 * yref ** 2 + a23 * xref *  yref ** 2 +
           a33 * xref ** 2 * yref ** 2
     yin = a11' + a21' * xref + a31' * xref ** 2 +
           a12' * yref + a22' * xref * yref +  a32' * xref ** 2 * yref +
           a13' * yref ** 2 + a23' * xref *  yref ** 2 +
           a33' * xref ** 2 * yref ** 2
  </PRE>
  <P>
  If the <B>fitgeometry</B> parameter is anything other than "<TT>general</TT>", the  order
  parameters assume the value 2 and the cross terms switches assume the value
  "<TT>none</TT>", regardless of the values set by the user. The computation can be done in
  either real or double precision by setting <I>calctype</I>. Automatic pixel
  rejection may be enabled by setting axiter &gt; 0 and <I>reject</I> to some
  number greater than 0.
  <P>
  <I>Xmin</I>, <I>xmax</I>, <I>ymin</I> and <I>ymax</I> define the region of
  validity of the fit in the reference coordinate system and must be set by
  the user. These parameters can be used to reject out of range data before the
  actual fitting is done.
  <P>
  GEOMAP may be run interactively by setting <I>interactive</I> = yes and
  inputting commands by the use of simple keystrokes.
  In interactive mode the user has the option of changing the
  fit parameters and displaying the data graphically until a satisfactory
  fit has been achieved. The available keystroke commands are listed
  below.
  <P>
  <PRE>
  ?	Print options
  f	Fit the data and graph with the current graph type (g, x, r, y, s)
  g	Graph the data and the current fit
  x,r	Graph the x fit residuals versus x and y respectively
  y,s	Graph the y fit residuals versus x and y respectively
  d,u	Delete or undelete the data point nearest the cursor
  o	Overplot the next graph
  c	Toggle the constant x, y plotting option
  t       Plot a line of constant x, y through the nearest data point	
  l	Print xshift, yshift, xmag, ymag, xrotate, yrotate
  q	Exit the interactive curve fitting
  </PRE>
  <P>
  The parameters listed below can be changed interactively with simple colon
  commands. Typing the parameter name alone will list the current value.
  <P>
  <PRE>
  :show				List parameters
  :fitgeometry			Fitting geometry (shift,xyscale,rotate,
  				rscale,rxyscale,general)
  :function [value]	        Fitting function (chebyshev,legendre,
                                  polynomial)
  :xxorder :xyorder [value]	X fitting function xorder, yorder
  :yxorder :yyorder [value]	Y fitting function xorder, yorder
  :xxterms :yxterms [n/h/f]	X, Y fit cross terms type
  :maxiter [value]		Maximum number of rejection iterations
  :reject [value]			Rejection threshold
  </PRE>
  <P>
  The final fit is stored in a simple text file in a format suitable for use
  by the GREGISTER or GEOTRAN tasks.
  <P>
  If <I>verbose</I>  is "<TT>yes</TT>", various pieces of useful information are printed
  to the terminal as the task proceeds. If <I>results</I> is set to a file name
  then the input coordinates, the fitted coordinates, and the residuals of
  the fit are written to that file.
  <P>
  The transformation computed by the "<TT>general</TT>" fitting geometry is arbitrary
  and does not correspond to a physically meaningful model. However the computed
  coefficients for the linear term can be given a simple geometrical geometric
  interpretation for all the fitting geometries as shown below.
  <P>
  <PRE>
  	fitting geometry = general (linear term)
  	    xin = a + b * xref + c * yref
  	    yin = d + e * xref + f * yref
  <P>
  	fitting geometry = shift
  	    xin = a + xref
  	    yin = d + yref
  <P>
  	fitting geometry = xyscale
  	    xin = a + b * xref
  	    yin = d + f * yref
  <P>
  	fitting geometry = rotate
  	    xin = a + b * xref + c * yref
  	    yin = d + e * xref + f * yref
  	    b * f - c * e = +/-1
  	    b = f, c = -e or b = -f, c = e
  <P>
  	fitting geometry = rscale
  	    xin = a + b * xref + c * yref
  	    yin = d + e * xref + f * yref
  	    b * f - c * e = +/- const
  	    b = f, c = -e or b = -f, c = e
  <P>
  	fitting geometry = rxyscale
  	    xin = a + b * xref + c * yref
  	    yin = d + e * xref + f * yref
  	    b * f - c * e = +/- const
  </PRE>
  <P>
  The coefficients can be interpreted as follows. Xref0, yref0, xin0, yin0
  are the origins in the reference and input frames respectively. Orientation
  and skew are the rotation of the x and y axes and their deviation from
  perpendicularity respectively. Xmag and ymag are the scaling factors in x and
  y and are assumed to be positive.
  <P>
  <PRE>
  	general (linear term)
  	    xrotation = rotation - skew / 2
  	    yrotation = rotation + skew / 2
  	    b = xmag * cos (xrotation)
  	    c = ymag * sin (yrotation)
  	    e = -xmag * sin (xrotation)
  	    f = ymag * cos (yrotation)
  	    a = xin0 - b * xref0 - c * yref0 = xshift
  	    d = yin0 - e * xref0 - f * yref0 = yshift
  <P>
  	shift
  	    xrotation = 0.0,  yrotation = 0.0
  	    xmag = ymag = 1.0
  	    b = 1.0
  	    c = 0.0
  	    e = 0.0
  	    f = 1.0
  	    a = xin0 - xref0 = xshift
  	    d = yin0 - yref0 = yshift
  <P>
  	xyscale
  	    xrotation 0.0 / 180.0 yrotation = 0.0
  	    b = + /- xmag
  	    c = 0.0
  	    e = 0.0
  	    f = ymag
  	    a = xin0 - b * xref0 = xshift
  	    d = yin0 - f * yref0 = yshift
  <P>
  	rscale
  	    xrotation = rotation + 0 / 180, yrotation = rotation
  	    mag = xmag = ymag
  	    const = mag * mag
  	    b = mag * cos (xrotation)
  	    c = mag * sin (yrotation)
  	    e = -mag * sin (xrotation)
  	    f = mag * cos (yrotation)
  	    a = xin0 - b * xref0 - c * yref0 = xshift
  	    d = yin0 - e * xref0 - f * yref0 = yshift
  <P>
  	rxyscale
  	    xrotation = rotation + 0 / 180, yrotation = rotation
  	    const = xmag * ymag
  	    b = xmag * cos (xrotation)
  	    c = ymag * sin (yrotation)
  	    e = -xmag * sin (xrotation)
  	    f = ymag * cos (yrotation)
  	    a = xin0 - b * xref0 - c * yref0 = xshift
  	    d = yin0 - e * xref0 - f * yref0 = yshift
  </PRE>
  <P>
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Compute the linear transformation between coordinate systems.
     A record called "<TT>m51.coo</TT>" will be written in the database
     file "<TT>database</TT>".
  <P>
  <P>
  <PRE>
  	cl&gt; geomap m51.coo database 1. 512. 1. 512.
  </PRE>
  <P>
  2. Compute the 3rd order transformation in x and y between two
     coordinate systems.  A record called "<TT>m51.coo</TT>" will be written in
     the database file "<TT>database</TT>". This record supersedes the one
     of the same name written in example 1.
  <P>
  <PRE>
  	cl&gt; geomap m51.coo database 1. 512. 1. 512. xxo=4 xyo=4 \<BR>
  	&gt;&gt;&gt; yxo=4 yyo=4 xxt=full yxt=full inter-
  </PRE>
  <P>
  3. Register a 500 by 500 image of m51 to an 800 by 800 image of the same
  field taken with a different instrument, and display the original
  800 by 800 image and the transformed image. Use the default fitting parameters.
  <P>
  <PRE>
  	cl&gt; geomap m51.coo database 1.0 800.0 1.0 800.0
  	cl&gt; gregister m51.500 m51.500.out database m51.coo
  	cl&gt; display m51.800 1 fi+
  	cl&gt; display m51.500.out 2 fi+
  </PRE>
  <P>
  4. Use the above transform to transform a list of object pixel coordinates
  in the m51.800 image to their pixel coordinates in the m51.500 system.
  <P>
  <PRE>
  	cl&gt; geoxytran m51.800.xy m51.500.xy database m51.coo
  </PRE>
  <P>
  5. Transform object pixel coordinates in the m51.500 image to their
  pixel coordinates in the m51.800 image. Note that to do this the roles
  of the reference and input coordinates defined in example 3 must be
  reversed and the inverse transform must be computed.
  <P>
  <PRE>
  	cl&gt; fields m51.coo 3,4,1,2 &gt; m51.coo.inv
  	cl&gt; geomap m51.coo.inv database 1.0 512.0 1.0 512.0
  	cl&gt; geoxytran m51.512.xy m51.800.xy database m51.coo.inv
  </PRE>
  <P>
  6. Compute 3 different transforms, store them in the same database file,
  and use them to transform 3 different images.  Use the original image names as
  the database record names.
  <P>
  <PRE>
  	cl&gt; geomap coo1,coo2,coo3 database 1. 512. 1. 512. \<BR>
  	&gt;&gt;&gt; transforms=im1,im2,im3
  	cl&gt; gregister im1,im2,im3  im1.out,im2.out,im3.out database \<BR>
  	&gt;&gt;&gt; im1,im2,im3
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  <P>
  The user should be aware that for high order fits the "<TT>polynomial</TT>" basis
  functions become very unstable. Switching to the "<TT>legendre</TT>" or "<TT>chebyshev</TT>"
  polynomials and/or going to double precision will usually cure the problem.
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imshift, magnify, rotate, imlintran, gregister, geotran, geoxytran
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>