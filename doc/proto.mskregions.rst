mskregions — Create or modify masks using regions lists
=======================================================

**Package: proto**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>mskregions (Dec01)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>proto</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>mskregions (Dec01)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>mskregions</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  mskregions -- Create mask from a list of region specifications
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  mskregions regions masks refimages
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_regions">regions</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='regions' Line='regions'>
  <DD>The list of input regions files. The number of regions files must be one or
  equal to the number of output mask images. Regions files contain a list of
  region specifications one region per line. The region specifications may be
  a simple region description, e.g. "<TT>circle 100. 100. 50.</TT>", or a region
  expression, e.g.  "<TT>circle (100., 100., 50.) &amp;&amp; circle (125., 100., 50.)</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_masks">masks</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='masks' Line='masks'>
  <DD>The output masks. The size of the output masks defaults to the size of
  the reference image or the value of the dims parameter in that order of
  precedence.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_refimages">refimages</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='refimages' Line='refimages'>
  <DD>The optional list of reference images. If the reference image list is defined
  there must be one reference image for every output mask.
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
  <DD>The default output mask depth in bits currently 27.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_regnumber">regnumber = "<TT>constant</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='regnumber' Line='regnumber = "constant"'>
  <DD>The region definition scheme. The options are:
  <DL>
  <DT><B><A NAME="l_constant">constant</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='constant' Line='constant'>
  <DD>Assign all the mask regions the value of <I>regval</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_number">number</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='number' Line='number'>
  <DD>Assign each region a sequential value beginning with <I>regval</I>.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_regval">regval = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='regval' Line='regval = 1'>
  <DD>The starting mask region value.
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
  <DT><B><A NAME="l_append">append = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='append' Line='append = no'>
  <DD>Add the region list to an existing mask ?
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
  Mskregions reads a list of region specifications from the input files
  <I>regions</I> and writes the results to the output masks <I>masks</I> image.
  The number of regions files must be on or equal to the number of output
  masks. The size of the output mask is determined by the reference image
  <I>refimages</I> if any <I>refmasks</I> if any or the values in the
  <I>dims</I> parameter in that order of precedence.
  <P>
  The output mask is an integer image. Therefore all mask values must be
  integer. The mask values assigned to the regions in <I>regions</I> are
  determined  by the <I>regnumber</I> and <I>regval</I> parameters. By
  default all new regions are assigned the value of 1. The depth of the output
  mask in bits is defined by the <I>depth</I> parameter. The default value is
  27 bits.
  <P>
  The input region specifications may be region descriptions or region
  expressions. Region descriptions are simple definitions of common geometric
  shapes. Evaluation of the regions expressions is carried out one line at a time.
  <P>
  <B>Regions Definitions</B>
  <P>
  The following region definitions are supported.
  <P>
  <PRE>
        point x1 y1
       circle xc yc r
      ellipse xc yc r ratio theta
          box x1 y1 x2 y2)
    rectangle xc yc r ratio theta
       vector x1 y1 x2 y2 width
          pie xc yc theta1 theta2
      polygon x1 y1 ..., xn yn
         cols ranges
        lines ranges
     cannulus xc yc r1 r2
     eannulus xc yc r1 r2 ratio theta
     rannulus xc yc r1 r2 ratio theta
     pannulus width x1 y1 ... xn yn
  </PRE>
  <P>
  <B>Operands Used in Region Expressions</B>
  <P>
  Input operands are represented symbolically in the input expression. Use of
  symbolic operands allows the same expression to be used with different data
  sets, simplifies the expression syntax, and allows a single input image
  to be used several places in the same expression.
  <P>
  There is a special builtin type of operand used to represent the
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
  <B>Operators Used in Region Expressions</B>
  <P>
  The expression syntax implemented by mskexpr provides the following
  set of operators:
  <P>
  <PRE>
          ( expr )                grouping
          &amp;&amp;                      logical and
          ||                      logical or
          !                       logical not
  </PRE>
  <P>
  <P>
  <B>Functions Used in Region Expressions</B>
  <P>
  Mskexpr supports a group of boolean region functions which can be used to set
  values inside or outside of certain geometric shapes. The routines may be
  called in two ways. The first way assumes that the output masks are two-
  dimensional. The second way assumes that they are multi-dimensional and
  specifies which dimensions the geometric operator applies to.
  <P>
  <PRE>
        point (x1, x2)
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
        point (I, J, x1, x2)
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
  cl&gt; type regions.dat
  cannulus 256. 256. 20. 40.
  cl&gt; mskregions regions.dat mask.pl ""
  </PRE>
  <P>
  2. Repeat the previous example but set all the pixels outside the circular
  annulus to 1. Note that in this case the user must use regions expression
  syntax not region definition syntax
  <P>
  <PRE>
  cl&gt; type region.dat
  ! cannulus (256., 256., 20., 40.) 
  cl&gt; mskregions regions.dat mask.pl ""
  </PRE>
  <P>
  3. Create a 0-valued 512 x 512 mask and set all the pixels inside the
  intersection of 2 circles to 1. The &amp; operator produces the same result
  as &amp;&amp;.
  <P>
  <PRE>
  cl&gt; type regions.dat
  circle (220., 220., 50.) &amp;&amp; circle (240., 220., 50.) 
  cl&gt; mskexpr regions.dat mask.pl ""
  </PRE>
  <P>
  4. Create a 0 valued 512 x 512 mask and set all the pixels inside a circle
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
  cl&gt; type regions.dat
  cmpie (256., 256., 50., 0., 30.) ? 1 : 0
  <P>
  cl&gt; mskregions regions.dat mask.pl "" exprdb=myexpr.db
  </PRE>
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
  imexpr, mskexpr
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>