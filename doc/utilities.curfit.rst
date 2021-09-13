.. _curfit:

curfit — Fit data with Chebyshev, Legendre or spline curve
==========================================================

**Package: utilities**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  curfit -- fit a curve to a list or an image section
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  curfit input 
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The data to be fit.  May be an image section, STDIN or a list of file names.
  </DD>
  </DL>
  <DL>
  <DT><B>function = legendre</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='function' Line='function = legendre'>
  <DD>The type of function with which to fit the data.  Choices are 
  legendre, chebyshev, spline1 (linear spline) or spline3 (cubic spline).
  </DD>
  </DL>
  <DL>
  <DT><B>order = 4</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='order' Line='order = 4'>
  <DD>The order of the fit or number of spline pieces. 
  </DD>
  </DL>
  <DL>
  <DT><B>weighting = uniform</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='weighting' Line='weighting = uniform'>
  <DD>The type of weighting for the fit. The options are:
  <DL>
  <DT><B>uniform</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='uniform' Line='uniform'>
  <DD>The weight w = 1.0.  This option may be used for both list input and image
  input.
  </DD>
  </DL>
  <DL>
  <DT><B>user</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='user' Line='user'>
  <DD>The weights are supplied by the user. This option may be used for list input
  only.
  </DD>
  </DL>
  <DL>
  <DT><B>statistical</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='statistical' Line='statistical'>
  <DD>The weight w = 1.0 / y. This option can be used for both list and image data.
  </DD>
  </DL>
  <DL>
  <DT><B>instrumental</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='instrumental' Line='instrumental'>
  <DD>The user supplies the sigmay for each point and w = 1.0 / sigmay ** 2.
  This option may be used for list input only.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>interactive = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = yes'>
  <DD>If <B>interactive</B> is set to yes, a plot of the fit is drawn and the
  cursor is available for interactively examining and adjusting the fit.
  </DD>
  </DL>
  <DL>
  <DT><B>axis = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='axis' Line='axis = 1'>
  <DD>If <B>input</B> names an image or image section, this parameter specifies
  the axis along which the image is projected for fitting.
  </DD>
  </DL>
  <DL>
  <DT><B>listdata = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='listdata' Line='listdata = no'>
  <DD>If <B>listdata</B> is set to yes, the only printed output will be the calculated 
  values for the X,Y pairs. This is useful as input to <I>graph</I> or some
  other list oriented program.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>If <B>verbose</B> is set to yes, the fitted (X,Y) pairs are listed in addition 
  to the default output of filename, function type, order, rejection parameters, 
  coefficients and their errors.
  </DD>
  </DL>
  <DL>
  <DT><B>power = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='power' Line='power = no'>
  <DD>If <B>power</B> is set to yes, the coefficients of the legendre or
  chebyshev polynomials will be converted to power series coefficients.
  </DD>
  </DL>
  <DL>
  <DT><B>calctype = "<TT>double</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='calctype' Line='calctype = "double"'>
  <DD>Calculation datatype.  The two datatypes are "<TT>real</TT>" (single precision) and
  "<TT>double</TT>" (double precision).
  </DD>
  </DL>
  <DL>
  <DT><B>device = "<TT>stdgraph</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='device' Line='device = "stdgraph"'>
  <DD>The output device for interactive graphics.
  </DD>
  </DL>
  <DL>
  <DT><B>cursor = "<TT>stdgcur</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cursor' Line='cursor = "stdgcur"'>
  <DD>The source of graphics cursor input.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  A curve is fit to data read from either an image section or a list.
  The type of curve is set by the <B>function</B> parameter as either
  a legendre polynomial, chebyshev polynomial, linear spline or cubic
  spline, with the order of the fit (or number of spline pieces) set by
  <B>order</B>.  If data is read from an image, the <B>axis</B> parameter
  is used to reduce the dimensionality of the image; it specifies the
  axis along which the image is projected.  For example, when <B>axis</B>
  = 1, the image is compressed to a column.  <B>Axis</B> = 2 would project
  the image along a line; <B>axis</B> = 3 indicates projection in the z
  direction, etc.
  <P>
  The input data must be ordered in x because of a restriction in the
  interactive plotting package.  If the input is from a list, the data
  are sorted prior to fitting; image input data are assumed to be ordered
  in x and are not explicitly sorted by <I>curfit</I>.
  <P>
  If the input is from a list the user may specify a set of weights,
  <B>weighting</B> = user or a set of errors, <B>weighting</B> =
  instrumental. An additional weighting option <B>weighting</B> = statistical
  can be used for both list and image data. The default is <B>weighting</B> =
  uniform.
  <P>
  When <B>interactive</B> = yes, the curve is plotted and cursor commands allow
  for interactive examining and adjustment of the fit. 
  The full range of interactive cursor commands is available
  including those for changing the function type, order, and rejection criteria,
  and examining the residuals.
  <P>
  The final fit parameters are written to STDOUT with the
  format controlled by parameters <B>verbose</B> and <B>listdata</B>.
  By default, the function type, order, and resulting chi-square are 
  printed as well as the coefficients and their standard deviations.  
  If <B>verbose</B> is set to yes, a list of X, Y_calculated, Y_input,
  and W_input is also printed.
  If <B>listdata</B> is set to yes, the only printed output will
  be a listing of X, Yc, Y and W. This provides a list suitable as input to
  <B>graph</B> or any other list oriented utility.  Setting <B>listdata</B> 
  to yes overrides the verbose option.
  <P>
  When <B>power</B> = yes, the coefficients are converted to power series
  coefficients of the form a0 + a1*X + a2*X**2 +a3*X**3 ....
  Only legendre and chebyshev coefficients are converted; a conversion
  of spline coefficients is meaningless.  Also, errors in the coefficients
  are not converted.
  <P>
  The user has a choice of single or double precision calculations.  Generally
  double precisions is used since the calculation time is only slightly
  longer.  The single precision calculation is used in many other tasks
  which do many fits.  This task provides a test tool to compare the
  results between the two levels of precision.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1.  The x,y pairs in file test.data are interactively fit with a fourth 
  order legendre polynomial.  The printed output is shown.
  <P>
  	cl&gt; curfit test.data 
  <P>
  <PRE>
  	NOAO/IRAF V2.0 Hammond@lyra Fri 11:45:41 13-Dec-85
  	file = test.data
  	function = legendre
  	grow = 0.
  	naverage = 1
  	order = 4
  	low_reject = 0., high_reject = 0.
  	niterate = 1
  	sample = *
  	total points = 8
  	sample points = 8
  	nrejected = 0
  	deleted = 0
  	square root of reduced chi square = 3.008706E-6
  		coefficient	  error
   	1	   2.633E1	  1.098E-6
   	2	   3.150E1	  1.820E-6
   	3	   8.167E0	  1.896E-6
   	4	 -1.621E-6	  2.117E-6
  <P>
  </PRE>
  2.  Fit a cubic spline to the last 12 columns of image "<TT>m74</TT>".
  <P>
     cl&gt; curfit m74[501:512,1:512] axis=2 func=spline3 order=5
  <P>
  3. Use <I>curfit</I> as a filter to overplot a smoothed curve to an existing
  plot of the data points.  The command line for <B>graph</B> is shown as
  well as the <B>curfit</B> command.  Note the interactive flag for 
  <B>curfit</B> is turned off.
  <P>
     cl&gt; graph points.list point+ mark=box wx1=.13 xlab="<TT>X VALUES</TT>"\<BR>
     &gt;&gt;&gt; ylab="<TT>Y VALUES</TT>" title="<TT>Legendre fit to points.list</TT>"
  <P>
     cl&gt; type points.list | curfit list+ inter- | graph append+
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  icfit,  polyfit
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
