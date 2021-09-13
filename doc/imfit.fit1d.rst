fit1d — Fit a function to image lines or columns
================================================

**Package: imfit**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>fit1d (Jul85)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>images.imfit</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>fit1d (Jul85)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>fit1d</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  fit1d -- fit a function to image lines
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage_">USAGE	</A></H2>
  <! BeginSection: 'USAGE	'>
  <UL>
  <PRE>
  fit1d input output type
  </PRE>
  </UL>
  <! EndSection:   'USAGE	'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>Images to be fit.  The images may contain image sections.  Only the region
  covered by the section will be modified in the output image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>Output images to be created or modified.  The number of output images
  must match the number of input images.  If an output image does not exist
  it is first created and initialized to zero for fit types "<TT>fit</TT>" and
  "<TT>difference</TT>" and to one for fit type "<TT>ratio</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_type">type</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='type' Line='type'>
  <DD>Type of output.  The choices are:
  <DL>
  <DT><B><A NAME="l_fit">fit      </A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='fit' Line='fit      '>
  <DD>An image created from the function fits to the image lines.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_difference">difference</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='difference' Line='difference'>
  <DD>The difference between the image and the fit (i.e. residuals).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ratio">ratio</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='ratio' Line='ratio'>
  <DD>The ratio of the image and fit.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_bpm">bpm = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='bpm' Line='bpm = ""'>
  <DD>List of bad pixel masks.  This may be a null string to not use a
  bad pixel mask, a single mask that applies to all input images, or
  a matching list.  The value may also be !&lt;keyword&gt; to specify a keyword whose
  value is the mask to use.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_axis">axis = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='axis' Line='axis = 1'>
  <DD>Axis along which the one dimensional fitting is done.  Axis 1 corresponds
  to fitting the image lines and axis 2 corresponds to fitting the columns.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interactive">interactive = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = yes'>
  <DD>If <B>interactive</B> is set to yes, a plot of the fit is drawn and the
  cursor is available for interactively examining and adjusting the fit.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_sample">sample = "<TT>*</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sample' Line='sample = "*"'>
  <DD>Lines or columns to be used in the fits.
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
  <DD>Function to be fit to the image lines or columns.  The functions are
  "<TT>legendre</TT>" (legendre polynomial), "<TT>chebyshev</TT>" (chebyshev polynomial),
  "<TT>spline1</TT>" (linear spline), and "<TT>spline3</TT>" (cubic spline).  The functions
  may be abbreviated.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_order">order = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='order' Line='order = 1'>
  <DD>The order of the polynomials or the number of spline pieces.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_low_reject">low_reject = 0., high_reject = 0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='low_reject' Line='low_reject = 0., high_reject = 0.'>
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
  <DT><B><A NAME="l_grow">grow = 0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='grow' Line='grow = 0.'>
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
  A one dimensional function is fit to each line or column of the input images.
  The function may be a legendre polynomial, chebyshev polynomial,
  linear spline, or cubic spline of a given order or number of spline pieces.
  The output image is of pixel type real and is formed from the fitted
  function values, the difference or residuals of the fit (pixel value -
  fitted value), or the ratio between the pixel values and the fitted values.
  <P>
  The output image may exist in which case a section in the input image is
  applied to the output image.  Thus, a section on the input image causes only
  that part of the output image to be changed.  If the output image does not
  exist it is first created with a size given by the full (without a section)
  input image and initialized to zero for fit and difference output types
  and one for ratio output types.
  <P>
  A bad pixel mask may be specified to exclude data from the fitting.  Any
  non-zero value in the mask is excluded.   It appears in the interactive
  fitting in the same way as manually deleted points.  The mask is matched to
  the input image(s) as described by <B>pmmatch</B>.  The default is matching
  in physical coordinates.
  <P>
  The points fit are determined by selecting a sample of lines or columns
  specified by the parameter <I>sample</I> and taking either the average or
  median of the number of points specified by the parameter <I>naverage</I>.
  The type of averaging is selected by the sign of the parameter and the number
  of points is selected by the absolute value of the parameter.
  The sample points are specified relative to any image sections.
  <P>
  If <I>low_reject</I> and/or <I>high_reject</I> are greater than zero the sigma
  of the residuals between the fitted points and the fitted function is computed
  and those points whose residuals are less than <I>-low_reject</I> * sigma
  and greater than <I>high_reject</I> * sigma are excluded from the fit.
  Points within a distance of <I>grow</I> pixels of a rejected pixel are also
  excluded from the fit.  The function is then refit without the rejected points.
  This rejection procedure may be iterated a number of times given by the
  parameter <I>niterate</I>.
  <P>
  The fitting parameters (<I>sample, naverage, function, order, low_reject,
  high_reject, niterate, grow</I>)
  may be adjusted interactively if the parameter <I>interactive</I> is yes.
  Lines or columns from the image are selected to be fit with the <B>icfit</B>
  package.  A single column or line may be chosen or a blank-separated range
  may be averaged.  Note that the averaging applies only to the graphed
  data used to set the fitting parameters.  The actual image lines and columns
  are fit individually.  The interactive cursor mode commands for this package
  are described in a separate help entry under "<TT>icfit</TT>".  Line 1 is automatically
  selected for one dimensional images and any number of lines or columns may be
  selected for two dimensional images.  Note that the lines or columns are
  relative to the input image section; for example line 1 is the first line of
  the image section and not the first line of the image.  When an end-of-file or
  no line(s) or column(s) are given then the last selected fitting parameters
  are used on each line or column of the image.  This step is repeated for
  each image in the input list.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  To create a smoothed version of an image by fitting the image lines:
  <P>
      cl&gt; fit1d image fitimage fit
  <P>
  If the interactive flag is set and the image is two dimensional then a prompt
  for an image line is printed:
  <P>
      image: Fit line = 100 200
  <P>
  The selected lines are averaged, graphed, and the interactive options for
  setting and fitting the line are used.  Exiting with <TT>'q'</TT> or return prompts for
  another line if the image is two dimensional.  When the fitting parameters
  are suitably set then respond with end-of-file or return to fit all the lines
  of the image and create the output image.
  <P>
  2.  To subtract a linear function fit to columns 10 to 20 and 80 to 100 from
  columns 10 to 100 and to subtract another linear function fit to lines
  110 to 120 and 180 to 200 from columns 110 to 200:
  <P>
  <PRE>
      cl&gt; fit1d image1[10:100,*] output diff axis=2 sample="1:11,71:91"
      cl&gt; fit1d image1[110:200,*] output diff axis=2 sample="1:11,71:91"
  </PRE>
  <P>
  Pixels outside columns 10 to 100 and 110 to 200 are not affected.  Note that the
  sample points are specified relative to the image sections.  The script
  <B>background</B> is available in other packages for doing background
  subtractions.
  <P>
  3.  To determine a small scale response image:
  <P>
      cl&gt; fit1d image1 flat ratio
  <P>
  The task <B>imred.generic.flat1d</B> is available for making flat field images
  by this method with the addition of an extra parameter to limit the data values
  for which the ratio is computed.
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imred.generic.background, imred.generic.flat1d
  xtools.icfit, lineclean, imsurfit
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>