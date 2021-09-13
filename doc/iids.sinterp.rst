sinterp — Interpolate a table of x,y pairs to create a spectrum
===============================================================

**Package: iids**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>sinterp (Mar92)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.onedspec</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>sinterp (Mar92)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>sinterp</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  sinterp -- Interpolate a tables of x,y pairs to produce a spectrum
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  sinterp tbl_file
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_tbl_file">tbl_file</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='tbl_file' Line='tbl_file'>
  <DD>The name of a file which contains the x,y pairs to be used as
  the basis for interpolation. The pairs must be in order of
  increasing x.
  </DD>
  </DL>
  <P>
  The following parameters may or may not be necessary, depending
  on the options selected.
  <P>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>If a few single elements are desired, rather than a full
  array of elements, the user may enter a sequence of x values
  from the terminal or a file to be used to interpolate into
  the x,y table (parameter curve_gen=no).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_image">image</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD>If parameter make_image=yes, then an image file name is needed
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_order">order = 5</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='order' Line='order = 5'>
  <DD>If the interpolator is a polynomial fit or spline (interp_mode=
  chebyshev, legnedre, spline3, spline1), the order of the fit
  is required.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_x1">x1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='x1' Line='x1'>
  <DD>If parameter curve_gen=yes, this is the starting x value to
  begin the curve generation.
  </DD>
  </DL>
  <P>
  Of the following three parameters, two must be specified, and the
  third will be derived.
  <P>
  <DL>
  <DT><B><A NAME="l_x2">x2 = 0.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='x2' Line='x2 = 0.0'>
  <DD>As above, but x2 determines the endpoint of the curve.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_dx">dx = 0.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dx' Line='dx = 0.0'>
  <DD>As above, but dx determines the pixel-to-pixel increment
  to be used during the curves generation.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_npts">npts = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='npts' Line='npts = 0'>
  <DD>As above, but this determines the number of pixels to be generated.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B><A NAME="l_curve_gen">curve_gen = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='curve_gen' Line='curve_gen = no'>
  <DD>If this parameter is set to yes, then parameters x1, and two of
  the three x2, dx, npts are required. The output is in the form
  of new x,y pairs and may be redirected to a text file.
  But if parameter make_image is also yes, the output is
  in the form of an IRAF image file having the name given by
  the parameter image. If curve_gen=no, the user must supply
  a set of x values and interpolation is performed on those values.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_make_image">make_image = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='make_image' Line='make_image = no'>
  <DD>If set to yes, then curve_gen=yes is implied and an image file name
  is requied. A one dimensional IRAF image is created.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_tbl_size">tbl_size = 1024</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='tbl_size' Line='tbl_size = 1024'>
  <DD>This parameter defines the maximum size to be set aside for
  memory storage of the input x,y pairs.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interp_mode">interp_mode = "<TT>chebyshev</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interp_mode' Line='interp_mode = "chebyshev"'>
  <DD>This parameter controls the method of interpolation. The linear
  and curve options are true interpolators, while chebyshev,
  legendre, spline3, and splin1 are fits to the data.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The specified file is read assuming it is a text file containing
  pairs of x,y values in the form: xxx yyy. The table is used
  to define the function y(x). The pairs must be entered in the file
  in increasing order of x.
  <P>
  The user specifies either specific x values for which the function
  is to be evaluated, or specifies that a sequence of values beginning
  with x1 are to be generated. In the former case, the explicit x values
  may come either from the keyboard or from a file. In the latter case
  the user must also specify the sequence by defining the increment, dx,
  the endpoint, x2, and the number of points to generate in the sequence.
  Then y(x) is evaluated at x1, x1+dx, x1+2*dx, ...  , x1+(n-2)*dx, x2.
  Only 2 of the 3 parameters (x2, dx, npts) are needed to fully
  specify the sequence.
  <P>
  The output of the function evaluation is either new x,y pairs written
  to STDOUT, or an IRAF image.
  <P>
  The function used to evaluated the tabular data may be any of the following
  forms:
  <P>
  <DL>
  <DT><B><A NAME="l_">(1)</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='(1)'>
  <DD>Linear interpolation between points.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(2)</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='(2)'>
  <DD>Smooth interpolation between points.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(3)</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='(3)'>
  <DD>A polynomial fit of either Legendre or Chebyshev types.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(4)</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='(4)'>
  <DD>A cubic or linear spline.
  </DD>
  </DL>
  <P>
  If the table of x,y pairs is very large, the parameter tbl_size
  should be set to the number of pairs. For example, if a spectrum
  is available as a text file of x,y pairs (such as might be
  obtained from IUE), and the number of pairs is 4096, then tbl_size
  should be set to 4096. This provides for sufficient memory to
  contain the table.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  The following shows how a text file may be used to generate a spectrum:
  <P>
  <PRE>
  	cl&gt; sinterp textfile make+ x1=4000 x2=5000 npts=1024 \<BR>
  	&gt;&gt;&gt; image=testimage interp_mode=curve
  </PRE>
  <P>
  The following sequence shows how to generate a spectrum of an IRS
  standard star using the calibration file data as the source.
  <P>
  <PRE>
  	cl&gt; lcalib flam feige34 caldir=onedstds$irscal/ &gt;textfile
  	cl&gt; sinterp textfile make+ x1=3550 dx=1.242 npts=1024 \<BR>
  	&gt;&gt;&gt; interp_mode=linear image=feige34
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_revisions">REVISIONS</A></H2>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_SINTERP">SINTERP V2.10.3+</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='SINTERP' Line='SINTERP V2.10.3+'>
  <DD>The image header dispersion coordinate system has been updated to the
  current system.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_SINTERP">SINTERP V2.10</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='SINTERP' Line='SINTERP V2.10'>
  <DD>This task is unchanged.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  lcalib
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>