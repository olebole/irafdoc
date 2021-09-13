linebias — Fit and subtract an average line bias
================================================

**Package: bias**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>linebias (Mar93)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.imred.bias</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>linebias (Mar93)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>linebias</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  linebias -- Fit and subtract an average line bias
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage_">USAGE	</A></H2>
  <! BeginSection: 'USAGE	'>
  <UL>
  <PRE>
  linebias input output
  </PRE>
  </UL>
  <! EndSection:   'USAGE	'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>Images to be bias subtracted.  The images may not contain image sections.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>Output bias subtracted images.  An output images may be the same as its
  matching input image.  The output image pixel type will real regardless
  of the input image pixel type.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_bias">bias = "<TT>[]</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='bias' Line='bias = "[]"'>
  <DD>Bias section appended to the input image to define the bias region.
  The default section or an empty string will use the full image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_trim">trim = "<TT>[]</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='trim' Line='trim = "[]"'>
  <DD>Trim section appended to the input image to define the region to be
  bias subtracted and output.  The default section or an empty string
  will use the full image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_median">median = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='median' Line='median = no'>
  <DD>Take the median of the bias lines?  If no then the bias lines are averaged.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_function">function = "<TT>spline3</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='function' Line='function = "spline3"'>
  <DD>The function fit to the average bias line.  The functions are "<TT>legendre</TT>",
  "<TT>chebyshev</TT>", "<TT>spline1</TT>", or "<TT>spline3</TT>".  Abbreviations are allowed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_order">order</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='order' Line='order'>
  <DD>The order (number of terms or number of spline pieces) in the function.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_low_reject">low_reject = 3.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='low_reject' Line='low_reject = 3.0'>
  <DD>The low sigma rejection factor.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_high_reject">high_reject = 3.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='high_reject' Line='high_reject = 3.0'>
  <DD>The high sigma rejection factor.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_niterate">niterate = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='niterate' Line='niterate = 1'>
  <DD>The maximum number of rejection iterations.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interactive">interactive = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = yes'>
  <DD>Fit the average bias line interactively?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_logfile">logfile = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logfile' Line='logfile = ""'>
  <DD>Name of a log file.  If no file name is given then no log file is kept.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_logfiles">logfiles = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logfiles' Line='logfiles = ""'>
  <DD>List of log files.  If no file name is given then no log file is kept.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_graphics">graphics = "<TT>stdgraph</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = "stdgraph"'>
  <DD>Graphics output device for interactive graphics.
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
  For each input image in the input image list an average or median bias line
  is determined from the bias region.  The bias region
  is defined by the bias section applied to the input image.  A function of
  the image columns is fit to the average bias line.  This function is subtracted
  from each image line in the trim region.  The trim region is defined by the
  trim section applied to the input image.  The bias subtracted and trimmed
  image is output to the output image.  The input and output images may not
  contain sections and the number of images in each list must be the same.
  <P>
  If the interactive flag is set then the user may interactively examine
  and fit the average bias line.  The interactive fitting is done using the
  interactive curve fitting routine (see icfit).  Before each image is
  processed a prompt of the form "<TT>linebias image (yes)? </TT>" is given.
  A response of yes allows interactive fitting for the specified image
  while a response of no uses the last defined fitting parameters.
  The default value is accepted with a carriage return.  The possible
  responses are "<TT>yes</TT>", "<TT>no</TT>", "<TT>YES</TT>", or "<TT>NO</TT>".  The capitalized responses
  permanently set the response to yes or no and the prompt is not
  issued again for the remaining images.  Thus, a response of NO processes
  the remaining images non-interactively while a response of YES processes
  the remaining image interactively without prompting.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  The bias region for a set of images occupies columns 1 to 800 and lines
  801 to 832.  To subtract the bias and remove the bias region:
  <P>
  <PRE>
  	cl&gt; linebias.bias = "[*, 801:832]"
  	cl&gt; linebias.trim = "[*, 1:800]"
  	cl&gt; linebias ccd* ccd*
  	linebias ccd001 (yes)? yes
  	linebias ccd002 (yes)?
  	linebias ccd003 (no)? NO
  </PRE>
  <P>
  The first two lines set the bias and trim parameters.  These parameters
  could be temporarily set on the command line but generally these parameters
  are only changed when new instruments are used.  The first image
  is interactively fit and the fitting order is change to 2.  The
  second image is examined and the fit found to be acceptable.  All remaining
  image are then fit non-interactively using the same fitting parameters.
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_revisions">REVISIONS</A></H2>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_LINEBIAS">LINEBIAS V2.10.3</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='LINEBIAS' Line='LINEBIAS V2.10.3'>
  <DD>The output pixel type is now real instead of preserving the pixel type
  of the input image.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  icfit
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>