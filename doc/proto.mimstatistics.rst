mimstatistics — Do image statistics through a mask
==================================================

**Package: proto**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>mimstatistics (Sep01)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>proto</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>mimstatistics (Sep01)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>mimstatistics</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  mimstatistics -- compute and print image pixel statistics using iterative
  rejection and masks
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage_">USAGE	</A></H2>
  <! BeginSection: 'USAGE	'>
  <UL>
  imstatistics images
  </UL>
  <! EndSection:   'USAGE	'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_images">images</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>The input images or image sections for which pixel statistics are to be
  computed. Image sections are automatically applied to the input masks
  <I>imasks</I> if input masks are not mask sections.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_imasks">imasks = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='imasks' Line='imasks = ""'>
  <DD>The list of input masks or input mask sections associated with <I>images</I>.
  Good and bad data values are assumed to be presented by mask values of 0 and
  1 respectively. The number of input masks must be 0, 1, or equal to the number
  of input images. Input mask sections if present override the input image
  sections.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_omasks">omasks = "<TT></TT>" </A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='omasks' Line='omasks = "" '>
  <DD>The list of output masks which are a combination of the input mask if any
  and pixels rejected using the good data limits and / or iterative clipping.
  Data used to compute the statistics are represented by 0 in the output mask,
  rejected data by zero. The number of output masks must be 0 or equal to
  the number of input images.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fields">fields = "<TT>image,npix,mean,stddev,min,max</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fields' Line='fields = "image,npix,mean,stddev,min,max"'>
  <DD>The statistical quantities to be computed and printed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_lower">lower = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lower' Line='lower = INDEF'>
  <DD>The minimum good data limit.  All pixels are above the default value of INDEF.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_upper">upper = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='upper' Line='upper = INDEF'>
  <DD>The maximum good data limit.  All pixels are above the default value of INDEF.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nclip">nclip = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nclip' Line='nclip = 0'>
  <DD>The maximum number of iterative clipping cycles. By default no clipping is
  performed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_lsigma">lsigma = 3.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lsigma' Line='lsigma = 3.0'>
  <DD>The low side clipping factor in sigma.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_usigma">usigma = 3.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='usigma' Line='usigma = 3.0'>
  <DD>The high side clipping factor in sigma.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_binwidth">binwidth = 0.1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='binwidth' Line='binwidth = 0.1'>
  <DD>The width of the histogram bins in sigma used for computing the midpoint
  (estimate of the median) and the mode.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_format">format = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='format' Line='format = yes'>
  <DD>Label the output columns and print the results in fixed format ? If format
  is "<TT>no</TT>" no column labels are printed and the output is in free format.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_cache">cache = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cache' Line='cache = no'>
  <DD>Cache the image data in memory ? This can increase the efficiency of the
  task if nclip &gt; 0 or if either of the midpt or mode statistics is computed.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The statistical quantities specified by the parameter <I>fields</I> are
  computed and printed for each image in the list specified by <I>images</I>.
  The results are printed in tabular form with the fields listed in the order
  they are specified in the fields parameter. The available fields are the
  following:
  <P>
  <PRE>
  	 image - the image name
  	  mask - the mask name
  	  npix - the number of pixels used to do the statistics
  	  mean - the mean of the pixel distribution
  	 midpt - estimate of the median of the pixel distribution
  	  mode - the mode of the pixel distribution
  	stddev - the standard deviation of the pixel distribution
  	  skew - the skew of the pixel distribution
        kurtosis - the kurtosis of the pixel distribution
  	   min - the minimum pixel value
  	   max - the maximum pixel value
  </PRE>
  <P>
  The mean, standard deviation, skew, kurtosis, min and max are computed in a
  single pass through the image using the expressions listed below.
  Only the quantities selected by the fields parameter are actually computed.
  <P>
  <PRE>
            mean = sum (x1,...,xN) / N
  	     y = x - mean
        variance = sum (y1 ** 2,...,yN ** 2) / (N-1)
          stddev = sqrt (variance)
            skew = sum ((y1 / stddev) ** 3,...,(yN / stddev) ** 3) / (N-1)
        kurtosis = sum ((y1 / stddev) ** 4,...,(yN / stddev) ** 4) / (N-1) - 3
  </PRE>
  <P>
  The midpoint and mode are computed in two passes through the image. In the
  first pass the standard deviation of the pixels is calculated and used
  with the <I>binwidth</I> parameter to compute the resolution of the data
  histogram. The midpoint is estimated by integrating the histogram and
  computing by interpolation the data value at which exactly half the
  pixels are below that data value and half are above it. The mode is
  computed by locating the maximum of the data histogram and fitting the
  peak by parabolic interpolation.
  <P>
  Pixels are rejected from the initial statistics computation by specifying an
  input mask <I>imasks</I> or by setting the good data limits <I>lower</I>
  and <I>upper</I>. Iterative rejection can be performed by setting the
  clipping parameters <I>nclip</I>, <I>lsigma</I>, and <I>usigma</I>.
  <P>
  The input masks <I>imasks</I> can be specified in a variety of ways as
  shown below.
  <P>
  <PRE>
  	       "" - empty mask, use all the pixels
  	    EMPTY - empty mask, use all the pixels
  	 !KEYWORD - use mask specified by  header keyword KEYWORD
  	!^KEYWORD - use inverse of mask specified by  header keyword KEYWORD
  	     mask - use specified mask
  	    ^mask - use inverse of specified mask
  </PRE>
  <P>
  In all cases the mask values are assumed to be 0 in good data regions and 
  non-zero in rejected data regions. The input masks may in pixel list, e.g.
  "<TT>.pl</TT>" format, or integer images format, e.g. "<TT>.imh</TT>", "<TT>.fits</TT>", etc.
  <P>
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Find the number of pixels, mean, standard deviation and the minimum
  and maximum pixel value of a bias region in an image.
  <P>
  <PRE>
      cl&gt; mimstat flat*[*,1] ""
      #      IMAGE      NPIX      MEAN    STDDEV       MIN       MAX
        flat1[*,1]       800     999.5     14.09      941.     1062.
        flat2[*,1]       800     999.4     28.87      918.     1413.
  </PRE>
  <P>
  The string "<TT>flat*</TT>" uses a wildcard to select all images beginning with the
  word flat.  The string "<TT>[*,1]</TT>" is an image section selecting row 1.
  <P>
  2. Compute the mean, midpoint, mode and standard deviation of a pixel
  distribution.
  <P>
  <PRE>
      cl&gt; mimstat m51 "" fields="image,mean,midpt,mode,stddev"
      #      IMAGE    PIXELS      MEAN     MIDPT     MODE     STDDEV
  	     M51    262144     108.3     88.75    49.4       131.3
  </PRE>
  <P>
  3. Compute the image statistics in an image section using a mask.
  <P>
  <PRE>
      cl&gt; mimstat m51[200:400,200:400] imasks=M51.bpm.pl 
  <P>
      cl&gt; mimstat m51[200:400,200:400] imasks=M51.bpm.pl[200:400,200:400] 
  <P>
      cl&gt; mimstat m51[200:400,200:400] imasks=M51.crm.pl[1:201,1:201] 
  </PRE>
  <P>
  Note that the first two examples are equivalent so there is no need to
  specify the input mask section in the second case.
  <P>
  4. Compute the image statistics using interactive rejection and save the
  rejected pixel mask.
  <P>
  <PRE>
      cl&gt; mimstat m51 omasks=m51.rej.pl nclip=3
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  When using a very large number of pixels the accumulation of the sums
  of the pixel values to the various powers may encounter roundoff error.
  This is significant when the true standard deviation is small compared
  to the mean.
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>