bscale — Linearly transform the intensities of a list of images
===============================================================

**Package: proto**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>bscale (Aug91)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>proto</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>bscale (Aug91)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>bscale</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  bscale -- linearly transform the intensity scales of a list of images
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage_">USAGE	</A></H2>
  <! BeginSection: 'USAGE	'>
  <UL>
  bscale input output 
  </UL>
  <! EndSection:   'USAGE	'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input </A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input '>
  <DD>List of images to be transformed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>List of output transformed images. If the output list is the same as the input
  list the input images are overwritten.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_bzero">bzero = "<TT>0.</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='bzero' Line='bzero = "0."'>
  <DD>The zero point to be subtracted before applying the scale factor.
  The options are a numerical value, "<TT>mean</TT>", "<TT>median</TT>", or "<TT>mode</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_bscale">bscale = "<TT>1.</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='bscale' Line='bscale = "1."'>
  <DD>The scale factor to be applied.  The options are a numerical value,
  "<TT>mean</TT>", "<TT>median</TT>", or "<TT>mode</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_section">section = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='section' Line='section = ""'>
  <DD>The image section to be used for computing the image statistics.  If section
  is "<TT></TT>", <I>step</I> is used to define the default image section. <I>Section</I>
  is used to confine the computation of the mean, median, and mode
  to a specific region of the image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_step">step = 10</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='step' Line='step = 10'>
  <DD>The step size in pixels which defines the default image section to be used
  for computing the mean, median, and mode.
  In image section notation the default section is equivalent to [*:10,*:10,...].
  <I>Step</I> is used if
  the sampling along an axis is not defined by <I>section</I>.
  Subsampling can significantly reduce the memory and 
  time required for the computation of the mean, median, and mode.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_upper">upper = "<TT>INDEF</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='upper' Line='upper = "INDEF"'>
  <DD>Upper intensity limit to be used for computing the mean, median, and mode.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_lower">lower = "<TT>INDEF</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lower' Line='lower = "INDEF"'>
  <DD>Lower intensity limit to be used for computing the mean, median, and mode.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print messages about actions taken by the task?
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  The specified input images <I>input</I>  are linearly transformed in intensity
  and written to the list of output images <I>output</I>, using the
  zero point specified by <I>bzero</I> and the scale factor specified by
  <I>bscale</I>.  If the output image list
  is the same as the input image list the input images will be overwritten.
  <P>
  The expression defining the linear transformation is listed below.
  <P>
  	NEW = (OLD - BZERO) / BSCALE
  <P>
  OLD is the input pixel brightness, NEW is the output
  pixel brightness, BZERO is the zero point offset, and BSCALE is the
  scale factor.  The values of the scaling parameters <I>bzero</I> and
  <I>bscale</I>
  may be specified explicitly or the mean, median, or mode of the image
  may be used for either quantity.  If the input image pixel type
  is short, integer, or long, overflow or truncation may occur.
  <P>
  When one of the scaling parameters is the image mean, median,
  or mode, then the image mean, median, and mode are calculated. The statistics
  computation can be restricted to a section of the input image by setting
  the parameter
  <I>section</I>. Otherwise the parameter <I>step</I> is used to
  define a default image section.
  Subsampling the image can significantly reduce the memory
  and time requirements for computing the statistics of large images.
  If numerical values for both the scaling parameters are specified, then
  the image statistics are not computed. The statistics computation can
  be limited to given intensity range by setting the parameters
  <I>lower</I> and <I>upper</I>.
  <P>
  The mean, median, and mode are computed using the following algorithm.
  Note that this algorithm requires that all the data to used for computing
  the statistics must be in memory.
  <P>
  <PRE>
  1. The data in the specified image section is read into a buffer.
  2. The data is sorted in increasing order of intensity.
  3. The points outside upper and lower are excluded.
  4. The median is set to the data value at the midpoint of the remaining
     data.
  5. The mean and sigma of the remaining data are computed.
  6. The histogram bin width (.1*sigma)  and separation (.01*sigma) are
     computed.
  7. The location of the bin containing the most data points is determined.
  8. The median of the data values in that bin is used to estimate the mode.
  </PRE>
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Use the mode to subtract a constant background from a list of images.
  Overwrite the input images.
  <P>
  <PRE>
  	cl&gt; bscale *.imh *.imh bzero=mode
  </PRE>
  <P>
  2. Scale a list of images to a unit mean. Overwrite the input images.
  <P>
  <PRE>
  	cl&gt; bscale *.imh *.imh bscale=mean
  </PRE>
  <P>
  3. Scale a list of images to the intensity range 0 to 511,
  where 234. and 1243. are the original data range. Overwrite the input
  images. This example uses the CL to calculate bscale.
  <P>
  <PRE>
  	cl&gt; bscale.bzero = 234.
  	cl&gt; bscale.bscale = (1243. - 234.) / 512.
  	cl&gt; bscale *.imh *.imh
  </PRE>
  <P>
  4. Scale an image using a user specified bzero and bscale and create a new
  output image: 
  <P>
  <PRE>
          cl&gt; bscale imagein imageout bzero=0.0 bscale=1.10 
  </PRE>
  <P>
  5. Median subtract a list of input images using the percent replace facility to
  create the output image names.
  <P>
  <PRE>
          cl&gt; bscale images*.imh %i%outi%*.imh bzero=median bscale=1.0
  </PRE>
  <P>
  6. Repeat the previous example but use the @ file facility for specifying
  the input and output image lists.
  <P>
  <PRE>
          cl&gt; bscale @infile @outfile bzero=median bscale=1.0
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imarith,imcombine
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>