lineclean — Replace deviant pixels in image lines
=================================================

**Package: imfit**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>lineclean (May85)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>images.imfit</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>lineclean (May85)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>lineclean</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  lineclean -- replace deviant pixels in image lines
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage_">USAGE	</A></H2>
  <! BeginSection: 'USAGE	'>
  <UL>
  <PRE>
  lineclean input output
  </PRE>
  </UL>
  <! EndSection:   'USAGE	'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>Input images to be cleaned.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>Output cleaned images.  The number of output images must be the same as the
  number of input images.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_sample">sample = "<TT>*</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sample' Line='sample = "*"'>
  <DD>Columns to be used in fitting the cleaning function.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_naverage">naverage = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='naverage' Line='naverage = 1'>
  <DD>Number of sample points to combined to create a fitting point.
  A positive value specifies an average and a negative value specifies
  a median.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_function">function = spline3</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='function' Line='function = spline3'>
  <DD>Cleaning function to be fit to the image lines.  The functions are:
  <DL>
  <DT><B><A NAME="l_legendre">legendre</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='legendre' Line='legendre'>
  <DD>Legendre polynomial of the specified order.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_chebyshev">chebyshev</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='chebyshev' Line='chebyshev'>
  <DD>Chebyshev polynomial of the specified order.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_spline1">spline1</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='spline1' Line='spline1'>
  <DD>Linear spline of the specified number of pieces.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_spline3">spline3</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='spline3' Line='spline3'>
  <DD>Cubic spline of the specified number of pieces.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_order">order = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='order' Line='order = 1'>
  <DD>The order of the polynomials or the number of spline pieces.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_low_reject">low_reject = 2.5, high_reject = 2.5</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='low_reject' Line='low_reject = 2.5, high_reject = 2.5'>
  <DD>Rejection limits below and above the fit in units of the residual sigma.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_niterate">niterate = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='niterate' Line='niterate = 1'>
  <DD>Number of rejection iterations.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_grow">grow = 1.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='grow' Line='grow = 1.'>
  <DD>When a pixel is rejected, pixels within this distance of the rejected pixel
  are also rejected.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_graphics">graphics = "<TT>stdgraph</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = "stdgraph"'>
  <DD>Graphics output device for interactive graphics.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_cursor">cursor = "<TT>stdgcur</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cursor' Line='cursor = "stdgcur"'>
  <DD>Graphics cursor input.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  A one dimensional function is fit to each line of the input images.
  The function may be a legendre polynomial, chebyshev polynomial,
  linear spline, or cubic spline of a given order or number of spline pieces.
  If <I>low_reject</I> and/or <I>high_reject</I> are greater than zero the sigma
  of the residuals between the fitted points and the fitted function is computed
  and those points whose residuals are less than <I>-low_reject</I> * sigma
  and greater than <I>high_reject</I> * sigma are excluded from the fit.
  Points within a distance of <I>grow</I> pixels of a rejected pixel are also
  excluded from the fit.  The function is then refit without the rejected points.
  This rejection procedure may be iterated a number of times given by the
  parameter <I>niterate</I>.  Finally, the
  rejected points in the input image are replaced by the fitted values
  to create the output image lines.
  <P>
  The output image may exist in which case a section in the input image is
  applied to the output image.  Thus, a section on the input image causes only
  that part of the output image to be cleaned.  If the output image does not
  exist it is first created by making a copy of the full (without a section)
  input image.
  <P>
  The points fit are determined by selecting a sample of columns specified by
  the parameter <I>sample</I> and taking either the average or median of
  the number of points specified by the parameter <I>naverage</I>.
  The type of averaging is selected by the sign of the parameter and the number
  of points is selected by the absolute value of the parameter.
  The sample points are specified relative to any image section.
  <P>
  The fitting parameters (<I>sample, naverage, function, order, low_reject,
  high_reject, niterate, grow</I>)
  may be adjusted interactively if the parameter <I>interactive</I> is yes.
  Lines from the image are selected to be fit with the <B>icfit</B> package.
  For images of greater than two dimensions sets of numbers giving the
  2nd, 3rd, etc. coordinates are entered.
  The image lines are specified relative to any image section.
  When an end-of-file or no line is given then the last selected fitting
  parameters are used on each line of the image.  This step is repeated for
  each image in the input list.  The interactive options are described
  in the help information <B>icfit</B>.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. To clean pixels deviating by more than 2.5 sigma:
  <P>
  	cl&gt; lineclean image cleanimage
  <P>
  If the interactive flag is set then a prompt for an image line is
  printed:
  <P>
  	image: Fit line = 100
  <P>
  For a one or two dimensional image the line number is entered (1 for a one
  dimensional image).  For a three dimensional image two numbers are entered.
  For example:
  <P>
  	image: Fit line = 10 2
  <P>
  for line 10 of the second image plane.
  <P>
  The selected line is graphed and the interactive options for setting and
  fitting the line are used.  Data points marked with diamonds indicate
  points to be replaced by the fitted value.  Exiting with <TT>'q'</TT> or return
  prompts for another line.  When the fitting parameters are suitably set
  then respond with end-of-file or return to fit all the lines of the image
  and create the output image.
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  fit1d, xtools.icfit, imsurfit
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>