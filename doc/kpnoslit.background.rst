background — Fit and subtract a line or column background
=========================================================

**Package: kpnoslit**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>background (Jul85)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.imred.generic</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>background (Jul85)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>background</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  background -- Fit and subtract a line or column background
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage_">USAGE	</A></H2>
  <! BeginSection: 'USAGE	'>
  <UL>
  background input output
  </UL>
  <! EndSection:   'USAGE	'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>Images to be background subtracted.  The images may contain image sections.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>Output images to be created and modified.  The number of output images must
  match the number of input images.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_axis">axis = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='axis' Line='axis = 1'>
  <DD>Axis along which to fit the background and subtract.  Axis 1 fits and
  subtracts the background along the lines and axis 2 fits and subtracts
  the background along the columns.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interactive">interactive = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = yes'>
  <DD>Set the fitting parameters interactively?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_sample">sample = "<TT>*</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sample' Line='sample = "*"'>
  <DD>Lines or columns to be used in the background fits.  The default "<TT>*</TT>" selects
  all lines or columns.
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
  <DD>Low and high rejection limits in units of the residual sigma.
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
  <DD>Graphics device for interactive graphics output.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_cursor">cursor = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cursor' Line='cursor = ""'>
  <DD>Graphics cursor input
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  For each line or column in the input images a function is fit to the columns
  or lines specified by the sample parameter.  This function is then subtracted
  from the entire line or column to create an output line or column.
  The function fitting parameters may be set interactively.
  This task is a script using <B>fit1d</B>.  For more discussion about
  the parameters see the help text for <B>icfit</B> and <B>fit1d</B>.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  A spectrum of an object runs down the center of a 500 x 500 image.  To
  subtract a constant background using columns 10 to 100 and 410 to 500:
  <P>
  	cl&gt; background image image sample="<TT>10:100,410:500</TT>"
  <P>
  To subtract a quadratic background from the columns of an image in which
  the spectrum lies between lines 50 and 70:
  <P>
  	cl&gt; background image image axis=2 sample="<TT>1:40,80:120</TT>" o=3
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  fit1d, icfit
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>